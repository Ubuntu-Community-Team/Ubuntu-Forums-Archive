---
title: "Is Ubuntu secure for my data ?"
date: 2006-07-11
forum: Desktop Environments
---

### Post by Me! on 2006-07-11
That is my question , Is This Ubuntu Secure and strong enough to keep my Data in safe place ?:rolleyes: 

we are on the Internet , My Computer is on the Internet 24 Hours. there is many intruders want to attacking other PCs.:twisted: 

So how can I make sure that my data in safe side ??:-k 

Thanks for all Ubuntu Developers & Users:D

---

### Post by T700 on 2006-07-11
1.  Run a firewall and/or a NAT enabled router.

2.  Keep updated on patches.

3.  Keep backups of your data.

4.  Physically secure the PC.

5.  Don't willy nilly install software from unknown sources.

6.  Set a strong password.

Do these things and unless the NSA or some similar agency is after your data, you'll be fine.

Paul

---

### Post by nanotube on 2006-07-11
> **T700 said:**
> 
Do these things and unless the NSA or some similar agency is after your data, you'll be fine.

Paul

all excellent suggestions.
and if the NSA is after your data, you should put it in a truecrypt encrypted volume. see [www.truecrypt.org](www.truecrypt.org) :)

---

### Post by ironfistchamp on 2006-07-11
Damn the NSA... no I didn't say that but that TrueCrypt thing looks damn secure. Great for a paranoid freak like me :D

---

### Post by T700 on 2006-07-11
> **nanotube said:**
> all excellent suggestions.
and if the NSA is after your data, you should put it in a truecrypt encrypted volume. see [www.truecrypt.org]("http://www.truecrypt.org") :)

If the NSA *is* after your data, even if encrypted, they will use "rubber hose" cryptoanalysis.  That's where they beat you with a rubber hose until you give up the password!

Paul

---

### Post by aysiu on 2006-07-11
If you're super paranoid, get two computers and have one connected to the internet and another not connected.

Put all your sensitive data on the disconnected one.

Put nothing personal on the connected one. Never use plain FTP or Telnet, as those send your passwords unencrypted. Use sFTP, https, or SSH whenever possible.

---

### Post by sefs on 2006-07-11
heard from an un-named source that they now have added brute force tweezer decryption analytics to their repotoire.  I did'nt bother to ask where they applied those analytics.

---

### Post by jordilin on 2006-07-11
Linux is the most secure OS in the world. But I recommend having a firewall either in your router or in linux himself by using iptables or some gui-frontend to iptables and test it.

---

### Post by Swab on 2006-07-11
> **jordilin said:**
> Linux is the most secure OS in the world.

Not really secure when anyone can boot up a linux box with a live CD and have root access to all data... I know there are ways to prevent this, and that no system is secure if physical access is granted... but still...

---

### Post by aysiu on 2006-07-11
> **Swab said:**
> Not really secure when anyone can boot up a linux box with a live CD and have root access to all data... I know there are ways to prevent this, and that no system is secure if physical access is granted... but still...
The word *most* is a relative term, meaning more than the others out there.

You can boot up *any* box (Windows or Mac, too) with a Linux live CD and have root access to all data.

---

### Post by Swab on 2006-07-11
> **aysiu said:**
> The word *most* is a relative term, meaning more than the others out there.

You can boot up *any* box (Windows or Mac, too) with a Linux live CD and have root access to all data.

Well as far as I'm aware a live CD won't let you access data on an NTFS partition that has proper permissions in place... but I could be wrong.

---

### Post by aysiu on 2006-07-11
> **Swab said:**
> Well as far as I'm aware a live CD won't let you access data on an NTFS partition that has proper permissions in place... but I could be wrong. A live CD can access anything in NTFS unless it's encrypted.

---

### Post by Me! on 2006-07-11
> **T700 said:**
> 1.  Run a firewall and/or a NAT enabled router.

