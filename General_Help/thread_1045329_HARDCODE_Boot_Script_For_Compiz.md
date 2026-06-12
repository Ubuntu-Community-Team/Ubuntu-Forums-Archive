---
title: "HARDCODE Boot Script For Compiz"
date: 2009-01-20
forum: General Help
---

### Post by fryser_d on 2009-01-20
Hi there!

I searched for ages to write a script that would setup by desktop the way I wanted when the session starts.

There's always that fonction in System>Preferences>Sessions>[Tab]Option>Remember...

But with compiz and multifaces desktop, it doesn't really work :P

So here's a litle script I wrote to setup 'MY' desktop the way I wanted.

App used:
xte (Hard key input simulation):
> sudo apt-get install xte

Suppose to do:
[LIST=1][*]Ubuntu Auto start: Opera[*]Ubuntu Auto start: Amarok[*]Ubuntu Auto start:  Mount "Data"[*]Ubuntu Auto start: MSN Mercury[*]Ubuntu Auto start: My_Script[*]My_Script: Turn cube face2;[*]My_Script: Start Terminal> LS command[*]My_Script:  Start terminal> TOP command[*]My_Script:  Turn Cube Face 3[*]My_Script: Start VirtualBox VM[*]My_Script: Make VM fullscreen[*]My_Script: Turn Cube Face 4[*]My_Script: Open home Window[*]My_Script: Run Bitcomet(Torrent client) with wine [*]My_Script: Turn Cube Face 1[*]My_Script: Completed
[/LIST]

My_Script:
> #!/bin/bash
#HARDCODE INPUT SCRIPT, MUST CUSTOMIZE BEFORE USE!
echo "&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&"
echo "&&&&&&     DO NOT TOUCH THE KEYBOARD        &&&&&&"
echo "&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&"
echo "&&&&&& Autoboot script will run in few secs &&&&&&"
echo "&&&&&& DO NOT touch the keyboard until you  &&&&&&"
echo "&&&&&& see the confirmation screen.         &&&&&&"
echo "&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&"
echo "&&&&&&   @By Fryser                         &&&&&&"
echo "&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&"

sleep 6
xte "key Return" #All commands with "xte" is a direct keyboard input.
#In that case that input is for the autostart of opera to take out the confirmation choice.
sleep 7

#Compiz, 4 faces cubes Only! how to turn the cube.
echo "Turning cube*[Face2]..."
xte "keydown Control_L" 
xte "keydown Alt_L"
xte "key Right"
xte "keyup Control_L"
xte "keyup Alt_L"
sleep 1

#Standard terminal that I use everyday.
echo "Starting Terminal Shell..."
nohup gnome-terminal& #Start new terminal.
sleep 2
xte "str ls" #Input string
xte "key Return" #Input key
sleep 1
nohup gnome-terminal&
sleep 2
xte "str top"
xte "key Return"
sleep 1


echo "Turning cube*[Face3]..."
xte "keydown Control_L" 
xte "keydown Alt_L"
xte "key Right"
xte "keyup Control_L"
xte "keyup Alt_L"
sleep 1

#What used to mount "DATA" for virtualBox
#but had issues with permissions, so I used another way to automount.
#echo "Mounting DATA..."
#mkdir /media/DATA
#mount /dev/sda7 /media/DATA
#echo "Data partition is mounted."


echo "Starting Virtual machine..."
#nohup is to detach the process, otherwise if the main terminal
#is close all apps will close with it.
nohup gnome-terminal --execute virtualbox -startvm Win_XP& 
echo "Virtual Machine started."
sleep 40
#To enter FullScreen mode.
xte "keydown Control_R"
xte "key f"
xte "keyup Control_R"
sleep 4
xte "key Control_R"
sleep 2

echo "Turning cube*[Face4]..."
xte "keydown Control_L" 
xte "keydown Alt_L"
xte "key Right"
xte "keyup Control_L"
xte "keyup Alt_L"
sleep 3

#To open a home window.
echo "Open the home dir"
nautilus /home/fryser&
echo "Home dir opened"
sleep 1

#Bitcomet with Wine... use same syntaxt with anyother Wine Progz
echo "Starting BitComet..."
nohup env WINEPREFIX="/home/fryser/.wine" wine "C:\Program Files\BitComet\BitComet.exe"&
echo "BitCommet Started"
sleep 15

echo "Turning cube*[Face5]..."
xte "keydown Control_L" 
xte "keydown Alt_L"
xte "key Right"
xte "keyup Control_L"
xte "keyup Alt_L"
sleep 1

echo ""
echo ""
echo ""
echo "&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&"
echo "&&&   THE SCRIPT HAVE SUCCESSFULLY COMPLETED   &&&"
echo "&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&"
echo "&&&&&& You can now touch the keyboard.      &&&&&&"
echo "&&&&&& Have a nice day.                     &&&&&&"
echo "&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&"
echo "&&&&&&   @By Fryser                         &&&&&&"
echo "&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&"
#Have Fun! :)



Once everything is setup and the script is ready to be trigged(System>Preferences>Sessions>[Add your script]), reboot

And watch the magic :popcorn:

;)

---

