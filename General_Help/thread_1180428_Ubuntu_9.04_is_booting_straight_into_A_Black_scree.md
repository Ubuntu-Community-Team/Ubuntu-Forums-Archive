---
title: "Ubuntu 9.04 is booting straight into A Black screen with Command prompt. GPU issues??"
date: 2009-06-06
forum: General Help
---

### Post by scrypt on 2009-06-06
Hi Guys.

I'm having a real troublesome issue with my Ubuntu 9.04 instalation on my dual boot Vista and Ubuntu 9.04.
On A Dell studio 1737. With An ATI HD 3650 GPU.

Ubuntu is instaled on it's own partition and I have Grub controling my Boot loader.

I managed to get Ubuntu running fine. But after a while, I get this error message that states that 'My screen is NOT composited' and that I should run compiz to fix this'.

I then try to run compiz to rectify this, but it does not work.

Then when i shutdown and rebooted last night, Ubuntu booted up, but did not start into the usual GDM Desktop. But to the A black screen with A command prompt. Also I caught a line that states that my screen is NOT recognized or found??

Does anybody know what I can do to to rectify this??

I am still pretty new to Ubuntu and especially tweaking it using the shell/command prompt. So I am still learning. So please bear this in mind if you take the time to reply.

I have read numerous posts on how I should be able to rectify my issue, with NO luck. and each thing I have tried has not worked.

I have ran :- 'sudo dpkg -reconfigre --xorg' But I am not sure which settings I should choose. Or even if this is the correct command I need to use to fix my problem?? I used all the default options, and they did not work either.

Can anyone help me to fix this issue.

I have a lot of files in Ubuntu that I do not want to loose!

Cheers in advance

---

### Post by mikewhatever on 2009-06-06
Did you install the proprietary ATI driver? If not, check under System->Admin->Hardware Drivers.

---

### Post by colau on 2009-06-06
System->Administration>Hardware Drivers

---

### Post by scrypt on 2009-06-06
Hi colau..

I cannot boot into my usual Desktop, So using Sysyem-Administration-hardawre drivers. Is imposible.

I can only boot stright into a black screen with a command prompt, similar to the recovery mode...

I have just been having a look in the recovery mode and I also found an error that states:-
Fatal Error
scrren is not being recognised.

But I think you are on the right lines. There seems to be an issue with my graphics...

---

### Post by scrypt on 2009-06-06
This is the error message I get on the scrolling text screen before I am presented with a black screen and command prompt, instead of my usual GUI desktop.

The Error is:-

Fatal Error

No Screen Found

????

---

### Post by colau on 2009-06-06
> **scrypt said:**
> This is the error message I get on the scrolling text screen before I am presented with a black screen and command prompt, instead of my usual GUI desktop.

The Error is:-

Fatal Error

No Screen Found

????
Try reinstalling the gnome desktop.

---

### Post by scrypt on 2009-06-06
How do I do that, do you know the command??

---

### Post by scrypt on 2009-06-06
I have tried:

sudo apt-get install ubuntu-desktop'

But it had NO effect whatsoever

---

### Post by colau on 2009-06-06
> **scrypt said:**
> I have tried:

sudo apt-get install ubuntu-desktop'

But it had NO effect whatsoever
```

sudo apt-get update
sudo apt-get install gnome
sudo apt-get install gnome-core
sudo apt-get install gnome-terminal
sudo apt-get install gdm
sudo apt-get install ubuntu-desktop
sudo gdm start

```

---

### Post by scrypt on 2009-06-06
I have just tried the commands you gave me in your last post and they unfortunately did'nt fix my problem1

I manged to read the boot screen before i am greeted with the command prompt and i read this error message:-

'Fatal error

No Screens found.

please consult x.org foundation support. check logfile @ /var/log/xorg.0.log'

but I am unsure how to do this??

CAn I just add when I finish putting in command at the command prompt, I press ctrl-alt-del to exit the screen and reboot.

Is this okay? this would not cause any issues involving the last commands i have just put into the command prompt??

Or is there a better way i should claose down and reboot??

---

### Post by cariboo on 2009-06-06
Have you tried starting in recovery mode and at the menu select drop to root prompt, then typing:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by scrypt on 2009-06-07
OKAY managed to fix this...

As I mentiones I have An ATI HD 3650 Graphics Card

When I was taken to the black screen with command prompt instead of my Ubuntu Desktop 

I tried just putting ati help into the terminal/command prompt,
and I noticed a new error output at the top of my screen that stated:

aticonfig is not installed. Run:- 

sudo apt-get install xorg-driver-fglxr

which I duely entered into the terminal.

This Downloaded and installed the missing display driver and some dependencies that where causing me the above problems..

  I then remembered a post I read earlier and made a note of, which read something about the command:-

sudo aticonfig --initial

 I then enetered Sudo aticonfig --initial into the terminal
and then ran 'startx' as I have done after trying every other command and fix 

and...

VOILA.
 Booted straight into My Ubuntu 9.04 GUI Desktop

PHEEEEWWWW..

So I will just recap the commands I used to fix my above issue.
 Here they are:-

1)      sudo apt-get install xorg-driver-fglxr

2)      sudo aticonfig --initial

3)      startx

Thsi took me back to my Ubuntu 9.04 desktop...

I then went to: system-Administration-Hardware Drivers and then re-activated my ATI/AMD Proprietary FGLXR graphics driver, and then restarted Ubuntu, and I am now back in business...

Thank's

Scrypt

---

### Post by colau on 2009-06-07
Cheers.

---

### Post by scrypt on 2009-06-07
Okay maybe I was a bit hastey in saying I have fixed this completely.

I am now still getting the original error message I got right before i got the issues with the black boot screen.

The error I am now getting when I boot into my Ubuntu desktop.
Is:-

Starting avant-window-navigator
Warning: Screen isn't composited. please run compiz (-fusion) or another compositing manger.

Also when I go to system-administration- Hardware Drivers and download and install the ati FGLRX 3D driver and restart ubuntu. the fglrx 3d driver is not instaled.

I have redownloaded and restarted ubuntu But each time it is not correctly instaled.

Can you shed any light on this??

---

### Post by scrypt on 2009-06-07
Hey again..

I manged to restore my Ubuntu desktop by running this command at the black screen with command prompt:

 sudo apt-get install xorg-driver-fglxr

  and then

 startx

I then get this error message: 

Starting AVANT-WINDOW-NAVIGATOR
 Warning: screen is not compozited please run compiz (-Fuzion or another composited manager)

Also when i go to system-Administator-Hardware Drivers,
and choose to activate and download the FGLRX ATI 3D Driver

It gives me this error message:-

FGLRX Graphics Driver A different version of this driver is in use!!
.

---

### Post by scrypt on 2009-10-12
Still having issues with this ATI 3650HD graphics card.

I ran sudo apt-get install dist-upgrade

ad upgraded from ubuntu 9.04 jaunty to ubuntu 9.10.

and now when I get to the login screen just after the splash screen my laptop display freezes and I cannot even move my mouse pad.

This has me stumped.

can anyone help me out.

none of my earlier commands work on this issue!

---

### Post by scrypt on 2009-10-12
okay this is weird.

I can start and boot into ubuntu by using startx from the recovery console.
but I cannot use my mousepad, just my usb mouse.

But Ubuntu still freezes when I try to boot into the normal way (not recovery console)

can anyone help??

---

