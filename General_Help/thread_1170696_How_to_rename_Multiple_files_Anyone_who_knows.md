---
title: "How to rename Multiple files? Anyone who knows ?"
date: 2009-05-26
forum: General Help
---

### Post by nickdbliss on 2009-05-26
Hi,
I was trying to rename files but it is a lengthy job if u have camera pics more than 200. So does anyone know any method, script, software or command for the same? I will really appreciate that Or else i have to continue renaming files manually lolz. 1,2,3,4,5... Ah...wheww...

---

### Post by swimmin on 2009-05-26
```
mv blabla*.jpg *.jpg
``` Could that work? * represents number?

---

### Post by 73ckn797 on 2009-05-26
I use Thunar, available in Synaptic. The renaming feature is fairly simple. I use it several times daily renaming 10 to 35 pictures at the same time.

---

### Post by nickdbliss on 2009-05-26
i dont think so. it is for renaming or moving one file at a time, i guess.

---

### Post by nickdbliss on 2009-05-26
> **73ckn797 said:**
> I use Thunar, available in Synaptic. The renaming feature is fairly simple. I use it several times daily renaming 10 to 35 pictures at the same time.

Thanks BUddy u save my day. Ah Thunar here i come.

---

### Post by michy99 on 2009-05-26
gprename is also a handy tool.

---

### Post by 73ckn797 on 2009-05-26
> **michy99 said:**
> gprename is also a handy tool.

I tried that one before. To me it was not as user friendly as Thunar. It really depends on what you get accustomed to.

---

### Post by leandromartinez98 on 2009-05-26
A script like this does the job:

```

#!/bin/bash
i=1
for file in `ls *.jpg`; do
  echo "Moving $file to newname$i.jpg"
  mv $file newname$i.jpg
  i=`expr $i + 1`
done   

```

ps. Test it with a copy of some of the files before to see
if it is doing exactly what you expect, in this case the 
script renames the files to newname1.jpg, newname2.jpg...

You can use other strategies to rename some other way if
you want.

