---
title: "How to change the splash screen"
date: 2024-06-07
forum: Desktop Environments
---

### Post by makem2 on 2024-06-07
I have just upgraded to Ubuntu 24.04 LTS and hate the splash screen :-(

I checked how to change the splash screen on the 'net and it seems so complex, building, getting involved in Snap etc.

Is there not a simple method such as that when changing the display? My display is black and I would prefer a black splash screen or the 23.04 one, anything other than the current screen. It is a glaring green with 'lightening' white lines from the top.

---

### Post by grahammechanical on 2024-06-07
I do not understand what you mean by splash screen. I have a fresh install Ubuntu 24.04 LTS. I see a splash screen put there by the supplier of the machine. Then the Grub boot screen (I have more than one installation of Ubuntu. Then I get the first login screen which I click to get the second login screen where I enter my password. Both of these screens are black with the new style Ubuntu logo bottom centre.

I suspect that the glaring green screen with 'lightening' white lines from the top is perhaps an issue with the video driver or some setting of the monitor. Perhaps the wrong resolution or frequency. A mismatch of some kind that corrects itself when the desktop loads.

Regards


Regards

---

### Post by makem2 on 2024-06-08
> **grahammechanical said:**
> I do not understand what you mean by splash screen. I have a fresh install Ubuntu 24.04 LTS. I see a splash screen put there by the supplier of the machine. Then the Grub boot screen (I have more than one installation of Ubuntu. Then I get the first login screen which I click to get the second login screen where I enter my password. Both of these screens are black with the new style Ubuntu logo bottom centre.

I suspect that the glaring green screen with 'lightening' white lines from the top is perhaps an issue with the video driver or some setting of the monitor. Perhaps the wrong resolution or frequency. A mismatch of some kind that corrects itself when the desktop loads.

Regards


Regards

The screen I complain about is that which comes up with the login box. In the previous version of Ubuntu it had a much less glaring bright screen. It was subdued and I never bothered to change it.

It is nothing to do with hardware but appears to be the new 'background' to the login box after choosing Ubuntu from the two options as I am dual booting windows.

I would like the following:

1. Grub screen - black (It is)
2. Login screen - black (currently the green screen I don't like)
3. Desktop - black

I don't have a logo anywhere. All I ever see is grub, login and the black desktop with the panel at the top where I like it.

---

### Post by tea for one on 2024-06-08
Are you using Ubuntu 24.04 or Xubuntu 24.04?

---

### Post by Dennis N on 2024-06-08
> The screen I complain about is that which comes up with the login box. 

The screen that shows a login box is not a splash screen. It's the login screen. There is a tool to change it's appearance called **GDM settings**. In GDM Settings, there is an option to change the background color (see attached screenshot).

I use this tool, but be aware that not all the options work with the different versions of GDM. I haven't changed the background - the default dark gray is OK with me.

Note: this tool is for Ubuntu 24.04 LTS (and other Ubuntu releases) which you state you "just upgraded to" in post #1.

---

### Post by tea for one on 2024-06-08
Assuming that the thread prefix (xubuntu) is correct:-
You use lightdm-gtk-greeter-settings to change the background in the login screen for Xubuntu 24.04
Elevated privileges (sudo) required.

---

### Post by makem2 on 2024-06-08
> **tea for one said:**
> Assuming that the thread prefix (xubuntu) is correct:-
You use lightdm-gtk-greeter-settings to change the background in the login screen for Xubuntu 24.04
Elevated privileges (sudo) required.

You assume correct.

Thank you for the push in the right direction. 

LightDM GKT Greeter settings are in my menu [IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG]

---

