---
title: "How to manage wallpapers with Appearance"
date: 2012-06-23
forum: Desktop Environments
---

### Post by le_phoceen on 2012-06-23
Hello !

I just installed Precise Pangolin with the Unity deskop environment and I have some difficulty with the Unity-flavored Appearance utility to manage wallpapers.

In Appearance, the drop-down list lets me select Wallpapers or Pictures Folder (or Colors & Gradients as a matter of fact). But when I'm in Wallpapers or Picture Folder and I click the + button to add my wallpapers to the list, they are added but are not there anymore next time I launch Appearance. It seems that Pictures Folder keeps only images that are in the root of the ~/Pictures folder, and Wallpapers those images that are in /usr/share/backgrounds.

I would like to know how to keep in the Appearance menu those wallpapers that are in some customized location on my disk, which worked perfectly in gnome-panel.

Has someone an idea ?

---

### Post by Frogs Hair on 2012-06-23
Alt + F2 ```
gksudo nautilus
``` Move the images into usr/share/backgrounds and they will appear as the default wallpapers do. Add the images one by one . If you drag an entire folder to that location they wont appear.

---

### Post by le_phoceen on 2012-06-24
Hi,

thank you for the answer, but on my computer it does not work, even when I copy an image in /usr/share/backgrounds one at a time. Is there an additional constraint (size, type, ...) to satisfy for the image to be listed in the Wallpapers section of Appearance ?

By the way, and it is only my opinion, the Appearance utility has taken a step backward from what it was in gnome-panel. It is not very handy if you have to put your wallpapers only in the root of ~/Pictures for them to be listed in Appearance.

Of course I'm still able to use the wallpaper of my choice by right-cliking to the deskop and choose Change Desktop Background, but...

---

### Post by Frogs Hair on 2012-06-24
It isn't working for me on 12.04 either . I wrongly assumed it would because had added wallpapers to the folder on previous versions . I don't know if there is a size requirement but the default wallpapers are 1920x1280.  The change in appearance preferences is a Gnome 3 change not a Ubuntu change.

---

### Post by zombifier25 on 2012-06-24
I heard you must also add the wallpaper's entry into some .xml file. I'll look it up.
EDIT: Oh yes, it's /usr/share/gnome-background-properties/precise-wallpapers.xml. You must add an entry into that file if you want your wallpaper to show up in Appearance.

---

### Post by le_phoceen on 2012-06-25
Ok I find I understand. It is not about the location of the wallpapers, it is about what is referenced in the /usr/share/gnome-background-properties/precise-wallpapers.xml file. I think there is just a bug because this file was probably meant to be updated not manually but by the + and - buttons in the Appearance utility.

I'm going to test it tonight (European time).

---

### Post by le_phoceen on 2012-06-25
> **zombifier25 said:**
> 
EDIT: Oh yes, it's /usr/share/gnome-background-properties/precise-wallpapers.xml. You must add an entry into that file if you want your wallpaper to show up in Appearance.

Yes, I confirm it works. Your wallpapers display well in the Wallpapers section of Appearance if you manually edit this XML file instead of using the + and - buttons of the graphical interface.

Thank you all for your help !

---

### Post by AleveSicofante on 2012-06-28
Now that's inconvenient. (Why did they do that? What was wrong with just dropping the files on the right folder?) Is there any utility that will scan the directory with the backgrounds in it and add them to that XML file?

I want my backgrounds to be available system wide. I understand this is the right way to make it.

---

### Post by zombifier25 on 2012-06-28
> **AleveSicofante said:**
> Now that's inconvenient. (Why did they do that? What was wrong with just dropping the files on the right folder?) Is there any utility that will scan the directory with the backgrounds in it and add them to that XML file?

I want my backgrounds to be available system wide. I understand this is the right way to make it.

Blame the GNOME devs. They have been removing functionality as of late. Maybe someone can write such an utility.

---

### Post by Zetheroo on 2012-07-26
Come on, this is absolutely ridiculous! I have something like 80 wallpapers that I want to add to the Appearance selection and now I am supposed to manually edit a XML file and add a seperate section for each and every picture!? :confused:  Talk about just plain wrong!

---

### Post by Freecore on 2012-11-07
Actually, you don't have to add manually your 80 wallpapers. I wrote a  script to do that (I have a lot of wallpapers I wanted to add to the  appearance menu too :smile:).

This is the script:

```

#!/bin/bash

# Freecore

# This script creates an xml file that you can
# put on /usr/share/gnome-background-properties (if you want wallpapers entrys to ALL users, requires administrator rights)
# or in /home/userA/.local/share/gnome-background-properties (if you want it only for userA).

# Instructions
# (Realize that the script it's supposed to be runned like this: sh namescript FOLDER/OF/PICTURES/DIRECTION/).
# Don't forget the last "/".
# This script creates a file named my-wallpapers.xml.
# The file will have the xml code that Ubuntu (Gnome) identifies when it search for backgrounds.
# ATTENTION: The file generated will NOT include hidden folders NOR sub-folders pictures.
# ATTENTION: The file will include xml code for EACH file, so only put pictures in that folder.


xmlFile="my-wallpapers.xml"

echo '<?xml version="1.0" encoding="UTF-8"?>' >> "$xmlFile"
echo '<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">' >> "$xmlFile"
echo '<wallpapers>' >> "$xmlFile"

# For each file in the folder ingresed by the user, it wll create an xml entry.
for img in "$1"*; do

     # We'll declare a variable with the entire name of the image (extention  included). It will be used to declare the next variable.
    CompleteName="${img##*/}"

    # We'll declare a variable with the name without the extention. It will be the name in the appearance menu
    Name=$(echo "$CompleteName" | cut -d "." -f 1)


    echo "  <wallpaper>" >> "$xmlFile"
    echo "    <name>$Name</name>" >> "$xmlFile"
    echo "    <filename>$img</filename>" >> "$xmlFile"
    echo "    <options>zoom</options>" >> "$xmlFile"
    echo "    <pcolor>#000000</pcolor>" >> "$xmlFile"
    echo "    <scolor>#000000</scolor>" >> "$xmlFile"
    echo "    <shade_type>solid</shade_type>" >> "$xmlFile"
    echo "  </wallpaper>" >> "$xmlFile"

done

echo '</wallpapers>' >> "$xmlFile"


echo 
echo 
echo "The file has been created with the pictures in «$1»"
echo 

```

All you have to do is put it in a .sh text file and run it in a terminal with something like
```
sh your-file.sh your/pictures/folder/
``` be aware of the last "/". And it's done!

If  you want the wallpapers to be able only in your appearance menu you   can put the xml file in your local folder (./local/share...) as I  mentioned in the script.

You can manage to convert the script to a Slideshow creator too with some little changes.

I hope it'll help some people. :cool:

---

### Post by FormatSeize on 2012-11-07
Thanks, Freecore. I've been manually moving pictures over one-by-one on the command line, and I didn't even know about the xml file.

---

### Post by AleveSicofante on 2012-11-07
Nice script. Still unsuitable for ordinary users (read: no terminal allowed).

I know its Gnome's fault, but since Ubuntu is taking its own path more and more, I wish this would be considered a paper cut (does that program still exist?) and corrected.

Today I had to add a wallpapers folder to a Windows 7 laptop of a family member and it was as easy as browsing to it. Now it appears as one of the sources for wallpapers when selecting one. It's not rocket science...

Also, maybe the script can be made to run with upcoming versions of Cuttlefish (the developer promised some "folder watching" for events), so there's a way to set it and forget it.

---

