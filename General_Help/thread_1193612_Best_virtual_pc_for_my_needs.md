---
title: "Best virtual pc for my needs?"
date: 2009-06-21
forum: General Help
---

### Post by blckpythn on 2009-06-21
Hello Ubuntu community, I have a need for Windows XP(I know, I never thought I'd see the day.)
I have a Windows XP 64-bit Pro disk and I'm currently running Ubuntu 9.04 64-bit

I'd like to know what the best virtual pc software would be to effectively run WinXP64 and I'm hoping that It will use my hardware as effectively as possible because I'm not fond of seeing "Display Adapter" where my 8600GT should be within XP.

I'm also considering dual booting both XP and Ubuntu, I have 2 seperate drives one of which is empty(potentially for XP) and if that would be a better solution then how would I go about safely installing XP on that second drive without disrupting GRUB?

Keep in mind this is all 64-bit and I'd like as direct of use of my hardware as possible.

Any suggestions would be helpful

---

### Post by psquared89 on 2009-06-21
Well, if you're "trying to use as much of my hardware as possible", then you have to remember that there will always be a price for virtualization.  That said, current CPU virtualization tech is pretty advanced, most modern CPUs support the VTX instruction set which are "virtualization extensions", with these enabled* CPU virtualization overhead will generally hover at ~3% overhead worst case.

As for graphics, virtualization tech is much newer here.  You're best bet if you're determined to virtualize is shop around a bit, try VirtualBox, try VMWare and see where you get the best performance.  You'll want to go straight to the source, since the VirtualBox in the repos is 2.1.4, and VB 2.2.* supports OpenGL virtualization.  If you really want to take full advantage of your graphics card, however, virtualization is not the way to go (yet - give it 5 years).

Given what you've said about your setup, dual-booting should be pretty painless and will definitely make the best use of your hardware. That said, modern virtualization tech is _really_ easy to setup and try, nothing will really hurt you there.

*By default, VTX is _not_ enabled.  You will generally have to look around in your BIOS to enable VTX.

---

### Post by blckpythn on 2009-06-21
Well thank you psquared, I took the liberty of downloading Virtualbox and after testing it it seems to work quite well, I think I'll continue to use this unless some of the games or software I need won't run due to resources or devices being emulated.

---

