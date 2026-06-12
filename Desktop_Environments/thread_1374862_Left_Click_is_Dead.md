---
title: "Left Click is Dead"
date: 2010-01-07
forum: Desktop Environments
---

### Post by _Narcisse_ on 2010-01-07
Hello Everyone, Happy New Year.

I need the help of the Ubuntu Community Hive Mind to figure out what's causing my left click to become at best capricious and at worst completely unresponsive since I updated Karmic a week or so ago.
I tried to disable Compiz, of course, and Gnome-Do's dock, reset the X server to it's defaults but nothing works. I have a Nvidia driver on (v 185). When the bug appears, my left click is dead, and so is my right click most of the time, I can't click any button, focus or close windows, click links or tabs. It's very weird. The mouse cursor is behaving fine and so is the keyboard. I figured out that the problem appears depending on which program I start first. Sometimes it's doing it immediately after boot (when I open Thunderbird or Firefox first for example) sometimes not at all, it's quite random. Someone on #ubuntu advised me to test with Xev which I did and it's not registering any event from the mouse. I'm using a desktop computer not a laptop and the mouse (which is a Logitech Trackball) works fine on Windows Vista. I never had any problem like this one in years of Ubuntu or other Linux distros.
Any advise ? Thanks a lot for your help.

---

### Post by RockinRob2258 on 2010-01-07
Does it do this with a regular ol' mouse?  The reason why I ask is in case the problem lies with some sort of issue unique to your type of Logitech mouse (and maybe you can find a workaround).  If it behaves this way with a regular mouse, there may be a problem with your installation of Ubuntu (reinstalling might be a quick and easy fix).

---

### Post by _Narcisse_ on 2010-01-08
Well, I never had any problem with the Logitech trackballs, they all worked fine previously. I already tried with a mouse and the left click's still dead. It's clearly software-related, not hardware. Thanks anyway.

---

### Post by fixitdude on 2010-01-09
That isn't the point, he was asking because it might be a driver issue specific to some sort of Logitech thing, who knows, you don't know and someone is trying to help and you act like you know it all.

So look at the driver issue.

Plug in a regular mouse and reboot so it doesn't detect the Logitech mouse, also you might try to find where you set up the mouse settings type and change it to generic then reboot again and see how that goes.

Also, it might be a hardware issue, it could depend on which way you bend the attached wires or the connector on your motherboard is going bad.

---

### Post by _Narcisse_ on 2010-01-11
@fixitdude: I'm sorry, I really didn't want to sound like I knew it all as you said, I just said I thought it was software related because the mouse worked before the update and on other OSes, that's all. Did not want to be rude.

Anyway, I found how to fix it, I plugged the same mouse I had on the PS/2 port with a USB-to-PS/2 adapter and it's working normally again now. I'd really like to know why it suddenly did this though.

---

### Post by ekim0095 on 2010-01-12
Does anyone know how to completely remove the mouse cursor or move it's initial postion away from the center of the screen? The computer will not have a mouse connected and I do not want to see the cursor in the middle of the monitor. Thanks

---

### Post by _Narcisse_ on 2010-01-12
@ekim0095 : I suggest you creating your own thread, you'll have more answers and more people will look at your question, which is a good one but I dont know how to do that. It should be possible. Bye.

---

### Post by AmaDaden on 2010-01-12
Had the same problem. This fix worked for me. My mouse is a different logitech mouse, it's a MX1000.

---

