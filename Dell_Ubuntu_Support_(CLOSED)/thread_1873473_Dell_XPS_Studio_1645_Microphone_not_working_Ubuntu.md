---
title: "Dell XPS Studio 1645 Microphone not working Ubuntu 11.10"
date: 2011-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by _El_Chojin_ on 2011-11-01
Hi:
I have done today a new fresh installation of ubuntu 11.10 and i'm unable to use internal microphones of this laptop with ubuntu.

I have been searching but i'm unable to find a solution to this problem on new ubuntu installations. Can anyone help me on this please? i use skype and at this moment i'm unable to speak.

Thanks in advance.

---

### Post by alab0 on 2011-11-02
Hi all...
I have the same problem on my XPS M1530.
The mic was doing well on the previous version,10.10 and 11.04.

---

### Post by nguyenhoangvk on 2011-11-09
Well, for me there's always problems when install Ubuntu on my Dell 1645, I had to keep myself from Ubuntu from 10.04 because my laptop became overheat and most of the reason is because too much random hang. I love Ubuntu and I decide to comeback but when I try to search google for some experience with Ubuntu on Dell 1645 I found this thread.

Your mic problem is not so big, do you find any other problem ? Overheat or crashes ?

My Dell config is i7 720QM, HD 4670 ATI, 4GB RAM

---

### Post by gueygel on 2011-11-28
I had the same problem. I fixed it adding

options snd-hda-intel model=dell-m6-dmic

to the text file /etc/modprobe.d/alsa-base.conf

---

