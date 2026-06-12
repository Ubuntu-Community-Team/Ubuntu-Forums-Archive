---
title: "New to Ubuntu! I need HELP"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Fr@nKy on 2006-08-24
I finally was able to install Ubuntu 6.06 ;) Now I need help! 

1)I own a geforce 6600GT I installed the drivers from synaptic! How do I make sure everything went ok? 

2)Secondly I can't change my resolution from 1024x768. I find the option but I have no 1280x1024 and 640x480 and 800x600 just make my monitor flicker a bit a go back to 1024x768. I really want 1280x1024.

3) I use Mozilla Firefox, but I can't install Flash player! How do I do it?

4) Synaptic is great but I heard that apt-get is better. Can you give me some basic commands?

Thanks in advance!

---

### Post by Ziox on 2006-08-24
> **Fr@nKy said:**
> I finally was able to install Ubuntu 6.06 ;) Now I need help! 

1)I own a geforce 6600GT I installed the drivers from synaptic! How do I make sure everything went ok? 

2)Secondly I can't change my resolution from 1024x768. I find the option but I have no 1280x1024 and 640x480 and 800x600 just make my monitor flicker a bit a go back to 1024x768. I really want 1280x1024.

3) I use Mozilla Firefox, but I can't install Flash player! How do I do it?

4) Synaptic is great but I heard that apt-get is better. Can you give me some basic commands?

Thanks in advance!

Resolution problem: do this command in terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

then reboot after that's done

Flash Player: Download Automatix from [www.getautomatix.com](www.getautomatix.com), then start automatix and choose to install Flash...

Synaptic/Apt-Get: synaptic and apt-get is the same thing, Synaptic is a GUI (front-end) for apt-get.  However, apt-get, since it's a command line tool, is naturally more powerful than a GUI tool. you can find the full list of commands for apt-get by looking at the manual for apt-get.  To access manuals for any software, enter:

```
man <name of the software>
```

in this case it would be:

```
man apt-get
```

Hopefully this helps...

---

### Post by Fr@nKy on 2006-08-24
And how do I configure it xorg??? I just had to reinstall Ubuntu because when i rebooted my monitor went crazy and I couldn't see a thing.

---

### Post by zxee on 2006-08-24
You generally don't need to re-install because of an xserver problem.
Just enter a terminal (Alt+Ctrl+F1) and then use the dpkg-reconfigure command as suppied by Ziox from there.

---

### Post by Fr@nKy on 2006-08-24
but what options should I use for making my monitor work at 1280x1024??

And to install NDVIDIA drivers can I use synaptic?

---

### Post by Ziox on 2006-08-24
> **Fr@nKy said:**
> but what options should I use for making my monitor work at 1280x1024??

And to install NDVIDIA drivers can I use synaptic?

I would assume that you haven't tried the command I had given you, because it is quite clear how to change the resolution once that command is executed...

anyway....space is used to select the options for resolutions and enter to move on to the next section...

install Nvidia driver by install it from the repos...

```
sudo aptitude install nvidia-glx
```

to find more apps for nvidia use this command:
```

apt-cache search nvidia | more
```

use this command to check if the driver works:

```
glxinfo | grep direct
```

---

### Post by Fr@nKy on 2006-08-24
And what is suposed to appear if it works?

---

### Post by Ziox on 2006-08-24
> **Fr@nKy said:**
> And what is suposed to appear if it works?

works:

```
direct rendering: Yes
```

doesn't work:

```
direct rendering: No
```

---

### Post by Fr@nKy on 2006-08-24
It worked! LoL But I still can't use 1280x1024! The only way is using that dangerous control you told me?

---

### Post by Ziox on 2006-08-24
> **Fr@nKy said:**
> It worked! LoL But I still can't use 1280x1024! The only way is using that dangerous control you told me?

Either that or edit the xorg.conf file manually, which I would say is even more dangerous.  And the "control" i told you about isn't dangerous at all, most of the specs and stuff are automatically detected...all YOU NEED to do is to pick the resolution you want....

