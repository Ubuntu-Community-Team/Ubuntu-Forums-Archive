---
title: "Cinnamon freezes in Ubuntu 13.10"
date: 2013-11-25
forum: Desktop Environments
---

### Post by renato3 on 2013-11-25
Hi, this is my situation:
 
Linux: Ubuntu 13.10
Notebook: Dell 14R 5421 notebook with Intel/Nvidia video cards
Symptom: I can successfully login to Cinnamon, but if I click to open the Menu or click anywhere else that pops up a menu, my X freezes.

First I thought that it was due to my Nvidia card, which is not properly installed yet (I have [an open thread about this already]("http://ubuntuforums.org/showthread.php?t=2189408")). But then I saw a lot of people complaining that Cinnamon doesn't work in Ubuntu 13.10. Could someone help me debug this problem to assess if it's a Nvidia video card's issue or if it's an Ubuntu's issue?

---

### Post by Frogs Hair on 2013-11-26
Cinnamon was breaking Unity in 13.10, but there was a fix released if using the ppa version. I don't if this is applicable to the problem you are experiencing or if you are using the ppa. I think the graphics card is a likely suspect.

---

### Post by molgrum on 2013-11-27
I have the same problem but with a Radeon HD 5770 card. I have tried both proprietary and free drivers, and both 3D and 2D Cinnamon. Unity works fine tho.

---

### Post by jon_gunnar on 2013-11-27
> **molgrum said:**
> I have the same problem but with a Radeon HD 5770 card. I have tried both proprietary and free drivers, and both 3D and 2D Cinnamon. Unity works fine tho.

Same problem with
Linux: Ubuntu 13.10
Notebook: Asus X73S with Intel/Nvidia video cards
Symptom: I can successfully login to Cinnamon, but if I click to open the Menu or click anywhere else that pops up a menu, my X freezes.

Mint 15/16 Cinnamon works okay, so it's the conflict with Ubuntu I guess.

---

### Post by renato3 on 2013-11-27
> **Frogs Hair said:**
> Cinnamon was breaking Unity in 13.10, but there was a fix released if using the ppa version. I don't if this is applicable to the problem you are experiencing or if you are using the ppa. I think the graphics card is a likely suspect.

I installed using only official repositories, I didn't use any ppa.

---

### Post by renato3 on 2013-11-27
> **molgrum said:**
> I have the same problem but with a Radeon HD 5770 card. I have tried both proprietary and free drivers, and both 3D and 2D Cinnamon. Unity works fine tho.

Yeah, Unity works just fine... but Cinnamon will crash.

---

### Post by SuperFreak on 2013-11-27
I have always used the PPA with no problems. Albeit I am on 12.04

---

### Post by real_neremor on 2013-12-02
> **renato3 said:**
> Yeah, Unity works just fine... but Cinnamon will crash.

I do have the same Problem here with cinnamon from the ubuntu repositories on ubuntu 13.10, using a nvidia card. When using gwendal repositories I do have the default-Icons-Problem, but apart from that it seems to work (does anybody know how to fix the "only-default-icons"-Problem?)

BTW: is this already reported as a bug?

---

### Post by jimbudler on 2014-02-20
I was having this problem on two different machines.

I was using the theme Void. When I switched to a simpler theme the problem went away.

---

