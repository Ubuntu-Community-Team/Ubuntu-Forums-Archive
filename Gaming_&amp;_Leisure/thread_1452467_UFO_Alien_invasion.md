---
title: "UFO: Alien invasion"
date: 2010-04-12
forum: Gaming &amp; Leisure
---

### Post by Kir_B on 2010-04-12
I've recently installed a new graphics card \\:D/ and can now enjoy a little gaming, so, first off on my list of must tries, is [UFO:AI]("http://ufoai.sourceforge.net/?page=Home") (or [UFO: Alien invasion]("http://ufoai.sourceforge.net/?page=Home")). It's a squad based strategy game inspired, and quite similar to the xcom series from Micropose which was, arguably, the best strategy game ever made.

Here's an excerpt from the [playdeb.net]("http://www.playdeb.net/updates/Ubuntu/9.10/?category=Strategy&page=1") website:
[UFO: Alien invasion]("http://ufoai.sourceforge.net/?page=Home") is a strategy game featuring turn-based tactical combat against hostile alien forces (human or computer controlled) which are infiltrating earth at this very moment. You are in command of a small special unit which has been founded to face the alien strike force. To be successful in the long run, you must research the alien technology in order to build bigger and better weapons to defeat your foes.:grin:

My search for a Karmic [PPA]("http://www.playdeb.net/updates/Ubuntu/9.10/?category=Strategy&page=1") has now been completed and so I thought that I'd take some time and share. Full credit to the folks at the [playdeb.net]("http://www.playdeb.net/updates/Ubuntu/9.10/?category=Strategy&page=1") website and their sponsors!

If your new to ubuntu and are a little freaked out by the terminal, like I was when I first started out 6 months ago, don't worry, just follow the instructions and **_always_**, **_always_**, double check your entries, _**before**_ you press the ENTER key.

To install the game, we of course have to add the required [PPA]("http://www.playdeb.net/updates/Ubuntu/9.10/?category=Strategy&page=1").

Open a terminal ( > applications >  accessories > terminal) and paste the following, then press the Enter key:```
**gksudo gedit /etc/apt/sources.list**
```If you prefer to use a different editor, by all means, replace the "gedit" with your choice.

Now copy, then paste the following line into the file, at the bottom of the document (it needs to be on it's own line), then save the file and close it:
```
**deb http://archive.getdeb.net/ubuntu karmic-getdeb games**
```Now to get the key. Once again in a terminal, copy, then paste the following line and press the Enter key:[PHP]
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -[/PHP]_**Note**_**:**
I noticed that this [PPA]("http://www.playdeb.net/updates/Ubuntu/9.10/?category=Strategy&page=1") has a tonne of games, so by all means, check them out [here]("http://www.playdeb.net/updates/Ubuntu/all"). Just select a genre and browse away. Remember they're all in your synaptic package manager once you've installed the [PPA]("http://www.playdeb.net/updates/Ubuntu/9.10/?category=Strategy&page=1") and reloaded the package information.

Now open the Synaptic Package Manager ( *> administration **> Synaptic Package Manager*), press the reload button to reload the package information and then simply install the following packages: [COLOR=#33ff33]**_ufoai_,                 _ufoai-data_, _ufoai-data-music_**[/COLOR]. 

Here's a link to the website, complete with a forum: [UFO: Alien invasion]("http://ufoai.sourceforge.net/?page=Home")

There are two other files: _**ufoai-tools**_ is the map-building tool and _**ufoai-server**_ is for the setup of a permanent game server. Both are unnecessary to simply play the game (I installed them anyway). You may find a use for them after trying the game and doing some further research.

**Note:**
Be careful if you're upgrading UFO:AI from an earlier version, as I've read that previous game saves are not compatible with the upgraded version. If anyone can confirm this, please leave a reply to let the rest of us know if this is true, or not (my saves from version 2.1 work so far on version 2.2.1-1, but confirmation is still needed).
 
If anyone has a better, more up to date [PPA]("http://www.playdeb.net/updates/Ubuntu/9.10/?category=Strategy&page=1") source, by all means post it here and I'll edit my first post, with you getting the full credit you deserve, of course.

The graphics card was a necessity, as my rig is a few years old, is a Dell and has a crappy on board graphics chipset, so you may have difficulties if you haven't done likewise. If the game moves slow or overheats your processor (keep an eye on this if you're not sure), you probably need to do the same. 

To add a Hardware monitor to keep an eye on your cpu temperature, right click a panel, select Add to panel, then select Hardware monitor and make it a cpu temp monitor via a right click on the newly added item, then Preferences and then select > Add > Temperature, (you may need to research this a little). Of course, full screen is out of the question while trying to see how your computer is handling things.

I hope you all enjoy, as I'm finally going to.):P

---

### Post by mastablasta on 2010-04-12
Does this install the latest dev version or the latest stable version? because the stable version has gamebeaking bug+it's not possible to finish the game :-(

---

### Post by Kir_B on 2010-04-12
> **mastablasta said:**
> Does this install the latest dev version or the latest stable version? because the stable version has gamebeaking bug+it's not possible to finish the game :-(

Near as I can tell, this is a stable version. It was uploaded on October  27th 2009. It is version 2.2.1.(the stable version) and so far I've yet to find anything about such an important bug (you'd think it would be easy to find). I'll continue to look into this a little further, but I'm pretty sure it's not the one with the serious bug.

Thanks for pointing this out. Kirby

P.S. If anyone has any further info, Please don't hesitate to post.

---

### Post by mastablasta on 2010-04-12
I am asking because my Ubuntu maschine is not fully operational yet. I played this game on WIndows version 2.2.1. After some time (playing for a while and getting into second month) i got a bug where i couldn't recruit anymore. Even if i fired a few people it would still say that not enough crew quarters. too bad cause i had a lot of fun until it lasted.
 
I was later told on forums that even if i didn't get this bug the game in this version has no ending. It could be different in Linux i don't know... In latest dev versions some of these bugs were already fixed. And it became possible to finish the game. unfortunatelly parts of game are still missing (not impplemented).

---

### Post by Kir_B on 2010-04-12
Thanks for the info. Very, very much appreciated.

I'm currently reworking the first post and I hope to finish sometime tonight or early tomorrow. Check back then, as I hope to have a ppa for the most recent version.

Kirby

---

### Post by Kir_B on 2010-04-12
O.K., I've edited my first post to include the most recent version that I could find. The original version was 2.2.1 and this version is 2.2.1-1, which I hope means that it doesn't contain any bugs of the nasty variety.

Good luck and good hunting. Kirby :P

---

### Post by gpwil1 on 2010-11-24
All - just to clarify UFO AI is not complete, and hence there is no way to "complete" the game. I played until the UFO's stopped coming.

Again great game, its just a shame there is no ending for it programmed in yet.

im now looking to find out how to get the nightly builds installed on my ubu-box

---

### Post by TiBaal89 on 2010-11-24
Very cool... I'll have to take a look at it.  I've been looking for something like this after finishing up a healthy addiction to WarZone 2100. :D

---

### Post by mastablasta on 2010-11-25
yeah dont' be dissapointed if it seems too tough. in my game (one of the later versions) aliens were super accurate and my team missed everything. oh the joy.....

---

### Post by Kir_B on 2010-11-25
> **TiBaal89 said:**
> Very cool... I'll have to take a look at it.

I just noticed that getdeb has the latest version (2.3-1~getdeb3) in their [repository]("http://www.getdeb.net/updates/ubuntu/10.04/") for Lucid and maverick. I haven't given it a go yet, but one day I'm going to.

