---
title: "I can't get any further then the log in screen"
date: 2004-12-13
forum: Desktop Environments
---

### Post by Teddy! on 2004-12-13
Hi all, first of all I wan't to tell you that I'm new to this forum so don't get to much upset if I posted this thread in the wrong forum-topic. And second of all I am completly new to pretty much everything that has to do with Linux but I think it's time for me to learn.

I choosed the Ubuntu dist becuase it seemed to be easy to install and then learn from there, but I got a problem pretty fast ;)

I have installed Ubuntu on my slave-hdd and I think the installation process went just fine and now when I start up the computer I can choose if I want to start Ubuntu or WinXP and so on, so far everything is just fine.

But then when I choose Ubuntu and it starts (some stuff fails to load (I can write them down if I need to) but not many and I don't think there was any fatal error stuff), then I get welcomed by the log in screen. Here I can choose alot of stuff that I don't really know the difference of (standard-something, gnome (which is the graphic-interface right?) and terminal-mode and so on (this was under the session-tab). But anyway now I'm just babbeling.

The problem comes when I try to log in with my username and password. Everything that happens is just that some strange bongo-trum music starts and the screen blanked to the Ubuntu background color, then if I wait just a little longer the Ubuntu-logo shows but then nothing more happens. The music sounds like it's stuck.

I have tried to log in with all the other options and nothing helps. The terminal-mode works, but I don't have a clue of how to use it...

Well I don't think anyone can help me with just this, but tell me how to get more error-reports and so on to you so you can help me :)

---

### Post by oscarh on 2004-12-13
[QUOTE=Teddy!]Hi all, first of all I wan't to tell you that I'm new to this forum so don't get to much upset if I posted this thread in the wrong forum-topic. And second of all I am completly new to pretty much everything that has to do with Linux but I think it's time for me to learn.

I choosed the Ubuntu dist becuase it seemed to be easy to install and then learn from there, but I got a problem pretty fast ;)

I have installed Ubuntu on my slave-hdd and I think the installation process went just fine and now when I start up the computer I can choose if I want to start Ubuntu or WinXP and so on, so far everything is just fine.

But then when I choose Ubuntu and it starts (some stuff fails to load (I can write them down if I need to) but not many and I don't think there was any fatal error stuff), then I get welcomed by the log in screen. Here I can choose alot of stuff that I don't really know the difference of (standard-something, gnome (which is the graphic-interface right?) and terminal-mode and so on (this was under the session-tab). But anyway now I'm just babbeling.

The problem comes when I try to log in with my username and password. Everything that happens is just that some strange bongo-trum music starts and the screen blanked to the Ubuntu background color, then if I wait just a little longer the Ubuntu-logo shows but then nothing more happens. The music sounds like it's stuck.

I have tried to log in with all the other options and nothing helps. The terminal-mode works, but I don't have a clue of how to use it...

Well I don't think anyone can help me with just this, but tell me how to get more error-reports and so on to you so you can help me :)[/QUOTE]
 does the whole computer hang or is it just gdm/gnome that does?

have you tried suda apt-get dist-upgrade in the termial?

---

### Post by Teddy! on 2004-12-13
> **oscarh]does the whole computer hang or is it just gdm/gnome that does?[/QUOTE]
I don't really know... I think it's only Gnome (I dont know if ctrl+alt+del works in linux so  said:**
> have you tried suda apt-get dist-upgrade in the termial?
I haven't tried anything cause I don't know anything about how to use the terminal ;)
And btw, I have a 56k modem so I can't connect to the internet with Ubunta (yet).
Like when it asked me if I wanted to download more packages and stuff from the internet I couldn't becuase I don't have broadband (adsl, and so on).

---

### Post by jdodson on 2004-12-13
[QUOTE=Teddy!]I don't really know... I think it's only Gnome (I dont know if ctrl+alt+del works in linux so ;)), but when I use the power button on the front of my comp then ubuntu logs of and goes out to the "dos-like env" and then turns of a lot of stuff and thens turns of the computer so...


I haven't tried anything cause I don't know anything about how to use the terminal ;)
And btw, I have a 56k modem so I can't connect to the internet with Ubunta (yet).
Like when it asked me if I wanted to download more packages and stuff from the internet I couldn't becuase I don't have broadband (adsl, and so on).[/QUOTE]

try running the following command from your home directory:

sudo chmod 777 .ICEauthority

