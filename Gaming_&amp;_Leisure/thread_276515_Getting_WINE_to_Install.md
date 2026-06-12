---
title: "Getting WINE to Install"
date: 2006-10-13
forum: Gaming &amp; Leisure
---

### Post by Kulluminatii on 2006-10-13
Hi, I wanted to install WINE so that my little brother can play his game on my old pc with Ubuntu while I can do my work on this pc. My topic in the "Absolute Begginner" section got a couple of my questions answered, but at the point I am at now, I think this forum is a much better place to get answers from. Link to topic: [http://www.ubuntuforums.org/showthread.php?t=276386&page=2](http://www.ubuntuforums.org/showthread.php?t=276386&page=2)

Basically, I downloaded the file from here: [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/) for 6.06 and burned it to a CD-R using this computer (it uses Windows-XP if that helps at all). When I went to my old pc and put in the disc, I tried to make it work using the Package Installer.

This is the error it gave me: "Error: Dependincy is not satisfiable: libartsc0"

What did I do wrong? Please keep in mind that my old pc does not have an internet connection (I cannot get the dial up to work.)

Thank you very much for taking your time to read this:D

---

### Post by pay on 2006-10-13
Download this file [http://mirror.isp.net.au/ftp/pub/ubuntu/pool/main/a/arts/libartsc0_1.5.2-0ubuntu1_i386.deb](http://mirror.isp.net.au/ftp/pub/ubuntu/pool/main/a/arts/libartsc0_1.5.2-0ubuntu1_i386.deb)
```
wget http://mirror.isp.net.au/ftp/pub/ubuntu/pool/main/a/arts/libartsc0_1.5.2-0ubuntu1_i386.deb
```
on ubuntu or put it into the browser on Xp and then install it on your Ubuntu machine
```
sudo dpkg -i libartsc0_1.5.2-0ubuntu1_i386.deb
```

---

### Post by Kulluminatii on 2006-10-13
Ok so I download that file with my Xp machine, then I burn it to a cd. I use the cd with my ubuntu machine and use the "sudo dpkg -i libartsc0_1.5.2-0ubuntu1_i386.deb" code?

---

### Post by pay on 2006-10-13
I'll be alittle more specific. ```
sudo dpkg -i /path/to/file/libartsc0_1.5.2-0ubuntu1_i386.deb
```so if it's on a cdrom the command will be something like this ```
sudo dpkg -i /media/cdrom0/libartsc0_1.5.2-0ubuntu1_i386.deb
```

---

### Post by Kulluminatii on 2006-10-13
Ok so if I want to use the file from the cd directly, I use the second code, but if I copy the code to the desktop, I use the first one. I think I got it, thank you very much, hoping this works!

---

### Post by pay on 2006-10-13
From the desktop it would be ```
cd
sudo dpkg -i Desktop/libartsc0_1.5.2-0ubuntu1_i386.deb
```

---

### Post by Kulluminatii on 2006-10-13
so i type cd, enter, then sudo...?
Sorry, im a n00b at this=\

---

### Post by pay on 2006-10-13
Yes (even though it is probably not necessary). cd is change directory. So cd will change it to the home users folder. I only said it so just incase you changed directory previously it will change back to the /user/home because if it was in another directory then it wouldn't find the Desktop folder. Sorry for being so confusing.

---

### Post by Kulluminatii on 2006-10-13
Ok, thank you very much, going to try this right now. I love you=)

---

### Post by Kulluminatii on 2006-10-13
I...I think it worked....wow...it worked!! Thank you very much for helping me! Before I get too carried away, im going to test out a game or two to make sure it works. Thank you so much!

---

### Post by Kulluminatii on 2006-10-13
Well I am pretty sure it is installed. Now I cant find it. Is their a way to put it on my desktop? Also, to use it, do I drag the game cd into the WINE program and then it will load or do I do something else?

---

### Post by pay on 2006-10-13
Wine is a command line program. ```
wine setup.exe
```so from the cdrom it would be something like ```
wine /media/cdrom0/setup.exe
```assuming your cdrom is 0. But before you try to install games it is probably best that you try ```
winecfg
```and then setup wine to use xp(or whatever the game supports) etc.

---

### Post by Kulluminatii on 2006-10-13
Thank you very much! I will try this out as soon as possible.

---

### Post by Kulluminatii on 2006-10-13
Well I tried 'wine setup.exe' This is what popped up.

wine:creating configuration directory '/home/vinny/.wine'...
failed to open the service control manager.
fixme:ole:ITypeInfo_fnRelease destroy child objects
wine: '/home/vinny/.wine' created sucessfully
wine: could not load L" c:\\Windows\\system32\\setup.exe": Module not found

*NOTE* If their is a smily face after fixme:, the word their is ole

Any solution to this?

---

### Post by pay on 2006-10-13
I meant ```
wine path/to/my.exe
```or you can use cd to change the directory to the one with your .exe file.```
cd /path/to/my <enter>
wine my.exe
```So from cdrom and the file is called setup.exe would mean you would use ```
wine /media/cdrom0/setup.exe
```assuming that your cdrom is 0. If you don't give a path it will look for the .exe in the home folder and if it's not there it will look for it in  your fake c_drive in /c_drive/windows/system32/setup.exe

---

### Post by Kulluminatii on 2006-10-13
Oh ok cool, i'll try this out now

---

### Post by Kulluminatii on 2006-10-14
First one didnt work because it couldnt find it, but im guessing the second one is the one im supposed to use.

---

### Post by Kulluminatii on 2006-10-14
I tried the second one, Im thinking im supposed to fill in where it says <enter> but it still doesnt work. I have put the wine software in a file called 'My Documents' from the cd. I've also tried the last code you listed, still did not work.

---

### Post by pay on 2006-10-14
Type in ```
winecfg
```to verify that you have wine installed. Then if a box with editable settings comes up then wine is installed if not then it wasn't installed. Then to install your game type in ```
wine /media/cdrom0/setup.exe

```or if that doesn't work```
wine /media/cdrom0/install.exe
```then a windows installers should come up.

Where I had <enter> I meant to press the enter key, not type it. The command line can be confussing at first but when you do master it you wont know how you lived without it.

---

### Post by Kulluminatii on 2006-10-14
Ok thank you very much for being patient with me as well as being helpful. Most people wouldve given up on me by now.

---

### Post by Kulluminatii on 2006-10-14
> **pay said:**
> Type in ```
winecfg
```to verify that you have wine installed. Then if a box with editable settings comes up then wine is installed if not then it wasn't installed. Then to install your game type in ```
wine /media/cdrom0/setup.exe

```or if that doesn't work```
wine /media/cdrom0/install.exe
```then a windows installers should come up.

Where I had <enter> I meant to press the enter key, not type it. The command line can be confussing at first but when you do master it you wont know how you lived without it.

Yes, WINE is installed, so thats good. I popped in my game and typed the first code, it said 'no such file or directory'. I tried the second code, it also said 'no such file or directory'.

Cant figure out whats wrong, I am sure it should work with what you gave me. 

Im not sure if this will help but when I pop in the game disc I check the CD-Rom/DVD-Rom drive and the name switches to. "CD-Rom/DVD-Rom Drive:EmperorRotMK"

I feel that im close to getting it to work, I cant thank you enough!

---

### Post by pay on 2006-10-14
You need the game disc in the drive while running "wine /media/cdrom0/setup.exe" Though the exe might have a different name. Open up the game disc and find out what the .exe's name is then subsitute it into the above command.

---

### Post by Kulluminatii on 2006-10-14
Yes the game disc was in the drive. So i replace 'setup.exe' with the one inside the game?

---

### Post by Kulluminatii on 2006-10-14
The files that end with .exe when i opened up the game disc was Setup.exe and autorun.exe, I even tried some of the others, but it still gave the same reply, 'no such file or directory'.

---

### Post by claydoh on 2006-10-14
One thing to remember is to run winecfg and go to the drives section and try to autodetect your drives.

if you still have problems with wine not seeing your cdrom, you may need to follow some of the instructions here:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

I have had problems with older versions of wine not seeing my cdrom unless I set up a D drive pointing to my cdrom as per the link above, so that maight be something to try as well

---

### Post by Kulluminatii on 2006-10-15
Ok cool, I will try that asap

---

### Post by Kulluminatii on 2006-10-15
> **claydoh said:**
> One thing to remember is to run winecfg and go to the drives section and try to autodetect your drives.

if you still have problems with wine not seeing your cdrom, you may need to follow some of the instructions here:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

I have had problems with older versions of wine not seeing my cdrom unless I set up a D drive pointing to my cdrom as per the link above, so that maight be something to try as well

This version of wine is the most recent one out, and my D drive is where the cdrom0 is located.

Still dont know what to do:-k

---

### Post by pay on 2006-10-15
I think that you might benifit from cedega. It costs money but it simplifies installing games on Linux. You can find a trial for it on softpedia.

---

### Post by pay on 2006-10-15
I think that you might benifit from cedega. It costs money but it simplifies installing games on Linux. You can find a trial for it on softpedia.

EDIT: Okay the message came up twice for some reason. Anyway Cedega is based on the wine code but with added directX support and a simplified graphical interface that detects the game disc. Heres the trial [http://linux.softpedia.com/progDownload/Cedega-Download-9843.html](http://linux.softpedia.com/progDownload/Cedega-Download-9843.html)
I think that may be a slightly older version but that won't matter much if you just want to test it out and I think that when you put in the code that's sent it lets you update it.

---

### Post by Kulluminatii on 2006-10-15
Ok cool. Cedega charges a monthly $5 right? So what If I cancel paying, does it stop me from using Cedega or I just cant get updates anymore?

---

### Post by pay on 2006-10-15
I have no idea but you might be able to ask on the cedega forums.

---

### Post by xethm55 on 2006-10-15
It looks as though you have a "case" problem.  Linux is case sensitive, i.e. 'a' is different from 'A'.  If the setup.exe program is really Setup.exe then you would need to type:
```
wine /media/cdrom0/Setup.exe
```However, if you have the cdrom configured you can get around this problem by typing:

```

wine "D:\Setup.exe"
```Replace D: with the drive the points to the location of your cdrom in your winecfg.

-Xethm55

---

### Post by Kulluminatii on 2006-10-15
Okay thank you, I will try that ASAP. I have tried using 'setup.exe' and 'Setup.exe', both gave me the same error, but I will try that other piece of information you gave me,thank you once again.

---

### Post by Kulluminatii on 2006-10-15
'wine "D:\Setup.exe" worked!! I want to thank you xethm55 for showing me this, and especially pay who went through this whole process with me, and in the end I learned a few things. Also anyone else who tried to help me.

One last question though. I remember reading somewhere that when the game askes you were you want to install, you pick a specific area to install, not the standard one they give you.

This is what showes up when I try to install Emperor.

Installshield Wizard
Choose Destination Location
 Select folder where Setup will install files.

**Destination Folder**
**C:\Sierra\EmperorRotMK**

Do I go ahead and click 'ok' and let it install their, or do I install it somewhere else?

---

### Post by Kulluminatii on 2006-10-15
Ok I found out where to install the game, but dont know where it is.
Link: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
**"If the application asks for a directory to install the application to, make sure that you select the newly created .wine directory (not the default Windows directory the application will assume you want to use).Direct the application you are installing to the .wine directory, which, by default, is installed in the home directory. By the default, the .wine folder will not be visible, as any other hidden folder. To have the .wine folder appear, go to the home directory, and press CTRL-H, or go to View > Show Hidden Files."**

Ok I have found where the .wine directory is.

I did this.

My Computer->Filesystem->home->vinny->CTRL-H to show hidden files->.wine

Now how do I direct where I want to install the game to .wine? I Clicked on browse in the install screen, and when I open up home, all it shows is examples, desktop, and something else.

Is their a way in linux, like in windows, to find the name of the file in the address bar. For example, if I open up My Documents in Windows, you look at the address bar and it shows "C:\My Documents" or something like that.

---

### Post by Kulluminatii on 2006-10-15
When I looked around, I found their was C:, D:, and H: (which I am sure is home.)

I typed in H:/home/vinny/.wine and pressed enter, but it gave me an error saying 'invalid or incomplete'.

---

### Post by Kulluminatii on 2006-10-15
Well, after waiting and being safe, I just said f it, I made a folder, and decided to install it to that then move it to the .wine directory, hopefully I can do that and the game will work.

---

### Post by Kulluminatii on 2006-10-15
Ok the install went well, it installed into the folder I named 'Emperor wine'. I have moved the folder into the .wine directory. Do I move the contents of the folder into a special area to run the game?

Do i do this? 'wine /home/vinny/.wine/emperor.exe'. I'll try that right now and see if it works.

---

### Post by Kulluminatii on 2006-10-15
Ok it works, but their is a slight problem. After I type 'wine /home/vinny/.wine/Emperor.exe' a little box pops up saying "no disc in drive", even when their is a disc in it. So I pop out the disc, put it back in, and then it gives the same error. Now whats wrong?

---

### Post by pay on 2006-10-16
Destination Folder
C:\Sierra\EmperorRotMK

That would be /home/user/.wine/drive_c/Sierra/EmperorRotMK
The game should work where ever you install it as long as you have permisions to that folder

I'm not sure how good wine is at copy protection, that might be why it is asking for a disc, try using a crack. [www.gameburnworld.com](www.gameburnworld.com)

---

