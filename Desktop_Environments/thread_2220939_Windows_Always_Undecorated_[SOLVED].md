---
title: "Windows Always Undecorated? [SOLVED]"
date: 2014-04-30
forum: Desktop Environments
---

### Post by gilga2 on 2014-04-30
Hi! 
I would like to know whether it 'd be possible to set all the windows to "undecorate"?
I can click on the top right of the window to switch to "un/decorate" but I would like to make it automatical for all the programs that I open 
(I like my programs take all the screen without space taken by not useful information for me)

Thanks a lot in advance!

EDIT : My configuration :
Lubuntu 14.04 (LXDE as Desktop environment then)

---

### Post by vasa1 on 2014-04-30
Which distro and desktop environment and window manager are you using?

---

### Post by gilga2 on 2014-04-30
Sorry, I've edited. Lubuntu 14.04 (LXDE as Deskop environment then)

---

### Post by vasa1 on 2014-04-30
Okay, you need to get very familiar with lubuntu-rc.xml!
Here is a nice link: [http://pclosmag.com/html/Issues/201107/page08.html](http://pclosmag.com/html/Issues/201107/page08.html)

Basically, you'll edit the appropriate section of ~/.config/openbox/lubuntu-rc.xml to ensure that windows open undecorated.
For that, you'll need to play with the lines in the <applications> section, near the very end of the file.

```
    <application type="normal">
      <maximized>true</maximized>
      <decor>no</decor>
    </application>

```
will open all application windows full-sized, without decoration.

Also take a look at [https://help.ubuntu.com/community/Lubuntu/Windows#Launching_Windows_Maximized](https://help.ubuntu.com/community/Lubuntu/Windows#Launching_Windows_Maximized). That mentions a GUI-based option as well but you need to do a bit of groundwork ensuring that program's dependencies are met.

---

### Post by gilga2 on 2014-04-30
Thanks a lot vasa! It was exactly what I needed!
Good day to you ! :p

---

