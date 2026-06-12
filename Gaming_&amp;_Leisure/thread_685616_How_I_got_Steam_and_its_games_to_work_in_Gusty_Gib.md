---
title: "How I got Steam and its games to work in Gusty Gibbon."
date: 2008-02-02
forum: Gaming &amp; Leisure
---

### Post by tsav87 on 2008-02-02
Ok, it's really simple, so any noob can do it...

First off you will need the latest version of [**_Cross Over for Linux_**]("http://www.codeweavers.com") to install Steam and DirectX 9.0c.

I have tried the latest version of Wine to install Steam and DirrectX, but it wouldn't install DirectX all the way, some of the files where missing and it wouldn't detect the sound card.

First things first, you will need to create a Windows 2000 Bottle in Cross Over, simply go to Applications>CrossOver>Configuration.  Select the Manage Bottles tab and then select Create New Bottle, then creat a Win2000 bottle.  Last step here is to make it your Default Bottle.

To install Steam with Cross Over, simply select Steam from  the Install Windows Software application found under Applications>CrossOver. 

[IMG]http://i50.photobucket.com/albums/f305/Travis_777/screenshot1.png[/IMG]

Then for DirectX 9.0c, you can download it [**_here_**]("http://filehippo.com/download_directx/").

The DirectX download is a compressed cab file, just choose a folder to dump the files into it.

[IMG]http://i50.photobucket.com/albums/f305/Travis_777/screenshot9.png[/IMG]

[IMG]http://i50.photobucket.com/albums/f305/Travis_777/screenshot3.png[/IMG]

Then open the folder with the DirectX files and run the DXSETUP.exe file.

[IMG]http://i50.photobucket.com/albums/f305/Travis_777/screenshot5.png[/IMG]

[IMG]http://i50.photobucket.com/albums/f305/Travis_777/screenshot6.png[/IMG]

Lastly you will need to download [**_ddrawex.dll_**]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/D/ddrawex.dll/5.03.2600.2180/download.html") and place it in your Win2000 Bottle's system32 folder. Remember, the .cxoffice folder is hidden in your Home folder.  When in your Home folder press CTRL + H and it will show you all the hidden folders inside your Home folder.

[IMG]http://i50.photobucket.com/albums/f305/Travis_777/screenshot8.png[/IMG]

And guess what, you're done, you are ready to install and play games with Steam.

:)

---

### Post by Sockerdrickan on 2008-02-02
Why not use WINE?
It's free and open source [www.winehq.org](www.winehq.org)
Steam and the games that comes with it works.

---

### Post by tsav87 on 2008-02-02
Read towards the top of the post, Wine wouldn't install all of the files needed to run DirectX and it wouldn't recognize a sound card.

---

### Post by Sockerdrickan on 2008-02-02
You are not supposed to install DirectX with WINE, that's what wine is for... god

---

### Post by tsav87 on 2008-02-02
Well it still doesn't work, even if Wine takes the place of DirectX.

---

### Post by Vadi on 2008-02-02
Glad you got it working, CrossOver is an excellent product.

---

### Post by DontThinkSo on 2008-02-02
What exactly was the problem with wine? I have Steam + Portal, HL2, TF2, and CS:S and they all run perfectly on my NVIDIA GeForce Go 7150M, after setting dxlevel to 80 (they run at dxlevel 90, but I set them to 80 for speed improvements).

---

### Post by tsav87 on 2008-02-03
The problem w/ wine was that there were several dll's missing and a .sys file.  And the other, major problem was that DirectX didn't recognize a sound card.  And to top it off, Steam wouldn't launch any games.

Maybe my case was an isolated incident, idk.

---

### Post by Vadi on 2008-02-03
Whatever works. CrossOver is funding a lot of wine development, so they're a good company I'd support if I needed windows apps.

---

### Post by blaise69 on 2008-02-03
I have Steam with Team Fortress 2 working under Wine, I didn't need to install Direct X it worked out of the box with some extra registry entries and the latest version of Wine (0.9.54)

---

### Post by Vadi on 2008-02-03
> **tsav87 said:**
> *-snip-*

And guess what, you're done, you are ready to install and play games with Steam.

:)

You should post this guide on the Ubuntu Wiki. Just mention CrossOver in the title to avoid confusion.

---

### Post by V0X on 2008-02-11
Yeah, you're right. But I needed to do some additional stuff in order for it to work properly:

Enable both OSS and ALSA Drivers in winecfg. Without this the sound wouldn't work.

Add launch option to games: +mat_forcehardwaresync 0. To get the vgui working in Steam games.

---

