---
title: "Wine 0.9 is out!"
date: 2005-10-25
forum: Deferred/Invalid Requests
---

### Post by stoffe on 2005-10-25
Announcement:
[http://www.winehq.org/pipermail/wine-announce/2005-October/000064.html](http://www.winehq.org/pipermail/wine-announce/2005-October/000064.html)

Sources:
[http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.tar.bz2](http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.tar.bz2) or
[http://prdownloads.sourceforge.net/wine/wine-0.9.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-0.9.tar.bz2)

I'm really anxious to try this out, would be excellent if this landed in backports soon. :)

---

### Post by glug101 on 2005-10-25
[QUOTE=stoffe]Announcement:
[http://www.winehq.org/pipermail/wine-announce/2005-October/000064.html](http://www.winehq.org/pipermail/wine-announce/2005-October/000064.html)

Sources:
[http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.tar.bz2](http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.tar.bz2) or
[http://prdownloads.sourceforge.net/wine/wine-0.9.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-0.9.tar.bz2)

I'm really anxious to try this out, would be excellent if this landed in backports soon. :)[/QUOTE]
Try out their Debian repository.  They have reportedly tested it on Ubuntu (or at least mention that it should work).

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

It's not canon, but I'm giving it a try later tonight. ;)

---

### Post by stoffe on 2005-10-25
Yeah, I usually run those repos also, but they seem really rarely updated. However, now that I check it "anyways" for the second time today I see that they have indeed updated it this time. Good, good.

Should still be in backports. ;)

---

### Post by paulle on 2005-10-26
you can update or install from winehq directly. it works.
i tried it today.   cao paulle

---

### Post by Terracotta on 2005-10-27
Why would this need to be in backports? there's nothing illegal about wine is it??? Isn't this more like something for universe?

---

### Post by overgee on 2005-10-28
> [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

I tried to install the WINE 0.9 Package from wine.sourceforge.net/Ubuntu/breezy but it got totally messed up. I couldn't access any input form fields inside wine, it wouldn't let me access my network devices and it got my keyboard settings totally messed up.

The same type of thing happened when I tried to install wine-20050930 manually earlier this month. I then thought it had something to do with my re-re-re-re-re-updated breezy dist. But I just had a complete installation of breezy so it should be fresh enough.

May be it it depends on my German configuration files or something.

But the latest wine version for breey repos works fine with me.


Björn

---

### Post by b_chris on 2005-10-28
I'm haveing trouble installing Wine 0.9.

Getting the following error message:

Err [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.0-winehq-1
  Error reading from server. Remote end closed connection
Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.0-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.0-winehq-1_i386.deb)  Error reading from server. Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



Any Ideas??

regards.

---

### Post by snowjunkie on 2005-10-28
[QUOTE=Terracotta]Why would this need to be in backports? there's nothing illegal about wine is it??? Isn't this more like something for universe?[/QUOTE]

Backports are not for illegal debs.  They are for updates that will form part of the next ubuntu release but are being released early for your enjoyment.

---

### Post by jdong on 2005-10-31
Wine 0.9 is sweet -- a bit more stable than the 20050725 snapshot. However, it's not in Dapper yet.

---

### Post by Kyral on 2005-10-31
GASP! JDong posts j/k ;P

---

### Post by jdong on 2005-10-31
Ugh, I can only stay awake 18 hours a day doing work, and Backports has been sitting on the back burner thanks to the Breezy release's refreshment...  I'm not supernatural yet.

---

### Post by Craig Gilman on 2005-10-31
I'm a newbie - just getting to grips with kubuntu... i just got wine using apt-get install wine ... it installed but now I don't know how to go about using it to load my windows software! Anybody help a noob?

Do I literally just run the install exe files ?

---

### Post by SickTwist on 2005-11-03
[QUOTE=Craig Gilman]I'm a newbie - just getting to grips with kubuntu... i just got wine using apt-get install wine ... it installed but now I don't know how to go about using it to load my windows software! Anybody help a noob?

Do I literally just run the install exe files ?[/QUOTE]
If you want to edit some of wine's configuration options (optional step) run

**winecfg**

If you want to run Setup.exe and it is on your desktop, run

**wine ~/Desktop/Setup.exe**

Wine creates a directory called ".wine" (without quotes) in your home directory. The period at the beginning means this is a hidden directory. Inside this directory is another directory called "drive_c" which which is Wine's emulation of the C: drive in Windows.

So C:\Program Files\Mozilla Firefox\ would be located in ~/.wine/drive_c/Program Files/Mozilla Firefox

Once the program is installed, you run it like this (substituting this path with the correct one). The quotation marks are to keep the terminal from getting confused with the spaces in the path:

wine "~/.wine/drive_c/Program Files/MyApp/MyApp.exe"

Hopefully that little introduction helps. I'd love to see somebody with more expertise than myself write a more in-depth guide to setting up wine 0.9 in Breezy Badger. Perhaps this will appear soon in the Tips and Tricks section <hint><hint>. :)

---

### Post by jdong on 2005-11-11
MOTU's already working on getting 0.9 for Dapper... But it's not an easy job.

---

### Post by YokoZar on 2005-11-15
Hey jdong, I'll be putting the Wine packages in the Dapper repositories in the next two weeks or so, after I get my key signed and everything can be official-like.

Till then, play Half Life 2 in Steam using the debs from the winehq repository ;)

---

### Post by jdong on 2005-11-16
cool, thanks. Keep us posted!

---

### Post by pdpmalcolm on 2005-11-16
where is the .wine directory located?

---

### Post by jdong on 2005-11-16
~/

---

### Post by TmP on 2005-11-22
Hey!
It's nice they've got it ready.

There's also a version of winetools at hand, that supports it.
It's here:
[http://www.von-thadden.de/Joachim/WineTools/index.html#download](http://www.von-thadden.de/Joachim/WineTools/index.html#download)

I've downloaded the tar.gz,
On my Breezy, i also had to add the Xdialog package from synaptics
The wt command didn't work for me, but it was fine to run the 
wt0.9jo
found in
/usr/local/winetools
Bummer. Winetools still doesn't download the IE6.0 , which is necessary for most of its components. oh well. Trash it. 

Than I downloaded the sidenet wine configuration tool.
Got bact into winecfg to change the version back to win2000.
Got some prompts about missing translations, but IE6 is comming nicely.

we'll see..

[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

I'm still a bit of a newb, so you could correct me by giving the best method of installing the winetools. I'm also looking foreward to a how-to 

Wouldn't it be fun to see how a win based virus would act in wine?

C'ya

---

