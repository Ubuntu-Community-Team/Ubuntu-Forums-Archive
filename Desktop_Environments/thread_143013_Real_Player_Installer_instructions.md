---
title: "Real Player Installer instructions"
date: 2006-03-11
forum: Desktop Environments
---

### Post by JDavid5381 on 2006-03-11
Hey does anyone have the updated installing instructions for Real Player on Ubuntu.  I checked the old ones, but I'm pretty sure they don't work anymore.

Thanks,
James

---

### Post by bluevoodoo1 on 2006-03-11
Have you seen this page?
[https://wiki.ubuntu.com/RealplayerInstallationMethods?highlight=%28realplayer%29](https://wiki.ubuntu.com/RealplayerInstallationMethods?highlight=%28realplayer%29)

it worked perfectly for me. I used the "Installing RealPlayer10 from Real" method.

---

### Post by mishranurag on 2006-03-11
Can anybody play songs from [www.raaga.com](www.raaga.com) or [www.musicindiaonline.com](www.musicindiaonline.com) for me on Dapper? They need real player, which I have installed, but the songs are not playing for me.
Surprisingly, it does play files from BBC News.

Anurag

---

### Post by JDavid5381 on 2006-03-11
Hey thanks for that link.  I tried installing real player with both the instructions for Real Player 10 and Real Player 8 using multiverse, which I now have enabled.  however neither of the attempts were succussful. In both cases I was stopped when I  got this error alert that said

 "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

So I tried running it in the CLI and then I would get:

"dpkg: requested operation requires superuser privilige"

what does this mean, where do I go from hear?  Any help would be much appreciated, thanks :)

-JAmes

---

### Post by bluevoodoo1 on 2006-03-11
Ok, try running what it has told you...
sudo dpkg --configure -a

to see if that fixes the problem it has stated. As for...

"dpkg: requested operation requires superuser privilige"

that means that you have to use dpkg with sudo in front of it.

---

### Post by JDavid5381 on 2006-03-11
Thanks again :) I got it installed ok and everything, however I can only run it by going directly into the RealPlayer directory on my desktop.  The RealPlayer icon shows up in in the Sound and Video section of the Applications menu but when I try to open it from there it says on the bottom panel of my desktop  "opening RealPlayer," but then  it goes away and it never opens. Its not that big of a deal, because I can still use it by going into the folder, but  does anyone know how to fix this so I can open it  from the Sound and Video section of the Applications drop down menu?

---

### Post by bluevoodoo1 on 2006-03-11
Hmmm that part about only clicking on your desktop folder is odd! You could try this. Right click on the menu and click 'edit menus' Navigate over to realplayer 10, right click on it and go to properties. Make sure it says "realplay" for command and run in terminal is NOT checked. 

Also, instead of clicking on your desktop, or using the menu, you can open it in a terminal with "realplay"

---

### Post by JDavid5381 on 2006-03-12
Hmmmn, I right clicked on the menu but didn't get any "edit menus" option.  I right clicked on the Sound and Video menu, was that what I was supposed to do or were you referring to another menu?

---

### Post by JDavid5381 on 2006-03-12
Oh another thing, 'realplay' doesn't work in terminal, it says 'no such file or directory.' Then I tried making one by typing 'sudo mkdir realplay,' than it asked for my passwrd so I typed it and everything, than it says 'mkdir: cannot create directory  `realplay': file exists.:-?

---

### Post by bluevoodoo1 on 2006-03-12
[QUOTE=JDavid5381]Hmmmn, I right clicked on the menu but didn't get any "edit menus" option.  I right clicked on the Sound and Video menu, was that what I was supposed to do or were you referring to another menu?[/QUOTE]


Yes the main menu in the panel "Ubuntu logo Applications Places System" If you right-click over any of those words you should see "Edit Menus" near the top. Should say...

Help
**Edit Menus**
Remove from Panel
Move
Lock to Panel

---

### Post by JDavid5381 on 2006-03-12
Oh ok, I see what you meant.  Yeah, everything is like you said it should be.  :-? weird. . .

---

### Post by JDavid5381 on 2006-03-12
Oh ok, I see what you meant. Yeah, everything is like you said it should be:-?  weird. . .

---

### Post by JDavid5381 on 2006-03-12
Oh ok, I see what you meant. Yeah, everything is like you said it should be.  weird. . .

---

### Post by bluevoodoo1 on 2006-03-12
Yes that is very strange. I'm not a realplayer guru, I rarely use it myself... hmmm.....

---

### Post by bluevoodoo1 on 2006-03-12
It might be an issue of where you installed it. Can realplayer be found in...

/opt/RealPlayer or /usr/local/RealPlayer

Mine is installed in /usr/local/RealPlayer

You said you have a Realplayer folder on your desktop right? Does it contain items such as...

Bin      README  common  install.log  mozilla  postinst  realplay.bak  share
LICENSE  codecs  doc     lib          plugins  realplay  realplay.bin

Because that's what my /usr/local/RealPlayer contains. Could you have installed it to the desktop??

---

