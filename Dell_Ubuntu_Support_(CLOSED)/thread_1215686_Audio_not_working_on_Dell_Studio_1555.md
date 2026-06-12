---
title: "Audio not working on Dell Studio 1555"
date: 2009-07-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Plasma_Snake on 2009-07-17
My audio was working fine on 8.10 but when I updated to 9.04, the Audio is not working. Mine is the default setup i.e. I didn't tinkered with the audio config and the hardware is the default one that comes in the laptop.

---

### Post by chenxiaolong on 2009-08-03
I have the exact same laptop (Studio 1555).

All you need to do is add

```
options snd-hda-intel model=dell-m6
```

to 

```
/etc/modprobe.d/alsa-base.conf
```

and then restart.

By the way, make sure you edit the file as root (sudo gedit /etc/modprobe.d/alsa-base.conf)

---

### Post by simeethi on 2009-08-04
im also having dell studio 1555.having ubutu over xp as dual boot.im new to ubuntu please help me.i too not getting Audio/sound in my laptop

i tried by typing the following code in terninal window but i got the following message

simeethi@ubuntu:~$ sudo gedit/etc/modeprobe.d/alsa-base.conf options snd-hda-intel model=dell-m6
sudo: gedit/etc/modeprobe.d/alsa-base.conf: command not found 

then tried by typing following

simeethi@ubuntu:~$ sudo gedit/etc/modeprobe.d/alsa-base.conf
sudo: gedit/etc/modeprobe.d/alsa-base.conf: command not found

then tried with following command 

simeethi@ubuntu:~$ /etc/modprobe.d/alsa-base.conf options snd-hda-intel model=dell-m6
bash: /etc/modprobe.d/alsa-base.conf: Permission denied

nothing works for me.idont know how to proceed.

please help somebody to get audio/sound in my laptop

help me by step by step  process

il be very thankful for you guys

---

### Post by chenxiaolong on 2009-08-04
```

```Sorry if my instructions were unclear.

First of all, you need to have a space between "gedit" and "/etc", which is why you get the command not found error. So the correct command is:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

After the text editor opens, paste the following line at the very bottom of the file (scroll down and paste it on a new line):

```
options snd-hda-intel model=dell-m6
```

and then restart your computer. 

I hope this works for you.

---

### Post by harry2006 on 2009-08-04
adding the mentioned line fixes the problem. i did the same and sound is working fine. i vouch for that. thanks.

---

### Post by chenxiaolong on 2009-08-04
You're welcome

---

### Post by Joe10438 on 2009-08-04
> **chenxiaolong said:**
> I have the exact same laptop (Studio 1555).

All you need to do is add

```
options snd-hda-intel model=dell-m6
```to 

```
/etc/modprobe.d/alsa-base.conf
```and then restart.

By the way, make sure you edit the file as root (sudo gedit /etc/modprobe.d/alsa-base.conf)

Thank you! I specifically signed up here (after a two-year hiatus) to ask this question, but you provided a working solution :) 

Ubuntuforums delivers once again!

---

### Post by chenxiaolong on 2009-08-04
You're welcome!! I'm glad it worked for you.

---

### Post by Plasma_Snake on 2009-08-10
Man It worked like a charm. Thank a Gazillion lot dude. If repping was allowed on this site, wud've repped u a million points.=D> BTW how'd u find the solution to this widespread problem?

---

### Post by Ciansy on 2009-09-25
I had the exact same problem and had been trawling the forums for a solution. This one worked perfectly after lots of failures. Thanks a million!

---

### Post by hacker.mnnit on 2009-11-28
_heyy dis is really working thnx a lot buddy,,,,,,,,,,,,,,,,,,,,,,;):P_

---

