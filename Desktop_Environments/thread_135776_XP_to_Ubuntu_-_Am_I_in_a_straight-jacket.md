---
title: "XP to Ubuntu - Am I in a straight-jacket?"
date: 2006-02-24
forum: Desktop Environments
---

### Post by Blind-Summit on 2006-02-24
Hi everyone. I have been using Ubuntu for a few weeks now. I was so pleased to have a totally free, open source and community driven OS that I became a new user with great enthusiasm. I have grown up using the usual Microsoft Windows OS and becase of that, I am having big problems.

I am slowly getting used to the command line, but this is so restrictive. I understand the use of sudo instead of root, but this is making things so very tiresome for moving files and folders quickly. 

I am looking for someone to tell me where I am going wrong!

Under windows, copy and past couldn't be easier. New files and folders are made with such ease. In Ubuntu I am using mkdir rmdir and cp etc etc - this is so inefficient! I have briefly read up on a chown command and I set my home directory to 777. I can now use that a bit more freely, but I also have a new error when I login about permissions.

Please - this is a cry for help. I really want to be an Ubuntu user, but if every simple task is restricted to command line - then why shouldn't I just use XP?

---

### Post by Swiss on 2006-02-24
As for Copy/Paste use Ctrl-c for copy & Ctrl-v for paste.
To create a new folder, go to the desktop, right click and select "new folder"



Swiss

---

### Post by suRoot on 2006-02-24
You already own your home directory - there should have been no need to change permissions.

Give us an example of what you're trying to do.  What are you trying to copy - from where, to where & as whom?

---

### Post by codejunkie on 2006-02-24
[QUOTE=Blind-Summit]Hi everyone. I have been using Ubuntu for a few weeks now. I was so pleased to have a totally free, open source and community driven OS that I became a new user with great enthusiasm. I have grown up using the usual Microsoft Windows OS and becase of that, I am having big problems.

I am slowly getting used to the command line, but this is so restrictive. I understand the use of sudo instead of root, but this is making things so very tiresome for moving files and folders quickly. 

I am looking for someone to tell me where I am going wrong!

Under windows, copy and past couldn't be easier. New files and folders are made with such ease. In Ubuntu I am using mkdir rmdir and cp etc etc - this is so inefficient! I have briefly read up on a chown command and I set my home directory to 777. I can now use that a bit more freely, but I also have a new error when I login about permissions.

Please - this is a cry for help. I really want to be an Ubuntu user, but if every simple task is restricted to command line - then why shouldn't I just use XP?[/QUOTE]
this might make it easier for you, press alt+F2, open a terminal, or create a desktop launcher and enter the command```
gksudo nautilus
```and now you can move files however and where ever you want as root through a gui. just be carefull in how you use it because you can damage your system if you move or delete the wrong file.

---

### Post by wylfing on 2006-02-24
Or perhaps he has simply not yet discovered "File Browser"? Go to Applications > Accessories > File Browser. That should look very familiar to you.

---

### Post by SVFUSiON on 2006-02-24
Welcome to the community. you'll get used to the command line real fast.

---

### Post by Swiss on 2006-02-24
I need to learn CMD Line... Where is a good place to learn?

---

### Post by Iandefor on 2006-02-24
[quote=Blind-Summit]Please - this is a cry for help. I really want to be an Ubuntu user, but if every simple task is restricted to command line - then why shouldn't I just use XP?[/quote] Hullo. 

Places menu -> Home folder. Right click in the window- the first option is "Create Folder".

About the permissions error during login- can we see the error message? It'll help us help you.

---

### Post by Iandefor on 2006-02-24
[quote=Swiss]I need to learn CMD Line... Where is a good place to learn?[/quote] Man pages. If you have a command you want documentation on, ```
man [command]
``` For an introduction,```
man intro
``` Another good source might be [BASH Help- A Bash Tutorial]("http://www.hypexr.org/bash_tutorial.php").
And Kyral posted a pretty good [howto for beginners]("http://www.ubuntuforums.org/showthread.php?t=73885"). Hope this helps.

---

### Post by wylfing on 2006-02-24
I don't want to hijack the thread, but **Swiss** you should search for such questions in the Ubuntu Wiki, where you will find abundant answers. Try these two pages, for example:

