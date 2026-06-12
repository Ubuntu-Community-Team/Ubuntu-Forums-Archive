---
title: "Please help, really stuck here!!"
date: 2006-02-13
forum: Desktop Environments
---

### Post by zeltak on 2006-02-13
Help!!

im new to linux (and very sick of windows). ive used ubuntu for a while (2 weeks) and loved it!!! i decided to swithc my HTPC to ubuntu as well using  this excellent guide: [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)
(i have the same computer specs as in the guide) and deleted my previous windows HTPC. All went well until i got to the line:

Then, do the following:

depmod
modprobe ivtv
dmesg

in the modprobe ivtv command  i get the following error:

"Fatal: module ivtv not founf"

What am i doing wrong? im kinda stuck here without an HTPC computer (and no tv for wife )... Can anyone help me out??

really appriciated

Zeltak

---

### Post by zeltak on 2006-02-13
Hi 

Sorry guys, i found out the problem:

"in some rare cases (I don't believe that this will happen to you, but I am leaving this bit here just in case) the drivers end up installed in the wrong place; they land in /lib/modules/<kver>/ivtv rather than /lib/modules/`uname -r`/ivtv.:

Apparently it isnt that rare LOL...oh well ill continue the install

Zeltak!

---

