---
title: "Jaunty Firefox and Liferea disk thrashing"
date: 2009-04-23
forum: General Help
---

### Post by timzak on 2009-04-23
Problem with a new Jaunty install (64 bit and ext4, if it matters).

The first time I launch Firefox or Liferea, there is a lot of hard disk thrashing, with FF and Liferea being unusable for about 5 seconds or longer until the disk activity is done.  After this initial thrashing, it doesn't happen anymore until I reboot the system.  Liferea is especially bad as it's updating a bunch of feeds for a good couple of minutes it is thrashing and can't be used.

Prior to Jaunty I used 32 bit Hardy and ext3 and never noticed these problems on the same system.

I only see this behavior with Firefox and Liferea.  All other apps seem to be fine.

Any ideas?

---

### Post by timzak on 2009-04-23
Just noticed it does it with Evolution too, so it seems to be related to internet accesses??

---

### Post by timzak on 2009-04-23
Fixed.  See:

[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/fb3f920b91a621e0](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/fb3f920b91a621e0)

I uninstalled the aqbanking and libchipcard files (I use Gnucash but not online banking) and the problem is now gone.  I noticed the chipcardd4 daemon getting lots of cpu cycles and that's how I traced it to the link above.

In case anyone else uses Gnucash, for some reason they made aqbanking a dependency when it doesn't need to be.  Just manually remove aqbanking (if you don't used it) and the *chipcard* files and you should be fine.

---

### Post by abhiroopb on 2009-04-24
> **timzak said:**
> Fixed.  See:

[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/fb3f920b91a621e0](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/fb3f920b91a621e0)

I uninstalled the aqbanking and libchipcard files (I use Gnucash but not online banking) and the problem is now gone.  I noticed the chipcardd4 daemon getting lots of cpu cycles and that's how I traced it to the link above.

In case anyone else uses Gnucash, for some reason they made aqbanking a dependency when it doesn't need to be.  Just manually remove aqbanking (if you don't used it) and the *chipcard* files and you should be fine.

How does this help? I have neither installed...

---

### Post by timzak on 2009-04-24
> **abhiroopb said:**
> How does this help? I have neither installed...

I'm not sure how it helps, but I noticed that whenever I got a bunch of disk accesses that chipcardd4 was at the top of the cpu usage in conky.  Since I didn't recognize chipcardd4, I googled it and found out that it is a daemon that runs in the background somehow allowing online banking to be automated with Gnucash.  Since I use Gnucash, but not for online banking, I removed it.  Once the daemon was not running in the background, the disk accesses were greatly reduced.  I don't understand the hows or whys, but it sounds like a reported bug if you read the link I provided above.

---

### Post by nanbanjin on 2009-04-24
I have the same problem wtih Liferea but not with Firefox since I installed Jaunty Beta with ext4 (32-bit though), I presumed it was an ext4 thing...

---

### Post by timzak on 2009-04-24
> **nanbanjin said:**
> I have the same problem wtih Liferea but not with Firefox since I installed Jaunty Beta with ext4 (32-bit though), I presumed it was an ext4 thing...

Hmmm...is there an easy way to switch back to ext3 to see if ext4 is somehow involved with this?

Although it's a LOT better since I made the change above, it's still noticeable.  Especially when I first open Firefox, then navigate to my first web page.  Before it loads the page, the disk thrashes for a few seconds.  After that initial page load, it doesn't do it anymore for the rest of my session until I reboot the computer.  I'm going to try disabling disk caching in Firefox and see if that helps.

Edit:  search the forums for "Liferea" and you'll find it's a known issue with Jaunty.  There doesn't seem to be a good solution yet.

---

### Post by abhiroopb on 2009-04-24
This is really annoying! Any suggestions for good readers? I've practically tried all the ones in the repos and all of them have some negative somewhere...

Akregator - seems to re-load ALL my feeds every time I restart
Straw - no folders
Blam - no folders
Yarssr - no gui at all!
Firefox extensions (e.g. sage, wizz) - does not load opml file

---

### Post by iamnotthemessiah on 2009-04-24
i found a solution that helps somewhat
add
deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/liferea/ppa/ubuntu](http://ppa.launchpad.net/liferea/ppa/ubuntu) jaunty main

to sources.list and update/install the packages

at first i thought it made no difference, but after a reboot it got a fair bit better. still not as fast as id like but a lot better. this is on 64 bit jaunty with ext4

---

### Post by Vadi on 2009-04-24
Fixed my disk trashing problems by optimizing the sqlite databases they used. In my case, I found [Lita]("http://www.dehats.com/drupal/?q=node/58"), then used it on the .sqlite files for firefox and .db ones for Liferea.

Generally any sqlite database management program should do though

---

### Post by abhiroopb on 2009-04-24
What does that do exactly? And can  you recommend any other such program? Lita seems to be Adobe Air, and that doesn't work to well on my computer.

---

### Post by Vadi on 2009-04-24
No idea to both, sorry. But it did help :/

---

### Post by abhiroopb on 2009-04-27
This is a temporary fix:

enter the following in a terminal:
```

cd /usr/src
mkdir libfsync
sudo gedit libfsync.c

```

Enter the following into the text file:
```

int fsync (int fd) {
 return 0;
}

```

Again in the terminal:
```

sudo gcc -Wall libfsync.c -o libfsync.so -shared -fPIC -Wl,-soname,libfsync.so
sudo gedit /usr/bin/liferea 

```


Enter the following into the SECOND LINE of the text file:
```

export LD_PRELOAD=/usr/src/libfsync/libfsync.so

```

No idea what it does, but it was suggested in the launchpud page and it worked for me ([https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/333718](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/333718)).

---

### Post by timzak on 2009-05-01
Well, it was simple enough to just backup my home, reinstall Jaunty 64-bit with ext3, and now Firefox and Liferea both run so much smoother.  No noticable disk thrashing in Firefox, and very minimal in Liferea.  Ahhhhhh.  I don't know what role 64-bit plays, but definitely ext4 has some issues to be worked out.  It boots oh so fast, but the disk grinding in Firefox was horrible.

I can't believe how fast and easy an alternate install of Ubuntu is. :-)

---

