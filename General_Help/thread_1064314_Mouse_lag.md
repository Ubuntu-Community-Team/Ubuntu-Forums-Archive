---
title: "Mouse lag"
date: 2009-02-08
forum: General Help
---

### Post by Andyet on 2009-02-08
Hello i have problem with my mouse. I have razer diamondback and ubuntu 8.04 64bit. When i`m playing in enemy territory i have in game mouse lag. I don;t know what is wrong. Mouse port is USB 2.0. This problem is only for Enemy Territory. When i moving slowly everything is fine but when i moving fast=lag. My xorg:
Section "InputDevice"
    Identifier      "Configured Mouse"
    Driver          "mouse"
    Option         "CorePointer"
    Option        "Protocol"             "auto" 
    Option        "Buttons"            "7"
    Option        "ButtonMapping"        "1 2 3 6 7"
    Option         "ZAxisMapping"         "4 5"
EndSection

---

### Post by fragos on 2009-02-08
is enemy territory a Windows game?

---

### Post by Andyet on 2009-02-09
No enemy territory is a windows and linux game.

---

### Post by Hemppainen on 2009-03-02
I'm having same kind of problems. My mouse works 100% fine on every other application, but when using Enemy Territory, mouse lags when I'm moving it vertically. Horizontal moving is fine.

---

### Post by Cope57 on 2009-03-02
> **fragos said:**
> is enemy territory a Windows game?

Google is your friend...

---

### Post by fragos on 2009-03-02
True but it's the job of the question asker to provide full information -- I was looking for clarification so I could help the OP. People who need help, need to learn to research their problems.

---

### Post by Hemppainen on 2009-03-15
I noticed I do not have this problem at another machine that is running Intrepid. The machine that has the problem is running Hardy. I also tested that the problem is not about mouse by switching them between these two machines (another is shitty ps/2 and another one good usb logitech). The thread starter has Hardy too, so maybe that is the problem?

EDIT: Just updated from Hardy to Intrepid at this other machine too, and now mouse works perfectly!

---

