---
title: "Login sound gets cut off every time"
date: 2008-08-21
forum: Desktop Environments
---

### Post by Ubuntiac on 2008-08-21
Hi all,

I have Kubuntu + KDE 4.1 on three different computers and all three are cutting off the login sound before it finishes.

Anyone have any ideas how to get around this?


Thanks!

---

### Post by carolinason on 2008-08-22
My install of KDE 4.1 was doing this and then it started working, not sure why, but I was playing with the system sounds. 

Check the sound in K->System Settings->Notifications->Event source = KDE System Notifications - Login

See if the sound file will play there.

---

### Post by maniheer on 2008-08-23
I have that with KDEmod on Arch. I just ignore it because every other sound works :)

---

### Post by Ubuntiac on 2008-08-30
I tried on all three computers, and they all play the sound fine from the system settings -> notification area, but bork every time logging in.

@maniheer - I was prepared to just ignore it, too, but to my wife this is a bigger irritation than the odd X breakage I've had to fix. In her mind, X breaking, I come in and fix it straight away and it goes away, where this is something that makes her log in "discordant" every time. ("Discordant" is very bad for her ;)) Anyway, I guess this is a long way of saying, yes, I understand it's minor, but in terms of wife points it's a major. :)

---

### Post by rlelliott on 2010-12-13
> **Ubuntiac said:**
> I tried on all three computers, and they all play the sound fine from the system settings -> notification area, but bork every time logging in.

@maniheer - I was prepared to just ignore it, too, but to my wife this is a bigger irritation than the odd X breakage I've had to fix. In her mind, X breaking, I come in and fix it straight away and it goes away, where this is something that makes her log in "discordant" every time. ("Discordant" is very bad for her ;)) Anyway, I guess this is a long way of saying, yes, I understand it's minor, but in terms of wife points it's a major. :)


Add about 2 seconds of silence to the end of your startup sound, should fix the problem. I used audacity to add the silence.

---

