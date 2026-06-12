---
title: "Help My Video Card screws up ubuntu"
date: 2009-03-17
forum: General Help
---

### Post by TheSlav on 2009-03-17
Whenever I go into hardware drivers options it installs my video card, BUT when i do I restart the computer and it says "wrong frequency or something like that. When this happens I cannot boot my computer up at all. I had to reinstall ubuntu. Please help meeee'zzz. 


ALso on another subject.
I have virtual box.
I also have a windows xp disc.
Tell me how to dual boot off of virtual box?

Thank you for viewing

---

### Post by prince_niceguy on 2009-03-17
what is your graphics card? which version of ubuntu are you using? have you tried going into the recovery kernel option in grub and try to fix the xserver?

---

### Post by LegendofTom on 2009-03-17
Virtualbox is virtualization software, which allows you to run an OS inside another OS.  Dualbooting is another concept, where two OS are installed beside eachother on one harddrive.

---

### Post by TheSlav on 2009-03-18
> **prince_niceguy said:**
> what is your graphics card? which version of ubuntu are you using? have you tried going into the recovery kernel option in grub and try to fix the xserver?\



Im using version 8.10 Ubuntu. and i have an ati video card. Please how did i keep my card activated without having that stupid fuc==== message

---

### Post by prince_niceguy on 2009-03-18
that is strange, ati card should work out of the box... try recovery option from grub menu and see if it resolves the issue or not.

also, please disable desktop effects for the time being to ensure that you do not end up running into the blank white screen.

can you put the lspci command output.

---

### Post by shadowdude1794 on 2009-03-18
Oops

---

### Post by D3ath on 2009-03-18
> **TheSlav said:**
> Whenever I go into hardware drivers options it installs my video card, BUT when i do I restart the computer and it says "wrong frequency or something like that. When this happens I cannot boot my computer up at all. I had to reinstall ubuntu. Please help meeee'zzz. 


ALso on another subject.
I have virtual box.
I also have a windows xp disc.
Tell me how to dual boot off of virtual box?

Thank you for viewing

Are you running the linux OS in the virtualbox?  If so there should be guess add-ons to install that will help with your vm. If not disreguard.  Maybe change your refresh rate in System > Preferences > Screen Resolution.

---

### Post by D3ath on 2009-03-18
> **shadowdude1794 said:**
> Oops


how is that going to help anybody?  Not cool.

---

### Post by shadowdude1794 on 2009-03-21
> **D3ath said:**
> how is that going to help anybody?  Not cool.

I had misread the post, and given information that wouldn't have helped him. Don't assume things my good sir.

---

### Post by D3ath on 2009-03-21
> **shadowdude1794 said:**
> I had misread the post, and given information that wouldn't have helped him. Don't assume things my good sir.
Understand. You could have put that lol. It's all good.

---

### Post by HughJarse on 2009-03-30
I would agree with that. I tried using the ATI support in Hardware Config and after that the PC just hangs when I try doing anything. I went into Recovery mode to roll back. It works but not at the best resolution.
BTW I have a Radeon 9600

---

