---
title: "Nautilus can't read my home folder"
date: 2006-06-26
forum: Desktop Environments
---

### Post by jimbob on 2006-06-26
Whenever I try to click on my home folder Nautilus displays nothing in it's window.  When I try to close this window it tells me that it it not responding so I have to force quit.

At that point Nautilus immediately spawns another blank window and all my desktop icons disappear.  

The only way out is to log out and back in again which brings back my normal desktop.  If I go to Places -> Desktop that displays just fine.  If I click on up in the desktop window back comes the blank and re-spawning again.

My home directory looks just fine from the command line.  The avatar you see here comes from my home directory so there doesn't appear to be anything corrupted in there.

While Nautilus is re-spawning itself 99% of the cpu is busy.  I have removed and  re-installed Nautilus to no avail.
&#65279;________________________________
  If I can't be Mr. Root I won't play ...
_________________________________
[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by mscman on 2006-06-26
It sounds as though your home directory is trying to load a very large file.  Try running:
```
ls -alh
```
and see if any files or folders are alarmingly large.  I'm not sure WHY it would lock up your computer, and this is only a thought...

---

### Post by Sonofmoog on 2006-06-26
You might also try a cat .xsession-errors, and see if there is anything in there.  If there is a big file in your home folder, I'm betting that's it.  

Other things to try: 

1) launch Thunar File Manager and see if you have the same problem.

2) sudo rm ~/.nautilus directory, which may likely cause more problems than it solves

3) You might consider starting fresh by removing - then recreating  - your user account.  I've solved problems doing this with KDE.  I've honestly never tried it in GNOME .. It's a rather drastic solution, and not to be tried until you've looked at other solutions.

---

