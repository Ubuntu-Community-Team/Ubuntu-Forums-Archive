---
title: "Dell A90 User"
date: 2009-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bladams on 2009-06-24
Just received this netbook today and noticed that the browser seems to be branded with Yahoo.  Now sure of the best way to get Ubuntu 8.04 back to Firefox.  Don't want to dumb the Dell configuration just yet, but would like to get Firefox and OpenOffice up to date.  Thanks,

---

### Post by coffeeaddict22 on 2009-06-28
Hi,
Ubuntu usually stays a bit behind the cutting edge- I believe it's called the bleeding edge where you get to troubleshoot the latest software's problems.  To get right on the edge, have a look [here and ]("http://ubuntumanual.org/posts/183/install-or-upgrade-to-firefox-3-5-rc2-in-ubuntu-karmic-jaunty-intrepid-hardy") [here]("http://ubuntumanual.org/posts/175/upgrade-to-open-office-3-1-in-ubuntu-jaunty-intrepid-hardy").
Ubuntu doesn't run vanilla open office; there's a non-Sun port called Go- OO that is used.  Have a look [here.]("http://www.linux.com/archive/feature/154364")

---

### Post by bladams on 2009-07-04
Thanks for the info., appreciate it. Got a little impatient and installed the Dell 9.04 ISO version.  That corrected both of the problems, got Firefox 3.0 and OO 3.0 and desktop looks familiar again.  Of course, new problems to work on.  Lost sound, that I believe is an known problem with the A90; have found a few fixs, some I tried, so far without success.  Still have others to try. Again, thanks for the reply.

---

### Post by jimrz on 2009-07-04
To fix "no sound" issue on Vostro A90 in UNR 9.04:

first go through the volume control and alsa-mixer and make sure all your controls are turned all the way up and none are muted, then in terminal

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

then add
```
options snd-hda-intel model=dell
```
at the end of the file and save the file.

---

