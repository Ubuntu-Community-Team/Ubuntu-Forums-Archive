---
title: "S-Video out on Lucid w xrandr"
date: 2010-05-15
forum: Desktop Environments
---

### Post by mplsrover on 2010-05-15
Hi Guys, May be you can help me here..

I used to have older version of ubuntu (previous to Lucid,10.4 LTS), and I have a Sony WEGA TV connected to my unbutu laptop w S-Video card connected for Video out...and I used to run following command to activate S-Video out to my TV and it worked perfect...

here's the command that worked :
~$ xrandr --output S-video --set load_detection 1

Now after updating to Lucid/10.4 LTS, this command started getting an error :
~$ xrandr --output S-video --set load_detection 1
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  27
  Current serial number in output stream:  27
---------

I have tried your earlier solution to update  i386 package but getting an error:
--$ sudo add-apt-repository ppa:xeros/xeros-test
$ sudo apt-get install linux-image-2.6.32-22xeros-generic linux-headers-2.6.32-22xeros-generic

and reboot.
------

Can you please help me here ? I can't figure this out...

Thanks in advance...

---

### Post by CarpKing on 2010-06-05
I'll go ahead and bump this for you.  I used a different xrandr command that seems to be failing silently, but your command produced the same error you're getting.  

The strange thing is that upon reboot, my TV is detected and added as a second monitor, and I can configure it using either the builtin GUI configuration tool or xrandr.  After I suspend and resume, the TV stops displaying and does not appear in the GUI tool, and while xrandr doesn't put out any errors (except the one you get) it doesn't display anything on the TV.  

My normal command is:

```
xrandr --output S-video --right-of VGA-1 --mode 800x600 --crtc 1
```

---

