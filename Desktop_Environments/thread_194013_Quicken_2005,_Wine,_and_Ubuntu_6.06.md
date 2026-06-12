---
title: "Quicken 2005, Wine, and Ubuntu 6.06"
date: 2006-06-10
forum: Desktop Environments
---

### Post by irv on 2006-06-10
My biggest hangup from letting go of WinXP was Quicken 2005. I have years worth of data in it to let it go. Well, I can let go a little more now because I have Quicken 2005 working flawless in Ubuntu Dapper 6.06 under gnome with wine. First let me tell you I did a lot of installs and uninstalls of wine and Quicken to get it to work. I followed the how-to at  [http://www.ubuntuforums.org/forumdisplay.php?f=132]("http://www.ubuntuforums.org/forumdisplay.php?f=132") and it would have worked if I would have stopped before editing my source list to upgrade to the newer version of wine. The key is to stay at wine 0.9.5. The big thing with Quicken is it wants to use Internet Explorer to work with Quicken Bill Pay. I don't do any online banking so I can't say if there is any problems with that, But everything I do works great. I even mapped a drive to an external USB drive to backup my files. I did this with winecfg.

After installing wine 0.9.5 and winetools I setup the fake windows, installed the fonts and IE6.0 and did all the other Base setups. I made sure IE6.0 was working before installing Quicken 2005. After everything I did an online upgrade to Quicken and it went flawless. I also did not have any problems restoring my backup files. 

I really use Linux 99% of the time and 1% WinXP, so now I will use Linux 99.9% because I need WinXp for my GPS and MP3 Player. That will take up about .1% now. I guess I am like everyone else who has bought a copy of XP, I paid for it so I will keep it around for odd things I can't do will Linux yet. But I am working on it.

Let me add this in closing: When I did do the upgrade to wine, it screwed up my IE connection in Quicken and my displays in some of the windows in Quicken got messed up.

I hope this thread will help other who would like to use Quicken 2005 on Ubuntu 6.06. By the way the How-to I followed was by someone using 5.10 so this might work on 5.10 also.

---

### Post by djaya2 on 2006-07-14
Just wanted to say thanks and add my experience with Quicken Basic 2006 for anyone it might help.

First, thanks.  Getting Quicken to work was essential for me.  I'm having trouble with my tv card and webcam, but Quicken was the real holdup on abandoning WinXP.  I couldn't get it to work until I tried your method.  (I wish I could get adept-updater to stop telling me there's a wine update available, but that's no big deal.)

An addition:  After downgrading wine, I still had problems with windows within Quicken flickering and/or appearing too small and not being susceptible to resizing.  I right-clicked on the windows in question, messed with their settings, and the problems seem to be solved for now.  I think the main fixes were to get rid of animation and to have Kubuntu detect the problematic windows' settings.  (I use Kubuntu Dapper.)

Thanks again.

An addition---  My advice about windows settings wasn't so good because I didn't remember very well what I had done.  I poked around a bit more, and here's the solution to flickering/too small windows.  I'll use the "Split Transaction" dialogue window as an example because that's one of the ones that caused problems for me:

- Right click on the window's title bar
- Go to Advanced-->Special window settings
- Under 'Window types', I wasn't sure what type of window to call it, so I selected Normal, Dialogue, and Utility.  Being over-inclusive here is no problem because the very next step makes your setting more specific.
- In the Window Extra tab, make sure the 'Window title' box names the correct window.  (In this case, it should say 'Split Transaction'.)
- In the pull-down menu just under the 'Window title' box, select 'Exact Match'
- Now click on the "Geometry' tab
- check 'Size'
- Type in the size you want the window to be.  (In my case, '550,450' is just right.)

Finally, I can't believe this--  Although superficial aspects of the program aren't quite as seemless as on Xp, a few things actually work better in wine.

---

### Post by kkuzia on 2006-10-21
> **djaya2 said:**
> An addition---  My advice about windows settings wasn't so good because I didn't remember very well what I had done.  I poked around a bit more, and here's the solution to flickering/too small windows.  I'll use the "Split Transaction" dialogue window as an example because that's one of the ones that caused problems for me:

- Right click on the window's title bar
- Go to Advanced-->Special window settings
- Under 'Window types', I wasn't sure what type of window to call it, so I selected Normal, Dialogue, and Utility.  Being over-inclusive here is no problem because the very next step makes your setting more specific.
- In the Window Extra tab, make sure the 'Window title' box names the correct window.  (In this case, it should say 'Split Transaction'.)
- In the pull-down menu just under the 'Window title' box, select 'Exact Match'
- Now click on the "Geometry' tab
- check 'Size'
- Type in the size you want the window to be.  (In my case, '550,450' is just right.)

Finally, I can't believe this--  Although superficial aspects of the program aren't quite as seemless as on Xp, a few things actually work better in wine.

Now, there is where I am falling into a problem.  Most of the key stuff is working for me in Quicken when using Wine, but the real sticking point is that when I try to right-click on a malfunctioning Window's title bar, I am unable to get anything about "Advanced" or "Special" settings for Wine at all.  I am currently using Wine version 0.9.5, especially since I cannot get Quicken to work with 0.9.12.

Anyone have any ideas here?:confused:

---

### Post by perspectoff on 2007-08-14
I'm still looking for a faster way to get Quicken 2005 working under Wine in Ubuntu Feisty.

My method is quite roundabout, but at least I have a stable Quicken 2005.

From what I've read, Quicken 2005 under Wine needs to run under Win98 "emulation" mode of Wine. (yeah, yeah, don't flame me because I said emulation.)

