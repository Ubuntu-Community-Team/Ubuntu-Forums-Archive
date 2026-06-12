---
title: "Clueless newb question regarding USB drives"
date: 2009-04-23
forum: General Help
---

### Post by Cheffrey on 2009-04-23
Hello, 

First time linux user and i just got kubuntu 8.10 up and seemingly running fine. My specific question is as follows: Linux recognizes my USB drives but its not exactly obvious to me how to copy all the contents of my USB drive to anywhere in my file/folder structure of this linux box. 

If i drill down into a folder and choose an individual .pdf for example, that has file --> save as options but that is just not practical considering i have hundreds and hundreds of folders and files i want to transfer to this machine. 

Sorry for what is probably a ridiculous question but googling and searching through Dolphin hasnt shown me the way so i very much appreciate any and all assistance. 

Thanks!

---

### Post by LowSky on 2009-04-23
copy any files/folders you like you your /home folder, any other place will need root acces, which would be a no no!

---

### Post by Cheffrey on 2009-04-23
> **LowSky said:**
> copy any files/folders you like you your /home folder, any other place will need root acces, which would be a no no!

First off, thank you for the response and secondly im afraid i am not quite sure how to accomplish what you suggest. I am familiar w/copying from one folder/location to another in *nix but i cannot seem to find my way in the terminal to the location of my usb drive in order to copy its contents to a folder under my /home directory.

---

### Post by JediJazz on 2009-04-23
I am not quite sure this will help but can you copy using the -R command so 
If it was me I would create a folder in my Home Directory 

mkdir /home/jedijazz/OldComputerFiles

Then I would Copy from my usb stick which should be mounted somewhere

cp -R /media/usbstick/FOLDERCONTAININGALLFILES /home/jedijazz/OldComputerFiles

I am sure one of the experts will be able to help better than I can but i hope it puts u on the right track.

the -R command is a recursive command so it copies the contents of your folders which may be other folders and files into the specified location.

Cheers

JediJazz

---

### Post by dabl on 2009-04-23
If you're looking for a graphical approach, open Dolphin, split the window, and use one side to browse to the external hard drive folder where the source files are located, and use the other side to browse to the folder where you want the copied files.

Once the windows are so arranged, highlight all the files that you want to copy, then drag them to the other window, and drop. A menu will pop up asking what you want to do.  Choose "Copy" to copy, "Move" to move, etc.

---

### Post by Cheffrey on 2009-04-23
> **JediJazz said:**
> 
mkdir /home/jedijazz/OldComputerFiles

Then I would Copy from my usb stick which should be mounted somewhere

cp -R /media/usbstick/FOLDERCONTAININGALLFILES /home/jedijazz/OldComputerFiles


Thanks Jedi! That is exactly what i needed - i want to learn to use the command line. I didnt know where to find my usb drive in the file structure but /media was right on the money. I initially forgot to use the -R flag but i noticed it soon enough and now i have 14GB worth of data copied over to my new linux box. I very much appreciate the help. 

Dabl - your suggestion seemed like it would work for me as well, so thanks for the idea, but when i tried to copy over the files i got a "access denied" error and no dialogue box opened up asking for my password.. When i copied the folders over via terminal i had to use sudo and then put in my password so i am assuming i couldnt use dolphin due to something like that. 

Now i can get back to studying. :) Thanks again.

-Cheffrey

---

### Post by JediJazz on 2009-04-23
No problem at all :) Cheers for the feedback

---

