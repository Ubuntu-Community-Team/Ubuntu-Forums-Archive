---
title: "XGL not working"
date: 2007-02-12
forum: Desktop Environments
---

### Post by DopeFish on 2007-02-12
Hello,

I've tried to install xgl with a script from this post: [http://www.ubuntuforums.org/showthread.php?t=127090](http://www.ubuntuforums.org/showthread.php?t=127090) and failed. The scripts works fine with no errors, but when I try to login on a xgl session I get a brown screen for 5 seconds or so and then it takes me back to the default login screen. Also if I try to login on my default session after the session loads it jams and I have to reboot.

What I would like to do know is unnistall in some sort of way (if I can) the xgl that has been added thru that script and try to install it again properly.
I'm a real begginer (I'm just learning the basic commands for the terminal :p) so if you can help me with something very easy to understand I'd appreciate it.

I thank anyone in advance that could help me.

---

### Post by energiya on 2007-02-13
Could you please post your hardware configuration? Mainly the graphics board.
Excuse my ignorance, but... what script?

---

### Post by Brunellus on 2007-02-13
thread moved.  XGL/Compiz are off-topic in Absolute beginners.

---

### Post by DopeFish on 2007-02-13
Thanks for moving didn't know it was a Desktop Enviroment category.

@energiya I've posted the wrong link, but I also can't seem to find the thread here in the forums. All that I can do is past in the code from the script that I still have on my hdd.

I have an ATi 9550 from Gigabyte and I have installed the original drivers from ati.com:

[img]http://static.zooomr.com/images/731021_5b1602bbf5.jpg[/img]