---

### Post by Fr@nKy on 2006-08-24
Still hasn't worked! But atlest now it boot ok. Don't you have a tutorial to help me with this issue?

---

### Post by Fr@nKy on 2006-08-24
And btw how do i become a sudo to edit it manually? I supose I only need to add "1280x1024" to the resolutions.

---

### Post by peabody on 2006-08-24
I'm guessing that Xorg is not properly detecting your monitors capabilities.  This sometimes does not work correctly.  Do you have a manual to your monitor, or could you tell us the make and model of your monitor.  We may have to manually set the vertical and horizontal refresh rate within the /etc/X11/xorg.conf file.

---

### Post by Fr@nKy on 2006-08-24
HELP Please!!

And BTW where can I get GAIM 2.0 beta 3.1?

---

### Post by peabody on 2006-08-24
> **Fr@nKy said:**
> HELP Please!!

And BTW where can I get GAIM 2.0 beta 3.1?

[http://sourceforge.net/project/showfiles.php?group_id=235](http://sourceforge.net/project/showfiles.php?group_id=235)

There doesn't appear to be a .deb file in the release, so you may have to compile from source, try the following from the command line:

```

sudo apt-get install build-essential
sudo apt-get build-dep gaim

```

When you extract the archive with the source code  (or you can wait to see if I can find you a deb and ignore these instructions), go to a terminal, cd to the archive folder and type:

```

./configure
make
sudo make install

```

You may wish to uninstall the previous version

```

sudo apt-get remove gaim

```

Then you can launch the new gaim from the terminal by

```

/usr/local/bin/gaim

```

See my above post for help with your previous problem.

---

### Post by mdwuznik on 2006-08-24
Please post the exact model of your monitor. And your existing xorg.conf file instead of repeating "please help". Even the highest gurus here do not have sufficient mental powers to guess your monitor config...
If you send it, someone may probably post the magic words needed to get 1280x1024 on your monitor:)

Cheers
Michal

PS:Nice to see a convert, always.

---

### Post by Fr@nKy on 2006-08-24
My monitor is a Samsung SyncMaster 172v. 1280x1024 @ 75Hz is the maximum resolution! The best I coulf get was 1024x768 @ 75Hz but I'll be happy with 1280x1024 @ 60Hz

---

### Post by mdwuznik on 2006-08-24
Better go for 75 Hz. I would personally use it 1152x864@85Hz or 1280x960@75, as you would see round, not oval circles than (1280x1024 has an awkward aspect ratio on a CRT). Sorry, I hope that someone will post the modelines soon, it's too late for me to dig the"magic" out of my mind, you'll survive a bit more with 1024x768  :)

Happy *nixing :)

---

### Post by Fr@nKy on 2006-08-24
Ok! Thanks! But don't forget me LoL BTW I couldn't make GAIM to work but well I'm a noob on UNIX based systems I still don't know how to compile an installer. I just want GAIM 2.0 beta 3.1 because GAIM 1.5 started to have problems and being kicked out by MSN servers like said on the official site

---

### Post by Fr@nKy on 2006-08-24
One more thing! I don't know how to be a Super User (or root) to be able to erase the backups made of xorg config file each time I used that command and I have about 8 files that I don't need but I can't erase because I haven't enough permissions!

---

### Post by peabody on 2006-08-24
```
sudo rm filename
```

This will delete a file.  BE CAREFUL WITH THIS COMMAND, THERE'S NO GOING BACK!  No trash, nothing.  In a terminal, you can type some of the filename and then press tab to complete the filename.  If tab doesn't work you haven't typed enough of the filename yet.

I'll try to see if I can pull up some Hfresh and Vfresh settings for that model monitor.

In trying to build gaim what was the exact problem you were having?  Anyway, do try to be more descriptive in the future.

---

### Post by peabody on 2006-08-24
These seem to be the refresh rates of your monitor.

