---
title: "Possible I may be missing some &quot;crucial&quot; directories?"
date: 2009-05-05
forum: General Help
---

### Post by OxentroT on 2009-05-05
When attempting to download anything or run some programs or files I am faced with errors pertaining to unfindable directories:

> [/home/clyde/Desktop/fixmint2.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/clyde/Desktop/fixmint2.exe or
          /home/clyde/Desktop/fixmint2.exe.zip, and cannot find /home/clyde/Desktop/fixmint2.exe.ZIP, period.

---

### Post by oldos2er on 2009-05-05
Is fixmint2.exe a Windows executable? If so, it won't run natively under Linux; you'd need to use Wine.

---

### Post by Achtung on 2009-05-05
Judging by a quick google, you are trying to install Linux Mint on a thumb drive / usb key. The "fixmint2.exe" is a Windows executable file that is designed to help you install Linux Mint on your thumb drive through a *Windows* Operating System. So boot into Windows and run the .exe file from there. 

Alternately, follow [these]("http://www.pendrivelinux.com/linux-mint-6-flash-drive-install-via-cd/") instructions from pendrivelinux to install the latest Linux Mint (version 6, Felicia) on your thumb drive.

---

### Post by OxentroT on 2009-05-06
Thankyou! I got it running!:guitar:

---