It also needs to see Internet Explorer 6 installed to finish the installation routines. So here's what I did:

1) Installed an updated version of Wine from the budgetdedicated website (Wine HQ):

Added the repository key from the command line:

 wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add - 

Added the repositories in Administration-->Software Sources-->Third Party:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main 
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main 

I then reloaded the sources, and installed the wine package from Synaptic Package Manager (or could also use apt-get install wine).

2) Made sure the cabextract package was installed (either from Synpatic Package Manager or apt-get install cabextract). This is required to unpack M$ Windows cab archives.

3) Installed Internet Explorer 6 using IEs4LINUX (see [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu) ). This script installs IE6 effortlessly (unlike the struggles I had trying it without the script):

 wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux

I strongly suggest using all the defaults exactly. If you mess up the script installation, you are doomed :confused: .

3)Now you are ready to install Quicken 2005. 

Supposedly you can go to Wine Configuration and "Add application..." for the installer. Choose "windows 98" for the Windows, and under the "graphics" tab **UNCHECK** the option to "Allow the window manager to control the windows."

These steps appear to be crucial for Quicken programs.

Browse to find the installer on you CD ROM, "Add the application" for install.exe with the options as noted, and click "apply." (For some reason, if you click "OK" it does not save the settings).

Now go to Wine File and click on install.exe on the CD-ROM.

4)  Run Quicken 2005

Once installation has completed, you must run qw.exe in the Windows 98 mode, and again without allowing the window manager to control the windows. Go back to Wine Configuration, "Add application" and browse until you find qw.exe in the quicken folder on the pseudo c:\ drive. 

Now you must make a menu item or launcher to launch
 wine ""/home/*user*/.wine/drive_c/Program Files/Quicken/qw.exe""

That should work.

Other method:

Ok, it should work. It didn't quite work for me. So I cheated.

I installed a demo version of Codeweavers' Crossover Linux. Crossover Linux is quite nice, and I highly recommend it, if you can afford the $70 price tag for the professional. (They have a $40 standard version, but it only allows one user on one machine. That doesn't cut it for my family of 4). The 30 day demo, however, is free.

So I installed the demo. Maybe I'll buy Crossover Linux anyway. In the meantime, I installed IE6 and Windows 98 compatibility with  two clicks -- Crossover did the rest. Then I installed Quicken from the Crossover menu. That also was very nice: it prompted me to put-it in the CD-ROM and everything. It installed Quicken 2005 without me having to lift another finger.

Then it put menus on the menu bar, and a desktop icon for Quicken 2005. I clicked on the icon and everything ran, the first time. No tweaking. It updated automatically from the web, and imported all my files without a problem.

I checked reports, downloaded files; it seems to do everything I routinely do (I don't do online banking through Quicken, but instead download data files from my banks and credit cards and import them into Quicken. I store all my data on removable media, naturally. I don't trust Intuit.)

So, once I pay the registration fee to Crossover Linux I will have to do nothing else to run Quicken 2005.

But that didn't stop me from trying to get things to run under Wine. For some reason, my first install of quicken 2005 under Wine would not complete, and would not uninstall, either. So I cheated.

Cross Over Linux creates its own fake drive_c, and installs everything there. There is no cross-pollination of the Cross Over install and my original Wine installations. Any wine files that CrossOver needs, it puts in its own wine subdirectory, within the primary CrossOver directory. If you choose not to buy Crossover, you can erase all the files without harming your original Wine installation.

So I then looked for and found the Quicken folder in the CrossOver fake drive_c\Program Files\ and copied it, kit and caboodle, to the Wine fake drive_c folder\Program Files\ folder (first erasing my old crippled Quicken folder there, of course).

Now I re-created the qw.exe configuration ("Add application") so that it would a) use Win98 and b)not allow the window manager to control windows. Using Wine File, I again ran Quicken from the new folder (wine "/home/user/.wine/drive_c/Program Files/Quicken/wq.exe").

It worked, just as if had been running in CrossOver.

As a test, I uninstalled the CrossOver Linux and all the files in the CrossOver folders. The Wine version of Quicken 2005 still worked flawlessly.

So, probably there was something funny about the way I installed Quicken 2005 the first time under Wine.

Of course, that's the appeal of CrossOver Linux. It does everything for you. With Wine, if you make one little mistake, or don't accept the default settings of Wine installation scripts, things tend to get screwed up easily.

So, my next project is Paperport. If CrossOver Linux supports Paperport, then Windows will become a distant memory for me.

---

### Post by KenKaplan on 2007-10-09
Have you had any luck with Paperport? As soon as a new hd arrives, I will load it with Feisty Fawn, Crossover, Quicken 2005, and Paperport. I'm hoping this will all work together. I am currently fed up with WinXP!

---

### Post by freshspinach on 2007-10-10
I just got my Quicken XG 2007 running using VMWare in Feisty. Everything seems to work just fine.

---

