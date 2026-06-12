---
title: "Xpde"
date: 2005-08-20
forum: Desktop Environments
---

### Post by xequence on 2005-08-20
I want to try different DEs to see which ones work. I downloaded the 5 MB ,tar,gz of XFCE and I cant understand how to install it.

I did

sudo dpkg -i /home/patrick/Desktop/xpde-0.5.0.tar.gz

but it gave me this:

dpkg-deb: `/home/patrick/Desktop/xpde-0.5.0.tar.gz' is not a debian format archive
dpkg: error processing /home/patrick/Desktop/xpde-0.5.0.tar.gz (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /home/patrick/Desktop/xpde-0.5.0.tar.gz

Can someone please explain how to install this? I dont understand how to install anything thats not in synaptic or apy-get.

---

### Post by heimo on 2005-08-20
No, you can't install .tar.gz packages using dpkg - dpkg is for deb packages. You have to find deb, or install with the usual mantra:
 ```

tar xzvf packagename.tar.gz
cd packagename
./configure
make
sudo make install

```
*) this assumes you downloaded source package

EDIT: I don't recommend installing from source if you're unexperienced. If your goal is trying different window managers and desktop environments, search repositories for other alternatives: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by xequence on 2005-08-20
Thank you very much =D And its ok, my questions are probably pretty basic :)

ANd I dont know if its the source. The file is .tar.gz and it unzips into a folder that has a bin folder in it and some files inside that.

---

### Post by heimo on 2005-08-20
[QUOTE=xequence]Thank you very much =D And its ok, my questions are probably pretty basic :)[/QUOTE]

No problem. I edited my post above. Sometimes you need to also install other software, libraries - these are dependencies for the software you're installing. You should primarily always install stuff from official repositories to avoid messing up your system, and avoid installing from source. Prepackages software is the easiest way to install stuff, installing from source involves usually some manual configuring and requires more knowledge of your system.

---

### Post by xequence on 2005-08-20
Posts: 999
Almost there ;)

I searched on the packages for xpde and nothing came up...

I tried the code you gave and it is all crazy. I am doing something stupid here, something I should know...

THe file I want to install is at /home/patrick/Desktop/xpde-0.5.0.tar.gz


THis stuff is really confusing to me :K

---

### Post by drizek on 2005-08-20
do "ls -l" on the xpde folder in a terminal and post here.

also, if yoou want to compile from source ,you need to install some compilers in synaptic. im not sure which ones though. when you do ./configure, youre going to get errors of missing depends. you will have to go into synaptic and search/install them all until ../configure finishes smoothly. you only need to do it one time though, all apps in teh fuuture will compile fine. 

and when you cant find something in synaptic, do a google search for

 <package> ubuntu


and you will most likely find a guide/deb to install it.

---

### Post by cwaldbieser on 2005-08-20
From the xpde web site:
> Each package contains binaries and sources,decompress the package and read the INSTALL file for general installation instructions 

Many folks won't want to download a 5MB archive just to extract a small text file, but if you could just read the contents of that file and post what you don't understand, it could make it easier for others to help you.

---

### Post by heimo on 2005-08-20
I downloaded couple xpde tar.gz packages, and my instructions above won't help. But at least 0.40 version comes with INSTALL file with instructions and that package looks like binary package, don't know if you would run into dependency problems. If you need to compile, you also need compiler - essential stuff for this is in package build-essentials

[QUOTE=xequence]Posts: 999
Almost there ;)
[/QUOTE]

:D There!


Beginning of INSTALL
```

XPDE INSTALL INSTRUCTIONS
-------------------------

To install XPde on your computer, follow these steps:

-Decompress the tar.gz file you downloaded

tar xvzf xpdeXXXXXXX.tar.gz

-Change the current directory to the one is created

-Change the current user to root using the su command

-Execute the install script

./install.sh

This script will create all the directory structure and will also
copy all the files to the default locations.

Now, as a normal user, execute the setup.sh script, this script
will copy the default desktop settings to your ~/.xpde directory
and also will copy xinitrcDEFAULT file to your HOME dir, this
file contain the lines you must add to your system to load XPde.
In most cases you just need to rename this file to .xinitrc
```

---

### Post by xequence on 2005-08-20
[QUOTE=drizek]do "ls -l" on the xpde folder in a terminal and post here.[/QUOTE]


total 4
drwxr-xr-x  4 patrick patrick 4096 1969-12-31 19:00 bin



> Many folks won't want to download a 5MB archive just to extract a small text file, but if you could just read the contents of that file and post what you don't understand, it could make it easier for others to help you.


there is one file that says startxpde and it has this:


export LD_LIBRARY_PATH=/usr/share/xpde/bin
if test -n $HOME/.xpde; then
  cp -r /usr/share/xpde/bin/defaultdesktop $HOME/.xpde
fi
/usr/share/xpde/bin/desktop &
/usr/share/xpde/bin/wm

---

### Post by heimo on 2005-08-20
xpde 0.5.1 version comes with this INSTALL file
([http://www.xpde.com/releases.php]("http://www.xpde.com/releases.php"))

> General installation instructions:
 -Decompress the tar.gz in /usr/share as root
 -Edit the .xinitrc file of the user you want to run XPde and put this line:
 /usr/share/xpde/bin/startxpde
 -Start X

If you want to use another installation directory, just edit the startxpde script.

If you want to post specific installation instructions for any distro, please, use the forums.

Changes on this release:
-Finally the Start Menu has been included and the "desktop paradigm" is complete.
-Updated to the last unnoficial K3 patch
-A bug fixed updating desktop contents
-A bug fixed on the taskbar

How you can help?
-The project can be divided right now in:
 *Desktop: The background with icons
 *Window Manager: The part responsible to manage windows
 *Taskbar: The area where tasks reside
 *Start Menu: The menu that shows all the options to the user

The next release is going to be focused adding capabilities to the desktop, so if you want to help, just tell me which things do you want to get included.

Sorry to all the people has sent me an e-mail, I will try to answer as soon as possible.

Please, feel free to use the forums and mailing lists to post your comments.

Regards.


---

### Post by xequence on 2005-08-20
I have to go very soon so ill finish doing this later. THanks everyone :)

---

### Post by heimo on 2005-08-20
Seems like I used ~40 minutes trying to get it working from those binary packages (on Breezy Badger), but for me it was too much. I don't know if it's the same on Hoary, but I'd try to compile it or search if someone already packaged it in deb. 

On the other hand, I probably would just skip it:
[http://www.ubuntuforums.org/showthread.php?t=50129]("http://www.ubuntuforums.org/showthread.php?t=50129")

Personally, I'm not interested to get this working and my earlier friendly suggestion remains, try the ones that are easy to install and already available on Ubuntu repositories.

---

