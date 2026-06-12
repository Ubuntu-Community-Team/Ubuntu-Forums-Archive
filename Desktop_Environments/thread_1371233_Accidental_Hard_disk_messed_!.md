---
title: "Accidental Hard disk messed !"
date: 2010-01-03
forum: Desktop Environments
---

### Post by shortsightedPenguin on 2010-01-03
Hi everybody, actually I'm in need of help, kinda desperate. I have typed 

```

df

```
at my Ubuntu Jaunty Desktop Terminal and
```

/dev/sda5

```
I saw that it's 100% usage and I thought that was my VirtuaBox hard disk space. I know I'm a newbie OK, never really good at Linux. So, I didn't know what I typed, now when I turned on my Ubuntu Jaunty it went into a warning Disk space full and won't allow me to lock in. What can I do ?

---

### Post by MichealH on 2010-01-03
Do some research on that command on the Internet using your Live CD... Have you got it?

---

### Post by shortsightedPenguin on 2010-01-03
> **MichealH said:**
> Do some research on that command on the Internet using your Live CD... Have you got it?

No, MichealH I upgraded from a previous Hardy Heron version. What might have caused it? Is there a way to check what's going on? I'm sure there was ample of hard disk space in the desktop. It was ruined by my behavior towards Vbox hard disk space, gosh. 

If anyone with such experience know how, it'd be great else I have to boot into live Hardy CD? hmmmm used do do that months ago and I'm not really sure anymore if I can still understand the hard disk stuff on a live CD.

Any help will be grateful, thanks Micheal.

---

### Post by shortsightedPenguin on 2010-01-03
I just read the warning message above. I try to recall the links I visited it's here:
[http://maketecheasier.com/shrink-your-virtualbox-vm/2009/04/06](http://maketecheasier.com/shrink-your-virtualbox-vm/2009/04/06)

Is it malicious? That was pretty much what I did and now I can't log in my desktop anymore as it says disk space is full. 

?

---

### Post by SecretCode on 2010-01-03
Can you download and burn a Jaunty (or Karmic - just as good since you won't need to change grub) live cd on another computer?

I'd like to see the whole output of 
```
sudo fdisk -lu
```
and
```
df -h
```

---

### Post by SecretCode on 2010-01-03
Also, did you follow those recommendations (zerofree etc) in the vbox guest or in the host? Which is saying 'disk full'?

---

### Post by shortsightedPenguin on 2010-01-05
> **SecretCode said:**
> Also, did you follow those recommendations (zerofree etc) in the vbox guest or in the host? Which is saying 'disk full'?

Hi SecretCode, I have resolved by doing this:

While stuck at login during boot, do this on your keyboard:

Step 1```

Alt + Ctrl + F2

```

After bypassing, it asked to login with username and password, do so. And follow with
Step 2```

sudo apt-get clean

```

Reboot, and you are able to login again. Note, for Ubuntu version older than Jaunty, you might just need to alter the first step above that is doing this instead:
```

Alt + Ctrl + F1

```

The second step should be the same.

Thanks for your concern.

---

### Post by SecretCode on 2010-01-05
Cool, that freed up enough space to log in.

You might want to have a look at Applications > Accessories > Disk Usage Analyzer and see if there is still a lot of space being taken up - otherwise this will just happen again.

---

### Post by shortsightedPenguin on 2010-01-05
> **SecretCode said:**
> Cool, that freed up enough space to log in.

You might want to have a look at Applications > Accessories > Disk Usage Analyzer and see if there is still a lot of space being taken up - otherwise this will just happen again.

Note taken. Thanks SecretCode and I will post when I need help again, thanks very much !

---

### Post by shortsightedPenguin on 2010-01-07
NOTE:

My actual problem which was freeing up VirtualBox hard disk space has been resolved as well. I found out about this as I cleared spaces for one of my folders in \Home

---

### Post by garryknight on 2010-01-07
> **shortsightedPenguin said:**
> 
sudo apt-get clean


Since this freed up enough space, it's possible that there were a large number of .deb files in your /var/cache/apt directory. If your machine isn't on a network, so you don't need to keep the .debs for installing on another machine, you could run Synaptic, go into Settings, Preferences, Files, and choose the "Delete downloaded packages after installation" option. You might also want to consider installing bleachbit - a utility which "deletes unnecessary files to free valuable disk space, maintain
privacy and remove junk. It removes caches, temporary files, cookies and broken shortcuts."

---

