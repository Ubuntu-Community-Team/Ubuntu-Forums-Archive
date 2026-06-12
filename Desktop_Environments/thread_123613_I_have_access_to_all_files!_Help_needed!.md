---
title: "I have access to all files! Help needed!"
date: 2006-01-30
forum: Desktop Environments
---

### Post by Tiede on 2006-01-30
I know I could have done better with the title, but that's what I had in my head at the moment and I am freaked out too much to think about a better one.
I reinstalled breezy badger three days ago due to a bad fs (/sbin/root always failing because of a deleted inode w/ zero dtime...) and since then, I have access to everything without ever needing to sudo.
Everything just opens up, and I can even edit some directories like /etc with my normal user account. Being as pocky as I am, this is surely not a good idea. Can someone tell me how I can have sudo back? I miss it so.
I also want to point that I did not take out sudo myself, but it was missing since I installed ('twas the first time I was installing ubuntu offline, but I ruled it out as a possible source)
I upgraded to dapper yesterday, and now everytime, it keeps on reminding me that I have too much privileges (which I agree) every time I open an administrator-controlled program (still without asking for a password)
I'll try to ```
 sudo passwd root 
``` later and see if that brings it back and then disable the root password again, but I was wondering if someone knew why that happened in the first place?
I will post the results of my pockings with sudo tomorrow morning.

---

### Post by Sutekh on 2006-01-30
Could you have a look at this section in the Ubuntu guide
[Ubuntu Guide - Use sudo without prompt for password]("http://ubuntuguide.org/#usesudowithoutpasswordprompt")
Check to see *if* your /etc/sudoers has been changed in the way specified.  If it looks like it has been changed, try changing the line ```
system_username	ALL=(ALL) NOPASSWD: ALL
```
back to ```
system_username	ALL=(ALL) ALL
```

---

### Post by Tiede on 2006-01-31
See, the weird thing is, it hasn't. It is just the way it is supposed to be. (well I was expecting that since I didn't change it...)

Here is the content of the file:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

```
Is the admin group the tick? I am thinking it might just be that.


EDIT: Upon further inspection, I realized I don't even *have* a system_username line at all. This does not look too promising :/

---

### Post by Sutekh on 2006-01-31
Try re-installing sudo itself and see what happens.

You need to be in the 'adm' group to use sudo.

---

### Post by Tiede on 2006-01-31
I believe I *am* in the adm group (I am the only user ;) ) and why I said maybe the adm group was the tick was because of the %admin ALL=(ALL)ALL line, which I now think is just the way it should be, if I believe my intuiton...
Reinstalling sudo. Will post results.

PS:Was this an undocumented bug? I wanna remind that it was also like taht for the 2-4 hours the laptop was in breezy transitionally. Can't pin this one on the drake :D

---

### Post by Tiede on 2006-02-01
Reinstalled sudo this morning. So far, it seems to be working fine, except it gave me the message one time yesterday afternoon before I went to school

---

### Post by Tiede on 2006-02-10
I wanna point out that even though sudo works fine now, it keeps on complaining when I open a file with gksudo within 15 minutes of using another one requiring it.
i.e, if I open a program that needs adm privs and enter the password, then a while later (within 15 minutes) open another program (or the same one again) requiring adm privs, even though the program opens just find without asking for a password (which is just normal...) a message pops up saying that the file was opened without needing to put in a password! If gksudo is himself timing my password for 15 minutes, why is it warnign me because it isn't asking me for it again during those 15 minutes??? I think that should be fixed as it might scare some people away.

---

