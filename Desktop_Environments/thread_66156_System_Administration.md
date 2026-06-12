---
title: "System Administration"
date: 2005-09-16
forum: Desktop Environments
---

### Post by AluX on 2005-09-16
hi,

i just installed Kubuntu 5.04 and i want to change some network settings. So i read the ubuntuguide and it says go to "System -> Administration". But i can't find the "Administration".
Next to the K Menu Button there is a Button System, but it only shows me the options Home Folder,Storage Media,Remote Places,Settings and Trash. But no "Administration"

Plz help

Thx

Alux

---

### Post by dave9191 on 2005-09-16
The ubuntu guide is wrtten with ubuntu in mind rather then kubuntu. The menu System > Administration is a menu in gnome and not in kde (which you are using). I haven't used kde in a while, but try looking under the K menu > Control Center. Or it might be in one of the submeus. 

Maybe someone else can give better directions :)

Dave

---

### Post by bsussman on 2005-09-16
It sounds like you are running KDE not gnome.

soo:

  ```
 Kmenu => system => Control Center is where you want to go (I think)
``` 

you will need to put in your password so that the security subsystem can authenticate you to do sysadm functions.

On my menu there are two System entries - it is the on upper one I find the Control Center.

---

### Post by AluX on 2005-09-16
Ok, i get that. Thx

But when i try to upen the Network option Netwok Settings and type in my root passwort nothing happens...i am sure that it is the right passwort cause su also works with this password

---

### Post by bsussman on 2005-09-16
this is after Control starts and you have typed your own password?

I am not having this behavior - I am challenged only once, enter my user password (not root password) and awaay I go!

Ubuntu is designed to never use a root password - only user password(s), with authorization to use an alternate method (sudo) to gain sysadm privs.

In theory, you should never need to even set a root pswd.

Have you changed this?

---

### Post by AluX on 2005-09-16
After i start the KDE Control Panel and switch to Network Settings it shows me my both network interfaces (both are in status "Disabled Ethernet Network Device").

If i push the button Administrator Mode ist asks me for my root password and after that nothing happens. Alle the settings are still marked grey

---

### Post by bsussman on 2005-09-16
This would take me a little while to figure out, since I am not seeing the same problem.  I hope somebody else is  reading this and has an idea.](*,)

---

### Post by melalcoolique on 2005-09-16
[QUOTE=AluX]After i start the KDE Control Panel and switch to Network Settings it shows me my both network interfaces (both are in status "Disabled Ethernet Network Device").

If i push the button Administrator Mode ist asks me for my root password and after that nothing happens. Alle the settings are still marked grey[/QUOTE]

A well known problem:

[https://bugs.kde.org/show_bug.cgi?id=61850](https://bugs.kde.org/show_bug.cgi?id=61850)

---

### Post by dave9191 on 2005-09-16
Start the control center using 

sudo kcontrol

 on the command line. That will give you access to all admin features. 

Dave

---

### Post by agm642 on 2005-09-16
Or try: K Menu -> System -> Networking

---

### Post by Ahmo on 2005-09-17
i see numerous references, throughout these forums, to the menu path System->Administration-> <option>
but i can't seem to find it. is that a valid menu path for both 4.10 and 5.04? i believe i installed 5.04, but how do i determine what version i have (i've looked lotsa places)?

---

### Post by agm642 on 2005-09-17
The System->Administration menu is only in GNOME, not in KDE. A way to determine your Ubuntu version is to look at the messages its displays during start-up (I think it mentions the version) or look at your /etc/apt/sources.list file (Warty is 4.10, Hoary is 5.04).

---

### Post by Ahmo on 2005-09-17
thanks! i determined i have Warty.

but i still can't find the System->Administration menu. i thought the Applications and Computer menus on the taskbar(?) at the bottom of the screen was Gnome. does Gnome come with Warty? do i have to start it? or install it first?

---

### Post by agm642 on 2005-09-17
GNOME is a complete GUI system that contains all the menus and windows you can see (if someone can explain it better, go on). What does the menu icon at the bottom left of the screen look like? If it's a foot, then you have GNOME, if it's a K, then you have KDE.
P.S.:I've never used Warty myself, so I can't exactly now how it's like... Is it possible that System->Administration only exists in Hoary?

---

### Post by Ahmo on 2005-09-17
i do have a foot at the bottom. you may be right about Warty vs Hoary. i think i will upgrade to the Kubuntu version and see what happens. thanks again!

---

### Post by agm642 on 2005-09-17
You're welcome. Just one question though, is there a special reason why you have Warty?

---

### Post by Ahmo on 2005-09-17
actually, no. i have the Hoary install CD. i guess i forgot i haven't installed it (duh)

---

### Post by bsussman on 2005-09-17
[QUOTE=agm642]GNOME is a complete GUI system that contains all the menus and windows you can see (if someone can explain it better, go on).[/QUOTE]

It also likes a particular set of interface subroutines that differentiate it from KDE. Thus there are very often different versions of the same 'program' such as Kynaptic/Synaptic and gvim/kvim

Many programs will work fine in either window manager, some will look different.

What this means to the average user is, after you choose which you like better, when there is a gnome/kde choice to make you are prudent to go with the one built for you preferred window manager.

---

