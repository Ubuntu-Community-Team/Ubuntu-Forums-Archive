---
title: "Unable to change login settings/ No seat ID found"
date: 2011-05-10
forum: Desktop Environments
---

### Post by maddbaron on 2011-05-10
I click unlock repeatedly but nothing happens... I ran it in terminal and got this
```
sudo gdmsetup
[sudo] password for wordsmith: 
** (gdmsetup:5106): DEBUG: init delay=10
** (gdmsetup:5106): DEBUG: "/usr/share/xsessions/une-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:5106): DEBUG: "/usr/share/xsessions/guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:5106): DEBUG: "/usr/share/xsessions/une-efl-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:5106): DEBUG: Init default session found:'xsession'
** (gdmsetup:5106): DEBUG: Failed to identify the current session: Unable to lookup session information for process '5106'

** (gdmsetup:5106): WARNING **: Unable to find users: no seat-id found

```

Help please!

---

### Post by maddbaron on 2011-05-10
bump...

---

### Post by jerrrys on 2011-05-10
no good answer, just a lead. dose any of this apply to you?

[http://www.google.com/search?client=ubuntu&channel=fs&q=Unable+to+find+users%3A+no+seat-id+found+linux+ubunyu&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Unable+to+find+users%3A+no+seat-id+found+linux+ubunyu&ie=utf-8&oe=utf-8)

---

### Post by maddbaron on 2011-05-10
> **jerrrys said:**
> no good answer, just a lead. dose any of this apply to you?

[http://www.google.com/search?client=ubuntu&channel=fs&q=Unable+to+find+users%3A+no+seat-id+found+linux+ubunyu&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Unable+to+find+users%3A+no+seat-id+found+linux+ubunyu&ie=utf-8&oe=utf-8)

Not really... my gui is working, gdm too.. I can use my password except in this case & when I try to update apps via update manager...i don't know what is wrong with this system...

---

### Post by Krytarik on 2011-05-11
> **maddbaron said:**
> I can use my password except in this case & when I try to update apps via update manager
It seems like your user is not part of the "admin" group.

Check it with:
```
groups USERNAME
```
If it isn't, boot into "recovery mode -> root shell prompt" and run:
```
adduser USERNAME admin
```
Note: No need to use 'sudo' here because you will already be root.

Greetings.

---

### Post by maddbaron on 2011-05-12
> **Krytarik said:**
> It seems like your user is not part of the "admin" group.

Check it with:
```
groups USERNAME
```
If it isn't, boot into "recovery mode -> root shell prompt" and run:
```
adduser USERNAME admin
```
Note: No need to use 'sudo' here because you will already be root.

Greetings.

```
wordsmith@Ecanus:~$ groups wordsmith
wordsmith : wordsmith adm dialout fax cdrom plugdev lpadmin netdev admin nopasswdlogin sambashare vboxusers jupiter

```  

is this correct?

---

### Post by Krytarik on 2011-05-12
> **maddbaron said:**
> ```
wordsmith@Ecanus:~$ groups wordsmith
wordsmith : wordsmith adm dialout fax cdrom plugdev lpadmin netdev admin nopasswdlogin sambashare vboxusers jupiter

```is this correct?
As far as it states "admin", yes.

Can you run any other graphical app as root, with "gksu/gksudo", for example Nautilus?:
```
gksu nautilus
```

---

### Post by maddbaron on 2011-05-13
> **Krytarik said:**
> As far as it states "admin", yes.

Can you run any other graphical app as root, with "gksu/gksudo", for example Nautilus?:
```
gksu nautilus
```

i got annoyed with maverick so i upgraded to natty... things running smoother now. thank you for your help and responding.

---

### Post by BHunsaker on 2011-05-29
I'm in the same boat with natty.

I can run nautilus with gksu no problem.  My user is a member of the admin group.

It does look like there are some permission problems, as I can't add or delete users or go to advanced settings in the "Users settings" dialog. But, I used the command line adduser to create a new user and added it to the admin group and this new user has all the same problems.

---

### Post by Krytarik on 2011-05-29
BHunsaker, are you running these tools from within Gnome (incl. Unity)?

If not, they won't work, because they rely on the Gnome PolicyKit.

If yes, check if these processes are running:
```
krytarik@krytarik-desktop:~$ ps ax |grep -v grep |grep policy
 1430 ?        S      0:00 /usr/lib/policykit-1/polkitd
 1624 ?        S      0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
krytarik@krytarik-desktop:~$
```

---

