---
title: "Init script for uTorrent (under Wine)"
date: 2009-01-31
forum: General Help
---

### Post by Musicalmidget on 2009-01-31
Hi,

I've recently set-up a home server powered by Ubuntu using some of the many spare components I had sitting around.  I need to be able to download torrents from time to time and I've been looking into ways of doing this remotely using the server.  For the most part I run the server headless so I installed Transmission and it's web interface.  This is fine for most things, but the web interface it seems to lack the ability to download only some of the files in a torrent rather than all of them.

For this reason, I've setup uTorrent today through Wine, my intention being to use Transmission where possible, but use uTorrent instead when I need a bit more flexibility such as individual file controls.  My problem is that since the server is usually running headless, I need uTorrent to start when the machine boots like Transmission does.

Is there an easy way to do achieve this?  I have a 'transmission' user without a password that is used for starting and running Transmission.  Maybe there's a way to use the same user for starting and running uTorrent?

I found a [similar thread](http://ubuntuforums.org/showthread.php?t=769489) which linked to an init script but I couldn't seem to get it working, possibly because the script appeared to do more than just start uTorrent.

[http://ubuntuforums.org/showthread.php?t=769489](http://ubuntuforums.org/showthread.php?t=769489)

Similarly, I found a script on the third post of [this](http://forum.utorrent.com/viewtopic.php?id=35787) thread that will start and stop uTorrent when run manually, but it wouldn't seem to work automatically.

[http://forum.utorrent.com/viewtopic.php?id=35787](http://forum.utorrent.com/viewtopic.php?id=35787)

As always, any advice would be very much appreciated.

---

### Post by Musicalmidget on 2009-02-01
Ok, with a lot more playing I finally managed to get the script to work, but now I'm noticing all kinds of defunct processes.  How would I go about fixing those?

```
5630 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.55 uTorrent.exe <defunct>                                                                          
5641 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.55 uTorrent.exe <defunct>                                                                          
5655 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.57 uTorrent.exe <defunct>                                                                          
5663 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.54 uTorrent.exe <defunct>                                                                          
5698 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.56 uTorrent.exe <defunct>                                                                          
5789 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.55 uTorrent.exe <defunct>                                                                          
5796 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.57 uTorrent.exe <defunct>                                                                          
5817 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.57 uTorrent.exe <defunct>                                                                          
5845 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.57 uTorrent.exe <defunct>                                                                          
5852 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.56 uTorrent.exe <defunct>                                                                          
5901 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.58 uTorrent.exe <defunct>                                                                          
5908 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.59 uTorrent.exe <defunct>                                                                          
5915 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.58 uTorrent.exe <defunct>                                                                          
6056 utorrent  20   0     0    0    0 Z  0.3  0.0   0:00.62 uTorrent.exe <defunct>
```

---

### Post by Jackie999 on 2009-02-01
I'm sorry I can't help with your question. But have you tried ktorrent? I use utorrent on windows and ktorrent on ubuntu and have no problems at all.

---

### Post by Musicalmidget on 2009-02-01
> **Jackie999 said:**
> I'm sorry I can't help with your question. But have you tried ktorrent? I use utorrent on windows and ktorrent on ubuntu and have no problems at all.

I've tried many different clients, but Transmission and uTorrent have the web interfaces I like.  Whichever client I use though, I need to have an init script to have it start on boot without a login (the script for Transmission was available on their website).

Both Transmission and uTorrent seem to be working in this way now, I just can't seem to get rid of the uTorrent zombie processes.

---

### Post by iBurger on 2009-06-01
hey mmidget

Guess we have very similar mindset when it comes to rrr- rrr * ahem * :). Running utorrent on a ubuntu is my summer project. Just wondering if you successfully managed to do so.

burger

---

### Post by Musicalmidget on 2009-06-01
I actually never did get this working correctly, but I actually stopped trying.  I was only really looking to setup uTorrent because I felt it had a better web interface than any other application I had tried.  I later discovered however that Transmission had a command line interface, transmission-remote, which allowed me to remotely do all the things I needed to that couldn't be done through the web interface.  I've been using transmission-remote happily for months.

Sorry I don't have any uTorrent success to pass on.

---

### Post by iBurger on 2009-06-17
**System setup:**
Virtualbox VM: Debian 5.0 GNU/Linux / kernel - 2.6.26-2-686.
+ wine 1.0.1 (not compiled)
+ uTorrent 1.8.3 - settings.dat copied from host machine.

**utorrent cli + wine without X**
It works for 75%. Wine will complain about not being able draw the gui, but it does not hamper functionality much because the webui still works. You can upload torrents, manage them, and change the majority uTorrent's settings trough Firefox.

**Downside**: uTorrent has a feature to 'automatically load torrents in directory xyz'. this does not work in CLI mode, unfortunately. There's a similar [report on winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11113&iTestingId=30300")* about this issue, however its probably outdated - different situation.
Strangely, uTorrent can automatically load torrents, if I run it not headless, but with X and gnome. (or fluxbox). Have to look into this. Any tips, howto make fix this are highly appreciated. : biggrin :

* Please refer to Michael. J. Ryan's post.

**Interesting read**:
[Linux: uTorrent + WebUI witouth vncserver.]("http://filesharefreak.com/tutorials/linux-utorrent-webui-without-vncserver/") 
- Rassah, the blog author describes how he runs uTorrent as a deamon
with Debian 4.0 / wine 0.9 / uTorrent 1.7.7. (includes deamon script).

---

