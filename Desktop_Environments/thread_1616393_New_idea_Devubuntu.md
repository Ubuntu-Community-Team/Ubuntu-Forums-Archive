---
title: "New idea: Devubuntu"
date: 2010-11-08
forum: Desktop Environments
---

### Post by TheAnachron on 2010-11-08
Hey guys, 

I would like to throw in a new ubuntu package idea: 
Devubuntu. (Or Devuntu) 

Basically in the installation you'll choose what languages you will code with. For example, if you choose PHP, you are allowed to do some more settings, like enable xdebug. (Debugging tool) 

Then after installation, you will automatically have everything installed.

Programs that are useless, like games, etc will just be removed and the whole desktop is development related, so you will have some basic tools, such as links to start/stop/restart the LAMPP server (if working with apache).

What do you think?

---

### Post by 3Miro on 2010-11-08
Instead of developing an entire new Ubuntu branch, you can make a custom script that does exactly that. From a clean install of Ubuntu, you can start the script that will uninstall games and such and then add packages for PHP or whatever.

---

### Post by TheAnachron on 2010-11-09
Hmm maybe.

---

### Post by KdotJ on 2010-11-09
You know, this isn't a bad idea really. I use my laptop for programming mainly, and this would be quite helpful. However, it's kind of a dead idea... Because ubuntu is aimed at the general computer user as an all round purpose operating system, and this must include stuff like music players, CD/DVD tools and games. So if this idea was to happen, you would be looking toward a fork... And we are already up to our eyes balls in *buntu's...

As for the script, a good possible option but it still involves uninstalling a lot, and you would have to look for orphaned packages and unneeded packages/dependancie if you stripped it down a lot. But still a good alternative

---

### Post by TheAnachron on 2010-11-16
Would another fork be so bad? 

I don't see why it should. You would still be allowed to check a flag which says something like "Install media software" which will install media stuff.

I don't need games or internet messengers on my work laptop.

---

### Post by deconstrained on 2010-11-16
Then sudo apt-get remove them. I'm pretty sure that when you run do-release-upgrade it won't re-install the unneeded, cluttery stuff that you uninstalled from Ubuntu previously. 

One fell swoop:
```
# apt-cache search games | grep gnome | cut -d ' ' -f 1 | xargs apt-get remove -y
```

---

### Post by mirearts KING SUNNY on 2010-11-16
download and Run custom scripts for Nautilus..

---

### Post by imagecko on 2010-11-16
I dont like the idea because evey developer and programmer has their own favourite setup of apps and tweaks.

---

### Post by rickyrockrat on 2010-11-16
I agree. Too many Ubuntu distros.  Personally, I would like to see them all go to one, then select your desktop on install.

Use a script. I use all kinds of wacky things, and code I pull out of my own CVS to build apps.

Here's my script which keeps track of what was sucessfully installed. I have a quick menu dohicky called tablaunch that I put at the corners of the screen. This script figures that out and places them accordingly.  

