---
title: "changing screen, now 640*480, help"
date: 2005-08-09
forum: Desktop Environments
---

### Post by adrislayer on 2005-08-09
Hi, I had a TFT 17" and now I have changed with an old CRT 19" wich supports 1280*1024 at 85hz without problem.

But since I chaned screen, I cannot modify screen resolution and it stuck at 640*480...

I already tried this:

sudo dpkg -reconfigure xserver-xorg

And after rebooting, still the same.

I have no other choice in the gnome resolution changer little programm...

Here is my xorg.conf file: [http://membres.lycos.fr/adrislayer/xorg.conf.txt](http://membres.lycos.fr/adrislayer/xorg.conf.txt)

I don't know what to do.

And I also tested lunching the programme of gnome in "sudo" but still the same...

I have an Nvidia 6600 GT, the drivers are correctly installed and all. Now what can I do?

Please help me, and thanks for your answers

---

### Post by Irony on 2005-08-09
I'm still new to this but I'd guess you'd have to put in horizontal and vertical figures, e.g.;

[I]sudo gedit /etc/X11/xorg.conf

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72[/I]

These are the figures for my monitor so your figures would be different. I got the correct figures by using the Live CD because it gave the correct resolution.

However before you alter your xorg.conf file do a back up of your xorg.conf file;

*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup*

On booting up if GUI doesn't appear but goes to command line, do the following;

[I]ubuntu login; username
password; password[/I]

Then type;

*sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf*

Then;

*Ctrl + Alt + Del*

This reboots and should bring you back to GUI.

---

### Post by adrislayer on 2005-08-09
thanks a lot !

It has saved me, now I'm at 1280*1024.

And also, can anyone give me an url where I can find the horizontal sync and vertical rate correctly? Well just a list of some monitors to give an idea.

thanks :p

---

### Post by WAM on 2005-08-10
I would try either the website of the company who made your monitor, or just typing your monitor name in Google (ie, Compaq 7550).

---

### Post by ad noiseam on 2005-08-10
[QUOTE=adrislayer]
And also, can anyone give me an url where I can find the horizontal sync and vertical rate correctly? Well just a list of some monitors to give an idea.
[/QUOTE]

It might not work at all for you, but what I did when I had this problem was to boot Windows XP, check the refresh rate that was working there, and put a range in the Xorg.conf that was bigger as that.
In my case, I needed 85 Hz and put the following in Xorg.conf

	HorizSync	28-90
	VertRefresh	43-90

It might not work at all for you, but it did the trick for me.

Nicolas

---

### Post by heimo on 2005-08-10
As already mentioned, for VertRefresh and HorizSync it's best to use values from user manual, which is usually available as a download from manufacturers website.

Collection of instructions on how to solve these problems (which I'd like to soon transfer to some wiki page):
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by ekravche on 2005-09-03
> **Irony]I'm still new to this but I'd guess you'd have to put in horizontal and vertical figures, e.g. said:**
> sudo gedit /etc/X11/xorg.conf

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72[/I]

These are the figures for my monitor so your figures would be different. I got the correct figures by using the Live CD because it gave the correct resolution.

However before you alter your xorg.conf file do a back up of your xorg.conf file;

*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup*

On booting up if GUI doesn't appear but goes to command line, do the following;

[I]ubuntu login; username
password; password[/I]

Then type;

*sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf*

Then;

*Ctrl + Alt + Del*

This reboots and should bring you back to GUI.

This fixed my problem. Thank you for the help

---

