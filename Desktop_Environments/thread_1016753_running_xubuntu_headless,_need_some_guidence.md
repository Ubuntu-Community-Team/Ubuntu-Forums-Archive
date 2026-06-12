---
title: "running xubuntu headless, need some guidence"
date: 2008-12-20
forum: Desktop Environments
---

### Post by prupert on 2008-12-20
Hi there

I am still learning linux and I need some help sorting something out.

I am wanting to run a box with Xubunut headless, but I do need access to a GUI as I am still learning Linux and am using conky to give me a quick overview of system status via VNC (as I get more confident, I will switch over to phpsysinfo and CLI only).

Anyway, I can't get the Xubuntu box to run without a monitor attached. The boot process always halts because the system detects there is no monitor attached - I guess this is Xorg halting the boot.

I understand that to get round this, I need to add additional details to my xorg.conf file, but I am not sure where to find these details and what exactly I need to add to ensure the box starts up without a monitor, but without screwing up my settings so that I can connect my monitor to the box if I need to (say if networking fails for whatever reason) and it will still work. 

I tried reading through my xorg logs, but it was full of so much info, I got a bit scared about what to do.

Searching on the forums hasn't helped much, since the answers given seem a little incomplete and it looks like the posters just gave up, most of the posts are fairly old too.

So, could anyone tell me, or point where to look, to edit my settings so Xubuntu loads without a monitor, but will still allow me to log in via VNC? I have VNC set-up all ok, that isn't an issue, it's just getting the box started without a monitor is the problem (I am presuming that if I just disabled xorg at start-up, it would mean that VNC also wont work).

If it helps, I am using the default xfce display manager on Xubuntu.

Looking forward to some advice.

---

### Post by albinootje on 2008-12-20
> **prupert said:**
> The boot process always halts because the system detects there is no monitor attached - I guess this is Xorg halting the boot.

How do you know that the system halts ?
Did you install the openssh-server ? And can you log in successfully ?
For vnc you need to start the vnc-server on that machine, did you do that ?
> 
(I am presuming that if I just disabled xorg at start-up, it would mean that VNC also wont work).

If it helps, I am using the default xfce display manager on Xubuntu.

For running X on a headless manage you don't need a display manager.
You can safely remove it, or disable it (For example with rcconf or sysvconfig).

In general for a headless server with X you would need the X libraries,some X fonts, a window-manager, and some small tools like xauth, as a minimum.

---

### Post by prupert on 2008-12-20
Sorry, I had meant to add the details of the system halt. Here you go:

During boot without a screen, the system gets so far then halts - if you try and log in via VNC or SSH you get a connection refused message. If you then attach a display to the box, you a Window that says:

Ubuntu is running in low-graphics mode.
The Following error was encountered. You may need to update your configuration to solve this.

(EE) intel(0):No valid modes.
(EE) Screens(s)found, but none have a usable configuration.

Then, if you click ok, you get.

What would you like to do?
Run Ubuntu in low-graphics mode for just this session
Reconfigure Graphics
Troubleshoot error


Interestingly, Troubleshoot error givesyou the option to view various logs, but then you can't view them, and choosing Run ubuntu in low graphics just then switches to a blank screen and you have to reboot.

So, this is the error, and it is stopping my other services like VNC and SSH from loading. If I boot with a screen attached it all works fine and I can log in with SSH and VNC remotely.

And yup, open SSH installed and running fine if I boot it with display attached, and VNC server set to auto-start and also running fine if I boot it with display attached.

---

### Post by albinootje on 2008-12-20
> **prupert said:**
> 
(EE) intel(0):No valid modes.
(EE) Screens(s)found, but none have a usable configuration.

> 
So, this is the error, and it is stopping my other services like VNC and SSH from loading. If I boot with a screen attached it all works fine and I can log in with SSH and VNC remotely.

