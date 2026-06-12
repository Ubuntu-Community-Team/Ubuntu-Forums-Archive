---
title: "Baldur's Gate 2 Aum in Feisty"
date: 2007-06-02
forum: Gaming &amp; Leisure
---

### Post by lingenfr on 2007-06-02
I installed BG2 in Feisty using the loki installer. I have KDE 3.5.7 and am using the intel video driver and direct rendering is working. I am running wine 0.9.38. My machine is a Toshiba Libretto U100. When I launch bg2 the response is 'Wine(X) not in your PATH'. Has anyone got this working? There is a README file in the /usr/local/games/bg2 directory that says:

NOTES
=====

        Wine-Config:
        Add these keys to your wine config.

        ;; Baldur's Gate 2
        [AppDefaults\\baldur.exe\\x11drv]
  "Managed"="Y"
        "Desktop"="800x600"
        "DXGrab"="Y"
        [AppDefaults\\BGMain.exe\\x11drv]
        "Managed"="Y"
        "Desktop"="800x600"
        "DXGrab"="Y"
        [AppDefaults\\BGConfig.exe\\x11drv]
        "Managed"="Y"
        "Desktop"="800x600"
        "DXGrab"="Y"

        Wine-Registry:
        Add these keys to your wine registry.
        Replace "\\usr\\local\\games\bg2\\" with YOUR installation direcotry.

        [Software\\Microsoft\\Windows\\CurrentVersion\\App Paths\\BG2Main.Exe]
        @="\\usr\\local\\games\bg2\\BG2Main.Exe"
        "Install"="\\usr\\local\\games\\bg2\\"
        "Path"="\\usr\\local\\games\\bg2\\"

        Wine-Registry location:
        ~/.wine/system.reg
 or
        ~/.transgaming/system.reg
-----

I don't know where to put those wine config changes and the information about changing the registry does not tell you where to make those changes. The paths do not exist, as I have looked through all the \software\microsoft\windows entries.

---

### Post by Ferrat on 2007-06-04
Have you looked thru 

[http://appdb.winehq.org/appview.php?iVersionId=408](http://appdb.winehq.org/appview.php?iVersionId=408)

---

### Post by lingenfr on 2007-06-10
That was not too helpful. Seems that BG2 requires Cedega. I am a subscriber but had not put it on this machine as the loki installer did not say it was required. I installed cedega and got the same error. Instead, I ran the following command and got it going:

cedega /usr/local/games/bg2/BGMain.exe

After all that, I really don't care for the game. I think my WoW playing sons will check it out.

---

