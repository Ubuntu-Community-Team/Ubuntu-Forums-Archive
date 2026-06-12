---
title: "Clock - Always on Top, Even Over OpenOffice Impress Slide Show?"
date: 2006-02-23
forum: Desktop Environments
---

### Post by rf131 on 2006-02-23
Hi There,

I'm wanting to display a clock (probably digital) on my display, even when I'm using **OpenOffice Impress** to present a slide show.  I have also posted there to see if I can get any feedback on a Java applet but haven't heard back (I saw some threads about the applet embedded in the slide not working like it should).

I'm using this for a public-information display system at a community center, and having a clock displaying the time is very important.

**Does anyone have an idea how I can get a simple clock working to display over everything else including a running OpenOffice Impress slide show? ** There are tons of clock programs out there, but I'm desperately seeking someone who has already done this instead of me searching and trying.  :-k 

Perhaps this is a straightforward setting in Gnome for the application?  If so, please tell me where to go.

Lastly, I want to let everybody reading this know that I consider Ubuntu the best distro I have worked with so far.  I have messed with a number of the recent distros over the last couple of years.  It loaded flawlessly on an old Gateway 400 MHz PII pc with 500 MB of RAM and a slow hard drive.  Performance even on this system is acceptable!

TIA,
Kevin

---

### Post by dude of wonders on 2006-02-23
you can try the gdesklets app. if you have'nt tried it yet i think i remember seeing an ability where you could make the desklet things always stay on top, but don't know if it would stay on top of the slideshow, but webpages and other things it should. hope this helps. you can get gdesklets from automatix. maybe someone else will help ya with more info. if this doesnt help.:-D

---

### Post by rf131 on 2006-02-23
Tried the gdesklets.  One clock stays on top until the show is started, no joy.

Thanks for your tips... anyone else got this working?  This might need to be some sort of brute force app; I really wish the Java clock applet would work; that would be much better.

Kevin

---

### Post by varunus on 2006-02-23
Have you tried macslow's cairo clock?  It can be found at gnome-look.org, and has an "on top" option.  I don't know if it will run on top of a slideshow though.  GNOME has an "on top" feature by right clicking on the window titlebar, but once again, a slide show might override that.

---

### Post by Madpilot on 2006-02-23
One (slightly odd) option you might want to explore is the "widgets" in the current (beta release) of Opera 9.

There's at least a couple of kinds of clock, and they seem pretty stubborn about staying on top all the time... although Opera 9 is still in beta, it seems very stable, and if all it's doing is running a clock, it should be OK.

It is an odd suggestion, I know... but the "browser widgets" are a bit odd too!

---

### Post by snifi on 2008-03-21
This old thread popped up when searching Google for stay-top-window-while-slide-showing.  This is how I managed to solve this in Kubuntu:

**1)** Get any clock that stays on top. (If you don't have one, you can use the code below.)
**2)** Delay the clock appearing for time it takes you to start your slide-show.
**3)** Start the slide-show, and the clock will pop over it after the time sleeped. 

That is: 

on command promt, write: **sleep 10; ./clock.py**
# now quickly start your slide-show

Here comes the source code for clock.py. This uses the Cairo-clock. This one is analog.