Cheers.
```

# \file ******************************************************************
#\n\b File:        new-computer
#\n\b Author:      RickyRockRat
#\n\b Company:     See Author

#\n\b Date:        12/01/2007 10:03 pm
#\n\b Description: Set up a new computer for development.
# We want tse32 and the scripts for it, bdiff, and tablaunch.

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.

#*/ /************************************************************************
#Change Log: \n
#
PREFIX=/usr/local
TMPDIR=~/.newcomputer
mkdir -p $TMPDIR
echo "new-computer $Revision: 1.14 $"
#************************************************************************
#
#************************************************************************
check_for_prog () {
cd $TMPDIR
if [ ! -e prog ]; then
	cvs co prog
	check_err "CVS co Maybe need a cvs login?"
fi
}
#************************************************************************
#	condition  object desc
# exist /some/dir desc
# nexist
#************************************************************************
checkfor () {
case $1 in
	nexist)
	  if [ ! -e $2 ]; then
	    echo "$2 does not exist"
	    exit 1
	  fi
	   ;;
	zero)
		if [ -z "$2" ]; then
			echo "$3 not set"
			exit 1
		fi
		;;
	sudo)
		TMP=$(sudo -l|grep -c "NOPASSWD: ALL")
		if [ $TMP -lt 1 ]; then
			echo "User $(whoami) is not sudo w/out passwd"
			echo "Add this line to /etc/sudoer (with visudo)"
			echo "$(whoami) ALL=(ALL) NOPASSWD: ALL"
			echo "OR %admin ALL=(ALL) NOPASSWD: ALL"
			exit 1
		fi
		;;
	wine)
	 TMP=$(wine --version)
	 	if [ -z "$TMP" ]; then
			echo "wine is not installed. please install"
			echo "sudo apt-get install wine"
			exit 1
		fi
		
esac
echo "$2 OK"
}
#************************************************************************
#
#************************************************************************
check_err () {
	if [ $? -ne 0 ]; then
		echo "$1 Failed. Abort"
		exit 1
	fi
}
#************************************************************************
#Note: lucon.ttf is the only font file required!!
#************************************************************************
install_tse () {
if [ -e $TMPDIR/install_tse ]; then return 0; fi
cd $TMPDIR
cvs co tse
check_err "CVS co Maybe need a cvs login?"
cd tse
tar -xjf tse-install.tar.bz2 
rm -rf tse32/ui
mv ui tse32
cd tse32
./b
cd ..
sudo mv tse32 $PREFIX
cd $TMPDIR
tar -xjf /pub/tools/graphics/fonts/win2k.font.tar.bz2
check_err "win2k fonts"
cp win2k/* ~/.wine/drive_c/windows/fonts
check_err "win2k font cp"
cd $CURDIR
touch $TMPDIR/install_tse
}
#************************************************************************
#
#************************************************************************
install_tablaunch () {
if [ -e $TMPDIR/install_tablaunch ]; then return 0; fi
check_for_prog
cd prog/tablaunch/src
make
sudo cp tablaunch $PREFIX/bin
check_err "make tablaunch"
mkdir ~/.tablaunch
cd ..
read -p "X resolution of monitor? " XRES
let FIRST=XRES-220
let SECND=FIRST-350
cd configs
for f in $(ls -d *); do
	if [ -f $f ]; then
		if [ "aes" = "$f" ]; then
			let OFFSET=XRES-220
		else
			let OFFSET=XRES-570
		fi
		echo "Setting $offset to $OFFSET  using $XRES"
		sed -i 's!\(.*xoffset \).*$!\1'$OFFSET!'' $f
	fi
done
cd ..
cp -a configs/* ~/.tablaunch
cp 	desktop/* ~/.kde/Autostart/
touch $TMPDIR/install_tablaunch
cd $CURDIR
}
#************************************************************************
#
#************************************************************************
install_scripts () {
if [ -e $TMPDIR/install_scripts ]; then return 0; fi
check_for_prog
chmod 755 prog/scripts/bin/*
cd prog/scripts
FILES=$(ls -d bin/* |grep -v CVS)
chmod 755 $TMPDIR/prog/scripts/bin/*

sudo cp $FILES $PREFIX/bin
check_err "install_scripts"
if [ ! -e ~/.dosboxrc ]; then
	cp dosboxrc ~/.dosboxrc
fi
touch $TMPDIR/install_scripts
cd $CURDIR
}
#************************************************************************
#
#************************************************************************
fix_bashrc () {
if [ -e $TMPDIR/fix_bashrc ]; then return 0; fi
BRC=$HOME/.bashrc
echo "# don't put duplicate lines in the history. See bash(1) for more options" >> $BRC
echo "export HISTCONTROL=ignoredups" >> $BRC
echo "# ... and ignore same sucessive entries." >> $BRC
echo "export HISTCONTROL=ignoreboth" >> $BRC
echo "" >> $BRC
echo "export PATH=$PATH:/sbin:/usr/sbin:/opt/bin" >> $BRC
echo "export CVSROOT=:pserver:dfs@s:/usr/local/cvs" >> $BRC
echo "#fixes mouse going to a corner of the dos screen in xinerama mode">> $BRC
echo "export SDL_MOUSE_RELATIVE=0" >> $BRC
echo "export TSE=$PREFIX/tse32" >> $BRC
echo "PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '" >> $BRC
TMP=$(grep -c bash_completion $BRC)
if [ $TMP -gt 0 ]; then
	echo " Edit $BRC and comment out bash_completion features"
fi
touch $TMPDIR/fix_bashrc
}
#************************************************************************
#
#************************************************************************
install_aptstuff (){
if [ -e $TMPDIR/install_aptstuff ]; then return 0; fi
sudo apt-get update
sudo apt-get remove brltty brltty-x11 
# Note: for a server install, kill the xfce4 stuff.
sudo apt-get install \
 bison g++ flex texinfo cvs subversion xfce4* tofrodos \
 minicom lrzsz libusb-dev libusb++-dev libusb-0.1-4 \
 libusb++-0.1-4c2 gpib-modules-source libgpib-bin \
 libgpib-perl libgpib0 libgpib0-dev python-gpib lha abiword \
 plotutils libplot-dev libplot2c2 libimlib2 libimlib2-dev \
 libpq-dev libpq4 openssh-server openssh-client rapidsvn \
 blackbox bbkeys bbrun bbappconf dosbox pgadmin3 \
 kqemu-common qemu-launcher qemuctl qemulator \
 qcad qcad-doc vim-common vim-full graphviz graphviz-doc \
 doxygen kubuntu-docs manpages-dev manpages gcc-doc libstdc++6-4.1-doc \
 xpdf flpsed chromium	unrar-free wine libwww-dev imagemagick \
 unifdef libbz2-dev libnewt-dev portmap nfs-kernel-server nfs-common \
 automake make pkg-config libgtk2.0-dev libncurses5-dev unzip zip \
 gimp gftp-gtk audacious grip lame yudit screem usbutils kalarm pidgin \
 firefox-2 kcalc esound-common esound galeon strace gerbv catdoc tree \
 cupsys-client smbfs bash-doc gawk gnuplot libtool autoconf kcharselect	\
 libc6-dev
# optional eclipse glade
check_err "install_aptstuff"
touch $TMPDIR/install_aptstuff
}

#************************************************************************
#
#************************************************************************
install_minicom_setups () {
if [ -e $TMPDIR/install_minicom_setups ]; then return 0; fi
if [ ! -e /etc/minicom ]; then 
	echo "Placing minicom setup files in /etc/minicom, but they most likely"
	echo " should be moved.  "
fi
sudo mkdir /etc/minicom
FILES=$(ls -d $TMPDIR/prog/scripts/minicom/* |grep -v CVS)
sudo cp $FILES /etc/minicom
check_err	"minicom setup"
touch $TMPDIR/install_minicom_setups
}
#************************************************************************
#
#************************************************************************
add_prog_exes () {
if [ -e $TMPDIR/add_prog_exes ]; then return 0; fi
check_for_prog
cd prog
make linux-bins
# set INSTALLDIR if not /usr/local/bin
sudo make INSTALLDIR=$PREFIX/bin install 
check_err "prog bins"
touch $TMPDIR/add_prog_exes
cd $CURDIR
}
#************************************************************************
#
#************************************************************************
add_gtk_inventory () {
if [ -e $TMPDIR/add_gtk_inventory ]; then return 0; fi
check_for_prog
cd prog/database/inventory/gtk
make
sudo cp gtk_inventory $PREFIX/bin
check_err "gtk_inventory"
touch $TMPDIR/add_gtk_inventory
cd $CURDIR
}
#************************************************************************
#
#************************************************************************
install_avr_cross () {
if [ -e $TMPDIR/install_avr_cross ]; then return 0; fi
mkdir -p $TMPDIR/avr
cd $TMPDIR/avr
$TMPDIR/prog/scripts/cross-compile4avr
check_err	"install_avr_cross"
touch $TMPDIR/install_avr_cross
}
#************************************************************************
#
#************************************************************************
install_avrdude () {
if [ -e $TMPDIR/install_avrdude ]; then return 0; fi
mkdir -p $TMPDIR/avr
cd $TMPDIR/avr
wget http://download.savannah.gnu.org/releases/avrdude/avrdude-5.5.tar.gz
check_err "download avrdude source"
tar -xzf avrdude-5.5.tar.gz
check_err "untar avrdude"
cd avrdude-5.5
patch -p1 < $TMPDIR/prog/scripts/patches/avrdude-5.5.usbtiny.64bit.patch
check_err	"patch avrdude"
./configure --prefix=/usr/local
check_err	"configure avrdude"
make
check_err	"make avrdude"
sudo make install
check_err	"install avrdude"
touch $TMPDIR/install_avrdude
}
#************************************************************************
#
#************************************************************************
install_partimage () {
	if [ -e $TMPDIR/install_partimage ]; then return 0; fi
	if [ ! -e /pub/tools/utils/HardDrive/partimage-0.6.6.tar.bz2 ] || 
	  [ ! -e /pub/tools/utils/HardDrive/partimage-0.6.6-amd64.patch ]; then
	  echo "Unable to find /pub/tools/utils/HardDrive/partimage-0.6.6-amd64.patch"
	  echo " or /pub/tools/utils/HardDrive/partimage-0.6.6-amd64.patch"
	  echo "Please locate these files and try again"
	  return
	fi
	cd $TMPDIR
	tar -xjf /pub/tools/utils/HardDrive/partimage-0.6.6.tar.bz2
	check_err "untar partimage"
	cd partimage-0.6.6
	patch -p1  < /pub/tools/utils/HardDrive/partimage-0.6.6-amd64.patch
	check_err "patch partimage"
	./configure --prefix=/usr/local 
	check_err "configure partimage"
	make
	check_err "make partimage"
	sudo cp src/client/partimage /usr/local/bin
	check_err "cp partimage"
	touch $TMPDIR/install_partimage
}
#************************************************************************
#
#************************************************************************
install_ffmpeg ()  {
	if [ -e $TMPDIR/install_ffmpeg ]; then return 0; fi
	sudo apt-get build-dep ffmpeg
	sudo apt-get install liblame-dev libfaad-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libx264-dev  libdts-dev
	sudo apt-get install ffmpeg 
	#sudo cp /usr/lib/libx264_pic.a /usr/lib/libx264.a
	apt-get source ffmpeg
	cd ffmpeg-*/
	./configure --enable-gpl --enable-pp --enable-pthreads  \ 
	--enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 \
	--enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad \
	--enable-libfaac --enable-xvid --enable-x264 --enable-libvorbis \
	--enable-libtheora  
	make
	sudo make install
	sudo apt-get install --reinstall libx264-dev
	touch $TMPDIR/install_ffmpeg
}
#************************************************************************
#
#************************************************************************
install_ghostpcl () {
if [ -e $TMPDIR/install_ghostpcl ]; then return 0; fi
	
cd $TMPDIR
wget http://ghostscript.com/releases/ghostpdl-1.52.tar.bz2
#/pub/tools/graphics/pcl /ghostpdl-1.52.tar.bz2
check_err "wget ghostpdl"
tar -xjf ghostpdl-1.52.tar.bz2
check_err "untarg ghostpdl"
cd ghostpdl-1.52
make
check_err "make ghostpdl"
sudo cp  main/obj/pcl6 $PREFIX/bin
for f in pcl2pdf pcl2pdfwr; do sudo cp tools/$f $PREFIX/bin; done
touch $TMPDIR/install_ghostpcl
cd $CURDIR
}
#************************************************************************
#	Installs the .desktop files and the icons so they appear in the menu
#************************************************************************
install_desktop_menu_items () {
if [ -e $TMPDIR/install_desk_menu ]; then return 0; fi
APP_DIR=/usr/share/applications
ICON_DIR=/usr/share/pixmaps
check_for_prog
for f in $(ls prog/desktop/*.desktop|sed 's!.*/!!'); do
	sudo cp prog/desktop/$f $APP_DIR/$f
done
for f in $(ls prog/desktop/icons/128x128/*|sed 's!.*/!!'); do
	sudo cp prog/desktop/icons/128x128/$f $ICON_DIR/$f
done
touch $TMPDIR/install_desk_menu
cd $CURDIR
}
#************************************************************************
#
#************************************************************************
add_mount () {
ME=$(grep -c $1 $TMPDIR/fstab)
if [ $ME -eq 0 ]; then
	echo "s:$1          $1            nfs     rw,suid,exec,user,wsize=8192,rsize=8192 0 0" >> $TMPDIR/fstab
	sudo mkdir -p $1
fi
}
#************************************************************************
#
#************************************************************************
add_mounts () {
if [ -e $TMPDIR/add_mounts ]; then return 0; fi
cp /etc/fstab $TMPDIR
for d in /pub /data; do
	add_mount $d
done
sudo cp $TMPDIR/fstab /etc/fstab
sudo chmod 644 /etc/fstab
}

#************************************************************************
#
#************************************************************************
CURDIR=$(pwd)
#************************************************************************
#sanity checks
#************************************************************************
checkfor nexist $TMPDIR
checkfor zero "$CVSROOT" CVSROOT
checkfor sudo
install_aptstuff
checkfor wine
#Add mount points
add_mounts
mount /pub
# first, install tse32
install_tse
# now install tablaunch
install_tablaunch
install_scripts
fix_bashrc

install_minicom_setups
add_prog_exes 
add_gtk_inventory
install_avr_cross
# the cross-compile script does avr dude now.
#install_avrdude
install_partimage
install_ffmpeg
install_ghostpcl
install_desktop_menu_items

cd $CURDIR


```

---

### Post by deconstrained on 2010-11-16
> **rickyrockrat said:**
> I agree. Too many Ubuntu distros.  Personally, I would like to see them all go to one, then select your desktop on install.
That is a fantastic idea. It's sort of like the way it's done in plain Debian (where you select categories of packages to install based on the type of system you want to build), but even that can be improved upon, i.e. by showing the meaning/role of each package/metapackage using a slick Software-Center-like interface that allows you to pick and choose.

---

### Post by rickyrockrat on 2010-11-16
> **deconstrained said:**
> That is a fantastic idea. It's sort of like the way it's done in plain Debian (where you select categories of packages to install based on the type of system you want to build), but even that can be improved upon, i.e. by showing the meaning/role of each package/metapackage using a slick Software-Center-like interface that allows you to pick and choose.

LOL. I remember the old Red Hat days (Remember the 2.4 kernel for the desktop?), and it was very much like that as well. I left RH with FedCore 3, when Yum blew up on me and put me into RPM hell on my server.  Apt has been bomb-proof so far.

---

