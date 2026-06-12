---
title: "Failed to Initialize HAL"
date: 2009-03-12
forum: General Help
---

### Post by Liesmith Loki on 2009-03-12
Hey guys. Ubuntu has been working fine for me for a while, but then a couple of days ago, out of the blue, an error pops up at startup and says "Failed to Initialize HAL", and there's no internet connection.

This was soon followed by a need to run a manual FSCK since there were some disk inconsistencies which auto disc check couldn't fix, which I did, so now at the very least, it boots up to the desktop now, but the Failed to Initialize HAL still appears, and still not network connection.

My network is connected directly to my computer through ethernet cable.

I've tried to restart HAL, but it says:

rm: cannot remove `/usr/share/hal/fdi/policy/gparted-disable-automount.fdi': Not a directory.

Can I get any help on this? And I don't have a net connection like I said before, so I can't use apt-get to reinstall it.

---

### Post by Neo_The_User on 2009-03-12
> **Liesmith Loki said:**
> Hey guys. Ubuntu has been working fine for me for a while, but then a couple of days ago, out of the blue, an error pops up at startup and says "Failed to Initialize HAL", and there's no internet connection.

This was soon followed by a need to run a manual FSCK since there were some disk inconsistencies which auto disc check couldn't fix, which I did, so now at the very least, it boots up to the desktop now, but the Failed to Initialize HAL still appears, and still not network connection.

My network is connected directly to my computer through ethernet cable.

I've tried to restart HAL, but it says:

rm: cannot remove `/usr/share/hal/fdi/policy/gparted-diable-automount.fdi': Not a directory.

Can I get any help on this? And I don't have a net connection like I said before, so I can't use apt-get to reinstall it.

```

sudo /etc/init.d/hal stop
sudo /etc/init.d/hal start
sudo /etc/init.d/hal restart

```

I got this error before when compiling a super small kernel around 650K and networking didn't work.

In case your resolutions are acting weird go into terminal and type in this command, then the next one when you dont have a GUI up.

```

sudo /etc/init.d/gdm stop
sudo Xorg -configure

```
Where it says if you want to test your displays type X -config /root/xorg.conf.new type in this command:
```

sudo cp /root/xorg.conf.new /etc/X11/xorg.conf

```

---

### Post by Liesmith Loki on 2009-03-12
> **Neo_The_User said:**
> ```

sudo /etc/init.d/hal stop
sudo /etc/init.d/hal start
sudo /etc/init.d/hal restart

```

I got this error before when compiling a super small kernel around 650K and networking didn't work.

In case your resolutions are acting weird go into terminal and type in this command, then the next one when you dont have a GUI up.

```

sudo /etc/init.d/gdm stop
sudo Xorg -configure

```
Where it says if you want to test your displays type X -config /root/xorg.conf.new type in this command:
```

sudo cp /root/xorg.conf.new /etc/X11/xorg.conf

```

My resolutions seem fine. But when I stop and start HAL manually, it still comes up with the thing about not being able to remove the gparted-disable-automount.fdi.

---

### Post by Neo_The_User on 2009-03-12
oh use the --force command. it wipes anything out.

```

sudo rm -rf --force /usr/share/hal/fdi/policy/gparted-diable-automount.fdi

```

It will be removed gaurenteed!

---

### Post by Liesmith Loki on 2009-03-12
> **Neo_The_User said:**
> oh use the --force command. it wipes anything out.

```

sudo rm -rf --force /usr/share/hal/fdi/policy/gparted-diable-automount.fdi

```

It will be removed gaurenteed!=[ Same error still pops up.

---

### Post by Neo_The_User on 2009-03-12
thats the weirdest thing ever. it shouldn't even be verbosing.

```

gksudo nautilus

```

Remove it graphically by hand. If it's not there and --force says it isn't, no idea.

chmod 000 gparted-disable-automount.fdi Path to it is /usr/share/hal/fdi/policy/

---

### Post by Liesmith Loki on 2009-03-12
> **Neo_The_User said:**
> thats the weirdest thing ever. it shouldn't even be verbosing.

```

gksudo nautilus

```

Remove it graphically by hand. If it's not there and --force says it isn't, no idea.

chmod 000 gparted-disable-automount.fdi Path to it is /usr/share/hal/fdi/policy/
The only thing in my hal folder is device-manager, and fdi which are both text files and not folders, so it's right in saying that those directories are not there. I think I need to reinstall HAL, but I can't use apt-get.

---

### Post by Liesmith Loki on 2009-03-12
Anyone else with any tips?

---

### Post by Neo_The_User on 2009-03-12
synaptic > hal > complete removal > install

---

### Post by Liesmith Loki on 2009-03-12
> **Neo_The_User said:**
> synaptic > hal > complete removal > install
Are you sure I should remove HAL? I heard you really shouldn't do that.

---

### Post by Liesmith Loki on 2009-03-12
> **Liesmith Loki said:**
> Are you sure I should remove HAL? I heard you really shouldn't do that.

Another thing. I tried to do it, but like I said I don't have an internet connection, so it's not working. =/

---

### Post by Liesmith Loki on 2009-03-13
Um. Bump. I still need help with this.

---

### Post by Liesmith Loki on 2009-03-13
Bump. Anyone?

---

### Post by Liesmith Loki on 2009-03-13
Bump.

---

### Post by Liesmith Loki on 2009-03-13
Can't someone help me out, seriously? >=[

When I try to reinstall via Synaptic, it attempts to download something through the internet which I can't do since it's disabled, and I get the error

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.9.1-6ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.9.1-6ubuntu5_i386.deb)
  Could not resolve 'us.archive.ubuntu.com'.

I've tried the trick where you put in a CD before boot up, and that doesn't work. I've tried reinstalling HAL through Ubuntu Live CD but I still get the same errors, even though when I'm running through Ubuntu LiveCD, I can access the internet.

PLEASE RESPOND.

---

### Post by Liesmith Loki on 2009-03-13
Bump.

---

### Post by Liesmith Loki on 2009-03-13
Can't anybody answer my question PLEASE?!

---

### Post by Liesmith Loki on 2009-03-13
Is there a reason why this thread is being ignored?

---

### Post by Liesmith Loki on 2009-03-13
Bump! D=<

---

### Post by Liesmith Loki on 2009-03-13
bump.

---

### Post by mercenaryhmster on 2009-03-13
dude, stop bumping your topic, and delete the second one you made.  if no one is answering you that means they don't know how to fix your problem.  wait, and your patience will be rewarded

---

### Post by Liesmith Loki on 2009-03-14
> **mercenaryhmster said:**
> dude, stop bumping your topic, and delete the second one you made.  if no one is answering you that means they don't know how to fix your problem.  wait, and your patience will be rewarded

If I wait, the thread will simply fall into the depths of the forum and be forgotten. =/

---

### Post by Liesmith Loki on 2009-03-14
Bump

---

### Post by Liesmith Loki on 2009-03-19
Bump

---

