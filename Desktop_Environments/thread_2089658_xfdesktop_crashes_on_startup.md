---
title: "xfdesktop crashes on startup"
date: 2012-11-29
forum: Desktop Environments
---

### Post by didiercool on 2012-11-29
It started yesterday after I ran the following .sh file...

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
echo "@  Alloc's Bash Minecraft Installer         @"
echo "@  Version 2.0                                               @" 
echo "@                                                                            @"
echo "@  Please feel free to improve               @"
echo "@  this script however you desire.           @"
echo "@                                                                            @"
echo "@  Alloc@dr.com                                             @"
echo "@-------------------------------------------@"

counter=1

#----------------------------------#
#                  DOTS FUNCTION                  #
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
#                INSTALL FUNCTION                #
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
#        SERVER INSTALL FUNCTION          #
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
echo -ne "       -minecraft_server.jar"
echo     "   done!"
wget -q http://www.minecraft.net/download/minecraft_server.jar

echo -ne "       -server_icon.png        "
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
#       SERVER UNINSTALL FUNCTION        #
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
#          UNINSTALL FUNCTION            #
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
#        TROUBLESHOOT FUNCTION          #
#----------------------------------#
function TroubleShoot {
echo ""
echo ""
echo "#----------------------------------#"
echo "#    Troubleshooting Menu    #"
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
#                 MAIN FUNCTION            #
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
#         CALL THE MAIN FUNCTION          #
#----------------------------------#

Main

# THE END 
```

I installed both minecraft and the server via this sh file.

I'm not really sure how to go about fixing this and google seems not to reveal any solutions.  When I run ```
xfdesktop & exit

``` in the terminal, the desktop flashes on and off a few times and then crashes.

Any hope/ideas?  I'm running xubuntu 12.04

---

### Post by Isamu715 on 2012-11-30
There doesn't seem to be anything wrong with the script. Does running:
```
xfdesktop
```give out any error messages?

---

### Post by Toz on 2012-11-30
There was a report previously about a similar problem with that script and xfdesktop. See here: [http://ubuntuforums.org/showthread.php?t=2037307&highlight=minecraft+xfdesktop]("http://ubuntuforums.org/showthread.php?t=2037307&highlight=minecraft+xfdesktop").

I wonder whether the script is causing some permission errors in your home folder. In addition to what @Isamu715 suggests, make sure that you are the owner of the files in your home directory - especially in these locations:
```
ls -al $HOME
ls -al $HOME/.config
ls -al $HOME/.config/xfce4
ls -al $HOME/.cache/sessions
```

---

### Post by didiercool on 2012-12-03
@Isam715 - 

The only error is: Segmentation fault (core dumped)

@Toz -

All of the locations you mentioned belong to me (according to ls -al).  I'm going to go through the thread you mentioned and report how that goes.  Good find!

---

### Post by didiercool on 2012-12-03
So... I ended up 'solving' it by deleting all the hidden folders and files in my home folder and replacing them with the hidden files and folders in a newly created user.  Not elegant, and I don't recommend it, but it did work.  Had to recalibrate my settings, etc., but at least I didn't have to re-os the stupid thing.  Moral of the story, don't use script files.

Thanks all!

---