(write these lines to a file, e.g. "movefiles.sh", and 
turn the file into an executable file with

chmod +x movefiles.sh

run it with

./movefiles.sh

The good thing about learnign a some bash scripting is that
you will learn how to do automatically many other tasks, with
the same logic.

---

### Post by 73ckn797 on 2009-05-26
> **nickdbliss said:**
> Thanks BUddy u save my day. Ah Thunar here i come.

My need for renaming files always involves renaming from the camera name, such as DC00123.jpg, DC00124 and so forth into a sequence of 1234 01.jpg, 1234 02.jpg or whatever it needs to be. If you have a series of photos of a family gathering just rename them to family_gathering 01.jpg and they will be sequential with the name + 01, 02 and so forth.

---

### Post by kay-man on 2009-05-26
I use this to rename my pictures:

```
#!/bin/sh

images=`find -maxdepth 1 -iname '*.jpg'  -printf "%f\n"`

index=1
for imageFile in $images
do
  counter=`printf %03d $index`
  # Construct new filename
  newName="foto-"$counter$1".jpg"
  echo "Renaming $imageFile to $newName"
  # Rename the file
  mv $imageFile $newName
  # Increment counter
  index=$(($index+1))
done
```

it creates names like "foto-" and then a running number padded with zeroes to a length of three, followed by an optional string, which is a parameter to the script.

Some tweaking with the order of these elements should give you what you need.

---

### Post by nickdbliss on 2009-05-26
Thanks guys for your help. I checked thunar and actually renamed all my files with it. I was renaming them to Friendwedding1,2,3 and so on. I found it very simple and effective. As far coding goes, i normally use C but guess it's time to learn something new.

---

### Post by 73ckn797 on 2009-05-26
> **nickdbliss said:**
> Thanks guys for your help. I checked thunar and actually renamed all my files with it. I was renaming them to Friendwedding1,2,3 and so on. I found it very simple and effective. As far coding goes, i normally use C but guess it's time to learn something new.


Glad it was able to help you out.

---

### Post by jack24 on 2009-05-26
I've tried a few of the renaming tools and the one I like best is KRename.  It's in the repositories.  The GUI is intuitive, it gives you a fair number of options and lets you undo any mistakes.   I use it for exactly what you want to do.

Another option is to install Gwenview with the built-in Gwenrenamer.  That works really well too.

By the way, I use Ubuntu, not Kubuntu -- it just seems like KDE has better renaming tools.  I also happen to like digiKam for organizing photos, mostly because it has nice built-in EXIF and IPTC tags.

Good luck,

jack

---

### Post by nickdbliss on 2009-05-27
hey thanks jack. I will check that out too.

---

### Post by nebileix on 2009-05-27
```

#!/bin/bash
#Rename mutiple files. Usage will be ./script_name "DIR_PATH" "NEW_NAME"

if [ ! $1 ] || [ ! $2 ] ; then
      echo "Please supply path of folder and new file name."
else
      if [[ $1 =  *\/ ]] ; then 
	      path="$1*"
      else
	      path="$1/*"
      fi
fi

newpath=${path%/*}
newname=$2
ext=".jpg"
counter=1

for files in $path
do
  rename="$newpath/$newname-$counter$ext"
  echo "Renaming $files to $rename"
  mv $files $rename
  ((counter++))
done

exit 0

```

Or u can try this script.

Save it to any name u like and make sure u can exec it. 

Example:

```
./rename_multi_file_script ~/Pictures MyPhoto
```

1 thing to take note. It rename all files in that folder.

---

### Post by nickdbliss on 2009-05-27
Thanks Nebileix. I appreciate u guys for helping me out.

Alright, now i have some other issue with renaming files. I had few files already existing in the folder. Then i added few others with different names. I selected them in Thunar and tried to rename them but it said some files were not renamed. The naming sequence with which u are trying to rename them already exists. Like pic001.jpg was already there. so it didnt rename the file havsomfan.jpg but started from pic002 and did the rest of the files. So havsonfan.jpg pic was left renamed. 

I would like to select all the files in the folder irrespective of their names and then rename them. It should ideally rename the file if it matches with the pattern as well making all in sequence. I know i could just set the numbering starting from 2 instead and it would not miss the file above. But imagine if there were 10-25 files and i added another 40 into the folder (forgetting to note the last file number), they all are going to mixed up and i wont be knowing what was the last number without lil trouble. Umm maybe i am expecting too much around here.lol. Thunar works but just thinking it can improve itself.

---

### Post by leandromartinez98 on 2009-05-27
You see, that's why learning a bit of scripting is so valuable. For instance, if you see my script above, you can simply change it to rename the files that match the pattern using

for file in `ls *.jpg | grep PATTERN` 

instead of the `ls *.jpg`. 

Of course you will feel not very confortable at first because of not knowing the syntax in details, that's why I say that you should always try the script with some copy of the files before actually using it. However, it is still worth trying this methodology. For instance, you may want, latter, to obtain smaller copies of all files. Then, you simply will add a line to your script using the "convert" command. Then, you may want send them by mail, and that you can also do in the same script. I mean, the possibilities are inumerous and, by using scripting, you can do all much more efficiently without having to discover a different program for each task. Of course there is a learning curve, but it really pays off, because the tool you will be learning is much more powerful and general than any of these specific programs. Considering that you have already some experience in C programming, you should not find learning bash scripting particularly complicated (and, for instance, all this can be done in Python, TCL, or other scripting language, if you prefer).

---

### Post by nebileix on 2009-05-27
Time to pick up some new language nick.

It's very easy to learn bash scripting if you know C previously. It took me a few days to pick up the basic and been scripting quite frequently to automate task of my own. Give it a try.

Check out this website and u will know the basic pretty fast.

[http://www.thing.dyndns.org/debian/bash.htm]("http://www.thing.dyndns.org/debian/bash.htm")

Have fun!!

---

### Post by kaibob on 2009-05-28
Everyone has their favorite way to rename photos, so I guess it's OK to mention mine. The exiv2 command-line utility extracts the exif data from digital photos and is more fully described as follows:

> exiv2  is a program to read and write Exif, IPTC and XMP image metadata
and image comments. Supported image formats are  JPEG,  Canon  CRW  and
Canon  THM.   Read-only support is currently available for PNG and TIFF
format and includes TIFF-based RAW formats: Adobe DNG, Canon CR2, Fuji&#8208;
film RAF, Minolta MRW, Nikon NEF, Olympus ORF, Pentax PEF, Sony ARW and
Sony SR2.

The exiv2 utility has a rename option, which I use as follows:

```
exiv2 rename -r "%m-%d-%y@%H:%M:%S" *.jpg
```

This command renames all jpg files in the current directory based on the date and time that the photo was taken. A sample renamed file would be:

> 09-23-08@16:30:28.jpg

You can add whatever identifying text you like. A somewhat wordy example of this is:

```
exiv2 rename -r "Arizona vacation on %m-%d-%y at %H:%M:%S" *.jpg
```

---

### Post by nikhilbhardwaj on 2009-05-28
excellent script kay-man

---

### Post by mister_p_1998 on 2009-05-28
Krename is nice & easy t ouse..
Steve

---

### Post by airtonix on 2009-05-28
Install zenity and wmctrl

```
sudo apt-get install zenity wmctrl
```

Save following text-block as file : 
*~/.gnome2/nautilus-scripts/rename-files*

```
#!/bin/bash
progressTitle="Rename Files: Progress"
if [ "0" == "$#" ] ; then
zenity --error --title="Copy files error" --text="Please select one or more files."
else
(    
    searchTitle="String to look for..."
    replaceTitle="Replace it with..."
    $(sleep .5 && wmctrl -a "$searchTitle")&
    lookfor=`zenity --entry --title="$searchTitle" --width=300`
    $(sleep .5 && wmctrl -a "$replaceTitle")&
    replacewith=`zenity --entry --title="$replaceTitle" --width=300`
    i=0
    for file in "$@"; do
        echo $(($i * 100 / $#)) 
        i=$(($i+1))

        new=`echo $file | sed "s/$lookfor/$replacewith/g"`
        mv "$file" "$new"
    done
    echo 100
) | zenity --auto-close --progress --auto-kill --title="$progressTitle" --width=400
exit 0
fi

```**Usage**
Select one or more files and select "*rename-files*" from the scripts sub menu in your context menu.

It will first ask you for the text to search for then it will ask you what you want to replace that text with.

---

### Post by nickdbliss on 2009-05-28
Thanks guys over there. Well its time to learn bash i guess. To be honest i kinda shy away from bash. No specific reasons just never feel like doing it you know some feeling u get sometimes lols. Anyways i am trying some of the scripts n they work pretty good so far. Saved them into files so that will work for now. hehe.

---

### Post by HeirPixel on 2009-05-28
pyRenamer is incredibly handy, especially for photo/video files with lots of extra characters you want to change/delete/number/etc. And unlike krename there's no need for KDE dependencies if you don't want them ;)

---

### Post by nebileix on 2009-05-29
Gd for u. You can edit my script to hold 3 argument for extension that u wan by editing the ext=".jpg" variable to "$3" in the script.

And u can use it like this:

```

./rename_multi_files [pathtofolder] [newname] [.extension]

```

Try it out to understand more on scipts.

---

### Post by jerrrys on 2009-08-29
:)

