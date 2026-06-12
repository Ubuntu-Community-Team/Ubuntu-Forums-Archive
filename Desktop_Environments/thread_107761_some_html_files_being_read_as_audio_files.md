---
title: "some html files being read as audio files"
date: 2005-12-23
forum: Desktop Environments
---

### Post by randlieb on 2005-12-23
i have a number of folders with various web site design files in them. have had no problem opening them in firefox or one of the web authoring apps (nvu, screem).....until now. now a few, but not all, html files are being read as audio/mpeg files. i try to double click on them and the icon changes from the html icon to the audio icon and then i get this message:

[B]The filename "index.htm" indicates that this file is of type "HTML document". The contents of the file indicate that the file is of type "MP3 audio". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "MP3 audio", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. [/B]

these are all files that are clearly html files! the icon changes but the file extension remains 'html'.

i have right clicked on them to go to preferences and it shows MIME TYPE audio/mpeg. i back out of the folder and return and they are html icons again.

anybody see anything like this???

how can i make sure all my html files can be read properly?

---

### Post by randlieb on 2006-01-01
[QUOTE=randlieb]i have a number of folders with various web site design files in them. have had no problem opening them in firefox or one of the web authoring apps (nvu, screem).....until now. now a few, but not all, html files are being read as audio/mpeg files. i try to double click on them and the icon changes from the html icon to the audio icon and then i get this message:

[B]The filename "index.htm" indicates that this file is of type "HTML document". The contents of the file indicate that the file is of type "MP3 audio". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "MP3 audio", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. [/B]

these are all files that are clearly html files! the icon changes but the file extension remains 'html'.

i have right clicked on them to go to preferences and it shows MIME TYPE audio/mpeg. i back out of the folder and return and they are html icons again.

anybody see anything like this???

how can i make sure all my html files can be read properly?[/QUOTE]

HELP!!!!

anybody seen this problem before???

i have about a dozen web site folders with hundreds of files, but only about 20 or so files are messed up (i just noticed some php files are this way too). and only in 4 of the folders. all the rest are fine!

---

### Post by sethmahoney on 2006-01-01
[QUOTE=randlieb]HELP!!!!

anybody seen this problem before???

i have about a dozen web site folders with hundreds of files, but only about 20 or so files are messed up (i just noticed some php files are this way too). and only in 4 of the folders. all the rest are fine![/QUOTE]

I've seen the problem with other types of files - video files being seen as text files, for example, but, unfortunately, I don't have a fix for you.  You might try (though I have no idea if this will work) opening the file from the terminal.

---

### Post by kaamos on 2006-01-01
Thats strange. I think this should be able to fix it: Open a terminal and
```
gedit ~/.local/share/mime/packages/Override.xml
```
and insert
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">

<mime-type type="text/x-extension-html">
<comment>Html document</comment>
<glob pattern="*.htm"/>
</mime-type>

<mime-type type="text/x-extension-html">
<comment>Html document</comment>
<glob pattern="*.html"/>
</mime-type>

</mime-info> 
```
Then do
```
update-mime-database ~/.local/share/mime
```
Hope it works. But this is bad solution, because it doesn't fix the problem why nautilus thinks some files are audio. This just overrides that.

---

### Post by randlieb on 2006-01-01
do i keep:

<mime-type type="application/x-extension-lnk"><comment>lnk document</comment><glob pattern="*.lnk"/></mime-type>
</mime-info>

....and just add your code?

---

### Post by hentaidan on 2006-01-01
Try right clicking on the files and going "Open with other application"

I have this problem with HTML/PHP files, where (I'm guessing here) Ubuntu gets conflicting information from the file extension (HTML) and finds <?php at the beginning of the file. And likewise if the extension is .php, and no <?php is found at the beginning of the file.

As to why they are appearing as mp3s.... odd.

---

### Post by kaamos on 2006-01-01
Make it looks like this:
```

<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">

<mime-type type="text/x-extension-html">
<comment>Html document</comment>
<glob pattern="*.htm"/>
</mime-type>

<mime-type type="text/x-extension-html">
<comment>Html document</comment>
<glob pattern="*.html"/>
</mime-type>

<mime-type type="application/x-extension-lnk">
<comment>lnk document</comment>
<glob pattern="*.lnk"/>
</mime-type>

</mime-info>
```

---

### Post by randlieb on 2006-01-01
the xml script didn't work (unless i have to reboot?)

this is a screenshot of one folder contents. you can see the icons with the music icon and the html extension. those are (were!) all html files. they changed to the music icon when i click on them (right or left). you can see it misreads a pdf file as well (and a php file in one other folder)!!!!

[ATTACH]5021[/ATTACH]

if i right click and 'open with' either firefox or an html editor i get the following goobledygook, about 60 lines worth.....!

1ÊË>o±êš¢}µ*ëw•$WcìŒî‘q+—{Ã³äšûË+¾ÖÞ &• y‡ÿýµ·U)Jà¤G_I÷Š”t¬sP½ã#E*Z!22f`È 6ŒaE

---

### Post by kaamos on 2006-01-01
No need to reboot, the update-mime-database should have done it. I probably just didn't get the syntax right.

If "open with" does not work, then this is not an issue with the mimetypes, but the files itself could be corrupt. :(

---

### Post by randlieb on 2006-01-01
any way to recover corrupt files or have i just lost those files for good?

---

