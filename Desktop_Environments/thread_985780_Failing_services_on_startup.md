---
title: "Failing services on startup"
date: 2008-11-17
forum: Desktop Environments
---

### Post by hansoffate on 2008-11-17
My computer is taking forever to start up because it waits for 3 different services to time out.

Starting NTP server ntpd [fail]
NFS common utilities {fail}
NFS kernel daemon [fail]

Any ideas on how to fix this?  Are there any logs that I should post?

Thanks,
Hans

---

### Post by hansoffate on 2008-11-30
Any Ideas?  This is starting to get really annoying.  It takes about 5 minutes to boot up because of the failing services.

---

### Post by Presto123 on 2008-12-02
I think I have it. I have been having a similar problem with it lately, so I went in to "System/Administration/Shared Folders" and removed the file (home folder) and left it empty. I then went in to "Add/Remove" and uninstalled ALL remote desktop applications but the Terminal Server Client that comes standard with Ubuntu. All of these remote desktop apps I added in myself because I wanted to get something to work. So, obviously on my end, there was some kind of conflict.

It boots normally now for me. Try it and see.

---

### Post by hansoffate on 2008-12-10
So, I should try to uninstall NTP and NFS?  I am using NFS to share my files with other network computers. 

Bests,
Hans

---

### Post by Presto123 on 2008-12-10
Main question to really answer here is what programs do you have for remote desktops? How many? etc. I wouldn't get rid of NFS and NTP just yet, just get rid of the programs 1st to see if it helps.

---

### Post by rakris on 2008-12-11
For newbies,

Install Boot up manager and remove services you dont want.

package is 'bum' i guess( nto sure)

---

