---
title: "fonts wont install?"
date: 2011-02-14
forum: Desktop Environments
---

### Post by Arminius on 2011-02-14
having real trouble installing weather fonts
I've attached 3 photos.
1st photo shows the fonts installing correctly, supposedly
2nd is the fonts folders, none of which contains the fonts I'm looking for.
3rd contains the conky on the middle bottom of the screen, that is ment to load the icons but is failing cause they seem to not be installing at all?

So any idea's?

---

### Post by VernonA on 2011-02-14
1) How did you install the font? Can you, for example, see it in OpenOffice or any other app which allows you to use the installed fonts? I see you installed it in the directory above the one where you put all your other Conky fonts, but I don't actually think that's the problem.
2) Could you show the Weather part of your Conky config file so we can see how you use them? I'm not aware that there is any standardised way of representing weather icons as letter glyphs, so it may be this font has the glyphs on the wrong letter for the ConkyWeather program.

---

### Post by Arminius on 2011-02-14
here's the weather part of the conky

```
${voffset 6}${font DroidSans:bold:size=8}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 0}${goto 59}${font Weather:size=38}${color2}y${font}${voffset -33}${offset 14}${font RadioSpace:size=32}${color3}${texeci 1800 conkyForecast -d HT -i}${font}
${voffset 0}${font Ubuntu:size=24}${color4}${alignc}${texeci 1800 conkyForecast -d CT}${font}
${voffset 10}${goto 20}${font ConkyWindNESW:size=41}${color3}${texeci 1800 conkyForecast -d BS}${font}${voffset -40}${goto 98}${font ConkyWeather:size=45}${texeci 1800 conkyForecast -d WF}${font}${voffset -39}${goto 188}${font MoonPhases:size=32}${texeci 1800 conkyForecast -d MF}${font}
${voffset 6}${goto 28}${font DroidSansFallback:bold:size=8.45}${color4}${execpi 1800 conkyForecast -d WS -i| sed -e 's/calm'/'\$\{offset 2}Calm/g' -e 's/mph'/'\$\{offset 2}mph/g'}${goto 88}Feels like ${texeci 1800 conkyForecast -d LT -ui}${execpi 1800 conkyForecast -d MP| sed -e 's/First.*'/'\$\{goto 182}First Qtr/g' -e 's/Last.*'/'\$\{goto 184}Last Qtr/g' -e 's/New.*'/'\$\{goto 195}New/g' -e 's/Full.*'/'\$\{goto 195}Full/g' -e 's/Waning.*'/'\$\{goto 187}Waning/g' -e 's/Waxing.*'/'\$\{goto 187}Waxing/g'}${font}
${voffset 8}${goto 36}${font DroidSans:bold:size=8.55}${color6}${texeci 1800 conkyForecast -d DW -s 1 -w}${goto 89}${texeci 1800 conkyForecast -d DW -s 2 -w}${goto 143}${texeci 1800 conkyForecast -d DW -s 3 -w}${goto 197}${texeci 1800 conkyForecast -d DW -s 4 -w}${font}
${voffset 4}${goto 25}${font ConkyWeather:size=8.55}${color2}${texeci 1800 conkyForecast -d WF -s 1 -e 4 -S 1}${font}
${voffset 0}${goto 25}${font DroidSans:bold:size=8.5}${color4}${texeci 1800 conkyForecast -d HT -s 1 -ui}${offset 2}/${offset 2}${texeci 1800 conkyForecast -d LT -s 1 -ui}${goto 79}${texeci 1800 conkyForecast -d HT -s 2 -ui}${offset 2}/${offset 2}${texeci 1800 conkyForecast -d LT -s 2 -ui}${goto 133}${texeci 1800 conkyForecast -d HT -s 3 -ui}${offset 2}/${offset 2}${texeci 1800 conkyForecast -d LT -s 3 -ui}${goto 187}${texeci 1800 conkyForecast -d HT -s 4 -ui}${offset 2}/${offset 2}${texeci 1800 conkyForecast -d LT -s 4 -ui}${font}
```

---

### Post by VernonA on 2011-02-14
Hmm, you didn't actually answer question 1, so I'm still not quite sure if you have the fonts installed or not. However, you certainly have Weather installed OK as I can see the thermometer symbol being displayed by the code:
```
    ${font Weather:size=38}${color2}y${font}
```
Unfortunately, you never use that font again. This still means you might not have installed RadioSpace, Ubuntu, ConkyWindNESW, ConkyWeather, MoonPhases, DroidSansFallback or DroidSans. I don't think I've ever seen so many different fonts used in such a short piece of code!
I'd suggest you comment out most of this code and reinstate it one line at a time. Do as much as you can using Weather, then, say, use ConkyWindNESW to add a weather vane. Once you get confident, add more as you need it.

---

### Post by ankspo71 on 2011-02-14
Hi,
I'm not an expert on conky, so I can't help much there, but depending on how you installed the fonts, they may have been installed in your home directory. This could explain how they installed but not appear in /usr/share/icons.

