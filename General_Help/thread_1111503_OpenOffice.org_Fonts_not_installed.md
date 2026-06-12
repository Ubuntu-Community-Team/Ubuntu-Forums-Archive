---
title: "OpenOffice.org Fonts not installed"
date: 2009-03-30
forum: General Help
---

### Post by gtbutler on 2009-03-30
I am running OpenOffice.org 2.4 on Ubuntu 8.04. The fonts for OpenOffice.org are something other than the standard fonts. I have read the FAQ on LaunchPad and have installed the cabextract and msttcorefonts use the following commands,
sudo aptitude update
sudo aptitude install cabextract
sudo aptitude install msttcorefonts

After I ran the command,

sudo fc-cache -f

So far I have not seen any of the standard English fonts.

I have been running OpenOffice.org on a Windows machine with the normal English fonts.

Has anybody got any suggestions? Any and all help will be very much appreciated.

---

### Post by VCoolio on 2009-03-30
You can drop fonts in this folder (create if it does not exist yet) that you want enabled in openoffice:
```
~/.openoffice.org2/user/fonts
```
the 'user' part btw is really 'user', not your username.

---

