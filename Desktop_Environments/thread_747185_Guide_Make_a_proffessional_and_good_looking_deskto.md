---
title: "Guide: Make a proffessional and good looking desktop in 9 steps."
date: 2008-04-06
forum: Desktop Environments
---

### Post by df9517 on 2008-04-06
Complete guide with pictures: [http://www.kimchikid.com/blog/]("http://www.kimchikid.com/blog/2008/04/06/how-to-make-a-gorgeus-and-cool-desktop-for-your-ubuntu-linux-machine-in-30-minutes/")

A clean install of Ubuntu the desktop looks not very cool at all. But relax, if you follow this guide you will be able to get a ultra cool desktop,

Edit: It will probably work very well also on other linux distributions but due to lack of own experience I won't guarantee that.

We will do following steps:

   1. Change background picture
   2. Change GTK2 theme with window border and controls
   3. Change icon set
   4. Change Fonts
   5. Configure the top bar
   6. Install a cool Mac-like dock (AWN)
   7. Install and get conky up and running to get the geeky text information about RAM usage, processes etc
   8. Change login theme
   9. Change the ugly orange color which is between the login screen and your fully loaded desktop

1 Change background picture

All dark or black background pictures will look really good in relation to this guide. Many free pictures can be found at Gnome-look. If you click[ here]("http://www.gnome-look.org/index.php?xcontentmode=170x171x172x173x174x175x176x177x178x179") it will take you to the Gnome-look,  wallpaper department. Be sure to pick one which has the same size as your desktop resolution.

The new wall paper can be installed by right clicking in the desktop, click "change desktop background", click the tab "background" and click "add" to install your new wallpaper.

Easy!

2 Change GTK2 theme with window border and controls

You would like to find a cool GTK2 theme to make your controls and window border to look nice. The best place for that is gnome-look.com. The theme I have used is called Darker Ice and it is truly a amazing theme, always looking great. Here is the [direct link]("http://www.gnome-look.org/content/show.php/Darker+Ice?content=70611") to download that theme.

You have to unpack the file and inside the folder you will find a file called "DarkerIce.tar.gz", this is the file you should install. Right clicking in the desktop, click "change desktop background", click the tab "Theme" and click "install" and point at the file "DarkerIce.tar.gz". You will then be able to chose Darker ice for both controls and Window border. In the Darkerice catalog you will also find another file to install and that will give you another three window borders to choose from. I use Darker-Ice-Devinorum but all of them are top notch.

3 Change icon set

Now you need to download a slick icon set and the best place I know for that again is Gnome look. The icon set I use is "Black-White 2 style". A direct link to the icon set is [here]("http://www.gnome-look.org/content/show.php/black-white?content=70299"). To install it is similar as for the GTK2 theme.

Download and install the icon theme by right clicking in the desktop, click "change desktop background", click the tab "Theme" and click "install" and point at the file. Click customize and click the "icon" tab and chose the new icon set. The change on the desktop will come immediately.

4 Change Fonts

Your desktop already looks quite nice but there are more important steps to do. One of the most important but often forgotten design feature in order to get that super feeling is to change to a good looking font. One free group of fonts which I personally have fallen in love with is the Liberation font group and especially Liberation sans. It can be found for download all over the Internet and  one of those places is [here]("http://www.dafont.com/liberation-sans.font").

First you need to unpack the font files and put them in a folder called .fonts and place them in your home folder. My user name is daniel so I have this folder in /home/daniel/

Once the font files are in the font folder they can be used by Linux.

You will have to chose "see hidden files and folders" in nautilus.

Next step is to change the system fonts. Right clicking in the desktop, click "change desktop background", click the font tab. Play around and make your configuration as you like. Mine look like this. If you know any good pages discussing system fonts, please let me know.

5 Configure the top bar.

Configure the bars as you like. I have deleted the bottom bar and kept the top one. You can change the default start menu to the small icon one. To make it look like mine chose background and "none".

To configure a bar, right click and chose "properties" to increase or decrease the size.
To add things to a bar, right click and chose "add to bar".
To delete things on a bar, right click on that thing a click and chose "remove from panel".
To move things on a bar, right click on that thing a click and chose "move".

6 Install a cool dock (AWN)

There are many cool Apple-like bars around and my favorite is Avant. Go to synaptics, download "awn-manager" and "avant-window-navigator".

To make this dock autostart when Linux start go to system - preferences - sessions. Click add and write a name for the dock and write avant-window-navigator in the command line. Restart Ubuntu and the dock should appear. You can add launchers by using drag and drop from the normal start menu. Configure avant by right clicking in the end of the dock and click preferences.

7 Install and get conky up and running to get the geeky text information about RAM usage, processes etc

This step is the most geeky and perhaps the most difficult. But if you succeed you will have one of the coolest gek tools of them all. If you feel it might be too difficult, skip this one, or do it later when you have more time.

Open up synaptics and install conky. Conky is a program that display information and present it in the way you want it, and it can appear to be presented on the actual desktop. To start the program press alt+F2 and write conky. But the looks is not so good. To reconfigure the program you have to open .conkyrc which is in your home folder. If you want to have a good start you can copy my configuration file into your configuration file. My configuration can be downloaded [here]("http://www.kimchikid.com/blog/wp-content/uploads/2008/04/conkyrc.txt"). However, since your system and my system is not exactly the same your information wont show up perfectly, so you still have to go in and change the file to fit to your computer and system. But the design will be same so you don't need to worry about that part.

You want to autostart your conky program and if you simply autostart conky program it wont work well by some reason. But if it starts with a 30 second delay it works perfectly. Therefor, download [this file]("http://www.kimchikid.com/blog/wp-content/uploads/2008/04/conky_start.sh"), and make autostart to the file (same as autostart AWN in 5 above) in system- preference- sessions. It is a script which will start conky 30 seconds after you start the computer.

8 Change login theme

Go to [gnome-look.com]("http://www.gnome-look.org/index.php?xcontentmode=150") and download a nice dark gdm theme.

Open up a terminal and write "sudo gdmsetup". click on the tab "local" and install your theme.

9 Change the ugly orange color which is between the login screen and your fully loaded desktop

Almost finished now and only one more step in order to get the ultimate desktop. After you logged in from your ultra cool gdm theme the color will briefly switch to a annoying orange color. This can be changed as follows:

Open a terminal and write: sudo gedit /etc/gdm/PreSession/Default

Then change
# Default value
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#dab082"
fi

to (this will make the color black)

# Default value
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#000000"
fi

I got a error message first but second time I logged in everything was alright.

I hope you enjoyed it and that the result will impress your family and friends.

---

### Post by Elzar on 2008-06-05
Thanks! Some good tips! :)

---

### Post by Redrazor39 on 2008-06-07
nice! I don't really like the all dark but I used a lighter gtk theme with the other tips and achieved something beautiful!

---

