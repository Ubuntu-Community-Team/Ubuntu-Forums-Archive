---
title: "Install QEMU 0.8 KQEMU 0.7.2 with KQEMU GUI"
date: 2006-03-09
forum: Desktop Environments
---

### Post by adamkane on 2006-03-09
[SIZE=5]Simple install script for QEMU 0.7.2 and KQEMU 0.7.2 and KDE QEMU GUI 0.2

Instructions for QEMU 0.8.0 KQEMU 0.7.2 KDE QEMU GUI 0.3 here:
[http://www.ubuntuforums.org/showthread.php?t=154265]("http://www.ubuntuforums.org/showthread.php?t=154265")
[/SIZE] 
References:

[http://oui.com.br/n/content.php?article.23]("http://oui.com.br/n/content.php?article.23")
[http://www.ubuntuforums.org/showthread.php?t=39513]("http://www.ubuntuforums.org/showthread.php?t=39513")
[http://kqemu.sourceforge.net/]("http://kqemu.sourceforge.net/")

Before you begin, you need to make sure your system is set up correctly.:

```

[COLOR=Black]uname -r
[/COLOR]
``` 

If you have a Pentium PC, the result should be:

> 
2.6.12-10-686
 

If you have an AMD PC, the result shoudl be:

> 
 2.6.12-10-k7
  

If you have an older legacy PC, the results should be:
 
 > 
 2.6.12-10-386
 

If the result matches your system, then continue. Otherwise see **Thread 7**.

 Download the simple QEMU/KQEMU install script and install:

```

cd ~
wget http://oui.com.br/n/e107_files/downloads/insQEMU.sh
sudo chmod +x insQEMU.sh
sudo ./insQEMU.sh

``` 

If you make a mistake, and need to re-start the install script, you must remove the temporary files that were created, and begin again:

```

sudo rm -R /root/qemu-src
sudo ./insQEMU.sh

``` 
If the installation succeeds, do the following to have the kqemu module restart after reboot:

```

sudo modprobe kqemu 
sudo gedit /etc/modules

``` 
Add this line to the end of the file:

```

kqemu

``` 

Save the file and close it.

Now use QEMU to create a virtual hard disc for the new OS:

```

cd ~
mkdir qemu
cd qemu
qemu-img create hd1.img 1000M

``` 
I chose 1000M (1 Gb), but you may need more.

For more options:

```

qemu-img --help

``` 
Install Kommander:
 
 ```

sudo apt-get install kommander

``` 
If you use KDE, download **KDE Qemu GUI 0.2 **to your desktop:
(Don't use version 0.3. Version 0.3 doesn't work with the version of QEMU you've just installed, and was written for multi-processor PCs.)
[http://kqemu.sourceforge.net/]("http://kqemu.sourceforge.net/") 

Extract the files and execute with Kommander:

```

cd ~/Desktop
tar xzf kqemu-0.2.tgz
kmdr-executor kqemu-0.2.kmdr

``` 

If you use, Gnome, I've translated the KDE Qemu GUI  to Gnome. 

To translate to Gnome I replaced the kdialog command with the zenity command. 

For example:
kdialog --msgbox "File saved."  ->  zenity --info --text "File saved."

(There was no reason why the author of KQemu GUI had to use kdialog, when he could have easily used zenity. Very frustrating.)

The Gnome script is located at the end of this post. Download it to your desktop, extract it, then execute it:

```

cd ~/Desktop
gzip -d kqemu-0.2-gnome.gz
kmdr-executor kqemu-0.2-gnome.kmdr

``` 
**KDE Qemu GUI:**
Now that you have the KQEmu GUI open, go to the disks tab, find HDA, and browse to the virtual hard disk image, hd1.img. 

Check the **enable CDROM** button. If your installation CD is a CDROM image, then browse to the image. Select d: as your boot drive. Select USER Mode networking.

With the KQEmu GUI, you have the option of creating a startup script for your new OS with the SAVE button.

Press the play button to begin the installation of the new OS.

If you are directly connected to the internet, and don't use a router, then you may prefer to set up bridged networking to access the internet and network with your host. Start at step 6 here:
[http://www.ubuntuforums.org/showthread.php?t=66694]("http://www.ubuntuforums.org/showthread.php?t=66694")

---

### Post by alancaerdydd on 2006-03-26
Hi, this looks like just what I need as I have a couple of windows progs which I need access to whilst evaluating other alternatives. My only other alternative was using a copy of vmware 4 (used to run fine on redhat 7.0) but on ubuntu leads me into all sorts of kernel compilation issues, the thread was over 350 posts... and I'm not a comp scientist!

However when I tried your script I got the following error message


Loading the KQEMU kernel module...
cp: cannot stat `kqemu/kqemu.ko': No such file or directory
FATAL: Module kqemu not found.

tried to find kqemu via synaptic and nothing showed up. Found it on sourceforge as a tar archive so downloaded that but can't find any documentation. tar zxf etc gives me a file in the same directory kqemu.kmdr but no scripts or read me files...

bit stuck at this point! hope you can help

Alan

---

### Post by Toxicity999 on 2006-03-26
I assume if you follow the direction to the letter the kmdr-executor is a binary that's installed. Infact, if you read at the bottom, the poster instructs you to execute this file using what I mentions =P Of course I haven't gotten there. and probably won't use the GUI extension thang. (you don't 'need' it, it's handy sure but goto a post like [http://ubuntuforums.org/showthread.php?t=39513]("http://ubuntuforums.org/showthread.php?t=39513") just trim off everything about the graphical extention and follow this guide's last few bits on installing Windows into QEmu running and etc all by commandline! It's really not that hard just a few drop in replacements =) I recommend using your install cd rather then an ISO rip if possible so you dont need a boot image or anything. Good luck.)

Also! If you want to try the easier way of this first... Install WINE! Basically its a compatibility layer (windows to linux naturally.)
Simply follow this for a basic installation of WINE:

1)Open a command prompt and enter:
sudo gedit /apt/sources.list

2)Goto the bottom and skip a few lines (just so you'll know what you added if forever reason you want to revert.)

There Enter:
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

Now, all this does is allow Apt to reference a new repository (storing WINE in this case.)

Save this and close.

3) Run sudo apt-get update

4)Wait for the list update to complete and enter:
sudo apt-get install wine

5)now run winecfg

6)now anythign you want to try to run just enter wine "path to exec." (You want to leave the quotes in place as generally windows applications are stored in Program files, the quotes make sure the entire string is interpreted.)

If you aren't a new user sorry if that came of, well y'know. Just trying to help, Wish you luck. (If QEmu and wine arent to your tastes read up on using VMware might suite better.)

---

### Post by adamkane on 2006-03-27
alancaerdydd:

The whole point of the insQEMU.sh installation script is to install QEMU and KQEMU at the **same time**. If you install QEMU first, and then KQEMU second, you won't receive any of the KQEMU speed benefits.

For most people, the insQEMU.sh script will work, but if you have an AMD computer, you'll get the following error:

> 
 Loading the KQEMU kernel module...
 cp: cannot stat `kqemu/kqemu.ko': No such file or directory
 FATAL: Module kqemu not found.
 
You need to edit the insQEMU.sh script the way I described, and then run the insQEMU.sh script again. 

The problem is that you are missing the linux-headers-k7 package for AMD computers. The insQEMU.sh installation script will try to install the linux-headers-686 package, which is only for Pentium computers. Without the correct headers, you can't create the kemu.ko module.

Alternatives to QEMU/KQEMU:

Wine is buggy still, and is mostly used by gamers. I put together a list of applications reported to work with Ubuntu and Wine:
[http://www.ubuntuforums.org/showthread.php?t=150352]("http://www.ubuntuforums.org/showthread.php?t=150352")

You can try to install the VMWare Player, if you can't get VMWare Workstation to work. VMWare Player won't let you create virtual PCs, but there are HOWTOs, that show you how to create virtual PCs with QEMU and a text editor:
[http://www.ubuntuforums.org/showthread.php?t=84275]("http://www.ubuntuforums.org/showthread.php?t=84275")

Here is a commercial product similiar to VMWare:
[http://www.parallels.com/]("http://www.parallels.com/")

There are live XEN and QEMU distributions, that run from a CD:
[http://www.cl.cam.ac.uk/Research/SRG/netos/xen/downloads.html]("http://www.cl.cam.ac.uk/Research/SRG/netos/xen/downloads.html")
[http://mirror.clarkson.edu/pub/distributions/xenophilia/xen-cd/]("http://mirror.clarkson.edu/pub/distributions/xenophilia/xen-cd/")
[http://www.zzine.org/articles/slax]("http://www.zzine.org/articles/slax")
[http://cyti.latgola.lv/ruuni/index_en.html]("http://cyti.latgola.lv/ruuni/index_en.html")
and others.

For those, who can't commit to Linux, you can install Linux on Windows without VMWare:
[http://www.colinux.org/]("http://www.colinux.org/")
[http://www.willmer.com/kb/2005/07/colinux-for-ubuntu/]("http://www.willmer.com/kb/2005/07/colinux-for-ubuntu/")

---

### Post by alancaerdydd on 2006-03-27
Well very many thanks for your very detailed replies, there's a considerable amount to read through and this will take me a few weeks, indeed many of these threads and solutions I have already read through and got some progs to work not others. Whilst I am not a beginner neither am I an expert linux user, it takes me most of my time being a good medical scientist.

As far as I know I do not have an AMD computer and I did uninstall qemu before running the script but will try again. 

I did however follow the written instructions sequentially, a habit born of thirty years in medical research. I'm afraid it did come across that way toxicity though I accept the apology.  I find one of the principal problems I face using linux is being patronised by experts who assume I am able to acquire as much knowledge as they do.

I shall continue my search for solutions.

Many Thanks

---

### Post by adamkane on 2006-03-27
Point well taken about toxicity. It's difficult to make a point without becoming overbearing. I've noticed as well that there are only a few forum posters that are both courteous and knowledgeable. I have a lot to learn.

I think most of us are waiting for Xen to become finished and installable on Ubuntu. It will probably replace QEMU over the next year or two.

For now, I would recommend the Windows XP with VMWare Player solution:
[http://www.ubuntuforums.org/showthread.php?t=84275]("http://www.ubuntuforums.org/showthread.php?t=84275")

---

### Post by adamkane on 2006-03-31
So Ubuntu didn't recognize your motherboard correctly, or you have already received the "can't stat kqemu.ko" error. If you continue, there is a chance you won't be able to boot into your system again, so please have a backup plan in place before you continue.

If the result of the following didn't match your system:

 ```

uname -r

``` 

then you have to install some motherboard-dependent packages and execute a modified insQEMU.sh script.

If you have a Pentium PC:

```

sudo apt-get install linux-686 linux-headers-686 linux-image-686 linux-restricted-modules-686

``` 
If you have an AMD PC:

```

sudo apt-get install linux-k7 linux-headers-k7 linux-image-k7 linux-restricted-modules-k7

``` 
Reboot to take advantage of the packages you've just installed, then continue to the next step.
 
After youv've rebooted, do this again, and make sure it matches your system:

```

uname -r

``` 

Create a new insQEMU.sh script, then install:

```

cd ~/Desktop
gedit insQEMU.sh

``` 

Enter fhe following code, if you have a Pentium PC:

```

#!/bin/sh
#
# How to write a shell script
# http://vertigo.hsrl.rutgers.edu/ug/shell_help.html
#

# Script configuration
# ====================
  BASE_DIR=/root
# BASE_DIR=/usr/local
# BASE_DIR=/tmp
    SRC_DIR=qemu-src
    QEMUVERSION=0.7.2
    PKGSOURCE=http://fabrice.bellard.free.fr/qemu/qemu-${QEMUVERSION}.tar.gz
        KERNEL=686

# Script starts executing here
# ============================
echo
echo "InsQEMU - version 0.1 (2005-12-15)"
echo "======= by Nando Florestan -- http://oui.com.br/n"
echo "This script downloads and installs QEMU ${QEMUVERSION},"
echo "with the KQEMU accellerator, in Ubuntu 5.10 Breezy Badger."
echo "Based on:"
echo "http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation"
echo
echo "If this script succeeds, you will see a message at the end saying:"
echo "\"InsQEMU SUCCEEDED!\""
echo "...else you have some problem."
echo
echo "If you have any difficulties, you can edit the script yourself."
echo "It is heavily commented so as to help."
echo "Please send any bug corrections to nandoflorestan@gmail.com"
echo

if [ $USER != "root" -o $UID != 0 ]; then
    echo "This script must be run as root. Type this to become root:"
    echo "sudo -s"
    echo "...then run this script again."
    echo
    exit 1
fi

echo "First of all, we install the dependencies."
# Ubuntu Breezy 5.10 and Debian Sid come with GCC 4.0 by default, but
# Qemu 0.72 will not compile with GCC 4.0 so we need to install GCC 3.4
# The SDL packages should provide sound support
# zlib is a compression library
# checkinstall is for generating .deb packages
apt-get install gcc-3.4 g++-3.4 libsdl1.2debian libsdl1.2debian-all build-essential libsdl1.2-dev zlib1g-dev || exit 2

echo


cd   ${BASE_DIR} || exit 3
mkdir ${SRC_DIR} || echo
cd    ${SRC_DIR} || exit 4
echo

# If the directory does NOT exist yet
if [ ! -d qemu-${QEMUVERSION}/kqemu ]; then
    echo "Downloading QEMU..."
    wget -nv ${PKGSOURCE}  || exit 5
    echo
    echo "Downloading KQEMU..."
    wget -nv http://fabrice.bellard.free.fr/qemu/kqemu-${QEMUVERSION}.tar.gz || exit 6
    echo
    echo "Uncompressing QEMU..."
    tar zxvf qemu-${QEMUVERSION}.tar.gz     || exit 7
    echo
    echo "Entering source dir."
    cd qemu-${QEMUVERSION}                  || exit 8
    echo
    echo "Uncompressing KQEMU..."
    tar zxvf ../kqemu-${QEMUVERSION}.tar.gz || exit 9
else
    echo "Directory already exists: ${BASE_DIR}/qemu-src/qemu-${QEMUVERSION}"
    echo "I will use its files instead of downloading them from the internet."
    cd qemu-${QEMUVERSION}
fi

echo "BEGINNING CONFIGURE !"
# sh configure  || exit 13
export CPP=g++-3.4
export CC=gcc-3.4
sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/usr/src/linux-headers-$(uname -r)/ || exit 13
echo
echo

echo "BUILDING QEMU !"
# In Ubuntu Breezy, if you just `make`, it will use GCC 4.0
# even though we configured for GCC 3.4. So we need this workaround:
# Change the symlink, compile, then change the symlink back
mv     /usr/bin/gcc     /usr/bin/gcc.bak
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
make
EXITCODE=$?
mv     /usr/bin/gcc.bak /usr/bin/gcc
echo

if [ $EXITCODE != 0 ]; then
    echo "PROBLEM IN MAKE: ${EXITCODE}"
    exit 14
fi

echo "Now let us remove Qemu if it is installed..."
apt-get remove qemu  || exit 15
echo

# Now make the PACKAGE. Using checkinstall is a great way to
# install applications because it makes '.deb' packages.
# This means Qemu can later be removed via apt-get or Synaptic.
echo "QEMU is a generic processor emulator. This package was compiled by InstQEMU.sh and also contains the KQEMU accellerator. http://fabrice.bellard.free.fr/qemu" > description-pak || exit 16
# The reason for overwriting install.sh so it is empty is
# to ensure the package made with checkinstall can install cleanly
cat /dev/null > kqemu/install.sh                || exit 17
# Create the .deb package
checkinstall -y --pkgname=qemu --pkgversion=${QEMUVERSION} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=$PKGSOURCE --exclude=kqemu/install.sh           || exit 18

echo "QEMU is now installed."
echo
echo "Loading the KQEMU kernel module..."
mkdir -p /lib/modules/2.6.12-10-686/misc && cp kqemu/kqemu.ko /lib/modules/2.6.12-10-686/misc && depmod -a
modprobe kqemu           || exit 19 # Load the kernel module
mknod /dev/kqemu c 250 0 || exit 20 # Create the KQEMU device
chmod 666 /dev/kqemu     || exit 21 # Make it accessible to all users    
echo

echo "When you reboot, the KQEMU accellerator will not load anymore."
echo "But you can add a few lines to a boot script to fix this."
echo "For more details, please refer to:"
echo "http://fabrice.bellard.free.fr/qemu/kqemu-doc.html"
echo
echo "InsQEMU SUCCEEDED!"
exit 0

``` 
Close the file and save it:

If you have an AMD PC, enter the following code ino the insQEMU.sh file:

```

#!/bin/sh
#
# How to write a shell script
# http://vertigo.hsrl.rutgers.edu/ug/shell_help.html
#

# Script configuration
# ====================
  BASE_DIR=/root
# BASE_DIR=/usr/local
# BASE_DIR=/tmp
    SRC_DIR=qemu-src
    QEMUVERSION=0.7.2
    PKGSOURCE=http://fabrice.bellard.free.fr/qemu/qemu-${QEMUVERSION}.tar.gz

# Script starts executing here
# ============================
echo
echo "InsQEMU - version 0.1 (2005-12-15)"
echo "======= by Nando Florestan -- http://oui.com.br/n"
echo "This script downloads and installs QEMU ${QEMUVERSION},"
echo "with the KQEMU accellerator, in Ubuntu 5.10 Breezy Badger."
echo "Based on:"
echo "http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation"
echo
echo "If this script succeeds, you will see a message at the end saying:"
echo "\"InsQEMU SUCCEEDED!\""
echo "...else you have some problem."
echo
echo "If you have any difficulties, you can edit the script yourself."
echo "It is heavily commented so as to help."
echo "Please send any bug corrections to nandoflorestan@gmail.com"
echo

if [ $USER != "root" -o $UID != 0 ]; then
    echo "This script must be run as root. Type this to become root:"
    echo "sudo -s"
    echo "...then run this script again."
    echo
    exit 1
fi

echo "First of all, we install the dependencies."
# Ubuntu Breezy 5.10 and Debian Sid come with GCC 4.0 by default, but
# Qemu 0.72 will not compile with GCC 4.0 so we need to install GCC 3.4
# The SDL packages should provide sound support
# zlib is a compression library
# checkinstall is for generating .deb packages
apt-get install gcc-3.4 g++-3.4 libsdl1.2debian libsdl1.2debian-all build-essential libsdl1.2-dev zlib1g-dev || exit 2

echo

cd   ${BASE_DIR} || exit 3
mkdir ${SRC_DIR} || echo
cd    ${SRC_DIR} || exit 4
echo

# If the directory does NOT exist yet
if [ ! -d qemu-${QEMUVERSION}/kqemu ]; then
    echo "Downloading QEMU..."
    wget -nv ${PKGSOURCE}  || exit 5
    echo
    echo "Downloading KQEMU..."
    wget -nv http://fabrice.bellard.free.fr/qemu/kqemu-${QEMUVERSION}.tar.gz || exit 6
    echo
    echo "Uncompressing QEMU..."
    tar zxvf qemu-${QEMUVERSION}.tar.gz     || exit 7
    echo
    echo "Entering source dir."
    cd qemu-${QEMUVERSION}                  || exit 8
    echo
    echo "Uncompressing KQEMU..."
    tar zxvf ../kqemu-${QEMUVERSION}.tar.gz || exit 9
else
    echo "Directory already exists: ${BASE_DIR}/qemu-src/qemu-${QEMUVERSION}"
    echo "I will use its files instead of downloading them from the internet."
    cd qemu-${QEMUVERSION}
fi

echo "BEGINNING CONFIGURE !"
# sh configure  || exit 13
export CPP=g++-3.4
export CC=gcc-3.4
sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/usr/src/linux-headers-$(uname -r)/ || exit 13
echo
echo

echo "BUILDING QEMU !"
# In Ubuntu Breezy, if you just `make`, it will use GCC 4.0
# even though we configured for GCC 3.4. So we need this workaround:
# Change the symlink, compile, then change the symlink back
mv     /usr/bin/gcc     /usr/bin/gcc.bak
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
make
EXITCODE=$?
mv     /usr/bin/gcc.bak /usr/bin/gcc
echo

if [ $EXITCODE != 0 ]; then
    echo "PROBLEM IN MAKE: ${EXITCODE}"
    exit 14
fi

echo "Now let us remove Qemu if it is installed..."
apt-get remove qemu  || exit 15
echo

# Now make the PACKAGE. Using checkinstall is a great way to
# install applications because it makes '.deb' packages.
# This means Qemu can later be removed via apt-get or Synaptic.
echo "QEMU is a generic processor emulator. This package was compiled by InstQEMU.sh and also contains the KQEMU accellerator. http://fabrice.bellard.free.fr/qemu" > description-pak || exit 16
# The reason for overwriting install.sh so it is empty is
# to ensure the package made with checkinstall can install cleanly
cat /dev/null > kqemu/install.sh                || exit 17
# Create the .deb package
checkinstall -y --pkgname=qemu --pkgversion=${QEMUVERSION} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=$PKGSOURCE --exclude=kqemu/install.sh           || exit 18

echo "QEMU is now installed."
echo
echo "Loading the KQEMU kernel module..."
mkdir -p /lib/modules/2.6.12-10-k7/misc && cp kqemu/kqemu.ko /lib/modules/2.6.12-10-k7/misc && depmod -a
modprobe kqemu           || exit 19 # Load the kernel module
mknod /dev/kqemu c 250 0 || exit 20 # Create the KQEMU device
chmod 666 /dev/kqemu     || exit 21 # Make it accessible to all users    
echo

echo "When you reboot, the KQEMU accellerator will not load anymore."
echo "But you can add a few lines to a boot script to fix this."
echo "For more details, please refer to:"
echo "http://fabrice.bellard.free.fr/qemu/kqemu-doc.html"
echo
echo "InsQEMU SUCCEEDED!"
exit 0

``` 

Save the file and close it.

Go back to **Thread 1** to continue the installation at the line that says:
```

sudo chmod +x insQEMU.sh

```

---

### Post by alancaerdydd on 2006-04-01
Many thanks for this update adamkane. You were correct, results of uname -r and -m  were inconsistent. Followed your new instructions and the script ran perfectly. This should allow me to keep the two windows progs I need until good alternatives become available. Very very many thanks.

Alan

---

### Post by lex1 on 2006-04-01
have a router and static ip so makes a diffrenceI sent you a message.

many many thanks for your how to well done 

lex1

Alex:cool: :cool: :cool:

---

### Post by art2003 on 2006-04-02
Hello I run a custom kernel as I work with embedded systems and need support for squashfs with lzma

So modprobe kqemu.ko results in:
FATAL: Module kqemu.ko not found.

uname -r
2.6.15-archck7
 uname -m
i686

This is an Athlon XP pc

If I do locate bt878.ko

/usr/src/linux-2.6.15archck7/drivers/media/dvb/bt8xx/bt878.ko
/usr/src/linux-2.6.15archck7/drivers/media/dvb/bt8xx/.bt878.ko.cmd
/usr/src/linux-2.6.15.4/drivers/media/dvb/bt8xx/bt878.ko
/usr/src/linux-2.6.15.4/drivers/media/dvb/bt8xx/.bt878.ko.cmd
/lib/modules/2.6.15-archck7/kernel/drivers/media/dvb/bt8xx/bt878.ko
/lib/modules/2.6.12-10-k7/kernel/drivers/media/dvb/bt8xx/bt878.ko

---

### Post by Olivier olejniczak on 2006-07-03
The install script (insQemu.sh) that did it for me (dapper on kernel 2.6.15-25-k7)

=====================================


#!/bin/sh
#
# How to write a shell script
# [http://vertigo.hsrl.rutgers.edu/ug/shell_help.html](http://vertigo.hsrl.rutgers.edu/ug/shell_help.html)
#

# Script configuration
# ====================
BASE_DIR=/root
# BASE_DIR=/usr/local
# BASE_DIR=/tmp
SRC_DIR=qemu-src
QEMUVERSION=0.8.1
KQEMUVERSION=1.3.0pre7
PKGSOURCE=http://fabrice.bellard.free.fr/qemu/qemu-${QEMUVERSION}.tar.gz

echo "Now let us remove Qemu if it is installed..."
apt-get -y remove qemu || exit 15



# Script starts executing here
# ============================
echo
echo "InsQEMU - version 0.1 (2005-12-15)"
echo "======= by Nando Florestan -- http://oui.com.br/n"
echo "This script downloads and installs QEMU ${QEMUVERSION},"
echo "with the KQEMU accellerator, verions ${KQEMUVERSION} in Ubuntu 6.04 Dapper Drake."
echo "Based on:"
echo "http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation"
echo
echo "If this script succeeds, you will see a message at the end saying:"
echo "\"InsQEMU SUCCEEDED!\""
echo "...else you have some problem."
echo
echo "If you have any difficulties, you can edit the script yourself."
echo "It is heavily commented so as to help."
echo "Please send any bug corrections to [email]nandoflorestan@gmail.com[/email]"
echo

if [ $USER != "root" -o $UID != 0 ]; then
echo "This script must be run as root. Type this to become root:"
echo "sudo -s"
echo "...then run this script again."
echo
exit 1
fi

echo "First of all, we install the dependencies."
# Ubuntu Dapper comes with GCC 4.0 by default, but
# Qemu 0.72 will not compile with GCC 4.0 so we need to install GCC 3.4
# The SDL packages should provide sound support
# zlib is a compression library
# checkinstall is for generating .deb packages
apt-get install gcc-4.0 g++-4.0 gcc-3.4 g++-3.4 libsdl1.2debian libsdl1.2debian-all build-essential libsdl1.2-dev zlib1g-dev checkinstall || exit 2

echo
echo "Finding out whether your kernel is i386 or i686 or k7."
# Run "uname -m" and store the result in the variable KERNEL
KERNEL=`uname -m` || exit 10
KERNELK7=`uname -r | grep "k7$"`

# Depending on KERNEL, get a package
if [ $KERNELK7 ]; then
echo "Downloading Linux headers for k7..."
apt-get install linux-headers-k7 || exit 11
elif [ $KERNEL == "i686" ]; then
echo "Downloading Linux headers for i686..."
apt-get install linux-headers-686 || exit 11
elif [ $KERNEL == "i386" ]; then
echo "Downloading Linux headers for i386..."
apt-get install linux-headers-386 || exit 12
fi
echo

cd ${BASE_DIR} || exit 3
mkdir ${SRC_DIR} || echo
cd ${SRC_DIR} || exit 4
echo

# If the directory does NOT exist yet
if [ ! -d qemu-${QEMUVERSION}/kqemu ]; then
echo "Downloading QEMU..."
wget -nv ${PKGSOURCE} || exit 5
echo
echo "Downloading KQEMU..."
wget -nv http://fabrice.bellard.free.fr/qemu/kqemu-${KQEMUVERSION}.tar.gz || exit 6
echo
echo "Uncompressing QEMU..."
tar zxvf qemu-${QEMUVERSION}.tar.gz || exit 7
echo
echo "Entering source dir."
cd qemu-${QEMUVERSION} || exit 8
echo
echo "Uncompressing KQEMU..."
tar zxvf ../kqemu-${KQEMUVERSION}.tar.gz || exit 9
else
echo "Directory already exists: ${BASE_DIR}/qemu-src/qemu-${QEMUVERSION}"
echo "I will use its files instead of downloading them from the internet."
cd qemu-${QEMUVERSION}
fi

echo "BEGINNING CONFIGURE !"
# sh configure || exit 13
export CPP=g++-3.4
export CC=gcc-3.4
sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/usr/src/linux-headers-$(uname -r)/ || exit 13
echo
echo

echo "BUILDING QEMU !"
# In Ubuntu Breezy, if you just `make`, it will use GCC 4.0
# even though we configured for GCC 3.4. So we need this workaround:
# Change the symlink, compile, then change the symlink back
mv /usr/bin/gcc /usr/bin/gcc.bak
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
make
EXITCODE=$?
echo

if [ $EXITCODE != 0 ]; then
echo "PROBLEM IN QEMU MAKE: ${EXITCODE}"
exit 14
fi

mv /usr/bin/gcc.bak /usr/bin/gcc


export CPP=g++-4.0
export CC=gcc-4.0
cd kqemu-${KQEMUVERSION}
sh ./configure --prefix=/usr --cc=gcc-4.0 --host-cc=gcc-4.0 --kernel-path=/usr/src/linux-headers-$(uname -r)/ || exit 13
echo
echo
echo "BUILDING KQEMU !"

mv /usr/bin/gcc /usr/bin/gcc.bak
ln -sf /usr/bin/gcc-4.0 /usr/bin/gcc
make
cd ..
EXITCODE=$?
echo

if [ $EXITCODE != 0 ]; then
echo "PROBLEM IN KQEMU MAKE: ${EXITCODE}"
exit 14
fi


echo

# Now make the PACKAGE. Using checkinstall is a great way to
# install applications because it makes '.deb' packages.
# This means Qemu can later be removed via apt-get or Synaptic.
echo "QEMU is a generic processor emulator. This package was compiled by InstQEMU.sh and also contains the KQEMU accellerator. http://fabrice.bellard.free.fr/qemu" > description-pak || exit 16
# The reason for overwriting install.sh so it is empty is
# to ensure the package made with checkinstall can install cleanly
cat /dev/null > kqemu-${KQEMUVERSION}/install.sh || exit 17
# Create the .deb package
checkinstall -y --pkgname=qemu --pkgversion=${QEMUVERSION} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=$PKGSOURCE --exclude=kqemu/install.sh || exit 18

echo "QEMU is now installed."
echo
echo "Loading the KQEMU kernel module..."
mkdir -p /lib/modules/$(uname -r)/misc && cp kqemu-${KQEMUVERSION}/kqemu.ko /lib/modules/$(uname -r)/misc && depmod -a
modprobe kqemu || exit 19 # Load the kernel module
mknod /dev/kqemu c 250 0 || exit 20 # Create the KQEMU device
chmod 666 /dev/kqemu || exit 21 # Make it accessible to all users
echo

echo "When you reboot, the KQEMU accellerator will not load anymore."
echo "But you can add a few lines to a boot script to fix this."
echo "For more details, please refer to:"
echo "http://fabrice.bellard.free.fr/qemu/kqemu-doc.html"
echo
echo "InsQEMU SUCCEEDED!"
exit 0

=====================================

the run scrip i use to install win98 (win98.sh)

=====================================
sudo umount /dev/shm
sudo mount -t tmpfs -o size=144m none /dev/shm
sudo modprobe kqemu
sudo mknod /dev/kqemu c 250 0
sudo chmod 666 /dev/kqemu
sudo qemu -boot d -hda win98.img -cdrom WINDOWS_98.iso

=====================================

---

### Post by adamkane on 2006-07-24
This page was written for breezy. I haven't updated it for dapper yet.

---

### Post by djohnjimmy on 2006-07-28
Hey,

I can never thank you enough for this script... Man, you saved me alotttt of trouble and frustration....

You have no idea how much I appreciate your work... Great work dude...

Keep up the good work... 

Man... YOU ROCK!!!

Thanks again,
John

---

### Post by adamkane on 2006-07-29
Much appreciated. It's not really my code though. I took someone else's code, and hopefully made it a bit easier to use. 

The goal is to show everyone how to use code to make Ubuntu do what you want.

---

### Post by moma on 2006-07-29
Hello,

I wrote a shell-script that installs the latest QEMU and KQEMU accelerator.
You can find it here
[http://www.futuredesktop.net/script-of-moma.html]("http://www.futuredesktop.net/script-of-moma.html")

The script will propably fail to install linux-source (or linux-headers) because you (art2003) do not run a standard kernel from Ubuntu's repo. Your kernel is  2.6.15-archck7.  So I suggest that you open the script file and run the steps 5) and 6) manually. Other Ubuntu-users can run the script as is.

---

### Post by adamkane on 2006-07-30
The whole of point of this thread is to help people install QEMU/KQEMU on non-Intel architecture.

Hopefully the original author of the script will create a working script that will install on both Intel and AMD systems, and I can finally retire this thread.

The point of this thread is to also point out that there is a handy KQEMU Kommander script that further automates the loading of OS images, so that users will not have to use the terminal with QEMU.

---

