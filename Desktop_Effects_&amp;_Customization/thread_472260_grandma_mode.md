---
title: "grandma mode"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by headward on 2007-06-12
I was trying to change my theme when the screen resolution all of a sudden just blew everything up. I've tried everything with the resolution through system>preferences>themes and even went back to the default Human. This did nothing but change the theme. When I go into the system>preferences>screen resolution im on the highest mode. Can I change this in a terminal so i get out of grandma mode?

---

### Post by rolf-c on 2007-06-12
So your resolution is set at the high setting you want, but your only realizing something monstrous like 640x480?  First thing I recommend is a quick restart of X via CTRL-ALT-BACKSPACE.

if that doesn't work, post some specifics of what you are experiencing - what is the "highest mode" and what are you actually experiencing resolution-wise?

---

### Post by headward on 2007-06-12
The system claims that I have 1024x768 but I actually have at least 800x600 or maybe 832x624. This first happened when I clicked on the high contrast large print inverse. I've tried restarting the whole system and when I switch users the resolution is normal in their respective accounts. How can I fix this problem?

---

### Post by rolf-c on 2007-06-12
edit - see next post.

---

### Post by rolf-c on 2007-06-12
I gotta run but this will get you back to the default - from the command line do this:

```
cd ~/.themes
ls
rm -rf <file_name>
```

Now restart X and hopefully you are back at the default theme.

---

### Post by Hendrixski on 2007-06-12
hhmmm... in the old days we used to have to edit /etc/X11/xorg.conf but I think that the screen resolution application does that for you. 

you don't ever need to REBOOT linux (except for kernel updates of course... which is rare and you can say no to them)  in the WORST case you'll have to restart a service (like your network or your graphical server called Xserver).

---

### Post by Hendrixski on 2007-06-12
by the way... I see you're new here so...

WELCOME TO THE COMMUNITY!
You've come to the right place to ask for stuff. At UbuntuForums you can ask questions or just talk.  We're all here because we love ubuntu, and we want to share our joy with others. Soon you will be too.

If you would prefer to ask questions via a chatroom full of community members who can help you then you can check out the channel #ubuntu on IRC.  Installing IRC is easy and fun.  Just go to applications-->Add/Remove and pick XChat from the list, click OK and it installs.

If you'd like to meet other Ubuntu users in your area check out the Ubuntu LoCo teams for your city or state. 

There is plenty of GREAT documentation written about Ubuntu, just ask google and you'll find it.  A lot of it is written by the same people who answer questions on the forums so you'll get the information faster.  if dry manuals aren't your thing then relax and watch some videos.  [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) is a great website to get started, how to install, how to customize, how to set up your mail. etc.  Also check out [www.ubuntuvideo.com](www.ubuntuvideo.com) and [www.ubuntuclips.org](www.ubuntuclips.org).

I hope I'll see you around some more.  :-)

---

### Post by headward on 2007-06-12
Okay so I went into xorg.conf and this is what the screen resolution area look 
SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "720x400"       "640x480"

        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1024x768"      "800x600"       "720x400"       "640x480"
        EndSubSection
What do I have to do to this to make it change?

---

### Post by whistle on 2007-06-12
I had that problem in my xorg.conf (I wanted 12801024 but it only showed up as 1024x768) so I ran (backup xorg.conf)
```
dpkg-reconfigure xserver-xorg
```

edit:

I just saw your other post and I couldn't tell if you *wanted* 1024x768 or not, but this is my display section...
[QUOTE=xorg.conf]Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia GeForce FX 5500"
	Monitor		"Samsung SyncMaster 172N"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection
[/QUOTE]

Well I lied, I only have a screen section w/ a display subsection.

And I actually have no idea if this will work for you or not cause I just installed Ubuntu this week, lol...

---

### Post by headward on 2007-06-13
I do actually want 1024x768 and I cant figure out how make it change. resolutions. I've edited the file and restarted X. I ran that command: dpkg-reconfigure xserver-xorg and it changed but I dont know how to set that as my default. Do I have to delete the other xorg.conf file?

---

### Post by whistle on 2007-06-13
That one should be your new xorg.conf, I think... have you installed your video card drivers?

---

### Post by headward on 2007-06-14
No, I have installed no new hardware on this machine.

---

