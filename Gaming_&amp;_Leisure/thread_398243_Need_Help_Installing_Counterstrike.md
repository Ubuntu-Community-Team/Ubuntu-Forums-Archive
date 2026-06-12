---
title: "Need Help Installing Counterstrike"
date: 2007-03-31
forum: Gaming &amp; Leisure
---

### Post by Catfish_lolipop on 2007-03-31
i need help with counterstrike. so far i have nothing downloaded because im so confused i dont know what to do first......can anybody help me?

---

### Post by 3rr0r on 2007-03-31
post here:  [http://www.ubuntuforums.org/forumdisplay.php?f=230](http://www.ubuntuforums.org/forumdisplay.php?f=230)

---

### Post by Catfish_lolipop on 2007-03-31
i couldnt find anything there.....do u have any other suggetions?

---

### Post by K.Mandla on 2007-03-31
(Moved to Gaming and Leisure, where there are more folks on hand who might be able to help. :) )

---

### Post by justin whitaker on 2007-03-31
> **Catfish_lolipop said:**
> i need help with counterstrike. so far i have nothing downloaded because im so confused i dont know what to do first......can anybody help me?

You need Wine, Cedega, or Crossover Office. 

There is a great WINE how-to over on LinuX Gamers:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam)

Don't know how relevant it is, since it's a little old now.

I used Crossover Office to get CounterStrike Source running. It does the job quickly and quite well.

---

### Post by Catfish_lolipop on 2007-03-31
it says that i need steam, but i dont know how to download it.........

---

### Post by Iceni on 2007-04-02
Steam can be found on [www.steampowered.com](www.steampowered.com)

---

### Post by Catfish_lolipop on 2007-04-02
i have steam installed but it says that there is an error....i already tried reinstalling....maybe it is my WINE? idk...isnt there something elsei could use instead of Wine ....crossover something i think..i just want to get counterstrike to work.

---

### Post by justin whitaker on 2007-04-02
> **Catfish_lolipop said:**
> i have steam installed but it says that there is an error....i already tried reinstalling....maybe it is my WINE? idk...isnt there something elsei could use instead of Wine ....crossover something i think..i just want to get counterstrike to work.

The most common error with Steam is MSFT Fonts, followed by a missing mozilla control. It requires Tahoma, or it's equivalent, and it requires mozcontrol from transgaming. 

The appdb listing is here:

[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

There are a bunch of workarounds. 

I have CS:S up and running via Codeweaver's Crossover Office: Steam runs fine, and I just used that to install CS:S, HL2, HL, and CS. All work flawlessly. Might be worth checking out.

---

### Post by lynxus on 2007-04-05
Ive just this second managed to get CS:S running on the Ubuntu 7.04

However this is how i did it.

0) Installed Wine and configured as per norm ( Thru the wine config app ,Set OS to WindowsXP )
1) Mount my old windows drive ( the one with the installed copy already on )
2) Copied the entire Valve directory to my home directory
3) Copied the tahoma font from the mounted drive ( windows/fonts ) then pasted that into the wine Drive c folder, in its own windows fonts folder to mimmic the font.
4) Made sure beryl etc was switched off and all was running on metacity.
5) Ran the steam.exe file from the copied valve directory in my home folder.

All seemed ok, Runs fine.. Some strange issues with water textures, but thats probably due to the lack of direct x.

---

### Post by FaceLeg on 2007-04-25
Yeah you must first install Steam

Try one of these:

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam#preface](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam#preface)

[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

You then purchase your games through the Steam software.

There is a load of information on how to do it.  I have had many problems though.

Let us know how you get on!

---

### Post by Gmaster1440 on 2007-04-25
[http://ubuntuforums.org/showthread.php?t=304528](http://ubuntuforums.org/showthread.php?t=304528)

---

