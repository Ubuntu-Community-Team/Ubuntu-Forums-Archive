---
title: "Windows Cursor under Ubuntu?"
date: 2007-07-09
forum: Desktop Effects &amp; Customization
---

### Post by sjc1963 on 2007-07-09
I just switched from Windows to Ubuntu Feisty Fawn 7.04 and I would like to know how to convert and install a pointer cursor from Windows. I've been using this pointer since Windows 3.11 and would like to continue to use it under Linux. So, could someone please help me to do this?

Here is a png of it.
[IMG]http://img.photobucket.com/albums/v399/sjc001/plugL.png[/IMG]

In case Photbucket goes down.

[http://rapidshare.com/files/41981076/plugL.png.html]("http://rapidshare.com/files/41981076/plugL.png.html")

---

### Post by prince_niceguy on 2007-07-09
install gcursors using synaptic.

now go to gnome-look.org and download the cursor theme which closly match the theme you have given or download the theme which you like :-)...

install the theme using gcursor. 

hope that helps.

---

### Post by chuckyp on 2007-07-09
How bout go to System > Preferences > Mouse and change the default pointer. 




Scratch that i'm not sure where to add pointers but the must be stored somewhere perhaps some locate action in the terminal to find them.

---

### Post by sjc1963 on 2007-07-09
Thanks for the suggestions, but neither is what I wanted to do. I alway tried gcursors, and the Mouse option only allows you to change to pointers that are already installed. There must be an easier way to install a custom pointer cursor? I've heard of xcursorgen but I can't find detailed instructions on how to use it exactly based on the image I have posted above. Maybe if someone would post the command line necessary to convert this png file I might get what I want in the end.

---

### Post by prince_niceguy on 2007-07-09
> **sjc1963 said:**
> Thanks for the suggestions, but neither is what I wanted to do. I alway tried gcursors, and the Mouse option only allows you to change to pointers that are already installed. There must be an easier way to install a custom pointer cursor? I've heard of xcursorgen but I can't find detailed instructions on how to use it exactly based on the image I have posted above. Maybe if someone would post the command line necessary to convert this png file I might get what I want in the end.

download the cursor you want. Open gcursors and drag the cursor file to the gcursors window and the new cursors would be installed and ready for use.

---

### Post by sjc1963 on 2007-07-09
I tried that already. It won't even load up. I get an error message.

Traceback (most recent call last):
  File "/usr/bin/gursormaker", line 23, in <module>
    import GursorMaker
ImportError: No module named GursorMaker

It did it as Root. Same error as regular user as well.

I installed it EXACTLY as they instructed to. It was version 0.6.0-2.

---

### Post by Matakoo on 2007-07-09
> **sjc1963 said:**
> 
I installed it EXACTLY as they instructed to. It was version 0.6.0-2.

Well, do like this:

Edit a textfile named cursor.txt and put this information in it:

32 1 1 plugL.png 0

Save the file. Make sure your png-file is in the same directory. Open a console in that directory and use this command:

xcursorgen cursor.txt left_ptr

Now you have a new file in the same directory, named left_ptr, that is an X-cursor file.
Find out which cursor theme you are currently using, using System > Preferences > Mouse. Say it's the one named redglass.

Cursors are saved under /usr/share/icons/name_of_theme/cursors
Save the original cursor like this (substitute redglass with whatever theme you are using):

cp /usr/share/icons/redglass/cursors/left_ptr  ~/cursor.bak

Copy your new one into place like so:

sudo cp left_ptr /usr/share/icons/redglass/cursors/left_ptr

Close all programs and logout (no reboot necessary). Login again and your new cursor should now be used instead of the original. Note that this is a rather quick and dirty approach but it should work.

---

### Post by sjc1963 on 2007-07-10
Now, that worked perfectly. Thank you very much for the help, Matakoo. \\:D/

---

### Post by Matakoo on 2007-07-10
> **sjc1963 said:**
> Now, that worked perfectly. Thank you very much for the help, Matakoo. \\:D/

Glad to be able to help :)

---

### Post by ELY_M on 2007-10-14
how can I import animated cursors?  

here is my fav cursor from windows. 
[http://www.bmx3r.com/103/ELYslightbulb.ani](http://www.bmx3r.com/103/ELYslightbulb.ani)
How can I use .ani file in ubuntu?

---

