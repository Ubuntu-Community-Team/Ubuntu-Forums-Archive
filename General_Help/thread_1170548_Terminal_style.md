---
title: "Terminal style"
date: 2009-05-26
forum: General Help
---

### Post by Vors on 2009-05-26
I don't know how to change the gnome-termina style. it is to borring and unreadable.
 using another not privileged account everything is ok, i can see different colors for different type of files etc.
Tell me please where i can change this.

---

### Post by doas777 on 2009-05-26
well for gnome-terminal, just go to Edit -> Default Profile

don't know what to do for your "Terminator" app though.

---

### Post by s.fox on 2009-05-26
Hi,

Have you tried  right clicking over your terminal and then edit current profile?

Hope this helps.

-Ash R

---

### Post by raymondh on 2009-05-26
> **Ash R said:**
> Hi,

Have you tried  right clicking over your terminal and then edit current profile?

Hope this helps.

-Ash R

as a follow-on post, I've found transparency to my liking :)

regards,

---

### Post by mcduck on 2009-05-26
> **Vors said:**
> I don't know how to change the gnome-termina style. it is to borring and unreadable.
 using another not privileged account everything is ok, i can see different colors for different type of files etc.
Tell me please where i can change this.

So you can't see colors for things like file types any more? Have you done any changes to your ~/bashrc or ~/.profile files?

---

### Post by Mirge on 2009-05-26
> **mcduck said:**
> So you can't see colors for things like file types any more? Have you done any changes to your ~/bashrc or ~/.profile files?

I never had colors in Ubuntu or Kubuntu 9.04... wish I did :).

---

### Post by mcduck on 2009-05-26
> **Mirge said:**
> I never had colors in Ubuntu or Kubuntu 9.04... wish I did :).

Try running this: "ls --color=always". If your current terminal supports colors (as both Gnome's and KDE's default terminals do) you should see the output in colors.

If that works, but you don't normally have colors there's something wrong with your bashrc file.

---

### Post by Mirge on 2009-05-26
> **mcduck said:**
> Try running this: "ls --color=always". If your current terminal supports colors (as both Gnome's and KDE's default terminals do) you should see the output in colors.

If that works, but you don't normally have colors there's something wrong with your bashrc file.

Oh my beloved colors that I've always wanted again!

Any idea how to add colors permanently? My ~/.bashrc is empty...

mike@mike-kubuntu:~$ cat ~/.bashrc

mike@mike-kubuntu:~$ ls -la ~ | grep .bashrc
-rw-r--r--  1 mike  mike        1 2009-05-22 17:35 .bashrc
mike@mike-kubuntu:~$

---

### Post by Mirge on 2009-05-26
bump

---

### Post by CatKiller on 2009-05-26
It's considered impolite to bump a thread more than once a day.

You could try renaming your .bashrc to .bashrc.backup to see if logging out and logging back in will give you a new one from the defaults, and if that doesn't work try copying the .bashrc from the other user, or from /etc/skel (which is the location for default settings for new users).

---

### Post by Mirge on 2009-05-26
My apologies for being rude! I was unaware of that unwritten rule.

Your advice did work, thank you!

cp ~/.bashrc ~/.bashrc.backup
cp /etc/skel/.bashrc ~/.bashrc

Closed Konsole, re-opened... voila. Many thanks.

---

### Post by CatKiller on 2009-05-26
No worries. Glad to help.

---

### Post by Vors on 2009-05-27
thx everybody.
I was very surprised to see  no .bashrc file in ~/  :)

so, > cp /etc/skel/.bashrc ~/.bashrc
 did work.
Thx, CatKiller.

---

