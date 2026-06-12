---
title: "pSX Install Ubuntu 13.04"
date: 2013-07-13
forum: Gaming &amp; Leisure
---

### Post by JavaBeansAndOreos on 2013-07-13
Hello,

I've been trying to install the pSX emulator on Ubuntu 13.04, but I have not been able to get pSX to run. I've followed the instructions from [ this]("http://www.maketecheasier.com/guide-to-playstation-emulator-on-ubuntu/2008/03/19") site.

As instructed:

(1) I've downloaded and untarred the suggested file. It now resides on my desktop.

(2) I've located the bios and placed it into the appropriate bios folder.

But when I get to the "**Activate pSX**" part, I run into trouble. As suggested, I change directories to the file (named pSX) on my desktop. 

Then I type the command:

```

./pSX

```

And I receive the message: 

```

bash: ./pSX: No such file or directory.

```

I've tried the commands:

```

./configure
make
make install

```

With no luck.

As you might expect, I've looked at various threads on this forum and others, but nothing seems to work. Any help is of course appreciated.

---

### Post by JavaBeansAndOreos on 2013-07-13
Disregard. 

Got it to work using Wine.

---

### Post by kostkon on 2013-07-13
That post is ancient. You don't need to compile your software.

Just install *PCSX* using the software centre.

For more info about installing software in Ubuntu, check [this helpful guide here.]("http://http://www.psychocats.net/ubuntu/installingsoftware")

Hope that helps.

---

