---
title: "n00b blog"
date: 2009-02-22
forum: General Help
---

### Post by Dan Again on 2009-02-22
Hello All...

I recently made the decision to run my new laptop as an all Linux system.  I wanted to start this thread to have some more experienced eyes go over my general plan, have a few specific questions answered, and hopefully provide a useful resource to others who are also making this transition.  I have ordered the laptop, but have not received it yet, so at this point this thread is all about what I PLAN to do - not what I HAVE done.

The decision to run an all Linux system came out of the frustration of dealing with the usual adware/spyware/malware that is prevalent in Windows systems as well as the general "glitchiness" and poor support that have become synonymous with Windows.  Initially, I planned on purchasing a MacBook, even though it was more than I really wanted to spend.  My friends and family had a pretty easy time dissuading me, though, because I'm pretty cheap.  After going over things with my brother (a long-time Linux user) I decided to buy a non-Apple laptop and run Linux on it.

After searching for inexpensive & high-performing laptops that have a high success rate of running Linux, I decided on [this system]("http://www.jr.com/acer-computer/pe/ACE_AS69306154/") from that retailer at a price of $650 (no tax or shipping charges) because it seemed to meet all my criteria.  After briefly looking at the reviews for Ubuntu 8.10, it was pretty obvious that that was going to be the distro I would want to use.

Initially, I planned on dual-booting Ubuntu with the Windows Vista Home Premium 64 that comes preloaded on the laptop I've chosen.  My brother recommended this method in case I decided I didn't like running Linux and wanted to go back to Windows.  However, after exhaustively researching the procedure for burning Windows Recovery CD's for the system I'm going to get, I decided that it didn't really make that much sense to dual-boot.  I feel pretty committed to the decision to switch to Linux, and everything I've read about Ubuntu 8.10 has been pretty amazing.  If I decide I really hate it I can just wipe the drive and re-install Windows with the Recovery Discs.

So that's about where I am so far.  I've made my Ubuntu 8.10 disc, a GParted disc (which I don't think I'll need anymore), and the Windows Vista Recovery Disc that I found [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") (I still plan on burning Recovery Discs once the computer arrives using the method described [here]("http://forum.notebookreview.com/showthread.php?t=70059")).

I do have a few specific questions...

1) Are there any big problems that I might have with not having Windows installed on the system at all?  Will I be able to use all the files from my current Windows desktop on my new Ubuntu only laptop?

2) Given that I want to have only Ubuntu installed on my computer, what will be the best way to handle the installation once I get the Windows Recovery Discs for the laptop made?  Do I need to do any partitioning of the drives before installation?  I'd like to have two partions, one for / and a /home partition for all my settings, files and programs.  Do I format the drive before booting Ubuntu from the Live CD or do I just shut down out of Windows, boot from the Live CD and install directly from there?

3) What programs will I need to download after installing Ubuntu 8.10?  I've read that you need something to play Flash.  What about Quicktime, Adobe, etc?  Can all the necessary programs be accessed through Ubuntu's Add/Remove feature?

4) Is there anything special I need to know or take into consideration when moving over my desktop's Windows files onto my new Ubuntu laptop?

5) Are there reliable disc imaging utilities for Ubuntu?  What is the best disc imaging/recovery option for Ubuntu?


Thanks in advance for your comments and suggestions!

Dan

---

### Post by _noob_ on 2009-02-22
I'm confused. Do you want to dual boot? or is it a straight installation? If it's a straight installation all you have to do is boot the disk. You can reformat and install from the disk. You don't have to use the live feature. That is just to see if it's something that you'd like (if you didn't know.)

---

### Post by kestrel1 on 2009-02-22
I would suggest running the live CD first. That way you can make sure that your hardware is going to work with Ubuntu. You can install from the live CD as well.
Do a custom partition if you want a '/' & '/home' & you also need a small amount of space for swap.
You can do the setting up of the partitions during the installation process.
Anyway, what ever you decide, you shouldn't regret moving to Ubuntu.

---

### Post by Dan Again on 2009-02-23
I do not want to dual boot.  I am planning on doing a straight installation.

