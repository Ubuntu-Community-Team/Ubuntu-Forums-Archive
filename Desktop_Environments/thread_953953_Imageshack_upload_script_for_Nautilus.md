---
title: "Imageshack upload script for Nautilus?"
date: 2008-10-20
forum: Desktop Environments
---

### Post by Ajantis on 2008-10-20
Hi guys, I was wondering if such thing exists and finally I managed to get my hands on it.
[http://linux.softpedia.com/get/Desktop-Environment/Tools/Upload-Files-34852.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Upload-Files-34852.shtml)
Seems it's pretty simple, just Bash and Curl, but still it is too difficult for me to edit. Anyway, it works great, but it sends images as an anonymous user, not as a registered one. Ergo, uploaded files are not shown in My Images section.
Do you know any other script which could do that? Or perhaps, if that is not too much, could someone have a look at this script? I tried to contact the author, but I got no response...

---

### Post by Psyphre on 2009-03-02
seems pretty cool, how do i install it into my nautilus?

edit:
found it, just go to .gnome2/nautilus-scripts/

Imageshack works perfectly (at first it may seem like it doesnt work but if you wait a bit, a window will popup with the link).

Rapidshare on the otherhand just doesnt work, i'm guessing the script it outdated for rapidshare :(

---

### Post by nait on 2009-04-02
Take a look at my script, maybe it will be less confusing(progressbars)
[http://www.gnome-look.org/content/show.php/Send2Imageshack?content=100952](http://www.gnome-look.org/content/show.php/Send2Imageshack?content=100952)
Haven't done rapidhsare though.(yet?:D)

---

### Post by binbash on 2009-04-02
> **nait said:**
> Take a look at my script, maybe it will be less confusing(progressbars)
[http://www.gnome-look.org/content/show.php/Send2Imageshack?content=100952](http://www.gnome-look.org/content/show.php/Send2Imageshack?content=100952)
Haven't done rapidhsare though.(yet?:D)

Awesome script,Keep up your good work!

---

### Post by crazybuntu on 2009-06-20
how do u run this script ?? i clicked it and says error no file selected ???

---

### Post by VCoolio on 2009-06-20
Put the script in ~/.gnome2/nautilus-scripts 
(.gnome2 is a hidden directory in your home folder). 

Now right click any file you want to upload and choose scripts > scriptname and watch it do its thing.

If it complains about permissions then in terminal do
sudo chmod u+x ~/.gnome2/nautilus-scripts/scriptname

Check [this link]("https://help.ubuntu.com/community/NautilusScriptsHowto?highlight=%28%28NautilusScriptsHowto%29%29") to find out more about nautilus-scripts.

---

