---
title: "[SOLVED] HELP! HELP!  Can't get gconfd or anything to run"
date: 2008-12-21
forum: Desktop Environments
---

### Post by tipiglen on 2008-12-21
I was shutting down and suddenly there was a power cut.

On restart, I get to normal login screen, username, password, usual wait for music, then blank black screen, and a message telling me > Failed to contact configuration server; some possible causes are that 
you need to enable TCP/IP networking for ORBit, or you have stale NFS locks 
due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. 

and another saying the power manager cannot be started and I ahould se my administrator )that's me, and I'm clueless)

In shell terminal as root, I can't get gconftool to spawn gconfd

I'm in bloody windoze just to get to the forum.

PLEASE SOMEBODY HELP!

I await a good Samaritan
ed

---

### Post by albinootje on 2008-12-21
> **tipiglen said:**
> I was shutting down and suddenly there was a power cut.

On restart, I get to normal login screen, username, password, usual wait for music, then blank black screen, and a message telling me 
and another saying the power manager cannot be started and I ahould se my administrator )that's me, and I'm clueless)

In shell terminal as root, I can't get gconftool to spawn gconfd

Can you boot in "recovery mode", "drop to root shell prompt",
and do this :
```

chown -R username:username /home/username
rm -r /tmp/orbit-*
rm -r /tmp/esd-*
init 2

```
where "username" is the name of your user.

---

### Post by tipiglen on 2008-12-21
> Can you boot in "recovery mode", "drop to root shell prompt",
and do this :
Code:

chown -R username:username /home/username
rm -r /tmp/orbit-*
rm -r /tmp/esd-*
init 2

where "username" is the name of your user. I'll try in a few minutes when I go back to linux.  I don't thing I have those files in my /tmp directory.  I don't have a clue what orbit is.

I haven't looked to see why I might no longer oen my oen home directory, but I'll give it a try.

I'm getting very frustrated.  I tried ```
 /etc/init.d/gdm restart
```and all that happens is I get a login screen which won't accept input.  Ctrl/Alt/f1 gets me back to shell, ...

```
find -name gconfd
```gets nothing.

Grrrrr!
ed

---

### Post by albinootje on 2008-12-21
> **tipiglen said:**
> I'll try in a few minutes when I go back to linux.  I don't thing I have those files in my /tmp directory.  I don't have a clue what orbit is.


Can you install the following :
```

sudo apt-get install icewm

```
And then choose "icewm" as "session" at the gdm screen.
Then you have a better change to log in and fix things.

And do you have any files in /lost+found ?

---

### Post by Aearenda on 2008-12-21
I'd be doing what albinootje said in the first post, assuming the fsck stage of startup works without complaint :-)

---

### Post by tipiglen on 2008-12-21
well, I got in with ```
/etc/init.d/gdm restart
```(somehow), by opening "another" X.

Seems to be working OK, but I don't know what happens if I shut down and restart... we'll see in a few moments.

I'll check out icewm later perhaps

I'll check back in awhile (If I can get back)

;-)
ed

---

### Post by tipiglen on 2008-12-21
Back in just like nothing had happened.

I did do one **important** thing```
mv /home/ed/.gconfd/saved_state /home/ed/.gconfd/saved_state~  
```Which I think is the key to being able to re-start.  I reckon the saved_state file got corrupted due to the power cutoff during shutdown....

Now there's a new one.

I hope this may be of use to anyone else who has this problem

Thanks guys and gals for your thoughts

A happy ed
[http://ubuntuforums.org/images/smilies/icon_razz.gif](http://ubuntuforums.org/images/smilies/icon_razz.gif)

---

### Post by albinootje on 2008-12-21
> **tipiglen said:**
> Back in just like nothing had happened.

I did do one **important** thing```
mv /home/ed/.gconfd/saved_state /home/ed/.gconfd/saved_state~  
```

Good! :)

I still recommend checking whether there are any files in /lost+found to get an idea whether you lost some files after that sudden shutdown.

---

### Post by tipiglen on 2008-12-21
Lost + Found is empty.  Thanks.

Happy Solstice (+1)
ed

---

### Post by iFrag_svk on 2008-12-29
Thank you, I had the same problem.
mv /home/username/.gconfd/saved_state /home/username/.gconfd/saved_state~
solved it. :)

---

