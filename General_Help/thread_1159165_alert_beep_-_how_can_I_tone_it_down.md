---
title: "alert beep - how can I tone it down?"
date: 2009-05-14
forum: General Help
---

### Post by raymondh on 2009-05-14
My goal is to minimize/reduce/alter the tone of the system (alert) beep that occurs specially on shutdown. 

I do not want to disable/blacklist my drivers/modules.  I know I can toggle off at system > preferences > sound but, I prefer to have the alert tone.  

I've been trying to alter values in setterm -blenght and -bfreq but to no avail.  Could it be because of ALSA?  Am I attacking my problem wrong?

I could edit with an .inputrc file and set bell none.  However, I really prefer to have that alert (I find it valuable) ... I just want it less "annoying/startling" (without me having to turn off my speakers).

Recommendations much appreciated.  Thanks in advance

---

### Post by WatchingThePain on 2009-05-14
Hi,

When I right click volume applet I have a slider for pc speaker.

Obviously it can be turned off like you said but I am not sure there is a way to change the volume as it's most likely built in.

Some people put a bit of tape over the speaker (don't laugh).

You could maybe replace the pc speaker on the mainboard with one which has a lower volume. I'm sure the speaker won't cost much.

I have seen them in Maplin.

---

### Post by DougieFresh4U on 2009-05-14
Also, in 'gnome alsa mixer' there is a button 'pc beep' which you can adjust volume level.

---

### Post by gooligan on 2009-05-15
I tried many tricks, but the shutdown was still bugging me ...... until I followed this post and removed the pcsprk module. Now I have silence...... :)
[http://www.foogazi.com/2008/05/01/how-to-disable-the-system-beep-in-ubuntu/](http://www.foogazi.com/2008/05/01/how-to-disable-the-system-beep-in-ubuntu/)
IMHO, this should be disabled by default.

---

### Post by Greenwidth on 2009-05-15
> **gooligan said:**
> IMHO, this should be disabled by default.

I agree.

---

### Post by evermooingcow on 2009-05-15
One of the many options for disabling the pcspkr is to set the frequency to zero - maybe you can use the same method to change the frequency of the beep - not to zero if you still want to be able to hear it but to something less annoying than the default.

Unfortunately I don't know the command for it but searching for "system bell debian" will bring up some relevant results.

---

