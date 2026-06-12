---
title: "Help!! Total Newbie!!"
date: 2005-09-21
forum: Desktop Environments
---

### Post by uthfull on 2005-09-21
I'm not sure if I'm in the right forum but neways I need help !
I'm not a pro. Actually I don't even know a single thing bout how linux works
I ordered for the free Ubuntu cds n got em yesterday.

Installation was fine.
I have a 80GB HDD with 4 partitions C, D, E, F n WinXP
WinXp is on C.

Now, I installed Ubuntu on D.
When I open WinXp... which is on C.........it doesnt show D anymore.
Now if I'm in Xp n I want to move files into D:, will it not be possible since the partition file systems r different??

Besides that..... I can't figure out how to run Ubuntu properly.
Firstly, the resolution is 640x480. I can't change it even in the settings. I keep clicking on the arrows n they display nuthin else.
I got an LG Studioworks520Si monitor.
Also, How do I see the files of my other partitions in Linux.

I access net through a LAN based ISP.
I configured my LAN card properly, got to the ISP download site n downloaded the dialer for linux.
I extracted the tar.gz archive on he desktop in a folder named sify. It has a bin file. When i double click on it it shows some more files. It has a readme... but I can't figure out how to install thru the install.sh file.
```
http://202.144.65.70:8090/downloaddialer.php
```
Please can sum1 help me configure the Linux Client for my ISP.

Now how do I install the dialer n then how n frm where do I open it post installation.

Also, if sum1 cud tell me sum basics of Linux.... it wud b of gr8 help. 

I had once tried RedHat... but it wuz too darn complicated for me.... din even let me play my mp3s.

I desperately need to make this work!!
PLEASE HELP!!

---

### Post by mlomker on 2005-09-21
> When I open WinXp... which is on C.........it doesnt show D anymore.


True, Windows cannot see linux.

