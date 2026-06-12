---
title: "I cannot mange my widows!"
date: 2009-07-03
forum: Desktop Environments
---

### Post by CheatCat on 2009-07-03
Something strange have happens. My widows have lost its borders and I cannot move them, resize them, switch between them.. Nothing! Look:
[[img]http://img197.imageshack.us/img197/1666/skrmdump3.th.png[/img]](http://img197.imageshack.us/i/skrmdump3.png/)
[[img]http://img197.imageshack.us/img197/4016/skrmdump4.th.png[/img]](http://img197.imageshack.us/i/skrmdump4.png/)

I tried to type in kwin --replace in the console and I get the borders back and can mange them. BUT.. If I close the console window or press Ctrl + C to quit the kwin --replace code, the window loose its borders and I cannot mange them. Also get some errors:

```
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2800117
kwin: X Error (error: BadPixmap [4], request: X_FreePixmap[54], resource: 0x280226d)
kwin: X Error (error: BadPixmap [4], request: X_FreePixmap[54], resource: 0x280226e)
kwin: X Error (error: <unknown>[DAMAGE+0], request: XDamageDestroy[DAMAGE+2], resource: 0x2802204)
kwin: X Error (error: <unknown>[DAMAGE+0], request: XDamageDestroy[DAMAGE+2], resource: 0x2802cf7)
```

Please help! :'(

---

### Post by mine070 on 2009-07-03
Try going to a Backup Or Reinstalling. Is it on the one user?

---

### Post by snl2587 on 2009-07-03
> **mine070 said:**
> Try going to a Backup Or Reinstalling. Is it on the one user?
Err...I wouldn't recommend reinstalling to fix things unless they we failing from the very start (and even then only if an odd setting was selected during the install)

Did you recently change any X server settings, install a different video driver, etc.?

---

### Post by Jarkycat on 2009-07-03
This isn't a fix per say, but try turning off the desktop acceleration/effects to see if that returns the window borders.

---

### Post by pritamps on 2009-07-03
Sorry to be of no help, but your subject is really funny! :lolflag:

> **CheatCat said:**
> Something strange have happens. My widows have lost its borders and I cannot move them, resize them, switch between them.. Nothing! Look:
[[img]http://img197.imageshack.us/img197/1666/skrmdump3.th.png[/img]](http://img197.imageshack.us/i/skrmdump3.png/)
[[img]http://img197.imageshack.us/img197/4016/skrmdump4.th.png[/img]](http://img197.imageshack.us/i/skrmdump4.png/)

I tried to type in kwin --replace in the console and I get the borders back and can mange them. BUT.. If I close the console window or press Ctrl + C to quit the kwin --replace code, the window loose its borders and I cannot mange them. Also get some errors:

```
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2800117
kwin: X Error (error: BadPixmap [4], request: X_FreePixmap[54], resource: 0x280226d)
kwin: X Error (error: BadPixmap [4], request: X_FreePixmap[54], resource: 0x280226e)
kwin: X Error (error: <unknown>[DAMAGE+0], request: XDamageDestroy[DAMAGE+2], resource: 0x2802204)
kwin: X Error (error: <unknown>[DAMAGE+0], request: XDamageDestroy[DAMAGE+2], resource: 0x2802cf7)
```

Please help! :'(

---

### Post by sdlynx on 2009-07-03
ah if only you were running GNOME the fix would be easy...

---

### Post by pritamps on 2009-07-03
Instead of typing in a console, you should press Alt+F2 and type "kwin --replace"

Here's some other stuff you can do:

Goto System Settings -> Default Applications -> Window Manager and make sure it's set to "Use the default KDE Window Manager"

If that is already set and since you say "kwin --replace" works, here's a sort of fix:

Create a start a file called wm.sh with the following contents

```
kwin --replace
```

Then in a terminal

```
chmod +x wm.sh
```

Then goto System Settings -> Advanced -> Autostart...Choose "Add Script", navigate to the folder in which the above is saved and add it. 

That should work...

> **CheatCat said:**
> Something strange have happens. My widows have lost its borders and I cannot move them, resize them, switch between them.. Nothing! Look:
[[img]http://img197.imageshack.us/img197/1666/skrmdump3.th.png[/img]](http://img197.imageshack.us/i/skrmdump3.png/)
[[img]http://img197.imageshack.us/img197/4016/skrmdump4.th.png[/img]](http://img197.imageshack.us/i/skrmdump4.png/)

I tried to type in kwin --replace in the console and I get the borders back and can mange them. BUT.. If I close the console window or press Ctrl + C to quit the kwin --replace code, the window loose its borders and I cannot mange them. Also get some errors:

```
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2800117
kwin: X Error (error: BadPixmap [4], request: X_FreePixmap[54], resource: 0x280226d)
kwin: X Error (error: BadPixmap [4], request: X_FreePixmap[54], resource: 0x280226e)
kwin: X Error (error: <unknown>[DAMAGE+0], request: XDamageDestroy[DAMAGE+2], resource: 0x2802204)
kwin: X Error (error: <unknown>[DAMAGE+0], request: XDamageDestroy[DAMAGE+2], resource: 0x2802cf7)
```

Please help! :'(

---

### Post by CheatCat on 2009-07-13
Well, I cannot find neither Default Applications nor Window Manager in System Settings. Are you sure that you haven't mix it up with GNOME?

But anyway it seems to be fixed now after restarting computer..

---

### Post by Zorael on 2009-07-13
FWIW, the "if only you were using GNOME" comments are unnecessary.

When you enter terminal commands and you want them to start as child processes ("running in the background"), append an ampersand (**&**) after the command.
```
$ kwin --replace **&**
```

Or just run the command via the alt+f2 run box, that should do it, too. No need for the ampersand then.

---

### Post by mine070 on 2010-03-16
Only fixes I can find are for Gnome :S

---

### Post by Fersure on 2010-03-16
> **zorael said:**
> fwiw, the "if only you were using gnome" comments are unnecessary.


+1

---

