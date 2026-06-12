---
title: "ubuntu 8.10 on T43: sometimes get very low brightness"
date: 2009-01-12
forum: General Help
---

### Post by woloo on 2009-01-12
The kernel is Linux ubuntu 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686 GNU/Linux.

And all packages are updated to latest.

The problem is seen back on about 2009-01-08.
If I press CTRL+ALT+F2 then press CTRL+ALT+F7, the brightness restores to normal. Sometimes, it does not swith to tty #2 when I press CTRL+ALT+F2, but the brightness restores.

I'm using built in ATI video driver, instead of compiz or glx.

**lspci** shows the driver:

**01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]**

Anybody has the same problem? It is so troublesome, sometimes I have to switch frequently between the black and white.

----------------------------------------------------------------
NOTE: This mesasge is updated on 2009-01-17 with the following content:
----------------------------------------------------------------

I finally get the conclusion that it is the hardware problem.
Say, the "LCD background light tube" fails to work after busy working for 40+ months. It is replaced today, now everything works fine.

---

### Post by DeMus on 2009-01-12
> **woloo said:**
> The kernel is Linux ubuntu 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686 GNU/Linux.

And all packages are updated to latest.

The problem is seen back on about 2009-01-08.
If I press CTRL+ALT+F2 then press CTRL+ALT+F7, the brightness restores to normal. Sometimes, it does not swith to tty #2 when I press CTRL+ALT+F2, but the brightness restores.

I'm using built in ATI video driver, instread of compiz or glx.

**lspci** shows the driver:

**01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]**

Anybody has the same problem? It is so troublesome, sometimes I have to switch frequently between the black and white.

Can you be a little more specific about your problem? What happens, when does it happen, etc.
What is the resolution you are using and what is the refresh rate? What type of monitor are you using?
Every help you give us makes it easier to help you.

Demus

---

### Post by woloo on 2009-01-12
> **DeMus said:**
> Can you be a little more specific about your problem? What happens, when does it happen, etc.
What is the resolution you are using and what is the refresh rate? What type of monitor are you using?
Every help you give us makes it easier to help you.

Demus

hi Demus,

The screen resolution of T43 notebook is 1400 x 1050 @ 50.0,
it should be OK, right? I did not change X settings for a long time. The monitor of course is a LCD.

I'm developing a **GTK+** program in eclipse, another frequently used application is firefox. I noticed that somebody said the power management daemons *acpid* and *apmd* are possible redundant,
so I disabled apmd, but after reboot it gets blacked within no more than 10 minutes, only firefox is opened.

I just had a look at my dairy, it records that the first "black screen" shown is 3 days ago. The interesting thing is that it is the first day I started to program GTK+ program in **eclipse**!

I'm new to GTK+! Is it possible to get black screen by buggy program? It is extremely dark, the brightness is 5% or so I guess.

Anyway, Demus, thanks for the tips. Maybe it is due to my poor programming skills on GTK+.

--Meng

---

### Post by DeMus on 2009-01-12
> **woloo said:**
> hi Demus,

The screen resolution of T43 notebook is 1400 x 1050 @ 50.0,
it should be OK, right? I did not change X settings for a long time. The monitor of course is a LCD.

I'm developing a **GTK+** program in eclipse, another frequently used application is firefox. I noticed that somebody said the power management daemons *acpid* and *apmd* are possible redundant,
so I disabled apmd, but after reboot it gets blacked within no more than 10 minutes, only firefox is opened.

I just had a look at my dairy, it records that the first "black screen" shown is 3 days ago. The interesting thing is that it is the first day I started to program GTK+ program in **eclipse**!

I'm new to GTK+! Is it possible to get black screen by buggy program? It is extremely dark, the brightness is 5% or so I guess.

Anyway, Demus, thanks for the tips. Maybe it is due to my poor programming skills on GTK+.

--Meng

When you say only 5% brightness do you mean something like which can be seen in the thread:
[http://ubuntuforums.org/showthread.php?t=1037907]("http://ubuntuforums.org/showthread.php?t=1037907")
The author included a picture and when I click that it is shown in front of an almost black screen.
If so there should be a button with a cross in it to close the window and you should be able to see what is behind it in full brightness.
I don't know GTK+, I never program myself, so I can't help you there, but I doubt the fact that it has anything to do with your programming skills.

DeMus

---

### Post by woloo on 2009-01-12
DeMus,

In my case, the monitor is totally dark'd off, darker and darker than the picture you mentioned. I'm not coding any special GUI effects at all, but just some manipulations on pictures to show on a window region.

I'll give more tries to see if it is caused by malfunctioned GTK+ program (started inside eclipse). And will post the result back while I get conclusions.

Thanks,
--Meng

---

