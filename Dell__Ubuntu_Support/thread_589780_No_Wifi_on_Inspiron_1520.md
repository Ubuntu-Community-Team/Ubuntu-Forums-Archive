---
title: "No Wifi on Inspiron 1520"
date: 2007-10-24
forum: Dell  Ubuntu Support
---

### Post by damonjablons on 2007-10-24
I installed Ubuntu a few days ago, and everything worked fine.  Recently, I've used synaptic to install some more software, and all of the sudden my wireless networks disappeared.  I know that they exist, because when i'm at school, there's a campus wide network, yet I cannot see it.

I'm still able to use a wired connection, but wireless connections do not show up.  In my network settings, it doesn't show a wireless option, only "wired connection" and "modem connection".

Thanks in advance for your help.

---

### Post by Ek0nomik on 2007-10-24
> **damonjablons said:**
> I installed Ubuntu a few days ago, and everything worked fine.  Recently, I've used synaptic to install some more software, and all of the sudden my wireless networks disappeared.  I know that they exist, because when i'm at school, there's a campus wide network, yet I cannot see it.

I'm still able to use a wired connection, but wireless connections do not show up.  In my network settings, it doesn't show a wireless option, only "wired connection" and "modem connection".

Thanks in advance for your help.

What wireless card do you have?

If you don't know, please post the output of this: (Acessories/Terminal)

```
lspci
```

---

### Post by damonjablons on 2007-10-24
Hey,

The wifi card is a Broadcom Corporation BCM4401-B0 100Base-TX

---

### Post by readingitsideways on 2007-12-11
I'm having the same problem. I've tried installing fwcutter, but it doesn't appear in the restricted drivers


Pleeeaaasse help

Duncan

---

### Post by wirah on 2007-12-11
The Broadcom you have listed is your wired ethernet card.

100BaseTX is that funny Cat5 cable sticking out of the back!

You probably have a Broadcom wireless card too, which will cause you ultimate pain. I suggest swapping it out for an intel wifi card. If you don't fancy that, your best bet is to use Ndiswrapper! Sorry to be the bearer of bad news!

---

### Post by Lorac1949 on 2007-12-11
> **damonjablons said:**
> Hey,

The wifi card is a Broadcom Corporation BCM4401-B0 100Base-TX

You may want to try this:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

A lot of folks have had success going this route.

Unfortunately, I'm not one of them.  After trying some of the Ubuntu forum suggestions, I called Dell.  The rep and her supervisor weren't much help.  Since then I've read something on the Dell Linix forum that says I need to install the Windows driver on Ubuntu.  Once I finish a project I'm working on, I'll try again.  Doesn't make sense that I can connect via wireless in Windows and not in Ubuntu.  I can see the wireless connection in Ubuntu, but that's it.

---

