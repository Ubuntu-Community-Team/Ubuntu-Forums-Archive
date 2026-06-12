---
title: "Spore, Wine, Online Authentication and DirectX"
date: 2008-12-22
forum: General Help
---

### Post by Vicker3000 on 2008-12-22
I can't get Spore to work on either my laptop or my desktop using Wine.  When I try to run it, I immediately get an error saying that it needs to access the internet to verify that I have legal ownership.  I do have a connection to the internet, and I've run other programs in Wine that connected to the internet just fine.

Looking around for a fix, I saw that everyone says to tell it not to install DirectX while installing Spore, as it ruins Wine's built in DirectX capabilities.  Unfortunately, I had told it to install DirectX, which of course didn't work correctly.  Could this be what's causing my problems with the internet authentication?  If so, how would I fix it?  I tried removing Wine and installing it again, but I'm not sure if that would fix it.

I get this error both with and without patching to version 1.03 of Spore.

---

### Post by sedawk on 2008-12-22
A nice thing about wine is that you can install every program in
an isolated enviroment without wasting much disk space.

E.g. set "WINE_PREFIX=/home/user/wine_spore", start "wine winefile"
and select Spore's installer from the file manager (winefile).
Now everything is installed to a subdirectory /home/user/wine_spore,
not your default wine directory.
To cleanly remove Spore you can simply remove directory "wine_spore".

If you have installed more than one application in the same directory
(e.g. the default wine directory) you can try to run 
"wine uninstaller" (without setting WINE_PREFIX first!).

I'm not sure that will remove the DirectX files. If DirectX is
listed as an uninstallable application you might have to remove it too.
(but then what if another application needs it ...).

---

### Post by Vicker3000 on 2008-12-24
Thanks for the reply, but that didn't seem to fix my problem.

On the WineHQ site, it says, "If you have problems with reaching the license server, please build from GIT or use this patch," which is then followed by a link to [http://www.winehq.org/pipermail/wine-patches/2008-September/061125.html](http://www.winehq.org/pipermail/wine-patches/2008-September/061125.html)

That sounds like my problem, but I have no idea how to use the information on that site.  Could someone please help me out with this?  I'm still relatively new to Ubuntu.

---

