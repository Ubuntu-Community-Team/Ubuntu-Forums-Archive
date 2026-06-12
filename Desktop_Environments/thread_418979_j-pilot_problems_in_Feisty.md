---
title: "j-pilot problems in Feisty"
date: 2007-04-22
forum: Desktop Environments
---

### Post by trents on 2007-04-22
J-pilot synced without problems with my Palm Z22 in Dapper and Edgy but I can't get it to work in Feisty. Wonder what the difference is? Anybody else had the same problem? Kpilot won't work either, but then I never could get it to work with the earlier Ubuntu versions either.

Steve

---

### Post by ghostofcain on 2007-04-22
> **trents said:**
> J-pilot synced without problems with my Palm Z22 in Dapper and Edgy but I can't get it to work in Feisty. Wonder what the difference is? Anybody else had the same problem? Kpilot won't work either, but then I never could get it to work with the earlier Ubuntu versions either.

Steve

I did indeed have this problem, j-pilot was zero config in edgy but in fiesty, I needed to enter **usb:** in the **Serial port** box of the settings menu under preferences, hope this helps!

---

### Post by trents on 2007-04-25
ghostofcain,

Adding "USB" to the Settiings port line didn't do it for me. Here's what works for me:  If I open terminal and issue the command "sudo modprobe visor" before attempting the hotsync then J-pilot is able to locate the palm device. I then tap the hotsync button on my Palm Z22 screen and then I mouse click on J-pilot's hotsync button. Oh yes, the port settings line can be left blank or you can enter /dev/pilot. Any other entry will prevent J-pilot from finding the device. At least that's how it is on my system. Issuing the command "sudo modprobe visor" is really  the key here and keep in mind that it must be issued anew with every restart of the computer. This suggestion came from Jed Montgomery, the J-pilot project lead. I had emailed him with the issue. 

By the way, I was even able to get Kpilot to sync after issuing the "psudo modprobe visor command". I had never gotten Kpilot to work before, even under Dapper and Edgy. With Kpilot, however, you must click on the blue "Reset Device Connection" after initially attempting a hotsync.

Steve

---

### Post by fgosse on 2007-04-27
I've the same problem with kpilot.

sudo modprobe visor seeems to be a solution
but usb : don't work for me

---

### Post by gnarly_buttons on 2007-04-27
I'm running Kubuntu Feisty and use Kpilot.  I got my Z22 to work with both dapper and edgy, but with an upgrade to feisty, I can't do anything.  I am still a newbie.  Any tips?

Thanks,
Scott

---

### Post by zvandiver on 2007-04-27
Evidently the visor module is not being loaded automatically in feisty.  Type "sudo modprobe visor" and then try to sync.  It should work at that point.
You can edit the /etc/modules file and add visor to the list to load it at boot.
Zane

---

### Post by gnarly_buttons on 2007-04-28
Thanks.  That fixed my problem.

Scott

---

### Post by Dante123 on 2007-04-28
Hi all,

I am running Ubuntu Feisty and had difficulty with the sync from gnome-pilot and my Palm Zire 22 (Z22)....anyway....the command that was mentioned here  "sudo modprobe visor" did the trick and now my Palm seems to be syncing just fine.  Thanks.   My question is......what do I need to do so that I do not have to enter that command everytime I reboot.  Is there a file where this command can be put so that it runs automatically on boot up?

Thanks,

Dante123

---

### Post by gnarly_buttons on 2007-04-28
You can edit the **/etc/modules** file and add **visor** to the list to load it at boot.

---

### Post by rclark68137 on 2007-04-30
Thanks, this forum is great!!  This solved my problem with j-pilot and my Palm TX. I'm back in business!

For me,   "usb:"  didn't work, but "sudo modprobe visor" did.

---

### Post by GolfHacker on 2007-04-30
I edited /etc/modules and added "visor", as mentioned previously, but kpilot still doesn't work for me. When I run through the configuration wizard and try to auto-detect, I get the hotsync sound from my palm tungsten 2, but kpilot doesn't seem to notice. If I hardcode the parameters to my user name and /dev/pilot, the hotsync doesn't work at all.

This worked fine on Kubuntu Edgy.

Any ideas?

---

### Post by gnarly_buttons on 2007-10-28
I'm back because I now have problems syncing with Gutsy.  Has anybody else had problems?  I have tried all my old tricks, but it doesn't seem to see that I have a palm.

Scott

---

### Post by darkazurka on 2007-12-19
trents: Your 3# post helped me to sync my Palm Z22 . The lines I followed to get it to work were:
> If I open terminal and issue the command "sudo modprobe visor" before attempting the hotsync then J-pilot is able to locate the palm device. I then tap the hotsync button on my Palm Z22 screen and then I mouse click on J-pilot's hotsync button.

very helpful (!!), after I set the device in preferences to /dev/ttyUSB1

---

### Post by iamclueless on 2007-12-21
excellent this thread deserves a thank you and a bump

ive spent so long looking in the forum, finally found it. 

im sure other people need this too :)

---

### Post by iamclueless on 2007-12-21
i celebrated too early

the sync kinda works (im trying to synch a Zire 72) i think everything is synched but it fails at the back up stage then the connection stops and jpilot hangs.  i end up having to kill it in the terminal

anyone with advice?

---

### Post by darkazurka on 2007-12-30
I don't think I have a solution. The only thing that worked for me was the sudo modprobe visor thing.

Though usually I first do: (then I write the password) ```
sudo su
``` and afterwards I just type ```
modprobe visor
```

---

