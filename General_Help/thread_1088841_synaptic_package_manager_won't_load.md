---
title: "synaptic package manager won't load"
date: 2009-03-06
forum: General Help
---

### Post by nikonfrz on 2009-03-06
i click on my synaptic package manager and it looks like it's going to load and then doesn't. i tried sudo apt-get remove synaptc and sudo apt-get install synaptic and it still won't load. i have tried restarting also. i'm not sure if for some reason i don't have permission to use it or if it's buggy

---

### Post by jmszr on 2009-03-06
nikonfrz,

         I had a similar problem where my Synaptic, Add/Remove, and Update Manager would start to load and then just fade away. The fix was:```
sudo rm /var/cache/apt/*.bin
``` Hope this helps.

---

### Post by kanikilu on 2009-03-06
Try ```
gksu synaptic &
``` from the terminal. Does it even ask for your password?

If that doesn't work, try another application that requires su, for instance ```
gksu update-manager &
```

When it "looks like it's going to load and then doesn't", can you see if it's maybe running in the background ```
ps -ef | grep synaptic
```

---

### Post by nikonfrz on 2009-03-06
i tried both of those and niether worked. this is what i got kanikilu:

```
vpkeebs@vpkeebs-laptop:~$ ps -ef | grep synaptic
vpkeebs   6985     1  4 12:28 ?        00:00:00 gksu /usr/sbin/synaptic
vpkeebs   6992  6924  0 12:28 pts/0    00:00:00 grep synaptic

```

---

### Post by kanikilu on 2009-03-06
Hmm, I think there should be a third process listed owned by root with just "synaptic"...

I might be barking up the wrong tree, but do you have problems using sudo elsewhere? Maybe try dropping to a root shell and then starting synaptic: ```
$ sudo -s
# synaptic
```

---

### Post by nikonfrz on 2009-03-06
well i went in terminal as su and did gksu synaptic & and it loaded the manager. but it still won't load from the system menu :\

---

### Post by kanikilu on 2009-03-06
Ok. You didn't answer one of my original questions, which was, when you use the menu icon, does it even ask for your password (when you use the menu icon)?

The menu icon is simply a launcher with the following command: ```
gksu /usr/sbin/synaptic
``` so the real question is, why doesn't that command work?

---

### Post by nikonfrz on 2009-03-06
oh i'm sorry. no it doesn't ask for a password. and i did gksu /usr/sbin/synaptic in terminal and it won't load. lol. i'm kinda confused:/

---

### Post by kanikilu on 2009-03-06
Alright. Out of curiosity, can you try "gksudo synaptic &" instead of "gksu". Do this from your shell, not root (don't do the previously mentioned "sudo -s" beforehand).

...I've never had that problem, so I'm just throwing things out there...

---

### Post by nikonfrz on 2009-03-06
i get this:

```
vpkeebs@vpkeebs-laptop:~$ gksudo synaptic &
[1] 9585
vpkeebs@vpkeebs-laptop:~$ 
```

---

### Post by kanikilu on 2009-03-06
So basically the same...

I found this suggestion in a bug report:

> I had the same problem on hardy and I found a solution.
Using
$ sudo gconf-editor
I went to /apps/gksu and checked the options "display-no-pass-info", "prompt" and "sudo-mode".

Maybe give that a shot...

Other than that, sorry man, I think I'm all out of ideas.

---

### Post by nikonfrz on 2009-03-07
So I'm bumping to see if anyone else can help me out. synaptic package manager and software sources won't load for me unless I use terminal commands. I've tried everything in this post thus far and I can get spm to open just not the way it should. it's not going to kill me it's just and inconvenience and possibly a bug?

---

### Post by nikonfrz on 2009-03-08
so i've read some other posts about synaptic pack manager not woring for others. can anyony explain the below? and i always have to su to do anything from terminal. why is this?

when i use kanikilu's command:
```
gksu synaptic &
```

i get this:
```
root@vpkeebs-laptop:/home/vpkeebs# gksu synaptic &
[1] 10560
root@vpkeebs-laptop:/home/vpkeebs# GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(gksu:10560): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

[1]+  Exit 1                  gksu synaptic
```

---

### Post by bobman on 2009-03-10
I have no other methods, but

sudo rm /var/cache/apt/*.bin

worked for me. Thanks. Also, I recently installed ntop. I'm not sure if that had anything to do with it or not, but it is the only thing I've installed lately.

---

