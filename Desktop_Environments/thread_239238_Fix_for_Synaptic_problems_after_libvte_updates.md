---
title: "Fix for Synaptic problems after libvte updates"
date: 2006-08-18
forum: Desktop Environments
---

### Post by TravisNewman on 2006-08-18
Thanks to DBO for helping out with this in #ubuntuforums. Here is his solution for those of you who have a broken Synaptic when using Quinn's compiz repos. You have to downgrade to the previous libvte4 package, which also breaks gnome-terminal, and therefore you have to downgrade gnome-terminal as well. Also, libcairo2 needs 1.0.4-0ubuntu1
```
sudo aptitude install gnome-terminal-data/dapper-updates gnome-terminal/dapper-updates libvte4/dapper-updates

sudo aptitude install libfreetype6/dapper-security

sudo aptitude install libcairo2=1.0.4-0ubuntu1
```

This is a good opportunity to remind you all that unofficial repositories are all use-at-your-own-risk. Things like this can break your system, as this past upgrade has done. From what I understand, Quinn has been contacted about this, so wait until further notice to upgrade these packages if you haven't already.

---

### Post by Fass on 2006-08-19
If you are happy with the updates (and have fixed the font issues and all that by recompiling the libfreetype packages) and don't want to downgrade, this got synaptic working for me again:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

A bit hackish, but it works.

---

### Post by trakz on 2006-08-19
> This is a good opportunity to remind you all that unofficial repositories are all use-at-your-own-risk.

... but when we're fortunate enough to have technical god's willing to post quick fixes I for one think the risk is worth it :) 

Thank you.

---

### Post by gibbylinks on 2006-08-19
> **Fass said:**
> If you are happy with the updates (and have fixed the font issues and all that by recompiling the libfreetype packages) and don't want to downgrade, this got synaptic working for me again:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

A bit hackish, but it works.

Once again the superheroes come to the rescue.... Thanks Fass worked a treat

---

### Post by manatlan on 2006-08-19
the solution is here, from this post :
[http://www.compiz.net/viewtopic.php?pid=26830#p26830](http://www.compiz.net/viewtopic.php?pid=26830#p26830)

---

### Post by DBO on 2006-08-19
> **Fass said:**
> If you are happy with the updates (and have fixed the font issues and all that by recompiling the libfreetype packages) and don't want to downgrade, this got synaptic working for me again:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

A bit hackish, but it works.

For the love of all thats unholy... wow.  I originally gave out that hack as a way to temporarly get synaptic working so you could fix the issue.  The new libvte has a new SONAME for a reason people, its not compatible with everything in dapper.  It just so happens that synaptic is one of the more obvious things.  Please downgrade appropriately.  If anyone has any issues or questions on the downgrade procedure please join #ubuntu-xgl on freenode and I will help you there.

---

### Post by Fass on 2006-08-19
> **DBO said:**
> For the love of all thats unholy... wow.  I originally gave out that hack as a way to temporarly get synaptic working so you could fix the issue.

You "gave" it out? News to me, especially seeing as symlinking isn't exactly that revolutionary a thing to think of.

---

### Post by DBO on 2006-08-19
> **Fass said:**
> You "gave" it out? News to me, especially seeing as symlinking isn't exactly that revolutionary a thing to think of.

Yeah I posted it on the compiz forums so a person could fire up synaptic to fix this issue.  That person then brought it over here, if you dont believe me you can check over and compiz.net.  Though perhaps I should have been more precise with my wording, regardless, that symlink fix should NOT be used for anything more than to get synaptic running so you can downgrade those packages.

---

### Post by Fass on 2006-08-20
> **DBO said:**
> Yeah I posted it on the compiz forums so a person could fire up synaptic to fix this issue.  That person then brought it over here, if you dont believe me you can check over and compiz.net.

Oh, I've no doubt you probably wrote something like that somewhere. What I doubt is that you're the only person out there to think of it and that you are the only one it can propagate from, which means I don't quite understand your, for lack of a better word, indignation in your previous post.

> Though perhaps I should have been more precise with my wording, regardless, that symlink fix should NOT be used for anything more than to get synaptic running so you can downgrade those packages.

Synaptic isn't exactly crucial for downgrading, as this thread clearly shows with its (fortunate and worthy of encouragement) use of aptitude.

Nonetheless, some of us like the updates and can see the hack for what it is - a hack. If it causes problems, that will be on us and will be easily rectified. No need for exasperation.

---

### Post by beercz on 2006-08-20
> **Fass said:**
> If you are happy with the updates (and have fixed the font issues and all that by recompiling the libfreetype packages) and don't want to downgrade, this got synaptic working for me again:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

A bit hackish, but it works.
Brilliant Fass!! Worked a treat.  Thanks for this.

---

### Post by cptjaben on 2006-08-20
Thanks, this thread cured my problem as well.

---

### Post by krang on 2006-08-20
> **Fass said:**
> If you are happy with the updates (and have fixed the font issues and all that by recompiling the libfreetype packages) and don't want to downgrade, this got synaptic working for me again:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

A bit hackish, but it works.

Nice, thank a lot.

Will there be a fix in coming versions to this? I dont like links all the way over my OS... ;)

