---
title: "The hard drive is clicking all the time in ubuntu (dell inspiron 1520)"
date: 2008-04-10
forum: Dell  Ubuntu Support
---

### Post by 8_Ball on 2008-04-10
Hy! 

      I have a problem with my hdd on my dell inspiron 1520. The hdd is  
clicking all the time.I know there is a bug in ubuntu that is killing the hdd.I am using Ubuntu 7.10 (it's a fresh installation).The thing is that on the old install (it was Ubuntu 7.10 before too) I didn't had the same problem.
     I've tried sudo hdparm -B 255 /dev/sda or hdparm -B 254 /dev/sda
but it didn't solved the problem.I am using Win XP too and you can barely hear the hdd.I am using the newest upgrade for BIOS (A07) for a couple of days and I am thinking if that's the problem....I had on the old install the A01 version that came with the laptop.I don't know what  to do....I need some help pls.

   Thanks a lot.

---

### Post by sdennie on 2008-04-10
How frequent are the clicks?  Every 5-10 seconds normally or are they fairly random?

---

### Post by 8_Ball on 2008-04-10
The hdd is clicking all the time...non stop and it's getting hot too.I'm getting a lot of Load_Cycle_Count/day ...the value is somewhere around 200.I don't know what to do...

---

### Post by harold4 on 2008-04-11
It's a well documented issue discussed [here]("http://ubuntuforums.org/showthread.php?t=591503")

---

### Post by Andy Mack on 2008-04-11
Im running Mint on a Vostro 1500 which I think is almost the same as yours except for a few cosmetic touches, anyway, I had that problem and was driving me mad but found a fix last week and not heard them clicks and beeps since.

Make sure hdparm is activated under Services

then, 

sudo nano /etc/hdparm.conf

scroll down to 

#command_line {
# hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

change it to this:

command_line {
hdparm -B 254 /dev/sda*
}

* is which ever partition number you use
Make sure to uncomment by deleting the #

Regarding the heat, there is a topic on this forum which sorted mine out search for something like Dell fan control.

Laptop is very cool despite being on for hours.

---

