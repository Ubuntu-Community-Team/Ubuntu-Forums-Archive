---
title: "xmms2 repository problems"
date: 2006-06-07
forum: Desktop Environments
---

### Post by Doughsay on 2006-06-07
I am trying to install xmms2 from the dapper repository at [http://exodus.xmms.se/](http://exodus.xmms.se/).  When I add the proper lines to my apt sources list, I get a 403 Forbidden error when running apt-get update.  The xmms2 mailing list hasn't been helpful (yet) and I was wondering if anyone else has experienced the same problem.  Thanks for any help.

---

### Post by Doughsay on 2006-06-11
Ok, I'll be a little more specific.  I see many people having similar problems on this forum but no good answers.  I'm not a total noob, but I have never seen this problem, nor do i know how to solve it.

My sources.list is simple:

```

# Official repos
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

# XGL and Compiz
deb http://www.beerorkid.com/compiz dapper main

# Wine
deb http://wine.budgetdedicated.com/apt dapper main

# XMMS2
deb http://exodus.xmms.se/debian dapper main

```

I use aptitude:

```

$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [189B]
Ign http://wine.budgetdedicated.com dapper Release.gpg
Hit http://archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://wine.budgetdedicated.com dapper Release
Ign http://exodus.xmms.se dapper Release.gpg
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Packages
Ign http://wine.budgetdedicated.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://wine.budgetdedicated.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Ign http://exodus.xmms.se dapper Release
Ign http://exodus.xmms.se dapper/main Packages
Err http://exodus.xmms.se dapper/main Packages
  403 Forbidden
Fetched 3B in 2s (1B/s)
Reading package lists... Done

```

I'm trying to get xmms2 from the official xmms2 dapper repositories, and I keep getting this 403 Forbidden error.  I saw someone's tip on using ftp instead of http,  this doesn't work since they are not hosting ftp.

Also, I have two ubuntu dapper machines.  This one, it doesn't seem to work on.  The other, it works no problems.  The sources.list files are identical.

Using apt-get or synaptic produce the same result.  Any help on this would be appreciated.

---

### Post by tronica on 2006-06-11
I too am having the same problem, i even tried the debian repo and got the same thing. I'm thinking they are just having probs with their repos.

---

### Post by Doughsay on 2006-06-11
I tried the debian repo as well with the same result.  But I think it's NOT their repository having problems, because it works completely fine on my other ubuntu machine, and as far as I can tell, I have identical package management setups.

---

### Post by tronica on 2006-06-11
well i've been trying to find debs to download and i came across something that said  that it doesn't have a frontend yet. so maybe i will just wait.

---

### Post by Doughsay on 2006-06-12
No it doesn't have a "fontend".  It's not meant for that, it's based on the client server model.  So, it is a daemon that many different (3rd party) clients can connect to and control it.  There are a few clients already available, and if you visit the xmms2 wiki, you will find the section on the different clients: [http://wiki.xmms2.xmms.se/index.php/XMMS2_Clients]("http://wiki.xmms2.xmms.se/index.php/XMMS2_Clients")

It's not really ready yet anyway, but I'm still very interested in trying it out.  My problem still persists, so if anyone can help, I'd really appreciate it.

The title of this thread is a little misleading right now, since it's really a general repository/apt problem I think, and not related to xmms2 directly.  I'll see if I can change it...

---

### Post by Doughsay on 2006-06-17
I have exhausted all of my knowledge and all of my will to search through endless forums on the web.  The problem is still here, and will not go away, no matter what i do.

[LIST]
[*]I have two different computers running Ubuntu Dapper.
[*]Both are using the EXACT SAME internet connection. (They're plugged into the same switch)
[*]One will "apt-get update" perfectly normally.
[*]One will NOT.  It gives me that stupid 403 Forbidden error, but only for the xmms2 repo.
[/LIST]

I would really like to install xmms2, but more than that, I just want to solve this problem.

Does this make any sense to anyone?  It makes no sense to me at all...  And it's very frustrating.

The only thing I am left with is to re-install dapper.  And that's not a good solution.  This is practically a clean install anyway!  Nothing else is wrong at all.

Please if anyone can help me, I would really really appreciate it.  Even a wild guess at something that might help would work.  Thanks in advance.

---

### Post by Doughsay on 2006-07-03
Not even a wild guess?  Does anybody care at all?  I hate to say this, but I have not gotten one shred of help for any of my problems on these forums since dapper came out.  I used to get help all the time during the Breezy days...  Now it seems nobody has anything helpful to say at all...

---

### Post by Doughsay on 2006-07-03
I solved this problem if anyone cares.  Please read my post at this other thread:  [here]("http://www.ubuntuforums.org/showthread.php?t=186455")

---

### Post by bibs on 2006-07-22
Ur change http with ftp suggestion doesnt work, but the strange thing is tha when u put the forbidden adress(from the erros messeges) in a Internet Browser like Firefox: [COLOR="Blue"][http://exodus.xmms.se/debian/dists/dapper/main/binary-i386/Packages.gz]("http://exodus.xmms.se/debian/dists/dapper/main/binary-i386/Packages.gz")[/COLOR] the [COLOR="Blue"]Packages.gz[/COLOR] can be read without problems, but apt somhow can't accsess the file [COLOR="Blue"]Package.gz[/COLOR]... hmm very strange, maybe they server doest respond to apt client... can someone more apt advanced plz check this out?

---

### Post by bibs on 2006-07-31
Oh sorry u did solve the problem, changing the file "/etc/apt/apt.conf" from:

APT::Authentication::TrustCDROM "true";
Acquire::HTTP::Proxy "false";

to:

APT::Authentication::TrustCDROM "true";
Acquire::::Proxy "false";

solved the problem, but I still don't know why.

---

### Post by iaquino on 2007-02-13
> **bibs said:**
> Ur change http with ftp suggestion doesnt work, but the strange thing is tha when u put the forbidden adress(from the erros messeges) in a Internet Browser like Firefox: [COLOR="Blue"][http://exodus.xmms.se/debian/dists/dapper/main/binary-i386/Packages.gz]("http://exodus.xmms.se/debian/dists/dapper/main/binary-i386/Packages.gz")[/COLOR] the [COLOR="Blue"]Packages.gz[/COLOR] can be read without problems, but apt somhow can't accsess the file [COLOR="Blue"]Package.gz[/COLOR]... hmm very strange, maybe they server doest respond to apt client... can someone more apt advanced plz check this out?


Hey there, I was having the same problems, 403 Forbidden, there was no problem on the browser or using wget to access the repositories, the ftp access was blocked by the firewall so that workaround didnt work for me, finally I took off the line -Acquire::http::Proxy "false";- from the /etc/apt/apt.conf file and it started to work.

---