[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands)
[https://wiki.ubuntu.com/CommandlineHowto](https://wiki.ubuntu.com/CommandlineHowto)

---

### Post by jchau on 2006-02-24
You should not chmod your home directory to 777.  This basically means that anyone with access to you computer can change your your home directory files (especially if you do a chmod -R ).  Normally, you would not want to give group or others write permissions to you home directory because doing so will allow them to change your files / settings / startup scripts.

---

### Post by az on 2006-02-24
[QUOTE=Blind-Summit] but this is making things so very tiresome for moving files and folders quickly. 
...

Under windows, copy and past couldn't be easier. New files and folders are made with such ease. In Ubuntu I am using mkdir rmdir and cp etc etc - this is so inefficient! I have briefly read up on a chown command and I set my home directory to 777. I can now use that a bit more freely, but I also have a new error when I login about permissions.

Please - this is a cry for help. I really want to be an Ubuntu user, but if every simple task is restricted to command line - then why shouldn't I just use XP?[/QUOTE]

Don't do that.

You should use your home directory for your personal stuff.  There should be very little that you need to copy move create and delete as root.

---

### Post by Swiss on 2006-02-24
I didn't know about the wiki, but I guess I do now... ;)  Thanks.

---

### Post by Blind-Summit on 2006-02-24
Wow, thanks for the replies. I wasn't expecting this many. I am new to linux but i'm not retarded!! I can do a few simple commands with the terminal like moving through folders and making / deleting with sudo commands

I guess i don't know how the files and folders are laid out compared to windows. Things like windows "program files" I see would be the same as /etc folder?

I understand the "home" folder is like XPs "my documents" and I can save and play with stuff there, but I can't even make a shortcut to the mounted NTFS drives on the desktop. I know I must sound like such an idiot but I have done the ususal google searches and can't find anything but keyboard shortcuts. I have mounted 3 drives in mnt/ folder and just like a shortcut on the desktop.

Under XP i would laugh at how simple this is!

Other things include working out what all the folders basically do. Under windows I could tell you about program files is where apps are installed, system32 holds drivers and then my documents is where you save stuff etc

My other really big niggle is SPDIF sound (I fixed my other niddle of dual screens \\:D/  ugh so happy!) I have an ASUS A7N8X board with onboard digital SPDIF port. I want to run this so my amp for surround sound but i have found no decent answer.

Thanks for your help guys - I really appreciate it. Sometimes it can be a little daunting as this is all pretty new!

---

### Post by JoshHendo on 2006-02-24
You do not have to use the command line. No one does. It is only for people that want to play around with their system. To copy and paste something, just click and hold what you want to copy, hold down ctrl, then drage and drope it where you want it to copy to. Same as Windows. The only thing that I do use the command line for is to install programs, though one thing I have noticed is that if I have a deb file on the desktop, that is included in Synaptic and I can install it via that, so I don't have to use the command line if I don't want to at all. Trust me, you feel weird to Ubuntu because it is DIFFERENT. Everyone feels weird using something that is different.

---

### Post by jchau on 2006-02-24
[QUOTE=Blind-Summit]Wow, thanks for the replies. I wasn't expecting this many. I am new to linux but i'm not retarded!! I can do a few simple commands with the terminal like moving through folders and making / deleting with sudo commands

I guess i don't know how the files and folders are laid out compared to windows. Things like windows "program files" I see would be the same as /etc folder?

I understand the "home" folder is like XPs "my documents" and I can save and play with stuff there, but I can't even make a shortcut to the mounted NTFS drives on the desktop. I know I must sound like such an idiot but I have done the ususal google searches and can't find anything but keyboard shortcuts. I have mounted 3 drives in mnt/ folder and just like a shortcut on the desktop.

Under XP i would laugh at how simple this is!

Other things include working out what all the folders basically do. Under windows I could tell you about program files is where apps are installed, system32 holds drivers and then my documents is where you save stuff etc

My other really big niggle is SPDIF sound (I fixed my other niddle of dual screens \\:D/  ugh so happy!) I have an ASUS A7N8X board with onboard digital SPDIF port. I want to run this so my amp for surround sound but i have found no decent answer.

Thanks for your help guys - I really appreciate it. Sometimes it can be a little daunting as this is all pretty new![/QUOTE]


Umm, /etc is not equiv to C:\Program Files.  You mainly put system wide configurations in /etc.  /bin /usr/bin and /usr/local/bin are more like Program Files.

---

### Post by jchau on 2006-02-24
Oh, and you can create links like the shortcuts in windows with:
```
ln -s *link_to_here* *place_link_here*
```

---

### Post by Blind-Summit on 2006-02-24
Roger that. I will spend a few mins looking through the folders and seeing what's what. I may look up some stuff on google on the folder structures.

Anyway

1. Shortcuts - still need to make those? EDIT - thanks jchau :D

ok - now ho do i get rid of the little padlock icon and the blue arrow (i realise the arrow means shortcut) I used to have thse links looking like harddrive icons


2. SPDIF / digital 5.1 audio out?

Alex

---

### Post by Blind-Summit on 2006-02-25
Heh, everyone goes blank on me when it comes to the audio setup.

OK, that arror message I was getting is this:


```
Your $HOME\.dmrc file has the incorrent permissions and is being ignored. This prevents the default session from being saved The file should be owned by the user and have 644 permissions
```

I guess this is because I followed another post amount chown -R 777 to let me edit files and folders.

---

### Post by tmahmood on 2006-02-25
Have you tried the Volume Control?
goto volume manager then preference
There you'll find all options to make your 5.1 system work.. :)
I turn on Wave surround, tone, Wave Center, Bass, Treble, PCM and do some settings :) and It works

