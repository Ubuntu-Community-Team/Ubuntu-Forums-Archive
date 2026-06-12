---
title: "How to turn off system beep in Cinnamon?"
date: 2013-10-22
forum: Desktop Environments
---

### Post by josephellengar2 on 2013-10-22
I am using 13.10 with a Cinnamon desktop. I just cannot figure out how to turn off the system beep. In cinnamon it's a splashing sound, like a drop of water, but it happens whenever there would normally be a system beep, for example in a terminal autocomplete with multiple possibilities. Going to the control panel -> sound -> disable sound effects didn't do anything, nor did `xset b off`. Any idea how I would do this?

---

### Post by josephellengar2 on 2013-10-23
bump.

---

### Post by whatthefunk on 2013-10-23
I dont know anything about Cinnamon, but you might be able to get it through alsamixer in the terminal.  Is there another mixer on your system?

---

### Post by ibjsb4 on 2013-10-23
Perhaps

[http://ubuntuforums.org/showthread.php?t=859176&p=5383887#post5383887](http://ubuntuforums.org/showthread.php?t=859176&p=5383887#post5383887)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=turn+off+system+beep&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=turn+off+system+beep&sa=Search&cof=FORID:9)

---

### Post by josephellengar2 on 2013-10-24
> **ibjsb4 said:**
> Perhaps

[http://ubuntuforums.org/showthread.php?t=859176&p=5383887#post5383887](http://ubuntuforums.org/showthread.php?t=859176&p=5383887#post5383887)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=turn+off+system+beep&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=turn+off+system+beep&sa=Search&cof=FORID:9)

I've tried all of that already. The problem is it's not the internal speaker. It is cinnamon making a sound effect whenever the internal speaker would ordinarily go off, so most of the available solutions don't work.

> **whatthefunk said:**
> I dont know anything about Cinnamon, but you might be able to get it through alsamixer in the terminal.  Is there another mixer on your system?

Cinnamon is a fork of Gnome 3, just with a more "normal" feel to it, so most of the Gnome 3 tools work. I've already turned off all sound effects in the Gnome 3 mixer, and it doesn't effect this.

---

### Post by whatthefunk on 2013-10-24
How about the suggestions offered here:
[https://wiki.archlinux.org/index.php/Disable_PC_Speaker_Beep](https://wiki.archlinux.org/index.php/Disable_PC_Speaker_Beep)

Keep in mind they are for Arch so all of them may not apply to a Debian based system.

---

### Post by josephellengar2 on 2013-10-25
> **whatthefunk said:**
> How about the suggestions offered here:
[https://wiki.archlinux.org/index.php/Disable_PC_Speaker_Beep](https://wiki.archlinux.org/index.php/Disable_PC_Speaker_Beep)

Keep in mind they are for Arch so all of them may not apply to a Debian based system.

Unfortunately, I had already tried all of these. I think that much of the problems stems from it being a system error, but it doesn't use the system bell. Is there any way that I could track down the sound file that makes this sound so that I could just rename it? Where are files like that kept for gnome 3? It should be the same for cinnamon.

---

### Post by semw2 on 2014-03-19
Old thread, but in case anyone else comes across this thread trying to find this out, I'll post the solution for posteriety: open dconf-editor, go to org.cinnamon.desktop.wm.preferences, and untick audible-bell.

---

