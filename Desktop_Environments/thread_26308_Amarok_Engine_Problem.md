---
title: "Amarok Engine Problem"
date: 2005-04-12
forum: Desktop Environments
---

### Post by rshd301 on 2005-04-12
Everytime I start Amarok I have to change the engine from Xine to either arts or gstreamer, apply (neither of these two work) and reset to xine for my sound to work.

Xmms works fine each time so what might be the problem in Amarok ?

---

### Post by F for Fragging on 2005-04-12
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8703](https://bugzilla.ubuntu.com/show_bug.cgi?id=8703)

In short, uninstall the package amarok-arts and install amarok-xine. That 
should make amaroK work.

---

### Post by rshd301 on 2006-05-04
I know it's been over a year since I posted my original nut I have been using an alternative distro since then. In the past few days I have got back into Ubuntu and am running Dapper. However, I still have an issue with Amarok which is my mp3 player of choice. I have xine installed with no other engines but when I try to play a track the player skips over the track and displays the playlist finished message. I'm currently using Quod Libet, JUK & XMMS for MP3 playback but would prefer Amarok. I'm going round the bend with this Amarok and MP3 playback issue and would dearly love to get it sorted for once and forall. Any assistance would be gratefuly received.

---

### Post by .t. on 2006-05-18
I am also running Dapper, and came across this thread on a search. I would advise reposting in the Dapper forum. Note that I am using amaroK 1.4 from the kubuntu.org repository. I don't know if you are, nor if that is the current one in the main repo. Nonetheless, I will outline a problem with the gstreamer engine which is the Ubuntu default. Basically, amaroK has dropped support for it as there was little support upstream and they had a supposedly working xine engine. However, I find that the xine engine refuses to play also, experiencing the results you posted above.

If there are no bugs pertaining to this matter already open, then I will open one in Launchpad. I still suggest that you post in the Dapper forum.

---

### Post by flankker on 2006-05-18
[QUOTE=.t.]I am also running Dapper, and came across this thread on a search. I would advise reposting in the Dapper forum. Note that I am using amaroK 1.4 from the kubuntu.org repository. I don't know if you are, nor if that is the current one in the main repo. Nonetheless, I will outline a problem with the gstreamer engine which is the Ubuntu default. Basically, amaroK has dropped support for it as there was little support upstream and they had a supposedly working xine engine. However, I find that the xine engine refuses to play also, experiencing the results you posted above.

If there are no bugs pertaining to this matter already open, then I will open one in Launchpad. I still suggest that you post in the Dapper forum.[/QUOTE]

count me in too, same problems using the new 1.4 version :(

---

### Post by conor on 2006-05-18
Me too...
And this thread should definately go to dapper.  

My issue:
amarok-xine, worked fine until I 'apt-get dist-upgrade' -ed
and now when I load amaroK I get a message "Xine was unable to load any audio drivers."  And it reverts to the 'void engine' aka nada.  

I have the libxine-extracodecs package installed and the libxine-main1 and the libarts1-xine package installed.  

IMPORTANT::  For those of you for whom the player just skips the track and says playlist finished, you need the libxine-extracodecs package available in the multiuniverse repository.  But I'm afraid that might just get you to where I am...

Anyone able to resolve this?

---

### Post by conor on 2006-05-18
I updated to amaroK 1.4 from the kubuntu..og site - still no change.

---

### Post by hermesrules on 2006-05-19
I used to be able to use Amarok with the gstremer engine (0.10) with the beta of amarok 1.4, until I did a dist-upgrade to get the final 1.4, which I am currently running, and I got the message that the package amarok-gstreamer has to be removed.

This is not a very nice situation for me, because with gstreamer I could have amarok play trough my Audigy2 ZS Notebook card, and I can't set xine to use it. Very annoying.

Does anyone know if the unavailability of gstreamer for amarok 1.4 is temporary or constant? If I need to use xine, which is a fine engine, how do I configure it to use my Audigy card (it is mapped at /dev/dsp1, but the latter does not show in the list with available deviced). I am able to hear my system sounds through the audigy, but can't make Kaffeine and amarok use it too (both using xine as an engine).

Thanks!

---

### Post by Aikurn on 2006-05-20
I have the same problem since I upgraded to 1.4, "Xine was unable to load any audio drivers.". This sounds like a bug. ](*,) 
Anyway, having just one engine available doesn't seem very sensible and amarok-gstreamer has always worked fine for me. I'd love to have it back.

---

### Post by mars05 on 2006-05-21
[QUOTE=conor]
My issue:
amarok-xine, worked fine until I 'apt-get dist-upgrade' -ed
and now when I load amaroK I get a message "Xine was unable to load any audio drivers."  And it reverts to the 'void engine' aka nada.  
[/QUOTE]

I just encountered the same problem,  switching to the amarok arts-engine resolved it though, after issuing a killall -9 artsd && amarok

I'm a noob, but maybe that helps, at least for me there is music again.

---

### Post by ghostdog on 2006-05-21
[QUOTE=Aikurn]I have the same problem since I upgraded to 1.4, "Xine was unable to load any audio drivers.". This sounds like a bug. ](*,) 
Anyway, having just one engine available doesn't seem very sensible and amarok-gstreamer has always worked fine for me. I'd love to have it back.[/QUOTE]

Had the same problem when I upgraded from Amarok 1.4 beta3 to 1.4 Final in Dapper, the Gurus at the Ubuntu IRC Channel "amarok" helped me by telling me to do the following.

This one did not work
$rm ~/.kde/share/apps/amarok/xine-config


This worked like a charm
$rm ~/.kde/share/config/amarokrc


In anycase you will lose your setting by erasing the last file, but it worked. :D

---

### Post by ruffneck on 2006-05-21
[QUOTE=Aikurn]I have the same problem since I upgraded to 1.4, "Xine was unable to load any audio drivers.". This sounds like a bug. ](*,) 
Anyway, having just one engine available doesn't seem very sensible and amarok-gstreamer has always worked fine for me. I'd love to have it back.[/QUOTE]

ditto for me. Whoever files the bug on launchpad please post the Bug# for us to add comments etc.

---

### Post by Aikurn on 2006-05-22
[QUOTE=ghostdog]This worked like a charm
$rm ~/.kde/share/config/amarokrc

In anycase you will lose your setting by erasing the last file, but it worked. :D[/QUOTE]

Thanks!!! I investigated a bit more and the bad lines are in the section [Xine-Engine]. There's no need to remove anything else :)

---

### Post by commodore on 2006-06-14
I have the problem too and I can't get Amarok to work.

---

### Post by commodore on 2006-06-14
I had to install libxine-extracodecs. At first I didn't find them anywhere but it's fixed now.

---

### Post by Daz_Man on 2006-08-18
commodore you are a genius! That has been driving me mad.

---

