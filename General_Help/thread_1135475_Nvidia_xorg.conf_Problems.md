---
title: "Nvidia xorg.conf Problems"
date: 2009-04-24
forum: General Help
---

### Post by Coderunner87 on 2009-04-24
First of all I had problems with low resolution, so I added Modes "1280x1024" to xorg.conf
I restart and I get a message saying it is running in low graphics mode. When it starts up though I have my desired resolution only now there is no 3D acceleration.

When I go to hardware it says my nvidia driver is in use, but when I go Nvidia X Server it says I am not using nvidia driver

when I run nvidia-xconfig its says

PARSE ERROR: Parse error on line 30 of section Screen in file
             /etc/X11/xorg.conf.
             "Modes" is not a valid keyword in this section.

---

### Post by andrewc6l on 2009-04-24
I'm not sure why your NVidia driver isn't working, but you will need to fix the parse error in /etc/X11/xorg.conf.

Maybe this link will help?
[http://ubuntuforums.org/archive/index.php/t-1086324.html](http://ubuntuforums.org/archive/index.php/t-1086324.html)

---

### Post by dcstar on 2009-04-24
> **Coderunner87 said:**
> First of all I had problems with low resolution, so I added Modes "1280x1024" to xorg.conf
I restart and I get a message saying it is running in low graphics mode. When it starts up though I have my desired resolution only now there is no 3D acceleration.

When I go to hardware it says my nvidia driver is in use, but when I go Nvidia X Server it says I am not using nvidia driver

when I run nvidia-xconfig its says

PARSE ERROR: Parse error on line 30 of section Screen in file
             /etc/X11/xorg.conf.
             "Modes" is not a valid keyword in this section.

Do not manually add lines to xorg.conf if you do not know exactly how you should do it, remove the line you put in and then use the Nvidia XServer Settings tool.

---

### Post by Coderunner87 on 2009-04-25
the lines i added was how i read to add the resolution, i have read a couple of different ways to add the resolution to the xorg.conf but none of them work. I can get it to load the nvidia driver without editing it but the highest resolution it offers me is 640x480 
 
what do i do this is becoming a nightmare

---

### Post by retiredtechie on 2009-04-26
I'm sure this has been covered elsewhere but, as the same thing happened to me I thought I would mention what worked here. Since Ubuntu could not "see" my monitor (Viewsonic) because I was using the digital (DVI) input, I could only get 640x480. Moving the cable to the monitor vga input, using an adapter fixed it. Of course the display isn't as sharp but I get all the required display options now.

Of course, this was after trying a few configuration file edits which obvioulsy weren't too effective as they were mostly ignored.

Edgar

---

