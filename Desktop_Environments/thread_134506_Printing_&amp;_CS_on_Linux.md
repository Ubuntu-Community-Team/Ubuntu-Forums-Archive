---
title: "Printing &amp; CS on Linux"
date: 2006-02-22
forum: Desktop Environments
---

### Post by lektrik on 2006-02-22
I'm trying to share my printer on my new Linux box.
I can print just fine, and i just setup samba, and after that windows sees the printer as "ready".

I set my smb.conf to 
[global]
  printcap name = cups  
  printing = cups   
  security = share   
[printers]   
  browseable = yes   
  printable = yes   
  public = yes   
  create mode = 0700   
  guest only = yes   
  guest account = smbprint   
  path = /home/smbprint   

But, when I print from a Windows computer, nothing prints, and no error is recognized in the debug log...
These lines repeat themselves:
D [22/Feb/2006:00:18:27 -0600] ProcessIPPRequest: 4 status_code=0
D [22/Feb/2006:00:18:27 -0600] ReadClient: 4 POST / HTTP/1.1
D [22/Feb/2006:00:18:27 -0600] ProcessIPPRequest: 4 status_code=1

I'm not sure what to do so that I can successfully network print


-----------------------------

Off topic, another problem I have.


After each time I run steam.exe, I get the error Fatal Error: Could not load module "bin/vgui2.dll". I don't want to always have to delete the ClientRegistry.blob to reupdate steam.
Sometimes I also get the error of "Steam.exe (man exception): ERROR: delete of Steam.exe fialed, Win32 Error 32 "Sharing violation"

When I enter a clean load, I still get these messages upon arrival of the MY Game / Server Selectiom Menu ::
ubuntu:~/.wine/drive_c/ProgramFiles/Steam$ wine ~/.wine/drive_c/ProgramFiles/Steam/Steam.exe
Segmentation fault
[email]matthew@ubuntu:~/.wine[/email]/drive_c/ProgramFiles/Steam$ err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless

One other problem beside random Computer lockups I receive is, when loading the game, I see the My Games / Server Selection menu still, and when I click it, just to close it/or move it, my screen pauses and flickers...then continues as normal..

I am very new to Linux & Ubuntu, and any indepth instruction would be much appreciated, as I am in for much wanting to learn this Operating System.
THANKS!

---

