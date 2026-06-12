---
title: "keylogger"
date: 2009-01-27
forum: General Help
---

### Post by wbjoly on 2009-01-27
My ex installed and set up my ubuntu os.  I suspect he may have installed a keylogger that sends him an email of my keystrokes or possibly uses Skype to send reports.  Is there a way to check this?

---

### Post by jespdj on 2009-01-27
Welcome to the forums.

There's no fool-proof way to check it, since such a keylogger could be hidden anywhere in the system.

If you're really so concerned about this, then reinstall Ubuntu from scratch on your computer - that's the only way to be sure that there is no malicious software running on your system.

---

### Post by cariboo on 2009-01-27
THere is only one keylogger in the repositories, so in a Applications-->Accessories--Terminal type:

```
ps ax | grep liki
```

If you have just a normal desktop, you shouldn't have a mail server running. Go to System-->Administration-->Network Tools-->Port Scan,
in network address type:

```
localhost
```

Look to see if port 25 is open, if it is, press Alt-F2 and type:

```
gksu nautilus
```

this will open nautilus as root, navigate to File System-->var-->spool-->mail, and check if there are any names other than your own in the directory. You can double click any of the names, and they will open in a text editor, so you can read the mail in the mail box.

If you find anything strange, lets us know.

Jim

---

### Post by wbjoly on 2009-01-27
terminal came up with 
 7483 pts/0    R+     0:00 grep liki


Port scan has open port numbers of 139, 445, 631, 5432, 42958, 54529, and 56912

No port 25

---

### Post by bodhi.zazen on 2009-01-27
If you are concerned about such things I advise you simply re-install Ubuntu.

It is not that hard and we can help, both with data backup or installation if needed.

---

### Post by wbjoly on 2009-01-27
I know you guys can help me reinstall and I may eventually do that but I just want to know if he did do something like that.

---

### Post by niteshifter on 2009-01-27
Hi,

Actually there is a fool-proof way to check this: Monitor the network traffic to/from the box. Wireshark - running on another machine connected to the local network - would be a good choice along with some of the tcpdump analysis scripts available.

But it's not easy, and it's time consuming. Plus, if wbjoly's need for this knowledge is to take legal action in response it really should be done by a neutral third party.

So wbjoly, it's choice between two things: Spend $ and time (days or weeks) to prove what you already know (the ex is a SOB) or just close this chapter, move on and re-install.

---

### Post by wbjoly on 2009-01-27
I'm not looking to take legal action.  I just want to know

---

### Post by cariboo on 2009-01-27
This is probably s stupid suggestion, but if you think the guy is checking up on you, type something that will get him mad and wait for his call. Then administer some Cariboo Justice.

Jim

---

### Post by wbjoly on 2009-01-27
Jim,

Tried that but the issue is that he is generally paranoid anyway so the response was not definitive.  So he general accuses me of things anyway and fishes for info.

---

### Post by bodhi.zazen on 2009-01-27
> **wbjoly said:**
> I'm not looking to take legal action.  I just want to know

Performing forensics (ie checking for a key logger) can be difficult to impossible to detect.

As has been suggested the only way to "know" is to examine the system for irregularities. The process of forensics is quite technical and, no offense intended, if you have to ask it is probably something you will not be able to do without a lot of time, effort, and reading.

This is the kind of thing you are talking about