---

### Post by slux on 2006-02-25
Command line not efficient? I usually hear the complete opposite, people claim to be much, much faster with it (which may be true in some cases but not in others such as navigating directories and looking for a certain file in a long list of them)

As others have pointed, there's certainly no need for the command line for a user's file management anyway and you shouldn't be touching much of the stuff outside your home directory by hand most of the time. If you have something like a windows fat32 disk mounted you should arrange for that too to be accessible by your regular user(s) instead of mucking around as root.

You don't need to run ln -s for symlinks in gnome. just drag the folder to your desktop and press ctrl-shift. This should show an icon resembling a chain as part of the cursor and letting go will create a link. Another way is right-clicking and selecting "Make a link" and dragging that wherever you want to afterwards.

You should be able to change the icons if you go to the properties dialog of a link and click on the icon, /usr/share/pixmaps is the folder you should look for. The padlock's signaling that you do not have write access to the NTFS mount. I guess you could also do this with a launcher if you really want to get rid of the padlock. In that case right click on the desktop, select new launcher and fill in "nautilus <path-to-mount>" as the command line.

---

### Post by Blind-Summit on 2006-02-25
[QUOTE=tmahmood]Have you tried the Volume Control?
goto volume manager then preference
There you'll find all options to make your 5.1 system work.. :)
I turn on Wave surround, tone, Wave Center, Bass, Treble, PCM and do some settings :) and It works[/QUOTE]

I'm new to Linux, not stupid!!

I can get the SPDIF to output audio with that ALSA hw,2 whatever but this is not 5.1. I will give the short cuts a go and I have a FAT32 setup espscially for using under Ubuntu and Windoze

Thanks for the help so far guys!!! Just need the sound sorted then I am happy :KS

---

### Post by GeneralZod on 2006-02-25
[QUOTE=Blind-Summit]
Other things include working out what all the folders basically do. Under windows I could tell you about program files is where apps are installed, system32 holds drivers and then my documents is where you save stuff etc
[/QUOTE]

I've been using Linux full-time for quite a while now, and I neither know nor care what any of the UNIX folders are for ;)

Seriously, there is pretty much no analogue to Program Files as an installed application will be spread out all over the place (libraries in one place; executables in another; system-wide settings in another; documentation in yet another; per person settings in your /home;  etc).  It's very rare that you'll need to know any of these - in fact, I personally have never had occasion to poke around in any of these places :) There is a link somewhere explaining what directories correspond to what in UNIX-y systems, though, if you're curious - I'll see if I can dig it up.

Edit:

This is the one, I think:

