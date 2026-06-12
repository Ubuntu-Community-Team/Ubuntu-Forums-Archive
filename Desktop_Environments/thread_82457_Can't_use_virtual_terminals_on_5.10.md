---
title: "Can't use virtual terminals on 5.10"
date: 2005-10-26
forum: Desktop Environments
---

### Post by wwuster on 2005-10-26
I installed 5.10 using the "server" method. I tried ctl-alt-f2, etc to get other terminal screens but that doesn't work. How can I enable this?

thanks,
William

---

### Post by Stormy Eyes on 2005-10-26
[QUOTE=wwuster]I installed 5.10 using the "server" method. I tried ctl-alt-f2, etc to get other terminal screens but that doesn't work. How can I enable this?

thanks,
William[/QUOTE]

That's strange. The /etc/inittab file is usually set up to allow six virtual terminals by default. You could hack on that file, or just do **sudo apt-get install screen** and read [this tutorial](http://www.kuro5hin.org/story/2004/3/9/16838/14935). I personally find GNU screen more useful than switching between VTs.

---

### Post by wwuster on 2005-10-26
this is from my /etc/inittab:

1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

I read something about disabling the splash screen(?) on startup. I can't find it right now. I'm not sure that's my problem, though. I do have a brownish graphic screen when I boot. Do you know how to get rid of that?

William

---

### Post by Tommy on 2005-11-13
[QUOTE=wwuster]I installed 5.10 using the "server" method. I tried ctl-alt-f2, etc to get other terminal screens but that doesn't work. How can I enable this?
[/QUOTE]

I'm having the same problem -- I just upgraded to Breezy from Hoary on my "oldworld" Mac using the "change the repositories in Synaptic and upgrade until it dies, then using aptitude" method. ;-)

Unfortunately I'm having the same problem. Being able to switch among VT7 and  VT9 is essential for running Mac-On-Linux... but I cannot get to ANY virtual terminals without killing X. And I can't seem to kill X with any of the usual keystrokes, either.

---

### Post by Tommy on 2005-11-13
[QUOTE=wwuster]I read something about disabling the splash screen(?) on startup. I can't find it right now. I'm not sure that's my problem, though. I do have a brownish graphic screen when I boot. Do you know how to get rid of that?
[/QUOTE]
Are you describing the Xwindows background, or the boot splash? (Are there boot messages on it, or just a plain screen?)

The brownish screen tends to appear before the login manager... did you check to make sure you don't have xserver-xorg installed, or GNOME or KDE? They won't HURT anything, but if you don't expect to use them and want every cycle of processing power and every byte of RAM on your server, you can keep them from running by not having them installed.

