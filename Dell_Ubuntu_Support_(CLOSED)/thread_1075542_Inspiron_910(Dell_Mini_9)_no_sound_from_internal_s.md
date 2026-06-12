---
title: "Inspiron 910(Dell Mini 9) no sound from internal speakers but headphone work fine"
date: 2009-02-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by trekgraham78 on 2009-02-20
I own a Dell Mini 9, which orginally had Windows XP on it, but having used Ubuntu in the past, I decided to load Intrepid 8.10 on it. 

I got sound working from earphones, but internal speakers produce no sound even if i unmute and turn up volume on them.  

from /etc/modprobe.d/alsa-base
options snd-hda-intel model=dell
is at the end.

I dont always use headphones or external speakers and would like to be able to hear music when i am mobile.

Any ideas?

---

### Post by trekgraham78 on 2009-02-20
dont know what i did but its working now

---

### Post by HighInBC on 2009-03-25
I had this problem and fixed it the same way. The sound did not just come back though, I had to double click on the volume icon and raise the speaker volume.

The speaker volume is separate from the main volume.

---

### Post by snoguy986 on 2009-03-31
I'm having this same problem.  I have no idea if the headphone jack works, but I tried adjusting the volume within Ubuntu, but I still did not get any sound.

I don't know if it makes a difference, but I'm currently running the latest build of Jaunty Netbook Remix.  I've had the standard installation of 8.10 running on this machine with no sound as well.  What has me puzzled is that the restore disc of Ubuntu 8.04 that came with my laptop has the sound working.  I'm guessing that Dell has a particular driver loaded on that. but I figured Ubuntu would have support for everything in the Mini 9 in future versions.

If someone knows where I can get that driver or knows how I can extract it off that restore DVD I would greatly appreciate it.  Thanks.

---

### Post by anjilslaire on 2009-03-31
Be sure and check this post:
[http://ubuntuforums.org/showpost.php?p=6178990&postcount=3](http://ubuntuforums.org/showpost.php?p=6178990&postcount=3)

This will work on 8.10 on the mini, and should work on Jaunty in theory.

---

### Post by snoguy986 on 2009-03-31
I made that edit in alsa-base.conf that the post you mentioned says to do, but I still don't have any sound.  I suppose it's possible since I'm running Jaunty that this fix may not work.

Would age of the machine have anything to do with it?  It's fairly new, I got it a few weeks ago.  Dell couldn't have already updated the hardware in this thing could they?  It's only been out for half a year roughly.

I will go through the restore DVD I got with the machine and see if there is a .deb or something that installs it, but I'm not holding my breath.

Thanks for your help.

---

### Post by anjilslaire on 2009-03-31
It looks like Jaunty handles sound with no other tweaks besides turning the Speakers volume up:
[http://www.ubuntumini.com/2009/03/ubuntu-904-jaunty-jackalope-beta-on.html](http://www.ubuntumini.com/2009/03/ubuntu-904-jaunty-jackalope-beta-on.html)

If yours are not working, it may indeed be a hardware issue :(

---

### Post by rose1 on 2009-04-01
I was happily getting on with Gaudy G; then downloaded Hardy H and the volume disappeared altogether.   Apparently this isn't unheard of.  My laptop's dell inspiron 1525.   Anyone got a clue how to get sound back??  In plan English please.  Ta!

---

### Post by brianchidester on 2009-04-01
Put 'alsamixer -c0' into the terminal and make sure you have all of the appropriate volumes turned up. Also check in your sound preferences and make sure you have the appropriate devices enabled.

---

### Post by snoguy986 on 2009-04-01
> **brianchidester said:**
> Put 'alsamixer -c0' into the terminal and make sure you have all of the appropriate volumes turned up. Also check in your sound preferences and make sure you have the appropriate devices enabled.

This did it.  The "Internal Speaker" volume setting was set to 0.  Put it at 100 and pulled out my headphones (I had music going already and found out those work) and became momentarily deaf lol.

Thanks for all the help!

---

### Post by altonbr on 2009-04-04
> **brianchidester said:**
> Put 'alsamixer -c0' into the terminal and make sure you have all of the appropriate volumes turned up. Also check in your sound preferences and make sure you have the appropriate devices enabled.

This helped on my Dell Inspiron Mini 9, fresh wiped to Ubuntu 9.04

Thank you!

---