Thanks for your advice...any input on my other questions?

---

### Post by kestrel1 on 2009-02-23
OK, lets take this one at a time:
1) The only problems that you may face is on the types of files that you want to port over to Ubuntu. Most Windows programs have their own file extensions, but some can be used as they are, notably Word, Excel & Powerpoint. These file types will open in OpenOffice. Obviously image files are pretty well sorted on Ubuntu, so no worries there. Really it depends on the files that you want to use. Let us have some examples.
2) I think I covered this in my previous post.
3) I would suggest that you install Ubuntu Restricted Extra's as this includes things like Flash, Java etc.
4) Pretty much what I said in 1)
5) There are few Imaging programs for Linux available. Partimage is fairly good: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page), but if you have something like Acronis True Image that should also work from a bootable CD.

---

### Post by Dan Again on 2009-02-23
Hi Kestrel,
Thanks for the response.  I'm just a personal computer user who isn't really that into anything fancy, so the files that I use are pretty much limited to media files (jpeg, gif, btm, mp3 wma, etc) and Office documents...that's really about it.  Doesn't sound like those will be problematic.  What about my iTunes, my iPod and other hardware like scanners, printers, mouse, keyboard, etc?

Can Ubuntu's Restricted Extra's be accessed through the Add/Remove feature or do I have to get them from the web?

Re the imaging programs - why do you describe Partimage as only "fairly good?"  Fairly good might be good enough for some other types of utilities, but when it comes to backup/recovery I'd prefer not to take any chances.  Do you like Acronis True Image more?  Is it free?

Thanks again for your advice...I really appreciate the input.

---

### Post by kestrel1 on 2009-02-23
No, I would imagine the files that you have should be fine. If you are using MS Works, then save any of these files as Word or Excel files, but if you have full blown MS Office (any version) you should be OK. If you have Office 2007, then installing OpenOffice version 3 will sort that out, I think 2.4 might open the 2007 format as well.
The file types you mention are supported. For image files you can use Gimp, which is installed out of the box, as is Open Office 2.4. I think version 3 will be in Ubuntu 9.04
Not sure about your iTunes, but a search on this forum should show some results. Not something that I use. I believe that the iPod is recognised.
Scanners, pretty much work out of the box & you use Xsane Image scanner to scan in images. Works very well, I was only using it last night.
Most printers are recognised, not found one that isn't personally. Mice & Keyboards should be fine.
Restricted Extra's can be found under Synaptic Package Manager & will be downloaded when you request them, that way you get the latest version that is in the repository.
I can only say fairly good as I have only heard reports on Partimage. It isn't one I have used. I do not generally take image backups as a rule. True Image is not free, so if you do not poses it, try out one of the free ones. Partimage is a starting point. Have a look at the link: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
Others may have different ideas of course.

---

### Post by Znupi on 2009-02-23
Hi. First of all, congratulations on your decision! Be sure it's the right one! About your hardware - I took a look and it seems quite powerful and linux-friendly, so no worries about that. Let's get on to the questions (trying not to repeat what others said):
1) No, there shouldn't be any problems. It will be (really) easy for you to access Windows network shared files and it will be easy to share files with other Windows computers (just right-click on a folder -> Sharing Options). I find setting up shares on Linux a LOT easier than on Windows.
2) Just boot the LiveCD, make sure everything is OK and then proceed to install the system. As to partitioning, you're probably going to have to partition your disk manually, but that is done fairly easy. If you're having trouble, your brother should be able to help you. This is the only part of the installation where you need a (tiny) bit of "skill".
3) Ubuntu comes with everything: music/movie players, Firefox browser, Evolution mail & calendar, OpenOffice, Transmission BitTorrent, Pidgin all-in-one IM client, drawing programs, photo managers etc. What you should do the first time you boot Ubuntu after installation is an update. You can either go to System -> Administration -> Update Manager or just wait a few seconds to a minute and an update icon will appear in the tray. Click it.
Although I said I will try not to repeat what other said, I have to say this: install Ubuntu Restricted Extras (from Applications -> Add/Remove) (make sure "All available applications" is chosen to the left of the search field). This includes, but is not limited to: Flash, Java, Microsoft fonts (which are mandatory if you want to browse the web), codecs for EVERYTHING (dvd, avi, mpeg, mp3, etc).
Another thing you should try (only if you are having problems with video) is to install VLC Player. It is well known for having codecs for EVERYTHING (more EVERYTHING than the Ubuntu Restricted Extras :P)
4) Just try to keep everything organized :)
5) I don't know, I never back up my whole hard drive (I just put important files on a different partition than /).

