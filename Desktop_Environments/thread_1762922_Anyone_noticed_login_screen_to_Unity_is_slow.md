---
title: "Anyone noticed login screen to Unity is slow?"
date: 2011-05-19
forum: Desktop Environments
---

### Post by crashed111 on 2011-05-19
Hi guys

I am not sure if anyone has noticed that once you have logged into Ubuntu over gdm it may take around 15 seconds for the desktop to show even of decent hardware.

I have noticed this on a few desktops however not on any laptops which run fine I am getting the problem with both the 2d and 3d versions? 

If anyone else is noticed it I may investigate further it seems to be around the same speed on an upgraded install and a fresh one. 

Cheers

---

### Post by cafejunkie on 2011-05-20
The same thing happens to me as well, I have also noticed a small regression in boot speed compared to 10.04 and 10.10. 
One thing I did notice however, and Gnome 3/gnome-shell does this as well, is that it waits until everything is loaded and running before displaying the desktop so that once it is finally displayed it's ready to go (as opposed to Gnome 2.x where it would display, but could potentially still be loading some services). 

One thing to keep in mind is that Ubuntu/Debian starts services automatically once you install the packages (where as other distros like Arch and Gentoo do not do this) so it's always a good idea to monitor your start-up services and daemons and keep them to a minimum. I have managed to increase my boot speed and login speed quite a bit by disabling everything that Ubuntu starts up and installs by default.

---

### Post by crashed111 on 2011-05-20
That does make sense now. Is there a way to stop this behaviour and just put it back to what Gnome2 used to be like?

---

### Post by teachop on 2011-05-20
Yes this happens to me as well.  It doesn't do it every time however.  The boot speed seems unchanged and fine, but often it takes 20 seconds from login until Unity gets itself painted.

Startup programs are pared to a minimum, Xubuntu doesn't do it on the same machine.

---

### Post by crashed111 on 2011-05-20
I have now managed to get mine down to around 5 seconds by getting rid of some of the apps that start up with gnome using Gconf. 

I am happy again now :)

---

### Post by teachop on 2011-05-20
> **crashed111 said:**
> I have now managed to get mine down to around 5 seconds by getting rid of some of the apps that start up
It would be good to try to narrow down what was causing your problem specifically, if  you have the chance, and post it here.

---

### Post by crashed111 on 2011-05-25
> **teachop said:**
> It would be good to try to narrow down what was causing your problem specifically, if  you have the chance, and post it here.

The apps I stopped from loading on start up are - 


[LIST]
[*]Bluetooth Manager
[*]Personal File Sharing (This was not configured and just sitting there loading at Gnome start up and probably should be disabled by default)
[*]Power Manager
[*]Ubuntu One
[*]Synaptics Toiuchpad tools
[/LIST]

All of which are pretty useless to a Desktop user. I had to leave the Synaptics and Power Manager up on the laptops but I dont think that was what was causing the problem. Disabling all of these moved my start up from about 20-30 secs to less than 5.

---

### Post by crashed111 on 2011-05-25
I think that the Bluetooth manager was causing some of the wait as it was waiting for a bluetooth device that was not there

---

### Post by 23dornot23d on 2011-05-25
> **crashed111 said:**
> The apps I stopped from loading on start up are - 


[LIST]
[*]Bluetooth Manager
[*]Personal File Sharing (This was not configured and just sitting there loading at Gnome start up and probably should be disabled by default)
[*]Power Manager
[*]Ubuntu One
[*]Synaptics Toiuchpad tools
[/LIST]

All of which are pretty useless to a Desktop user. I had to leave the Synaptics and Power Manager up on the laptops but I dont think that was what was causing the problem. Disabling all of these moved my start up from about 20-30 secs to less than 5.


What method are you using to disable these ..... 

I noticed they have removed the startup applications ..... 

( Which I find ever so useful now  :confused: ).

---

### Post by wojox on 2011-05-25
> **23dornot23d said:**
> What method are you using to disable these ..... 

I noticed they have removed the startup applications ..... 

( Which I find ever so useful now  :confused: ).

It still resides in gnome-control-center. There's also bum (boot up manager).

---

### Post by 23dornot23d on 2011-05-25
> **wojox said:**
> It still resides in gnome-control-center. There's also bum (boot up manager).

Cheers for the quick response .... do you have a screenshot ..... so I can quickly do this ....

I have just upgraded the gnome-control-center ..... but am not used to the new method.

Is the task as easy a before ...... a tick in a box .... ?

searched for it in Unity ..... under gnome .... maybe its somewhere else. ..... (gnome-control-center)

[IMG]http://img829.imageshack.us/img829/425/gnome1.jpg[/IMG]


Startup maybe .... ?

Ok got it now .... ;)

is there anyway to move it into cairo-dock ...... used to be able to  right click on things like this and move them
somewhere more useful for me ...... like into the dock ....

Where is its properties .... so I can find the program to run it too ..... sorry for all the questions ....

just seems like being in a strange town at the moment ...... all the shops are here its just finding them .....

---

### Post by mc4man on 2011-05-25
> is there anyway to move it into cairo-dock
Don't use cairo-dock but the .desktop is sitting in in /usr/share/applications - drag or copy from there.

(after removing all the generally unneeded apps from start up load times should improve quite a lot, the exception would be when switching some logins from previous,(Classic> Unity > Classic, ect.),  some things need to be switched (gconf, dconf settings

---

### Post by 23dornot23d on 2011-05-25
> **mc4man said:**
> Don't use cairo-dock but the .desktop is sitting in in /usr/share/applications - drag or copy from there.

(after removing all the generally unneeded apps from start up load times should improve quite a lot, the exception would be when switching some logins from previous,(Classic> Unity > Classic, ect.),  some things need to be switched (gconf, dconf settings

Cheers will now do this ...... thank you .. drag and drops onto cairo-dock too - nice one .....

---

### Post by mc4man on 2011-05-25
While atm am using unity w. unity launcher, (will have to see what gnome-shell/mutter brings along w. the new nautilus) 
Because .desktops plays a big part in manipulating unity I find it's useful  to add /usr/share/applications and ~/.local/share/applications as bookmarks in nautilus

(any if modding and or creating .desktops some nautilus actions to open them are quite useful, one for root, one for user

---

