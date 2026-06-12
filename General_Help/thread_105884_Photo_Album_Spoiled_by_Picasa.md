---
title: "Photo Album?? Spoiled by Picasa"
date: 2005-12-19
forum: General Help
---

### Post by shane2peru on 2005-12-19
Ok, I'm in need of a nice Photo Album Program that can:  1.  Burn to CD's, 2.  Print Photos (4x6, 5x7, 8x10, wallet, 4x6 borderless), 3.  Organize my photos.  I have 3 GB of photos on another partition.  I want to keep them there.  I tried F-Spot and it tried to bring all my photos to /home/*username*  I don't want them there, I ran out of space and had to find them and delete them all because I don't have enough room!  I have been spoiled by Picasa on Windows, and really like its capabilities.  Any suggestions?  Ok, I could do without the Burning Photos to CD - that is extra, but I would really like the Print capability.  Thanks.

Shane

PS I'm currently using Gnome and I'm using the digikam Photo album, greatly lacks printing.

---

### Post by earobinson on 2005-12-19
picasa works under wine
[http://www.ubuntuforums.org/showthread.php?t=28612&highlight=Picasa+wine](http://www.ubuntuforums.org/showthread.php?t=28612&highlight=Picasa+wine)

---

### Post by yanik on 2005-12-19
how about gthumb?

---

### Post by shane2peru on 2005-12-19
Wow, I'm picasa-ing!  What is gthumb?  I would really prefer a Gnome native if it works well.  I will run picasa with Wine till I find something worth while.  Wine is a resource hog, and runs much like windows.  - I guess that is what it is suppose to do, but then again, that is a reason I want freed from windows.

Shane

---

### Post by yanik on 2005-12-19
[QUOTE=shane2peru]What is gthumb?[/QUOTE]

You asked for a photo album program earlier, remember?

---

### Post by shane2peru on 2005-12-19
Rigth, I didn't mean what is it.  I guess I meant what all does it do.  I do have it installed, and was just going to comment that it is pretty nice too.  I was impressed with its Print ability.  It is much nicer than digikam.  It allows you to put more than one picture on a page, lay it out how you want.  That was what I was looking for.  I give gthumb a =D> .  It's not as user friendly, but not a bad program!  Thanks Yanik.

Shane

---

### Post by earobinson on 2005-12-19
I googled (gthumb) and found this [http://gthumb.sourceforge.net/](http://gthumb.sourceforge.net/)

---

### Post by JELaVallee on 2005-12-19
[QUOTE=shane2peru]Ok, I'm in need of a nice Photo Album Program that can:  
...
PS I'm currently using Gnome and I'm using the digikam Photo album, greatly lacks printing.[/QUOTE]

I've been using F-Spot (here: [http://www.gnome.org/projects/f-spot/](http://www.gnome.org/projects/f-spot/)) for some time now and find it to be very handy for this sort of thing.  I actually like it more than using iPhoto on my wife's Powerbook.

It has an excellent timeline based organization system that allows you to use tagging for managing your photos (e.g. I have tags for people, places, events, and categories... I can apply one-or-many of these tags to a given photo or set of photos and then can filter on a tag).  

I've been able to print fine from this to my directly connected Epson Stylus Photo R300 printer for making 2x3, 4x6, and 5x7 prints.  It also has exporter plugins for producing photo-CD's, very simple web gallery output, and a Flickr uploader (which I love).  Oh yeah, and it's GTK-Mono based which is just a nice thing to see.

I've also successfully installed ShutterFly's Linux Smart Upload Manager... it's really only good for what it's supposed to do and even then I find it very finicky about network config/issues.  And of course their replacement software doesn't run in anything but IE... sigh...

Enjoy!,
Cheers,
Etienne

---

### Post by shane2peru on 2005-12-19
JELaVallee,

    I did like the F-Spot package, and I especially liked the system of organization that it used since that is the same way that I organize my files (by date).  However there must be a way to overcome the issue with it importing all the 3.5GB worth of pictures to my 2.5GB /home/*username* directory.  I have all my pictures on a separate partition for access with windows and Ubuntu.  Is there any way to overcome this?  I want to leave the pictures where they are and organize them or catagorize them, print them, etc from that location.  Thanks for the post.

Shane

---

### Post by JELaVallee on 2005-12-19
[QUOTE=shane2peru]JELaVallee,

    I did like the F-Spot package, and I especially liked the system of organization that it used since that is the same way that I organize my files (by date).  However there must be a way to overcome the issue with it importing all the 3.5GB worth of pictures to my 2.5GB /home/*username* directory.[/QUOTE]

shane2peru,

Not sure on this one... I'm using F-Spot against a photo directory within my /home/username directory and as a result have not seen it doing an import replication of the files.  That is during import it only appears to index/catalog the images and their locations and doesn't actually copy them into the /home/username space...

Will have to experiment with importing from a share to see if I can get a different behavior.

When you did an import with F-Spot from your 3.5GB shared partition/mount-point, where exactly did you see the images being imported/replicated?

cheers,
Etienne

---

### Post by shane2peru on 2005-12-19
It puts them into /home/*username*/Photos  I had to delete them all again.  I use the import folder to get to see them in f-Spot.  If I don't import them I can't see them.  Is there another way?

