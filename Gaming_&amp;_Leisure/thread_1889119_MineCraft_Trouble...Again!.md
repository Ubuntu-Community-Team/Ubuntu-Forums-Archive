---
title: "MineCraft Trouble...Again!"
date: 2011-11-30
forum: Gaming &amp; Leisure
---

### Post by HavoK360 on 2011-11-30
Hi All!
Okay so Ive seen a TON of threads on how to mark Minecraft.jar as excutiable (not shure if I spelt it right lawl), but I just have one problem...whats my username? Its Braden Wolfe, but do I type BradenWolfe,braden,Braden, or what? I know how to mark it with the sudo command, but still cant seem to do so. Any help? Thanks!
:)

---

### Post by Jaybyrrd on 2011-11-30
In what application. As in the Ubuntu Login? Or the Minecraft Login?

---

### Post by efflandt on 2011-11-30
It should NOT be necessary to give minecraft.jar execute permission (mine is just rw), but I had to give it other parameters to get it to run even when prefixed with java.  So I use this script simply called "minecraft" to launch it:

```
#!/bin/sh
# Change cd line to your path to orig minecraft.jar, NOT ~/.minecraft/bin
cd ~/Downloads
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```But note that Linux is case sensitive, so if instead of minecraft.jar (small "m") yours is Minecraft.jar (big "M"), you would need to use that case in middle of java line (but not for LauncherFrame).

Any personal scripts (which do need execute permission) should be put in a "bin" directory created in your home directory.  Then the next time you login, ~/bin should automatically be in your $PATH.

---

### Post by creator101 on 2011-11-30
Just type your username the same way as the one you registered.

So for Braden Wolff, type just that (including the space)

---

### Post by creator101 on 2011-11-30
Sorry, spelled that wrong.

---

### Post by luks255 on 2011-11-30
You should give more details about your problem. Is it in the console (which I don't think so) that you have this problem or just in the Minecraft Launcher?

EDIT: Also I don't quite understand the problem :|

-Greetz

---

### Post by Jaybyrrd on 2011-12-02
Have any of these posts solved this yet? If so hit thread tools, mark thread as solved.

---

