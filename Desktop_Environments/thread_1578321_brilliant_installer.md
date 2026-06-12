---
title: "brilliant installer"
date: 2010-09-20
forum: Desktop Environments
---

### Post by caieng on 2010-09-20
just a note to express my admiration for the newest version of the ubuntu installer, found on the Lubuntu (LXDE) flavour.

It is VERY skillfully done, best in the business, in my opinion.

You can read my blog to see the test results, but, the bottom line, is this:

Lubuntu trumps all the other distros, in execution, boot, and shut down for this particular task:  streaming audio (internet radio station).

I haven't yet tested the 64 bit version, but the 32 bit version is faster than most 64 bit Linux versions, running on a 64 bit cpu, in my testing thus far.....

My only criticism/suggestion for improvement:  incorporate VLC, make it the default, so that I am not obliged to download both VLC and Konqueror, just to use Lubuntu.

Thanks for a very good accomplishment!!

[http://www.linuxquestions.org/questions/blog/caieng-308178/one-keeper-two-to-throw-back-3191/](http://www.linuxquestions.org/questions/blog/caieng-308178/one-keeper-two-to-throw-back-3191/)

CAI ENG

---

### Post by caieng on 2010-09-22
Follow up:

Strange, on both test machines, Lubuntu suddenly stops the application (web browser), after ten minutes have elapsed....

Any idea why?

The application is Konqueror (because it is the only browser I know of, that permits one to assign VLC as streaming audio player of choice for each of the three different formats:

OGG,
mp3
aaC+

The OS itself is sitting there, on one machine, (PIII), available for another ten minute run, if the user so chooses, but, on the other computer (PIV-'D'), the OS freezes, no mouse, no keyboard, must hard reboot.

Any ideas?  I have not noticed these problems with any other OS....

CAI ENG

---

### Post by 3Miro on 2010-09-22
KDE apps are less stable under GTK environment and this counts double for very system specific apps (like Konqueror) and even more for a somewhat new DE like LXDE (gonme for example has been around for a long time and many of those issues have been addressed over time). Basically, I would have been surprised if Konqueror was stable.

Other than that, there are other reasons that may cause the crash:
1. Check both CPU usage and CPU temperature. PIV-D had some bad reputation for overheating at the time and with Konqueror you are running extra KDE services that you wouldn't normally need.

2. Check Memory usage, with the extra QT libraries that are loaded, you may be running into a memory leak of some sort.

Probably the best way to check for the above is to run "top" in the terminal. You may also install lm_sensors for the temperature.

---

### Post by caieng on 2010-09-22
Thank you very much 3Miro.

I may not have written very clearly, but this problem--shutting off every ten minutes, is not isolated to the PIV "D" cpu computer.  It also is seen on the PIII Tualatin.

The problem is not related to Konqueror, or VLC, in my opinion, as I have run PCLinuxOS LXDE with the same two downloads, Konqueror and VLC, on both computers, without encountering this problem.

The same issue does not arise, as well, when running either XP, or win98 on either machine, so I doubt a problem with heat.  Further, I am using, on the "D" cpu, the world's premier heat sink:  Noctua.  The temperature is WELL below the maximum.

I have also not noticed this problem with Unity 32 or 64 bit versions, though, perhaps there I have not devoted enough time to observe the problem develop.

I will reinstall Unity 64 to test whether or not the problem arises as well with that distro....

Thanks again for your suggestions....

CAI ENG

---

### Post by caieng on 2010-09-23
I reinstalled first CrunchBang from June 2010, works fine, however, there is no need to download VLC with CB, so then I installed Unity 64, from September 2010.

It also works very well, after downloading VLC, and Konqueror.

I have no problem with either computer shutting down with those two distros, as I do, with Lubuntu.  Both distros have run for HOURS, not minutes, without interruption.

Anyone have an idea how this problem can be repaired? Lubuntu simply stops VLC every ten minutes, on the PIII computer, and stops the entire OS on the PIV-"D" computer, after the same ten minute period of time.

CAI ENG

---

### Post by caieng on 2010-09-24
I just finished reinstalling PCLinuxOS LXDE, 32 bit version, with both downloads:  VLC and Konqueror, and it works fine on the Pentium D computer.

It has played streaming audio for more than two hours without interruption.  

The problem is with Lubuntu.

It is a fatal error, for my application, and if anyone has any idea, how it can be fixed, I am all ears.....

CAI ENG

---

