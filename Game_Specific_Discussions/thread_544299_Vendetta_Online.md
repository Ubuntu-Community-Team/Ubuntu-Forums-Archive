---
title: "Vendetta Online"
date: 2007-09-06
forum: Game Specific Discussions
---

### Post by Perfect Storm on 2007-09-06
**UGA's News Discussion of Vendetta Online.**

Discuss here. All discussions fall under the general rules of the UGA Code. 
No swearing, profanity, nudity or other such subversive images or communications. 
No Personal Attacks. Spamming of any kind will not be tolerated.

---

### Post by compiledkernel on 2007-09-06
How does this game compare to say, X2/X3 egosoft games? 

I couldnt quite bring myself to pay out MMO fees, thats why I ask.

---

### Post by Perfect Storm on 2007-09-06
Honestly I would say x2/x3 is better for solo. And if people want MMO should wait for CCP releasing the binary ubuntu package of EVE-Online (the beta can start anytime soon).
But the diffrent between EVE-Online and Vendetta Online is that EVE-Online is more Strategy and Vendetta Online is about your skill as a person to control the ship.


By the way Vendetta Online guide is under construction.

---

### Post by Sammi on 2007-11-22
Vendetta Online looks interesting.

I know that although it is released to the public, Vendetta is still considered to the in alpha development. As such, how far along would you say it has come in the development. How much of the expected content is implemented?

---

### Post by Vadi on 2008-02-15
I tried the 64bit guide, and got this:

"vadi@ubuntu:~/Desktop$ sh vendetta-linux-amd64-installer.sh
vendetta-linux-amd64-installer.sh: 1: Syntax error: Unterminated quoted string
vadi@ubuntu:~/Desktop$"

Any ideas? I couldn't find a support email on the website.

---

### Post by jasonbrisbane on 2008-05-08
Hui,

I got it working simply by creating a bin directory in my home directory.
ie: /home/<user>/bin

Then run the installer and it works ok.
This is the basic game and the base program will prompt to download the latest version, which is a nice touch. (Hate having to look for versions of programs). 

You can add and modify the basic skins (HUD layout, coloring, etc by creating a skin folder under the .vendetta dir (once you've installed it!) Then look at the wiki site ([http://www.vo-wiki.com/wiki/Main_Page](http://www.vo-wiki.com/wiki/Main_Page)) and download the zip to that skins directory (most zips will actually contain a folder called skin, so you copy it in. Modify the config.ini and add skin=skin/ under the vendetta section and your away.

I'm now using the insurrection skin, so thought I'd share how I did it, for other Ubuntu users!

:guitar:

---

### Post by Vadi on 2008-05-09
Ooh, thanks for the tip.

---

### Post by Tiwaz44 on 2009-05-20
Looks like a cool game, but I have this file "vendetta" in my /home/tiwaz/bin folder which is an executable that when run gives me this error: "There is no Windows program configured to open this type of file."

Help?!  I know it's probably an easy fix... but ...I'm a noob.

Thanks,
Tiwaz

---

### Post by Vadi on 2009-05-20
Try dragging it into the terminal and pressing enter to launch it. The terminal is in Applications - Accessories.

---

### Post by Tiwaz44 on 2009-05-21
```
tiwaz@tiwaz-laptop:~$ sudo '/home/tiwaz/bin/vendetta' 
[sudo] password for tiwaz: 
sudo: /home/tiwaz/bin/vendetta: command not found
tiwaz@tiwaz-laptop:~$ 
```

Didn't seem to work... I like that approach though, since instead of having no reaction it outputs something.

---

### Post by Vadi on 2009-05-21
Their installer was buggy a year ago and still is now. It's trying to use some command which isn't present - and I have no idea which...

---

### Post by HarrisonNapper on 2009-08-22
This may be slightly belated, but if you follow the steps listed in the Linux AMD64 installation section, it should work just fine now. Make sure you delete the .vendetta and bin directories from your home folder first, though. Also, mine says that the default program is Wine, so you may want to install that beforehand just in case. This is also the case if you installed with the Windows installer (though I don't forsee any reason to do so).
 
Can you give us some more details on your system like the distro you're running, specific error message/command the script seems to be looking for, et cetera? I know that was fairly generic and you may have already tried since the 1.8 release and if so, just post that you have and I'll see what I can figure out. Thank you.

---

