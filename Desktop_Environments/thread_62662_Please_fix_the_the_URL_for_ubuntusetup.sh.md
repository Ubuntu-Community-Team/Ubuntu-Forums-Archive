---
title: "Please fix the the URL for ubuntusetup.sh"
date: 2005-09-05
forum: Desktop Environments
---

### Post by seedofconspiracy on 2005-09-05
Hi,

I'm am unable to wget the ubuntusetup.sh.  Instructions on the wiki point to:

**[http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh](http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh) **

When I wget this per the instructions, I get:

[I]--13:22:04--  [http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh](http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh)
           => `ubuntusetup.sh'
Resolving download.ubuntuforums.org... 69.46.19.10
Connecting to download.ubuntuforums.org[69.46.19.10]:80... failed: Connection refused.[/I]

Thanks.

---

### Post by seedofconspiracy on 2005-09-05
Is there a possible mirror site for this script?

---

### Post by tiwaris on 2005-09-08
or can someone just post the script

the link is broken, and I cannot find it elsewhere.

Thanks
Tiwaris

---

### Post by bob k on 2005-09-08
Here ya go. I just copied it. I commented out the security keys because they didn't work the last time I used it. I also uncommeted the java stuff, I couldn't remember if it was commented out or not.

from the terminal gedit filename.sh
mark and copy shell script
paste in gedit and save, exit, and gedit and customize for your install (ie mirror sites for repositories, they were contained in a file where the script was and can be changed in the global section in the script).

#!/bin/bash
#												
# +*** WANRING WARNING WARNING WARNING WARNING ***----------------------------------------------+
# | Purpose of this script is to automate/tweak setting up a new ubuntu system.			|
# |												|
# | This script installs 3rd party programs and are not supported by canonical/ubuntu.		|
# | If this script blows up your installation it's not my fault :)				|
# |												|
# | This script has been tested on Hoary Hedgehog 5.04.						|
# | +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++	|
# | This script will perform the following functions. 						|
# | 1. Install beep-media-player, gstreamer0.8-mad (for mp3's)					|
# | 2. Enable debian-marillat, universe and multiverse repo's					|
# | 3. Install latest java and enable java in firefox						|
# | 4. Give you nice forms in firefox								|
# | 5. Install streamtuner 									|
# | 6. Install msttcorefonts									|
# | 7. Install latest acrobat reader and firefox plugin						|
# | 8. Install dvd playback support								|
# | 9. Install w32codecs and dvd libraries							|
# | 10. Install gnomebaker									|
# | --------------------------------------------------------------------------------------------|
# | 5/2/2005 - using backports for java | remove acrobat reader its broke			|
# +---------------------------------------------------------------------------------------------+

### global options ###
wget="/usr/bin/wget"
apt="/usr/bin/apt-get"
core_packages="build-essential" 
media_packages="beep-media-player gstreamer0.8-mad w32codecs streamtuner xine-ui totem-xine"
misc_packages="msttcorefonts libdvdcss2 gnomebaker gftp flashplayer-mozilla"
useing backports java
java_jre_url="http://download.ubuntuforums.org/ubuntusetup/jre-1_5_0_02-linux-i586.bin"
firefox_forms="http://download.ubuntuforums.org/ubuntusetup/ff-forms.tar.gz"
sources_list_url="http://download.ubuntuforums.org/ubuntusetup/sources.list"
misc_fonts_url="http://download.ubuntuforums.org/ubuntusetup/miscfonts.tar.gz"

### functions ###
check_errs()
{
  if [ "${1}" -ne "0" ]; then
    echo "ERROR # ${1} : ${2}"
    exit ${1}
  fi
}
### main script starts here ###

### snag the updated sources.list   ***** I commented out the next 5 lines ** key problems **

#cd /etc/apt/ && mv sources.list sources.list.orig && ${wget} ${sources_list_url}
#gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
#gpg --armor --export 1F41B907 | sudo apt-key add -
#check_errs $? "There was an error downloading the sources.list."
#sleep 5

### lets update the apt repo
${apt} update
check_errs $? "There was an error in apt-get update."
sleep 5

### lets install build-esstential
echo "Additional packages maybe need to be installed select yes if asked"
${apt} install ${core_packages}
check_errs $? "There was an error in ${core_packages} installation."
sleep 5

### lets install media_packages
echo "Additional packages maybe need to be installed select yes if asked"
${apt} install ${media_packages}
check_errs $? "There was an error in ${media_packages} installation."
sleep 5

### lets install misc_packages
echo "Additional packages maybe need to be installed select yes if asked"
${apt} install ${misc_packages}
check_errs $? "There was an error in ${misc_packages} installation."
sleep 5

### lets install misc windows fonts that are not in the msttcorefonts package
echo "Installing Misc fonts"
cd /usr/share/fonts/truetype/msttcorefonts
${wget} ${misc_fonts_url}
tar xvzf miscfonts.tar.gz
rm -f miscfonts.tar.gz
check_errs $? "Misc Fonts Installation has failed..."
sleep 5

### lets install firefox forms
echo "Installing firefox forms"
cd /usr/lib/mozilla-firefox/
${wget} ${firefox_forms}
tar xvzf ff-forms.tar.gz
rm -f ff-forms.tar.gz
check_errs $? "Firefox forms Installation has failed..."
sleep 5

### lets install java
echo "Installing java"
${apt} install sun-j2re1.5

echo "If you made it this far job well done."

---

