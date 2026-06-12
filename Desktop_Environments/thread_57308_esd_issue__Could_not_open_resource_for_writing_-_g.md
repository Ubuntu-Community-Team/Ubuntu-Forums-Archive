---
title: "esd issue:  Could not open resource for writing - gnome-cd"
date: 2005-08-16
forum: Desktop Environments
---

### Post by danns on 2005-08-16
This problem is not limited to gnome-cd as I have experienced it in Totem also.  I run fluxbox instead of gnome, and thus do not run esd.

For audio playing I primarily use xmms but the other day I fired up gnome-cd to play a cd and realized I could not.  Same thing with Totem, it would not play the cd.  Since I started these from a terminal I could see a warning:

** (gnome-cd:9624): WARNING **: Could not open resource for writing.

After some playing around I realized that the problem was esd was not running.  If esd was running I would not get this error.  

I've seen the reverse of this where xmms will not play because it is set for alsa or oss and not esound if esd is running.  I can easily make the necessary changes in xmms to get it working again, I don't seem to be able to do this with gnome-cd or totem.

Is there a way to get gnome-cd or totem to use a different sound system?  My /etc/libao.conf is set to alsa09 instead of esd.  But this did not help.  I do not have a .libao.conf overriding the settings either.

---

### Post by jmcnaught on 2005-08-16
hey,

i think all you need to do is change the gstreamer default output.  in gnome you can do this by going to system>preferences>multimedia system selector.   elsewhere, from the terminal you could run ```
gstreamer-properties
```  
you can change the default audio output to alsa, oss, esd, arts or custom.

hope that helps,

jeremy mcnaughton

---

### Post by danns on 2005-08-16
That seemed to do the trick there, although I ran into another issues.  It seems under the gstreamer-properties I cannot set the Default Sink to alsa, I get the following error:

Failed to construct test pipeline for 'ALSA'

when I test.  If I try to play:

(gnome-cd:9928): GStreamer-CRITICAL **: gst_pad_send_event: assertion `GST_STATE (parent) >= GST_STATE_PAUSED' failed

I tried re-installing the gstreamer0.8-alsa plugin, but nothing changed.

Thanks for the heads up though!  One step closer.

---

