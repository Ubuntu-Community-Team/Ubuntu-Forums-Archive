---
title: "Can't play nwn"
date: 2006-03-24
forum: Gaming &amp; Leisure
---

### Post by althepcman on 2006-03-24
Hi all,

I am running dapper drake and when I install nwn and try and run it it gives me the following error:
```
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/username/.kde/socket-localhost.
can't create mcop directory
```

---

### Post by althepcman on 2006-03-31
Can anyone help

---

### Post by Zeroedout on 2006-03-31
Did, you try launching it from anything else besides KDE? seems like a KDE error, however, you need to be able to write to the directry where nwn is installed. If you installed it anywhere else besides /home/username/  launch it with sudo nwn, or gksudo nwn.

---

### Post by althepcman on 2006-04-01
[QUOTE=Zeroedout]Did, you try launching it from anything else besides KDE? seems like a KDE error, however, you need to be able to write to the directry where nwn is installed. If you installed it anywhere else besides /home/username/  launch it with sudo nwn, or gksudo nwn.[/QUOTE]

I am trying to launch the game in gnome, should I try doing it from kde?
I use sudo and I get the follwing:
Creating link /root/.kde/socket-localhost.
can't create mco8&#65533;|&#65533;8&#65533;&#65533;&#65533;p directory

---

### Post by Zeroedout on 2006-04-01
damn, i'm totally stumped. Why would a program launched from gnome use anything in a .kde directry? I don't belive nwn uses anything from KDE or even from the QT libraries, however i could be wrong. Did you try asking in the dapper forums? It's still not stable, so it may be a problem with a dapper sepefic package. Otherwise, if it is safe to do so, perhaps try updating dapper? Worse comes to worse, completly purge KDE from your system, or if you're a little daring, delete the .kde directry, though I have no idea how that would effect kde as i have no idea how it works. It works perfectly with me, but I installed it to /usr/local/games .  I launch with sudo as well.

---

### Post by adamkane on 2006-04-01
You should describe how you installed nwn.

---

### Post by althepcman on 2006-04-01
[QUOTE=adamkane]You should describe how you installed nwn.[/QUOTE]
I di it a very simple way. 
I downloaded the installer on this page:
[http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)

I did the following:
sudo nwn_129_final.run

When it prompted me for the next CD, I ejected the on in the tray and put the one in that is specifed.

I have winex install, should I remove it.

I found a kde package installed, that I didn't think I had installed. I removed it. I will se what happens now. :)

---

### Post by althepcman on 2006-04-01
It did the same thing on ubuntu thats why I updated to try to see if it would work.

---

### Post by Zeroedout on 2006-04-02
You're not using those installlers for the platinum edition, are you?

---

### Post by althepcman on 2006-04-02
[QUOTE=Zeroedout]You're not using those installlers for the platinum edition, are you?[/QUOTE]
No, this is just for Never Winter Nights and no Expansions. :)

---

### Post by Zeroedout on 2006-04-03
[quote=althepcman]No, this is just for Never Winter Nights and no Expansions. :)[/quote]

hrmm, so you're using the right installer, and it installed with no errors. You're launching it with sudo, so it should have no problem writing to directries. By all logic, it should work. The error you posted is a problem with mcop, but are all other applications working fine? Have you tried playing other 3d games to make sure your video card drivers were installed? Though these wont adress the mcop issue, it's strange that it's stoping the game from starting. Usually you'll just get no sound. Try, ```
 killall artsd 
