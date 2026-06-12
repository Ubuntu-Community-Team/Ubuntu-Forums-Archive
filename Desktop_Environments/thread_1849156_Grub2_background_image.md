---
title: "Grub2 background image"
date: 2011-09-23
forum: Desktop Environments
---

### Post by 02darkRS on 2011-09-23
In grub2 Drop in background thread it states:
 "**Gotchas**
[LIST]
[*]Don't forget to run  "sudo update-grub"
[*]If you have multiple distros on your system, remember the change must be made to the controlling Grub
[*]Grub 1.99 RC  or later."
[/LIST]
I have 1.99 RC1 i believe it was. Does this mean I cannot add an image?

---

### Post by Blasphemist on 2011-09-23
No, it doesn't mean that. 1.99 is Grub2, I know it's confusing.

---

### Post by logiblocs on 2011-09-24
Yous should probably do what it says and run ```
sudo update-grub
```

Natty does not have a background image as such, it just has a plain color.

---

### Post by oscarivera9 on 2011-09-24
YES, you can change the background image.  With the new Grub 1.99 things have changed.  The official documentation up on the web is for versions 1.98 and older, so if you're trying to follow those, you'll get nowhere.  I had the same question a while back and I finally figured out how to do it.  Someone else here on the forums has taken the time to post a guide for the new Grub2 (version 1.98 is also Grub2 but I call it the 'old' Grub2).  Here's the link to the guide:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) 

And here's the link for the section within the guide that deals with changing the background image:
[http://ubuntuforums.org/showthread.php?t=1739412](http://ubuntuforums.org/showthread.php?t=1739412)

I hope all of that helps you.  If you have any more questions I'll be more than happy to help.  However, being that I **am** a musician and it **is** the weekend right now, don't be surprised if it takes me a more than couple of days to answer.  But then again, it may not.  :guitar:

Either way, I'll get back to you ASAP if you  need more help.

---

### Post by 02darkRS on 2011-09-24
> **logiblocs said:**
> Yous should probably do what it says and run ```
sudo update-grub
```Natty does not have a background image as such, it just has a plain color.
already done. i also loaded the images as it says. however, i cannot find the specified lines as listed in the tutorial to direct it to load my chosen image. even using the search function shows none of the listed statements to change are there. 


oscarivera9 - thanks for the links & info. I will try this tonight but since I am also a musician :guitar: I am on break from a leader seminar showing how to work in different instruments to various types of music..... thus, i will have to attempt the fix tonight.

edit: i quickly looked at the links & what you provided is what i tried. I cannot copy an image to the specified folder. Also,it says gotcha's are RC or later. I have 1.99 RC1 so what is the gotcha for rc or later editions?

---

### Post by 02darkRS on 2011-09-24
ok, i believe I have found my problem. which, also appears to be my problem with most other ubuntu issues. it needs to be assumed that the beginning user does not know which commands, or even which actions need commands, to be entered into terminal in order to allow tutorials to be followed. for instance, no where in these tutorials does it state you need to give yourself access to drag & drop files. it just assumes you know this? 

so, in terminal: 
<><>
sudo nautilus
enter password
<><>
follow the tutorial for dragging & dropping your file
back in terminal:
<><>
sudo update-grub
exit
<><>

shut down pc & see your boot image! :)

---

### Post by Lisiano on 2011-09-24
Note: Don't do ```
sudo nautilus
``` Use gksudo instead
```
gksudo nautilus
```
sudo - console commands
gksudo - Gnome programs.

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

Also you can just open a terminal and do this, type ```
sudo cp 
``` and put a space after cp, drag&drop a image on the terminal, put another space and type ```
/boot/grub/backgroud.jpg
```
Change .jpg to .png or to whatever your image is.
It'll look something in the lines of```
sudo cp '/path/to/image.jpg' /boot/grub/background.jpg
```
and after that, finaly run ```
sudo update-grub
```

---

### Post by 02darkRS on 2011-09-29
So the drag & drop statement wasn't like a windows explorer drag & drap. I was dragging it from a folder window & dropping it in another folder window. i did not try dropping it in the terminal.

---