Shane

---

### Post by macgyver2 on 2005-12-19
[QUOTE=shane2peru]It puts them into /home/*username*/Photos  I had to delete them all again.  I use the import folder to get to see them in f-Spot.  If I don't import them I can't see them.  Is there another way?[/QUOTE]
With the disclaimer that I haven't tested this, what about if you just make a link from the photo folder on your shared partition to ~/Photos?  Or, if the shared partition *only* holds photos just mount the partition on ~/Photos...  Like I said, I haven't tested it; my photos are already on my /home partition.

---

### Post by shane2peru on 2005-12-19
It was a good idea.  I tried to make a link, but it wouldn't let me.  I really can't change my mount points because there is more than just my Pictures on the partition.  I have a 10 GB fat 32 partition to share work files with my XP side.  3.5 GB is pictures on that partition.  It said ```
 Error "Operation not permitted" while creating a link to "/media/doc/My Pictures".  Would you like to continue?  Cancel Retry 
```  either choice fails.  Still open to suggestions.  

Shane

---

### Post by macgyver2 on 2005-12-19
[QUOTE=shane2peru]I really can't change my mount points because there is more than just my Pictures on the partition.[/QUOTE]
There's another mounting possibility, then.  If you use the --bind option you can mount a directory tree to another place.  On the commandline it would be
```
mount --bind /media/doc/My\ Pictures /home/<username>/Photos
```
or you can put it in your /etc/fstab anywhere after the entry for the original partition itself:
```
<...>
/media/doc/My\ Pictures    /home/<username>/Photos    none    bind    0    0
<...>
```

---

