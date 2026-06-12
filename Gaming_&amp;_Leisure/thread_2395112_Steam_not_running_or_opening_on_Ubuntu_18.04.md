---
title: "Steam not running or opening on Ubuntu 18.04"
date: 2018-06-26
forum: Gaming &amp; Leisure
---

### Post by seekerdev on 2018-06-26
So I went to the steam website and hit "Download", downloaded the .deb file, and used the command ```
steam
``` and what I get is
```
Repairing installation, linking /home/seeker/.steam/steam to /home/seeker/.local/share/Steam
Running Steam on ubuntu 18.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
/home/seeker/.local/share/Steam/ubuntu12_32/steam: symbol lookup error: /usr/lib/i386-linux-gnu/libxcb-dri3.so.0: undefined symbol: xcb_send_request_with_fds
/home/seeker/.local/share/Steam/steam.sh: line 444: no match: ssfn*


```

Another issue is when I click on the Steam logo on my desktop literally nothing happens. There's no popup or anything. I've browsed post after post on steam not working for people and tried all the methods that helped other people yet nothing worked for me. So I'm kinda at a loss.

---

### Post by danja95 on 2018-07-09
You are missing a dependency.
[https://packages.ubuntu.com/bionic/libxcb-dri3-0](https://packages.ubuntu.com/bionic/libxcb-dri3-0)

Try to remove your deb version and install steam from a mirror:

apt install steam

Thats how it worked for me

---

### Post by oldrocker99 on 2018-07-09
The ONLY way to install Steam is to download it from the repositories. It will automatically pull in all the dependencies, and you should be set to go. You need to put 'sudo' before the installation, thus:

```
sudo apt install steam
```

---

### Post by seanos on 2018-07-17
I *did* install from the repos (in a fresh install of 18.04) and today Steam won’t start. *libxcb-dri3-0* is present under the *~/.steam/ubuntu12_32* folder.

```
steam
Running Steam on ubuntu 18.04 64-bit
STEAM_RUNTIME is enabled automatically
Pins up-to-date!
```

```
cd ~
.steam/ubuntu12_32/steam
```
(no output)

---

### Post by oldrocker99 on 2018-07-17
Try this:
```
sudo apt purge steam && sudo apt install steam
```

It might work, of course, sometimes the magic works, and sometimes the magic doesn't work.

---

### Post by MattBro on 2018-07-24
Steam is not working for me either on ubuntu 18.04.  Launching steam from the command line reveals that it's missing the following 32 bit libraries:
STEAM_RUNTIME is enabled automatically
Pins up-to-date!
Error: You are missing the following 32-bit libraries, and Steam may not run:
libva.so.1
libva.so.1
libva-x11.so.1

It appears that 32 bit libraries for libva do not exist on ubuntu 18.   Is there any way to get these?

---

### Post by toyson on 2018-07-30
Same Steam not working on my Xubuntu 18.04, it just act like nothing is happening

---

### Post by oldrocker99 on 2018-07-31
Interesting. I have only installed from the repos, and all the dependencies were automagically installed with it. 

Those missing libraries are installed thus:
```
sudo apt install libva-drm2 libva-x11-2
```

There aren't any .so libraries in the repos. Look for the lib* files, BTW.

That should set you up. I don't know why they didn't install when Steam was installed.

---

