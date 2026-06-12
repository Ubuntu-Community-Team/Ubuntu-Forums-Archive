---
title: "Lubuntu Wallpaper Changer"
date: 2011-09-14
forum: Desktop Environments
---

### Post by Gaygerbil on 2011-09-14
I noticed a lot of people are having problems finding a proper wallpaper changer for Lubuntu. I for one haven't been able to find a program that actually works right with PCManFM, this includes Nitrogen and feh among others.

However I've been able to create a pretty simple script to get around this. 

Make sure to add this into your autostart programs if you want to use this. You can do this by going to:
 
/etc/xdg/lxsession/Lubuntu/autostart

Edit the file and add "@ /home/USERNAME/PATHTOSCRIPT" as you may notice with the other autostart apps.

PATHTOSCRIPT means the file path to script.

This is the script:

```
#!/bin/bash
#Script
n=10
while [ $n -le 10 ]
do
sleep 8m &&
NUMBER=$[ ( $RANDOM % 81 )  + 1 ]
pcmanfm --set-wallpaper=/FILE_PATH_TO_WALLPAPERS/$NUMBER.jpg
done
```

For FILE_PATH_TO_WALLPAPERS you set the correct file path for me this was /home/bewbman/Wallpapers/ then my wallpaper was selected from this folder. 

The n set to 10 is obviously to create an infinite while loop so this keeps going on as long as its running. 

You can set whatever time you want for sleep, whether it be 5s or 1h, you choose that option.

The NUMBER variable is to create a random variable to choose a picture from your folder, in here I have renamed the desktop pictures 1 - 81. 

So if you have 50 wallpapers **MAKE SURE** to change the number after "$RANDOM %" to how many wallpapers you have.

It will pick a random number from 1 to whatever the number you have defined is and set the file path to that.

For png images you can simply rename them to jpgs and it will recognize them as jpgs. 

When taking this script after you've modified it to the correct values place it in the folder you want, and save it in a text file. Make sure the name ends in .sh to make it a script. For me it was random.sh. Make sure to right click on it as well and go to properties, go to properties and click on 'Make It Executable'.

After this you can test it in terminal just by running the filepath/filename.sh in terminal.

It needs some user modifications but it works as a charm and as far as I'm concerned I haven't found anything that really works for this. This is also very light and does the job that you want so I'm happy with it. Was sharing it for others.

---

### Post by jonee316 on 2011-10-18
cool! I will test it later. 

Some suggestions for tweaks- 
- get a random image from a directory (including subdirectories) without renaming the images to numbers
- allow png, jpg, jpeg and gif extensions

---

### Post by Rodney9 on 2011-10-26
I can't get this to work, I have 4 wallpapers I wish to change every 15 minutes.

I have re-named my wallpapers numerical 1 to 4.

Change the sleep number to 15m , this means how often they will change, does it ??

Changed the number after "$RANDOM %" to 4

Named it wallpaperchange.sh , made it executable.

Here is my wallpaperchange.sh

```
#!/bin/bash
#Script
n=10
while [ $n -le 10 ]
do
sleep 2m &&
NUMBER=$[ ( $RANDOM % 4 )  + 1 ]
pcmanfm --set-wallpaper=/home/rodney/wallpaper/$NUMBER.jpg
done
```

What am I doing wrong ?


Rodney

---

### Post by ac_d600 on 2011-10-26
Your images are jpg or you have named as such?
Your path to your images is correct?

Just trying to think about what it could be, my experience
has been its usually the simplest thing that causes the biggest
headaches. :)

---

### Post by makitso on 2011-10-26
Yea, I could not get it to work either.  Running it in  terminal mode gave me some unknown error on line 8 about an invalid option for PCmanfm.

---

### Post by Rodney9 on 2011-10-26
> **makitso said:**
> Yea, I could not get it to work either.  Running it in  terminal mode gave me some unknown error on line 8 about an invalid option for PCmanfm.

When I run it in a terminal nothing happens, the cursor just goes to the next line, and nothing.

---

### Post by Rodney9 on 2011-10-26
Well Well Well
I left the terminal open and went and had breakfast, came back and the wallpaper is changing, HURRAH :D

