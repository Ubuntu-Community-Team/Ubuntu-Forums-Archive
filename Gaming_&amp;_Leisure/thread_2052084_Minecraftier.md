---
title: "Minecraftier"
date: 2012-09-02
forum: Gaming &amp; Leisure
---

### Post by DarkAmbient on 2012-09-02
[SIZE=2]UPDATED: 2013-08-15. Do not use, this is outdated![/SIZE]

[SIZE="3"]Minecraftier is a lightweight app for managing Minecraft.[/SIZE]
It can do this for you:

[LIST]
[*] Install Minecraft and add a systemwide launcher to start it
[*] Update LWJGL (can fix blackscreen, mouse-issues or various glitches)
[*] Reserve RAM for Minecraft
[*] Create new Minecraft-launchers wherever you want em 
[*] Reset Minecraft (You'll get a vanilla install, except that savefiles is intact)
[*] Launch Minecraft
[*] Debug Minecraft (Saves runtime-log to user-selected location)
[*] Uninstall Minecraft
[*] Install Java (OpenJDK 7)
[*] Backup all your savefiles and settings
[*] Restore a previously created backup
[*] Help you translate glyphs from ingame (Standard Galactic Alphabet)
[*] Install Forge & Forge Modloader for Minecraft 1.5.2
[*] Install Optifine HD for Minecraft 1.5.2, adds loads of graphic-options to Minecraft (highly recommended!)
[*] Assist with installing Mods
[*] And a few more 
[/LIST]
**[SIZE=4][Download latest version from Github]("https://github.com/rikardjo/minecraftier/archive/master.zip")[/SIZE]**

_Instructions:_
Download Minecraftier to your computer
Open up the archive and enter the "minecraftier-master" folder
Drag minecraftier to your desktop (or any other folder)
Doubleclick minecraftier and choose run

 _Alternatively you may download to your desktop using this command:_
```
cd `xdg-user-dir DESKTOP` && wget https://github.com/rikardjo/minecraftier/archive/master.zip && unzip -j master.zip minecraftier-master/minecraftier -d . && rm master.zip
``` 

In case your unable to run it, and it only opens up in a texteditor, [make it executable first]("http://askubuntu.com/questions/122428/how-to-run-sh-file").

If it still won't run, paste this in a terminal to make Nautilus to ask you if you want to run executable files: 
```
gsettings set org.gnome.nautilus.preferences executable-text-activation ask
```
Then try doubleclicking minecraftier again.

[COLOR="#FF8C00"][SIZE=3]Video Instructions:[/SIZE]
[SIZE=4][http://www.youtube.com/watch?v=hTsfVXdccMs](http://www.youtube.com/watch?v=hTsfVXdccMs)[/SIZE][/COLOR]

**Screenshot:**

[IMG]http://ubuntuone.com/4Q4orkpgs8LqOKmj4XeXRF[/IMG]

You'll see a GPLv3 license-agreement upon start, I wanted to be both clear and a cool kid so I added it. Upon accepting your total freedom of using Minecraftier it stores a settingsfile in /tmp so that you don't need to accept every time you run it. (only after each reboot, but that will be fixed soon)

More ideas when I get the time is to improve the ugly glyph-translator. It's something I threw together in JS rather quick. Also splitting up menus into several sub-windows might be something. Feel free to come up with ideas. :)

And enjoy Minecraftier!

---

### Post by asdk on 2012-09-02
> **DarkAmbient said:**
> Wrote this installer some time ago, but updated it a lot today.

[IMG]http://ubuntuone.com/5k91UQf4TSTCb698b2vIof[/IMG]

[SIZE="3"]Download: **[Minecraft-installer]("http://ubuntuone.com/57ir7n3xuMJIzi87CdUvcM")**[/SIZE]

Download the installer, rightclick it and go to the permissions tab. Then make it executable. (not sure on the correct string in english Ubuntu, someone fill me in please)

Then with a few button-clicks you may:

[LIST=1]
[*] Install Minecraft w/ custom launcher added to your menu/dash
[*] Fix the black-screen-issue
[*] Set amount of memory to reserve for Minecraft
[*] Uninstall Minecraft
[*] Install java or remove+install other version of java
[/LIST]

Please try it and let me know of any bugs, suggestion... This is all written from Arch Linux, so I'm unable to try "Ubuntu-specific stuff" like apt-get.. I plan on updating both this post and this script so.. help

It depends on packages zenity, xterm and wget, but I'm pretty sure all packages comes with Ubuntu.(?)

In the future i plan on adding progressbar for downloads. And an option (a working one) to backup the players worlds. Also cross-distro-support. 

Have funzy!
Yes, you are right that you have to right click > Properties >  permissions > Allow executing file as a program. And yes, executable is what you would call it in English :P

Is it supposed to create a new txt file called 0? 

Minecraft does not install at all when I try to install it. This could be my machine, I'm not sure, Terminal is saying "unexpected operator" and "illegal number", if you need the exact terminal text, just ask.

When I had the .minecraft folder ready and working, it never recognized minecraft as installed, so everything else did not work.

---

### Post by DarkAmbient on 2012-09-03
> **asdk said:**
> Yes, you are right that you have to right click > Properties >  permissions > Allow executing file as a program. And yes, executable is what you would call it in English :P

Is it supposed to create a new txt file called 0? 

Minecraft does not install at all when I try to install it. This could be my machine, I'm not sure, Terminal is saying "unexpected operator" and "illegal number", if you need the exact terminal text, just ask.

When I had the .minecraft folder ready and working, it never recognized minecraft as installed, so everything else did not work.

Thanks for your reply! Bash is a peculiar langauge, but I'm pretty sure I've fixed all the issues now. Even added a visual progress-bar on downloads while at it. Will update mainpost in a min. :)

---

### Post by asdk on 2012-09-03
Thanks for the update, everything works now :)

