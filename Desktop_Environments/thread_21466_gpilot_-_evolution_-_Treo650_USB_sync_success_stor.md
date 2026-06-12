---
title: "gpilot - evolution - Treo650 USB sync success story"
date: 2005-03-22
forum: Desktop Environments
---

### Post by Blackneto on 2005-03-22
Thought i'd write this up for anyone that might be having difficulties.

I coulnd't get the sync to work no matter what I tried.

I'll list the changes i made that helped get this solved.

1. make sure /usr/share/gnome-pilot/devices.xml
 has the following entry:
 <!-- Palm Treo 650 -->
 <device vendor_id="0830" product_id="0061" />

2. make sure when you run the gpilot wizard from Evolution you use /dev/ttyUSB1. set speed to 115200, set the timeout to 40, set the type to USB.
I believe that theres some udev settings you can use if you want to use the symling /dev/pilot.

3. On the first sync set the conduits to copy from whiever has the most data, computer or device.

heres a short list of all the websites that provided bits and pieces of info that helped:
> [http://ubuntuforums.org/archive/index.php/t-3591.html](http://ubuntuforums.org/archive/index.php/t-3591.html)
[http://gentoo-wiki.com/HOWTO_USB_sync_for_Palm_PDAs_with_Evolution_2.0_a](http://gentoo-wiki.com/HOWTO_USB_sync_for_Palm_PDAs_with_Evolution_2.0_a)
nd_udev
--------------
[http://forums.gentoo.org/viewtopic-p-2113508.html](http://forums.gentoo.org/viewtopic-p-2113508.html)

Check for gnome-pilot apps installed.

[http://www.sujee.net/geeky/zire31.html](http://www.sujee.net/geeky/zire31.html)  Check for gpilotd running in the
background.

----

[http://www.wombatnation.com/2005/02/treo-600-sync-to-evolution](http://www.wombatnation.com/2005/02/treo-600-sync-to-evolution) 
[http://www.clasohm.com/blog/one-entry?entry_id=12096](http://www.clasohm.com/blog/one-entry?entry_id=12096) udev issues?
[http://fedoranews.org/tchung/gnome-pilot/](http://fedoranews.org/tchung/gnome-pilot/)

-------
[http://cpbotha.net/weblogs/cpbotha/archives/000929.html](http://cpbotha.net/weblogs/cpbotha/archives/000929.html) problem has been
around for a while.

[http://howto.pilot-link.org/evosync/index.html](http://howto.pilot-link.org/evosync/index.html) Yet another how to
timeout to 40?

One problem that I ran into that I couldn't find anything on was everything freezing, computer and device when syncing the calendar.  This only happened the first time.

note during trouble shooting i installed and un-installed a lot of the pilot apps in the repository. not sure if any library provided the final piece or not. but currently i only have the following installed according to apt:
gnome-pilot
gnome-pilot-conduits
jpilot (it was with this that I discovered that usb sync was working)
libgnome-pilot2
libgnome-pilot2-dev
libpisock8
libpisync0
pilot-link
python-pysock

Not the best instructions but if this helps anyone that will be great.

This is my fp here and i just installed warty for the first time on friday. I've replaced my Mandrake 10 desktop with it.
So far, on the same hardware, it's faster and less troublesome than Mandrake was.
Cheers to all you fellows that participate in this.

---

### Post by minxmertzmomo on 2005-09-27
For help with that udev trick, see

[http://www.clasohm.com/blog/one-entry?entry_id=12096](http://www.clasohm.com/blog/one-entry?entry_id=12096)

basically, it takes whatever port your treo comes in on (ttyUSB[13579]) and symlinks it to /dev/pilot, so you can then just use /dev/pilot in your palm app config and know that no matter your USB set up, the Treo will always end up on /dev/pilot.

Thanks, by the way, for this post, which helped me get my treo working in about 5 minutes!

---

### Post by openback on 2005-10-04
I've been trying to get my Treo 650 workin gfor a little while now, and after finally figuring out that I needed to load the visor module, I got somewhere. now dmesg tells me that it's connected to ttyUSB1 (and 0), but it's never made. after doing searches for that device, I found it in /.dev and I was able to connect to my Treo through that. But why isn't ttyUSB0 and 1 being created in /dev when I connect it?

---

### Post by palmdoc on 2006-01-29
Has anyone succeeded in getting Card ExportII to work with the Treo650 & Ubuntu?

---

