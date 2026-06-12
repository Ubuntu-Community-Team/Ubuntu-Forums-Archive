---
title: "show file transfer status for USB stick?"
date: 2006-03-07
forum: Desktop Environments
---

### Post by sv!en on 2006-03-07
I have the following problem when working with USB sticks (via USB 1) under Ubuntu:

When I copy files bigger than just one or two MB to the stick, the file manager shows the symbol for the copied file immediately on the stick, but there is no indication of how long the copying takes. Sometimes I even have the impression that the copying does not start immediately, as also the stick does not show any activity -- it seems to me as if the file transfer is scheduled internally for a later time.

Even when I unmount the stick via its Desktop symbol, Ubuntu makes it appear that the device is immediately unmounted, but when I remove the stick from the USB port, a warning appears that the file system is missing and that there are still files to be copied.

Is it possible to make Ubuntu behave like this: (?)
[LIST]
[*]When I move files to the USB stick via the file manager, the reading/writing is done as soon as possible. 
[*]As long as the reading/writing is not completed, a message/progress bar/whatever shows that there is still work being done to the file system.
[*]When I decide to unmount the stick as long as the files are not completely moved or copied over, a message/warning/... tells me I still have to wait before I remove the stick from the USB port.
[/LIST]

Thank you very much in advance for any help!
Sv!en

---

### Post by ppd on 2006-03-07
See this script, it gives you a progress bar when unmounting: [http://home.arcor.de/guenter.federle/ubuntu/install](http://home.arcor.de/guenter.federle/ubuntu/install)

Max

---

### Post by gibson on 2006-03-07
after copying a large file, i would recommed opening a terminal then

> sync

this will write all changes in memory to the physical disc.

---

### Post by sv!en on 2006-03-08
**edit: problems partly solved, the script works now. please see next post.**

Hi Max,

Thanks for your reply!

[QUOTE=ppd]
  See this script, it gives you a progress bar when unmounting:   
  [http://home.arcor.de/guenter.federle/ubuntu/install](http://home.arcor.de/guenter.federle/ubuntu/install)

  Max
[/QUOTE]

I have got your script, it ran (sudo-ing) without any failure message but it did not change anything: Even after a reboot, the problem is still the same. Unmounting the USB stick makes the symbol disappear from the desktop without further mention, and the USB stick happily blinks its 'working'-blink for some more time.

The terminal reads the following after install:
```

user@laptop:~$ sudo ./install
Password:

install/uninstall/exit?
install

*****************************************
* gumount Installer                     *
*****************************************
Ubuntu  : breezy
Temp dir: gumount/
Language: English
Version : nice

Generate temp sources.list
Load gumount.c
user@laptop:~$

```
Is it possible that the install is not complete (even though there is no error message)?

**gibson**, thanks also for your reply ... I know about sync, but, honestly, I do not use one of the most userfriendly linux desktop distributions to resort to the terminal every time I use my USB stick. (Apart from the fact that I would forget it every once in a while ...) Sorry, I don't intend to be rude, but in my eyes this is not an option on the longer term.

(My problem with this is also that I am currently setting up a laptop with Ubuntu for somebody else, and as I expect him to use USB sticks quite frequently, I need a solution that is as bulletproof as possible as he is no linux expert.)

Sv!en

---

### Post by sv!en on 2006-03-10
Hi,

It works now. I had to correct a typo in the script: In line 14, there is an "_" missing (marked red in the following line):
```

FILE="http://home.arcor.de/guenter.federle/ubuntu/gumount_english[COLOR="Red"]**_**[/COLOR]"$VERSION".c"

```

There were two other, minor problems: 
I did not realize at first that I had to change the Permissions to "executable", and I did not have dpkg-source installed, so I had to apt-get the package **dpkg-dev**, before it really worked.

I have saved the output of the script, there were quite a number of warnings -- do I have to care about them? (The forum machine refused to include the log text, otherwise I would have included it.)

Furthermore, the update manager now refuses to update the packages
```

  libgnomevfs2-0
  libgnomevfs2-0-dbg
  libgnomevfs2-common
  libgnomevfs2-dev

```
It advises me to use **apt-get dist-upgrade**, but even this (and even after reloading the package lists) keeps back these four packages. Do I have to care about that?

However, thank you very much for your help, the warning message for the USB stick seems to work perfectly!

Sv!en

---

### Post by kaamos on 2006-03-10
>     * When I move files to the USB stick via the file manager, the reading/writing is done as soon as possible.
    * As long as the reading/writing is not completed, a message/progress bar/whatever shows that there is still work being done to the file system.

I think it would be the simplest to add a line to fstab with the option "sync".. Has someone more knowledgable a comment on this?

---

### Post by sv!en on 2006-03-10
Hi kaamos,

Since my first post, I have found some discussions on this problem in general: USB sticks have a limited number of possible write-cycles and are (as of USB1) of limited speed. This is why they are mounted 'async', which makes the filesystem keep data in temporary places before actually saving them to a USB stick. I did not have this problem present in mind when I wrote the first post.

It might be different for others, but for me the solution with **gumount** (which is installed by the script **ppd** has posted) is just perfect. gumount produces a warning/message that tells the user to wait until the data is sync'ed, and shows a progress bar for the writing progress.

---

