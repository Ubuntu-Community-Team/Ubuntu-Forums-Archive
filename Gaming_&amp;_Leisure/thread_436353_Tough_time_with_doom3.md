---
title: "Tough time with doom3"
date: 2007-05-07
forum: Gaming &amp; Leisure
---

### Post by LaidbackBill on 2007-05-07
I recently got my 3-d working and tought I would check out the results with a copy of Doom # I have.  I know my 3-d is working as beryl works.  I have the directories installed and I think I have the pk4 files installed but for the life of me I can't get the installer to work.  The error message is it can't open  "doom3-linux-1.3.1302.x86.run", any help would be aprreciated.

---

### Post by dorath on 2007-05-07
It took me quite a while to discover that what I actually needed to type to install Doom 3 was: ```
sudo sh doom3-linux-1.3.1302.x86.run
```

:(

---

### Post by LaidbackBill on 2007-05-07
That's the installer I used and the "error" is in my first post.  I turned off beryl and used the commands from "installing Doom 3- Linux questions".  I got the directories installed and the pak files but the installer gives the above error when I put it in the terminal.  Anyone else have a solution. 
Thanks

---

### Post by noerrorsfound on 2007-05-07
You must make it executable:
```
chmod +x ./doom3-linux-1.3.1302.x86.run
```
That will work if the installer is in your home folder (/home/youruser).

If it's on your desktop, first type this (case sensitive):
```
cd ~/Desktop
```

Then run the above command.

After making it executable you can then run it
```
sudo sh ./doom3-linux-1.3.1302.x86.run
```

---

### Post by LaidbackBill on 2007-05-07
O.K., you're saying make the doom run file executible then run the installer.  The file is on the cdrom I can assume unless its one of the pak files because those are the only files I have from doom.  Anyway I give it a try and report back tomorrow.

Thanks.

---

### Post by LaidbackBill on 2007-05-07
Actually I just looked at your post again and the files are in usr/local/games etc.  But I'll give it a try.  More than one way to skin a cat.

Bill

---

### Post by LaidbackBill on 2007-05-08
Well I've spent the last two hours trying every combination to get to the doom run file but to no avail.  I must be missing something simmmmmple here but for the life of me I can't seem to find it.  No matter what directory I'm in I get the same "cannot open doom3.....run.  I tried a search of the files and can"t find it either on the cdrom or in the doom directory, or anywhere.  I guess I'll have to try another day after the frustration wanes.

Bill

---

### Post by noerrorsfound on 2007-05-08
> **LaidbackBill said:**
> O.K., you're saying make the doom run file executible then run the installer.  The file is on the cdrom I can assume unless its one of the pak files because those are the only files I have from doom.  Anyway I give it a try and report back tomorrow.

Thanks.
> **LaidbackBill said:**
> Well I've spent the last two hours trying every combination to get to the doom run file but to no avail.  I must be missing something simmmmmple here but for the life of me I can't seem to find it.  No matter what directory I'm in I get the same "cannot open doom3.....run.  I tried a search of the files and can"t find it either on the cdrom or in the doom directory, or anywhere.  I guess I'll have to try another day after the frustration wanes.

Bill
I'm now slightly confused. I assumed you wanted to run the Doom 3 installer that can be downloaded from [ftp://ftp.idsoftware.com/idstuff/doom3/linux]("ftp://ftp.idsoftware.com/idstuff/doom3/linux").

The steps I gave you were how to make that file executable and then run it. But to my knowledge the Linux installer is not provided on the CD, unless you bought from Tuxgames.com because they apparently include the installer on a separate CD.

Installing Doom 3 from start to finish should be like this:
1. Download installer
2. Chmod installer  to make it executable
3. Run installer
4. Copy pak000.pk4, pak001.pk4, pak002.pk4, pak003.pk4, and pak004.pk4 to /**Doom3-Install-Directory**/base (usually /usr/local/games/doom3/base)

--
There's also the option of using the Loki installer which has a GUI (which the official Doom 3 Linux installer doesn't have) and should automatically copy the pk3 files to the correct directory during the install process: [http://liflg.org/?what=dl&catid=6&gameid=48&filename=doom3_1.3.1.1304-multilanguage.run](http://liflg.org/?what=dl&catid=6&gameid=48&filename=doom3_1.3.1.1304-multilanguage.run)

---

### Post by Sockerdrickan on 2007-05-08
I don't have to chmod it

---

### Post by noerrorsfound on 2007-05-08
> **Tux0r said:**
> I don't have to chmod it
I'm talking about the installer file (ends in .run) and not the game executable.

---

### Post by LaidbackBill on 2007-05-09
> **noerrorsfound said:**
> I'm now slightly confused. I assumed you wanted to run the Doom 3 installer that can be downloaded from [ftp://ftp.idsoftware.com/idstuff/doom3/linux]("ftp://ftp.idsoftware.com/idstuff/doom3/linux").

The steps I gave you were how to make that file executable and then run it. But to my knowledge the Linux installer is not provided on the CD, unless you bought from Tuxgames.com because they apparently include the installer on a separate CD.

Installing Doom 3 from start to finish should be like this:
1. Download installer
2. Chmod installer  to make it executable
3. Run installer
4. Copy pak000.pk4, pak001.pk4, pak002.pk4, pak003.pk4, and pak004.pk4 to /**Doom3-Install-Directory**/base (usually /usr/local/games/doom3/base)

--
There's also the option of using the Loki installer which has a GUI (which the official Doom 3 Linux installer doesn't have) and should automatically copy the pk3 files to the correct directory during the install process: [http://liflg.org/?what=dl&catid=6&gameid=48&filename=doom3_1.3.1.1304-multilanguage.run](http://liflg.org/?what=dl&catid=6&gameid=48&filename=doom3_1.3.1.1304-multilanguage.run)

Well I'm back again I want to thank you for your patience and for the links.  The installer was and is my problem.  I know it's stupid of me for not downloading the installer from Id's webpage but for some reason I missed that part of the instructions.  I just downloaded the installer "doom3-linux-1.3.1.1304.x86.run", took about two hours(only have dial-up), it was the only one that looked like it was close to the one that has been listed.  But after dwnlding it ,according to Firefox it goes to the desktop,but it wasn't there and again I couldn't find it anywhere.  Don't know what happened to it.  Anyway I have your instructions so when and if I find the installer I'll try again.

Thanks again
Bill

---

### Post by noerrorsfound on 2007-05-09
> **LaidbackBill said:**
> Well I'm back again I want to thank you for your patience and for the links.  The installer was and is my problem.  I know it's stupid of me for not downloading the installer from Id's webpage but for some reason I missed that part of the instructions.  I just downloaded the installer "doom3-linux-1.3.1.1304.x86.run", took about two hours(only have dial-up), it was the only one that looked like it was close to the one that has been listed.  But after dwnlding it ,according to Firefox it goes to the desktop,but it wasn't there and again I couldn't find it anywhere.  Don't know what happened to it.  Anyway I have your instructions so when and if I find the installer I'll try again.

Thanks again
Bill
Perhaps you selected *Open with* by accident on the save dialog instead of *Save to*. I have done that myself a few times because Firefox will select "Open with" by default for certain filetypes. You could also try searching for it by going to Places => Search for Files... and searching for *doom3*.

---

### Post by LaidbackBill on 2007-05-10
Finally, dwnlded from the second link, had to do twice as the first time it didn't finish loading, 4 1/2 hours, WOW.  After the second dwnld finished it was a piece of cake.  Followed noerrors found instructions, setup the game and everything works fine so far.  Not too impressed with the graphics, seems like it was better in windows, but it does play, and that was all I was looking for.  Thanks again for holding a noobies hand and for your time.  Resolved.

Bill

---