---

### Post by amjjawad on 2011-10-26
I'm going to test that on 11.04 and 11.10 and if all will work, I'll include this guide on my Mega Thread :)

Lubuntu needs stuff like that. Keep them coming ;)

---

### Post by Gaygerbil on 2011-11-11
I'm glad to hear someone got this to work, sorry I haven't logged on to my Ubuntu forums account in a while so I had no idea I got views and replies.

A great way to test this is just set it to 5s instead of 8m to see what's wrong. If people are still having problems post what your code is and I can help. 

Keep in mind you can autostart this script with Openbox or assign it to a shortcut.

Not only this you can use this base script to create a next wallpaper script like I have done which doesn't autoswitch just gets another one and put int he Openbox menu so you can right click your desktop and hit Next Wallpaper. 

If people need more explanation on this I can definitely help out.

I will work on finding a way around png and other image types. I also want to create something that chooses a random file from a directory of course that might take a bit, I created this as a quick bandage for a problem many people face.

---

### Post by Rodney9 on 2012-01-01
Any news on updates, I am enjoying it as it.

Rodney

---

### Post by singedwings on 2012-01-28
I have an alternative script for anyone interested. Adapted from the script I used to use with gnome, with help from the script's original author mhgsys.```
#!/bin/bash
until [ 1 -eq 2 ]; do

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/tv/Public/Wallpaper"

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
pcmanfm --set-wallpaper=$PIC

sleep 30s
done
```

---

### Post by Gaygerbil on 2012-02-22
This script works beautifully, thank you for the help this addresses the two biggest problems I've had one the filename and two the filetype. Thank you, I'm sure this will help many Lubuntu users who see this. 

Love the avi BTW.

---

### Post by jhonsdeya on 2012-02-22
Yeuh I like this, I new make ubuntu thanks

---

### Post by singedwings on 2012-06-08
This works fine with 12.04 and I have added the commands to set the wallpaper mode as well!```
#!/bin/bash
until [ 1 -eq 2 ]; do

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/tv/Public/Wallpaper"

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
# Set mode of desktop wallpaper. <mode>=(color|stretch|fit|center|tile)
#  --wallpaper-mode=fit
pcmanfm --set-wallpaper=$PIC --wallpaper-mode=fit

sleep 30s
done
```

---

### Post by xfctr on 2012-08-15
I suggest you try Variety Wallpaper Changer - it is a new application that I've been working on during the past 2-3 months and I think it is shaping as one of the best wallpaper changers for Linux. Response from users so far has been vastly positive.

Current version in the ppa (0.4.7) supports Lubuntu out-of-the-box.

Supports local folders, online sources (Flickr, Wallbase and several others), can apply some nice filters to the images (e.g. heavy blurring for obtaining abstract blurry wallpapers in the spirit of the default one in Ubuntu).

[Video demo for 0.4.3]("http://www.youtube.com/watch?v=7bmpNR7mQ4k")
[Screenshots]("http://imgur.com/a/BFMJn")
[Project page and source-code]("https://launchpad.net/variety")

Installation (installs in /opt):
```

sudo add-apt-repository ppa:peterlevi/ppa
sudo apt-get update 
sudo apt-get install variety
```
Or simply grab the latest deb from [here]("https://launchpad.net/~peterlevi/+archive/ppa/+packages")

The version in Ubuntu Software Center (0.3.9) is outdated and does not work in Lubuntu.

---

### Post by critin on 2012-09-08
> **xfctr said:**
> I suggest you try Variety Wallpaper Changer - it is a new application that I've been working on during the past 2-3 months and I think it is shaping as one of the best wallpaper changers for Linux. Response from users so far has been vastly positive.

Current version in the ppa (0.4.7) supports Lubuntu out-of-the-box.

Supports local folders, online sources (Flickr, Wallbase and several others), can apply some nice filters to the images (e.g. heavy blurring for obtaining abstract blurry wallpapers in the spirit of the default one in Ubuntu).

[Video demo for 0.4.3]("http://www.youtube.com/watch?v=7bmpNR7mQ4k")
[Screenshots]("http://imgur.com/a/BFMJn")
[Project page and source-code]("https://launchpad.net/variety")


Installation (installs in /opt):
```