**[Edit: NEVERMIND, USE Ziox's post below to fix the problem!]**

Horizontal 30-81 KHz - Vertical 56-75 Hz.

Give me a second and I'll tell you what to put in your xorg.conf file exactly.

Okay, try this.  You should of course make a backup of the original /etc/X11/xorg.conf that is currently working.  If you don't know how to properly edit the /etc/X11/xorg.conf file, from with in a terminal, copy and paste the following:

```
sudo editor /etc/X11/xorg.conf
```

Find the section of the xorg.conf file that reads something like this:

```

           Section "Monitor"
               Identifier "name"
               entries
               ...
           EndSection

```

Somewhere between the Section and EndSection add two new lines that look like this:

HorizSync "30-81"
VertRefresh "56-75"

Save the file and log out.  Then at the login screen, press Ctrl+Alt+Backspace all at once.  The login screen will go black for a second and then (hopefully) come back up.  Login and you should now be able to get your desired resolution.

---

### Post by Fr@nKy on 2006-08-24
Ok Thank you very much! About the delete command when you say filename I have to put all the adress to the file right?

---

### Post by peabody on 2006-08-24
Depends which folder you are in.  It's like a url.  If you're in the current folder the file is in you only need the name of the file.  Type "pwd" to learn your current folder.  "cd foldername" changes to that folder.  Don't forget tab completion, type some of a file or folder name and then hit tab.  This will save you a lot of typing.  "ls" will also show you all the files in the current directory.  See above for my instructions for fixing your x problem.

---

### Post by Ziox on 2006-08-24
> **Fr@nKy said:**
> Ok Thank you very much! About the delete command when you say filename I have to put all the adress to the file right?

I have a SamSung SyncMaster as well, why did you say so before? :p  I'm running it in 1280x1024 @ 60Hz...and I solved by using my method butX1 here's the section in my xorg.conf file that affects the monitor:

```
Section "Monitor"
	Identifier	"SamSung"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
	Monitor		"SamSung"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by Fr@nKy on 2006-08-24
But which values should i use?? peaboy's or Ziox's?

P.S.: I haven't said that I gad a **Samsung SyncMaster 172v** because I didn't know it was important. As I said before I'm a noob. I used all my life and I'm pretty good when it comes to Windows but on Unix I'm a noobie :P

---

### Post by peabody on 2006-08-24
I would use Ziox's since they seem to actual work since they're what he's using.  The values I sluethed were pulled after much googling and the page that came up wasn't even in English! (though it did seemed to be for your exact model and they were talking about xorg.conf settings).

---

### Post by Fr@nKy on 2006-08-24
ok! I edited but I don't know how to save it!

---

### Post by peabody on 2006-08-24
Just how are you editing the file?  You should be editing it via the ```
sudo editor /etc/X11/xorg.conf
```.

---

### Post by Fr@nKy on 2006-08-24
yeah i used that and changes the values but then how do i save it?? ^O does nothing besides typing Ô.

(BTW after solving this I may need help in other things I'll keep it on this post ;))

---

### Post by peabody on 2006-08-24
^O means Ctrl+O.

---

### Post by Fr@nKy on 2006-08-24
thanks! See I'm a noob

---

### Post by Fr@nKy on 2006-08-24
I did it! I have it @ 1280x1024. I love yyou guys! Now I need some help with Flash and if Possible WINE.

Can you tell me what to do to get these two working?

---

### Post by peabody on 2006-08-24
There are a few ways to get flash up and running, you can do it manually, you can do it via Automatix, and apparently there's a script or two to automatically do it.  I confess, I did it a long time ago when I was running fedora, manually into my user folder and when I switched to Ubuntu I had the same user folder so I can't recommend the best newbie way to do it.

As for wine, that depends on a lot of things.  What do you need working?  Wine is hit or miss with quite a few things.  Some things work out of the box, somethings can be made to work, some things require grabbing dll files from a windows install.

---

### Post by Ziox on 2006-08-24
> **Fr@nKy said:**
> I did it! I have it @ 1280x1024. I love yyou guys! Now I need some help with Flash and if Possible WINE.

Can you tell me what to do to get these two working?

can you not install flash or WINE? What do you need help with?

---

### Post by Fr@nKy on 2006-08-24
i installed Wine first by Ubuntu repositorie and than i found out about the official Wine HQ one and updated. i need to know how to run a Setup to install a program. For example MSN Messenge 7.0.

Flash I just don't understandvery well how to install Automatix.

---

### Post by peabody on 2006-08-24
> **Fr@nKy said:**
> i installed Wine first by Ubuntu repositorie and than i found out about the official Wine HQ one and updated. i need to know how to run a Setup to install a program. For example MSN Messenge 7.0.

Flash I just don't understandvery well how to install Automatix.

Just MSN messenger 7?  Let me see if that works via my Wine.

---

### Post by Fr@nKy on 2006-08-24
that is one of the things I wanted to try Lol But there's many more possibilities!

---

### Post by Ziox on 2006-08-24
> **Fr@nKy said:**
> i installed Wine first by Ubuntu repositorie and than i found out about the official Wine HQ one and updated. i need to know how to run a Setup to install a program. For example MSN Messenge 7.0.

Flash I just don't understandvery well how to install Automatix.

to install automatix go to [www.getautomatix.com](www.getautomatix.com) and check the left side of the page, and click on install....and follow the commands for "automatic automatix installer"....as for Wine, you basically install Wine, then do this command in terminal:

```
winecfg

```
and then you just run the setup files that Windows applications include....though not every application will work with Wine...

---

### Post by peabody on 2006-08-24
The Messenger 7 install didn't work for me, even after changing the settings to Windows XP in the winecfg.  I am using the Ubuntu wine, not the one from winehq.  An earlier version of messenger may work.  I'm under the impression that WinXP has the least support in Wine.

---

### Post by Fr@nKy on 2006-08-24
Ok I'll try your tips. Well and now one more thing. Well I installed Ubuntu i386 and I have an AMD Athlon 64 3800+ there's a kernel optimized for my Processor or this is something I should not mess with for now?

---

### Post by Ziox on 2006-08-24
> **peabody said:**
> The Messenger 7 install didn't work for me, even after changing the settings to Windows XP in the winecfg.  I am using the Ubuntu wine, not the one from winehq.  An earlier version of messenger may work.  I'm under the impression that WinXP has the least support in Wine.

I agree, change the setting to Win 98 may work better than XP

@Franky

if you don't mind uninstalling WINE, you can try an older version of WINE, and then use WineTools to help you install various "Windows" components that might get applications working...

Another alternative...if you have a decent computer, you can try using VMWare Server...

---

### Post by peabody on 2006-08-24
from what I understand that is often more trouble than it's worth, although perhaps someone with more experience could shed some light on the subject.  I believe the issue is that you want to be careful and make sure you get the right one for your architechture or it could lead to random problems (slowness, apps chrashing, etc.).

---

### Post by Ziox on 2006-08-24
> **Fr@nKy said:**
> Ok I'll try your tips. Well and now one more thing. Well I installed Ubuntu i386 and I have an AMD Athlon 64 3800+ there's a kernel optimized for my Processor or this is something I should not mess with for now?

don't mess with the kernels right now, after you are more familiar with Ubuntu, and various "problems" then you can mess with the kernel...

---

### Post by peabody on 2006-08-24
> **Ziox said:**
> I agree, change the setting to Win 98 may work better than XP


Messenger 7 requires XP as the installer will politely tell you if you try to install under any other settings under wine ;) .

---

### Post by Ziox on 2006-08-24
> **peabody said:**
> Messenger 7 requires XP as the installer will politely tell you if you try to install under any other settings under wine ;) .

o...well...you can tell that I've never tried messenger 7...

@Franky

why don't you use gaim or kopete? they both support various IM protocals

to install kopete:

```
sudo aptitude install kopete
```

but I would suggest to use gaim because kopete is a KDE app...if you need help, I'll be here, or you can IM me....

---

### Post by peabody on 2006-08-24
> **Ziox said:**
> o...well...you can tell that I've never tried messenger 7...

@Franky

why don't you use gaim or kopete? they both support various IM protocals


I think that's why he wanted the latest gaim, because I think the current gaim in Ubuntu is having troubles working with the MSN network.  I could be wrong.

---

### Post by Fr@nKy on 2006-08-24
it was just for fun LoL! i'm using aMSN for MSN for now. I managed to install eMule Bowlfish (a Portuguese Mod of eMule that limits the traffic to be only among portuguese users because of the international traffic limits that most ISPs here have) but I don't know how to run the program after installing it! After this I'll go check Automatix :P

---

### Post by peabody on 2006-08-24
> **Fr@nKy said:**
> it was just for fun LoL! i'm using aMSN for MSN for now. I managed to install eMule Bowlfish (a Portuguese Mod of eMule that limits the traffic to be only among portuguese users because of the international traffic limits that most ISPs here have) but I don't know how to run the program after installing it! After this I'll go check Automatix :P

The default drive C for wine is usually under .wine/drive_c.  If you show hidden folders and files in nautilus you should be able to navigate to the Program Files directory and double click the exe.

---

### Post by Fr@nKy on 2006-08-24
Doesn't work! The exe just pops up an error saying that impossible to present the file ... What's the problem?

---

### Post by Fr@nKy on 2006-08-24
Automatix is working! Waiting for help on Wine guys

P.S.: I have flash :P

---

### Post by peabody on 2006-08-24
> **Fr@nKy said:**
> Doesn't work! The exe just pops up an error saying that impossible to present the file ... What's the problem?

Hmm, try the right click menu and seleceting open with other application.  Then in the bottom of that window, there should be an option to enter a custom command.  Enter wine.

---

### Post by Fr@nKy on 2006-08-24
I haven't tried that tip for Wine yet but I will!

Another thing I need is to get my HP Officejet 6110 to work. At least I need to print but scanning would be great to. What can I do?

---

### Post by Uchiha Sasuke^^ on 2006-08-24
> **Ziox said:**
> works:

```
direct rendering: Yes
```

doesn't work:

```
direct rendering: No
```

mine does't work, what can i do?

---

### Post by peabody on 2006-08-24
> **Fr@nKy said:**
> I haven't tried that tip for Wine yet but I will!

Another thing I need is to get my HP Officejet 6110 to work. At least I need to print but scanning would be great to. What can I do?

System->Administration->Printing.  Setup the printer from there.

For scanning

Applications->Graphics->XSane.

Provided that model is supported (which I think it is, HP compatibility with linux is fairly good if memory serves).

---

### Post by Fr@nKy on 2006-08-25
I'm going to try that for my Officejet =P And finally I need help getting my AC'97 onboard (on my ASUS A8N-SLI Dluxe) playing on my 5.1 speakers.

---

### Post by Fr@nKy on 2006-08-25
Officejet Working! Now I need help with that above ;)

---

### Post by Fr@nKy on 2006-08-25
[http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True](http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True)

This the Download Page. They have packages for Fedora Core but not for Deb. Where can I find it?

---

### Post by peabody on 2006-08-25
> **Fr@nKy said:**
> [http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True](http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True)

This the Download Page. They have packages for Fedora Core but not for Deb. Where can I find it?

There is a general linux package.  You might be able to use that one, though I'm betting that it'll require building a kernel module, in which case:

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

That's a ` not a '

I don't have this hardware so I'm sure anything I have to offer is of limited help.  Try reading the instructions in the archive after extracting it.

---

### Post by Fr@nKy on 2006-08-25
Well after looking a bit on the options I was able to put 4 speakers to work! Maybe it's better to stay this way. (I never had the 5 working only on games that support 5.1)

---