[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

---

### Post by aysiu on 2006-02-25
[QUOTE=GeneralZod]I've been using Linux full-time for quite a while now, and I neither know nor care what any of the UNIX folders are for ;)[/QUOTE] Likewise. In fact, the only times I've had to know that my Windows programs were in C:\Program Files were when I needed to find the .exe launcher.

In Ubuntu, you don't need to know the "launchers" are in /usr/bin
You can just type the command, and it'll run. If I create a launcher with the command ```
gimp
``` I know it'll launch GIMP. I don't have to know where all the GIMP files are.

These are the system files I've had to get to know:
/etc/apt/sources.list
/etc/fstab
/boot/grub/menu.lst
/usr/lib/mozilla-firefox/plugins
/etc/kde3/kdm/kdmrc
/usr/share/apps/kdm/themes
/usr/share/pixmaps
/usr/share/icons

I think that's about it.

---

### Post by deathbyswiftwind on 2006-02-25
I would just like to tell you I believe you are picking the best linux out there. I have tried so many other distros out there and none of them are as pleasing to me as ubuntu. With cedega I can play all my Windoze games even fast in linux and I love the features the ubuntu team offers. Linux is a tad tricky to get used to at first but once you learn it youll love it. The best of luck to you. Also these forums are filled with so many well knowledge linux vets that basically ask and you shall recieve. They are willing to share their knowledge so there is no reason to ever look back

---

### Post by Blind-Summit on 2006-02-26
Again, thanks for the replies. My new understand would therefore be where Windoze has a folder for each program containing everything that app needs to run (more or less), Ubuntu will share stuff all over the place. I am happier about the whole "only need the home folder" stuff now. I also have a FAT32 drive that I want to write to though as i will probably want to share things between OSs

I am going to try out that game thingy cedega - would like to be able to run a fe woldschool games like Diablo 2 :D

I also found out that my touch slider for volume works now for some reason. That Autotatix seems pretty damn good. I have an MX5000 keyboard and MX1000 mouse (logitech) but is there any way to get all the features to work? Some sort of logitech clone?

Is there anything else that you all use that's worth installing? I really need some audio and video editing software as I do a lot of home recording (Cubase SX level) and video editing (Vegas Video) - what are the best replacements for this?

Thanks again

Alex

---

### Post by Joey French on 2006-02-26
> I also found out that my touch slider for volume works now for some reason. That Autotatix seems pretty damn good. I have an MX5000 keyboard and MX1000 mouse (logitech) but is there any way to get all the features to work? Some sort of logitech clone?

Some features on multimdia keyboards do not have drivers to provide full functionality. This is the case with my MS Wireless Desktop. I simply configured the non-working multimedia keys with xbindkeys. This is not ideal (the ideal would be a native linux driver), but hey, it only took a few minutes, and I don't think MS is gonna provide linux drivers anytime soon...:rolleyes: 

> Is there anything else that you all use that's worth installing? I really need some audio and video editing software as I do a lot of home recording (Cubase SX level) and video editing (Vegas Video) - what are the best replacements for this?


I used Cubase and other Win apps for sound for years. There are some strong audio programs for linux such as Ardour, Rosegarden, Hydrogen, etc. You may want to check out [this page]("http://ubuntustudio.com/wiki/index.php/Welcome%2C_Musicians%21") for more info.

Joey French

---

### Post by cdsboy on 2006-02-26
if you want to copy a whole folder really easily all you have to do is cp -R *path to folder* *path to where you want to the folder to go* it seems to work for me and it is really fast.

---

### Post by Blind-Summit on 2006-02-26
I'm really trying to make shortcuts not copy folders. 

Many thanks for that audio apps link - will have a look. I'll give that bind keys function a go as well.

Talking of other apps - amsn is lame and gaim does the job - but no audio / video chat. I know skype is good for that but not many people will convert. MSN is unfortunatley my main haunt. Any ideas for audio video?

---

### Post by ronmarley1 on 2006-02-26
[QUOTE=Swiss]I need to learn CMD Line... Where is a good place to learn?[/QUOTE]

This site relly helped me.
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by Iandefor on 2006-02-26
[quote=Blind-Summit]Is there anything else that you all use that's worth installing? I really need some audio and video editing software as I do a lot of home recording (Cubase SX level) and video editing (Vegas Video) - what are the best replacements for this?

Thanks again

Alex[/quote] Kino and LiVES for video edting. Kino will accept DV input (I don't know about LiVES). I don't know about their quality (my desktop setup is pretty basic, and I'm not even going to try to make them work), but they're both free.

[Kino]("http://www.kinodv.org/")
[LiVES]("http://lives.sourceforge.net/")  

Kino can be had via Automatix, and LiVES has an Ubuntu repository. Check their downloads section for more details.

Audacity isn't that bad in terms of an audio editor.

---

### Post by Blind-Summit on 2006-02-28
Sometimes Microshaft can really piss you off. Outlook was trying to "configure" itself as does every office app when I open it. So I said sod it. I'm done with this useless OS. I've not covered everything with Ubuntu yet, but I can't wait to get myself settled in properly and ditch M$ Winblows for good.

I've already got one mate to order the Ubuntu disks and I shall be shouting this from the rooftops and one day, people will buy a new PC and DEMAND linux distros and not be force fed this tired lame windows corporate crap.

The help I have been given so far, and the warm welcome has been such a nice change. I've started to customise my desktop a little, and it's sharting to feel like home \\:D/

---

### Post by thespazzz on 2006-02-28
[QUOTE=Blind-Summit]Again, thanks for the replies. My new understand would therefore be where Windoze has a folder for each program containing everything that app needs to run (more or less), Ubuntu will share stuff all over the place. I am happier about the whole "only need the home folder" stuff now. I also have a FAT32 drive that I want to write to though as i will probably want to share things between OSs

I am going to try out that game thingy cedega - would like to be able to run a fe woldschool games like Diablo 2 :D

I also found out that my touch slider for volume works now for some reason. That Autotatix seems pretty damn good. I have an MX5000 keyboard and MX1000 mouse (logitech) but is there any way to get all the features to work? Some sort of logitech clone?

Is there anything else that you all use that's worth installing? I really need some audio and video editing software as I do a lot of home recording (Cubase SX level) and video editing (Vegas Video) - what are the best replacements for this?

Thanks again

Alex[/QUOTE]

I've recently started playing with a program called Kino which I belive is a KDE based application.  It should work fine in Ubuntu however and it seems to be a decent video editor.  I don't know how powerfull it is because i've not played with it a lot yet.

---

### Post by thespazzz on 2006-02-28
[QUOTE=Blind-Summit]Sometimes Microshaft can really piss you off. Outlook was trying to "configure" itself as does every office app when I open it. So I said sod it. I'm done with this useless OS. I've not covered everything with Ubuntu yet, but I can't wait to get myself settled in properly and ditch M$ Winblows for good.

I've already got one mate to order the Ubuntu disks and I shall be shouting this from the rooftops and one day, people will buy a new PC and DEMAND linux distros and not be force fed this tired lame windows corporate crap.

The help I have been given so far, and the warm welcome has been such a nice change. I've started to customise my desktop a little, and it's sharting to feel like home \\:D/[/QUOTE]

*nods* As far as Linux desktops go you really can't beat Ubuntu.  It can be hard at first but once to slog through that initial adjustment and get the system working and then start actualy using it you learn pretty fast.  Eventualy you need less and less time to figure out how to do something though I usualy go hunting for command's from time to time.

Just a word of advice.  And just give me a second to put my flame protection suit on *Zip* Ok there we go. *heh*

Keep windows on your system for at least the first few months.  I know your sick of Micro$haft.  I hate them too.  However there are still programs that work alot better in Windows and have no Linux equivelent.  Leave yourself that safty net and that way if something goes wrong and you need to do something for school or work, if push comes to shove you can always go back and do it in the enviorment you know then come back to Ubuntu later when your not pressured for time and figure out how to make it work there.  I still have Windows on my box.  I don't have much installed on it, Open Office, Firefox, Orbiter and FlightSimulator are about it.  But I have it and I need it.. and the way I see it... I paid for the darn thing I might as well have it around.

---

### Post by Blind-Summit on 2006-02-28
[QUOTE=jchau]You should not chmod your home directory to 777.  This basically means that anyone with access to you computer can change your your home directory files (especially if you do a chmod -R ).  Normally, you would not want to give group or others write permissions to you home directory because doing so will allow them to change your files / settings / startup scripts.[/QUOTE]

If I go back and CHMOD to 644, will this all be OK again?

I'm giving Kino a go - looks ok so far, but will see what I can do with it. Last thing is 3D software. I'm new to the whole 3D design anyway, but I recently got the open source "Blender" and a nice big tutorial guide with that. Does it run on Ubuntu or can anyone suggest a good free alternative?

---

### Post by Blind-Summit on 2006-02-28
[QUOTE=thespazzz]*nods* As far as Linux desktops go you really can't beat Ubuntu.  It can be hard at first but once to slog through that initial adjustment and get the system working and then start actualy using it you learn pretty fast.  Eventualy you need less and less time to figure out how to do something though I usualy go hunting for command's from time to time.

Just a word of advice.  And just give me a second to put my flame protection suit on *Zip* Ok there we go. *heh*

Keep windows on your system for at least the first few months.  I know your sick of Micro$haft.  I hate them too.  However there are still programs that work alot better in Windows and have no Linux equivelent.  Leave yourself that safty net and that way if something goes wrong and you need to do something for school or work, if push comes to shove you can always go back and do it in the enviorment you know then come back to Ubuntu later when your not pressured for time and figure out how to make it work there.  I still have Windows on my box.  I don't have much installed on it, Open Office, Firefox, Orbiter and FlightSimulator are about it.  But I have it and I need it.. and the way I see it... I paid for the darn thing I might as well have it around.[/QUOTE]

Point taken. I think I'm scarred for life with it anyway. and XP can do certain things that I am really fluid with using. But have you seen Vista? Oh my god. There is rumour of needing 2GB of RAM to run it at a sensible rate. I can't image how bad it's going to be. They need to totally rethink the whole idea.

---

### Post by thespazzz on 2006-02-28
[QUOTE=Blind-Summit]Point taken. I think I'm scarred for life with it anyway. and XP can do certain things that I am really fluid with using. But have you seen Vista? Oh my god. There is rumour of needing 2GB of RAM to run it at a sensible rate. I can't image how bad it's going to be. They need to totally rethink the whole idea.[/QUOTE]

Vista.. Blech... I'll probobly end up needing to buy it simply because there are certian programs I need and they won't run under Ubuntu even with WINE and CEDEGA.  Your right though the hardware requirements they're suposedly going to be asking for it are absurd.  Your just now really getting to the point where systems with 1GB of RAM are becomeing common place.  I don't really belive they'll be requiring 2GB just for the OS.  This is M$ so you never know.

---

### Post by Blind-Summit on 2006-02-28
Something is going to get smahed in a second. This is why I hate permissions. I own the PC, the software - everything and this is telling me I don't have permissions? OMFG I could scream.

sudo chmod -R /home 700 is all I want to do - just need to restore the permissions back to avoid that startup warning.

Then i need to edit the grub menu with win XP up the top as my second keyboard that I use to press up / down on the grub boot is messed up.

Please someone help :mad: :mad: :mad:

EDIT - sorry about the swear word. Removed 
Alex

---

### Post by Swiss on 2006-02-28
Please don't use foul words! There are people younger then yourself here!

---

### Post by Thund3rstruck on 2006-02-28
Install the Xfe File Browser
sudo apt-get install xfe

This is the greatest file manager ever. It's similar to the fantastic xplorer2 for windows that gives you a 2 pane view of the file system. Moving files and folders are a breeze!

---

### Post by Blind-Summit on 2006-05-13
I now get this error :(

/var/run/sudo writable by non-owner (040777), should be mode 0700

the folder is owned by root and is set to 777 - any ideas of how to get this back

---

### Post by malius on 2006-05-13
It would appear that you have inadvertently changed the owner of your home area to root.

One way to solve this is:

**sudo chown -R <username> ~<username>/**

**Note:**  Change the username in the above command.

i.e. sudo chown -R malius ~malius/

Now, if you still have permission issues, you can simply type:

**chmod -R 700 ~/**

**Note:** don't use the sudo command here.

---

### Post by Blind-Summit on 2006-05-15
didn't work. first of all, i can't run any sudo commands as it says that the permissions are set wrong on the /var/run/sudo folder - hence not being able to run sudo

i tried the chmod and that failed also:

blind-summit@BreezyBadger:/var/run/sudo$ chmod -R 700 ~/
chmod: changing permissions of `/home/blind-summit/docs': Operation not permitted
chmod: changing permissions of `/home/blind-summit/docs/images': Operation not permitted
chmod: changing permissions of `/home/blind-summit/docs/images/skins': Operation not permitted

---

### Post by blackgibson on 2006-05-15
[QUOTE=Blind-Summit]MSN is unfortunatley my main haunt. Any ideas for audio video?[/QUOTE]
There aren't any MSN clients with voice and / or video under an OSS license. Gaim + the gaimvv stuff + farsight may give us a free speech IM with MSN confrencing eventually, but I wouldn't hold my breath waiting for it to happen any time soon. If plain old free for use is good enough for you than you might want to try [Mercury]("http://www.mercury.to/")

Oh yea.. welcome to Linux ;)

