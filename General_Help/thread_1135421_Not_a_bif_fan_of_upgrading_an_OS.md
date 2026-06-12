---
title: "Not a bif fan of upgrading an OS"
date: 2009-04-24
forum: General Help
---

### Post by dardack on 2009-04-24
So with that said, what can I keep that will keep my bookmarks/wine settings/rythmbox settings/ so I can do a fresh install and just copy this stuff to it?

Oh I also run dansguardian, can I just keep the exception lists for whitelisting?

---

### Post by kanikilu on 2009-04-24
All your personal settings should be in your home directory, usually as "dot" files or folders (for example, .mozilla/ has your firefox profile). Either back these up individually, or just take the entire directory (/home/username).

I haven't used dansguardian, but I think the conf file is in /etc/dansguardian/

---

### Post by dardack on 2009-04-24
Ok i know the dansguardian is in /etc/dansguardian, as for the home directory if i just copy that back over after the install would I run into issues?

Kinda nervous want to try 64bit and Jaunty but I have everything set up like perfectly.  Just hear ext4 and 64 bit are much faster, would love to check it out.

---

### Post by kanikilu on 2009-04-24
I don't think you'll necessarily run into issues restoring your entire home directory, that's why a lot of people put /home on a separate partition. Plus, as long as you keep your backup around for a while, if something does go pear-shaped, just remove the configuration that you restored for it and let the program in question create a new one...

Even though I backup my entire home directory, personally, I selectively restore my configuration ("dot") files and folders - for instance, Firefox, Thunderbird, Pidgen, etc.

I've been using ext4 for a couple weeks with no issues on 3 computers.

As for 64 bit, I still use the 32 bit version because in my experience, there are still a lot of workarounds and hoops I'd have to jump through to get the applications that I use working.

Plus, I don't really see the point of using something like dpkg's --force-architecture or getlibs if you're just going to end up using 32 bit applications and libraries.

The notable exception to this is if you have 4GB+ of RAM and want to be able to address all available memory, in which case 64 bit is necessary.

---

### Post by tom56 on 2009-04-24
Upgrading is much better tested than re-installing using the same /home, so I would recommend upgrading using Update Manager.

---

### Post by dardack on 2009-04-24
> **tom56 said:**
> Upgrading is much better tested than re-installing using the same /home, so I would recommend upgrading using Update Manager.


Yea but what about the benefits of ext4?

---

### Post by cariboo on 2009-04-24
To upgrade from ext3 to ext4 have a look at this [thread=1118295]howto[/thread]

---

### Post by dardack on 2009-04-24
> **cariboo907 said:**
> To upgrade from ext3 to ext4 have a look at this [thread=1118295]howto[/thread]

Thank you.  So if I delete some of the files and copy over backups to the newly formed ext4 they will benefits from the performance of ext4?  Even tho the drive was originally formated as ext3?

---

### Post by oldos2er on 2009-04-24
> **dardack said:**
> Kinda nervous want to try 64bit and Jaunty but I have everything set up like perfectly.  Just hear ext4 and 64 bit are much faster, would love to check it out.

 There is no upgrade from 32-bit to 64-bit. If you want to try 64-bit, you'll need to do a fresh install.

---

### Post by fcuk112 on 2009-04-24
just as an aside - why not use delicious for your bookmarks?  it saves you from having to back them up all the time.

---

