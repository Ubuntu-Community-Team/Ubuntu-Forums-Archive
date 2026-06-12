---
title: "Music File Tags"
date: 2005-02-20
forum: Desktop Environments
---

### Post by animalstyle on 2005-02-20
Im having some trouble with my music file tags.  I am organizing the album Zoso, by Led Zeppelin.  Now the songs were obtained *ahem* semi-legally, therefore they are all from random sources.  So naturally, to make them all fit, I used 'easy tag' to give them uniform file names in the form of <track #> - <song title> and also updated all of the tag information including track number, title, artist, and album.  Now Im trying to get them onto my ipod using gtkpod, and it does work, to the point of actually getting them on the ipod.  However, both gtkpod and my ipod will display them as all part of the Zoso album, but in a seemingly completeley random order.  They are also displayed with one word titles.  For example, "Stairway to Heaven"'s title is simply "Heaven", "Misty Mountain Hop" is just "Hop".  So whats up?  Is there some hidden tag that easy tag doesnt cover or what?  Obviously gtkpod is getting information from somewhere, and its not the information easy tag is supposed to be modifying.

P.S.  Rhythm box *does* display the information correctly, this is soley a gtkpod/ipod issue

---

### Post by kassetra on 2005-02-20
I'm looking into this... 
 
 Some things I'm thinking:
 What are the actual file names (not id3tags)?
 What character set did you use to rename the id3tags?
 
 also, I'm looking into which version of id3tags gtkpod uses.

---

### Post by animalstyle on 2005-02-20
the file names are <track #> - <song name>, placed in the album directory, which is then placed in the artist directory.  I used this because this is the default setting for the CD ripper.  Im not sure what you mean by character set, Im using whatever easy tag uses by default i guess.

---

### Post by kassetra on 2005-02-20
When you use rhythmbox to load your ipod, does it show the correct names?
 
 character set: is you computer language set up for english or another language?

---

### Post by piedamaro on 2005-02-20
You can set the encoding in the preferenecs of easytag. It should default to ISO-8859-1.

---

### Post by animalstyle on 2005-02-20
Im using english....and when i use rhythmbox to load my iPod tunes it does display them correctly...strange because the iPod Does not...

---

### Post by kassetra on 2005-02-20
[QUOTE=animalstyle]Im using english....and when i use rhythmbox to load my iPod tunes it does display them correctly...strange because the iPod Does not...[/QUOTE]
 
 Ok, so even though rhythmbox shows the song names correctly, when you load the files from rhythmbox to your ipod, the ipod does not show the names correctly?
 
 Is that correct?

---

### Post by animalstyle on 2005-02-20
The ipod by itself, when im playing songs from it does not display them correctly - the songs are shortened to single words and they are completely out of order, and the same goes for when I load my ipod up with GTKpod.  When using the ipod through rhythmbox it *does* display them correctly, in order, with full song names.  So basically the ipod is interpereting something differently.

---

### Post by kassetra on 2005-02-20
[QUOTE=animalstyle]The ipod by itself, when im playing songs from it does not display them correctly - the songs are shortened to single words and they are completely out of order. When using the ipod through rhythmbox it *does* play them correctly, in order, with full song names. So basically the ipod is interpereting something differently.[/QUOTE]
 
 Are you  transferring your songs to the ipod with a playlist, by any chance?

---

### Post by animalstyle on 2005-02-20
Hmm thats interesting...because I do have a zoso playlist on Rhythbox....that may be the culprit, but im not sure because i dont know how that would affect the ipod in any way. Im gonna check into it.

P.S. Its not a play list on the iPod itself; its just a play list inside rhythmbox, on my computer

---

### Post by kassetra on 2005-02-20
[QUOTE=animalstyle]Hmm thats interesting...because I do have a zoso playlist on Rhythbox....that may be the culprit, but im not sure because i dont know how that would affect the ipod in any way. Im gonna check into it.
 
 P.S. Its not a play list on the iPod itself; its just a play list inside rhythmbox, on my computer[/QUOTE]
 
 If what I understand about the ipod is correct, it handles the names from the playlist....

---

### Post by mattack on 2005-02-20
[QUOTE=kassetra]When you use rhythmbox to load your ipod, does it show the correct names?[/QUOTE]

How can I get this to work? I don't see any option to load my iPod with rhythmbox...

---

### Post by kassetra on 2005-02-20
[QUOTE=mattack]How can I get this to work? I don't see any option to load my iPod with rhythmbox...[/QUOTE]
 
 Is your ipod mounted under linux?

---

### Post by animalstyle on 2005-02-20
[QUOTE=kassetra]If what I understand about the ipod is correct, it handles the names from the playlist....[/QUOTE]

From the rhythmbox playlist?  The thing is, my rhythmbox playlist doesnt even show up on the iPod, it doesnt seem like rhythmbox is really connected to my iPod.  Hmm.  I just thought of something.  Maybe i need to delete the songs off of the ipod, and reload them from my computer onto the ipod.  Ill try that.


[QUOTE=mattack]How can I get this to work? I don't see any option to load my iPod with rhythmbox...[/QUOTE]