2.  Keep updated on patches.

3.  Keep backups of your data.

4.  Physically secure the PC.

5.  Don't willy nilly install software from unknown sources.

6.  Set a strong password.

Do these things and unless the NSA or some similar agency is after your data, you'll be fine.

Paul
These nice things but I didn't want a complex rules that make my live too slow. 

I will try to find NAT and good firewall . 

But I asked if I leave the Ubuntu Dapper with the updated packges ; is there any way to access to my PC by others.

---

### Post by Ramses de Norre on 2006-07-11
When the nat router is working properly not, otherwise they could use the ssh server that's installed by default but they'll need your ip, username and password to be able to log in. (and enough knowledge of the commandline to be able to do anything)

---

### Post by T700 on 2006-07-11
> **Me! said:**
> These nice things but I didn't want a complex rules that make my live too slow. 

You my friend, are an ideal candidate for data compromise.  Those are by no means burdensome suggestions.  If you think that's too much for you, I suggest you keep your data buried in a box in the backyard, because your PC *will* be owned.

Paul

---

### Post by Me! on 2006-07-11
> **jordilin said:**
> Linux is the most secure OS in the world. But I recommend having a firewall either in your router or in linux himself by using iptables or some gui-frontend to iptables and test it.
I will try iptables !

Thank you jordilin

---

### Post by nealklomp on 2006-07-11
I do agree that if security is your concern those few rules were pretty easy.
I mean really. They do not seem to be too burdensome at all, in fact they are basically what I do now, and I am not worried about it at all and do not feel slowed down. 
that said, what personal info are you planning on keeping on your box?
Really? 
Linux is by far the most secure OS in use for the general public, in large part because it is so fragmented and such a small part of the market, but still. Without password and username, and then command line specific knowledge, there is nada anyone can get or do. If you want encrypt that info. I mean what do you want, a tech to come to your house?

---

### Post by Me! on 2006-07-11
> **Swab said:**
> Not really secure when anyone can boot up a linux box with a live CD and have root access to all data... I know there are ways to prevent this, and that no system is secure if physical access is granted... but still...
But you can put a BIOS passward so no body can access to change boot drive !

No body can access without opening the PC's hardware !

The big problem is with the big network or Internet

---

### Post by T700 on 2006-07-11
> **Me! said:**
> But you can put a BIOS passward so no body can access to change boot drive !

No body can access without opening the PC's hardware !

The big problem is with the big network or Internet

You can:

1.  Reset the BIOS

-or-

2.  Take the drive and mount it in another PC

I promise you that with 5-10 minutes of physical access to your PC, I can have your unencrypted data, regardless of BIOS passwords.   If your data is really that valuable to you, take some basic measures and consider serious, open source, encryption.

Good luck,
Paul

---

### Post by dgh1973 on 2006-07-11
> **Swab said:**
> Well as far as I'm aware a live CD won't let you access data on an NTFS partition that has proper permissions in place... but I could be wrong.

This is false, access controls on file systems are handled at the operating system level and tools like "ntfsdos" have been around for a long time. 

I've found Ubuntu to be relatively secure in terms of remote access possibilities out of the box.  The desktop version has very few (if any) ports open by default after a fresh install. It's when you install added things that you have to be careful, sshd, samba, and anything else that opens a port creates a potential point of entry for a cracker.

This is the key point when you consider security from the perspective of a 24/7 internet connection. As stated above, ANY OS can be rendered insecure with local access and a live cd/boot disk... not even a CMOS password can save you because opening the case and setting a jumper can undo that.

Go into your System menu then Administration and open the Network Tools application. Click the port scan tab and plug in 127.0.0.1 or your internet IP address in and click scan. The more ports you have listening the more you have to worry about.

---

### Post by ironfistchamp on 2006-07-12
It seems the only way to be secure really is to not have a computer and even then not have any personal data.

What a world we live in where people would want to steal this kind of data :(

---

