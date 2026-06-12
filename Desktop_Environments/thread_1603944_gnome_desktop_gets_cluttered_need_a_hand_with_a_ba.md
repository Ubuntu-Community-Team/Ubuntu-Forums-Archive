---
title: "gnome desktop gets cluttered need a hand with a bash script"
date: 2010-10-23
forum: Desktop Environments
---

### Post by swimfish on 2010-10-23
essentially what i need is, have one folder on my desktop called "central"  then in it have folders whos folder names were actually date stamps.  inside those date stamps would be all things saved to my desktop for that day.  under the folder whos name is date stamped would be a number of folders by which files were sorted by their extension such as links, images, documents.  the folder names, would be the extension, except in caps.  inside those folders would be "my stuff".  on dates that nothing was saved to desktop, there would be no datestamped folder.  i cannot offer money for this for i am broke as a doornail.  i could possibly trade or give a gift of something i had, should someone have the time to whip this up.

---

### Post by nitstorm on 2010-10-23
would be a nice idea to learn some commands and put it into bash yourself, 
```

#!/bin/bash

#Creating folder
echo "Creating Folders for today"
mkdir ~/Desktop/Central/$(date +%d%B%Y)
mkdir ~/Desktop/Central/S(date +%d%B%Y)/JPG


#moving the files
echo "Moving files"
mv ~/Desktop/*.jpg ~/Desktop/Central/$(date +%d%B%Y)/JPG


```

Replicate the commands as required depending on what files get clustered and stuff. ( I mean create whatever directories you need, and create whatever you want to be moved around )

---

### Post by nitstorm on 2010-10-23
Ofcourse you also have to create your Central folder separately, and that is a very basic, bash script but it should get the work done, as you learn more of bash, you can put in loops and all and make it nicer :) Have fun learning bash :)

---

### Post by swimfish on 2010-10-23
could you tell me how to not create a datestamp folder if there are no files for that day ?

---

### Post by swimfish on 2010-10-23
one last thing, btw, thanks so much.  

how do i handle files without an extension ?

also, could you teach me how on ubuntu forums to make that smaller box appropriate for computer output/input ?

have a very nice day sir.

---

### Post by Boondoklife on 2010-10-23
> **swimfish said:**
> one last thing, btw, thanks so much.  

how do i handle files without an extension ?

also, could you teach me how on ubuntu forums to make that smaller box appropriate for computer output/input ?

have a very nice day sir.

Try this out
```

#!/bin/bash
folder_container='central'            #Where to deposit the files
files_only=0                          #Copy only files or copy whole directories too
prompt_overwrite=0                    #Prompt to overwrite files or force overwrite
date_folder=`date +'%d.%m.%Y'`

#check if folder container exists
if [ ! -e ~/Desktop/"$folder_container" ]; then
    mkdir ~/Desktop/"$folder_container"
fi

#Find files, exlcude the folder container
if [ "$files_only" -ne 1 ]; then
    files=$( find ~/Desktop -maxdepth 1 | grep -v ~/Desktop/"$folder_container" | grep -ve 'Desktop$')
else
    files=$( find ~/Desktop -type f | grep -v ~/Desktop/"$folder_container" | grep -ve 'Desktop$')
    dirs=$( find ~/Desktop -type d | grep -v ~/Desktop/"$folder_container" | grep -ve 'Desktop$')
fi

#move files
IFS_OLD="$IFS"
IFS='
'
for f in $files; do
    #check if a folder for today exists
    if [ ! -e ~/Desktop/"$folder_container"/"$date_folder" ];then
        mkdir ~/Desktop/"$folder_container"/"$date_folder"
    fi
    
    #check to see if we are dealing with a folder
    if [ -d "$f" ]; then
        if [ "$prompt_overwrite" -eq 1 ]; then
           nice -n 18 mv "$f" ~/Desktop/"$folder_container"/"$date_folder"
        else
           nice -n 18 mv -f "$f" ~/Desktop/"$folder_container"/"$date_folder"
        fi
        rm -fR "$f"
    #if dealing with a file
    else
        extention=${f##*.}
        if [ "$extention" == "$f" ];then
            extention="NO_EXTENTION"
        fi
        extention=$( echo $extention | tr [:lower:] [:upper:] )
        if [ ! -e ~/Desktop/"$folder_container"/"$date_folder"/"$extention" ];then
            mkdir ~/Desktop/"$folder_container"/"$date_folder"/"$extention"
        fi
        if [ "$prompt_overwrite" == "1" ]; then
            mv -i "$f" ~/Desktop/"$folder_container"/"$date_folder"/"$extention"
        else
            mv -f "$f" ~/Desktop/"$folder_container"/"$date_folder"/"$extention"
        fi
    fi
done

for d in $dirs; do
    #remove left over folders
    rm -R "$d" > /dev/null
done
IFS="$IFS_OLD"

```*Please back up your data by copying it into your home folder just in case some thing go wrong.
**the option files_only controls if folders should be searched too. By default it will scan your folders on the desktop and move the files (including those in folders) to the central folder. Setting it to 0 will cause it to move just files and move the folders into a date folder as is.

