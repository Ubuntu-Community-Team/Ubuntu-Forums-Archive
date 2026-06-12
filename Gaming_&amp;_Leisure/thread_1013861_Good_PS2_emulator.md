---
title: "Good PS2 emulator?"
date: 2008-12-17
forum: Gaming &amp; Leisure
---

### Post by crazyfuturamanoob on 2008-12-17
I want to play PS2 games on my Ubuntu laptop, how could I do that?

---

### Post by Tom Mann on 2008-12-17
You want to check out PCSX2, I believe there is a guide somewhere on these very forums :)

---

### Post by Izek on 2008-12-17
If using Wine for it, I believe you may have trouble. Wine doesn't like to negotiate with sound hardware very well. Unless they finally fixed all that.

I have trouble with PCSX2 as well, of course, it's because it's slow, and I have the double image problem with it (IE: Where the image is right-side up and upsidown overlapping each other.)

No matter what system, PCSX2 will be slow if I recall correctly. I suggest avoiding ZeroSPU by the way, it's given me nothing but trouble on all three computers I've owned.

---

### Post by crazyfuturamanoob on 2008-12-17
> **Izek said:**
> If using Wine for it, I believe you may have trouble. Wine doesn't like to negotiate with sound hardware very well. Unless they finally fixed all that.

I have trouble with PCSX2 as well, of course, it's because it's slow, and I have the double image problem with it (IE: Where the image is right-side up and upsidown overlapping each other.)

No matter what system, PCSX2 will be slow if I recall correctly. I suggest avoiding ZeroSPU by the way, it's given me nothing but trouble on all three computers I've owned.

Wine doesn't relate this anyhow. That emulator works natively under Linux. I just installed it with synaptic.

But I read somewhere that emulator needs BIOS dumped from ps2, and it's not included with the emulator. I don't have a ps2.

---

### Post by Izek on 2008-12-17
> **crazyfuturamanoob said:**
> But I read somewhere that emulator needs BIOS dumped from ps2, and it's not included with the emulator. I don't have a ps2.

google search ps2 bios, and you'll find a package or a rar file. Hopefully you can extract the rar file without it extracting the files as empty files like what 7zip does with prx files on linux (but not windows.)

---

### Post by crazyfuturamanoob on 2008-12-17
> **Izek said:**
> google search ps2 bios, and you'll find a package or a rar file. Hopefully you can extract the rar file without it extracting the files as empty files like what 7zip does with prx files on linux (but not windows.)

How to get a ps2 game then? Is an ISO ok? Or can I use a regular ps2 game cd/dvd/disk thing?

---

### Post by Maheriano on 2008-12-17
> **crazyfuturamanoob said:**
> How to get a ps2 game then? Is an ISO ok? Or can I use a regular ps2 game cd/dvd/disk thing?

Getting ISO if you don't own the game is illegal. The best way is to buy the game and play it from the ROM or make a backup disc and play that in the ROM.

---

### Post by crazyfuturamanoob on 2008-12-17
> **Maheriano said:**
> Getting ISO if you don't own the game is illegal. The best way is to buy the game and play it from the ROM or make a backup disc and play that in the ROM.

Let's not talk about getting the iso. But can that emulator run an iso?

---

### Post by Maheriano on 2008-12-17
> **crazyfuturamanoob said:**
> Let's not talk about getting the iso. But can that emulator run an iso?
I'm going to start installing the emulator tonight and I'll let you know once it's up and running. Unless someone else confirms it first.

---

### Post by hikaricore on 2008-12-18
[B]WOAH WOAH WOAH

No talking about pirated bios files or iso images.[/B]
Only warning, i will shut this thread down and smack the hell out of you all.

---

### Post by Izek on 2008-12-18
Yes, I suggest going to cheat/homebrew communities to talk about stuff like this. They're usually a little more lax about it.

---

### Post by crazyfuturamanoob on 2008-12-18
If I ask can that emulator run an iso and how, is it talking about piratism?

---

### Post by Izek on 2008-12-18
> **crazyfuturamanoob said:**
> If I ask can that emulator run an iso and how, is it talking about piratism?

It's leading into it because a CD/DVD isn't an ISO, it's a disk. The emulator can run an ISO if it is an ISO. If it's a disk, you need a completely different CDVD plugin.

I suggest looking at the different CDVD Options that your CDVD plugins offer. One of them will _only_ boot from the CD/DVD Drive you have.

---

### Post by Maheriano on 2008-12-18
> **hikaricore said:**
> [B]WOAH WOAH WOAH

No talking about pirated bios files or iso images.[/B]
Only warning, i will shut this thread down and smack the hell out of you all.

I'm not pirating anything, I own a PS2 and a pile of games that I'll be testing after installing the emulator. However I never got to it last night like I had hoped I would. Maybe over the weekend.

---

### Post by crazyfuturamanoob on 2008-12-18
Hey maybe I could install the official PS2 BIOS into a virtual machine?

---

### Post by Barky on 2008-12-19
> **crazyfuturamanoob said:**
> Hey maybe I could install the official PS2 BIOS into a virtual machine?

3d isn't supported with vm's as far as I know

---

### Post by crazyfuturamanoob on 2008-12-19
> **Barky said:**
> 3d isn't supported with vm's as far as I know

Ok. 

What if I make a special partition onto my hard drive, then install PS2 BIOS there and I could dual-boot it with Ubuntu! :D How to do it?

---

### Post by crazyfuturamanoob on 2008-12-19
sorry i got a double post, laag ^.^

---

### Post by jorj82 on 2008-12-19
> **crazyfuturamanoob said:**
> Hey maybe I could install the official PS2 BIOS into a virtual machine?

The only thing a Playstation BIOS is good for (outside of the PS itself) is putting it in the BIOS folder of an emulator.  It is basically the "brain" of the emulator.  If you want some good tutorials about emulation, check out NGemu.com

---

### Post by dfreer on 2008-12-19
> **crazyfuturamanoob said:**
> Hey maybe I could install the official PS2 BIOS into a virtual machine?

This really doesn't make any sense, it won't work. The PS2 has unique chips that a computer simply doesn't have, requiring them to be emulated. Furthermore, the chips the computer does have in common are different (different processor speeds, different graphic cards, etc etc). 

Nothing to do with whether the virtual machine can support 3D acceleration really.

---

