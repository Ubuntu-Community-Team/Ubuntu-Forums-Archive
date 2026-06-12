---
title: "Unity launcher does not retain changes"
date: 2011-07-14
forum: Desktop Environments
---

### Post by vikdak on 2011-07-14
I installed Natty Narwhal on a brand new Ideapad Z570 and everything worked out of the box except wifi for which I had to blacklist acer_wmi. 

I installed Google Chrome and replaced firefox with chrome in the launcher. So everything works fine until I reboot. Firefox is back. I saw this a couple of times so I though why not just get rid of firefox. Unfortunately now there's nothing in place of firefox. 

I tried unity --reset but that just shows a bunch of errors. I have dconf-tools and libdconf0 installed.

---

### Post by Krytarik on 2011-07-14
> **vikdak said:**
> I have dconf-tools and libdconf0 installed.
Have you already tried reinstalling "libdconf0"!?:
```
sudo apt-get install --reinstall libdconf0
```
Thereafter, relogin and then see if it retains your settings beyond the session.

Greetings.

---

### Post by vikdak on 2011-07-15
Seems to work. Thanks

---

