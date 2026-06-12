---
title: "Getting Wine programs to work right in Docky"
date: 2012-04-03
forum: Desktop Environments
---

### Post by ngagun on 2012-04-03
Hi all,

I am having problems getting Docky to handle Wine apps (Microsoft Office Word, Excel, Powerpoint) correctly. I'm on xubuntu 11.10 but I suspect this would apply to all variants.

It is easy enough to make launchers, but the windows don't get linked up to the launchers. I tried setting StartupWMClass in the launchers as described here:

[http://wiki.go-docky.com/index.php?title=How_to_Customize_Window_Matching](http://wiki.go-docky.com/index.php?title=How_to_Customize_Window_Matching)

But it doesn't seem to work. If you run xprop on any Wine Office app, you get:

WM_CLASS(STRING) = "WINWORD.EXE", "Wine"

It seems that the second of the two strings is the one used by Docky? And it's always "Wine" no matter which Wine app it is.

Does anyone know how to make Wine launchers for Docky that will correctly recognize their windows?

Thanks.

---

### Post by volkerbradley on 2012-06-05
I'm sure that there are many more elegant ways to do this but the following worked for me when I wanted to open MSWordpad from Docky:
Downloaded an image file for wordpad from images.google.com
Gave the commands: 
locate wordpad.exe
cd /usr/share/applications
sudo -s
vi wordpad.desktop
Entered the following info into that file:
[Desktop Entry]
Version=1.0
Terminal=false
Icon=/home/username/wordpad.png
Type=Application
Categories=Office;
Exec=wine /home/username/.wine/drive_c/windows/system32/wordpad.exe %U
Name=Wordpad
GenericName=Simple Word Processor
Save the file
cp wordpad.desktop ~/Desktop
cd ~/Desktop
sudo chown username.username wordpad.desktop
chmod +x wordpad.desktop
Drag the icon from the deskop to Docky
Hopefully this will work for you with MSWord.  I don't have that application to test it.

---

