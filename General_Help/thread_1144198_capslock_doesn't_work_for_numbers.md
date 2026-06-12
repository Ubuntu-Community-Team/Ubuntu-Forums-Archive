---
title: "capslock doesn't work for numbers"
date: 2009-04-30
forum: General Help
---

### Post by mobidyc on 2009-04-30
Hi,

My keyboard is an AZERTY, french generic 105
When i use the CAPSLOCK and want to write a number, it doesn't.
instead, it writes another letter.

I can obtain what i want by pressing the SHIFT plus the number I want but it's not efficient for me.

I'm on a portable computer so i can't use a keypad.

please, could you help me.

Best regards,
Mobidyc

---

### Post by kanikilu on 2009-04-30
It sounds like you want a function lock rather than caps lock. On keyboards around here it's usually marked as "F Lock" or "Fn Lock".

---

### Post by mobidyc on 2009-04-30
Hi kanikilu,

no it's not.
I want to use my keyboard like i use it on Windows desktop at work.
maybe my english is too bad to explain my problem :/

All that i want is to pass my keyboard in Uppercase when i press the capslock, and pass in Lowercase if I press another time the capslock.

I saw in the layout management that I can activate the capslock (the button with the lock icon) to simulate the SHIFT key continuously pressed.
But it's not what I want because in this case, in oocalc by example, i can't select a cell, it's select multiple cells.

Please tell me if i am clear.

Best regards,
Mobidyc

---

### Post by davidgarcia on 2009-09-21
Yes you are explaining well your problem and I have the same problem as you :(...

In french keyboards numbers are not "principal" used as english keyboard so we need caps lock to "block" the number keys and use it as "principal" but it's seems that linux didn't take in account this issue... somebody could help to see what we can do?

Thanks!
DGS

---

### Post by Leeroy Jenkins on 2009-11-19
I have the exact same problem but also did'nt find any solution yet, eventhough I think there should be one.

is every linux user in france, belgium etc suffering from this?

I love ubuntu but i need the numbers a lot for my work, i will need to switch back to windows if i can not fix it :-(

please help! anybody?

---

### Post by bluenova on 2009-11-19
I work in Brussels but use a GB QWERTY keyboard mainly for this reason.

---

### Post by Leeroy Jenkins on 2009-11-19
found the solution here (thanks to Yves Bruggeman)

[https://bugs.launchpad.net/ubuntu/+bug/292158](https://bugs.launchpad.net/ubuntu/+bug/292158)

works perfect for me! 

in short: include a file (in your keyboard layout file) where you say that a the numerical keys should be seen as letters. make sure you have write privileges  in the /usr folder.

---

### Post by Vinger on 2010-04-05
I have the same problem.
My Keyboard doesn't mension 'caps lock', but 'Shift lock'

Can someone explain howto  use the patch?

Allready thanks.

---

### Post by Vinger on 2010-10-30
Hello,

I had a tip from the dutch forum what solved my problem
In "regional settings - keyboard layout - advanced" you can change a setting that the keyboard uses capslock as shiftlock...

grz

---

### Post by rakoko on 2013-04-24
I got the same problem and I've solved it, I'm using a laptop, the french user will understand what i'm saying 'cause this problem always occur in french system
Open "paramètres systèmes" -> "clavier"->"paramètres d'agencement"->"options"->"comportement de la touche verr. maj." et "cocher verr. maj.active ou desactive maj., ce qui affecte toutes les touches".
That's it and enjoy ubuntu.

---

### Post by wildmanne39 on 2013-04-24
Thread closed. Please do not post in old threads.

---

