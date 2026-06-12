---
title: "Avast Found Elf:Suckit"
date: 2009-01-21
forum: General Help
---

### Post by JohnWesleyMethodist on 2009-01-21
Hey all!

 I am sure this is no big deal but I want to confirm that.

 I just installed Avast for Linux, updated and ran a thorough scan. Avast popped up and said a virus was found and so I moved the virus to the chest (I deleted it from the chest now which I probably shouldn't have). Anyway, the virus was found in the cache of firefox, so I am guessing this hasn't infected the computer at all.

 I did see on Google that Planet Ubuntu was showing an article on this particular rootkit and that Windows users some time ago were getting virus warnings from that site.

 Anyway, again, I just want to confirm that something found in the Firefox cache can in no way have infected Ubuntu Intrepid.

 Thanks!

---

### Post by sPiN1 on 2009-01-21
virus' are hard to come by on linux did you download anything you shouldn't have? or something that might have contained it?

---

### Post by mcduck on 2009-01-21
That's most likely a Windows virus (since they are pretty much the only thing Linux virus scanners are searching for, there really are no Linux viruses in the wild)

Since the virus is a Windows program, it will not run on Linux. If you want, you can try to start it using Wine but it definitely will not be able to run on it's own, or without you starting it.

Since the infected file was in Firefox cache you just got it from some web site you have visited. If you were running Windows, you'd now have a virus infection on your computer (unless your Windows antivirus software had been a good one and had detected the virus before it does any damage).

(Running Linux doesn't make viruses magically disappear, you can still get infected files from the Internet, usually as files your internet browser stores in it's cache. It's just that the virus itself doesn't activate or even work in Linux.)

---

### Post by sPiN1 on 2009-01-21
> **mcduck said:**
> That's most likely a Windows virus (since they are pretty much the only thing Linux virus scanners are searching for, there really are no Linux viruses in the wild)

Since the virus is a Windows program, it will not run on Linux. If you want, you can try to start it using Wine but it definitely will not be able to run on it's own, or without you starting it.

Since the infected file was in Firefox cache you just got it from some web site you have visited. If you were running Windows, you'd now have a virus infection on your computer (unless your Windows antivirus software had been a good one and had detected the virus before it does any damage).

(Running Linux doesn't make viruses magically disappear, you can still get infected files from the Internet, usually as files your internet browser stores in it's cache. It's just that the virus itself doesn't activate or even work in Linux.)
because linux is the ******* ****

/endthread

---

### Post by heindsight on 2009-01-21
I just did some quick googling and it looks like Suckit is a linux rootkit...

---

### Post by dagnabit dang doohickey on 2009-01-21
Seems like a good time to post these links:
[chkrootkit]("http://www.chkrootkit.org/")
[Rootkit Hunter]("http://www.rootkit.nl/projects/rootkit_hunter.html")

---

### Post by JohnWesleyMethodist on 2009-01-21
I ran Avast again last night and no further issues.
 I just ran Chkrootkit and no issues
 I am running the much prettier looking Rkhunter -C. It says that Suckit is not found. Obviously nothing to worry about. I just wonder what exactly I got in my cache...

     Checking /dev for suspicious file types                  [ Warning ]

 Just the usual warning with Rkhunter.

 Thanks all!

 Hmm... I can't find the option to set this thread to [Solved]...

---

