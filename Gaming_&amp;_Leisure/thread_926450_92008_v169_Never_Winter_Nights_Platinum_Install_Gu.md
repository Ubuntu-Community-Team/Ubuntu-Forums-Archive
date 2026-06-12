---
title: "9/2008 v169 Never Winter Nights Platinum Install Guide"
date: 2008-09-21
forum: Gaming &amp; Leisure
---

### Post by attrezzop on 2008-09-21
I wrote this because of the vastly varying data on the topic, and after about a day of trial and error and trying numerous things I managed to get it to work reliably install after install.

First, this is for Neverwinter Nights Platinum I didn't work with the other versions and I know for everything up until gold there is actually a linux executable installer. Available from [http://icculus.org/~ravage/nwn/]("http://icculus.org/~ravage/nwn/")


First make sure you're added to the **games** group. There's a number of ways to do this, if you don't already know one then this would be a good time to search for it.

# Make a directory you wish to play the game from. This can be done in the Bash shell with mkdir pathname (e.g.** mkdir */var/games/nwn***). You will need to unzip all the files to this directory. You may need to sudo mkdir. If so don't forget to chown and chmod your new directory (e.g. **chown -R root:games */var/games/nwn* && chmod 770 */var/games/nwn***)

Follow the steps in this order.

# Insert Disk Two.


#  Extract disk2.zip to your nwn directory. Like this:

[B]cd /media/cdrom 
unzip disk2.zip -d */var/your/dir/here* [/B]
   

# Insert Disk Three.

# Extract the contents of Data_Linux.zip.

# Extract the contents of disk3.zip.

# Extract the contents of language_data.zip.

# Insert Disk Four.

# Extract the contents of disk4.zip.

# Extract the contents of xp1.zip.

# Extract the contents of xp1_data.zip.

# Insert Disk One.

# Extract the contents of Data_Shared.zip.

# Extract the contents of Language_data.zip. **Note the above Language_data.zip is different from the one on Disk Three and both are needed.**

# Extract the contents of Language_update.zip.

# Install the **unshield** package using the synaptic package manager. 

# Make a temporary directory and Extract the contents of disk1.lhr like this:

[B]mkdir /home/*yourun*/temp
cd /home/*yourun*/temp
unsheild x /media/cdrom/disk1.lhr [/B]

# Now we move a few of the files we need into the proper directories. Starting from where we left off:

[B]mkdir */var/games/nwn*/nwm
mv ./NWN_Platinum/nwm/* */var/games/nwn*/nwm
mv ./NWN_Platinum/modules/* */var/games/nwn*/modules
mv ./NWN_Platinum/ambient/* */var/games/nwn*/ambient[/B]

Finally for the CDS REMOVE ALL FILES IN THE OVERRIDE DIRECTORY! This is very important at this time.

The shell command would look something like this:
**rm -rf */var/games/nwn*/override/***

# Download the Linux Hordes of the Underdark patch [English_linuxclient169_xp2.tar.gz]("http://nwn.bioware.com/support/patch_linuxhotu169.html")

# Extract the contents of the Linux 1.69 HotU patch into your nwn directory.

# Make sure you have permissions over the new files by running **chown -R *urusername*:games *** from inside your nwn directory. (e.g. */var/games/nwn*)

# Some people have problems with this file, some don't this makes a copy under the two names NWN uses so you basically eliminate issues. To fix it run:
**cp ./texturepacks/xp2_gui.erf ./texturepacks/XP2_GUI.erf**

# Edit the nwn shell script. (Again there are many ways to to this I use vim. To open it **vim ./nwn**. Once inside Shift+I to insert (things act as you might expect in a text editor now. When you're done editing press escape key and type :wq (enter) to save and quit.)

You will want to erase ./lib: from the LD_LIBRARY_PATH variable. Apparently, the ones with the game are WAAYYYYY out of date. Also add **cd */var/games/nwn*** or your directory to the top of the file so there are no problems with relative paths.
It should look something like this.

> #!/bin/sh

# This script runs Neverwinter Nights from the current directory
cd */var/games/nwn*

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

./nwmain $@


# Run the fixinstall shell script. This can be done with the Bash shell by typing **./fixinstall** from inside your nwn directory.

# Run the game **./nwn**. It will ask for all three keys in succession once they're entered the game runs. 




Other notes... if you want movies see this post [URL="http://nwn.bioware.com/forums/viewtopic.html?topic=445734&forum=72"]http://nwn.bioware.com/forums/viewtopic.html?topic=445734&forum=72
[/URL]
I didn't try it but it should work if you start from step three.

Also running **./dmclient** to get the Dungeon Master Client is the same as running. **./nwn -dmc** You can make a launcher to that or ***/var/games/nwn*/dmclient** but if you do the later you'll have to edit the third of fourth line of the file to include **cd */var/games/nwn***

---

### Post by DrHackenbush on 2008-09-22
About halfway down your instructions, you have this block...

# Make a temporary directory and Extract the contents of disk1.lhr like this:

mkdir /home/yourun/temp
cd /home/yourun/temp
unsheild x /media/cdrom/disk1.lhr 

...

I *think* that last line should read...

unshield x /media/cdrom/data1.hdr

... that's what I did anyway and NWN works though it is currently VERY choppy in multiplayer.

Nice work with the instructions, by the way.  I found them to be very helpful!

---

