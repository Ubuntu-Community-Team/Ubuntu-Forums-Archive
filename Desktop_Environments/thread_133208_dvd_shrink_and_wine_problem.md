---
title: "dvd shrink and wine problem"
date: 2006-02-19
forum: Desktop Environments
---

### Post by tanman on 2006-02-19
I have downloaded dvd shrink with wine and see it. When I right click the exe file and open with wine everything is good. 
When I open up disk it sees what I have a dzd in the drive but when I click on it it says it has encountered a problem:
invalid file name
path not found

Also when I look in wine to add applications and I use the drop down to "look in" 
nothing appears if that makes any sense so I can not add wine dvdshrink to it.

The weird thing is I had dvd shrink added to the wine applications at one time and I had the open disk working, but it would get to 42% analizing and then quiet. So I unistalled everything and reinstalled now all this is happening.

I noticed in the forms that there is a xdvdshrink that is for linux, but I can not find it.

I have used dvdshrink on windows for about a year and have always liked it.
Any suggestions would be great.
Thanks

---

### Post by tanman on 2006-02-19
Even when I click on open file tab in DVD shrink it says look in , but it is empty. The first time I used it it gave me a bunch of options of where to look. I am sure this is a simple problem for it was working. 
Seems weird that both on wine and dvdshrink the "look in" is empty.
Please post if you have any siggestions
Thanks

---

### Post by pdxsam on 2006-02-19
Have you checked out this tutorial on using DVD Shrink with Wine?

[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

Using those instructions  DVDShrink works perfectly on my machine.

Cheers,
Sam

---

### Post by nalmeth on 2006-02-20
yeah, have you run winecfg yet?
I believe the 'jist' of the howto is that in winecfg, dvdshrink must be added to the applications list, and should be set as windows XP. Also your cdrom drive must be setup correctly in the DEVICES tab. Open up the advanced settings and make sure the device type is a cdrom.

here's a link for xdvdshrink, but I think there is a difference with the DVD menu. Worth a look: [http://doc.gwos.org/index.php/Xdvdshrink](http://doc.gwos.org/index.php/Xdvdshrink)

---

### Post by manicka on 2006-02-20
[QUOTE=pdxsam]Have you checked out this tutorial on using DVD Shrink with Wine?

[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)
[/QUOTE]

That how-to was written for hoary and won't work in breezy

Have a look here

[http://doc.gwos.org/index.php/DVD_Shrink_Breezy](http://doc.gwos.org/index.php/DVD_Shrink_Breezy)

---

### Post by tanman on 2006-02-20
Yes I can run wine cfg and it opens up, but when I go to click on add applications and it says to "look in" the space is empty so I can not add any applications to wine.
When I right click on the dvdshrink .exe I can open it with wine, but when I say open disk it will see I have a DVD in the drive but I get a error when I click to open the disk.
The thing that I do not get is that I had everything working at one time except the analizing. As I said it would get to 42% and then freeze. So I had read in the forums about a problem with DVDshrink and a later version of wine so I unistalled wine and than reinstalled it now I have this problem of not being able to search for files in either the wine cfg or the dvd shrink application. The fact I can not add anything to the wine application is the part I do not understand. I had a few applications added at one time. When I clicked on add application it always brought up places to look for applications, now nothing.
I am just wondering if I had clicked on something at one time that would not allow me to search for files in both circumstances.

---

### Post by tanman on 2006-02-20
OK so I opend up dvd shrink again and looked for a file using all the following methods:
Browse for folders, but it is empty:( 
I clicked on file ; open iso image and I get the same type of window that I get by clicking on "add applications" in wine and in that window you have a box wih a arrow init that says "look in" but this is empty.
If I could get this part to work I am sure I can get dvd shrink to work.
Just not sure why it will not let me search for a file to add.
This is driving me crazy for this morning I was able to add both a file to dvd shrink and also a application to "winecfg"
Thanks foor the help so far but until I can get this "look in" figured out I am not going to be able to use wine.

---

### Post by manicka on 2006-02-20
backup your .wine directory by renaming it .winebak, Then from the CLI or alt-f2 run winecfg, which will setup a new .wine directory. With this new setup you can then follow the step in the how-to at [http://doc.gwos.org/index.php/DVD_Shrink_Breezy](http://doc.gwos.org/index.php/DVD_Shrink_Breezy)

If it works then delete the backup directory. If not you can always go back to your old configuration by deleting the new .wine directory and restoring the backup.

---

### Post by handy on 2006-02-20
I used WineTools to install DVDshrink, with no prob's.

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

---

### Post by tanman on 2006-02-20
Well I give up. I have reinstalled wine and I still can not add a application:( 
When I click on add application and a window pops up to add a windows executable file the look in box is empty. This seems to be the root of all evil, for the same thing happens in dvd shrink when it asks to add a file. The look in box is empty.
Not sure why I all of a sudden can not add applications, for I had dvd shrink, and a couple other applications added at one time. 
There must be a setting some where that I am missing that will not let me look for a file under the windows emulator.
Could this be that under wine it is not seeing my computer at all. Is there a setting for a different path I can check.
Not to be a pain but I just want to figure this out.
thanks

---

### Post by tanman on 2006-02-20
Thanks manicka I now understand the problem and what you were trying to say. I am fairly new to this linux OS. Eventhough I installed and reinstalled wine the directory was always there. So when I renamed it and then went to winecfg it started a new dirctroy from scratch. This seemed to help.
i am going to try and reinstall everything and see how it goes.
Thanks again for all the help.

---

### Post by tanman on 2006-02-20
Success. It worked really well. This gives me one more reason not to have to boot into windows.
Is there a list of applications that will work with wine.
I have a PSP and use PSP video9 to put videos on it.

---

### Post by manicka on 2006-02-20
[QUOTE=tanman]
Is there a list of applications that will work with wine.
[/QUOTE]

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Mithrilhall on 2007-02-02
There is no need to add DVDShrink to the Applications Settings.

Try this...


Click the Drives tab. Make sure you have the cdrom listed (mine shows as 'D: /media/cdrom0').

Here is where I was having a problem....

Click the D: letter or whatever you have for your cdrom. Then click the 'show advanced' button. Make sure 'type' is set to 'CD-ROM'. Mine was showing as 'local hard disk'.

Once I changed the type it worked fine for me. I hope this helps you.

---

