---
title: "system update hangs"
date: 2007-03-13
forum: Desktop Environments
---

### Post by jmaiolo on 2007-03-13
This is my first experience with Ubuntu, and my first with Linux in a long time.  I just installed Edgy on a fairly old machine (PII, 650 MHz, 128 M ram), and everything seems to work fine except when I try to install the system updates.  Whenever I open the update app, it gets the headers for all the updates (133 of them), but then when I click install, the window is grayed out and the busy cursor comes up.  I've left it that way for several hours, assuming that it was working, but there was no change.  My internet connection is not fast, but it is DSL and it should have been able to download all of the updates during the time I left it.  
At this point I'm thinking of just installing Dapper Drake and hoping that since it is the LTS version it will work more smoothly.
Thanks,
Jim.

---

### Post by daengbo on 2007-03-13
You could have a problem with your repositories, but since there's no error message, we can't know.

Try pulling up a terminal and typing:

sudo apt-get update
sudo apt-get upgrade

inputting your password when requested. Look at the text flowing by and see if there are any errors, then report what you saw.

I'll try to help.

---

