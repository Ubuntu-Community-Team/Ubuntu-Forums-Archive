---
title: "Gaphor 0.8.1."
date: 2006-06-12
forum: Desktop Environments
---

### Post by derk.d on 2006-06-12
Gaphor 0.7 doesn't work on dapper for me but when I went to the website op gaphor I saw version 0.8.1. was out. Can somebody make a .deb for me of the 0.8.1 version???

thnx, a linux noob

---

### Post by fer5437 on 2006-06-12
You can install alien for that if you want to convert .tar.gz to debian.

---

### Post by fer5437 on 2006-06-12
ya forgot to write just now. You can use sudo apt-get install alien. Then in terminal type alien -d <filename>. <filename> is the application that you download. -d is for you to convert to debian. You can type man alien in the terminal to see the manual.

---

### Post by derk.d on 2006-06-12
THANKs!!! I'm going to try it!!

---

### Post by derk.d on 2006-06-12
I installed it succesfully but gaphor won't start, just like the 0.7 version!
When I say run in terminal he is starting and then exit, I can't read the errors because the terminal goes away automaticly...

---

### Post by fer5437 on 2006-06-12
Are you have the error like diacanvas 0.14.2 is old version then failed. I try to download the new diacanvas version 0.14.3 but the page under construction.
So I think you can refer to [http://gaphor.sourceforge.net/manual](http://gaphor.sourceforge.net/manual) for more information.

---

### Post by fer5437 on 2006-06-12
I found out this link [http://www.t2-project.org/packages/gaphor.html](http://www.t2-project.org/packages/gaphor.html) about gaphor. Try it out maybe useful for you.

---

### Post by derk.d on 2006-06-13
thnx!!

I think it has something to do with python, I can't find gnome-python in the repositories but when I install gaphor he checks dependencies right?? and he isn't saying that he is missing something dueing install...strange

---

### Post by luopio on 2006-09-11
I just downloaded the current version (0.8.1) from [http://packages.debian.org](http://packages.debian.org)

Getting the packages gaphor, python-diacanvas and libdiacanvas2 (unstable) I got it installed. However here on my Edgy laptop gaphor causes a segfault and won't start. This happended with the supported old version as well. I've filed this as a bug here: 

[https://launchpad.net/distros/ubuntu/+source/python2.4/+bug/59884](https://launchpad.net/distros/ubuntu/+source/python2.4/+bug/59884)

Anyone else experiencing this?

---

