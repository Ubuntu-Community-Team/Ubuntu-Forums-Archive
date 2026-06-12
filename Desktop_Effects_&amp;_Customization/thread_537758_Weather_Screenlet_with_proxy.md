---
title: "Weather Screenlet with proxy"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by vapore0n on 2007-08-29
Heres is the Weather screenlet fixed to use the global Proxy settings.

changes were to use urllib2 instead of urllib, and use its proxy call.
Make sure to change the proxy to your own. 



```

#!/usr/bin/env python
import re
import urllib2 
import screenlets
from screenlets.options import StringOption, BoolOption
from Numeric import *
import pygtk
pygtk.require('2.0')
import cairo
import pango
import sys
import gobject
import time
import datetime
import math
import gtk
from gtk import gdk


class WeatherScreenlet(screenlets.Screenlet):
	"""A simple Weather Screenlet."""

	opener=urllib2.build_opener(urllib2.ProxyHandler({"http": "http://proxy.com:80"}))))	#use your own proxy
	urllib2.install_opener(opener)
	

	# default meta-info for Screenlets
	__name__ = 'WeatherScreenlet'
	__version__ = '0.1'
	__author__ = 'robgig1088'
	__desc__ = 'A simple Weather Screenlet.'

	# internals
	__timeout = None

	update_interval = 300
	show_error_message = 1

	lasty = 0
	lastx = 0   ## the cursor position inside the window (is there a better way to do this??)
	over_button = 1

	ZIP = "USCA0035"
	use_metric = True

	mini = False
	
	latest = []          ## the most recent settings we could get...
	
	updated_recently = 0 ## don't keep showing the error messages until a connection has been established
			     ## and then lost again.
	
	# constructor
	def __init__(self, text="", **keyword_args):
		#call super (and not show window yet)
		screenlets.Screenlet.__init__(self, width=int(100 * self.scale * 3), height=int(100 * self.scale * 3),
			uses_theme=True, **keyword_args) 
		# set theme
		self.theme_name = "novum"
		# add zip code menu item 
		self.add_menuitem("zipcode", "Zip Code...")
		self.add_menuitem("forecast", "View extended forecast")
		self.add_menuitem("mini", "Toggle mini-view")
		# add default menu items
		self.add_default_menuitems()
		# init the timeout function
		self.update_interval = self.update_interval
                self.add_options_group('Weather',
                        'The weather widget settings')
                self.add_option(StringOption('Weather', 'ZIP',
                        str(self.ZIP), 'ZIP', 'The ZIP code to be monitored taken from Weather.com'), realtime=False)
		self.add_option(BoolOption('Weather', 'show_error_message', 
			bool(self.show_error_message), 'Show error messages', 
			'Show an error message on invalid location code'))
		self.add_option(BoolOption('Weather', 'use_metric', 
			bool(self.use_metric), 'Use metric over imperial units', 
			'Use the metric system for measuring values'))
		self.add_option(BoolOption('Weather', 'mini',
			bool(self.mini), 'Use mini-mode',
			'Switch to the mini-mode'))

	
	# attribute-"setter", handles setting of attributes
	def __setattr__(self, name, value):
		# call Screenlet.__setattr__ in baseclass (ESSENTIAL!!!!)
		screenlets.Screenlet.__setattr__(self, name, value)
		# check for this Screenlet's attributes, we are interested in:
		if name == "ZIP":
			self.__dict__[name] = value
			gobject.idle_add(self.update_weather_data)
		if name == "update_interval":
			if value > 0:
				self.__dict__['update_interval'] = value
				if self.__timeout:
					gobject.source_remove(self.__timeout)
				self.__timeout = gobject.timeout_add(value * 1000, self.update)
			else:
				# TODO: raise exception!!!
				pass


	def update(self):
		gobject.idle_add(self.update_weather_data)
		return True


	def update_weather_data(self):
		temp = self.parseWeatherData()
		
		if temp[0]["where"] == '':    ##did we get any data?  if not...
			if self.show_error_message==1 and self.updated_recently == 1:
				self.show_error()
			self.updated_recently = 0
		else:
			#if temp[0]["where"].find(',') > -1:
			#	temp[0]["where"] = temp[0]["where"][:temp[0]["where"].find(',')]
			self.latest = temp
			self.updated_recently = 1
			self.redraw_canvas()


	def parseWeatherData(self):
		if self.use_metric:
			unit = 'm'
		else:
			unit = 's'
		data = urllib2.urlopen('http://xoap.weather.com/weather/local/'+self.ZIP+'?cc=*&dayf=10&prod=xoap&par=1003666583&key=4128909340a9b2fc&unit='+unit).read()

		forecast = []

		dcstart = data.find('<loc ')
		dcstop = data.find('</cc>')     ###### current conditions
		data_current = data[dcstart:dcstop]
		forecast.append(self.tokenizeCurrent(data_current))

		for x in range(10):
			dcstart = data.find('<day d=\"'+str(x))
			dcstop = data.find('</day>',dcstart)   #####10-day forecast
			day = data[dcstart:dcstop]
			forecast.append(self.tokenizeForecast(day))

		return forecast


	def tokenizeForecast(self, data):
	
		day = self.getBetween(data, '<part p="d">', '</part>')
		daywind = self.getBetween(day, '<wind>', '</wind>')
	
		night = self.getBetween(data, '<part p="n">', '</part>')
		nightwind = self.getBetween(night, '<wind>', '</wind>')

		tokenized = {
		'date': self.getBetween(data, 'dt=\"','\"'),
		'day' : self.getBetween(data, 't=\"','\"'),
		'high': self.getBetween(data, '<hi>','</hi>'),
		'low': self.getBetween(data, '<low>','</low>'),	
		'sunr': self.getBetween(data, '<sunr>','</sunr>'),
		'suns' : self.getBetween(data, '<suns>','</suns>'),		
		'dayicon' : self.getBetween(day, '<icon>','</icon>'), 
		'daystate' : self.getBetween(day, '<t>','</t>'), 
		'daywindspeed' : self.getBetween(daywind, '<s>','</s>'), 
		'daywinddir' : self.getBetween(daywind, '<t>','</t>'), 
		'dayppcp' : self.getBetween(day, '<ppcp>','</ppcp>'), 
		'dayhumid' : self.getBetween(day, '<hmid>','</hmid>'),
		'nighticon' : self.getBetween(night, '<icon>','</icon>'), 
		'nightstate' : self.getBetween(night, '<t>','</t>'), 
		'nightwindspeed' : self.getBetween(nightwind, '<s>','</s>'), 
		'nightwinddir' : self.getBetween(nightwind, '<t>','</t>'), 
		'nightppcp' : self.getBetween(night, '<ppcp>','</ppcp>'), 
		'nighthumid' : self.getBetween(night, '<hmid>','</hmid>'),
		}
		return tokenized

	
	def tokenizeCurrent(self, data):
		wind = self.getBetween(data, '<wind>', '</wind>')
		bar = self.getBetween(data, '<bar>', '</bar>')
		uv = self.getBetween(data, '<uv>', '</uv>')

		tokenized = {
		'where': self.getBetween(data, '<dnam>','</dnam>'),
		'time' : self.getBetween(data, '<tm>','</tm>'),
		'sunr': self.getBetween(data, '<sunr>','</sunr>'),
		'suns' : self.getBetween(data, '<suns>','</suns>'),	
		'date' : self.getBetween(data, '<lsup>','</lsup>'),
		'temp' : self.getBetween(data, '<tmp>','</tmp>'),	
		'flik' : self.getBetween(data, '<flik>','</flik>'), 
		'state' : self.getBetween(data, '<t>','</t>'), 
		'icon' : self.getBetween(data, '<icon>','</icon'),
		'pressure' : self.getBetween(data, '<r>','</r>'),
		'windspeed' : self.getBetween(wind, '<s>','</s>'), 
		'winddir' : self.getBetween(wind, '<t>','</t>'), 
		'humid' : self.getBetween(data, '<hmid>','</hmid>'),
		'vis' : self.getBetween(data, '<vis>','</vis>'),
		'dew' : self.getBetween(data, '<dewp>','</dewp>'),
		}
		return tokenized		


	def getBetween(self, data, first, last):
		x = len(first)
		begin = data.find(first) +x
		end = data.find(last, begin)
		return data[begin:end]


	def get_icon(self, code):
		if code < 3:
			weather = " severe"
		elif code < 5 :
        		weather = " thunderstorm"
		elif code < 7:
			weather = " rainy"
		elif code == 7:
			weather = " snowy"
		elif code < 13 :
			weather = " rainy"
		elif code < 19 :
		        weather = " snowy"
		elif code < 23 :
		        weather = " foggy"
		elif code < 31 :
		        weather = " cloudy"
		elif code < 35 :
		        weather = ""
		elif code == 35 :
		        weather = " rainy"
		elif code == 36 :
		        weather = ""
		elif code < 41 :
     			weather = " rainy"
		elif code < 44 :
 		       weather = " snowy"
		elif code == 44 :
		        weather = " cloudy"
		elif code == 45 :
		        weather = " thunderstorm"
		elif code == 46 :
		        weather = " snowy"
		elif code == 47 :
		        weather = " thunderstorm"
		elif code == 3200:
			weather = " unavailable"
		return weather


	def get_day_or_night(self, weather):
		time = weather[0]["time"].split()[0]
		ampm = weather[0]["time"].split()[1]
		sunset = weather[0]["suns"].split()[0]
		sunrise = weather[0]["sunr"].split()[0]

		hour = time.split(':')[0]
		min = time.split(':')[1]
		risehr = sunrise.split(':')[0]
		risemin = sunrise.split(':')[1]
		sethr = sunset.split(':')[0]
		setmin = sunset.split(':')[1]

		if int(hour) == 12:
			hour = 0
		if ampm == "AM" :
		        if int(risehr) > int(hour) :
		                dark = 1
		        elif int(risehr) < int(hour) :
				dark = 0
		        else :
		                if int(risemin) > int(min) :
        	                	dark = 1
      		          	elif int(risemin) < int(min) :
       	 	                	dark = 0
         		        else :
           				dark = -1

		elif ampm == "PM" :
		        if int(sethr) > int(hour) :
		                dark = 0
		        elif int(sethr) < int(hour) :
		                dark = 1
		        else :
		                if int(setmin) > int(min) :
		                        dark = 0
		                elif int(setmin) < int(min) :
		                        dark = 1
		                else :
		                        dark = -1
		if dark == 1:
			return "moon"
		else:
			return "sun"


	def on_draw(self, ctx):
		weather = self.latest

		# set size
		ctx.scale(self.scale * 3, self.scale * 3)
		# draw bg (if theme available)
		ctx.set_operator(cairo.OPERATOR_OVER)
		if self.theme:
			if (self.mini == False and weather != []):
				self.theme['weather-bg.svg'].render_cairo(ctx)
			else:
				self.theme['weather-bg-mini.svg'].render_cairo(ctx)
		# draw memory-graph
		if self.theme:
			if (self.theme_name == "glassy"):
				ctx.set_source_rgba(0, 0, 0, 0.8)
			else:
				ctx.set_source_rgba(1, 1, 1, 0.8)

			if weather == []:
				ctx.save()	
				ctx.translate(10, 17)
				p_layout = ctx.create_layout()
				p_fdesc = pango.FontDescription()
				p_fdesc.set_family_static("Sans")
				p_fdesc.set_size(3 * pango.SCALE)
				p_fdesc.set_weight(300)
				p_fdesc.set_style(pango.STYLE_NORMAL)   ####render no info message
				p_layout.set_font_description(p_fdesc)
				p_layout.set_markup('<b>No weather information available</b>')						
				ctx.show_layout(p_layout)
				ctx.restore()
			else:
				ctx.save()
				ctx.scale(.6,.6)
				icon = str(self.get_day_or_night(weather)+ self.get_icon(int(weather[0]["icon"]))+ ".svg")
				self.theme[icon].render_cairo(ctx)
				ctx.restore()

				ctx.save()
				ctx.translate(75,10)
				degree = unichr(176)
				p_layout = ctx.create_layout()
				p_fdesc = pango.FontDescription()
				p_fdesc.set_family_static("Sans")
				p_fdesc.set_size(10 * pango.SCALE)
				p_fdesc.set_weight(300)
				p_fdesc.set_style(pango.STYLE_NORMAL)
				p_layout.set_font_description(p_fdesc)   ######render current temp
				if len(str(weather[0]["temp"])) == 3:
					ctx.translate(-7, 0)
				p_layout.set_markup('<b>' + weather[0]["temp"] + degree +'</b>')							
				ctx.show_layout(p_layout)
				ctx.restore()

				ctx.save()	
				ctx.translate(30, 10)
				p_layout = ctx.create_layout()
				p_fdesc = pango.FontDescription()
				p_fdesc.set_family_static("Sans")
				p_fdesc.set_size(4 * pango.SCALE)
				p_fdesc.set_weight(300)
				p_fdesc.set_style(pango.STYLE_NORMAL)   ####render current location
				p_layout.set_font_description(p_fdesc)
				p_layout.set_markup('<b>' + weather[0]["where"][:weather[0]["where"].find(',')] +'</b>')
				ctx.show_layout(p_layout)
				ctx.translate(0, 6)
				p_layout = ctx.create_layout()
				p_fdesc.set_size(3 * pango.SCALE)
				p_layout.set_font_description(p_fdesc)
				p_layout.set_markup('<b>'+weather[0]["where"][weather[0]["where"].find(',') + 2:]+'</b>')
				ctx.show_layout(p_layout)

				ctx.translate(0, 6)
				p_layout = ctx.create_layout()
				p_fdesc = pango.FontDescription()
				p_fdesc.set_family_static("Sans")
				p_fdesc.set_size(3 * pango.SCALE)
				p_fdesc.set_weight(300)
				p_fdesc.set_style(pango.STYLE_NORMAL)   ####render today's highs and lows
				p_layout.set_font_description(p_fdesc)
				p_layout.set_markup('<b>' + "High: "+weather[1]["high"] + degree + "   Low: " +weather[1]["low"] + degree +'</b>')						
				ctx.show_layout(p_layout)
				ctx.restore()
				

				if (self.mini == False):
					ctx.save() 
					ctx.translate(0, 28)
					self.theme['day-bg.svg'].render_cairo(ctx)   ###render the days background
					p_layout = ctx.create_layout()
					p_fdesc = pango.FontDescription()
					p_fdesc.set_family_static("Monospace")
					p_fdesc.set_size(3 * pango.SCALE)
					p_fdesc.set_weight(300)    ##### render the days of the week
					p_fdesc.set_style(pango.STYLE_NORMAL)
					p_layout.set_font_description(p_fdesc)
					p_layout.set_markup('<b>' + "  "+weather[1]["day"].center(14)+weather[2]["day"].center(14)+weather[3]["day"].center(12)+'</b>')						
					ctx.show_layout(p_layout)
					ctx.restore()	

					ctx.save()	
					ctx.translate(0, 50)   ###render the days background
					self.theme['day-bg.svg'].render_cairo(ctx)
					p_layout = ctx.create_layout()
					p_fdesc = pango.FontDescription()
					p_fdesc.set_family_static("Monospace")
					p_fdesc.set_size(3 * pango.SCALE)
					p_fdesc.set_weight(300)    ###render the days of the week (second row)
					p_fdesc.set_style(pango.STYLE_NORMAL)
					p_layout.set_font_description(p_fdesc)
					p_layout.set_markup('<b>' + "  "+weather[4]["day"].center(14)+weather[5]["day"].center(14)+weather[6]["day"].center(12)+'</b>')						
					ctx.show_layout(p_layout)
					ctx.restore()

					ctx.save()
					ctx.translate(36, 28)
					self.theme['divider.svg'].render_cairo(ctx)
					ctx.translate(31,0)     ######render the dividers
					self.theme['divider.svg'].render_cairo(ctx)
					ctx.restore()
		

					ctx.save()
					ctx.translate(6, 30)
					ctx.scale(.4, .4)
					self.theme[self.get_day_or_night(weather)+ self.get_icon(int(weather[1]["nighticon"])) + ".svg"].render_cairo(ctx)				
					ctx.translate(80,0)
					self.theme["sun"+ self.get_icon(int(weather[2]["dayicon"])) + ".svg"].render_cairo(ctx)	
					ctx.translate(77,0)
					self.theme["sun"+ self.get_icon(int(weather[3]["dayicon"])) + ".svg"].render_cairo(ctx)	
					ctx.restore()

					ctx.save()
					ctx.translate(6, 55)
					ctx.scale(.4, .4)
					self.theme["sun"+ self.get_icon(int(weather[4]["nighticon"])) + ".svg"].render_cairo(ctx)				
					ctx.translate(80,0)
					self.theme["sun"+ self.get_icon(int(weather[5]["dayicon"])) + ".svg"].render_cairo(ctx)	
					ctx.translate(77,0)
					self.theme["sun"+ self.get_icon(int(weather[6]["dayicon"])) + ".svg"].render_cairo(ctx)	
					ctx.restore()						
					

					p_layout = ctx.create_layout()
					p_fdesc = pango.FontDescription()
					p_fdesc.set_family_static("Monospace")
					p_fdesc.set_size(3 * pango.SCALE)
					p_fdesc.set_weight(300)    ###note:: this font needs to be set only once for the next few 
					p_fdesc.set_style(pango.STYLE_NORMAL)  #things we need to do, so I'll do it here.
					p_layout.set_font_description(p_fdesc)	
		
					if (self.theme_name == "glassy"):
						ctx.set_source_rgba(.1, .1, .2, 0.8)####setting the default color for the temps
					elif (self.theme_name == "dark"):
						ctx.set_source_rgba(1, 1, 1, 0.8)
					else:
						ctx.set_source_rgba(.6, .8, 1, 0.8)
		
					ctx.save()
					ctx.translate(27, 36)
					p_layout.set_markup('<b>' + weather[1]["high"]+'</b>')					
					ctx.show_layout(p_layout)   ##day1's temps
					ctx.translate(0, 7)
					p_layout.set_markup('<b>' + weather[1]["low"]+'</b>')
					ctx.show_layout(p_layout)
					ctx.restore()
		
					ctx.save()
					ctx.translate(59, 36)
					p_layout.set_markup('<b>' + weather[2]["high"]+'</b>')					
					ctx.show_layout(p_layout)
					ctx.translate(0, 7)   ###day2's temps
					p_layout.set_markup('<b>' + weather[2]["low"]+'</b>')
					ctx.show_layout(p_layout)
					ctx.restore()

					ctx.save()
					ctx.translate(89, 36)
					p_layout.set_markup('<b>' + weather[3]["high"]+'</b>')					
					ctx.show_layout(p_layout)
					ctx.translate(0, 7)
					p_layout.set_markup('<b>' + weather[3]["low"]+'</b>')
					ctx.show_layout(p_layout)
					ctx.restore()

					ctx.save()
					ctx.translate(27, 58)
					p_layout.set_markup('<b>' + weather[4]["high"]+'</b>')					
					ctx.show_layout(p_layout)   ##day4's temps
					ctx.translate(0, 7)
					p_layout.set_markup('<b>' + weather[4]["low"]+'</b>')
					ctx.show_layout(p_layout)
					ctx.restore()

					ctx.save()
					ctx.translate(59, 58)
					p_layout.set_markup('<b>' + weather[5]["high"]+'</b>')					
					ctx.show_layout(p_layout)
					ctx.translate(0, 7)   ###day5's temps
					p_layout.set_markup('<b>' + weather[5]["low"]+'</b>')
					ctx.show_layout(p_layout)
					ctx.restore()

					ctx.save()
					ctx.translate(89, 58)
					p_layout.set_markup('<b>' + weather[6]["high"]+'</b>')					
					ctx.show_layout(p_layout)
					ctx.translate(0, 7)
					p_layout.set_markup('<b>' + weather[6]["low"]+'</b>')
					ctx.show_layout(p_layout)
					ctx.restore()


	def on_draw_shape(self,ctx):
		if self.theme:
			# set size rel to width/height
			ctx.scale(self.scale * 3, self.scale * 3)
			self.theme['weather-bg.svg'].render_cairo(ctx)

	def menuitem_callback(self, widget, id):
		screenlets.Screenlet.menuitem_callback(self, widget, id)
		if id=="zipcode":
			self.show_edit_dialog()
			self.update()
		if id == "forecast":
			self.show_10_day()
		if id == "mini":
			self.mini = not self.mini
			self.update()


	def show_edit_dialog(self):
		# create dialog
		dialog = gtk.Dialog("Zip Code", self.window)
		dialog.resize(300, 100)
		dialog.add_buttons(gtk.STOCK_OK, gtk.RESPONSE_OK, 
			gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL)
		entrybox = gtk.Entry()
		entrybox.set_text(str(self.ZIP))
		dialog.vbox.add(entrybox)
		entrybox.show()	
		# run dialog
		response = dialog.run()
		if response == gtk.RESPONSE_OK:
			self.ZIP = entrybox.get_text()
			self.updated_recently = 1
		dialog.hide()
		self.update()


	def clicked_10_day(self, widget, event):
  	  # toggle window manager frames
		print self.lastx, self.lasty
		if (self.lastx > 200) and (self.lastx < 300) and (self.lasty > 510) and (self.lasty < 550):
			widget.hide()			
		else:
 			widget.begin_move_drag (event.button, 
				int(event.x_root), int(event.y_root), event.time)


	def redraw_10_day(self, widget):
		global supports_alpha
		cr = widget.window.cairo_create()
		cr.scale(self.scale, self.scale)
	
		if supports_alpha == True:
			cr.set_source_rgba(1.0, 1.0, 1.0, 0.0) # Transparent
		else:
			cr.set_source_rgb(1.0, 1.0, 1.0) # Opaque white
    
		cr.save()
 		cr.set_operator(cairo.OPERATOR_SOURCE)
 		cr.paint()
		cr.restore()

		p_layout = cr.create_layout()
		p_fdesc = pango.FontDescription()
		p_fdesc.set_family_static("Free Sans")
		p_fdesc.set_size(9 * pango.SCALE)
		p_layout.set_font_description(p_fdesc)
		p_layout.set_width((self.width) * pango.SCALE) #### create our font info
		if (self.theme_name == "glassy"):
			cr.set_source_rgba(0, 0, 0, 1)
		else:
			cr.set_source_rgba(1,1,1,.8)

		cr.set_operator(cairo.OPERATOR_OVER)


		cr.save()
		cr.scale(5 * self.scale,6 * self.scale)          ###draw background
		self.theme["10-day-bg.svg"].render_cairo(cr)
		cr.restore()


		cr.save()
		cr.scale(5 * self.scale, 3.6  * self.scale)
		cr.translate(-2, 5)  ###draw header
		self.theme["day-bg.svg"].render_cairo(cr)
		cr.restore()

		cr.save()
		cr.translate(12,22)
		p_layout.set_markup('<b>' +"  Date" +'</b>')
		cr.show_layout(p_layout)			
		cr.translate(175,0)
		p_layout.set_markup('<b>' +"Condition" +'</b>')
		cr.show_layout(p_layout)         ##draw header text
		cr.translate(95, 0)
		p_layout.set_markup('<b>' +'High/Low' +'</b>')
		cr.show_layout(p_layout)
		cr.translate(100, 0)
		p_layout.set_markup('<b>' + "precipitation" +'</b>')
		cr.show_layout(p_layout)
		cr.restore()

		cr.save()
		cr.scale(2 * self.scale, 10 * self.scale)
		cr.translate(88,3.2)
		self.theme["divider.svg"].render_cairo(cr)			
		cr.translate(42,0)
		self.theme["divider.svg"].render_cairo(cr)
		cr.translate(50, 0)
		self.theme["divider.svg"].render_cairo(cr)
		cr.restore()		

		p_layout = cr.create_layout()
		p_fdesc = pango.FontDescription()
		p_fdesc.set_family_static("Free Sans")
		p_fdesc.set_size(8 * pango.SCALE)
		p_layout.set_font_description(p_fdesc)
		p_layout.set_width((self.width) * pango.SCALE) #### create our font info
		cr.save()
		cr.set_operator(cairo.OPERATOR_OVER)
		cr.scale(1 * self.scale, .9 * self.scale)
		
		cr.translate(20, 0)

		for x in range(10):
			cr.translate(0, 51)
			p_layout.set_markup('<b>' +self.latest[x+1]["day"] + " " + self.latest[x+1]["date"] +'</b>')
			cr.show_layout(p_layout)			
			cr.save()
			cr.translate(180,-15)

			cr.save()
			cr.scale(.9 * self.scale, .9 * self.scale)
			icon = str("sun"+ self.get_icon(int(self.latest[x+1]["dayicon"])) + ".svg")
			self.theme[icon].render_cairo(cr)
			cr.restore()

			cr.translate(95, 10)
			p_layout.set_markup('<b>' +self.latest[x+1]["high"] + " / " + self.latest[x+1]["low"] +'</b>')
			cr.show_layout(p_layout)
			cr.translate(115, 0)
			p_layout.set_markup('<b>' + self.latest[x+1]["dayppcp"] + "%"+'</b>')
			cr.show_layout(p_layout)
			cr.restore()

		cr.restore()
		cr.save()
		cr.translate(int((widget.get_size()[0] / 2) - (50 * self.scale)), int(widget.get_size()[1] - (90 * self.scale)))
		self.theme["button.svg"].render_cairo(cr)
		cr.translate(30, 15)
		p_layout = cr.create_layout()
		p_fdesc = pango.FontDescription()
		p_fdesc.set_family_static("Free Sans")
		p_fdesc.set_size(13 * pango.SCALE)
		p_layout.set_font_description(p_fdesc)
		p_layout.set_width((self.width) * pango.SCALE)
		cr.set_source_rgba(1, 1, 1, .8)
		p_layout.set_markup('<b>' + "Done"+'</b>')
		cr.show_layout(p_layout)
		cr.restore()


# This is called when we need to draw the windows contents
	def expose_10_day(self, widget, event):
		self.redraw_10_day(widget)
		return False

	def screen_changed_10_day(self,widget, old_screen=None):
    
		global supports_alpha
    
    # To check if the display supports alpha channels, get the colormap
		screen = widget.get_screen()
		colormap = screen.get_rgba_colormap()
		if colormap == None:
			print 'Your screen does not support alpha channels!'
			colormap = screen.get_rgb_colormap()
			supports_alpha = False
		else:
			print 'Your screen supports alpha channels!'
			supports_alpha = True
    
		# Now we have a colormap appropriate for the screen, use it
		widget.set_colormap(colormap)
    
		return False

	def move_10_day(self, widget, event):
		print event.x, event.y
		self.lastx = event.x
		self.lasty = event.y
			
			
	def show_10_day(self):
		win = gtk.Window(gtk.WINDOW_TOPLEVEL)
		win.set_keep_above(True)

		win.set_decorated(False)

		win.set_default_size(int(500 * self.scale), int(600 * self.scale))
		win.connect('motion-notify-event', self.move_10_day)
		win.set_events(gdk.POINTER_MOTION_MASK)    
  		win.connect('delete-event', gtk.main_quit)
  		win.set_app_paintable(True)

     
 		win.connect('expose-event', self.expose_10_day)
 		win.connect('screen-changed', self.screen_changed_10_day)


  		# toggle title bar on click - we add the mask to tell 
  		# X we are interested in this event
  		win.add_events(gdk.BUTTON_PRESS_MASK)
 		win.connect('button-press-event', self.clicked_10_day)
    
  		  # initialize for the current display
  		self.screen_changed_10_day(win)


 		   # Run the program
  		win.show()
		win.realize()
		if self.is_widget:  		# make widget if screenlet is widget
			win.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_UTILITY)
			win.window.property_change("_COMPIZ_WIDGET", gtk.gdk.SELECTION_TYPE_WINDOW, 
				32, gtk.gdk.PROP_MODE_REPLACE, (True,))	
		return True


	def show_error(self):

		dialog = gtk.Dialog("Zip Code", self.window)
		dialog.resize(300, 100)
		dialog.add_buttons(gtk.STOCK_OK, gtk.RESPONSE_OK)

		label = gtk.Label("Could not reach weather.com.  Check your internet connection and location and try again.")
		dialog.vbox.add(label)
		check = gtk.CheckButton("Do not show this again")
		dialog.vbox.add(check)
		dialog.show_all()
		response = dialog.run()
		if response == gtk.RESPONSE_OK:
			if check.get_active() == True:
				self.show_error_message = 0			
			dialog.hide()


if __name__ == "__main__":
	import screenlets.session
	screenlets.session.create_session(WeatherScreenlet)

```

---

