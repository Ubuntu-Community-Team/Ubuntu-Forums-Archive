---
title: "Repositories and backports to use in Kubuntu 5.10?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by mbourd25 on 2005-10-17
Hi, I installed Kubuntu 5.10 and I was looking at installing Firefox and some games from the repositories that's in the source.lst file when Kubuntu is installed. But doing some searching, I was unable to find anything, just KDE stuff.

My question is which repositories and backports should I use in my source.lst to get all these software?

Thanks.

---

### Post by desertViking on 2005-10-17
I installed Firefox last night by enabling the repositories in /etc/apt/sources.list.  I just uncommented some of the provided default repositories.  

You then need to reload the repository information to see the available programs.

I was also wanting to load Thunderbird, but it wasn't discovered.  I'll solve that another day.

Hope this helps,

desertViking

---

### Post by Brando569 on 2005-10-17
dont uncomment the backports, they dont work yet youll just get alot of error messages

---

### Post by desertViking on 2005-10-17
Correct,  I should have mentioned that in my previous post.  Thx for adding the information.

desertViking

---

### Post by jdong on 2005-10-17
[QUOTE=Brando569]dont uncomment the backports, they dont work yet youll just get alot of error messages[/QUOTE]


Correct -- the Backports will open around the time that the Dapper Drake release opens, which is tomorrow, approximately :)

---

### Post by desertViking on 2005-10-17
:p Cool!

---

### Post by manicka on 2005-10-17
[QUOTE=mbourd25]
My question is which repositories and backports should I use in my source.lst to get all these software?
Thanks.[/QUOTE]

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by desertViking on 2005-10-17
Hi,

I'm trying to do some upgrades (was going to try the kernel 686, but that doesn't look like a good idea at the moment).  At any rate, there's some other stuff I want, too.

I used the list just provided here, and tried to apt-get update, and ran into these issues:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I seem to remember that one could ignore keys, but perhaps there's a more elegant solution?

Kind regards,

desertViking

P.S.

Appologies if this seems to be hijacking this thread.  I could post a new one but thought this was relavant here.

---

### Post by praecantator on 2005-10-17
This has popped up a couple of times in a few other threads--just delete the "us." part of "us.archive.ubuntu.com" on the relevant lines of /etc/apt/sources.list and run apt-get update again.  From what others have said, there seems to be some problem w/the GPG key on  the US mirror...

edit:
and as soon as I say that, the error pops up for me on the non-mirror URI.  Worked earlier, though...  :)

---

### Post by aysiu on 2005-10-17
By the way, I've updated the [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html) page to not include the *us* in the URL parts of the repositories.

---

