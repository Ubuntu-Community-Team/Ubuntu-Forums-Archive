---
title: "How do I install themes on Ubuntu?"
date: 2013-03-15
forum: Desktop Environments
---

### Post by KingJosiah on 2013-03-15
Greetings Programs! I must confess, I am a complete newb when it comes to Ubuntu, Linux, and the whole shebang. However, I did get Ubuntu 12.10 installed on an external hard drive and am currently dual booting it alongside my Windows 7, to try it out, play with it, and learn. Now the default themes are nice, but I am a big TRON fan, and when I discovered that the interface on Flynn's terminal in TRON: Legacy was a form of Ubuntu, I thought it would way cool to have that type of display set as a theme. So I found these: 

[http://linux.softpedia.com/get/Desktop-Environment/Themes/newtonian-flynn-ui-68556.shtml](http://linux.softpedia.com/get/Desktop-Environment/Themes/newtonian-flynn-ui-68556.shtml) 

[http://gnome-look.org/content/show.php/?content=141391](http://gnome-look.org/content/show.php/?content=141391)

Trouble is, I have no CLU how to install either one, although I do think they are both the same theme. Could someone give me directions on how to install these? I have made no modifications to the install that I did, outside of fixing the GRUB 2 boot loader (I accidentally installed it half on my internal and half on my external, so I had to have the external drive plugged in to boot Windows at all. I was able to install the GRUB on the external solely and fix the Windows boot loader with a recovery disk, then I configured the BIOS so it tries to boot from my external first).

---

### Post by slickymaster on 2013-03-15
You just have to download them to your home folder. Then open a terminal window and run the following:
```
tar -zxvf filename.tar.gz
```
Afterwards just drag-and-drop the extracted folder to the styles list in **Settings Manager > Appearance**.

---

### Post by ManamiVixen on 2013-03-15
What version of Ubuntu you have?

---

### Post by KingJosiah on 2013-03-15
I have 12.10. And thank you slickymaster, I will try that. We'll see what happens.

---

### Post by ManamiVixen on 2013-03-15
12.10? That theme isn't compatible. Ubuntu 12.10 comes with GTK 3.6 and what you gave for your theme is only for GTK 2.0-2.32. Technically, you can use it, but only GTK2 apps will be themed, GTK3 apps with look like Windows 98. If you are not happy with the default theme, you have to pic a theme that states GTK 3.6 compatibility.

---

### Post by slickymaster on 2013-03-15
Here's some places were you can find some good themes for 12.10:

[http://gnome-look.org/index.php?xcontentmode=167](http://gnome-look.org/index.php?xcontentmode=167)
[http://xfce-look.org/](http://xfce-look.org/)
[http://browse.deviantart.com/?q=ubuntu+12.10+themes](http://browse.deviantart.com/?q=ubuntu+12.10+themes)

---

### Post by KingJosiah on 2013-03-15
Hmm. Well those are all very nice themes, but I would really like a theme that looks like the terminal shown in Legacy and in the themes I linked to above. Is there a way to convert a theme to make it GTK 3.6 compatible? Can I take some of the saved files in those themes and tweak them to work? Better yet, is there a tutorial where I could learn how to make a theme myself, and use the creator of these there's work as a springboard?

---

### Post by slickymaster on 2013-03-15
> **KingJosiah said:**
>  Better yet, is there a tutorial where I could learn how to make a theme myself, and use the creator of these there's work as a springboard?
Well, you can go to **/usr/share/themes/**, where all the themes you have on your system are, and start editing/replacing the images and the colors in the configuration files.

If you want to make your own from scratch, you have this guide to help you getting started: [Gtk Theme Creation Guide]("http://orford.org/gtk/")

---

### Post by ManamiVixen on 2013-03-15
No, converting isn't possible. You'll have to rewrite the theme from the ground up using CSS, as gtk 3.6 is written using that language. Even then, GTK 3.6 and Unity's Window Decorator dosen't support transparencies, so you can't make the glassy air look. On a light note, GTK 3.6 still supports Legacy GTK 2 apps. When creating a GTK3 theme, you'll have to provide a GTK-2.0 and GTK-3.0 version of the theme in the joint theme folder. 

This isn't a tutorial, but it would make sense to CSS programmers as it lists the styling and requirements for GTK 3.6 Themes.
[URL="https://developer.gnome.org/gtk3/3.6/GtkCssProvider.html"]https://developer.gnome.org/gtk3/3.6/GtkCssProvider.html
[/URL]

What [ 						 					]("http://ubuntuforums.org/member.php?u=1753126") 				 				 					 						 	[**[COLOR=#000000]slickymaster[/COLOR]**]("http://ubuntuforums.org/member.php?u=1753126")  provided was only for GTK 2

---

### Post by Frogs Hair on 2013-03-15
Install Downloaded Themes or icons in 11.10-12.04-12.10


Install the Gnome Tweak Tool / Advanced Settings for making theme selections from the software center .  


Use only GTK 3.6 themes for 12.10-GTK 3.4 for 12.04 and GTK 3.2 themes for 11.10. Check this in the theme description at the download location. 


Download and fully extract the theme packages and hold the folders on the desktop until needed . (Right Click Extract Here)


(Single User) Create a .themes and .icons folder in home / hidden folders . Use Crtl + H to open hidden folders in Nautilus.


(All Users) Use gksudo nautilus in the terminal to open  Nautilus as root and navigate to > File System / usr / share / themes or icons .


Place the folders in either Location . Use the Tweak Tool / Advanced Settings to make theme selections . Logout - in may be required before themes are visible in Advanced Settings . 

[http://gnome-look.org/index.php?xcontentmode=167](http://gnome-look.org/index.php?xcontentmode=167)

---

### Post by KingJosiah on 2013-03-15
Thank you all. I may have to download some random theme and install it to see if I know what I'm doing now.

I dug up some theme making and CSS tutorials, so I'll see what I can do as to making the theme the way I want. In case anyone already knows of a theme, I want to make my desktop look like what is shown on [http://www.helloflynn.com/](http://www.helloflynn.com/) , minus the keyboard and access history of course. I can get the little ENCOM doohickey in the lower right corner as a background wallpaper by taking a screenshot.

I will update this thread when I have access to my computer to see if my issue was trying to use an incompatible theme.

---

