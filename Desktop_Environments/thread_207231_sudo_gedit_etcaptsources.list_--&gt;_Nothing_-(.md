---
title: "sudo gedit /etc/apt/sources.list --&gt; Nothing :-("
date: 2006-07-01
forum: Desktop Environments
---

### Post by Banter on 2006-07-01
I'm a college student trying to switch from windows to linux.

I love ubuntu, but when i open my terminal and type in . . .
```
sudo gedit /etc/apt/sources.list
```
. . . nothing happens. The terminal just sits there and nothing opens up. Its really odd. Does anyone know what the deal is?

Thanks.

---

### Post by aysiu on 2006-07-01
Just sits there...? Or does it go to the next line? In other words, are you seeing this? ```
banter@ubuntu:~$ sudo gedit /etc/apt/sources.list


``` Or are you seeing this? ```
banter@ubuntu:~$ sudo gedit /etc/apt/sources.list
banter@ubuntu:~$
```

---

### Post by Banter on 2006-07-01
aysiu,

I'm seeing the first one. It just hangs there and does not move to the next line.

---

### Post by aysiu on 2006-07-01
Well, let's see if it's a *sudo* thing or a *gedit* thing.

Can you try this and see if it hangs? ```
sudo nano /etc/apt/sources.list
```

---

### Post by bukwirm on 2006-07-01
Try 'sudo nano /etc/apt/sources.list'

Edit: My goodness, simultaneous posting.

---

### Post by Banter on 2006-07-01
sudo nano works fine.

By the way, firefox doesn't work well w/ my WPA connection, so im using a hit-or-miss connection from a neighbor's house. So if i'm silent for a while, that is why. Also, this is a clean install. The previous clean install to this had the same problem. FYI

---

### Post by Banter on 2006-07-01
sudo nano works fine.

By the way, firefox doesn't work well w/ my WPA connection, so im using a hit-or-miss connection from a neighbor's house. So if i'm silent for a while, that is why. Also, this is a clean install. The previous clean install to this had the same problem. FYI

---

### Post by aysiu on 2006-07-01
Okay. So it's not a *sudo* problem. It must be gedit then. What happens if you type ```
gedit
``` or ```
gedit /etc/apt/sources.list
```?

---

### Post by Banter on 2006-07-01
```
gedit
```
causes gedit to open an unsaved document

```
gedit /etc/apt/sources.list
```
causes sources.list to open

---

### Post by aysiu on 2006-07-01
That makes things really weird, then.

So Gedit by itself works.
Gedit with /etc/apt/sources.list works.
Nano with /etc/apt/sources.list works with root privileges.

But Gedit with /etc/apt/sources.list doesn't work with root privileges.

Hm.

One last test: ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Banter on 2006-07-01
```
banter@localhost:~$ gksudo gedit /etc/apt/sources.list

(gedit:5972): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

causes gedit to open, but it freezes and needs a force quit. nothing shows up in the gedit window inlcuding file, edit, view, etc.

I tried to take a screen shot, but that crashed too!

---

### Post by aysiu on 2006-07-01
I have no idea what's wrong.

Can you *gksudo gedit* or *sudo gedit* any other files? /etc/fstab, for example?

---

### Post by Banter on 2006-07-01
those actions produce the same results

---

### Post by aysiu on 2006-07-01
So something weird with launching gedit with root privileges...

Hm. [I found someone with the same problem in Breezy](http://ubuntuforums.org/showthread.php?t=77283). Unfortunately there was no solution posted in that thread.

---

### Post by Banter on 2006-07-01
presently, i used nano to update my sources.list. I got the list from a list generator at linux something something.nl. I'm hoping i get the downloads done before this awful connection putters out again.

---

### Post by Banter on 2006-07-01
```
banter@localhost:~$ time sudo gedit /etc/apt/sources.list
Password:

real    0m1.808s
user    0m0.124s
sys     0m0.032s
banter@localhost:~$
```

and nothing pops open. huh.

---

### Post by aysiu on 2006-07-01
Unfortunately I have no clue how to solve this. Since no error messages appear, it's a hard problem to diagnose. It also appears to be a fairly obscure problem, as I was able to turn up only one other thread about it, and it had no solution.

You may just have to deal with *nano* for now. I'm sorry!

---

### Post by Banter on 2006-07-01
thanks for you help aysiu. I'm updating and hoping the problem will work itself out.

---

### Post by tturrisi on 2006-07-01
are you already logged in as root?

---

### Post by Activa on 2006-07-07
Hi, I have the same problem also.

Additionally, if I try to run gedit from root I get this error message

cannot open display: (null)

Richard

---

### Post by keithweddell on 2006-07-07
This is a problem with the DISPLAY environment variable.  I don't know how to fix it but running set | grep DISPLAY may give you somewhere to start from.
Good luck

Keith

---

### Post by Activa on 2006-07-08
That returns

DISPLAY=:0.0

I'm a bit out of my depth here I think
Richard

---

### Post by maguss on 2006-09-14
Hi there,

I have found this thread after searching for solution on this problem as I am experiencing exactly the same issue with gedit as Banter did/does.

Does someone figured it out how to fix this?

Cheers,
Luki

---

### Post by maguss on 2006-09-15
Got it!
Don't ask me why (I'll appriciate any explanation), but when I enabled

```
auto lo
iface lo inet loopback
```

in /etc/network/interfaces and rebooted, finally sudo gedit started to work!

First check if turning off network interfaces helps, if so, try with the loopback.

Cheers,
Luki

---

### Post by mungy on 2006-10-21
I had this problem.

After reading this thread I checked my networking and I noticed my wireless card was activated as well as my usual lan. I remember trying to get wireless to work without any success. I just checked the settings and discovered that the key was set as text instead of hex. That changed I unplugged the wire and I was suddenly wireless. I then disabled the normal lan.

now sudo gedit works 8) 

cheers :KS

---

### Post by airtonix on 2006-10-21
i have a workaround .....
```

sudo apt-get install leafpad 

```or 

```

sudo apt-get install mousepad 

```see if those behave proplery with the sudo prefix

edit : oh yeah...it may laso be realted to the fact that gedit has more file access types to choose from than nano probably would...

like you can open a file remotely through ssh, smb, ns, ftp etc etc

oh and if you have bookmarks that are remotes filesystems, then gedit will want to probe each one, sooo this could e part of the problem.....what not having proper network access.

wierd *** problem, but when you consider all thigns it really isnt, just obscure like aysiu says.

---

### Post by robrmd9 on 2006-10-25
> **maguss said:**
> Got it!
Don't ask me why (I'll appriciate any explanation), but when I enabled

```
auto lo
iface lo inet loopback
```

in /etc/network/interfaces and rebooted, finally sudo gedit started to work!

First check if turning off network interfaces helps, if so, try with the loopback.

Cheers,
Luki

This solution worked for me, and also caused several other applications (such as gkrellm) that were experiencing delays starting up to act as they should.

Gedit works again!

---