Look for a hidden folder in your home folder named ".fonts", then look for your font's inside there. /home/yourname/.fonts/*

Another thought is conky forecast might not be able to find the fonts if they are not in the location it looks for them. ex: /usr/share/icons/conkyforecast ?  It seems to make sense since I see you have a folder named conkyforecast in your system's icon folder. 

Hope this helps.

---

### Post by Arminius on 2011-02-15
ok, there's the pic of what's in the .fonts folder
so what's missing?
I've found most of the fonts listed that I need for the weather conky
but only the temperate gauge is showing up still

---

### Post by 42dorian on 2011-02-15
Arminius, did you reload your fonts?  Type this into a command prompt:

```

fc-cache -f -v

```

Even better, what you can do is add a shortcut to your .bashrc file called an Alias.  It has a special file you can use for it too.  Type this into a prompt:

```

sudo (your favourite text editor's name. Gedit/Mousepad/whatever.) .bash_aliases

```

This will open a file.  It may well be blank, and that's fine.  Add this line to it, save and exit.

```

alias fontreload='fc-cache -f -v'

```

The next time you reboot or start up, you will be able to type "fontreload" into a prompt after installing a font and it'll run that font cache reload for you with an easier to remember name.

Try, for now, just the reloading the cache part, and let us know.

---

### Post by Arminius on 2011-02-15
I'm afraid that code had no effect
still no new fonts showing up

---

### Post by Arminius on 2011-02-15
I tried this conky weather script ```
# conky configuration
# edited by Mark Buck (Kaivalagi) <m_buck@hotmail.com>

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=9

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 0
maximum_width 300

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 35

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer right

# colours
color1 white
# light blue
color2 6892C6
# orange
#E77320
color3 FC8820
# green
color4 78BF39
# red
color5 CC0000

text_buffer_size 2048

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}Weather${font}  ${hr}${color1}
${color3}Template Output:${color1}
${execpi 1800 conkyForecast --location=UKXX0103 --template=/usr/share/conkyforecast/example/conkyForecast.template}

${color3}Standard Output:${color1}
${font Bitstream Vera Sans Mono:size=14}${execi 1800 conkyForecast --location=UKXX0103 --datatype=CT}${font}
${font ConkyWeather:style=Bold:size=40}${execi 1800 conkyForecast --location=UKXX0103 --datatype=WF}   ${font ConkyWindNESW:size=40}${execi 1800 conkyForecast --location=UKXX0103 --datatype=BS}${font}
${execi 1800 conkyForecast --location=UKXX0103 --datatype=HT --centeredwidth=4}/${execi 1800 conkyForecast --location=UKXX0103 --datatype=LT --centeredwidth=4}  ${execi 1800 conkyForecast --location=UKXX0103 --datatype=WS --imperial} - ${execi 1800 conkyForecast --location=UKXX0103 --datatype=WD}

```

I ran that, and the code I got it from was at [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)
the part of the thread after I ran it said it should have lots of information, but as u can see in the screen shot it has nothing, not even any fonts?

so is it still suffering from whatever my other conky weather scripts were having trouble with?

---

### Post by stinkeye on 2011-02-15
All the required weather fonts are installed when you install conkyforecast.

Your problem is you haven't registered with the Weather.com XOAP Service.
See here: [**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=869328[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=869328")

Then you put this info in your **~/.conkyForecast.config** file.(If I remove this file I get the same output as you ...see pic)
eg here's mine
```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE =
XOAP_PARTNER_ID = [COLOR="#ff00ff"]xxxxxxxx[/COLOR]
XOAP_LICENCE_KEY = [COLOR="#ff00ff"]xxxxxxx[/COLOR]
MAXIMUM_DAYS_FORECAST = 4
AUTO_NIGHT = True
BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=5&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
#BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
PROXY_HOST = 
PROXY_PORT = 8080
PROXY_USERNAME = 
PROXY_PASSWORD = 
```
[COLOR="#ff00ff"]You need to register to get these codes.[/COLOR]


Also if your using someone else's conky code
eg```
${execi 1800 conkyForecast --location=[COLOR="Purple"]UKXX0103[/COLOR] --datatype=CT}
```
You need to replace the [COLOR="#800080"]location code[/COLOR] with your own.

---

### Post by Arminius on 2011-02-16
are these the codes u mean?
Your weather.com XML Partner ID & License Key:

Partner ID:
License Key:

I got them from the email when i signed up
I put them in the conky code where I think they were ment to go, also replaced the default locale code with my city's, still no change, still no fonts or any info

---

### Post by stinkeye on 2011-02-16
Do you have a **~/.conkyForecast.config** file?
If you do check that you haven't swiched around your codes
and they are entered in the same format as my previous post.
**Note the spaces either side of the = sign.

Run your conky in terminal with
```
conky -c /path/to/conkyrc
```
to check for errors.

---

### Post by VernonA on 2011-02-16
That last advice was spot on. If you run conky from a terminal you will soon see what the problem is.
A couple of points of clarification:
1) In the weather config file the LOCALE entry is NOT your location, it is your locale (which is what the os uses to decide what currency you deal in, and how you like your decimal points displayed). It should be set to something like en or fr or es. If you leave it blank the conky script will get the default locale from your os. This is the best way to do it.
2) The latest version of conky supports a DEFAULT_LOCATION = XXYYZZAA entry in the config file, so you no longer have to keep putting --location=XXYYZZAA in the conky file on every call to the weather script. This is a new addition so make sure you have the latest version if you want to use it.

