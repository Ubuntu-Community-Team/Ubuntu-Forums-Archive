---
title: "today's update broke opengl"
date: 2006-06-08
forum: Gaming &amp; Leisure
---

### Post by kevlarman on 2006-06-08
i just recently installed ubuntu and got it mostly set up. Opengl was working perfectly for a couple of days, but today right after installing the update (edit: i don't believe i have done anything else that could have broken it, but i'm not 100% sure), my opengl programs (tested with Wolfenstien: Enemy Territory and planetpenguinracer) will constantly flicker for a few minutes and then crash. I was wondering where I could find the list of things updated and what the old versions were.
edit: also, the sound will randomly not work

---

### Post by B0rsuk on 2006-06-08
Moral of the story

- updates are important
- config file backups are important
- when you do something manually, you remember what you did and how to undo it.
- relying on automatic stuff too much can be dangerous.
- people who don't agree with sentences above are wrong.

 I will disable automatic updates as soon as I install Dapper... or I'll check Debian Etch instead. I heard it's nice.

---

### Post by kevlarman on 2006-06-08
it appears the opengl bugs weren't from the update. for some strange reason, after running 'sudo dpkg-reconfigure xserver-xorg', and finding that i should set my refresh rate to 60hz (which I already knew), Gnome wouldn't let me set the refresh rate to anything other that 85hz. Anyway, messing with xorg.conf fixed that, now just to figure out the sound.
edit: automatic updates aren't enabled by default in dapper

---