---

### Post by swimfish on 2010-10-23
wow.  

thank you

---

### Post by nitstorm on 2010-10-23
@Boondoklife : Now that's something i revere, true bash scripting, hoping to write bash like that someday :)


@Swimfish : To post code in the forums, click on the # button above that says Wrap Code Tags :) 

Have a fun day all :)

---

### Post by Boondoklife on 2010-10-23
@nitstorm: Thanks and I look forward to seeing your contributions to the community.

@Swim: I posted this cause I had something very similar already written, but you really should look at how it is made and take it a part. There are lots of good examples and key elements in this script. Once you get the basics down, it just gets easier.

---

### Post by t3chn0b0y on 2010-10-23
This is a prime example of why I love Ubuntu so much. A community that helps one another, and a willingness to reach out and give a hand when one has issues or trying to learn more.:guitar:

---

### Post by swimfish on 2010-11-01
Boondoklife,

that script was actually a bit nightmarish to me.  it took things that weren't already filed in seperate folders and left the folder empty, and the folder naming scheme was a little inconsistant so that some folders might only have a file or two in them.  and there would be alot of inconsistant folders, not exclusively by filetype.  


```
bobcat@oceana:~$ cd ~/Desktop/central/
bobcat@oceana:~/Desktop/central$ ls
23.10.2010  24.10.2010
bobcat@oceana:~/Desktop/central$ ls -al
total 16
drwxr-xr-x  4 bobcat bobcat 4096 2010-10-24 13:36 .
drwxr-xr-x  5 bobcat bobcat 4096 2010-11-01 08:33 ..
drwxr-xr-x 89 bobcat bobcat 4096 2010-10-23 14:39 23.10.2010
drwxr-xr-x 46 bobcat bobcat 4096 2010-10-24 13:36 24.10.2010
bobcat@oceana:~/Desktop/central$ cd 24.10.2010/
bobcat@oceana:~/Desktop/central/24.10.2010$ ls -al
total 272
drwxr-xr-x 46 bobcat bobcat  4096 2010-10-24 13:36 .
drwxr-xr-x  4 bobcat bobcat  4096 2010-10-24 13:36 ..
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 01.990.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 05.08-14.58.24.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 1024.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 12.8.1777(W7-RC-01).ZIP
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 1.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 33430973.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 36888817.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 4.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 51334907.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 5.LARGE.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 65551FB6F6D25BA836C94D9B866018BD.GIF.JPEG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 6.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 9973.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 9QKPZXH7.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 BASILEO-800.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 COM.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 DEDCE.IT.THUMB.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 GIF
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 GIF.JPEG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 GODEL.550.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 IMG_ASSIST_CUSTOM.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 INI
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 JPEG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 JPEG.JPG
drwxr-xr-x  2 bobcat bobcat 90112 2010-10-24 13:36 JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 .JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 JPG_595.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 JPG_984.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 JPG (CASE CONFLICT 1)
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 JPG.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 JPG.PNG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 LARGE.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 LG.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 LOVESONG_MUSIC_SMALL.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 NNN80.090908125957.PHOTO00.QUICKLOOK.DEFAULT-245X169.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 NO_EXTENTION
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 PHP.JPEG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 PNG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 RUFOUS_HUMMINGBIRD.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 SIZED.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 SLEEPINGKOALA_24428.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 STARCHILD.JPG
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 THUMBNAIL.GIF
drwxr-xr-x  2 bobcat bobcat  4096 2010-10-24 13:36 UOVG3G4X.REDFOX2871.JPG
bobcat@oceana:~/Desktop/central/24.10.2010$
```