---

### Post by salguod on 2009-11-03
Hi,

I have been looking for a good GUI program which will rename my photo files the way I want to. Many rename multiple files, but not the style I like.

So, I've used the command line programs jhead and exiv2 to rename many jpg files at once, the way I want.

I personally like to name the files according to date and time.

First, install the programs (sudo apt-get install exiv2 jhead)

to batch rename with jhead, open terminal, then go to the folder with the images you want to rename. then type:
jhead -n%Y%m%d_%H%M%S *jpg

(that will rename all jpgs with the date and time: 20091102_122010.jpg will be the name for a photo taken at 12:20:21 on Nov. 2, 2009) 

You can create your own syle as well. 
The command:
jhead -n photo%03i *jpg 
should name all the jpgs as photo001.jpg, photo002.jpg and so on. (i think). 

to batch rename with exiv2, open terminal, go to the folder with the images you want to rename, then type:
exiv2 rename *jpg

(that will rename all jpgs with the date and time: 20091102_122010.jpf will be the name for a photo taken at 12:20:21 on Nov. 2, 2009)

I have not learned how to do custom names with exiv2 yet.

I am also trying to learn how to edit the captions on multiple photos (IPTC) with exiv2. It is apparently possible, but I keep getting errors. Anyone have Ideas on that?