---

### Post by kostkon on 2012-09-03
Nice app.

---

### Post by DarkAmbient on 2012-09-04
> **kostkon said:**
> Nice app.

thank you! :) And its just been updated to work even better!

Edit: updated it again.. had a typo/error in the script, until now. :)

---

### Post by RLewellen on 2012-09-11
Hello, Dark Ambient

Thanks so much for all the effort you have put into this downloader/fixer/etc

I do however receive an error when I attempt to run your bash script

> ./minecraftinstaller120906.sh: 314: ./minecraftinstaller120906.sh: Bad substitutionAny help is much obliged!

---

### Post by DarkAmbient on 2012-09-12
> **RLewellen said:**
> Hello, Dark Ambient

Thanks so much for all the effort you have put into this downloader/fixer/etc

I do however receive an error when I attempt to run your bash script

Any help is much obliged!

Hi, thank you for mentioned it! :)

I have honestly no idea what caused the bad substitution. Re-tested all the options again, no errors on my front. Might be due to me running Arch and is unable to try it on Ubuntu atm (Ubuntu-machine is broken) But i've fiddled around a lot now, will upload in a few sec. I'd love it if you could try again and let me know if it works. :)

It doesn't seem like I can edit first post anymore, so I'll make a new one.

---

### Post by DarkAmbient on 2012-09-12
[CENTER][SIZE="3"]Updated 2012-09-12[/SIZE][/CENTER]

[SIZE="3"]Minecraftinstaller[/SIZE] can do this for you:

[LIST]
[*] Install Minecraft and add a launcher to your application-menu / dash
[*] Fix the black-screen-issue (by updating the LWJGL-files)
[*] Set amount of RAM to reserve for Minecraft
[*] Uninstall Minecraft
[*] Install java (or a different version of java)
[*] (next release) Backup your worlds
[/LIST]
[CENTER]
(Oh and don't laugh at my computers cccp-specs) ;)
[IMG]http://ubuntuone.com/0BV4I7yKIyIfIvvd0vI5Mo[/IMG]


[SIZE="3"]>> **[DOWNLOAD-LINK]("http://ubuntuone.com/4JMPJtAIa4GIBiYB6CMotZ")** << [/SIZE]
[/CENTER]


It is totally safe to install Minecraft with this installer even if you've been playing Minecraft on your computer since before. In fact, the minecraft.jar you normally start with is not needed and can be removed before/after installing using this.


_To run Minecraftinstaller:_

[I]Save file to your computer then rightclick it, choose properties
Go to the permissions-tab, then make it executable
Close properties and run the installer by doubleclicking[/I]


_Alternatively you may start from the terminal with:_
```
./minecraftinstaller120912.sh
```

_or make it executable from the terminal:_

```
chmod +x minecraftinstaller120912.sh
``` then start by doubleclicking minecraftinstaller120912.sh

(In both terminal-examples we assume you downloaded the minecraftinstaller to your homefolder)


_update 2012/09/12:_
Reworked the way the installer figure out stuff, and how it presents it.
Added a funny clock, since last version was made. =)
Users can now go to this thread from inside the installer.
No duplicates of downloaded files anymore 
  
