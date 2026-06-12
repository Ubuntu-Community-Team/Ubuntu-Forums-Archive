---
title: "create a c drive for dosbox"
date: 2012-03-04
forum: Emulators
---

### Post by flyturkishinc on 2012-03-04
[FONT=Arial Narrow]hello i am new to ubuntu and linux I struggle a bit  but I really enjoy it , I would like to create a c drive for dosbox i have found a great tutorial but I can not create a c drive i've tried 

$ mkdir ~/dos/c  

when i execute the command i get "[/FONT][FONT=monospace][FONT=Arial Narrow]cannot create directory"

not sure why 

it would be great if some one had a tip for me 

thanks in advance[/FONT] 

 [/FONT]

---

### Post by MG&amp;TL on 2012-03-04
*mkdir* will not make more than one level of directories at a time.  You can use:

```
mkdir ~/dos
mkdir ~/dos/c
```

or use the -p (make all parent directories first) flag to do this for you:

```
mkdir -p ~/dos/c
```

I am assuming you are doing this from the terminal, not DOSBOX?

---

### Post by Arthur_D on 2012-03-04
You don't need to create a C drive for dosbox; you can mount any local folder as a drive with e.g. 'mount c /home/username/games/dos/gamename' and then 'c:' and then just launch the game executable with 'gamename.exe'.

---

### Post by mastablasta on 2012-03-05
you can also use a GUi froint end and just skip all this... for example DBGL
[http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)

---