Now, Ubuntu has come a long way. On your hardware, I'd say you have about 90% chances of installing Ubuntu without any problems. But, be prepared for that 10%.

Have fun with your new lappy :)

---

### Post by Znupi on 2009-02-23
As far as I know, there's no iTunes Store for Linux. You can, however, transfer files to and from your iPod (you can't import iTunes-proprietary DRM files -- i.e. files bought from the iTunes Store) and you can play music files directly from your iPod (again, not DRMed files).
Rhythmbox (the default Ubuntu music player) can share music via DAAP (e.g. can play files in the iTunes library on your PC and from your PC you can play music files from your laptop, using iTunes).
Hope I made sense (I'm a bit in a rush).

---

### Post by Dan Again on 2009-02-23
Thank you, Znupi for the thorough and thoughtful responses!

At this point in time I think I have most of my questions answered, but if anyone has anything they'd like to add I'd love to hear it.  I just downloaded the Ubuntu Pocket Guide and am going to continue doing research on the web while I wait for my new computer to come.  I think I really just need to get down to the nitty gritty to see how everything works out...I'm confident I will have few problems.

Thanks again to everyone who took a second to read and/or respond.  I will update with more info or questions as they come!

---

### Post by kestrel1 on 2009-02-24
Everyone has a few problems when starting with a new OS until they get used to it.
I remember having problems programming in Basic. Yes I do mean Basic & not Visual Basic :lolflag:
That was a while ago now. It was a whole new learning curve just to move from Windows 3.11 to Windows 95, so moving to Linux was huge. Glad I did though.

---

### Post by Hallvor on 2009-02-24
"1) Are there any big problems that I might have with not having Windows installed on the system at all?  Will I be able to use all the files from my current Windows desktop on my new Ubuntu only laptop?"

Everything but the applications should work.

"2) Given that I want to have only Ubuntu installed on my computer, what will be the best way to handle the installation once I get the Windows Recovery Discs for the laptop made?  Do I need to do any partitioning of the drives before installation?  I'd like to have two partions, one for / and a /home partition for all my settings, files and programs.  Do I format the drive before booting Ubuntu from the Live CD or do I just shut down out of Windows, boot from the Live CD and install directly from there?"

An Ubuntu livecd comes tith an easy partition tool called gparted. It is very easy to use, and you can do everything you need to from there without the need to format it in advance.

"3) What programs will I need to download after installing Ubuntu 8.10?  I've read that you need something to play Flash.  What about Quicktime, Adobe, etc?  Can all the necessary programs be accessed through Ubuntu's Add/Remove feature?"

Download what you need through Synaptic. Do not install files from webpages on the internet unless you know that they will work. You can use the webpage below to find good linux alternatives for your windows applications. 

[http://www.linuxalt.com/](http://www.linuxalt.com/)

"4) Is there anything special I need to know or take into consideration when moving over my desktop's Windows files onto my new Ubuntu laptop?"

Just make sure there are linux applications for them. :)

"5) Are there reliable disc imaging utilities for Ubuntu?  What is the best disc imaging/recovery option for Ubuntu?"

You could try something called Partimage. It should be in the repositories.  [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by Znupi on 2009-02-24
A few more things to add:

If you can't find a specific program in Add/Remove, or it's an outdated version, always check [http://getdeb.net/](http://getdeb.net/)

You'll have to get used to the new environment. Here are a few tips:
1) You will have multiple desktops. You can switch between desktops by clicking on them in the right part of your bottom panel or by using Ctrl+Alt+Arrows.
2) To minimize all windows, click the button in the left part of the bottom panel.
3) All your applications reside in the Applications menu in the left of the top panel. No need to clutter up your desktop!
4) To access important folders, like your home folder etc, use the Places menu. You can also bookmark other folders you frequently use and they will show up in the Places menu.
5) There's no "Control Panel". Any configurations are done from the System menu or from the command line (don't be afraid of it!)
6) Your system tray (you know, the place where you have little icons of programs that mostly run in the background) which, in Windows, is in the lower right part of your screen, in Ubuntu it's in the right part of the top panel, toghether with the date and time.
7) You probably know there's no Start button. So, to shut down, log off or stand by, either use the options under System or click your name in the top right of the screen.

