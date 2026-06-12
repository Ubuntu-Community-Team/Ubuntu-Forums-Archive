---
title: "Globualtion2 config files?"
date: 2007-11-15
forum: Gaming &amp; Leisure
---

### Post by richardc1 on 2007-11-15
I am new to ubuntu and love it. I installed Globulation2 and love it. Then I couldn't help myself, and started messing with the settings. I changed it to fullscreen, AND OpenGL. I restarted the game, it went to full screen, and crashed after like two seconds. Then my desktop was at oh, 640x480 resolution or lower. I couldn't reset it in the display settings, heck, it showed that it was still at 1024x768!

So restarted the computer. Everything returned to normal...until I tried to start the game again. Same thing. So my question is, is there a config file somehwere that I can edit to change those settings back? If not, how do I uninstall it so that when it is reinstalled, it won't do what it's doing now?
:confused:
I need some 'duh' time. I haven't palyed an RTS game in like 3 years. Please help!

---

### Post by KIAaze on 2007-11-15
The settings are stored in "**~/.glob2/preferences.txt**".
The graphic settings are stored as a number under "screenFlags".

I just tested it myself and I have:
-without openGL and without fullscreen: screenFlags=24
-without openGL and with fullscreen: screenFlags=18
-with openGL and with fullscreen: screenFlags=19

This should be enough to help you.

By the way, the online gaming system of Globulation 2 is great because it allows you to talk with all people present on the **irc.globulation2.org/#glob2** IRC channel.

So if you want to play online, when you log into the YOG server, don't hesitate to type the names of the users listed in it. Depending on how they have set up their IRC programs, it will notify them, so they'll be more likely to respond. ;)

And I also recommend you install **Xchat**, an IRC chat program and log onto this channel too.

I'm currently often on the channel, since I've set it to automatic login. Unfortunately, globulation 2 crashes for me in Ubuntu. :(
It works in Windows, but I rarely boot into it.

Note that almost all programs store their settings in hidden folders in the home directory.
Hidden folders are folders whose name begins with ".".
To list them do this:
```
ls -ld ~/.*/ 
```
("~" stands for /home/<username> and "*" is the "joker"; "-l" is for detailed listing and "-d" for directories)

P.S:
A few good strategy games on Ubuntu:
-Battle for Wesnoth (turn based)
-Warzone 2100
-And Starcraft and Warcraft are said to work very well with Wine/Dosbox! I just haven't tried that yet myself. ^^

---

### Post by donkyhotay on 2007-11-15
If you ever accidently configure bad settings within globulation2 you can reset it be deleting 
~/.glob2/preferences.txt
at which point next time you load the game up it will recreate the file with default settings again. You can also manually tweak that file too if you know exactly what setting is incorrect and how to repair it.

---

### Post by richardc1 on 2007-11-15
Thank you KIAaze! It worked like a charm. I guess it was the OpenGL that was crashing the game and messing my resolution and mouse up. I change teh 19 to 18 and baddabing!

Thank you donkyhotay also, I am a sucker for messing with settings. I will keep in mind that if I ever mess it up again, and can't figure it out, I'll delete the preferences file. 

I guess uninstall doesn't delete that file, because I tried to uninstall it and reinstall it, hopeing that the install defaults would be used but they weren't. That would explain the same behavior after reinstalling it.

Thanks!

---

