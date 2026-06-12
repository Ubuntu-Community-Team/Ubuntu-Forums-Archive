---
title: "/etc/group file got wiped, trying to restore..."
date: 2009-03-01
forum: General Help
---

### Post by aliking on 2009-03-01
Hi, I'm hoping someone can help me this. 

Long story short, I lost my /etc/group file. So I used liveCD and copied the stock /etc/group file from there and replaced every instance of 'ubuntu' in it with my username. Now I can login again and sudo, but there are lots of things not working - NetworkManager and a lot of the configuration screens for e.g.

Question is: is my only option here to reinstall, or is there some way that I can reconstruct or regenerate what should be in this file? 

thanks, Al

---

### Post by aliking on 2009-03-01
You know, I'm assuming that the /etc/group file being wiped was the only problem, but that could be wrong. 

So, for context, what happened was this:
I went to Administration > Users and Groups applet to check what groups I was in (I'm running mythtv and wanted to check I was in the mythtv group). After unlocking there were no groups in my list, so I added one called mythtv. I put my username and root into the group, those were the only users there. 

Then i stopped being able to sudo. So I followed some instructions here: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo) to restore sudo access. That was when I found out that the admin group did not exist. Looks like the Users and Groups applet failed to load all groups and then when I added one in and closed, it rewrote the group file with JUST the group I added then. so maybe the Applet also did some other stuff i haven't seen.

I'm fully prepared to admit that this is user error, but doesn't this sound like a bug in the Users and groups applet?

---

### Post by aliking on 2009-03-01
last ditch before a reinstall, which I really don't want to do, I'm going to try to dpkg-reconfigure some of the bigger packages like ubuntu-desktop and NetworkManager. 

Any others that might be good?

---

### Post by aliking on 2009-03-01
Update:

maybe I'd have got more responses if I'd posted this somewhere other than the General section.

Anyway, solved and resolved, I took my first step away from n00b by not reinstalling at the first all-nighter sign of trouble. For anyone experiencing similar troubles, this is what did it for me:

I found out in my searches about /var/backups, very useful, there are a number of files in there including /var/backups/group.bak and /var/backup/passwd.bak

**n.b. all commands below are from memory and should be taken as pointers, not copied verbatim without knowing what you're doing**

so far so good, I copied the potentially buggered files just in case:
```
sudo cp /etc/group /etc/group.bork
sudo cp /etc/passwd /etc/passwd.bork
```

and swapped in the backups - i guess I was lucky that these were good, your mileage may vary:
```
sudo cp /var/backups/group.bak /etc/group
sudo cp /var/backups/passwd.bak /etc/passwd
```

then I banged my head against a wall for an hour or so and tried a bunch of things. What I should have done right away was this:
```
sudo chmod --reference=/etc/group.bork /etc/group
sudo chmod --reference=/etc/passwd.bork /etc/passwd
```
which copies the permissions from the old group and passwd files to the newly restored backups - essentially so that they can be read. The --reference option of chmod was a new one on me, very useful.

Well I hope that this helps someone. By the way, does anyone have a view on whether this is likely a bug in users-admin (the Users and Groups applet)? I don't know enough to make that call, but I know I won't be using it again...

---

### Post by master5597 on 2010-02-10
Sorry to wake up an old thread, but I had the same problem. I found this post very useful and actually found and fixed my problem with the help of Milan Bouchet-Valat.  The info is at [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/160862](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/160862)

But my basic problem was that some update made my group file invalid. (see format spec here [http://www.debianhelp.co.uk/passwordfile.htm](http://www.debianhelp.co.uk/passwordfile.htm) )

audio:x:29:pulse:username
should actually be
audio:x:29:pulse,username

It also wiped my /etc/gshadow file, besides the noted /etc/passwd and /etc/group files.

---

