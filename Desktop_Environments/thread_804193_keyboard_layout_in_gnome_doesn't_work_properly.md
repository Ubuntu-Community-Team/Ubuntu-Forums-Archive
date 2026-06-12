---
title: "keyboard layout in gnome doesn't work properly"
date: 2008-05-22
forum: Desktop Environments
---

### Post by yochaigal on 2008-05-22
The GNOME keyboard layout switch doesn't work properly. Even though I map it to a key it only works until I restart my machine.
Any ideas/workarounds besides disabling automatic logon?
See bug report on bottom.

Steps to reproduce:
1. Keyboard Preferences -> Layouts tab -> Layout options...
2. Under "Ctrl key position" choose "Make CapsLock an additional Ctrl"
3. Close the control panel and observe that CapsLock now acts as Ctrl
4. Reboot and log in again.
5. Observe that the setting change is no longer in effect (CapsLock does not act as Ctrl). To restore it, I need to open up the Layout Options control panel and choose that setting again, even though it already appears to be selected.


[https://bugs.launchpad.net/gnome-control-center/+bug/173721](https://bugs.launchpad.net/gnome-control-center/+bug/173721)


Thanks

---

### Post by yochaigal on 2008-05-28
Really? No one?

Well I'll just have to figure this one out by my lonesome, then...

---

### Post by stasplamadeala on 2008-05-29
I have almost the same problem. My keybord layout preferences doesn't save after reboot. Instead of three languages afailable for typing there apear only two and one of them doesn't work properly.

---

### Post by rootkowski on 2008-08-12
> **stasplamadeala said:**
> I have almost the same problem. My keybord layout preferences doesn't save after reboot. Instead of three languages afailable for typing there apear only two and one of them doesn't work properly.

You're not alone. I have exactly the same problem and no solution. I described my problem at [http://www.linuxmint.com/forum/viewtopic.php?f=55&t=14831]("http://www.linuxmint.com/forum/viewtopic.php?f=55&t=14831"). Since Husse is at work on this one there should be a solution, but as he says in the linked thread it's hard to say when.

Cheers

---

### Post by FiFtHeLeMeNt on 2008-08-12
I have this problem too :(

---

### Post by yochaigal on 2008-08-12
The weird thing is, It doesn't happen on my wife's laptop.  She has hardy as well, all the updates, same languages chosen (hebrew and english) yet gnome doesn't give her any issues. If it had, I believe she wouldn't have used linux as her primary machine.  Kind of a deal-breaker to a lot of people.

thanks

---

### Post by Svenstaro on 2008-09-01
I can confirm this trouble. I use a wireless Sharkoon media keyboard and after every reboot it forgets its setting which is annoying as hell.
On no other Ubuntu machine have I ever had this problem.

Does nobody know a solution? :(

---

### Post by yochaigal on 2008-09-02
I wish I had a solution... what's weird is that my wife's machine (an HP Pavilion DV4000) has NO problem.

---

### Post by Svenstaro on 2008-09-02
I just fixed it using a hard-solution: Just add Options "XkbLayout" "de_DE" to your Xserver. Of course, this is only a workaround.

---

### Post by rootkowski on 2008-09-15
Hi everyone!

I'd like to say that I have come to a sort of solution. It seems, that, at least on my system, it's 2nd and 4th languages that get messy. So if you need only 2 languages, set a third one but place it as second and then the two you need (first and third) should work well. If you want to read how exactly it went for me you can head for [http://www.linuxmint.com/forum/viewtopic.php?f=55&t=14831]("http://www.linuxmint.com/forum/viewtopic.php?f=55&t=14831")

I hope it will at least partly solve your issues.

Cheers

---