as you can see many of those are both messy and extraneous.  and i never hoped that existing folders would have their contents removed but i would not have mind if existed folders were moved to their corresponding date stamp folder as long as their contents were intact, in fact inside of those, it wouldn't be horrible if those files were sorted by extension either, as long as only "files on the loose" were arranged in a simple directory.  things such as JPG, GIF, ODT, DOC, PDF, HTML would have been a whole lots more suitable to me.  

if there is any chance on you or anyone else perfecting that script for my needs, i'd be happy to offer a small donation.  like i say i would like to keep contents of existing files in existing folders within that folder, but those could be sorted too.

and you'll note, that there were many directory whos folder names were based on the filename itself.  

thank you for your assistance.  looking forward to hearing from you or anyone else in getting this working.

you'll also note there are many many JPG entries there instead of one single solitary one for filenames of both extensions and some folders took on the names of the files themselves.

I could offer $15 to perfect this script.

---

### Post by Boondoklife on 2010-11-01
I am not sure what you mean? All the script did was:

1) create folders with a date stamp "DD-MM-YYYY"
2) find files on the desktop and create folders with the extentions for names (ISO, DOC, DOCX, ETC) (The only exception is files with no extention, those go in the NO_EXETENTION folder)
3) move the files to their corresponding folder.

The script can not move whole folders as they are not a file and it would be pointless as they would be empty considering the contents was moved into its extention folder.

Maybe if you can give me a few examples I can see, but it is working just fine for me.

Here is an output from me:
```
boondoklife@athena:~$ ls -lA /home/boondoklife/Desktop/
total 4591140
-rw-r--r-- 1 boondoklife boondoklife 4699979776 2010-10-25 21:56 3.iso
-rw-r--r-- 1 boondoklife boondoklife      75776 2010-10-31 12:31 bill.pdf
-rw-r--r-- 1 boondoklife boondoklife    1224092 2010-10-20 11:30 Namoroka_wallpaper.png
-rw-r--r-- 1 boondoklife boondoklife      40960 2009-09-17 11:18 Resume final.doc
boondoklife@athena:~$ ./clean_desktop 
boondoklife@athena:~$ ls -lA /home/boondoklife/Desktop/
total 4
drwxr-xr-x 3 boondoklife boondoklife 4096 2010-11-01 10:37 central
boondoklife@athena:~$ ls -lAR /home/boondoklife/Desktop/
/home/boondoklife/Desktop/:
total 4
drwxr-xr-x 3 boondoklife boondoklife 4096 2010-11-01 10:37 central

/home/boondoklife/Desktop/central:
total 4
drwxr-xr-x 6 boondoklife boondoklife 4096 2010-11-01 10:37 01.11.2010

/home/boondoklife/Desktop/central/01.11.2010:
total 16
drwxr-xr-x 2 boondoklife boondoklife 4096 2010-11-01 10:37 DOC
drwxr-xr-x 2 boondoklife boondoklife 4096 2010-11-01 10:37 ISO
drwxr-xr-x 2 boondoklife boondoklife 4096 2010-11-01 10:37 PDF
drwxr-xr-x 2 boondoklife boondoklife 4096 2010-11-01 10:37 PNG

/home/boondoklife/Desktop/central/01.11.2010/DOC:
total 40
-rw-r--r-- 1 boondoklife boondoklife 40960 2009-09-17 11:18 Resume final.doc

/home/boondoklife/Desktop/central/01.11.2010/ISO:
total 4589828
-rw-r--r-- 1 boondoklife boondoklife 4699979776 2010-10-25 21:56 3.iso

/home/boondoklife/Desktop/central/01.11.2010/PDF:
total 76
-rw-r--r-- 1 boondoklife boondoklife 75776 2010-10-31 12:31 bill.pdf

/home/boondoklife/Desktop/central/01.11.2010/PNG:
total 1196
-rw-r--r-- 1 boondoklife boondoklife 1224092 2010-10-20 11:30 Namoroka_wallpaper.png
boondoklife@athena:~$
```

