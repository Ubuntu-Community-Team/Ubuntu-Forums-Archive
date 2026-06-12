---
title: "Web developer IDE for cross-platform use"
date: 2009-03-29
forum: General Help
---

### Post by napi on 2009-03-29
Hello all,

I was wondering if any one with experience in this area could give me some guidance/advice on an IDE.

I have a laptop (which dualboots Ubuntu and XP) and a Desktop with XP on.

The laptop predominantly uses Ubuntu (keep XP there for few particular bits and bobs). I do a fair amount of web developing, but due to travel requirements, am finding myself wasting more time by not continueing work while 'on the move'.

So I thought; is there a good IDE which provides for php-orientated work, which would be easy to keep sync'd between my laptop and my desktop (and even cooler would be if the stuff on the laptop is accessible by both Ubuntu and XP although this is not required). 

Ideally I'd like a way to do it without having to continuously transfer a folder with a usb stick, but perhaps there is a sync method? (Either built in or as an extra program/app)?

Any thoughts/advice on this would be much appreciated.

---

### Post by cybergalvez on 2009-03-29
> **napi said:**
> Hello all,

I was wondering if any one with experience in this area could give me some guidance/advice on an IDE.

I have a laptop (which dualboots Ubuntu and XP) and a Desktop with XP on.

The laptop predominantly uses Ubuntu (keep XP there for few particular bits and bobs). I do a fair amount of web developing, but due to travel requirements, am finding myself wasting more time by not continueing work while 'on the move'.

So I thought; is there a good IDE which provides for php-orientated work, which would be easy to keep sync'd between my laptop and my desktop (and even cooler would be if the stuff on the laptop is accessible by both Ubuntu and XP although this is not required). 

Ideally I'd like a way to do it without having to continuously transfer a folder with a usb stick, but perhaps there is a sync method? (Either built in or as an extra program/app)?

Any thoughts/advice on this would be much appreciated.

Well here is my 2 cents
I like [komodo]("http://www.openkomodo.com/"), but there are lots of them.  I know that Eclipse has a good following.

so you want to sync your ubuntu laptop with your XP desktop.  My personal experience with this was to install sshd on my XP machine and then just connect from ubuntu to XP either with sftp or with sshfs.  I preferred sshfs because it mounted the XP share much simpler then samba.  Sorry I don't know how program like rsync would work in this situation, but I've heard that the windows implementation of rsync does not work that wall

---

### Post by linorics on 2009-03-29
For all of my PHP work I use NetBeans on my laptop. And I just copy all my stuff to my desktop smb(windows) share. But rsync will do the trick of syncing the files but its kind of techy.

---

### Post by FluffyElmo on 2009-03-29
I second Netbeans for php development. I've also used Komodo and Komodo Edit and liked them. Komodo is commercial though, while Netbeans offers a full range of features for free which tipped the balance for me. 

For synchronizing between machines I suggest that you look into a version control system. You can then synchronize between machines but also roll back the project to an earlier version. I'd suggest Mercurial or Git as they let you commit changes on the go and merge them later, but Subversion may also work.

---

### Post by napi on 2009-03-30
Thanks for the replies all.

Am going to have a look at NetBeans for the IDE, then investigate the various different version control systems available.

At some point in the not-too-distant future I'm going to get a small server at home, so can then use that as the 'hub' for work on the other 2 machines (this makes sense in my head, although likely awful use of the word 'hub'!).

Thanks again.

---