> I've been looking for something like this after finishing up a healthy addiction to WarZone 2100. :D

I hear you! I spent weeks playing the life out of it!!!

Warzone 2100 is definitely one of those games I'll be going back to, again and again. I still haven't finished the game though, as I keep starting from near the beginning, where I've got a save that has 4 commanders already built up and ready to go, or I just play one of the campaigns, if I don't feel like getting too involved in another addiction. It sure is re-playable! 

Did you finish it, and if so, how difficult were the last couple of chapters?

Peace. Kirby :p

---

### Post by TiBaal89 on 2010-11-25
Well, I "finished" it...:lol:

I don't remember the exact mission off the top of my head, but I got through about half the game in an honest fashion before it became obscenely difficult.  At that point I wanted to continue the fun and resorted to maximum cheating. 

I played the rest of the game with a small force of nearly indestructible veteran units.  Also, I used the 'stop mission timer' cheat and infinite resources to build the greatest imaginable base with probably hundreds of defensive towers and completely ridiculous manufacturing capacity.  It was massively fun.  

Honestly, I don't know how any human being could possibly beat the game... if anyone on here has, wow.  The final levels are truly obscene.

---

### Post by Kir_B on 2010-11-26
> **TiBaal89 said:**
> Well, I "finished" it...:lol:

Honestly, I don't know how any human being could possibly beat the game... if anyone on here has, wow.  The final levels are truly obscene.

Did you go to youtube and follow any of the video walkthroughs? I was using that resource to some success on warzone.

Peace. Kirby

---

### Post by Kir_B on 2010-11-26
> **gpwil1 said:**
> All - just to clarify UFO AI is not complete, and  hence there is no way to "complete" the game. I played until the UFO's  stopped coming.
 
 Again great game, its just a shame there is no ending for it programmed in yet.

I was under the understanding that the latest release was supposed to be completable, but that may not have happened.
 
 > im now looking to find out how to get the nightly builds installed on my ubu-box

I  installed the "svn" version of the nightly builds, but whenever I ran  it, everything was fine until I entered a mission, It looked like it was  trying to strangle my processor to death. I never did get around to  figuring out whether I'd done something wrong, as my Ubuntu system got  borked shortly after (still is).

Peace and good luck. Kirby

---

### Post by gpwil1 on 2010-12-21
> **Kir_B said:**
> I was under the understanding that the latest release was supposed to be completable, but that may not have happened.
 
 

I  installed the "svn" version of the nightly builds, but whenever I ran  it, everything was fine until I entered a mission, It looked like it was  trying to strangle my processor to death. I never did get around to  figuring out whether I'd done something wrong, as my Ubuntu system got  borked shortly after (still is).

Peace and good luck. Kirby

Will have to try the SVN version then!

I constantly kill my Ubuntu install! Hence the reason I wrote a script for remastering the ISO with a list of packages and custom settings for the desktop etc.

Combine that with a liveUSB (multiboot ISO), and I can break my install and never have to worry about starting again :)

---

### Post by Kir_B on 2010-12-21
> **gpwil1 said:**
> Will have to try the SVN version then!

I constantly kill my Ubuntu install! Hence the reason I wrote a script for remastering the ISO with a list of packages and custom settings for the desktop etc.

Combine that with a liveUSB (multiboot ISO), and I can break my install and never have to worry about starting again :)

Can you please post your script, I'm very curious to see it.

Peace. Kirby

---

### Post by gpwil1 on 2011-01-10
> **Kir_B said:**
> Can you please post your script, I'm very curious to see it.

It's still a bit rough, not very user friendly. 
I'll post when its completed.


g

---

### Post by Kir_B on 2011-01-10
> **gpwil1 said:**
> It's still a bit rough, not very user friendly. 
I'll post when its completed.


g

Thank you. I look forward to seeing it.

Kirby :biggrin:

---

### Post by gpwil1 on 2011-02-16
ok Kir_B here it is...

This is still **_VERY_** rough, but should give you an idea/start if you are looking to do something similar.

I adapted this from another site which is mentioned in the comments.

I use this in a virtual machine in conjunction with UCK to do the remastering - but im looking to do away with UCK once I have the knowledge.

I have to reiterate that this is a custom script, so dont complain that it doesn't work for you, there are a few times I use specific commands for my system - and i have used the compizsnap script from these forums.

I use the image for virtual machines - hence the VM drivers etc, live usb images and fresh installs.

There are basically 3 main sections to the script; one for remastering from outside the chroot, one from within and one for post remastering.


