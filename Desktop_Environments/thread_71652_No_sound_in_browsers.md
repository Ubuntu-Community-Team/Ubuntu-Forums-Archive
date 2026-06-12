---
title: "No sound in browsers"
date: 2005-10-04
forum: Desktop Environments
---

### Post by joegum on 2005-10-04
I just installed  HH 5.04.  IMPRESSIVE!!!

I'm just having one issue...

I have system sound, but no sound in my browsers (Firefox and Epiphany).  Specifically,  at the <www.calculus-help.com> site.  I did download Macromedia Flash Player as  Firefox suggested.  I now have the video, but still no sound.  

Thanks,  -Joe G.

I

---

### Post by Dolphin on 2005-10-04
Yeah, unfortunately the flash plugin mozilla auto-installs doesn't work.  Or at least, it didn't for me.

There was a flashplayer plugin available on the repositories as an apt-get (sudo apt-get install flashplayer-mozilla) but it's gone now for some reason.

---

### Post by joegum on 2005-10-04
Ubuntu really is terrific.  I guess that I can live with one little issue. 

 Thanks for the info!

-Joe G

---

### Post by Hairy_Palms on 2005-10-04
u can make sound work in the browser by typing, 
killall esd
before running firefox then sound should work

---

### Post by joegum on 2005-10-04
Hey Hairy Palms,  I did what you said and it worked.   Thanks!!! -Joe G

---

### Post by pataphysician on 2005-10-04
i did this to get sound working in flash

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

i don't know what it does, but it worked.

---

### Post by Roel Groeneveld on 2005-10-06
For me, this advice made sound in flash work: 
[http://thomer.com/howtos/sound_in_firefox.html](http://thomer.com/howtos/sound_in_firefox.html) 

(hope that helps someone else)  :)

---

