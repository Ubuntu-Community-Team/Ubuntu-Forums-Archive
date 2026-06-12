---
title: "Show hidden files on desktop"
date: 2011-09-06
forum: Desktop Environments
---

### Post by prisae on 2011-09-06
A question that appears every now and then. However, google and ubuntu forum searches never resulted in a solution - most posts answer how to hide drives from the desktop, and how to show hidden files in nautilus.

BUT MY QUESTION IS:
Is there a way to show hidden files and folders (e.g. '.*' or '*~') on the desktop? Hence not in a terminal nor in nautilus (because there it is no problem), but visually on the desktop.

Many thanks,
Dieter

---

### Post by Linux_junkie on 2011-09-06
View this: [http://ubuntuforums.org/showthread.php?t=1752683](http://ubuntuforums.org/showthread.php?t=1752683)

---

### Post by haqking on 2011-09-06
press Alt+f2

type

gconf-editor


choose desktop/gnome/file_views

then tick show hidden files

this will show all files beginning with a dot .

tick show backup files to show all with a tilde ~

---

### Post by prisae on 2011-09-06
Linux_junkie, I know this thread, and it does not provide a solution! The solution is only for nautilus, not for the actual desktop. The thread is from 2008, that's why I thought I start a new one instead of reactivating the old, unsolved one.

haqking, same here: This makes the files visible in nautilus, but they are still not visible on the desktop.

I made a screenshot with an example: I have two files on the desktop:
.dottest
tildatest~

I can see both in the terminal and in nautilus, but they do NOT appear on the desktop (and they are not behind the terminal/nautilus).

Thanks for your replies. Any other ideas?

---

### Post by haqking on 2011-09-06
> **prisae said:**
> Linux_junkie, I know this thread, and it does not provide a solution! The solution is only for nautilus, not for the actual desktop. The thread is from 2008, that's why I thought I start a new one instead of reactivating the old, unsolved one.

haqking, same here: This makes the files visible in nautilus, but they are still not visible on the desktop.

I made a screenshot with an example: I have two files on the desktop:
.dottest
tildatest~

I can see both in the terminal and in nautilus, but they do NOT appear on the desktop (and they are not behind the terminal/nautilus).

Thanks for your replies. Any other ideas?

oh right.

I remember this popping up before a while back but cant find the thread now.

interestingly enough if you create a file on your desktop whose filename starts with a . it stays visible, in nautilus you wont see it unless you ask it to show hidden files.

are they your files which you created ?

if i create a hidden file in nautilus it shows on my desktop but not in naultius unless i ask it to.

see attachment and you can see the .test on the desktop

---

### Post by prisae on 2011-09-07
haqking,

yes, I created these files on the Desktop, and hit <F5> afterwards. Same result if I create them in nautilus.

Are you sure you can see your created dot-file even after refreshing/F5 your desktop, or logout/login?

Thx

---

### Post by haqking on 2011-09-07
> **prisae said:**
> haqking,

yes, I created these files on the Desktop, and hit <F5> afterwards. Same result if I create them in nautilus.

Are you sure you can see your created dot-file even after refreshing/F5 your desktop, or logout/login?

Thx

yep

---

### Post by prisae on 2011-09-07
Weird. I couldn't make it work on any Gnome desktop I tried, on any machine.

Any other ideas?

---

### Post by haqking on 2011-09-07
> **prisae said:**
> Weird. I couldn't make it work on any Gnome desktop I tried, on any machine.

Any other ideas?

Sorry my bad, worked after f5, not a logout then it dissapeared.

Sorry.

out of interest why the need ?

if they are ones you are creating why need to be hidden ?

---

### Post by prisae on 2011-09-07
More interest than urgent need, really.

I usually have my desktop empty, but quit frequently use it as temporary space to store files or work on something. So it often happens that the file I drop to the desktop is a hidden file and hence 'disappears'. Or the desktop is my standard place where I download files from eg firefox. Or where I extract archives. Simply my working area.

---

### Post by haqking on 2011-09-07
> **prisae said:**
> More interest than urgent need, really.

I usually have my desktop empty, but quit frequently use it as temporary space to store files or work on something. So it often happens that the file I drop to the desktop is a hidden file and hence 'disappears'. Or the desktop is my standard place where I download files from eg firefox. Or where I extract archives. Simply my working area.


ahh gotcha,, yeah i always use the /tmp and its a seperate partition.

my downloads go into ~/Downloads but working is /tmp

---

