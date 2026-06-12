---
title: "xfdesktop and xfce4-panel won't start unless sudo"
date: 2012-08-04
forum: Desktop Environments
---

### Post by Champlin93 on 2012-08-04
On start-up the desktop and panel flash for a moment and then disappear. If I try to run it in a terminal I get this
 xfce4-panel:
```
Segmentation fault (core dumped)
josh@josh-Satellite-C655:~$ 
(wrapper:5702): Gdk-WARNING **: GdkWindow 0x2e00004 unexpectedly destroyed
The program 'wrapper' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 222 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```
xfdesktop:
```
xfdesktop[5762]: starting up
Segmentation fault (core dumped)
```
If I run the --sync option as it says nothing changes and will still display the exact same thing in the terminal. If I run either of these programs under sudo then they work fine so I think this might be an issue of ownership. I just need to know what file i need to take ownership of.  
I'm running Ubuntu 12.04

---

### Post by ajgreeny on 2012-08-04
Have you added xfce to a full Ubuntu unity installation, or is this a Xubuntu system?

What happens if you make a new user, temporarily if you want, and then login to xfce with that user?  If the new user works OK it points to your /home folder or partition having problems in some configuration or other.

---

### Post by Champlin93 on 2012-08-04
I have a full Ubuntu unity installation.
I just tried creating a new user and it worked perfectly, however I really don't want to start over with a new account is there a way to make mine work?

---

### Post by Toz on 2012-08-04
Perhaps something is corrput in your sessions cache. Log out and go to the first tty (Ctrl+Alt+F1), log in and delete the sessioins cache:
```
rm -rf $HOME/.cache/sessions
```
...(NOTE: be careful typing in that command - it will recursively delete and you want to make sure you are only deleting the .cache/sessions folder in your home directory)

Go back to the gui (Ctrl+Alt+F7) and log in again.

---

### Post by Champlin93 on 2012-08-05
Deleting my .cache/sessions did nothing.  Isn't there a command other than  --sync that shows more detail?

---

### Post by Toz on 2012-08-05
It should log error messages to ~/.xsession-errors. Check there.

You might also want to rename your ~/.config/xfce4 directory (to ~/.config/xfce.BAK) from tty1. This will remove all your settings and when you re-login, Xfce will re-create it's configuration files (in case there is something corrupt there). Just note that all your configuration settings will be reset.

---

### Post by Champlin93 on 2012-08-08
Deleting my settings did nothing.
Here's my .xsession-errors file:
> xfce4-settings-helper: Another instance is already running. Leaving...

(xfwm4:9964): GLib-CRITICAL **: g_str_has_prefix: assertion `prefix != NULL' failed

(xfwm4:9964): xfwm4-WARNING **: The property '/general/double_click_distance' of type int is not supported

(xfce4-settings-helper:10115): GLib-CRITICAL **: g_str_has_prefix: assertion `prefix != NULL' failed
** Message: applet now removed from the notification area

---

### Post by Toz on 2012-08-08
Interesting.

Try doing them both at the same time.
- logout of the Xfce session
- Ctrl+Alt+F1
- clear the sessions cache:
```
rm -rf ~/.cache/sessions
```
- move the Xfce settings config directory
```
mv ~/.config/xfce4 ~/.config/xfce4.BAK2
```
- Ctrl+Alt+F7
- log back in to Xfce.

---

### Post by Champlin93 on 2012-09-02
No such luck

---

### Post by Champlin93 on 2012-10-04
Well I recently had to reinstall Ubuntu on my computer so I had a fresh start. XFCE worked perfectly for weeks until I ran a Minecraft installer shell script. Immediately after running the shell script xfdesktop suddenly crashed. When I ran it in the terminal i got that same exact error.  
> #!/bin/bash


# Alloc's Minecraft Installer:

# feel free to change, update, improve, and release this script

# suggestions of feedback? reach me at [email]alloc@dr.com[/email]

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
echo "@  [email]Alloc@dr.com[/email]                                             @"
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
wget -q [www.minecraft.net/download/minecraft.jar](www.minecraft.net/download/minecraft.jar)
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
wget -q [http://www.minecraft.net/favicon.png](http://www.minecraft.net/favicon.png)
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
echo -e "Minecraft has been successfully Downloaded and Installed \nCheck your desktop and Applications menu for launchers! \nYou can also run it from terminal with a 'minecraft' command! \ncontact: [email]alloc@dr.com[/email]" 
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
wget -q [http://www.minecraft.net/download/minecraft_server.jar](http://www.minecraft.net/download/minecraft_server.jar)

echo -ne "       -server_icon.png        "
echo     "   done!"
dots
wget -q [http://i.imgur.com/ugDRM.png](http://i.imgur.com/ugDRM.png)
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
So I suspect something this shell script does might be breaking XFCE due to the immediate crash of xfdesktop after running it but i have no idea what it could be or how to fix it. So far i've just used it to install minecraft and the server.

---

### Post by pqwoerituytrueiwoq on 2012-10-05
if something only works with sudo you probably messed up some permissions
if you had to use root you probally should have used gksudo
to fox permissions ```
sudo chown -r $USER:$USER ~/
```
and change your quote tags to code tags

---

### Post by Champlin93 on 2012-10-08
Didn't help. Maybe it's something in /usr I need to take ownership of?

---

### Post by JKyleOKC on 2012-10-09
> **Champlin93 said:**
> XFCE worked perfectly for weeks until I ran a Minecraft installer shell script. Immediately after running the shell script xfdesktop suddenly crashed.

==snip==

So I suspect something this shell script does might be breaking XFCE due to the immediate crash of xfdesktop after running it but i have no idea what it could be or how to fix it.No, you don't need to take ownership of anything in /usr. It's rather clear that something in that script has damaged your system. The solution is to avoid using the script for any purpose.

More poorly-written scripts may exist, and probably do, but this one with its frequent use of "sudo" to make system changes certainly rates high on the list of things to avoid. It probably DID mess up the permissions for something on the desktop or panel and as a result they now require root privilege just to load.

After running the script, trying to fix the system is somewhat akin to putting a band-aid on a slashed artery -- it won't help but only makes matters worse. Your best bet would be to re-install the system one more time, and this time leave the script alone. Or, if the game is that important to you, then leave things as they are and put up with using "sudo" each time you boot...

---

### Post by Champlin93 on 2012-10-09
Strange thing is it's not only sudo that can run it without a problem its any other user including guest. I might re-install at some point but for now I'm happy to using another desktop environment.  I'm definitely staying away from that shell script in the future.

---

### Post by JKyleOKC on 2012-10-09
Since all other users can work properly without having to use sudo, that's very strong evidence that nothing at all is wrong in /usr. Any problem in one of the system areas such as /usr would affect all users the same.

That, by elimination, leaves only your own home directory as the site of the problem. The script creates a hidden file there, to hold its configuration data, and it's possible that while doing so, it changed ownership of some critical configuration file from you to "root." I'd almost bet that it did this to ".ICEauthority" but it could have been any of several others that are accessed during your login process.

You can check this by issuing the command "ls -al" and posting the output here (use the code tags to keep the result readable). The thing to look for is files owned by root; you should own everything that's in your home directory although the directory ".." (which is another name for /home) should be owned by root.

---