---

### Post by steve.horsley on 2006-05-15
[QUOTE=Blind-Summit]I now get this error :(

/var/run/sudo writable by non-owner (040777), should be mode 0700

the folder is owned by root and is set to 777 - any ideas of how to get this back[/QUOTE]

You will have to fix this from another system, because this one is borked and won't let you in. The easiest way is to boot the installer CD. At the prompt, type **rescue** and press enter. After loading, it will ask you which partition to chroot to - I hope you know which partition you are on. This will give you a root prompt at which you can enter the command:
chmod 700 /var/run/sudo
Then reboot your normal Linux and see what the next problem is.

Do you think you did this yourself? I am just wondering if someone else has gotten into your system.

Don't fight the permissions thing. It's a fight you will lose. Learn to live with it. If you need to do anything outside your home directory (which should be rare once you have the machine set up to your liking), then use sudo in front of the commands, or if you are doing a lot use **sudo su** to get a root prompt, or **gksudo nautilus** to get a root file manager. I set the background preference of my root nautilus to pale red (yes allright, pink) to remind me to be careful. I understand that Vista will not give full admin rights to users by default, so the permissions thing is coming to Vista too - passwords before you can install software or change global system settings etc. Even MS is admitting it is necessary.

If you have done a **chmod -R** on the whole filesystem from root down, it may be easier to reinstall than fix all the necessary exceptions. Sorry.

---

### Post by Blind-Summit on 2006-05-16
blackgibson - thanks for the welcome. It was just a nice feature - I presume skype still works with audio and video?

I still don't have my audio setup properly to give 5.1 :(

Anyway - the chmod stuff - yeah, I got confused. Normally you can give windows some spanking and you are in control. It seems that I have to behave under linux. The red background (pink ;)) seems like a really good idea. Would like to know who to do that if you have a minute - also - what other folders are good to mark up with red?

