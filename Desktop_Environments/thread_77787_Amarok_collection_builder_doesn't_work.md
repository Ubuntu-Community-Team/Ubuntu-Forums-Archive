---
title: "Amarok collection builder doesn't work"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Mrtn on 2005-10-17
I just installed ubuntu for the first time on my PC with 64-bit processor (though I installed the 32 bit version so the codecs and plugins would work).

It gives the following error:

During the previous startup, KNotify crashed while instantiating KNotify. Do you want to try again or disable aRts sound output?
If you choose to disable aRts output now, you can re-enable it later or select an alternate sound player in the System Notifications control panel.

It says building collection, but the progress bar either stays 0% or starts at 100% (and nothing is added).

Can this problem be solved by using a mysql database instead of a litesql database?

Is it worth the hassle?

---

### Post by Mrtn on 2005-10-17
Nobody knows of any older version to install or a new version so I can give it another shot? :(

Everything works fine except adding music to the collection.

---

### Post by kosmic on 2005-10-18
Hum i have the same problem with my AMD 64, but the same system in my AMD Athlon runs just fine...I don't know what is causing this :(

---

### Post by yage on 2005-10-18
how long have you waited for the collection database to be buildt? I have about 15gigs of music on my machine and it took 20-30 minutes for amarok to finish the building.. a long time saying 0% and then moving to 50% and hanging there for a long time... Using sqlite

---

### Post by YanH on 2005-10-18
I have a similar problem. Amarok works correctly in every other way but the collection builder doesn't work. It scans the music library but when it gets to 100% it adds nothing. :( 

This is really frustrating as Amarok is such a cool media player.

---

### Post by Mrtn on 2005-10-18
[QUOTE=yage]how long have you waited for the collection database to be buildt? I have about 15gigs of music on my machine and it took 20-30 minutes for amarok to finish the building.. a long time saying 0% and then moving to 50% and hanging there for a long time... Using sqlite[/QUOTE]

I am sure it is a malfunction because I formatted my comp and I only had like 2 - 3 albums on my PC. Even when told amaroK to only search in the folder where my albums were located it would not find them.

If I press the build collection button just no action occurs at all, it doesn't start since I don't hear my computer working hard to scan for the files. Yet it either displays 0 or 100% without any change... weird :(

I am really saddened, because amaroK seems the niced player to catalogue your music...

Hopefully a new version will be released soon so I can give that one a try ;)

---

### Post by mpettitt on 2005-10-18
I was having some problems with the catalogue failing with certain files in the collection directory. I think the tag reading functions in amaroK are slightly messed up, since most files will load perfectly, but others will jam it up completely.
In my case, it was a bunch of .ogg files converted with KAudioCreator. With them there, collection regeneration failed every time I tried. Removed them, and tried again, and it worked perfectly. Reencoding the same files with Sound Juicer solved that (presumably some different settings passed to the encoder).

---

### Post by kosmic on 2005-10-18
[quote=mpettitt]I was having some problems with the catalogue failing with certain files in the collection directory. I think the tag reading functions in amaroK are slightly messed up, since most files will load perfectly, but others will jam it up completely.
In my case, it was a bunch of .ogg files converted with KAudioCreator. With them there, collection regeneration failed every time I tried. Removed them, and tried again, and it worked perfectly. Reencoding the same files with Sound Juicer solved that (presumably some different settings passed to the encoder).[/quote]
 
Hum i've also some ogg files in the directory, when i get home i will move them to another part, and make amarok build the colection wizard again to see if works :)

---

### Post by YanH on 2005-10-18
If it is down to file types and tag encoding then it must be specific to the Breezy version of Amarok as my collection of music files are treated differently by Hoary and Breezy. The Hoary version of Amarok successfully builds a collection whereas Breezy claims to be building a collection but when the task bar reaches 100% the collection remains empty.

---

### Post by Mrtn on 2005-10-18
I am quite sure that for me it is a different problem, since I don't have any OGG files and it fails to scan completely.

You should notice your computer working hard when it scans your whole HD for music files ;)

Any way I could install the hoary version?

---

### Post by Mrtn on 2005-10-18
But it seems many people are having problems with this program. Do KDE people also have so many problems?

Everything works perfectly fine here as far as I can tell... except that blasted program :P

---

### Post by Hairy_Palms on 2005-10-18
amarok scanned all my music in both hoary and breezy but it never added the .wma files (not ripped by me, i always hated .wma even in windows)

---

### Post by Mrtn on 2005-10-18
Wonder why anyone would rip to wma :D

Thats like... almost as bad as ripping to atrac ;)

---

### Post by mlomker on 2005-10-18
You could consider compiling your own copy of the latest version.  [Check out this post.]("http://www.ubuntuforums.org/showthread.php?p=424062#post424062")

---

### Post by kanogil on 2006-01-02
[QUOTE=YanH]I have a similar problem. Amarok works correctly in every other way but the collection builder doesn't work. It scans the music library but when it gets to 100% it adds nothing. :( 

This is really frustrating as Amarok is such a cool media player.[/QUOTE]

I believe I had the same problem: Amarok was able to play all my files, but the collection browser was blank (although I could still see the track and album count below).

Here's how I fixed the problem: 

1. removed amarok and the sqlite-related packages in Adept
2. removed the directory ~/.kde/share/apps/amarok/
3. updated the repositories and reinstalled the packages uninstalled in step 1.

Hope this helps :)

---

### Post by tUrtleAE86 on 2006-01-10
I was having the same problems with the collection builder, so I installed amarok svn. It didn't work at first, BUT, I decided to install it using sudo, although this isn't recommended, because it warns you that you don't need to run as sudo. 

But, after installing with sudo, the collection builder just worked!

EDIT: Hrm... I still get problems on certain folders. This is just bizzare.

---

