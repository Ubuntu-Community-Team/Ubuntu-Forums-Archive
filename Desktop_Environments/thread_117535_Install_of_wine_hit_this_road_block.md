---
title: "Install of wine hit this road block"
date: 2006-01-15
forum: Desktop Environments
---

### Post by nu2this on 2006-01-15
I was configuring Wine after clicking the audio tab this came up:
[IMG]http://img67.imageshack.us/img67/1324/screenshot6dy.png[/IMG]
What is it talking about?:confused:

---

### Post by briancurtin on 2006-01-15
just like it says: install libjack.so

---

### Post by nu2this on 2006-01-15
Fine & dandy how or where? Its not in Synaptic & in terminal igot thisrobbie@emma:~$ sudo apt-get install libjack.so
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libjack.so
robbie@emma:~$
Did I goof?

---

### Post by ronnielsen1 on 2006-01-15
I have this problem too. Hopefully we can find a fix

---

### Post by deNoobius on 2006-01-15
The following libjack files are in the repos:

libjack0.80.0-dev
libjackasyn0
libjack0.71.2-0
libjackasyn-dev
libjack0.80.0-0
libjack-dev

My suggestion would be to install those.

EDIT:  The libjack libraries have to do with allowing multiple programs to connect to an audio device, according to Synaptic.

---

### Post by ronnielsen1 on 2006-01-15
Thank you and everyone who makes up the linux community. Due to frustrations over the virus called windows, i've been windows free for about 45 days. Now if I can get the dvd working in one screen instead of two halves (the same 2 halves), configure the video card better, make runescape load faster and get diablo2 working (my son will be happy) and I'll have a better operating system than Microsloft ever thought about

---

### Post by deNoobius on 2006-01-15
[QUOTE=ronnielsen1]Thank you and everyone who makes up the linux community. Due to frustrations over the virus called windows, i've been windows free for about 45 days. Now if I can get the dvd working in one screen instead of two halves (the same 2 halves), configure the video card better, make runescape load faster and get diablo2 working (my son will be happy) and I'll have a better operating system than Microsloft ever thought about[/QUOTE]

Ronnie, OP:  if any or all of the library files mentioned above solve the Wine problem, can you please post it (it may be helpful to others)?  Also, it could be helpful to others to know which program you were installing with Wine when you ran into this issue.

---

### Post by nu2this on 2006-01-15
For my next dumb questions:
1) I just installed the above mentioned libjack in my case it was libjack0.80.0-dev then in terminal I put in winecfg just the conifure dialog box came up without the error line in terminal, so that means its in right?

2) now that I have wine installed How exactly does it work?

---

### Post by dcstar on 2006-01-15
It is expecting that file, but it really has no effect anyway if it isn't there.

---

