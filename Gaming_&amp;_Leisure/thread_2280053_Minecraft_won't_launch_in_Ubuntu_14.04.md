---
title: "Minecraft won't launch in Ubuntu 14.04"
date: 2015-05-27
forum: Gaming &amp; Leisure
---

### Post by Cu Rua on 2015-05-27
Before: Double-click on Minecraft.jar, launcher launches, play game.
Many Ubuntu updates/Tweaks later... 
After: Double-click on Minecraft.jar, opens with Archive Manager. 
What happened? How do I get Minecraft back?

---

### Post by cwblanch on 2015-05-28
> **Cu Rua said:**
> Before: Double-click on Minecraft.jar, launcher launches, play game.
Many Ubuntu updates/Tweaks later... 
After: Double-click on Minecraft.jar, opens with Archive Manager. 
What happened? How do I get Minecraft back?

You should be able to right-click on the minecraft.jar -> click on "Open with Other Application" -> scroll until you see the Java version you installed and then click open. 
I'm guessing with the updates/tweaks you changed what opens the .jar files.

---

### Post by alex393 on 2015-05-30
Hi,

You can also launch try launching minecraft from the terminal. So for example if my minecraft is in /home/user/.minecraft, then I would do this in order to launch it from the terminal.

**1.**
```
cd /home/user/.minecraft
```

**2.**
```
java -jar launcher.jar
```

---

