---
title: "noob help with ut04"
date: 2007-08-19
forum: Gaming &amp; Leisure
---

### Post by payton5 on 2007-08-19
i have had linux for less than a week and am trying to avoid booting into windows.  i need some games to play and i have ut2004 so i would like to install that but linux is not like windows where you just tell it next next next and you play.  i have almost no clue what i am doing.  i need a step by step on what i need to type into the terminal.  i am using 7.04 amd64 with fluxbox.  please help me soon not having any games drives me nuts!

---

### Post by Cresho on 2007-08-20
well, ill bookmark this thing.  I was in the same boat as you were.  I have an mx518 which i managed to get all the buttons working recently and especially in unreal2004.  was very easy.

now for unreal to be installed, all you need to do is copy the sh file from the disk to the desktop and launch it in terminal like sh linux-install.sh  and use mount taskbar utility to remount the new disk inserted.  Do not run the sh from the cd because it will not allow you eject it.  run it from the desktop.

to navigate in the terminal to the desktop, do this

cd /home/yourusername/Desktop

and then execute it like     sh linux-install.sh

after it asks for the second cd, eject it and insert the second cd but you need to mount it and the way i did it was open up the places and click computer and double click on the cd drive.  then it will mount it.  post if you expirience problems.

---

### Post by Zimbaly on 2007-08-20
If you're installing it off Unreal Anthology [http://ubuntuforums.org/showthread.php?t=394706](http://ubuntuforums.org/showthread.php?t=394706)

Although I'm having problems with that.

Also this seems to be a good point of reference = P
[http://www.linux-gamers.net/modules/wiwimod/](http://www.linux-gamers.net/modules/wiwimod/)

Hope these help.

Oh and can't forget this one [http://www.liflg.org/?catid=4](http://www.liflg.org/?catid=4)

One that I saw was recommended. Yet to try since I haven't needed to do any of those yet.

---

### Post by Perfect Storm on 2007-08-20
If you have UT2004 DVD you can run the script file (sh) from the DVD.

Note if you want to install UT2004 globally;

cd <distination>
sudo sh XXXXXX.sh/.run/.bin

that you exit the installer window, don't launch the game....exit it.


You also need: [UT2004 Megapack (latest patch included)](http://www.gamershell.com/download_11865.shtml)

---

### Post by payton5 on 2007-08-21
ok now for the real noob ?     how do i launch the game? i want to the ut2004 folder and did a "ls" and dont know what to do.

---

### Post by payton5 on 2007-08-22
help?

---

### Post by Perfect Storm on 2007-08-23
Which installation method did you follow? And which arch (x86 or am64)?

---

### Post by payton5 on 2007-08-23
am64,  and ran the file off of the dvd

---

### Post by Cresho on 2007-08-24
go into the default installation directory.  mines was /home/yourusername/ut2004

now there is a file called "ut2004"  double click on it and it will run.

you will also need to make some updates.

download.....ut2004-lnxpatch3369-2.tar.bz2 and extract it into the folder overwritting all.  the is also some additional packages like the ut2004-ecebonuspack.tar.zip which might interest you as well.

you will also need to create an icon and if you right click on the application in the taskbar, you can create a launcher/icon.  It's simple.  for my pc, i run compiz fusion.  I created a sh script which disabled fusion and enables it back after i am done with unreal2004.  It was fun setting it all up.

---

### Post by payton5 on 2007-08-24
ok i launched it threw thunar but get this

Exiting due to error
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History: 

Exiting due to error




what do i do?

---

### Post by Cresho on 2007-08-25
what is your graphics card?  what do you get when you type glxgears in the terminal?

you most likely do not have your graphics card set up.  It is simple if you have an nvidia.

---

### Post by payton5 on 2007-08-25
i get 3 gears spinning, i have onboard graphics.  i havenot set up my graphics card but i can see the gears so idk whats going on.

---

### Post by Cresho on 2007-08-25
what graphics cards are you running?

---

### Post by payton5 on 2007-08-26
my onboard heres my mobo...[http://www.newegg.com/Product/Product.aspx?Item=N82E16813186114](http://www.newegg.com/Product/Product.aspx?Item=N82E16813186114)

---

### Post by Cresho on 2007-08-26
your onboard video is an ATI aka AMD 690G, also known by its codename RS690.  So far, ATI and Linux don't go together but do not despair because AMD vows to make ATI drivers available to linux users.  here is a link.  [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) and you may need to look through the forums to help install the updated drivers.  also, after installing the drivers you would need to run "sudo dpkg-reconfigure xserver-xorg" in the terminal without quotes to get the drivers properly running in your system.  There are people here with expirience as well as ati postings on how to do this.  Just search around and you will bounce into stuff like this post.  [http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/](http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/)  but you really need to do a search.

have you configured your system yet?  under system->Administration->Restricted  Drivers Manager does it show an ATI driver?

---

