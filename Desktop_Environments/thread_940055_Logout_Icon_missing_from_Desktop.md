---
title: "Logout Icon missing from Desktop"
date: 2008-10-06
forum: Desktop Environments
---

### Post by mikey5555 on 2008-10-06
Hello all, 
I have somehow managed to delete the Logout Icon from the upper task-bar or menu-bar, right-hand side.  Can someone enlighten me as to how to replace that Icon/Link?  The normal user of this machine does not feel comfortable using the command line to shutdown/reboot/logoff the system, and I'm having a serious "brain-fart" trying to remember how to replace that link.

Regards...

mikey5555

---

### Post by roger_1960 on 2008-10-06
Hi

Right click on the menu bar

Click on "add to panel"

Select "Quit" and click the add button

---

### Post by mikey5555 on 2008-10-06
> **roger_1960 said:**
> Hi

Right click on the menu bar

Click on "add to panel"

Select "Quit" and click the add button

Thanks roger_1960...  
Dooohhh!!!  I knew it was simple.   I guess my brain was still at lunch.....

Regards...

mikey5555

---

### Post by aritaro on 2009-01-01
My case is a little bit different, i didn't delete the quit icon, but it popup a error saying gnome error ... (cant remember that message) .. then i notice the quit icon had missing. i search for help, every1 also saying that add panel->quit ... but I totally cant find the "**Quit**" in the Add to Panel window.... how to add back the "Quit"? or where can i find that quit command/application?

---

### Post by Sin@Sin-Sacrifice on 2009-01-01
> **aritaro said:**
> My case is a little bit different, i didn't delete the quit icon, but it popup a error saying gnome error ... (cant remember that message) .. then i notice the quit icon had missing. i search for help, every1 also saying that add panel->quit ... but I totally cant find the "**Quit**" in the Add to Panel window.... how to add back the "Quit"? or where can i find that quit command/application?

You could always just "sudo reboot" (without quotes) from a terminal but that's not really a fix.

---

### Post by aritaro on 2009-01-02
there is a lot way i can use to shut down or reboot, but as you said that is not a fix, i wanna learn troubleshooting and fixing my ubuntu. linux is different from windows, everything is open, there must be a way to fix. 

anyone have any idea how to add back the quit? and i got few question in my mind now...

1. quit is an executed application? 

2. full name is guit? or gtk-quit? i search the key "quit" i found gtk-quit.png and gtk-quit.svg, but dont have executable gtk-quit.

3. i cant find either quit or gtk-quit in synaptic package manager. can i use apt-get to install it?

---

### Post by Ben Page on 2009-01-02
Do you have the quit item in your system menu on the task bar? It would help if you could remember what was that error message.

---

### Post by jbruced on 2009-01-02
Ok, this may be a stupid comment, but there is no "quit" choice, have you tried looking for "shutdown" or "logout" in the add to panel dialog, not "quit"?

---

### Post by aritaro on 2009-01-03
Ben Page.

sorry I new to ubuntu, i tried check the system log but I can't find that error message. I remember it saying something like gnome:...... error... 
I search the word gnome in the system log but nothing appear. :(


jbruced,

I have **Log Out** and and **Shut Down** in the System menu and the Add to Panel. But I they are different from the quit button at the top right side of the panel. 

The quit icon looks like this [IMG]http://img353.imageshack.us/img353/9557/powerdy8.jpg[/IMG], when i clicked it, it shows a dropdown with the option such as Logout, shot down, reboot ...

---

### Post by jbruced on 2009-01-03
Duh, I feel stupid. Add the "user switcher" to the panel, it has the options you're looking for.

Hope this finally helped.

Bruce

---

### Post by mcduck on 2009-01-03
There are two applets for Gnome-panel that allow you to shut down etc.. "Shut Down" is the simple power that allows you to shut down, log out and so on. Then there's the "User Switcher" that adds options for changing users, logging in to guest session and locking the screen. User Switcher's icon will also change to show your status if you use Pidgin for instant messaging.

---

### Post by Ben Page on 2009-01-03
Guys, I think he means this "Quit"

[http://phorolinux.com/images/u810a1/ubuntu810-desktop.jpg](http://phorolinux.com/images/u810a1/ubuntu810-desktop.jpg)

This is the default ubuntu desktop layout, I had that quit button to, but I have removed it, because I have changed my layout. It sayed : User "username" instead of "quit" and it offered logout and shut down dialogs together, not separately, like shut down and logout buttons.
Now i know what you mean, but I don't know how to put it there (I dont need it).

---

### Post by aritaro on 2009-01-03
jbruced,

yup... i had found out that myself too, it is user switcher... lol...

very very sorry because of my stupid... :oops: hahaha... sorry for trouble you guys so much, and thank you for yours patient.. [-o<

---

