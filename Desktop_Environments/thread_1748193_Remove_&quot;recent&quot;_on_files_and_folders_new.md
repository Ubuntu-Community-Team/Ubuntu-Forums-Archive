---
title: "Remove &quot;recent&quot; on files and folders new 11.04"
date: 2011-05-03
forum: Desktop Environments
---

### Post by aj_the_first on 2011-05-03
On the new 11.04 when you select files and folders, "recent" are displayed at the top, and I can't find any options to make "recent"  never appear.  I don't know who, on a personal and not work PC, would want their recently uploaded and opened documents and files displayed at a simple click.
Imagine this, I take dirty pics with the wife, I upload them to a secret folder, I use the same computer to show vacation pictures to my mom, I click on "files and folders", and poof, my mom sees naked pics of my wife displayed right across the "recent" files and folders section right at the top, regardless of the location of those files on the computer.
So to avoid these situations, I would like to know how to disable the "recent" section of files and folders quick pop-out display.

---

### Post by Melotten on 2011-05-04
here you should have a solution, didn't try it yet but I will do it soon:


[http://linux.aldeby.org/ubuntu-natty-11-04-unity-clear-recent-documents.html](http://linux.aldeby.org/ubuntu-natty-11-04-unity-clear-recent-documents.html)

---

### Post by aj_the_first on 2011-05-05
Activity Journal won't open a front end after installing it...

The command line worked, but only for recent and not for downloads.  I would like to remove them both.

Oh, and on the subject of the new ubuntu 11.04, I would like my weather and time bar back...  this one sucks, and the text is a dark gray just like my bar color, so I can't see it anyway.

---

### Post by Megaptera on 2011-05-05
Hi aj_the_first,
I can't offer a tech fix ... only a suggestion - until you get this sorted, don't show your mom those vacation pics!!:)

---

### Post by nash black on 2011-05-15
Hi,

This won't technically disable the downloads section, but it will cause that section to disappear. The downloads section doesn't monitor and save all of your downloads, it just displays the contents of that one, particular "downloads" folder. You can move downloads from that folder to another downloads folder in another location and change your browser settings to download files to that new folder. There will be nothing in the downloads folder that unity checks, so the downloads section will not show up. You can also just delete the original downloads folder, which will cause the downloads section to show the contents of your home folder (I did this because it is a convenient way for me to access all of my files).

To change your browsers' download location, first create a new folder that you would like to use for downloads and copy its directory to your clipboard. 

In chrome/ chromium: Click on the wrench > Preferences > Under the Hood, paste the directory into the "Download location:" box. Alternatively, you can check the box that will tell chrome to ask you where to download each file.

In Firefox: Edit > Preferences > General (tab), Click the browse button and find your desired downloads folder or again, check the box telling Firefox to always ask you where to download a file.

So go through all of your web browsers and do this, effectively rendering your initial downloads folder useless and causing the downloads section to never show up in your files browser. I've noticed that browsers don't always honor this directory, so also go through each browser and save a random image from a website to your new downloads folder. That way new files will get saved there if the browser defaults to the last save location. You may have to do this with each new file type depending on how annoying your browser is.

---

### Post by nash black on 2011-05-15
Also, the Activity Journal from the official repository doesnt seem to be working with 11.04, but the program does if you can get the .deb file somewhere else.

---

### Post by harvindercs on 2011-10-04
[http://www.webupd8.org/2011/05/keep-files-from-showing-up-in-unity.html](http://www.webupd8.org/2011/05/keep-files-from-showing-up-in-unity.html)

---

