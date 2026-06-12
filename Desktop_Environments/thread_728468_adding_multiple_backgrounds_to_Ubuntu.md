---
title: "adding multiple backgrounds to Ubuntu"
date: 2008-03-18
forum: Desktop Environments
---

### Post by bishounen on 2008-03-18
Hey all,

I have a new install of Gutsy I'm working with, and I've just transferred my collection of background images from my home server into the "/home/<uname>/Pictures" folder.  This is a large collection of desktop backgrounds sorted into multiple folders, and I'd like to easily add them to the "Background" tab of the "Appearance Preferences" app.  It appears that I can only select individual files via the GUI app.

Is there any command or tweak I can apply to simply add all the images in one go?  I have well over 3000 desktop images in this collection, so you can imagine I'd really rather not have to manually select and add each and every one.

Thanks in advance!

Bish.

---

### Post by Zimmer on 2008-03-18
The xml file that controls the list is in your home folder (hidden) 
/.gnome2/backgrounds.xml

I expect a script could be written to write out your file list and wrap the relevant xml text around the filenames to aceive the desired result...

---

### Post by bishounen on 2008-03-19
> **Zimmer said:**
> The xml file that controls the list is in your home folder (hidden) 
/.gnome2/backgrounds.xml

I expect a script could be written to write out your file list and wrap the relevant xml text around the filenames to aceive the desired result...

Great!

Anyone have a script like that?

Seriously.  I can't program my way out of a paper bag.

Anyone?

I'll also take suggestions for "replacement" options as far as software to simply replace the "backgrounds" function.

---

### Post by Zimmer on 2008-03-19
Unaccustomed as I am to script language I have made a quick attempt at using a spreadsheet (would you believe) to concatenate the text with the out put of a file listing.

I have to do other things at the moment, so I will have a go later, if possible, just for the fun of it..  I know it is possible, but am a bit rusty after 4 years of retirement and I WAS used to Excel, not Open Office ;)

I got so far, but got a few errors with the function arguments and handling of imported strings..... need a quieter time...
And, yes, I know the script would be the more elegant way.....if I knew more about scripting.. but I will learn more about the capabilities of OO..

---

### Post by AZzKikR on 2008-03-19
> **bishounen said:**
> Is there any command or tweak I can apply to simply add all the images in one go?  I have well over 3000 desktop images in this collection, so you can imagine I'd really rather not have to manually select and add each and every one.

Well, I didn't have anything to do this last hour or so, so I investigated a little bit of Python. Finally learned what the yield statement does thanks to this 'assignment' :D

Anyway, check out the attached file. Download it to your home directory /home/$USER. Run it as follows:
```

$ cd /home/$USER
$ chmod +x peepee.py
$ ./peepee.py "/home/$USER/pictures" # -- no trailing slash after 'pictures'

```

This will recurse through the pictures folder and write a "backgrounds.xml" file in the /home/$USER directory. Copy this file over the /home/$USER/.gnome2/backgrounds.xml file and the backgrounds *should* be there. 

Make a backup of your original backgrounds.xml though ;-)

---

### Post by bishounen on 2008-03-19
Well, that "sort of" worked.

The Python script worked wonderfully.  It generated the .xml file, and I was able to copy over the sections of the original XML and paste them into the generated one so that I would still have the default backgrounds.  However, when I went to overwrite the original backgrounds.xml with my new one, the system automatically deleted it and overwrote it with a fresh backgrounds.xml that only  included the stock backgrounds.

I tried it 3 times, with the same result each time.  For some reason, I can't overwrite the stock backgrounds.xml.  I'm going to try just copying the text from the new one first, and see how that goes.

-------------------------------------
Ok...

No luck.  Copying the text over from one file to another didn't work.  As soon as I closed the saved file the system reverted it.  I even tried logging in via failsafe terminal and running:

> cp backgrounds.xml /home/<uname>/.gnome2

That didn't work either.  For some reason the system keeps overwriting the file.  The only thing I can think is that it's a specially protected file to prevent someone "goatse"-ing people with a remote exploit.  Anyone have any idea how to get around this one?

---

### Post by AZzKikR on 2008-03-19
That's interesting. I had somewhat the same issue.

I tried to overwrite the backgrounds.xml on my RedHat 4 box, and it worked. However, the default backgrounds were added to the overwritten xml file:

- I ran the script, 2 backgrounds were added
- Copied over the existing xml file
- Tried to change the background; the two files were listed, in addition with the default 8 others.
- Closed the background changing window
- The file was written with my 2 backgrounds, plus the 8 others

Weird and all. I think a default backgrounds.xml exists somewhere else on the filesystem. Perhaps in /usr/share/... ? I'm gonna take a look soon.

---

### Post by Zimmer on 2008-03-19
My test is ok, although it contains the stock Ubuntu pictures, picked up from a file in usr/share..  it is not called backgrounds :)

The UI also hangs on to the current background, I think.  What did concern me was the first attempt I used a directory with many sub directories that had all sorts of files from .tiff to wma. and avi files and the Desktop background process failed to respond, either becuse of the filetypes or the volume of them .  (that UI produces titled thumbnails that perhaps reside in temporary memory...) So I chose another simpler folder with a few .jpg s  and that has worked, even a few reboots later.

try the gnome-background-properties folder for the other xml files
The UI must create the links from the shared .xml files and the user one to allow all users to have the stock pictures plus any they add in their /$HOME folder

---

### Post by Zimmer on 2008-03-19
> **bishounen said:**
> Well, that "sort of" worked.

The Python script worked wonderfully.  It generated the .xml file, and I was able to copy over the sections of the original XML and paste them into the generated one so that I would still have the default backgrounds.  However, when I went to overwrite the original backgrounds.xml with my new one, the system automatically deleted it and overwrote it with a fresh backgrounds.xml that only  included the stock backgrounds.




That didn't work either.  For some reason the system keeps overwriting the file.  The only thing I can think is that it's a specially protected file to prevent someone "goatse"-ing people with a remote exploit.  Anyone have any idea how to get around this one?

I just renamed my original backgrounds.xml to bbackgroundscopy.xml  and pasted the new file in its place.

---

### Post by Zimmer on 2008-03-19
Az'  Thanks for the script
any particular reason why you used the colour #dadab0b08282   in your code or was that just taken from your backgrounds.xml ?

Mine is set at #2c160a  and your number reverts to that in the xml file for each background that I select and keeps that value permanently in the file... 

Nice script BTW , I have decoded the gist of it, but with no real Python experience I cannot fully understand the best bits,  I can see the concatenation of the output filenames, but the os  and sys  parts are a mystery....

---

### Post by AZzKikR on 2008-03-20
Hi, glad the script worked :)

I used the color #dadab0b08282 because I think that was the default color described in existing backgrounds.xml files. You can edit the script and change the lines
```

fwriter.write("    <pcolor>#dadab0b08282</pcolor>\n")
fwriter.write("    <scolor>#dadab0b08282</scolor>\n")

```
to your own, I guess.

os.walk does the 'walking' through directories recursively.
sys.argv simply gets the script's arguments (i.e. , "/home/azzkikr/pictures") :D

---