You might be confused at first, but you'll get used to it quickly :)

**Edit:** 8) There's a quicklaunch-like area next to the menus in the left part of the top panel. You can add items my simply right-clicking an application in the Applications menu and selecting "Add this launcher to panel".
You can always rearrange your panels, add panels, delete panels, add widgets to your panels, remove widgets from your panels etc. :). You'll find Ubuntu very customizable.

---

### Post by Dan Again on 2009-02-24
This is awesome, guys.  I am already starting a folder of useful Linux links with Linux Alternative Project, GetDeb and this site, of course...pass on any other useful Linux related webpages you have.

I have a new question.  My computer arrives on Friday (woot!) and I am scheduling a time to work with my brother getting Linux up and running on Saturday.  My brother suggested I spend a few hours with the computer to make sure everything works (he seems mostly concerned about hardware).  I plan on doing this Friday evening, but I'm not 100% certain what are the important things for me to check and how I go about checking them or knowing if they are in fact working properly.  I looked online for a pre-fab comprehensive checklist of what to look for, but wasn't really able to find one.  Any thoughts?

---

### Post by kestrel1 on 2009-02-24
With a laptop you need to check that your wireless functions if you are able to. You also need to check the keyboard & touchpad (mouse). The CD/DVD writer needs to be checked for writing & reading of disk's. The screen needs to be checked for any white or black dots, too many & you need to complain (these are mostly OK these days though.)
Make sure that the battery has a good life after a full charge. I would suggest using the battery as much as possible. I would also suggest a full discharge every so often before a full charge. To do this you can set the machine running & press the appropriate key to enter the BIOS & let it run out before connecting back to the mains power to recharge. (this is the way I have found best)
Make sure the machine doesn't get too hot & that the processor fan runs correctly (it may not run all of the time, this is normal)
On an eyecandy & usefulness point, if you have ever seen a MAC with OSX installed you would have seen the dock. This can be achieved with a few programs in Linux & I would suggest Cairo-Dock. Find out how to install it here: [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)
These are my suggestions, others may think of others.
Bet you can't wait until Friday :lolflag:

---

