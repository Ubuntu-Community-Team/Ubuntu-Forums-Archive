---
title: "Unable to install SkypeMate"
date: 2008-12-17
forum: General Help
---

### Post by unknown user on 2008-12-17
I am trying to install Skypemate, but I have had no luck so far. I have tried the command line and got the following:

unknown@unknown-laptop:~$ sudo apt-get install SkypeMate
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package SkypeMate

Does anyone know how to get around this?

---

### Post by binbash on 2008-12-17
what is skypemate ? and which repos are you trying to use since it is not in official repos?

---

### Post by unknown user on 2008-12-17
Skypemate is used to get usb phones to work in linux/ubuntu
what is repos?

---

### Post by unknown user on 2008-12-26
still having no luck here with this one, is there anyone who can do this?

---

### Post by ispy on 2008-12-26
SkypeMate is a windows driver.

It won't work natively with Ubuntu.

You can try installing WINE and running the .EXE through that.

open Synaptic Package Manager and search for WINE.

---

### Post by GrahamM on 2008-12-31
> **ispy said:**
> SkypeMate is a windows driver.

It won't work natively with Ubuntu.

You can try installing WINE and running the .EXE through that.

open Synaptic Package Manager and search for WINE.

There is a linux driver available from [www.voicegear.ca/downloads](www.voicegear.ca/downloads), but whether it will work with Ubuntu is another thing. There are several threads going on same subject - Do a search. 

I actually got it to work, after a fashion. I can enter numbers from phone but I have to first click on skype-call ordinary phones. It is actually easier to enter the numbers using Skype. Once the call is made, the phone works and it is possible to hang up.  So, in a way, this works as well as a USB headset would.

first chmod +x install-SkypeMate to make it executable
then
sudo ./install-SkypeMate

It asks if you want to install (i/I) - go ahead. This brings up a graphic screen showing something happened, but all you can do is ESC out of it.

Looking at device manager, it shows that the phone is now recognised as a USB device. (see screenshot below). An icon shows up on Desktop that is a link to /usr/bin/SkypeMate but this link is not functional. Presumably this would be needed to allow contact list etc to display on phone and for phone to be fully functional.

Next went to Skype, main menu (bottom left corner icon), options, Sound Devices and change Sound In, Sound out and ringing to VOIP USB Phone, (hw:default,0). (see screenshot)

There is another option for me (plughw:default,0) - this didn't seem to work. Anyone know what that is?

So now phone works similar to a usb headset plus it is possible to use keys to dial if you want to. But that's it.

Maybe installing the windows driver under Wine would be better? anyone tried that?

---

### Post by GrahamM on 2008-12-31
After getting this sort of work, I shut my computer down - I got hundreds of messages saying Yealink unexpected response. same happened when I re-started.

I would like to un-install Skypemate since it does not work properly and I have it on Windows anyway. 

I know how to uninstall using Synaptic, but how do I uninstall a program like this that was installed from a binary file? 

I did a search and found a number of files with names yealink.ko amd yealink.h . There is one Skypemate file in /usr/bin and a link to it on the desktop.

ADDED Later: OK - I got rid of Skypemate by searching for and deleting all files starting with SkypeMate or Skypemate or Yealink. I had also installed it using Wine with no success, so uninstalled it from there too (although it still appears in the Wine Menu)

---

### Post by unknown user on 2009-01-05
> **GrahamM said:**
> 
first chmod +x install-SkypeMate to make it executable
then
sudo ./install-SkypeMate

I have downloaded the file that you stated Graham, but I have no idea how to make it a executable so that I can run the sudo line.
How do I do this as I am stuck on the first part?
Cheers, Phil

---

