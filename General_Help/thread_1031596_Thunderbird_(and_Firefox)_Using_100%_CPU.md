---
title: "Thunderbird (and Firefox) Using 100% CPU"
date: 2009-01-05
forum: General Help
---

### Post by ooolongT on 2009-01-05
I am running Intrepid, Thunderbird 2.0.0.18 and Firefox/3.0.4, and this problem is killing me.  Thunderbird uses ~100% of my CPU whenever I do anything with it! 

If I launch it, it sucks up 100% CPU for ~2 minutes while it is loading and I can not do anyhting else until it is done.  If it is running but I am working on something else, and then try to bring up the TB window, all of a sudden CPU goes to 100% and I get a lag.  If I am trying to change some preferences BAM! 100%.  Sometimes, even if all I am doing is moving from one message to another Woosh! 100%.  Other times, like right now, it is just chilling in the background and it is using up 100%.  

I have searched the forums here and have seen plenty of people asking about similar issues, and they get some advice, but no solution ever presents itself - most of the threads go nowhere.  Most of the bugs filed  with Ubuntu and Mozilla seem to get ignored.  For me this is an Ubuntu deal breaker.  If I can not move quicky around my OS, it makes no sense for me to continue to use it. 

I have tried using Evolution, but it simply does not meet my needs. 

Yes, I mentioned FF before, but Epiphany seems to be a reasonable work around for that right now, so I would like to focus on fixing this issue in TB.  However, I am open to FF suggestions as well! 	
](*,)

---

### Post by MusicMastaMike on 2009-01-05
Try running them from a terminal: Applications>Accessories>Terminal, then type either firefox or thunderbird.  See if any error messages present themselves.  If you see some error messages, post them up here, please.

---

### Post by ooolongT on 2009-01-05
No complaints about either application in the terminal window upon launch nor on shutdown of the applications.  However, when I launch TB, I do get a pop-up from it that says "Connection to server localhost timed out"  I just click ok on it and it seems that it will continue doing what it should do. 

I should tell you that these issues are on my home machine and all of my email is POP email - several Hotmail and Gmail accounts I have using the WebMail plugin.

I also was watching htop while they were launching and running, and as suspected, they were resource hogs when launching, and tbird remained at the top after launch, but FF seems to have sat there at the 3rd or fourth position even though it was doing nothing.  # 2 most of the time was this:

root [...] /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
where [...] is several columns of informaiton

I do not know if that helps at all, as I can not discern what the heck that is. 

Thanks for your help!

---

### Post by ooolongT on 2009-01-05
One other thing I should mention: This machine dual-boots with Windows XP.  I do not have these problems in XP.

---

### Post by MusicMastaMike on 2009-01-05
Well I'm not sure about your original issue now.  That error message you get in tbird, though, is from Hotmail.  Go to the Hotmail website and log in, then try tbird again.  They've been making some changes to the site that require you to login and click through some initial info pages before getting to your e-mail.  Sorry I can't help more.

---

### Post by ooolongT on 2009-01-05
I appreciate the help you have given me.  Anyone else?

---

### Post by ooolongT on 2009-01-07
Bump

---

### Post by joval on 2009-03-16
In my case, I was accessing my mailbox via IMAP, and found that the INBOX.msf was just too large ~4MB, which included hundreds of "deleted" emails, and TB was allocating > 1.2GB RAM!

Removing this file, forced TB to regenerate it and solved all my problems.

---

### Post by ooolongT on 2009-03-17
Thanks Joval, since originally posting this, I have changed my primary applications since I could not get these two working.  Now, I am using epiphany and Kontact on my Linux box.  Both are much lighter weight and while they are not as feature rich (hence the lighter weight) what I have discovered is that I really don't need all the plug-ins and what-not I was using before if the core functionality works!

So, my advice to anyone reading this thread and experiencing the same problems, is to switch apps.  It is a lot easier than you think and you will learn a lot about how these things work in the process.

---

