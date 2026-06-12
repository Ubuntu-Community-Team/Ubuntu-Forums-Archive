---
title: "Virtualbox VRDP + Compiz + Seamless - Ubuntu 8.10.  Very strange issues!"
date: 2008-12-21
forum: General Help
---

### Post by geekman on 2008-12-21
Ok, so I followed two guides in particular which are meant to setup virtualbox in seamless mode, but in a way different to the now built-in version.  I did it this way essentially because I need the use of two monitors and it also doesn't have the desktop bug associated with having no windows open in the VM.

The method I used is described in these two threads:
[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)
[http://ubuntuforums.org/showthread.php?t=821461](http://ubuntuforums.org/showthread.php?t=821461)

These are obviously for older systems, but it can be applied, from memory, exactly as shown in the latter thread.  This gets things working mostly, but now the issue...

When the start menu, task bar, a tooltip, or a windows app shows up; they are all shown in their own gnome window.  Hopefully the linked screenshot will give you a better idea:

[http://www.matrixmud.net/~geekman/Screenshot.png](http://www.matrixmud.net/~geekman/Screenshot.png)

I was initially using Compiz with Emrald with a custom theme, I've changed the desktop effects to normal, and stopped using Emrald in the hope this might kill the bug.  And of course, in order to use dual monitors I'm using the "restricted" nVidia drivers.  Forgive my ignorance, I am as yet unsure as to what further information might be needed, and instead of appending as much output as I can conjure up I rather wait and post more information as needed.  Hopefully someone else knows what's causing this!

Thanks in Advance.

---

### Post by geekman on 2008-12-22
Anyone?  Really want to get this working as I need to finish my current development project in the next month.  Could it be that I need a newer version of the seamlessrdp files?  By the way, I'm using *Virtualbox 2.0_2.0.6*

---

### Post by geekman on 2008-12-22
I just found the following, so I'll investigate that; possibly downgrading rdesktop will help? [https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/275528]("https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/275528")

**Edit:**

*From said page*

> Here's a Temporal workaround if you're using compiz:
Go to Compiz-Config Settings Manager (install it if you don't have it) and in Window Decorations replace 'any' with '!(class=SeamlessRDP)' or if you have other options you can just add '&!(class=SeamlessRDP)' at the end (everything without the quotes). Note that if you grab it by the windows border it may be a little lag before it updates the position of the window, but if you alt+grab it, everything's fine

I did that as follows, and also added the same exception for the window animations since I found that annoying.  It's all working pretty well, except for one last thing.  When I maximize Windows in GNOME they seem to ignore the Windows start bar so therefore it disappears, anyone know a way around this?

---

### Post by geekman on 2008-12-30
Nobody can help with this one last small annoyance?

---

### Post by omriasta on 2009-03-18
Am also using VRDP and virtualbox with compiz. For some reason I am getting a blank taskbar and no start button in my windows guest. I searched and can't seem to find one single other person with this bug. Has anyone noticed this? Attached is screenshot...
I don't mind the window borders and I have tried changing the location of the taskbar and getting rd of awn and a few hundred other things.
Has anyone else seen this? Where would I post this bug? Ubuntu? VirtualBox?

---

### Post by amadeus266 on 2009-05-20
This is a known bug and has been reported in Launchpad. I too have this problem in Jaunty. Thankfully it adds a cool effect to the program I am using it with while compiz is running (it makes the menus and popup windows burn up). I didn't realise it was in 8.10 as well since I skipped that release. It also manifests itself using rdesktop so it must be a Gnome bug.

---

