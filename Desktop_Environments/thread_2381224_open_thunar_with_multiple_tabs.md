---
title: "open thunar with multiple tabs"
date: 2017-12-28
forum: Desktop Environments
---

### Post by Kilarin on 2017-12-28
I had what I thought was a simple question, but I can't seem to find an answer anywhere.
I want to open thunar from the command line, with two different folders in two different tabs.
if I do

thunar /home/username/location1 /media/otherdrive/location2

It opens up two different thunar windows.  Is there some option to say open only ONE thunar window, and open these folders in 2 different tabs?

If there isn't, there ought to be. :)

Thank you

---

### Post by flocculant on 2017-12-31
I don't think there's an option to do so.

Assuming these places are somewhere you want to regularly visit, then add them to the Places sidebar (which is what I do)

You could report it to [bugzilla]("https://bugzilla.xfce.org/enter_bug.cgi?product=Thunar&component=Core&resolution=---"), and hope someone who can do something is actually interested enough to do so. 

Or you could report it and create a patch to add what you want ;)

---

### Post by Kilarin on 2017-12-31
Ah well, I guess I'll have to look into adding a patch, if I can find the time.  That is the proper way to do with with open source anyway.  Want a fix?  Fix it yourself! :)
Thanks!

---

### Post by LostFarmer on 2017-12-31
I have a script that works with nemo but just tested it with thunar and it does not work.  one reason nemo uses 'F3' to open tab and thunar uses the right mouse and I do not know how to send the right mouse code  in the script or (?).  If you want to look at the script I can post it , about 100 lines.  The script asks for the paths and check if they are valid and root privilege not required and then opens nemo in 2 pane mode

---

### Post by Kilarin on 2017-12-31
Sure, would be happy to see it, and thank you for sharing!

---

### Post by LostFarmer on 2017-12-31
the below script works for 'nemo' only, not yet works for 'thunar' and might never work.  There is some code that does not work, for opening nemo as root and it is commented out (#).  You will have to change all occurrence of 'nemo' to 'thunar' to even try.

there could be other problems, I do not know how to write script, this is taken from 2 non-working scripts found on line. (trial and error)

```
#!/bin/bash

#check if xdotool is installed
dpkg -s xdotool &> /dev/null
if [ $? -ne 0 ]; then
        echo -e "\e[31m  needed program -- xdotool --is NOT installed! \e[0m"
read -p "press enter to exit and run-- apt install xdotool --or some other "
exit
fi

# get first directory path and check permission
root=0
n=0
while  [ $n -lt 1 ]
do
read -r -p " Enter the path of left pane. -- /boot--- " theSubDir1
if  [ -d "$theSubDir1" ];then #test if directory
if [ ! -r "$theSubDir1" ]  #test for permission
then
echo -e "\e[31m Read access permission required on selected path\e[0m" , "\e[35m re-enter path \e[0m"
#root=$(($root + 1))
#n=$(($n + 1))
continue
fi
n=$(($n + 1))
else
 echo -e "\e[31m input not a directory, try again\e[0m"
continue
fi 
done  
# get second directory path and check permission
n=0
while  [ $n -lt 1 ]
do
read -r -p " Enter the path of right pane. -- /etc--- " theSubDir2
if  [ -d "$theSubDir2" ];then
if [ ! -r "$theSubDir2" ]
then
echo -e "\e[31m Read access permission required on selected path\e[0m" ,# "\e[35m re-enter path \e[0m"
#root=$(($root + 1))
#n=$(($n + 1))
continue
fi
n=$(($n + 1))
else
echo -e "\e[31m input not a directory, try again\e[0m " 
continue
fi 
done  

#open nemo -check if root permission needed code not used till -else
if [ $root = "1" ] ; then
pkexec /usr/bin/nemo $theSubDir1
sleep 1.5
xdotool key --clearmodifiers F3
sleep 0.5
xdotool key Control_L+l
xdotool type $theSubDir2 
echo line76
xdotool key Return
exit
else
#no root permission
nemo $theSubDir1
fi
 sleep 1.5
file_browser_id=$(xdotool search --name "$theSubDir"| head -1 )
# check if nemo is running
if [ -n  "$file_brower_id" ]; then
  echo "\e[35 mnemo is not running. restart \e[0m"
  exit 
fi 
#open pane #2 to path
xdotool key --clearmodifiers F3
sleep 1.5
xdotool key Control_L+l
xdotool type $theSubDir2 
xdotool key Return
exit
```

If you get it working , post the updated one

---

