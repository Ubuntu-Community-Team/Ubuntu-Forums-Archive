---
title: "Cups"
date: 2005-04-27
forum: Desktop Environments
---

### Post by petertc on 2005-04-27
I am having problems with cups, to start off it would not see my printer, it did the 
sudo adduser cupsys shadow
this then lets me see the printer and install the drivers. but i can't print to it.
i goto [http://localhost:631](http://localhost:631) 
manage printers and click the green button to start printer but it then comes up with the user and pasword dialog box, no user or password works. 

Using the kde print manager you can see the print que but the printer is not started.
and i can not get into the administrator mode in the KDE control panel 

The printer works fone with cups as i having it runnig on another box using an hd install of knoppix 

any thoughts would be helpful

Regards

---

### Post by petertc on 2005-04-29
I think i have got this sorted now.
I had the same issue a work on mepis 3.3 . 

I found by adding user to sys group. 
then when you are asked for a user name an password enter your user name and password this then works 

I can't take credit for this is i found the answer on the cups forum. but thought i would pass it on

---

### Post by petertc on 2005-04-29
UM ok,

adding user to sys wont work on it own it's the same as adding user to lpadmin. But if you use mepis it will !!
but i changed the cups.conf file in etc and changed Group System from lpadmin to sys and added user to sys.
this now means that you can  now use the administration pages on loaclahost:631 

but i am now getting this error    
Description: 
 Location: usb1
 Printer State: processing, accepting jobs. 
"Unable to open USB device "usb://7260?serial=CN3B43C179I5": No such device" 
Device URI: usb://7260?serial=CN3B43C179I5

any one else go an idea? 
I am going to change the cups conf back and see if ican look at things again

---

### Post by petertc on 2005-04-29
AH 

It's a permissions thing, 

just found this on a post on the ubuntu part of the forum
do sudo chmod o=rw /dev/usb/lp0  
and things work !!

this may be a bug ?

---

### Post by jebe on 2005-05-19
hi,

can you give a short step by step tutorial how to do the stuff ?
i have the same problem...

this would be nice

jebe

---

### Post by petertc on 2005-05-20
[QUOTE=jebe]hi,

can you give a short step by step tutorial how to do the stuff ?
i have the same problem...

this would be nice

jebe[/QUOTE]


Jebe ,

I am at work at the moment but will try and do somthing over the weekend,
I am still having some permissions issues but have added "username" to lp group.
I just have to plug the laptop in and see if it has worked. 

I will  get back on this later 

Peter

---

### Post by petertc on 2005-05-23
[QUOTE=petertc]Jebe ,

I am at work at the moment but will try and do somthing over the weekend,
I am still having some permissions issues but have added "username" to lp group.
I just have to plug the laptop in and see if it has worked. 

I will  get back on this later 

Peter[/QUOTE]
 Sorry did not get time to do the how to over the weekend but did get the permissions thing sorted out so can now bootup and print OK without having to do this sudo chmod o=rw /dev/usb/lp0.

I will get round to posting as soon as i can

---

