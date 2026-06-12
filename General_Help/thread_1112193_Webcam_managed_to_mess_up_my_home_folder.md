---
title: "Webcam managed to mess up my /home folder?"
date: 2009-03-31
forum: General Help
---

### Post by TyrantWave on 2009-03-31
Today I bought myself a webcam (Microsoft VX 1000), as my other one does not work under ubuntu.

So first problem here, the inbuilt microphone of the webcam doesn't work.
After some fiddling around, it seems I cannot get *any* microphone to work, which annoyed me.

However, all I was going to do was return the webcam and just forget about streaming.

After rebooting my computer, however, I now get this error:

> GDM could not write to your authorisation file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator.

What the hell?
I know I've got the disc space (55GB), and I *am* the sys admin on this laptop.
The last thing I installed as alsa-oss, which was recommended to get microphones to work when ALSA doesn't.

I'm running Ubuntu 8.10 Hardy, on a 1.6GHz, 1GB RAM laptop, if that helps anyone.

So any ideas? I do not want to have to reformat this laptop *again*.

---

### Post by kanikilu on 2009-03-31
Can you boot up in recovery mode to check the permissions of your home folder as well as check disk usage?

If you're not dual-booting, shortly after turning on the computer, press ESC to get to the grub boot menu. Select a recovery mode. When that starts, you can either try one of the repair options, or drop to a root shell.

If you go to a root shell, check the permissions on your home folder:```
cd /home
ls -l
```
Then check your disk free space:```
df
- or -
df -h
```

---

### Post by TyrantWave on 2009-03-31
Tried the recovery options now, tried the dpkg fixer and fdisk check.

As a root terminal, if I do ls -l on my home/ directory, it says:

> total 0

Haven't run the df command yet (I'll do it after this post).

Now when I boot the computer I get this error message:

> Your home directory is listed as: '/home/chris' but it does not appear to exist. Do you want to log in with the / (root) directory? It is unlikely anything will work unless you use a failsafe session.

So I clock OK, then I get this error:

> User's $HOME/.dmrc file is being ignored. This prevents the current session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directoy must be owned by user and not writeable by other users.

I click OK here, and get the GDM error again, then it goes to the login window.
I can't log in as root as the password I have for my root user just doesn't work. =/.

On the LiveCD (Which I'm on now), it says the home/ folder is unreadable, and it's owner is root, and it's root is group.

Now to run the df and df -h commands..
Edit: The commands say that the root partition (My main comp) has 55GB free, and all other items listed have 496MB~500MB free.

---

### Post by TyrantWave on 2009-03-31
More info:

I ran these two commands (Which seems to be a fix for the $HOME error):

> sudo chmod 644 /home/chris/.dmrc
sudo chmod 755 /home/chris

And I'm still getting the same errors. =/.

---

### Post by kanikilu on 2009-03-31
From what it's saying, it's almost like your home directory is gone...I have no idea how that could be :?:

Perhaps it's not getting mounted? Do you know if you put /home in it's own partition? To find out, from a root terminal (recovery mode), check the output of ```
cat /etc/fstab
```

// Edit - You said you could chmod the /home/chris dir. If it's there, can you chown it to your user? ```
chown -R chris /home/chris
```

---

### Post by TyrantWave on 2009-03-31
The home directory isn't on another partition.

I've tried the chown as well, and this is the odd part: I simply get:

```
chown: invalid user: `chris'

```

Which I should have, as I was using it earlier today, and since I last installed Ubuntu too....

Running Nautilus as root on the LiveCD, it says that the owner (And group) of my /chris file is "1000". Which is kinda confusing.

I know the /chris folder is there, as root (In terminal or root nautilus), I can browse all the files freely and they're all present.

---

### Post by kanikilu on 2009-03-31
> **TyrantWave said:**
> The home directory isn't on another partition.

I've tried the chown as well, and this is the odd part: I simply get:

```
chown: invalid user: `chris'

```

Which I should have, as I was using it earlier today, and since I last installed Ubuntu too....

Running Nautilus as root on the LiveCD, it says that the owner (And group) of my /chris file is "1000". Which is kinda confusing.

I know the /chris folder is there, as root (In terminal or root nautilus), I can browse all the files freely and they're all present. Did you chown from the live cd or recovery mode? Because I don't think it will work from the live cd...

---

### Post by TyrantWave on 2009-03-31
LiveCD, I'll quickly try from the recovery mode.

---

### Post by TyrantWave on 2009-03-31
OK, it allowed me to change the ownership this time, but I'm still getting the same errors.

I'm thinking it might be to do with the permissions of /home?

I'm getting this when running ls -l:

```
drw-r--r--   3 root root  4096 2009-03-30 16:56 home

```

And this for when running ls -l inside home/:

```
drwxr-xr-x 107 1000 1000 4096 2009-03-31 16:58 chris

```

And lastly this for ls -l .dmrc:

```
-rw-r--r-- 1 1000 1000 28 2009-03-31 15:15 .dmrc

```

Also, the owner of home/ is root, as is the group.

(All this was ran on the LiveCD)

---

### Post by kanikilu on 2009-03-31
> **TyrantWave said:**
> OK, it allowed me to change the ownership this time, but I'm still getting the same errors.

I'm thinking it might be to do with the permissions of /home?

I'm getting this when running ls -l:

```
drw-r--r--   3 root root  4096 2009-03-30 16:56 home

```


I think not having execute on /home may be a problem. Even though read is on for group and other, I don't think those people can go into that directory without execute. From your recovery mode, try:```
chmod a+x /home
``` The other 2 look ok.

---

### Post by TyrantWave on 2009-03-31
Ok, something worked nicely here, I don't get the previous 3 error messages :D

However, now it gets to the point where it tries to log me in, and I now get this error message:

> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem

I checked the XSession error log and it says this:

> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default
mkdtemp: private socket dir: Permission denied.

Just one error to the next with me, hey? XD

---

### Post by kanikilu on 2009-03-31
Hmm...try ```
chmod 777 /tmp
``` You'll probably have to do this from the recovery console as well, unless you can mount your Ubuntu partition from the livecd.

---

### Post by TyrantWave on 2009-03-31
I could mount it from the LiveCD nicely :)

And it worked!

Finally back on my normal profile :D

You've been a tremendous help thanks ^.^

Now I suppose I should make a thread in the hardware section about my complete inability to get a mic to work o_O (USB Webcam microphone doesn't work [The webcam works fine], and hooking a mic to my microphone jack doesn't work either, despite what I try...)


Thanks again! Saved me from another reboot! :D

---

### Post by kanikilu on 2009-03-31
No problem :)

There may be some systemic issue that I'm not aware of, though...I haven't a clue why the /home *and* /tmp directories would have their permissions changed.

Just keep an eye out for more problems and check permissions first as that appears to have been the case here...

// Edit - Oh, and I can't even get my webcam to show *picture*...Creative Labs FTL :(

---

### Post by TyrantWave on 2009-03-31
Will do :)

I'll mark this as solved now.

---

