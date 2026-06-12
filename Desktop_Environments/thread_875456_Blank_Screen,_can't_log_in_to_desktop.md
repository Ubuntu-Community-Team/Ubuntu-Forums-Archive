---
title: "Blank Screen, can't log in to desktop"
date: 2008-07-30
forum: Desktop Environments
---

### Post by Bodhidharmazen on 2008-07-30
Hi all, first post here.

For the last month I have been playing/using Ubuntu in my laptop, it ran terribly slow on vista so I decided to take action. Anyway, everything worked well (except for problems with the wireless manager which sometimes forget the login and password for my home network, so I have to manually input them again, which is a pain, because my wife uses the computer too).

Anyway, as I said, everything worked ok until yesterday, when I was trying to change the appearance of the icons and their colors (btw I use the Compiz 3D desktop with the rotating cube). Suddenly the computer ceased to respond and my natural reaction was to shut it off to restart.

Thats it, I have not reached the desktop again, the computer starts, I put my login and password and then a blank screen remains, with a small white box in the upper left (approx 1/6 size of the screen). 

I can reach the prompt with ctrl+alt+f1 and have tried to restart with the "restore" options. Nothing happens.

More data:

Ubuntu 8.04
Nvidia 6100
Screensaver still works

I couldn't find an option to reinstall without formatting the HD again, can a reinstall (if it is possible with Ubuntu) solve the problem by reinstalling the original desktop without the 3D stuff?


Please HEEEELP!!!!!!!!!!!!!!!

BTW, one month ago I knew NOTHING about linux in general... so yes, Im a newbie (but learn fast)

---

### Post by overdrank on 2008-07-31
> **Bodhidharmazen said:**
> Hi all, first post here.

For the last month I have been playing/using Ubuntu in my laptop, it ran terribly slow on vista so I decided to take action. Anyway, everything worked well (except for problems with the wireless manager which sometimes forget the login and password for my home network, so I have to manually input them again, which is a pain, because my wife uses the computer too).

Anyway, as I said, everything worked ok until yesterday, when I was trying to change the appearance of the icons and their colors (btw I use the Compiz 3D desktop with the rotating cube). Suddenly the computer ceased to respond and my natural reaction was to shut it off to restart.

Thats it, I have not reached the desktop again, the computer starts, I put my login and password and then a blank screen remains, with a small white box in the upper left (approx 1/6 size of the screen). 

I can reach the prompt with ctrl+alt+f1 and have tried to restart with the "restore" options. Nothing happens.

More data:

Ubuntu 8.04
Nvidia 6100
Screensaver still works

I couldn't find an option to reinstall without formatting the HD again, can a reinstall (if it is possible with Ubuntu) solve the problem by reinstalling the original desktop without the 3D stuff?


Please HEEEELP!!!!!!!!!!!!!!!

BTW, one month ago I knew NOTHING about linux in general... so yes, Im a newbie (but learn fast)

Hi and welcome, have you tried booting into recovery mode and use the xfix option? If you can reach the command prompt with ctrl,alt,F1 have you tried to reconfigure you xorg? ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by tuxxy on 2008-07-31
Also try starting GNOME from command line,

```
startx
```

---

### Post by Bodhidharmazen on 2008-07-31
> **overdrank said:**
> Hi and welcome, have you tried booting into recovery mode and use the xfix option? If you can reach the command prompt with ctrl,alt,F1 have you tried to reconfigure you xorg? ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Yes, tried the xfix, no results. Yes I can reach the command prompt and I just wrote this code. First it says that it is unable to resolve the name of the host (my router), then it asks me for the password, then it says that it is overwriting a file and that it is making a backup.

I then tried two things, 1) rebooting but all I got was the same blank screen with the upper left white box

Then I entered the code again and wrote the "startx" code that tuxxy suggested and I got this:

unknown host
bad display name in list command
fatal server error, server is already active for display 0, it asks me to remove a file (and I dont know how to do that, tried the rm command and it says that "operation not permitted"), the last response is:

