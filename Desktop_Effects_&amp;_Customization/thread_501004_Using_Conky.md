---
title: "Using Conky"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by lsutiger on 2007-07-14
I am running conky and it is staying on top of any application I run. I have the background set to yes. I am attaching my .conkyrc file.
The question is how to change this?

---

### Post by yabbadabbadont on 2007-07-14
Looks like you forgot to attach your .conkyrc file...  :)

---

### Post by lsutiger on 2007-07-14
Odd there are 2 posts..one with the file, one wihout...
[http://ubuntuforums.org/showthread.php?t=501008](http://ubuntuforums.org/showthread.php?t=501008)
I will upload here
and an update: It only happens like this on startup of X. If I kill it then run it again it works fine.

---

### Post by lsutiger on 2007-07-14
I copied a small script from a post for someone having a different problem, but it was a startup problem, so I gave it a try and it worked. So here it is for anyone have a similar problem with conky.

Create the script```
gedit .conkylaunch
```
then pasted these commands```
#!/bin/sh
sleep 10 &&
conky &
exit
```
then added it to sessions (System-->Preferences-->Sessions
```
sh /home/YOUR USER NAME/.conkylaunch
```

I am still having 'flickering' problems. I setup the double buffer in the config file andedited the x.org file as instructed by many here, but it still has a flicker from time to time.
Any suggestions?

---

### Post by crimesaucer on 2007-07-14
I didn't read your .conkyrc, but I'll post a piece of my new one...for transparent window. It also had the double buffer setting for the flicker.

```

# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_transparent yes
#own_window_type normal
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
# I think the "use spacer" option only works with mono fonts.
use_spacer yes
use_xft yes

```


Now, I used to use:

```
own_window yes
```

...but it always had an issue starting with my Beryl and Compiz during boot up...right as my computer would show my desktop, it would "black out" the desktop wallpaper, and only draw the conky box.


...so, changing the "own_window" to "no" made it start perfectly, the only problem is that icons won't show on your desktop...but I don't use desktop icons so it doesn't matter.


You also have to turn Conky off to use Google Earth, because it needs it's own window or else it will flash every 3 second interval. Same thing with the program called Stellarium.

---

### Post by walkerk on 2007-07-14
i give compiz-fusion 10 seconds and conky an additional 50 seconds.. works well

```

!#/bin/bash
sleep 10
compiz --replace -c emerald
sleep 50
conky

```

works well..
be sure to make the above script executable and call for it in System > Preferences > Sessions

---

### Post by lsutiger on 2007-07-14
Well, I have mine setup just like that, and still get a flicker from time to time. Also, it is reporting my cpu speed incorrectly sometimes. I have a 1,6Ghtz and sometimes it reports 800, sometimes 1600???

---

### Post by lsutiger on 2007-07-14
I figured out the flicker. I had this Fortune program that would spit out some type of fortune cookie stuff every 120 seconds and it caused the flicker, so I got rid og it...still focusing on the cpu reporting wrong. From what I have observed, it reports @ 1/2 (800Mhtz) when less than 10% is utilized. I tested this by running some beryl stuff and watching the monitor. When utilized more, it reports correctly. Is this some type of throttling down by AMD processors? I know you can throttle down on some laptops when using just the battery. But to do it on the fly? Thats new to me!
Any ideas?

---

### Post by crimesaucer on 2007-07-15
> **lsutiger said:**
> I figured out the flicker. I had this Fortune program that would spit out some type of fortune cookie stuff every 120 seconds and it caused the flicker, so I got rid og it...still focusing on the cpu reporting wrong. From what I have observed, it reports @ 1/2 (800Mhtz) when less than 10% is utilized. I tested this by running some beryl stuff and watching the monitor. When utilized more, it reports correctly. Is this some type of throttling down by AMD processors? I know you can throttle down on some laptops when using just the battery. But to do it on the fly? Thats new to me!
Any ideas?


If you are measuring the cpu clock cycles in GHz then use this:

```
${freq_dyn_g}GHz
```



....also read this page for settings: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)



....and read this page for how to draw it to your desktop: [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)



this is the main page: [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by crimesaucer on 2007-07-15
Now I now why you're confused...I looked at your .conkyrc script and it's written in a very confusing way.


There are many more variables that are possible: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)


And many more settings: [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)


You might want to study a few .conkyrc's of other people's to see how it can be written in an easier way.


Check out this page: [http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)


and also look at Conky thread in this forum:  [http://ubuntuforums.org/showthread.php?t=281865&highlight=Conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=Conky)



....anyway, I fixed the cpu area for you, try this now (I also added a cpu clocked reading):


```

TEXT
${color white}[${color #00ff00}complexity${color white}] ${color #CCCCCC}@ ${color white}[${color red}$nodename${color white}]:
${color #888888}$sysname $kernel ${color #CCCCCC}on ${color #888888}$machine
${color #888888}Uptime: $uptime
${color #888888}${time %a,}${time %e %B %G}                   ${color #00ff00}${time %H:%M:%S}
${color white}${hr 2}

${color #ffccaa}System:
${color #888888}cpu: ${color #CCCCCC}${freq_g} GHz 
${color #888888}clocked: ${color #CCCCCC}${freq_dyn_g} GHz
${color #888888}load: ${color #CCCCCC}${cpu}%
${color #888888}${cpugraph 25 ff0000 ff00ff}
${color #888888}ram: ${color #CCCCCC}$mem${color #888888}/${color #CCCCCC}$memmax ${color #888888}, ${color #CCCCCC}$memperc%
${color #888888}swap: ${color #CCCCCC}$swap${color #888888}/${color #CCCCCC}$swapmax ${color #888888}, ${color #CCCCCC}$swapperc%
${color #888888}avg load: (${color #CCCCCC}$loadavg${color #888888})
${color #888888}processes: ${color #CCCCCC}$processes	${color #888888}running: ${color #CCCCCC}$running_processes
${color white}${hr 1}


${color #ffccaa}Wireless Networking:
${color #888888}ip address: ${color #CCCCCC}${addr eth1}
${color #888888}status: ${color #CCCCCC}${linkstatus eth1} %  
${color #888888}total download: ${color #CCCCCC}${totaldown eth1}	 
${color #888888}download speed: ${color #CCCCCC}${downspeed eth1} k/s	
${color #888888}${downspeedgraph eth1 25,100 ff0000 0000ff}
${color #888888}total upload: ${color #CCCCCC}${totalup eth1}
${color #888888}upload speed: ${color #CCCCCC}${upspeed eth1} k/s
${color #888888}${upspeedgraph eth1 25,100 0000ff ff0000}     		   	      
${color white}${hr 1}

${color #ffccaa}File Systems:
${color #888888}root: ${color #CCCCCC}${fs_used /}${color #888888}/${color #CCCCCC}${fs_size /} ${color #888888}(${color #CCCCCC}${fs_free /}, ${fs_free_perc /}% ${color #888888}free)
       ${fs_bar /}



```


...if you read the pages I linked you to, you will see that the variables given on your .conkyrc did not include the settings you needed for cpu in GHz.

---

### Post by lsutiger on 2007-07-15
Thanx for your reply and your work :D
But that didn't change the CPU being reported at half of it's speed sometimes. It reports correctly when I am actually 'using' the computer, but when idle it reports at 1/2 it's speed.
Thanx for the links, I will read up :)

---

### Post by yabbadabbadont on 2007-07-15
> **lsutiger said:**
> Thanx for your reply and your work :D
But that didn't change the CPU being reported at half of it's speed sometimes. It reports correctly when I am actually 'using' the computer, but when idle it reports at 1/2 it's speed.
Thanx for the links, I will read up :)

