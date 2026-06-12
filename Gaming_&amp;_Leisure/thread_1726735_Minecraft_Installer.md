---
title: "Minecraft Installer"
date: 2011-04-11
forum: Gaming &amp; Leisure
---

### Post by allocateB on 2011-04-11
[SIZE=4][COLOR=#404080]Complete Ubuntu Installer Script[/COLOR][/SIZE]
[SIZE=3][COLOR=#ff8000]by Alloc[/COLOR][/SIZE]
[COLOR=#804080]alloc@dr.com[/COLOR]

[COLOR=Red]**UPDATES!**[/COLOR]
[COLOR=#404080]-added desktop shortcut feature
-the script checks for Sun-Java, and downloads it if you dont have it
-minecraft will be added to your applications menu under games
-improved java detection script
-checks for the existence of files before creating new ones
-fixed the multiple launch bug 
-redesigned code based on shorter functions  
-user is now asked what they'd like to do  
-complete uninstall function implemented 
-now uses the official minecraft icon [/COLOR][IMG]http://www.minecraft.net/favicon.png[/IMG]
[COLOR=#404080]-troubleshooting menu added
[/COLOR][COLOR=#404080]-server install feature added[/COLOR]
 [IMG]http://i.imgur.com/ugDRM.png[/IMG]<< server icon

Setting up a solid installation of minecraft on Ubuntu can be a hassle.
But this installer script will do all the hard work for you!
[SIZE=3][COLOR=#ff8000]
How To Run It[/COLOR][/SIZE]
 1. Download the file from the link below
 2. Right click and open the file's Properties 
 3. Browse to the Permissions tab and check the executable box
 4. Double click on the file and choose _RUN IN TERMINAL_!

[SIZE=3][COLOR=#ff8000]Basically the script does this:[/COLOR][/SIZE]
 - Looks for java
 - Downloads and installs OpenJDK if needed
 - Downloads Minecraft for you!
 - Installs it to a new .minecraft folder!
 - Writes a shell script to your bin folder
 - Creates a shortcut on your desktop that you can use to run Minecraft!
 - Creates a launcher in your Applications menu for Minecraft!
 - Lets you run Minecraft from terminal with a simple "minecraft" command!
 - also, it makes you happy!

**[COLOR=Red]TUTORIAL[/COLOR]**
_[http://www.youtube.com/watch?v=odo6QbdCfeU](http://www.youtube.com/watch?v=odo6QbdCfeU)_


[COLOR=#ff8000]Alternatively[/COLOR]: you can give it executable permissions via the terminal and run it from there
```
:~$ cd /path/to/downloaded/file/
:~$ chmod -x Minecraft_Installer_20.sh
:~$ bash Minecraft_Installer_20.sh
```[SIZE=3][COLOR=#ff8000]After the script has run, you'll have a nice launcher on your desktop and you'll be able to just open up terminal and type "minecraft" to play![/COLOR][/SIZE]


[COLOR=#ff8000][SIZE=150]  [SIZE=3]Download Link:[/SIZE][/SIZE][/COLOR][HERE]("http://www.filedropper.com/mincraftinstaller20")

 
I'd love to here your feed back and suggestions!
oh, and I wouldn't mind your problems and errors either [Notch] 
 [EMAIL="alloc@dr.com"]alloc@dr.com[/EMAIL]
 

[COLOR=#404080]The Script:[/COLOR]
```
#!/bin/bash


# Alloc's Minecraft Installer:

# feel free to change, update, improve, and release this script

# suggestions of feedback? reach me at alloc@dr.com

# This script, in no way, is directly distributing any protected minecraft files
# all files are downloaded directly from minecraft.net. Don't worry, you won't be
# breaking the "one big rule" :)

# happy mining!

# latest update 5/07/2011


echo ""
echo "@-------------------------------------------@"
echo "@     Alloc's Bash Minecraft Installer      @"
echo "@     Version 2.0                           @" 
echo "@                                           @"
echo "@     Please feel free to improve           @"
echo "@     this script however you desire.       @"
echo "@                                           @"
echo "@     Alloc@dr.com                          @"
echo "@-------------------------------------------@"

counter=1

#----------------------------------#
#           DOTS FUNCTION          #
#----------------------------------#
# this function simply prints three dots. It waits .1 seconds between each dot
function dots {
while [ $counter -le 3 ]
do
echo -ne "."
sleep .1
((counter++))
done
let counter=1
echo
}
## END DOTS

#----------------------------------#
#         INSTALL FUNCTION         #
#----------------------------------#
# This is the main install function, here all the files are downloaded/created and installed
function Install {
# the first thing it does is check to see if the .minecraft folder already exists
# if so, then we don't need to create a new one, if not, we do.
if [ -e /home/$(whoami)/.minecraft ]
then
    echo  ".minecraft folder exists"
    if [ -e /home/$(whoami)/.minecraft/minecraft.jar ]
    then
        echo  -ne "have you run this before?"
        dots
    
    fi
    echo ""
else 
echo -ne "creating /home/$(whoami)/.minecraft"
dots
cd /home/$(whoami)
mkdir .minecraft
fi    




#--------------------------------------------
cd /home/$(whoami)/.minecraft
#--------------------------------------------
# after the .minecraft folder is created, the script checks for Sun-Java
# by checking to see if the installation folder is present, if so, then
# it will not download it, however it will still make sure that sun-java
# is default, just in case openjdk is already installed
echo -ne "looking for Sun-Java"
dots
if [ -e /usr/lib/jvm/java-6-sun ] 
then
    if [ -e /usr/lib/jvm/java-6-sun/bin ]
    then 
        if [ -e /usr/lib/jvm/java-6-sun/bin/java ]
        then
        echo "Sun-Java is already Installed!"
        echo -ne "We need to make sure that it is the default Java installation"
        dots
        echo "Don't worry if you see lots of errors"
        echo "this requires root access"
        # setting the default java creates alot of unneeded text, therefore it is done 
        # in a new terminal window, because people dont' really need to see it
        sudo gnome-terminal -x sudo update-java-alternatives -s java-6-sun
        echo "Sun Java set as Default."
        fi
    fi
echo ""
else
echo -ne "you'll need to install Sun-Java-JRE"
dots
echo "this will require root access!"
echo "prepare for lots of text!"
sudo apt-get install sun-java6-jre sun-java6-plugin
sudo update-java-alternatives -s java-6-sun
echo ""
echo ""
echo ""
echo " JAVA INSTALL SUCCESSFUL!"
echo "------------------------------------"
echo ""
echo ""
echo ""

fi 

#--------------------------------------------
# the .jar file is simply downloaded to the .minecraft folder from minecraft.net
# it first checks to see if the user already has it, if so, it won't be downloaded
echo -ne downloading minecraft.jar
dots
if [ -e /home/$(whoami)/.minecraft/minecraft.jar ] 
then
echo looks like you already downloaded it!
else
wget -q www.minecraft.net/download/minecraft.jar
echo "downloaded."
fi
echo""
echo -ne downloading icon
# the icon is also downloaded from minecraft.net, only if needed
dots
if [ -e /home/$(whoami)/.minecraft/icon.png ] 
then
echo "you already have the icon!"
else
wget -q http://www.minecraft.net/favicon.png
mv favicon.png icon.png
echo saved to /home/$(whoami)/.minecraft
fi
echo ""
#---------------------------------------------
echo -ne "writing bin shell"
# this writes a seperate shell script in the /usr/local/bin folder, this is what allows the user
# to run minecraft from terminal, just by typing minecraft.
dots
if [ ! -e /usr/local/bin/minecraft ] 
then
touch minecraft
echo java -jar /home/$(whoami)/.minecraft/minecraft.jar >> minecraft
echo -ne saving to usr/local/bin
dots
echo this requires root access:
sudo cp minecraft /usr/local/bin/
cd /
cd /usr/local/bin
sudo chmod +x minecraft
echo "done"
else 
echo excecutable already written
fi
echo ""
#--------------------------------------------
echo -ne writing desktop shortcut
dots
cd /home/$(whoami)/.minecraft/
if [ -e /home/$(whoami)/.minecraft/install_files ] 
then
echo -ne previous version detected, updating
dots
rm -rf install_files
fi
mkdir install_files
cd install_files

touch alloc-installer.desktop
echo "[Desktop Entry]" >> alloc-installer.desktop
echo "Type=Application" >> alloc-installer.desktop
echo "Encoding=UTF-8" >> alloc-installer.desktop
echo "Name=Minecraft" >> alloc-installer.desktop
echo "Comment=awesome game" >> alloc-installer.desktop
echo Exec= java -jar /home/$(whoami)/.minecraft/minecraft.jar >> alloc-installer.desktop
echo Icon= /home/$(whoami)/.minecraft/icon.png  >> alloc-installer.desktop
echo Categories=Game >> alloc-installer.desktop
echo "Terminal=false" >> alloc-installer.desktop
#----------------------------------------------------
echo -ne granting the shortcut excecution permissions
dots
echo this requires root access
cp alloc-installer.desktop /home/$(whoami)/Desktop
sudo chmod +x /home/$(whoami)/Desktop/alloc-installer.desktop
echo "done"
echo ""
#---------------------------------------------
echo -ne writing menu item
dots
touch alloc-menu.directory
echo [Desktop Entry] >> alloc-menu.directory
echo Value=1.0 >> alloc-menu.directory
echo Type=Directory >> alloc-menu.directory
echo Encoding=UTF-8 >> alloc-menu.directory
echo "done"
echo ""
echo -ne installing to Applications menu
dots
xdg-desktop-menu install alloc-menu.directory alloc-installer.desktop
xdg-desktop-menu forceupdate
echo installed
#--------------------------------------------
echo ""
echo "SUCCESS!"
echo ""
echo -e "Minecraft has been successfully Downloaded and Installed \nCheck your desktop and Applications menu for launchers! \nYou can also run it from terminal with a 'minecraft' command! \ncontact: alloc@dr.com" 
echo "Happy Mining!"

echo""

}
## END INSTALL

#----------------------------------#
#     SERVER INSTALL FUNCTION      #
#----------------------------------#
function ServerInstall {
echo -ne "Looking for Server File"
dots
if [ -e /home/$(whoami)/Minecraft_Server/bin/minecraft_server.jar ]
then
    echo -ne "Server Files already installed!"
    dots
    Main
else
echo "not found!"
fi
echo ""
echo -ne "Creating Server Directory"
dots
mkdir /home/$(whoami)/Minecraft_Server
cd /home/$(whoami)/Minecraft_Server
mkdir bin
cd bin
echo ""
echo -ne "Downloading"
dots
echo -ne "     -minecraft_server.jar"
echo     "   done!"
wget -q http://www.minecraft.net/download/minecraft_server.jar

echo -ne "     -server_icon.png     "
echo     "   done!"
dots
wget -q http://i.imgur.com/ugDRM.png
mv ugDRM.png server_icon.png

echo ""
echo -ne "Writing Shell Launcher"
dots
if [ -e minecraft_server ] 
then
    rm minecraft_server
fi
touch minecraft_server
echo "cd /home/$(whoami)/Minecraft_Server" >> minecraft_server
echo "pwd" >> minecraft_server

echo "java -Xmx1024M -Xms1024M -jar bin/minecraft_server.jar" >> minecraft_server
echo -ne  "Copying to bin folder"
dots
echo "This may require root access:"
sudo cp minecraft_server /usr/local/bin
sudo chmod +x /usr/local/bin/minecraft_server
echo "done"
echo ""

echo -ne "Creating launchers"
dots

mkdir install_files
cd install_files

if [ -e alloc-server_installer.desktop ] || [ -e alloc-menu.directory ] 
then
    rm alloc-server_installer.desktop
    rm alloc-menu.directory
fi
touch alloc-server_installer.desktop
  echo "[Desktop Entry]" >> alloc-server_installer.desktop
  echo "Type=Application" >> alloc-server_installer.desktop
  echo "Encoding=UTF-8" >> alloc-server_installer.desktop
  echo "Name=Server Minecraft" >> alloc-server_installer.desktop
  echo "Comment=Server GUI" >> alloc-server_installer.desktop
  echo Exec=  minecraft_server >> alloc-server_installer.desktop
  echo Icon= /home/$(whoami)/Minecraft_Server/bin/server_icon.png  >> alloc-server_installer.desktop
  echo Categories=Game >> alloc-server_installer.desktop
  echo "Terminal=false" >> alloc-server_installer.desktop
#----------------------------------------------------
echo -ne "Granting the shortcut excecution permissions"
dots
echo this requires root access
cp alloc-server_installer.desktop /home/$(whoami)/Desktop
sudo chmod +x /home/$(whoami)/Desktop/alloc-server_installer.desktop
echo "done"
echo ""

echo -ne "Writing menu item"
dots
touch alloc-menu.directory
  echo [Desktop Entry] >> alloc-menu.directory
  echo Value=1.0 >> alloc-menu.directory
  echo Type=Directory >> alloc-menu.directory
  echo Encoding=UTF-8 >> alloc-menu.directory

echo -ne "Installing server launchers"
dots
xdg-desktop-menu install alloc-menu.directory alloc-server_installer.desktop
xdg-desktop-menu forceupdate
echo "done"
echo ""
echo  -e "The Minecraft server client has been installed! \nrun it from the launchers, or by typing 'minecraft_server' into terminal"


## END SERVER INSTALL 
}

#----------------------------------#
#    SERVER UNINSTALL FUNCTION     #
#----------------------------------#
function ServerUninstall {
if [ ! -d /home/$(whoami)/Minecraft_Server ]
then
    echo Server is not installed!
    return
fi
cd /home/$(whoami)/Minecraft_Server/bin/install_files
echo -ne "Removing Launchers"
dots
xdg-desktop-menu uninstall alloc-menu.directory alloc-server_installer.desktop
echo "done"
echo ""
echo -ne "Removing Desktop Icon"
dots
cd /home/$(whoami)/Desktop
if [ -e alloc-server_installer.desktop ]
then
    rm alloc-server_installer.desktop
    echo "done"
else
    echo "Does not exits"
fi
echo ""
echo -ne "Removing Server"
dots
if [ -d /home/$(whoami)/Minecraft_Server/bin ]
then
    cd /home/$(whoami)/Minecraft_Server
    rm -rf bin
    echo "done"
fi
echo ""
echo -ne "Removing launch script"
dots
echo "this requires root access"
sudo rm /usr/local/bin/minecraft_server
echo "done"

echo "Uninstall Successful"
}
#----------------------------------#
#       UNINSTALL FUNCTION         #
#----------------------------------#
function Uninstall {
echo -ne "Looking for Minecraft"
dots
if [ ! -e /home/$(whoami)/.minecraft/minecraft.jar ]
then
    echo -ne "  -folder not detected"
    dots
    if [ ! -e /usr/local/bin/minecraft ]
    then
    echo -ne "  -bin launcher not detected"
    dots
    echo""
    echo "Minecraft doesn't seem to be installed!"
    Main
    return
    fi
fi
echo "Minecraft found!"
echo -ne "Uninstalling Minecraft"
dots
echo "NOTE: You're save files will be kept"
cd /home/$(whoami)/.minecraft
echo ""
echo -ne "Deleting files and folders"
dots
rm -rf bin
rm -rf texturepacks
rm minecraft.jar
if [ -e options.txt ]
then
    rm options.txt
fi
if [ -e lastlogin ]
then
    rm lastlogin
fi
rm minecraft
rm -rf resources
rm icon.png
cd install_files
echo "Removing Application Launcher"

xdg-desktop-menu uninstall alloc-menu.directory alloc-installer.desktop
echo "Removing Desktop Shortcut"
rm /home/$(whoami)/Desktop/alloc-installer.desktop
rm -rf /home/$(whoami)/.minecraft/install_files
echo ""
echo -ne "Removing Binary Launcher"
dots
echo "this requires root access:"
sudo rm /usr/local/bin/minecraft
echo ""
echo "Minecraft has been uninstalled :(" 

}
## END UNINSTALL

#----------------------------------#
#     TROUBLESHOOT FUNCTION        #
#----------------------------------#
function TroubleShoot {
echo ""
echo ""
echo "#----------------------------------#"
echo "#       Troubleshooting Menu       #"
echo "#----------------------------------#"

echo "What would you like to do? (enter number of choice)"; echo "";
echo "1. install/update Sun-Java"
echo "2. install/update OpenJDK"
echo "3. use Sun-Java to run minecraft from now on"
echo "4. use OpenJDK to run minecraft from now on (not generally encouraged)"
echo "5. these options didn't fix it!"
echo "6. return to the main menu"
TINPUT=0
read TINPUT
if [ $TINPUT -eq 1 ]
then
    echo -ne "Installing/Updating Sun-Java"
    dots
    echo "this requires root access:"
    sudo apt-get install sun-java6-jre
    echo ""; echo ""; echo; echo "Finished!"; echo "";
    TroubleShoot
else
if [ $TINPUT -eq 2 ]
then
    echo -ne "Installing/Updating OpenJDK"
    dots
    echo "this requires root access:"
    sudo apt-get install openjdk-6-jre
    echo ""; echo ""; echo; echo "Finished!"; echo "";
    TroubleShoot
else
if [ $TINPUT -eq 3 ]
then
    echo -ne "Making Sun-Java the default"
    dots
    echo "Don't worry if you see lots of errors"

    sudo gnome-terminal -x sudo update-java-alternatives -s java-6-sun
    echo ""; echo ""; echo; echo "Finished!"; echo "";
else 
if [ $TINPUT -eq 4 ]
then
    echo -ne "Making OpenJDK the default"
    dots
    echo "Don't worry if you see lots of errors"

    sudo gnome-terminal -x sudo update-java-alternatives -s java-6-openjdk
    echo ""; echo ""; echo; echo "Finished!"; echo "";
else
if [ $TINPUT -eq 5 ]
then
echo "-------------------------------------------------"
echo "if these troubleshooting options didn't fix your,"
echo "problem, I'd be glad to help you out! "
echo "Alloc@dr.com"
echo "-------------------------------------------------"
read NOTHING
Main
else
if [ $TINPUT -eq 6 ]
then
return
else
echo invalid choice
TroubleShoot
fi
fi
fi
fi
fi
fi
}

## END TROUBLESHOOT

#----------------------------------#
#          MAIN FUNCTION           #
#----------------------------------#
function Main {
echo ""
echo "------------------------------------------------------"
echo "What would you like to do? (enter number of choice) "; echo "";
INPUT=0
while [ $INPUT != 1 ] && [ $INPUT != 2 ] && [ $INPUT != 3 ]
do
echo "1. Install Minecraft"
echo "2. Uninstall Minecraft"
echo "3. Install Minecraft Server"
echo "4. Uninstall Minecraft Server"
echo "5. TroubleShooting"
echo "6. Exit"
if [ -e /usr/local/bin/minecraft ] && [ -e /home/$(whoami)/.minecraft/minecraft.jar ]
then
echo "7. Play Minecraft!"
fi
read INPUT
if [ $INPUT -eq 1 ] 
then
    Install
    Main
    return
else 
if [ $INPUT -eq 2 ] 
then
    Uninstall
    Main
    return
else
if [ $INPUT -eq 3 ]
then
    ServerInstall
    Main
    return
else
if [ $INPUT -eq 4 ]
then
    ServerUninstall
    Main
    return
else
if [ $INPUT -eq 5 ]
then
    TroubleShoot
    Main
    return
else
if [ $INPUT -eq 6 ]
then
    return
else
if [ $INPUT -eq 7 ] && [ -e /usr/local/bin/minecraft ] && [ -e /home/$(whoami)/.minecraft/minecraft.jar ]
then
minecraft
else

    echo "invalid choice"
    Main
fi
fi
fi
fi
fi
fi
fi

done
}


#----------------------------------#
#      CALL THE MAIN FUNCTION      #
#----------------------------------#

Main

# THE END 

```Notice:
This script does not hold or contain any protected material or files. You are free to change and distribute this script however you so desire.

---

### Post by bryogenic on 2011-04-12
Looks interesting. I'm looking forward to trying it out.

One thing that might need changed though is to install and select Sun Java 1.6 instead of OpenJDK.  While OpenJDK may work fine I've seen anecdotal evidence that many have found that it runs better with Sun Java.  Maybe you could add a selection option at the start of the script to choose which version of Java to check for and use.

Thanks for the script!

---

### Post by allocateB on 2011-04-12
> **bryogenic said:**
> Looks interesting. I'm looking forward to trying it out.

One thing that might need changed though is to install and select Sun Java 1.6 instead of OpenJDK.  While OpenJDK may work fine I've seen anecdotal evidence that many have found that it runs better with Sun Java.

Thanks for the input! I'm working on just that feature right now! But I'm at a bit of a snag. I've found that when people use sun java, the desktop and menu launchers don't work! I'm sure its possible to get them to work however, I just need to keep looking!
Thanks!

---

### Post by thefinn93 on 2011-04-16
Very neat! however, two suggestions:

1. It might be better to use sun-java6 instead of openJDK (as is suggested on the [official download page]("http://www.minecraft.net/download.jsp"))

2. I'd much prefer the favicon for minecraft.net over the "creeper" image you have. It seems to fit the game better (IMO). I'd suggest getting [http://minecraft.net/favicon.png](http://minecraft.net/favicon.png) over the photobucket link you have. If you want to keep that one at least stick it on a host that doesn't cap your bandwidth. Otherwise some people might end up getting the photobucket "Bandwitdh Expired" message instead of the Minecraft icon. I'd suggest imgur.com

---

### Post by allocateB on 2011-04-16
**[SIZE=4][COLOR=DarkOrchid]Updates[/COLOR][/SIZE]** (all the updates since original post, the first four had already been released)
[COLOR=#404080]-added desktop shortcut feature
-you no longer need gcc!
-the script checks for openjdk, and downloads it if you dont have it
-minecraft will be added to your applications menu under games
[COLOR=Red]NEW:[/COLOR]
-improved java detection script
-checks for the existence of files before creating new ones
-fixed the multiple launch bug 
-redesigned code based on shorter functions  
-user is now asked what they'd like to do  
-complete uninstall function implemented 
-now uses the official minecraft icon [/COLOR]



> **thefinn93 said:**
> Very neat! however, two suggestions:

1. It might be better to use sun-java6 instead of openJDK (as is suggested on the [official download page]("http://www.minecraft.net/download.jsp"))

2. I'd much prefer the favicon for minecraft.net over the "creeper" image you have. 

Thanks for the suggestions finn!
The script has been almost completely reworked, and has now about doubled in size.
Part of those updates is that it does now use the official minecraft favicon!

I'm working on an trouble shooting option in the script that lets user choose their java distribution. keep an eye out for it!

Thanks for the support!

---

### Post by termin on 2011-04-22
Not that I would, but how would you uninstall this?

---

### Post by allocateB on 2011-04-24
> **termin said:**
> Not that I would, but how would you uninstall this?

The script now has an uninstall feature. I forgot to update the download link so you may have an outdated version! The link has been updated now with the latest version!

---

### Post by mbudden on 2011-04-27
Interesting. This didn't work in Linux Mint 10 LXDE which is basically like Lbuntu, which is based off of Ubuntu.

---

### Post by penalt on 2011-04-29
This just isn't working for me.  I'm pretty new with Linux and I just don't seem to be getting function.  The script doesn't seem to do anything

---

### Post by El3mentGamer on 2011-05-01
Worked perfect for me! But now that i updated to Ubuntu 11.04, fullscreen crashes Ubuntu. Is there a fix?

---

### Post by allocateB on 2011-05-03
> **penalt said:**
> This just isn't working for me.  I'm pretty new with Linux and I just don't seem to be getting function.  The script doesn't seem to do anything

You'll need to make sure you are running it in terminal, else it will do nothing! 

[QUOTE=mbudden]Interesting. This didn't work in Linux Mint 10 LXDE which is basically like Lbuntu, which is based off of Ubuntu.     [/QUOTE]

again, it may just be that you aren't running it in terminal, if you just have it run by itself it won't do anything because it requires user input. If you run it from terminal you should see the main menu pop up!

---

### Post by ELD on 2011-05-05
Is there a way to get it to work with unity properly at all?

Having a link there in unity and clicking it just makes the icon flash and then it does nothing.

Is it possible to get it to work correctly with KDE menu's as well as the desktop icon?

---

### Post by allocateB on 2011-05-07
[SIZE=3][COLOR=Indigo]UPDATE![/COLOR][/SIZE]
- The script allows you to download and install (or uninstall) the minecraft server client.
- I made a nice little icon for the server launchers.
[IMG]http://i.imgur.com/ugDRM.png[/IMG] << server icon

> **ELD said:**
> Is there a way to get it to work with unity properly at all?

Having a link there in unity and clicking it just makes the icon flash and then it does nothing.

Is it possible to get it to work correctly with KDE menu's as well as the desktop icon?

It should work with unity? heres a video of it doing so, you're problem concerns me though.
[http://www.youtube.com/watch?v=odo6QbdCfeU](http://www.youtube.com/watch?v=odo6QbdCfeU)

It should not create a launcher in the unity quick bar on installation, only on the desktop and in unitys menu system, the launchers that it creates executes this command
```
java -jar /home/username/.minecraft/minecraft.jar
```which is the same command that is executed when you type 
```
:~$minecraft
```into terminal. Try running it from terminal just by typing minecraft and see what the output is, this'll help identify you're problem

Also,
Making the script work with all distros and desktops is next on my to-do list! but right now it's pretty much made for vanilla ubuntu.
The reason it doesn't work well on other desktops and distros:
its assumes apt-get (for java installation)
it assumes compliance with the xdg desktop specifications

However, if you run the script on say... fedora with KDE:
it won't be able to install java for you (fedora uses yum) nor will it create menu launchers for you, BUT, it should still download minecraft and write a shell script in your usr/local/bin directory.

So, regardless of what distro you use, you should at least still be able to run it with just a "minecraft" command from terminal!

---

### Post by ELD on 2011-05-07
I switched recently to Kubuntu so it would be nice to get proper icons for it, that is my main request :)

---

### Post by allocateB on 2011-05-07
> **ELD said:**
> I switched recently to Kubuntu so it would be nice to get proper icons for it, that is my main request :)

I'm going to be setting up a fedora KDE today and will start working on support for Yum and KDE today!

---

### Post by ELD on 2011-05-07
Sweet well keep us updated :)

If you need a little bit of webspace for a mini site i can always help you out just send me a PM :)

---

### Post by mbudden on 2011-05-11
> **allocateB said:**
> again, it may just be that you aren't running it in terminal, if you just have it run by itself it won't do anything because it requires user input. If you run it from terminal you should see the main menu pop up!

Nope. I tried running it by selecting "Open with" and then selecting LXTerminal. Didn't work, nothing runs.

So I use this.

```
:~$ cd /path/to/downloaded/file/
:~$ chmod -x Minecraft_Installer_20.sh
:~$ bash Minecraft_Installer_20.sh
```

And it gets me going, but I encounter errors.
But it looks like I'm going to have to go through and edit your code  since yours is written for Ubuntu running Gnome, & I'm running Ubuntu with LXDE. While Linux Mint 10 LXDE is based off of Ubuntu, there is some quirks as you can see below.

The only thing that works is that it creates the .minecraft folder and that it checks for JAVA. Other than that, downloading the .jar from Minecraft etc doesn't work. 

```
1
.minecraft folder exists

looking for Sun-Java...
Sun-Java is already Installed!
We need to make sure that it is the default Java installation...
Don't worry if you see lots of errors
this requires root access
Usage:
  lxterminal [Options...] - LXTerminal is a terminal emulator

Options:
  -e, --command=STRING             Execute the argument to this option inside the terminal
  --geometry=COLUMNSxROWS          Set the terminal's size
  -l, --loginshell                 Execute login shell
  -t, -T, --title=STRING           Set the terminal's title
  --working-directory=DIRECTORY    Set the terminal's working directory

Sun Java set as Default.

downloading minecraft.jar...
downloaded.

downloading icon...
mv: cannot stat `favicon.png': No such file or directory
saved to /home/mbudden/.minecraft

writing bin shell...
touch: cannot touch `minecraft': Permission denied
Minecraft_Installer_20.sh: line 153: minecraft: Permission denied
saving to usr/local/bin...
this requires root access:
cp: cannot stat `minecraft': No such file or directory
chmod: cannot access `minecraft': No such file or directory
done

writing desktop shortcut...
mkdir: cannot create directory `install_files': Permission denied
Minecraft_Installer_20.sh: line 177: cd: install_files: No such file or directory
touch: cannot touch `alloc-installer.desktop': Permission denied
Minecraft_Installer_20.sh: line 180: alloc-installer.desktop: Permission denied
Minecraft_Installer_20.sh: line 181: alloc-installer.desktop: Permission denied
Minecraft_Installer_20.sh: line 182: alloc-installer.desktop: Permission denied
Minecraft_Installer_20.sh: line 183: alloc-installer.desktop: Permission denied
Minecraft_Installer_20.sh: line 184: alloc-installer.desktop: Permission denied
Minecraft_Installer_20.sh: line 185: alloc-installer.desktop: Permission denied
Minecraft_Installer_20.sh: line 186: alloc-installer.desktop: Permission denied
Minecraft_Installer_20.sh: line 187: alloc-installer.desktop: Permission denied
Minecraft_Installer_20.sh: line 188: alloc-installer.desktop: Permission denied
granting the shortcut excecution permissions...
this requires root access
cp: cannot stat `alloc-installer.desktop': No such file or directory
chmod: cannot access `/home/mbudden/Desktop/alloc-installer.desktop': No such file or directory
done

writing menu item...
touch: cannot touch `alloc-menu.directory': Permission denied
Minecraft_Installer_20.sh: line 201: alloc-menu.directory: Permission denied
Minecraft_Installer_20.sh: line 202: alloc-menu.directory: Permission denied
Minecraft_Installer_20.sh: line 203: alloc-menu.directory: Permission denied
Minecraft_Installer_20.sh: line 204: alloc-menu.directory: Permission denied
done

installing to Applications menu...
xdg-desktop-menu: file 'alloc-menu.directory' does not exist
installed

SUCCESS!

Minecraft has been successfully Downloaded and Installed 
Check your desktop and Applications menu for launchers! 
You can also run it from terminal with a 'minecraft' command! 
contact: alloc@dr.com
Happy Mining!
```

---

### Post by robgraves on 2011-05-11
has anyone tested this with ubuntu 11.04?

---

### Post by robgraves on 2011-05-11
> **robgraves said:**
> has anyone tested this with ubuntu 11.04?

actually it looks like this did work in 11.04 natty narwhal, but i don't have premium access so i can't do anything...yet

---

### Post by ELD on 2011-05-11
Any update on KDE integration?

---

### Post by dean36963 on 2011-05-11
Nice script!

I'm using ubuntu 11.04. I ran the script by marking as executable, double clicking on it and selecting run in terminal.
The script worked fine and I can run minecraft using dash, the icon on the desktop or by typing 'minecraft' in a terminal.

> **ELD said:**
> Having a link there in unity and clicking it just makes the icon flash and then it does nothing.

I added a shortcut to the unity launcher (on the left) by dragging the desktop icon onto it, and minecraft ran the first time I clicked on it, but after closing minecraft, it stops working: If I click on the launcher it flashes, like ELD said, but nothing happens. Clicking again will do nothing either (until you log out and back in again).

I think this might be a bug in unity rather than the install script as I have experienced the same problem when clicking on other launcher items.

If you edit the minecraft main menu entry so that it is an 'application in terminal' it will always work but you will have to put up with two items in the launcher when you are playing minecraft (because the terminal comes up too).

---

### Post by allocateB on 2011-05-12
> **mbudden said:**
> Nope. I tried running it by selecting "Open with" and then selecting LXTerminal. Didn't work, nothing runs.


I find it strange that you don't have permission to create a file and then edit it or make a directory, usually such a task would not require root access, I'd be interested in what happens if you were logged in as root when you ran it.

Also sorry to say that right now this really is only meant for straight up ubuntu with gnome, I'll be trying to get it to work with other distros and desktops in the future.


>  		Any update on KDE integration? 	
Here is where I'm am:
I have it working with KDE right which is nice but at the beginning of the script, the user has to pick which distro and which desktop they are running. The purpose of this script was to make it really easy for people new to linux to get minecraft up and running so I don't want users to have to declare what they have. Right now I am working on getting the script to automatically detect these options.
My life has become really busy now that school is done for summer and all my time is taken up by work. This weekend I hope to have some more time to work on it!

---

### Post by ELD on 2011-05-18
Well i'm actually back on Ubuntu now anyway, so the only thing that bothers my is the iffy support on Unity that the other person in this thread also has.

[https://picasaweb.google.com/liamdawe/GameBugs#5607985535200953346](https://picasaweb.google.com/liamdawe/GameBugs#5607985535200953346)

Thats a shot of what happens, it launches fine but the original launcher flashes and flashes, while the Minecraft window creates another launches which when you quit dissapears back to the old one, very odd behaviour!

---

### Post by mc4man on 2011-05-19
> **ELD said:**
> 
Thats a shot of what happens, it launches fine but the original launcher flashes and flashes, while the Minecraft window creates another launches which when you quit dissapears back to the old one, very odd behaviour!

It's likely that's what will happen with java and some other apps.
The desktop launcher command is not the same as the 'running' command so you'll get a 2nd 'active' icon while the app is open.

What can be done is run these apps from  quicklist entries, though only really useful if you have several similar apps that make sense to place in a single 'category' launcher 
(the launcher is a category, the quicklist entries  are a menu.

If you had a number of java apps the a Java Apps icon to launch any of them would make sense, or if a number of games than a Games launcher, ect.

Here, Atm I have 4, -  Multimedia, Utilities, Graphics & Editors and Home folder icons that provide quick access to around 35 or so apps, scripts, commands and locations.

(very easy to do and shortly a Quicklist Editor app should be done and available

---

### Post by ELD on 2011-05-19
Still a big pain though, i hope the next version of unity handles it a bit better :/

---

### Post by MRoeDesigns on 2011-05-31
I used the installer, and it said it went successfully. But when I try to run it from the terminal it says 

"/usr/local/bin/minecraft: line 1: java: command not found"

and if I try to run it from the shortcut I get

"There was an error launching this application.

Details: Failed to execute child process "java" (No such file or directory)"


It may have something to do with the fact that for some reason my updates haven't been working, and my software center always says it cant connect to the internet. Though if I use sudo to install things it works fine.

---

### Post by allocateB on 2011-06-02
crack open synaptic package manager and check these for installation, it should fix your problem.

sun-java6-jre
sun-java6-bin
sun-java6-plugin

---

### Post by 1111peoy on 2011-06-04
Hey Alloc, check this out;) [http://getminecraft.net/](http://getminecraft.net/) :popcorn:

---

### Post by 1111peoy on 2011-06-04
by the way, a simple web site kit for minecraft fans out there:) [http://getminecraft.net/kit/](http://getminecraft.net/kit/) 
tested and it works on all browsers(IE, chrome, firefox, mobile phones etc)

---

### Post by MRoeDesigns on 2011-06-04
> **allocateB said:**
> crack open synaptic package manager and check these for installation, it should fix your problem.

sun-java6-jre
sun-java6-bin
sun-java6-plugin

Seems to have worked, thank you very much!!

---

### Post by msbealo on 2011-06-24
Thank you very much!!

Who'd have thought that getting a game working with Ubuntu was easier than Windows? I booted into Windows 7 just to install and play Minecraft but was defeated. 

This script was very straight forward. Does anyone know if it would be possible to package it as an Ubuntu package to make it even easier?

Mark

(One complaint.. my last day has just disappeared down a mine shaft! Thanks.)

---

### Post by allocateB on 2011-07-09
> **1111peoy said:**
> hey alloc, check this out;) [http://getminecraft.net/](http://getminecraft.net/) :popcorn:

[size="3"]mi gusta![/size]

---

### Post by dubois928 on 2011-07-23
Ignore, made into new thread here:

[http://ubuntuforums.org/showthread.php?p=11079855](http://ubuntuforums.org/showthread.php?p=11079855)

-Ken

---

### Post by GZ33 on 2011-08-04
> **ELD said:**
> Well i'm actually back on Ubuntu now anyway, so the only thing that bothers my is the iffy support on Unity that the other person in this thread also has.

[https://picasaweb.google.com/liamdawe/GameBugs#5607985535200953346](https://picasaweb.google.com/liamdawe/GameBugs#5607985535200953346)

Thats a shot of what happens, it launches fine but the original launcher flashes and flashes, while the Minecraft window creates another launches which when you quit disappears back to the old one, very odd behaviour!

I  haven't used this installer, but I had the same issue as you after setting up my own shortcut. I fixed it by opening up the shortcut in gedit and adding the following line to get rid of the extra icon:
```
StartupWMClass=net-minecraft-LauncherFrame
```

Then moving the file to /usr/share/applications so it is recognised properly by unity (so the arrows show up, etc).

---

### Post by cocolover76 on 2011-08-08
(Never mind. I got it.)

---

### Post by g123386761 on 2011-09-28
I can't get it to work :l When I right click the file, Terminal isn't an option... I think it's because when I was setting up Ubuntu it asked me if i want to open sh files w/ terminal or gedit. I picked gedit not thinking ahead... So how do I change that??

Thanks in advance!
Gage

---

### Post by g123386761 on 2011-09-29
> **g123386761 said:**
> I can't get it to work :l When I right click the file, Terminal isn't an option... I think it's because when I was setting up Ubuntu it asked me if i want to open sh files w/ terminal or gedit. I picked gedit not thinking ahead... So how do I change that??

Thanks in advance!
Gage
Hey I fixed that... idk how but i did xD... so now when I'm installing minecraft and it's downloading Java JRE it shows some wierd screen... like the about me of the JRE... i hit esc a couple times and it would come right back D:

HELP MEH!

---

### Post by g123386761 on 2011-09-30
> **g123386761 said:**
> Hey I fixed that... idk how but i did xD... so now when I'm installing minecraft and it's downloading Java JRE it shows some wierd screen... like the about me of the JRE... i hit esc a couple times and it would come right back D:

HELP MEH!
fixed :D

---

### Post by EricDownz on 2011-10-01
Uhmm... Make a video or atleast please tell me where to find the main minecraft.jar file? I downloaded it and... Uhh... WHERE DO I PUT THE MODS?!
:P Thanks! 


~ EricDownz

---

### Post by Drat333 on 2011-10-09
I want to start minecraft with more memory with the launcher. How do?

---

### Post by DaimyoKirby on 2011-10-20
I seemed to run into an error of sorts.
When I ran your installer, it installed Sun-Java, OpenJDK, and Minecraft correctly, but when it finished, my desktop turned gray, and I can't right click on it, and I can't see any of the icons on it. So I don't know what's wrong, but maybe someone can point me to a fix (other than re-installing xubuntu) or to something that will help determine the bug/problem.

I'm running on a fresh install of xubuntu 11.10; I've installed the initial updates that come up in the update manager, installed a new video card driver recommended for my card (nVidia), and installed Battle For Wesnoth 1.8 and LibreOffice from the Ubuntu Software Center.

I hope someone can figure this out.

**NOTE:** This has worked successfully in xubuntu 11.04 with no side effects on my laptop before, so it might be a new incompatibility with something in the xubuntu 11.10 package.

**EDIT: **I did just try running it, though, and the game works fine, so as far as I can tell, it seems to currently only be a problem with the desktop. I do need my computer to be able to function properly, though, so I will be reinstalling xubuntu 11.10 (again). Let me know if you want me to try something, and I'll try it from a startup disk.

---

### Post by robbosch on 2011-10-22
Having a similar problem. The script seems to run just fine. But there is no icon created on the desktop and running from Terminal gives: Unable to access jarfile /home/rob/.minecraft/minecraft.jar
I checked permissions and even ran sudo minecraft. But still no go.

Running on oneiric with unity desktop.

Any ideas?

/edit: when I look at permissions after installation, permissions are set for root and not for the user that installed the program. How can root have permission when installed with user credentials?

---

### Post by greenblob on 2011-10-29
Hi,
I've installed this successfully on a fresh install of 11.04 natty 32 bit on a Dell Dimension 5100 with a dual core hyper-threaded 3.1GHZ Intel Pentium 4 processor, 2GB 400mhz DDR2 RAM, and a 256MB ATI RADEON X300SE, so I know my PC is capable of running Minecraft, as I can run a standard FPS with all settings on max and get 40FPS easily.

Minecraft DOES RUN FINE, bit is RIDICULOUSLY laggy though, does anybody know anything I can do to speed it up a bit (in terms of software) please? :(

I also get this message when typing minecraft into terminal. Minecraft runs fine, but there still appears to be some sort of error... :confused::confused::confused:
```
[B][COLOR="Red"]luke@luke-Dimension-5100:~$ minecraft[/COLOR]
[COLOR="RoyalBlue"]java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:460)
	at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
	at java.lang.UNIXProcess.<init>(UNIXProcess.java:148)
	at java.lang.ProcessImpl.start(ProcessImpl.java:65)
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:453)
	... 1 more
java.io.FileNotFoundException: /home/luke/.minecraft/lastlogin (No such file or directory)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(FileInputStream.java:120)
	at net.minecraft.LoginForm.readUsername(LoginForm.java:131)
	at net.minecraft.LoginForm.<init>(LoginForm.java:76)
	at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:30)
	at net.minecraft.LauncherFrame.main(LauncherFrame.java:158)
	at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:36)
17 achievements
161 recipes
Setting user: private, -1260345861567849824
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event11): Failed to open device /dev/input/event11 (13)

Failed to open device (/dev/input/event10): Failed to open device /dev/input/event10 (13)

Failed to open device (/dev/input/event9): Failed to open device /dev/input/event9 (13)

Failed to open device (/dev/input/event8): Failed to open device /dev/input/event8 (13)

Failed to open device (/dev/input/event7): Failed to open device /dev/input/event7 (13)

Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers[/COLOR]

[COLOR="Lime"]Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.[/COLOR]

[COLOR="RoyalBlue"]New max size: 400
New max size: 784
New max size: 1764
New max size: 5476
New max size: 18496
New max size: 19044[/COLOR]
[COLOR="DarkOrange"]Stopping![/COLOR]
[COLOR="Lime"]AL lib: ALc.c:1352: exit(): closing 1 Device
AL lib: ALc.c:1329: alcCloseDevice(): destroying 1 Context
AL lib: alSource.c:2361: alcDestroyContext(): deleting 32 Source(s)[/COLOR]
[COLOR="Red"]luke@luke-Dimension-5100:~$ [/COLOR][/B]

```

**[SIZE="4"]Thanks For Any Help[/SIZE]** :KS:KS:KS

---

### Post by iamjagman on 2011-12-13
Minecraft won't run. I get this message in the terminal:

```
27 achievements
174 recipes
Setting user: iamjagman, -3541158989659340236
failed to create drawable
org.lwjgl.LWJGLException: X Error - disp: 0x28bbf60 serial: 94 error: BadGC (invalid GC parameter) request_code: 60 minor_code: 0
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
	at org.lwjgl.opengl.LinuxKeyboard.nSetDetectableKeyRepeat(Native Method)
	at org.lwjgl.opengl.LinuxKeyboard.setDetectableKeyRepeat(LinuxKeyboard.java:152)
	at org.lwjgl.opengl.LinuxKeyboard.destroy(LinuxKeyboard.java:163)
	at org.lwjgl.opengl.LinuxDisplay.destroyKeyboard(LinuxDisplay.java:1015)
	at org.lwjgl.input.Keyboard.destroy(Keyboard.java:349)
	at org.lwjgl.opengl.Display.destroyWindow(Display.java:350)
	at org.lwjgl.opengl.Display.create(Display.java:867)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at net.minecraft.client.Minecraft.a(SourceFile:205)
	at net.minecraft.client.Minecraft.run(SourceFile:644)
	at java.lang.Thread.run(Thread.java:636)
java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
	at org.lwjgl.opengl.Display.create(Display.java:846)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:237)
	at net.minecraft.client.Minecraft.run(SourceFile:644)
	at java.lang.Thread.run(Thread.java:636)

```

---

### Post by martinix97 on 2011-12-17
hi,
i realy like this game:D, so thanks for the script. while i was playing i notest a bug.:( when i use the F11 fullscreen utility, i can't look in every direction, instead of lookining 360º i can only see 180º.
thanks for the atencion and the script.

ps:srry by the bad inglish but im portugues and im only 14.

---

### Post by ExpL0it0R on 2011-12-23
When you press F11 and go into full screen, press escape twice and you will be able to.

---

### Post by metalinspired on 2012-01-08
Thank you sooooo much

---

### Post by Hekabe on 2012-01-12
Is it possible to play the game offline using the infrastructure set up by this script?

---

### Post by zack346 on 2012-01-21
When I tried to use it, it worked and downloaded minecraft, but it never let me use it.
I said the error because it failed to download the child process java... is there anything i can do to still make it work???         :confused:

---

### Post by Oneanimefan on 2012-01-26
THANK YOU I HAVE A UBUNTU COMP. FOR MY SCHOOL AND I SOOO WANTED TO PLAY MINECRAFT! only one problem, when i try to "play minecraft" it says

Invalid or corrupt jarfile /home/user/.minecraft/minecraft.jar


IM SO MAD :mad: plz help!!!! [-o<

---

### Post by regor210 on 2012-01-26
As of Ubuntu 11.10 sun-java is not in the repositories.
Sun was bought out by Oracle. Oracle has a shaky relationship with the open source community.
So Java 7 is Oracle Java and is not in are repositories.
The good news is before Oracle bought out Sun, Sun made Java open source as in OpenJDK.
Ubuntu uses OpenJDK. The bad news is Minecraft runs best using sun-java. The bash script you are using was made for earlier versions of Ubuntu that had sun-java in there repositories.

Ubuntu recommends  
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

The bash script your using calls for 

$ sudo apt-get install sun-java6-jre sun-java6-plugin
$ sudo update-java-alternatives -s java-6-sun

I think it can be found here.
[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

---------------------------------------------------------------------
Alternately  

Many of us use this ppa  
[http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric](http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric)

The problem is who is ferramroberto. Getting software and updates from who know where poses a security risk. 

I use his repositorie but after installing Mincraft I goto Ubuntu software source > Other Software and I disable ferramroberto ppa's to some what minimize the risk.

---

### Post by Oneanimefan on 2012-01-27
??? what i dont really understand, sorry could you just explain without using terms i dont understand XD sorry i dont understand code (but i understand geek :lolflag:) ya
TYTYTYTYTYTYTYTY!

---

### Post by regor210 on 2012-01-27
If your using the newest Ubuntu 11.10  Oneiric Ocelot, this is what I would do.
Assuming you downloaded the installer and ran this 

$ cd \Downloads 
$ chmod -x Minecraft_Installer_20.sh

Run this in a terminal. 

$ sudo add-apt-repository ppa:ferramroberto/java
$ sudo apt-get update
$ cd \Downloads 
$ bash Minecraft_Installer_20.sh

---

### Post by BlasterMaster555 on 2012-01-31
Installer script doesn't check for a manual installation of Java 7 JRE. "Cheated" the system by not entering in rot password until it thought Java was installed, then continued setup as normal. Works fine.

For users having problems with Minecraft not starting up (black screen after login or CTD), you need to update the LWGJL systems.

[http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.3/](http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.8.3/)

After downloading the package, unzip and replace the jars in the .minecraft/bin folder with updated versions, jinput.lar, lwjgl.jar, lwjgl-util.jar, then go to native/linux and copypasta ALL the .so files into the .minecraft/bin/native folder. Now Minecraft will run again.

Future versions of Minecraft will use the updated LWJGL system - it doesn't now because some users have odd system configurations that don't work with it.

---

### Post by allocateB on 2012-02-02
Thanks for all the nice posts and emails everyone!

I'm checking up on this after a loooong time away and see that some problems have come up. I'll try to update the script and fix the bugs caused from the sun-java stuff. If anyone one wants to help out, PLEASE DO! Everything the script does is written in a certain function so it should be pretty easy to find. 

Hopefully I'll get it worked out soon, but for now, time for more homework.

---

### Post by Oneanimefan on 2012-02-03
sry but im still confused by this stuff still, terminal? Ubuntu 11.10  Oneiric Ocelot?
AH! going insane out of confusion

---

### Post by regor210 on 2012-02-03
If your using the newest Ubuntu 11.10 Oneiric Ocelot just click on the Ubuntu icon on the upper left side of your desk top and type term in the search window to bring up your terminal options. Any of them should work fine.

After you have a terminal open just cut and past or type in the line you would like to run minus the $ 

The problem is Minecraft is telling us.
[http://www.minecraft.net/download](http://www.minecraft.net/download)
Minecraft for Linux / Other

Download minecraft.jar (89 KB). The jar is executable and might work as-is. If you run into memory issues, try launching it with java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame, also **please use Sun's JVM**.

Others are saying

- As of August 24th 2011, Canonical no longer have permission to redistribute new Java packages as Oracle has retired the &#8220;Operating System Distributor License for Java&#8221;.
- Oracle has published an advisory about security issues in the version of Java currently in the partner archive. Some of these issues are currently being exploited in the wild.
**- Due to the severity of the security risk**, Canonical released a security update for the Sun JDK browser plugin which disables the plugin on all machines.

Knowing the risk, this is what I would do.

1st download the installer using the link provided. 

$ sudo apt-add-repository ppa:flexiondotorg/java

$ sudo apt-get update

$ cd \Downloads 

$ chmod -x Minecraft_Installer_20.sh

$ cd \Downloads 

$ bash Minecraft_Installer_20.sh

---

### Post by ethanzh on 2012-02-05
Hi, I am experiencing this error while starting with terminal

ethanzh@ubuntu:~$ minecraft
java.io.IOException: Cannot run program "javaw": error=2, No such file or directory
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:1029)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: error=2, No such file or directory
    at java.lang.UNIXProcess.forkAndExec(Native Method)
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:135)
    at java.lang.ProcessImpl.start(ProcessImpl.java:130)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:1021)
    ... 1 more

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


I also get a black screen after login whenever i use the launcher... Any fix?

Thanks.

btw im on Ubuntu 12.04 and MC 1.1

---

### Post by regor210 on 2012-02-05
[http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line](http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line)


There was a bug in Ubuntu 11.10, see if this is installed?

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install gtk2-engines-pixbuf

---

### Post by Oneanimefan on 2012-02-10
this is becoming too complicated i dont know if i will use this entirely...
but before i ditch this, could some one help me find a download that doesn't require me to go to minecraft.net because i can't do that on this computer D:dont ask.....

---

### Post by regor210 on 2012-02-10
Do you have permission? The administrator can see everything you do or did. Don't get your self in trouble! 

If you do have permission, how about going to 

[http://www.minecraft.net/download](http://www.minecraft.net/download)

on a friends computer and placing minecraft.jar on a flash drive or get a free Ubuntu One account and place minecraft.jar in it to access it anyplace.

[https://one.ubuntu.com/](https://one.ubuntu.com/)

Back in Ubuntu
Just right click on 
minecraft.jar
select **Properties**
select **Permissions**
mark X **Make the file executable**

Then just double click on  minecraft.jar to run it.
if it will not run
right click 
minecraft.jar
select **open with**
select **Custom Command line**
type in
**java -jar**
slect **ok**
 


Note. Torrents or a Tor enabled Browser is likely to get you kick out of school on your bum! So there not recommended.

---

### Post by memzak on 2012-02-12
Wow, this is extremely useful, pity I never found it earlier. I ended up writing my own sh... but then again I personally edited it on whether to start minecraft up using a proxy server to connect to the internet or not depending on location... BUT if I didn't need that, this download would have saved me a lot of time.

---

### Post by manij on 2012-03-17
HWne i try to install it i get this error

[B][I]XXXX@XXXXX-desktop:~/Desktop# bash Minecraft_Installer_20.sh
Minecraft_Installer_20.sh: line 1: syntax error near unexpected token `newline'
Minecraft_Installer_20.sh: line 1: `<br />'[/I][/B]


Help please!

---

### Post by regor210 on 2012-03-17
This bash script is old.
You don't want to use it with Xubuntu.
And you need to get a Java PPA before you use it.

Minecracft uses Sun Java 6 and recommends its use.
Ubuntu uses java-6-openjdk.
The easiest way to install Sun Java 6 is using a non Ubuntu repository or PPA. Non Ubuntu repositories can pose a security risk because your getting software and updates from who knows where. 
That said some of us are using this PPA 
[http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric](http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric)

---

### Post by manij on 2012-03-17
> **regor210 said:**
> This bash script is old.
You don't want to use it with Xubuntu.
And you need to get a Java PPA before you use it.

Minecracft uses Sun Java 6 and recommends its use.
Ubuntu uses java-6-openjdk.
The easiest way to install Sun Java 6 is using a non Ubuntu repository or PPA. Non Ubuntu repositories can pose a security risk because your getting software and updates from who knows where. 
That said some of us are using this PPA 
[http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric](http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric)

Regor, 

i get the login page and i encounter some sort of fatal error when i try to login. here is bit of the error log


[B][I]#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb3757ef6, pid=7328, tid=3017542512
#
# JRE version: 6.0_31-b04
# Java VM: Java HotSpot(TM) Client VM (20.6-b01 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [libGL.so.1+0x65ef6]  XF86DRIQueryExtension+0x8e
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#[/I][/B]

---

### Post by regor210 on 2012-03-17
I think you have 2 threads going here.

Looks like your ATI video drivers may be the problem.

Run these in a terminal minus the $ 

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install mesa-utils


Now run these in terminal and post what you get.
video driver 3D test FPS

$ glxgears

video card and driver information

$ lspci -vmk | grep -A 8 -B 2 VGA

System information 
$ uname -a
$ lsb_release -a

Here's a thread with a similar issue. 
[http://ubuntuforums.org/showthread.php?t=1639074](http://ubuntuforums.org/showthread.php?t=1639074)

The simple answer is how attached are you to your ATI property drivers?  

Blitaxos said
&#8220;Hey there! I recently had a similar problem where using either sun or open jdk minecraft would simply close itself when I tried starting a level. The same problem occurred in ubuntu 10.10 as well as 11.04. 

But I FIXED IT 

I finally noticed in the scripts that it was having a graphics issue - so all I did was remove my graphics driver (ATI/AMD proprietary FGLRX graphics driver). And minecraft started working 

Good luck, I hope this applies to your issue as well.&#8221;

Blitaxos un-installed his ATI  property driver and the open source ATI drivers worked for him.

If you show us your hardware we may ba able to find you a better answer.

---

### Post by manij on 2012-03-17
**I think you have 2 threads going here.**

Regor, thanks for your help. Minecraft stopped working and my son is driving me crazy!

**Looks like your ATI video drivers may be the problem.**

I removed the ATI driver, but i still have a graphics problem in both sun java 6 and the open jdk. this time it is actually in the minecraft window. it reads

[B][I]--- BEGIN ERROR REPORT 7cf3a456 --------
Generated 3/17/12 5:51 PM

Minecraft: Minecraft 1.2.3
OS: Linux (i386) version 2.6.32-39-generic
Java: 1.6.0_20, Sun Microsystems Inc.
VM: OpenJDK Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Could not choose GLX13 config
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:230)
	at net.minecraft.client.Minecraft.run(SourceFile:650)
	at java.lang.Thread.run(Thread.java:636[/I][/B])
--- END ERROR REPORT 59307d06 ----------

the output you asked for 
[B][I]
$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14[/I][/B]


video card and driver information
[B][I]$  lspci -vmk | grep -A 8 -B 2 VGA

Device: 01:05.0
Class:  VGA compatible controller
Vendor: ATI Technologies Inc
Device: 760G [Radeon 3000]
SVendor:        Lenovo
SDevice:        Device 3600
Driver: fglrx_pci
Module: radeon

Device: 01:05.1[/I][/B]


System information 
[B][I]$ uname -a
Linux manij-desktop 2.6.32-39-generic #86-Ubuntu SMP Mon Feb 13 21:47:32 UTC 2012 i686 GNU/Linux[/I][/B]
[B][I]
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:        10.04
Codename:       lucid[/I][/B]

[B]
The simple answer is how attached are you to your ATI property drivers?  [/B]

Not very!

Help me please!

---

### Post by regor210 on 2012-03-17
You don't have 3D support with the open source drivers.

Here is what you are looking for. 
[http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/](http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/)
How-to Install Minecraft in*Ubuntu

Scroll down to 
How-to install ATI Catalyst Video Drivers:

looks like you need you need to download 32-bit drivers

---

### Post by scrub jay on 2012-03-18
> **manij said:**
> HWne i try to install it i get this error

[B][I]XXXX@XXXXX-desktop:~/Desktop# bash Minecraft_Installer_20.sh
Minecraft_Installer_20.sh: line 1: syntax error near unexpected token `newline'
Minecraft_Installer_20.sh: line 1: `<br />'[/I][/B]


Help please!

> **regor210 said:**
> This bash script is old.
You don't want to use it with Xubuntu.
And you need to get a Java PPA before you use it.

Minecracft uses Sun Java 6 and recommends its use.
Ubuntu uses java-6-openjdk.
The easiest way to install Sun Java 6 is using a non Ubuntu repository or PPA. Non Ubuntu repositories can pose a security risk because your getting software and updates from who knows where. 
That said some of us are using this PPA 
[http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric](http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric)

Ok, I've used this script in the past to install Minecraft with no problems on Kubuntu and Xubuntu boxes. Today, I downloaded the script via the File Dropper link (couldn't find the usb I have it saved on :confused:) and received the same "***syntax error near unexpected token `newline" ***as manij. The script has changed for whatever reason. No problem, just open the script with gedit or whatever text editor is comfortable to you and replace the text with the script [allocateB]("http://ubuntuforums.org/member.php?u=1278008") posted in his original post (or copy and paste into a new editor screen and save). I did this a few mins. ago on a Mint Debian Xfce box with no issues.

---

### Post by lordboobatron on 2012-03-25
when i try to run this, the terminal will open up for a split second and then close. nothing seems to happen, no minecraft or .minecraft folder.

---

### Post by regor210 on 2012-03-26
Asuming Minecraft_Installer_20.sh is in your Downloads file.

Could you run these in terminal and post the output if it does not work?


Howto
If your using the newest Ubuntu 11.10 Oneiric Ocelot just click on the Ubuntu icon on the upper left side of your desk top and type term in the search window to bring up your terminal options. Any of them should work fine.

After you have a terminal open just cut and past or type in the line you would like to run minus the $ 

$ cd ~/Downloads/ && chmod -x Minecraft_Installer_20.sh

$ cd ~/Downloads/ && bash Minecraft_Installer_20.sh

$ java -jar /home/reg/.minecraft/minecraft.jar

---

### Post by Gadzevsky on 2012-03-26
Make sure to download the installer from the video tutorial above becouse the script from this link is messed up

---

### Post by regor210 on 2012-03-27
The

Download Link:HERE

does not install Minecraft!!!!!

**Please do not use this Bash script!!!!!!!!**

The 
Download Link:HERE
is broken. And this Bash script has a missing dependency. As Sun Java 6 is no longer found in the Ubuntu repositories. Minecraft runs on Sun Java 6 and recommends its use. Sun Java 6 has some security issues as it was replaced with Oracle Java 7. In Minecraft Oracle Java 7 works fine except you have to update  LWJGL by hand.   
[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)

So if you want to use this bash script you will have to cut and past everything in the  #!/bin/bash window scrolling all the way down, into a text editor and save it as Minecraft_Installer_20.sh and place it in your Download folder.

And you will need Sun Java 6. knowing the risk some of us are using this PPA that is outside the Ubuntu repositories. 

[http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric](http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric)

---

### Post by efflandt on 2012-03-27
People seem to be making this more complicated than it needs to be.

I have been running Minecraft in Linux since I think 1.8 beta in 64-bit 11.10 and subsequent snapshots and releases with no major problems using the default openjdk installed by **ubuntu-restricted-extras**.  MC 1.2.3 had occasional freeze issues in SMP (survival multi-player), but people had those issues in Windows too using Sun Java.  At least in Linux it eventually thaws, although, if it freezes too long you get disconnected from the server.  I don't remember having that issue in MC 1.2.4 yet, which runs smoother even if it is so busy that rendering is delayed (especially jungles).

If you create a **bin** directory in your home directory, once you log out of X and log back in, that directory is in your $PATH.  Then you can create a script in that bin called **minecraft** something like this:

```
#!/bin/sh
# Change cd line to your path to orig minecraft.jar, NOT ~/.minecraft/bin
cd ~/MC-client
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```It does not matter which version minecraft.jar you use to launch it, just that it is a complete minecraft.jar with the launcher, not one from .minecraft/bin, nor a prerelease snapshot (which you have to put in .minecraft/bin).

Although if you have the RAM, 1.2 versions work better with **-Xmx2G -Xms2G** because when I use that I have sometimes seen it use more than 1 GB which would keep more in RAM instead of having to reload data.

Then for a Unity launcher in Dash search for "main menu" (which should come up after you type **main**) and add something to launch the **minecraft** script **in a terminal**.  Once you launch it from Dash you can check **Keep in launcher**.

For an icon I use [IMG]http://efflandt.freeshell.org/img/minecraft.png[/IMG] or for the server I use [IMG]http://efflandt.freeshell.org/img/minecraft-server.png[/IMG]

I did update the **lwjgl** version in the .minecraft directory to 2.6, because the 2.4 version that comes in minecraft (which may be changed soon) occasionally results in stuck movement keys (or press same key in direction you are moving to unstick it).  That requires replacing a bunch of files in different paths with the newer versions.

When a new version comes out and I want to be able to run both versions, I just copy the entire .minecraft directory with a number appended representing the version, for example I copied it to .minecraft-123 before updating minecraft to 1.2.4.  Then to switch versions, I run this **mineswitch** script (modify MINEA and MINEB for new versions):

```
#!/bin/bash

DIR="/home/efflandt"
MINE=".minecraft"
MINEA=".minecraft-123"
MINEB=".minecraft-124"

cd $DIR
ls -la |grep minecraft
if [ -d "$MINEA" ]; then
 echo "** Switching to 1.2.3"
 mv $MINE $MINEB && mv $MINEA $MINE
elif [ -d "$MINEB" ]; then
 echo "** Switching to 1.2.4"
 mv $MINE $MINEA && mv $MINEB $MINE
fi
```As I mentioned earlier, the minecraft.jar you use for the launcher does not matter, because it will launch whatever is in an existing .minecraft directory.

And if you are looking for a *nix friendly place to play, check out [http://sdf.lonestar.org/](http://sdf.lonestar.org/)

They run NetBSD on their shell accounts, but I think their MC servers run on Ubuntu.  They have 5 worlds on their main Bukkit server (currently running 1.2.3), another server running most recent vanilla version (currently 1.2.4 on a 1.1 world), and a development server for testing or fixing Bukkit plugins before updating the main server (currently running a 1.2.4 world).

I thought if I looked like one they might ignore me.  Nah.

[IMG]http://efflandt.freeshell.org/img/spider-av150.png[/IMG]

---

### Post by alfonsojon on 2012-03-31
I will be updating the shell script to use the OpenJDK-JRE-7 package as I found that is stable enough. I may also create a LWJGL updater script while I'm at it.

I'll post it on here soon, sorry for the wait guys :P

---

### Post by alfonsojon on 2012-03-31
I  am separating the Server install script and the Client install script in case someone hits the wrong number and accidentally chooses the wrong option. I am also rewriting the scripts from scratch (using the first as reference), should now detect any form of Java, OpenJDK or Java official, 5, 6, or 7. 

I'm about 50% done with the client script, have yet to start on the server script :(

I'm also trying to get it to not require root access and install to your local user account.

---

### Post by regor210 on 2012-03-31
Thanks for your hard work, it will be appreciated.

---

### Post by alfonsojon on 2012-03-31
> **regor210 said:**
> Thanks for your hard work, it will be appreciated.

No problem. I have the installer code re-written, no longer uses a combination of local user files and global system files, it installs a menu item to /usr/share/applications/mojang-Minecraft.desktop (how it should be), and I am done writing the installer portion. Now I just have to write the uninstaller portion and modify it to install Minecraft Server (maybe even bukkit :) )

---

### Post by alfonsojon on 2012-03-31
> **alfonsojon said:**
> No problem. I have the installer code re-written, no longer uses a combination of local user files and global system files, it installs a menu item to /usr/share/applications/mojang-Minecraft.desktop (how it should be), and I am done writing the installer portion. Now I just have to write the uninstaller portion and modify it to install Minecraft Server (maybe even bukkit :) )

Forgot to mention I'll try to package it up as a .deb when I learn how and submit it to Mojang :)
EDIT: Scratch local user only, that can be a minor hazard when it comes to accidentally deleting things so I made it go where any other program would go - /usr/local/bin for the "minecraft" shell script (to type minecraft in the terminal to launch it) and /usr/share/applications/ for the launcher icon. Hopefully I release it in the next few hours, I'm sure it could be useful to many :)

---

### Post by alfonsojon on 2012-04-01
And the moment you've all been waiting for - The client installer!
I tested this at least 20 times and I am 100% confident it works on any Debian-based OS (including Ubuntu :D).

You can download it here:
[www.live-craft.com/mifu]("http://www.live-craft.com/mifu") (Minecraft installer for Ubuntu)

I hope you guys like it (and if you can, donate once I get a Paypal tomorrow)

I'll be busy rewriting the server install portion to support Bukkit, the default server software, and maybe MCForge for those who want to go classic :)

Enjoy!

---

### Post by alfonsojon on 2012-04-02
> **regor210 said:**
> The

Download Link:HERE

does not install Minecraft!!!!!

**Please do not use this Bash script!!!!!!!!**

The 
Download Link:HERE
is broken. And this Bash script has a missing dependency. As Sun Java 6 is no longer found in the Ubuntu repositories. Minecraft runs on Sun Java 6 and recommends its use. Sun Java 6 has some security issues as it was replaced with Oracle Java 7. In Minecraft Oracle Java 7 works fine except you have to update  LWJGL by hand.   
[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)

So if you want to use this bash script you will have to cut and past everything in the  #!/bin/bash window scrolling all the way down, into a text editor and save it as Minecraft_Installer_20.sh and place it in your Download folder.

And you will need Sun Java 6. knowing the risk some of us are using this PPA that is outside the Ubuntu repositories. 

[http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric](http://superuser.com/questions/353983/how-do-i-install-the-sun-java-sdk-in-ubuntu-11-10-oneric)
This is fixed in my updated version of the Minecraft installer. I don't want to force it upon anybody, but I highly recommend using mine rather than the version that was originally made about a year ago.

---

### Post by regor210 on 2012-04-03
**To install Mincraft** goto
[http://www.live-craft.com/mifu](http://www.live-craft.com/mifu)

and click on 
**Download :D**

to download mifu.sh

Then open a terminal ctrl+alt+t cut and paste the following commands into the terminal window one line at a time minus the $.

$ cd ~/Downloads/ && chmod -x mifu.sh

$ cd ~/Downloads/ && bash mifu.sh

press 1 to install minecraft.

After the installation there will be a launcher in your games menu.

Note. if you are using Ubuntu 12.04 you have to update LWJGL by hand or you will get a black screen when loading the game. 

[http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tutorials/Update_LWJGL)

---

### Post by davidgillen on 2012-04-15
The [http://www.live-craft.com/mifu](http://www.live-craft.com/mifu) appears not to be working. Is the mifu.sh script hosted anywhere else, github or similar perhaps?

---

### Post by regor210 on 2012-04-15
I don’t know what happened there, the Download page is gone.

You could try installing Minecraft by hand.

 [http://ubuntuforums.org/showthread.php?t=1812767](http://ubuntuforums.org/showthread.php?t=1812767)

---

### Post by alfonsojon on 2012-04-30
My apologies, our ISP started throttling my upload speeds so I had to temporarily shut down the web server, so I'll be uploading it to dropbox shortly, sorry guys :(

---

### Post by alfonsojon on 2012-04-30
[http://dl.dropbox.com/u/54213557/MIFU/mifu.sh](http://dl.dropbox.com/u/54213557/MIFU/mifu.sh)

There, sorry for the 2 week delay :(

---

### Post by regor210 on 2012-04-30
Grate installer thanks alfonsojon.

---

### Post by alfonsojon on 2012-04-30
Thanks :D and I'm updating it right now to add support for installing servers such as the default server, Bukkit, or MCforge.

---

### Post by JoeA42 on 2012-05-18
Hello ive installed minecraft using this installer before and i ran perfectly but due to some issues with my desktop (i broke unity) i had to install ubuntu all over again, and this time when i downloaded the file it seems that it was corrupted so what i did was copy the script from the page and replace the script from the file, and the installer ran, and i was able to install minecraft, but i click the icon and nothing happens it just lits up and then does nothing again, and if a try to run from terminal but it said there is no such program, if anybody knows what the problem migth be i would really apreciate the help, the previous setup was ubuntu 11.10 upgraded to 12.04 64 bit version,and now im running a 32 bit version of 12.04 installed from a live cd thanks in advance.

---

### Post by JoeA42 on 2012-05-18
> **JoeA42 said:**
> Hello ive installed minecraft using this installer before and i ran perfectly but due to some issues with my desktop (i broke unity) i had to install ubuntu all over again, and this time when i downloaded the file it seems that it was corrupted so what i did was copy the script from the page and replace the script from the file, and the installer ran, and i was able to install minecraft, but i click the icon and nothing happens it just lits up and then does nothing again, and if a try to run from terminal but it said there is no such program, if anybody knows what the problem migth be i would really apreciate the help, the previous setup was ubuntu 11.10 upgraded to 12.04 64 bit version,and now im running a 32 bit version of 12.04 installed from a live cd thanks in advance.
i did not noticed that there was a troubleshooting option, i reinstalled sun java and open jdk and it works now, sorry for the hassle

---

### Post by Enkouyami on 2012-07-03
I have a complete, up-to-date, regularly updated _[Bash Minecraft Installer]("http://ubuntuforums.org/showthread.php?p=12072979")_ that automates EVERYTHING, even tasks such as updating the LWJGL. The reason some of you haven't seen it is because I only had _[it on the MC forums.]("http://www.minecraftforum.net/topic/1114574-complete-ubuntu-installer-script-v14-updated-3-july-2012/")_

---

### Post by Zenyx on 2012-07-22
Thank you so much!!!  That was driving me crazy!

---

### Post by cindy1990 on 2012-07-24
Details: Failed to execute child process "java" (No such file or directory)

this is what happens when i try to open minecraft..how can i fix it

---

### Post by cindy1990 on 2012-07-24
it opens now BUT i get a black screen after i sign in :(

nevermind i fixed it! thank you!

---

### Post by regor210 on 2012-07-24
Minecraft on Ubuntu 12.04 

On Ubuntu 12.04 you have to update the Lightweight Java Game Library or you will get a black screen.

Sorry [http://modifyubuntu.com/#minecraft](http://modifyubuntu.com/#minecraft) is out of date due to lwjgl-2.8.4. Sorry again but this is a bit long. 

To open a terminal press ctrl+alt+t all at the same time. Then cut and paste the following commands into the terminal window one line at a time minus the $. 

#make sure you have Openjdk-7 and all the Openjdk-7 extensions. 

$ sudo apt-get update 

$ sudo apt-get upgrade 

$ sudo apt-get install ca-certificates-java icedtea-7-jre-cacao icedtea-7-jre-jamvm java-common libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common libgnome2-0 libgnomevfs2-0 libgnomevfs2-common openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib ttf-dejavu-extra tzdata-java 

Download minecraft.jar from here. 
[http://www.minecraft.net/download](http://www.minecraft.net/download) 

Download the Lightweight Java Game Library or lwjgl from here 
[http://sourceforge.net/projects/java...d?source=files](http://sourceforge.net/projects/java...d?source=files) 

If you haven’t yet run Minecraft and log in, it will automatically create the folder .minecraft in your home folder. Note. You will get a black screen. Here's how. 

------------------------------------------------ 

$ cd ~/Downloads 

$ sudo chmod a+x minecraft.jar 

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame 
------------------------------------------------- 
Close Minecraft 

In Ubuntu 12.04 you have to update lwjgl by hand due to Java 7 or Openjdk-7. You can go here or read down and use the command line. 

Lightweight Java Game Library download 

[http://www.minecraftwiki.net/wiki/Tu...s/Update_LWJGL](http://www.minecraftwiki.net/wiki/Tu...s/Update_LWJGL) 


The command line. 

Then open a terminal ctrl+alt+t cut and paste the following commands into the terminal window one line at a time minus the $. 
------------------------------------------------------------------------------ 
#update LWJGL 
# Note. lwjgl-2.8.4.zip will change over time as updates become available. so you will have to change the names as needed. 
# 4-29-2012 the Minecraft version is 1.2.5. When version 1.2.6 comes out its likely you will have to update lwjgl by hand again. Word is, when Minecraft hits version 2.0 they will switch to Java 7 and you will not need to update lwjgl by hand any more. 

# update lwjgl by replacing these 9 files 

$ cd ~/Downloads 

$ unzip lwjgl-2.8.4.zip 

# type A for all 

$ sudo cp -f ~/Downloads/lwjgl-2.8.4/jar/jinput.jar ~/.minecraft/bin/jinput.jar 
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/jar/lwjgl_util.jar ~/.minecraft/bin/lwjgl_util.jar 
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/jar/lwjgl.jar ~/.minecraft/bin/lwjgl.jar 


$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/libjinput-linux.so ~/.minecraft/bin/natives/libjinput-linux.so 
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/libjinput-linux64.so ~/.minecraft/bin/natives/libjinput-linux64.so 
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/liblwjgl.so ~/.minecraft/bin/natives/liblwjgl.so 
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/liblwjgl64.so ~/.minecraft/bin/natives/liblwjgl64.so 
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/libopenal.so ~/.minecraft/bin/natives/libopenal.so 
$ sudo cp -f ~/Downloads/lwjgl-2.8.4/native/linux/libopenal64.so ~/.minecraft/bin/natives/libopenal64.so 

# close the terminal. 
# Open a new terminal ctrl+alt+t 

------------------------------------------------------------------------------------ 
#make sure everything has permission for you to run it. 

$ sudo chmod -R 777 .minecraft 

$ cd ~/Downloads 

$ sudo chmod a+x minecraft.jar 

$ java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame 

Note. if you have 2GB or more ram on your mother board you may get better performance by alocating more ram to Minecraft. $ java -Xmx1048M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame 

After this you can goto your Downloads folder right click on minecraft.jar, scroll down to properties. Use the slider named Open with and select OpenJDK Jave 7 Runtime. Click OK.

Now you can start Minecraft by double clicking the minecraft.jar icon, you can pick it up with your mouse and move it to your desktop if you like.

If you still have problems, sometimes Ubuntu’s 3D desktop effects has issues with Minecraft. You could try logging out of your Desktop, select Unity 2D then log back in.

---

### Post by ActionParsnip on 2012-08-17
May want to review the java install using this:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by howard09 on 2012-11-17
Hey i am having trouble logging in..  I watched the video and everything, it downloads fine and i get the icon but once you click the icon and the minecraft screen pops up and it asks for your account info it says login failed idk whats wrong..   i have uninstalled then re installed and still getting login failed..  any ideas?

---

### Post by ubudog on 2012-11-17
> **howard09 said:**
> Hey i am having trouble logging in..  I watched the video and everything, it downloads fine and i get the icon but once you click the icon and the minecraft screen pops up and it asks for your account info it says login failed idk whats wrong..   i have uninstalled then re installed and still getting login failed..  any ideas?

It might be Mojang's (creators of Minecraft) servers having issues.  According to [http://isminecraftdown.net/]("http://isminecraftdown.net/"), minecraft.net seems to be up.  What about now?

---

### Post by ctrlaltnarwhal on 2012-11-26
Hey I love your installer but I've noticed that A. this installer really screws up XFCE installs. B. it only can install OpenJDK 
I took a little time and reworked the script so that it works with XFCE as well as any other flavor of Ubuntu by removing the launcher option. You can still launch Minecraft with [FONT=Courier New]minecraft[/FONT] from your console. I also added the ability to install Sun-Java which I find works better with Minecraft. That feature is still a little rough around the edges.  Uninstalls and the debugging feature are still fully functional. 

Here's a download: [http://dl.dropbox.com/u/26498135/installer.sh](http://dl.dropbox.com/u/26498135/installer.sh)

---

### Post by alfonsojon on 2012-12-22
I've been working on an updated, fully re-written installer. I'll post here when it's ready :)

(FYI, I separated the server installer from the client installer; they will be separate scripts :D)

---

### Post by IsaacJGL on 2012-12-23
I think that this is a bit too much, all I do with minecraft is put the .jar file on my desktop, double click on it, and vwalla, perfect minecraft, without several lines of code and having to type minecraft each time I want to play :P

---

### Post by MestreLion on 2013-03-17
> **IsaacJGL said:**
> I think that this is a bit too much, all I do with minecraft is put the .jar file on my desktop, double click on it, and vwalla, perfect minecraft, without several lines of code and having to type minecraft each time I want to play :P

That's all it takes for some people, Isaac, *when you have the requirements* already set up. In your case, you already had Java installed and working fine. You also have manually downloaded the .jar., placed it in desktop (equivalent to creating a launcher). Your desktop also had a convenient .jar->java file open association, and the default parameters worked fine. Now add a nice icon and that's what most basic install scripts will do.

It worked for you, it works for some, perhaps even for most, but not for everyone. Some require a few tweaks and workarounds. And that's what some install scripts try to do. Some also add nice features like mod management.

---

### Post by MestreLion on 2013-03-27
I'm sure Alloc had the best intentions and spent countless hours developing his script, so kudos for being so helpful towards the community, it was indeed an admirable effort.

But the code itself has dozens of the worse Bash programming practices.. so while it may work for most, and I'm sure it saved the day of many Minecraft players, I really do not recommend using it or learning from it.

A few examples:

- /home/$(whoami)/some/dir instead of "$HOME/some/dir". Not all users have their $HOME at /home/<user>, and no need to invoke an external command when "$HOME" is safer and faster. Also any variable expansion must be double-quoted.

- sudo chmod +x /some/file: sudo should not be used when dealing with files owned by the user.  The user can change permissions on his own files. Also, +x should be used only with *executables*, not for every file. And a ".jar" file is *not* an executable (java is).

- using multiple lines of "echo '1. ...'" for menus with dozens of "if"s later: there is "select" and "case" for that.

- using multiple lines of "echo '...' >> file". There is "cat > file <<_EOF_ ... multiple .... lines  ... _EOF_" for that.

- Lack of indentation leading to several "fi fi fi" lines in the same column. Very hard to follow.

- Installing some files (executable) in system dir (/usr/local/bin) and others in user dir (desktop, icons). If an executable is /usr/local/bin the .desktop should be at /usr/local/share/applications. Either make a system install or user install, but don't mix both.

- sudo gnome-terminal -x sudo update-alternatives .... ??? Why invoke a 2nd shell? and why gnome-terminal?

- Value=1.0 in a .desktop file. It's not "Value", its "Version". And it should not be used unless the .desktop conforms with the spec, which the ones created by the script aren't.

The list goes on and on...

---

### Post by MestreLion on 2013-03-27
Here is my take on the subject of Minecraft installers and launchers:

[https://github.com/MestreLion/minecraft](https://github.com/MestreLion/minecraft)

It's hosted at github, using a git repository, so feel free to suggest, improve, make corrections, etc. 

Happy mining! :)

---

### Post by alfonsojon on 2013-06-02
Hey guys, been a while since my last post! I've been busy with a rewrite of that script I posted on page 10, and it's finally done. I haven't had time to work on it but I finished it up last night.

Here's what it has:
[LIST]
[*]Server installation
[LIST]
[*]Supports Bukkit, Vanilla, and Spigot. Will add support for Tekkit soon.
[/LIST]

[*]Server upgrades
[*]Client installation
[*]Client troubleshooting
[*]Automatic OpenJDK installation
[LIST]
[*]Supports Ubuntu, Fedora, Arch Linux, and others.
[*]I'm currently working on getting OpenJDK for ARM processors working!
[/LIST]

[*]Launcher creation & Unity (dockapi) integration
[*]Debug tools for client
[/LIST]

Here's what I'm planning (in order of priority)
[LIST]
[*]LWJGL updater
[*]Minecraft server as system service (init.d)
[*]Python port (With PyGTK as a GUI)
[*]Chrome OS support?
[LIST]
[*]When implemented, your Chrome OS device MUST BE in developer mode in order to access bash.
[/LIST]
[/LIST]
[INDENT][[SIZE=4]**Download (BitBucket)**[/SIZE]]("https://bitbucket.org/alfonsojon/mc-nix/src")

(Download mcnix.sh and run in a terminal)[/INDENT]

---

### Post by lord-yurij on 2013-08-15
Wouldn't it be better to check for java 7 instead of java 6?

---

### Post by GameGuru on 2013-08-16
Ok I have a problem.  I went in and changed it's permission and it looks like this:

[IMG]http://i39.tinypic.com/jk83tl.png[/IMG]

And when I double left click the file it loads in gedit:

[IMG]http://i40.tinypic.com/ojl1zn.png[/IMG]

What do I do to get this to work?

---

### Post by DarkAmbient on 2013-08-16
I THINK it's standard behaviour for Nautilus in Ubuntu 13.04 to only open text-files in text-editors. In Nautilus, go File->Setting->Behaviour, under "Executable Text Files" pick "Ask every time", or something like that. 

PS. I don't have english as default, so my translation may be off.

---

### Post by GameGuru on 2013-08-16
Ok I will try that when I get home, thanks.

---

### Post by whatthefunk on 2013-08-16
Do we even need Minecraft installers anymore?  A couple years ago, Minecraft was a bit of a pain to install, but these days its one of the easiest things to do.  I installed it last week on this system and it took about two minutes.
Step 1: Download Minecraft .jar file
Step 2: Install openjdk7
Thats it.

---

### Post by DarkAmbient on 2013-08-17
This should do it GameGure:

```
gsettings set org.gnome.nautilus.preferences executable-text-activation ask
```

whatthefunk: Installing Java and Minecraft isn't the "hard" part, updating lwjgl and modding is.

---

### Post by GameGuru on 2013-08-17
I did this and it worked.  I installed Minecraft and it says it worked.  I launch it and it asked for my username and password, went to Mojang's site and created one and it keeps saying Login failed and Play Offline is grayed out and it said Not Downloaded.  How do I play offline and how do I get it downloaded?

---

### Post by DarkAmbient on 2013-08-17
You need to buy Minecraft "for your" account as well, it's &#8364;19.95.

---

### Post by merlinlcb on 2013-10-06
your installer doesnt install the new launcher

---

### Post by Laurence02 on 2013-10-13
Worked on my previous installation! Thanks sir, you made my day!

---

### Post by rungms on 2013-10-30
i did do it for my[ minecraft servers]("http://topg.org/Minecraft") and worked

---

### Post by Will_McDade on 2013-11-01
What does this actually... do..?

---

