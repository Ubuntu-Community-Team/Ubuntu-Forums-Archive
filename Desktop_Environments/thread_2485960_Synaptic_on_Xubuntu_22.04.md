---
title: "Synaptic on Xubuntu 22.04"
date: 2023-04-15
forum: Desktop Environments
---

### Post by Colin@oxford on 2023-04-15
I have installed the basic version of Xubuntu 22.04 and want to use synaptic to download the packages I use.

I installed it with:

sudo apt-get install synaptic

If I start it as:

sudo synaptic

I get a message about incompatibility with Wayland.

If I start it from the main menu, it asks for authentication but then nothing appears on the screen.

What am I doing wrong?

---

### Post by him610 on 2023-04-15
> ...incompatibility with Wayland. 
Unless you are deadset on using Wayland, you should consider using X11 instead. From other entries within these forums, it appears the Wayland is not quite ready for prime time.

---

### Post by Colin@oxford on 2023-04-15
I know nothing about Wayland.  How do I turn it off?

---

### Post by Holger_Gehrke on 2023-04-15
If you're using XUbuntu, how did you manage to get it running with a Wayland session ? AFAIK XFCE - the desktop environment in XUbuntu - is not yet capable of running on Wayland. Wayland is a set of protocols for the interaction between applications and the basic graphical system. By completely reimplementing the basic graphical system and leaving out old capabilities that aren't used by current applications, Wayland promises to be faster and lighter than the old X11 system. At least that's been the goal for the last 10 years (+/- 3) and it still is not even close to finished or stable. Since a lot of things that used to be done by the basic system are now the job of the compositor - a component that a DE has to supply itself and that isn't trivial to develop - a lot of smaller projects - especially simple window managers - are probably not going to ever be ported to Wayland.

You should have an option in the login screen for the type of session you want to run. In the top panel of the login screen should be an icon that becomes clickable after selecting a user name (on my system it take the mouse-head shape of the XFCE mascot and offers session for XUbuntu and XFCE without the XUbuntu specific setup).

Holger

---

### Post by Colin@oxford on 2023-04-16
> **Holger_Gehrke said:**
> If you're using XUbuntu, how did you manage to get it running with a Wayland session?



I have absolutely no idea.  I simply installed the minimal system and that is what I got.

If I start synaptic without using sudo, then it shows fine - just that I can't use it to install anything directly! That implies that sudo is using Wayland while my user is not ??

---

### Post by tea for one on 2023-04-16
> **Colin@oxford said:**
>  I simply installed the minimal system and that is what I got.
Which ISO did you use to install?

---

### Post by ajgreeny on 2023-04-16
If you installed synaptic in the normal manner with ***sudo apt install synaptic*** it will appear in your menu system and when clicked it should then ask for your admin password, ie, your user password you set at installation of Xubuntu.

Normally synaptic is installed by default in Xubuntu so I wonder why you had to install it manually, but see below.

You talk of a minimal installation but I also don't know what you mean by that. Did you use the mini.iso or the full desktop iso?
If the latter there is a choice at installation of the normal install or a cropped/ reduced install with only a browser and essential GUI apps included which probably means without synaptic  but I've never looked into that option so I'm not sure.

Use your menu and you may find everything works as I describe above without the need for a terminal command to start synaptic.

---

### Post by Colin@oxford on 2023-04-16
I installed

xubuntu-22.04.2-desktop-amd64.iso

I then asked for the minimum when it asked what I wanted to do.

Maybe I didn't need to install it - I think that when I asked it to nothing mush happened.  I did not check beforehand whether it was there, but I assumed it was not.

---

### Post by tea for one on 2023-04-16
I've just tried a minimal Xubuntu 22.04 installation in a VM.
Synaptic was included and opened via the menu with a password prompt.
Wayland session not available.

---

### Post by Colin@oxford on 2023-04-16
I am away for a few days - I'll try again when I get back.

---

### Post by Colin@oxford on 2023-04-26
I re-installed and everything seems to be OK.  Strange.

---

### Post by ajgreeny on 2023-04-26
> **Colin@oxford said:**
> I re-installed and everything seems to be OK.  Strange.

Agreed!
But that is the way things occasionally happen and I'm glad you got it running fine now.
Just out of interest, did you use the "minimum install" again this time or the full installation?

---

### Post by Colin@oxford on 2023-04-27
I did exactly as last time, just did not try to install synaptic afterwards :-)

---

