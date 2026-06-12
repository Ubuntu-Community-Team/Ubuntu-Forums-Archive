---
title: "Grub Image Script"
date: 2006-01-04
forum: Desktop Environments
---

### Post by dsbeav on 2006-01-04
I've been teaching myself Python during the holidays.  I also have been playing around with Grub and setting different images as the background.  So I wrote a little python script that takes most image types  and converts it to a grub useable file (640x480 res and only 14 colors) and then updates the grub conf file.

Hopefully someone else might find this useful.  I'm sure it could probally be written more elegantly in BASH, but hey, python is sweet and I wanted the practice.

Requirements: 

imagemagick (apt-get install imagemagick)
gzip
bash
python

You'll notice that a few lines into the script there are a few global variables.  You should set these. Grub normally resides in the /boot/grub directory.  I would suggest creating a directory images(sudo mkdir /boot/grub/images) and setting the variable IMAGE_LOCATION to that value. This directory will be where all the images created by grubconvert will reside.
GRUB_CONF = the location of your grub conf file.  In Kubuntu it is /boot/grub/menu.lst
GRUB_BACKUP = the location and name of the grub conf file backup that will be created when the script is ran for the first time (ex /boot/grub/menu.lst_backup
HARDDRIVE_LOCATION = The harddrive were the grub image resides.  '(hd0,6)' the 'hd0' means on the first harddrive (hd0 = 1st harddrive  hd1 = 2nd harddrive etc)  and the '6' means the sixth parition.  So for my computer my grub images are stored on the first harddrive's 6th partition.  Set these accordly.

Make the script executable and put it somewhere in your path. I put it in /usr/local/bin/grubconvert

usage: 

grubconvert [original image] [output name (no file extension)] 
(This will output a resized and decolored .xpm.gz file. This will not update your grub conf file)

sudo grubconvert [original image] [output name (no file extension)] [true]
This will update your grub conf file

Here it is: 
```


#!/usr/bin/env python
###########################################################################
# grubconvert.py
# Dwight Beaver
# dsbeav@gmail.com
###########################################################################
#                                                                         
#   This program is free software; you can redistribute it and/or modify  
#   it under the terms of the GNU General Public License as published by  
#   the Free Software Foundation; either version 2 of the License, or     
#   (at your option) any later version.                                   
#                                                       
###########################################################################

import sys
import string
import os

###########################################################################
#Global variables.  Change these to match your configuration
IMAGE_LOCATIONS = '/boot/grub/images/'
GRUB_CONF = '/boot/grub/menu.lst'
GRUB_BACKUP = '/boot/grub/menu.lst_backup'
HARDDRIVE_LOCATION = '(hd0,6)'


###########################################################################
def invalidArgError() :
    print "Usage == grubconvert [original_file] [newfile] [write to grub file (true or blank)]"

    
###########################################################################    
def invalidFileError() :
    invalidArgError()
    print "Original file does not exist"

    
###########################################################################    
def writeToGrub(new_image) :
    
    #Check for Root Access
    if not os.geteuid()==0:
        sys.exit("\nOnly root can write to GRUB_CONF file\n")
    
    #Make a grub backup if one does not already exist
    backup = GRUB_CONF + '_backup'
    if os.path.isfile(backup) :
            pass
    else :
         print "Making GRUB_CONF file backup"
         os.system("cp " + GRUB_CONF +  " " + GRUB_BACKUP)
    
    #Copy image to IMAGE_LOCATION 
    print "Moving image to IMAGE_LOCATION = " + IMAGE_LOCATIONS
    os.system("mv " + new_image + " " + IMAGE_LOCATIONS)
    
    #Update GRUB_CONF file with new slash image
    updateGrubConf(new_image)
    
    
###########################################################################
def updateGrubConf(new_image) : 
    
    #Slashimage command for grub conf file
    splashimg = "splashimage" + " " + HARDDRIVE_LOCATION  +  IMAGE_LOCATIONS + new_image
    
    #Write to the grub conf file
    try :
        
        #Open grub conf file
        conf = open(GRUB_CONF, "r")
        
        #Search for line containing splashimage 
        text = ""
        found = 'false'
        for line in conf :
            if line.find('splashimage') == -1 :
                text = text + line
            else :
                print "Splashimg command = " + splashimg
                text = text + splashimg + "\n"
                found = 'true'
        
        #No splash image in the file to begin with.  Add it
        if found == 'false' :
            print "Splashimg command = " + splashimg
            text = splashimg + "\n" + text 
        
        #Close readfile
        conf.close()
        
        #Write the Updated Grub File
        try:
            grubwrite = open(GRUB_CONF, "w")
            grubwrite.write(text)
            grubwrite.close()
            print "GRUB_CONF successfully updated"
        except IOError :
            sys.exit("\nError writing changes to file\n")
   
    except IOError :
        sys.exit("\nGRUB_CONF file does not exist\n")
        
        
    
###########################################################################    
def convertImage(original_image, new_image, add_to_grub) :
    
    if add_to_grub == 'true' :
       manipulateImage(original_image, new_image)
       new_image = new_image + ".xpm.gz"
       writeToGrub(new_image)
    else :
        manipulateImage(original_image, new_image)

###########################################################################
def manipulateImage(original_image, new_image) :
    if os.path.isfile(original_image) :
        convertstring = "convert -resize 640x480\! -colors 14 " +  original_image  + " "  + new_image + ".xpm && gzip " + new_image + ".xpm"
        os.system(convertstring)
    else : 
        invalidFileError()
        sys.exit()
    
###########################################################################
if __name__ == '__main__' :
    
    if len(sys.argv) < 3 :
        invalidArgError() 
    elif len(sys.argv)  > 3 :
        convertImage(sys.argv[1],  sys.argv[2], sys.argv[3])
    else :
        convertImage(sys.argv[1] , sys.argv[2], 'false')


```

Hope it's useful.  Email me if you have any problems.

Thanks

dsbeav

---

