---
title: "How to use dosbox in Ubuntu?"
date: 2012-08-13
forum: Emulators
---

### Post by Sarys on 2012-08-13
So how to use it? I know how to use it with Windows but not how to use it with Ubuntu. With windows it's easy just to type mount c c:\.... or mount d d:\ -cdrom
How to do that with Ubuntu???

---

### Post by TheFu on 2012-08-13
There are problably lots of ways to do this. This is the easiest to explain in a forum:
* Open a terminal
* type "dosbox -h"<enter>
* follow the help or instructions.  It says here to type "**INTRO**" for a short introduction. That worked for me. There is information on mounting things inside that intro.

If you need more details, type '**man dosbox**' for the manual page. There is a large section describing how to use the **MOUNT** command with optical drives.  It appears that **'mount -cd**' should be all that is needed, at least on the version I have installed.  '**mount -h**' provided a summary of the command arguments.

Google found this article: [http://www.ubuntugeek.com/howto-auto-mount-a-drive-in-dosbox.html](http://www.ubuntugeek.com/howto-auto-mount-a-drive-in-dosbox.html) with this example
```
 mount d /media/cdrom0 -t cdrom
```
I can't test it now, sorry.

---

### Post by Sarys on 2012-08-16
Okay thanks. But how do I change resolution? Dosbox resolution is smaller in my Ubuntu than in Win7

---

### Post by albandy on 2012-08-16
Take a look at the dosbox wiki, 
[http://www.dosbox.com/wiki/Dosbox.conf#Linux](http://www.dosbox.com/wiki/Dosbox.conf#Linux)

you will see options like fullresolution = width x height | original | desktop

---

### Post by Sarys on 2012-08-16
> **albandy said:**
> Take a look at the dosbox wiki, 
[http://www.dosbox.com/wiki/Dosbox.conf#Linux](http://www.dosbox.com/wiki/Dosbox.conf#Linux)

you will see options like fullresolution = width x height | original | desktop

I already checked that. Didn't help me at all since I have no idea how to find Dosbox config file.

---

### Post by albandy on 2012-08-16
> **Sarys said:**
> I already checked that. Didn't help me at all since I have no idea how to find Dosbox config file.

open your home folder
type crtl+h (this will show hidden files)
go to .dosbox
you will see a file like dosbox-X.YZ.conf

where X.YZ is your dosbox version.

---

### Post by Sarys on 2012-08-16
> **albandy said:**
> open your home folder
type crtl+h (this will show hidden files)
go to .dosbox
you will see a file like dosbox-X.YZ.conf

where X.YZ is your dosbox version.

I think i tried it but I didn't find it...anyway I take a better look first.

---

### Post by albandy on 2012-08-16
> **Sarys said:**
> I think i tried it but I didn't find it...anyway I take a better look first.

OK, by terminal is easier. See the image attached:

---

### Post by Sarys on 2012-08-16
> **albandy said:**
> OK, by terminal is easier. See the image attached:

Okay found it thanks :)

---

### Post by Sarys on 2012-08-30
BTW I'm installing Master of Orion 1+2 from gog and I want to use my dosbox 0.74. But I don't know how to find it from my computer (path)

---

