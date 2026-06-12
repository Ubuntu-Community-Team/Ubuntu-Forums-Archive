---
title: "Black Screen in Minecraft After Logging In"
date: 2013-05-14
forum: Gaming &amp; Leisure
---

### Post by Tununias on 2013-05-14
I played Minecraft in the past, but it's been a while so I didn't have it installed. Anyway, after login, the window just goes blank instead of showing the game. I had the same thing happen in the past and fixed it by updating the LWJGL libraries, but that didn't do anything. I also tried both Java 6 and Java 7. I have Ubuntu 13.04 and the latest version of Minecraft.

Any ideas?

---

### Post by |{urse on 2013-05-14
sudo apt-get install compizconfig-settings-manager[FONT=Lucida Grande, Arial, Lucida Sans Unicode, sans-serif][COLOR=#666666] 

Look around for an option to disable Compositing (sorry I don't have time to google it at the moment)
But that might be the problem.


[/COLOR][/FONT]

---

### Post by Tununias on 2013-05-15
So I'm supposed to uncheck the checkbox that says Enable Composite? A message came up when I started CompixConfig Settings Manager that I could be left with an unusable desktop if I don't know what I'm doing. I just want to be sure thats what I'm supposed to do before I do anything.

---

### Post by derklempner on 2013-05-15
This'll sound silly, but I made the same mistake multiple times before I realized it:

The **lwjgl** files you have to copy over to the **natives** directory actually are packed into a directory named **native**. See the difference in names? Make sure you're not just copying over the directory but instead actually copying the files into the proper directory. That's one of the most common fixes I've seen for the black-screen while loading Minecraft.

---

### Post by DarkAmbient on 2013-05-16
Feel free to try out Minecraftier, link in sig. It can patch lwjgl and a lot more. Feedback and/or ideas is welcomed. :-)

---

### Post by Tununias on 2013-05-17
Sorry for not replying sooner. I treid Minecraftier and it fixed everything. Thanks everyone for all your help.

---

