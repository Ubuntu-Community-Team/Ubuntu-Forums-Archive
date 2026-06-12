---
title: "Enlightenment 19"
date: 2014-08-20
forum: Desktop Environments
---

### Post by Jordan_Henley on 2014-08-20
I installed Enlightenment 19 via a script well writen by someone, whom I could not find the name of, I just have one problem, it installed everything into my home folder at '/home/owner/Enlightenment19'. Im trying to figure out how to install the Entrance Display Manager but for now sense I cant find out how to do that, I was going to login via console, but the script did not put enlightenment_start at '/usr/local/bin/enlightenment_start'. So I have no idea how to execute it from console now, could someone please help me, it would be much apreciated. Im going to try to put the script below if it lets me. This script works to install Enlightenment in Ubuntu 14.04, and has no issue with installation, there are some bugs, but the install works well. If you are here on account of trying to install Enlightenment 19, this will help you, I spent hours finding this script and would like to share it, the script works for Ubuntu and from what I understand its suppose to work for Debian too, the script allows you to install, update, and remove Enlightenment 19, when I installed it got to the end with an error, so when you install it I recommend you do an update right after the install, credit to creator (unknown). Also I would like to request a tag for Enlightenment 19, I only see 17. ```
#!/bin/bash
#
# NINETEEN.SH
# This script allows you to install/update Enlightenment 19 git version on
# Ubuntu 14.04 LTS or Debian wheezy/sid, or remove E19 git from your system.
# Originally from: http://ubuntuforums.org/showthread.php?t=2203190
# By: Philippe J. Guillaumie (batden AT sfr DOT fr).
# Additional updates by: Bryan Hundven (bryanhundven AT gmail DOT com).
#
# Tip:
# Running Ubuntu? Get the Faenza icon set for your enlightened desktop before
# running the script for the first time!
# See http://www.noobslab.com/2013/10/faience-and-faenza-icons-for.html
#
# If you are using Debian, you can find Faience theme here:
# http://gnome-look.org/content/show.php/Faenza?content=128143
# and the Faenza theme here:
# http://gnome-look.org/content/show.php/New+Faience+icon+pack?content=157437
#
# To execute the script:
# 1. Open Terminal
# 2. Change to the download folder
# 3. Make the script executable with chmod +x
# 4. Run it with ./nineteen.sh
#
# Feel free to use this script as you see fit.
 
# VARIABLES
bld="\e[1m" # Bold text.
bdr="\e[1;31m" # Bold red text.
bdg="\e[1;32m" # Bold green text.
bdy="\e[1;33m" # Bold yellow text.
off="\e[0m" # Turn off ansi colors.
 
msg_bold () {
printf "\n${bld}%s ${off}%s\n" "$@"
}
msg_red () {
printf "\n${bdr}%s ${off}%s\n" "$@"
}
msg_green () {
printf "\n${bdg}%s ${off}%s\n" "$@"
}
msg_yellow () {
printf "\n${bdy}%s ${off}%s\n" "$@"
}
 
trap '{ msg_red " KEYBOARD INTERRUPT."; exit 130; }' INT
 
PREFIX="/usr/local"
export CPPFLAGS="-I/usr/local/include -I${PREFIX}/include"
export LDFLAGS="-L/usr/local/lib -L${PREFIX}/lib"
export PKG_CONFIG_PATH="/usr/local/lib/pkgconfig:${PREFIX}/lib/pkgconfig"
export CC="ccache gcc"
export CXX="ccache g++"
 
NCPU=$(getconf _NPROCESSORS_ONLN)
NJOBS=$((NCPU*2))
export MAKE="make -j ${NJOBS}"
 
E19="${HOME}/Enlightenment19"
TITLE="wmctrl -r :ACTIVE: -N"
GEN="./autogen.sh --prefix=${PREFIX}"
RELEASE="$(lsb_release -sc)"
CODE="$(locale | grep 'LANG=' | cut -d= -f2 | cut -d_ -f1)"
DROPB="https://dl.dropboxusercontent.com/u/"
NO_NLS=0
 
DOCUDIR="$(test -f ${XDG_CONFIG_HOME:-~/.config}/user-dirs.dirs && \
source ${XDG_CONFIG_HOME:-~/.config}/user-dirs.dirs
echo ${XDG_DOCUMENTS_DIR:-$HOME})"
 
DEPS_EN="aspell-${CODE} manpages imagemagick xserver-xephyr \
manpages-dev automake autopoint build-essential ccache \
check doxygen freeglut3-dev git libasound2-dev \
libblkid-dev libbullet-dev libfontconfig1-dev \
libfreetype6-dev libfribidi-dev libgif-dev libglib2.0-dev \
libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev \
libharfbuzz-dev libiconv-hook-dev libjpeg-dev libblkid-dev \
libluajit-5.1-dev libmount-dev libpam0g-dev libpng12-dev \
libpoppler-dev libpulse-dev libraw-dev librsvg2-dev \
libsndfile1-dev libspectre-dev libssl-dev libtiff5-dev libtool \
libudev-dev libudisks2-dev libunibreak-dev libvlc-dev libwebp-dev \
libxcb-shape0-dev libxcb-keysyms1-dev libxcomposite-dev \
libxcursor-dev libxine-dev libxinerama-dev libxp-dev libxrandr-dev \
libxss-dev libxtst-dev ragel valgrind wmctrl"
 
TRIM_EN="${DEPS_EN:46}"
 
DEPS="aspell-${CODE} manpages.${CODE} imagemagick xserver-xephyr \
manpages-dev manpages-${CODE}-dev manpages-${CODE}-extra automake \
autopoint build-essential ccache check doxygen freeglut3-dev \
git libasound2-dev libblkid-dev libbullet-dev \
libfontconfig1-dev libfreetype6-dev libfribidi-dev \
libgif-dev libglib2.0-dev libgstreamer1.0-dev \
libgstreamer-plugins-base1.0-dev libharfbuzz-dev libiconv-hook-dev \
libjpeg-dev libblkid-dev libluajit-5.1-dev libmount-dev libpam0g-dev \
libpng12-dev libpoppler-dev libpulse-dev libraw-dev librsvg2-dev \
libsndfile1-dev libspectre-dev libssl-dev libtiff5-dev libtool \
libudev-dev libudisks2-dev libunibreak-dev libvlc-dev libwebp-dev \
libxcb-shape0-dev libxcb-keysyms1-dev libxcomposite-dev \
libxcursor-dev libxine-dev libxinerama-dev libxp-dev libxrandr-dev \
libxss-dev libxtst-dev ragel valgrind wmctrl"
 
TRIM="${DEPS:48}"
 
CLONEFL="git clone git://git.enlightenment.org/core/efl.git"
CLONEVL="git clone git://git.enlightenment.org/core/evas_generic_loaders.git"
CLONEGP="git clone git://git.enlightenment.org/core/emotion_generic_players.git"
CLONELM="git clone git://git.enlightenment.org/core/elementary.git"
CLONE19="git clone git://git.enlightenment.org/core/enlightenment.git"
CLONETY="git clone git://git.enlightenment.org/apps/terminology.git"
CLONEBPFL="git clone git://git.enlightenment.org/bindings/python/python-efl.git"
CLONEECON="git clone git://git.enlightenment.org/apps/econnman.git"
 
EPROG="efl evas_generic_loaders emotion_generic_players elementary
enlightenment terminology python-efl econnman"
 
tmp_count=0
EPROG_COUNT=$(for i in $(echo ${EPROG}); do tmp_count=$((tmp_count+1)); done && echo ${tmp_count})
unset tmp_count
 
# Enable this option to force messages to display in English
# during the build process (bug reporting):
# export LC_ALL=C
 
# TESTS
msg_bold "SYSTEM REQUIREMENTS CHECK..."; sleep 1
 
dpkg -l | egrep 'e17|enlightenment' &>/dev/null
if [ $? == 0 ]; then
msg_red " ANOTHER VERSION OF ENLIGHTENMENT IS INSTALLED."
msg_red " SCRIPT ABORTED."
exit 1
fi
 
if [ $(pidof enlightenment) ]; then
msg_red "PLEASE LOG IN TO UBUNTU TO EXECUTE THIS SCRIPT."
exit 1
fi
 
if [ "${RELEASE}" == "trusty" ]; then
msg_green "Ubuntu ${RELEASE}... OK"; sleep 1
elif [ "${RELEASE}" == "sid" -o "${RELEASE}" == "wheezy" ]; then
msg_green "Debian ${RELEASE}... OK"; sleep 1
else
msg_red " UNSUPPORTED VERSION."
exit 1
fi
 
# FUNCTIONS
warn () {
zenity --no-wrap --info --text "
If you proceed with the installation,\n\
nearly 1.5 GB of additional disk space\n\
will be used.\n
Bear in mind that running other applications\n\
during the build process will affect\n\
compilation time."
sleep 1
}
 
should_we_disable_nls () {
if [ ${NO_NLS} -eq 1 ]; then
GEN=${GEN} --disable-nls
msg_green "Building with NLS disabled!"
else
msg_green "Building with NLS enabled!"
fi
}
 
bin_deps () {
sudo apt-get update && sudo apt-get dist-upgrade --yes
 
if [ ! -f "${DOCUDIR}/installed.txt" ]; then
dpkg --get-selections > "${DOCUDIR}/installed.txt"
sed -i '/linux-headers*/d' "${DOCUDIR}/installed.txt"
sed -i '/linux-image*/d' "${DOCUDIR}/installed.txt"
sed -i '/linux-generic*/d' "${DOCUDIR}/installed.txt"
sed -i '/linux-signed*/d' "${DOCUDIR}/installed.txt"
fi
 
if [ "${CODE}" == "en" ]; then
sudo apt-get install --yes ${DEPS_EN}
sleep 1
else
sudo apt-get install --yes ${DEPS}
sleep 1
fi
}
 
ls_ppa () {
local PPA="$(awk '$1 == "Package:" { print $2 }' \
/var/lib/apt/lists/*ppa*Packages)"
for i in $(echo ${PPA} | xargs -n1 | sort -u); do
dpkg-query -Wf'${db:Status-abbrev}' ${i} &>/dev/null
if [ $? == 0 ]; then
sed -i "/${i}/d" "${DOCUDIR}/installed.txt"
fi
done
}
 
build () {
for i in ${EPROG}; do
${TITLE} "Processing $i..."
cd "${E19}/${i}"
should_we_disable_nls
msg_bold "Building ${i}..."
case ${i} in
"efl")
${GEN} --enable-harfbuzz --enable-image-loader-webp \
--enable-multisense --enable-xine --enable-xinput22
;;
"enlightenment")
${GEN} --enable-mount-eeze --disable-wl-desktop-shell
;;
"python-efl")
sed -i -e \
"s#setup.py install#setup.py install --prefix=${PREFIX}#" \
Makefile
;;
*)
${GEN}
;;
esac
echo
make
if [ $? -ne 0 ]; then
msg_red " BUILD ERROR&#8212;TRY AGAIN LATER."
# (Relaunch the script at a later time and select option #1)
rm -rf "${E19}/${i}"
exit 1
fi
sudo make install
sudo ldconfig
done
}
 
rebuild () {
for i in ${EPROG}; do
${TITLE} "Processing ${i}..."
cd "${E19}/${i}"
should_we_disable_nls
msg_bold "Updating ${i}..."
make distclean &>/dev/null
git reset --hard &>/dev/null
git pull
echo
case ${i} in
"efl")
${GEN} --enable-harfbuzz --enable-image-loader-webp \
--enable-multisense --enable-xine --enable-xinput22
;;
"enlightenment")
${GEN} --enable-mount-eeze --disable-wl-desktop-shell
;;
*)
${GEN}
;;
esac
echo
make
if [ $? -ne 0 ]; then
msg_red " BUILD ERROR&#8212;TRY AGAIN LATER."
# (Relaunch the script at a later time and select option #2)
exit 1
fi
sudo make install
sudo ldconfig
echo
done
}
 
remove () {
msg_bold "Cleaning $i..."
sudo make uninstall &>/dev/null
make maintainer-clean &>/dev/null
echo
}
 
deep_clean () {
msg_bold "Deeper cleaning..."; sleep 1
 
for i in \
"econnman/" \
"python-efl/" \
"terminology/" \
"enlightenment/" \
"elementary/" \
"emotion_generic_players/" \
"evas_generic_loaders/" \
"terminology/" \
"efl/" \
"custom*"; \
do
rm -rf "${E19}/${i}"
done
 
for i in \
"Enlightenment19/" \
".e/" \
".elementary/" \
".cache/efreet/" \
".cache/evas_gl_common_caches/" \
".config/terminology/"; \
do
rm -rf "${HOME}/${i}"
done
 
for i in \
"enlightenment/"; \
do
sudo rm -rf "${PREFIX}/etc/${i}"
done
 
for i in \
"ecore*" \
"edje*" \
"eet*" \
"eeze*" \
"efl*" \
"efreet*" \
"eina*" \
"eio*" \
"eldbus*" \
"elementary*" \
"embryo*" \
"emotion*" \
"enlightenment*" \
"eo*" \
"ephysics*" \
"ethumb*" \
"evas*"; \
do
sudo rm -rf "${PREFIX}/include/${i}"
done
 
for i in \
"ecore*" \
"edje*" \
"eeze*" \
"efl*" \
"efreet*" \
"elementary*" \
"emotion*" \
"enlightenment*" \
"eo*" \
"ephysics*" \
"ethumb*" \
"evas*"; \
do
sudo rm -rf "${PREFIX}/lib/${i}"
done
 
for i in \
"Ecore*" \
"Edje*" \
"Eet*" \
"Eeze*" \
"Efreet*" \
"Eina*" \
"Eldbus*" \
"Elementary*" \
"Eo*" \
"Ethumb*" \
"Evas*" \
"Emotion*"; \
do
sudo rm -rf "${PREFIX}/lib/cmake/${i}"
done
 
for i in \
"ecore*" \
"e_dbus*" \
"edje*" \
"efl*" \
"elementary*" \
"emotion*" \
"evas*" \
"python_efl*.egg-info"; \
do
sudo rm -rf "${PREFIX}/lib/python2.7/dist-packages/${i}"
done
 
for i in \
"dbus*" \
"ecore*" \
"edje*" \
"eeze*" \
"efreet*" \
"elementary*" \
"embryo*" \
"emotion*" \
"enlightenment*" \
"eo*" \
"ethumb*" \
"evas*" \
"terminology*" \
"econnman*"; \
do
sudo rm -rf "${PREFIX}/share/${i}"
done
 
for i in \
"connman*"; \
do
sudo rm -rf "${PREFIX}/var/lib/{$i}"
done
 
cd /usr/share/
sudo rm -rf xsessions/enlightenment.desktop
cd unity-greeter/
sudo rm custom_enlightenment_badge.png &>/dev/null
cd ../dbus-1/services/
sudo rm -rf org.enlightenment.Efreet.service
sudo rm -rf org.enlightenment.Ethumb.service
echo
}
 
# SELECTION
INPUT=0
msg_bold "Please enter the number of your choice."
 
if [ $INPUT -lt 1 ]; then
msg_bold "1. Install Enlightenment 19."
msg_bold "2. Update my E19 installation."
msg_bold "3. Uninstall E19 programs only."
msg_bold "4. Uninstall E19 programs AND binary dependencies."
sleep 1
msg_bold "(Or press Ctrl-C to quit)"
read INPUT
fi
 
# INSTALLATION
if [ ${INPUT} == 1 ]; then
clear
msg_bold "Proceeding to install Enlightenment 19..."
warn 2>/dev/null; sleep 1
 
if grep -q ppa /var/lib/apt/lists/*ppa* &>/dev/null; then
bin_deps
ls_ppa
else
unset -f ls_ppa
bin_deps
fi
 
cd "${HOME}"; mkdir -p "${E19}"; cd "${E19}"
${TITLE} "Downloading Source Code..."
msg_bold "Fetching git code..."
${CLONEFL}; echo
${CLONEVL}; echo
${CLONEGP}; echo
${CLONELM}; echo
${CLONE19}; echo
${CLONETY}; echo
${CLONEBPFL}; echo
${CLONEECON}; echo
 
COUNT=$(ls "${E19}" | wc -l)
 
if [ ${COUNT} -ge ${EPROG_COUNT} ]; then
msg_green "All programs have been downloaded."
sleep 2
elif [ ${COUNT} == 0 ]; then
msg_red "PLEASE CHECK YOUR NETWORK CONNECTION AND TRY AGAIN."
# (Relaunch the script and select option #1)
exit 1
else
msg_yellow "WARNING: ONLY ${COUNT} OF ${EPROG_COUNT} PROGRAMS HAVE BEEN DOWNLOADED."
sleep 3
fi
 
$TITLE "Processing Enlightenment Programs..."
echo
 
read -p "Build internationalization support in Enlightenment? [y/n] " answer
case "${answer}" in
[yY])
: Nothing... NLS is built by default.
build
;;
[nN])
NO_NLS=1
build
;;
*)
msg_yellow "Please answer y or n"
;;
esac
 
sudo ln -sf \
${PREFIX}/share/dbus-1/services/org.enlightenment.Ethumb.service \
/usr/share/dbus-1/services/org.enlightenment.Ethumb.service
sudo ln -sf \
${PREFIX}/share/dbus-1/services/org.enlightenment.Efreet.service \
/usr/share/dbus-1/services/org.enlightenment.Efreet.service
 
cd "${E19}"
wget "${DROPB}/58695863/custom_enlightenment_badge.png" &>/dev/null
sudo cp -f custom_enlightenment_badge.png /usr/share/unity-greeter
sudo ln -sf "${PREFIX}/share/xsessions/enlightenment.desktop" \
/usr/share/xsessions/enlightenment.desktop
sudo ldconfig
$TITLE "That's All Folks..."
printf "\n%s\n\n" " That's All Folks..."
 
# UPDATE
elif [ ${INPUT} == 2 ]; then
clear
msg_bold "Proceeding to update Enlightenment 19..."
sleep 1
 
msg_bold "Checking required Ubuntu/Debian packages..."
if [ "${CODE}" == "en" ]; then
sudo apt-get install --yes ${DEPS_EN}
sleep 1
else
sudo apt-get install --yes ${DEPS}
sleep 1
fi
echo
 
${TITLE} "Processing Enlightenment Programs..."
echo
 
read -p "Build internationalization support in Enlightenment? [y/n] " answer
case "${answer}" in
[yY])
# Rebuild
rebuild; echo
;;
[nN])
# Rebuild without NLS
NO_NLS=1
rebuild; echo
;;
*)
msg_yellow "Please answer y or n"
;;
esac
 
sudo ln -sf \
"${PREFIX}/share/dbus-1/services/org.enlightenment.Ethumb.service" \
/usr/share/dbus-1/services/org.enlightenment.Ethumb.service
sudo ln -sf \
"${PREFIX}/share/dbus-1/services/org.enlightenment.Efreet.service" \
/usr/share/dbus-1/services/org.enlightenment.Efreet.service
 
cd "${E19}"
wget -nc "$DROPB/58695863/custom_enlightenment_badge.png" &>/dev/null
sudo cp -f custom_enlightenment_badge.png /usr/share/unity-greeter
sudo ln -sf "${PREFIX}/share/xsessions/enlightenment.desktop" \
/usr/share/xsessions/enlightenment.desktop
sudo ldconfig
${TITLE} "That's All Folks..."
printf "\n%s\n\n" " That's All Folks..."
 
# UNINSTALL E19
elif [ ${INPUT} == 3 ]; then
clear
msg_bold "Proceeding to uninstall Enlightenment 19..."
sleep 1
 
for i in ${EPROG}; do
${TITLE} "Processing $i..."
cd "${E19}/${i}" && remove
done
deep_clean
${TITLE} "That's All Folks..."
printf "%s\n\n" " That's All Folks..."
 
# COMPLETE UNINSTALL
elif [ ${INPUT} == 4 ]; then
clear
msg_bold "Complete uninstallation of E19 and deps..."
sleep 1
 
for i in ${EPROG}; do
${TITLE} "Processing ${i}..."
cd "${E19}/${i}" && remove
done
deep_clean
 
${TITLE} "Processing Ubuntu Packages..."
msg_bold "Removing binary dependencies..."
 
if [ "${CODE}" == "en" ]; then
sudo apt-get autoremove ${TRIM_EN}
sleep 1
else
sudo apt-get autoremove ${TRIM}
sleep 1
fi
 
sudo dpkg --set-selections < "${DOCUDIR}/installed.txt"
sudo apt-get dselect-upgrade
sudo apt-get update
sudo apt-get dist-upgrade
 
rm "${DOCUDIR}/installed.txt" &>/dev/null
sudo updatedb
sudo apt-get autoremove --purge
sudo dpkg --purge $(COLUMNS=200 dpkg -l | grep '^rc' | tr -s ' ' | \
cut -d ' ' -f 2) &>/dev/null
printf "\n%s\n\n" " That's All Folks..."
printf "\n%s\n\n" " If you want, you should delete your ~/.ccache to save space."
 
else
echo; exit 1
fi
# vi: ts=4:sw=4:et
```

---

### Post by Frogs Hair on 2014-08-20
Here is the link to the thread referenced in the beginning of the script you'll find a name there too.  

[http://ubuntuforums.org/showthread.php?t=2203190&highlight=build+enlightenment](http://ubuntuforums.org/showthread.php?t=2203190&highlight=build+enlightenment)

---

### Post by Jordan_Henley on 2014-08-20
I swear I looked through that whole script and didnt notice that link.

---

### Post by batden on 2014-08-26
Thanks Frogs Hair  ;)

---

### Post by Frogs Hair on 2014-08-26
You're Welcome !

---

