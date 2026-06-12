---
title: "arg arg OMG make it stop WTF!?!?!?!"
date: 2006-09-02
forum: Desktop Environments
---

### Post by ResponseTrigger on 2006-09-02
hi im very new to linux and just trying to get it installed on my  machine. the problem is when it boots and gets to the gui the video looks all garbled. im guessing its the video drivers. (BTW i have a nvidia 7800gt) so how can i get the video working? im sorry to sound so blunt and aggressive im just really frustrated and dont really know anything about linux ](*,) ](*,) ](*,) ](*,) :confused: :frown:

---

### Post by 0okami on 2006-09-02
did this happen as well when using the ubuntu live cd?

---

### Post by ResponseTrigger on 2006-09-02
the copy i have is the install one i think. i downloaded it (64 bit dapper drake, i have a amd x2 64 bit 4800+) and ripped it to a cd at the college

---

### Post by dguido on 2006-09-02
Just a hunch, do this:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

and then

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by ResponseTrigger on 2006-09-02
mmmmmmmmmmmm nope. i have problems with the 2nd line to add the repositories. when i put in 

gksudo gedit /etc/apt/sources.list

it gives me 

(gksudo:6935):Gtk-WARNING **: cannot open display:

](*,) ](*,)

---

### Post by dguido on 2006-09-02
Try using 'sudo' instead of 'gksudo'.  If that doesn't work use:
sudo nano -w /etc/apt/sources.list
but be warned, that's a command line editor.  Middle click on your mouse is paste, btw.

---

### Post by ResponseTrigger on 2006-09-02
im not sure i can paste as im just trying to install still

---

### Post by ResponseTrigger on 2006-09-02
ok got the repositories and the nvidia drivers. now what do i do? restart computer or

Ctrl + Alt + "Backspace"

or

sudo /etc/init.d/gdm restart

when i try Ctrl + Alt + "Backspace" nothing happens 
when i try sudo /etc/init.d/gdm restart it get:

* Stopping GNOME Display Manager...                                  [ ok ]
* Starting GNOME Display Manager...                                  [fail]


so what do i do now?

---

### Post by microthorne on 2006-09-02
I just had the same issue. Also have a 7800GT.  Do you have a menu at the bottom of your screen when the cd first boots?  (i.e. F1 blah F2 fu F3 bar F4 VGA F5 wee F6 Other)  If so, press F4 and select a resolution your monitor supports.  For example, my LCDs display natively in 1280x1024 x 32bpp.  They are not able to display the standard VGA resolution.

HTH!

---

### Post by ResponseTrigger on 2006-09-02
well everything seems fine except that if i let it start to go to the gui yeah the mouse looks fine but the window manager logo looks all garbled and thats where it just hangs. everything ive done while in console seems fine but i cant restart GNOME without rebooting the computer so im still stuck either way. ive tried the F4 to change the resolution and all that does is make the driver loading screen look better. so really i havent gotten any closer to getting ubuntu installed ](*,) ](*,) some one please save me

---

### Post by ResponseTrigger on 2006-09-11
booted to safe graphics and it works YAAAAAAAAAAAAAAA

---

