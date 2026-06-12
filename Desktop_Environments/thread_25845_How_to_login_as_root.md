---
title: "How to login as root?"
date: 2005-04-11
forum: Desktop Environments
---

### Post by maxsideburn on 2005-04-11
I cannot edit any system files! Ubuntu did not allow me to choose a root password during install, so now how do I access the root account?

---

### Post by iom on 2005-04-11
sudo passwd root

enter new root password and voila.

---

### Post by Adrenal on 2005-04-11
Rtfm

---

### Post by Cool_dude_Prav on 2005-04-11
[QUOTE=Adrenal]Rtfm[/QUOTE]
 BTW wat is Rtfm???

Just type
```
sudo <commmand>
```

And enter the password that you used to create the first user account while installation...

---

### Post by scottlc on 2005-04-11
[QUOTE=Cool_dude_Prav]BTW wat is Rtfm???

Just type
```
sudo <commmand>
```

And enter the password that you used to create the first user account while installation...[/QUOTE]
RTFM == Read The F***ing Manual

Actually, it's your own password that you must enter to use sudo. The account must also have sudo-to-root privilages.

---

### Post by maxsideburn on 2005-04-11
RTFM huh?? Well not my fault everybody has to do everything so F****** different. I don't see why it can't just let you set up a root account during install.

---

### Post by wfx on 2005-04-11
@Adrenal
Is not a answer!!!

i change to root with:
sudo su YOUR_USER_PASSWORD

---

### Post by neighborlee on 2005-04-11
[QUOTE=Adrenal]Rtfm[/QUOTE]
-------------
hey..that is not how we do things around here in ubuntu..RTFM posts are NOT..repeat NOT allowed..

1) get over yourself meaning in the grander scheme of things you are NOT more important than anyone else

2) rinse and repeat till your 'clean'

I dont know about ubuntu team but "I" certainly dont tolerate this kind of nonsense to poor unsuspecting newbies..let along anyone else..

you sir are not only ignorant but not nice..

get over it..

cheers
nl
-----

---

### Post by neighborlee on 2005-04-11
[QUOTE=maxsideburn]RTFM huh?? Well not my fault everybody has to do everything so F****** different. I don't see why it can't just let you set up a root account during install.[/QUOTE]
-----------
I appologise for ubuntu and for the  'person' that used 'RTFM' to you as there is NO excuse for that period.

anyway MOST of us are decent linux users so just ignore this guy completely till he comes to his senses ( and appologises )

cheers
nl
----

---

### Post by Buffalo Soldier on 2005-04-11
[QUOTE=maxsideburn]RTFM huh?? Well not my fault everybody has to do everything so F****** different. I don't see why it can't just let you set up a root account during install.[/QUOTE]I would like to join other people in apologising for that. But I also understand his/her frustration. Cause the no root user policy of Ubuntu is well documented:[list]
[*] During installation before/when the installer asked for a username and password, there is an explaination about no root user and sudo.
[*] And it also has been well discussed in here (forum)
[/list]

Now that we have that set aside. Let's get to business.[list]
[*] [Sudo and the Root Account](http://www.ubuntulinux.org/wiki/RootSudo) from Ubuntu User Documentation Wiki
[*] [Sudo](http://ubuntuforums.org/showthread.php?t=25509) thread
[*] [how do you use su or sudo](http://ubuntuforums.org/showthread.php?t=24195) thread
[*] [ubuntu root password](http://ubuntuforums.org/showthread.php?t=23432) thread
[/list]

---

### Post by cabu on 2005-04-11
But give sudo a chance. I know it seems kind of foreign at first, but once you use it for awhile you get used to it. I personally didn't like it when I first started with Ubuntu, but gave it a try since it was the default. I now definitely prefer it over using a root account.

---

