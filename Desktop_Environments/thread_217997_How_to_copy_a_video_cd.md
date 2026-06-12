---
title: "How to copy a video cd?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by beforewisdom on 2006-07-17
What is the easiest way to copy a video cd in Ubuntu?

I'm not adverse to the command line( as long as I have the commands! :) )

Thanks in advance

Stevve

---

### Post by bruenig on 2006-07-18
perhaps this will help?
[http://www.vcdimager.org/](http://www.vcdimager.org/)

---

### Post by orb9220 on 2006-07-18
What kind of video ? there many kinds of video cd's VCD,SVCD,DVD ?

If you are talking dvd like a movie you bought or rented. Then you are talking about a 8.5 dual layer DVD and you want to put it on a single layer dvd +r that is 4.38GB then it has to be ripped and compressed to fit.

You can also rip it to fit on a reg 700 mb cd+r disk.
First you have to decide what exactally what you want.

Well I want to back up my DVD movie collection cheapest way and keep the menu's and extra menu's Just like the orig.

Well for that you need a program that rips the dvd to hardrive and does compression so that you can fit a 8.5GB disk onto a 4.38GB disk.

I use a windows freeware program called dvd shrink running under wine.
In fact it is ripping and compressing a movie right this second. When it's 
done which takes about an 56-60 mins. then I can run another program to burn it to a blank disk. DVD Shrink also removes the encryption and regions code.

There are other ways just search the forum.
Thsi is what i used to install wine and dvd shrink by this thread
[http://ubuntuforums.org/showthread.php?t=78611](http://ubuntuforums.org/showthread.php?t=78611)

---

### Post by beforewisdom on 2006-07-18
I had no idea it would be this complicated.  I used to do it with knoppix & kde just by firing up k3b and then "copy cd".

Oh well, I get liberated from other hassles with ubuntu so it more than balances out.

---

### Post by taurus on 2006-07-18
You can use k3b even if you use Gnome!!!  Just install it and have fun with it...

```

sudo apt-get update
sudo apt-get install k3b

```

---

### Post by Bolorino on 2006-07-18
I did this little shell script for a friend.
It reads a VCD from a CD/DVD device and copies to another one.
I think the same device could be used -but not sure-.
It uses cdrdao.

Save it as duplicatevcd and set execution permission (chmod +x duplicatevcd).
Ensure READ_DEVICE and WRITE_DEVICE point to your CD unit.

```
#!/bin/bash
# Duplicate VCD (duplicatevcd)
# Reads VCD from device1 and writes VCD to device2
# Jose Bolorino

#Config 
ROOT_UID=0   # Root has $UID 0.
TMP_PATH=/tmp  #Tmp iso images
READ_DEVICE=/dev/hdc
WRITE_DEVICE=/dev/hdd
WRITE_SPEED=16
# End config

if [ "$UID" -eq "$ROOT_UID" ]  # Will the real "root" please stand up?
then
   cdrdao read-cd -v 2 --device $READ_DEVICE --read-raw --datafile $TMP_PATH/image.bin $TMP_PATH/image.toc
   cdrdao write -v 2 --device $WRITE_DEVICE --speed $WRITE_SPEED --buffers 64 $TMP_PATH/image.toc
else
  echo "Write: sudo duplicatevcd OR sudo ./duplicatevcd"
fi

exit 0
```

---

### Post by beforewisdom on 2006-07-22
I got "error reading /dev/hdc exclusively" thanks anyway.

I found instructions for doing this with cdrdao, but I need to get information from cdrecord -scanbus to use it, and that doesn't work with the latest kernel that the update manager installed for me :(

---

### Post by manmath on 2007-11-27
The most definite ways are:

copy the disc to the hard disk as a raw/iso (dd if=/dev/cdrom of=/tmp/image.iso) then use vcdgear to extract the dat to mpg:

vcdgear -raw2mpg /tmp/image.iso movie.mpg


This is pretty much the method I would recommend as well, the one change I would add is that I use readcd as it handles copying from the CD medium much better than dd, IMHO.

"vcdgear -fix -cue2mpg" has been reliable in extracting a working mpg from a standard image file set.

Just tried with DD and had an issue. readcd is a good tool, I prefer cdrdao myself and this command line should get you a lovelly bin/cue to use vcdgear on:

cdrdao read-cd --device ATA:1,1,0 --driver generic-mmc-raw --read-raw image.cue

Change the device for whatever is your reader!

OR

install readvcd and then 

# readvcd 2 > mv.mpg

OR

Install vcdimager
# vcdxrip

OR

install cdfs
mount -t cdfs /dev/cdrom (or whatever your drive is) /home/movie (or whatever your destination)

---

