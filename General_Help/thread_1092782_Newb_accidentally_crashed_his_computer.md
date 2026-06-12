---
title: "Newb accidentally crashed his computer"
date: 2009-03-10
forum: General Help
---

### Post by julz7 on 2009-03-10
I was messing with the settings on my Ubuntu 8.10 computer, and I accidentally changed my home folder (in System>Administration>Users and Groups).... Nothing would open, and now whenever I start my computer and log in, it gives me four errors:

User's $HOME/.dmrc is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

Could not update ICEauthority file /.ICEauthority

There is a problem with the configuration server. (/user/lib/libgconf2-4/gconf-sanity-check2 exited with status 256)

Cannot create the directory "/.gnome2/share/fonts". This is needed to allow changing the mouse pointer theme.\

I can still log in using the "Failsafe Terminal" option, though. I tried creating a new user to see if it could log in, but it gave me the same errors.  Is there any way I can use the terminal to change my home directory back?

---

### Post by darco on 2009-03-10
The .dmrc error just popped up on me again after something like 6 mos. ago...

[http://ubuntuforums.org/showthread.php?t=1092085&highlight=.dmrc](http://ubuntuforums.org/showthread.php?t=1092085&highlight=.dmrc)

not sure about the other messages

darco

p.s. make sure you search the forums for help!

---

### Post by yeats on 2009-03-10
So do you remember what you actually did to your home directory? (rename it? move it?)  As long as you didn't remove it altogether, it should be just a matter of moving it back to /home/*your username*.

---

### Post by julz7 on 2009-03-10
> **chrissharp123 said:**
> So do you remember what you actually did to your home directory? (rename it? move it?)  As long as you didn't remove it altogether, it should be just a matter of moving it back to /home/*your username*.
I believe I accidentally changed it to just "/".  I didn't delete it (the folders in it show up when I use the commands "cd /home/julz" and "ls").

---

### Post by yeats on 2009-03-10
Okay, do the commands

```
ls /
ls /home
```

and post back what the output is (I understand that you can't copy/paste)

---

### Post by julz7 on 2009-03-10
I get:
```
julz@julzubuntu:/$ ls /
bin   dev  initrd.img     lost+found opt  sbin tmp vmlinuz
boot  etc  initrd.img.old media      proc srv  usr vmlinuz.old
cdrom home lib            mnt        root sys  var
julz@julzubuntu:/$ ls /home
julz
```

---

### Post by yeats on 2009-03-10
> **julz7 said:**
> I get:
```
julz@julzubuntu:/$ ls /
bin   dev  initrd.img     lost+found opt  sbin tmp vmlinuz
boot  etc  initrd.img.old media      proc srv  usr vmlinuz.old
cdrom home lib            mnt        root sys  var
julz@julzubuntu:/$ ls /home
julz
```

Hmm.  Okay.. so when you do

```
echo $HOME
```

what do you get?

Also do:

```
grep julz /etc/passwd
```

while you're at it (editing out any personal information you wouldn't want the world to see) :-)

---

### Post by julz7 on 2009-03-10
> **chrissharp123 said:**
> Hmm.  Okay.. so when you do

```
echo $HOME
```

what do you get?

I just get "/".  Lemme guess... I somehow change it to say "/home/julz"?

EDIT: For "grep julz /etc/passwd", I get:
```
julz:x:1000:123:(my name here),,,:/:/bin/bash
```

---

### Post by Peasantoid on 2009-03-10
I think should be able to modify /etc/passwd to change your home directory. See the ":/:" part before it says /bin/bash (or whatever your shell is)? Change that to ":/home/julz:" so it reads something like "some_random_stuff:/home/julz:/bin/bash".

---

### Post by yeats on 2009-03-10
> **julz7 said:**
> I just get "/".  Lemme guess... I somehow change it to say "/home/julz"?

Exactly.  Do this:

```
sudo nano /etc/passwd
```

and find the line that says julz and edit it to look something like this:

```
julz:x:1000:1000:*[Real Name]*,,,:/home/julz:/bin/bash
```

Where *[Real Name]* is your name listed in the file.  Then save and reboot.  That *should* do it.

---

### Post by julz7 on 2009-03-10
Thanks! It worked, and everything is exactly as it was before it crashed (except for the screen resolution, but I can fix that).

---

### Post by yeats on 2009-03-11
Awesome.  Glad it was so simple to fix. ;)

---

