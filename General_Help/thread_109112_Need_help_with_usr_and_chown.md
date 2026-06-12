---
title: "Need help with /usr and chown"
date: 2005-12-27
forum: General Help
---

### Post by wacky_ninjas on 2005-12-27
I've just made a rather dumb (but maybe not fatal) mistake, and I'd appreciate some help to fix it. This is on Breezy 5.10.

I was installing some drivers for a Lexmark printer (given to me used - I wouldn't buy one for a Linux system, with their driver issues) and I was trying to fix the ownership for some of the files. I got a little too... let's say "aggressive" with the chown command and ended up doing this from the root directory:
```
# sudo chown -R root:root usr
```

The result, of course, is that _all_ files under /usr are now owned by root and in the root group as well. Fortunately, the damage is limited to /usr (which should mostly be owned by root anyway) and I don't think the command followed any symlinks.

I tried out several of my installed programs and they all seemed to work except for some games (which apparently need some "games" ownership). I fixed the games by reinstalling them via synaptic. I rebooted to be sure that _that_ worked, and all seems to be well.

My question is: Am I missing anything *important*? That is, something that really affects the system, as opposed to a user-level application. I noticed in /etc/passwd that the "daemon" account uses /usr/sbin as its home - wouldn't want to disturb the daemons. :) 

Can someone please run "ls -lr" on their (relatively clean) /usr directory in Breezy and grep for files that are not "root:root"? If you do this, make sure to check the groups as well as the owners - I noticed after reinstalling some games that they're owned as "root:games", so other files may have similar issues.

I'd rather not have to do a complete system reinstall to fix this - this isn't M$, after all. At least all my files are intact, so I won't really lose anything but time if it comes to that.

Thanks for any help you can offer.

---

### Post by sciurus on 2005-12-27
**ls -lR /usr/bin | grep -v "root   root "**
total 117456
-r-sr-sr-x  1 daemon daemon    34880 2005-08-04 10:47 at
-rwxr-sr-x  1 root   tty        7768 2005-07-07 07:48 bsd-write
-rwxr-sr-x  1 root   shadow    34032 2005-10-11 12:14 chage
-rwxr-sr-x  1 root   crontab   26616 2005-05-02 19:09 crontab
-rwxr-sr-x  1 root   shadow    16176 2005-10-11 12:14 expiry
-rwsr-xr--  1 root   fuse      17208 2005-12-01 06:17 fusermount
-rwxr-sr-x  1 root   mail      12372 2005-05-02 22:10 lockfile
-rwsr-xr-x  1 cupsys root       9132 2005-09-14 09:47 lppasswd
-rwsr-xr--  1 root   plugdev   28088 2005-10-04 07:11 pmount
-rwxr-sr-x  1 root   mail      68152 2005-05-02 22:10 procmail
-rwsr-xr--  1 root   plugdev   20628 2005-10-04 07:11 pumount
-rwxr-sr-x  1 root   utmp     297080 2005-02-28 10:23 screen
-rwxr-sr-x  1 root   slocate   26680 2004-09-23 16:17 slocate
-rwxr-sr-x  1 root   ssh       55828 2005-10-10 16:10 ssh-agent
-rwxr-sr-x  1 root   tty        9824 2005-09-20 12:43 wall

**ls -lR /usr/sbin | grep -v "root root"**
total 7928
-rwsr-xr--  1 root dip  257688 2005-05-27 12:16 pppd

**ls -lR /usr/local | grep -v "root root"**
/usr/local/lib:
total 12
drwxrwsr-x  3 root staff 4096 2005-10-31 08:20 python2.4

/usr/local/lib/python2.4:
total 4
drwxrwsr-x  2 root staff 4096 2005-10-31 08:20 site-packages

/usr/local/lib/site_ruby/1.8:
total 4
drwxrwsr-x  2 root staff 4096 2005-10-31 14:00 i486-linux

/usr/local/share:
total 20
drwxrwsr-x  2 root staff 4096 2005-10-31 13:31 fonts
drwxrwsr-x  7 root staff 4096 2005-10-31 13:31 sgml
drwxrwsr-x  6 root staff 4096 2005-10-31 13:31 xml

/usr/local/share/fonts:
total 0
-rw-r--r--  1 root staff 0 2005-10-31 13:33 fonts.cache-1

/usr/local/share/sgml:
total 20
drwxrwsr-x  2 root staff 4096 2005-10-31 13:31 declaration
drwxrwsr-x  2 root staff 4096 2005-10-31 13:31 dtd
drwxrwsr-x  2 root staff 4096 2005-10-31 13:31 entities
drwxrwsr-x  2 root staff 4096 2005-10-31 13:31 misc
drwxrwsr-x  2 root staff 4096 2005-10-31 13:31 stylesheet

I hope that helps.

---

### Post by wacky_ninjas on 2005-12-27
Thanks, sciurus. I've got some checking to do...

I don't have accounts named "dip" and "staff". Are these usernames on your system, or are they system accounts like "games" and "mail"?

---

### Post by wacky_ninjas on 2005-12-28
Well, this has gotten even stranger. Many of the account names in sciurus's listing do not appear in my /etc/passwd, which AFAIK means that they don't exist in my system. The missing ones are:

tty
shadow
crontab
fuse
plugdev
utmp
slocate
ssh
dip
staff

Most of these are the names of common GNU system programs that I _should_ have, and most of the files listed are in my system. I can see two possible explanations:
1) It's possible to have these account names on files even if they're not in passwd.
2) My system is different from sciurus's, maybe because I upgraded from Hoary to Breezy instead of a fresh install for Breezy.

Does anybody have some advice about this? I'm going to try to fix some of these by reinstalling the appropriate packages instead of chowning them directly. That's partly because the first chown also cleared some setuid and setgid bits in my affected files, and I'd rather not guess at the correct values for those. Come to think of it, I wonder how many other suid bits got cleared that didn't show up in the listing...

sciurus - Did you install Breezy clean, or upgrade like I did?

Thanks, again.

The moral of the story: Don't mess around with sudo and recursive traversal together, even if you're not using "rm".

---

### Post by wacky_ninjas on 2005-12-28
...or I could check /etc/group, instead of just /etc/passwd. It looks like all of those names are there.

I don't know where my brain was yesterday, but it must've been a nice place, because it was gone for a while...

Ah, well. Live, learn, and patch.

---

