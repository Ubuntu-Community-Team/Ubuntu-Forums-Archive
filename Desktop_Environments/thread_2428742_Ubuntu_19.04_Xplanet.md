---
title: "Ubuntu 19.04 Xplanet"
date: 2019-10-08
forum: Desktop Environments
---

### Post by 27grains on 2019-10-08
I have xplanet installed. I see in "Tools" that it is working but I can't see it on the Desktop. I tried to copy xplanetFX1.png to backgrounds thinking that was the problem, I copied it to pictures.  I am not sure what I did but I have xplanetfx1.png as a picture on my desktop.

I don't know what to do to get it working. I paid for clouds and find that site went down.

I need help. maybe a Youtube video on How to install xplanet and get the clouds. I know free clouds are available and paid ones.

I don't know where xplanet is putting the picture or how to get it on the desktop.

Please help.
Thank You

---

### Post by Frogs Hair on 2019-10-12
I installed the xplanet images .deb to find out where the directory was created. The location is usr/share/doc/xplanet-images. I can't get the application to open on 19.10

---

### Post by cruzer001 on 2019-10-12
> **Frogs Hair said:**
> I can't get the application to open on 19.10
Same in 18.04 even though there is a /usr/bin/xplanet, it will not execute.

So looking around I found this:
[http://xplanet.sourceforge.net/FAQ.php#gnome](http://xplanet.sourceforge.net/FAQ.php#gnome)

I think you should visit their forum.
[http://xplanet.sourceforge.net/FUDforum2/](http://xplanet.sourceforge.net/FUDforum2/)

---

### Post by 27grains on 2019-10-13
> **Frogs Hair said:**
> I installed the xplanet images .deb to find out where the directory was created. The location is usr/share/doc/xplanet-images. I can't get the application to open on 19.10

I have read everything I can. I am looking for an answer.

---

### Post by Frogs Hair on 2019-10-13
> I don't know where xplanet is putting the picture  It was stated where Xplanet images were installed when using the following. ```
sudo apt install xplanet-images 
``` Their forum has been mostly inactive since 2012 with a few exceptions.

---

### Post by Holger_Gehrke on 2019-10-13
xplanet is an old-fashioned graphics hack. Unless told otherwise it draws it's picture in the root window. Which is fine if you're running a minimal system with a window manager and not much else, but with modern Desktop Environments that put an undecorated window in front of the root window it leads to severe confusion. In theory you can find out the window id of the desktop window and use  the -window-id option to make xplanet put it's graphics there, in  practice this will lead to the image repeatedly getting drawn and then  hidden again when the DE refreshes the desktop. The manual page for xplanet describes the many options for using it to create image files either singly or in series. The script cruzer001 linked to is probably your best bet but will need some work to get it to run the way you want it to.

For clouds you need to change the configuration file /etc/xplanet/config/default and insert 'cloud_map=picture_file' in the section [earth] (if you put it in the global configuration, the clouds will be overlaid on all planets ... might be amusing, but is probably not quite what you want). If you're using the images from the Space Science and Engineering Center of the University of Wisconsin-Madison ([https://www.ssec.wisc.edu/data/comp/latest_moll.gif](https://www.ssec.wisc.edu/data/comp/latest_moll.gif) , updated every 3 hours) you also need to give the option 'cloud_ssec=true' in the configuration to remove the coastline and to correct for the used projection. You could set up a cron job to download the newest cloud image every three hours ...

Holger

---

### Post by 27grains on 2019-10-14
> **cruzer001 said:**
> Same in 18.04 even though there is a /usr/bin/xplanet, it will not execute.

So looking around I found this:
[http://xplanet.sourceforge.net/FAQ.php#gnome](http://xplanet.sourceforge.net/FAQ.php#gnome)

I think you should visit their forum.
[http://xplanet.sourceforge.net/FUDforum2/](http://xplanet.sourceforge.net/FUDforum2/)

I have read both links several times. I see "How can I get xplanet to work with Gnome?   " Add this script to System->Preferences->Sessions->Startup Programs (GNOME 2)# or Startup Applications (GNOME 3) " I have no idea how to follow those instructions.

Those instructions are for xplanet, is it valid for xplanetFX ?

In the sourceforge forum it was explained to me that xplanet is not xplanetFX ..When I installed the tar.gz from sourceforge and the images... I launched the xplanetconf icon and I got a terminal in German. 

Using translate I made selections and got nothing.
typing xplanet -window a box popped up with planet earth (a picture), xplanetFX is working I can see it in tools  I have tried many paths to output, pictures, wallpaper, gnome nothing works. The background folder is root all pictures are .jpg I read that xplanet needs .png. what I had was xplanetFX and xplanet both installed.

I gparted the partition and installed ubuntu 19.10  and I get the same nothing.

I sudo cp xplanetFX1 and 2.png into the background folder went to desktop right clicked to change and the .png pictures were not available... it didn't read them.

What changed in Ubuntu 12 to 19 that causes fplanetfx not to work? is there a desktop environment I can use instead of Gnome? or is it something else that changed.

Where is the source code for xplanetFX that I can read?

Thank You I didn't come here expecting anyone to tell me a simple answer. Mein blog is just about useless.

[https://ubuntuforums.org/showthread.php?t=2365985](https://ubuntuforums.org/showthread.php?t=2365985)  is when this started,.  following those instructions worked until the ubuntu upgrade. I have been trying to learn linux a long time, it's not easy for me.

Thank You Gary

---

### Post by cruzer001 on 2019-10-14
> **27grains said:**
> Those instructions are for xplanet, is it valid for xplanetFX ?
In the sourceforge forum it was explained to me that xplanet is not xplanetFX
Sorry, but that is just how little I know about xplanet.  Seems Holger is better suited to answer.  I simply loaded xplanet into a virtual machine and found it would not boot for me.

And based on what Holger has posted I think I would move on to another program.  Maybe Celestial, I am not familiar with that one either.

[https://celestia.space/](https://celestia.space/)

---

### Post by Holger_Gehrke on 2019-10-14
xplanetFX is just a UI for xplanet. '/usr/bin/xplanetFX' is a massive shell script (**76kb** is massive for a shell script) and '/usr/share/xplanetFX/xplanetFX_gtk' (which gets exec'ed if you execute the shell script with the option '--gui' as the desktop file does)  is a Python script (not small either at just under 200kb + more than 200kb for the .glade-file that describes the GUI). To make things more interesting the Python GUI seems to call the shell script with various parameter to do the actual work. So if you've installed xplanetFX you've got the source. All xplanetFX does is make xplanet render an image and then post process it with ImageMagick.

And regarding the question what changed from 2012 to now, I can only ask the counter question: "What hasn't ?".  There also seem to be a couple of problems in the shell code, it has ways to recognize several DE's and as far as I can tell the code for recognizing XFCE (which I am using) should work, but it still fails to set the background with a message about not being able to identify my DE ...

Holger

---

### Post by Holger_Gehrke on 2019-10-15
Okay, *somewhat* good news. On my XFCE xplantFX now renders and sets a wallpaper. The GUI saves a configuration in '~/.xplanetFX/xplanetFX.conf. That configuration sets the right options for XFCE (a line saying 'XFCEOPTIONS=Single,monitor0/workspace0' is created) **but** it also sets 'DESKTOP=' (yep: nothing, empty, nil, zip, zilch, nada). Editing that file, removing that line and being careful afterwards to avoid anything that might make the GUI save it again (and restoring the mistake), I got it to render and set the wallpaper.

Holger

---

