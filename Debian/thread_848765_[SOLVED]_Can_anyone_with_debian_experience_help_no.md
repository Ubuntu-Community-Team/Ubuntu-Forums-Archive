---
title: "[SOLVED] Can anyone with debian experience help noob?"
date: 2008-07-03
forum: Debian
---

### Post by bhadotia on 2008-07-03
Alright, I heard about how fast debian was , so I installed it . But , now I;m a little confused as to how to add the repositories. Debian does not have synaptic by default so I have to use appititude. Search on google is one which is causing all the confusion (or may be just lack of sleep tonight- I did not sleep all night! :)).
I have found a link for the restricted repos but can't seem to find a link to the official debian repos so that I can add them to the sources.list.
Here is the link that I found:
[http://debian-multimedia.org/debian-m.php](http://debian-multimedia.org/debian-m.php)
Please tell me if its correct and post links on easy-to-understand Howtos on how to add the official debian repos.
BTW, I downloaded the testing version ISO (onlty one CD) and installed it.
Many thanks in advance.

---

### Post by wrtpeeps on 2008-07-03
Surely the official repos are in sources.list by default?

---

### Post by bhadotia on 2008-07-03
They are ? I mean I did not notice any . Oh.. heck it's the sleep - I'm really sllepy may be thats why .
Alright , I'll take a little sleep and come back in 2-3 hours. I'll keep you posted just in case.

Also , one last question :is the above link to restricted repos correct?

---

### Post by bodhi.zazen on 2008-07-03
What version of Debian exactly ?

You can always :

```
sudo apt-get install synaptic
```

Also, just as in Ubuntu, take a look at :

/etc/apt/sources.list

It may be as simple as removing a few #

---

### Post by annda on 2008-07-03
as far as i know debian testing includes synaptic (at least mine does). you can also install it with apt-get or aptitude if it's really missing.

here's a list of extra repos (yours is one of them)
[http://wiki.debian.org/UnofficialRepositories](http://wiki.debian.org/UnofficialRepositories)

---

### Post by bhadotia on 2008-07-03
I think the version is called 'Lenny'.

---

### Post by bhadotia on 2008-07-03
> **annda said:**
> as far as i know debian testing includes synaptic (at least mine does). you can also install it with apt-get or aptitude if it's really missing.

here's a list of extra repos (yours is one of them)
[http://wiki.debian.org/UnofficialRepositories](http://wiki.debian.org/UnofficialRepositories)


Thanks a lot for the link, I am feling a little comfy now!

---

### Post by xebian on 2008-07-03
> **bhadotia said:**
> I think the version is called 'Lenny'.

Debian has these repos - main contrib non-free

```

###sid
deb http://ftp.us.debian.org/debian/ sid main contrib non-free
deb http://security.debian.org/ sid/updates main contrib non-free

###lenny
#deb-src http://ftp.us.debian.org/debian/ lenny main
#deb http://ftp.us.debian.org/debian/ lenny main


```

---

### Post by bhadotia on 2008-07-03
Just one questio what is the difference between '##' and '#' in the list.

---

### Post by Sef on 2008-07-03
Moved to Debian Forum.

---

### Post by xebian on 2008-07-03
> **bhadotia said:**
> Just one questio what is the difference between '##' and '#' in the list.

Those are comments.  I started mine as lenny (which is now commented out ), but now is sid.

---

### Post by bhadotia on 2008-07-03
> **Sef said:**
> Moved to Debian Forum.
You should PM me before doing that - I got worried where it went.

---

### Post by bhadotia on 2008-07-03
> **xebian said:**
> Those are comments.  I started mine as lenny (which is now commented out ), but now is sid.
If they are all used to comment out then why repeat #.

---

### Post by xebian on 2008-07-03
> **bhadotia said:**
> If they are all used to comment out then why repeat #.
Because I want to. :)

Isn't the pattern obvious?  The repeated ## are kind of section headers.

---

### Post by bhadotia on 2008-07-03
K.. get it. 
Thanks.

---

### Post by bhadotia on 2008-07-03
Alright people the official repos are not in my sources .list. Can someone please post a copy of his sources .list so for lenny so that I can add it to mine.

---

### Post by bhadotia on 2008-07-03
Sorry forgot Xebian has already done that:)

---

### Post by bhadotia on 2008-07-03
Can some one post a link to where I can find a list of the mirrors to the main repos , I think this us mirror of Xebian is too slow.

---

### Post by kerry_s on 2008-07-03
you do know that Xebian and debian are different os's?

mixing different os's can break a install fast.
it's like ubuntu, it's based on debian, but very different in the way it's put together.

---

### Post by bodhi.zazen on 2008-07-03
see if this link helps :

[http://tintax.net/2008/02/29/install-a-lightweight-desktop-xfce-on-debian-lenny/](http://tintax.net/2008/02/29/install-a-lightweight-desktop-xfce-on-debian-lenny/)

---

### Post by xebian on 2008-07-03
> **bhadotia said:**
> Can some one post a link to where I can find a list of the mirrors to the main repos , I think this us mirror of Xebian is too slow.

Of course , you should change 'us' (USA) to one closest to you.  But I don't see any India except for a secondary mirror.  You can try from Asia- say 'hk' hong kong, or 'tw' taiwan.

Here is the mirror list

[http://www.us.debian.org/mirror/list](http://www.us.debian.org/mirror/list)

There is no primary in India but there is a secondary mirror
ftp.iitm.ac.in

---

### Post by xebian on 2008-07-03
> **kerry_s said:**
> you do know that Xebian and debian are different os's?

mixing different os's can break a install fast.
it's like ubuntu, it's based on debian, but very different in the way it's put together.

:confused::confused::confused:

Xebian is my UbuntuForum ID who happens to use Debian.

:):):):):)

