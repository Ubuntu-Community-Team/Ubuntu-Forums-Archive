---
title: "help with xfce4 panel and taskbar"
date: 2010-02-20
forum: Desktop Environments
---

### Post by aarons6 on 2010-02-20
i had to switch to xfce4 as kde4 doesn't support dual head monitors without using xinerama and gnome kept crashing and doesn't allow the moving of windows on separate panels and desktops.

im trying to get this taskbar/panel thing working like the kde one is by default.

one thing isnt working, thats the pop-up notifications.. those end up in a black box in the upper left corner of the right monitor.. 

in kde they are by the clock.
the Internet connection icon, can you make it light up on send and receive?


anywhere i can go to jazz up xfce4? im not looking for themes i like the clear one.

the cursor feedback thing seems broken. does it not show when you double click on stuff?? i find myself oping up many windows because i didn't notice it is loading the program.

can you switch thunar with the nautlus or pidgin desktop?

i checked out some postings but they are 2 years old.

---

### Post by Hero of Time on 2010-02-21
Notifications can be changed in Settings > Notifications. If you have xfce4-notify, then you have those settings there, else it might be called differently. At it, you can change the style and location.

When I open a program, my cursor changes to a loading one and on the tasklist an entry appears about loading a program, same like on Gnome. It only shows when you open a file though and it gets opened with the associated program. I don't get any feedback or anything when I open the program directly. However, the program is loaded fairly quickly, in a few seconds I see either it's splash screen or the program itself.

Thunar isn't really responsible for the desktop, that is the task of xfdesktop. I wonder why you want to change it, as it's imo, better that the features you get with Gnome's Nautilus. No idea about KDE's desktop though.

You are free to run any application or panel while you run the Xfce environment. I do advise you to stick with xfdesktop as desktop manager, as that is the one that renders your screen for dual monitor, and xfwm4 as window manager. You're free to change xfwm4 to Compiz for example, but I wouldn't bet on metacity (Gnome) or kwin (KDE).

---

### Post by aarons6 on 2010-02-21
i tried compiz and it slowed my system to a halt.
so the xdesktop is what im liking about xfce4 with the dual monitor on its own system with the ability to drag windows over.. 

in gome you either get 2 seperate desktops or one large one.. what i didnt like was the windows loading half on one screen half on the other.
and kde4 wont even start up without turning on xinerama.

this whole switch was because of a new video card witch i think was a mistake lol.. 
i switched out an old nvidia gforce 6600gt 128 with an ati radeon 3650 1gb.
the ati card is 3x the nvidia card but its not working out to be better.

---

### Post by aarons6 on 2010-02-22
as for the notifications, i had installed notifify-osd.

im trying the xfce one.
installing this wants to remove the ubuntu-desktop
thats just a pseudo program installer it wont actually uninstall ubuntu will it?

that didnt work.. it is the same, upper right monitor, not attached to the taskbar like gnome.

you know what im talking about, like in kde when you move a folder or delete files it shows a icon in the task bar that when you click on it you can see how much time is left?

---

### Post by Hero of Time on 2010-02-22
Afaik, notifications aren't really attached to a panel, they only appear to be because they aren't allowed on it. You can change the settings for notifications in the location I said earlier. At least I can pick the corner where it needs to be. With dual monitor, I will probably be on the right monitor if you set it to a right corner. So having it on the right corner of the left monitor can be tricky. Maybe some Compiz rules can help with that, but as you said, it's slow on your system (weird though, maybe a wrong setting somewhere?).
That it wants to remove Ubuntu-dekstop is normal, as ubuntu-desktop depends on notify-osd and it's removed in favour of xfce4-notifyd.
But even notify-osd should have the option to change it's location.

When you copy, move or delete a file or folder, Thunar shows the progress in a separate window that is not shown on the task list. If you click on the entry for Thunar, that separate window will come up. It's the same behaviour as with Windows Explorer, you don't see the progress on the taskbar either until you close Explorer, but that sometimes stops the action. Haven't tried closing Thunar while copying data, but I rather not risk loosing the work.

I can't really help you with dual monitor, as it's something I don't have.

---

### Post by aarons6 on 2010-02-22
i understand, thanks for your help.. i think the task notifications are a kde4 thing, as gnome and xfce4 both place them on the top right of the monitor.

i dont understand why compiz is so slow, my system is, amd 2000mhz with 1.5gb ram.
before i was running kde4 with all of the effects turned on with a geforce 6600gt.
moved to an ati hd 3650 and compiz, metacity and the xfce4 effects wont work.

kde4 wont boot up without turning on xinerama and wine games crash with some opengl error.

im using the newest ati catalyst drivers.

---

### Post by Hero of Time on 2010-02-22
Maybe the fglrx driver (ATi proprietary one) is the problem. I didn't have much issues on my old laptop, until Jaunty was released. The fglrx driver that was released with Jaunty support also removed my video card and I had to use the open source version, which worked perfectly too with Compiz. Now I have a laptop with an Intel card (GMA4500mhd if I'm correct) and my PC has an nVidia 7800 GTX (with the nVidia driver). Works fine and fast. Maybe you aren't really using the fglrx driver, is it noted in xorg.conf?

---

### Post by aarons6 on 2010-02-22
yeah, i tried the open ones but the computer wouldnt reboot.
when you uninstall the ati ones it deletes the xorg.conf file and when you install the open ones it didnt remake it. i tried for about an hour to get the file working, i tried ati, and radeon and fglrx with the open drivers installed but it kept saying no devices found.. 

i went back to the ati ones. the new ones are new as of this month, i dont know if i can find the last ones i might try those.


two more things, how do i get a 12 hr clock without the seconds? i tried putting custom and then %l:%m and the clock was right, but then it didnt move, it stayed the time it was started.. 
and how do i start up without the cpu being in powersave mode?
everytime i boot the computer its running half speed.. i cant seem to find a way to turn that off?

---

### Post by Hero of Time on 2010-02-23
The CPU governor was mentioned in a different thread on this forum, or somewhere else I happened to stumble upon. You can either change the 'ondemand' init script or rename it to prevent it loading and keep the CPU on performance.

As for the driver problem, the OpenSource ones won't work if you have the fglrx version installed. You don't need an xorg.conf for the open source drivers, Xorg should pick them up automatically. Only when you use proprietary drivers or need to specify a specific one, you need an xorg.conf file.

No idea about the clock though, I use Orage Clock, which comes with the Orage calender. Using '%H:%M:%S' gives me hours, minutes and seconds. It uses strtime syntax.

---

