---
title: "df: `/root/.gvfs': Permission denied"
date: 2009-06-24
forum: General Help
---

### Post by t0p on 2009-06-24
I've recently installed eeebuntu on my eee pc 701.  I haven't finished installing all the apps I want yet.

I run **df -h** and get the following output:

```
t0p@machine:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  2.1G  1.5G  60% /
tmpfs                 246M     0  246M   0% /lib/init/rw
varrun                246M  116K  246M   1% /var/run
varlock               246M     0  246M   0% /var/lock
udev                  246M  152K  246M   1% /dev
tmpfs                 246M   84K  246M   1% /dev/shm
/dev/sdb1             3.8G  113M  3.5G   4% /home
/home/t0p/.Private    3.8G  113M  3.5G   4% /home/t0p/Private
df: `/root/.gvfs': Permission denied

```

That last bit - df: `/root/.gvfs': Permission denied - concerns me.  I never had that come up before.

So, I try **sudo df -h** and get this:

```
t0p@machine:~$ sudo df -h
[sudo] password for t0p: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  2.1G  1.5G  60% /
tmpfs                 246M     0  246M   0% /lib/init/rw
varrun                246M  116K  246M   1% /var/run
varlock               246M     0  246M   0% /var/lock
udev                  246M  152K  246M   1% /dev
tmpfs                 246M   84K  246M   1% /dev/shm
/dev/sdb1             3.8G  113M  3.5G   4% /home
/home/t0p/.Private    3.8G  113M  3.5G   4% /home/t0p/Private

```

As you can see, no mention of /root/.gvfs.  So what's it mean?

---

### Post by jimv on 2009-06-24
I don't know exactly what the file is used for, but it has always been inaccessible to me no matter what.  I'm pretty sure it's normal.

---

### Post by The Cog on 2009-06-24
It's a virtual directory - a kind of mapped drive. Its contents are only visible to the owner/creator of the mapping. It's probably normal, though I don't have an eeepc myself.

---

### Post by paxmark1 on 2009-06-25
Not sure about .root/.gvfs  but I use at times mc and go through ~/.gvfs to acess and trAansfer network storage on my router.

---

### Post by t0p on 2009-06-29
Well, this issue is no longer an issue.  Not because I consciously "fixed" it, but because it "fixed" itself - when I do the **df -h** command now, there is no mention of /root/.gvfs.  Why not?  I don't know.

I've been installing a fair bit of software recently - I installed the "base" version of eeebuntu, which comes with little in the way of apps - and I assume that the installation of one program or another sorted the problem out for me.

Thanks for the feedback, peeps.  Appreciated.

---