In the future I plan on making the option to backup your worlds to work. 

Let me know if something is not working, or if you got any suggestions.

Enjoy!

---

### Post by justifier on 2012-09-16
No matter what i try it sticks on Done Loading, I see this is a common issue and everything i try and cannot get it to move on past it. any ideas?

---

### Post by justifier on 2012-09-16
dont worry got it!

---

### Post by contributor on 2012-09-17
I am using it and it is working properly without showing any error. :) Nice work man.

---

### Post by DarkAmbient on 2012-10-04
Hi, sorry for no response, been out of town. What error did you encounter justifier? 

Glad you liked it, contributor, I'm planning on adding support for modding and other stuff (like backup).. no idea on how modding works with Minecraft. But will look into it! Ciao!

---

### Post by TooManyFeet on 2012-10-04
> **DarkAmbient said:**
> Hi, sorry for no response, been out of town. What error did you encounter justifier? 

Glad you liked it, contributor, I'm planning on adding support for modding and other stuff (like backup).. no idea on how modding works with Minecraft. But will look into it! Ciao!

Does it update all the LJGL files (i.e. /bin and /bin/native)?  If it does that's extremely useful - even after playing MC for so long I *still* get the sticky key problem and have to install those libraries..

---

### Post by DarkAmbient on 2012-10-05
> **TooManyFeet said:**
> Does it update all the LJGL files (i.e. /bin and /bin/native)?  If it does that's extremely useful - even after playing MC for so long I *still* get the sticky key problem and have to install those libraries..

It replaces all of the lwjgl-files that Minecraft use yes. I've had some problems with sticky keys as well in the past. 



On a sidenote: if a moderator reads this. Could it be possible to ask for persmission to edit first post of this thread? I would like to update first post instead of posting updates in new ones. Thanks

---

### Post by will1982 on 2012-10-07
Nice program.

Thanks!

---

### Post by DarkAmbient on 2012-10-08
[CENTER][SIZE="3"]Updated 2012-10-08[/SIZE]

[SIZE="3"]>> **[DOWNLOAD-LINK]("http://ubuntuone.com/6Dh7W9yIAHr2yjtsQazdcw")** << [/SIZE][/CENTER]

[SIZE="3"]Minecraftinstaller[/SIZE] can do this for you:

[LIST]
[*] Install Minecraft and add a launcher to your application-menu / dash
[*] Add extra launcher to location of choice
[*] Update Minecrafts LWJGL-files to possible fix black-screen etc
[*] Set amount of RAM to reserve for Minecraft
[*] Uninstall Minecraft
[*] Backup your worlds, playerstat etc
[*] Restore backups... (good right) ;)
[*] Install java (or a different version of java)
[*] Minecraftinstaller now has a nice messagesystem
[*] Some more...
[/LIST]
[CENTER]

On Arch Linux (in my case without indicator-messages)
[IMG]http://ubuntuone.com/0N9DAzohShdm7reIFRPAmB[/IMG]

On Ubuntu 12.10 (indicator-messages should work)
[IMG]http://ubuntuone.com/5YwbAa3GXBPQVZPnM81Ac8[/IMG]


[SIZE="3"]>> **[DOWNLOAD-LINK]("http://ubuntuone.com/6Dh7W9yIAHr2yjtsQazdcw")** << [/SIZE]
[/CENTER]


If you already have Minecraft on your computer, installing Minecraft using this won't hurt your Minecraft-experience a bit. 


_To run Minecraftinstaller:_

[I]Save file to your computer then rightclick it, choose properties
Go to the permissions-tab, then make it executable
Close properties and run the installer by doubleclicking[/I]


