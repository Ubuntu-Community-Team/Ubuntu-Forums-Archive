---
title: "Everytime I put a DVD in or CD it opens things"
date: 2006-02-11
forum: Desktop Environments
---

### Post by PapaWiskas on 2006-02-11
Whenever I put a disc in my drive, in KDE it opens Konqueror, gives me some kind of error message, then Kaffeine opens up and starts playing a movie....

I get tired of having to click all this stuff closed.  How do you turn off all this stuff from opening up.

Even Ubuntu opens a movies player up automatically, I hate that....


Thanks...

---

### Post by plexi50 on 2006-02-11
In Ubuntu, you go to System/Preferences/Removable Drives and Media and uncheck the items you do not want to open. I am not sure about Kubuntu however.

---

### Post by Lord Illidan on 2006-02-11
This used to happen to me in Kubuntu too.. How do we stop it? It got frustrating, because everytime I put in a dvd, a blank Konqueror window came up, along with another one containing the dvd contents.

---

### Post by Matchless on 2006-02-11
Hi,
     This is done by IVMAN. You can just use Synaptic or adept to uninstall it. Use forum ad search for IVMAN if you want to know more.

---

### Post by PapaWiskas on 2006-02-11
Okay after some reading and doing the search as suggested on IVMAN, here is what I did.  I now dont have these problems.  Thanks Matchless!!!

first run

sudo gedit /etc/ivman/IvmConfigActions.xml

Then find the sections below in your file, notice how all of mine are commented out.  Konqueror no longer opens, Kaffeine dosnt open and the Audio CD doesnt automatically open anymore.  Make sure you save your changes after you make the edits.  And you dont have to restart or anything, the change is immediate.


   <!-- open konqueror -->
   <!--ivm:Match name="hal.info.category" value="volume"-->
           <!--ivm:Option name="exec" value="MOUNT=$hal.block.device$; kfmclient openURL media:/${MOUNT#/*/}" /-->
   <!--/ivm:Match-->

   <!-- open kscd for audiocds -->
   <!--ivm:Match name="hal.volume.disc.type" value="cd_rom"-->
       <!--ivm:Match name="hal.volume.disc.has_audio" value="true"-->
           <!--ivm:Match name="hal.volume.disc.has_data" value="false"-->
               <!--ivm:Option name="exec" value="/usr/bin/kscd -s $hal.block.device$" /-->
           <!--/ivm:Match-->
       <!--/ivm:Match-->
   <!--/ivm:Match-->

   <!-- kaffeine for videos -->
   <!--ivm:Match name="hal.volume.disc.type" value="dvd_rom"-->
       <!--ivm:Option name="execdvd" value="pumount $hal.block.device$ &amp;&amp; /usr/bin/kaffeine dvd://1" /-->
   <!--/ivm:Match-->

Hope this helps someone.

Thanks for helping me out everyone, I appreciate it.

---

### Post by CyberAngel on 2006-02-11
[QUOTE=Lord Illidan]This used to happen to me in Kubuntu too.. How do we stop it? It got frustrating, because everytime I put in a dvd, a blank Konqueror window came up, along with another one containing the dvd contents.[/QUOTE]


I had this problem too with KDE 3.5.0
After I upgraded to KDE 3.5.1 this issue has been solved for me :)

---

### Post by aysiu on 2006-02-11
There's a great [HowTo on this](http://ubuntuforums.org/showthread.php?t=90457) in the customizations: tips and tricks section of the forum.

---

