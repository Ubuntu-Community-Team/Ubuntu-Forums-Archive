---
title: "Running Kate as root"
date: 2006-01-07
forum: General Help
---

### Post by randal on 2006-01-07
I wanted to write a note and save it directly to my windows partition. Since only the administrator can write on that partition, opened the terminal then I ran Kate as root by typing: sudo kate.

It was unsuccessful. It reported:

[I]"/var/tmp/kdecache-<username>" is owned by uid 1000 instead of uid 0.
Link points to /var/tmp/kdecache-root[/I]

After, when I run kate as user (from the menu), it wouldn't appear.

Seeing the word "owned", I added the root to the user group where my user acount is. Then I:

*sudo chown :<usergroup> /var/tmp/kdecache-<username>*

which I really don't know if is a good thing to do. :p

---

### Post by aysiu on 2006-01-07
Try ```
sudo kwrite
``` instead or ```
kdesu kate
```

---

### Post by randal on 2006-01-07
May I ask what kdesu is?

---

### Post by aysiu on 2006-01-07
[QUOTE=randal]May I ask what kdesu is?[/QUOTE] So you know how if you want to run something in the terminal with root privileges, you say *sudo blah* and get prompted for your password *in the terminal*? If you have a command that says *kdesu blah* in KDE (or *gksudo blah* in Gnome), the password prompt will be in a graphical dialogue box, instead of in a terminal.

---

### Post by randal on 2006-01-08
Oh I see... Thanks.. But I think Kate has problem when ran as root. I can't get kdesu kate working... but running kwrite as root worked and got the job done.

---

### Post by jferrando on 2006-01-08
If you previosly ran kde apps (like kate) with sudo, some of the temporary files created can be with a wrong user id.
I corrected it in my machine with:

*$ chown -R mysername .kde*

---

