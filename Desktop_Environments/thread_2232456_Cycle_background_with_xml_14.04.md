---
title: "Cycle background with xml 14.04"
date: 2014-07-02
forum: Desktop Environments
---

### Post by Leon_Adams on 2014-07-02
Searched the threads but could not find specific help...

I have set up a folder with some images I would like to cycle through.  The xml file is ready, however when I go to choose the background image with the appearance gui only image files are shown and am unable to select the xml file that defines the slideshow.

So how to I use the xml file to show the slideshow?

Also, I have dual screen setup and would like the images to span both desktop.  Is there an option for this use case as well?

Thanks in advance 

Leon

---

### Post by Bucky Ball on 2014-07-02
Welcome. I'm using Xfce4, but right click on desktop>Desktop Settings>Background>Folder>Choose folder with your pics in>Tick 'Change the background' and set how often. Done.

I've never used an .xml file to change desktop wallpaper, which is what you're trying to do if I'm understanding correctly ...

---

### Post by grahammechanical on 2014-07-02
The default file is usr/share/backgrounds/contest/trusty.xml and the images are put in usr/share/backgrounds/

Where are your images? And what is the name of your xml file and where is it put? When I last did this I modified the existing xml file. I kept the file locations the same but I added different image names and I placed the new images in the same backgrounds folder. I of course made a backup copy and put it in a folder.

The only problem I found was with duplicate entries in Appearance because Gedit was making a backup of the xml file and putting a tilde ( ~ ) character in front of the file name which made the file a hidden file but Appearance was able to read both xml files and showed a duplicate.

And then there is usr/share/gnome-background-properties/trusty-wallpapers.xml which contains the instructions for loading static background images. I think it best to use the same files names and just change the image names but keep to the same locations. Or change the locations. The key I think is to use the same file names.

Regards.

---

### Post by Hypnoz on 2014-07-02
I use a program called Variety in the software center. It's really great, you point it to a folder and it handles all the work of rotating. You can also tell it to get images from some preset websites like NASA. I also enabled a checkbox that overlays a quote over the wallpaper and the quote changes with the wallpaper.

---

### Post by Leon_Adams on 2014-07-02
Thanks...

Originally I copied the file to my home directory and used pictures from my Pictures folder.  I edited the xml file to reflect the files in the new location.  Just thought there would have been some way to point to a new slideshow since I did not want to lose the trusty slideshow.  

Thanks for the response though...

Leon

---

### Post by Leon_Adams on 2014-07-02
Cropped files to resolution of dual monitor, then point variety to the folder.  Nice little program.  Thanks for the suggestion...

Leon

> **Hypnoz said:**
> I use a program called Variety in the software center. It's really great, you point it to a folder and it handles all the work of rotating. You can also tell it to get images from some preset websites like NASA. I also enabled a checkbox that overlays a quote over the wallpaper and the quote changes with the wallpaper.

---

