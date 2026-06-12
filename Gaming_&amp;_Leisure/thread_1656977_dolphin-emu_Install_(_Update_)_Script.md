---
title: "dolphin-emu Install ( Update ) Script"
date: 2010-12-31
forum: Gaming &amp; Leisure
---

### Post by AngelDE98 on 2010-12-31
I just made an little script which installs / updates dolphin-emu ( Yes , there is an Linux Version ... ) and it is just some piece of code from [here]("https://code.google.com/p/dolphin-emu/wiki/Linux_Build") . 

You need to insert your password ~2 times ! 

Oh , it makes some errors if some folders are not existing . And you NEED to change your username / path where to build in the source or it can not work properly ! I know , it is just an piece of code which needs some improvements and an GUI but at least it is an easy-to-use-bash-script for these who do not want to use the commands at [https://code.google.com/p/dolphin-emu/wiki/Linux_Build](https://code.google.com/p/dolphin-emu/wiki/Linux_Build) . 

Short : Have the LATEST SVN BUILD installed with this nice tool .  

Tip ( ed.granada , Thanks ! ) : Install libnotify-bin for notify-send functions ( I forgott the name but thanks to ed.granada for the name ! )

Changelog in Readme .

First Version : 1.0 ( renamed to Basic , Uploaded )
Next Versions ( Not uploaded ) : 1.2 , 1.3 
Next Versions ( Uploaded ) : 1.1 , 1.4b1 
Canceled ( Not working ) Versions : 1.2 , 1.3
Testing Versions ( Unstable , Can not work ) : 1.4b1

---

### Post by AngelDE98 on 2011-01-02
New Version with new README and with CHANGELOG .

---

### Post by AngelDE98 on 2011-01-02
Could someone at least look here ?

---

### Post by thatguruguy on 2011-01-02
Why not just use the [ppa]("https://launchpad.net/%7Eglennric/+archive/dolphin-emu"), which updates about once a week?

---

### Post by AngelDE98 on 2011-01-03
I used it but the updates are being uploaded tooo rapidly on the main web page ... And I need to track the updates because I want to have the missing body parts bug fixed . And sometimes important updates are not uploaded . I mean , this is only an alternative for such people like me who want the latest version . 

Also , I used the PPA but I noticed it was outdated and somehow Dolphin was slower than the latest release . But next day it was uploaded into the PPA . No bad thing , but I just say . 

So you are right , but it is better ( even the dolphin-emu webpage says it ) to use the LATEST SVN RELEASE .

---

### Post by AngelDE98 on 2011-01-03
1.2 is not starting because it finds no command ( Command XYZ not found ) ... It is most likely corrupted . Gonna try to make another one basing of 1.0 and with the extras of 1.1 . 

Edit : Almost made .

---

### Post by AngelDE98 on 2011-01-03
Umm ... I need help ... My script is somehow no more working properly ... After 1.1 , I did something wrong . Everytime I launch this script it does nothing than giving output like " command wget not found " . Can someone help me please ?

---

### Post by ed.granada on 2011-01-06
Thanks men! I did not tested it yet, but I thank you a lot for doing this work.

I´ll test it in my 10.04 box, and comment results here.

¡Thanks!

---

### Post by ed.granada on 2011-01-06
Hi! Well, I had a "bad start":

When I execute the script, it says:

```
./update_dolphin-emu: línea 7: notify-send: orden no encontrada
```

In  English: ./update_dolphin-emu: line 7: notify-send: order not found.

Is that notify-send a program? I´m running Ubuntu 10.04.

):P

EDIT: notify-send is not on my "standard" ubuntu repositories.

---

### Post by ed.granada on 2011-01-06
Ok, the app that uses "notify-send" is called "libnotify-bin"...

---

### Post by AngelDE98 on 2011-01-07
ed.granada , thanks ! Tip added because I forgott the name myself . And I was AFK , sorry . Do it works for you or do you get other errors ? I need to know because I want to fix it . Thanks !

---

### Post by AngelDE98 on 2011-01-13
Ok , I changed my mind : Use 1.1 or 1.2 . 1.1 is more stable but try 1.2 first . I will pause this project until something big happens ...

---

### Post by TheLittleGreenManIsDead on 2011-02-01
Hi! I have a problem. I'm an absolute Linux noob, running Ubuntu on a Dell Inspiron 1520, and I think I may have messed up somewhere in the install procedure. After everything had finished, it showed this:
[I]
[100%] Built target dolphin-emu
odette@odette-laptop:~/dolphin-emu-read-only/Build$ make install[/I]

so I typed 'dolphin-emu', and then this happened:

[I]odette@odette-laptop:~/dolphin-emu-read-only/Build$ make install dolphin-emu
[  5%] Built target translations
[  7%] Built target bdisasm
[ 14%] Built target lua
[ 14%] Built target lzo2
[ 16%] Built target sfml-network
[ 16%] Built target SOIL
[ 16%] Built target clrun
[ 18%] Built target audiocommon
[ 26%] Built target common
[ 35%] Built target videocommon
[ 36%] Built target videouicommon
[ 39%] Built target videoogl
[ 40%] Built target inputcommon
[ 84%] Built target core
[ 84%] Built target debugger_ui_util
[ 87%] Built target debwx
[ 92%] Built target discio
[100%] Built target dolphin-emu
Install the project...
-- Install configuration: "Release"
CMake Error at cmake_install.cmake:36 (FILE):
  file cannot create directory: /usr/local/share/dolphin-emu/user.  Maybe
  need administrative privileges.


make: *** [install] Error 1[/I]

Now, when I type 'dolphin-emu', I receive this message:
[I]
dolphin-emu: command not found[/I]

What did I do wrong? It was all going well until it finished. Do I need to run the script again with some change? Thanks for your help.

---

### Post by AngelDE98 on 2011-02-01
After ```
make
``` , do ```
sudo make install
``` and then just ```
dolphin-emu
``` , not ```
make install dolphin-emu
``` .

---

### Post by TheLittleGreenManIsDead on 2011-02-01
Thanks a lot. I think it's working now - haven't yet managed to run a game, but it's a learning experience.

---

### Post by cchhrriiss121212 on 2011-02-02
^ You won't be able to run anything at playable levels on a Dell Inspiron 1520, the specs are too weak.

---

### Post by AngelDE98 on 2011-02-02
I grew up with laggy PCs and for me Lag is not such an problem . I got games running , but somehow the 3D models are rendered wrong ( Screen-Sized Triangles in the middle of the Screen flackering and invisible Characters ... ) . I did an stop and have an Idea to make an Bugfix to 1.2 and 1.3 , but it is risky and changes from bash to sh . Gonna do it and upload it .

Edit : Bad news , everything I try , " COMMAND NOT FOUND " at every command . I think I need to rework it from scratch ... Or can someone help me ?

---

