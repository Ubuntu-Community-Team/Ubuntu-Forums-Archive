---
title: "LightDM not working properly!"
date: 2011-10-25
forum: Desktop Environments
---

### Post by MoonLitOwl on 2011-10-25
So I instaled LightDM onto the 2D version of Ubuntu.

I can get the background as a single  solid color, but when I try an image, it instead turns black with a  bunch of tiny white dots all over the damn place.

I'm highly confused by this and would love some help!

---

### Post by Utew on 2011-10-25
Here's a simple little GUI program for changing your login background. 
[http://www.webupd8.org/2011/10/simple-lightdm-manager-change-lightdm.html](http://www.webupd8.org/2011/10/simple-lightdm-manager-change-lightdm.html)

Btw, those dots are coded into lightdm and you'll have those no matter what background image you use.
Also, the black screen simply means it couldn't find the background image you wanted to use.. either due to incorrect naming or incorrect file path (folder).

---

### Post by MoonLitOwl on 2011-10-26
> **Utew said:**
> Here's a simple little GUI program for changing your login background. 
[http://www.webupd8.org/2011/10/simple-lightdm-manager-change-lightdm.html](http://www.webupd8.org/2011/10/simple-lightdm-manager-change-lightdm.html)

Btw, those dots are coded into lightdm and you'll have those no matter what background image you use.
Also, the black screen simply means it couldn't find the background image you wanted to use.. either due to incorrect naming or incorrect file path (folder).

That's the one I used. It doesn't say if I'm supposed to rename my image or put it into a different folder either.

---

### Post by MoonLitOwl on 2011-10-26
> **MoonLitOwl said:**
> That's the one I used. It doesn't say if I'm supposed to rename my image or put it into a different folder either.

Alright so I was able to get it to work when I picked an image from the folder that had the origingal lightdm wallpapers, but when i tried using one of my own, it went right back to the black background.

---

### Post by MoonLitOwl on 2011-10-27
Giving this a bump. I still can't figure out what I'm doing wrong.

---

### Post by Utew on 2011-10-27
Ok, well if all else fails... you can manually change the background image by renaming the default image (warty-final-ubuntu.png) which is in your usr/share/backgrounds   folder.... to something else... say warty-final-ubuntu.old.png  and then copy your _new image_ to that folder and name it warty-final-ubuntu.png (or ,jpg as the case may be).

Alternatively. you can just place your own background images in the same folder.. and use the Simple Lightdm app to change images at will.. again usr/share/backgrounds....

---

### Post by Utew on 2011-10-27
Just playing around with different images and using Simple Lightdm. 

I am having no problems with any images being set as login background.. and it doesn't matter where they are located nor in what folder.  Not sure why you are having problems. 

I'd make sure that the images you are trying to use are either png's or jpg's.. and make sure to hit "Apply" after picking the image you want. (Sorry if I'm stating the obvious here). ;)

---

### Post by MoonLitOwl on 2011-10-28
> **Utew said:**
> Ok, well if all else fails... you can manually change the background image by renaming the default image (warty-final-ubuntu.png) which is in your usr/share/backgrounds   folder.... to something else... say warty-final-ubuntu.old.png  and then copy your _new image_ to that folder and name it warty-final-ubuntu.png (or ,jpg as the case may be).

Alternatively. you can just place your own background images in the same folder.. and use the Simple Lightdm app to change images at will.. again usr/share/backgrounds....

I've been trying to move my wallpapers into that folder, but every time I do, it just goes to the folder where my wallpapers already area. And copy and paste doesn't seem to work either.

---

### Post by dmoconnell on 2011-10-28
first let me add that I had this same problem (thought I didn't use an app to change mine (i edited the config file)
the /usr/share/backgrounds folder is locked down. you need root access.(not to be confused with admin access) you have 2 options. use terminal to move the picture (I can't advice you on how to do this as I myself do not know how to do so) or login as root and then move the picture. (very simple yet many would say that its not a good idea to have root access (you can, inadvertently, compromise your system if your not careful)) 
I am going to assume you'll be careful in the root account. while logged into your account open terminal (ctrl+alt+T) and type sudo passwd root. then follow the prompts (asks for your password then asks for the new password for root) then log out then go to "Other" type root and then the password. then copy and paste into the /usr/share/backgrounds/ folder. If you want to edit the conf file directly I also recommend doing it in root (i've tried in my main account and it just doesn't work (at least for me) go to terminal and type "gksu gedit /etc/lightdm/unity-greeter.conf" (without quotes) then (presuming that you moved the image into /backgrounds folder) change the image to the desired image. click save and close gedit and terminal and log out. simple as that
Dm

---

### Post by devanson on 2012-03-18
> **MoonLitOwl said:**
> So I instaled LightDM onto the 2D version of Ubuntu.

I can get the background as a single  solid color, but when I try an image, it instead turns black with a  bunch of tiny white dots all over the damn place.

I'm highly confused by this and would love some help!

I am having the same issue.. Still not able to pick out why I am getting none other than just some white dots in black screen.

---

### Post by soad6 on 2012-04-23
Ok so for all you who want to change lightdm I found the simple solution to why your background is black. it has to do with permissions. if you look at the original file that is done as the background its permissions are different then that of the new files you added to /usr/share/backgrounds/folder/warty-...

So simply just change permissions for whatever picture you want to rwx.

to do this:

sudo chmod 777 /path_to_picture/picture.jpg
then go and run gksudo simple-lightdm-manager from the terminal and change the picture to the one you just changed permissions for.
then make sure its correctly set in the lightdm config file.( if not correct it so its the same as /path_to_picture/picture.jpg.)
gksu gedit /etc/lightdm/unity-greeter.conf
then log out. 

This works in ubuntu 11.04, 11.10, and 12.04. Also in Linux Mint 12.

---

