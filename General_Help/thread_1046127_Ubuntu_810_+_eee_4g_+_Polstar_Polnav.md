---
title: "Ubuntu 810 + eee 4g + Polstar Polnav"
date: 2009-01-21
forum: General Help
---

### Post by Danzarak on 2009-01-21
Hello,
Slightly random query here..

I have an eee 4g which I use with Ubuntu 8.10 without issues.  I have just purchased the PolNav GPS software by PolStar (from AT Imports UK) with the intention of using the eee as a GPS unit.  I have an external bluetooth GPS unit, and a bluetooth dongle - and that part works fine as tested in xgps.

The PolNav software is a version designed to run on the Xandros OS, the netbook version which come preinstalled on the eee.  I'm installing the software on a USB stick to save space on the eee.  I've run the setup file on the stick, and the setup has successfully extracted all the files into their folders.

My query then is this - what do I need to do to install the software on Ubuntu, when it is by default a Xandros install?  Is this possible?  I'd hoped so since they are both debian based.

What looks to be the main file is an exe file?  Any ideas?  I haven't put much more info in this post yet, as I'm not sure what you'd need to know.

Thanks, I really want to get this going, and if so I'd like to create an alternative installer for Ubuntu.

Danzarak

---

### Post by Danzarak on 2009-01-21
Ok... a little more information...

The setup script does this:

#!/bin/bash
INSTALL_PATH=/home/user
CUR_PATH=`pwd`
MKDIR_PATH=GPS_PolNav
TAR_FILE=polnav_file.gz
TAR_MAP=polnav_map.gz
TAR_BIN=polnav_bin.gz
cd $INSTALL_PATH
mkdir $MKDIR_PATH 
cd $CUR_PATH
mv $TAR_FILE $TAR_MAP $TAR_BIN $INSTALL_PATH/$MKDIR_PATH/
cd $INSTALL_PATH/$MKDIR_PATH
tar xvfz $TAR_FILE 
tar xvfz $TAR_MAP 
tar xvfz $TAR_BIN 
mv $TAR_FILE $TAR_MAP $TAR_BIN $CUR_PATH
cd Install
sudo ./uninstall.sh
sudo ./install.sh

...the last script - install.sh - does this:

#!/bin/bash

echo "Installing PolNav..."
CUR_PATH=`pwd`
RC_PATH=/opt/xandros/share/AsusLauncher/
ROOT_RC_FILE=/opt/xandros/share/AsusLauncher/simpleui.rc
RC_FILE=$CUR_PATH/temp.rc
POL_PATH=$CUR_PATH/polnav

CHK_INST=`sudo cat $ROOT_RC_FILE | grep polnav`
if [ "$CHK_INST" != "" ] ; then
  echo "PolNav is already installed";
  exit;
fi

echo "Backup simpleui.rc as simpleui.rc.bak"

sudo cp $ROOT_RC_FILE $CUR_PATH/simpleui.rc.bak
sudo cat $ROOT_RC_FILE | grep -Ev '<\/simpleui>' > $RC_FILE 

echo "Creating icon for PolNav"

sudo echo "<parcel simplecat=\"Work\" extraargs=\"$POL_PATH\"" >> $RC_FILE
sudo echo "        icon=\"polnav.png\"" >> $RC_FILE
sudo echo "        selected_icon=\"polnav_hi.png\">" >> $RC_FILE
sudo echo "        <name lang=\"en\">PolNav</name>" >> $RC_FILE
sudo echo "        <desc lang=\"en\">This is a navigation software.</desc><!--PolNav-->" >> $RC_FILE
sudo echo "</parcel><!--PolNav-->" >> $RC_FILE
sudo echo "</simpleui>" >> $RC_FILE

sudo mv $RC_FILE $ROOT_RC_FILE
sudo cp *polnav*.png $RC_PATH

echo "Creating path link for PolNav"

sudo echo "cd $CUR_PATH" > $POL_PATH
sudo echo "cd .." >> $POL_PATH
sudo echo "sudo ./runRelease" >> $POL_PATH
sudo chmod +x $POL_PATH 
if [ -d /opt/xandros/sbin ] ; then
sudo /opt/xandros/sbin/update-launcher
fi
echo "Install Complete!"

...and the ./runrelease that it creates the link to does this:

./polnav_linux_release.exe

...so it looks like the main program IS an exe... is that not a windows executable?  Does Xandros use exe?

---

### Post by Danzarak on 2009-01-21
Hello again,

Ok, I am a little further along now.  I have managed to get the exe to run after finding a terminal message mentioning libsdl-image1.2.  I installed this and it ran ok.  I can only assume that this package is installed by default as part of the Xandros eee OS.

Anyhow... my next problem is that I am using a Bluetooth connection to my GPS tracker.  I have gone through the connection process to pair with the device, and it is registered as /dev/rfcomm4.  If I cat /dev/rfcomm4 I get the NMEA responses... and if I gpsd to it, I can xgps it and see the satellites.

However, in the PolNav software, I am trying to select a GPS Port and the only options are USB1 to USB4, and ACM1 to ACM4.  I'm not sure what the ACM part means... and I don't know what to select.  There is also a baud rate, which I'm not sure of.

I know this is a seperate product to Ubuntu, but I'm hoping someone might be able to explain how the Ubuntu com port structure might map to the one in the PolNav software.  I'm so very close to getting this working, and I know there are a lot of people out there with eee and ubuntu who'd be interested (in lieu of there being a good GPS product on Ubuntu.)

Thanks,
Dan

---

### Post by Danzarak on 2009-01-22
Bump... no-one have any advice on Ubuntu com ports?

---

### Post by savantelite on 2009-03-30
In jaunty you can easily connect your bluetooth dongle even if it has a fixed code. :)

Unfortunaly I am still working on finding how GPSD grabs info from the dongle and puts it into my tango gps program:(

---

