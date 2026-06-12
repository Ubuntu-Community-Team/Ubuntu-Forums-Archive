---
title: "glibc problem with Wolfenstein: Enemy Territory installation"
date: 2006-09-21
forum: Gaming &amp; Leisure
---

### Post by Kauna on 2006-09-21
Hello!

I tried to install Wolfenstein: Enemy Territory, but it seems that
my glibc - whatever it is.. I don't have the slightest clue because
I'm new to Linux - is out of date or something. 

```
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55.............................................. .................................................. .................................................. .................................................. .................................................. .................................................. ...
This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
See http://zerowing.idsoftware.com/linux/ for troubleshooting
The setup program seems to have failed on unknown/glibc-2.0

See http://zerowing.idsoftware.com/linux/ for troubleshooting
```

If anybody has had the same problem or knows what I should do,
please take some time to reply. I'd appreciate it very much. [IMG]http://mbnet.fi/lehtiweb/oot_iha_kei/1.gif[/IMG]

---

### Post by haxer on 2006-09-21
Do as it says look in to this !! [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/)

your using an 64 cpu?

---

### Post by croak77 on 2006-09-21
Try typing, export SETUP_LIBC=glibc-2.0, before you run setup.

---

### Post by Kauna on 2006-09-22
Thanks for help, but I got the game installed after I downloaded
the newest version of the installer. Yes, the problems were probably
due to my processor being 64bit, but luckily the newest installer didn't
have problemes with that.

Now that I got the game up and running, it seems I can't hear any sounds.
But I guess I can figure out how to solve it by googling it. :)

---

### Post by fatsheep on 2006-09-23
Here's some info on getting the sound to work in ET if you haven't already fixed the problem:

[http://www.ubuntuforums.org/showthread.php?t=254397](http://www.ubuntuforums.org/showthread.php?t=254397)

---

### Post by gcamaro32 on 2006-09-28
Can anybody supply the links that would bring me to an updated installer? I am have trouble myslef getting ET installed.


root@gcamaro32-desktop:~# sh /home/gcamaro32/Desktop/et-linux-2.55.x86.run Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55~.......................................~
/setup.sh: line 143:  8930 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting

If you can't tell, I'll save you the time in finding out later, that I am a complete noob at Linux. I do hope to become the one teaching instead of learning though. :) Any help would be appreciated. THX!

---

### Post by Kauna on 2006-09-28
Search from the splashdamage's site. I'm sure you can find the 2.60 installer. :)

---

### Post by dmn_clown on 2006-09-29
```
makedir ~/et
mv et*run ~/et/
cd ~/et
sh et*run --tar xvf
mv ~/et/bin/Linux/x86/* ~/et/
./et.x86
```:cool:

---

### Post by lakersforce on 2007-04-21
I found the solution! Look here: [http://ubuntuforums.org/showthread.php?t=416871](http://ubuntuforums.org/showthread.php?t=416871)

---

