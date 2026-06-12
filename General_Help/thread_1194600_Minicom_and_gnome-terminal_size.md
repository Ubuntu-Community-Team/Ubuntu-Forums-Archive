---
title: "Minicom and gnome-terminal size"
date: 2009-06-22
forum: General Help
---

### Post by iimess on 2009-06-22
Previously (8.10 and prior) I could run minicom in a terminal window larger than 80x25. Now (9.04) whenever I start minicom or switch to a tab running minicom, the terminal window shrinks from whatever it was to 80x25, and fights back (bad flickers) whenever I try to change it away from 80x25.

I need a larger size because in the same window, I have other tabs that can benefit from wider size. And it doesn't switch back to the previously set size when I switch away from the minicom tab.

Pure speculation:
Is it a problem with minicom requesting an ideal size, or gnome-terminal trying to be smart to fit the content?

---

### Post by cdub3030 on 2009-07-01
I have have this same problem since upgrading to 9.04 and have not been able to find a resolution either.

---

### Post by cdub3030 on 2009-07-02
Although I still have not found a resolution to the minicom issue, I did come across a good replacement named picocom.  Picocom runs in the existing terminal window it is initiated from and conforms to whatever size the window is set to.

'aptitude install picocom'

---

### Post by ningke on 2009-07-07
picocom works great. Adjusting width of screen is no problem. Thanks!

---

### Post by michael.barnes on 2009-07-30
I know this is an old thread, but there was not a real solution to the problem.  So, has anyone found a solution yet?

The problem is, when starting minicom in a terminal window, it resizes the window and will not allow you to change it.  This is very annoying in some systems I dial into because it wraps the screen.  I also ssh into other machines (mostly they are running SUSE) and run minicom to access remote equipment.  Even through ssh, it resizes my terminal window.

Changing to picocom is not a viable option for me, as I still have to use minicom on remote machines.

I'm using  Ubuntu 9.04 - the Jaunty Jackalope.  I have never had this problem with any other OS.

Any ideas are appreciated.

Michael

---

### Post by iponeverything on 2009-07-30
Is the behaviour the same with xterm?

---

### Post by Mark20 on 2009-08-19
Hi all,

I was having the same issue.  This is a known [_Gnome Terminal bug_]("http://bugzilla.gnome.org/show_bug.cgi?id=579759").  You can verify this by launching xterm and then running minicom - it'll work no problem.  

If you prefer to launch minicom from Gnome terminal here is a hack you can use:

Instead of launching minicom by typing: ```
minicom
``` type the following instead: ```
TERM=linux minicom
```

Cheers,
Mark

---

### Post by klepon on 2009-08-20
Code:

TERM=linux minicom


Hi Mark,

This trick works for me.

Thank you.

---

### Post by cdub3030 on 2009-08-25
'TERM=linux minicom' works for me as well thanks for the tip.

I took this one step farther and added the following to **/etc/bash.bashrc **to make this a permanent setting in all terminal sessions:

```
TERM=linux
```This way you can just type 'minicom' again instead of having to set the env variable each time you launch minicom

---