``` if that doesn't work, completly purge all KDE packages from your system.

---

### Post by Belibem on 2006-04-10
I have the same problem when I try to access the audio tab in winecfg. I'm also using gnome but have kdesktop package installed. There definitely seems to be a bug.

---

### Post by vayde on 2006-06-15
Nwn ran perfectly (in fact better than it did under windows) until I upgraded the kernel this morning.  Now Im getting the mcop error.

'killall artsd' does nothing, as it's not running.

Did anyone find a solution?

EDIT:  Fixed it, just needed to do the following:
mkdir ~/.kde/socket-<hostname>

works now

---

### Post by weasel fierce on 2006-06-26
[QUOTE=vayde]Nwn ran perfectly (in fact better than it did under windows) until I upgraded the kernel this morning.  Now Im getting the mcop error.

'killall artsd' does nothing, as it's not running.

Did anyone find a solution?

EDIT:  Fixed it, just needed to do the following:
mkdir ~/.kde/socket-<hostname>

works now[/QUOTE]

I am getting the same error. What should I put instead of <hostname> ? My home directory name or ?

---

### Post by sidefx on 2006-06-27
I assume <hostname> should be whatever cat /etc/hostname outputs.

Might be easiest to do: mkdir ~/.kde/socket-$(cat /etc/hostname)

---

### Post by sidefx on 2006-06-27
BTW, if that still doesn't work, you might try the steps here:

[http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72)

They solved my problems when I first tried NWN on ubuntu. HTH.

---

### Post by mlind on 2006-06-27
I hope none of you are trying to run it using wine, because it works natively.

I've installed nwn twice with all expansion, using the official instructions
[http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)

those work fine.

---

### Post by michaeljb2005 on 2006-06-27
[QUOTE=sidefx]I assume <hostname> should be whatever cat /etc/hostname outputs.

Might be easiest to do: mkdir ~/.kde/socket-$(cat /etc/hostname)[/QUOTE]

I had the exact same problem as you and this person is correct.  Creating the directory it's asking for is the thing to do.

---

### Post by weasel fierce on 2006-06-27
executing the mkdir command gives me a message that the file already exists

---

### Post by pharmd24 on 2006-08-01
> **vayde said:**
> Nwn ran perfectly (in fact better than it did under windows) until I upgraded the kernel this morning.  Now Im getting the mcop error.

'killall artsd' does nothing, as it's not running.

Did anyone find a solution?

EDIT:  Fixed it, just needed to do the following:
mkdir ~/.kde/socket-<hostname>

works now

That fixed it for me too.

Thanks

---

### Post by Urbandale on 2007-12-26
```
kim@kim-desktop:~$ cd NwN
kim@kim-desktop:~/NwN$ ./nwn
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/kim/.kde/socket-kim-desktop.
can't create mcop directory
kim@kim-desktop:~/NwN$ mkdir ~/.kde/socket-kim-desktop
kim@kim-desktop:~/NwN$ ./nwn
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Failed to initialize graphics.
Aborted (core dumped)

