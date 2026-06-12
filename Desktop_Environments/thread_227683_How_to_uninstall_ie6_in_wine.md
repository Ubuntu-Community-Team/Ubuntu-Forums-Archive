---
title: "How to uninstall ie6 in wine?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by hkl8324 on 2006-08-02
I fail to installed ie6 in wine as wine hanged in the end of the installation process...

When I tried the launch the installer again, the installer told me I have ie6 already installed, but actually I cannot found the exe of ie6 in my internet explorer folder.

I tried using ```
wine uninstaller
``` without success and tried regedit.exe and delete all the entrys with the names related to internet explorer and delete the ie folder itself. The installer still told me that I have ie installed...

How can I solve the problem???

(I need ie because some e-banking and audition site I use to go is IE exclusive...](*,) )

(Note: I also tried the ie4linux script but it also dont work for me...(when I click the ie icon on my desktop...xorg will take up 100% cpu and I have to reboot the computer..](*,) )

---

### Post by rattlerviper on 2006-08-02
> **hkl8324 said:**
> I fail to installed ie6 in wine as wine hanged in the end of the installation process...

When I tried the launch the installer again, the installer told me I have ie6 already installed, but actually I cannot found the exe of ie6 in my internet explorer folder.

I tried using ```
wine uninstaller
``` without success and tried regedit.exe and delete all the entrys with the names related to internet explorer and delete the ie folder itself. The installer still told me that I have ie installed...

How can I solve the problem???

(I need ie because some e-banking and audition site I use to go is IE exclusive...](*,) )

(Note: I also tried the ie4linux script but it also dont work for me...(when I click the ie icon on my desktop...xorg will take up 100% cpu and I have to reboot the computer..](*,) )



Try this 
Apt-get remove wine
Then go to your home folder and view show hidden files.  Delete the WHOLE wine folder.

then
sudo apt-get install wine

winecfg

once the GUI pops up for wine set the sytem preference to 2000 if it is not already there and close it down.

Sudo apt-get install cabextract

now go [here]("http://www.tatanka.com.br/ies4linux/index-en.html#get") and get IEs4Linux and follow there directions...yes it is a tar but you do not have to make a package out of it!  it works on my sytem great.

[SIZE="3"]What are your system specs? I just saw that you had tried IEs4Linux with no luck.  Is this a REALLY REALLY old computer?[/SIZE]

---

