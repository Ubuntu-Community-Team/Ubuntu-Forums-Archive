---
title: "Installing Games..."
date: 2009-07-07
forum: Gaming &amp; Leisure
---

### Post by Aidenstar on 2009-07-07
Hey, I was wondering how you install games on ubuntu. When I put my game disk in the tray, it pops up in ubuntu. I can open it up and view all the files on it. But it won't let me install it, it just shows me this archive thing.

 Is there a way to install games without using wine? I understand that there has been a lot of problems with it. Plus the game I want to play isn't installable with wine...The game I want to play is Star Wars Galactic Battlegrounds Clone Campaigns. Oh, and I have ubuntu 9.04. Thanks for any help you can give me.

---

### Post by LinuxFox on 2009-07-07
If the game is Linux-native, then it could be installed easily.  These installers are sometimes a .run package, an autopackage, or .deb package in the case with Ubuntu.

The only way I could think of installing a Windows game is by using Wine.  I did a quick search on the game, and according to Wikipedia, it's a Windows and MacOS X game.

---

### Post by Grishka on 2009-07-07
perhaps you're double clicking the installer executable? try right clicking and selecting "open with Wine".

---

### Post by SerenityKill3r on 2009-07-07
> **Aidenstar said:**
> Hey, I was wondering how you install games on ubuntu. When I put my game disk in the tray, it pops up in ubuntu. I can open it up and view all the files on it. But it won't let me install it, it just shows me this archive thing.

 Is there a way to install games without using wine? I understand that there has been a lot of problems with it. Plus the game I want to play isn't installable with wine...The game I want to play is Star Wars Galactic Battlegrounds Clone Campaigns. Oh, and I have ubuntu 9.04. Thanks for any help you can give me.

You can't natively run Windows games in Linux.

Think of it as trying to run diesel on a petrol engine. They just won't work together. Now if there was a way to convert that diesel to petrol, that would be done using WINE. WINE basically makes the application think it's being installed on Windows, and converts all the DirectX commands, to OpenGL commands.

---

### Post by Tibuda on 2009-07-07
I have not played Galactic Battlegrounds in Linux, but I know it uses the Age of Empires II engine. Age II runs fine under Wine, so I guess Galactic Battlegrounds will work. EDIT: This is not what the [wine application database says]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3757").

The game is not released yet, but keep an eye on [http://www.imperialwinter.com/](http://www.imperialwinter.com/) . It is a Star Wars RTS that uses the cross-platform Spring engine. This means it would run natively in Linux.

---

### Post by random turnip on 2009-07-07
Why isn't it installable with wine?
Have you tried?
Because i'm yet to find something that wine won't run.

---

### Post by Aidenstar on 2009-07-07
> **danielrmt said:**
> I have not played Galactic Battlegrounds in Linux, but I know it uses the Age of Empires II engine. Age II runs fine under Wine, so I guess Galactic Battlegrounds will work. EDIT: This is not what the [wine application database says]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3757").

The game is not released yet, but keep an eye on [http://www.imperialwinter.com/](http://www.imperialwinter.com/) . It is a Star Wars RTS that uses the cross-platform Spring engine. This means it would run natively in Linux.

Ya, I saw that on the wine database. Oh, and thanks for the heads up on imperial winter, it looks really good.

---

### Post by Aidenstar on 2009-07-07
> **SerenityKill3r said:**
> You can't natively run Windows games in Linux.

Think of it as trying to run diesel on a petrol engine. They just won't work together. Now if there was a way to convert that diesel to petrol, that would be done using WINE. WINE basically makes the application think it's being installed on Windows, and converts all the DirectX commands, to OpenGL commands.

Wow, good comparison...that makes a lot of sense.

---

### Post by Aidenstar on 2009-07-07
> **random turnip said:**
> Why isn't it installable with wine?
Have you tried?
Because i'm yet to find something that wine won't run.

Yes, I figured out how to use wine to install it. The installation worked perfectly. But it runs very slowly. Its good enough though I guess, its better than nothing.

---