Well the thing is, you cant really transfer songs over to your computer with rhythmbox as far as I have seen.  You need to use gtkpod for that.  But what rhythmbox *can* do is to read the iPod, while it is connected to the computer, and play songs off of the ipod.  You also have to mess around with mounting the iPod, and there is a tutorial somewhere I cant remember off the top of my head, but just search the forums/google for it.

---

### Post by animalstyle on 2005-02-20
Now that i think about it, I wonder if this is a compatibility issue?  I have the newest 20 gig, and it hasnt worked perfectly with gtkpod.  I get errors like "could not load iTunes_DB" and it crashes alot.  But it works occasionally.

---

### Post by kassetra on 2005-02-20
[QUOTE=animalstyle]
 Well the thing is, you cant really transfer songs over to your computer with rhythmbox as far as I have seen.[/QUOTE]
 
 You can, you just have to build rhythmbox with ipod transfer support (because it's not stable yet)... and then when you mount your ipod, it shows up under radio and library and such, and you can drag & drop files to it... (but it's very buggy!!)

---

### Post by kassetra on 2005-02-20
[QUOTE=animalstyle]Now that i think about it, I wonder if this is a compatibility issue? I have the newest 20 gig, and it hasnt worked perfectly with gtkpod. I get errors like "could not load iTunes_DB" and it crashes alot. But it works occasionally.[/QUOTE]
 
 hmmmm.  WAIT!  How are you mounting your ipod?  Is it mounted as vfat??

---

### Post by animalstyle on 2005-02-21
Im not positive....it is mounted under /dev/sdb2 if thats any help?

---

### Post by kassetra on 2005-02-21
[QUOTE=animalstyle]Im not positive....it is mounted under /dev/sdb2 if thats any help?[/QUOTE]
 
 Ok, sdb2 means it's the windows-based ipod... that's good... if it said sdb1 that would mean it was the mac-based ipod...
 
 Ok, now do this:
  ```
sudo gedit /etc/auto.removable
``` 
 
 and look for a line starting with "ipod" ... and change it to this:
  ```
ipod            -fstype=vfat            :/dev/ipod
``` 
 
 Because if it's not mounting as vfat -- it mounts as msdos, which would give you ALL of the errors you've been getting.
 
 You'll probably need to reboot to make these changes happen.

---

### Post by animalstyle on 2005-02-21
well all my music just decided to disapear off my ipod.  So whether or not this is a larger problem, i dont know.  Im going to have to use windows  :|  ugh.  Gotta reset my ipod, and try to load my music back up.

---

### Post by kassetra on 2005-02-21
[QUOTE=animalstyle]well all my music just decided to disapear off my ipod. So whether or not this is a larger problem, i dont know. Im going to have to use windows :|  ugh.  Gotta reset my ipod, and try to load my music back up.[/QUOTE]
 
 I know this is going to sound all wrong, but I believe that it had been mounting under msdos, and now it's mounted under vfat, so it should all work now... honest.
 
 the difference between the two mounting options are how linux writes information to the drive... and msdos would make all of your music files stick with 8.3 naming conventions and make it act "buggy", because the windows ipod is vfat.
 
 You could probably load your ipod from gtkpod now without any troubles...

---

### Post by animalstyle on 2005-02-21
okay well first off.../etc/auto.removable does not exist on my computer.  But i remember editing a file a while back after looking at a tutorial....it was located at /etc/fstab and i had already edited it to look like this : 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
**/dev/sdb2       /mnt/ipod       vfat    noauto,rw,user  0       0**

So the bold is what I added.  Its been like that for a while.  I tried to reset my ipod in windows and i got an error message.  It mounted in windows and everything, and it even plays songs through rhythmbox.  But it doesnt show any files on the iPod itself anymore.  Man... :shock:

---

### Post by kassetra on 2005-02-21
[QUOTE=animalstyle]okay well first off.../etc/auto.removable does not exist on my computer. But i remember editing a file a while back after looking at a tutorial....it was located at /etc/fstab and i had already edited it to look like this : 
  
  
  # /etc/fstab: static file system information.
  #
  # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  proc            /proc           proc    defaults        0       0
  /dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
  /dev/sda5       none            swap    sw              0       0
  /dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
  /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
  **/dev/sdb2       /mnt/ipod       vfat    noauto,rw,user  0       0**
  
 So the bold is what I added. Its been like that for a while. I tried to reset my ipod in windows and i got an error message. It mounted in windows and everything, and it even plays songs through rhythmbox. But it doesnt show any files on the iPod itself anymore. Man... :shock:[/QUOTE]
  
  auto.removable is like the automount on insert stuffs.. ok same thing though.
  
 When you say you tried to reset your ipod, are you trying to format it?  Also have you tried "restoring" it...?  (unless you have irreplaceable files on it...)

---

### Post by animalstyle on 2005-02-21
Well, I used the windows "iPod Updater" a software program to "restore to factory settings".  Except that it didnt work and it gave me an error message.  Im wondering, is there a way to format the ipod in linux?  Without erasing the "apple software" (if there is any - i guess they use firmware).  Because in GTK-Pod there is an option called "create ipod directories".  Im wondering if I should use that after i format the iPod, and maybe it would eliminate some of the errors (as opposed to restoring it using windows).  I dont know.  Im willing to try anything, all my music is saved on my computer, so my iPod can pretty much be a guinea pig.

---

