---
title: "Installed Kubuntu, now OpenOffice won't work"
date: 2006-09-29
forum: Desktop Environments
---

### Post by malachi on 2006-09-29
I just installed kubuntu-desktop to try it out. I was currently using the normal Gnome version. Now, OpenOffice doesn't work. I get this error:

```
Details: Failed to execute child process "openoffice.org-2.0" (No such file or directory)

```

I'm at my wits end, because I really need OO.org 2.0 back.

Also, KDE has proven to be a disaster, and I'm wondering how to completely uninstall it and all the programs it installed with it.

---

### Post by hopstah on 2006-09-29
you may have to just reinstall openoffice.

for the removal thing, if you installed using aptitude instead of apt-get, then just execute a ```
sudo aptitude remove kubuntu-desktop
```otherwise i'm afraid i can't help you out.

---

### Post by mephisto786 on 2006-09-30
<<I just installed kubuntu-desktop to try it out. I was currently using the normal Gnome version. Now, OpenOffice doesn't work. >>

This just hit me last nite in the middle of updates. Not only that but Thunderbird got killed and couldnt find its executable....a bit of googling suggested that something in updates and the packages I was adding broke Open Office in KDE.....uninstalling OO I found it uninstalls both ubuntu and kubuntu desktop.  IME, Open Office has been getting slower and buggier of late.  And of course OO has links to Mozilla among other programs.

Generally this system runs well with all three desktops installed. Its when I only install partial desktops and try to save space that lots of apps start to crash.

Atm, seems to be a OO reaction to kde updates...try 2.0.3.....and dont be suprised if you have to reinstall Thunderbird as well....annoying but fixable, the price of free software :P

Oh, btw the solution is to (?!) re-install ubuntu desktop and load the 2.0.3 release of OO which gets downloaded with ubuntu-desktop when you apt-get it.  Then I reinstalled thunderbird via apt as well.   Theres a link if you google on upgrading to the 2.03 with the relevant commands and the apt-get ubuntu-desktop as well.....sorry I dont have it on hand....

Good luck

---

