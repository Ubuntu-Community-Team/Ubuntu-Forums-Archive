---
title: "Cairo-Dock - Clock and Dustbin not working"
date: 2010-03-16
forum: Desktop Environments
---

### Post by DogoDave on 2010-03-16
Hi I just recently started making my desktop a little more aesthetically pleasing.  I am running Ubuntu 9.10 and I installed Cairo-Dock v2.1.3-7.  I had originally installed it using the Ubuntu Software Centre and I got the problems I describe below, this also doesn't install the newest version so I un-installed cairo-dock and reinstalled using the following code first to clean up
```
su -c "rm -r /usr/share/cairo-dock/"
```

Then to install this 
```
sudo -v
echo "deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu $(lsb_release -sc) main ## Cairo-Dock-PPA" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins

```

Also I put this code in 
```
wget -q http://repository.glx-dock.org/cairo-dock.gpg -O- | sudo apt-key add -
```

After a fresh install however neither the Clock or the DustBin (dustbin v2.2.6 by Fabounet) works, properly regardless of the version I got installed.  Installing via the command line method to get latest version did however get more themes and plugins for other applets on the dock.

When I start up the Cairo-Dock I get an error for each saying that "The theme could not be found; the default theme will be used instead".  

For the Dustbin - There is a empty area where the trash icon goes and it does have functionality, I can drag and drop something to the area and it does move to trash and the total file size is displayed in that place. What I want is an animated icon there like it is supposed to be showing when the trash is empty and when there are items in the trash.

For the Clock - I get an ugly black window with plain red text that doesn't fit into the window properly. 

I don't know how to install the missing theme components into cairo-dock to make these item work as they should.

Note: I have launched Cairo-Dock both without OpenGL and with OpenGL as I have an ATI card I and thought I needed to use the one without OpenGL but neither seemed to make a difference.

---

### Post by fabounet on 2010-03-17
try opening the config of these 2 applets, and select one of the available themes. ;-)

---

### Post by DogoDave on 2010-03-17
Problem Solved, Thank You! 

The problem was that the 1024x768 resolution I am using was not letting me see the drop menu for theme selection on the right-hand side, and I didn't notice the slider to move over at the bottom.

Your solution was exactly right. (nice to know I actually got it installed correctly and it was just me screwing up)

Awesome dock by the way, I like it very much


Dave

---

### Post by bmwebinfo on 2010-03-20
I am having a similar problem with 10.04. However, the themes look to be set correctly.
Additionally, when I use the Theme manager directly from the dock, so:
right-click on dock->Manager Themes->sort by rating-> select something->apply->hard lock for the cairo-dock.

I know that the OS is unstable and I'm using the default version of glx-dock which is one minor number down (6 vs 7).

---

