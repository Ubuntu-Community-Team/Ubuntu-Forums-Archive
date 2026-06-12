---
title: "simple lightweight timer - perfect for LXDE"
date: 2012-02-17
forum: Desktop Environments
---

### Post by Subito Piano on 2012-02-17
This is mostly taken from [this post]("http://urukrama.wordpress.com/2010/06/16/a-simple-timer/#comment-8415") by urukrama:

       This is a little script using zenity that functions as a timer . When I run the script I am asked to enter a task description and then in how many minutes I want to be reminded of that (“10&#8243; is ten seconds, “10m” is ten minutes). When the time is up, a simple dialog appears that reminds me to do the task I set myself.[INDENT]#!/bin/bash
#
REMINDER=`zenity --entry --title="Timer" \
 --text="What should I do?"`
WAIT=`zenity --entry --title="Timer" \
 --text="When should I do this?"`
sleep $WAIT
zenity --info --title="Timer" --text="$REMINDER"
[/INDENT]To add an alarm sound to the timer, use this script:[INDENT]#!/bin/bash
#
REMINDER=`zenity –entry –title=”Timer” \
–text=”What should I do?”`
WAIT=`zenity –entry –title=”Timer” \
–text=”When should I do this?”`
sleep $WAIT
play [path to sound file] &
zenity –info –title=”Timer” –text=”$REMINDER”
[/INDENT]for the "path to sound file" - for example, that line could read[INDENT] play /home/Mike/sounds/sound.wav &
[/INDENT]- or stick your favorite noise in /usr/share, etc.  

He preferred a commandline timer but i prefer a button on my taskbar.  So I opened up an editor, pasted the script in it, saved it as "Timer," put it in /usr/bin (some would prefer it in their home folder), made it executable, fetched an icon for it, added it to my menu, then added a shortcut to the Application Launch Bar in my LXPanel.

Thank-you to urukrama!  :-)

---

