---
title: "Some Problems with the update .."
date: 2010-12-22
forum: Desktop Environments
---

### Post by var1989 on 2010-12-22
Hi 

The thing is that I have trouble updating my Ubuntu 10.10 . I recently formatted my laptop and installed Ubuntu and using this [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) I got a list and also I selected both Canonical updates and stuff like that ...

Now whenever i try to update using update manager i get an error that 

"Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources."

so please help me

Thanks in advance

---

### Post by germanix on 2010-12-22
Just give me a  little bit of time. I am writing an answer to your question and will be back soon.

---

### Post by germanix on 2010-12-22
Go to applications-administration-software sources and list here which sources you have listed there.

---

### Post by var1989 on 2010-12-22
Thanks for replying 

Okay 

I would have done that but  then i realized  i didnt really get what you said . Should i list all the contents i selected under "Ubuntu Software" ? Or "Other software " ?

Thanks again

---

### Post by germanix on 2010-12-22
Tell me both

---

### Post by var1989 on 2010-12-22
okay here it goes

goin to select the ones i have selected 

Canonical-Supported open source software (main)
Community-maintained open source software(universe)

Other Software

Canonical Partners
then there is long list of application's names like Banshee ,AWN,Chromium,DeadBeef,Deluge etc.

Thanks

---

### Post by germanix on 2010-12-22
Wow, you live dangerously my friend. So lets start cleaning up. For the meantime go to software sources and to the tab "other software". Leave Canonical partners and if you have things like "Ubuntu 10.10 officialy surported non free drivers", Important security updates, or medibuntu on that list, leave it also. The rest you remove by highlighting each one with the left mouse button and then clicking the tab at the bottom of the window saying "remove". When you have done that come back

---

### Post by germanix on 2010-12-22
So while I am waiting for you to come back here some general advice.
Always keep things stupid/simple
Less is more!
If you want your system to keep running stable you should never use "sources" that has not been approved and tested.
I myself only use "main" and important security updates. I am even wary of using the " ubuntu recommended updates" as they sometimes break my system. I wait until it has been tested for a while and watch this forum before I install them.
I do use the medibuntu depository for all the codecs. (this is not legal in all countries, so check it out first for your country)

---

### Post by var1989 on 2010-12-22
Yeah Did what you told me to do ..

And I tried updating it and again the error came up again that these  are the unauthorized packages 

"intel-gpu-tools libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libice6 libpciaccess0 libpixman-1-0 libsm6 libva-x11-1 libva1 libx11-6 libx11-data libx11-xcb1 libxaw7 libxcb-dri2-0 libxcb-randr0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfixes3 libxfont1 libxi6 libxinerama1 libxkbfile1 libxmu6 libxmuu1 libxpm4 libxrandr2 libxrender1 libxres1 libxt6 libxtst6 libxv1 libxxf86dga1 libxxf86vm1 linux-libc-dev notify-osd nvidia-current-modaliases ttf-symbol-replacement wine wine1.2 x11-common xorg xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo"


