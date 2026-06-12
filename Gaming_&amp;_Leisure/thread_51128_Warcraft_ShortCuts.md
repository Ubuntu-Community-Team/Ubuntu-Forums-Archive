---
title: "Warcraft ShortCuts"
date: 2005-07-22
forum: Gaming &amp; Leisure
---

### Post by Sunil on 2005-07-22
Hey Guys, I recently recieved my copu of Ubuntu 5.04...I absolutely love it.

However i am an avid Warcraft Player and count it as one of my MUST HAVE games installed....

On to the problem..

I have ubuntu updated to all the recent patches (cept openoffice), i have cedega 4.3-1 installed, and i can install warcraft just perfect....however the problem arises when cedefa needs to create the desktop shortcuts (must have these...i could run it from the terminal but its a lot faster for me to use it from the shortcut) Warcraft Prompts to create the shortcuts and goes about its thing, but no shortcuts on the desktop....

My home folder is: /home/sunil

command i use to run the install: sudo cedega /media/cdrom/install.exe

I have been searching for a solution to this problem a while and would appreciate any help u guys can offer...

Sunil

---

### Post by damonw5 on 2005-07-22
[QUOTE=Sunil]Hey Guys, I recently recieved my copu of Ubuntu 5.04...I absolutely love it.

However i am an avid Warcraft Player and count it as one of my MUST HAVE games installed....

On to the problem..

I have ubuntu updated to all the recent patches (cept openoffice), i have cedega 4.3-1 installed, and i can install warcraft just perfect....however the problem arises when cedefa needs to create the desktop shortcuts (must have these...i could run it from the terminal but its a lot faster for me to use it from the shortcut) Warcraft Prompts to create the shortcuts and goes about its thing, but no shortcuts on the desktop....

My home folder is: /home/sunil

command i use to run the install: sudo cedega /media/cdrom/install.exe

I have been searching for a solution to this problem a while and would appreciate any help u guys can offer...

Sunil[/QUOTE]
 Try creating your own shortcuts!

Right-click -> Create Launcher

Give it a name and under "command" type the command you would type in the terminal to play it (such as sudo cedega warcraft [example only]).

Click OK and you have your desktop shortcut!

---

### Post by varunus on 2005-07-22
The windows "shortcut on desktop" thing isn't going to work in Linux, unfortunately.  But you can make your own shortcut as said above.  Just right click the desktop and make a new launcher.  You can also right click the panel, choose add to panel, and choose custom application launcher to make one there.

If you're using a custom launcher, I would make your launcher have the command "gksudo cedega warcraft.exe"(or whatever you would type, but add the gk to the sudo command so it'll make a nice GUI prompt for you).  If you just you sudo, make sure to check the "run in terminal" box just in case.

---

### Post by Sunil on 2005-07-22
[QUOTE=varunus]The windows "shortcut on desktop" thing isn't going to work in Linux, unfortunately.  But you can make your own shortcut as said above.  Just right click the desktop and make a new launcher.  You can also right click the panel, choose add to panel, and choose custom application launcher to make one there.

If you're using a custom launcher, I would make your launcher have the command "gksudo cedega warcraft.exe"(or whatever you would type, but add the gk to the sudo command so it'll make a nice GUI prompt for you).  If you just you sudo, make sure to check the "run in terminal" box just in case.[/QUOTE]
 ok guys thanks a bunch, however just to clarify i would need to include the exact path to the warcraft binary such as 
(eg of command: sudo cedega /home/sunil/Transgaming_drive/.../war3.exe)

Thanks for the Speedy Reply

Sunil

---

### Post by smack on 2005-07-22
You should probably put quotes around the path part so you don't have to put backslashes to cancel out the spaces.

Example

cedega "/home/seth/path/to/war3.exe"


Also, if you have any funny troubles with war3 try using the -opengl switch.


cedega "/home/seth/path/to/war3.exe" -opengl

---

### Post by Sunil on 2005-07-22
kk, will reply later with results, reinstalling Ubuntu now 

I have never had any problems running Warcraft without the -openGL parm it works pretty good, even BETTER than on windows (when i had it, bye windows)

 \\:D/ 

Sunil

---

### Post by Sunil on 2005-07-22
Guys i tried createing the launcher item as we discussed, however it did not work :(

I have read that cedega uses a special format for the shortcuts...im currently investigating this

Sunil

---

### Post by gil-galad on 2005-07-23
Try 

cedega -workdir "<war3 directory>" "<war3 directory>/war3.exe"

---