I will try that boot fix. I think it's only that one folder but I'm not sure. My home directory also seems wrong.

What are the usual things to backup before a reinstall? I know the drive mount config file is useful. Ditto my display setup as I have dual screen. Can someone let me have a brief list?

Thanks for this great support. I've not known such a great community.

Alex

---

### Post by varunus on 2006-05-16
Making shortcuts can be done without the command line too.  Just open your file browser, go to the folder you want, and then drag the folder to the desktop with the middle mouse button.  Then, select "link here."  You'll get a shortcut.

Also, if you want an application on your desktop, click "applications->submenu" and then right click on the application in the menu, and choose "add launcher to desktop."

If you're backing up, aside from your personal documents in your home directory, you may want to back up your "/etc/fstab' file (holds drive mounting) and your '/etc/X11/xorg.conf' file (holds your display configuration).  Other than that, most of the system files will be regenerated.  Permission problems can be a large issue to solve, and can cause many problems in the long run.  One person I know was rendered unable to print due to some chmod mistakes...I recommend reinstalling.

---

### Post by Blind-Summit on 2006-05-16
Thanks for that info. Just wanted to be sure. It's always the case when you reinstall XP and then swaer because you forgot the contents of my documents.

Anyway - I booted into the rescue mode and went through all that - I then got the choice of partitions to boot to.

I have 2 physical HDDs which are SDA and SDB - nothing is on HDB so we can ignore that.

I have my table split like this:

[IMG]http://www.blind-summit-host.co.uk/partitions.jpg[/IMG]

