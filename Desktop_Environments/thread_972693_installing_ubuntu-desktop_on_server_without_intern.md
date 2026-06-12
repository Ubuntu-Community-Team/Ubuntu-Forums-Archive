---
title: "installing ubuntu-desktop on server without internet alternate cd"
date: 2008-11-06
forum: Desktop Environments
---

### Post by deltaprime on 2008-11-06
I got stuck with this problem last weekend so i figured I'd write a short tutorial for you all who might get stuck with this._ this installs the ubuntu-desktop (gui) for your ubuntu server if you are not connected to the net yet. _all commands that you type into the shell are in **bold**

1) download the alternate cd [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

The alternate cd is: a text based installer."This installation CD is suited for computers unable to run the graphical desktop based installation, either because their computer does not meet the minimum requirements for the live cd or because their computer requires configuration after the installation is complete in order to use the desktop."

2) burn the iso like you burned the ubuntu iso. go to download.com for a bunch of iso software.

3)boot the server up and isert the alternate cd once you logged in.

4) type **sudo apt-cdrom add**
this adds the cd you just inserted to the software sources list. 

5) type **sudo apt-get update**
this will update the software sources and make the cd available. It will stop at somepoint because it cannot retrieve this info from the internet. you will have to quit the update by pressing ctrl+c.

6) type **sudo apt-get install ubuntu-desktop**
this will install the ubuntu gui. it will ask you to confirm a few times and it will go on for quite some time. Time for you to kick back and relax or something like that :)

7) **sudo dpkg-reconfigure xserver-xorg**
this will reconfigure your xserver. you dont have to do this but i found the gui will be more stable.

8)time to start it up! **startx**

9) sudo gui - now be very careful with this as you can seriously damage some stuff. if you want to run every programm in your gui and even the shell in the gui as a super user you can start the gui with **sudo startx**. this will only work this one time though.

10) optional.
as a server admin i find it more useful to use the shell instead of the gui. i do need the desktop environment though to quickly configure some stuff sometimes. so what i do is set the system to boot into tty without x. this allows me to start the gui whenever i want with **startx** or **sudo startx. **here is how you do this:
10.1) type **sudo update-rc.d -f gdm remove**

now youre all ready to go.:popcorn: I hope this works for you all the way it did for me.

good luck!


greetings,

delt4

---

