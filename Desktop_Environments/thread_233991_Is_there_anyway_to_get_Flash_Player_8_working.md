---
title: "Is there anyway to get Flash Player 8 working?"
date: 2006-08-10
forum: Desktop Environments
---

### Post by rippon on 2006-08-10
Is there any way to get Flash 8 working. I get flak everytime they click the link to open the video off Comcast.net, and it says it needs flash player 8.
Last time I checked there wasn't any solution to it. Is there a way now?

---

### Post by Jagot on 2006-08-10
[http://www.howtoforge.com/ubuntu_flash_player](http://www.howtoforge.com/ubuntu_flash_player)

---

### Post by visik7 on 2006-08-10
right now the only way is to run firefox with wine

---

### Post by chocbar31 on 2006-08-10
Also, try ies4linux (Internet Explorer for Linux). It runs much faster and smoother and faster on my machine than firefox, using wine.

Try them both though. You can get ies4linux here:
[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

### Post by Jagot on 2006-08-11
> **chocbar31 said:**
> Also, try ies4linux (Internet Explorer for Linux).

But that then exposes you to the well documented inherent insecurity and general crappiness of IE.

---

### Post by rippon on 2006-08-11
Thanks, they aren't exactly the best solution, I wish adobe/macromedia would make a linux compatible flash8, or sites would let flash7 somehow still work. It pisses me off how everyone assumes that everyone else runs Windows XP or other Microsoft viruses.... I mean software.

Suddenly Ubuntu is much harder to use, "if you want to watch the flash 8 stuff open this browser, for normal web surfing use this browser."

Thanks for your help though, It just isn't fair how flash8 (non)support isn't Ubuntu's or Linux's fault, yet of course they are the ones who suffer most from it (both image wise and functionality wise).

Thanks again.

---

### Post by AlanV on 2006-08-11
Thanks chocbar31 for the tip on ies4linux. Works well on Dapper x64.

---

### Post by chajuram on 2006-09-02
Yes, I wish there was a non-wine version.

---

### Post by Anduu on 2006-09-03
> **rippon said:**
> Thanks, they aren't exactly the best solution, I wish adobe/macromedia would make a linux compatible flash8, or sites would let flash7 somehow still work. It pisses me off how everyone assumes that everyone else runs Windows XP or other Microsoft viruses.... I mean software.

Suddenly Ubuntu is much harder to use, "if you want to watch the flash 8 stuff open this browser, for normal web surfing use this browser."

Thanks for your help though, It just isn't fair how flash8 (non)support isn't Ubuntu's or Linux's fault, yet of course they are the ones who suffer most from it (both image wise and functionality wise).

Thanks again.

Patience Grasshopper...A linux version of Flash 9 is in the works and is making great progress.

They are speculating on an early 2007 release but I wouldn't be suprised to see a beta much sooner than that given how well things are going.

---

### Post by someguyouknow on 2006-09-03
There is a way you can "trick" some sites into thinking you have flash 9.
Its very simple but i forgot the link to it but its on digg.com.
i havent done it yet though so i cant say whether it will work or not.

---

### Post by deanlinkous on 2006-09-03
[http://www.ubuntuforums.org/showthread.php?t=210945&page=3](http://www.ubuntuforums.org/showthread.php?t=210945&page=3)

Open the file ~/.mozilla/firefox/pluginreg.dat
change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$

This gets past the "check" for the version but of course does not help if they are using newer features than 7 provides.

Works for a good number of sites, my kids games sites...

Looks like someone else has been credited for my little hack... :(

---