_Alternatively you may start from the terminal with:_
```
bash minecraftinstaller121008.sh
```

_or make it executable from the terminal:_

```
chmod +x minecraftinstaller121008.sh
``` then start by doubleclicking minecraftinstaller121008.sh

(In both terminal-examples we assume you downloaded the minecraftinstaller to your homefolder)


As usual, let me know if something isn't working. I'm not here to pollute your Minecraft-experience in any way, but I take no responsibilities if anything doesn't go the way you want. But I can assure you that I've tested this script AAAA LOT! That's all, enjoy!

---

### Post by DarkAmbient on 2012-10-08
> **will1982 said:**
> Nice program.

Thanks!

Thank you, glad you like it. Let me know of what you think of the 0.8 version I just uploaded. :)

---

### Post by rainbatt on 2012-10-08
Link on 1st post not working.

---

### Post by gnihc11 on 2012-10-08
Got this error when double click on the installer,
Failed to run bash '-c' 'echo \'
[Desktop Entry]
Version=1.0
Type=Application
Name=Minecraft
Comment=Minecraft is a game about placing blocks to build anything you can imagine. At night monsters come out, make sure to build a shelter before that happens. It also has music by C418!
The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

How do I go round it?  I'm using GUI.

---

### Post by DarkAmbient on 2012-10-09
> **rainbatt said:**
> Link on 1st post not working.

Yea, Ubuntuforums don't allow editing posts for longer than 3 weeks. So no choice but to write a new one on each update, check a few posts up for a link like [SIZE="3"][this]("http://ubuntuone.com/6Dh7W9yIAHr2yjtsQazdcw")[/SIZE]

Edit: now they allow editing again. First post updated

[QUOTE=gnihc11]Got this error when double click on the installer,
Failed to run bash '-c' 'echo \'
[Desktop Entry]
Version=1.0
Type=Application
Name=Minecraft
Comment=Minecraft is a game about placing blocks to build anything you can imagine. At night monsters come out, make sure to build a shelter before that happens. It also has music by C418!
The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

How do I go round it? I'm using GUI.
[/QUOTE]

That's strange, what distribution/version are you using? Could you try this in a terminal and tell me the output?
```
dpkg -s bash sudo gksu zenity wget | grep 'Package\|Status'
```

That will tell you if you got all the packages required by Minecraftinstaller installed. (If you got the tool dpkg installed that is)

---

### Post by DarkAmbient on 2012-10-10
Took my time to update the installer with dependency-check upon start to prevent errors. Check pictures further down.

[CENTER][SIZE="4"] [Download MinecraftInstaller version 0.8.1]("http://ubuntuone.com/5xNXgBQbaYcvSwDIi8uIxg")[/SIZE][/CENTER]

MinecraftInstaller in Ubuntu 12.10:

[IMG]http://ubuntuone.com/5ApSSsNnfzkQOEY2T8Zrzh[/IMG]



MinecraftInstaller in Arch Linux:

[IMG]http://ubuntuone.com/3xN2Y84z8fLPRX37KVLSQT[/IMG] 


Fallbackmode, if we in this case don't have zenity installed. (All dependencies should come pre-installed with Ubuntu)

[IMG]http://ubuntuone.com/6iBYW5uKssvvAoYtekuSQ7[/IMG]

Please tell me if something doesn't work, Right now I can't find anything that doesn't behave like it should, which really is a good thing though. ;) Download link is furthest up if you wanna check it out. Enjoy!

---

### Post by insanity54 on 2012-10-11
Real nice, I'm loving the update lwjgl feature... No more [sticky keys]("https://getsatisfaction.com/mojang/topics/lwjgl_on_linux_needs_to_be_updated#reply_7249951")!

---

### Post by rx7145 on 2013-03-08
Thanks so much. 

Only problem I had was that I had not downloaded Java.

After that it worked like a charm.

Thanks again.

---

### Post by highfish42 on 2013-05-13
Hi man,

Nice installer :)

But I have still a problem:

I installed java and minecraft with your installer. The lwjgl updates as well. But if I start minecraft, after login, I get a black screen and afterwards it tells me, that minecraft is crashed. (I could send you the error log, if it would help you.)

