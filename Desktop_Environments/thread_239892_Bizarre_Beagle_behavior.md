---
title: "Bizarre Beagle behavior"
date: 2006-08-19
forum: Desktop Environments
---

### Post by Hikaru79 on 2006-08-19
So I gave Beagle a try, and it installed with no problems. however, it's showing some very bizarre behaviour.

I wish I could say it was not indexing, but it is. However, it seems to be very selective in what it indexes. Let me give you two screenshots for an example:

[http://ubuntuforums.org/attachment.php?attachmentid=14574&d=1156045938](http://ubuntuforums.org/attachment.php?attachmentid=14574&d=1156045938)

[http://ubuntuforums.org/attachment.php?attachmentid=14573&stc=1&d=1156031191](http://ubuntuforums.org/attachment.php?attachmentid=14573&stc=1&d=1156031191)

Look at the first screenshot. It seems okay, right? It saw 'd' in the Test file, and showed it. The only thing Test contains is 'a d'. However, in the second screenshot, i searched for 'a' and it finds nothing! It does this with other files too. In smb.conf, it finds 'd' but not the word 'panic'. It finds 'smb.c' but not 'smb.conf' even though the file is named smb.conf. Basically, the index is almost completely random.

Note that inotify DOES work, but only for the searches I mentioned. I've followed the ubuntu installation instructions that tell you to check/uncheck the "index home directory' box. And I've even deleted the index and had beagled rebuild it. Nothing helps.

This is totally bizarre. Any suggestions?

PS: By the way, in case this has anything to do with it, this Ubuntu is running in a VMWare Virtual Machine. I don't know why this would matter, but in case it does.

Thanks :D

---

### Post by Hikaru79 on 2006-08-19
An interesting note -- while I was writing that post, I saved the screenshots to the desktop as 'a.png' and 'd.png'. Beagle finds d.png perfectly, but has nothing on a.png ...

It has had ample time for indexing, there's only about 10 files in my home directory, and I've given it a very long time to index. I could index faster if I was writing down the files on a piece of paper with my left hand.

Another example -- searching for 'e' returns Synaptic Package Manager, but if I search for 's' or 'er' or any other substring of "Synaptic Package Manager", it doesn't find anything.

---

### Post by kerry_s on 2006-08-20
Have you tried the deskbar? It's a part of gnome so its already installed(right click panel>add to panel>(accessories)deskbar). It's got a few features(right click preferences) but i only use 7, you can search the web,open web url's,dictionary,search files and folders,launch programs,run commands...there's also a few things that are part of google, for instance if your using google as your main search engine you can do math,money conversion...I'm still finding features, here's my search order->

---

### Post by HanZo on 2006-08-21
have similar problems... beagle seems to be quite selective in how it searches and shows search results: I have 3 files with similar names:
lapaqui.ttf, paquita.sfd and paquita.ttf, if I type "paqui" in beagle it only shows paquita.sfd, if I type "paquita", it shows the lasyt two, but to see the first one I have to type "lapaqui". I noticed that I usually have to type the whole name of a file to get beagle to find it, ex: if I want to find somestuff.txt I have to type somestuff, just some or stuff won't do.
That's not what I call a very useful search app though... or am I just not getting it?

---

### Post by rossinio on 2006-09-04
I have exactly the same problem, its very selective in what it finds (whcih makes it pretty worthless). It can find some things but couldnt find EVE_4557.exe even when i typed it in directly.. and thats located in /home/myname/

...

is there a way of deleting beagle completely and reverting to searching using "old" way in gnome? wanted to delete it but trying to delete beagle-libs or something with synaptic asked me to delete ubuntu!

---

### Post by ryan on 2006-09-07
beagle has worked very well for me it seems that recently it will index my mail but not files and not Tomboy or Gaim ( see below) or "indexing service ". Is there a way to set the indexing flag from "false" to "true" ?

ryan@ubuntu:~$ beagle-status
ryan@ubuntu:~$ beagle-index-info
&#65279;Index information:
Name: EvolutionDataServer
Count: 121
Indexing: False

Name: EvolutionMail
Count: 26877
Indexing: True

Name: KMail
Count: 0
Indexing: False

Name: Files
Count: 20732
Indexing: False

Name: GaimLog
Count: 712
Indexing: False

Name: IndexingService
Count: 0
Indexing: False

Name: Tomboy
Count: 21
Indexing: False

Name: Blam
Count: 0
Indexing: False

Name: Liferea
Count: 0
Indexing: False

Name: Akregator
Count: 0
Indexing: False

Name: KonquerorHistory
Count: 2
Indexing: False

Name: Kopete
Count: 0
Indexing: False

Name: applications
Count: 153
Indexing: False

Name: documentation
Count: 3609
Indexing: False

Name: windows
Count: 0
Indexing: False

---

