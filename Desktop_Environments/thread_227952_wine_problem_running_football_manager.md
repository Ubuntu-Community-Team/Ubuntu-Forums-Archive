---
title: "wine problem running football manager"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Vlatko on 2006-08-02
i am trying to use wine to run football manager 2006. what i did was the following. i copied my fm installation directory to my home folder and tried to run it using the following command.

```
wine /home/vlatko/fm/fm.exe
```

i get the following error:
```
vlatko@vlatko-desktop:~/winetools-0.9jo-III$ wine /home/vlatko/fm/fm.exe
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
```

anyone know how i can fix this? running fm in ubuntu would really decrease my windoze usage. :D

thanks!

---

### Post by Vlatko on 2006-08-03
impossible no one runs fm on wine here! :D come on people this is important!

---

### Post by aptget on 2006-08-03
"err:module:import_dll Library ntoskrnl.exe"

Only thing I can assume is that it's trying to find 'ntoskrnl.exe' and it's coming up with an error. It must be required by the program to run and it doesn't ship with Wine. Copying the exe from Windows and placing it there could fix, but I wouldn't know.

---

### Post by Buffalo Soldier on 2006-08-03
[list]

[*] [WINE HQ Application Database](http://appdb.winehq.org/)

[*] [[http://appdb.winehq.org/appview.php?iAppId=1866](http://appdb.winehq.org/appview.php?iAppId=1866)

[/list]

---

### Post by Buffalo Soldier on 2006-08-03
[list=1]
[*] I've tried to get it to work in WINE. Cause my friend who's a MS Windows fan insist on having it before he can use Ubuntu. But so far I've hit onto a brick wall.

[*] [WINE HQ Application Database](http://appdb.winehq.org/)

[*] You can try voting for Football Manager 2006 here -> [http://appdb.winehq.org/appview.php?iAppId=1866](http://appdb.winehq.org/appview.php?iAppId=1866)

[/list]

---

### Post by Vlatko on 2006-08-03
[QUOTE=Buffalo Soldier]I've tried to get it to work in WINE. Cause my friend who's a MS Windows fan insist on having it before he can use Ubuntu. But so far I've hit onto a brick wall.[/QUOTE]
that is completelly understandable. :D

[QUOTE=Buffalo Soldier]WINE HQ Application Database
You can try voting for Football Manager 2006 here -> [http://appdb.winehq.org/appview.php?iAppId=1866](http://appdb.winehq.org/appview.php?iAppId=1866)[/QUOTE]
i voted but my vote is only 6th. :(

thanks anyway

---

### Post by AndyCooll on 2006-08-08
Yeah, I get the same error messages and I'm also unsure how to fix it. 

Awhile back I too voted for FM, and indeed logged some details about the game.

At the moment I play the game inside my XP VMware image, and it runs perfectly ok. In fact it's now the only reason I keep an XP image at all!

---

### Post by scotty2hott2k on 2006-08-08
the error you are getting ntkernel, is copy protection, you have to use a nocd patch to make it work in wine.

the game runs fine although the cursor doesnt work proeprly (although someone has uploaded a patch/hack to make it work) and the 2d match engine is far too slwo to watch (ive logged a bug but no one has taken a look or commented on it in a few months).

apart from the cusor and 2d pitch the game runs very well, so you just have to watch the game wtih commentry only.

---

### Post by AndyCooll on 2006-08-08
> **scotty2hott2k said:**
> the error you are getting ntkernel, is copy protection, you have to use a nocd patch to make it work in wine.

the game runs fine although the cursor doesnt work proeprly (although someone has uploaded a patch/hack to make it work) and the 2d match engine is far too slwo to watch (ive logged a bug but no one has taken a look or commented on it in a few months).

apart from the cusor and 2d pitch the game runs very well, so you just have to watch the game wtih commentry only.

Thsnks for the information. Do you have a link to the cursor patch?

:cool:

---

### Post by scotty2hott2k on 2006-08-09
[mouse fix patch]("http://bugs.winehq.org/attachment.cgi?id=2736&action=view")

you have to download wine source, apply the patch then recompile it for it to work.

---

