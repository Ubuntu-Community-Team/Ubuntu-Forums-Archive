---
title: "Cannot Reboot after update from 9.04 to 9.10"
date: 2009-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by treeclimber on 2009-11-03
I just finished updatung my Dell Inspiron 530/531 from 9.04 to 9.10.  When the computer restarted, the computer showed the Ubuntu logo, then gave me the following message:

init: sreadahead main process (2089) terminated withstatus 1
mountall:/proc/self/mountinfo:no such file or directory
mountall: rootfilesystem is not mounted
init: mountall mainprocess (2079) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminated this shell and re-try.
root@dell-desktop:~#

I tried CONTROL=D.  It did nothing.  I then shut it off and restarted.  I got the same message.  I shut it off again, hit ESC, and got the menu.  It gave me choices of booting onto 8.04 and 8.04 (recovery mode).  Both gave the same message above.

I have no idea what to do next.  I looked on the update forum, but could not find anything like this.  Can anybody help me?

---

### Post by lidex on 2009-11-03
Network install? Did you make sure to update system before upgrade?

You can go into recovery mode using LiveCD and try to fix from there or just boot from the disk and take a look at log files in /var/log directory for clues.

---

### Post by treeclimber on 2009-11-04
Yes, this was using Update Manager.  I ran it several times to get all the updates for 9.04.  But it kept showing like there were updates, but they were whited out and would not let me update.  So I went ahead with the only thing it would let me do, and that was update to 9.10.  Now I can't get in at all.

Which CD should I use?  I have a full install CD for 9.04.  Do I need to make a new CD with 9.10?  Which one?  Are there directions on how to use the CD for this purpose?  I am not very familiar with all this.  This computer is less than 6 months old and actually belongs to my DH.  My laptop installed with no problems.  Any help at all will be appreciated.

---

### Post by treeclimber on 2009-11-04
I should add I am not at home today, so I can't get this done until tomorrow at the earliest.  We have a H1N1 vaccine Clinic today at our health department where I work and I have a 12 hour day today. Yikes!

---

### Post by Bunnybugs on 2009-11-04
Had the same problem with the last updates of Jaunty...

Best is to make a livecd, and recover... or, back up your filesystem, and boot from scratch on the new version(that&#347; what I did, but i wanted to remove widdows)

---

### Post by lidex on 2009-11-04
You can use the disk you have. Check out these guides:
[http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html]("http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html")
[http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/]("http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/")

---

### Post by treeclimber on 2009-11-06
I made a boot CD and booted with that.  There was no rescue choice, like is talked about in the info you gave me.  I can get into the terminal.  What do I put in to get it to make the necessary repairs?

---

