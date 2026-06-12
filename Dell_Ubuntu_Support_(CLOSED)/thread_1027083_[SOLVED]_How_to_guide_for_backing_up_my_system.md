---
title: "[SOLVED] How to guide for backing up my system?"
date: 2008-12-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by schimschone on 2008-12-31
So I want to create a complete backup of my system (Mini, Ubuntu 8.10, Netbook Remix, with a system and a home partition), and all the little themes, tweaks, and programs I've installed.. so my question is, how?

If I did a complete reinstall after repartitioning my hard drive, I want to be able to plug in a thumbdrive and in a matter of minutes have my system and all of the peripherals just like I left them.. including repositories. 

The only limitation is my relative inexperience with Ubuntu.. I would prefer GUI over command line, but either way a step by step guide would be great.. both describing the backup and restore processes.

Any suggestions?

schim

And if I could test the backup to compare the data to the original, that would be awesome.

---

### Post by magicfab on 2009-01-01
Anyone owning a Mini 9 with Ubuntu should also take a good look at this wiki page:
[https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)

It lists common issues for the Mini 9 with Ubuntu, either pre-installed from factory or installed from an Ubuntu vanilla 8.04.1 CD.

It also has direct links to the documentation that came with the computer in electronic form, as well as links to other community sites, forums and mailing lists.

If you have a specific question about the Mini 9, it is also possible to ask it here:
[https://answers.launchpad.net/dell-mini/+addquestion](https://answers.launchpad.net/dell-mini/+addquestion)

I can't answer all questions here in the forum, but I keep a close eye on questions asked via Launchpad.

Thank you.

---

### Post by schimschone on 2009-01-01
Well magicfab I appreciate your response but I'm not sure how it applies to the wikipage.. this isn't really a problem with my Mini 9 so much as a question of backing up what's on it, and doing the same for my other laptop. I only stated that I was using a mini so that no one would have to ask me what I was on.

Never the less, I found a solution using Quickstart ([http://quickstart.phpbb.net](http://quickstart.phpbb.net)) and I'm very happy with the results.. my only complaint is that it was so easy I didn't really learn anything. However it isn't technically open-source, and if any one knows of another method I'm still open to it.

Thanks anyhow magicfab.. and in advance to anyone who has something to say on the topic.

schim

---

### Post by llamakc on 2009-01-01
Ubuntu has a package in the repositories called "sbackup".

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

### Post by constantinos692 on 2009-01-01
I believe that the one you need is located here. [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)
   I haven't tried sbackup but remastersys works fine for me the last few months. It creates a live CD/DVD that reinstalls your system exactly as it was before. It is very easy to do it. I have done what you want at least 5 time the last few months.
   Just add the repository located at the above url, install remastersys and you are ready for creating the full back up of the system.

---

