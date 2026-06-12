---
title: "OK, so it totally doesn't work"
date: 2009-05-30
forum: General Help
---

### Post by ozone_00 on 2009-05-30
I've tried intalling both 32 and 64 bit versions of Ubuntu Studio 9.04 with pretty much the same results.  Windows load and close slowly from top to bottom; scrolling is jerky; system froze when I tried to surf the net, restart, and listen to mp3s or view photos on Windows partition; system monitor shows one two cores always at 100%.  I was able to make a simple beat in Hydrogen and a test recording in Audacity, but curser movement was jerky.  I'm running on AMD QL-62 CPU (64 bit, dual core, 2GHz), 2GB RAM.  I'm using abot 10GB for root partition, 4GB swap and 50GB for home.  GPU is Nvidia GeForce 8200M G.

---

### Post by benoy4007 on 2009-05-30
Give sys configuration,
And error output.

---

### Post by Wiebelhaus on 2009-05-30
> **benoy4007 said:**
> Give sys configuration,
And error output.

Yea , we really need system specifications to even begin a diagnostic process.

---

### Post by ozone_00 on 2009-05-30
I'm running on AMD QL-62 CPU (64 bit, dual core, 2GHz), 2GB RAM. I'm using abot 10GB for root partition, 4GB swap and 50GB for home. GPU is Nvidia GeForce 8200M G.

---

### Post by steeleyuk on 2009-05-30
It sounds like you need to install the nvidia driver to me.

Go to System > Administration > Hardware Drivers and see if there is anything listed.

---

### Post by ozone_00 on 2009-05-30
> **steeleyuk said:**
> It sounds like you need to install the nvidia driver to me.

Go to System > Administration > Hardware Drivers and see if there is anything listed.
Haven't tried this but I did try downloading the driver from nvidia and when I tried to install it said there was a problem with character encoding.
edit: nope the only thing it shows is the wifi card driver.

---

### Post by ozone_00 on 2009-05-30
> **ozone_00 said:**
> Haven't tried this but I did try downloading the driver from nvidia and when I tried to install it said there was a problem with character encoding.
edit: nope the only thing it shows is the wifi card driver.
I did find something in package installer called something like Nvidia x driver.org, is this what I need?

---

### Post by ozone_00 on 2009-05-30
> **benoy4007 said:**
> Give sys configuration,
And error output.

What do you mean by error output.

---

### Post by snowpine on 2009-05-30
Have you tried using the regular kernel instead of the real time kernel?

---

### Post by themusicalduck on 2009-05-30
There's a particular method to installing the Nvidia drivers downloaded from the site that you need to follow.

Save the nvidia driver file to your home folder firstly and then name it something easy to remember. Then save anything you're in the middle of and press ctrl+alt+f1.

You'll be dropped down to a command prompt. Log in and then enter

```
sudo killall gdm
```

When that completes type this command

```
sudo sh nameofdriverfile
```

Then follow the onscreen instructions. Don't worry if it tries to download a module and can't, it'll compile one for you automatically.

When the installer is finished type

```
sudo /etc/init.d/gdm restart
```

and you'll be dropped back into the login screen with the drivers activated.

---

### Post by ozone_00 on 2009-05-30
> **snowpine said:**
> Have you tried using the regular kernel instead of the real time kernel?

NO, not yet.  Can Studio Jaunty be installed without the realtime kernel or do I have to install a different version?

---

### Post by ozone_00 on 2009-05-31
> **snowpine said:**
> Have you tried using the regular kernel instead of the real time kernel?

That might be it, I just installed regular Jaunty and it seems to work fine.

---

