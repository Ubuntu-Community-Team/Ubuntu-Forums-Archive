---
title: "Assistance with WoW Installing"
date: 2006-12-22
forum: Gaming &amp; Leisure
---

### Post by yange on 2006-12-22
When I try to install WoW, I enter:

cd /home/yange/WorldofWarcraft/WorldofWarcraftInstall
wine installer.exe

I get the install prompt but when I begin to install, I'm greeted with:

Unrecognized key "options". (AttributeParser::Parse)

Previously I was told that my wine wasn't installed correctly. But I've installed ventrilo, and windows firefox and active x, trying to get wow to work another way.
Also, I copied the wow game folder from a different computer. When I try to run WoW.exe the screens flashes then just stays real bright and a larger resolution. (I've tried also running wow.exe with -opengl if that would do anything. 
Any help?

---

### Post by Naegling23 on 2006-12-22
Go to blizzards site and download the 14 day trial.  Open the .exe in wine.  

I had some trouble installing wow from the cd, my disks were not being recognized (well, they were, there just was nothing on them!).

I just downloaded the demo from blizzard, it updated and everything without a hitch.

---

### Post by hikaricore on 2006-12-22
Be aware that after the original download you're going to be in for a very very hellish update download.  You have been warned :)

---

### Post by Naegling23 on 2006-12-22
yes, but if you have the cd version, your still going to need to update it.  It actually took longer to update my windows version which was installed from cd (yes, im running two copies on two os's)...well the windows version took longer because I tried to open a web page while it was downloading, so windows locked up, but it still took longer.

So yes, big update, but you need it if you have the cd version anyway.

---

### Post by hikaricore on 2006-12-22
:P  500mb patch for 2.01 between like 3 patches, I laughed at my girl who spent all day downloading it /w blizzards p2p, I just mounted her drive and copied it.  done in 2 minutes.  bam.  lol

---

### Post by yange on 2006-12-22
Alright, thanks guys, I'm downloading as we speak, I'll update soon.

---

### Post by Sammi on 2006-12-22
Here is a howto on installing and playing WoW using Wine under Ubuntu:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Hope it is helpful.

---

### Post by yange on 2006-12-22
> **Sammi said:**
> Here is a howto on installing and playing WoW using Wine under Ubuntu:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Hope it is helpful.

These were the exact instructions that I followed that lead me to this problem. I've also tried several other different How-to's.  
Currently I'm downloading the 3.16 GB install from official blizzard, only at 2% after 5 hours... taking a while =(

---

### Post by NeoGreen on 2006-12-23
I am trying to install now, I have already installed Wine and I get to the part where I insert the CD and it start to install.  The problem I am having is that when it asked me to install the second CD, it just freezes.  It tries to read the CD then it doesn't do anything.  Anybody have any ideas?:confused:

---

### Post by Sammi on 2006-12-23
> **yange said:**
> These were the exact instructions that I followed that lead me to this problem. I've also tried several other different How-to's.  
Currently I'm downloading the 3.16 GB install from official blizzard, only at 2% after 5 hours... taking a while =(
Ok that means than there is something missing from the howto, that can be added. If that download works, then you're welcome to add instructions to the howto on that matter ;):D

> **NeoGreen said:**
> I am trying to install now, I have already installed Wine and I get to the part where I insert the CD and it start to install.  The problem I am having is that when it asked me to install the second CD, it just freezes.  It tries to read the CD then it doesn't do anything.  Anybody have any ideas?:confused:

You most definatively could be helped by the howto I mentioned. There are two different approaches to installing WoW mentioned in it, which both could solve your problem.
One is copying all the files from all the cd's to a folder on the harddrive and then installing from that folder. That will most likely solve you cd switching problem.
The other is installing WoW in Windows and then just copying the folder over to a Linux partition.

---

### Post by hikaricore on 2006-12-23
> **NeoGreen said:**
> I am trying to install now, I have already installed Wine and I get to the part where I insert the CD and it start to install.  The problem I am having is that when it asked me to install the second CD, it just freezes.  It tries to read the CD then it doesn't do anything.  Anybody have any ideas?:confused:

Your best bet would be to make a temporary folder on your Desktop or on another hard drive (if you don't have enough room on your main drive) and one by one copy the contents of each cd to your computer.  Then run the Setup.exe via wine from that folder, no cd switching, no worries.  This method has been mentioned in many Howtos and I believe still is.

Good luck,

--Aaron

---

### Post by NeoGreen on 2006-12-25
Awesome, I'll try it thanks for the info.:p

---

### Post by Ferrat on 2006-12-26
Recommended for all, after a big update copy the Update file to a disk or backup you WoW folder so you don't have to go thru that hell again ;)

---

### Post by NeoGreen on 2007-01-04
Yeah, you are right.  I don't want to go through that again.:)

---

### Post by graigsmith on 2007-01-05
there were a couple dll overrides i had to use to install my copy.  im not sure what those dll's were. try overrriding these dll files.  you have to find a copy of the dll, and throw it in this folder  .wine/drive_c/windows/system32/  

riched32.dll
msgsm32.acm
msvcp60.dll
riched20.dll
mfc42.dll

then you go into winecfg, and set each of those dlls on override to use a real version of that dll. and it should install.  Also, you only need these to install it.  you won't need them overidden to play wow.

---

### Post by graigsmith on 2007-01-05
also, if you have a minimap crashing problem, the one where the minimap turns white when you go indoors and then you get flickering problems and all the text dissapears and then you just have to close it.

you can fix that with a registry edit.

go to the linux console, type regedit

add the key "HKEY_CURRENT_USER\Software\Wine\OpenGL"

under that add a string value "DisabledExtensions"  with Value "GL_ARB_vertex_buffer_object"


After installing this registry key, your minimap will stop crashing when you go inside. it will still turn white.  but at least it doesn't crash.

---

### Post by hikaricore on 2007-01-05
> **graigsmith said:**
> also, if you have a minimap crashing problem, the one where the minimap turns white when you go indoors and then you get flickering problems and all the text dissapears and then you just have to close it.

you can fix that with a registry edit.

go to the linux console, type regedit

add the key "HKEY_CURRENT_USER\Software\Wine\OpenGL"

under that add a string value "DisabledExtensions"  with Value "GL_ARB_vertex_buffer_object"


After installing this registry key, your minimap will stop crashing when you go inside. it will still turn white.  but at least it doesn't crash.


I thought the minimap bug was fixed.  It's been working for me nearly a month now.  Though if it is not fixed I suspect that my UI scale may be saving me, I have it set to "0.64999997615814" and I can't remember if the map was working before I changed this.

---

### Post by graigsmith on 2007-01-05
it was fixed for nvidia hardware apparently. 

i'm still experiencing the bug on my ATI 9200 using open source drivers, (because i can't use ati's drivers because they are unstable and crash my system)

---

### Post by hikaricore on 2007-01-05
> **graigsmith said:**
> it was fixed for nvidia hardware apparently. 

i'm still experiencing the bug on my ATI 9200 using open source drivers, (because i can't use ati's drivers because they are unstable and crash my system)

Ah that would explain it.  I got my nvidia card, played with a crappy broken minimap, updated wine a few weeks later without thinking about it, then the minimap was working.  lol  Thanks for clarifying that this was indeed fixed for nvidia, now I can mess with my Config.wtf settings without fear of losing the minimap again.  :)

---

### Post by Sammi on 2007-01-05
> **graigsmith said:**
> there were a couple dll overrides i had to use to install my copy. im not sure what those dll's were. try overrriding these dll files. you have to find a copy of the dll, and throw it in this folder .wine/drive_c/windows/system32/ 
 
riched32.dll
msgsm32.acm
msvcp60.dll
riched20.dll
mfc42.dll
 
then you go into winecfg, and set each of those dlls on override to use a real version of that dll. and it should install. Also, you only need these to install it. you won't need them overidden to play wow.
Great. We'll have to get this in to the howto. I don't have time to do it here and now. If anybody else feels up to it, then you are free to do it. Else I'll do it later :rolleyes: 
 
Remember the community help site, which that howto resideds in, is open, so anybody can edit ;)

---

### Post by Afteraffekt on 2007-01-06
My advice...install on windows and put it in the drive wine makes..the one it mounts, and run it from there...how i did it and wow runs freaking awsome

---

### Post by MaT0 on 2007-07-03
Hi,

I don't know if this is still a matter of discussion, but I've managed to solve the problem with the 

Unrecognized key "options". (AttributeParser::Parse)

..
Do the following:

1. Click on Places -> Home Folder in the top panel. Use this application to create a directory and copy all of the files from all of the CD's to this directory on your hard drive (DON'T overwrite when prompted). 

2. Then start the installation by opening a terminal and doing these commands: 

 [B]cd /<path-to-directory>/
 wine Installer.exe[/B]

*Replace <path-to-directory/> with the right path to the directory where you copied all the files.*

**!!!   the key to success is that you MUSTN'T overwrite the installer.exe from CD1 !!!**

hope this helps :p

---

