---
title: "Dell Mini 9 and Ubuntu 8.10 and No Microphone?"
date: 2008-11-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jpatten on 2008-11-14
Hi All..

I've installed the 8.10 release of Ubuntu on a Dell Mini 9. Everything works fine with one exception. I can not get the internal microphone to work. I have checked the forums and have not found a solution.  

Does anyone have a solution to enabling the internal microphone?

Thank you!

---

### Post by barryjohnwilliams on 2008-11-14
I had a problem with my Mini 9 at first.  First check you have enabled the option 
'dell' in your alsa modules.  If you can hear sound then it should only be a matter of setting the front mic as the input source.  In volume control I enabled all the options in the preferences and was able to set the first input source to front mic.  Then I needed to adjust the recording volume and mutedness.

---

### Post by nedx on 2008-11-14
I'm having the same trouble with the microphone.  Your solution sounds promising, although for me, its a little vague.  I've been using Ubuntu since 6.10 and I've never had to do anything to the alsa modules (I've had to do a lot to get my stupid wifi working on my old laptop which works great on 8.10 with no hassle btw).  So, if you could provide a little more info on specifically where I configure alsa, it would be appreciated.

---

### Post by barryjohnwilliams on 2008-11-15
Hi,

Sorry should have been clearer about the alsa portion of my post (I presumed the original poster had sound working and only their mic was the problem).  What you need to do is:

edit /etc/modprobe.d/alsa-base

At the end of alsa-base file add:
options snd-hda-intel model=dell

This was taken straight from the following guide:
[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

Barry

---

### Post by Rallg on 2008-11-15
Regarding sound: I had seen the alsa-base editing thing before, but couldn't get it to work... because I did not read all instructions. After editing alsa-base and rebooting, be sure to double-click the volume control, and turn up the SPEAKER volume. Previously, I had only turned up the MASTER volume, which is not good enough. (Not sure about the microphone, since I have not tried it.)

---

### Post by Tyche on 2008-11-19
> **Rallg said:**
> Regarding sound: I had seen the alsa-base editing thing before, but couldn't get it to work... because I did not read all instructions. After editing alsa-base and rebooting, be sure to double-click the volume control, and turn up the SPEAKER volume. Previously, I had only turned up the MASTER volume, which is not good enough. (Not sure about the microphone, since I have not tried it.)

You know?  Sometimes I feel VERY dumb.  :)  I took the reference to the SPEAKER volume to mean the PC speaker, as it would be in a desktop computer.  But, of course, the Mini 9 isn't using external speakers, so it WOULD be the PC speaker.  Now that you straightened me out, it works.  Thanks.

---