Have you an idea whats wrong?
I'm using minecraft on Ubuntu 12.04 on a laptop with i7 and 8gb ram, the hardware should not be a problem.

Regards
Fish

---

### Post by DarkAmbient on 2013-05-14
Hey, glad you liked it. I'm not too keen with log-files, havn't used Java in years either. It's hard to tell if the issue would be with the installer, java or even Minecraft itself.

If you want, you could try run Minecraftier 0.9.2 (which i linked below) and pick Reset Minecraft. Then try run Minecraft again. 

Hope you get it solved!

EDIT: updated first post with link.

---

### Post by uganda on 2013-07-07
Hi,

first, I love Minecraftier, it makes things so easy!  I did the 'Install Optifine HD for Minecraft' and the extra options allowed me to tune the performance so it runs nicely on my PC.

However, not thinking about it much, I upgraded to Minecraft 1.6.1 now and all of a sudden all the options are gone, the fog is back on, etc. and it runs really slow :-(((  ...rest of family (kids) are not impressed :-/

Help!  Is there an update to Minecraftier coming?  Would I have to install a new Optifine?  What's the easiest way to do that?

Many many thanks for any help!

---

### Post by DarkAmbient on 2013-07-07
Hello uganda, and thanks for the nice feedback! 

Got today off, so if there is optifine-version for 1.6~ then I'll try to update Minecraftier and hopefully the github-master with it later today.

Edit: I've decieded to stick with the stable-non-manually-install-required-versions of Minecraft. It's a lot of work as 1.6.2 brings a new folder-structure once installed, not sure if it will stay that way or stick with the current structure once 1.6.2 become the latest default-version.

---

### Post by DarkAmbient on 2013-08-15
Updated master-version:

Fix: Now fetches correct and latest version (for Minecraft 1.5.2) of both Forge and Optifine.

Fix: Checks if Forge is installed before installing Optifine. Minecraft will crash if installed in wrong order.


Note: I got a branch which is loads of updates in advance to master-version. I will merge it with master once stable (or/and Minecraft 1.6.2 is latest default version)

---

### Post by geronl on 2013-08-15
I have no idea what is going, I am such a noob..

mkdir: created directory `/home/floyd/.icons'
mkdir: created directory `/home/floyd/.minecraft'
mkdir: created directory `/home/floyd/.minecraft/bin'
mkdir: created directory `/home/floyd/.minecraft/bin/natives'
asdf
java.io.FileNotFoundException: /home/floyd/.minecraft/lastlogin (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.java:137)
    at net.minecraft.LoginForm.readUsername(LoginForm.java:110)
    at net.minecraft.LoginForm.<init>(LoginForm.java:55)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:23)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:167)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:13)
/home/floyd/Desktop/minecraftier: line 990:  4936 Done                    echo message:"${welcomeMsg}"
      4937 Terminated              | zenity --notification --listen 2> mcistderr
/home/floyd/Desktop/minecraftier: line 990:  5008 Done                    echo message:"Minecraftier says:\n ${1}"
      5009 Terminated              | zenity --notification --listen 2> /dev/null
/home/floyd/Desktop/minecraftier: line 990:  5016 Done                    echo message:"Minecraftier says:\n ${1}"
      5017 Terminated              | zenity --notification --listen 2> /dev/null
asdf
java.io.FileNotFoundException: /home/floyd/.minecraft/lastlogin (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.java:137)
    at net.minecraft.LoginForm.readUsername(LoginForm.java:110)
    at net.minecraft.LoginForm.<init>(LoginForm.java:55)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:23)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:167)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:13)

---

### Post by geronl on 2013-08-15
Wait, I actually have to get Minecraft first, right? This isn't going to give me Minecraft?

---

### Post by DarkAmbient on 2013-08-16
Not sure on what you'r doing, looks like your running Minecraftier and trying to start Minecraft twice atleast? What happens then?


Oh, I uploaded a video-instruction for Minecraftier: [http://www.youtube.com/watch?v=hTsfVXdccMs](http://www.youtube.com/watch?v=hTsfVXdccMs)

Also added it to first post. Did you fetch and use Minecraftier something like that?

Edit: ofcourse this installs Minecraft for you as well.

---

