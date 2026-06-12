---
title: "Nexuiz"
date: 2006-07-27
forum: Gaming &amp; Leisure
---

### Post by Ryan H on 2006-07-27
I'm running Ubuntu 6.06 64-bit edition, and I recently downloaded Nexuiz. I extracted it to /home/ryan/Nexuiz, and in the terminal I ran these commands:
```

# /home/ryan/Nexuiz/nexuiz-linux-x86_64-dedicated
# /home/ryan/Nexuiz/nexuiz-linux-x86_64-glx
# /home/ryan/Nexuiz/nexuiz-linux-x86_64-sdl

```
And when I run any of them the game loads a black screen with the error
> You have reached this menu because due to missing or unlocatable content/data

You may consider adding
-basedir /path/to/nexuiz
to your launch commandline

And I have the option to Quit, or Open Console. Open Console just shows a really choppy page filled with errors, and Quit allows me to exit the program.

I don't know what to do?

-Ryan H

---

### Post by Carrots171 on 2006-07-27
First change to the Nexuiz directory:
```
cd /home/ryan/Nexuiz/
```
And then run Nexuiz:
```
./nexuiz-linux-x86_64-sdl
```
OR
```
./nexuiz-linux-x86_64-glx
```
"nexuiz-linux-x86_64-dedicated" is the server app, so don't run that if you want to play Nexuiz.

---

### Post by Ryan H on 2006-07-27
I get the same results with both of those.=\

-Ryan H

---

### Post by Carrots171 on 2006-07-28
The problem is that the Nexuiz executable can't access the game data for some reason. Check the Nexiuz directory. Is the "data" folder there with the files "common-spog.pk3" and "data20060614" in it?

---

