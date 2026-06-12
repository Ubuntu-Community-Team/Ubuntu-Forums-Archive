---
title: "Wine Winetricks Cabextract &amp; AutoCAD for Noobs"
date: 2009-04-29
forum: General Help
---

### Post by interestinfellow on 2009-04-29
I am a noob so, to all you salted users of Linux, correct me if I'm wrong.  There that's out of the way.

My only problem with Linux is the lack of AutoCAD, or a decent GNU version; but alas! I just installed ACAD2k on my Ubuntu Hardy PC.  How you ask? I'm glad you did. let me explain.

After a little research, I found out that I don't have the time, or patience to learn the GNU CADs out there, that don't really fit my needs.  SO I looked around on how to install Acad using a program called Wine.  For those of you who don't know, Wine lets you run windows programs in Linux.

Basically, Wine puts the missing pieces of windows in place, so a program can run on it's own in Linux, and the emulators (the other kind) run a full blown MS Windows OS inside of Linux, and then run your program of choice inside that virtual OS.
I have not tried the second method, as it is my impression that it is slower, because it is doing more at one time.

In any case, for anyone looking to install AutoCAD 2k on Ubuntu 8.1 Hardy, here is how I did it.  For anyone else reading this post, I hope it helps you in whatever it is that your doing; unless it's evil, then I hope you fail miserably:twisted:

The quick and dirty, ignore this if you don't really knonw what you're doing.
[LIST=1]
[*]Make sure you have Wine installed.
[*]Copy and save the text on [_this page_]("http://winezeug.googlecode.com/svn/trunk/winetricks") as winetricks.txt in /home
[*][INDENT]chmod u+x ~/winetricks.txt
sudo apt-get update
sudo apt-get install cabextract
~/winetricks.txt 
[/INDENT]
[*]select the following components<p>
[INDENT][LIST]
[*]comctl32
[*]comctl32.ocx 
[*]corefonts 
[*]dcom98 
[*]fm20 
[*]gecko 
[*]mdac25 
[*]mfc42  
[*]riched20 
[*]tahoma 
[*]vb3run 
[*]vcrun6 
[*]wsh56 
[*]win2k
[/LIST][/INDENT]
[*]Wait to see "MS Scripting Host 5.6" is installed
[*][INDENT]wine SETUP.EXE[/INDENT]
[/LIST]


Now, if you don't know what all that was, then keep reading and follow these instructions.

[LIST=1]
[*]Go to Add/Remove, and make sure you have Wine installed.



[*] Go [_HERE_]("http://winezeug.googlecode.com/svn/trunk/winetricks"), copy all the text into a text document, and save it in your home folder as winetricks.txt



[*]Turn that text file into a program.
Open a terminal (equivalent of a DOS box) (check out [_THIS THREAD_]("https://help.ubuntu.com/community/UsingTheTerminal") if you are unfamiliar with how to use terminal.
Also, know that Linux is case sensitive, so winetricks.txt Winetricks.txt WINETRICKS.txt and WINETRICKS.TXT are 4 different names.. 

Type
[INDENT]chmod u+x ~/winetricks.txt[/INDENT]



[*]Install cabextract
      
Type
          [INDENT]sudo apt-get update

          sudo apt-get install cabextract
[/INDENT]
Just wait for terminal to display the "user@computer-name" before proceeding.



[*]Launch Winetricks by typing

         [INDENT]~/winetricks.txt 
[/INDENT]




[*]Go through the box that pops up, and select the following components<p>
[INDENT][LIST]
[*]comctl32
[*]comctl32.ocx 
[*]corefonts 
[*]dcom98 
[*]fm20 
[*]gecko 
[*]mdac25 
[*]mfc42  
[*]riched20 
[*]tahoma 
[*]vb3run 
[*]vcrun6 
[*]wsh56 
[*]win2k
[/LIST][/INDENT]



[*]Now be patient, wait, and keep clicking "yes" "I agree" and "ok"
After you see that the "MS Scripting Host 5.6" is installed, count to 60, and go back to terminal (if you closed terminal before, just open a new one, it's OK)



[*]Navigate to the location of the install file for AutoCAD and type the installer name (mine was SETUP.EXE; see above about case sensitivity)
[INDENT][LIST]
[*]wine SETUP.EXE
[/LIST][/INDENT]
[/LIST]

I have not tested AutoCAD 2k extensively, I only verified that it would run and open documents,  I was so excited to have done it, I wanted to post it for any other noobies who don't know what they are doing, and need the info I found (giving back, that sort of thing).

Good luck!


EDIT: There is a known problem with undocked toolbars in ACAD2k not displaying or docking, no fix AFAIK.


I got my info from the following pages
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=102&iTestingId=26162](http://appdb.winehq.org/objectManager.php?sClass=version&iId=102&iTestingId=26162)
[http://wiki.jswindle.com/index.php/Winetricks](http://wiki.jswindle.com/index.php/Winetricks)
[http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)

---

### Post by ruelle on 2009-05-08
In of a couple of months a specific Wine version for autocad will be realised.
link to original wine forum
[http://forum.winehq.org/viewtopic.php?p=24033#24033]("http://forum.winehq.org/viewtopic.php?p=24033#24033")

what do you think about?

If you are a programmer you can also help to fix Autocad Wine bugs and make this wine version available soon!!
[URL="http://bugs.winehq.org/buglist.cgi?quicksearch=autocad"]
http://bugs.winehq.org/buglist.cgi?quicksearch=autocad[/URL]

---

### Post by mb125 on 2009-05-10
[QUOTE=ruelle;7242165]In of a couple of months a specific Wine version for autocad will be realised.

That is awsome, i wont have a need for X-peeee anymore

---

### Post by interestinfellow on 2009-05-11
Cool. Thanks

---

