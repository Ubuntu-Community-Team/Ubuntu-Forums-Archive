---
title: "kopete cant login in MSN"
date: 2005-05-20
forum: Desktop Environments
---

### Post by engos on 2005-05-20
hi says that my password is wrong, it works fine in Gaim

---

### Post by Zelut on 2005-05-20
What version are you running?  I had problems using MSN in an older version with the same error.  It turned out that MSN now requires SSL authentication & the older version didn't supply that.  This may be why it works ok in GAIM (I'm assuming you're using 1.2.x+) but not in kopete.  You may want to try & update it or check the kopete site for info on SSL.

---

### Post by fdoving on 2005-05-20
[QUOTE=engos]hi says that my password is wrong, it works fine in Gaim[/QUOTE]
 It's a known issue.
[http://wiki.kde.org/tiki-index.php?page=Kopete+SVN](http://wiki.kde.org/tiki-index.php?page=Kopete+SVN)
[http://bugs.kde.org/show_bug.cgi?id=105929](http://bugs.kde.org/show_bug.cgi?id=105929)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=309745](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=309745)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=10993](https://bugzilla.ubuntu.com/show_bug.cgi?id=10993)


- Frode

---

### Post by engos on 2005-05-20
but i using the last version, 0.10, and it works fine until the last week

---

### Post by Zelut on 2005-05-20
If you read the posts above, namely [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=309745](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=309745) you'll see that as of 5.19.05 there was an update and kopete hasn't been upgraded yet to be compatible.  Its a known issue, so you're not the only one with the problem.

---

### Post by engos on 2005-05-20
thanks and sorry, i dont see the link before reply again :/

---

### Post by Firetech on 2005-05-20
There seems to be updates in the repository now. Just run an upgrade with synaptic och kynaptic (or maybe even kpackage)

Edit: Just tested the update and it works now... And I had just finished to compile the svn version... ;)

---

### Post by Terracotta on 2005-05-20
[QUOTE=Firetech]There seems to be updates in the repository now. Just run an upgrade with synaptic och kynaptic (or maybe even kpackage)

Edit: Just tested the update and it works now... And I had just finished to compile the svn version... ;)[/QUOTE]

The update fixed it for me too, thanks to the devs for such a fast response to this problem.

---

### Post by rune on 2005-05-21
what version of Kopete are you running? I can't seem to update mine. The about box says 0.10 and ubuntu says:  kopete         3.4.0-0ubuntu2 Instant messenger program.

I still get the password prompt all the time.

---

### Post by Firetech on 2005-05-21
The fixed version has number 3.4.0-0ubuntu2.1

Are you sure you have enabled hoary-updates in /etc/apt/sources.list?
Make sure the lines containing "hoary-updates" are not preceeded with "#", and that the end of it contains at least "main".

**EDIT:** Silly me, the kubuntu packages are in main, not in universe...

---

### Post by rune on 2005-05-21
Thanks,  didn't know about hoary-updates.

---

### Post by frs-design on 2005-05-24
hi !

I had the same problem and i just did:

sudo apt-get update
sudo apt-get upgrade kopete and that's ok !

Bye ++

---

### Post by ykpaiha on 2005-05-24
same issue with cvs
So rebuild if so...

---

### Post by parkash on 2005-05-25
Ok, I have hoary-updates enabled... I've already upgraded my system (everything) and still have the problem with kopete...  Maybe I'm missing some repository?   Could someone give me a clue?

---

### Post by frs-design on 2005-05-25
Hi !

If you do

sudo apt-get update
sudo apt-get upgrade kopete

you need to restart your computer in order to apply the changes because of the upgrade of specific network packages.

And it rulez !!!

Bye

---

### Post by parkash on 2005-05-25
Ok, I did 

```
$sudo apt-get update
``` 

And then:

```
$ sudo apt-get upgrade kopete
```
I got:

