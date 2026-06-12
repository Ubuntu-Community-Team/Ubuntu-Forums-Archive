---
title: "STALKER and Guild Wars both crash"
date: 2007-07-15
forum: Gaming &amp; Leisure
---

### Post by Jordan777 on 2007-07-15
I just recently installed STALKER: Shadow of Chernobyl and Guild Wars and they both crash when I try to start them.  Stalker just gives me a black screen,resetting my screen resolution and then cuts to desktop.  Guild Wars crashes and makes everything except the mouse unresponsive so i have to do a restart.  I installed both of them from the CDs is this not the way to do it?  Is there something I should show you guys so that someone can help me out with what's going on?  I have the latest version of WINE 0.9.41.  I don't know what's going on.  Also if anyone could tell me how to install Septerra Core using WINE because when i use the CD to install and then go to play it says it wasn't installed correctly. :(

---

### Post by cogadh on 2007-07-15
Are you cd-ing to the install directory before you launch the games?
```
cd $HOME/.wine/Program\ Files/Game/Directory
wine game.exe
```
Also, until you get the game running fully, you might try using the "Emulate virtual desktop" option in winecfg, that will prevent the game from screwing up your desktop if/when it crashes.

---

### Post by Jordan777 on 2007-07-15
Well I was just using the link the is automatically made in my applications>Wine>programs folder because Starcraft, Diablo 2/LoD, Return to Castle Wolfenstein all work using that.  I'll try what you said though.

---

### Post by Jordan777 on 2007-07-15
I tried what you said and no luck.  Same crash.  I didn't try emulate windows though because it still would be the same thing.

---

### Post by cogadh on 2007-07-15
The emulate virtual desktop is just for troubleshooting purposes, it creates less hassle when crashes occur.

Have you looked at Wine's AppDB and tried the install/config pointers there?
S.T.A.L.K.E.R. - [http://appdb.winehq.org/appview.php?iVersionId=7377](http://appdb.winehq.org/appview.php?iVersionId=7377)
Guild Wars - [http://appdb.winehq.org/appview.php?iVersionId=7530](http://appdb.winehq.org/appview.php?iVersionId=7530)

---

### Post by Jordan777 on 2007-07-15
I looked through there on STALKER it had my bug (i guess?) listed but I don't understand how to fix it and Guild Wars doesn't even have my problem listed.  I think I'll just continue using them on Windows.  That sucks.  I was a little siked about possibly getting them to work on Ubuntu.  Can't win with them all I guess :(

---

### Post by Jordan777 on 2007-07-15
Oh thanks for trying to help by the way.  I appreciate it.

---

### Post by cogadh on 2007-07-15
You shouldn't give up so quickly. Getting games to run with Wine generally requires more effort than running them in Windows, but it is worth the effort.

What part of the STALKER problem didn't you understand? Also, the Guild Wars page had some general configuration tips that get the game working, but not specific problems/solutions. I was directing you towards that, moreso than a direct problem/solution.

---

### Post by Jordan777 on 2007-07-15
Some of the editing stuff I don't really understand as I'm quite new to the whole Linux/Freedom to mess with stuff scene.  I haven't uninstalled yet so i will still be looking at those pages.

---

### Post by Jordan777 on 2007-07-15
To get S.T.A.L.K.E.R. to run:

   1. Install at least Wine version wine-0.9.35
   2. Make sure sound is working - use OSS, stop all other programs using sound
   3. Use -dsound command line option to start the game. Otherwise it will crash with "Divide by zero" error
   4. Enable GLSL - using ARB will brake some geometry (like flipped or missing guns)
   5. Set "OffscreenRenderingMode" to "fbo" and select "Static lighting" render in the game(dx8 mode) - fixes broken lighting (too bright/dark)
   6. Use -nodistort command line option to fix slowdown from using fbo

Like that.  I starting from #3 how do I do all that?

---

### Post by cogadh on 2007-07-15
Yeah, that is pretty uninformative, isn't it.

3. Lanch the game like this: wine game.exe -dsound
4. Enabling GLSL requires a registry edit
[list]
[*] Run "regedit" from the terminal
[*] Navigate the tree to the HKEY_CURRENT_USER/Software/Wine key
[*]Right-click in the right hand pane and select New > Key
[*]Name the key "Direct3D"
[*]Right-click in the right hand pane again and select New > String value
[*]Name the string "UseGLSL"
[*] Double Click on the new string and enter "enable" 
[/list]
5. The OffScreenRenderingMode is also a registry edit. In the same Direct3D key, do this
[list]
[*]Right-click in the right hand pane and select New > String value
[*]Name the string "OffscreenRenderingMode"
[*]Double click on the new string and enter "fbo"
[/list]
The second part of that instruction is an in-game setting, so you will have to change that once we get the game to launch
6. This is just like the earlier one, just add "-nodistort" after the game executable

---

### Post by Jordan777 on 2007-07-15
Ok so -dsound helps it start up but there is no sound (I guess that's what it does) and now the text is invisible I have to look that up.

---

### Post by cogadh on 2007-07-15
Sorry I hit submit before I finished typing (meant to hit the "Go Advanced" button). I hope you got the full instruction I added after editing.

---

### Post by Jordan777 on 2007-07-15
Yeah I did thanks.  I just wanted to ask is -dsound supposed to make it so I have no sound?  Because that would kind of defeat one of the purposes of my wanting to play the game.  But thank you very much I will try your instructions to see what I come up with.

---

### Post by cogadh on 2007-07-15
As far as I know, it should disable DirectSound functions, but not actually disable sound itself. That particular option is a game option, not a Wine option, so I can't be really sure.

---

### Post by Jordan777 on 2007-07-15
Grrr.  I can only use the OSS driver and I get no sound, text, or full dynamic lighting.  Oh bugger.  Guild Wars starts up but I can't enter any text I'm gonna look that up too.  It seems the invisible text is just a problem that hasn't been fixed with wine for a while.  That sucks.

---

