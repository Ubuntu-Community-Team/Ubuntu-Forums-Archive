---
title: "everything was fine until..."
date: 2010-08-08
forum: Desktop Environments
---

### Post by semmtexx on 2010-08-08
I have a desktop with windows xp installed on a 250 gb drive and Ubuntu installed on a 200 gb drive.  I have had the Ubuntu drive running fine until today.  My internet connection is through a wireless router and was working fine until today.  Neither firefox nor chrome will connect to the internetin Ubuntu (Under XP, the internet conn. is fine).  All I get is "resolving host..."  I went into terminal and entered ifconfig, iwconfig and lspci.  I copied the results from the commands into the "Sam notes" application (I think that's what it's called).  Here's what and how my problem started (internet in Ubuntu is the least of my worries!)  I took this note file that I made and exported it as either a html or xml file (I forget what the option is in the notes app) to my 250 gb drive so that I could boot back into XP and have the list of outputs from the commands to post in the forum and ask a question about my connectivity issue.  PROBLEM:  after exporting the note file (xml or html), restarting the machine and booting into windows, It takes about 8 to 10 minutes for windows to completely boot up.  I know for a fact everything was fine and booting up normally before exporting the note.  I can even log off XP and log back in and everything starts up fast.  It's just an initial boot that takes forever.  I deleted the exported note file and still no change.  Like I said, the internet issue is the least of my worries.  Anyone have any suggestions as to why after exporting a file from Ubuntu to the 250 gb XP drive would cause XP to load slow?  Thanks for any help!!

---

### Post by clrg on 2010-08-08
NTFS write access is experimental. Microsoft does not provide the specifications to others, so it has to be reverse-engineered, a painful, slow and improper work. 

I recommend against writing on NTFS partitions from Linux.

If it says "resolving host.." and doesn't get past that, you most likely have DNS problems. Try editing /etc/resolv.conf like so:

```
gksudo gedit /etc/resolv.conf
```

There should be some lines saying "nameserver a.b.c.d". If not, add some, like this:

```

nameserver 8.8.8.8
nameserver 8.8.4.4
nameserver 195.186.1.111
nameserver 195.186.4.111

```

Alternatively, configure the DNS servers with network manager.

---

