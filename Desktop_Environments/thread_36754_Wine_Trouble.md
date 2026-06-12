---
title: "Wine Trouble"
date: 2005-05-24
forum: Desktop Environments
---

### Post by !nkubus on 2005-05-24
I wanted to install DVDShrink onto my kubuntu.
I heard that it was very easy so i have installed wine then winesetuptk and run it. 

When i launch dvdsrhink installer nothing comes up, but in my process list i see a whole bunch of wine processes.

I also tryed to launch it through konsole but nothing happened until i have hit ctrl-c then suddenly i see dvdshrink installer telling me i've hit ctrl-c and it started to crash like a crazy i had to kill wine.

I have also tried to purge wine configs and reinstall it and i still have the same error


thank you very much , any help will be appreciated.

P.S sorry for my very lame english...

---

### Post by !nkubus on 2005-05-24
This what i get from the konsole:

wine dvdshrink32setup.exe
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
fixme:font:load_VDMX Failed to retrieve vTable
fixme:richedit:RichEditANSIWndProc EM_AUTOURLDETECT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub

thanks again for your help
  **EDIT**

ok i got it i have found that i had to oerwrite a dll:

WINEDLLOVERRIDES="riched20=n" wine dvdshrink32setup.exe

---

### Post by philipacamaniac on 2005-05-24
DVDShrink may not be compatible with Wine. You can try dvd::rip (package name is dvdrip). It is in the Marillat (Multiverse) repositories.

---

### Post by frs-design on 2005-05-25
Hi,

You should try to download winetools and to install all of what you need before.I mean Windows Installer, DCOM, VB5/6 Runtime...

You just have to launch the program and a graphic ui will display and let you choose what to do, it's easy and very usefull.

After installing all the needed files, you got a perfect wine config and a lot of apps are running on linux !

Bye !

---

