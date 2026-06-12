---
title: "Beryl always starts in KWin instead of Beryl"
date: 2007-03-09
forum: Desktop Environments
---

### Post by Metallinut on 2007-03-09
So I've got Beryl installed on my Kubuntu, and it's working just fine.  (ATI, fglrx, XGL)

I've got Beryl in my ~/.kde/Autostart so it starts up when I log in.

But when I login, Beryl seems to default to KWin as the Window Manager.  I can simply right-click on the beryl jewel, and select Beryl from "Select Window Manager," but shouldn't it default to that automatically?  Is there just a simple setting somewhere I need to check?

Thanks,

---

### Post by Metallinut on 2007-03-15
Bump?

---

### Post by FruitieX on 2007-03-15
Maybe you could try to log out and then in and open up a terminal, write beryl. If it worked like this you can make a little shell script into your ~/.kde/Autostart folder that only has one line: beryl. Then you have to go to the properties of the icon, go to the second tab (can't remember the name, only position (not using KDE anymore :)) Check the Make executeable box. Then try to logout and then in and see if it works? If it didn't, delete the file you just created...

Edit: What thee?? I just tried running the beryl command myself and guess what happened! The kwin window manager got running, even though I don't have KDE installed?!?! Lol! :D

Edit2: Just to let you know: I use Xfce4.

Edit3: How about editing the Beryl Autostart entry and making it beryl-manager instead? Does that work?

---

