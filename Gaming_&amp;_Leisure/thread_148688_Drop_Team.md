---
title: "Drop Team"
date: 2006-03-22
forum: Gaming &amp; Leisure
---

### Post by KingBahamut on 2006-03-22
Has anyone toyed with the Demo for this game yet? 

Im interested, would be cough up the extra change for it , if it truely does play as good as it looks. 

[http://www.battlefront.com/products/dropteam/](http://www.battlefront.com/products/dropteam/)

---

### Post by Perfect Storm on 2006-03-22
I was thinking to tinkering with it this weekend. It looks good the description and the screenshots.

Added to the gamelist 4 days ago: [http://doc.gwos.org/index.php/DropTeam](http://doc.gwos.org/index.php/DropTeam)

---

### Post by KingBahamut on 2006-03-22
yeah, me too. Need a fairly high end card to play it though. Are they going to do a box release, or an electronic one?

---

### Post by Perfect Storm on 2006-03-22
My new nvidia 6600 GT 256mb should handle it 8) :mrgreen:

As  understands it it's box version they gonna ship, but I hope later that they make a download version.

Edit: found it
> &#8226; Game runs on Windows 98, Windows ME, Windows 2000, Windows XP, Windows Server 2003, Linux, and Mac OS-X. Game ships with all versions together and each game version is fully compatible with the others.

---

### Post by charlieg on 2006-03-22
Apparently it suffers from almost-unplayable lag.  Still, it looks very promising.

---

### Post by akiro.yamamoto on 2006-03-22
I think I'll give it a try later today..... ;)
It looks pretty interesting.

---

### Post by Silwenae on 2006-03-22
I've been playing with it off and on for a few days.  I haven't experienced any lag at all, and I'm on a normal cable connection.

It's cool - steep learning curve, but cool.

---

### Post by MaX on 2006-12-12
I get libDemeter.so is missing? 
How did you guys fix that?

(Using the demo)

---

### Post by earobinson on 2006-12-12
looks kinda cool ... if i was a gamer

---

### Post by randell6564 on 2007-04-11
> **KingBahamut said:**
> Has anyone toyed with the Demo for this game yet? 

Im interested, would be cough up the extra change for it , if it truely does play as good as it looks. 

[http://www.battlefront.com/products/dropteam/](http://www.battlefront.com/products/dropteam/)

I bought the game and have only played it in Windows XP.  It's fun, though it has some server issues (depending on what part of the world that you live in)  It's completely modifiable, and actually the Mods are much more fun than the original creation!

Definately worth the money!  Good community of DT gurus, and tech support.

My issue at this time is getting it installed on Ubuntu Dapper Drake.  Have finally got my Ubuntu back and forgot a lot of stuff!  Oh, and BTW., I'm using a Readon 9200 graphics card, and it works fine with that.

---

### Post by Perfect Storm on 2007-04-12
If you can wait (later today), I can fetch howto together. The bad news is I can only test it in edgy.

---

### Post by randell6564 on 2007-04-12
> **Artificial Intelligence said:**
> If you can wait (later today), I can fetch howto together. The bad news is I can only test it in edgy.
No problem my friend!  I'm sure the method used to install it is the same.  I've been trying to google a how-to, but can't seem to find what I'm looking for.

I also just emailed the DropTeam tech support.  If I get something before you, I'll be sure and post it.

Cheers!

---

### Post by Perfect Storm on 2007-04-12
Here it is: [http://gaming.gwos.org/e107_plugins/content/content.php?content.67](http://gaming.gwos.org/e107_plugins/content/content.php?content.67)


:popcorn:

---

### Post by randell6564 on 2007-04-12
> **Artificial Intelligence said:**
> Here it is: [http://gaming.gwos.org/e107_plugins/content/content.php?content.67](http://gaming.gwos.org/e107_plugins/content/content.php?content.67)


:popcorn:
Thank you very much!  I'm actually trying to get it installed from the DropTeam Cd that I purchased. 
When I pop the CD in, I just get a browser window, showing all the files.  I'm sure that all I need to do is 'cd' to my cdrom and run the 'runLinuxInstall', but I can't remember how to 'cd' to my cdrom from the terminal! :P

It's been a while since I've used Ubuntu because I moved and could not get it back online.  So I was forced to install Windows on my other drive.  Now that I have my Ubuntu back, I can't remember how to do anything!

---

### Post by zekopeko on 2007-04-12
open terminal and type:

cd /media/cdrom

TAB for autocompletion, sudo if the script requires it.

---

### Post by randell6564 on 2007-04-12
> **zekopeko said:**
> open terminal and type:

cd /media/cdrom

TAB for autocompletion, sudo if the script requires it.
Thanks zekopeko!
Heres what I keep getting:
```
bigboss@room224:~$ cd ~/media/cdrom
bash: cd: /home/bigboss/media/cdrom: No such file or directory
bigboss@room224:~$ cd /media/cdrom
bigboss@room224:/media/cdrom$ sh runLinuxInstall
runLinuxInstall: line 3: ./InstallData/bin/LinuxInstall: Permission denied
bigboss@room224:/media/cdrom$ sudo sh runLinuxInstall
runLinuxInstall: line 3: ./InstallData/bin/LinuxInstall: Permission denied
bigboss@room224:/media/cdrom$
```
I know that I'm doing something wrong, but I have to step out for a bit.  I'll be back in a while.  Thanks again!

---

### Post by Perfect Storm on 2007-04-12
Ah, the howto was made for download installer in mind (That's the version I have).

```
cd ~/Desktop
mkdir DropTeamSetup
cd /media/cdrom
cp -r * ~/Desktop/DropTeamSetup
cd ~/Desktop/DropTeamSetup
chmod +x DropTeamSetup
sh runLinuxInstall
cd && mkdir .Games
mv DropTeam .Games
```

Instead of 

```
cd ~/Desktop
unzip -o DropTeamSetup.zip
cd DropTeamSetup
sh runLinuxInstall
cd && mkdir .Games
mv DropTeam .Games
```


(Do not install this game with root permission, it's not build to handle global installation).

and then continue the howto guide.

---

### Post by randell6564 on 2007-04-13
> **Artificial Intelligence said:**
> Ah, the howto was made for download installer in mind (That's the version I have).

```
cd ~/Desktop
mkdir DropTeamSetup
cd /media/cdrom
cp -r * ~/Desktop/DropTeamSetup
cd ~/Desktop/DropTeamSetup
chmod +x DropTeamSetup
sh runLinuxInstall
cd && mkdir .Games mv DropTeam .Games
```
(Do not install this game with root permission, it's not build to handle global installation).
Thank you!  Well everything went well until I got to the chmod part:
> bigboss@room224:~/Desktop/DropTeamSetup$ chmod +x DropTeamSetup
chmod: cannot access 'DropTeamSetup' : No such file or directory
Strange to me.  Didn't we just create a DropTeamSetup directory?  There is now one on my desktop!
Anyway, I skipped that and ran 'sh runLinuxInstall' and I think it worked because a window popped up with the license agreement mumbo-jumbo.

---

### Post by Perfect Storm on 2007-04-13
meh, It's a typo...sorry

```
chmod +x runLinuxInstall
```

---

### Post by randell6564 on 2007-04-13
> **Artificial Intelligence said:**
> meh, It's a typo...sorry

```
chmod +x runLinuxInstall
```
AAAlright!  No problem.  Your directions worked beautifully!

Thanks again my friend!

---

### Post by randell6564 on 2007-04-13
Ok..,as I said 'Artificial Intelligence', everything worked!  Everything that YOU provided.  
The [Ubuntu Gamers Arena ]("http://gaming.gwos.org/e107_plugins/content/content.php?content.67")on the other hand, goofed up the part concerning the DT Icons.
"```
Launcher:


Copy this Icon to your Desktop;
Code:

cd ~/Desktop
mv DropTeam.png ~/.Games/DropTeam
nano ~/.Games/DropTeam/StartDropTeam.sh
Add the following;


#!/bin/bash

cd ~/.Games/DropTeam
./runClient.sh


Save [ctrl]+[o] and exit [ctrl]+[x].


Next;


Code:

chmod +x ~/.Games/DropTeam/StartDropTeam.sh
alacarte
Go to the Game section in Alacarte and push the New Item button. Fill in;


Name: DropTeam
Comment: FPS/TPS Tactical game.
Command: sh /home/***USERNAME***/.Games/DropTeam/StartDropTeam.sh


Icon: ~/.Games/DropTeam/DropTeam.png



Save and exit. When done;
```
This part didn't work.  It's THERE in Applications>Games, but it's not the Icon.
It is not a big deal (To ME anyway) because the game works!  Just thought that I should post it though.

---

### Post by Perfect Storm on 2007-04-14
The icon isn't there? Then I need to fix it ;)

---

### Post by randell6564 on 2007-04-14
> **Artificial Intelligence said:**
> The icon isn't there? Then I need to fix it ;)
Well.., I copied it to my desktop, and it dissappeared when I did the 'mv' part (don't really know where it went.  Don't really know where ANY of it went after the move from desktop. Game included!)

Like I said though, the game starts from 'Applications>Games'.

---

### Post by Perfect Storm on 2007-04-14
It's moved to a hidden folder in your home folder. (**./Games**) so check when setting up the menu link. The command as I describe (**~/.Games/DropTeam/DropTeam.png**) Should take care of the icon issue.

---

### Post by randell6564 on 2007-04-14
> **Artificial Intelligence said:**
> It's moved to a hidden folder in your home folder. (**./Games**) so check when setting up the menu link. The command as I describe (**~/.Games/DropTeam/DropTeam.png**) Should take care of the icon issue.
Hello.  
Once I open Alacarte, select Games, and enter >  DropTeam
 FPS/TPS Tactical game. sh /home/bigboss/.Games/DropTeam/StartDropTeam.sh I get stuck at the>  ~/.Games/DropTeam/DropTeam.png
Check out the screenshot.  There is no where to enter the above command, so I can't complete the icon part.
I know it's me! :confused:   Please bare with me my friend.

---

### Post by Perfect Storm on 2007-04-14
You need to click the icon button first.

---

### Post by randell6564 on 2007-04-14
> **Artificial Intelligence said:**
> You need to click the icon button first.
Yes..,I did all of this. there is still nowhere to enter```
~/.Games/DropTeam/DropTeam.png
```
See screenshot please.

---

### Post by Perfect Storm on 2007-04-14
Ah, I see you run Dapper. Try when hitting the change icon button, then afterwards <ctrl> + <L>

---

### Post by randell6564 on 2007-04-14
> **Artificial Intelligence said:**
> Ah, I see you run Dapper. Try when hitting the change icon button, then afterwards <ctrl> + <L>
I'm sorry! I thought that[ I mentioned I was running Dapper Drake.]("http://ubuntuforums.org/showpost.php?p=2438700&postcount=10"). :D 
I'll give it a shot.  Thanks Man!!  You have been a HUGE help!!

---

### Post by randell6564 on 2007-04-14
Ok..,I feel REALLY Fricken stupid!
After clicking on the icon button, all I had to do was enter```
~/.Games/DropTeam/DropTeam.png
```in the form box, and 'BADA BING, BADA BOOM'! It's now there!

Sorry man!  But I DID add the disclaimer to my OP that I "forgot how to do anything"!
:) 
Thank you 'Artificial Intelligence'!  You are officially OFF-the-HOOK!:popcorn:

---