---

### Post by anmys on 2009-11-03
In addition to the solutions offered so far, I would suggest you take a look at rename. It is a perl script and should be installed by default. Since it uses regex, files can be renamed quite easily.

I would also suggest to take a look at mmv. Of course, both the solutions are cli.

Regards.

---

### Post by Barriehie on 2009-11-03
I use this python script.  It's directory dependant but generates a 20 character random name.  Wouldn't take to much to use sequential #'s, padded with 0's on the left.  I was using Thunar but the lack of padding on the left didn't sequence correctly.  It could be coded more efficiently but it does work...

Barrie


```

#!/usr/bin/env python
#
#   Python 2.5.2
#

from os import *
from random import seed as rSeed, randint as rInt

filez = []
newfilename = ''
rSeed()

NameGenList = { 0:'0', 1:'1', 2:'2', 3:'3', 4:'4', 5:'5', 6:'6', 7:'7', 8:'8', 9:'9', 10:'A', 11:'a', 12:'B', 13:'b', 14:'C', 15:'c', 16:'D', 17:'d', 18:'E', 19:'e', 20:'F', 21:'f', 22:'G', 23:'g', 24:'H', 25:'h', 26:'I', 27:'i', 28:'J', 29:'j', 30:'K', 31:'k', 32:'L', 33:'l', 34:'M', 35:'m', 36:'N', 37:'n', 38:'O', 39:'o', 40:'P', 41:'p', 42:'Q', 43:'q', 44:'R', 45:'r', 46:'S', 47:'s', 48:'T', 49:'t', 50:'U', 51:'u', 52:'V', 53:'v', 54:'W', 55:'w', 56:'X', 57:'x', 58:'Y', 59:'y', 60:'Z', 61:'z' }

#preceeder = ''
#loop = 0
#while loop < 12:
#    NameGenListKey = rInt(0, 61)
#    preceeder = preceeder + NameGenList[NameGenListKey]
#    loop+=1
#print preceeder

listpath = '/home/barrie/Desktop/temp/pics'
for dirpath, dirnames, filenames in walk(listpath):
    nofiles = len(filenames)
    x = 0
    if dirpath == listpath:
        while x < nofiles:
            filez = filenames[(x)]
            if filez[-3:] == 'jpg':
                preceeder = ''
                loop = 0
                while loop < 20:
                    NameGenListKey = rInt(0, 61)
                    preceeder = preceeder + NameGenList[NameGenListKey]
                    loop+=1
                newfilename = preceeder + '.jpg'
                rename(filez, newfilename)
            x += 1

```

---

### Post by graphguru on 2009-11-04
Picasa for linux from google has quite a few batch operations including rename, and it's gui.

Graphguru

---

### Post by stinger30au on 2009-11-04
gnome commander is the go

fireup shell and copy/paste this

sudo apt-get install gnome-commander

then type in your password

you will find it under 

applications

accessories

---

