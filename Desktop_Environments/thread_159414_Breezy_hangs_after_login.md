---
title: "Breezy hangs after login"
date: 2006-04-12
forum: Desktop Environments
---

### Post by adx442 on 2006-04-12
I installed Ubuntu 5.10 and there's something wrong with the video support.  When I get to the login screen, everything looks fine, but as soon as I login, I get a rectangle of junk pixels in the center of the screen and a brown background, and no key response (mouse still works). Even Ctrl-alt-del does nothing.  A hard reboot is the only way out.   I'm relatively new to Ubuntu, though I did get it installed and working on my laptop.  The problem machine has the following components:

Nvidia Geforce 7800GT
Dell 2005FPW
Pentium D 930 3Ghz
Intel 945PVS motherboard
Hauppage PVR150 tuner card
2xSATA drives (no RAID)

Can someone help me out with this particular issue?

---

### Post by johnc4510 on 2006-04-12
did you install the glx drivers for the nvidia card?

---

### Post by adx442 on 2006-04-12
[QUOTE=johnc4510]did you install the glx drivers for the nvidia card?[/QUOTE]

I just went through the installer.  I have no idea if it installed those or not ... how can I check or re-install from CD to ensure that they are installed?

---

### Post by rfruth on 2006-04-12
A cold boot (power cycle) is the only way, no more keyboard LEDs, no VT (Ctrl-Alt-F1)

---

### Post by johnc4510 on 2006-04-12
In synaptic it's listed under nvidia-glx
If it's not installed do this,
1.close synaptic
2.open your terminal:Applications>Accessories>Terminal
3.Type the following:
sudo apt-get install nvidia-glx
type in your password
sudo nvidia-glx-config enable
then type exit in termiinal and reboot computer

---

### Post by Ramses de Norre on 2006-04-12
No rebooting in linux, ctrl+alt+backspace should do the trick.

---

### Post by johnc4510 on 2006-04-12
Correct!!!!

---

### Post by adx442 on 2006-04-12
[QUOTE=johnc4510]In synaptic it's listed under nvidia-glx
If it's not installed do this,
1.close synaptic
2.open your terminal:Applications>Accessories>Terminal
3.Type the following:
sudo apt-get install nvidia-glx
type in your password
sudo nvidia-glx-config enable
then type exit in termiinal and reboot computer[/QUOTE]

Thanks for the responses, but I can't get to Synaptic or anything else.  Once logged in, the machine is unusable. Nothing works, I just get the pixelated rectangle and a brown background.  I've even tried the "Fail-proof Terminal" and Fail-Proof Gnome, and get the same thing.  

Thanks for the tip about rebooting (I'll remember it for the future), but that doesn't work either in Ubuntu's current state.

---

### Post by Ramses de Norre on 2006-04-12
When you're at the login screen, press alt+ctrl+F1 to get into text only mode and execute the command (sudo apt-get install nvidia-glx && sudo nvidia-glx-config enable).
When finnished do sudo /etc/init.d/gdm restart
Enter your user password (which you logged in with) when ask for a password.

---

### Post by adx442 on 2006-04-12
[QUOTE=Ramses de Norre]When you're at the login screen, press alt+ctrl+F1 to get into text only mode and execute the command (sudo apt-get install nvidia-glx && sudo nvidia-glx-config enable).
When finnished do sudo /etc/init.d/gdm restart
Enter your user password (which you logged in with) when ask for a password.[/QUOTE]

Thank you!  That's just what I needed ... posting from Ubuntu right now!  

Many thanks for all the help ...

---