### Post by Znupi on 2009-02-24
In terms of useful websites, [http://help.ubuntu.com/](http://help.ubuntu.com/) is a very good resource. Especially the community contributed documentation -- you can find docs for almost anything! For example the Cairo Dock documentation kestrel1 gave you :)

As to testing the hardware -- why do you want to test it? Is it one of those laptops on which your warranty is voided if you install another operating system?

As to customizing, well, I've customized Ubuntu to the moon and back (to see some of the customizations I've done check out [my deviantart gallery](http://znupi.deviantart.com/gallery/#Screenshots)) but I usually end up using stock Ubuntu. For window manager and gtk themes, I suggest [http://gnome-look.org/](http://gnome-look.org/). For tweaking and customizing your desktop effects (read: Compiz) see [enabling extra effects](https://help.ubuntu.com/8.10/desktop-effects/C/compiz-configure-advanced.html). Cairo Dock seems really cool (never used it myself) but it also seems a bit too cool and may be resource heavy. If you want a simpler dock, try [Avant Window Navigator](https://help.ubuntu.com/community/AvantWindowNavigator) (AWN for short). Although, I wouldn't recommend installing such an application from start because it's going to involve quite a lot of tinkering (removing default panels, adding useful widgets to other panels etc.) which you may not enjoy, at first. Once you get a bit comfortable with Ubuntu, you can try all sorts of things.

One cool thing I like about Linux is that if you make a separate /home partition, you can mess your system up in any way you want because at any point you can just reinstall and all your preferences, files, e-mails etc. will be there.

I guess it's going to be quite a weekend for you. Have fun! :)

---

### Post by kestrel1 on 2009-02-24
> **Znupi said:**
>  Cairo Dock seems really cool (never used it myself) but it also seems a bit too cool and may be resource heavy. 
Just a quick one. Not found Cairo-Dock to be heavy on resources. My system isn't a super fast machine & Cairo runs like a dream. Just checked & it is using 15.4mb of ram. Some might say that is heavy, I don't think it too bad. I used AWN before, but couldn't really get it to do what I wanted. Only my opinion of course.

---

### Post by Dan Again on 2009-02-26
Hey Everyone,
Thanks for the responses re doing a hardware check on the laptop.  UPS initially said it was scheduled to arrive on Friday, but their tracking page now shows it out for delivery today (Thursday)...woot!

I attempted to boot Intrepid Ibex from the disc onto my desktop last night and it was a no go.  Tried twice after first using built in tool to check the accuracy of the disk.  First time desktop took quite a bit of time to load, which I was expecting.  Once desktop loaded computer was still moving much more slowly than I would have expected.  Initially there were two empty error messages that disappeared by themselves.  Desktop loaded with two icons that seemed to respond to having the mouse floated over them.  I tried to open a drop down menu from the top left side of desktop and got an error message about a panel problem loading the trash applet.  After that it the icons disappeared and I was still able to move the mouse, but menus weren't responding to mouse clicks.  I couldn't figure out any other way to get out of there but by force shutting down the system by holding the power button.  Second go round desktop seemed to load a little bit faster, but there was zero response.  Mouse did not work at all, did not hear any start up noises coming from the comp.  Had to force shut down again.

Some questions...

1) Does this sound like a common problem...is there a simple way to fix it?

2) Is there a better way to quit an unresponsive Ubuntu (other than force shut down) that I don't know about?

3) Do I need to have an anti virus package for Ubuntu, or is that pretty much completely unnecessary?

I'm not stressing too much...this desktop is pretty old and janky and I didn't really have very high hopes for things.  Furthermore, given the fact that I only have like 8.5 gigs of HDD space (12%) remaining, I wasn't ever really planning on running Ubuntu full time on this system anyways.  On the positive side, all the clean up stuff I did in preparation for trying to run Ubuntu has made Windows run much more quickly and smoothly.

Anyways, just wanted to give another update on my transition to Linux and see what y'all think.  Thanks in advance for your input.

Dan

---

### Post by Znupi on 2009-02-26
Hm, that's sad. It would've been nice if you could make the full transition to Linux. It seems like a hardware recognition problem (probably the graphics card?) or there could be a problem with your optic drive. The optic drive is very stressed when running a Live CD as you can imagine. I've had similar problems with other machines. On to your questions:
1) It doesn't sound like a common problem (to me). You could try using another CD drive if you have one available. If it still doesn't work, it's a hardware recognition problem. You can also try booting Hardy which is a stable release and it might support your hardware.
2) It depends on how unresponsive it is. You can try different combinations like Ctrl+Alt+Backspace, Ctrl+Alt+F1 etc. Ideally you will get to a shell where you'll be able to stop unresponsive processes and shut down (use `sudo poweroff').
3) No, you don't need any antivirus / antispam / firewall. Sure, there are solutions such as ClamAV and iptables for the paranoid :)

Hope your laptop works better. Cheers :)

---

### Post by Dan Again on 2009-02-28
Okay...so my laptop came, and it's awesome.  Totally happy with it.

I made my recovery CD's and then prepared to shrink the Windows partition.  I ended up getting it down to 30G using GParted.

