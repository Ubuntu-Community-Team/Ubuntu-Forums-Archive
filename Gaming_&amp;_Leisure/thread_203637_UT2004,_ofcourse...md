---
title: "UT2004, ofcourse.."
date: 2006-06-25
forum: Gaming &amp; Leisure
---

### Post by odbod on 2006-06-25
Before I go through the hassle of getting ubuntu on again, I would like to know if ubuntu would be better for gaming. With these specs, mainly:

Intel P.4 @ 3 ghz HT technology
1 gb (pc5400)
nVidia geforce 7300 512 mb(? I forget) pcie 16x
200 gb sata drive.

Mainly UT2004, I play that game non stop, and I feel like using ubuntu as my main operating system.

I heard that the nvidia cards are mainly supported in linux and have there own drivers for linux, so that's good for me! But, I'm still not sure if everything would be the same or better.

---

### Post by bocmaxima on 2006-06-25
UT2k4 runs amazingly for me under Linux, way better than the Windows version.


[QUOTE=odbod]Before I go through the hassle of getting ubuntu on again, I would like to know if ubuntu would be better for gaming. With these specs, mainly:

Intel P.4 @ 3 ghz HT technology
1 gb (pc5400)
nVidia geforce 7300 512 mb(? I forget) pcie 16x
200 gb sata drive.

Mainly UT2004, I play that game non stop, and I feel like using ubuntu as my main operating system.

I heard that the nvidia cards are mainly supported in linux and have there own drivers for linux, so that's good for me! But, I'm still not sure if everything would be the same or better.[/QUOTE]

---

### Post by autocrosser on 2006-06-25
Well--I'm waiting for the parts for my Pent D 3.2 to show up (:D:-D) & I decided to try UT2004 on a old Pent3 650--It not only loads fairly well--but with the details turned down to Low--It plays fairly well:p--Tried Rankin & Plunge to test it & in single player I had a good time8)--(this old dog runs 1800+FPS)

Specs on this LOW_END unit are:
650MHZ--384 ram--30GB drive--Gforce 5200

So--I can hardly wait til my new unit is together!!!!!!!

---

### Post by professor_chaos on 2006-06-25
I can't compare to windows, as I dont have that installed. But my specs are well below yours, and I have absolutely no complaints about the preformance. It's truely unbelivable. 

3200+ AMD athlon
1gb ram
5700 GE Nvidia

---

### Post by Perfect Storm on 2006-06-26
I don't have windows either. But UT2004 runs smoothly on my machine even if I run it in 1600x1200 with high graphic details.

P4 2.4 GHz 1024mb 800mhz ram.
GF 6600 GT

---

### Post by odbod on 2006-06-26
ok.. That's cool.. So ubuntu can play games well then.. Out of the box, will the nvidia stuff work?](*,) I heard it can, I'm just wondering if the out of the box drivers will be good enough, or do I have to get the latest?

(guess sata drives will work too I see)

---

### Post by Perfect Storm on 2006-06-26
It's quiet easy to enable nvidia drivers on ubuntu. It would be worser if you had ATI card (not ubuntu or linux fault, the blame is at ATI).

The one that you can install through apt-get works good.

---

### Post by Hg80 on 2006-06-26
im getting 300+ fps as a rule using Ubuntu, AMD x2 4400, 1 GB OCZ mem, and a 7800GT 256mb

---

### Post by bocmaxima on 2006-06-26
[QUOTE=odbod]ok.. That's cool.. So ubuntu can play games well then.. Out of the box, will the nvidia stuff work?](*,) I heard it can, I'm just wondering if the out of the box drivers will be good enough, or do I have to get the latest?

(guess sata drives will work too I see)[/QUOTE]

Yeah, I have a SATA drive and had no problem (unlike windows where I had to buy a floppy disk and load the drivers on). I also have a 6600gt and the drivers were pretty simplistic and work quite well.

---

### Post by odbod on 2006-06-30
cool cool cool! Can't wait!

---

### Post by dipswitch on 2006-06-30
Can someone point me towards a guide on installing UT2004 in Ubuntu? So far I haven't been able to sucessfully install it at home and I think thats just about the remaining factor in switching for good.

---

### Post by Perfect Storm on 2006-06-30
What have you tried so far?

---

### Post by dipswitch on 2006-07-01
I can't find the guide that I tried to use to install and I really don't remember (its been a few weeks and I got frustrated and quit and went back to XP).

I do know that what ever I tried KILLED MY AUDIO and still haven't been able to get it working. It also created a ut-436 folder on my desktop that I CAN'T get rid off. I don't know what the hell to do now except for a total reinstall at maybe try it again. 

Anyone have any suggestions on how to...

1) get my audio working again
2) get rid of the ut-436 folder on my desktop
3) install UT2004

TIA

---

### Post by Perfect Storm on 2006-07-01
Let's try. 

If the you don't have any sound it could be you should run killall on the sound first. There's a thread about it a couple a days ago. [http://ubuntuforums.org/showthread.php?t=201855](http://ubuntuforums.org/showthread.php?t=201855)

Installing ut2004:

Prerequirement: 3d acc. card driver installed.

Installing:

Open the terminal and the ut2004 
in the terminal you write **sudo sh** and afterwards drag the linux ut2004 installer file into the terminal. It should look something like this or similiar:
```
sudo sh /media/cdrom/ut2004-installer.sh
```

an installer window should pop up, just follow it with its default settings.
Now exit it the ut2004 installer. **Don't hit the "start ut2004" button**. When you have exited the installer. type **ut2004** in the terminal.

---

### Post by dipswitch on 2006-07-01
Thanks for the reply. I'll give the install another shot with your instruction and report back.

I'll work on the evil undeletable ut-436 folder after. And my dead audio. :(

---

### Post by dipswitch on 2006-07-01
[QUOTE=dipswitch]Thanks for the reply. I'll give the install another shot with your instruction and report back.

I'll work on the evil undeletable ut-436 folder after. And my dead audio. :([/QUOTE]

It didn't work...


```
dipswitch@dipswitch-desktop:~$ sudo sh
Password:
sh-3.1# /media/cdrom0/linux-installer.sh
sh: /media/cdrom0/linux-installer.sh: /bin/sh: bad interpreter: Permission denied
sh-3.1#

```

---

### Post by Perfect Storm on 2006-07-01
```
sudo sh /media/cdrom0/linux-installer.sh
```




> I'll work on the evil undeletable ut-436 folder after. And my dead audio. 

```
 cd Desktop
sudo rm -rf ut-436
```

You can't properly delete it normally because you don't have user previledge to do so.

---