---

### Post by swimfish on 2010-11-01
did you see my bash output with the folders whos names corresponded not to the extension but to the filename + extension itself ?

also -- i had folders with files within them.  they were already sorted by group, not filetype.  i would have hoped the script would have either left those intact, or mv the folders into the central folder under their appropriate date stamp and further sort them by extension after being moved (subfolders).  you'll note that it created many directories for me, that do not correspond with a filetype but rather to the name of the file itself.  those folders would actually more appropriately belong in another folder.  

i hope that helps.  please have a look at my ls -al

thank you

---

### Post by Boondoklife on 2010-11-01
> **swimfish said:**
> did you see my bash output with the folders whos names corresponded not to the extension but to the filename + extension itself ?

also -- i had folders with files within them.  they were already sorted by group, not filetype.  i would have hoped the script would have either left those intact, or mv the folders into the central folder under their appropriate date stamp and further sort them by extension after being moved (subfolders).  you'll note that it created many directories for me, that do not correspond with a filetype but rather to the name of the file itself.  those folders would actually more appropriately belong in another folder.  

i hope that helps.  please have a look at my ls -al

thank you

I did look at your output, but with out knowing what was there before it is useless. I posted a snippet from me running it.

There are a couple of options in the script, by default move file_only is set true. This will pull all the files from the desktop and all its subfolders, except then central folder. If you set it to 0 then it will just move folders themselves into a dated folder. There is not any logic in it to not move folders as I did not see it in your request. It can be done, but you have to be specific as to what you need.

As far as mangled names I have no idea, the script simply moves the file to another folder. At no point does it specify it's target name so it should be what ever it was named to begin with.

Try to rename the central folder to 'new' and recopy the script to ensure you have a valid copy. You can also download it [here]("http://ubuntuone.com/p/NG8/"). This should force it to reread all the files and sort them again.

I have added a warning to the post, before you run this please copy your data to your home folder just in case some thing goes ape.

---

### Post by swimfish on 2010-11-01
is there a certain location that script must be run from ?

did you by chance see my folders, that took on the names of a single file itself ?  i am getting too many folder names i guess, most of them were photos.  i had other types of documents, and was hoping for more simply output to minimize the number of different folders i get when i run the script.  the directory structure of your "central" folder ?

thank you so much.

you did understand that i had hoped for all .html files to go into a HTML folder and all .jpg and .JPG to go into a JPG folder, and all folders ending with .desktop should go into a DESKTOP folder (links to web pages).  things of that nature ?

---

### Post by swimfish on 2010-11-01
i'm really baffled.  for you -- the bash script worked absolutely perfectly.  i don't know what to say.

---

### Post by Boondoklife on 2010-11-01
> **swimfish said:**
> is there a certain location that script must be run from ?

did you by chance see my folders, that took on the names of a single file itself ?  i am getting too many folder names i guess, most of them were photos.  i had other types of documents, and was hoping for more simply output to minimize the number of different folders i get when i run the script.  the directory structure of your "central" folder ?

thank you so much.

you did understand that i had hoped for all .html files to go into a HTML folder and all .jpg and .JPG to go into a JPG folder, and all folders ending with .desktop should go into a DESKTOP folder (links to web pages).  things of that nature ?

Yup and if you look at my output it does just that. Try what I said and do it again, you may wanna just download it from the link and try that. Maybe you had a rogue post format or something.

---

### Post by Boondoklife on 2010-11-01
If you want, just hit me on one my IM's Ill see what we can get going.

---

