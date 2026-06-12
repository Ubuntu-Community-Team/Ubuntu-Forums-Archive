---
title: "Firefox sucks? Help!"
date: 2009-06-22
forum: General Help
---

### Post by Spaceman7o on 2009-06-22
Currently using firefox 3 on Jaunty and ive noticed its increadably SSLLOOWW ... any ways to speed it up?

---

### Post by dhughes on 2009-06-22
Maybe try reinstalling it or start it from the command line to check for errors when exiting?

---

### Post by Revolutionary101 on 2009-06-22
If you don't like Firefox then you could try Opera. Other than that I don't know any ways to speed Firefox up

To install Opera type this into Terminal

```
sudo apt-get install opera
```

---

### Post by Brandon Williams on 2009-06-22
Try to describe the nature of the slowness in more detail. For example: Does it take a long time to start rendering pages? After it starts renderring pages, does it take a long time for it to finish? If it appears to be stalled at any point in time, what it does it say in the status bar? Try to identify anything that might give us more of a clue as to which part of what it does isn't working well for, and therefore what might be improved.

---

### Post by fooman on 2009-06-22
maybe its just a bad extension/add-on thats slowing it down.

try creating a new profile and see if the new one is any faster.  open a terminal and run this command to load the firefox profile manager:

```
MOZ_NO_REMOTE=1 firefox -P
```

hope that helps.

---

### Post by Spaceman7o on 2009-06-22
> **Brandon Williams said:**
> Try to describe the nature of the slowness in more detail. For example: Does it take a long time to start rendering pages? After it starts renderring pages, does it take a long time for it to finish? If it appears to be stalled at any point in time, what it does it say in the status bar? Try to identify anything that might give us more of a clue as to which part of what it does isn't working well for, and therefore what might be improved.

Its just in general slow takes a long time to load everything including videos and pics etc.

---

### Post by Spaceman7o on 2009-06-22
> **fooman said:**
> maybe its just a bad extension/add-on thats slowing it down.

try creating a new profile and see if the new one is any faster.  open a terminal and run this command to load the firefox profile manager:

```
MOZ_NO_REMOTE=1 firefox -P
```hope that helps.

nah ive only installed any add ons today and ive noticed no change sinse installing them.

---

### Post by fooman on 2009-06-22
> Its just in general slow takes a long time to load everything including videos and pics etc.

do you have flash installed?

if not,  try this in a terminal:

```
sudo apt-get install ubuntu-restricted-extras
```that will install flash as well as some other codecs/fonts/goodies.  then close firefox and reopen it to see if its any better.

---

### Post by lovinglinux on 2009-06-22
Visit [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) and check the Speed Optimization section.

BTW, re-installing Firefox is hardly necessary and only solve issues with broken installations.

---

