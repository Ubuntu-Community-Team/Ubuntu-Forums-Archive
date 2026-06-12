---
title: "What is this?"
date: 2006-02-21
forum: Desktop Environments
---

### Post by ardchoille on 2006-02-21
I spend a lot of time on the command line and anything that makes cli life easier is valuable. I spent some time booted into [SystemRescueCD]("http://www.sysresccd.org") this morning, I like to use partimage to image my hard drive so that I can restore it rather than reinstall the OS in case of a catastrophe. Creating the image with partimage takes about 10 minutes and restoring takes about 15 minutes. 

When I was in SystemRescueCD this morning I noticed that there are some tools on that cd that I'd lke to have in Ubuntu. Here is what I found:

**1)** I have the following files on /dev/hda2 mounted at /mnt/work while in systemrescuecd:

[COLOR="DarkBlue"]-rw-r--r--  1 root root  926533031 2006-02-20 00:33 ubuntu-current00.tar.gz.000
-rw-------  1 root root 3106319139 2006-02-21 04:56 ubuntu-current01.tar.gz.000
-rw-r--r--  1 root root  674234265 2006-02-18 23:17 ubuntu-fresh.tar.gz.000
-rw-r--r--  1 root root  701496077 2006-02-19 11:04 ubuntu-tweaked.tar.gz.000[/COLOR]

Partimage automatically chmods a new image to 600 and I wanted the new image (ubuntu-current01.tar.gz.000) to be 644 so I typed "chmod 644 /mnt/work/u" and pressed the tab key so the cli could print the rest of "ubuntu" out for me (yes, I am that lazy). But instead of printing out the rest of ubuntu for me, it paused a second and then finished the entire filename for me as "ubuntu-current01.tar.gz.000", which you can see from the above list of files is the exact file I wanted to chmod 644. I am guessing that the system looked at the perms of all the files in /mnt/work, saw that all but one were already 644 and gave me the only choice possible, which was to chmod 644 a file that was 600 since I cannot chmod 644 a file which is already 644. What the hell happened? Is this something which is built into current shells? I noticed that I was using zsh instead of bash. Is this a feature of the zsh shell? I noticed that bash on Ubuntu 5.10 doesn't do this. How can I get this feature in bash on my Ubuntu box? This is extremely useful.

**2)** I typed "shurdown -r now" and as you can see there is a typo in that command, there is an "r" where there should be a "t". But, when I pressed the enter key a message came up in the terminal asking me if I wanted to correct "shurdown -r now" to "shutdown -r now" and gave me a prompt waiting for me to type yes or no. What was happening was that the system had caught my typo and asked me if it could corect it for me before carrying out the command. Just out of curiousity I typed "Y" for yes, the system corrected the typo and rebooted like I wanted. What the hell? Systems are spell checking the command line entries now? W00T!!! What is the name of the package that enables spell checking of cli entries and how can I get it on my Ubuntu box? That would make cli life much easier.

Spending some time in SystemRescueCD made me see a few things that make cli life much easier and I want this stuff on my Ubuntu box :)

If the above features are part of zsh, I would like to install it. Does anyone have any experience with zsh? Is it a decent replacement for bash?

---

### Post by ardchoille on 2006-02-22
I found out what I needed to know. The zsh shell has many features, two of which are listed in my original post. This is a nice shell :)

---

### Post by galeron on 2006-02-22
Is the basic syntax the same as in bash? zsh sounds really cool, but I would hate to relearn the syntax all over again

---

