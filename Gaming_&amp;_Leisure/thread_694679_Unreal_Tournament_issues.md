---
title: "Unreal Tournament issues"
date: 2008-02-12
forum: Gaming &amp; Leisure
---

### Post by cris on 2008-02-12
After figuring out how to install the game , i ran into some problems :
1. mouse cursor , after entering the game , it's in the upper left corner  , and there it stays,no matter how much i move the mouse. after presing with both hands on the keyboard , alt+tab and everything else , it starts to respond, and works fine.
2. after playing a while and reentering the game , when I try to resume a saved tournament , there's no save, all the slots are empty. does this have to do with permissions ?

Need help ! :)

---

### Post by FrozenFox on 2008-02-12
1) It would be useful for us to know how you installed it. Did you install it with WINE or native (ie the linuxinstall.sh or whatever)?

2) Probably. Permission problems usually happen if you run an install script or binary or something as sudo/root/su when you should have just run it as the current user.  If you installed it native, NOT in Wine, then I think the default UT2004 folders are /home/YOURNAME/ut2004 and /home/YOURNAME/.ut2004 (notice the dot). In the terminal/console/konsole, please sudo chmod 777 -R /home/YOURNAME/ut2004 and sudo chmod 777 -R /home/YOURNAME/.ut2004 please and tell us if you still have issues. You may have installed them to a different place, but the latter folder with the dot should be made there (after running a game once) no matter where you installed the original files and that's where your stuff is saved anyway, so try changing those permissions. you may also want to chown them, ie sudo chown YOURNAME blahblahut2004paths

---

### Post by cris on 2008-02-12
it's a native linux, and it's the first  unreal tournament , it's not 2004
i did as you said , but the problems remain. 
the game works fine when i start it from terminal with sudo ./ut  but there is problem here too , after winning a few matches , it should open up other game types , like Domination , Capture the flag , instead , it just goes on with Domination.

---

### Post by OffAxis on 2008-02-12
if it's the first unreal tournament (ut99) then this may help.
[http://www.utpg.org/]("http://www.utpg.org/")
Looks like work stopped some time ago, but they've got a few patches on there after the official support stopped. Your issues may have been addressed.

---

### Post by BLTicklemonster on 2008-02-12
Try this.

[http://ubuntuforums.org/showthread.php?t=289796&highlight=unreal+tournament](http://ubuntuforums.org/showthread.php?t=289796&highlight=unreal+tournament)

then come play with us at the black legion, it's a great place, you'll just die, I promise.

:)

---

