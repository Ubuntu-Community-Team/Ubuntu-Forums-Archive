---
title: "Beryl is Broke"
date: 2007-09-05
forum: Desktop Effects &amp; Customization
---

### Post by Dwiman89 on 2007-09-05
Hey, I recently installed Beryl. It worked great for a while. I was playing with the settings, i made the cube invisable and everything was fine. Then i tryed to put different wallpapers on the different sides. when I did this beryl went absolute haywire, so i restarted. After tha beryl wont work. I undid those settings and it still didnt work. Ive tryed compleatly removing beryl through synaptic, and installing it again. Beryl will still not work. I love beryl, i misss it a lot. Can you please help me fix it?

---

### Post by FuturePilot on 2007-09-05
Right click on Beryl Manager and go to Select Window Manager and select Beryl. It most likely just crashed.

---

### Post by Inxsible on 2007-09-05
Only removing Beryl from synaptic doesn't help. you also have to remove all the config files from your home folder.

The "Different wallpapers on different desktop" has always caused a lot of grief to people. It would sure be nice if it would work flawlessly :)

---

### Post by dulbirakan on 2007-09-05
When something like that happened to me with compiz after removing from synaptic I did

> sudo find / -name "*compiz*"-exec rm -rf {} \;

It removes all files with compiz in their names. It might be dangerous but it worked for me, just replace compiz with beryl and pray that it does not delete anything critical.

---

### Post by -SpaZ on 2007-09-05
> **dulbirakan said:**
> When something like that happened to me with compiz after removing from synaptic I did



It removes all files with compiz in their names. It might be dangerous but it worked for me, just replace compiz with beryl and pray that it does not delete anything critical.

I really would not recommend this method, it could really mess with your system, important files might be deleted, and it might delete things that you still need with Beryl in the name.

---

