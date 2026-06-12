---
title: "Problem in Installing MPlayer"
date: 2006-09-21
forum: Desktop Environments
---

### Post by marufsiddiqui on 2006-09-21
Well i first download the mplayer_0.99+1.0pre7try2+cvs20060117-0ubuntu8_i386.deb file. when I click the file it shows errors that dependency not satisfiable-- libggi2. SO download libggi2. when i click libggi2 it says i need libgii0. so i download libgii0. then when i click libgii0 it says i need libgii0-target-x_.

when i click libgii0-target-x it says i need libgii0. SO i found that libgii0-target-x & libgiio are dependent on each other. one cant be installed without other. so what should i do. how can i solve this problem

I hope I have managed to say what I want to say

plz help me its urgent

---

### Post by FyreBrand on 2006-09-21
You can install MPlayer, VLC, and Totem-gstreamer from the "Add/Remove Programs" interface in the Applications menu.  It is the bottom menu item by default.

You can also install them using the advanced interface which is Synaptic, found in the menu: System -> Administration -> Synaptic Package Manager.

There is a forum thread here: [**[COLOR="Sienna"]Ubuntu Customization Guide -- Quick Start[/COLOR]**]("http://www.ubuntuforums.org/showthread.php?t=186792").  It includes a lot of customizations, among them how to install mplayer from the terminal.

Make sure you have the proper repositories enabled.  You can read about that and a sample sources.list here: [**[COLOR="Sienna"]Ubuntu-Demon's Recommended Dapper Sources List[/COLOR]**]("http://www.ubuntuforums.org/showthread.php?t=185758").

I think it is always a wise idea to use Synaptic or aptitude from the terminal to install packages whenever possible as opposed to just installing binaries that you downloaded.  The Add/Remove programs interface is good too.  I think the only two applications I haven't installed this way is Google Earth and PlaneShift.

---

### Post by marufsiddiqui on 2006-09-21
I dont have direct internet connection. so I think i cant use synaptic/add armove program

So my request or i wanna know is there any way for offline install. i mean first i download the necessary packages form internet from a cyber cafe & then install the software on my pc(i.e standalone)

plz plz tell me if i can do the offline install

---

### Post by FyreBrand on 2006-09-21
Yes you can install offline.  You can still use aptitude to do that.  What you need to do when you download the debian packages is to make sure that you also download all the dependencies.  Put the main package and all the dependent packages in the same folder, then use aptitude to install them.  You can also configure your sources.list manually or through Synaptic to look in a certain folder for packages instead of the internet.

So create a folder where you want to copy all the packages you downloaded.  Then add that as a repository to your sources list or by using Synaptic.  The one thing you need to make sure of though, is that you download all the appropriate dependencies before you try to do the install.  Query aptitude to list the dependent packages before you download.

I hope that helps a little more.

---

### Post by marufsiddiqui on 2006-09-21
Well another problem (I'm a beginner, u know)? The problem is just like bellow

I downloaded all necessary (dependent packages) packages. Then i bring them in a pendrive. I plug the pendrive. suppose pendrive's name MARUF01062. & the packages are in a folder named "packages"

so the location of the packages folder is 
/media/MARUF01062/Packages, is it? i am not sure. I start Synaptic, then i click repository-->settings--->Add-->Custom, in Custom I add the following line

deb /media/MARUF01062/Packages

then i close the settings dialog & reload & got message that there's error ie. the command line "deb /media/MARUF01062/Packages" is not right. so what would be the correct command line?

Should i copy the packages into folder in desktop-->tmp. yet i dont understand what would be the correct command line

plz help me with it. Hurry, I cant wait to enjoy multimedia

---

### Post by FyreBrand on 2006-09-21
I wouldn't use a USB drive to setup my repositories.  Just make a permanent place (folder and subfolders for organizations sake) where you copy the packages. You could do it in your home folder if you wanted or you could make a folder in the root folder.  The point is you want them to remain in the same place.

Just so you know MPlayer, Xine, Totem, and others are only going to play open format files by default.  You have to install other codecs and libraries to play proprietary formats like windows media and quicktime movie files.  You are also supposed to have a license to use those formats (that basically means Microsoft wants you to have a Windows OS license).  The procedure to install those codecs/libraries is in the customization link I provided above.

---

### Post by marufsiddiqui on 2006-09-21
Al right, this time first I copied the packages in **/home/ubuntu/Packages**. Then I add the following command line

***deb /home/ubuntu/Packages*** 

& when I reload I got the following error

```

E: Malformed line 15 in source list /etc/apt/sources.list (dist)
E: Unable to lock the list directory

```

so what should i do? why  cant u give me a sample command line that i need to add in the Repositories? plz plz

---

### Post by marufsiddiqui on 2006-09-21
Plz someone help me. i am still in the same condition. I cant solve the problem

Plz someone clearly tell me how can i install software offline/ or what should i write in the sources.list file

plz plz help

---

