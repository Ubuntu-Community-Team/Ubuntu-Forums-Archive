---
title: "BURG has no splash"
date: 2010-07-04
forum: Desktop Environments
---

### Post by borth92 on 2010-07-04
I wanted a more graphical screen when I chose what OS to boot into, so I installed BURG. It works great, I love the GRUB interface now. But after I choose my OS (I have not tried windows) I get like a command line showing what is going on in the boot. I do not want this, I want the old loading screen back with the BURG partition interface. How can this be accomplished?

---

### Post by ajgreeny on 2010-07-04
You could have added an image to grub2, and used that still.  It is not hard to do, but I admit it needs some config file editing.

I presume burg does all this with a gui of some sort, but have never looked at it, so am not sure.

_**Change the GRUB2 splash image**_

Now we will see how we can change the default GRUB2 splash image. First  select the image file that you want to install from the following  locations or elsewhere:
/usr/share/images/desktop-base/
/usr/share/images/grub/
For this example, I have selected “Plasma-lamp.tga” from  /usr/share/images/grub/.
Now edit the file following file:
```
gksudo gedit /etc/grub.d/05_debian_theme
```
 and change the following line from:
 for i in  {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga}
**to**
for i in  {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Plasma-lamp.{png,tga}  and save the file.
 This basically tells GRUB2 to look for image name “Plasma-lamp” in the  locations:
/boot/grub
/usr/share/images/desktop-base
/usr/share/images/grub
 Now you need to regenerate the grub.cfg file by giving the following  command:
```
sudo update-grub
```
Updating /boot/grub/grub.cfg ...  etc etc.

---

### Post by borth92 on 2010-07-04
> **ajgreeny said:**
> You could have added an image to grub2, and used that still.  It is not hard to do, but I admit it needs some config file editing.

I presume burg does all this with a gui of some sort, but have never looked at it, so am not sure.

_**Change the GRUB2 splash image**_

Now we will see how we can change the default GRUB2 splash image. First  select the image file that you want to install from the following  locations or elsewhere:
/usr/share/images/desktop-base/
/usr/share/images/grub/
For this example, I have selected “Plasma-lamp.tga” from  /usr/share/images/grub/.
Now edit the file following file:
```
gksudo gedit /etc/grub.d/05_debian_theme
```
 and change the following line from:
 for i in  {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga}
**to**
for i in  {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Plasma-lamp.{png,tga}  and save the file.
 This basically tells GRUB2 to look for image name “Plasma-lamp” in the  locations:
/boot/grub
/usr/share/images/desktop-base
/usr/share/images/grub
 Now you need to regenerate the grub.cfg file by giving the following  command:
```
sudo update-grub
```
Updating /boot/grub/grub.cfg ...  etc etc.
those directories do not exist for me. all I have is usr/share/images/C  and  usr/share/images/desktop-base

---

### Post by borth92 on 2010-07-04
Also, that file did not look like you described, could you paste the code of the whole program you asked me to change

---

### Post by ajgreeny on 2010-07-04
Here you go, the full default /etc/grub.d/05_debian_theme.  I did also say you could use an image from elsewhere
```
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=${COLOR_NORMAL}
  set color_highlight=${COLOR_HIGHLIGHT}
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi

```

Also see this webpage with a lot more detail on using your own image.
[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html#make_your_own_](http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html#make_your_own_)

---

### Post by borth92 on 2010-07-05
after going through some solutions, I am missing usr/bin/dpkg. coud you provide me with the lines for that?

---

### Post by ajgreeny on 2010-07-05
> **borth92 said:**
> after going through some solutions, I am missing usr/bin/dpkg. coud you provide me with the lines for that?
Do you mean that file is missing in your file system?  If so I have no idea how you can proceed, I'm afraid, as I think it will mean you can not install anything.

Maybe you can download the package from ubuntu somehow, but I have no idea how you could then get dpkg installed, as you need dpkg to install packages.  A bit of a chicken and egg situation, which I will have to bow out of.

Just as a matter of interest, how on earth did you manage to remove the file, and why?
Also, and I should really have already asked this, what version of ubuntu are you using?  My answers are for 9.10 and 10.04.

---

### Post by borth92 on 2010-07-05
I did not remove it and I can install packages right now so maybe i'm wrong about it being missing. I am a former Windows Guru jut switching over to ubuntu. It definitely feels weird not knowing whats going on lol. I get an error when following the instructions on the site you directed me to...heres the command line stuff that came up.

danborth@danborth-laptop:~$ sudo apt-get install grub2-splashimages
[sudo] password for danborth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  grub2-splashimages
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 9,776kB of archives.
After this operation, 14.5MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe grub2-splashimages 1.0.0 [9,776kB]
Fetched 9,776kB in 29s (337kB/s)                                               
Selecting previously deselected package grub2-splashimages.
(Reading database ... 130615 files and directories currently installed.)
Unpacking grub2-splashimages (from .../grub2-splashimages_1.0.0_all.deb) ...
Setting up grub-pc (1.98-1ubuntu7) ...
Installation finished. No error reported.
Generating grub.cfg ...
/etc/grub.d/05_debian_theme: line 59: unexpected EOF while looking for matching `"'
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub2-splashimages (1.0.0) ...
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by borth92 on 2010-07-05
o ok i was looking under bin for dpkg not usr/bin.

---

### Post by ajgreeny on 2010-07-05
Perhaps burg does not have or use **grub-pc** at all and that is why you are getting this error message when trying to do things to burg.

Sorry, I am now lost, and I think you need to go to a burg forum if there is one and ask there.

---

### Post by borth92 on 2010-07-07
GOT IT!

You had me editing etc/default/grub
I needed it edit the almost identical file etv/default/burg

All I needed to do was change the quiet boot to quiet splash and the splash is now enabled in burg

---

### Post by borth92 on 2010-07-24
I got it a while ago and forgot to tell you that this is solved. I just needed to look at the grub.conf file to see a line says quiet splash. And in the burg.conf file, it just says quiet. So all I needed was to add splash to the quiet and it displayed the splash.

---

