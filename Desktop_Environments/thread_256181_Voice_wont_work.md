---
title: "Voice wont work"
date: 2006-09-12
forum: Desktop Environments
---

### Post by MrLeN on 2006-09-12
I tried to make a Skype call. Skype seems to work ok, except the guy couldn't hear me. So I loaded sound recorder to see if my mic was working -- but I got a message saying: 

Your audio capture settings are invalid. Please correct them in multimedia settings. However, I can't find multimedia settings.

MrLeN

---

### Post by WagnerVaz on 2006-09-12
Just execute alsamixer 
adjust the volume and the settings
after it press ESC and run
sudo alsactl store

Hope it help

---

### Post by MrLeN on 2006-09-12
Sorry mate, I am still on my first day using Ubuntu. I have no idea what you mean :confused: 

What is alsamixer?

What do I do with this? 

sudo alsactl store

Type it in Konsole?

Thanks for your help.

MrLeN

---

### Post by WagnerVaz on 2006-09-12
Yes in Konsole can be.

---

### Post by MrLeN on 2006-09-12
Sorry mate, but this doesn't help me much.

MrLeN

---

### Post by WagnerVaz on 2006-09-12
Did you set the volumes, you can browse with arrow keys,
try to change the inputs (in the alsa mixer).

Good Look

---

### Post by MrLeN on 2006-09-12
Where are the volumes?

---

### Post by WagnerVaz on 2006-09-12
In Konsole execute:
alsamixer

You will see a lot of bar that can be up with arrow keys and you can go to anothers pressing the > key and come back with < key.

Up all volumes with mic on hand, speak and up the volumes when mic start reproduce sound press ESC and execute on Konsole:
alsactl store

---

