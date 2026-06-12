---
title: "Launching games that don't appear in the games folder"
date: 2017-12-30
forum: Gaming &amp; Leisure
---

### Post by nolte919 on 2017-12-30
I'm new to lubuntu and don't have a whole lot of linux experience in general. When I install a game using the Synaptic Package Manager it often appears in the game folder from the "start" menu (or whatever it's called, sorry. Dash is it?). But sometimes it doesn't. On one occasion, after muuuuuch googling, I finally found the command I needed to enter from the terminal to launch it. It was something I never would have guessed on my own. So my question is how do I know what command I need to enter if the installed game doesn't appear in the game folder? I'd hate to think I'd have to resort to a ton of googling just to play the game I just installed every single time. I feel there must be a better way. I did search google in general and this forum in particular trying to figure this out but, alas, I've failed.

Sorry if the answer should be obvious to me or if it's been answered a dozen times already.

Thank you so much.

---

### Post by Tadaen_Sylvermane on 2017-12-30
I had this issue with Minecraft. I ended up making a .desktop file and dropping it in my /usr/share/applications. Look up how to create .desktop files and you can create a shortcut to do or launch anything you want.

---

### Post by deadflowr on 2017-12-30
*Thread moved to **Gaming and Leisure***

---

### Post by nolte919 on 2017-12-30
Creating a .desktop file still requires knowing what to launch. That's the part I'm missing. When I install a game how do I know what to launch to run the game? How do I run a game I just installed if it doesn't appear in the games folder?

---

### Post by Holger_Gehrke on 2017-12-31
Look at the properties of the package in synaptic after installation. You'll see that there is a tab named 'Installed files' (This list is - of course - empty for an uninstalled package). Files that got installed into directories on the PATH are likely to be executables.

Holger

---

### Post by nolte919 on 2017-12-31
This advice totally worked! Thank you. I'll add one more tiny tidbit of information for any other hopeless newbies out there. After I navigated to the directory I needed in the terminal I couldn't just type the name of the program. It was cube2 and the program was cube2_client, what I needed to type was ./cube2_client. Go figure. Thanks to everyone who helped me. I don't know if this forum marks questions as answered but this one can be marked as such.

---

### Post by yetimon_64 on 2017-12-31
> **nolte919 said:**
> ...I don't know if this forum marks questions as answered but this one can be marked as such.

You can mark your own threads as [SOLVED] from the "Thread Tools" drop down menu at the top of this thread.

 If you need a guide for how to do so, click on the middle (blue) link in my signature at the bottom of this post. Cheers, yeti.

---

### Post by leunam12 on 2018-01-01
There are easier ways to launch applications when the menu entry is not where you
think it is supposed to be; these are just two possibilities:

Install cairo-dock and set it to auto start with the session, then press Ctrl+F1 and type the name
of the application and it will pop-up on the menu just click it.

Install Synapse and launch it and type the name of the application and press enter.

---

