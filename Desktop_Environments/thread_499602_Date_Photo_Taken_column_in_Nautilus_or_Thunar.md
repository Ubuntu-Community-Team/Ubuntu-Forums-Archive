---
title: "Date Photo Taken column in Nautilus or Thunar?"
date: 2007-07-12
forum: Desktop Environments
---

### Post by ridgeland on 2007-07-12
Is there a way to see the "date photo taken" in a column in Nautilus?
Any scripts I can add in to get it?
I know that I can right click on a photo and go to Properties -> Image and see the "Date Taken" for a single file.  I want a column that shows Date Taken for all the files in the directory.
g-script's web page is so vague it's impossible to tell if such a script exists.

Can Thunar do this?

Why?
We take pictures with a digital camera.  I organize the photos by date, creating new directories for new sets of photos, like "2007 07 12 Brunet Island WI State Park".  When we return from our RV excursions we have photos from several dates, even months.  To minimize the drain on the camera battery I move all the photos to /Images/TempFromCamera.  Now the date columns in Nautilus all show today! Yuck! 

This was very easy in Windows (Windows Explorer) I just displayed the 'date taken' column.  Am I the first Linux user to want this?  Will Windows Explorer work under Wine?

Work arounds.  Don't protect the camera's battery.  Do all the sorting while the camera is still on.  Then the "Date Modified" can sustitute for "Date Photo Taken".  This is not welcome when you need to empty the camera fast to keep taking photos now.  Where is the "Date Created"?  I find this a major short coming in Nautilus since I've read that "date created" is a field in the Linux file system.

Once the photos have been moved from the camera to the PC the "Date Modified" is only the date the file was moved, no longer indicative of the date the photo was take.  If I later rotate a photo 90 degrees now I've got yet another date stamp, still misleading.  If the next day I rename a file from DSCN7648 to "Camp Site 40" another new date.  What a mess.

---

### Post by fjgaude on 2007-07-12
I'm not sure but a photo handling app like f-spot might do what you wish. Load the pix into it and not a temp file.

There must be a way to do what you want but it is beyond me, for the moment.

frank

---

### Post by Sweet Spot on 2007-08-16
Wow. I was just about to ask the same question. And yes, that is a horrible freeking mess which I'm embarrassed to say is a much better situation in Windows Explorer. That's depressing. 

I use Digikam to organize stuff BUT... I first get things straightened out in Nautilus, as in figure out which photos go to which category I created for them and this is problematic since I now have to sift through photos which were taken 2 days ago, and are mixed in with ones I took today. So sorting for cut and paste is a tedious task. Truly not cool. 

I'll explain further: I upload all of my photos that were taken each day to a folder called "Test Shots". A lot get deleted, and some make the cut into alternate folders (which are part of my "photos" folder) that are named appropriately. Example: People; Animals; Macro; Urban Action; Landscapes;  and so on. Those show up just spiffy as albums in Digikam, but I first have to separate those photos in the test folder. And in order to do that, it's easier to see all the photo's I've taken on one day, rather than seeing a few days mixed up all together. 

This stinks.

---

### Post by CameO73 on 2007-08-17
I have no idea how to do this in Nautilius, but maybe a special photo manager could help you out? Just take a look at [this page](http://linuxondesktop.blogspot.com/2007/05/managing-photos-on-your-desktop-linux.html) and [this page](http://www.linux.com/articles/58887) for some pointers.

Although I haven't personally used it for photos, F-Spot is a really good program (and can be easily installed using Synaptic -- just search for **f-spot**).

---

### Post by ridgeland on 2007-08-17
Thanks for the leads and the recommendations of photo management software available in Linux.
But...
So far every Linux package, just like Nautilus, shows ONLY the meta data for the ONE photo that is selected.
This is TOTALLY TOTALLY TOTALLY not what I want.  I want to see in Linux what I saw in WinXP Windows Explorer.  When viewing the files in a directory (folder) I want a column that says "Date Photo Taken".
Seems the only hope is an extension, add-on to Nautilus.   I'm not a programmer so I cannot create it.  The information is in each file, just like the preview thumbnail.  Someday someone with the skill set will make it happen, until then we'll just wait.

---

### Post by oneguess on 2008-01-26
For what it's worth the date is stored in the photo as a string so you can make a script to change the timestamp of your files or display the list of files time taken.

as an example:

strings picture.jpg | grep 2007

I don't have time to write the script or go into it further but from there you can pull the necessary information

---

### Post by kiratimerlan on 2008-01-27
did you  find any solution yet? i was having the exact same wish already for some time to just have a category in nautilus.

---

### Post by ridgeland on 2008-01-27
Hi kiratimerlan,

I still don't have a solution.

I bet Thunar gets there first.  I like its mass rename better that what Nautilus offers.

---

### Post by samwyse on 2008-01-27
Konqueror's "info list view" shows all kinds of metadata.

---

### Post by oneguess on 2008-01-28
I have a bit more time to actually put some more information and a script together.
Ok so as I said before the time is actually a date stored in binary as a string within the file, hence by using the command strings we can retrieve the date out of the file. Please note that I only assume that the date stored in the file is the date the picture was taken, so if it refers to something else in your files then this wont work for you and could be dangerous.
I've made a couple of scripts to do figure out the date depending on your needs (please note these haven't been fully tested and will have different effects on different systems):

To display the list of files and the date photo was taken:
==============================================

Using a temporary file to hold the list of files:
-------------
TMPFILES="/tmp/tmp_list_files.txt"
ls -1 > $TMPFILES
while read cmd_line
do
strings -f "$cmd_line" | grep '[0-9]\{4\}:[0-9]\{2\}:[0-9]\{2\}'
done < $TMPFILES
 
This method accepts files with spaces in them from processing without a temporary file:
-------------
for line in *.jpg
do
    strings -f "$line" | grep '[0-9]\{4\}:[0-9]\{2\}:[0-9]\{2\}'
done


This method removes the duplicates (requires unique to be installed)
------------
TMPFILES="/tmp/tmp_list_of_dates"
for line in *.jpg
do
    strings -f "$line" | grep '[0-9]\{4\}:[0-9]\{2\}:[0-9]\{2\}' > $TMPFILES
done
unique TMPFILES


Change the the date of the file to the time the picture was taken (be careful with this as it could have side effects)
==============================================
for line in *.jpg
do
    TMPVAL1=`strings "$line" | grep '[0-9]\{4\}:[0-9]\{2\}:[0-9]\{2\}' | tr -d ':' | tr -d ' '`
    TMPVAL2=`echo $TMPVAL1 | cut -c 1-12`
    TMPVAL3=`echo $TMPVAL1 | cut -c 13-14`
    if [ $TMPVAL2 -gt 1000 ]
    then
    if [ $TMPVAL3 -gt 0 ]
    then
    touch -t $TMPVAL2.$TMPVAL3 "$line"
    fi
    fi
    TMPVAL2=-1
    TMPVAL3=-1
done

*******************************************************
The author takes no responsibility for any use, damage caused by the scripts.

---

