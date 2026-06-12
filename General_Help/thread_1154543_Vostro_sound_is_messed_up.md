---
title: "Vostro sound is messed up"
date: 2009-05-09
forum: General Help
---

### Post by spetsacdc on 2009-05-09
Hi, I just installed jaunty on my vostro 1500. Originally my sound did not work at all. The first thing I did was this:

[http://ubuntuforums.org/showthread.php?t=635333](http://ubuntuforums.org/showthread.php?t=635333)

After that, the sound still didn't work at all and I had the annoying system onboard beep when I shutdown and backspace too much in terminal.

Then, I followed the last post on the first page of this page:

[http://ubuntuforums.org/showthread.php?t=569082](http://ubuntuforums.org/showthread.php?t=569082)

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Now, my sound works but I have 2 problems: my headphones do not work at all, and I still have the system beep. The sound does keep working after standby.

I tried to fix the system beep with at least 3 methods. I put blacklist pcspkr in a bunch of files, and ran some commands. My bios doesn't have an option for mother board speaker.


Any help would be great.

Thanks

---