---

### Post by mrgnash on 2006-08-20
The downgrade method in the first post works **without** symlinking -- which is always preferable. Hopefully a fix will be released soon so that we can upgrade to the latest versions again :(

---

### Post by DBO on 2006-08-21
> **Fass said:**
> Oh, I've no doubt you probably wrote something like that somewhere. What I doubt is that you're the only person out there to think of it and that you are the only one it can propagate from, which means I don't quite understand your, for lack of a better word, indignation in your previous post.



Synaptic isn't exactly crucial for downgrading, as this thread clearly shows with its (fortunate and worthy of encouragement) use of aptitude.

Nonetheless, some of us like the updates and can see the hack for what it is - a hack. If it causes problems, that will be on us and will be easily rectified. No need for exasperation.

I really dont feel like fighting with you.  I was never trying to imply that others wouldnt come up with the same stupid hack, just that I regret being partly responsible for its continued propagation.  Though, upon a further reading, it does kind of come off that way, I am sorry about that, not much I can do though.  You can now continue your worthless rampage at a poorly worded post, or if you wish to have a chat on the matter I am almost always available on freenode.  I consider this matter closed now.

Regardless, the further propagation of this hack should be stopped, which is the primary purpose of this thread.  You are correct in one thing though, you are perfectly welcome to continue to use it, but telling new users who might not know how to downgrade is just bad policy.  So please, stop it.

---

### Post by xinix on 2006-08-21
for those who have applied the hack.  What's the best way to correct this?  Downgrade libvte and remove the symlink?

---

### Post by Uncle Spellbinder on 2006-08-21
```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

Is this a bad thing to keep or should it be un-done so it can be corrected by future updates? If it needs to be un-done to allow future updates to correct the original problem, how can I ud-do it?

---

### Post by lazyd2 on 2006-08-21
After downgrading I can only get synaptic and terminal to work if I do
```
sudo ln -s /usr/lib/libvte.so.4.5.1 /usr/lib/libvte.so.4
```:-k

---

### Post by DBO on 2006-08-21
> **lazyd2 said:**
> After downgrading I can only get synaptic and terminal to work if I do
```
sudo ln -s /usr/lib/libvte.so.4.5.1 /usr/lib/libvte.so.4
```:-k

thats fine, so long as the SONAME is the same.  The downgrade instructions need to be applied with some common sense of course since aptitude will present you with options.  Nine time out of ten the first one is not the one you want with this particular downgrade, it should have put in that symlink on its own, but no matter, put it in yourself.

---

### Post by lazyd2 on 2006-08-21
> **DBO said:**
> thats fine, so long as the SONAME is the same.  The downgrade instructions need to be applied with some common sense of course since aptitude will present you with options.  Nine time out of ten the first one is not the one you want with this particular downgrade, it should have put in that symlink on its own, but no matter, put it in yourself.Ok then :)

---

### Post by Chris Anckaert on 2006-08-21
Good stuff guys! I had Synaptic as well as gnome-terminal not working anymore, all for that bit of 3D which after all turns out to be more of a nuissance than anything useful.
Thanks a lot for helping me restore my system to a working level!

Chris.:D

---

### Post by gibbylinks on 2006-08-21
> **Fass said:**
> If you are happy with the updates (and have fixed the font issues and all that by recompiling the libfreetype packages) and don't want to downgrade, this got synaptic working for me again:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

A bit hackish, but it works.

Ok so I did this when I should have downgraded. Would somebody like to tell us mere mortals how to unde the link.

Thanks

---

### Post by tmtjjhnsn on 2006-08-21
1

---

### Post by tmtjjhnsn on 2006-08-21
> **panickedthumb said:**
> Thanks to DBO for helping out with this in #ubuntuforums. Here is his solution for those of you who have a broken Synaptic when using Quinn's compiz repos. You have to downgrade to the previous libvte4 package, which also breaks gnome-terminal, and therefore you have to downgrade gnome-terminal as well. Also, libcairo2 needs 1.0.4-0ubuntu1
```
sudo aptitude install gnome-terminal-data/dapper-updates gnome-terminal/dapper-updates libvte4/dapper-updates

sudo aptitude install libfreetype6/dapper-security

sudo aptitude install libcairo2=1.0.4-0ubuntu1
```

This is a good opportunity to remind you all that unofficial repositories are all use-at-your-own-risk. Things like this can break your system, as this past upgrade has done. From what I understand, Quinn has been contacted about this, so wait until further notice to upgrade these packages if you haven't already.



Okay, I tried that, and now my Synaptic still won't work, AND I and can not open a terminal.  Any suggstions?  ](*,)

---

### Post by DBO on 2006-08-21
> **tmtjjhnsn said:**
> Okay, I tried that, and now my Synaptic still won't work, AND I and can not open a terminal.  Any suggstions?  ](*,)

when you use those aptitude commands you should make sure that it isnt displaying a message along the lines of keep the following packages at their current version, otherwise weird stuff will happen (you will get partially downgraded).  It sounds to me that either your libvte didnt get fully downgraded or your gnome-terminal didnt.

gibbylinks, to undo the link just sudo rm /usr/lib/libvte.so.4

---

### Post by tmtjjhnsn on 2006-08-21
> **DBO said:**
> when you use those aptitude commands you should make sure that it isnt displaying a message along the lines of keep the following packages at their current version, otherwise weird stuff will happen (you will get partially downgraded).  It sounds to me that either your libvte didnt get fully downgraded or your gnome-terminal didnt.

gibbylinks, to undo the link just sudo rm /usr/lib/libvte.so.4

Okay, thanks.  But, what do I do, now?

---

### Post by gibbylinks on 2006-08-22
> **DBO said:**
> 
gibbylinks, to undo the link just sudo rm /usr/lib/libvte.so.4

Thanks DBO

---

### Post by DBO on 2006-08-22
> **tmtjjhnsn said:**
> Okay, thanks.  But, what do I do, now?

you hop on #ubuntu-xgl on freenode and we can work it out there =)  Things will go much faster/smoother if I can talk to you directly.

---

### Post by anasofiapaixao on 2006-08-22
> **Fass said:**
> What I doubt is that you're the only person out there to think of it and that you are the only one it can propagate from, which means I don't quite understand your, for lack of a better word, indignation in your previous post.

Nonetheless, some of us like the updates and can see the hack for what it is - a hack. If it causes problems, that will be on us and will be easily rectified. No need for exasperation.

You realize you are BOMBARDING against a new user who just got happy to a) be the first to figure something out and b) having people thankful for that? I would react the same way for sure. No need for harshness.

For the sake of non-flaming I'd better say nothing except for: Believe I am still in doubt about whether this post should be reported or not.

---

### Post by Fass on 2006-08-23
> **anasofiapaixao said:**
> You realize you are BOMBARDING against a new user who just got happy to a) be the first to figure something out and b) having people thankful for that? I would react the same way for sure. No need for harshness.

I respectfully disagree with your claim that it is "bombarding" someone to tell them politely that you do not understand the indignation aired in their initially quite confrontational posts and that there is no need for exasperation. No flames were uttered, no offence was taken by me, no offence was meant either, nor any sarcasm or causticity. So, lo, there was indeed no need for exasperation. Not then, not now.

---

### Post by slibuntu on 2006-08-23
You sir, Mr Thumb, are a god amongst men, thank you thank you thank you! I'd been pulling my hair out about that and you solved in two seconds! Again, thank you!

---

### Post by ubuntu_demon on 2006-08-24
I linked to this thread in the "installation and upgrade help" sticky :

READ THIS FIRST prior to posting/upgrading/installing - IMPORTANT links
[http://www.ubuntuforums.org/showthread.php?t=232037](http://www.ubuntuforums.org/showthread.php?t=232037)

---

### Post by TNBY963 on 2006-08-24
This worked for me. Just had to make sure aptitude was DEgrading everything.

Thanks!!!

---

### Post by eyesonly on 2006-09-04
Unfortunately I am getting nowhere with updates and python problems here is what I see

jbs@jbs-ubuntu:~$ gksudo update-manager
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 71, in ?
    app.main(options)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 749, in main
    self.fillstore()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 599, in fillstore
    self.initCache()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 716, in initCache
    self.cache._depcache.Init()
SystemError: E:The package mfc8420lpr needs to be reinstalled, but I can't find an archive for it.
jbs@jbs-ubuntu:~$                  

I could use some help.........

Thanks

---

### Post by alexis259 on 2006-09-07
coment on fait you create yor terin???

---

### Post by eyesonly on 2006-09-07
I really am lost with the update problem.  This what happens when I try the commands.

Can anyone point me in the right direction for a fix?????????

jbs@jbs-ubuntu:~$ sudo aptitude install gnome-terminal-data/dapper-updates gnome-terminal/dapper-updates libvte4/dapper-updates
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  amarok amarok-engines amarok-xine bind9-host dnsutils imagemagick
  libbind9-0 libdns21 libisc11 libisccc0 libisccfg1 libkrb53 liblwres9
  libmagick9 libmysqlclient15off libssl0.9.8 libtag1c2a libtagc0 libtheora0
  libxfont1 mysql-common openssl xserver-xorg-core
0 packages upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the mfc8420lpr package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
jbs@jbs-ubuntu:~$
jbs@jbs-ubuntu:~$ sudo aptitude install libfreetype6/dapper-security
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  amarok amarok-engines amarok-xine bind9-host dnsutils imagemagick
  libbind9-0 libdns21 libisc11 libisccc0 libisccfg1 libkrb53 liblwres9
  libmagick9 libmysqlclient15off libssl0.9.8 libtag1c2a libtagc0 libtheora0
  libxfont1 mysql-common openssl xserver-xorg-core
0 packages upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the mfc8420lpr package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
jbs@jbs-ubuntu:~$ sudo aptitude install libcairo2=1.0.4-0ubuntu1
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  amarok amarok-engines amarok-xine bind9-host dnsutils imagemagick
  libbind9-0 libdns21 libisc11 libisccc0 libisccfg1 libkrb53 liblwres9
  libmagick9 libmysqlclient15off libssl0.9.8 libtag1c2a libtagc0 libtheora0
  libxfont1 mysql-common openssl xserver-xorg-core
0 packages upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the mfc8420lpr package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
jbs@jbs-ubuntu:~$ sudo synaptic
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory
jbs@jbs-ubuntu:~$

---

### Post by cyclone on 2006-09-11
im new to this but i have a synaptic problem as well heres the error i get.
  

ype 'http://ubuntu-backports.mirrormax.net/' is not known on line 39 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by mycelo on 2006-09-13
Yet another stick support thread not clear enough for noobs. I'm having error messages in apt-get since yesterday and I can't say that it's related to the issue discussed here at all.

Hell, do you think that I even pay attention to which things were updated in my last upgrade? I'd never remember that bunch of wacko mnemonics, not to mention their geeky version numbers. ;)

Anyway, I'm having this:
```
Fetched 13.4kB in 6s (2063B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.bz2  MD5Sum mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```
And I'd like to know if the solution(s) presented here apply to my case.

Regards,

mycelo

---

### Post by d2vge on 2006-10-02
I made the mistake of trying the "hackish" fix first, but it just made my terminal stop working. The fix in the original post worked, though, even though I'm a total newbie and had no idea what I was doing.
Thanks!

---

### Post by d2vge on 2006-10-04
Okay, so that worked, but now Update Manager and Synaptic aren't working (but Add/Remove is...) A window opens saying "Starting Administrative Application" but then it disappears.
Any ideas? :???:

---

### Post by dannyboy79 on 2006-10-04
i had that happen before, i forgot what I did, i know i shut down and restart but other than that not sure? I would also like to point out that this thread hasn't been accessed for over 3 weeks. it usually is good to start your own thread I would think. i could be wrong though. good luck.

---

### Post by justinj100 on 2006-10-05
I am using Kubuntu and this did not fix mine :-(

Any ideas how?

---