sudo add-apt-repository ppa:peterlevi/ppa
sudo apt-get update 
sudo apt-get install variety
```Or simply grab the latest deb from [here]("https://launchpad.net/~peterlevi/+archive/ppa/+packages")

The version in Ubuntu Software Center (0.3.9) is outdated and does not work in Lubuntu.

In the last two days I've installed Variety to two computers.  It was  easy to install and set up, and the wallpapers change just like they're  supposed to.  Good work!!

Only one thing.  I chose to add the clock and I like it, but I can't find the edit page to change it from 12 hour to 24 hour.   

I'm back for the addy so I can install to another machine now.  Guess I need to bookmark it.  lol

---

### Post by Guilden_NL on 2012-09-10
> **xfctr said:**
> I suggest you try Variety Wallpaper Changer - it is a new application that I've been working on during the past 2-3 months and I think it is shaping as one of the best wallpaper changers for Linux. Response from users so far has been vastly positive.

Current version in the ppa (0.4.7) supports Lubuntu out-of-the-box.

Supports local folders, online sources (Flickr, Wallbase and several others), can apply some nice filters to the images (e.g. heavy blurring for obtaining abstract blurry wallpapers in the spirit of the default one in Ubuntu).

[Video demo for 0.4.3]("http://www.youtube.com/watch?v=7bmpNR7mQ4k")
[Screenshots]("http://imgur.com/a/BFMJn")
[Project page and source-code]("https://launchpad.net/variety")

Installation (installs in /opt):
```

sudo add-apt-repository ppa:peterlevi/ppa
sudo apt-get update 
sudo apt-get install variety
```
Or simply grab the latest deb from [here]("https://launchpad.net/~peterlevi/+archive/ppa/+packages")

The version in Ubuntu Software Center (0.3.9) is outdated and does not work in Lubuntu.

Thank you very much!  This is a great addition to Lubuntu - it's great!

---

### Post by xfctr on 2012-09-12
Thanks guys for the nice words about Variety, it's always great to hear feedback from the users.

> **critin said:**
> Only one thing.  I chose to add the clock and I like it, but I can't find the edit page to change it from 12 hour to 24 hour.

I have just created a FAQ about editing clock settings, it answers your question about 12/24-hour format: [click here]("https://answers.launchpad.net/variety/+faq/2095")

---

### Post by Gaygerbil on 2013-01-06
Hey guys me again been working on integrating a Previous Wallpaper option into Openbox, cuz why not....

Got some stuff going if anyone wants to help though it would be greatly appreciated.

```

#!/bin/bash
DIR="/home/bewbman/Pictures/Wallpapers"
declare -i x
declare -i y
if [ $[x] = "1" ];
then
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)
pcmanfm --set-wallpaper=$PIC
echo $PIC
while read line; do 
y=$line+1
done < /home/bewbman/Documents/Scripts/number2.txt
echo $y > /home/bewbman/Documents/Scripts/number2.txt
if [ $[$y % 2] = "0" ];
then
echo $PIC > /home/bewbman/Documents/Scripts/number.txt
echo $y
fi
fi
if [ $[x] = "2" ];
then
while read line; do 
PIC=$line
done < /home/bewbman/Documents/Scripts/number.txt
pcmanfm --set-wallpaper=$PIC
fi

```

Basically it would set X as 1 for clicking 'Next Wallpaper' through Openbox and X as 2 for clicking 'Previous Wallpaper' when you click Next Wallpaper it'll store the value of the wallpaper you go to every other time, allowing for you to revert back to the previous one if you chose to.

However there are problems with this script which is what I'm currently working on...for the hell of it. One being that clicking 'Previous Wallpaper' more than once results in well nothing happening because it doesn't store multiple values. One thing I want is for there to be a log of all the wallpapers I switch to and for me to be able to keep going back until I go to the first one in the log where it tells me that. If I click next after say 5 times of going back I want it to clear everything ahead of it, so the 4 wallpapers you just hit previous on would be removed from the log.

Any help would be greatly appreciated as I'm fairly new to Bash scripting in general and don't often do it.

---

