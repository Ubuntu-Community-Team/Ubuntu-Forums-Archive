---
title: "Wine install help?"
date: 2005-09-23
forum: Gaming &amp; Leisure
---

### Post by ThePerson98 on 2005-09-23
Hey guys, new to unbuntu. Don't understand the language of linux yet. So try and keep it english..
I was trying to install WINE, yet it is deciding not to work. Following instructions, still having problems.
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
I dunno what I am doing wrong.
I go to syaptic package manager/settings/repositories
Comes up with a completely different list than the guide says that should come up. And its funny, the guide even mentions ubuntu in it, but doesnt work.

---

### Post by Dolphin on 2005-09-23
[QUOTE=ThePerson98]Hey guys, new to unbuntu. Don't understand the language of linux yet. So try and keep it english..
I was trying to install WINE, yet it is deciding not to work. Following instructions, still having problems.
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
I dunno what I am doing wrong.
I go to syaptic package manager/settings/repositories
Comes up with a completely different list than the guide says that should come up. And its funny, the guide even mentions ubuntu in it, but doesnt work.[/QUOTE]

```
sudo apt-get install wine
```

Should be all you need to do.

---

### Post by Benzima on 2005-09-24
I did that and got this:

*****
blaxima@ubuntu:~$  sudo apt-get install wine winesetuptk
Reading package lists... Done
Building dependency tree... Done
winesetuptk is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libwine (= 0.0.20050310-1.1) but 0.0.20050419-1~5.04ubp1 is to be installed
E: Broken packages
blaxima@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libwine (= 0.0.20050310-1.1) but 0.0.20050419-1~5.04ubp1 is to be installed
E: Broken packages
blaxima@ubuntu:~$

*****
To me it souds like my version of libwine is "too new". So does that mean the newer libwine is not backward compatible?!!? That wouldn't make any sense to me. Must be something else.

Argh !!!

Any ideas? Thanxxx in advance.

Ok...I got it by following the instructions here: [http://www.ubuntuforums.org/showthread.php?t=56892&highlight=apt+wine](http://www.ubuntuforums.org/showthread.php?t=56892&highlight=apt+wine)

---

### Post by Goober on 2005-09-25
If you weren't already, try going to the root terminal, and installing wine there.  The root terminal works for me sometimes when the regular command line fails.

---

### Post by wishyjr on 2005-10-10
hi, im also having problems running 'sudo apt-get install wine'. I get this:

paul@ubuntu:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
paul@ubuntu:~$

any thoughts? ta.

---

### Post by seethru on 2005-10-10
sounds like you need to add repositories.

sudo gedit /etc/apt/sources.list

add these lines
```
# Wine
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/
```

---

### Post by BLTicklemonster on 2005-10-10
One thing about source list I've found. Always go back and clean up what you did, and get the file back the way it was at first. Sure I guess you can leave some stuff on there, but I have seen some pretty wierd error messages in synaptic that I knew were caused by leaving some repository stuff in there. Maybe not stuff that would hurt anything, but if you're like me, even those error messages when you're installing cause a freak out, lol.

---

### Post by wishyjr on 2005-10-12
[QUOTE=seethru]sounds like you need to add repositories.

sudo gedit /etc/apt/sources.list

add these lines
```
# Wine
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/
```[/QUOTE]


tried that but i still get the same message. could it be anything else?

---

### Post by seethru on 2005-10-12
did you sudo apt-get update?

---

### Post by wishyjr on 2005-10-12
i did my good sir! im abit confuzzled, i read quite a lot on getting wine but it just doesnt want to know. 
i was thinking the the repos dont currently have in on but that was a few days ago now - im sure its on a repo somewhere.

---

### Post by SeanCallan on 2005-10-12
Wow thanks this post really helped.

I initially ran the update and still got nothing, I then added those lines to the source, ran the update and it installed perfectly!  You guys are awesome.

Thanks!

---