```

:(

I tried... Anyone have any suggestions? I used Galpin's Installer script, posted below, if that helps.

```
#!/bin/sh
# Neverwinter Nights installer
# Written by Morgan Galpin
# date: November 1, 2004
# original file name: install-nwn.sh
#---------------------------------------------------------------------
# This script installs Neverwinter Nights Platinum from the CDs.
# It also applies the current hotu patch, which can be obtained from
# the Bioware website. The orginal game plus both expansion packs
# are installed since that seems to be the point of buying the
# Platinum version.
# 
# Instructions:
# 
# Make sure you meet the few requirements below, set the 
# configuration parameters, then at a shell prompt, type:
#     ./install-nwn.sh
# Enter the CDs when asked to do so, and soon you will be enjoying
# Neverwinter Nights Platinum!
# 
# Note:
# The files installed from the Platinum CDs and the files from the 
# current hotu patch match those in Eyrdan's valid installation 
# guide md5sums for common and both expansion packs (1 and 5), 
# except for ./fixinstall. The one included with the Platinum CDs 
# may be older, but they only differ by a few characters. It 
# certainly won't break your install.
#---------------------------------------------------------------------
# Requirements:
#
# unshield: You must have this installed since some of the required
#     files are in installshield .cab files. Type 'unshield -h'
#     at your shell prompt to see if you have it installed.
#     If you don't, you can get it from:
#     http://synce.sourceforge.net/synce/unshield.php
#     It's free and it does the job with less patch downloading.
# linuxhotuclientupdate1xxto164eng.tar.gz: The latest linux Hordes
#     of the Underdark patch. Some of the files from the install
#     CDs are not extracted since they would only be overwritten
#     by the latest patch, so you need this. You can get it from:
#     http://nwn.bioware.com/support/patch.html
# The game cds: You need the cds. This script installs most of the
#     files for the game from the cds.
#---------------------------------------------------------------------
# Configuration parameters:
# No trailing slashes (/) for directories.
# The cdrom drive mount point where each of the cds will be
# mounted one at a time.
OPT_CDROM=/media/cdrom0
# The destination directory where all the files will be extracted.
# You must have write access to this directory.
OPT_INSTALL_DIR=/home/kim/NwN
# The patch to apply after the install is done. Some of the
# required files are only found in the patch.
OPT_PATCH=./English_linuxclient168_xp2.tar.gz
# Whether or not to use the mount command. Some systems automatically
# mount a cdrom drive when a cd is inserted. If your system does this,
# then this should be set to 0. If you have to manually mount cds
# with the mount command, set this to 1. You might have to run the 
# script as root to use the mount command.
OPT_USE_MOUNT_COMMAND=0
# The username and group to make the owner of all the files.
# If this is other than your own, then the script will have to
# be run as root. If you've opted to OPT_USE_MOUNT_COMMAND, then
# likely you *are* running the script as root and you will want
# to set these options to the user and group that you will play
# the game as.
# OPT_USERNAME=root
OPT_USERNAME=`kim`
#OPT_GROUPNAME=root
OPT_GROUPNAME=users
# NOT USED, but could be if someone is so inclined to write it.
# Whether to install from 4 cds or from the dvd.
OPT_CD_OR_DVD=CD
# End of configuration. Run the script!
#---------------------------------------------------------------------
# Prompt the user and wait for Enter to be pressed. Any input
# is ignored.
# Paramters:
#   $1: The text to use for a prompt.
give_prompt() {
  echo "$1 Press Enter to continue."
  read $ENTER
  return 0
}
# Get all desired zip files from a disk:
# Parameters:
#   $1: The disk number, ie. 1, 2, 3, or 4.
#   $@: The list of files to get, eg. "disk4" "xp1" "xp1_data"
get_zips_on_disk() {
  disk_num="$1"
  shift
  give_prompt "Please insert Neverwinter Nights disk $disk_num in $OPT_CDROM."
  if [ $OPT_USE_MOUNT_COMMAND -eq 1 ]; then
    mount $OPT_CDROM
  fi
  for file in $@
  do
    filename="$OPT_CDROM/$file.zip"
    while [ ! -r "$filename" ]; do
      give_prompt "Cannot read \"$filename\". Please check that disk $disk_num is in $OPT_CDROM."
    done
    unzip -o "$filename"
  done
  
  return 0
}
# Unmount the cd only if that's what the user wants.
do_umount()
{
  if [ $OPT_USE_MOUNT_COMMAND -eq 1 ]; then
    umount $OPT_CDROM
  fi
  return 0
}

# Same as get_zips_on_disk(), but unmounts the cdrom afterwards.
get_zips_on_disk_umount() {
  get_zips_on_disk $@
  do_umount
  return 0
}
# Conditionally create a directory.
# Parameters:
#   $1: The name of the directory to create.
make_dir() {
  if [ -d "$1" ]; then
    if [ ! -w "$1" ]; then
      echo "You do not have write permission for $1!" 1>&2
      return 1
    else
      return 0
    fi
  else
    if ( mkdir "$1"); then
      return 0
    else
      echo "Unable to create $1!" 1>&2
      return 1
    fi
  fi
}
# Create a directory and enter it.
# Parameters:
#   $1: The name of the directory to create and enter.
make_and_enter() {
  if ( make_dir "$1" ); then
    cd "$1"
    return 0
  else
    return 1
  fi
}