---

### Post by Teddy! on 2004-12-13
[QUOTE=jdodson]try running the following command from your home directory:

sudo chmod 777 .ICEauthority[/QUOTE]
Sure thing, I'll be back when I have tried that.

I found out one of the problems that shows when booting the system too.

This is what it says while loading alot of other stuff to:

```
* Starting hotplug subsystem...
modprobe: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitted.
```

And by the way, my "home directory" where is that..? Is that the default place I'll get to when I login into the terminal? Well I'll try it out anyways ;)

---

### Post by Teddy! on 2004-12-13
Well I tried the tip that jdodson gave me and I don't know if it made any different. I logged in to with my default user "teddy" and wrote "sudo chmod 777 .ICEauthority" and then it asked me for a password and I wrote my own password and then it just returned to normal in terminal no message what so ever, so I don't know what happened...

---

### Post by adbak on 2004-12-13
[QUOTE=Teddy!]

```
* Starting hotplug subsystem...
modprobe: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitted.
```

And by the way, my "home directory" where is that..? Is that the default place I'll get to when I login into the terminal? Well I'll try it out anyways ;)[/QUOTE]
First off, your home directory is simply "/home/<username>", username being whatever name you gave it during install.  And yes, it is the default place for the terminal.

As far as shpchp and pciehp, I don't think they're anything to worry about.  However, if the FATAL ERROR message scares (like it does me) and you want to shave a few seconds off of your boot-up, then simply add "shpchp" and "pciehp" to your /etc/hotplug/blacklist.  At least I think that's where you add it, lemme check....  Yes, I was right.  The directions to do so are listed below:

Open up a terminal (Applications -> System Tools -> Terminal).
At the terminal, type, without the quotes, "sudo gedit /etc/hotplug/blacklist" or simply copy and paste.  At the prompt, enter the password.
Scroll to the bottom of the document and add the following (it's best to just copy and paste):
```

#added
shpchp
pciehp
```
Save the file and exit.

On your next boot-up, these errors should disappear.

---

### Post by Teddy! on 2004-12-13
Well thanks for the answers so far, I'll add the shpchp and pciehp to the blacklist as adbak told me to but if I get this right, this won't help me be able to login... so I still need help. Hasn't this happent to anyone else?

By the way adbak, I can't use the menu-way to open the terminal (Applications -> System Tools -> Terminal), cause as I told you guys I can only login with the terminal no GUI, hehe :)

---

### Post by Teddy! on 2004-12-14
Something funny happent when I added shpchp and pciehp to my blacklist. When I wrote "sudo gedit /etc/hotplug/blacklist" in the terminal a text editor opened up where I could edit the file and so on. I could also open other files and so on so I guess "some" of the Gnome works. But still, when I try to login to gnome itself it "crashes" after the login screen. The background is blank and the logo shows but nothing more and the music is stuck for sure.

---

### Post by ulrich on 2004-12-15
when in gdm, click 'session' and choose 'Gnome (failsafe)' or similar 

does this work?

---

### Post by wallijonn on 2005-01-11
[QUOTE=Teddy!]The background is blank and the logo shows but nothing more and the music is stuck for sure.[/QUOTE]

This may be an idication that "sound" should be included in /etc/hotplug/blacklist.d. You'll need to see if there is a file entitled "alsa-base" in that folder and if your device is listed in that alsa-base file.

---

### Post by renier on 2005-01-14
[QUOTE=adbak]First off, your home directory is simply "/home/<username>", username being whatever name you gave it during install.  And yes, it is the default place for the terminal.

As far as shpchp and pciehp, I don't think they're anything to worry about.  However, if the FATAL ERROR message scares (like it does me) and you want to shave a few seconds off of your boot-up, then simply add "shpchp" and "pciehp" to your /etc/hotplug/blacklist.  At least I think that's where you add it, lemme check....  Yes, I was right.  The directions to do so are listed below:

Open up a terminal (Applications -> System Tools -> Terminal).
At the terminal, type, without the quotes, "sudo gedit /etc/hotplug/blacklist" or simply copy and paste.  At the prompt, enter the password.
Scroll to the bottom of the document and add the following (it's best to just copy and paste):
```

#added
shpchp
pciehp
```
Save the file and exit.

On your next boot-up, these errors should disappear.[/QUOTE]
 Thanks this helped me a lot with my problem on my Compaq Armada 7800 machine.

---