It sounds like you have cpu frequency scaling enabled.  That is what it is supposed to do in order to reduce power consumption.

---

### Post by lsutiger on 2007-07-15
Thanx...learn something new everyday!
Now it is a dual core. Is there a way to differentiate the load on each core?

Nevermind, reading about it now...

---

### Post by walkerk on 2007-07-19
> **crimesaucer said:**
> Now I now why you're confused...I looked at your .conkyrc script and it's written in a very confusing way.


There are many more variables that are possible: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)


And many more settings: [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)


You might want to study a few .conkyrc's of other people's to see how it can be written in an easier way.


Check out this page: [http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)


and also look at Conky thread in this forum:  [http://ubuntuforums.org/showthread.php?t=281865&highlight=Conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=Conky)



....anyway, I fixed the cpu area for you, try this now (I also added a cpu clocked reading):


```

TEXT
${color white}[${color #00ff00}complexity${color white}] ${color #CCCCCC}@ ${color white}[${color red}$nodename${color white}]:
${color #888888}$sysname $kernel ${color #CCCCCC}on ${color #888888}$machine
${color #888888}Uptime: $uptime
${color #888888}${time %a,}${time %e %B %G}                   ${color #00ff00}${time %H:%M:%S}
${color white}${hr 2}

${color #ffccaa}System:
${color #888888}cpu: ${color #CCCCCC}${freq_g} GHz 
${color #888888}clocked: ${color #CCCCCC}${freq_dyn_g} GHz
${color #888888}load: ${color #CCCCCC}${cpu}%
${color #888888}${cpugraph 25 ff0000 ff00ff}
${color #888888}ram: ${color #CCCCCC}$mem${color #888888}/${color #CCCCCC}$memmax ${color #888888}, ${color #CCCCCC}$memperc%
${color #888888}swap: ${color #CCCCCC}$swap${color #888888}/${color #CCCCCC}$swapmax ${color #888888}, ${color #CCCCCC}$swapperc%
${color #888888}avg load: (${color #CCCCCC}$loadavg${color #888888})
${color #888888}processes: ${color #CCCCCC}$processes	${color #888888}running: ${color #CCCCCC}$running_processes
${color white}${hr 1}


${color #ffccaa}Wireless Networking:
${color #888888}ip address: ${color #CCCCCC}${addr eth1}
${color #888888}status: ${color #CCCCCC}${linkstatus eth1} %  
${color #888888}total download: ${color #CCCCCC}${totaldown eth1}	 
${color #888888}download speed: ${color #CCCCCC}${downspeed eth1} k/s	
${color #888888}${downspeedgraph eth1 25,100 ff0000 0000ff}
${color #888888}total upload: ${color #CCCCCC}${totalup eth1}
${color #888888}upload speed: ${color #CCCCCC}${upspeed eth1} k/s
${color #888888}${upspeedgraph eth1 25,100 0000ff ff0000}     		   	      
${color white}${hr 1}

${color #ffccaa}File Systems:
${color #888888}root: ${color #CCCCCC}${fs_used /}${color #888888}/${color #CCCCCC}${fs_size /} ${color #888888}(${color #CCCCCC}${fs_free /}, ${fs_free_perc /}% ${color #888888}free)
       ${fs_bar /}



```


...if you read the pages I linked you to, you will see that the variables given on your .conkyrc did not include the settings you needed for cpu in GHz.

if its flickering add the bold biit to you xorg.conf:
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	**Load	"dbe"**
EndSection
```

---

