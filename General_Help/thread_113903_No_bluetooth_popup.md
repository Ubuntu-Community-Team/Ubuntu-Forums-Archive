---
title: "No bluetooth popup"
date: 2006-01-07
forum: General Help
---

### Post by hove99 on 2006-01-07
I have been trying for hours :-( to get my bluetooth on my Ubuntu Breezy to connect to my Nokia HS-11W headset and my Nokia 6230. I have followed the guide ([http://ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth+headset)](http://ubuntuforums.org/showthread.php?t=75978&highlight=bluetooth+headset)), but I never get the popup on the PC asking for the pairing pin neither for phone or headset.
When I use the headset it just says "Pairing not allowed".

Can anyone help? Thanks :-)

---

### Post by gpothier on 2006-01-16
Have a look at /var/log/syslog
If it says something like "PIN helper exited abnormally with code 256" then you probably have the same problem than I have: the pin helper program that prompts you for a PIN cannot connect to your display because it is running as root.
A simple and temporary hack is to allow connections to your X server from everybody: type "xhost +" in a terminal (as a normal user) and retry.

It would be nice is things were properly configured out of the box, though...
g

---

### Post by p221072 on 2006-03-20
Thank you so much
your post saved my mental sanity!
I wasn't able to make it through even reading thousand other posts
now finally the pop-up prompts for the pin-code.
You said it's a temporary solution, found out anything new?

thank u again
Paolo

---

### Post by AndrewB on 2006-03-20
You may also wat to read this:[http://ubuntuforums.org/showthread.php?t=43843&highlight=bluetooth]("http://ubuntuforums.org/showthread.php?t=43843&highlight=bluetooth")

It works in Breezy too.

---

### Post by anders.ostling on 2006-03-30
[QUOTE=p221072]Thank you so much
your post saved my mental sanity!
I wasn't able to make it through even reading thousand other posts
now finally the pop-up prompts for the pin-code.
You said it's a temporary solution, found out anything new?

thank u again
Paolo[/QUOTE]

Hi Paolo
I have the same problem pairing an HBH-600 headset. I can see it with hcitool scan, but get permission denied errors. No popups. I am not running as root. Could you please give a step by step instruction on what you did to make it work!

Anders

---

### Post by warpforge on 2006-04-08
My new wiki entry might be of help:
[https://wiki.ubuntu.com/BluetoothDialup](https://wiki.ubuntu.com/BluetoothDialup)

---

