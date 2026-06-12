---
title: "Desktop Effects Could Not Be Enabled"
date: 2009-09-06
forum: Desktop Environments
---

### Post by emoguitarist06 on 2009-09-06
System>>Preferences>>Apperance "Visual Effects -TAB"

When I choose "normal", "extra", or "custom" my screen flashes and a dialog box opens up saying "desktop effects could not be enabled"

When I run compiz in the terminal I get: 
> pumpkinfeet@ubuntu:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1unhandled buffer attach event, attacment type 7
unhandled buffer attach event, attacment type 7
Comparing resolution (1366x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: unhandled buffer attach event, attacment type 7
unhandled buffer attach event, attacment type 7
present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

and when I run compiz-check I get this
[http://www.flickr.com/photos/42294217@N08/3895480212/](http://www.flickr.com/photos/42294217@N08/3895480212/)
then
[http://www.flickr.com/photos/42294217@N08/3894695175/](http://www.flickr.com/photos/42294217@N08/3894695175/)
and when i say yes my screen turns from this
[http://www.flickr.com/photos/42294217@N08/3895488338/](http://www.flickr.com/photos/42294217@N08/3895488338/)
to this
[http://www.flickr.com/photos/42294217@N08/3895488492/](http://www.flickr.com/photos/42294217@N08/3895488492/)

then i have to restart my gnome session ctrl+alt+backspace

what's going on? please help!

---

### Post by peterthinking on 2009-09-07
Looks like you may be missing some plugins and Nvidia driver for video card....or you don't have a video card.

I have read Nvidia drivers are sometimes difficult for linux and need winwrap.

I'd help more but I just have crappy onboard video and can't run Compiz or desktop effects at all, even though I have a 2.4 Ghz processor....

Go figure!

peterthinking

---

### Post by emoguitarist06 on 2009-09-07
> **peterthinking said:**
> Looks like you may be missing some plugins and Nvidia driver for video card....or you don't have a video card.

I have read Nvidia drivers are sometimes difficult for linux and need winwrap.

I'd help more but I just have crappy onboard video and can't run Compiz or desktop effects at all, even though I have a 2.4 Ghz processor....

Go figure!

peterthinking

Well I actually don't have Nvidia just an Intel graphics card. But I know it's possible for Compiz to work b/c I had ubuntu 9.04 running compiz just yesterday and last night I decided to do a nice clean install and so I downloaded the Alternate ISO and installed a CLI system and built it from the "ground up" and I got my wireless to work but for some reason not  the 3d effects on my laptop

---

### Post by bagy on 2009-09-07
You must have driver for your  VGA...

---

