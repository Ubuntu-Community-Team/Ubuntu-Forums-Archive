---
title: "Please, need help with multichannel audio on Inspiron 1525"
date: 2008-11-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by k.p.odoherty on 2008-11-25
Hi,
I have a few questions regarding multichannel audio on a Dell Inspiron 1525.

I would like to use the two headphone jacks + the mic jack as outputs to create a 6 channel output (3 x stereo).

So in qjackctl or patchage I guess I will need to patch it like this:
audio out_1 & out_2 to system playback_1 & playback_2 (going to 1st headphone jack);
audio out_3 & out_4 to system playback_3 & playback_4 (going to 2nd headphone jack);
audio out_5 & out_6 to system playback_5 & playback_6 (going to mic jack).

My problem is that I am already a few too many steps ahead of myself! To start off with I can't even get the 2nd headphone jack working, let alone set the mic up to send a signal.  

I've look at the help "Second Headphone Jack Does Not Work" at

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Second_Headphone_Jack_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Second_Headphone_Jack_Does_Not_Work)

But I'm on 8.10 so this doesn't help. 

Can anyone help me at least get started with setting the 2nd headphone jack up and getting independent audio to it? At least then I'll have 4 outs.

Thanks a lot,
Peter

---

### Post by k.p.odoherty on 2008-11-29
*BUMP*

No takers? Surely there's someone out there who can do this..?

---

### Post by dennis1200 on 2008-12-15
I have had the same problem with the second headphone jack, and after fiddling around, I figured part of it out. In volume control (double-click on the volume icon or type in ```
gnome-volume-control
``` you need to click on Preferences, and check the boxes next to Center, LFE (and maybe, for your future setup, Side as well). Unmute those two, raise the volume level if applicable and you should have two channel output from the second-headphone jack. Center seems to activate the left channel and LFE the right channel.

Unfortunately, the first headphone jack seems to override anything - if something is plugged into the first jack, the second jack is silent. Hrumph.

---

### Post by k.p.odoherty on 2008-12-18
Thanks a lot for your reply. As you say, the 1st jack overrides the 2nd. It's very frustrating and such a waste of a second headphone jack!
Regards,
Peter

---

### Post by dennis1200 on 2008-12-19
However, I know that both jacks would work simultaneously in 7.10 (which the Dell support page talks about, but doesn't correspond to 8.10 menu options), so it ought to be possible. Perhaps something to do with pulse audio vs. alsa?

---

### Post by gustavofuhr on 2009-01-05
Hi, I was dealing with this problem ... and finally get the solution ..

I ve posted it in another thread, please follow 

[http://ubuntuforums.org/showthread.php?t=903828]("http://ubuntuforums.org/showthread.php?t=903828")

greetings

---

### Post by k.p.odoherty on 2010-12-01
Sorry for the very belated reply. I've got it working now. Many thanks for your help.
Peter

---

