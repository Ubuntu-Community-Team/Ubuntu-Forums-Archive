---
title: "Unreadable Fonts - Installing from Source"
date: 2009-04-12
forum: General Help
---

### Post by themusicdan on 2009-04-12
I have been running Ubuntu since January or February this year, and have been working on setting my computer up to act as a music server for my house, so that I could hook the machine up to the sound system and control it from elsewhere. Anyway, I found a great service for it, called mpd and the frontend GMPC, so that I could do exactly what I wanted. Unfortunately, it required a good amount of setup, but that was okay, because I really wanted to have some good experience with configuration and such, so I really enjoyed that part. Then, this past week, I decided to try working on plugins for GMPC, and found that I had to install from source. I'm not that comfortable with installing from source yet, but again, I took it as an interesting challenge and ran with it. So in order to get GMPC working, I found that I needed to install the newest version of it, and that the only way to do that was from source.

When I went to install from source, there were a lot of dependencies missing, and so I started installing them as I found that they were needed. I installed git, gtk+-2.0, freetype, atk, cairo, libmpd, libpng, glib, and pango. I also updated my fontconfig, 

After getting all of this done, but before I could finish the whole process, I found that I was having issues in some dialog boxes, that instead of ascii characters, they were displaying outlined boxes. This seemed like a weird glitch, and I decided to restart my computer to see if that would fix the problem. When I restarted, all of the icons on my desktop were labeled with boxes instead of text, and all of my menus had the same problem. I thought it might be a problem with a recently installed program, and I ran synaptic to see if there was something I could try removing, but all of its text was garbled as well. I have a terminal window, but that is it.

So, two questions: 
1) How do I remove things that were installed from source?  
2) How do I fix the problems with the fonts? I believe it may be a problem with freetype or fontconfig, but I don't really know what I'm doing, so I can't really say for sure.

I am writing this right now from a liveCD, and would really appreciate any help that could help me get back up and running. Thank you for your time.

---

### Post by themusicdan on 2009-04-12
Update: I decided to go back into my OS that's giving me problems and try running some basic programs from terminal. Here's what I got when I went to run firefox. I hope it helps. 

```
dan@themusicdan:~$ firefox

(firefox:6815): Pango-WARNING **: failed to choose a font, expect ugly output. engine-type='PangoRenderFc', script='latin'

(firefox:6815): Pango-WARNING **: failed to choose a font, expect ugly output. engine-type='PangoRenderFc', script='common'

(firefox:6815): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed

(firefox:6815): Pango-CRITICAL **: pango_font_describe: assertion `font != NULL' failed
Segmentation fault
dan@themusicdan:~$ 

```

---

### Post by unutbu on 2009-04-12
Pango is involved in the rendering of fonts, so I'm guessing that the font problem may be related to your new installation of pango. (The firefox error message also indicates a Pango error.)

To uninstall the pango source package from the LiveCD:

```
sudo mount /dev/sdX /mnt       # change sdX to your Linux root partition
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt               # this gives you root shell, as though you had booted Ubuntu normally
cd /path/to/source/pango
sudo make uninstall
```

Or, if you are booted into Ubuntu:
```

cd /path/to/source/pango
sudo make uninstall
```


Then reinstall Ubuntu's libpango package:
```

sudo apt-get install --reinstall libpango1.0-0 
```

---

### Post by qball on 2009-04-12
A guide to install developer snapshot for gmpc
[http://gmpc.wikia.com/wiki/GMPC_INSTALL_DEV_COPY_GUIDE](http://gmpc.wikia.com/wiki/GMPC_INSTALL_DEV_COPY_GUIDE)

If you install something from source and it requires gtk, you don't have to install gtk itself. What you should have done is installed the gtk developer packages (containing the files needed to compile a gtk program).
This package for gtk+ is libgtk2.0-dev.

Installing gtk by hand will/can cause problem, as the packages installed from ubuntu are not build using this gtk. 


Q

p.s. For gmpc you need to type
sudo apt-get install build-essential libgtk2.0-dev libcurl4-gnutls-dev libsoup2.4-dev libglade2-dev gob2 automake1.10 curl git-core libtool intltool
to install the required dependencies for compiling gmpc.

But you don't have to compile stuffby hand to get gmpc +plugins.  Thanks to Ripps  there are packages (of the developers branch)  of gmpc, including plugins. 

[http://gmpc.wikia.com/wiki/Installation_GMPC_Ubuntu](http://gmpc.wikia.com/wiki/Installation_GMPC_Ubuntu)

Next time try reading the programs website :D.

---

### Post by themusicdan on 2009-04-12
Thanks for the help, from both of you.

unutbu - that worked. It appears that pango was my problem. :) 

qball - Yes, I should have been more thorough in reading their website. I did try reading it, and got into the individual plugins pages, which didn't really help me install them at all. I made the assumption that if they have individual pages for plugins, they should show how to install and use them there. The other thing I assumed was that the installation page was meant for the installation of GMPC and not its plugins. Oops. I don't think either of these assumptions was that bad, but yes, I should have been more thorough. Thank you for your help and the sites for me to check out.

---

### Post by TRSS2 on 2010-02-08
I am having a similar issue, I am trying to install ubuntu 9.10 and  all i get is vertical rectangles instead of text... This is my first attempt at installing a linux distro so.. I preemptively am apoligizing for my arrogance. Any/All assitance is more than appreciated, Thanks.[IMG]http://i137.photobucket.com/albums/q221/TRSS2/DSC07806.jpg[/IMG]

---

### Post by HaruSiga77 on 2011-01-04
For those who need another method, this is another method:

Go to **Synaptic Package Manager** in System>Administration

Type pango in the search field and toggle the column with the boxes till you see green boxes. Then choose the first and then **while** pressing the shift key press the down button until the green boxes are highlighted and then right click. Select reinstall. then the BIG apply button and accept. 

Next minimize your windows until you can see your wall paper. Right click on your background and select **Change Desktop Background**. Click on the Font tab and change your fonts to any other font. 

Restart Firefox-4.0 or Firefox (which ever the problem is occurring on...) and then to check if it worked go to your add-ons.(**Tools>Add-ons**) And if your can see the window/tab you should be good to go.

Enjoy! :p

P.S. You can change your fonts back now.

---

