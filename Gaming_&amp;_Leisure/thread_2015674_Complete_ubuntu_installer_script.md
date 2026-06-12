---
title: "Complete ubuntu installer script"
date: 2012-07-03
forum: Gaming &amp; Leisure
---

### Post by Enkouyami on 2012-07-03
[COLOR=#0000ff]Complete Ubuntu Installer Script v1.4.1 (Updated 9 July 2012)[/COLOR]
[COLOR=#008000]by Enkouyami[/COLOR][IMG]http://static.minecraftforum.net//public/style_emoticons/default/mobzombie.png[/IMG]
[COLOR=#ffa500]enkouyami@gmail.com[/COLOR]

This script was inspired by [Alloc]("http://www.minecraftforum.net/user/338581-alloc/")'s [Ubuntu Minecraft Installer Script (v2.0)]("http://www.minecraftforum.net/topic/250945-install-ubuntu-minecraft-installer-update-20/") [IMG]http://static.minecraftforum.net//public/style_emoticons/default/mobskeleton.png[/IMG]
This is the first script I ever made. This installer will do all the hard work of installing java and minecraft for you![IMG]http://static.minecraftforum.net//public/style_emoticons/default/steve_shocked.gif[/IMG]

My original thread is on [http://www.minecraftforum.net/topic/1114574-enkouyamis-complete-ubuntu-installer-script/](http://www.minecraftforum.net/topic/1114574-enkouyamis-complete-ubuntu-installer-script/)

[COLOR=#0000ff]What the script can do [/COLOR]
[LIST]
[*][COLOR=#008000]Unity right click option to run minecraft in terminal[/COLOR]
[*][COLOR=#008000]Install icons[/COLOR]
[*][COLOR=#008000]Update the Lightweight Java Game Library[/COLOR]
[*][COLOR=#008000]Checks for the existence of files before creating new ones[/COLOR]
[*][COLOR=#008000]Install the Minecraft regular or server client.[/COLOR]
[*][COLOR=#008000]Check to see what which Java is installed on your system[/COLOR]
[*][COLOR=#008000]Installs Oracle-Java or OpenJDK[/COLOR]
[*][COLOR=#008000]Set Oralce, Sun, and OpenJDK as default Java[/COLOR]
[*][COLOR=#008000]Downloads Minecraft for you[/COLOR]
[*][COLOR=#008000]Installs it to a new ".minecraft" or "Minecraft_Server" folder in your home directory[/COLOR]
[*][COLOR=#008000]Writes a shell script to the /usr/local/games folder and add it to PATH[/COLOR]
[*][COLOR=#008000]Creates a shortcut on your desktop that you can use to run Minecraft[/COLOR]
[*][COLOR=#008000]Create a launchers in your Applications menu[/COLOR]
[*][COLOR=#008000]Lets you run Minecraft from terminal with a simple "minecraft" command![/COLOR]
[/LIST]

[COLOR=#0000ff]How To Run It[/COLOR]
1. Download the file from the link below
2. Right click and open the file's Properties
3. Browse to the Permissions tab and check the executable box
4. Double click on the file and choose 'Run in terminal'

[COLOR=#0000ff]Alternatively[/COLOR]: you can give it executable permissions via the terminal and run it from there:
```
cd /path/to/Minecraft_Installer/
sudo chmod -x Minecraft_Installer.sh
bash Minecraft_Installer.sh
```[COLOR=#008000]After the script has installed minecraft, you'll be able to open up terminal and type "minecraft", or the launcher on your desktop to play![/COLOR]

[COLOR=#ff0000]Download Link[/COLOR][COLOR=#FF8000]:[/COLOR][HERE]("http://enkouyami.minus.com/uploads")

**[COLOR=#800080]Changlog[/COLOR]**
**Version 1.4.1 (09 July 2012)**
[COLOR=#008080]Renamed the second UninstallMinecraftA to UninstallMinecraftB since it was incorectly named.[/COLOR]
[COLOR=#008080]Moved UninstallMinecraftB function up above UninstallMinecraft2 since procedurally it comes before.[/COLOR]
[COLOR=#ff0000]Removed the spaces before () througout the script.[/COLOR]

**Version 1.4 (03 July 2012)**
[COLOR=#008000]Added more checks for existing files & folders in installation processes.[/COLOR]
[COLOR=#008000]Added checks for items that could have been made in previous versions but have changed.[/COLOR]
[COLOR=#ff0000]Removed the need for the folder "install_files".[/COLOR]
[COLOR=#008000]Added /usr/local/games to PATH by creating a script in /etc/profile.d/ [/COLOR]
[COLOR=#008080]Reorganized script and other minor improvements/corrections.[/COLOR]
[COLOR=#008080]Fixed spelling and other language errors.[/COLOR]
[COLOR=#008080]Fixed my error in thinking that Description AKA GenericName was actually description instead of a generic name.[/COLOR]
[COLOR=#008000]Added new content to the menu shortcut such as options from right clicking with unity.[/COLOR]
[COLOR=#008000]Made it so that the icons are installed via xgd.[/COLOR]
[COLOR=#008080]Updated Java Menu and checking.[/COLOR]

**Version 1.3 (03 June 2012)**
[COLOR=#008080]Changed the location of the shell script from '/usr/local/bin' to '/usr/local/games'.[/COLOR]
[COLOR=#008080]Changed the the description for the desktop launcher from being a Comment to a Description(GenericName).[/COLOR]
[COLOR=#008080]Fixed the UpdateLwjgl function and put a comment briefly explaining what it does.[/COLOR]
[COLOR=#008080]Fixed 'folder still exists' errors when using remove directory commands.[/COLOR]
[COLOR=#008080]Edited script to use 'case' for letter and number choices in selection menus.[/COLOR]
[COLOR=#008080]Minor fixes here and there.[/COLOR]

**Version 1.2 (8 May 2012)**
[COLOR=#008000]Added and option to update the Lightweight Java Game Engine in Troubleshooting.[/COLOR]
[COLOR=#008080]Changed names of labels and functions.[/COLOR]
[COLOR=#008080]Changed uegensan:ppa to webupd8:ppa for more update. Webupdate uses uegensan then does bug fixes.[/COLOR]
[COLOR=#008000]Added more comments to be shown when going through the various steps of the script.[/COLOR]
[COLOR=#008080]Updated the installation and removal functions.[/COLOR]
[COLOR=#008080]Fixed problems in writing shortcuts where values were not being written.[/COLOR]
[COLOR=#ff0000]Removed redundant steps.[/COLOR]

**Version 1.1 (22 March 2012)**
[COLOR=#008080]Minor fixes here and there.[/COLOR]

**Version 1.0 (Some time in March)**
[COLOR=#008080]Fixed a some of allocs's syntax problems.[/COLOR]
[COLOR=#008000]Reorganized the entire script into separate functions and added new ones.[/COLOR]
[COLOR=#008080]Made the script more legible.[/COLOR]
[COLOR=#008080]Fixed a few problems here and there.[/COLOR]

[COLOR=#0000ff][IMG]http://static.minecraftforum.net//public/style_emoticons/default/wheatgrown.png[/IMG]The Script[/COLOR][IMG]http://static.minecraftforum.net//public/style_emoticons/default/wheatgrown.png[/IMG]
Just replace i386 with amd64 for a 64bit version with CTRL+H in a text editor.
```
#!/bin/bash

# Enkouyami's Bash Minecraft Installer
# Copyright (C) 2012  Ely Lizaire

# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

# For any suggestions or feedback, reach me at http://www.minecraftforum.net/topic/1114574-bash-minecraft-installer/ or send me an e-mail at enkouyami@gmail.com

# This script was inspired by Alloc's Minecraft Installer at http://www.minecraftforum.net/topic/250945-install-ubuntu-minecraft-installer-update-20/
# Alloc's e-mail: Alloc@dr.com

# This script attempts to install Minecraft.
# It also has s to download Minecraft files directly from minecraft.net, install Oracle Java, Sun Java, and or OpenJDK.

echo "------------------------------------------------------" echo ""
echo "Enkouyami's Bash Minecraft Installer  Copyright (C) 2012  Ely Lizaire"
echo "This program comes with ABSOLUTELY NO WARRANTY; for details type 'show w'."
echo "This is free software, and you are welcome to redistribute it"
echo "under certain conditions; type 'show c' for details."
echo ""
echo " _____________________________________________"
echo "/*  ***    **       *****       **      ***  *\ "
echo "|*********************************************| "
echo "|*    Enkouyami's Bash Minecraft Installer   *|"
echo "|*                Version 1.4                *|" 
echo "|*                9 July 2012                *|"
echo "|*      My email: enkouyami@gmail.com        *|"
echo "|*********************************************|"
echo "\_____________________________________________/"
echo "Visit http://www.minecraftforum.net/topic/1114574-bash-minecraft-installer/ for more help."

#------------------#
#   License Menu   #
#------------------#
licenseMenu() {
echo ""
echo "The GPLv3 license imposes the requirement that any freedom that is granted regarding the original work must be granted on exactly the same or compatible terms in any derived work."
echo ""
echo "Enter '1' to download the full license details at http://www.gnu.org/licenses/gpl-3.0.txt and then press 'q' to quit reading"
echo "Enter '2' to go back to main menu."
echo ""
read character
case $character in
    1 ) Showlicense
    return;;
    2 | q ) return
    return;;
    *) echo "Invalid choice"
    return
esac
} ## END LicenseMenu

#----------------#
#  Show License  #
#----------------#
Showlicense() {
License='$(dirname -- "$0")/gpl-3.0.txt' # GNU General Public license
cd '$(dirname -- "$0")' && wget -c http://www.gnu.org/licenses/gpl-3.0.txt
less "$License" # Can either use the basic "more", or "less", dialog, and "most" to display the file.
} ## END ShowLicense

counter=1
#-----------#
#   Dots    #
#-----------#
# This simply prints three Dots. It waits .1 seconds between each dot.
Dots() {
while [ $counter -le 3 ]
do
echo -n "."
sleep .1
((counter++))
done
let counter=1
echo ""
} ## END Dots

#-------------------#
#   Java Checking   #
#-------------------#
CheckJavas() { # Here, this script will attempt to check for Java by checking to see if installation folders are present.
echo -n "Checking for Java"
Dots
echo ""
echo -n "looking for Oracle Java"
Dots
if [ -e /usr/lib/jvm/java-7-oracle ] && [ -e /usr/lib/jvm/java-7-oracle/bin ] && [ -e /usr/lib/jvm/java-7-oracle/bin/java ]; then
    echo "Oracle Java 7 is Installed"
    echo ""
else
echo "Oracle Java 7 is NOT installed"
echo ""
echo "Looking for Sun Java 6"
if [ -e /usr/lib/jvm/java-6-sun ] && [ -e /usr/lib/jvm/java-6-sun/bin ] && [ -e /usr/lib/jvm/java-6-sun/bin/java ]; then
    echo "Sun Java 6 is Installed!"
    echo ""
else
echo "Sun Java 6 is NOT installed"
echo ""
echo -n "Looking for OpenJDK 7"
Dots
if [ -e /usr/lib/jvm/java-7-openjdk-common ] && [ -e /usr/lib/jvm/java-7-openjdk-common/jre ] && [ -e /usr/lib/jvm/java-7-openjdk-common/jre/lib ]; then
    echo "OpenJDK 7is Installed"
    echo ""
else
echo "OpenJDK 7 is NOT installed"
echo ""
echo "Looking for OpenJDK 6"
if [ -e /usr/lib/jvm/java-6-openjdk-common ] && [ -e /usr/lib/jvm/java-6-openjdk-common/jre ] && [ -e /usr/lib/jvm/java-6-openjdk-common/jre/lib ]; then
    echo "OpenJDK 6 is Installed"
    java -version
    javac -version
echo "folders detected:"
ls /usr/lib/jvm/
else
echo "OpenJDK 6 is NOT installed"
echo ""
fi
fi
fi
fi
ls /usr/lib/jvm/
} ## END CheckJavas

#-----------------#
#    Java Menu    #
#-----------------#
JavaMenu() {
echo "------------------------------------------------------"; echo ""
echo "#---------------------#"
echo "#      Java Menu      #"
echo "#---------------------#"
echo "What would you like to do? (enter number of choice)"; echo ""
echo "1) Check the default Java client"
echo "2) Install Oracle/Sun Java (Recommended)"
echo "3) Install OpenJDK"
echo "4) Manually select which Java to use (Recommended)"
echo "5) Use OpenJDK 7 to run minecraft from now on"
echo "6) Use Oracle Java 7 to run minecraft from now on"
echo "7) Use Sun Java 6 to run minecraft from now on(May not work)"
echo "8) Go back to main menu"
echo ""
read character
case $character in
    1 ) java -version
    JavaMenu;;
    2 ) OracleJavaMenu
    JavaMenu;;
    3 ) OpenJDKInstall
    javac -version;;
    4 ) sudo update-alternatives --config java
    sudo update-alternatives --config javac
    sudo update-alternatives --config javaws
    echo ""; echo "Done!"; echo "";
    JavaMenu;;
    5 ) OpenJDKDefault
    JavaMenu;;
    6 ) OracleJavaDefaultA
    JavaMenu;;
    7 ) SunJavaDefault
    JavaMenu;;
    8 ) return;;
    * ) echo "Invalid choice"
    JavaMenu
esac
} ## END JavaMenu

#----------------------#
#   Oracle Java Menu   #
#----------------------#
OracleJavaMenu() {
echo "------------------------------------------------------"
echo ""
echo "#-------------------------------------#"
echo "#   Installing Oracle/Sun Java Menu   #"
echo "#-------------------------------------#"    
echo "1. Install Oracle Java 7"
echo "2. Install/update Sun Java 6"
echo ""
read character
case $character in
    1 ) OracleJavaInstallA;;
    2 ) SunJavaInstallA;;
    * ) echo ""; echo "Invalid Choice!"
esac
} ## END OracleJavaMenu

#--------------------------------#
#   Oracle Java 7 InstallationA  #
#--------------------------------#
OracleJavaInstallA() {
echo "Do you wish to purge OpenJDK from your system? [y/N]"
echo ""
read character
case $character in
    y | Y ) PurgeOpenJDK
    OracleJavaInstallB;;
    n | N ) OracleJavaInstallB;;
    * ) echo "" echo "Invalid Choice!"
esac
} ## END OracleJavaInstallA

#-----------------------#
#    Purge OpenJDK 7    #
#-----------------------#
PurgeOpenJDK() {
echo -n "Purging OpenJDK from your system!"
Dots
echo "This requires root access:"
sudo apt-get purge openjdk* && sudo apt-get purge icedtea6*
echo "" echo "Done!"; echo ""
} ## END PurgeOpenJDK

#---------------------------------#
#   Oracle Java 7 InstallationB   #
#---------------------------------#
OracleJavaInstallB() {
echo "Do you wish to add the PPA? [y/N]"
echo ""
read character
case $character in
    y | Y ) OracleJava7PPA
    OracleJavaInstall;;
    n | N ) OracleJavaInstall;;
    * ) echo "" echo "Invalid Choice!"
esac
} ## END OracleJavaInstallB

#-----------------------------#
#  Install Oracle Java 7 ppa  #
#-----------------------------#
OracleJava7PPA() {
echo -n "Adding Oracle Java 7 PPA"
Dots
echo "This requires root access:"
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
echo ""; echo "Done!"; echo ""
} ## END OracleJava7PPA

#-------------------------#
#  Oracle Java 7 Install  #
#-------------------------#
OracleJavaInstall() {
echo -n "Installing Oracle Java 7"
Dots    
echo "This requires root access:"
sudo mkdir -p /usr/lib/mozilla/plugins
sudo apt-get install Oraclejava7-installer
echo ""; echo "Done!"; echo ""
} ## END OracleJavaInstall

#--------------------------------#
#  Set Oracle Java 7 as Default  #
#--------------------------------#
OracleJavaDefaultA() {
echo -n "Making Oracle Java the default"
Dots
echo "Don't worry if you see lots of errors"
sudo update-java-alternatives -s java-7-oracle
echo ""; echo "Done!"; echo ""
} ## END OracleJavaDefaultA

#-------------------#
#  OpenJDK Install  #
#-------------------#
OpenJDKInstall() {
echo -n "Starting OpenJDK installation"
Dots
echo "This requires root access:"
sudo mkdir -p /usr/lib/mozilla/plugins
sudo apt-get install openjdk-7-jre icedtea-7-plugin
echo ""; echo "Done!"; echo ""
} ## END OpenJDKInstall

#--------------------------#
#  Set OpenJDK as Default  #
#--------------------------#
OpenJDKDefault() {
echo -n "Making OpenJDK the default"
Dots
echo "Don't worry if you see lots of errors"
sudo update-java-alternatives -s java-1.7.0-openjdk-i386
echo ""; echo "Done!"; echo ""
} # END OpenJDKDefault

#----------------------#
#  Install Sun Java 6  #
#----------------------#
SunJavaInstallA() {
    echo ""
    echo -n "Installing Sun Java 6"
    Dots
    echo "Do you wish to add the PPA? [y/N]"
    echo ""
    read character
    case $character in
        y | Y ) SunJavaInstallPPA
        SunJavaInstall
        return;;
        n | N ) SunJavaInstall
        return;;
        * ) echo "Invalid Choice"
        InstallJavaA
    esac
} # END SunJavaInstallA

#----------------------#
#  Install Sun Java 6  #
#----------------------#
SunJavaInstall() {
echo "Installing Sun Java 6"
echo "This requires root access:"
sudo mkdir -p /usr/lib/mozilla/plugins
sudo apt-get install update-sun-jre
echo ""; echo "Done!"; echo ""
} # END SunJavaInstall

#--------------------------#
#  Install Sun Java 6 PPA  #
#--------------------------#
SunJavaInstallPPA() {
echo "This requires root access:"
sudo add-apt-repository 'deb http://www.duinsoft.nl/pkg debs all/'
sudo apt-get update
} ## END SunJavaInstallPPA

#-----------------------------#
#  Set Sun Java 6 as Default  #
#-----------------------------#
SunJavaDefault() {
echo -n "Making Sun Java the default"
Dots
echo "Don't worry if you see lots of errors"
echo ""
sudo update-java-alternatives -s java-6-sun
sudo update-java-alternatives -s java-6-sun-i386
echo ""; echo "Done!"; echo ""
} ##END SunJavaDefault

#---------------------#
#  Install Minecraft  #
#---------------------#
InstallMinecraft() { # Here this script will first check to see if the user already has minecraft.jar
# If so, it won't be downloaded.
echo ""
echo "#--------------------------#"
echo "#  Minecraft Installation  #"
echo "#--------------------------#"
echo ""
echo -n "Checking if minecraft is already installed"
Dots
echo ""
if [ -e /home/$(whoami)/.minecraft/install_files ]; then
    echo  -ne "Removing uneeded install_files folder"
    rm -rf /home/$(whoami)/.minecraft/install_files
fi
if [ -e /home/$(whoami)/.minecraft/minecraft.jar ]; then
    echo  "Minecraft is already present!"
    return
else
cd /home/$(whoami)
if [ ! -e /home/$(whoami)/.minecraft ]; then
    echo -ne "Creating ~/.minecraft"
    Dots
    echo ""
    mkdir .minecraft
fi
fi
cd /home/$(whoami)/.minecraft
echo -n "Downloading minecraft.jar"
Dots
wget -q www.minecraft.net/download/minecraft.jar
echo -ne "Downloading the icon to ~/.minecraft"
Dots
wget -q http://www.minecraft.net/favicon.png
mv /home/$(whoami)/.minecraft/favicon.png /home/$(whoami)/.minecraft/Minecraft.png
echo ""
echo -e "Minecraft has finished downloading!"
echo ""
#--------------------------------------------
echo -ne "Setting up the minecraft /usr/local/games shell script"
Dots
# This writes a shell script in the /usr/local/games folder, if it already exists in /usr/local/games or /usr/local/bin, it will be replaced.
if [ -e /usr/local/games/minecraft ]; then
    echo -n "Removing previous version"
    Dots
    echo ""
    rm -rf /usr/local/games/minecraft
fi
if [ -e /usr/local/bin/minecraft ]; then
    echo -ne "Removing previous version"
    Dots
    rm -rf /usr/local/bin/minecraft
fi
touch minecraft
echo "java -jar /home/$(whoami)/.minecraft/minecraft.jar" >> minecraft
echo ""
echo -n "Moving and changing permission of Minecraft shell script"
Dots
echo "This requires root access:"
sudo chmod +x minecraft
sudo mv minecraft /usr/local/games/
echo "Done!"
echo ""
#--------------------------------------------
echo "Installing the minecraft icon"
xdg-desktop-icon install --novendor /home/$(whoami)/.minecraft/Minecraft.png
rm -rf Minecraft.png
echo ""
#--------------------------------------------
echo -n "Creating a desktop launcher"
Dots
if [ -e /home/$(whoami)/Minecraft.desktop ]; then
    rm -rf /home/$(whoami)/Minecraft.desktop
fi
touch 'Minecraft.desktop'
echo "[Desktop Entry]" >> Minecraft.desktop
echo "Version=1.0" >> Minecraft.desktop
echo "Name=Minecraft" >> Minecraft.desktop
echo "GenericName=Game" >> Minecraft.desktop
echo "Comment=Minecraft is a game about placing blocks to build anything you can imagine." >> Minecraft.desktop
echo "Exec=minecraft" >> Minecraft.desktop
echo "Terminal=false" >> Minecraft.desktop
echo "Icon=Minecraft"  >> Minecraft.desktop
echo "Categories=Game;Application;" >> Minecraft.desktop
echo "Type=Application" >> Minecraft.desktop
echo "StartupNotify=true" >> Minecraft.desktop
echo "Actions=RunInTerminal" >> Minecraft.desktop
echo "" >> Minecraft.desktop
echo "[Desktop Action RunInTerminal]" >> Minecraft.desktop
echo "Name=Run in Terminal" >> Minecraft.desktop
echo "Exec=sudo gnome-terminal -x minecraft" >> Minecraft.desktop
#---------------------------------------------
echo -n "Granting the launcher executable permissions and adding it to your desktop"
Dots
echo "This requires root access:"
sudo chmod +x Minecraft.desktop
cp Minecraft.desktop /home/$(whoami)/Desktop
echo "Done!"; echo ""
#----------------------------------------------------
echo -n "Adding it to your application menu"
Dots
xdg-desktop-menu install --novendor Minecraft.desktop
xdg-desktop-menu forceupdate
rm -rf Minecraft.desktop
rm -rf /home/$(whoami)/Desktop/Minecraft.png
echo ""
#---------------------------------------------
# This writes a script that will add /usr/local/games to PATH which will then allow the user to run minecraft from terminal, just by typing "minecraft"
if [ ! -e /home/$(whoami)/.minecraft/add_usr-local-games_to_PATH.sh ]; then
    rm -rf add_usr-local-games_to_PATH.sh
fi
if [ ! -e /etc/profile.d/add_usr-local-games_to_PATH.sh ]; then
    echo -ne "Adding /usr/local/games to PATH so you can run minecraft with 'minecraft' from terminal"
    Dots
    touch add_usr-local-games_to_PATH.sh
    echo "# set PATH so it includes /usr/local/games if it exists" >> add_usr-local-games_to_PATH.sh
    echo "if [ -e '/usr/local/games' ]; then" >> add_usr-local-games_to_PATH.sh
echo "    export PATH=/usr/local/games:$PATH" >> add_usr-local-games_to_PATH.sh
echo "fi" >> add_usr-local-games_to_PATH.sh
sudo chmod +x add_usr-local-games_to_PATH.sh
sudo mv add_usr-local-games_to_PATH.sh /etc/profile.d/add_usr-local-games_to_PATH.sh
source /etc/profile.d/add_usr-local-games_to_PATH.sh
echo ""
fi
#---------------------------------------------
echo "SUCCESS!"
echo ""
echo -ne "Hopefully Minecraft has been successfully downloaded and installed without any problems. Check your desktop and Applications menu for launchers. You can also run it from terminal with a 'minecraft' command."
echo "Visit the forum at http://www.minecraftforum.net/topic/1114574-bash-minecraft-installer/ (I would prefer you do that) or e-mail me at enkouyami@gmail.com if you have any questions"
echo "Enjoy! :D"
echo ""
} ## END InstallMinecraft

#-----------------------#
#  Uninstall Minecraft  #
#-----------------------#
UninstallMinecraft() {
echo -n "Looking for Minecraft"
Dots
if [ -e /home/$(whoami)/.minecraft/minecraft.jar ]; then
    echo "Minecraft found!"
    echo -n "Uninstalling"
    cd /home/$(whoami)/.minecraft
    Dots
    echo ""
    echo "Do you wish to save your settings and save data? [y/N]"
    read character
    case $character in
        y | Y ) UninstallMinecraftA
        echo "";;
        n | N ) UninstallMinecraftB
        echo "";;
        * ) echo "Invalid choice!";;
    esac
UninstallMinecraft2
else
echo "Minecraft not detected!"
fi
} ## END UninstallMinecraft

#------------------------#
#  Uninstall MinecraftA  #
#------------------------#
UninstallMinecraftA() {
    echo -n "Uninstalling minecraft while keeping your personal data"
    Dots
    echo ""
if [ -e /home/$(whoami)/.minecraft/install_files ]; then
    echo  -ne "Removing install_files folder"
    echo ""
    rm -rf /home/$(whoami)/.minecraft/install_files
fi
    rm -rf bin
    rm -rf texturepacks
    rm minecraft.jar
    rm -rf minecraft
    rm -rf resources
} ## END UninstallMinecraftA

#------------------------#
#  Uninstall MinecraftB  #
#------------------------#
UninstallMinecraftB() {
    echo -n "Removing minecraft folder"
    Dots
    echo ""
    rm -rf /home/$(whoami)/.minecraft
    echo ""
} ## END UninstallMinecraftB

#------------------------#
#  Uninstall Minecraft2  #
#------------------------#
UninstallMinecraft2() {
echo "Uninstalling the icon"
xdg-desktop-icon uninstall --novendor Minecraft.png
echo ""
#--------------------------------------------
echo ""
echo -n "Removing menu launcher"
Dots
xdg-desktop-menu uninstall Minecraft.desktop
echo ""
#--------------------------------------------
if [ -e /home/$(whoami)/Desktop/Minecraft.desktop ]; then
    echo -n "Removing Desktop launcher"
    Dots
    rm -rf /home/$(whoami)/Desktop/Minecraft.desktop
    echo ""
fi
#--------------------------------------------
echo -ne "Removing Launcher in '/usr/local/games'"
Dots
echo "This requires root access:"
sudo rm -rf /usr/local/games/minecraft
echo ""
if [ -e /usr/local/games/minecraft ]; then
    echo -ne "Removing launcher in '/usr/local/bin/minecraft'"
    rm -rf /usr/local/bin/minecraft
    fi
    echo "Minecraft has been uninstalled :("
} ## END UninstallMinecraft2

#----------------------------#
#  Install Minecraft Server  #
#----------------------------#
ServerInstall() {
echo ""
echo "#----------------------------------#"
echo "#  Minecraft Server Installation   #"
echo "#----------------------------------#"
echo ""
echo -n "Checking if minecraft server is already installed"
Dots
if [ -e /home/$(whoami)/Minecraft_Server/bin/minecraft_server.jar ]; then
    echo "Minecraft server client is already present!"
    return
else
echo ""
echo -n "Installing Minecraft Server"
Dots
echo ""
fi
if [ ! -e /home/$(whoami)/Minecraft_Server ]; then
    echo -ne "Creating ~/Minecraft_Server"
    Dots
    mkdir /home/$(whoami)/Minecraft_Server
fi
cd /home/$(whoami)/Minecraft_Server
if [ ! -e /home/$(whoami)/Minecraft_Server/bin ]; then
    echo -ne "Creating ~/Minecraft_Server/bin"
    Dots
    echo ""
    mkdir bin
fi
cd bin
echo -n "Downloading minecraft_server.jar"
Dots
wget -q http://www.minecraft.net/download/minecraft_server.jar
echo -n "Downloading the icon to ~/Minecraft_Server"
Dots
wget -q http://i.imgur.com/ugDRM.png
mv /home/$(whoami)/Minecraft_Server/bin/ugDRM.png /home/$(whoami)/Minecraft_Server/bin/Minecraft_Server.png
echo ""
echo -e "Minecraft Server has finished downloading!"
echo ""
#---------------------------------------------
echo -ne "Setting up the Minecraft '/usr/local/games' shell script"
Dots
# This writes a shell script in the /usr/local/games folder, if it already exists in /usr/local/games or /usr/local/bin, it will be replaced.
if [ -e /usr/local/games/minecraft_server ]; then
    echo -n "Removing previous version"
    Dots
    rm -rf /usr/local/games/minecraft_server
fi
if [ -e /usr/local/bin/minecraft_server ]; then
    echo -n "Removing previous version"
    Dots
    rm -rf /usr/local/bin/minecraft_server
fi
touch minecraft_server
echo "java -Xmx1024M -Xms1024M -jar /home/$(whoami)/Minecraft_Server/bin/minecraft_server.jar" >> minecraft_server
echo -n "Moving and changing permission of Minecraft shell script"
Dots
echo "This requires root access:"
sudo chmod +x minecraft_server
sudo mv minecraft_server /usr/local/games
echo "Done!"
echo ""
#--------------------------------------------
echo "Installing the minecraft icon"
xdg-desktop-icon install --novendor /home/$(whoami)/.minecraft/Minecraft_Server.png
rm -rf Minecraft_Server.png
echo ""
#---------------------------------------------
echo -n "Creating a desktop launcher"
Dots
if [ -e /home/$(whoami)/Minecraft_Server.desktop ]; then
    rm -rf /home/$(whoami)/Minecraft_Server.desktop
fi
touch Minecraft_Server.desktop
echo "[Desktop Entry]" >> Minecraft_Server.desktop
echo "Version=1.0" >> Minecraft_Server.desktop
echo "Name=Minecraft Server" >> Minecraft_Server.desktop
echo "GenericName=Server game client GUI" >> Minecraft_Server.desktop
echo "Comment=Minecraft Server GUI" >> Minecraft_Server.desktop
echo "Exec=minecraft" >> Minecraft_Server.desktop
echo "Terminal=false" >> Minecraft_Server.desktop
echo "Icon=Minecraft_Server"  >> Minecraft_Server.desktop
echo "Categories=Game;Application;" >> Minecraft_Server.desktop
echo "Type=Application" >> Minecraft_Server.desktop
echo "StartupNotify=true" >> Minecraft_Server.desktop
echo "Actions=RunInTerminal" >> Minecraft_Server.desktop
echo "" >> Minecraft_Server.desktop
echo "[Desktop Action RunInTerminal]" >> Minecraft_Server.desktop
echo "Name=Run in Terminal" >> Minecraft_Server.desktop
echo "Exec=sudo gnome-terminal -x minecraft" >> Minecraft_Server.desktop
#----------------------------------------------------
echo -n "Granting the launcher executable permissions and adding it to your desktop"
Dots
echo "This requires root access:"
sudo chmod +x Minecraft_Server.desktop
cp Minecraft_Server.desktop /home/$(whoami)/Desktop
echo "Done!"
echo ""
#---------------------------------------------
echo -n "Adding it to your application menu"
Dots
xdg-desktop-menu install --novendor Minecraft_Server.desktop
xdg-desktop-menu forceupdate
rm -rf Minecraft_Server.desktop
rm -rf /home/$(whoami)/Desktop/Minecraft_Server.png
echo "Done!"
echo ""
#---------------------------------------------
# This writes a script that will add /usr/local/games to PATH which will then allow the user to run Minecraft Server from terminal, just by typing "minecraft_server"
if [ ! -e /home/$(whoami)/.minecraft/add_usr-local-games_to_PATH.sh ]; then
    rm -rf add_usr-local-games_to_PATH.sh
fi
if [ ! -e /etc/profile.d/add_usr-local-games_to_PATH.sh ]; then
    echo "Adding /usr/local/games to PATH so you can run minecraft with 'minecraft' from terminal"
    Dots
    touch add_usr-local-games_to_PATH.sh
    echo "# set PATH so it includes /usr/local/games if it exists" >> add_usr-local-games_to_PATH.sh
    echo "if [ -e '/usr/local/games' ]; then" >> add_usr-local-games_to_PATH.sh
echo "    export PATH=/usr/local/games:$PATH" >> add_usr-local-games_to_PATH.sh
echo "fi" >> add_usr-local-games_to_PATH.sh
sudo chmod +x add_usr-local-games_to_PATH.sh
sudo mv add_usr-local-games_to_PATH.sh /etc/profile.d/add_usr-local-games_to_PATH.sh
source /etc/profile.d/add_usr-local-games_to_PATH.sh
echo "Done!"
echo ""
fi
#---------------------------------------------
echo "SUCCESS!"
echo ""
echo -ne "Hopefully Minecraft Server has been successfully downloaded and installed without any problems. Check your desktop and Applications menu for launchers. You can also run it from terminal with a 'minecraft' command."
echo "Visit the forum at http://www.minecraftforum.net/topic/1114574-bash-minecraft-installer/ (I would prefer you do that) or e-mail me at enkouyami@gmail.com if you have any questions"
echo "Enjoy! :D"
echo ""
} ## END ServerInstall

#------------------------------#
#  Uninstall Minecraft Server  #
#------------------------------#
UninstallServer() {
echo -n "Looking for Minecraft Server"
Dots
if [ -e /home/$(whoami)/Minecraft_Server/bin/minecraft_server.jar ]; then
    echo "Minecraft Server found!"
    echo "Do you wish to save your settings and save data? [y/N]"
    read character
    case $character in
        y | Y ) UninstallServerA
        echo "";;
        n | N ) UninstallServerB
        echo "";;
        * ) echo "Invalid choice!";;
    esac
UninstallServer2
else
echo "Minecraft Server not detected!"
fi
} ## END UninstallServer

#-------------------------------#
#  Uninstall Minecraft Server2  #
#-------------------------------#
UninstallServer2() {
    echo -n "Removing Desktop launcher"
    Dots
    rm -rf /home/$(whoami)/Desktop/Minecraft.desktop
    echo ""
#--------------------------------------------
echo -n "Removing menu launcher"
Dots
xdg-desktop-menu uninstall Minecraft_Server.desktop
echo ""
#--------------------------------------------
echo "Uninstalling the icon"
xdg-desktop-icon uninstall Minecraft_Server.png
echo ""
#--------------------------------------------
if [ -e 'home/$(whoami)/Desktop/Minecraft_Server.desktop' ]; then
    echo -n "Removing desktop launcher"
    Dots
    rm -rf '/home/$(whoami)/Desktop/Minecraft_Server.desktop'
    echo ""
fi
#--------------------------------------------
if [ -e /usr/local/games/minecraft_server ]; then
    echo -ne "Removing shell launcher in '/usr/local/games'"
    Dots
    echo "This requires root access:"
    sudo rm -rf /usr/local/games/minecraft_server
    echo "Done!"
    echo ""
fi
#--------------------------------------------
if [ -e /usr/local/bin/minecraft_server ]; then
    echo -ne "Removing shell launcher in '/usr/local/bin'"
    Dots
    echo "This requires root access:"
    sudo rm -rf /usr/local/bin/minecraft_server
    echo "Done!"
    echo ""
fi
echo "Minecraft Server has been uninstalled"
} ## END UninstallServer2

#-------------------------------#
#  Uninstall Minecraft ServerA  #
#-------------------------------#
UninstallServerA() {
    echo -ne "Uninstalling while keeping some items in ~/Minecraft_Server/"
    Dots
    echo ""
if [ -d /home/$(whoami)/Minecraft_Server/bin ]; then
    echo -n "Removing Minecraft Sever bin folder"
    Dots
    rm -rf /home/$(whoami)/Minecraft_Server/bin
echo ""; echo "Done!"; echo""
fi
} ## END UninstallServerA

#-------------------------------#
#  Uninstall Minecraft ServerB  #
#-------------------------------#
UninstallServerB() {
echo -n "Removing the Minecraft Server folder"
Dots
rm -rf /home/$(whoami)/Minecraft_Server
echo ""; echo "Done!"; echo""
} ## END UninstallServerB

#-------------------#
#  Troubleshooting  #
#-------------------#
Troubleshoot() {
echo "------------------------------------------------------"
echo ""
echo "#------------------------#"
echo "#  Troubleshooting Menu  #"
echo "#------------------------#"

echo "What would you like to do? (enter number of choice)"; echo ""
echo "0) Check to see default Java client (Recommended)"
echo "1) Install/update Java"
echo "2) Update Lightweight Java Game Library"
echo "3) Use Sun Java 6 to run minecraft from now on(May not work)"
echo "4) Use Oracle Java 7 to run minecraft from now on"
echo "5) Use OpenJDK 7 to run minecraft from now on"
echo "6) Manually select which Java to use"
echo "7) These options didn't solve my problem!"
echo "8) Return to the main menu"
read character
case $character in
    0 ) java -version
    javac -version;;
    1 ) JavaMenu;;
    2 ) UpdateLwjgl
    Troubleshoot;;
    3 )SunJavaDefault
    Troubleshoot;;
    4 )OracleJavaDefaultA
    Troubleshoot;;
    5 ) OpenJDKDefault
    Troubleshoot;;
    6 ) sudo update-alternatives --config java
    sudo update-alternatives --config javac
    sudo update-alternatives --config javaws
    echo ""; echo "Done!"; echo "";;
    7 ) echo "-------------------------------------------------"
    echo "If these Troubleshooting options didn't fix your, problem, I'd be glad to help you out!"
    echo "Visit the forum at http://www.minecraftforum.net/topic/1114574-bash-minecraft-installer/ (I would prefer you do that) or e-mail me at enkouyami@mail.com"
    echo "-------------------------------------------------"
    return;;
    8 ) return;;
    * ) echo "Invalid choice!"
    Troubleshoot
esac
} ## END Troubleshoot

#-----------------------------------------#
#  Update Lightweight Java Game Library   #
#-----------------------------------------#
UpdateLwjgl() {
echo -n "Checking for pre-existing lwjgl.zip"
Dots
echo ""
if [ ! -e /home/$(whoami)/.minecraft/lwjgl/ ]; then
    echo "Creating '~/.minecraft/lwjgl' folder"
    mkdir /home/$(whoami)/.minecraft/lwjgl
fi
cd /home/$(whoami)/.minecraft/lwjgl
if [ -e /home/$(whoami)/.minecraft/lwjgl/lwjgl.zip ]; then
    echo "lwjgl.zip detected! What would you like to do? (enter number of choice)"; echo ""
    echo "1) Re-download lwjgl and replace the previous one."
    echo "2) Continue"
    read character
    case $character in
        1 ) echo -n "Removing previous lwjgl.zip"
        Dots
        rm /home/$(whoami)/.minecraft/lwjgl/lwjgl.zip
        echo -n "Downloading"
        Dots
        wget -c http://sourceforge.net/projects/java-game-lib/files/latest/download?source=files
        mv download?source=files lwjgl.zip;;
        2 ) return;;
        * ) echo "Invalid choice"
        UpdateLwjgl
    esac
fi
#--------------------------------------------
echo -n "Extracting archive"
Dots
unzip /home/$(whoami)/.minecraft/lwjgl/lwjgl.zip
#--------------------------------------------
# These files in .minecraft/bin/ will be replaced:
# jinput.jar
# lwjgl.jar
# lwjgl_util.jar
#
# These files in ~/.minecraft/bin/natives/ will be replaced: 
# libjinput-linux.so
# libjinput-linux64.so
# liblwjgl.so
# liblwjgl64.so
# libopenal.so
# libopenal64.so
echo -n "Updating local lwjgl files"
Dots
echo ""
cd /home/$(whoami)/.minecraft/lwjgl/lwjgl-2.8.3/jar/
mv jinput.jar /home/$(whoami)/.minecraft/bin/
mv lwjgl.jar /home/$(whoami)/.minecraft/bin/
mv lwjgl_util.jar /home/$(whoami)/.minecraft/bin/
cd /home/$(whoami)/.minecraft/lwjgl/lwjgl-2.8.3/native/linux
mv libjinput-linux.so /home/$(whoami)/.minecraft/bin/natives
mv libjinput-linux64.so /home/$(whoami)/.minecraft/bin/natives
mv liblwjgl.so /home/$(whoami)/.minecraft/bin/natives
mv liblwjgl64.so /home/$(whoami)/.minecraft/bin/natives
mv libopenal.so /home/$(whoami)/.minecraft/bin/natives
mv libopenal64.so /home/$(whoami)/.minecraft/bin/natives
rm -rf /home/$(whoami)/.minecraft/lwjgl/lwjgl-2.8.3/
echo ""; echo "Done!"; echo ""
} #END UpdateLwjgl

#--------#
#  Main  #
#--------#
Main() {
echo "------------------------------------------------------"
echo ""
echo "What would you like to do? (enter number of choice) "; echo ""
echo "1) Check installed Java versions"
echo "2) Java Menu"
echo "3) Install Minecraft"
echo "4) Uninstall Minecraft"
echo "5) Install Minecraft Server"
echo "6) Uninstall Minecraft Server"
echo "7) Troubleshooting"
echo "8) Show license"
echo "9) Exit"
if [ -e /usr/local/games/minecraft ] && [ -e /home/$(whoami)/.minecraft/minecraft.jar ]; then
echo "0) Play Minecraft!"
fi
if [ -e /usr/local/games/minecraft_server ] && [ -e /home/$(whoami)/Minecraft_Server/bin/minecraft_server.jar ]; then
echo "-) Start Minecraft Server!"
fi
echo ""
while [ character != 1 ] && [ character != 2 ] && [ character != 3 ] && [ character != 4 ] && [ character != 5 ] && [ character != 6 ] && [ character != 7 ] && [ character != 8 ] && [ character != 9 ]; do
read character
case $character in
    1 ) CheckJavas
    Main
    return;;
    2 ) JavaMenu
    Main
    return
    ;;
    3 ) InstallMinecraft
    Main
    return;;
    4 ) UninstallMinecraft
    Main
    return;;
    5 ) ServerInstall
    Main
    return;;
    6 ) UninstallServer
    Main
    return;;
    7 ) Troubleshoot
    Main
    return;;
    'show w'|'show c' ) licenseMenu
    Main
    return;;
    9 ) return;;
    0 ) if [ -e /usr/local/games/minecraft ] && [ -e /home/$(whoami)/.minecraft/minecraft.jar ]; then
            minecraft
        fi;;
    - ) if [ -e /usr/local/games/minecraft_server ] && [ -e /home/$(whoami)/Minecraft_Server/mincraft_server.jar ]; then
            mincraft_server
        fi;;
    * ) echo "Invalid choice"
    Main
esac
done
} ## End Main

#-------------------------#
#      Call The Main      #
#-------------------------#
Main
# THE END
```

---

### Post by Dlambert on 2012-07-03
Very good. Thank you. Already have it running but this will help many people I'm sure.

---

### Post by Enkouyami on 2012-07-10
Version 1.4.1 fixes an incorrectly named function. I had two UninstallMinecraftA, the second one was to be UninstallMinecraft2.

---