```
#!/bin/bash

# - Please keep in mind that I have not thoroughly tested this, that I do not have a NVIDIA graphics card, and again, that I have NOT thoroughly tested this yet.
# - Currently, this script will not function under KDE (Kubuntu) or Intel graphics cards; it might in the future though.

# - Wicher (a.k.a. Ra211)

Superuser() {
  xit=$1;shift
  msg=$@
  if [ "$UID" -ne "0" ]; then
    echo $msg
    if [ ${xit:-"0"} -eq "1" ]; then
      exit -1
    fi
  fi
}
Username()
{
 if [ -n "$Username" ]; then 
   echo "$Username"
 else
   echo $(echo $HOME | sed 's/^.*home\///' | sed 's/\/.*$//')
 fi 
}
Backup()
{
 fil="$1"; shift
 if [ ! -f "$fil" ]; then 
   echo "I'm sorry, but \"$fil\" does not seem to exist."
   return  -1
 fi 
 cp --backup=t "$fil" "$fil_backup"
}
Update()
{
 pushd . 
 if (! grep -qi "compiz" /etc/apt/sources.list ); then
  Backup /etc/apt/sources.list  
  wget -c http://www.beerorkid.com/compiz/quinn.key.asc
  apt-key add quinn.key.asc
  cd /tmp
  rm sources.list 
  echo -e "deb http://en.archive.ubuntu.com/ubuntu/ dapper main restricted\ndeb-src http://en.archive.ubuntu.com/ubuntu/ dapper main restricted\ndeb http://en.archive.ubuntu.com/ubuntu/ dapper-updates main restricted\ndeb-src http://en.archive.ubuntu.com/ubuntu/ dapper-updates main restricted\ndeb http://en.archive.ubuntu.com/ubuntu/ dapper universe\ndeb-src http://en.archive.ubuntu.com/ubuntu/ dapper universe\ndeb http://en.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse\ndeb-src http://en.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse\ndeb http://security.ubuntu.com/ubuntu dapper-security main restricted\ndeb-src http://security.ubuntu.com/ubuntu dapper-security main restricted\ndeb http://security.ubuntu.com/ubuntu dapper-security universe\ndeb-src http://security.ubuntu.com/ubuntu dapper-security universe\ndeb http://www.beerorkid.com/compiz/ dapper main" > /etc/apt/sources.list
  echo -e "Your repository list has been changed; a backup of the old version has been made.\n"
 fi 
 echo -e "Running the software updater.\n"
 dpkg --configure -a
 apt-get update
 apt-get -y upgrade 
 echo -e "\nYour system is now up-to-date.\n"
 popd
}
Chipset()
{
  msg=$1; shift
  CARD=$( Graphics_card )
  if test "x$CARD" = "x"; then 
   echo -e "\n$msg\n"
   exit -3
  fi
}
Graphics_card()
{
 lspci | egrep -i "VGA|Display" | grep -qi "ATI Technologies"
 if [ $? -eq 0 ]; then 
   echo "ATI." 
 fi 
 lspci | egrep -i "VGA|Display" | grep -qi "Nvidia"
 if [ $? -eq 0 ]; then 
  echo "NVIDIA."
 fi
 echo 
}
DriverNVIDIA()
{
 echo -e "\nInstallling the driver from NVIDIA.\n"
 Backup /etc/X11/xorg.conf 
 apt-get -y install nvidia-kernel-common nvidia-glx
 nvidia-glx-config enable
 sed -e 's/\tLoad\t"glx"/# \tLoad\t"glx"/' -i /etc/X11/xorg.conf
 sed -e 's/\tLoad\t"dri"/# \tLoad\t"dri"/' -i /etc/X11/xorg.conf
 sed -e 's/\tLoad\t"GLcore"/# \tLoad\t"GLcore"/' -i /etc/X11/xorg.conf
 sed -i -e 's/"Module"/"Module"\n\tLoad\t"glx"/' /etc/X11/xorg.conf
 sed -i -e 's/"nvidia"/"nvidia"\n\tOption\t"RenderAccel"\t"true"/' /etc/X11/xorg.conf
 echo -e '\nSection "Extensions"\n\tOption\t"Composite"\t"Enable"\nEndSection' >> /etc/X11/xorg.conf
 echo -e "Xgl -fullscreen :0 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1\nexec gnome-session" > /usr/local/bin/Xgl.sh
 nvidia-xconfig
}
DriverATI()
{
 echo -e "\nInstalling the fglrx driver from ATI.\n"
 apt-get -y install xorg-driver-fglrx
 echo fglrx | tee -a /etc/modules
 depmod -a ; modprobe fglrx
 Backup /etc/X11/xorg.conf 
 sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf
 echo -e "Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1\nexec gnome-session" > /usr/local/bin/Xgl.sh
}
Driver()
{
  case $( Graphics_card ) in 
    ATI*) 
      echo "An installation for graphics cards from ATI will now follow."
      DriverATI
      ;;
    NVI*) 
      echo "An installation for graphics cards from NVIDIA will now follow."
      DriverNVIDIA
      ;;
    *) echo -e "Your graphics card is currently not supported."; exit -1
    ;;
  esac
}
Xgl()
{
 dpkg-divert --package xserver-xorg-core --divert /usr/share/man/man1/Xserver.1x.gz.xgl --rename /usr/share/man/man1/Xserver.1x.gz
 apt-get -y install --reinstall libgl1-mesa libglitz1 libglitz-glx1 xserver-xgl compiz compiz-gnome gset-compiz
 chmod +x /usr/local/bin/Xgl.sh
 echo -e "[Desktop Entry]\nEncoding=UTF-8\nName=Xgl\nExec=/usr/local/bin/Xgl.sh\nIcon=\nType=Application" > /usr/share/xsessions/Xgl.desktop
 User=$(Username)
 sudo -u "$User" mkdir $HOME/.config
 sudo -u "$User" mkdir $HOME/.config/autostart
 sudo -u "$User" echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=compiz --replace gconf\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/compiz.desktop
 sudo -u "$User" echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=gnome-window-decorator\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/gnome-window-decorator.desktop
 sudo -u "$User" echo -e "[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=killall gnome-panel\nX-GNOME-Autostart-enabled=true" > $HOME/.config/autostart/gnome-panel.desktop
 sudo -u "$User" echo -e '[Desktop Entry]\nName=No name\nEncoding=UTF-8\nVersion=1.0\nExec=xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"\nX-GNOME-Autostart-enabled=true' > $HOME/.config/autostart/xmodmap.desktop
}
Preferences()
{
 User=$(Username)
 sudo -u "$User" gconftool-2 --set --type=Boolean /apps/panel/global/enable_animations "False"
# sudo -u "$User" gconftool-2 --set --type=Boolean /apps/compiz/plugins/cube/screen0/options/in "True"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/move/screen0/options/opacify_min_opacity "50"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/move/screen0/options/opacity "50"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/resize/screen0/options/opacify_min_opacity "50"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/resize/screen0/options/opacity "50"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/scale/screen0/options/corners "TopRight"
 sudo -u "$User" gconftool-2 --set --type=list --list-type=string /apps/compiz/plugins/state/screen0/options/opacity "[w:Unknown:75,w:Dock:75,p:Gnome-terminal:60,p:Cairo-clock:50]"
 sudo -u "$User" gconftool-2 --set --type=list --list-type=string /apps/compiz/plugins/trialfocus/screen0/options/exclude "[Cairo-clock]"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/trailfocus/screen0/options/maximum_trail_count "2"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/trailfocus/screen0/options/minimum_window_opacity_level "50"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/water/screen0/options/rain_delay "2500"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/wobbly/screen0/options/map_friction "3"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/wobbly/screen0/options/map_spring_k "8"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/wobbly/screen0/options/maximize_friction "3"
 sudo -u "$User" gconftool-2 --set --type=string /apps/compiz/plugins/wobbly/screen0/options/maximize_spring_k "8"
 sudo -u "$User" gconftool-2 --set --type=Boolean /apps/compiz/plugins/wobbly/screen0/options/visual_bell "True"
}
Chipset "To use this script, you must either have a graphic card from ATI or NVIDIA."
Superuser 1 "This script must be executed with root privileges (use sudo)." 
Update
Driver
Xgl
Preferences
echo;echo;echo
echo "This scrip may have modified and backed up the following files: /etc/apt/sources.list and /etc/X11/xorg.conf."
echo "Installation of Xgl, Compiz, several tweaks and possibly new drivers is now completed."
echo "You can start Xgl and Compiz by selecting the Xgl X session in the GNOME Display Manager (the loginscreen)."
echo "Please reboot your computer and report your results."
echo;echo;echo
```

---