I tried to boot to the one that I thought was the main linux partition (and not the windows or linux swap partition) I had an error message for one of them (I think I got the wrong one) and it stopped me in my tracks.

I chose another and this didn't give an error as such - but said that it couldn't find a shell to boot to? Is said that it could take me to some prompt and I could carry on there, but it wasn't right as I couldn't do the chmod command.

Shall I just re-install?

---

### Post by steve.horsley on 2006-05-17
Sorry for the delay. I think you may well find it easier to just reinstall. 

Don't go changing permissions or ownerships outside of your home directory unless you are really sure. Sudo, in particular, checks the permissions of its files and just refuses to play if it doesn't like them, and because Ubuntu doesn't normally have a root password this means permanent lockout. But you already discovered that.

For the reinstall, the easiest way for you will be to use the windows disk manager to delete the two unknown partitions (presumably your swap and root linux partitions) and then you can just tell the Ubuntu installer to use the available free space. This avoids struggling with an unfamiliar and rather cryptic partitioner in the installer.

---

### Post by ed_agamemnon on 2006-05-17
i think he means things like copying files from CDs or windows shares where Ubuntu changes the files and folders to read-only by default. Can be a bit of a pain when you have to chown everything...

he's right that having to sudo file creation in the filesystem is a faff in linux when windows was so easy; but then, there are pretty serious security advantages for doing it the linux way.

---

### Post by Blind-Summit on 2006-05-17
I guess I'm still just pretty new to it all still. I don't just want to take one look and run away back to windows because this has the grounds to be a great system. I love how easy it is to install things with just a simple command line, the huge increase in stability - and the great reduction in viruses and spyware. Having said all that - they way I could just float around my files and folders in windows was pretty simple. I know people have said command line can be quicker and easier - but just 2 or 3 clicks of the mouse and i can do all sorts of things to files and folders?

People have also said not to rey and look for replacements for windows applications. This phased me a bit, because this is one of the things I would look for in changing OS. OK, so I'm not going to look for applications with identical features as that's daft. All I want to be able to do is edit music and video (I do home recording and I like to edit videos). I have found that the audio capabilities of Ubuntu are a little lacking. I use a digital out SPDIF into a home cinema amp to power a 5.1 setup, but I've had no luck with this in Ubuntu :( I have heard of a linuxaudio site or maybe ubuntuaudio - will have to google that one!

Anyway - I will reinstall and backup those config files first. See you on the otherside!

---

### Post by changlinn on 2006-05-17
[QUOTE=blackgibson]There aren't any MSN clients with voice and / or video under an OSS license. 
*snip*[/QUOTE]
Uh yeah there is [amsn]("http://amsn.sourceforge.net/"), it is a bit kludgey with its need to forward ports to get it to work properly, but still it solves the need.
The program I am really after is Dameware mini-remote or chriscontrol, that is all I need to move 100%, I am going to put a bounty up as such a thing doesn't currently exist afaik.

---

### Post by Blind-Summit on 2006-07-15
So it's been 5 months as a fulltime user of Ubuntu. I guess this is enough for me to pass comment about the overall experience.

](*,) 

That sums it up nicely. I wanted to give this a proper go - so I decided to not run back to XP when I got stuck - but to look around for the applications or packages I needed. Software installation was a breeze! My biggest issue has been configuration. My sound as I have said in many other posts is far from setup. My mouse is laggy, I cannot do any audio or video editing even close to the standard I could on windows. HTML and web coding is pretty bad - there seem to be no design studios WYSIWYG editors with a preview / design / hard code window like front page on XP.

Every time I log on - I have to tune XMMS to a different audio device driver. I have to manually turn my wifi on, i can't use my webcam over IM, I cannot voice chat with my friends, my keyboard and mouse do not work fully, image editing is OK with GIMP, my iPod is near to impossible to update with songs (very slow to update the song list - even over USB2) I cannot copy over videos such as m4v / mp4, I cannot connect my camera via USB to get the photos off it.

I have no reason to delete windows from my system yet as Ubuntu has a long way to go. Newer PC systems are harder and harder for Ubunto to cope with.

If I have to end on a positive note - the support and friendliness of these forums is unsurpassed, the ease of installing and updating is very very good and the menu system is simple.

---

