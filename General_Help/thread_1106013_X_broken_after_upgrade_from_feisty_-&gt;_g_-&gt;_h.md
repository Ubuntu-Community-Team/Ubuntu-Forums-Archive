---
title: "X broken after upgrade from feisty -&gt; g -&gt; h -&gt; intrepid"
date: 2009-03-25
forum: General Help
---

### Post by hickninja on 2009-03-25
I booted an old system I had feisty on, upgraded it to gutsy, then hardy, then intrepid, and now X is broken and it boots into "low graphics mode" no matter what I do. I have tried forcing reinstalls of all xorg-related things, including drivers, all to no avail.

The problem is that X crashes with the following during boot:

(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed

<backtrace here>

lspci shows me:

VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

This happens no matter what driver I try to use, and even if I use the default xorg.conf. Any ideas?

Thanks!

---

### Post by Therion on 2009-03-25
I'd suggest a fresh install.  

I've done dist-upgrades in the past and have widely varying degrees of success (or just as commonly, failure) with them.  I always recommend a fresh install, especially when spanning that many release versions.

---

### Post by theDaveTheRave on 2009-03-25
are you able to test the system with an intrepid live cd?

maybe this "old" system can't handle the new graphics drivers, I don't know how, but are you able to "blacklist" the newer graphics drivers and force the use of an "old" one?

I'm not sure if this helps at all... but maybee it will give you an idea for a solution?

David

---

### Post by hickninja on 2009-03-25
> **Therion said:**
> I'd suggest a fresh install.  

I've done dist-upgrades in the past and have widely varying degrees of success (or just as commonly, failure) with them.  I always recommend a fresh install, especially when spanning that many release versions.
I have a lot of data lying around in various places that I don't want to blow away. I guess I could figure out where all of it is, back it up somewhere, then do a fresh install. It's just a bit of a hassle. I was hoping there was some way to do a "nuke everything X related and reinstall it" kind of solution.

In the future, maybe I'll mount /home on another partition and just do clean installs.

---

### Post by theDaveTheRave on 2009-03-27
hickninja.

If you have a load of data in your /home you could try the following.

create a tar of the whole of the /home, and copy it to a spare hdd.

then you should be able to do a fresh install without loosing anything important.

You can even tar directly to a networked drive (or alternatively mount a networked drive into a sub-directory, and then tar into that).

Other alternatives:

move to a different tty (normaly using the alt-F(key) ) to get a new logon.
Then from this teletype (tty) you can use top and kill the current running x session.

then try re-starting x, that may solve the problem of the graphics, but I don't know?

If not, you should be able to uninstall the whole of the x-windowing system, then do a fresh install of it (I would recomend a reboot in between, just to be sure).

Things to bear in mind. You will lose your graphical login, so you will have to add a line to the GRUB for you to be able to login to a "console" (an old fashioned black screen), I can't advise how to do this but the info is out there on the forums somewhere, as I was going to do it for our works server - so it didn't have the overhead of running a windowing system - but this just plain "scared" the boss when he saw a black screen with the single word <login> on it :lolflag:

David

---

