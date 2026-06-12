---
title: "Permission denied when running conky or deleting /home/ files!"
date: 2007-06-18
forum: Desktop Effects &amp; Customization
---

### Post by nightfire117 on 2007-06-18
Here's my Conky config, which I have a problem with. I'm using Ubuntu 7.04 and fluxbox on a Gateway 450SX4 (no dual-boot with Windows, woo hoo!) and 1024x768 display. Here's the config:

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
on_bottom yes

# Xft font when Xft is enabled
#xftfont dejavu sans:size=10
#xftfont handelgothic bt:size=10
xftfont dejavu sans:pixelsize=12
#xftfont Bitstream Vera Sans Mono:pixelsize=10
# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no
a
# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use pseudo transparency with own_window?
own_window_transparent no

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour black

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 1 1

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 1

# border width
border_width 1

# Default colors and also border colors
default_color c1c1c1
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 180
gap_y 0

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
use_spacer yes

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
TEXT
${color #000000}  - ${color} CPU: $cpu%${color #000000}  -  ${color}${freq_dyn}MHz${color #000000}  ${color}${acpitemp}C${color #000000}  -  ${color}$mem / $memmax${color #000000}  -  ${color}Down: ${downspeed ath0} KB/s${color #000000}  -  ${color}Up: ${upspeed ath0} KB/s${color #000000}  -  ${exec ~/.conky/weather.sh JAXX0055}
```

So, I ran the command "conky" in the terminal to start it up. Here's the output:

```
wenshan@kr-laptop:~$ conky
Conky: /home/wenshan/.conkyrc: 23: no such configuration: 'on_bottom'
Conky: /home/wenshan/.conkyrc: 35: no such configuration: 'a'
Conky: forked to background, pid is 31429
wenshan@kr-laptop:~$ 
sh: /home/wenshan/.conky/weather.sh: Permission denied
Conky: desktop window (4d) is root window
Conky: drawing to desktop window
Conky: failed to set up double buffer
Conky: drawing to single buffer
sh: /home/wenshan/.conky/weather.sh: Permission denied
sh: /home/wenshan/.conky/weather.sh: Permission denied
sh: /home/wenshan/.conky/weather.sh: Permission denied
sh: /home/wenshan/.conky/weather.sh: Permission denied
sh: /home/wenshan/.conky/weather.sh: Permission denied
sh: /home/wenshan/.conky/weather.sh: Permission denied
sh: /home/wenshan/.conky/weather.sh: Permission denied
```

- where I finally killed the process. For the record, not that it has any relevance (I guess...?), even "sudo conky" doesn't help that. >.< I've had to do everything like move and copy files in the terminal, which is fine and easy enough, but that doesn't fix the "permission denied" issue. (The terminal has a sort of, erm, novelty to it that I enjoy. Hehe. Even if, at times, I don't find it the most convenient method.)

In Gnome, I have none of these issues. In fact I just installed Ubuntu on this system last night  - so it's clean. Anyways, thanks in advance, any info you could provide would be great. XD

~Nightfire

---

### Post by nightfire117 on 2007-06-19
B-b-b-bump. *Shamelessly* (Hehehe.)

~Nightfire

---

### Post by digitalbenji on 2007-06-19
it looks like you are not logged in as root, which is good, because you should never run x windows sessions as root.  try removing the .conkyrc file and starting conky on its own, to see if conky will even run.  It sounds like maybe your .conkyrc has some syntax errors.

---

### Post by nightfire117 on 2007-06-19
Alright, trying that right now. (Actually got the same errors in Gnome.)

Mmkay, Conky starts up, but obviously enough it doesn't by default have the weather plugin. Erm, syntax errors you say? Is there a way around them, or something, or do I have to just forget the plugin altogether? (The reason is I want to use Fluxbox full-time rather than Gnome since the initial startup in Fluxbox reports that I only use about 90 MB of RAM with it, and I certainly like *that*.) The purpose being that I want my system resources monitored by Conky - and in Gnome you have the toolbar icons, but nothing like that in Fluxbox. (Plus Conky is more configurable though I know nothing about it, heh.) Thanks for the response. 

~Nightfire

---

### Post by shearn89 on 2007-06-19
Syntax errors: its saying it doesn't have an option called on_bottom, and there is a random "a" in the middle of your .conkyrc.

The on_bottom can be fixed by replacing it with:
```

own_window yes
own_window_transparent yes
own_window_type utility
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

Which i think would replace your own_window no.

I'm using fluxbox, and that works for me!


As to the weather thing, you could try doing:
```

chmod a+x weather.sh

```
in the weather.sh directory... I'm not certain "weather" (ha...) it would work or not, but its worth a try. Maybe back it up first?

---

### Post by nightfire117 on 2007-06-19
Heh, thanks. Got a bit farther with that one, I think, but I can't tell for sure since I haven't used Conky very long:

```
wenshan@kr-laptop:~/.conky$ conky
Conky: /home/wenshan/.conkyrc: 25: config file error
Conky: forked to background, pid is 10923
wenshan@kr-laptop:~/.conky$ 
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek
unable to parse -
Conky: desktop window (4d) is root window
Conky: drawing to desktop window
Conky: failed to set up double buffer
Conky: drawing to single buffer
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek
unable to parse -
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek
unable to parse -
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek
unable to parse -
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek
unable to parse -
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek
unable to parse -
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek
unable to parse -
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek
unable to parse -
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek
unable to parse -
Conky: received SIGINT or SIGTERM to terminate. bye!
```

I'm assuming it found an error in the script weather.xslt. I didn't write it myself, so I wouldn't know what's wrong with it.

**weather.sh:**
```
#!/bin/sh

#
# Grab weather data from weather.com and format it according to the given XSLT
# Script written by boojit
# Modified by Hellf[i]re
# The orignal script and xslt can be downloaded from http://pondol.com/weather.tar.gz

# Usage:
# ${execi 1800 /path/to/weather/weather.sh location}
# Usage Example:
# ${execi 1800 /home/user/weather/weather.sh 03833}

# your Location ID: use http://xoap.weather.com/search/search?where=[yourcity] to find it 
# U.S. users can just use their zip code; doubt that works for anyone else though (YMMV)
LOCID=$1

# s=standard units, m=metric units
UNITS=m

# where this script and the XSLT lives
RUNDIR=~/.conky

# there's probably other stuff besides CURL that will work for this, but i haven't 
# tried any others. 
# you can get curl at http://curl.haxx.se/
CURLCMD=/usr/bin/curl

# get it at http://xmlsoft.org/XSLT/
XSLTCMD=/usr/bin/xsltproc

# you probably don't need to modify anything below this point....

# CURL url. Use cc=* for current forecast or dayf=10 to get a multi-day forecast
CURLURL="http://xoap.weather.com/weather/local/$LOCID?cc=*&unit=$UNITS&dayf=2"

# The XSLT to use when translating the response from weather.com
# You can modify this xslt to your liking 
XSLT=$RUNDIR/weather.xslt 

#filter (if you want to convert stuff to lower-case or upper case or something)
#FILTER="|gawk '{print(tolower(\$0));}'"


#####
eval "$CURLCMD \"$CURLURL\" 2>/dev/null| $XSLTCMD $XSLT - $FILTER"
```

**weather.xslt:**
```
<!-- 

 This XSLT is used to translate an XML response from the weather.com
 XML API. 

 You can format this file to your liking. Two things you may feel 
 like doing:

	1) Modify the layout of the fields or static text already defined
	2) Add other fields from the XML response file that aren't referenced in this
	   XSLT. You can grab a full list by just doing a: 
           wget "http://xoap.weather.com/weather/local/$LOCID?cc=*&unit=$UNITS" 
           (change $LOCID and $UNITS to suit your needs)
-->

<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0" > 
	<xsl:output method="text" disable-output-escaping="yes"/>
	<xsl:template match="weather">
		<xsl:apply-templates select="cc"/>
		<xsl:apply-templates select="dayf/day[@d='1']"/>
	</xsl:template>
 
	
	<xsl:template match="cc">
		<xsl:text>Location: </xsl:text><xsl:value-of select="obst"/>  
<xsl:text>:
</xsl:text>
<xsl:text>  Temperature: </xsl:text><xsl:value-of select="tmp"/><xsl:value-of select="/weather/head/ut"/>
<xsl:if test="tmp != flik">
<xsl:text>
  Feels Like: </xsl:text><xsl:value-of select="flik"/><xsl:value-of select="/weather/head/ut"/>
</xsl:if>
<xsl:text>
  Conditions: </xsl:text><xsl:value-of select="t"/>
<xsl:text>
  Wind: </xsl:text>
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>0</xsl:text></xsl:when>
	<xsl:otherwise><xsl:value-of select="wind/s"/></xsl:otherwise>
</xsl:choose>
<xsl:value-of select="/weather/head/us"/> 
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>(0mph)</xsl:text></xsl:when>
	<xsl:otherwise><xsl:text> (</xsl:text><xsl:value-of select="round(wind/s * 0.6214)"/><xsl:text>mph)</xsl:text></xsl:otherwise>
</xsl:choose>
<xsl:text> (</xsl:text><xsl:value-of select="wind/t"/>
<xsl:text>)</xsl:text>
	</xsl:template>

	<xsl:template match="dayf/day[@d='1']">
<xsl:text>
  Tomorrow: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text>, </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/>
<xsl:text>
</xsl:text>
	</xsl:template>
</xsl:stylesheet>
```

Anyways, thank you for your fix. It corrected the permission denied error but now apparently there is an error with the XSLT file. The chmod and the own_window fixed it, and thanks for pointing out that random "a."

~Nightfire

**[EDIT]:** Hehe, somehow I noticed there are some dependencies I failed to install, libxml and libxslt. I'm compiling libxml right now and then will sudo make install, then compile and make install for libxslt and try it again, I'll let you know how that goes. Argh, takes a while. Haha, incidentally I found a GTK theme changer, I wonder if it'll change some stuff in Fluxbox - hopefully. Doesn't matter since it installed some dependencies I needed for something else anyway. Hehe. *Yawn* Still waiting for the make, not the sudo make install yet.

~Nightfire

---

### Post by shearn89 on 2007-06-19
glad it worked!

not sure about this, as i don't know the script, but you're running
```

${exec ~/.conky/weather.sh JAXX0055

```
in your .conkyrc file - the weather script says it needs a number before the path:
```

# Usage Example:
# ${execi 1800 /home/user/weather/weather.sh 03833}

```

Don't know if that helps? I'll check back in a mo to find out how the lib compiling helped...

---

### Post by nightfire117 on 2007-06-20
Umm, I cancelled the compile once I realized I had the latest versions (apparently) anyways....

As for that ```
# Usage Example:
# ${execi 1800 /home/user/weather/weather.sh 03833}
``` I'll try it out right now though I think it was that way before. o.o

~Nightfire

**[EDIT]:** Thanks for all your help! After browsing the forums someone else got a "parse error" on the XSLT and I figured, "well, I may as well try what fixed theirs," so I installed curl from the repo and it works now.  ([http://ubuntuforums.org/showthread.php?t=319516]("http://ubuntuforums.org/showthread.php?t=319516")) No more "no < tag found at beginning" or whatever it says. Only thing now is that it flickers constantly and has the "double buffer" error, but I could find the solution to that easily enough. Again thanks for your help, with a bit of tweaking it'll be  nicer. XD

~Nightfire

---

### Post by shearn89 on 2007-06-20
theres an extra module you can download to stop it flickering... Search for the howto called "howto get a beautiful conky set up".

Glad i could help!

---

### Post by nightfire117 on 2007-06-20
Thanks again, I've tried that fix on that thread (which seems good for conky questions should I have them) and have yet to see if it will work. XD

~Nightfire

---