# Make the destination directory:
make_and_enter "$OPT_INSTALL_DIR" || exit 1
# Unpack all the needed zip files.
get_zips_on_disk_umount 2 "disk2"
get_zips_on_disk_umount 3 "disk3" "language_data" "Data_Linux"
get_zips_on_disk_umount 4 "disk4" "xp1" "xp1_data"
get_zips_on_disk 1 "Data_Shared" "Language_data"
# Get some files from the cab files.
make_and_enter unshielded_files
unshield x $OPT_CDROM/disk1/data1.hdr
make_dir ../nwm/
mv NWN_Platinum/nwm/Chapter1E.nwm ../nwm/
mv NWN_Platinum/nwm/Chapter4.nwm ../nwm/
mv NWN_Platinum/nwm/XP1-Chapter*.nwm ../nwm/
mv NWN_Platinum/nwm/XP1-Interlude.nwm ../nwm/
make_dir ../docs/
mv NWN_Platinum/docs/* ../docs/
make_dir ../modules/
mv NWN_Platinum/modules/Contest\ Of\ Champions\ 0492.mod ../modules/
mv NWN_Platinum/modules/DEMO\ -\ A\ Bucket\ of\ Gnolls.mod ../modules/
cd ..
rm -rf unshielded_files
do_umount
# Apply the current patch.
rm -rf override # Not needed, but for good measure.
echo Extracting $OPT_PATCH ...
tar -xvzf $OPT_PATCH
# Fix any files that need fixin'.
mv ./texturepacks/xp2_gui.erf ./texturepacks/XP2_GUI.erf
chown -R $OPT_USERNAME:$OPT_GROUPNAME *
./fixinstall
# Give final instructions.
echo "Add \"cd $OPT_INSTALL_DIR\" to \"$OPT_INSTALL_DIR/nwn\" to be able to run Neverwinter Nights from anywhere. You may also want to add a symbolic link to it from a bin directory, or somewhere else in your PATH."
echo "Enjoy!"
exit 0

```

---

### Post by Urbandale on 2007-12-26
Ok, I did some research on my own machine to try and help people who want to help me. I unziped the update onto the folder where I tried to save Neverwinter, then I went to look at the libraries it requires, what fun.
```
 ldd nwmain
        linux-gate.so.1 =>  (0xffffe000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7f13000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7efb000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7e99000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e16000)
        libmss.so.6 => /lib/libmss.so.6 (0xb7da2000)
        libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0xb7d13000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7bc9000)
        /lib/ld-linux.so.2 (0xb7f47000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7ad8000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7ac9000)
        libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0xb7ac4000)
        libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb7ac1000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb7abc000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ab8000)
        libdrm.so.2 => /usr/lib/libdrm.so.2 (0xb7aae000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb79ba000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb79af000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0xb78e9000)
        libdirectfb-0.9.so.25 => /usr/lib/libdirectfb-0.9.so.25 (0xb7892000)
        libfusion-0.9.so.25 => /usr/lib/libfusion-0.9.so.25 (0xb788c000)
        libdirect-0.9.so.25 => /usr/lib/libdirect-0.9.so.25 (0xb787c000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7879000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7874000)

```

Ok, so I'm not missing anything, but I'll look at the nwn script anyway, to see if its paths are correct.

```
less nwn
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

./nwmain $@

```

Nothing seems to be out of place, so I run ./nwn again. This time, all it says is 
```
Failed to initialize graphics.
Segmentation fault (core dumped)


```

I'm guessing that's a major clue, but I have no idea as to what its referring to since all the libraries are there. If anyone can help me, I would greatly appreciate it.

---

### Post by Non Plus Ultra on 2008-03-01
yep, same problem here. It worked fine at first, but I broke the rule that says "if it ain't broken do not fix it" .
I installed the Ati Catalyst drivers yesterday and that was the most stupid thing I could ever do. Everything is slooooow and nwn always worked flawless, until after the update of the drivers. :frown:
What I' m trying to do now is figure out what drivers I used in the first place.

---

### Post by Non Plus Ultra on 2008-03-02
okay, I did some reinstalling with previous Catalyst drivers and following the tutorials to the letter and all that. Nwn now starts, but is still very slow. Appears that 3D acceleration is somehow throttled. Even maximising a normal window is slow now. I'm afraid I have to do a reinstall of my laptop to fix it. Crickey!

---

### Post by Non Plus Ultra on 2008-03-03
sorry for kicking the topic.... installed Hardy yesterday with default drivers and although I have a lot of other problems now ;) nwn runs like a charm. So I'll stay away from Catalyst in the future :)

---

### Post by MulletMan on 2008-05-12
Not sure if people are still having this problem...

But I noticed that some (all?) user defined signal handlers don't work under Ubuntu, at least in 'userland.'I would imagine it's a security measure of sorts. But is this right? How is it fixed?

---

### Post by hjalmarso on 2008-05-13
I can't even get the nwn_129_final.run to execute. I have Ubuntu Hardy Heron 8.04 and when I try to run 

```
 ./nwn_129_final.run
bash: ./nwn_129_final.run: Permission denied

```

I tried this in the Root terminal. What to do?

---