There's no problem being new, but the better the questions that you ask the more likely that you'll get the right answer.  Doing a search and reading through the [Ubuntu Guide](http://www.frankandjacq.com/ubuntuguide/5.04/index.html) first is always a good bet.

> 
Firstly, the resolution is 640x480. I can't change it even in the settings. I keep clicking on the arrows n they display nuthin else.


Your monitor probably isn't the problem.  You'll have to figure out what video card is in your machine and get the proper driver working.  **lspci** will list most of the hardware in your machine and tell you what kind of video card it is.  However, it's a lot easier to check that stuff out in Windows and write it down.  The **sudo dpkg-reconfigure xserver-xorg** command allows you to reconfigure the driver being used by answer some questions.

> install thru the install.sh file.

Usually you'd change to the directory in a terminal and type **sudo sh install.sh**.

I'm not sure why you'd need a dialer to connect to an ISP over Ethernet.  Do you know if your router requires PPOE?  That can be a bit more challenging.

> 
I had once tried RedHat... but it wuz too darn complicated for me.... din even let me play my mp3s.


I know that others on here will disagree with me, but linux is a lot more difficult than Windows.  If you have a desire to learn linux for career reasons then that's a good reason, but I think most people are better off with Windows.

---

### Post by uthfull on 2005-09-22
[QUOTE=mlomker]True, Windows cannot see linux.

There's no problem being new, but the better the questions that you ask the more likely that you'll get the right answer.  Doing a search and reading through the [Ubuntu Guide](http://www.frankandjacq.com/ubuntuguide/5.04/index.html) first is always a good bet.



Your monitor probably isn't the problem.  You'll have to figure out what video card is in your machine and get the proper driver working.  **lspci** will list most of the hardware in your machine and tell you what kind of video card it is.  However, it's a lot easier to check that stuff out in Windows and write it down.  The **sudo dpkg-reconfigure xserver-xorg** command allows you to reconfigure the driver being used by answer some questions.



Usually you'd change to the directory in a terminal and type **sudo sh install.sh**.

I'm not sure why you'd need a dialer to connect to an ISP over Ethernet.  Do you know if your router requires PPOE?  That can be a bit more challenging.



I know that others on here will disagree with me, but linux is a lot more difficult than Windows.  If you have a desire to learn linux for career reasons then that's a good reason, but I think most people are better off with Windows.[/QUOTE]
 Thx

got to a max resolution of 800x600 tho after going thru the same procedure 5-6 times. I used to restart but it still showed the same resolution options.

But then suddenly when after some time I checked..... it showed 2 options for resolution but now only one option... i.e. 85Hz for refresh rate.

How do I get 60....?

Also the command which u told me... is this for configuring the whole OS?? Cuz after I configured my card.... it went onto keyboard then mouse. I closed it in between.

---

### Post by mlomker on 2005-09-22
> 
How do I get 60....?

Also the command which u told me... is this for configuring the whole OS?? Cuz after I configured my card.... it went onto keyboard then mouse. I closed it in between.

It configures your graphical environment.  Why would you want to lower the refresh rate?

---

### Post by uthfull on 2005-09-22
[QUOTE=mlomker]It configures your graphical environment.  Why would you want to lower the refresh rate?[/QUOTE]
 The last post I had made wuz thru XP. 
Now that I have finally been able to access the net thru Ubuntu... I am posting thru it. The problems back again..... resolution back at 640x480 and no options available.

Forget the refresh rate mlomker... what I need to fix is the resolution.... i basically need just two options 800x600 n 1024x768.

---

### Post by DeadEyes on 2005-09-22
> 
Now, I installed Ubuntu on D.
When I open WinXp... which is on C.........it doesnt show D anymore.
Now if I'm in Xp n I want to move files into D:, will it not be possible since the partition file systems r different??a


the guide that mlomker pointed out will show you how to read files from windows in linux i.e. mounting the ntfs partition. If you want to go the other way there is a program called explore2fs available [here](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) 

Altough probably the best way to share between the two is to create a FAT partition, that way linux and windows can both read and write to it

---

### Post by mlomker on 2005-09-22
> Forget the refresh rate mlomker... what I need to fix is the resolution.... i basically need just two options 800x600 n 1024x768.

Then why don't you run the reconfigure like I suggested?  If you're not sure on an answer then just take the default setting--it reads the settings from your current file.

---

### Post by professor_chaos on 2005-09-22
Resolutions, resolutions, everyone problems with resolutions.

Man, I sure hope strides are made in making configuring and debuging resolution issues are made to really make Ubuntu a great desktop OS. 

If you search the forum uthfull, for "resolution" your going to find lots of answers regarding resolution issues like to one your having.

But, I suggest you find out....
1.) Your target resolution you want (I would assume this is your highest res supported by the monitor).
2.) Then find the highest matching refresh rate for that resolution. Sometimes, at the highest capable resolution, you may have to lower the refresh rate.)
3.) Also find out your monitors supported Vertical and Horizontal Refresh rates.