### Post by megamania on 2005-12-20
[QUOTE=earobinson]I googled (gthumb) and found this [http://gthumb.sourceforge.net/](http://gthumb.sourceforge.net/)[/QUOTE]

Right, Earobinson.

I underestimated gThumb for a long while, until a few weeks ago I found that website, which lists a lot of features "hidden" in the program.

At the moment I only use gThumb. It's not perfect, but it's light and nice, and it reminds me of Acdsee 4.0 or 5.0...

---

### Post by Mr. Electric Wizard on 2005-12-20
I know this thread has moved from Picassa, but I just loaded it with Wine last night and I like what I see so far...

---

### Post by shane2peru on 2005-12-20
I think I'm going to stick to gthumb too, unless I can work through all this stuff on F-Spot.  Even then I haven't tried F-Spot to see if it will print the way that I want it.  I do like gthumb's printing and cataloging too, it seems easy to use.  Thanks.

Shane

---

### Post by JELaVallee on 2005-12-20
[QUOTE=macgyver2]There's another mounting possibility, then.  If you use the --bind option you can mount a directory tree to another place...[/QUOTE]

shane2peru,

Have you had the chance to try this with your FAT32 partition?

I had not reallized that F-spot used the ~/Photos directory as it's repository as that's the directory I had already created to store my photos in *prior to* importing them into F-spot. 

Let us know if that mount binding method works for you.  I'm very interested in having a similar setup to what you discribed on my home workstation and this would be a valuable option to have.

cheers,
Etienne

---

### Post by shane2peru on 2005-12-20
I will let you know when I get a chance.  We are getting ready to travel, so I will be offline for about a week or so.  I will save the page and instructions so I can try it later.  Gotta run!  Thanks for the info, and I will give it a try!

Shane

---

### Post by shane2peru on 2005-12-20
[QUOTE=macgyver2]There's another mounting possibility, then.  If you use the --bind option you can mount a directory tree to another place.  On the commandline it would be
```
mount --bind /media/doc/My\ Pictures /home/<username>/Photos
```[/QUOTE]
I tried this command, but when I opened F-Spot it didn't see the pictures.  I don't know why.  It was really wierd, there were some pictures from before from my import, but not all the pictures.  I had deleted the file, but it still "seemed" to see them.  I even emptied the trash since I had NO room left on my /home partition.  I can't seem to unmount this command without rebooting the computer.  This is too complex for me.  I like the simple and working things.  I think I will stick to gthumb, until F-Spot can fix their space wasting problem.  I stay away from programs that do the same on MS too, that was the nice thing about Picasa, it left the pictures where they were.  Thanks for the help!

Shane

---

### Post by rasmusbp on 2006-01-05
I'm also (still) very interested in getting F-spot to work without having to move my files to the home/user directory. Please come forward if anyone has other ideas than the ones already tested here...

Cheers

---

### Post by landotter on 2006-01-05
I find gThumb to be much easier to use than Picasa, and I prefer using an external editor like the Gimp for photo tweaking. The exported web albums are simple and elegant.

That said, I think photo printing and printing under Gnome in general to be pretty lousy compared to KDE. :/

I've even run kprint within Gnome in the past to get all the functionality out of my printer.

Anybody know if the Gnome people are going to take the printing support out of the stone age?

---

### Post by pkoufalas on 2006-01-15
[QUOTE=landotter]I find gThumb to be much easier to use than Picasa, and I prefer using an external editor like the Gimp for photo tweaking. The exported web albums are simple and elegant.

That said, I think photo printing and printing under Gnome in general to be pretty lousy compared to KDE. :/

I've even run kprint within Gnome in the past to get all the functionality out of my printer.

Anybody know if the Gnome people are going to take the printing support out of the stone age?[/QUOTE]
I found this while searching for some info on how to layout and print photos with f-spot and gnome-photo-printer:

[http://mail.gnome.org/archives/usability/2005-December/](http://mail.gnome.org/archives/usability/2005-December/)
msg00122.html

I ran into the same problems with f-spot and gnome-photo-printer as the guys whose post is commented on in the above. I hadn't really tried gthumb so I'll give it a go.

---

### Post by pkoufalas on 2006-01-15
When I tried f-spot, I had a folder called ~/photo containing my photos. I used the import option and navigated until I selected that folder. My experience is identical to Etienne's, i.e. no replication.

Until yesterday, when I tried to import a new subfolder under photos. I clicked on import and then rather than on folder (or browse or whatever the button is called) I clicked on a drive icon, intending to browse to it. Unfortunately f-spot started to search and copy every single image on my hard drive, including from my mounted windows partition. Thankfully I could kill it. I did notice it had created a ~/Photo folder. 

Hope this helps.

---

### Post by irish rebel on 2006-01-18
picassa works under wine yes but will not create a cd I have tried on 4 distros digikam will not under any conditions for me create a vcd or dvd.I magine if we could get 3 or 4 projects to combine together to come up with a suite just like ILIFE imagine drag and drop photo and video adding music ect ect

---

