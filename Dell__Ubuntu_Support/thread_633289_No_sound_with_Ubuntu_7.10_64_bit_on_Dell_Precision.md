---
title: "No sound with Ubuntu 7.10 64 bit on Dell Precision M6300"
date: 2007-12-06
forum: Dell  Ubuntu Support
---

### Post by sakisg on 2007-12-06
No sound with Ubuntu 7.10 64 bit on Dell Precision M6300

Please, I have try some things but the problem steel exists
Any help is welcome

 cat /proc/asound/cards
return ...
--- no soundcards ---

---

### Post by moleculeman on 2007-12-07
I have a similar problem with my new Inspiron 1520.

 cat /proc/asound/cards
--- no soundcards ---

Grr

---

### Post by moleculeman on 2007-12-07
Ah. Hold on a second

[http://ubuntuforums.org/showthread.php?t=632748](http://ubuntuforums.org/showthread.php?t=632748)

Whoops :oops:

---

### Post by leub on 2007-12-08
This trick does not resolv DELL precision M6300 sound problem.


With the "l linux-backports-modules-generic"
the sound seems to be ok, boot and os sounds ok and jack works but the sound anormaly grow up when playing....:(
the codecs used are these ones:
[B][I]> 
root@m6300:~# grep Codec /proc/asound/card0/codec#*
/proc/asound/card0/codec#0:Codec: SigmaTel STAC9205
/proc/asound/card0/codec#1:Codec: Conexant ID 2c06[/I][/B]

i tired to follow a procedure for SigmaTel STAC9205 (another DELL model)
but it doesnot work well..



....waiting for news...

---

### Post by sakisg on 2007-12-12
It does not work on my m6300
After  sudo apt-get install linux-backports-modules-generic 
I am still get 
cat /proc/asound/cards
--- no soundcards ---

Please help me no sound = no music  ;(

---

### Post by linux23dragon on 2007-12-12
> **sakisg said:**
> It does not work on my m6300
After  sudo apt-get install linux-backports-modules-generic 
I am still get 
cat /proc/asound/cards
--- no soundcards ---

Please help me no sound = no music  ;(

Try using the 32Bit version of Ubuntu-7.10.  And then install the backports.

---

### Post by sakisg on 2007-12-12
> **linux23dragon said:**
> Try using the 32Bit version of Ubuntu-7.10.  And then install the backports.

Thanks linux32dradon but I am afraid that 32 Bit version is not an option to me... because of the memory.
And It is not easy to re-Install my Laptop as I am already in production

---

### Post by linux23dragon on 2007-12-12
> **sakisg said:**
> Thanks linux32dradon but I am afraid that 32 Bit version is not an option to me... because of the memory.
And It is not easy to re-Install my Laptop as I am already in production


Well there is lots of other solutions to try. 

This following post is a step by step process that should help.  You have already done some of the steps mentioned on this thread : -

[***_[COLOR="Blue"]Sound card solutions[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=530374&highlight=dell+1520")


It should cover most things, including Ubuntu support and Alsa Wiki links.
Please remember that other people have put lot of effort (to help people in your situation) in putting threads together with a lot of solutions.

---

### Post by psypher on 2007-12-14
don't know bout 64bit ubuntu, but I followed this:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) option g

followed the rest of the instructions and it fixed the increasing sound problem and my front control buttons work perfectly. But I also have the Intel HD audio controller not sigmatel, might be the reason

---

### Post by linux23dragon on 2007-12-14
> **psypher said:**
> don't know bout 64bit ubuntu, but I followed this:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) option g

followed the rest of the instructions and it fixed the increasing sound problem and my front control buttons work perfectly. But I also have the Intel HD audio controller not sigmatel, might be the reason

Hi psypher

Sigmatel is one of many codecs used with some Intel HDA sound cards.

You can find out what codec your sound card uses by pasting this command in a terminal (example) : - 

```
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by EcliptuX on 2008-01-26
> **leub said:**
> With the "l linux-backports-modules-generic"
the sound seems to be ok, boot and os sounds ok and jack works but the sound anormaly grow up when playing....:(
There is a bug report about this problem : [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/186054](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/186054)

---