Okay, good.
Disable the display manager (I think it's gdm in Xubuntu), and try again.

Are you using Network-manager?
For a headless server it's recommended to use only /etc/network/interfaces and disable Network-manager.

---

### Post by prupert on 2008-12-20
Ahh, sorry, this is where my noobiness comes in. How would I go about:

- disabling the display manager - yup, I think it is gdm
- checking that I am using Network-manager
- disabling Network-manager so I only use /etc/network/interfaces
- re-enabling these if I mess up? (I guess via SSH)

Aha, I can just untick Network-manager, done that one

---

### Post by albinootje on 2008-12-20
> **prupert said:**
> Ahh, sorry, this is where my noobiness comes in. How would I go about:

- disabling the display manager - yup, I think it is gdm
- checking that I am using Network-manager
- disabling Network-manager so I only use /etc/network/interfaces
- re-enabling these if I mess up? (I guess via SSH)

To disable gdm, use rcconf or sysvconfig, or update-rc.d 
(see : man update-rc.d)

To check for Network-manager : dpkg -l|grep -i network
See whether you can disable it with rcconf or the like.

To edit /etc/network/interfaces :

Here's an example :
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.3.90
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255

Is your vnc-server physically within reach or far away ?

---

### Post by prupert on 2008-12-20
****, what I feared might happen has happened. I used the systems services GUI to untick GDM, and the display went away. Now, even when I reboot the box with a display attached, I get nothing. No display after the BIOS Post and after Grub loads, and I can't SSH in or VNC in :(


Do you know what file I need to edit to re-enable GDM? I can boot into a LiveCD and change it I guess - but at the moment, my system is borked :( :(

I guess maybe I needed to do it one at a time, before disabling network manager, rookie mistake....

The VNC server is right next to me.

I am gonna have to go for a bit and tend to the wife, any suggestions for fixing my balls up whilst I am away are much appreciated. Will look back into this in 4 or 5 hours. Thanks for all your help so far ;)

---

### Post by albinootje on 2008-12-20
> **prupert said:**
> ****, what I feared might happen has happened. I used the systems services GUI to untick GDM, and the display went away. Now, even when I reboot the box with a display attached, I get nothing. No display after the BIOS Post and after Grub loads, and I can't SSH in or VNC in :(

Okay, no worries, please start up in "recovery mode".
And then (after a while) choose the "drop to root shell" option.

Type in : ```
 dhclient 
```
And see whether you get an ip-address.
If so, continue to work on having /etc/network/interfaces working.
I gave a link and an example already for that, but you can also read :
```
man interfaces
```
for more info.

---

### Post by prupert on 2008-12-20
ok, cool, I didn't know about recovery mode. I'll try as you suggested and report back.

Thxs.

---

### Post by prupert on 2008-12-20
Right, I managed to sort out the intefaces file, not sure if eth0 is working or wlan0 is working, but I can worry about that later.

I can now SSH into the box, I am playing around with starting xorg and gdm from SSH to get back to a screen, no luck as yet.

VNC doesn't work at the moment for some reason - maybe I had it set to only load AFTER GDM started, if I have disabled that, tehn I guess no VNC. Thing is, I really want GDM to still load, i just want the box to boot and not complain that there is no monitor attached. My Ubuntu box does it fine.

---

### Post by prupert on 2008-12-20
Right, I managed to sort out the interfaces file, not sure if its eth0 that is working or wlan0, but I can worry about that later.

I can now SSH into the box, I am playing around with starting xorg and gdm from SSH to get back to a screen, no luck as yet.

VNC doesn't work at the moment for some reason - maybe I had it set to only load AFTER GDM started, if I have disabled that, tehn I guess no VNC. Thing is, I really want GDM to still load, i just want the box to boot and not complain that there is no monitor attached. My Ubuntu box does it fine.


Hmm, things are very wrong now. Originally I set Xubuntu to log in automatically. When I reload GDM via SSH, on the screen it loads the login window, but I get an Authentication Error message constantly, no matter how many times I click on OK.

If I then reboot (which is all I can do) via SSH and try to load Xorg using a new config, I just get a crazy screen with loads of wavy lines - which is the same screen I get when I tried to first install Ubuntu on my first install. Maybe the graphics driver is corrupt....

---

### Post by prupert on 2008-12-20
Hmm, I think there is something wrong with Ubuntu/Xubuntu and the specific config I have. I have installed Ubuntu 8.04 on a Siemens/Fujitsu using exactly the same config and it boots headless no problem. But on this box, a Dell Optiplex SX260 I get a constant error on boot with no screen - this low-graphics mode window. If you then select what screen and driver to use, I just then get a blank screen. CTRL ALT Backpace simply loads the login again (I can hear the login sound, but still a blackscreen). Obviously my xserver is freaking out with the onboard graphics intel 845G - I have read about there being problems with Linux and this graphics chip, so I guess I will just have to lump it....

I note that there have been a few posts about this, and a bug on launchpad with a similiar error, but looks like it hasn't been fixed. What can I do to submit info to help progress it???

---

