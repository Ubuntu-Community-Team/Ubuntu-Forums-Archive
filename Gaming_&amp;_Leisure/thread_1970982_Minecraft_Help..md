---
title: "Minecraft Help."
date: 2012-05-02
forum: Gaming &amp; Leisure
---

### Post by jnesbrandon on 2012-05-02
This may be stupid, but I just got Ubuntu in my laptop and I wanted to get Minecraft on it.  But I do not know how to update thay LWJGL file or find the .minecraft file.  I saw the forum on what to do it was just so confusing! Any help would be greatly appreciated

---

### Post by LinuxCharms on 2012-05-02
My set up is a little funky, but easy to understand:

Download the Mincraft.jar file.

Make a folder on your desktop called "Games".

Put Minecraft.jar in said folder.

Open a Terminal.

Run:

```
java -jar /home/user/Desktop/Games/Minecraft/minecraft.jar
```

Minecraft should open. Once it's all squared away, you can go into your home folder, and you will see a .minecraft file which is where you can add mods into or gets screenshots and such.

---

### Post by Strojar on 2012-05-04
before running minecraft i had to make the file executable, you will have to go with the terminal to the folder where minecraft is and tipe:
```
chmod u+x minecraft.jar
```
wtich means, give user execution on that file.

red somwhere that you can do it in graphics mode just by clicking on the file with the right mouse button and finde a box that says executable, or something like that. didn't try the second option

---

### Post by electrojustin on 2012-05-04
.minecraft is in your home directory: /home/<yourusernamehere>/.minecraft
It is a hidden folder so you won't normally see it in the file manager unless you hit ctrl-h.
Once you find .minecraft just follow the tutorial on the minecraft wiki.

---

### Post by oldos2er on 2012-05-04
Moved to Gaming & Leisure.

---

