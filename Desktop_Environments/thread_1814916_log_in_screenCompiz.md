---
title: "log in screen/Compiz"
date: 2011-07-30
forum: Desktop Environments
---

### Post by fidelandche on 2011-07-30
Hi all,
I have download the following file GDM-BrazilinuxEye.tar.gz and then extracted the file, it contains a pictue in ajpg file format and GdmGreeterTheme.desktop and olho xml when I click on the GdmGreeterTheme I get asked to open to display contents or run in terminal, I have clicked run in terminal but the log in picture has not changed, what else do I have to do to change the log in screen?

On to Compiz, I am running 11.04 and would like to mess around with Compiz, I know it is installed because I have checked in the software center but I am unable to find it, so where do I look to find it.

Cheers

Andy

---

### Post by fidelandche on 2011-07-30
Ok, I have got Compiz to work, however still stuck on changing the log in screen. I have installed Ubuntu tweak but it will not pick up JPG images, is there any way to change which type of image it will use?

---

### Post by fidelandche on 2011-07-30
Now I have completely broke it! I can log into my system without any problems but all I get is the background image and everything else has gone!! This happened because in Compiz I enabled the cube and to be able to rotate the cube, now all I can do to get to everything is log into classic mode.... (I prefer Unity) I have disabled the cube and the rotate cube options but that did not work, so I have now removed Compiz in the hope this would sort everything out but no this has not changed a thing, I think that when I removed Compiz, Unity went as well as part of the package. So how do I get back to Unity?

---

### Post by wildmanne39 on 2011-07-30
Hi, open a terminal by hitting ctrl+alt+t or tty by hitting ctrl+alt+f1, then run these commands.
```
sudo apt-get update && sudo apt-get install compiz
```
```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```
```
sudo apt-get install ubuntu-desktop
```
then you will most likely still need to reset unity if you do 
```
unity --reset 
```
let reset unity run for three minutes the restart your system and you should be good.

---

### Post by fidelandche on 2011-07-31
Thanks for that.

---

### Post by wildmanne39 on 2011-07-31
Hi, your welcome!

---

