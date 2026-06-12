---
title: "How to: create background sets thet periodically change (like the space one)"
date: 2010-06-08
forum: Desktop Environments
---

### Post by theGiallo on 2010-06-08
Have you noticed the space "background set" that is in Ubuntu from the 9.04?

[IMG]http://img63.imageshack.us/img63/4632/spacebgset.png[/IMG]

It is an xml file (as I discovered on this beautiful forum :D).

But creating it manually is very boring and long, it would be simpler to put wallpapers into a directory and use them all as background set. So I've created a simple script that generate the xml background file with the images in a directory. You can set the time duration of wallpapers and of transitions setting the proper parameters.

here's the link to the script:
[generateXMLBackground.sh](http://digilander.libero.it/giallodue/development/ubuntuscripts/generateXMLBackground.sh)

**How to use it?**

[LIST]
[*]Create a directory and put into it all images you want to be in the background set
[*]Open a terminal [Applications-&gt;Accessories-&gt;Terminal]
[*]Type "cd " and drag into the terminal the directory previously created and press enter
[*]Drag into the terminal the script generateXMLBackground.sh and press enter [you can use parameters -t -d. For help use the parameter -h]
The xml file has been created!!
[*]Now you only have to set it as background:
in the "Change desktop background" window click "Add", navigate to the directory created at the beginning, set the type filtre to "All files" (at right bottom, normally it is 'Images') and choose the .xml file named #DIRNAME#Background.xml.
[/LIST]

**Note:**
*if you cannot run the script generateXMLBackground.sh you have not rights type into the terminal "chmod +x " drag the script and press enter (to make it executable).*

---

### Post by K.Mandla on 2010-06-10
Moved to Desktop Environments.

---

### Post by llawwehttam on 2010-06-10
[http://feedproxy.google.com/~r/d0od/~3/wsCHfLX_mNI/crebs-ultimate-wallpaper-slideshow.html](http://feedproxy.google.com/~r/d0od/~3/wsCHfLX_mNI/crebs-ultimate-wallpaper-slideshow.html)

---

### Post by JohnnyC35 on 2010-06-10
To switch desktop wallpapers I use Drapes. Give it a directory to get wallpapers from, tell it how to scale them and how many minutes to change it, and it just works :)

---

### Post by Tigerclawz on 2010-06-11
I was always too slack to do it myself, but given the convenience, I'll deffinately use this. Thanks a bunch. :)

---

### Post by pietjanjaap on 2010-06-11
Wallpaper Tray

---

### Post by gingivere0 on 2010-06-11
There's also gbackground that comes in the directories.  Just point it to the directory with your desired background and tell it how often it should change.

---

### Post by cptr13 on 2010-06-11
I second using "drapes" for this.  It's the simplest wallpaper changing program I've found under linux.  Install it from the repository, import your wallpapers and that's it.  Simple, easy and effective!

---

### Post by quirkification on 2010-06-11
I just got drapes... Yea that was simple.
If you wanted to have multiple sets of wallpapers though, you will need something else.

---

### Post by ffixcollector on 2010-06-11
I used to use drapes, but since I've upgraded to 10.04, it does not run on startup. Anyone have a fix for this?

---

### Post by gingivere0 on 2010-06-11
It sounds as simple as System>Preferences>Startup Applications.  Then look to see if drapes is on the list. If it is, check the little tick box and it'll be there on the next login/restart. If not click on new and add the command and name it.

---

### Post by JohnnyC35 on 2010-06-11
Go to this thread: [http://ubuntuforums.org/showthread.php?t=1486921&highlight=drapes](http://ubuntuforums.org/showthread.php?t=1486921&highlight=drapes)
... or actually I'll just paste from it...

From Wired99 (Post #2)
> 
 				 				**Re: Drapes Wallpaper management** 			
 			 			 		   		 		 		I found the  answer.

I added the following line to **~/.config/autostart/drapes.desktop** :

 	Code:
 	Type=Application 
saved the file and DONE!!

I found the answer in a bug report:
[https://bugs.launchpad.net/drapes/+bug/292051](https://bugs.launchpad.net/drapes/+bug/292051)

I hope this helps someone else as well.



---

### Post by theGiallo on 2010-06-12
hey I didn't see my thread because it was moved :D

> **llawwehttam said:**
> [http://feedproxy.google.com/~r/d0od/~3/wsCHfLX_mNI/crebs-ultimate-wallpaper-slideshow.html](http://feedproxy.google.com/~r/d0od/~3/wsCHfLX_mNI/crebs-ultimate-wallpaper-slideshow.html)

Hei! Yes that seems to be more useful and complete than my tiny tiny script! :D i didn't find it!


And for those who write to use other programs:
me too used that programs, but just because they are **other programs** they uses CPU and battery, so I prefer to use an already built in feature.

---

### Post by EvCrock on 2010-06-12
Whoa!  Desktop Drapes works great!!

not exactly great, it's a little buggy, but it gets the job done

---

### Post by ecksun on 2010-12-19
I liked this script. There were no package for crebs and I was to lazy to package it, so I used this instead, which didnt require installation.

However there are a couple of issues.

[LIST]
[*]Couldnt handle spaces in filenames
[*]Parameters were mixed up
[*]Off by one error, missed the first file
[/LIST]
Im including a patch that fixes all those issues, apply it with patch < generateXMLBackground.patch once you extracted it.

---

### Post by theGiallo on 2010-12-19
> **ecksun said:**
> I liked this script. There were no package for crebs and I was to lazy to package it, so I used this instead, which didnt require installation.

However there are a couple of issues.

[LIST]
[*]Couldnt handle spaces in filenames
[*]Parameters were mixed up
[*]Off by one error, missed the first file
[/LIST]
Im including a patch that fixes all those issues, apply it with patch < generateXMLBackground.patch once you extracted it.

oh, I didn't noticed those bugs...

thanks for fixing :D

---

