---
title: "running Unreal Tournament 2004"
date: 2005-08-18
forum: Gaming &amp; Leisure
---

### Post by bloodpuppy on 2005-08-18
ok, first of, I'm a linux newbie. 

I installed unreal tournament 2004 Editor Choice Edition (the DVD version). the install seems to have gone through fine. but I can't figure out how to start the game. I've noticed a .ut2004 folder in /home but I don't have premissions for it. I've also tried running the game using "run application" which briefly displays the UT splash screen, but then nothing else happens. I haven't installed any patches to the game yet. But then I should be able to start a game even without the patches.

thanks in advance for any help.

---

### Post by bogoliubov on 2005-08-18
Perhaps a silly question, but have you made sure that 3D acceleration is working?

If I remember correctly you can test this by typing "glxinfo | grep rendering" in a terminal.
The result should be "Yes"

Normally you should be able to start UT2004 by opening a terminal and do:
ut2004

then the game should start.

I think there has been some trouble with the Editors edition stuff. I had to install one patch before the bonus pack, then another patch afterwards....

---

### Post by bloodpuppy on 2005-08-18
[QUOTE=bogoliubov]Perhaps a silly question, but have you made sure that 3D acceleration is working?

If I remember correctly you can test this by typing "glxinfo | grep rendering" in a terminal.

The result should be "Yes"[/QUOTE]
I tried that, and I do get a "yes"
[QUOTE=bogoliubov]Normally you should be able to start UT2004 by opening a terminal and do:
ut2004

then the game should start.[/QUOTE]
I try this, I get this message in response:

Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error
[QUOTE=bogoliubov]I think there has been some trouble with the Editors edition stuff. I had to install one patch before the bonus pack, then another patch afterwards....[/QUOTE]
I'll try installing the patch, I'm downloading it now.

thanks for the help.   :grin:

---

### Post by fragmental on 2005-08-18
You should have read and write permissions over the .ut2004 folder in home(every fold in ~/ really).

That's weird that you don't.  Maybe it was an installer bug or something.  I believe, if you cannot read the directory, that is what "Can't find 'ini:Engine.Engine.GameEngine' in configuration file" probably means.

---

### Post by bloodpuppy on 2005-08-18
I "chown'ed the ut2004 folder in home and everything in it, and gave myself rwx permission. That got the game working. no sound though  :-k and I get this message:

open /dev/[sound/]dsp: Device or resource busy
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".

btw, is there anyway to chown and chmod a folder and everything in it all at once.

Thanks again.

---

### Post by gryphius on 2005-08-18
[QUOTE=bloodpuppy]btw, is there anyway to chown and chmod a folder and everything in it all at once.[/QUOTE]


This should be "chmod -R /folder". If not, try "man chmod" and read the part about recursive  ;-)

---

### Post by fragmental on 2005-08-18
[QUOTE=gryphius]This should be "chmod -R /folder". If not, try "man chmod" and read the part about recursive  ;-)[/QUOTE]
 I don't think sound works for me either, in the demo.  You could try searching the forum for a post about someone who had the same problem.  A patch might help.  You could also google.  the lgfaq on icculus.org is a good place to look.  I'm getting ut2004 in the mail in a few days(or a week) so I would be more helpful then.

---

### Post by bloodpuppy on 2005-08-19
I've looked around the forums, invoking "killall esd" in a terminal before running the game works best for me. just run esd afterwards to return sound.

thanks for the 'recursive' tip, I was't sure want recursive ment. I even looked it up in the dictionary; it wasn't much help.

---

### Post by fragmental on 2005-08-19
[QUOTE=bloodpuppy]I've looked around the forums, invoking "killall esd" in a terminal before running the game works best for me. just run esd afterwards to return sound.

thanks for the 'recursive' tip, I was't sure want recursive ment. I even looked it up in the dictionary; it wasn't much help.[/QUOTE]
 I read [this](http://ubuntuforums.org/showthread.php?t=26567) thread and I was going to suggest killall esd, but I didn't.  I think that thread outlines a method that esd will only run when it's needed and that should be a better, more permanent, solution.

---

### Post by linkunderscore on 2005-09-11
same thing happened to me when i installed the demo.

just type

sudo ut2004
password:

and you should be set

---

### Post by haddog on 2005-09-17
just type

sudo ut2004
password:
____________________________________________________________________________

This works!!! Thnx. You have to open a terminal window and type your admin psw but that's ok. As long as I can get my UT2004 Editors Choice Edition fix!!!

---

### Post by fragmental on 2005-09-17
Running games as root is a bad idea.  It's insecure.  If it works as root, you might want to make sure your sound is set to alsa or that your permissions are not messed up.

If it's a sound error, search the forums or the unofficial guide or the wiki for tips on fixing the sound.  You might just want to run off "sound server startup" or "sound for events" and make sure the "multimedia systems selector" is set to alsa.

---

### Post by linkunderscore on 2005-09-17
[QUOTE=fragmental]Running games as root is a bad idea.  It's insecure.  If it works as root, you might want to make sure your sound is set to alsa or that your permissions are not messed up.

If it's a sound error, search the forums or the unofficial guide or the wiki for tips on fixing the sound.  You might just want to run off "sound server startup" or "sound for events" and make sure the "multimedia systems selector" is set to alsa.[/QUOTE]


well this is what i get in console when I try to do it without "sudo"
```
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error
```

---

### Post by fragmental on 2005-09-17
[QUOTE=linkunderscore]well this is what i get in console when I try to do it without "sudo"
```
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error
```[/QUOTE]
 make sure you have write privileges to the .ut2004 directory in your home directory.

---

### Post by linkunderscore on 2005-09-17
[QUOTE=fragmental]make sure you have write privileges to the .ut2004 directory in your home directory.[/QUOTE]


that was it :) 

I love these boards!!! I learn something new everytime I look at them. 

Thanks:)

---

### Post by fragmental on 2005-09-17
I think the installer might do that if you click "play now" or whatever on the installer screen after the installer has finished.  It's kind of lame for it to make the user config directory root only.  I always close the installer and then open the game up separately just to make sure I avoid the issue.

---

### Post by PSyMastR on 2005-09-18
Ive got a weird problem.  I installed it fine, ran it fine, and the intro played in good 3d and everything.  I have no sound though.  My speakers are on and the sound levels I played with were fine.  Why is there no sound output?

---

### Post by fragmental on 2005-09-18
[QUOTE=PSyMastR]Ive got a weird problem.  I installed it fine, ran it fine, and the intro played in good 3d and everything.  I have no sound though.  My speakers are on and the sound levels I played with were fine.  Why is there no sound output?[/QUOTE]
 Because I love to quote myself...
> If it's a sound error, search the forums or the unofficial guide or the wiki for tips on fixing the sound. You might just want to run off "sound server startup" or "sound for events" and make sure the "multimedia systems selector" is set to alsa.

You can also try typing "killall esd" in the terminal before you play.

---

### Post by JimmyBEng on 2005-11-11
I'm getting this error just after splash screen. any thoughts?

```
MeshAnimation HumanMaleA.BipedMaleA: Serial size mismatch: Got 129945, Expected 789286

History:

Exiting due to error
```

---

