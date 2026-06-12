---
title: "Baldur's Gate 2 and Wine"
date: 2006-02-28
forum: Gaming &amp; Leisure
---

### Post by remick182 on 2006-02-28
I'm trying to get Baldur's Gate 2 to run under Wine, and I'm having an issue with loading the maps.  According to the WineHQ site, you need to install it under windows, copy the installation over to your linux partition under the drive_c folder (or whatever you've named it) and it should run fine.

Well, it does up to a point.  So far, it runs the movies, goes through the entire character creation screen with sound and music working great, but once it tries to load a map, it locks up.  At first, it wasn't finding the CD directory (I've copied all cd's and edited the baldur.ini file to locate them under my BGII directory - the actual CD is in the drive too) but after editing the .ini file a couple of times, it was able to target the correct folder.  Now I get the loading screen, but nothing happens.  I don't see any errors in the terminal either.  :???: 

I then tried to copy over some old saved games and load those up directly, and I thought I was golden because I got about 30% loaded, then it too froze up.  What's up?  :confused: 

I noticed that copying over the installation caused every file and folder to not have the write ability.  I used chmod on a couple folders and the baldur.ini file to make changes, but might my problem be caused by the lack of write permissions to other files/folders?  If so, how do I chmod everything w/o having to hit every single file/folder individually?

---

### Post by wr0x2 on 2006-02-28
I don't have an answer for you, but was anything beyond copying the BGII folder to drive_c necessary to get it to the main screen? Also, I'm guessing you're using a cd crack, which one?

---

### Post by remick182 on 2006-02-28
[I]> by Anonymous on Thursday November 18th 2004, 8:14
 
BG2 working with wine 20040716 

I copied the bg2 installation I had on a windows partition I was about to remove over to my home directory. I then copied the contents of the bg2 cds to my harddrive and altered my baldur.ini to point at them. 

To play I have to mount cd2 and then simply do wine BGMain.exe from the commandline. I'd guess that a no-cd crack would eliminate the need to have the cd mounted but I couldn't find a patch & crack combination for the same version of BG2[/I]

This was the only info posted on the WineHQ site in regards to this game.  There are a few no-cd cracked .exe's available for download, but I'm not sure if I need them.  When I installed Planescape: Torment, the game ran fine w/o any cracked .exe file.

I did download a no-cd crack and tried to apply it in wine, but I got an error as soon as I tried to play BG2 that said I cannot play BG2 w/o a cd rom installed, so unless I have to do something special with the patch, it doesn't work in my current setup.

---

### Post by remick182 on 2006-02-28
I think I've solved part of my problem.

After some research, I found that by typing:

sudo chmod -R a+w /(BGdir)

I was given WRITE permissions on all files and subdirectories.  From there, the maps loaded right up.

Now I've experienced another issue.  I haven't done too much experimenting yet, but it seems like whenever one of my PC's die, the game crashes.  I'm hoping there is an option to keep this from happening, otherwise I'll just have to try REALLY hard not to die...hehehe.:D

---

### Post by wr0x2 on 2006-03-01
OK, I got home and I tried running BGII.. I placed the entire dir in my drive_c folder, and I made everything writable, but it crashes. When I run baldur.exe, the launcher loads but it doesn't give an option to play, only to install. Is there a "registry" in wine that I will have to edit? I want to help out here but I have to get BG working first :-p.

---

### Post by remick182 on 2006-03-01
Ok.  The first thing you need to do is run _BGMain.exe_, not _baldur.exe_.  I ran into the same problem with the baldur.exe only giving me the install option.  If you run _BGMain.exe _you should be good to go.  Also, if you don't get the intro movies, you'll need to edit the baldur.ini file to direct it to look further into the CD2 folder.  Mine looked like this:

**.../BGII-SoA/CD2/**

but I had to change it to look like:

.**../BGII-SoA/CD2/cdrom0/CD2/**

because of the way the disc got copied.

Try that out and see what you get.

---