4.) Then just edit the /etc/X11/xorg.conf by entering all those values. First make a copy ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` Then edit the file ```
sudo gedit /etc/X11/xorg.conf 
```And then restart your graphical server (ctrl+alt+backspace)

or "dpkg-reconfigure xserver-xorg" and go thru the steps making sure you select only the resolutions you want (making sure they are supported) and try selection "Advanced" when configuring horizontal and vertical refresh rates and enter the maufactures refresh range values.

Good Luck.

---

### Post by Velox Letum on 2005-09-23
Note that Xorg is not Ubuntu, but a seperate project that Ubuntu uses, as it is with almost all Linux distros. In sudo dpkg-reconfigure xserver-xorg did you select the resolutions you wanted? You have to hit the space bar to make [ ] into [X] next to the resolution(s) you want. 

Linux is difficult at times, but I recommend it far over Windows.

---

### Post by uthfull on 2005-09-23
[QUOTE=Velox Letum]Note that Xorg is not Ubuntu, but a seperate project that Ubuntu uses, as it is with almost all Linux distros. In sudo dpkg-reconfigure xserver-xorg did you select the resolutions you wanted? You have to hit the space bar to make [ ] into [X] next to the resolution(s) you want. 

Linux is difficult at times, but I recommend it far over Windows.[/QUOTE]
 Velox Lectum... I typed that cmd but only got some questions bout my graphics card n nuthin more... no resolutions to choose. Though I'll try professor_chaos's procedure n let u guys know.

Thx everybody.... this community's gr8!!

---

### Post by uthfull on 2005-09-23
[QUOTE=uthfull]Velox Lectum... I typed that cmd but only got some questions bout my graphics card n nuthin more... no resolutions to choose. Though I'll try professor_chaos's procedure n let u guys know.

Thx everybody.... this community's gr8!![/QUOTE]
 OK I tried Pro_chaos's steps... but I don't get those questions regarding resolutions n no such advanced or simple options when I type "dpkg-reconfigure xserver-xorg"

I manually set the V & H refresh rates in xorg.conf. 
My display was flickering from left to right... It stopped for sumtime.... but nw its started flickerin again.

Resolutions I get now r 640x480, 800x600, 1024x768.
When i select the last option.... the screen increases in both height n width although everything remains same as in 800x600. I have to drag my cursor to the ends of the screen to view properly.

---

### Post by mlomker on 2005-09-23
> When i select the last option.... the screen increases in both height n width although everything remains same as in 800x600. I have to drag my cursor to the ends of the screen to view properly.

You need to adjust your monitor.  There should be some buttons on the front that you can push to adjust the size and placement of the picture.  If you have the manual for your monitor it'll make that easier to figure out.

---

### Post by uthfull on 2005-09-23
OK damnsilly of me not to think bout that.
Will do that.

But the fonts n colors r not crisp. N the flickering of display persists.

---

### Post by mlomker on 2005-09-23
> But the fonts n colors r not crisp. N the flickering of display persists.

That's where things get complicated.  The monitor, the videocard, and the driver can all place limits on how high of a *refresh rate* is permitted.  Usually the higher the resolution the lower the refresh rate becomes.

There is something called a **modeline** that you can use to force the system to use a specific resolution and refresh rate but it's really tricky to get working.

It's possible that there's an information menu in your monitor menus that'll tell you what the current resolution and refresh rate is.  It depends on how fancy your monitor is.

---

### Post by uthfull on 2005-09-23
mlomker..... man adjusting the screen through the monitor DID NOT work in 1024x768.
I decreased it height n width wise frm there. But then again... even after adjusting.... the full screen wasnt shown. I had to move my mouse to the edges to go further.

What I'm saying is... while 800x600 is displayed properly within the limits.. but as soon as I choose 1024x768.... it goes beyond the monitor. The icons or the desktop doesnt get ne smaller lik it shud in going frm 800x600 1024x768. I try n adjust it frm the monitor.....for example I decrease it vertically as much as possible... the whole display shud get crunched... but what I'm telling u is... since in 1024x768 it is already outside... even if I crunch it... it remains outside. Black borders come up above n below the display. But still I have to travel to the edge of the visible area to move further.

n the monitors not at all fancy... 15" LG Studioworks 520Si.... quite outdated.

---

### Post by Dooglus on 2005-09-23
I think what he's trying to say is that his screen is like a 800x600 window onto a virtual 1024x768 desktop.  I've seen it before a long time ago, but not in ubuntu, and not since switching to x.org from xfree86.  You can run the mouse up again the edge of the screen to scroll the view around the virtual desktop.

---

### Post by mlomker on 2005-09-23
> scroll the view around the virtual desktop.

Exactly -- it's a virtual desktop.  The reason that he's getting this is because his monitor is old.  The new plug-and-play monitors actually tell the driver what modes it is capable of and the driver picks the best one that they agree on.  With an older monitor you are going to have to create a custom modeline and, unless you're lucky, do a lot of trial-and-error to find one that'll work.

There's an example of a modeline [in this post.](http://www.ubuntuforums.org/showpost.php?p=365144&postcount=6)

---

### Post by uthfull on 2005-09-23
In short... I'm screwed right!!

---

### Post by mlomker on 2005-09-23
[QUOTE=uthfull]In short... I'm screwed right!![/QUOTE]

No, it means that you'll have to do some searches to read up on **modeline** and try a bunch of them until one works.

---

### Post by madz on 2006-01-16
Hey uthfull, Can u tell me how u got sify working in ubuntu? i downloaded their client and installed it but it says 
"Login Failed : Invalid session,Please relaunch your dialer"

when i try to login.

---

