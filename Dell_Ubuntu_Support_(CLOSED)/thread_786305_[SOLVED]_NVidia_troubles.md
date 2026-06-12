---
title: "[SOLVED] NVidia troubles"
date: 2008-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DoubleDee on 2008-05-08
Ok, so I've been having troubles with my nvidia drivers ever since the Hardy beta, I figured that the issue would be fixed by release, however, I cant seem to get it to work.  First of I'm running a Dell Latitude d830, with an Nvidia Quadro NVS 140M. Now, I've been googling and searching the forums since Hardy's release and I've found posts people make saying they had problems with nvidia drivers, but got them to work by using envyng. Thats about as detailed as I can find. I've tried using envyng, and the hardware drivers from hardy's menu, and Synaptic package manager but no matter what I do when i reboot, I get a what screen with some colored lines. Now I know that ubuntu is running cuz I can hear the start up sounds. So I figure it must be something wrong with my xorg.conf file. I'm really hoping that someone can help walk me through this. I'm not a complete newb, but I'm no expert either. Please help, I love ubuntu but this is really starting to get frustrating. I thank you for any assistance.

---

### Post by DoubleDee on 2008-05-08
this is really starting to get annoying, like to the point where windows is looking like a better made OS than ubuntu.:mad:

---

### Post by briandu on 2008-05-08
Use this it works

[http://ubuntuforums.org/showthread.php?t=782230](http://ubuntuforums.org/showthread.php?t=782230)

---

### Post by njparton on 2008-05-08
Install envy, use it to remove your drivers and then re-install them.

---

### Post by briandu on 2008-05-08
Not always BTW I used Envyng and it did not work which is why I placed the link

---

### Post by DoubleDee on 2008-05-08
k so i tried what the link said, same outcome, blank white screen with colored lines, when i reboot into recovery and did xfix, now it won't even log in i just get a blank black screen. looks like i'm going to have to do a fresh install in the morning but for now im too tired and frustrated to function, but thanks for the help so far it is appreciated:)

---

### Post by njparton on 2008-05-08
> **briandu said:**
> Not always BTW I used Envyng and it did not work which is why I placed the link
 
Sorry I didn't pick up on that.
 
Did you back up your xorg.conf file first? If so just reinstate it to get back a working system. If you didn't, remember to do that in the future :wink:

---

### Post by briandu on 2008-05-08
What I meant was that the Envy script did not work - I tried varous options but as pe the link I have worked out the manner to achieve this manually. Envy does not cleanup prperly and also does not support 9600GT cards.

---

### Post by DoubleDee on 2008-05-25
ok so i got it working, i followed what reggie123 said at the bottom of this thread

[http://ubuntuforums.org/showthread.php?p=5023945]("http://ubuntuforums.org/showthread.php?p=5023945")

thanks so much to briandu and njparton for trying to help your attempts are appreciated :)

PS the solution in the other thread uses beta software so there is a chance it may not work, but for anyone thats stuck like i was give it a try

---

