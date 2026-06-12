---
title: "How do you install DirectX 9.0c on Wine?"
date: 2007-01-23
forum: Gaming &amp; Leisure
---

### Post by j.miller565 on 2007-01-23
How do you install DirectX 9.0c on Wine? The game loads to it's start up screen but it's (Incredibly laggy) but the error message in the terminal says

> fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!


so how can I install it?

---

### Post by Phesto on 2007-01-23
Not to sound like an *** but it would help to know what game you are trying to get running.

---

### Post by j.miller565 on 2007-01-23
LEGO Star Wars

---

### Post by rabid emu on 2007-01-23
I was under the impression that Linux uses opengl, not Directx.  Does Wine actually emulate directx successfully?

---

### Post by Phesto on 2007-01-24
i have never tried that game. so i'm not familar with the setup and file structure of the game. If you haven't tried it, try launching the application with the opengl flag for example:
```
wine "application.exe" -opengl
```
if this doesn't work. Let me know what version of wine you are using.
As rabid emu stated wine does not emulate directx very well. If the game has the ability to run in opengl that is what is needed.

---

### Post by Cheizzz on 2007-01-24
As far as I'm concerned, you don't install DirectX on wine, because wine already has quite some Direct3D funcionality to run you non-opengl windows games.

---

### Post by j.miller565 on 2007-01-24
doesn't work. I use wine version 0.9.29-0

---

### Post by YokoZar on 2007-01-25
The short answer is that you don't install DirectX on Wine.  DirectX is a driver, and Wine doesn't do drivers, just apps.

Wine does, however, provide its own implementation of DirectX.  It does this by translating DirectX commands into OpenGL commands, then passing them onto the operating system, in much the same way it translates Windows API commands into X commands.  In order for this to work, however, you need OpenGL working on your computer.

DirectX isn't fully implemented in Wine yet, but gets worked on all the time.  Make sure you're using the latest Wine, as a lot of work has been done since Edgy came out ([http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)).  After installing, just run the app as normal and Wine should try its best.

---

### Post by Sammi on 2007-01-25
> **j.miller565 said:**
> How do you install DirectX 9.0c on Wine?
That's so cute :KS

You need to do some reading about the difference between OpenGL and DirectX, though YokoZar's explaination is very clear and says mostly all you need to understand. Only, DirectX is not a driver it's a collections of multimedia API's.

DirectX is made by Microsoft = closed source
OpenGL is a open community project = open source

---

### Post by dbd on 2007-01-25
Lego Star Wars II doesn't seem to work in wine yet:
[http://appdb.winehq.org/appview.php?iVersionId=6150](http://appdb.winehq.org/appview.php?iVersionId=6150)

So I doubt that the first Lego Star Wars will work either. However it is always worth grabbing the latest version of wine and giving it a spin.

---

### Post by jmiahman on 2007-01-26
Have you tried wine version .9.30 ? It was updated on the 25th and they've done some Direct3D work.

---

### Post by j.miller565 on 2007-01-27
I've tried getting Wine 0.9.30 but when I follow the instructions and when I'm about to install it, it says "you already have the latest version" and afterwards I check what version I have. I realise I still have wine 0.9.29.  

Can someone help me to try an install the latest version of wine please

---

### Post by hikaricore on 2007-01-29
> **j.miller565 said:**
> I've tried getting Wine 0.9.30 but when I follow the instructions and when I'm about to install it, it says "you already have the latest version" and afterwards I check what version I have. I realise I still have wine 0.9.29.  

Can someone help me to try an install the latest version of wine please

From a terminal:

```
sudo gedit /etc/apt/sources.list
```

Type in your password, then paste this at the end of the file:

> 
## Wine ##
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main


Save the sources.list file and close gedit, you should be back to the terminal you started it.

Run:

```

sudo gpg --keyserver subkeys.pgp.net --recv 387EE263 && sudo gpg --export --armor 387EE263 | sudo apt-key add -
sudo apt-get update
sudo apt-get install wine

```

This should add the budgetdedicated wine repo's key to your trusted key list and install the most recent version of wine.  If you run the update notifier in gnome it will also alert you from now on when a new version of wine is available via this repo.

---

### Post by bribaetz on 2008-05-23
yeah do i get the opengl from the terminal

---