and then while i removed the things you told me to then i reloaded the updates and another error occured with this

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://repo.palatinus.cz](http://repo.palatinus.cz)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5D755BF52031C974
W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
W: GPG error: [http://update.yuuguu.com](http://update.yuuguu.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 483881FD2506E8CC
W: GPG error: [http://www.fbreader.org](http://www.fbreader.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B5FC5445BA702101
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0EE1BF5F3C8E2A7F
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E38FDEE72D75E850
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
W: GPG error: [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43F1DC4F2B8638D0
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 978228591BD3A65C
W: GPG error: [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43F1DC4F2B8638D0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D45DF2E8FC91AE7E
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5E
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F191A5A8844C542
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A16033A9A6FE242
W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF

thanks

---

### Post by germanix on 2010-12-22
OK. So first have a look on the software sources window, both under Ubuntu and others, if any of these sources that are causing the problems (launchpad and others) are to be seen and remove them. Then re-start your computer and try update again. Then come back here.

---

### Post by var1989 on 2010-12-22
Okay 

Done that ! But that didnt work either  still the same error

---

### Post by karthick87 on 2010-12-22
Try this,
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A040830F7FAC5991 5D755BF52031C974 F9A2F76A9D1A0061 483881FD2506E8CC  B5FC5445BA702101  54422A4B98AB5139 7D2C7A23BF810CD5 4874D3686E80C6B7 5A9BF3BB4E5E17B5 0EE1BF5F3C8E2A7F C5E6A5ED249AD24C E38FDEE72D75E850 7FB8BEE0A1F196A8 43F1DC4F2B8638D0 2EBC26B60C5A2783 978228591BD3A65C 43F1DC4F2B8638D0 6E871C4A881574DE 6AF0E1940624A220  D45DF2E8FC91AE7E 71346C8340130828 5A9A06AEF9CB8DB0 6D975C4791E7EE5E 4F191A5A8844C542  5A16033A9A6FE242 A8A515F046D7E7CF
```
```
sudo apt-get update
```

---

### Post by var1989 on 2010-12-22
this is what is showing 


?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
^C
gpg: Interrupt caught ... exiting

thanks

---

### Post by germanix on 2010-12-22
Hi karthich87, thanks for helping with. Any new ideas?
var1989. Are you sure you typed it correctly. Did you copy-paste the code?
Also it seems the connection timed out (took to long) try it again

---

### Post by var1989 on 2010-12-22
I copied the whole thing and pasted as it is and still the same problem ....

---

### Post by sikander3786 on 2010-12-22
We need to see the output of these commands.

```
cat /etc/apt/sources.list
```

```
ls -l /etc/apt/sources.list.d
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

Thanks.

---

### Post by var1989 on 2010-12-22
[FONT=monospace]this is the list

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick universe

###### Ubuntu Update Repos
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates universe

###### Ubuntu Partner Repo

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) maverick main # AWN (Avant Window Navigator) Testing Packages - [http://awn-project.org/](http://awn-project.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) maverick main # Banshee - [https://edge.launchpad.net/~banshee-team](https://edge.launchpad.net/~banshee-team)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb [http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu](http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu) maverick main # DeaDBeeF - [http://deadbeef.sourceforge.net/](http://deadbeef.sourceforge.net/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) maverick main # Deluge BitTorrent - [http://www.deluge-torrent.org/](http://www.deluge-torrent.org/)

## Run this command: wget -q -O - [http://repo.palatinus.cz/repo.key](http://repo.palatinus.cz/repo.key) | sudo apt-key add -
deb [http://repo.palatinus.cz/stable](http://repo.palatinus.cz/stable) / # Esmska - [http://code.google.com/p/esmska/](http://code.google.com/p/esmska/)

## Run this command: [http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc](http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc) -O- | sudo apt-key add -

## Run this command: wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps # GetDeb - [http://www.getdeb.net](http://www.getdeb.net)

## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -

## Run this command: 2. Add the GPG signing key: sudo apt-key adv --keyserver keyserver.quickbuild.pearsoncomputing.net --recv-keys 2B8638D0 
deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu) maverick main # KDE 3.5 (1) - [http://trinity.pearsoncomputing.net/](http://trinity.pearsoncomputing.net/)

## Run this command: 2. Add the GPG signing key: sudo apt-key adv --keyserver keyserver.quickbuild.pearsoncomputing.net --recv-keys 2B8638D0 
deb [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu) maverick main # KDE 3.5 (2) - [http://trinity.pearsoncomputing.net/](http://trinity.pearsoncomputing.net/)

## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D75E850
deb [http://ppa.launchpad.net/pcf/miro-releases/ubuntu](http://ppa.launchpad.net/pcf/miro-releases/ubuntu) maverick main # Miro HD Video Player - [http://www.getmiro.com/](http://www.getmiro.com/)

## Run this command: sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) maverick main # Pidgin - [http://pidgin.im](http://pidgin.im)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1BD3A65C
deb [http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu](http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu) maverick main # Terminator - [http://www.tenshu.net/terminator/](http://www.tenshu.net/terminator/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) maverick main # Themes for GNOME and Ubuntu - [https://edge.launchpad.net/~bisigi/+archive/ppa](https://edge.launchpad.net/~bisigi/+archive/ppa)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) maverick main # Ubuntu Tweak - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) maverick main # UNetbootin - [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

## Run this command: wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) maverick main # VLC Media Player  - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main # Wine - [https://launchpad.net/~ubuntu-wine/+archive/ppa/](https://launchpad.net/~ubuntu-wine/+archive/ppa/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 91E7EE5E
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main # XBMC Media Center - [http://xbmc.org/](http://xbmc.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542  
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) maverick main # Xorg Edgers - [https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)



####### 3rd Party Source Repos

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9A6FE242
deb-src [http://ppa.launchpad.net/ailurus/ppa/ubuntu](http://ppa.launchpad.net/ailurus/ppa/ubuntu) maverick main # Ailurus (Source) - [http://code.google.com/p/ailurus/](http://code.google.com/p/ailurus/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
deb-src [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) maverick main # AWN (Avant Window Navigator) Testing Packages (Source) - [http://awn-project.org/](http://awn-project.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) maverick main # Chromium Project (Source) - [http://code.google.com/chromium/](http://code.google.com/chromium/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb-src [http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu](http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu) maverick main # DeaDBeeF (Source) - [http://deadbeef.sourceforge.net/](http://deadbeef.sourceforge.net/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb-src [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) maverick main # Deluge BitTorrent (Source) - [http://www.deluge-torrent.org/](http://www.deluge-torrent.org/)

## Run this command: [http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc](http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc) -O- | sudo apt-key add -

## Run this command: 2. Add the GPG signing key: sudo apt-key adv --keyserver keyserver.quickbuild.pearsoncomputing.net --recv-keys 2B8638D0 
deb-src [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu) maverick main # KDE 3.5 (1) (Source) - [http://trinity.pearsoncomputing.net/](http://trinity.pearsoncomputing.net/)

## Run this command: 2. Add the GPG signing key: sudo apt-key adv --keyserver keyserver.quickbuild.pearsoncomputing.net --recv-keys 2B8638D0 
deb-src [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu) maverick main # KDE 3.5 (2) (Source) - [http://trinity.pearsoncomputing.net/](http://trinity.pearsoncomputing.net/)

## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D75E850
deb-src [http://ppa.launchpad.net/pcf/miro-releases/ubuntu](http://ppa.launchpad.net/pcf/miro-releases/ubuntu) maverick main # Miro HD Video Player (Source) - [http://www.getmiro.com/](http://www.getmiro.com/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) maverick main # Pidgin (Source) - [http://pidgin.im](http://pidgin.im)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1BD3A65C
deb-src [http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu](http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu) maverick main # Terminator (Source) - [http://www.tenshu.net/terminator/](http://www.tenshu.net/terminator/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) maverick main # Themes for GNOME and Ubuntu (Source) - [https://edge.launchpad.net/~bisigi/+archive/ppa](https://edge.launchpad.net/~bisigi/+archive/ppa)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) maverick main # Ubuntu Tweak (Source) - [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb-src [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) maverick main # UNetbootin (Source) - [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb-src [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) maverick main # VLC Media Player  (Source) - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main # Wine (Source) - [https://launchpad.net/~ubuntu-wine/+archive/ppa/](https://launchpad.net/~ubuntu-wine/+archive/ppa/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 91E7EE5E
deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main # XBMC Media Center (Source) - [http://xbmc.org/](http://xbmc.org/)

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542

then the other output is 


total 12
-rw-r--r-- 1 root root  0 2010-12-22 22:39 am-monkeyd-nautilus-elementary-ppa-maverick.list
-rw-r--r-- 1 root root 85 2010-12-22 22:39 am-monkeyd-nautilus-elementary-ppa-maverick.list.save
-rw-r--r-- 1 root root  0 2010-12-22 22:39 bisigi-ppa-maverick.list
-rw-r--r-- 1 root root 61 2010-12-22 22:39 bisigi-ppa-maverick.list.save
-rw-r--r-- 1 root root  0 2010-12-22 22:39 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root 68 2010-12-22 22:39 tualatrix-ppa-maverick.list.save

[/FONT]

---

### Post by germanix on 2010-12-22
I am at my wits end. I must admit I do not know how to help any further. I did find this "how to"
[http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)
but I do not fully understand it myself and would not want you to try it if you are not comfortable doing it.
There are however a lot of real "experts" on this forum and I hope with you that one of them comes along pretty soon and help to solve this problem.
If it was me and I have my whole "home" backed up and on its own partition, I would just re-install the OS and this time choose my "sources" very carefully and only install software from the "software center" on Ubuntu and not direct from internet sites.
Lets hope a solution is not long in coming.
Should I think of anything else I will be back.

Edit: I see these experts are already here. Hooray. Thanks guys/ladies

---

### Post by sikander3786 on 2010-12-22
No wonder there were so many error messages. You don't need those testing PPAs until you _KNOW_ you need them.

Backup your sources.list.

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
```

Create a new one.

```
gksudo gedit /etc/apt/sources.list
```

Paste this text in that file.

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://in.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse 
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://in.archive.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse 
deb http://in.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse 
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse 
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

```

Save and close and once again, post the output of this command.

```
sudo apt-get update
```

---

### Post by var1989 on 2010-12-22
yes did that ! and output is 

Get:1 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]               
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN
Get:2 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Get:3 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources [3,782B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN
Get:4 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages [6,686B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN                                                                                           
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security Release.gpg [198B]                                                                                                
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                                                                         
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN                                                                                      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en                                                                                   
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN                                                                                
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                                                                                   
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN                                                                                
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                                                                                     
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN                                                                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg                                                                                                          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                                                                                          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN                                                                                       
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en                                                                                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN                                                                                 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en                                                                                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN                                                                                 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security Release [27.2kB]         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release                       
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources [829kB]                                                                                                       
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources [4,370B]                                                                                                
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources [4,179kB]                                                                                                 
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources [151kB]                                                                                                
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main amd64 Packages [1,491kB]                                                                                             
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted amd64 Packages [6,002B]                                                                                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe amd64 Packages                                                                                                      
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse amd64 Packages [180kB]                                                                                         
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/main Sources [16.9kB]                                                                                            
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/restricted Sources [14B]                                                                                         
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/universe Sources [6,295B]                                                                                        
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/multiverse Sources [649B]                                                                                        
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/main amd64 Packages [53.8kB]                                                                                     
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/restricted amd64 Packages [14B]                                                                                  
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/universe amd64 Packages [22.7kB]                                                                                 
Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-security/multiverse amd64 Packages [1,531B]                                                                               
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources [67.9kB]                                                                                             
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources [14B]                                                                                          
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources [21.4kB]                                                                                         
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources [1,068B]                                                                                       
Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main amd64 Packages [187kB]                                                                                       
Get:27 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted amd64 Packages [14B]                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe amd64 Packages                                                                                              
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages [2,382B]                                                                                
Fetched 7,267kB in 1min 27s (83.4kB/s)                                                                                                                                 
Reading package lists... Done

---

### Post by sikander3786 on 2010-12-23
That output tells "All is Well".

If satisfied, please mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by pbvijay on 2011-01-20
Karthick,
Thank you very much...

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  ,,,,,,,

is resolved my issue.

Cheers
Vijay

---

### Post by zot171 on 2011-02-14
i noticed a few sources in your old /etc/apt/sources.list file which may have been causing some problems as well.

[HTML]http://ppa.quickbuild.pearsoncomputing.net[/HTML]

these sources have presented problems for me. i havent been able to obtain any gpg keys and apt-get update does not read from those sources. they are supposed to supply the old KDE 3.5 interface. if you are not interested in this interface, i would suggest not adding these sources.

---

### Post by halfprice on 2011-02-18
> **sikander3786 said:**
> No wonder there were so many error messages. You don't need those testing PPAs until you _KNOW_ you need them.

Backup your sources.list.

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
```Create a new one.

```
gksudo gedit /etc/apt/sources.list
```Paste this text in that file.

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://in.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse 
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://in.archive.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse 
deb http://in.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse 
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse 
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

```Save and close and once again, post the output of this command.

```
sudo apt-get update
```

Solved the same problem for me, thanks very much Sikander

---

### Post by sikander3786 on 2011-02-18
> **halfprice said:**
> Solved the same problem for me, thanks very much Sikander
Welcome to the forums :-)

And happy that you found the fix to your issue.

If some other users come wandering here, instead of copying/pasting the code from above post, please generate a new sources.list with your own Ubuntu release and preferred repositories. See here for a how to.

[http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html](http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html)

---