---

### Post by bhadotia on 2008-07-04
> **xebian said:**
> :confused::confused::confused:

Xebian is my UbuntuForum ID who happens to use Debian.

:):):):):)
Hee hee.

Thanks guys.

---

### Post by bhadotia on 2008-07-04
Another Question: How to get compiz working on debian?
Tried searching the net but none of the tutorials made it working for me.

---

### Post by brian_p on 2008-07-04
> **bhadotia said:**
> Just one questio what is the difference between '##' and '#' in the list.

Nothing, it just makes the file more readable for a human. One or more '#'s at the beginning of a line means the line is not used by the program.

---

### Post by cdiem on 2008-07-04
I think, that the Indian Debian repos for Lenny may look like this:

```
#Main, contrib and non-free
deb http://ftp.iitm.ac.in/debian lenny main non-free contrib
deb-src http://ftp.iitm.ac.in/debian lenny main non-free contrib

#Security repos
deb http://security.debian.org lenny/updates main contrib non-free
deb-src http://security.debian.org lenny/updates main contrib non-free
```
( Changed a bit from here: [http://playingwithsid.blogspot.com/2007/10/indian-debian-repositories-sourceslist.html](http://playingwithsid.blogspot.com/2007/10/indian-debian-repositories-sourceslist.html) ). 

I think, that for Compiz you may want to take a look at this:
[http://forums.debian.net/viewtopic.php?t=26966](http://forums.debian.net/viewtopic.php?t=26966)

---

### Post by Arthur Archnix on 2008-07-06
I predict your time with Debian is not going to go well. It demands a bit more on the part of its users. Is there a reason you're not using Ubuntu?

I don't find it any faster than Ubuntu once I've configured it. It simply installs much less by default, so it's initally very fast. But once you get it to act like Ubuntu, then it might even be slower. You might be better off tweaking Ubuntu for speed, look into ext3 tweaks, reduce services, profile your boot, reduce swappiness, etc...

---

### Post by bhadotia on 2008-07-06
Yup! you said it! After installing all the stuff it was no faster than ubuntu. Plus after the update the sound won't work properly - it very loud and harsh.
So I replaced it with suse11 yesterday. 
I  am still using ubuntu , frankly I have never really uninstall  ubuntu after  - I always dual boot with it (- windows or another distro). Even if I have ever completely wiped it is only to come back to it in a week or so:)

---

### Post by Arthur Archnix on 2008-07-06
It was loud and harsh because you had to run alsaconf and reconfigure. It also helps to check out alsamixer and then aslastl store. Just some tips for a few months down the road when Lenny is releaesd and you're tempted to try it again.

Enjoy suse. It's nice booting into a professional looking desktop, instead of what looks like an accident at the chocolote factory. ;)

---