I think I will file a bug about the Virtual Terminals because that's just about a show-stopper for me. In your case, as long as X doesn't start up, you can use screen like Stormy Eyes suggested (though it's NOT equivalent -- if your tty gets hung sometimes you really need to have another available).

---

### Post by 23meg on 2005-11-13
I have the same problem, and removing usplash fixes it. I think it has something to do with usplash not releasing the framebuffer device. I'd love a solution to this.

---

### Post by singamayya on 2006-02-19
[QUOTE=23meg]I have the same problem, and removing usplash fixes it. I think it has something to do with usplash not releasing the framebuffer device. I'd love a solution to this.[/QUOTE]

Unfortunately, usplash is not installed on my system and I am still stuck with the problem. I started out by doing a minimal "server" installation. Then I installed the following packages:

xserver-xorg
rxvt

When there is no X running, I am able to switch between all 6 virtual terminals. But, when I launch X using this command ```
xinit `which rxvt`
```, the Control-Alt-F*n* keys do not work. I become stuck inside X and have to exit X in order to access the virtual terminals again. :-k

---

### Post by Tommy on 2006-02-20
singamayya, are you using a PowerPC computer? I have been told the problem is probably a flaky keymap in xorg (apparently several of them were flaky for PowerPC machines), but I have not yet taken time it would take to learn xorg and track down the problem.

Here's the workaround I use -- as soon as I log in I open an X terminal and when I need to switch to another VT I use the chvt command to switch.

So for example, to switch to Mac-On-Linux on VT9 I use the command

sudo chvt 9

and then once I've switched out of X I can switch among any of the VTs as normal until getting back to X. Xorg seems to "eat" the Ctrl-Alt-Fn keystrokes.

Check out the following two bug reports -- you may be able to resolve it as the other person did.

Here's bug 4465, where someone uncovered and repaired an installation problem:

[https://launchpad.net/distros/ubuntu/+source/xkbutils/+bug/4465](https://launchpad.net/distros/ubuntu/+source/xkbutils/+bug/4465)

Here's the bug I reported (though apparently I am alone because nobody has confirmed it):

[https://launchpad.net/distros/ubuntu/+bug/25701](https://launchpad.net/distros/ubuntu/+bug/25701)

---

### Post by singamayya on 2006-02-20
Many thanks, Tommy!

My system is i686, not PowerPC. So, this problem seems to affect PPC and x86 equally.

[QUOTE=Tommy]Here's bug 4465, where someone uncovered and repaired an installation problem:

[https://launchpad.net/distros/ubuntu/+source/xkbutils/+bug/4465](https://launchpad.net/distros/ubuntu/+source/xkbutils/+bug/4465)
[/QUOTE]

This one doesn't apply to me, because the /etc/X11/xkb/symbols/pc path doesn't exist on my system. The closest I have is: /etc/X11/xkb which is a directory.

[QUOTE=Tommy]Here's the bug I reported (though apparently I am alone because nobody has confirmed it):

[https://launchpad.net/distros/ubuntu/+bug/25701](https://launchpad.net/distros/ubuntu/+bug/25701)[/QUOTE]

You're not alone; this report describes the exact bug I am having. I guess we will have to wait and hope that things get fixed in Breezy.

---

### Post by singamayya on 2006-03-14
Finally, I have found the solution! :-D

Just install the **x-window-system-core** package and it restores the ability to switch between different Virtual Terminals using Control-Alt-F*number*.

---

### Post by Tommy on 2006-03-17
[QUOTE=singamayya]Just install the **x-window-system-core** package and it restores the ability to switch between different Virtual Terminals using Control-Alt-F*number*.[/QUOTE]

I am very glad you found a solution for your system! In my case, that package was already installed. When you installed it, did you happen to notice which packages it "picked up" that were not already installed? You see, x-window-system-core is a "metapackage" and does not really contain much -- except for two documentation files.

But again, I am glad you found a solution that works for you. I have RE-installed it on my system and will report back if anything changes.

---

### Post by khc on 2006-03-18
Does it work if you use the command chvt?

---

### Post by dcstar on 2006-03-18
[QUOTE=wwuster]I installed 5.10 using the "server" method. I tried ctl-alt-f2, etc to get other terminal screens but that doesn't work. How can I enable this?

thanks,
William[/QUOTE]
"**CTRL**-ALT-Fn" is only for when you use the X system, "ALT-Fn" is used when you are **not** running X to switch between screens.

---

### Post by Tommy on 2006-03-19
[QUOTE=khc]Does it work if you use the command chvt?[/QUOTE]

Yes, that has been my workaround since Breezy came out. When I need to switch to full-screen Mac-On-Linux, I use sudo chvt 9 to get to MOL, and from there I can ctrl-alt-Fn among any other vt until I get stuck on vt7 again. X "eats" that key sequence so it goes nowhere.

And to answer another person, I regularly use ctrl-alt-Fn vs. alt-Fn (and all sorts of other keyboard gymnastics) -- my PowerBook Wallstreet keyboard doesn't use the keys in the same way as a PC does. And I don't use a mouse on this system (no desk space) so I use fn-ctrl and fn-option for middle and right click. (Remember it's a Mac so it has only one mouse button built in, and it has a little fn key in the lower left corner that under MacOS you toggle between things like volume up/down, eject and such and PC-style Fn keys.)

Months ago the Debian folks told me there were several bad keymaps in early releases of Xorg for PowerPC, so sometime soon I will try the newer release to see if the problem has been addressed. If not, eventually maybe I'll learn enough about X to figure out the keymap issue myself.

---

### Post by khughes on 2006-04-24
Just thought I would post my results up here in case this might work for anyone else.

I was just reading through this topic because I am experiencing the same issue. After trying all of the suggestions here, still nothing seem to help. I just got mad and slammed my fingers down on the Ctrl + Alt + Fkey for a longer than normal period of time and the terminal switched.

My dad always used to joke that ](*,) "If all else fails, use violence!"](*,)  This theory has now been successfully applied to auto work, plumbing, bosses denying raises, and computers running ubuntu. Thanks DAD!!!

---

### Post by Tommy on 2006-04-27
[QUOTE=khughes]I just got mad and slammed my fingers down on the Ctrl + Alt + Fkey for a longer than normal period of time and the terminal switched.
[/QUOTE]

I'm glad you found a workaround that works on your system! Unfortunately, I haven't been able to make it work here... about how long are you talking about? I held the keys down about 35 seconds, and succeeded only in making the desktop hang. (I didn't want to wait to see if it was going to recover, so I killed X using Ctrl-Alt-Backspace.) I'm using xfce4 on this system, but I've seen the same behavior in Gnome and KDE.... soon maybe I'll be able to test some different keymaps.

---

