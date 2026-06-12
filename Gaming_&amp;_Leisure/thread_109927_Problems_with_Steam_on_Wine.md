---
title: "Problems with Steam on Wine"
date: 2005-12-29
forum: Gaming &amp; Leisure
---

### Post by niels on 2005-12-29
I just installed Steame as described in [this post]("http://www.ubuntuforums.org/showthread.php?t=89697").

Now I'm able to start Steam, but i halts all the time, and is therefor useles. I have Wine 0.9.3. I know there is a newer version, but would it help to compile that one?

When I run Steam my shell writes the following:
> niels@nielslaptop:~/.wine/drive_c/Program Files/Steam$ wine steam.exe
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless


And when I exit Steam (using the 'Close' cross) Wine-systray stays alive.

Can anyone help me. I have never used Wine before...

---

### Post by alinuxfan on 2005-12-29
someone stated that they had problems with the current version of steam but that you could DL an older version here:
[http://mirror.snowulf.com/SteamInstall.exe]("http://mirror.snowulf.com/SteamInstall.exe")
and they said that it helps, now sure if it'll help you or not but it is worth a try
P.S. I found that link in another thread the other day
Adam

---

