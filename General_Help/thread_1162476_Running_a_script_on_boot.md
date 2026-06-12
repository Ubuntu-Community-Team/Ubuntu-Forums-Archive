---
title: "Running a script on boot"
date: 2009-05-17
forum: General Help
---

### Post by afonteijn on 2009-05-17
I'm having trouble with scrolling in combination with the nvidia video driver. I have found a work around, I need to run 
 nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1 & . In the terminal this works great. Now I want it to work on startup. I have tried the following things.

I have created the following script:
#!/bin/bash
sleep 10 
nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1 &

I have added it to system -> preferences -> Startup Applications
Didn't work. 
I have copied it to /etc/init.d
Didn't work
I have tried to add the following lines to the xorg.conf:

Section "Screen"
	Option         "InitialPixmapPlacement" "2"
    	Option         "GlyphCache" "1"
Didn't work

What am I doing wrong? Any help is appreciated
PS. I have chmoded the script 755 -> I can run it.
PPS. sleep command in script, I added it to be sure that compiz is loaded before this command is executed.

---

### Post by soro2005 on 2009-05-17
try
```
/usr/bin/nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1 &
```
You might be able to execute it in the Startup programs and without a script. Like this:
```
bash -c "sleep 10; /usr/bin/nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1"
```
Give it a little more timeout perhaps.

---

