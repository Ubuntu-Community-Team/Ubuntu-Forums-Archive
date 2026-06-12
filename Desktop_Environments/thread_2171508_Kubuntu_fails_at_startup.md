---
title: "Kubuntu fails at startup"
date: 2013-08-31
forum: Desktop Environments
---

### Post by bill-lancaster on 2013-08-31
I get "unable to launch /usr/bin/startkde when booting the system."

After clicking "okay" I get

"Failed to load session 'gnome'"

Have found my way to 'recovery mode' and have tried:-
1 repair broken packages
2 check all files systems
3 update grub loader

none of that helped.

Any help would be appreciated

Kubuntu 12.10

---

### Post by bill-lancaster on 2013-08-31
As an after thought, the only change to the system since the previous boot (that I know of) is the installation of skype.

Perhaps this will generate some ideas!

---

### Post by GwL3eNC on 2013-08-31
Maybe this helps you

[http://ubuntuforums.org/showthread.php?t=1750430](http://ubuntuforums.org/showthread.php?t=1750430)

---

### Post by bill-lancaster on 2013-08-31
Thanks for the link - I had read it earlier but went through it again.

sudo apt-get update, after amany lines reported it ends with "the package list or status file could not be parsed or opened"

Is this significant?

Also my HD seems to have plenty of space free.

---

### Post by GwL3eNC on 2013-08-31
Hello again,

try

sudo rm /var/lib/apt/lists/* -rf 
sudo mkdir /var/lib/apt/lists/partial  
sudo apt-get update

Plenty of free space is good or?

---

### Post by bra|10n on 2013-08-31
Have you checked the contents of ~/.xinitrc?

---

### Post by bill-lancaster on 2013-08-31
Thanks  GwL3eNC, "sudo rm /var/lib/apt/lists/* -rf" returns all files as read-only

Can I change permissions?

Yes, the HD available spacfe looks about right.

---

### Post by bill-lancaster on 2013-08-31
```
sudo edit ~/.xinitrc
``` produces a warning about mim-type the an error due to no write permissions.
The question of changing permissions arises again!

---

### Post by GwL3eNC on 2013-08-31
What? No, cant believe that becasue rm should delete this files and folders. Nothing should be returned that all files
are read only. You can also try it like that

sudo rm -r /var/lib/apt/lists 
sudo mkdir -p /var/lib/apt/lists/partial 
sudo apt-get update

It was taken from [http://wiki.ubuntuusers.de/Paketverwaltung/Problembehebung](http://wiki.ubuntuusers.de/Paketverwaltung/Problembehebung), a german side for troubleshooting with package management.

---

### Post by bill-lancaster on 2013-08-31
```
sudo rm -r /var/lib/apt/lists 
``` produces "cannot remove xxx read-only file system"

I'm using ctrl + alt + delete at boot to get into the Recovery Menu (which I now notice says "filesystem state : read-only")
Then I go to "drop to root shell prompt"

Is it significant that I haven't logged in using my password?

---

### Post by GwL3eNC on 2013-08-31
Hi,

aahh, file system ro. you should let your system load normal. If you think it's ready an hang up try

CTRL+ALT+F1

for example. If you are a lucky one you can reach the terminal where you can
login. If this is not possible you must use a live cd to boot, then mount your
file system and apply the commands.

ps. think your username is not important, because the files are system files
     not user files and possibly in recovery mode the file system is always mounted ro.

---

### Post by bill-lancaster on 2013-08-31
CTRL+ALT+F1 takes me to GNU GRUB where 'c' gives me a grub command line.

Would it be possible to login from there?

---

### Post by GwL3eNC on 2013-08-31
I realy dont understand that, becasue in your first post you tell about the graphical login where
you click the ok button. Do i understand that wrong? On this screen type the key combination.

If i realy understand you wrong i think you have only the cd option. Possibly you can enter
grub commands directly in it's command line but therefore i am the wrong person.

---

### Post by steeldriver on 2013-08-31
If you need to get into read-write mode in the recovery mode 'root shell', you can do so as follows

```
mount -o remount,rw /
```

(note: there is no space between the remount,rw options - just a comma)

However you may want to try exiting from the root shell and selecting the 'fix broken packages' recovery option first.

---

### Post by GwL3eNC on 2013-08-31
cool, learning never ends. thanks.

---

### Post by bill-lancaster on 2013-08-31
Yes, but login was giving me a blank screen.  Your sugestion of using CTRL+ALT+F2 was the answer.  It takes me from the blank screen to terminal.
The rm, mk and update commands ran perfectly.

Sorry about the confusion - my ignorance is to blame.

Having run the update command I tried a reboot but still get the same message so what should I do next?

---

### Post by GwL3eNC on 2013-08-31
blame is mine, because i dont know if i can suggest you the right commands. I believe there are some X,
gnome or kubuntu files missing, broken ir something like that. I would play around with some apt-get
commands. Possibly

sudo apt-get build-dep xorg kubuntu-desktop gnome-session

helps you out. Hopfully some other guys have a better idea.

---

### Post by bill-lancaster on 2013-09-01
Ah well!  Thanks for all the help.

Last night I saw "do-release-upgrade" being sugested in terminal and, foolishly thinking this was similar to "update" I proceeded.

The computer ran all night upgrading to 13.04 and got into some kind of loop which I had to abort.

So now I have a failed upgrade as well!

---

### Post by bill-lancaster on 2013-09-01
OK, perhaps a summary of where I am will help.

The upgrade to 13.04 seems not to have made much difference.

Startup produces:-
Unable to launch "/usr/bin/startkde" x session "/usr/bin/startkde" not found; falling back to default session" - click "okay" button.
libk
Then
Failed to load session 'gnome' - click "Log Out" button.

I then get a login screen which leads to a blank screen.

CTRL+ALT+F2 takes me to command line.

these commands:-

sudo rm /var/lib/apt/lists/* -rf
sudo mkdir /var/lib/apt/lists/partial

run OK then

sudo apt-get update
 produces a lot of output, mostly with "Something wicked happened resolving error -11" (or something like it)

followed by the sugestion to run "sudlibko dpgk --configure -a"
this results in a lot more output ending with:-
Errors were encountered while processing:-
libkcalutils4
libkpimutils4
libkalarmca12
libkmicroblog4

I'll do some more searching but that is where I am at the moment

---

### Post by bra|10n on 2013-09-01
Sorry to hear that's how it's turned out...

IMO a fresh install is probably your best option now. 

At least that's what I'd do.


As a side note I tried Kubuntu 13.04 not long ago, Kubuntu having been my distro of choice for a very long time previously. 
Now I found it rigid and awkward when it came to the pre-installed app's, and wanting to simply remove/install some app's seemingly always led to the situation where kubuntu-desktop was also going to be removed. I have been using Manjaro KDE (Arch based) ever since via a net-install and honestly I wouldn't return to Kubuntu the way it is. My point is not to down Kubuntu, but to suggest while you *are likely* to have to reinstall, perhaps a look at Manjaro or other KDE distro while you have the time and opportunity would not hurt.

best wishes

---

### Post by bill-lancaster on 2013-09-01
Yes, was preparing for just that but will look at other desktops as well - perhaps some good will come of all this!

Thanks all again

---

