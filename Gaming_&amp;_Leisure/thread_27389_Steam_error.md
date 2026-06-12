---
title: "Steam error"
date: 2005-04-15
forum: Gaming &amp; Leisure
---

### Post by eXidos on 2005-04-15
Ok I just started to use ubuntu H.H. today, everything has gone very smoothly but now im having trouble with steam, im getting this error after steam updates itself:

steam.exe (main exception) Win32 structured Exception 7e7a43a8: Attempt to write to virtual address 4241737248 without appropriate access rights.

I did chmod 0777 the dir before i setup steam and now when the app tries to load i get this error. any suggestions?

---

### Post by eXidos on 2005-04-15
Ok I chmoded every file and dir, and launched the app like this ( wine /usr/steam/steam.exe ) now it says that:

This application is requesting an activeX browser object but the mozilla activeX controll is currently not installed do you wish to download and install it?

I hit yes my computer thinks for a bit then i get this:

Steam.exe (main exception) win32 structured exception 7e6c0725: attemt to execute invaled instruction.

Im using wine that i got today downloaded/installed from synaptic

---

### Post by jago25_98 on 2005-06-29
"The solution is simple - simply browse to your Steam folder (usually c:\program files\steam) and delete the file "ClientRegistry.blob". Restart Steam and it should work fine."

---

### Post by Gags666 on 2005-06-29
If you still got problems try to install [Mozilla for Windows](http://www.mozilla.org/products/mozilla1.x/) and the [Mozilla ActiveX Control](http://www.iol.ie/~locka/mozilla/control.htm) **with Wine**. Some games, e.g. "World of Warcraft", do need this.
You should also use the newest version of Wine. The one in the standard repositories of Ubuntu is pretty outdatet as well as the one in the backports as far as I know. Use the official one from Wine like described on [winehq.org](http://www.winehq.org/site/download-deb).

Although you should know that Steam only got a bronze rating on the [application database of Wine](http://appdb.winehq.org/appview.php?appId=1163). For this you would better use [Cedega (formally known as Winex) from Transgaming](http://www.transgaming.com/). The CVS version is free available but you have to compile it by yourself. You can get many information about this at [linux-gamers.net](http://www.linux-gamers.net/modules/wfsection/index.php?category=1).

---

### Post by jsimmons on 2005-06-29
[QUOTE=Gags666]If you still got problems try to install [Mozilla for Windows](http://www.mozilla.org/products/mozilla1.x/) and the [Mozilla ActiveX Control](http://www.iol.ie/~locka/mozilla/control.htm) **with Wine**. Some games, e.g. "World of Warcraft", do need this.
You should also use the newest version of Wine. The one in the standard repositories of Ubuntu is pretty outdatet as well as the one in the backports as far as I know. Use the official one from Wine like described on [winehq.org](http://www.winehq.org/site/download-deb).

Although you should know that Steam only got a bronze rating on the [application database of Wine](http://appdb.winehq.org/appview.php?appId=1163). For this you would better use [Cedega (formally known as Winex) from Transgaming](http://www.transgaming.com/). The CVS version is free available but you have to compile it by yourself. You can get many information about this at [linux-gamers.net](http://www.linux-gamers.net/modules/wfsection/index.php?category=1).[/QUOTE]
 The CVS version doesn't support the various forms of copy protection though.

---

