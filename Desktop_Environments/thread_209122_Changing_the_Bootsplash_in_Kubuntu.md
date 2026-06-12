---
title: "Changing the Bootsplash in Kubuntu"
date: 2006-07-04
forum: Desktop Environments
---

### Post by tartarian on 2006-07-04
On Kde-look.org there are a number of different bootsplashes. I was wondering how  I can install them. I did read something on one forum about kbootsplash but it doesn't appear in synaptic and seems to be only available for SuSe and Quellen on the homepage. Is there a different program/how-to or maunal method anyone can suggest please? Thankyou!

---

### Post by Jucato on 2006-07-04
Just to clarify things, are you talking about
a. bootsplash - the splash screen that you see while starting Linux, with the scrolling text on a black background?

or

b. splash screen - the splash screen that you see while loading KDE, usually around 5-10 seconds, where you either see icons or text like "loading session"?

If it's a bootsplash, I'm afraid there's not easy way to change that in Ubuntu or in Kubuntu. It's possible, but not very easy. If it's a splash screen, it's easy to install one from KDE-look.org.

---

### Post by tartarian on 2006-07-05
It's bootsplash - the splash screen seen when starting Linux with the big Kubuntu letters on and lots of text on a black background. Why would KDE look have a huge section of them if they were impossible to install???

---

### Post by Jucato on 2006-07-05
[quote=tartarian]Why would KDE look have a huge section of them if they were impossible to install???[/quote]

Because Ubuntu has it's own bootsplash program, which is different from what other KDE distros use. The name of Ubuntu's bootsplash is [USplash](https://help.ubuntu.com/community/USplash), and AFAIK this is the only way to change it:
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

---

### Post by tartarian on 2006-07-06
Can i use USplash in Kubuntu? I thought ubuntu used GNOME by default? So why would the bootsplashed be on KDE look?

---

### Post by Jucato on 2006-07-06
USplash is not a GNOME application. It's a bootsplash program created by Ubuntu/Canonical and is used in all Ubuntu distros: Ubuntu, Kubuntu, and Xubuntu. 

The bootsplash themes on KDE-Look are for other bootsplash programs. I'm not sure what other distros use for their bootsplash. But it's definitely not USplash. So AFAIK, you can't use those bootsplash themes in Kubuntu.

I don't know how or if you can change USplash and install something else.

EDIT: I'd like to correct myself a bit. Theoretically, you can use those bootsplash screens, because they are just images. However, in order to use them with USplash, you  have to edit the image in such a way that many of the colors will be practically useless. Also, you have to compile those .png images into .so (as per the instructions in the wiki). You might find this thread useful as it gives instructions on how to edit images into the proper format.

[http://www.ubuntuforums.org/showthread.php?t=207341](http://www.ubuntuforums.org/showthread.php?t=207341)

---

### Post by tartarian on 2006-07-06
well this is interesting..... just typed sudo usplash into konsole and it has messed up my screen, big style. Last time i type somethin i dont know about into the konsole. Loads of colors have gone iike bright green and pink! Any ideas how I can fix it??? Stupid me:( 

EDIT: Problem solved: Just fiddled with my Gamma levels and it went back. Don't know what I did!

As with the original problem, I basically need a different bootsplash program??? Any suggestions? 

Btw, what does AFAIK mean?

---

### Post by Jucato on 2006-07-06
Like I said, I'm not familiar with installing/replacing bootsplash programs. And I'm pretty sure it will not be that easy. 

AFAIK = As Far As I Know
IIRC = If I Remember Correctly
IMO = In My Opinion
IMHO = In My Humble Opinion

---

### Post by DoorGunner on 2006-07-07
I had the same problem.... What i did to solve it was to 
sudo apt-get remove usplash
reboot (with no splash screens)
sudo apt-get install usplash

everything went back to normal

I wanted to keep the kde-core but just wanted the origional ubuntu splash....this fixed it.


------------------------------------
what i saw was that the /usr/lib/usplash had both kubuntu and ubuntu default.... 
when i used the $ sudo update-alternatives --config usplash-artwork.so I noticed that you can select one and that works for shutdown ubuntu splash but not the start up..... so i just tried to reload usplash hoping that it would reset the whole thing....and it did.

---

