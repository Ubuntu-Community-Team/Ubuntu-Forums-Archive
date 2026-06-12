---
title: "Error using Wine (from Synaptic Package Manager, Installing HTML-Kit"
date: 2005-08-02
forum: Desktop Environments
---

### Post by Statik on 2005-08-02
Hi all,

I gave up trying to get the newer, CVS versions of WineX and Cedega installed and I went back to the version of Wine that's in the Repository.

When I try to install HTML-Kit (Chami.org) I get the following output:
> statik@ubuntu:~$ wine HKSetup.exe
Invoking /usr/lib/wine/wine.bin HKSetup.exe ...
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config fil e
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config fil e
fixme:font:load_VDMX Failed to retrieve vTable
fixme:richedit:RichEditANSIWndProc EM_AUTOURLDETECT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
wine-pthread: run.c:522: ME_CalcRunExtent: Assertion `size.cx' failed.
fixme:richedit:ME_ReleaseStyle all style references freed (good!)
Wine failed with return code 3
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset 

This is the one application that I haven't found the equivalent of in native Linux. I use it pretty much daily on my windows box so I'd like to have it here. Any hints?

Statik

---

### Post by KLineD on 2005-08-02
This one is a long shot... I see there's reference to a fontset, maybe this has to do with the ms fonts not installed???

Try installing msttcorefonts package using apt and try again your app, maybe we are lucky and that's it but I can't guarantee anything since I'm no Wine expert.

---

### Post by Statik on 2005-08-02
No go, the fonts are already installed and I reinstalled to verify. Same errors. Also tried running it in Root Terminal and Terminal. Same trouble.

Running it as root gives:
> root@ubuntu:/home/statik # wine HKSetup.exe
Invoking /usr/lib/wine/wine.bin HKSetup.exe ...
fixme:font:load_VDMX Failed to retrieve vTable
fixme:richedit:RichEditANSIWndProc EM_AUTOURLDETECT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
wine-pthread: run.c:522: ME_CalcRunExtent: Assertion `size.cx' failed.
fixme:richedit:ME_ReleaseStyle all style references freed (good!)
Wine failed with return code 3 

Still hoping to get this running.

Statik

---

### Post by KLineD on 2005-08-02
Well in [here](http://www.chami.com/html-kit/support/docs/pages/h000134.html) they say it CAN run on Linux using Wine. I'm not sure if this info is outdated or what. Also, why don't you add the Wine repositories from winehq.org and upgrade your wine copy? Wine is one of those apps you always want the latest version.

---

### Post by Statik on 2005-08-02
And how do I upgrade them? The repository isn't showing me the upgrades. I'll visit the site and see what I can get but more information would be appreciated.

Statik

---

### Post by KLineD on 2005-08-02
To get the upgrade, do the following:

first, add a line to your /etc/apt/sources.list
```

sudo gedit /etc/apt/sources.list

```
Add the following line to the end of sources.list: 
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

Save the modified file and now in a console do:
```

sudo apt-get update

```
To update your package listings. Now in synaptic you should see a wine upgrade available, I have 0.0.20050725-winehq-1. Upgrade using synaptic

---

### Post by Statik on 2005-08-05
It looks like my problems may have been caused by my RAM which seems to be ~30% bad. Incredible that Linux even ran. Replacing it Monday and my problems should be solved (hopefully).

Statik

---