Enjoy, and let me know if you have any comments suggestions etc
```

#! /bin/bash
################################################################################
# This script is based on a script found on this site:
# Ubuntu TIP: Automating Package Installation &#8211; apt-get to the rescue
# http://tech.shantanugoel.com/2008/03/06/
# ubuntu-tip-automating-package-installation-%E2%80%93-apt-get-to-the-rescue.html
################################################################################

customise () {
	
	echo "Clearing desktop background"
	gconftool-2 --type string --set /desktop/gnome/background/picture_options none 
	gconftool-2 --type string --set /desktop/gnome/background/color_shading_type solid 
	gconftool-2 --type string --set /desktop/gnome/background/primary_color "white"
	gconftool-2 --type bool --set /apps/gnome-session/options/show_splash_screen false


	echo "Changing from default theme"
	gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "Clearlooks"
	gconftool-2 --type string --set /apps/metacity/general/button_layout ":minimize,maximize,close"
	gconftool-2 --type string --set /desktop/gnome/interface/icon_theme "gnome"

	echo "change nautilus to list view and change icon size"
	gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_view "list_view"
	gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_viewer "list_view"

	echo "Changing the default volume (e.g. the Ubuntu default is 6)"
	gconftool-2 --set --type int /apps/gnome_settings_daemon/volume_step 2

	echo "Showing the mounted volumes as icons on the desktop"
	gconftool-2  --set --type boolean /apps/nautilus/desktop/volumes_visible true

	echo "Enabling the check for full distribution update"
	gconftool-2  --set --type boolean /apps/update-manager/check_dist_upgrades true

	echo "Showing hidden files"
	gconftool-2 --type boolean --set /desktop/gnome/file_views/show_hidden_files true

	echo "Making the DVD be played with VLC by default (instead of the Ubuntu default Totem player)"
	gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "gxine dvd:/%m"
	gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "vlc %m"

	echo "Disable screensaver lock"
	gconftool-2 --type boolean --set /apps/gnome-screensaver/lock_enabled false

	echo "Disable autopopup of update manager"
	gconftool-2 --type boolean --set /apps/update-notifier/auto_launch false

	echo "Disable login screen at bootup"
	echo "
	TimedLoginEnable=false
	AutomaticLoginEnable=true
	TimedLogin=gpwil1
	AutomaticLogin=gpwil1
	TimedLoginDelay=30
	DefaultSession=gnome
	" >> /etc/gdm/custom.conf

	echo "Adding shortcuts to top panel"
	/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/gnome-terminal.desktop --panel=top_panel_screen0 --right-stick

	/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/chromium-browser.desktop --panel=top_panel_screen0 --right-stick

	/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/gedit.desktop --panel=top_panel_screen0 --right-stick

	echo "Disabling startup sound"
	gconftool-2 --type bool --set /desktop/gnome/sound/event_sounds false
	
	echo "Moving top panel to bottom"
	gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation bottom

}

extractaccompanyingdebpackages () {
	echo "Downloading and Extracting Accompanying .deb packages"

	#download latest Ubuntu customization kit
	wget http://sourceforge.net/projects/uck/files/uck/2.0.11/uck_2.0.11-0ubuntu1_all.deb 

	#download vbox key
	wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -

	#add virtualbox to sourcelist
	sudo sh -c 'echo "#---added by me---\ndeb http://download.virtualbox.org/virtualbox/debian maverick non-free" >> /etc/apt/sources.list'

	#install vbox
	sudo apt-get install virtualbox-3.2

	sudo dpkg -i -R *

	echo -n "Delete packages after install? (y/n)"
	read choice2
	 
	case $choice2 in
		y) sudo rm *.deb ;;
		*) echo "files not removed" ;;
	esac
	
	#download dependencies for packages with missing dependencies:
	sudo apt-get -f install
}

virtualboxdrivers () {
	echo "Removing OSE drivers (installed by vbox) and reinstalling guest tools"
	sudo apt-get remove virtualbox-3.2
	sudo apt-get autoremove
	sudo apt-get remove dkms
	sudo apt-get install build-essential
	echo "remember to restart and install guest additions"
}

mountvirtualbox () {
	echo "Modprobe virtualbox drivers"
	sudo modprobe vboxdrv
	echo "Mounting default virtualbox shared folders"
	sudo mount -t vboxsf docs /media/docs/ 
	sudo modprobe vboxdrv
}

beginremaster () {
	echo "Beginning remaster"
	sudo rm -rf ~/tmp/*
	/usr/bin/uck-gui
}

copyhostsettings () {
	echo "Removing example content from fresh install desktop"
	sudo rm -rf /usr/share/example-content/
	sudo rm ~/tmp/remaster-root/etc/skel/examples.desktop
	
	echo "Copying Desktop files and settings to remastered desktop"
	sudo mkdir ~/tmp/remaster-root/etc/skel/Desktop/
	sudo cp -R ~/Desktop/Newinstall ~/tmp/remaster-root/etc/skel/Desktop/
	sudo cp -R ~/.gconf ~/tmp/remaster-root/etc/skel
	
}

postinstall () {

	echo "Disable screen dimming"
	gconftool-2  --set --type boolean /apps/gnome-power-manager/backlight/idle_dim_ac false
	gconftool-2  --set --type boolean /apps/gnome-power-manager/backlight/battery_reduce false
	gconftool-2  --set --type boolean /apps/gnome-power-manager/backlight/idle_dim_battery false

	echo "Adding Windows Aero snap style windows"

	sudo mkdir ~/.scripts
	sudo mv ~/Desktop/Newinstall/compizsnap.sh ~/.scripts/compizsnap.sh
	sudo chmod 777 ~/.scripts/compizsnap.sh

	#enable plugins:
	pluginlist2=$(gconftool-2 --get --list-type string /apps/compiz/general/allscreens/options/active_plugins)
	checkcommands=$(echo "$pluginlist2" | grep commands)
	if [[ ! $checkcommands ]]; then
		pluginstoset=$(echo "$pluginlist2" | sed -e "s/]/\,commands]/")
		gconftool-2 --set --type list --list-type string /apps/compiz/general/allscreens/options/active_plugins "$pluginstoset"
	fi

	#assign the commands to the window borders:

	gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command0_edge "Left"
	gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command1_edge "Right"
	gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command2_edge "Top"
	gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command3_edge "Bottom"

	#add the commands to metacity
	gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_1 "~/.scripts/compizsnap.sh left"
	gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_2 "~/.scripts/compizsnap.sh right"
	gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_3 "~/.scripts/compizsnap.sh top"
	gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_4 "~/.scripts/compizsnap.sh bottom"

	echo "Installing network drivers"
	sudo apt-get --reinstall install bcmwl-kernel-source
	sudo modprobe -r b43 ssb wl
	sudo modprobe wl
	
}

installpackages () {
	clear
	echo "--------------------------------------------------------------------------------"
	echo "                 (cleanstart) Script for installing packages (client)           "
	echo "--------------------------------------------------------------------------------"

	#Uncomment multi and universe in sources list and update
	sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
	sudo apt-get update

	# package names to be installed
	PACKAGE_NAME_LIST=""
	PACKAGE_NAME_LIST=$(cat packageslist | grep -v -e "^#" | cut -f1 -d' ')

	echo ""
	echo "Installing packages:" ${PACKAGE_NAME_LIST}
	echo "--------------------------------------------------------------------------------"

	sudo apt-get install -y ${PACKAGE_NAME_LIST}

}

installgames () {
	clear

	# package names to be installed
	GAMES_NAME_LIST=""
	GAMES_NAME_LIST=$(cat gameslist | grep -v -e "^#" | cut -f1 -d' ')

	echo "Installing games:" ${GAMES_NAME_LIST}
	sudo apt-get install -y ${GAMES_NAME_LIST}
}

removepackages () {
	echo "Removing packages"

	# package names to be removed
	PACKAGE_REMOVAL_LIST=""
	PACKAGE_REMOVAL_LIST=$(cat removalpackageslist | grep -v -e "^#" | cut -f1 -d' ')

	echo "Removing packages:" ${PACKAGE_REMOVAL_LIST}
	sudo apt-get remove -y ${PACKAGE_REMOVAL_LIST}
}


finishremaster () {
	sudo mount -t vboxsf docs /media/docs
	sudo cp ~/tmp/remaster-new-files/livecd.iso /media/docs/ubuntu-10.10-desktop-i386-X.iso

}



while : # Loop forever
do
cat << !
 
Install Menu:
-----------------------------------
	b. Begin Remaster
	h. Copy host desktop files/settings to remaster and remove example content
	f. Finish remaster (move remaster image to host)
-----------------------------------
From Chroot environment of Remaster
-----------------------------------
	c. Customise desktop (theme, backgrounds etc)
	d. Download and extract proprietary packages
	i. Install packages
	g. Install games packages
	r. Remove packages
-----------------------------------
Post install/boot
-----------------------------------
	p. Post install script	
	v. Install virtual box guest additions on VM 
	m. Modprobe drivers and mount shared folders
	q. Quit

!
 
echo -n " Your choice? : "
read choice
 
case $choice in
	b) beginremaster ;;
	h) copyhostsettings ;;	
	f) finishremaster ;;
	c) customise ;;
	d) extractaccompanyingdebpackages ;;
	i) installpackages ;;
	g) installgames ;;
	r) removepackages ;;
	p) postinstall ;;	
	v) virtualboxdrivers ;;
	m) mountvirtualbox ;;
	q|n|N|exit|quit) 
		echo ""
		echo "Exiting..."
		echo ""
		exit 0;;
	*) echo "\"$choice\" is not valid "; sleep 2 ;;
esac
done



```

---

### Post by gpwil1 on 2011-03-30
Well I've made many more changes since then.

I may post this in the howto's, since I use it so frequently, but here is the updated script:

