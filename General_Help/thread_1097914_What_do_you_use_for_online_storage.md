---
title: "What do you use for online storage?"
date: 2009-03-16
forum: General Help
---

### Post by agim on 2009-03-16
I have begun using dropbox for collaboration, and adrive as a more static backup, for things like photos, music, and possibly, to backup a partition.

Dropbox has a great desktop app that makes things very easy to sync, and adrive offers 50GB of free storage.

Unfortunately, dropbox is not open source, and when you download the open source package 'nautilus-dropbox', it downloads the dropboxd program, without asking.

I don't think adrive is open source either.

Which is why I have decided to ask what other people are using? What are my alternatives?

---

### Post by agim on 2009-03-18
bump
Someone has to use online storage here...
Right?

---

### Post by jdorenbush on 2009-03-18
I store things with Google... :)

You can use Gspace as well. Which allows your Gmail to be used for file storage.

---

### Post by omegamormegil on 2009-03-19
Check out spideroak.com - free 2GB of storage and native Ubuntu client software which will automate some backup tasks, the service is "zero knowledge" meaning they don't know your password and can't view your data, which is encrypted.  They have plans to make the client open source or free software, probably.  Looks like the best option so far.

---

### Post by mcla0203 on 2009-03-19
I made my own server and plopped a 500gb hard drive in it.

---

### Post by omegamormegil on 2009-03-19
Yes, that is surely one of the best options.  You still need to make sure you have protection for when, not if, your hard drive fails, such as routine data backups or raid.  Even then, however, you are out of luck if you have a fire or another form of physical loss such as theft.  I also have a server for  backups, but I'm looking for something offsite which I can entrust my most important stuff to.

I'd really like to find something I can ssh into, so that I could use sshfs to administer the files.  That would be awesome.

---

### Post by hikaricore on 2009-03-19
Honestly I just send anything important to myself on my Gmail account.
I never have any super important files over 10mb or so.  *shrug*

---

### Post by omegamormegil on 2009-03-19
I have done the same thing in the past.  Recently, however, I've been looking to get out of gmail, for privacy reasons.  

I trust Google so far, but they can read everything in my email.  I'm eventually planning on setting up my own mail server (probably Zimbra) to work towards decoupling myself from google.  

It's not just email either.  They have my documents, they know my schedule (Calendar), and have directions to my house and everywhere else I go (Maps).  They know what I read on a daily basis (Reader), they know who I call (Goog-411).  And of course, they know what I'm looking for online.  Google has far too much access to my personal data.  It's not that I'm paranoid; it's more a matter of not letting the Internet take away my natural privacy, as much as possible.

But I digress.  You could always encrypt the stuff you upload to google.  Or perhaps we could institute some sort of Ubuntu Buddy System.  Each Ubuntu user could have a buddy in a different country who could store encrypted backups of their important documents.  That would fix the whole worrying about a fire issue, eh?

---

### Post by hikaricore on 2009-03-19
Anywhere you store your data it can be viewed by someone if it's unencrypted. :p

---

### Post by omegamormegil on 2009-03-19
Yeah.  That's why I'm looking at spideroak, as all your data is encrypted on their server.  They can't even recover your password if you lose it.  

Just like clipperz.

---

### Post by lisati on 2009-03-19
I have a three external HDDs totalling something like 1000Gb, to store camcorder footage. 

<aside>I must get round to figuring out why one of the three I currently have seems to have been corrupted and what to do about it (no great rush since most of what's on it is a backup of stuff stored elsewhere, and probably the wrong thread for answers to that particular puzzle)</aside>

---

### Post by giarca on 2009-03-19
> **agim said:**
> Unfortunately, dropbox is not open source, and when you download the open source package 'nautilus-dropbox', it downloads the dropboxd program, without asking.

No use for that application, if you use nautilus (and so Gnome) you can connect a server via Places --> Connect to Server preferibly with ssh and then you have access to online folder directly via nautilus.
If you add a bookmark to that new folder you will be able to connect online server just pressing on the bookmark and nautilus connect to the host and to unmount just click on the "eject" button.
Best regards!

---

