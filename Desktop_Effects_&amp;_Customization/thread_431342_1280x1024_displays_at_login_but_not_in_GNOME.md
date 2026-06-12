---
title: "1280x1024 displays at login but not in GNOME"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by Henaro on 2007-05-02
Well~

I followed this guide:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

And it seems to be working at the login screen when I first boot up my computer.  But when GNOME loads then it goes right back to 1024x782.  

I'm not sure what I did wrong.   :(

Please help ;D

Thanks,
Henaro

---

### Post by Ferrat on 2007-05-03
What driver are you using for grafics? 
What graficcard do you have? 

=)

---

### Post by orb9220 on 2007-05-03
Just open your xorg.conf file :

> gksudo gedit /etc/X11/xorg.conf


Fine the mode lines where the show "1024x768","etc,,,,"

and add the **"1280x1024"** in front of any mode line you use 24bit,16bit

> Mine is

SubSection "Display"
		Depth		24
		Modes		"**1280x1024" **"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection


---

### Post by Henaro on 2007-05-03
Blah I feel dumb!

I just needed to change it in the screen resolution under the System tool bar.  :frown: 

But now it seems to have made the Desktop Effects->Workspace in a cube to stop working completely.  :confused: 

When I switch back to 1024x786 it will not work either.  

I hope I didn't do anything wrong D:

---

