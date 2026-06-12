---
title: "A submarine sim for linux!"
date: 2006-11-07
forum: Gaming &amp; Leisure
---

### Post by redbluemangle on 2006-11-07
[http://dangerdeep.sourceforge.net](http://dangerdeep.sourceforge.net)


anyone know how to get this working on ubuntu?

---

### Post by catlett on 2006-11-07
This one is easy believe it or not. Ubuntu is based on Debian Linux. To be more specific it is based on the 'unstable' version of Debian 'Sid".
What this means is, almost all packages made for Debian will install on Ubuntu (emphasis on 'almost', some may not)
When you go to the download page for dangerdeep, you will see a Debian installation package. Select that package and when it downloads you will have the option to install it automatically with 'gdebi installer'. Say yes to gdebi and it will install the package for you. It most likely won't show up in a menu so just enter ```
dangerdeep
``` in the terminal and it will start. You can make a launcher (shortcut) for it by right clicking anywhere on the desktop and selecting 'create launcher'. Browse to /usr/share/games, dangerdeep should be there, and select the dangerdeep binary for the file to launch.
Sometimes debian packages don't install or work properly but hopefully this one does.

---

### Post by ardvark71 on 2006-11-07
> **catlett said:**
> This one is easy believe it or not.

Really?

That hasn't been my experience. I can't get dpkg or aptitude to do anything with it. Keeps complaining about "dpkg: need an action option" even though I typed in "sudo dpkg install..." unless I typed in the wrong command or got something backwards. What do I need to do, draw a picture for it???

How I DETEST command line installs](*,)

---

### Post by 23meg on 2006-11-07
You have to type ```
sudo dpkg -i **package_path**
```
[QUOTE=ardvark71]How I DETEST command line installs[/QUOTE]If you're using Edgy or Dapper, a double click will also do.

---

### Post by catlett on 2006-11-07
> **ardvark71 said:**
> Really?

That hasn't been my experience. I can't get dpkg or aptitude to do anything with it. Keeps complaining about "dpkg: need an action option" even though I typed in "sudo dpkg install..." unless I typed in the wrong command or got something backwards. What do I need to do, draw a picture for it???

How I DETEST command line installs](*,)

Sorry I assume everyone is using firefox. When firefox downloads the deb, it will give you the option of opening the file with gdebi installer.
But if you just download the deb, you can double click on the file just like in windows and gdebi will open up and install the deb.
The last thing is what meng just said. To install through the command line, you ned to use the dpkg command with the -i option as root. 
```
sudo dpkg -i dangerdeep_0.2.0_ideb
```

---

### Post by ardvark71 on 2006-11-07
Hi guys...

Thank you very much for your help....getting pretty frustrated at a whole day wasted trying to install a couple games....

I finally was able (with your assistance) to get dangerdeep installed but now I get this error message when I try to run it:

Caught exception: Error opening directory '/usr/share/games/dangerdeep/objects/airplanes/'
Stack trace: (5 frames)
0x806ced3 in dangerdeep at ??:0
0x806b4b4 in dangerdeep at ??:0
0x806b58e in dangerdeep at ??:0
0xb7a86ec2 in __libc_start_main at ??:0
0x804e291 in __gxx_personality_v0 at ??:0

Oh, well....:(

---

### Post by redbluemangle on 2006-11-07
i'm not even sure if my ATi card is working well enough for 3D. Any screen savers with shading effects run at about 2fps.

---

### Post by rabid emu on 2006-11-07
ardvark71, I got the same error.  I don't know a solution yet.

---

### Post by jm2003uk on 2006-11-08
> **ardvark71 said:**
> Hi guys...

Thank you very much for your help....getting pretty frustrated at a whole day wasted trying to install a couple games....

I finally was able (with your assistance) to get dangerdeep installed but now I get this error message when I try to run it:

Caught exception: Error opening directory '/usr/share/games/dangerdeep/objects/airplanes/'
Stack trace: (5 frames)
0x806ced3 in dangerdeep at ??:0
0x806b4b4 in dangerdeep at ??:0
0x806b58e in dangerdeep at ??:0
0xb7a86ec2 in __libc_start_main at ??:0
0x804e291 in __gxx_personality_v0 at ??:0

Oh, well....:(

> **rabid emu said:**
> ardvark71, I got the same error.  I don't know a solution yet.


I get the same error. I saw somewhere that you can use the older version...which does seem to work apart from there's no sound. Hope that prob can get sorted at some point. Looks like a really good sim.

---

### Post by jm2003uk on 2006-11-08
Hmm....i've just re-downloaded it all and extracted the data files (seperate download) into the /usr/share/games/dangerdeep directory again and it worked!! I've got some sounds and it hasn't crashed! Will have a proper play around later on.

---

### Post by ardvark71 on 2006-11-08
> **jm2003uk said:**
> Hmm....i've just re-downloaded it all and extracted the data files (seperate download) into the /usr/share/games/dangerdeep directory again and it worked!! I've got some sounds and it hasn't crashed! Will have a proper play around later on.

Right on!

I think I'll give that a shot too...

:KS

---

### Post by ardvark71 on 2006-11-08
Hmmm...

Doesn't work, I get the same error message....and it keeps asking for this:

Caught exception: Error opening directory '/usr/share/games/dangerdeep/objects/airplanes/'

I didn't see this or any data files in the "data.tar.gz" file I extracted.

Can someone tell me what I'm doing wrong?

Thanks!

---

### Post by catlett on 2006-11-08
> **ardvark71 said:**
> Hmmm...

Doesn't work, I get the same error message....and it keeps asking for this:

Caught exception: Error opening directory '/usr/share/games/dangerdeep/objects/airplanes/'

I didn't see this or any data files in the "data.tar.gz" file I extracted.

Can someone tell me what I'm doing wrong?

Thanks!

Did you extract the files from the tar file and then copy those files over or did you just copy the tar file into the folder? A tar file is like a zip file, it needs to be unzipped. After you download the tart, right-click on it and select "extract here". Next you have to copy the files to /usr/share/games/dangerdeep
You can use the cp command to copy the files 
```
sudo cp ???dangerdeepdata??? /usr/share/games/dangerdeep
```Obviously the question marks represent the name of the files you extract.
A gui way is to launch nautilus as root ```
gksudo nautilus
```When it opens browse to /usr/share/games/dangerdeep and then drag and drop the extracted files into it.
Hope that helps.

---

### Post by ardvark71 on 2006-11-09
8) 8) 8) 

We've got contact gentlemen (after much effort:-?)

Although, I think there will be a couple bugs to iron out but what can you expect with an old Pentium III and a Radeon 7200? I'm not complaining though, it's been an extremely reliable system. :) 

Thank you for your guy's help, it's VERY much appreciated!

:KS

---

### Post by Perfect Storm on 2006-11-09
We have a howto on Ubuntu Gamers Arena on Dangers from the Deep:
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=150&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=150&Itemid=63)

---

