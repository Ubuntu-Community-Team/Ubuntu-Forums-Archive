---
title: "How-To: Install and Update Kohan: Immortal Sovereigns on Feisty Fawn"
date: 2007-10-10
forum: Gaming &amp; Leisure
---

### Post by beeldings on 2007-10-10
[i]I would like to thank fellow Ubuntu Forums members [**Footissimo](http://ubuntuforums.org/showthread.php?t=402777)** and **[janga](http://ubuntuforums.org/showthread.php?t=61629)** for their post(s) on installing and updating old Loki Linux titles. I would also like to give credit to the author of [ this web page](http://www.cs.virginia.edu/~kgs3c/kohanlinux.html) for providing additional information on fixing a bug with Kohan. In addition, I extend my sincere thanks to the fine folks at [Tux Games](http://www.tuxgames.com) for providing a stable resource for the Loki patches.

Before we proceed with installing Kohan, make sure your system is up-to-date and that your video drivers are correctly installed.[/i]

First, insert the Kohan disc into your optical drive. If the disc is not mounted automatically, be sure to mount it manually either through Nautilus or in a terminal:

```

mount /dev/hdc

```

If you have more than one optical drive or if you are using an SATA optical drive, please modify */dev/hdc* to correspond to your set-up.

With the Kohan installation disc mounted, proceed to run the installation program. In a terminal execute:

```

cd /cdrom && sudo sh setup.sh

```

The Loki installer should now open. For an optimal installation, proceed to check the boxes for all available install options. When the installation finishes, click 'Exit".

You can now run Kohan from a terminal by executing:

```

kohan

```

***You will be prompted to enter the CD Key when the game is first run. Be sure to have your Kohan manual available for this information.***

At this stage, the game is playable but it is not the latest version. To upgrade Kohan to the latest version, we will need to download two patches. The following steps must be executed in a terminal.

First, download patch 1.2:

```

cd ~/ && wget -c http://lokifiles.tuxgames.com/updates/kohan/kohan-1.2.0-x86.run

```

As is the case with these older patch files, we need to update the patcher before we can properly upgrade Kohan.

```

sh kohan-1.2.0-x86.run --keep

```

This will output an error message to the terminal, this message can be ignored. Now we will want to move to the appropriate directory for proper patching:

```

cd ~/kohan-1.2.0-x86/bin/Linux/x86/

```

The culprit here is the file "loki_patch". Remove it and download a working version:

```

rm loki_patch && wget -c http://icculus.org/~msphil/loki/x86/loki_patch

```

Next, set the permissions of loki_patch to "execute":

```

chmod +x loki_patch

```

Proceed to the directory for the upgrade program and execute the patcher:

```

cd ../../../ && sudo sh update.sh

```

When prompted by the patcher for the Kohan installation directory; simply hit "Enter". Now Kohan should have been upgraded to version 1.2. Next, we are going to upgrade from 1.2 to the final version, 1.3.1.

Switch to your home directory and then proceed to download patch 1.3.1:

```

cd ~/ && wget -c http://lokifiles.tuxgames.com/updates/kohan/kohan-1.3.1-x86.run

```

The updating and installation of patch 1.3.1 is similar to what we did with the 1.2 patch. Extract the necessary files from the archive:

```

sh kohan-1.3.1-x86.run --keep

```

You will receive yet another error message, but this can also be ignored. Now let's switch to the appropriate directory:

```

cd ~/kohan-1.3.1-x86/bin/Linux/x86/

```

Delete the bugged version of loki_patch, download the working version, and change the files permissions to "execute":

```

rm loki_patch && wget -c http://icculus.org/~msphil/loki/x86/loki_patch && chmod +x loki_patch

```

Once the new loki_patch file has been properly set-up, let's proceed to upgrade Kohan to 1.3.1:

```

cd ../../../ && sudo sh update.sh

```

Again, when prompted by the installer for the Kohan installation directory, hit "Enter".

To launch Kohan, simply open a terminal and execute:

```

kohan

```

Alternatively, if you opted for the installer to create menu/desktop shortcuts, under Gnome the menu shortcut will be installed to "Applications > Other > Kohan".

However, if you attempt to run Kohan after updating to the latest version, the game will hang at the loading screen. From the information I retrieved through Google, this is due to the fact that Kohan was compiled with an older version of glibc. To correct this we will need to install a compatible glibc layer. To do this, we will be installing an RPM file. But, since Ubuntu is a Debian-based OS we will need to install a program which will convert the RPM file to a DEB file. In a terminal execute:

```

sudo apt-get install alien

```

To install the glibc file execute:

```

wget ftp://194.199.20.114/linux/redhat/7.3/en/os/i386/RedHat/RPMS/compat-glibc-6.2-2.1.3.2.i386.rpm && sudo alien -i compat-glibc-6.2-2.1.3.2.i386.rpm

```

With that file installed, you should now run Kohan with:

```

LD_LIBRARY_PATH=/usr/i386-glibc21-linux/lib:$LD_LIBRARY_PATH /usr/local/games/kohan/kohan

```

We're almost finished. Some users will notice that the mouse cursor is extremely slow. To correct this simply add "-x" when launching Kohan:

```

LD_LIBRARY_PATH=/usr/i386-glibc21-linux/lib:$LD_LIBRARY_PATH /usr/local/games/kohan/kohan -x

```

The cursor will now operate at a normal speed, but it is now an ugly mess of black & white compared to the default Kohan cursor. I have yet to learn how to correct this problem, so if anyone knows how to fix the mouse cursor, please feel free to post that information. With that out of the way:

:) **Congratulations! You have managed to install and upgrade Kohan: Immortal Sovereigns to the final Linux version.** :)

---