---

### Post by Arminius on 2011-02-16
yes there has always been a conkyForecast.config

and here is the code inside it 

```
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE =
XOAP_PARTNER_ID = my partner ID from the email which u can't have
XOAP_LICENCE_KEY = my licence key from the email which u can't have
MAXIMUM_DAYS_FORECAST = 4
AUTO_NIGHT = True
BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=5&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
#BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
PROXY_HOST = 
PROXY_PORT = 8080
PROXY_USERNAME = 
PROXY_PASSWORD =

```

I ran it with ```
conky -c /usr/share/conkyforecast/example/conkyrc &
``` in terminal, and still not getting anything.

---

### Post by VernonA on 2011-02-16
I see what you're doing now, and its not right. The conky command ('conky') runs a conky configuration file (/usr/share/conkyforecast/example/conkyrc) which runs conky commands (like execi) which run conky scripts (like conkyForecast.py) which sometimes need their own config files (like /usr/share/conkyforecast/example/conkyForecast.config). You have confused the two config files when you read the conky installation instructions.
What you really need to do is copy the conkyForecast.config file to you home directory and edit it there to contain your ID and Key. The one in the example directory is just that and is not visible to the ConkyForecast program (it will also get overwritten every time conky is updated!). By the same token, your conky script should also be in your home directory, and you shouldn't be pointing at /usr/.. anything.
You are getting close, so don't give up!

---

### Post by stinkeye on 2011-02-16
Yeah, I think we're getting close.
When you copy the file /usr/share/conkyforecast/conkyForecast.config to your home folder
make sure to rename as **.conkyForecast.config** with the preceding dot.


[COLOR="Red"][SIZE="3"]Edit[/SIZE][/COLOR]: You can use this command to copy the file to your home directory.```
cp /usr/share/conkyforecast/conkyForecast.config ~/.conkyForecast.config
```

---

### Post by Arminius on 2011-02-17
thank u for all your help, u guys are great, I won't give up
I'll get to what u want me to do in a second, but for now, I've moved my conky files from /etc/conky to /home/Conky as per what I think u said I need to do.

my conky_start file used to have ```
#!/bin/bash
exec conky --config=/etc/conky/conky.conf &
exec conky --config=/etc/conky/conkyrc1 &
exec conky --config=/etc/conky/conkyrc2
fi

```

and this used to load all 3 conky files, but now it reads ```
#!/bin/bash
exec conky --config=/home/conky/conky.conf &
exec conky --config=/home/conky/conkyrc1 &
exec conky --config=/home/conky/conkyrc2
fi

```

and now only the first one conky.conf is loading as show in the photo I attached, so if u could help me figure this step back out then I would be grateful.

---

### Post by VernonA on 2011-02-17
There's a few things wrong with this startup script, but we'll sort that out later. You haven''t actually done what stinkeye requested and put your config files in your home directory (unless you happen to be called conky of course!). Your home dir is the place where you login to, like /home/arminius for example. When you are in a terminal, this location is given the shorthand name ~ cos you type it so often. You will see that the tilda is used in the command line stinkeye asked you to type. You need to have all your conky configuration files in your home directory. Most people give them names which start with a dot because this hides them from normal view (so you wont accidentally delete them for example). The weather config file MUST be called .conkyForecast.config - this is hard-coded in the Python weather program, and is the reason it isn't finding your file and so isn't giving you any weather info.

1) Put all your config file in your home directory. Give them names which start with a period so for example .conky_system and .conky_weather and .conky_misc.
2) Put the weather config file in your home directory too. Its name is not negotiable and must be .conkyForecast.config
3) Whilst in a terminal in your home directory, start a conky session by typing:
```
conky -d -c .conky_system
```
The -d means run the process in background, so you can do other things in the terminal. The -c says that the next thing on the command line is the name of one of your conky files.
4) Assuming (3) works, do it again for .conky_misc and .conky_weather, ie type:
```
conky -d -c .conky_misc
conky -d -c .conky_weather
```

You should see everything working. Assuming that it is, you need to put similar lines into your startup script. That can be another post!

---

### Post by Arminius on 2011-02-18
thank u guys, I'm over the finish line
as you can see in the attached photo it's all working in the top right, I'll make a few changes and I'm sure it will be ok from now on

---

### Post by VernonA on 2011-02-18
Delete the last two lines of your startup script. Then add a sleep at the beginning, as you need to allow other things to start before conky gets going. Your script should say:
```
#!/bin/bash
sleep 15
conky -d -c .conky.conf
conky -d -c .conkyrc1
conky -d -c .conkyrc2
```
Now you need to edit your three config files to taste - that part can take months!
Congratulations,
Vernon

---

