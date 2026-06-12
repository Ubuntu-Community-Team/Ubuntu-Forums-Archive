---
title: "cant get ubuntu 3D games to work"
date: 2009-03-27
forum: General Help
---

### Post by sabith on 2009-03-27
i cant run ubuntu 3D games if i try it justs does nothing like i did not click on it or anything other games work just not 3D

i have a good graphix card i can run 3D games on windows
PLEASE HELP

---

### Post by kanikilu on 2009-03-27
What games are you trying to run? What video card do you have? Are there any restricted drivers available for you video card if you go to System > Administration > Hardware Drivers?

---

### Post by sabith on 2009-03-27
i have athros and no restrictions trying to run sabre a flight sim in app/games

---

### Post by sabith on 2009-03-27
altho it does say no proprietary drivers in use

---

### Post by fooman on 2009-03-27
what *video card* do you have?  ....nvidia? ...ati? ...intel?

---

### Post by sabith on 2009-03-27
it says vga compatable controler

---

### Post by Slim Odds on 2009-03-27
> **sabith said:**
> it says vga compatable controler

That doesn't mean that it's 3D capable. 

You'll do give more info

---

### Post by sabith on 2009-03-27
its not the card!!!! can play pc games fine and 3D games on my other os vista

---

### Post by decoherence on 2009-03-27
Hi Sabith,

There is a command you can run that will tell you what kind of video hardware you have. Please go to Applications > Accessories > Terminal and type

```
lshw -C video
```

Then copy/paste the output here.

While the card may be easily capable of doing 3D, if it's an ATI or nVidia card, you need to install extra drivers to enable 3D acceleration. For legal reasons, the 'good' drivers can't be shipped with the operating system. In theory, that "Hardware Drivers" thing should take care of this for you, but it seems to only see your Atheros card (probably for wireless network.)

---

### Post by sabith on 2009-03-27
PCI (sysfs)

---

### Post by decoherence on 2009-03-27
> **sabith said:**
> PCI (sysfs)

Was that the entire output? There should be much more.

If that is all it output, try prefacing the command with sudo instead

```
sudo lshw -C video
```

It will ask you for your password. Type it in and hit enter... note that no characters will be displayed as you type the password. Just type it and hit enter.

Here's the output of mine, for example

```
  *-display               
       description: VGA compatible controller
       product: Mobility Radeon HD 3450
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

```

the important parts are "product:" and "vendor:"

---

### Post by sabith on 2009-03-27
description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
tyler@tyler-laptop:~$

---

### Post by sabith on 2009-03-27
description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---

### Post by decoherence on 2009-03-27
Okay, you have Intel graphics. That means you shouldn't need any special drivers to get 3D working. What happens if you go to the Terminal again and type

glxgears

Does a window with spinning gears come up? Or does the terminal print out an error?

If it prints an error, please copy/paste that here, too.

---

### Post by sabith on 2009-03-27
tyler@tyler-laptop:~$ sudo glxgears
[sudo] password for tyler: 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
tyler@tyler-laptop:~$ tyler@tyler-laptop:~$ sudo glxgears
bash: tyler@tyler-laptop:~$: command not found
tyler@tyler-laptop:~$ [sudo] password for tyler: 
bash: [sudo]: command not found
tyler@tyler-laptop:~$ X Error of failed request:  BadRequest (invalid request code or no such operation)
bash: syntax error near unexpected token `('
tyler@tyler-laptop:~$   Major opcode of failed request:  143 (GLX)
bash: syntax error near unexpected token `('
tyler@tyler-laptop:~$   Minor opcode of failed request:  19 (X_GLXQueryServerString)
bash: syntax error near unexpected token `('
tyler@tyler-laptop:~$   Serial number of failed request:  10
bash: Serial: command not found
tyler@tyler-laptop:~$   Current serial number in output stream:  10
bash: Current: command not found
tyler@tyler-laptop:~$ tyler@tyler-laptop:~$ 
bash: tyler@tyler-laptop:~$: command not found
tyler@tyler-laptop:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
tyler@tyler-laptop:~$

---

### Post by decoherence on 2009-03-27
Here's the part that matters...

> tyler@tyler-laptop:~$ sudo glxgears
[sudo] password for tyler:
X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 10
Current serial number in output stream: 10

There is something funny with your Intel video driver or perhaps with your xorg configuration. My suggestion would be to run System > Administration > Update Manager and make sure you have all the latest updates. Reboot and try again. If it still doesn't work, reboot once more but this time watch for a prompt to enter the GRUB boot menu... it'll happen early on in the boot process, so watch  for it.

In the menu that comes up, tell it to boot in Recovery Mode (usually the second item in the list) and run "Fix X" or "X Fix" or whatever it's called.

These are fairly generic troubleshooting steps for X problems. Not sure if it'll help out 3D and unfortunately I now have a long commute ahead of me. Perhaps someone else can suggest something more specific to try?

Good luck,

---

### Post by sabith on 2009-03-27
did not work

---

### Post by Wragie on 2010-07-28
Hopefully someone will notice this ;-]

I have the same problem with the same game and the same video card/chipset thats in my tosh tecra a-8. Following this thread I did get glxgears to pop up and run. When I try to start saber I see the drive activity light grind away for as long as I leave it. I've reinstalled saber just to make sure I had all the dependents etc but that had no effect.

I've managed to get a few fps shooters running with no problems other than attracting a lot of bullets but that may be more my problem than ubuntu's ;)
I'd love to get this running at least long enough to see how close it might be to Chuck Yeagers air combat. Used to love that game.

Appreciate any help.

Dave

---

