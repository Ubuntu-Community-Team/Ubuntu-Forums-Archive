---
title: "Chromium Shockwave Flash Crash After Update"
date: 2011-03-08
forum: Desktop Environments
---

### Post by nshiell on 2011-03-08
After running an upgrade Chromium browser Shockwave Flash Plugin crashed!

If you have the same problem I have a workaround.

[LIST=1]
[*]firstly open Firefox goto a website that uses flash (not YouTube) I used BBC iPlayer, then right click and click on "settings..."

[*]The left most tab shows the "Enable hardware acceleration" tickbox
Untick it

[*]Then close and reopen Chromium and go back to a flash site e.g. YouTube and test it is working.
[/LIST]

The reason this worked for me is that there is a bug in either Googles Chromium or the Unix/X11 build of Shockwave Flash or my graphics card drivers

There seems to sevral bug reports regarding this on the net
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/716640](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/716640)

Flash could be a little slower now it doesn't have the hardware accelerating it. So maybe the setting could be re-enabled in the future?

---

### Post by dwpbike on 2011-03-08
tanks for the workaround.  after the youtube/google deadly embrace, doubly infuriating.  did a firefox (which i never use) update this am.  makes debian look attractive.

---

### Post by rodrigoeblanco on 2011-03-08
Thanks I have been looking up for this for so long and installing and removing things, but it worked great for me!! Thanks again!!

---

### Post by quattroman on 2011-03-08
Thanks, I had some videos crash all day, this was helpful.

---

### Post by u-lukatico on 2011-03-12
Thaks!!!!!

---

### Post by foolishdonkey on 2011-03-12
I had been trying to fix this for quite a while, and this was the only thing that worked, thanks!

---

### Post by h8uthemost on 2011-03-17
EDIT: That worked perfectly. Thank you very much for the solution.

---

### Post by enginedave on 2011-03-18
Thanks again this was bugging me for days. What a simple and effective solution. Great work.

---

### Post by Egor Tensin on 2011-03-19
Worked like charm! Thanks, this was really annoying.

---

### Post by Gazoo01 on 2011-03-20
Thank you!! Such a simple solution for such a long standing problem.=D>

---

### Post by eflix on 2011-03-20
> **dwpbike said:**
> tanks for the workaround.  after the youtube/google deadly embrace, doubly infuriating.  did a firefox (which i never use) update this am.  makes debian look attractive.

Yeah Im feeling the same here my fellow, as things are not working as they supposed to in my ubuntu box lately (samba, mysql on amarok, flash plugin, and my windows xp entry on grub has vanished). But I'll stick around the forums and find a way. Thank you nshiell for the workaround!

---

### Post by muawwiz on 2011-03-22
Thanks a lot.

---

### Post by knattlhuber on 2011-03-26
Thanks, that had been bugging me a lot lately.
On the other hand, the crashing plugin was a blessing because I wouldn't waste HOURS playing this: [http://poppit.pogo.com/hd/PoppitHD.html](http://poppit.pogo.com/hd/PoppitHD.html)
;)

---

### Post by faisalshah on 2011-10-27
Hello,

This information is for windows but you can get some information to this post.


I got you this question I am sharing some useful information about this problem.



[FONT=Calibri]1.       [/FONT]First of all you have to update your Google chrome web browser.
  [FONT=Calibri]2.       [/FONT]After updating the browser download the Registry Cleaner Software.
  [FONT=Calibri]3.       [/FONT]Disconnect the Internet connection from your computer.
  [FONT=Calibri]4.       [/FONT]Remove Adobe Flash Player to your PC.
  [FONT=Calibri]5.       [/FONT]Remove or Disable Plugin from Google Chrome web Browsers. 
  [FONT=Calibri]6.       [/FONT]Start Scan for Active-X, Flash and Registry Errors.
  [FONT=Calibri]7.       [/FONT]Install again Flash.


If you need more information please visit this article you will get more useful information to this article,: [http://ezinearticles.com/?Shockwave-Flash-Crash---Learn-Easy-Fix-For-Shockwave-Flash-Crash-in-Your-Internet-Browser&id=3994780](http://ezinearticles.com/?Shockwave-Flash-Crash---Learn-Easy-Fix-For-Shockwave-Flash-Crash-in-Your-Internet-Browser&id=3994780)

---

### Post by glenndrew on 2011-11-21
Hello,
i have been looking for this. i also faced this problem many times but after reading this article i fixed it. Thanks for sharing this post. i also got some help from this article   [http://ezinearticles.com/?Chrome-Shockwave-Flash-Crash---Fix-Shockwave-Flash-Crash-in-Chrome-Browser-to-Smoothly-Play-Videos&id=4002309](http://ezinearticles.com/?Chrome-Shockwave-Flash-Crash---Fix-Shockwave-Flash-Crash-in-Chrome-Browser-to-Smoothly-Play-Videos&id=4002309)
   , hope someone might get help from this article.

---

### Post by NMeyne on 2012-04-04
Hi,

Sadly I can't seem to get this fix to work because firefox seems to have a similar problem - using Lubuntu.  I have reinstalled all of Lubuntu and Chromium afresh, and installed Firefox to see if i could get the fix to work, but the flash seems to refuses to load in firefox (no errors - just unresponsive - so no chance to set / reset any switches).  I have tried this on two different machines - both older athlon / sempron processors.

Help - looks like I will have to give up on this distro  and Chromium  - any suggestions of alternative lightweight free distros that might work?

Regards,

Nick

---

### Post by CTolley on 2012-04-21
Worked for me as well.  Many thanks

10.10 Maverick
32bit system
ASUS laptop

---

### Post by meduser on 2012-05-10
> **nshiell said:**
> After running an upgrade Chromium browser Shockwave Flash Plugin crashed!

If you have the same problem I have a workaround.

[LIST=1]
[*]firstly open Firefox goto a website that uses flash (not YouTube) I used BBC iPlayer, then right click and click on "settings..."

[*]The left most tab shows the "Enable hardware acceleration" tickbox
Untick it

[*]Then close and reopen Chromium and go back to a flash site e.g. YouTube and test it is working.
[/LIST]

The reason this worked for me is that there is a bug in either Googles Chromium or the Unix/X11 build of Shockwave Flash or my graphics card drivers

There seems to sevral bug reports regarding this on the net
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/716640](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/716640)

Flash could be a little slower now it doesn't have the hardware accelerating it. So maybe the setting could be re-enabled in the future?

When I try that, I get to the hardware acceleration tag, but the I can not unclick it....?

---

### Post by Kossilar on 2012-05-11
> When I try that, I get to the hardware acceleration tag, but the I can not unclick it....?


I'm having the same problem.

---

### Post by Blackhood on 2012-05-25
> **nshiell said:**
> After running an upgrade Chromium browser Shockwave Flash Plugin crashed!

If you have the same problem I have a workaround.

[LIST=1]
[*]firstly open Firefox goto a website that uses flash (not YouTube) I used BBC iPlayer, then right click and click on "settings..."

[*]The left most tab shows the "Enable hardware acceleration" tickbox
Untick it

[*]Then close and reopen Chromium and go back to a flash site e.g. YouTube and test it is working.
[/LIST]

The reason this worked for me is that there is a bug in either Googles Chromium or the Unix/X11 build of Shockwave Flash or my graphics card drivers

There seems to sevral bug reports regarding this on the net
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/716640](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/716640)

Flash could be a little slower now it doesn't have the hardware accelerating it. So maybe the setting could be re-enabled in the future?


Where am I supposed to right click?  I keep getting the standard menu as if I just right click in a web page.

---