I then used GParted to make a large extended partition which I divided up into four logical partitions - 2 Linux "/" partitions 30G each (to be used while upgrading, per my brother's advice), a large /home and shared data partition and a 1.5G swap partition.

I downloaded the ext2IFS app, but I'm having trouble getting it to work.  It creates the drive letter for my shared partition in Windows, but then when I try to access it through Windows Explorer it says I need to reformat it.  When I run mountdiag it doesn't return anything.  Can anyone help?

---

### Post by Dan Again on 2009-02-28
Still haven't been able to get ext2IFS to work.  Also tried downloading ext2FSD and had basically the same result.

Did I do something wrong when I created my partitions...is there an important step I missed?

[SCREENSHOT]("http://s615.photobucket.com/albums/tt240/DanForbes/?action=view&current=AcerLaptopPartitionScreenshot3-1-20.jpg")

---

### Post by Dan Again on 2009-03-01
So, Ubuntu is up and running on my computer and I have to say I don't think things really could have gone any better.

Everything seemed to pretty much work seamlessly out of the box other than ext2IFS.  After doing a little bit of research on that I was able to come up with a solution.  ext2IFS is designed to manage data formatted to 128b, but Ubuntu 8.10 is set to format at 256b.  After installing Ubuntu I went back to the partition that I mounted my /home settings and planned on mounting my documents to and reformatted it as a 128b partition.  Of course after doing this I had to remount /home, but that was not a big deal.  Everything is working great now and I am able to create icons on my Ubuntu desktop from Windows and open the files on my /home partition in Windows.

All things considered this was a relatively easy transition...I think a large part of that is due to the fact that when I purchased my computer I made sure that the model I was getting had a good history of Linux compatability.  I would recommend the Acer AS6930 to anyone looking to do something similar.

Thanks again to everyone for all your suggestions and advice!

---

### Post by Znupi on 2009-03-01
I'm glad you got it working :). But the real challenge starts now. Since you decided to dual boot, you will be tempted to boot Windows all the time. This is how I switched to Linux. At first, I was booting Windows most of the time, and Linux only when I was bored and wanted to hack a few things. Slowly but steadily I started booting more and more into Linux and doing more and more of my daily activities in it until one day I was able to completely wipe Windows. Good luck and happy laptoping :)

Any questions you bump into, don't hesitate to post on this forum :)

---

### Post by Dan Again on 2009-03-01
Okay...I'm having some issues with AWN.  I can get programs to launch from the dock just fine, but I cannot figure out how to add a link to launch a document.  Furthermore, I would like to add Fast User Switch Applet (the button that is located in upper right side of desktop that lets you hibernate, switch user, shut down, etc), but am having trouble getting it to work.  Any ideas?

---

### Post by kestrel1 on 2009-03-02
I don't use AWN myself as I prefer Cairo-dock. With Cairo you can just drag a launcher to it & it is added or if you right click you can add a launcher manually. You may be able to do the same with AWN. With regard to the switcher, you add an applet with Cairo, may be similar in AWN.

---

### Post by Znupi on 2009-03-02
I'm not sure AWN can handle gnome-panel applets. As for linking to a document, just create a launcher to "gnome-open /path/to/your/file" and it should do the trick :)

---

### Post by Dan Again on 2009-03-02
Okay, I got solutions to my problems...

**To get put a shortcut for an OpenOffice document on AWN...**

AWN Preferences > Launchers > Add > 

Set the command to "ooffice -calc [path of your file]"

Please note that spaces and special characters are indicated by placing a "\" in front of them.  For example, if you have a file named "Cool Things.ods" and it is located in a folder called "Dan's Stuff", you would write the command as follows "ooffice -calc /home/dan/documents/dan\'s\ stuff/cool\ things.ods"...assuming that the folder and document are located in /home/[your login name]/documents

You can set the name, description and icon as whatever you'd like.

**To get shutdown menu on AWN...**

I downloaded an app called KShutDown and made a launcher for it on AWN.

I had to do a little tweaking to get it to work in Ubuntu 8.10, if it doesn't work for you try the following...

KShutDown > Settings > Configure KShutDown > Actions

Click on the action that needs to be edited and click "Edit."  I'm not 100% certain that I have the right commands for Shutdown and Restart, but the commands to lock the computer and log off are...

"gnome-screensaver-command --lock" (Locks computer)
"/usr/bin/gnome-session-save --kill --silent" (Log off)

I also got **the answer to another problem** I was having.  Every time I logged out or shut down the computer, my **num lock would turn off**.  This is aggravating if you have a number in your username or password and are accustomed to using the ten key pad to type it in...if you don't remember to turn num lock on each time, the first time you try to log in you get an error message.  To fix this problem...

First go to Synaptic Package Manager and install numlockx.  Then...

Alt+F2 > "sudo nautilus" (make sure "Run in terminal" is checked) > enter your password > File System > etc > gdm > Init > Default

Right click on Default > Properties > Permissions > Access (set to Read & Write)

Now open Default and choose "Display".  This will open a text document.  Near the very end of the document you should find a line that says "exit 0".  Above that line, add...

"if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi"

Now save the changes and close out of the document.  Done.  Make sure to change the permission on Default back to "Read Only" before closing the file browser or else you will have to re-open Nautilus with the "sudo" command in order to change it back.

**And one more solution I found to an AWN problem...**

If you add a Launcher to AWN by simply typing the program's name as the command, then you will not be able to edit that program's name or comments.  However, if you type the command as "[name of program] %u", then you will be able to edit these things.

[B]
Okay, now I have a couple of questions for you guys...[/B]

1) What are the proper commands for Shutdown and Restart?

