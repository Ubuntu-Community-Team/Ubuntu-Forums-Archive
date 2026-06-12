---
title: "Alt-Tab in window locked mode?"
date: 2006-01-23
forum: Gaming &amp; Leisure
---

### Post by Garyu on 2006-01-23
I was playing Americas Army the other day, and wanted to say a few words to a friend on ICQ, so I tried Alt-tab to exit and keep the game running in the background, but that only opened up some console. 

So I tried Alt-Enter instead, which brought the game to windowed mode. So now I could see the entire desktop, including GAIM, but I couldn't do anything else except keep playing, because the mouse was locked to the game window and Alt-Tab still did nothing except opening up the console. 

So... How do I Alt-Tab in such a case? It is annoying to quit the game and leave the server just to pop back in one minute later... :confused:

---

### Post by phibxr on 2006-01-24
Try using Ctrl+Alt+<left/right arrow> to switch desktops. I used this while playing Warcraft 3.

---

### Post by Garyu on 2006-01-24
[QUOTE=phibxr]Try using Ctrl+Alt+<left/right arrow> to switch desktops. I used this while playing Warcraft 3.[/QUOTE]

well, I tried, but it didn't work for me. It works normally, but not while Americas Army is running. :(

---

### Post by phibxr on 2006-01-25
I guess some games use libraries for the graphics that lock this UI-function. I have a vague recollection of using the feature while playing Enemy Territory.

---

### Post by Garyu on 2006-01-25
[QUOTE=phibxr]I guess some games use libraries for the graphics that lock this UI-function. I have a vague recollection of using the feature while playing Enemy Territory.[/QUOTE]

So that's it? "Get used to it"? Whatever happened to "you can do anything in Linux as opposed to Windows"? Because in XP I have never had any kind of problem Alt-Tabbing, because when that won't work I can always press Ctrl-Esc instead to bring up the start menu...

Come on, there has to be a way to do this?

---

### Post by IsSuE on 2006-01-25
i got the same question, but for quake4. i really want to switch to irc while playing sometimes, but alt + tab just brings up my scores :/ is there any possibility for switching back to desktop?

---

### Post by jon_z on 2006-01-25
Alt - Enter will release the window, I'm not sure howto release the mouse though.

---

### Post by lungdart on 2006-01-26
Same problem here with starcraft. It complains about resolution issues so i used winecfg to enforce window emulation at 640x480. This makes starcraft run in said window which is how i like to play games, non full screen, but no alt+tab or alt+ctrl+left/right to switch desktops.

Sometimes wine openes C:\windows\system\pstores.exe as well, and this opens in a 640x480 sperete window with nothing in it, and i cant get out. I have to ctrl+alt+f1 to kill the wine proccess then go back to X and restart starcraft.

Anyone know how to fix this? is there another way of making something load in a window of its on resoution like an argument? IE wine -r 640x480 starcraft.exe?

Thanks

Edit: Tried disabling "allow Directx apps to stop the mouse from leaving there window" Which allowed me to alt tab to my hearts content. The moust obciously would not stay in the window which is no good, and as well, if i left the window or alt tab'd it would still put the mouse wherever my mouse was in the program. So as i use other apps in linux, starcraft is flying all over the place on the map. Is there a specific DLL that performs this function that we can replace with a standard windows dll file? maybe then alt tab would not get disabled.

Also pstores.exe opens every time now, and i have to kill it to continue starcraft, or move it out of my way. Getting rid of the global emulated window setting removes this, but again starcraft can not launch in that mode on my machine.

---

### Post by Garyu on 2006-01-27
[QUOTE=lungdart]Edit: Tried disabling "allow Directx apps to stop the mouse from leaving there window" Which allowed me to alt tab to my hearts content. The moust obciously would not stay in the window which is no good, and as well, if i left the window or alt tab'd it would still put the mouse wherever my mouse was in the program. So as i use other apps in linux, starcraft is flying all over the place on the map. Is there a specific DLL that performs this function that we can replace with a standard windows dll file? maybe then alt tab would not get disabled.[/QUOTE]

OK, so there is actually a solution for Wine. Then there HAS to be a solution for native software! Only question is, who knows what and how???

I tried searching gconf for "mouse" but nothing in there...

---

### Post by lungdart on 2006-01-27
That isnt really a solution for wine, and also sorry for the typos, I type sloppy some times, it happens.

It's more of a workaround with more drawbacks then benifits. Now it is very interesting indeed to see a native game doing this aswell (Never realized that the game was not being emulated, sorry). This gives me very low hopes of getting it working correctly in wine. If you or anyone has any other native directx or opengl type games that run nativily on linux, give it a try. See if you can alt tab to another program, or if your stuck in that window.

There must be some Issue with X11 and its mouse locking feature for games and the like. Or maybe just drivers. I know im using a Nvidia Geforce FX 5200, with the nvidia drivers. Maybe basic drivers will work for this and not nvidias?

Man I would really like this to work.

---

### Post by minisori on 2006-01-28
It's not the drivers. It happends with some of them also (american army for example). But in most of them the focus changes to another window when u ALT+TAB. I guess is a bug of the game itself.

Try this workaround.. edit xorg.conf and add into the Section "ServerFlags" the Option "AllowDeactivateGrabs" "true". Now when you press CTRL+ALT+/ it would release the mouse focus.

Another workaround would be to start another x server runing the game:
X :1 -ac & DISPLAY=:1 et

---

### Post by Garyu on 2006-04-08
Oh yes! Finally I have the answer to this annoying riddle. :cool:

If you press Alt-Enter you will go from full-screen mode to windowed mode. This way you can see everything, but the mouse is locked to the armyops window. Now press Ctrl-G to release the focus. Then press Alt-Tab to switch applications.

Tadaa. :cool:

I owe the solution to an admin at the "Do not and friends" armyops server who called himself tU.Pilac and just burped it out when someone else asked. :) I already asked him to marry me as a token of my appreciation, but he turned me down on my generous offer. Can't imagine why. :P

---

