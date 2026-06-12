---
title: "can anyone tell me why i am getting alot of these error messages??"
date: 2009-06-12
forum: General Help
---

### Post by scrypt on 2009-06-12
Hi All
 I am getting allot of the following error messages when I boot up and shutdown

can anybody tell me what i can di to fix this error plz??



WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

---

### Post by Yellow Pasque on 2009-06-12
It means all the files in that directory will need .conf on the end, or they won't be recognized in future versions of Debian/Ubuntu.

Did you upgrade to Jaunty from an earlier Ubuntu version? If so, you probably kept a customized version of blacklist. ndiswrapper generates that file, so you can rename it ndiswrapper.conf safely.

---

### Post by scrypt on 2009-06-13
> **Temüjin said:**
> It means all the files in that directory will need .conf on the end, or they won't be recognized in future versions of Debian/Ubuntu.

Did you upgrade to Jaunty from an earlier Ubuntu version? If so, you probably kept a customized version of blacklist. ndiswrapper generates that file, so you can rename it ndiswrapper.conf safely.

Hoo Do I Rename ndiswrapper.conf safely??

---

### Post by scrypt on 2009-06-13
How Do I rename these:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, 

/etc/modprobe.d/blacklist.conf

/etc/modprobe.d/ndiswrapper.conf

?????

---

### Post by scrypt on 2009-06-13
Should I just rename the config
> file in /etc/modprobe.d/ so that they all have .conf at the end, or is
> there another process I need to do?

---

### Post by jenkinbr on 2009-06-13
```
sudo cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && sudo rm /etc/modprobe.d/blacklist
sudo cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && sudo rm /etc/modprobe.d/ndiswrapper
```

That should do it.

Those commands will copy the contents of the effected files to the correct file, then remove the error-causing files.

---

### Post by scrypt on 2009-06-13
Than's for replying.

I am getting a permission denied error message::

mark@mark-laptop:~$ sudo cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && sudo rm /etc/modprobe.d/ndiswrapper
bash: /etc/modprobe.d/ndiswrapper.conf: Permission denied

I have absolutely No wireless whatsoever,

---

### Post by scrypt on 2009-06-13
bump

---

### Post by scrypt on 2009-06-13
Here are the two permission denied errors I am getting:

mark@mark-laptop:~$ sudo cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && sudo rm /etc/modprobe.d/ndiswrapper
bash: /etc/modprobe.d/ndiswrapper.conf: Permission denied

mark@mark-laptop:~$ sudo cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && sudo rm /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist.conf: Permission denied

---

### Post by synapsys on 2009-06-13
Try:

```
sudo su
```

Then run the same commands minus both instances of sudo e.g.

```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist

```

be sure to 'exit' terminal when done, so as not to stay logged in as root.

or

```
sudo nautilus /etc/modprobe.d/
```

right click said files and rename them with .conf at the end.

---

### Post by jenkinbr on 2009-06-13
> **synapsys said:**
> Try:

```
sudo su
```

Then run the same commands minus both instances of sudo e.g.

```
cat /etc/modprobe.d/ndiswrapper >> /etc/modprobe.d/ndiswrapper.conf && rm /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist >> /etc/modprobe.d/blacklist.conf && rm /etc/modprobe.d/blacklist

```

be sure to 'exit' terminal when done, so as not to stay logged in as root.

or

```
sudo nautilus /etc/modprobe.d/
```

right click said files and rename them with .conf at the end.
Thanks - that was going to be my next suggestion, but I had some spam reports to send.

@scrypt: Please use the edit feature if you are the previous poster and the post is less than 1 day old.

---

### Post by synapsys on 2009-06-13
wow kudo's to the mods.... those spam posts were deleted with ninja-like quickness

---

### Post by scrypt on 2009-06-13
Thank-you synapsys that solved my problem.

Good on Ya :)

How do I tag this as solved??

Also How you can't give me a hand with my other thread:
 
Cannot connect wirelessly with BCM4312 WLAN card!!

Ive not had much help with it :(

---

### Post by scrypt on 2009-06-13
Jenkinbr I'm not sur what you mean??

> **jenkinbr said:**
> Thanks - that was going to be my next suggestion, but I had some spam reports to send.

@scrypt: Please use the edit feature if you are the previous poster and the post is less than 1 day old.

---

### Post by jenkinbr on 2009-06-13
To mark as solved:

at the bottom of the page, just below the bookmarks and above quick-reply, you can edit tags.

add a [solved] tag.

---

### Post by jenkinbr on 2009-06-13
> **scrypt said:**
> Jenkinbr I'm not sur what you mean??
There is an edit button next to the quote button on posts you have made.  looks like [img]http://ubuntuforums.org/images/buttons/edit.gif[/img]

---

### Post by scrypt on 2009-06-13
Thanks for the tip jenkinbr. I'll keep it in mind for future reference!

---

### Post by lswb on 2009-06-13
Why not just "sudo mv file file.conf"  ?

---

### Post by jenkinbr on 2009-06-13
> **lswb said:**
> Why not just "sudo mv file file.conf"  ?
so it doesn't overwrite any changes or content in the *.conf file.

---

### Post by jack24 on 2010-01-12
Thanks for posting this help synapsys, it saved me a lot of work.

---