[http://en.wikipedia.org/wiki/Computer_forensics](http://en.wikipedia.org/wiki/Computer_forensics)

So what are you waiting for ? Image the hard drive and start examining the image.

The problem is that, if your ex installed the system, there are many potential exploits above and beyond a key logger.

---

### Post by SteelCore on 2009-02-09
> **cariboo907 said:**
> THere is only one keylogger in the repositories, so in a Applications-->Accessories--Terminal type:

```
ps ax | grep liki
```

If you have just a normal desktop, you shouldn't have a mail server running. Go to System-->Administration-->Network Tools-->Port Scan,
in network address type:

```
localhost
```

Look to see if port 25 is open, if it is, press Alt-F2 and type:

```
gksu nautilus
```

this will open nautilus as root, navigate to File System-->var-->spool-->mail, and check if there are any names other than your own in the directory. You can double click any of the names, and they will open in a text editor, so you can read the mail in the mail box.

If you find anything strange, lets us know.

Jim

I was reading this post and carried out the instructions.  I found things like:

```
Warning: Hidden directory found: /etc/.java
Warning: Hidden directory found: /dev/.static
Warning: Hidden directory found: /dev/.udev
Warning: Hidden directory found: /dev/.initramfs

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

```
Also many of these warnings:

```
Warning: The file properties have changed:
         File: /usr/bin/perl
         Current hash: 7308c1ae9a71eee0c1c4c1d149ded54ce4a6f66f
         Stored hash : 9c4d220d96fbaf9aaedbe4e034a767e8d510d7f6
         Current inode: 1651578    Stored inode: 1651726
         Current size: 1078096    Stored size: 1078128
         Current file modification time: 1229999605
         Stored file modification time : 1196759924
Warning: The file properties have changed:
         File: /usr/sbin/groupadd
         Current inode: 1655257    Stored inode: 1655097
         Current file modification time: 1228727589
         Stored file modification time : 1226558941
Warning: The file properties have changed:
         File: /usr/sbin/groupdel
         Current inode: 1655268    Stored inode: 1655099
         Current file modification time: 1228727589
         Stored file modification time : 1226558941

```

And:

```
From root@bashar-laptop Sun Jan 04 06:58:26 2009
Return-path: <root@bashar-laptop>
Envelope-to: root@bashar-laptop
Delivery-date: Sun, 04 Jan 2009 06:58:26 +0800
Received: from root by bashar-laptop with local (Exim 4.67)
	(envelope-from <root@bashar-laptop>)
	id 1LJFRq-0007jW-1e
	for root@bashar-laptop; Sun, 04 Jan 2009 06:58:26 +0800
Subject: [rkhunter] Daily run
Message-Id: <E1LJFRq-0007jW-1e@bashar-laptop>
From: root <root@bashar-laptop>
Date: Sun, 04 Jan 2009 06:58:26 +0800
```


Is this normal or do these warnings indicate something wrong?
Thanks

---

### Post by cain171562 on 2009-02-27
If your not doing anything wrong, let him log your keystrokes to his hearts content. Better yet, do something that will generate millions of keystrokes while your not using the computer, then search for recently enlarged log files.

---

### Post by fionnulaqijce on 2011-01-16
> **wbjoly said:**
> My ex installed and set up my ubuntu os. I suspect he may have installed a keylogger that sends him an [[COLOR=#000000]email[/COLOR]](http://www.powdershell.com/bg/press-release/airplay-direct-selects-alexander-shulgin-as.html) of my keystrokes or possibly uses Skype to send reports. Is there a way to check this?Thanks for your instruction! It's good for reference, I understand this part.

---

### Post by sammiev on 2011-01-16
Install a anti-virus program and scan. A key logger would be picked up by the AV. GL :)

---

### Post by bodhi.zazen on 2011-01-16
> **sammiev said:**
> Install a anti-virus program and scan. A key logger would be picked up by the AV. GL :)

Not necessarily, depends on the key logger.

antivirus != keylogger detection.

For example, seee

[http://clamav-du.securesites.net/cgi-bin/clamgrok](http://clamav-du.securesites.net/cgi-bin/clamgrok)

Yes the database lists some key loggers, but not all.

I did not see lkl in the database. I assume this would be because one would install lkl and thus it is not considered a virus.

One "problem" is see is that many people equate "virus" as all forums of malware and I do not think this is true in Windows.

The then think any and every problem they might see is a virus, and that antivirus == security.

Antivirus can not detect zero day exploits and often alerts you to a problem AFTER it has occurred.

---