### Post by xyz on 2006-07-15
How about checking out Ubuntu Studio Project for a start?
You could find answers/ask questions to folks directly involved in this. Hope it helps.
[http://www.ubuntuforums.org/forumdisplay.php?f=128](http://www.ubuntuforums.org/forumdisplay.php?f=128)

---

### Post by SuperMike on 2006-07-15
For a quicker command line where you don't have to type sudo all the time, I'll show you how, but please be careful when using this especially if you're a new user. You could fry your system by typing the wrong command. For instance, on Windows, you wouldn't want to throw away your Windows folder, would you? No, you wouldn't. The same goes with Ubuntu. By forcing you to do sudo all the time, newbies can't easily throw away their important folders like /usr, /boot, /etc, etc.

From a command line, do:

sudo passwd root

Type in your current login password for yourself. Now it will prompt you for the root password. Make it a tough one and then verify it and it's done. From here on out at command line, if you tire of doing sudo all the time, you can type 'su' and type in the root password. You'll become root at command line. When you want to leave that mode and go back to yourself, type 'exit'. Type 'exit' again to get out of the Terminal window, should you want to do that.

However, saying this, note that you *can* work with your home directory in the Nautilus file explorer by choosing the Applications menu, then Accessories, then File Browser. Once there, find your /home/<you> directory (if it's not already shown) and you can right-click in here, choose New, Folder, New Empty Document, and so on. You can also right-click and delete folders.

---

### Post by fogster74 on 2006-07-16
I feel for you, and I totally empaphise with everything you have said. I'm an MSc computer science student (postgrad) who has tried numerous distros on an Inspiron 8600. My friebds tell me "leave Windows! leave Windows! leave Windows!".

It's taken me 72 hours of solid tinkering to get dual screens running on my laptop. I've created a total of 92 xorg.conf backup files - if that's any measure of what I've been through. I've now got dual screen monitors - but with no control options whatsoever. I can't change the resolution on either screen, I can't switch from dual screen to clone, I can't turn the laptop screen off and just use the external monitor. It took me six horus to install my printer. These things under Windows would have been instant.

Why am I persevering?  A number of reasons 

1) I don't like Microsoft's monopoly position. It bothers me.
2) I don't see how I'll ever cut it in computing if I don't know unix (or at least linux), especially dealing with server stuff
3) I want to progamme in PHP and develop on a LAMP server - I've heard this is so much easier to set up on Linux than Windows.

However - the lack of driver support is truly appaling. Even in Windows 3.x (remember the good old days - adjusting extended memory, losding drivers 'high', checking for conflicting resources), driver installation worked better than this.

So, what's the solution? The problem is one of economics - lots of people use Microsoft, so it's profitable for hardware companies to produce drivers for those people. We can campaign, picket, shout, beg and scream for these companies to produce drivers for us linux users - but the economic argument will always stand in the way. Hence the answer here could possibly be legislation...

'Legislation', you ask? How would that help? Quite simply, make it law that any company selling hardware for Windows must also produce Linux drivers too. The effect on the linux community would be massive. Remember when Microsoft started licencing companies (with the launch of Windows 95) to put "Designed for Microsost Windows 95" on the box of everything from a sound card to a pre-assembled PC? Imagine the same thing, but for linux. No more 72 hours for a task that would take less than 30 seconds in Windows. You'd switch it on, and it would work. This has, in my opinion, to be the single biggest issue in preventing wide-spread adoption of linux by the desktop community.

It stands to reason that the software etc will follow. With so many issues with sound cards, video cards and cameras not efficiently working with our operating system, it is no wonder that there are few users demanding programs for this type of hardware - no point programming amsn to support video calls when the webcam doesn't work! Also, if there were 5 million more linux users, there's a huge base to provide software for.

And finally, and here's where I'm sure I'm going to get shot down in flames, I'm not sure how the whole Open Source thing works from a financial persepctive? Does this mean any company releasing a program that they've spent possibly millions of dollares developing, that they have no ownership of their code? That they can't sue if the code is copied? That they can't charge for the software? Until some industrial heavyweights get behind making software, Linux will still, surely, be for enthusiasts only. And can we really expect Electronic Arts to be producing the next-generation game, for free? With no ownership rights? I'm probably being incredibly naiive in saying this and probably have totally missed the point of "Open Source" - but perhaps that's another issue, one of needing to educate those who don't understand our platform.

Anyway, hope this hasn't bored you all too much but, as a new-to-linux user (I think I'll persevere with this distro!) I thought my initial impression may be helpful...

Fogster

---

### Post by fogster74 on 2006-07-16
PS meant to say  not looking for help with the above issues (I've posted those on the appropriate parts of the site), but just wanted to share my thoughts.

---

### Post by punkybouy on 2006-07-16
For what it is worth I assigned a password to the root user and sometimes instead of sudo I just do an "su" and type in the root password.  Seems to work.  I bought the book "Ubuntu Hacks" and it has been very helpful.

---

### Post by Blind-Summit on 2006-07-25
I don't know what this sudo issus is - Maybe I brought it up a while back (I didn't re-read my old posts) but command line is a sinch now. I managed to work out how to build stuff from source so I feel pretty good.

Still got sound issues especially with Skype - really annoying as I used that a lot to speak to my mate in London. Ideally want to use my webcam mic with Skype and output the sound via SPDIF to my external amp.

On a very very plus side - I have UT2004 installed and running with sound - hell yeah! Thate game is amazing. Never realised it could be installed on Windows, Linux and Mac all from the same DVD!!

I agree with fogster - it should be mandatory to include drivers for all OSs

---