```
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

And restarted my system...

Still have the problem... I think maybe my repositories are wrong. See, I use:

"http://mx.archive.ubuntu.com"
"http://archive.ubuntu.com"

Of course I use sections main, restricted, universe and multiverse...

This is getting to my nerves already...  :?

---

### Post by frs-design on 2005-05-25
ok so i give you mine:

```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## To fetch major bug fix updates produced
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## To add software from the 'universe' repository.
deb http://us.archive.ubuntu.com/ubuntu hoary universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

# les depots pour wine - emulateur de windows
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/

# les depots pour tout ce qui touche au multimedia-son-video etc...
deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main
``` 

With that, it works for sure !!

good luck
Bye @+

---

### Post by parkash on 2005-05-27
Well thanx! I'll give it a try today  :smile:

---

### Post by Firetech on 2005-05-27
[QUOTE=frs-design]Hi !

If you do

sudo apt-get update
sudo apt-get upgrade kopete

you need to restart your computer in order to apply the changes because of the upgrade of specific network packages.

And it rulez !!!

Bye[/QUOTE]
 Now you're lying... You never need to reboot a Linux computer, except for kernel panics and kernel changes. I didn't have to do anything to apply those network things...

---

### Post by parkash on 2005-05-27
Lying or not... I still can't connect to msn...

I'm giving up now...  Maybe I'll just download the source from kopete's page...  :-x

---

### Post by ludi on 2005-05-27
[QUOTE=parkash]Lying or not... I still can't connect to msn...

I'm giving up now...  Maybe I'll just download the source from kopete's page...  :-x[/QUOTE]
 Hi.
I don't know if a missed something, but you have to update your system, not just kopete. There are few updates related to kopete error (use ubuntu-update or synaptics).
If I got it right, has been change something in Msn server that break up the kopete log in, well, this is not the first time...

---

### Post by parkash on 2005-05-27
I did upgrade all my system (usually I love to have everything as new as possible). The curious thing is I already downloaded the latest version from kopete's web page and the problem persists...  I really don't know what to do now...  It's just. Strange.  ](*,)

---

### Post by parkash on 2005-05-28
I'm done with msn messenger...   :mad: 

I looked up for more info on kopete's forums and it seems it's becoming more and more difficult to log in from linux...
[HTML]http://www.kde-forum.org/thread.php?threadid=11478&sid=&threadview=0&hilight=&hilightuser=0&page=6[/HTML]

So... Why not use yahoo or icq... Whatever???

My only question is...  Is there another IM service as fancy as MSN?  I mean, the pics, webcam, etc...  Besides, file transfers in msn s**k...  

So I'm open to suggestions :D

---
Already using aim, icq and yahoo.

Say no to M$  [-X

---

### Post by parkash on 2005-05-28
Found this browsing on gentoo forums :D

> Right click the small jabber icon at bottom of kopete screen and select services.

On window that opens, select query server.

If your jabber server supports passthrough, you will have an option listed called MSN transport.

Select it and you can access your MSN contacts through jabber in kopete now. 

Now, that should do the trick for a while  \\:D/ 

I am invincible!!!  (And then, unexpectedly, I die)

---

### Post by fdoving on 2005-05-28
[QUOTE=parkash]Found this browsing on gentoo forums :D

 

Now, that should do the trick for a while  \\:D/ 

I am invincible!!!  (And then, unexpectedly, I die)[/QUOTE]
 Hi.

I don't know what you've been doing. But this fix has been in hoary-updates for some time. Make sure you get the version 4:3.4.0-0ubuntu2.1 of the kopete package from your hoary-updates mirror. It works.

If you don't know how to add hoary-updates to your setup, go to: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

When you've added it: 'apt-get update;apt-get install kopete=4:3.4.0-0ubuntu2.1'

- Frode

---

### Post by laurent on 2005-06-08
Hello,

I'm having the 4:3.4.1-0ubuntu0hoary2 and it not working.

Is there some specific option on the 3.4.1 ?

Cheers,
Laurent.

---

### Post by skyboy on 2005-06-08
MSN protocol has changed, 
you need kopete version 0.8.4 at least

---

