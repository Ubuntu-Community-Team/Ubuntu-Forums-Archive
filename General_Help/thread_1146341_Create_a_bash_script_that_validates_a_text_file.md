---
title: "Create a bash script that validates a text file"
date: 2009-05-02
forum: General Help
---

### Post by aikiwaza on 2009-05-02
I am writing a program that will only run when a USB key is inserted and do a file transfer.  In my program I want it to check a file that has a date on it.  The end goal is to have a date set on the USB key, and if the current date is greater than the date on the USB it will end the program with out doing a transfer.  Also I would like to create a security key on the USB so that only keys with this security code on the key (like a dongle) will allow it to work.  My programming is limited,so please if you can, be clear about what you are saying.

Essentially I guess I am trying to create a registration for the program based on the USB.

In this my user name is aikiwaza

Here is what I have:

#For sound you may need to run sudo apt-get install sox
# Get username
# USERNAME probably isn't necessarily defined already...

USERNAME=$(id -nu) 
SEARCH_KEY='1234567890'
SEARCH_DATE=''
FILE='/media/USB/security'

#here i should note that I want the program to search a text file on the USB key (called security) for 1234567890 to validate that it is correct if not kill the program.  I also want it to look at the same text file and look at a date written there (ie 5/2/09) and if todays date is greater I want it to kill the program.

#This is for when the USB is plugged in successfully.

#CONNECT=$(aplay -d playback /home/$USERNAME/sounds/connect.wav)

#One for when it is ok to disconnect.

#DISCONNECT=$(aplay /home/$USERNAME/sounds/disconnect.wav)

#One for when the error kills the program.

#ERROR_SOUND=$(aplay -d playback /home/$USERNAME/sounds/error.wav)

#If the drive is not designed to update, ie: has no "security" file, the program dies quietly.
#Well not quite because it should give an audio cue to the users but it should not give a error
#that requires user intervention.

if [ ! -d "/media/USB/security" ]
  then 
     exit 0

else 

grep  $SEARCH_DATE $FILE > /dev/null

if [ $? -eq 0 ] ; 
   then 
        # Its found, so now we check the file to validate it.   
            
	#VERY IMPORTANT: using current date to verify.
        current_time=`date +%k%M%S`
        
        if 
           $current_time > $SEARCH_DATE
               then 
                   #should play a sound to notify of error
                   exit 0 
        fi  
fi 

grep  $SEARCH_KEY $FILE > /dev/null

if [ $? -eq 0 ] ; 
   then 
        # Its found, so now we check the file to validate it.   
            
	if 
           $SEARCH_KEY != "1234567890"
               then 
                   exit 0 
        fi  
fi 


fi

#Copy over all files on the external drive.
#The sleep time is just to give it time to mount.

sleep 5

#This is the process of copying files
#This should zip the data folder into a .zip and move it to the USB key.

zip /home/aikiwaza/Desktop/data.zip /home/aikiwaza/Desktop/data/*.*
mv /home/aikiwaza/Desktop/data.zip /media/USB/audio/

#This process will copy a file to the computer.  

rsync -ru "/media/USB/" "/home/aikiwaza/Desktop/"

#This sleep is to allow the transfer time to take place.

sleep 5

#This is supposed to close the open file browser windows that opened on the mount.

killall nautilus

#This is to unmount the drive afterward. 
#The sleep is just to give time for all processes to finish before unmounting.
#This also needs to have an audio cue that will notify the user that it is safe to remove.

sleep 5

#umount /media/USB/

---