```

#!/bin/bash

################################################################################
# This script is a complete rewrite based on a script found on this site:
# Ubuntu TIP: Automating Package Installation – apt-get to the rescue
# http://tech.shantanugoel.com/2008/03/06/
# ubuntu-tip-automating-package-installation-%E2%80%93-apt-get-to-the-rescue.html
################################################################################

################################################################################
# Initialise variables and arrays...
################################################################################
version_number="0.41"
essid=""
network_password=""
nas_name=""
nas_sharename=""
nas_username=""
nas_password=""
username=""

packageslist=$(cat <<"EOF"
# gnome-do / Avant Window Navigator / DockbarX ??
# Check out the following: Handbrake Bluetooth Manager Mobile phone manager apache

#*** Extras
ubuntu-restricted-extras - Commonly used restricted packages
msttcorefonts - MS fonts

#***Preferences
compizconfig-settings-manager - Compiz configuration settings manager
hardinfo - UNIX/Linux hardware information
gsynaptics - for touchpad controls
compiz - pretty window manager
fusion-icon - icons?
emerald
nvidia-settings - Tool of configuring the NVIDIA graphics driver

#***Administration
#firestarter - gtk program for managing and observing your firewall
gparted - GNOME partition editor
#uck - ubuntu customisation kit (ADDED THROUGH PPA) dont need gfxboot-dev with PPA

#***Accessories
acetoneiso - an application to mount different images
mdf2iso - convert mdf files to ISO files
bchunk - convert bin and cue files into iso
unrar-free - to Extract RAR files
unace - extract ACE files
lzma - another archive method

#***Accessories - Text
gedit - another GUI text editor
vim - terminal text editor

#***Graphics
#blender - 3d Graphics application
gimp - The GNU Image Manipulation Program
inkscape - vector graphics drawing application

##***Internet
chromium-browser
links - text based browser
deluge - Torrent client

#***Office
#openoffice.org

#***Programming
#meld - graphical tool to diff and merge files
#regexxer - A visual search and replace tool
#monodevelop - nice IDE for common languages
#g++

#***Sound & Video - Player
vlc - multimedia player and streamer

#***Sound & Video - DVD
#audacity - A fast, cross-platform audio editor
#avidemux - a free video editor - gtk version
#dvdrip - perl front end for transcode
#padevchooser - PulseAudio Device Chooser
#pavumeter - PulseAudio Volume Meter

#***System Tools
#sysinfo - UNIX/Linux system information (MONO)
nautilus-gksu - privilege granting extension for nautilus using gksu - Open as Administrator
nautilus-open-terminal - nautilus plugin for opening terminals in arbitrary local paths
gconf-editor - An editor for the GConf configuration system
samba - a LanManager-like file and printer server for Unix
openssh-server - SSH server
openssh-client - SSH client
nmap - port scanning util
traceroute - server return info
wine - windows under linux
aptitude - package installer
dkms
googlecl - google docs command line interface
conky - system monitoring
glipper - clipboard manager, stops anoying loss of copy paste items, remember to add to taskbar to enable
xdotool - required for windows aero style snapping
wmctrl - required for windows aero style snapping
dnotify - dnotify -r *directory name* monitors files in directory

#***Aesthetics
gvfs-bin
EOF
)

removalpackageslist=$(cat <<"EOF"
firefox
gnomine
tomboy
totem
gwibber
quadrapassel
transmission-common 
rhythmbox
gnome-dictionary 
aisleriot
gbrainy 
gnome-sudoku 
#screenlets 
shotwell 
simple-scan 
empathy 
vinagre 
pitivi
openoffice.org-core 
#evolution 
#evolution-common 
#evolution-webcal 
#evolution-indicator 
#evolution-data-server 
#evolution-data-server 
#evolution-data-server-common
EOF
)


gameslist=$(cat <<"EOF"
#ufoai - UFO Alien invasion
playonlinux - Application to allow installation of windows games
uqm - ur quan masters
pokerth - texas holdem poker
dosbox - emulator for old pc games
#zsnes - snes emulator			WHY WONT THIS INSTALL!?!?!?!?!
#scummvm - adventure emulator for lucasarts games
#neverball - mouse ball game
#frozen-bubble - like puzzle bobble
#pingus - lemmings clone
#xmoto - like old pc game moto
#glest
#foobillard - virtual pool
#mupen64plus - nintendo 64 emulator
#gfceu - snes emulator
#xmame-common 
#snes9x-x

#gbrainy - brain training
#scorched3d - scortched earth in 3d
#chromium-bsu - too hard!
#yofrankie - doesnt run on liveUSB/CD
EOF
)

conkyrc=$(cat <<"EOF"
# UBUNTU-CONKY
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 2.0
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3

# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color black
 
own_window_colour ff0000
own_window_transparent yes
 
# Text alignment, other possible values are commented
alignment top_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 10
 
#stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color #fff000}SYSTEM ${hr 2}$color
$sysname $kernel on $machine $alignr $nodename 
${font}Update: $alignr ${execi 600 aptitude search "~U" | wc -l | tail} package(s)
${font}Uptime: $alignr ${uptime} 
${font}Time: $alignr $time
${font}Processes: $alignr $processes ($running_processes active)

${color #fff000}CPU / MEMORY / DISK ${hr 2}$color
${color #fff000}CPU: ${color }${freq}Hz ${acpitemp}°c ${cpu cpu1}%  $alignr ${cpugraph cpu1 8,60}
${color #fff000}RAM:  ${color } $mem/$memmax $memperc% $alignr ${memgraph 8,60}
${color #fff000}SWAP: ${color }$swapperc% $swap/$swapmax $alignr ${swapbar 8,60}
${color #fff000}ROOT:    ${color }${fs_free /}/${fs_size /}$alignr ${fs_bar 8,60 /}
${color #fff000}HOME:  ${color }${fs_free /home}/${fs_size /home}$alignr ${fs_bar 8,60 /home}

${color #fff000}NAME $alignr PID    CPU  MEM${color}
${top name 1} $alignr ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4} ${top mem 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5} ${top mem 5}

${color #fff000}NETWORK ${hr 2}$color
Public: ${alignr}${execi 900 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
Top net process: ${alignr}${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${if_existing /sys/class/net/eth0/operstate up}IP (eth0):$alignr${addr eth0}
Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 8,60 } ${alignr}${upspeedgraph eth0 8,60 }
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${endif}${if_existing /sys/class/net/eth1/operstate up}IP (eth1):$alignr${addr eth1}
Down: ${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 8,60} ${alignr}${upspeedgraph eth1 8,60}
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
${endif}${if_existing /sys/class/net/eth2/operstate up}IP (eth2):$alignr${addr eth2}
Down: ${downspeed eth2} k/s ${alignr}Up: ${upspeed eth2} k/s
${downspeedgraph eth2 8,60 } ${alignr}${upspeedgraph eth2 8,60 }
Total: ${totaldown eth2} ${alignr}Total: ${totalup eth2}
${endif}${if_existing /sys/class/net/wlan0/operstate up}IP (wlan0):$alignr${addr wlan0}
Down: ${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 8,60 } ${alignr}${upspeedgraph wlan0 8,60 }
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
${endif}${if_existing /sys/class/net/ppp0/operstate}IP (ppp0):$alignr${addr ppp0}
Down: ${downspeed ppp0} k/s ${alignr}Up: ${upspeed ppp0} k/s
${downspeedgraph ppp0 8,60 } ${alignr}${upspeedgraph ppp0 8,60 }
Total: ${totaldown ppp0} ${alignr}Total: ${totalup ppp0}
${endif}

${color #fff000}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
EOF
)


backgroundimage=$(cat <<"EOF"
<?xml version="1.0" standalone="no"?>

<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN"
"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

<svg width="1000" height="1000" version="1.1"
xmlns="http://www.w3.org/2000/svg">

<text x="700" y="700">versionnumber</text>

<path style="fill:#000000" transform="translate(-80,-500) scale(2)"
       d="m 270,585 c -3.5,-1.6 -8,-3.5 -10.5,-4 -4.6,-1.2 -18.2,-8.4 -23.7,-12.6 -2,-1.5 -6.5,-4.9 -10,-7.6 -3.4,-2.5 -7.7,-5.4 -9.3,-6.1 -1.6,-0.7 -3.8,-2.2 -4.8,-3.3 -1,-1.1 -3.7,-2.9 -5.9,-4 -6.3,-3 -13.8,-11.1 -19.4,-20.8 -4,-7 -5.4,-10.7 -7.1,-18.7 -1.1,-5.4 -2.4,-12.1 -3,-14.7 -1.9,-3.2 -2.3,-10 -2.3,-15.7 0.5,-25.9 5.3,-43.7 13.1,-66.4 7.9,-21.1 21,-30 31.2,-46.6 C 222.5,357.3 243,346.8 251.2,342.8 c 3.7,-1.8 7.9,-2.7 15.3,-3.4 5.5,-0.5 13,-1.4 16.5,-1.9 4.1,-0.6 8.3,-0.6 12.3,0 3.2,0.5 8,0.9 10.6,0.9 23,3.2 39.0,11.7 56.6,28.2 9.8,9.1 16.1,12.5 26.8,28.3 14.5,18.7 18.9,43.7 18.8,59.2 -0.3,18.8 3.7,27.1 -0.2,40.4 -2.6,16.6 -9.2,25.9 -18.7,39.1 -1.3,1.8 -4.1,4.4 -6.2,5.8 -2,1.4 -5.3,4 -7.3,5.7 -1.9,1.7 -4.9,4.2 -6.7,5.4 -1.7,1.2 -5.2,5 -7.7,8.5 -4.2,5.8 -4.9,6.4 -9.7,7.4 -3.1,0.6 -7.3,2.6 -10.7,5 -9.8,7 -17.4,10 -29,11.6 -5.7,0.7 -12.7,2 -15.5,2.8 -2.7,0.8 -8.6,1.4 -13,1.4 -6.5,0 -8.9,-0.5 -14.2,-2.9 z m 19.2,-7.5 c 2.6,-1 1.8,-2.5 -4.5,-9.3 -3.3,-3.5 -7.2,-8.3 -8.7,-10.6 -3.2,-5.1 -10.2,-10.4 -20.4,-15.7 -4.3,-2.2 -9.7,-5 -12,-6.2 -2.2,-1.2 -7,-3.4 -10.6,-4.9 -7,-3 -11,-5.7 -21,-14.4 -3.5,-3.1 -7.5,-6.2 -8.8,-6.8 -1.2,-0.6 -3.6,-2.6 -5.1,-4.4 -2.5,-2.8 -2.9,-2.9 -3.5,-1.3 -0.4,1.2 0,2.6 1.7,4.5 3.6,4 5.8,7.8 7.4,13.2 1.3,4.6 4.9,9.6 13.3,18.4 2,2.2 4.1,5 4.5,6.2 0.3,1.2 2.8,3.3 5.3,4.7 4.8,2.6 12.6,7.7 17.4,11.4 4.1,3.1 21.9,10.9 31.1,13.5 8.5,2.3 11.3,2.7 13.9,1.7 z m 21.3,-4.8 c 2.2,-1.2 6.8,-3.3 10.3,-4.5 19.7,-7.1 45.2,-24.8 52.6,-36.6 1,-1.6 3.8,-5.5 6.2,-8.7 6.3,-8.4 11.3,-20.7 8.4,-20.7 -0.4,0 -4.1,2 -8.2,4.5 -4.7,2.9 -11.4,8.6 -18.4,15.7 -6,6.1 -13.7,13.2 -17,15.8 -6.9,5.3 -17.1,15.2 -19.6,19 -2.1,3.1 -9.3,8.1 -16.2,11.2 -2.7,1.2 -5.9,3.2 -6.9,4.3 l -1.9,2.1 3.4,0 c 1.8,0 5.2,-1 7.4,-2.2 l 0,0 z m 10,-21.6 c 6,-5.5 14.9,-13.4 19.9,-17.6 4.9,-4.1 12.1,-10.5 16,-14.2 3.8,-3.6 9.5,-8.8 12.6,-11.4 3.2,-2.7 5.9,-5.8 6.3,-7.4 1,-4.1 4.4,-7.2 7.9,-7.2 3.7,0 7,-2.1 9,-6 2,-3.9 1.8,-6.5 -0.5,-9.8 -1.1,-1.5 -2.4,-4.6 -2.9,-6.8 -0.5,-2.2 -2.6,-6.6 -4.8,-9.9 -2.1,-3.2 -5.7,-8.6 -7.9,-12 -3.2,-4.7 -7,-5.1 -9.6,-10.4 -0.3,-1 -6.2,-7.4 -8.3,-8.5 -4.6,-2.3 -13.2,-11.2 -12.4,-12.4 1,-1.6 10.1,4.6 15.6,9.7 3,2.7 8.3,5.5 10.4,6.6 2.1,1.1 6.8,7 10.4,9.8 3.6,2.7 7,5 7.5,5 2.8,0 -1.7,-17.1 -6.5,-24.5 -0.7,-1.1 -2,-4.5 -2.9,-7.5 -1.8,-6.2 -7.5,-15.1 -14.4,-22.4 -2.6,-2.7 -5.4,-6.4 -6.3,-8.1 -1.9,-3.8 -15.9,-14.6 -21.3,-16.3 -2.1,-0.6 -6,-2.5 -8.8,-4 -6.9,-3.8 -19.1,-6.2 -28,-5.4 -3.8,0.3 -13.4,0.7 -21.3,1 -13.1,0.3 -14.6,0.6 -18,2.8 -2,1.3 -5.4,2.7 -7.5,3 -2.3,0.3 -5.1,1.7 -7,3.6 -1.6,1.6 -4.6,3.6 -6.5,4.4 -7.8,3.3 -24.8,25 -29.1,37.2 -1.1,3.2 -2.8,6.7 -3.8,7.8 -4.4,5 -11.5,18.7 -14.2,27.4 -1.6,5.2 -4.1,13.2 -5.5,17.8 -3.4,10.9 -3.7,23.7 -0.7,29.6 1.1,2.1 2.4,4 3,4.2 0.5,0.1 2,-4.5 3.3,-10.4 6.6,-30.7 19.5,-60.4 18.5,-42.4 -0.2,5.4 -4.3,11.4 -2.4,12.8 l 2,1.5 -1.9,12 c -1,3.6 -3.5,9.3 -5.4,12.5 -1.9,3.1 -3.5,6.9 -3.5,8.4 0,5.6 23,27.5 32,30.3 5.9,1.8 28.4,14.6 32.5,18.4 1.6,1.5 5.2,4.3 8,6.1 2.7,1.8 7.9,6.6 11.5,10.6 l 6.4,7.2 4.5,-0.6 c 9.2,-1.1 18,-8.9 24.1,-14.5 z m -79,-49.7 c -4.3,-0.5 -12.3,-3.2 -15.9,-5.3 -3.6,-2.1 -6.1,-6 -7,-11.1 -1.3,-7 5.3,-17.1 16.2,-24.7 4.4,-3.1 6.5,-3.9 10,-3.9 5.7,0 7.5,1 14.6,8.4 9.6,10 10.1,13.3 3.5,25.6 -5.4,10.2 -10.2,12.7 -21.4,11.2 z m 2.9,-13.5 c 1.7,-2.5 2.1,-13.2 0.4,-14.3 -1.8,-1.1 -6.4,1.4 -8.3,4.6 -4.2,7.2 3.1,16.3 7.8,9.6 z m 86.6,-0.2 c -7.9,-2.7 -10.9,-13.6 -7.5,-27.1 1.6,-6.3 3.8,-8.9 10.7,-12.5 7.8,-4.1 14.5,-1.9 22.1,6.9 4.3,5 4.5,5.6 4.5,11.5 0,6.5 -2.2,12.8 -5.6,15.8 -5.3,4.7 -18,7.5 -24.2,5.3 z m 13.2,-14.4 c 2.5,-3.4 3.8,-6 3.8,-8.2 0,-3.4 -0.1,-3.4 -6.7,-0.9 -5.7,2.1 -8,8.2 -4.6,12 2.4,2.7 3.5,2.2 7.6,-3 z M 340.7,459 c 0.9,-0.7 0.9,-1.3 0.1,-2.3 -1.4,-1.7 -2.2,-1.7 -4.9,0.4 -2.7,2.2 -1.8,4.5 1.3,3.5 1.1,-0.3 2.7,-1.1 3.4,-1.6 z m -1.3,-46.6 c -3.6,-2.2 -6.9,-5.8 -6,-6.7 0.7,-0.7 8.4,-3.6 15.4,-5.8 3.9,-1.2 4.4,-1.2 6.2,0.5 1,1 4.4,4.2 4.4,5.3 0,1.7 -3.1,0.5 -7.3,0.5 -5,0 -8.1,1.9 -8.1,5.2 0,2.5 -1.3,2.7 -4.5,0.8 z"/>

</svg>
EOF
)

menulist=$(cat <<"EOF"
default 4
timeout 10
color NORMAL HIGHLIGHT HELPTEXT HEADING
splashimage=/background_boot.xpm.gz
foreground=FFFFFF
background=000000

# Suggested by Erhan Sohail
title Boot First Hard Drive (HDD)
map (hd0) (hd1)
map (hd1) (hd0)
map --hook
chainloader (hd0)+1
rootnoverify (hd0)

title Restart
reboot

title Shutdown
halt

title --- Custom MultiBoot Entries ---
root
title Ubuntu 10.10 (ubuntu vversionnumber)
find --set-root /ubuntu-10.10-desktop-amd64-versionnumber.iso
map /ubuntu-10.10-desktop-amd64-versionnumber.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-10.10-desktop-amd64-versionnumber.iso splash
initrd /casper/initrd.lz"
EOF
)

compizsnap=$(cat <<"EOF"
#!/bin/bash
##GENERAL INFORMATION###########################################################
# This script adds window snapping functionality to compiz using the commands plugin.
# CompizSnap LinuxUndIch.de Edition is a collaborative project from people from ubuntuforums.org
# and additions from LinuxUndIch. The script is licensed under GPL v3.
#
# Help and support:
# http://wwww.ubuntuforums.org/showthread.php?t=1294661
# http://linuxundich.de/de/ubuntu/aero-snap-mit-gnome-und-compiz/
##END OF HEAD###################################################################

# Check if necessary programs are installed
if [ -z $(command -v xdotool) ]; then
	MISSING=xdotool
fi

if [ -z $(command -v wmctrl) ]; then
	MISSING="wmctrl $MISSING"
fi

if [ ! -z "$MISSING" ]; then
	echo
	echo "Error (compizsnap):"
	echo "You need to install the following program(s): $MISSING"
	if [ -r /etc/debian_version ]
	then
		echo "In order to do so, run:"
		echo "sudo apt-get install $MISSING"
	fi
	exit 1
fi
## End of check, script starts here

# Uncomment to get more output for troubleshooting
# Alternatively, run Compiz like this in the command line: 'VERBOSE=yes compiz'
#VERBOSE=yes

MOUSE=$(xinput -list | grep -i 'mouse' | grep -v 'Macintosh mouse button emulation' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:')
TOUCHPAD=$(xinput -list | grep -i 'touchpad' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:')
TRACKPAD=$(xinput -list | grep -i 'trackpoint' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:')

WIDTH=$(xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x')
HEIGHT=$(xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d p)
HALF=$(($WIDTH/2-10))
TEMPWIDTH=$(($WIDTH-10))


left() {
#would be nicer, but --shell option works only under maverick
#eval $(xdotool getmouselocation --shell)
X=$(xdotool getmouselocation | awk '{print $1}' | cut -d : -f 2)
if [ $X -le 10 ]
then
	wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-10
fi
}  

right() {
#eval $(xdotool getmouselocation --shell)
X=$(xdotool getmouselocation | awk '{print $1}' | cut -d : -f 2)
if [ $(($WIDTH-$X)) -le 10 ]
then
	wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$(($HALF+18)),-10
fi
}

max() {
#eval $(xdotool getmouselocation --shell)
Y=$(xdotool getmouselocation | awk '{print $2}' | cut -d : -f 2)
if [ $(($HEIGHT-$Y)) -ge $(($HEIGHT-$10)) ]
then
	wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
fi
}

if [ ! "$VERBOSE" = "yes" ]
then
	QUIET=-q
fi

DEVICE=touchpad

loop() {
while (xinput --query-state $DEVICE_ID | grep $QUIET down)
do
	if [ "$VERBOSE" = "yes" ]
	then
		echo "$DEVICE button pressed"
	else
		:
	fi
done
}

# ----- Don't edit below this line unless you know what you are doing.
if [ -n "$MOUSE" ]
then
	if xinput --query-state $MOUSE | grep $QUIET down
	then
		DEVICE_ID=$MOUSE
		DEVICE=mouse
		loop
		$1 $MOUSE
	fi
fi

if [ -n "$TOUCHPAD" ]
then
	if xinput --query-state $TOUCHPAD | grep $QUIET down
	then
		DEVICE_ID=$TOUCHPAD
		loop
		$1 $TOUCHPAD
	fi
fi

if [ -n "$TRACKPAD" ]
then
	if xinput --query-state $TRACKPAD | grep $QUIET down
	then
		DEVICE_ID=$TRACKPAD
		loop
		$1 $TRACKPAD
	fi
fi

EOF
)
################################################################################
# End of Initialisation of variables
################################################################################

customise () {
	echo "--Creating conky script"
	echo "${conkyrc}" > ~/.conkyrc

	echo "--Creating background image"
	backgroundimage=${backgroundimage//'versionnumber'/"$version_number"}
	echo "${backgroundimage}" > /usr/share/backgrounds/background.svg
	
	echo "--Adding Windows Aero snap style windows"
	mkdir ~/.scripts	
	echo "${compizsnap}" > ~/.scripts/compizsnap.sh

	echo "--Adding network settings"
	sudo awk -v var="blah" '{ gsub(/dns mdns4/,"wins dns mdns4",$0); print }' /etc/nsswitch.conf > temp.conf
	sudo mv temp.conf /etc/nsswitch.conf

	echo "--Changing from default theme"
	gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "Clearlooks"
	gconftool-2 --type=string -s /apps/metacity/general/theme "Clearlooks"
	gconftool-2 --type string --set /apps/metacity/general/button_layout ":minimize,maximize,close"
	gconftool-2 --type string --set /desktop/gnome/interface/icon_theme "ubuntu"

	echo "--Clearing desktop background"
	gconftool-2 --type string --set /desktop/gnome/background/picture_options none 
	gconftool-2 --type string --set /desktop/gnome/background/color_shading_type "vertical-gradient"
	gconftool-2 --type string --set /desktop/gnome/background/primary_color "#a987b673b90c"
	gconftool-2 --type string --set /desktop/gnome/background/secondary_color "white"
	gconftool-2 --type bool --set /apps/gnome-session/options/show_splash_screen false

	echo "--Changing default background image"
	gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/usr/share/backgrounds/background.svg"
	gconftool-2 --type string --set /apps/gnome-session/options/splash_image "/usr/share/backgrounds/background.svg"
	gconftool-2 --type string --set /desktop/gnome/background/picture_options "scaled"
	
	echo "--Change nautilus to list view and change icon size"
	gconftool-2 --type string --set /apps/nautilus/preferences/default_folder_viewer "list_view"
	#gconftool-2 --type string --set /apps/nautilus/icon_view/default_zoom_level "smaller"
	gconftool-2 --type string --set /apps/nautilus/preferences/side_pane_view "NautilusTreeSidebar"

	echo "--Changing the default volume (e.g. the Ubuntu default is 6)"
	gconftool-2 --set --type int /apps/gnome_settings_daemon/volume_step 2

	echo "--Showing the mounted volumes as icons on the desktop"
	gconftool-2  --set --type boolean /apps/nautilus/desktop/volumes_visible true

	echo "--Enabling the check for full distribution update"
	gconftool-2  --set --type boolean /apps/update-manager/check_dist_upgrades true

	echo "--Disable screen dimming"
	gconftool-2  --set --type boolean /apps/gnome-power-manager/backlight/idle_dim_ac false
	gconftool-2  --set --type boolean /apps/gnome-power-manager/backlight/battery_reduce false
	gconftool-2  --set --type boolean /apps/gnome-power-manager/backlight/idle_dim_battery false
	gconftool-2  --set --type boolean /apps/gnome-power-manager/backlight/brightness_dim_battery "100"

	echo "--Disable Power settings"
	gconftool-2  --set --type boolean /apps/gnome-power-manager/actions/sleep_type_battery nothing
	gconftool-2  --set --type boolean /apps/gnome-power-manager/actions/sleep_type_ac nothing
	gconftool-2  --set --type boolean /apps/gnome-power-manager/backlight/idle_brightness "100"

	echo "--Showing hidden files"
	gconftool-2 --type boolean --set /desktop/gnome/file_views/show_hidden_files true

	echo "--Making the DVD be played with VLC by default (instead of the Ubuntu default Totem player)"
	gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "gxine dvd:/%m"
	gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "vlc %m"

	echo "--Disable ask before logoff"
	gconftool-2 --type boolean --set /apps/gnome-session/options/logout_prompt false

	echo "--Auto power off session when pressing power button"
	gconftool-2 --type string --set /apps/gnome-power-manager/buttons/power "shutdown"

	echo "--Disable screensaver lock"
	gconftool-2 --type boolean --set /apps/gnome-screensaver/lock_enabled false

	echo "--Disable autopopup of update manager"
	gconftool-2 --type boolean --set /apps/update-notifier/auto_launch false

	echo "--Disabling startup sound"
	gconftool-2 --type bool --set /desktop/gnome/sound/event_sounds false
	
	echo "--Enabling compiz plugins"
	pluginlist2=$(gconftool-2 --get --list-type string /apps/compiz/general/allscreens/options/active_plugins)
	checkcommands=$(echo "$pluginlist2" | grep commands)
	if [[ ! $checkcommands ]]; then
		pluginstoset=$(echo "$pluginlist2" | sed -e "s/]/\,commands]/")
		gconftool-2 --set --type list --list-type string /apps/compiz/general/allscreens/options/active_plugins "$pluginstoset"
	fi

	echo "--Assigning the commands to the window borders"
	gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command0_edge "Left"
	gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command1_edge "Right"
	gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command2_edge "Top"
	gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command3_edge "Bottom"

	echo "--Adding commands to metacity"
	gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_1 "~/.scripts/compizsnap.sh left"
	gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_2 "~/.scripts/compizsnap.sh right"
	gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_3 "~/.scripts/compizsnap.sh top"
	gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_4 "~/.scripts/compizsnap.sh bottom"
	
	gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command4_key "<Super>e"
	gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_5 "nautilus" #Windows Logo+E (Open My Computer)

	gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command5_key "<Super>f"
	gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_6 "gnome-search-tool" #Windows Logo+F (Search for a file or a folder)

	gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command6_key "<Ctrl><Shift><Esc>"
	gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_7 "gnome-system-monitor" #CTRL+SHIFT+ESC (Open Task Manager)

	gconftool-2 --set --type string /apps/metacity/global_keybindings/panel_main_menu "<Super>" #Windows Logo (Display or hide the Start menu)

	gconftool-2 --set --type string /apps/metacity/global_keybindings/panel_run_dialog "<Super>r" #Windows Logo+R (Open the Run dialog box)

	gconftool-2 --set --type string /apps/metacity/window_keybindings/toggle_maximised "<Alt>m" #Alt+m (Maximise window)

	gconftool-2 --set --type string /apps/metacity/window_keybindings/toggle_fullscreen "<Alt><Enter>" #ALT+ENTER (View the properties for the selected item) / maximise/restore

	#gconftool-2 --set --type string /apps/metacity/window_keybindings/minimize "<Alt>m" #Alt+M (Minimize window )

	#gconftool-2 --set --type string /apps/metacity/window_keybindings/minimize "" #Windows Logo+SHIFT+M (Restore the minimized windows)

	#single run configs:
	echo "--Adding shortcuts to top panel"
	#/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/gnome-terminal.desktop --panel=top_panel_screen0 --right-stick

	#/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/chromium-browser.desktop --panel=top_panel_screen0 --right-stick

	#/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/gedit.desktop --panel=top_panel_screen0 --right-stick

	echo "--Moving top panel to bottom"
	#gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation bottom

	#end single run configs

}

extractaccompanyingdebpackages () {
	clear
	echo "--Adding PPA's..."
	#download latest Win2-7 pak (windows 7 theme)
	#wget http://lite.fr.nf./r-z 
	#mv r-z win7.lzma

	echo "--Adding virtualbox to source list"
	echo "--(Virtualbox OSE doesnt have USB support)"
	wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
	sudo sh -c 'echo "#---added by me---\ndeb http://download.virtualbox.org/virtualbox/debian maverick contrib" >> /etc/apt/sources.list'

	echo "--Adding wine PPA to source list"
	sudo add-apt-repository ppa:ubuntu-wine/ppa
		
	echo "--Adding uck PPA to source list"
	sudo add-apt-repository ppa:uck-team/uck-stable
	echo "--Updating source list"
	sudo apt-get update
	echo "--installing PPA's"
	sudo apt-get install -y uck wine virtualbox-4.0

	echo "--Extracting accompanying deb packages"
	sudo dpkg -i -R *
	echo -n "--Cleaning up (Removing  packages after install)"
	sudo rm *.deb
	echo -n "--download dependencies for packages with missing dependencies"
	sudo apt-get -f install
}

virtualboxdrivers () {
	clear
	echo "--Removing OSE drivers (installed by vbox) and reinstalling guest tools"
	sudo apt-get remove -y virtualbox-4.0
	sudo apt-get autoremove
	sudo apt-get remove dkms
	sudo apt-get install -y build-essential
	echo "Remember to restart and install guest additions"
}

mountvirtualbox () {
	clear
	echo "--Modprobe virtualbox drivers"
	sudo modprobe vboxdrv
	echo "--Create mount point folder"
	sudo mkdir /media/docs
	echo "--Mounting default virtualbox shared folders"
	sudo mount -t vboxsf -o uid=1000,gid=1000 docs /media/docs
}

beginremaster () {
	clear
	echo "--Beginning remaster"
	sudo rm -rf ~/tmp/*
	/usr/bin/uck-gui
	#note that /usr/bin/uck has many options to start at different stages!

}

copyhostsettings () {
	clear
	echo "--Removing example content from host machine"
	sudo rm -rf /usr/share/example-content/
	echo "--Removing example content from remaster machine"
	sudo rm ~/tmp/remaster-root/etc/skel/examples.desktop
	
	echo "--Copying background image"
	sudo cp /usr/share/backgrounds/background.svg ~/tmp/remaster-root/usr/share/backgrounds/background.svg
	
	echo "--Copying desktop shortcuts"
	sudo cp ~/Desktop/*.desktop ~/tmp/remaster-root/etc/skel/Desktop

	echo "--Copying Desktop files and settings to remastered desktop"
	sudo mkdir -p ~/tmp/remaster-root/etc/skel/Desktop/newinstall
	sudo cp -R ~/Desktop/newinstall ~/tmp/remaster-root/etc/skel/Desktop
		
	echo "--Copying compiz snap script"
	sudo mkdir ~/tmp/remaster-root/etc/skel/.scripts
	sudo cp ~/.scripts/compizsnap.sh ~/tmp/remaster-root/etc/skel/.scripts
	
	echo "--Copying conky script"
	sudo cp ~/.conkyrc ~/tmp/remaster-root/etc/skel/

	echo "--Copying game files to correct install path"
	#do this by finding what .iso files are accompanying the newinstall folder
	sudo cp -R ~/Desktop/newinstall/games/quake ~/tmp/remaster-root/usr/share/games/
	sudo cp -R ~/Desktop/newinstall/games/quake2 ~/tmp/remaster-root/usr/share/games/
	sudo cp -R ~/Desktop/newinstall/games/yamagi-quake2 ~/tmp/remaster-root/usr/lib/games/
	sudo cp ~/Desktop/newinstall/games/quake/quake.desktop ~/tmp/remaster-root/usr/share/applications/
	sudo cp ~/Desktop/newinstall/games/quake2/quake2.desktop ~/tmp/remaster-root/usr/share/applications/
	sudo cp ~/Desktop/newinstall/games/quake2/quake2_dedicated.desktop ~/tmp/remaster-root/usr/share/applications/
	echo "--Removing game files from desktop of remaster"
	sudo rm -rf ~/tmp/remaster-root/etc/skel/Desktop/newinstall/games

	echo "--Copying user settings"
	sudo cp -R ~/.gconf ~/tmp/remaster-root/etc/skel
	
}

postinstall () {
	clear

#	echo "--Disable login screen at bootup"
#	this causes the live cd to stop at the login screen

#	echo "
#	TimedLoginEnable=false
#	AutomaticLoginEnable=true
#	TimedLogin=$username
#	AutomaticLogin=$username
#	TimedLoginDelay=30
#	DefaultSession=gnome
#	" > /etc/gdm/custom.conf

	#echo "Downloading howto and post install script from google docs"
	#cd ~/Desktop/ 
	#google docs get --folder Linux .

	
	echo "--Installing network drivers"
	sudo apt-get --reinstall install bcmwl-kernel-source
	sudo modprobe -r b43 ssb wl
	sudo modprobe wl
	

	echo "Connecting to home network - need to look into how to do this"
	
	echo "--Sharing NAS storage device"
	sudo mkdir /media/$nas_sharename
	sudo mount -t smbfs -o username=$nas_username,password=$nas_password //$nas_name/$nas_sharename /media/$nas_sharename/

}

installpackages () {
	clear
	echo "--Uncomment multi and universe in sources list and update"
	sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
	sudo sh -c 'echo "#---added by me---\ndeb http://archive.getdeb.net/ubuntu maverick-getdeb games" >> /etc/apt/sources.list'
	wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
	sudo apt-get update

	PACKAGE_NAME_LIST=""
	PACKAGE_NAME_LIST=$(echo "${packageslist}"| grep -v -e "^#" | cut -f1 -d' ')

	echo "Installing packages:" ${PACKAGE_NAME_LIST}
	sudo apt-get install -y ${PACKAGE_NAME_LIST}
}

installgames () {
	clear
	GAMES_NAME_LIST=""
	GAMES_NAME_LIST=$(echo "${gameslist}" | grep -v -e "^#" | cut -f1 -d' ')
	
	echo "Installing games:" ${GAMES_NAME_LIST}
	sudo apt-get install -y ${GAMES_NAME_LIST}

}

removepackages () {
	clear
	PACKAGE_REMOVAL_LIST=""
	PACKAGE_REMOVAL_LIST=$(echo "${removalpackageslist}" | grep -v -e "^#" | cut -f1 -d' ')
	
	echo "Removing packages:" ${PACKAGE_REMOVAL_LIST}
	sudo apt-get remove -y ${PACKAGE_REMOVAL_LIST}	
	sudo apt-get autoremove
}


finishremaster () {
	clear
	mountvirtualbox ;
	echo "--Moving remastered image to desktop version:" $version_number
	sudo mv ~/tmp/remaster-new-files/livecd.iso ~/Desktop/ubuntu-10.10-desktop-amd64-$version_number.iso
	sudo chmod 777 ~/Desktop/*.iso

	echo "--Copying remastered image to My documents folder"
	sudo cp ~/Desktop/ubuntu-10.10-desktop-amd64-$version_number.iso /media/docs/
	

	echo "--Copying menu list to My documents folder"
	menulist=${menulist//'versionnumber'/"$version_number"}
	echo "${menulist}" > ~/Desktop/menu.lst
	sudo cp ~/Desktop/menu.lst /media/docs/

	echo "--Uploading customisation script to google docs"
	google docs upload ~/Desktop/newinstall/installscript.sh --folder Linux

}

while : # Loop forever
do
cat << !
 
Remaster host Menu:						Install order:
------------------------------------------------------------------------------
	c. Customise desktop (theme, backgrounds etc )		1
	h. Copy host settings/files to remaster			3
	b. Begin Remaster					2
	f. Finish remaster (move remaster image to host)	8
-----------------------------------			
From Chroot environment of Remaster
-----------------------------------
	d. Download and extract proprietary packages		4
	i. Install packages					5
	g. Install games packages				6
	r. Remove unwanted packages				7
-----------------------------------
Post install/boot
-----------------------------------
	p. Post install script					9	
	v. Install virtual box guest additions on VM 			
	m. Modprobe drivers and mount shared folders			
	q. Quit

!
 
echo -n " Your choice? : "
read choice
 
case $choice in
	b) beginremaster ;;
	h) copyhostsettings ;;	
	f) finishremaster ;;
	c) customise ;;
	d) extractaccompanyingdebpackages ;;
	i) installpackages ;;
	g) installgames ;;
	r) removepackages ;;
	p) postinstall ;;	
	v) virtualboxdrivers ;;
	m) mountvirtualbox ;;
	q|n|N|exit|quit) 
		echo ""
		echo "Exiting..."
		echo ""
		exit 0;;
	*) echo "\"$choice\" is not valid "; sleep 2 ;;
esac
done

```

---

### Post by Kir_B on 2011-03-31
> **gpwil1 said:**
> Well I've made many more changes since then.

I may post this in the howto's, since I use it so frequently, but here is the updated script:



That is awesome... Although, it may take me some time to sort through it all.

Awesome work! That must have taken a lot of time and effort to do? 

Thanks again.
Kirby ):P

---

