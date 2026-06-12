---
title: "NWN1 resolution problem."
date: 2007-01-29
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2007-01-29
I have a small problem with resolution in neverwinternights1

I cannot change to higher resolution then my current Ubuntu desktop resolution even if it's supported.

I have my desktop resolution setup to 1024x768 with 75Hz refresh rate.
I can setup the desktop resolution up to 1024x1200 with 60Hz refresh rate.

if I try to setup the INGAME resolution to higher then 1024x768 it quits.
only after I setup my desktop resolution to higher I am able to setup the game resolution to higher as well.

how can I setup the ingame resolution higher without effecting my desktop Ubuntu resolution ?

---

### Post by DoktorSeven on 2007-01-29
xorg.conf:

SubSection "Display"
  Depth 24 # or whatever
  Modes "1024x768" "1280x960" "1600x1200" "800x600" "640x480"
  #place desired desktop res first, the rest after.
EndSubSection

---

### Post by MaximB on 2007-01-29
what happened to the xorg.conf ???
it was there in Dapper.
I thought I've seen it in Edgy.
but now as I try to edit the file he is blank.....like a new file.
is it soppose to be like this in Edgy ?

---

### Post by leech on 2007-01-30
sudo nano /etc/X11/xorg.conf

Leech

---

### Post by podfish on 2007-01-30
This solution does not work.  It's not just NWN, it's any app that tries to switch to a higher resolution desktop than is currently the default.  The order of your modes line shouldn't have anything to do with it.

```
steve@monolith:~$ neverball
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x118
  Serial number of failed request:  125
  Current serial number in output stream:  127

```

That's the bug.  There's a problem with the xvidmode extension that is blocking this.  At first I thought there was something wrong with the sdl libs, but, since it's pervasive, and not necessarily dependent upon sdl apps to fail, I'm thinking it's an xserver bug.

On second thought, I could be wrong, doesn't neverball depend heavily on sdl to get its work done?  Anyhow, I get the same with neverball, foobillard, neverputt (basically the same game), Neverwinter Nights.  Testing other apps now.

Obvious workaround is to change your desktop resolution to something >= what you want to run.  But that sucks.

The Podfish

Edit:  Planet Penguin Racer does the same thing, switch to a higher resolution than your "default" desktop, and it crashes to desktop.  Change desktop to higher resolution, runs great.

---

### Post by MaximB on 2007-01-30
it did NOT solve the problem :(

---

### Post by podfish on 2007-02-05
bump

---

