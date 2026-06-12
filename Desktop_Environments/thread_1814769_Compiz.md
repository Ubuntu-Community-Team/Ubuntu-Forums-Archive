---
title: "Compiz"
date: 2011-07-30
forum: Desktop Environments
---

### Post by giganut on 2011-07-30
i am having trouble with compiz in the new ubuntu 11.4 some of the features that were in the 10.10 are no longer being installed with the program like 3D windows and deformation. i was wondering if there is a way to fix it?

---

### Post by Frogs Hair on 2011-07-30
Hello and Welcome 

Run the following in the terminal   ```
sudo apt-get install compiz-plugins-extra
```
If you are planning to enable the cube in Unity see the link . See the second link for some tweaks for Unity.  [http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)   
You will need the plugins for either desktop environment .

[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by giganut on 2011-07-30
when i enter it in the terminal i get a error message that reads E: Couldn't find package compiz-plugins-extra

---

### Post by Frogs Hair on 2011-07-30
The plug-ins can also be installed from the software center  , just use the search filter . I tested the command and it is working on my computer. I'm assuming  that you have the CCSM installed already if not install that from the software center first .

---

### Post by giganut on 2011-07-30
thanks for the help, i have the plug-ins now, but now i have to figure out why i keep getting errors in my terminal. any suggestion ?

---

### Post by Frogs Hair on 2011-07-30
> **giganut said:**
> thanks for the help, i have the plug-ins now, but now i have to figure out why i keep getting errors in my terminal. any suggestion ?

Run the update manager or try this .```
sudo apt-get update
```

---

### Post by giganut on 2011-07-30
Thanks for all you help!

---

### Post by giganut on 2011-07-30
where do you find all the commands to run in the terminal?

---

### Post by Frogs Hair on 2011-07-30
> **giganut said:**
> Thanks for all you help!

You're Welcome :)

---

### Post by Frogs Hair on 2011-07-30
> **giganut said:**
> where do you find all the commands to run in the terminal?
[http://linuxcommand.org/](http://linuxcommand.org/)

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)

---

### Post by giganut on 2011-07-30
thanks for all the help

---

### Post by pritam_par on 2011-07-31
[FONT=Arial][SIZE=2]Enabling Cube with unity will kill the unity. This can be solved just follow the process below

1.In compiz setting manager disable these plugin:
[/SIZE][/FONT] [FONT=Arial][SIZE=2]            i) OpenGL[/SIZE][/FONT]
[FONT=Arial][SIZE=2]            ii) Composite[/SIZE][/FONT]
[FONT=Arial][SIZE=2]            iii) Ubuntu unity plugin[/SIZE][/FONT]
[FONT=Arial][SIZE=2]           iv) Desktop wall.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]    Select ***disable plugins*** when a window appears asking for disabling other plugins.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]After disabling these plugins your panels and unity will disappear,don't panic and follow next step.

2. Now enable these plugins sequentially. [/SIZE][/FONT]  
[FONT=Arial][SIZE=2]        i)OpenGl[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       ii)Composite[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]      iii)Desktop cube [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]      iv)Rotate cube[/SIZE][/FONT]
[FONT=Arial][SIZE=2]        v)Ubuntu unity plugin.

And you are done.

source [/SIZE][/FONT][http://http://ubuntuforums.org/showthread.php?t=1780912]("http://http//ubuntuforums.org/showthread.php?t=1780912")

---