xauth: (argv):1: bad display name"HAL:0" in "remove" command

HAL, btw, is the name of my router, I dont know why is trying to access it.

EDIT:

remember Im a linux newbie, still I thought that maybe entering "sudo" before the rm would do the trick (have read somewhere that sudo is the equivalent for root and I believe it is a privileged access to the core of the OS). So yes, I could erase the file and with the startx command (for which I also used the "sudo" prefix) I could reach the desktop!

Of course, it is the original Ubuntu desktop, without my files, wallpaper or fancy looking gadgets but at least I regained access to the graphical interface using this method... **_BUT, the problem is not gone_**. I rebooted the computer and... guess what my old friend the blank screen :(

---

### Post by Bodhidharmazen on 2008-07-31
Tried again, if I do what you two suggested I can reach the desktop, but only the original Ubuntu one and only in "root" mode (it says root right on top). But when I restart the computer it gives me the blank screen again. 

How can I recover my desktop or create a new one for my "normal" user instead of the "root"?

---

### Post by Bodhidharmazen on 2008-07-31
I couldn't think in a better forum, but please, as I note this one is slow, can you point me to where can I find a solution for my problem?

Thanks!

---

### Post by Bodhidharmazen on 2008-07-31
Please excuse me for bumping my thread up, but I have a business travel on monday, and I need my computer to work! I'm leaving windows and trusting Ubuntu and its community... 

Please! Help!

---

### Post by nbayiha on 2008-07-31
Maybe you should try to reinstall you card driver.
I mean you use nvidia or ATI  ?

---

### Post by Bodhidharmazen on 2008-07-31
> **nbayiha said:**
> Maybe you should try to reinstall you card driver.
I mean you use nvidia or ATI  ?

:) thx. Nvidia 6100. How can I do that?

---

### Post by nbayiha on 2008-07-31
first if you have them installed from synaptic try first to uninstall them and reinstall them again. Reboot your computer and report here if the problem is still present.
I will show you another way.
Don't worry i will be here waiting .

Edit: If you are having any kind of problem just report it , even the most silly one :D , this forum and his member are here to help You.

---

### Post by Bodhidharmazen on 2008-07-31
:) Ok, I dont know what is synaptic, I installed from the CD and then on the top right it told me something about the nvidia drivers, I installed them from there. Then I was working with the 3D desktop until it failed.

I can only reach the graphical environment as "root" but lost access to the internet (it won't show my wireless router but every other in the surroundings).

---

### Post by nbayiha on 2008-07-31
LOL i wasn't looking the second page , it's why i took so much time to see that you replied sorry . Anyway , synaptic is in
System->Administration->synaptic Package Manager 

there you should search nvidia uninstall and reinstall .

Edit : So actually you are working without internet connection in the Ubuntu pc?

Edit2 : I am about to go and sleep , anyway if the first option didn't work , i mean uninstall and reinstall . Follow those step i gave in this thread and you should definitely have you graphic card install. 
[http://ubuntuforums.org/showthread.php?t=871529&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=871529&highlight=nvidia)

And if after all that you are still having the same problem..... Then tomorrow morning more people will be sitting here to help you . :D

Good night and Good Luck

---

### Post by Bodhidharmazen on 2008-07-31
the only way I can enter the graphical environment is described in my previous posts, I have only the "root" access and when I enter the synaptic package manager everything related to Nvidia is already disabled.

---

### Post by Bodhidharmazen on 2008-07-31
update, for the few answering this thread.

Without knowing what I was doing it occured to me that maybe I could create another user to try to boot with the graphical environment. Well, it works! now I can access the computer again, including the Internet... BUT.... this new user do not have any of the documents nor my session in Firefox.. how can I put all my files in the new user and delete the old one?

Thanks.

---

### Post by Burro Adelante on 2008-10-24
Hi,
I'm having the same problem now. How did you create a new user? I feel this is the only option!
Thanks

---

