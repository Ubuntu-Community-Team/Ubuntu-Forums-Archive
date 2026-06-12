---
title: "Xubuntu Thunar date display"
date: 2007-07-21
forum: Desktop Environments
---

### Post by BradPhipps on 2007-07-21
I use Xubuntu and it's file manager Thunar. I love Xubuntu, but there's one thing in Thunar that really annoys me, that I'd really like to change.

In the "detailed list view" of files, the date modified isnt in a format I'd like. 
If it's showing a file I modified more than a few days ago, it shows the "mm/dd/yy" format. But if I have modified a file recently it literally says "yesterday" or "Monday" in the date column.  And it never shows the time.

The reason I dont like this is I often will have modified 2 files today, and I dont remember which is the most current, and all Thunar will show is "today" and "today" for both modified times. If I use Nautilus, it shows "mm/dd/yy hh:mm:ss" for both files like I want.

Does anyone know of a way to make Thunar show an exact date and time like Nautilus?
Maybe a special setting to put in the thunarrc file?

Thanks for any tips.

Xubuntu Fiesty, Xfce 4.4.0, Thunar 0.8.0.

---

### Post by themeone on 2007-07-22
I also hate the way Thunar shows the dates, and doesn't show the time.  I was just researching how to make it show the time, and came across something which said this isn't possible.  If anybody knows different I would love to hear about it.

In the meantime, I am using the command line if I need times:

ls -l (shows permissions, owner, size, modification time etc)
ls -g (as for -l but without file owners)

In addition the -t option will order the files by modification time, most recent first.

---

### Post by aparigraha on 2007-09-03
Yeah. Have to agree. Kind of annoying. If anyone has any info on this... please share it.

---

### Post by BradPhipps on 2007-09-13
I got the latest svn version of Thunar, and compiled and installed it by myself, following the instructions on  [http://thunar.xfce.org/pwiki/documentation/installation](http://thunar.xfce.org/pwiki/documentation/installation).

Thunar 0.8.1_r26077 has multiple "date format" settings just like Nautilus now! Yay!
The changelog says they added this feature 2007-05-22.

Feisty is Thunar 0.8.0, and it looks like Gutsy will also ship Thunar 0.8.0... 
so unless you can find a repository that has  a version >0.8.1 2007-05-22, we're out of luck.

To the Xubuntu guys: please try and get Thunar 0.8.1 in Gutsy so we can have this feature!

---

### Post by kenwong on 2007-12-17
I'm using Xubuntu 7.10.

The Thunar (0.8.0) never shows the exact dates.  It always displays "today", "yesterday", "Sunday", "Saturday", "Friday", ......

Not like what BradPhipps said.

Do I miss anything here?

---

