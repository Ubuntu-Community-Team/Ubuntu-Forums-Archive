---
title: "USB problem with VirtualBox/Zune"
date: 2009-04-30
forum: General Help
---

### Post by jwharmon on 2009-04-30
I've searched the forums for this, and no one seems to be having the problems I'm having. I switched last week to Ubuntu, and I've been having trouble getting my Zune working properly through VirtualBox.

I've installed the "closed source" Vbox, installed XP, got the service pack updates and installed the Zune software with no problem. However, I have only been able to get the Zune connected once, and then it wouldn't show any music. I have the Zune USB filter enabled, but when I try to activate it I almost always get an error message saying "Microsoft Zune [0200]" is "busy with a previous request." I've enabled and disabled the USB 2.0 setting in VBox to seemingly no effect. I've unmounted the Zune in Ubuntu, but that doesn't seem to do anything either. 

I'm guessing I have to disable a USB setting in Ubuntu. I'm still fairly new to this, so please spell things out.

---

### Post by tjwoosta on 2009-04-30
hmm... strange problem

you shouldn't need to disable usb in ubuntu


im not sure if it has anything to do with the usb support, but have you tried installing the virtualbox guest additions?

---

### Post by jwharmon on 2009-04-30
I knew I'd forget to mention something....yes, the guest additions were installed to set up a share directory.

---

### Post by tjwoosta on 2009-04-30
in the virtual machine, at the top of the window click the devices menu

do you see anything listed under usb devices?

if so, you just need to click on it and it should start to work in the VM

---

### Post by jwharmon on 2009-04-30
When I plug the Zune in, the Microsoft Zune [0200] filter is there. When I click it, I get the "busy with a previous request" error.

---

### Post by tjwoosta on 2009-04-30
ahh.. i see

i somehow missed that part when i first read your post, sorry


it seems almost like an issue with zune rather then the VM usb support

have you tried using it with an actual physical windows install?


EDIT: nevermind, its not a zune problem, i just found this

[http://www.virtualbox.org/ticket/3033]("http://www.virtualbox.org/ticket/3033")

it seems its a bug with virtualbox

---

