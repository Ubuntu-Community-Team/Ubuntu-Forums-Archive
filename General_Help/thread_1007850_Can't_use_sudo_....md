---
title: "Can't use sudo ..."
date: 2008-12-10
forum: General Help
---

### Post by Bucky Ball on 2008-12-10
Hi all,

I've done something dumb. I was setting up my dv camera and trying to use the controls in the gui to manipulate the camera (ff, rew, play etc) inside kino (and cinelerra). The controls worked sometimes. So I found a site with some instructions which may make this more possible. Part of the procedure was to create a group named 'firewire' and put myself into that group. So, I went about doing that, but for some reason, I decided to put 'root' in that group as a user also.

Not a good idea. Next time I try to sudo anything, not allowed, not is sudoers group!

So, not sure what has happened but all I do know is that when I go to users and groups, I can't unlock the group named 'firewire' to delete it, take root out or anything else. It seems to be acting the same way as root (shaded and impenetrable!).

I've hunted about and am about to get back into doing that, but has anyone got any ideas how I might resolve this quickly? I need to get that machine back to stable so I can finish the vid project I am working on within the next couple of days. This is my first foray into dv editing in Linux so there is bound to be some teething problems, especially with an 'idiot outside'! From memory (something similar has happened in the early days), I need to use vi or vim? All clues gratefully accepted ... :)

---

### Post by Bucky Ball on 2008-12-11
Okay, I have just read this:

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

... and realise perhaps my problem may be something I am going to need to solve elsewhere. Sorry if I have breached any guidelines, but the information I am looking for seems to be heading to that end ... I need to get into /etc/groups and delete that 'firewire' group and check in /etc/sudoers to make sure all is well there. Both completely impossible if you get an error:

```
Username is not in the sudoers file. This incident will be reported.
```everytime you try to use sudo! :(

ps: Can't boot any of the kernels now so I have the day's work cut out. Let's me login as root when I drop to recovery shell, but that is it. Still no sudo, same error. Think I might just install server, Xfce then Ubuntu Studio packages instead and see how that goes. Add Open Office, OpenBox ... might be a whole lot easier!

Cheers all ... :tongue:

---

### Post by adult swim on 2008-12-11
whenever you go to users and groups from the menu, are you able to click the unlock button and then enter in your password from there?

---

### Post by aysiu on 2008-12-11
When you're in the root recovery console, you can add yourself back into the sudoers group.

More details here:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Bucky Ball on 2008-12-11
Thanks for that, aysiu. In recovery as root. Can get to /etc/sudoers and everything looks right. When I try to apply the fix:

```
adduser username admin
```

... gives the message

```
adduser: the group 'admin' does not exist.
```

I also changed my defaults to look like those on the link:

```
# Defaults 
 Defaults        !lecture,tty_tickets,!fqdn

```

and added

```
env_reset
```

which was already there before the changes. No difference.

All the problems started when I added the 'firewire' group, added my username and root to that and 'chmod 666' for the permissions. I figure if I can delete the 'firewire' group things may right themselves but can't find it.

Tnx for the help ... :)

---

### Post by aysiu on 2008-12-11
You can edit /etc/group to take out *firewire* and make sure *admin* is in there.

---

### Post by Bucky Ball on 2008-12-11
Thanks for that. Sorry about the delay, it is raining over here and roof started to leak! I noticed a wet patch right next to the power board about an inch and a half away from an empty socket!!! That was real lucky.

I have moved a few things and have a bucket in place so apart from the water torture, set to try out your suggestion ... Cheers and will let you know.

* UPDATE: Okay, opened file /etc/group and this is what I have:

```
root:x:0:
nogroup:x:65534:
```and nothing else. Odd, no sign of 'firewire' group. Do I just add 'admin' to the end of that?

Tried adding 'admin' as the last entry in that file, saved then ran:

```
adduser username admin
```

and same result as last time:

```
adduser: the group 'admin' does not exist
```

?

---

### Post by Bucky Ball on 2008-12-11
By running:

```
addgroup -system admin
```

I successfully added the group, added my username to the group and now have 'sudo' operating again. A step in the right direction so sincere thanks. 

Now I am getting this message:

```
chown: invalid group: 'klog:klog'
```

So, there was no 'firewire' group in there, as I mentioned, so perhaps not that screwing it up. Probably to do with the 'chown 666' permission change that was supposed to affect the 'firewire' group but maybe has affected something else. I will plough ahead but may be time to re-post under another heading  ... ?

Incidentally, this last error message is as far as I am getting at the moment - still can't get to the login, let alone desktop.

---

### Post by nothingspecial on 2008-12-11
Maybe not the best advice but I always use ```
gksudo kino
```.
This lets Ubuntu access your camera through firewire.
Then it`s just a matter of permissions with the video file when you`ve finished.

Never had a problem with that method.

---

### Post by Bucky Ball on 2008-12-11
> **nothingspecial said:**
> Maybe not the best advice but I always use ```
gksudo kino
```.
This lets Ubuntu access your camera through firewire.
Then it`s just a matter of permissions with the video file when you`ve finished.

Never had a problem with that method.

Thanks for that. When I eventually get back to the stage where I open Kino again, I'll try it.

So, when the login screen eventually came up, I had the choice of logging in as my usual user name or ... firewire! So 'firewire' has become a user on my machine and, of course, a root user that I can't do anything about deleting when I try going through:

System->Admin->Users and groups

When I look for that user elsewhere, nowhere to be found. Has no password, no trace.

Things are getting a bit messed up here, but this *is* my experimental plaything machine. Just attempted installing Ubuntu minimal, but that crashed, so might go Xubuntu and load the Studio bits I need in with that (rt kernel and apps) and try not to screw up next time I get to adding myself to the 1394 group!

Thanks all. :)

If anyone has got any suggestions as to what has gone on though, I would still be curious to hear them ... looks like my /etc/group file is basically empty in comparison with all others I am seeing so don't really know what has happened here.

---

