---
title: "Disabled GDM - Bodged up"
date: 2009-04-16
forum: General Help
---

### Post by Magma828 on 2009-04-16
First of all, I'm relatively new to Ubuntu and I only use it for linux only tasks and running my server. I know I should be using the server edition of ubuntu to run my server but I installed home edition a while ago when I was even more inexperienced.

Anyway, I disabled GDM from the services editor box thing so the server doesn't have to load up a GUI just to run a webserver and a few server side apps and I was under the impression that I could just type "gdm" on the prompt to get back into the GUI at any time (it worked for the Ubuntu boot on my laptop).

When I try to boot the server it prints the following:
```

Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/a791c6b2-4c0e-499b-9b54-d0503bb7e3d8) = da5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/a791c6b2-4c0e-499b-9b54-d0503bb7e3d8
kinit: No resume image, doing normal boot...
_

```

I'm sure this is fine and Ubuntu normally looks for a boot image but the problem is that nothing happens. The _ blinker just keeps flashing and doesn't let me type any commands. It should let me login first (which it doesn't) and then give me a prompt but instead just seems to be loading. It may be because I set it to automatically login with a set username and password when it actually had the graphical login, but something stranger happens. If I press ctrl alt del to restart the server it starts the shutdown scripts but keeps attempting to ask me for a username - I don't have time to type anything in because the scripts keep riding over me. Also the computer is obviously shutting down so I can't stop them.

If there is any way to stop what it's trying to do without actually shutting the computer down, then i think it would help. Then I could type the GDM command to get booted back into something with a UI I'm used to.

Sorry if this is all a bit confusing I always blab on about everything and the "symptoms" are quite complicated... Just ask me if you're unsure about what I mean.

---

### Post by Windsurfer619 on 2009-04-16
Those messages are typically shown on vt8, while the x-server runs on vt7. Try pressing ctrl+alt+F7 when you get that blinking cursor to switch to vt7.

Also, the normal way to start the gdm is to type:
```
sudo /etc/init.d/gdm start
```

---

### Post by Magma828 on 2009-04-16
> **Windsurfer619 said:**
> Those messages are typically shown on vt8, while the x-server runs on vt7. Try pressing ctrl+alt+F7 when you get that blinking cursor to switch to vt7.

Also, the normal way to start the gdm is to type:
```
sudo /etc/init.d/gdm start
```

Thanks for the speedy response :D

I have no idea what vt8, vt7 or the x-server is but just to confirm, it's running home edition not server edition.

I tried holding ctrl, alt, f7 but it had absolutely no response :(

I just realised I can boot ubuntu in recovery mode, well I did and it's a small jump forward. It works fine (well almost, I have another problem but thats another thread) but how do I set that to boot normally?

I've also tried the third option - repairing the xserver (i think).

---

### Post by Windsurfer619 on 2009-04-16
Oh I'm sorry. vt7 means "virtual terminal 7". By default, ubuntu has 8 virtual terminals, I believe. You can access them by pressing ctrl+alt+F1 to F8. They are real terminals, kind of like the recovery terminal. You can mess around there...
Yeah, it sounds like something got messed up with your xserver. Doing a repair doesn't sound like a bad idea, unless you have an ATI or Nvidia card....

---

### Post by Magma828 on 2009-04-16
Ah yes CTRL+F2 opened a new terminal and asked for username/password then gave a working prompt :)

What's the actual purpose and difference of these terminals? Thanks for the help too, I'd never have got that by myself.. I can have a play with it now to try and get to the source of the problem.

---

### Post by Magma828 on 2009-04-16
Actually would it be reasonable to say that the default terminal is running lampp (or one of my other java based server side programs) so I cannot input anything into that particular terminal?

Oh wow this is amazing, my different applications are running in different terminals. vt1 appears to be the boot terminal, and all the other apps run from vt8 downwards :D

---

### Post by Windsurfer619 on 2009-04-16
Oh cool! I've never actually played with an the ubuntu server edition. That sounds awesome!

---