2) In AWN Preferences > Launchers there is a Launcher in the list that does not have a name and the little icon off to the left of where the name would be is some gears.  I do not know where this came from and I cannot get rid of it.  It's not really that big of a deal because the Launcher does not show up on AWN proper, but it's kind of annoying and I'd like to get rid of it.  Anyone?

---

### Post by kestrel1 on 2009-03-02
To use the shutdown command you need to be root, so it would be```
sudo shutdown -h now
```
& to restart```
sudo reboot
``` or ```
sudo shutdown -r now
```
This will ask for a password though & is run from the terminal.

---

### Post by Znupi on 2009-03-02
1) There's also
```
sudo poweroff
```
2) It's a known bug. I don't know if you can do anything about it. Here's a [bug report](https://bugs.launchpad.net/awn/+bug/275884) I filed and they said they had fixed it.

As to logging out, check out [Quit applet](http://wiki.awn-project.org/Quit_applet). :)

---

### Post by kestrel1 on 2009-03-02
Of course if you use Cairo-Dock instead there is an aplet that works for logoff, restart, shutdown etc.

---

### Post by Dan Again on 2009-03-03
Figured it out...**use gksudo, not sudo**.  Gksudo allows you to open graphical interface to enter password, which is needed to run poweroff and reboot commands.  God that was driving me crazy...

---

### Post by kestrel1 on 2009-03-03
You may find it rather annoying to keep typing in the password, that is why I suggested Cairo-Dock.

---

### Post by Znupi on 2009-03-03
Did you try the Quit applet?

---

### Post by Dan Again on 2009-03-04
The Quit applet that is offered through AWN?  I did try that one and for some reason I did not like it...can't quite remember why.

Typing in the password does not bother me.  I am happy with this solution.

---

### Post by Dan Again on 2009-03-04
I'm currently trying to use the GLMatrix screensaver, but sometimes it does not work.  If I just let me computer sit for three minutes, screen fades away as if it's going to start GLMatrix, but then screen just stays black.  If I use my shutdown app to lock the computer, then the screensaver works fine no problem.  I think after I've run it once manually, it will run fine on its own, but I'm not 100% sure.

I read that this is due to a problem between GLMatrix and CompizConfig.  Does anyone know a workaround?  Does CompizConfig actually enable settings, or does it just make it more easy to change them.  If I delete CompizConfig, will my computer lose the ability to do Desktop Cube.  Will all the settings I saved (like the picture on top of the cube) be deleted?
Is there another Matrix type screensaver that looks cool and does not have this problem?  I tried the other Matrix screensaver that comes with Intrepid, but I thought it was kind of cheesy.

---

