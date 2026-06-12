---
title: "Steam problem?"
date: 2006-10-02
forum: Desktop Environments
---

### Post by Ebzero on 2006-10-02
Ok i just installed steam using wine I have ubuntu 6.06.1 everything works fine just i cant see anything i mean i got gecko for the html but i cant see what the buttons say, same goes for some games on newgrounds anyone know the fix?
Thanks in advance :D 
Ebzero :)

---

### Post by orb9220 on 2006-10-02
alt-F2 and enter winecfg select the app listed in winecfg and click on graphics. There is a checkbox for double-buffering uncheck it. This only helps in some apps.

Also check and post in games forum since I have seen Steam threads there.

---

### Post by aidanr on 2006-10-02
google filetype:ttf inurl:tahoma

download tahoma.ttf

copy it to ~/.wine/drive_c/windows/fonts

---

### Post by deanhopkins on 2006-10-02
Yeah basically, install the Tahoma font mate :)

---

### Post by Ebzero on 2006-10-02
Alright i downloaded the font and manually found the folder but when i attempt to place the font it says *ERROR while copying to "/usr/share/wine/fonts". You do not have permission to write to this folder.*

any ideas??

When i right click and do propertyes then permissons it says i am not the owner of this file.

---

### Post by aidanr on 2006-10-02
your putting it in the wrong folder, go to your home folder, show hidden files and folders and put it in ./wine/drive_c/windows/fonts

---

### Post by ctrl_freak on 2006-10-18
To install fonts in Linux - or copy them into the fonts folder;

Open a terminal and put:
```
sudo nautilus ~/.wine/drive_c/windows/fonts
```
This should open a file viewer window in your fonts folder, and allow you write access. (Replace the path with the path to your own fonts folder.)

It works the same way for installing fonts into Ubuntu. Just a different path.

Of course this is assuming you are using Ubuntu and Nautilus...

---

