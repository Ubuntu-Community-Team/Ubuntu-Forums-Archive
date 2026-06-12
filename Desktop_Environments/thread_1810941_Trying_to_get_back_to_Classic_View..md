---
title: "Trying to get back to Classic View."
date: 2011-07-23
forum: Desktop Environments
---

### Post by Addalaide on 2011-07-23
I am sure this has been posted before. I have no panels after i switched  to the Laptop Desktop from the Classic View. Its a simple fix just go  back to Classic View, but i cant get to the login screen. How can i get  back to the screen to switch desktop views? Is there a way to set it in a  terminal? All i can use is a terminal and somehow i managed a firefox  browser but other then that i cant get to any apps. I have tried several things to reset the panels but no luck so far.

---

### Post by coffeecat on 2011-07-24
Welcome to the forum!

> **Addalaide said:**
> Its a simple fix just go  back to Classic View, but i cant get to the login screen.

Press Alt+PrintScreen+k. This will kill the xserver and all running processes and return you to the login screen. On some keyboards/hardware, you need to use the AltGr key and the Print key may be labelled SysReq.

> **Addalaide said:**
> I have no panels after i switched  to the Laptop Desktop from the Classic View.

By "laptop desktop" do you mean Unity in 11.04/Natty? Or, if not, which version of Ubuntu are you running? If you do mean Unity I can assure you that it's no "laptop" desktop. I'm posting from it using my main desktop machine and a 1920x1200 24" monitor and it makes more sense to me on a large monitor than on a small screen.

> **Addalaide said:**
> I have tried several things to reset the panels but no luck so far.

If you do mean Unity, the panel in Unity is quite different from the classic gnome panel, although it looks similar. Post details of your hardware, including graphics card, and someone may be able to help you get Unity working.

---

### Post by Addalaide on 2011-07-24
I was able to do a Ctrl+Alt+t and open a terminal run gdmsetup and switch. From there i did a sudo reboot and everything worked fine .

The option i was referring to was Ubuntu Netbook Edition, sorry i didnt remember it correctly and couldnt get back to the screen where it was.

---