```

#!/usr/bin/env python

# This code is from
# http://www.ralph-glass.homepage.t-online.de/clock/readme.html
# Window keep top routines added on lines 158-170

import pygtk
pygtk.require('2.0')

import gobject
import pango
import gtk
import math
import time
from gtk import gdk
try:
    import cairo
except ImportError:
    pass

if gtk.pygtk_version < (2,3,93):
    print "PyGtk 2.3.93 or later required"
    raise SystemExit

TEXT = 'cairo'
BORDER_WIDTH = 10

def progress_timeout(object):
    x, y, w, h = object.allocation
    object.window.invalidate_rect((0,0,w,h),False)
    return True

class PyGtkWidget(gtk.Widget):
    __gsignals__ = { 'realize': 'override',
                     'expose-event' : 'override',
                     'size-allocate': 'override',
                     'size-request': 'override',}

    def __init__(self):
        gtk.Widget.__init__(self)
        self.draw_gc = None
        self.layout = self.create_pango_layout(TEXT)
        self.layout.set_font_description(pango.FontDescription("sans serif 8"))
        self.timer = gobject.timeout_add (1000, progress_timeout, self)
                                           
    def do_realize(self):
        self.set_flags(self.flags() | gtk.REALIZED)
        self.window = gdk.Window(self.get_parent_window(),
                                 width=self.allocation.width,
                                 height=self.allocation.height,
                                 window_type=gdk.WINDOW_CHILD,
                                 wclass=gdk.INPUT_OUTPUT,
                                 event_mask=self.get_events() | gdk.EXPOSURE_MASK)
        if not hasattr(self.window, "cairo_create"):
            self.draw_gc = gdk.GC(self.window,
                                  line_width=5,
                                  line_style=gdk.SOLID,
                                  join_style=gdk.JOIN_ROUND)

	self.window.set_user_data(self)
        self.style.attach(self.window)
        self.style.set_background(self.window, gtk.STATE_NORMAL)
        self.window.move_resize(*self.allocation)

    def do_size_request(self, requisition):
	width, height = self.layout.get_size()
	requisition.width = (width // pango.SCALE + BORDER_WIDTH*4)* 1.45
	requisition.height = (3 * height // pango.SCALE + BORDER_WIDTH*4) * 1.2

    def do_size_allocate(self, allocation):
        self.allocation = allocation
        if self.flags() & gtk.REALIZED:
            self.window.move_resize(*allocation)

    def _expose_gdk(self, event):
        x, y, w, h = self.allocation
        self.layout = self.create_pango_layout('no cairo')
        fontw, fonth = self.layout.get_pixel_size()
        self.style.paint_layout(self.window, self.state, False,
                                event.area, self, "label",
                                (w - fontw) / 2, (h - fonth) / 2,
                                self.layout)

    def _expose_cairo(self, event, cr):
        
        # time 

        hours = time.localtime().tm_hour
        minutes = time.localtime().tm_min
        secs = time.localtime().tm_sec
        minute_arc = (2*math.pi / 60) * minutes
        if hours > 12:
            hours = hours - 12       
        hour_arc = (2*math.pi / 12) * hours + minute_arc / 12
       
        # clock background

        x, y, w, h = self.allocation
        cr.set_source_rgba(1, 0.2, 0.2, 0.6)
        cr.arc(w/2, h/2, min(w,h)/2 - 8 , 0, 2 * 3.14) 
        cr.fill()
        cr.stroke()

        # center arc

        cr.set_source_color(self.style.fg[self.state])
        cr.arc ( w/2, h/2, (min(w,h)/2 -20) / 5, 0, 2 * math.pi)
        cr.fill()
        cr.line_to(w/2,h/2)
        cr.stroke()

        # pointer hour

        cr.set_source_color(self.style.fg[self.state])
        cr.set_source_rgba(0.5, 0.5, 0.5, 0.5) 
        cr.set_line_width ((min(w,h)/2 -20)/6 )
        cr.move_to(w/2,h/2)
        cr.line_to(w/2 + (min(w,h)/2 -20) * 0.6 * math.cos(hour_arc - math.pi/2),
            h/2 + (min(w,h)/2 -20) * 0.6 * math.sin(hour_arc - math.pi/2))
        cr.stroke()

        # pointer minute

        cr.set_source_rgba(0.5, 0.5, 0.5, 0.5) 
        cr.set_line_width ((min(w,h)/2 -20)/6 * 0.8)
        cr.move_to(w/2,h/2)
        cr.line_to(w/2 + (min(w,h)/2 -20) * 0.8 * math.cos(minute_arc - math.pi/2), 
            h/2 + (min(w,h)/2 -20) * 0.8 * math.sin(minute_arc - math.pi/2))
        cr.stroke()
 
        # pango layout 
        
        fontw, fonth = self.layout.get_pixel_size()
        cr.move_to((w - fontw - 4), (h - fonth ))
        cr.update_layout(self.layout)
        cr.show_layout(self.layout)
        
    def do_expose_event(self, event):
        self.chain(event)
        try:
            cr = self.window.cairo_create()
        except AttributeError:
            return self._expose_gdk(event)
        return self._expose_cairo(event, cr)

win = gtk.Window()
win.set_title('clock')
win.connect('delete-event', gtk.main_quit)

event_box = gtk.EventBox()
event_box.connect("button_press_event", lambda w,e: win.set_decorated(not win.get_decorated()))

win.add(event_box)

w = PyGtkWidget()
event_box.add(w)

# added these lines to make clock-window stay top:
try:
  win.set_keep_above(True)
except:
  print "AttributeError: 'gtk.Window' object has no attribute 'set_keep_above'"
# end of add

# If you want to delay clock appearing, uncomment:

#delay = 10 # (in seconds)
#print "Delaying Clock appearance for %i seconds..." % delay
#time.sleep(delay)
#print "Ready to show Clock."

win.move(gtk.gdk.screen_width() - 120, 40)
win.show_all()

gtk.main()


```

---

