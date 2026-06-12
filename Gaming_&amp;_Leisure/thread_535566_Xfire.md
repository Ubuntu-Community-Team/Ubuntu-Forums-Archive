---
title: "Xfire?"
date: 2007-08-26
forum: Gaming &amp; Leisure
---

### Post by azurelight1337 on 2007-08-26
So I downloaded the latest version of Xfire, and when I open the installer with WINE, I get this error...

```
allan@allan-desktop:~$ wine /home/allan/xfire_installer_27409.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"

err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.

```

---

### Post by hikaricore on 2007-08-26
[The WINE Application Database]("http://appdb.winehq.org") is down at the moment, but here's a cache (google) copy of the most recent version listed there:

[http://64.233.167.104/search?q=cache:aJxrS5-vQUEJ:appdb.winehq.org/appview.php%3FiVersionId%3D8681%26iTestingId%3D14426+appdb.winehq.org/appview.php%3FiVersionId%3D8681&hl=en&ct=clnk&cd=1](http://64.233.167.104/search?q=cache:aJxrS5-vQUEJ:appdb.winehq.org/appview.php%3FiVersionId%3D8681%26iTestingId%3D14426+appdb.winehq.org/appview.php%3FiVersionId%3D8681&hl=en&ct=clnk&cd=1)

Pretty much as far as I know and can see here, Xfire does not run under WINE.

I may be wrong, but I'm pretty sure I'm not.

---

### Post by azurelight1337 on 2007-08-26
> **hikaricore said:**
> [The WINE Application Database]("http://appdb.winehq.org") is down at the moment, but here's a cache (google) copy of the most recent version listed there:

[http://64.233.167.104/search?q=cache:aJxrS5-vQUEJ:appdb.winehq.org/appview.php%3FiVersionId%3D8681%26iTestingId%3D14426+appdb.winehq.org/appview.php%3FiVersionId%3D8681&hl=en&ct=clnk&cd=1](http://64.233.167.104/search?q=cache:aJxrS5-vQUEJ:appdb.winehq.org/appview.php%3FiVersionId%3D8681%26iTestingId%3D14426+appdb.winehq.org/appview.php%3FiVersionId%3D8681&hl=en&ct=clnk&cd=1)

Pretty much as far as I know and can see here, Xfire does not run under WINE.

I may be wrong, but I'm pretty sure I'm not.

Hmmm, there's people who have gotten it to work on the Xfire forums though... :confused:

I'll try installing it on another PC and then copying the files over, since I get the same error.

---

### Post by hikaricore on 2007-08-26
In that case you may want to search around the forums for more answers.
There have been several xfire related threads around here over time, maybe one of them has answers for you.

---

### Post by Cappy on 2007-08-26
GAIM Install:
[http://ubuntuforums.org/showthread.php?t=504661](http://ubuntuforums.org/showthread.php?t=504661)

Customization on launching games and setting your "in-game" status:
[http://ubuntuforums.org/showthread.php?t=397255](http://ubuntuforums.org/showthread.php?t=397255)

As far as I have read, you cannot use WINE + Xfire because it has several text bugs and I don't know why you would want to anyway because the GAIM plugin is so good.

---

### Post by ner0tic on 2007-08-28
is there a port/release for pidgin? i know the gaim one should work in therory...b ut who knows...

---

### Post by Cappy on 2007-08-28
The answer is in the thread I posted that says "GAIM Install". Answer: Only for Gutsy or if you compile from the plugin from source.

[http://gfire.sourceforge.net/snapshots/](http://gfire.sourceforge.net/snapshots/)

---

### Post by ner0tic on 2007-08-28
> **Cappy said:**
> The answer is in the thread I posted that says "GAIM Install". Answer: Only for Gutsy or if you compile from the plugin from source.

[http://gfire.sourceforge.net/snapshots/](http://gfire.sourceforge.net/snapshots/)

yea i had found it after i posted this.. i'm recompiling it now..

thanks

---

### Post by Burbruee on 2007-08-28
I couldn't install xfire either, but I downloaded an older version and then modified the .ini file to trick xfire into thinking it's the latest version so it won't autoupdate.. And I made it run without any problems, only a hidden dialog box at the launch of the application, but just press enter and it will go away.
Yes, there is a text-bug. But it registeres gaming-hours on your profile, which GAIM does not do as far as I know.

So if you want xfire for chat -> GAIM
But if you just want to register gametime -> Old Xfire-version on WINE with fake .ini file.

---

### Post by ner0tic on 2007-08-28
could you post the tweaked ini?

---

### Post by Cappy on 2007-08-28
> **Burbruee said:**
> 
Yes, there is a text-bug. But it registeres gaming-hours on your profile, which GAIM does not do as far as I know.


It does you just have to configure it like in the second link I gave earlier.

---

### Post by azurelight1337 on 2007-08-28
Does the Gaim add-on track gameplay hours?

---

### Post by Cappy on 2007-08-28
yes

---

### Post by azurelight1337 on 2007-08-28
> **Cappy said:**
> yes

Well, I got it to work anyways, you just have to set the Windows version for X-Fire to Win98 to install it. But there's still those awkward text errors, but I don't use it to chat.

---

