---
title: "Change from ubuntu to Xubuntu.desktop hangs at bootup, stuck at splash screen"
date: 2014-06-21
forum: Desktop Environments
---

### Post by Camy on 2014-06-21
Hi All
I have an old computer that was running Ubuntu Lts12.04 but I could not watch youtube vids as it was jurky.
I tried installing xubuntu.desktop with '**sudo apt-get install xubuntu-desktop**' and then rebooted.
Now all I get is the xubuntu splash screen and it hangs there.
Any suggestions really appriciated.
Thanks

AMD Athlon XP 3000
2 Gig Ram
NVidia Geforce FX5200

---

### Post by Dreamer Fithp Apprentice on 2014-06-21
If it were me I'd try uninstalling that and installing either lubuntu or plain lxde. When it is hung, I'd get a tty with cntrl-alt-F1 or some F-number up to 6, inclusive. If the first one you get doesn't have a login prompt, try a different function key (1-6) until you get one that does.
It will look like a "terminal" without a window. Log in. Then:```
sudo apt-get purge [B]xubuntu-desktop
sudo apt-get install lubuntu-desktop
[/B]
```and when it's finished:```
sudo shutdown -r now
```When you login you can choose either you present bloated DE, Lubuntu, or LXDE.

---

### Post by Camy on 2014-06-21
Thanks Dreamer. When I installed it I was expecting to have a choice while booting but it doesn't get that far. All I get after turning the computer on is the splash screen, no choices :(
I tried Ctrl Alt  F1 to 6 nothing happens. The only keys that worked were Ctrl+Alt+Del

---

### Post by Camy on 2014-06-21
Ok, I managed to get into the computer by pressing Ctrl Alt F1 just before the splash screen comes up and that way I can get a login.
Then I did as you said
sudo apt-get purge [B]xubuntu-desktop
sudo apt-get install lubuntu-desktop

Purge xubuntu only said it was going to remove 44K but it installed over 200Mb

Anyway now I still get the xubuntu splash screen and it still hangs :( :(

[/B]

---

### Post by Camy on 2014-06-21
Also tried 
sudo apt-get install --reinstall ubuntu-desktop

still hangs on xubuntu screen

---

### Post by Camy on 2014-06-21
Also tried 
sudo apt-get install lubuntu-desktop lxde
sudo dpkg-reconfigure lightdm

no change :(

Was getting an error with saned and edited the file 
/etc/default/saned ..... set the no to yes

tried startx from shell prompt and get 
cannot stat /etc/X11/X     no such file or directory

---

### Post by robin7 on 2014-06-21
Something has corrupted the boot software.  **The xubuntu desktop has nothing to do with choppy video playback**, and merely using a different desktop environment is not the solution.  I use Xubuntu 12.04 on an ancient, very underpowered computer and it runs wonderfully. Better on it, in fact, than Lubuntu for some reason I can't explain. But *for videos* you need to install the **restricted-extras** packages that are appropriate to your particular "flavor" of Ubuntu.  xubuntu-restricted-extras for Xubuntu, ubuntu-restricted-extras for ubuntu, etc.

I can't tell you how to fix the boot-up issue (other than do a fresh install of Xubuntu if you want Xubuntu, Lubuntu if that's what you want, Ubu, Kubu, etc). But I *can* counter the above claim that Xfce or Xubuntu-desktop is "bloated" and that LXDE is superior for video playback. Neither is true.

---

### Post by Camy on 2014-06-21
I managed to solve the boot up hang by doing the following
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall xserver-xorg
BUT
while booting and while shuting down I'm still getting the xubuntu splash screens
Anyone know how to get rid of them?

---

### Post by deadflowr on 2014-06-21
> **Camy said:**
> 
while booting and while shuting down I'm still getting the xubuntu splash screens
Anyone know how to get rid of them?

```
sudo update-alternatives --config default.plymouth
```

---

### Post by Camy on 2014-06-21
That did it, deadflowr :) 
Thanks to everybody.

---

### Post by Dreamer Fithp Apprentice on 2014-06-23
Glad you got it working, Camy. I was afraid you might have to reinstall, but since installing xubuntu-desktop was the last thing you did before it quit booting and you were getting the splash screen which is the very last instruction grub sends the kernel, I thought it was worth a try, on the principle of always trying the easy things first. Sorry it didn't work.

@ Robin:
> **robin7 said:**
> But I can counter the above claim that Xfce or Xubuntu-desktop is "bloated" and that LXDE is superior for video playback. Neither is true.
One at a time:
> **robin7 said:**
> . . . that LXDE is superior for video playback.No such claim was made, implied, or even remotely hinted at. It should be obvious I was addressing the booting problem, which after all, had to be solved first.

> **robin7 said:**
> . . . that Xfce or Xubuntu-desktop is "bloated" . . .I did use that adjective, although a dispassionate reading will show it as a minor and somewhat jocular aside and not the point of the sentence. Certainly Xubuntu isn't bloated compared to the flagship Ubuntu main distro or something like Sabayon. Not the sort of thing I'd call bloatware outside of a humorous comparison to something still lighter. If you want to get picky, Lubuntu IS lighter. Starting from my own main system, here is how installation of each DE compares:
```
me@ubuntu:~$ sudo apt-get install lubuntu-desktop
. . .
The following extra packages will be installed:
  abiword . . .
. . . xpad
0 upgraded, 303 newly installed, 0 to remove and 0 not upgraded.
Need to get 107 MB of archives.
After this operation, 372 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
. . .
me@ubuntu:~$ sudo apt-get install xubuntu-desktop
. . .
  abiword . . .
. . . xubuntu-wallpapers
0 upgraded, 378 newly installed, 0 to remove and 0 not upgraded.
Need to get 159 MB of archives.
After this operation, 509 MB of additional disk space will be used.
Do you want to continue? [Y/n] n

```
That's starting from a system using plain Openbox as the only DE. On a VM, starting from a plain system made from the mini.iso, for Lubuntu:
```
0 upgraded, 1104 newly installed, 0 to remove and 0 not upgraded.
Need to get 348 MB of archives.
After this operation, 1,287 MB of additional disk space will be used.
```vs. for Xubuntu:```
0 upgraded, 1131 newly installed, 0 to remove and 0 not upgraded.
Need to get 419 MB of archives.
After this operation, 1,526 MB of additional disk space will be used.
```

BTW, if you need one, I have an extra sense of humor, slightly used, I can let you have cheap.

---

### Post by robin7 on 2014-06-23
> **Dreamer Fithp Apprentice said:**
> 
I did use that adjective, although a dispassionate reading will show it as a minor and somewhat jocular aside and not the point of the sentence. 

A new user wouldn't know you were joking. The difference in demand on resources between Xubu and Lubu is *minimal*. So using the word "bloated" to describe one which so closely compares with the other is more of a gross overstatement than a "jocular aside."

>  BTW, if you need one, I have an extra sense of humor, slightly used, I can let you have cheap.

If you think FUD is funny, just keep it. And stop spreading it.

---

### Post by Dreamer Fithp Apprentice on 2014-06-23
My, aren't you the cheerful fellow? I refuse to engage in a flame war. It wouldn't be fair. After all, I have a cannon.

---

### Post by Iowan on 2014-06-23
OP's problem is solved. Thread closed.

---

