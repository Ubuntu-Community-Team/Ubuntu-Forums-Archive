---
title: "tray icon for compiz-fusion?"
date: 2007-07-09
forum: Desktop Effects &amp; Customization
---

### Post by amadeus266 on 2007-07-09
Anyone know if there is, or is going to be, a tray icon for Compiz-Fusion like the one for beryl-manager?

---

### Post by tgm4883 on 2007-07-10
I would say yes.  A quick google search found fusion-icon for fedora

---

### Post by luckyd on 2007-07-10
assuming you have the trevino repo

> sudo apt-get install git git-core compiz-dev

> git-clone git://anongit.opencompositing.org/users/crdlb/fusion-icon


> cd fusion-icon

> make

> sudo make install

alt+f2 fusion-icon

---

### Post by AndrewGene on 2007-07-10
Thanks!! That worked perfectly.

---

### Post by ermali86 on 2007-07-15
for me too. now playing with that icon :popcorn: hahaaha :P lol

thank you

---

### Post by coolen on 2007-07-23
Thanks for that! This was the final thing missing from my laptop with Fusion :)

---

### Post by BetaguyGZT on 2007-07-23
Works perfectly. Thanks. :guitar:

---

### Post by CowzRule on 2007-08-09
Here's a deb package for it

---

### Post by Cannon9559 on 2007-08-13
hmmm......doesn't seem to work for me
it installs the git fine, but then i can't get the files from:git-clone git://anongit.opencompositing.org/users/crdlb/fusi on-icon
any ideas?

---

### Post by Cannon9559 on 2007-08-13
lol, nvmind didn't see the space in the fusion   <<--Dunce:lolflag:

---

### Post by Cannon9559 on 2007-08-13
Wow, works great guys, thnx

---

### Post by schnupi on 2007-08-13
yap works great thanks!

---

### Post by mevets on 2007-08-14
For post 3,
> git-clone git://anongit.opencompositing.org/users/crdlb/fusi on-icon
should be
> git-clone git://anongit.opencompositing.org/users/crdlb/fusion-icon
** GOD, vB adds a space in fusion... you must delete it in order for it to work!

---

### Post by Paul133 on 2007-08-14
Is it necessary to do ```
make
``` before ```
sudo make install
``` It seems redundant.

---

### Post by coolen on 2007-08-15
The make command basically compiles all the different parts of the programs, giving you a nice, shiny exectuable at the end.
I imagine the install option puts that shiny executable somewhere, such as a path directory, and possibly does some other things (such as removing old versions).
Not redundant, considering that many who use GNU systems are programmers (I do assignments on my Linux machines). You wouldn't necessarily want them to go off into your filesystem, but keep them in the one spot for testing.

---

### Post by Paul133 on 2007-08-15
So it is important to do ```
make
``` before ```
sudo make install
```?

---

### Post by explemonk on 2007-08-15
> **Paul133 said:**
> So it is important to do ```
make
``` before ```
sudo make install
```?

In the case of fusion-icon, no.  make by itself will not do anything in this case except display instructions for using make install, because there is nothing to compile.  The makefile for fusion-icon just tells it to copy the python scripts to the directory you specify with make install.

---

### Post by coolen on 2007-08-15
Thanks to explemonk.
The make utility really doesn't have to do any compiling. It updates a set of files (by executing the specified commands) based on the dependancies of those files. For example, if I have an executable file that uses a header file I created, I'd list that header as one of its dependancies. If I run make, and the header has a more recent modification time than the executable, it'd run the commands I specify to recompile. This is all specified in the makefile, and can be quite complex for large projects.
You can use this principle with any command that can be run from the shell.

Generally, you'll use make to compile source code, in which case it would be important to run make before make install.

---

### Post by Paul133 on 2007-08-16
All right, thanks guys.

---

### Post by LuisC-SM on 2007-08-16
To the Original Author
Thanks so much!!!
Works like a charm

To CowsRule
Great Deb file... alos works with no single issue (Thanks A Lot !!)

Regards

Luis

---

### Post by CowzRule on 2007-08-16
> **LuisC-SM said:**
> To the Original Author
Thanks so much!!!
Works like a charm

To CowsRule
Great Deb file... alos works with no single issue (Thanks A Lot !!)

Regards

Luis

Cool :) Glad it worked for you.

---

### Post by indieboy445 on 2007-08-17
Wow, much thanks. This works fine in Gutsy too in case anyone was wondering

---

### Post by kushelmex on 2007-08-18
nice!

---

### Post by ubername on 2007-08-18
Hi

I installed fusion-icon by both command line method and deb package. In both cases when I activate the icon (either from terminal or by selecting menu item added by deb package) my entire screen freezes. windows lose all content, go white with grey borders, panels (i.e. where Applications, Places, System etc. appear) go grey. Mouse pointer continues to move but nothing else. Have to power off to get going again.

I'm using Gutsy. The reason I wanted the icon is because I can get compiz to work fine but it doesn't use 'emerald' themes. Rather it uses those which appear from the system>preferences>appearance option. I saw that in beryl you had to switch windows-decorator to emerald, but couldn't find anything in compizsettingsmanager, so though the icon might do the trick

Can anyone help

TIA

---

### Post by tgm4883 on 2007-08-18
The icon is in the repos in gutsy

---

### Post by ubername on 2007-08-18
> **tgm4883 said:**
> The icon is in the repos in gutsy

Thanks

My problem is not getting the fusion-icon installed, but getting to use it without crashing the GUI. Hope you can help

TIA

---

### Post by 5h4rk on 2007-08-19
> **ubername said:**
> Hi

I installed fusion-icon by both command line method and deb package. In both cases when I activate the icon (either from terminal or by selecting menu item added by deb package) my entire screen freezes. windows lose all content, go white with grey borders, panels (i.e. where Applications, Places, System etc. appear) go grey. Mouse pointer continues to move but nothing else. Have to power off to get going again.

I'm using Gutsy. The reason I wanted the icon is because I can get compiz to work fine but it doesn't use 'emerald' themes. Rather it uses those which appear from the system>preferences>appearance option. I saw that in beryl you had to switch windows-decorator to emerald, but couldn't find anything in compizsettingsmanager, so though the icon might do the trick

Can anyone help

TIA

I got the same problem with Feisty...

---

### Post by coolen on 2007-08-19
I had a problem on my laptop where many windows went black. Try enabling Indirect Rendering from the icon menu. You should be able to do this from Metacity, then switch over to Fusion.
Loose Binding may help, but I doubt it. I used that option to stop Totem crashing when I went fullscreen, though, so it might come in handy.
Did you have Fusion working before, without the icon? If not, it may be a problem with your Xorg configuration, or a driver issue. Off the top of my head, if AddARGBVisuals is missing from your xorg.conf, it could cause some major issues.

---

### Post by FuturePilot on 2007-08-19
> **CowzRule said:**
> Here's a deb package for it

Wow! Thanks! Awesome! I missed the Beryl Manager.

---

### Post by 5h4rk on 2007-08-23
What is the command to run it startup programs in sessions?

---

### Post by coolen on 2007-08-23
fusion-icon

---

### Post by 5h4rk on 2007-08-23
thanks, I did "compiz-icon", that's why was not starting haha...

---

### Post by Dark Star on 2007-08-23
> **CowzRule said:**
> Here's a deb package for it

Whoaaa thanks a ton jkukst helped my 1'st problem solved :guitar:

---

### Post by Inxsible on 2007-08-23
I don't see why you would need the icon in the tray?

I set up all the plugins once the way I like it through the CCSM. Once that's done, all I do is start CF and all plugins selected work. Why would I need an additional icon to go to the CCSM and of course eat a bit more memory?

Are there other features that the fusion-icon provide other than simply allowing you to get to the CCSM?

---

### Post by tgm4883 on 2007-08-23
> **Inxsible said:**
> I don't see why you would need the icon in the tray?

I set up all the plugins once the way I like it through the CCSM. Once that's done, all I do is start CF and all plugins selected work. Why would I need an additional icon to go to the CCSM and of course eat a bit more memory?

Are there other features that the fusion-icon provide other than simply allowing you to get to the CCSM?

I think you can quickly turn it on and off

---

### Post by FuturePilot on 2007-08-23
> **Inxsible said:**
> I don't see why you would need the icon in the tray?

I set up all the plugins once the way I like it through the CCSM. Once that's done, all I do is start CF and all plugins selected work. Why would I need an additional icon to go to the CCSM and of course eat a bit more memory?

Are there other features that the fusion-icon provide other than simply allowing you to get to the CCSM?

It also lets you open the Emerald theme manger if you use Emerald. It lets you easily switch back to Metacity if you need to do so. Along with a couple CF options like the --loose-bindings (increases performance for Nvidia users) option and the --indirect-rendering option (workaround for the black window bug) and it also lets you switch window decorators.
Pretty much it does what Beryl Manager did.

---

### Post by _simon_ on 2007-08-23
> **tgm4883 said:**
> The icon is in the repos in gutsy

What's it called in the repo?

I can't seem to find it...

---

### Post by Inxsible on 2007-08-23
> **FuturePilot said:**
> It also lets you open the Emerald theme manger if you use Emerald. It lets you easily switch back to Metacity if you need to do so. Along with a couple CF options like the --loose-bindings (increases performance for Nvidia users) option and the --indirect-rendering option (workaround for the black window bug) and it also lets you switch window decorators.
Pretty much it does what Beryl Manager did.

1) I don't use Emerald..but I might give it a try

2) Doesn't the crash-handler plugin do the same - ie switch to metacity in event of crash. I wouldn't wanna go to metacity in any other scenario ;)

3) --loose bindings --- now thats interesting. Worth a try I should say !


Thanks for the info !

---

### Post by FuturePilot on 2007-08-23
> **_simon_ said:**
> What's it called in the repo?

I can't seem to find it...

gnome-compiz-manager

> **Inxsible said:**
> 1) I don't use Emerald..but I might give it a try

2) Doesn't the crash-handler plugin do the same - ie switch to metacity in event of crash. I wouldn't wanna go to metacity in any other scenario ;)

3) --loose bindings --- now thats interesting. Worth a try I should say !


Thanks for the info !
No problem :)
The only time I would go back to Metacity for something is for a game maybe.

---

### Post by qamelian on 2007-08-23
> **Inxsible said:**
> 2) Doesn't the crash-handler plugin do the same - ie switch to metacity in event of crash. I wouldn't wanna go to metacity in any other scenario ;)

Sometimes you want to switch WMs for a reason other than a crash though, such as when you run an app that doesn't play nice with compiz-fusion.

---

### Post by Inxsible on 2007-08-23
> **qamelian said:**
> Sometimes you want to switch WMs for a reason other than a crash though, such as when you run an app that doesn't play nice with compiz-fusion.
I have yet to find such an app. Hopefully, my search will never end ;)

---

### Post by tgm4883 on 2007-08-23
> **Inxsible said:**
> I have yet to find such an app. Hopefully, my search will never end ;)

I could see turning it off if you were going to play a game, unreal or doom 3 perhaps

---

### Post by qamelian on 2007-08-23
> **Inxsible said:**
> I have yet to find such an app. Hopefully, my search will never end ;)

Well, depending on the version of Java you use, it may be necessary to switch back to Metacity to avoid having Java apps appear as blank Windows. This was caused by a bug in several versions of Java and has been corrected in the newest release from Sun. If you run any Java apps that require a specific release of the JRE to run properly, this could still be an issue.

---

### Post by dondad on 2007-08-24
> **Inxsible said:**
> I don't see why you would need the icon in the tray?

I set up all the plugins once the way I like it through the CCSM. Once that's done, all I do is start CF and all plugins selected work. Why would I need an additional icon to go to the CCSM and of course eat a bit more memory?

Are there other features that the fusion-icon provide other than simply allowing you to get to the CCSM?

For me, it makes it easy to return to metacity. For whatever reason (haven't figured anything out yet) my system will not shutdown the monitor after the timeout if I am running compiz. It shuts down fine in metacity. I switch to metacity when I am done for the day so the monitor will shut down overnight, then back into compiz when I wake it up the next day.

---

### Post by coolen on 2007-08-24
> **Inxsible said:**
> I don't see why you would need the icon in the tray?

I set up all the plugins once the way I like it through the CCSM. Once that's done, all I do is start CF and all plugins selected work. Why would I need an additional icon to go to the CCSM and of course eat a bit more memory?

Are there other features that the fusion-icon provide other than simply allowing you to get to the CCSM?

Makes it easy to return to Metacity, mostly. Whenever gksudo grabs my screen, it doesn't release it. I can, in some cases, close the offending application, then go back in under the limit. However, for some applications, this isn;t enough (Gdebi, for example, asks every time...no memory).
It can also be used to reload the window manager, which can be handy.
There are two tweaks available through the menu, each of which solved major problems on my laptop (black screen and totem crashing when entering fullscreen mode).
You can choose the window decorator you want.
It also allows you to switch to alternate window managers, such as Kwin. Not a massively useful feature, but there could be some use.

---

### Post by jimbo99 on 2007-08-24
The git stuff fails for me on virtually every machine.  I'm using the trevino repo.  The trevino repo also has a bunch of problems with the version of compiz-fusion that they have available for download.  In fact, it got incredibly messy a couple days ago making it nearly impossible to use.  Then yesterday it was updated again and became better, but still has lots of problems over the first release.

---

### Post by EXCiD3 on 2007-08-24
Have you tried using the CF Installer script? Its awesome and it installs and updates Compiz Fusion for you! [http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

---

### Post by jimbo99 on 2007-08-24
I found the reference to the .deb file and used that.  That worked well to get me a tray icon to control it.  Not as nice as the original beryl icon but it appears to have done the trick.

---

### Post by santiagoward2000 on 2007-08-25
Hi Luckyd, thanks for that mini-how-to. I worked perfectly!

---

### Post by skinrock on 2007-08-27
I'm running a 64 bit version of Feisty Fawn, and got a "Wrong Architecture i386" error.  This is the second installer I've ran into this issue with.  I noticed some guys have the 64 bit version listed in their sigs, is there something I can edit to trick the installer into working?

---

### Post by coolen on 2007-08-27
I don't use 64-bit, but if you're getting it through a repo, it should automatically resolve that issue. It may not: on Edgy, I used to get errors about wrong architecture (i386? Huh?). This only happened with Add/Remove, so try it through Synaptic or apt-get.
This method apparently gets pre-compiled binaries...if you could get your hands on the source code, then it should work.
If you got the deb posted earlier, you'll definitely have troubles. I got my deb from a Debian repo, though I didn't bookmark it or anything. I found it pretty easily through Google.

---

### Post by dondad on 2007-08-27
> **CowzRule said:**
> Here's a deb package for it
Is there a reason that this will not work in Gutsy? I have it in Fiesty and it runs great. I have Gutsy set up as a dual boot on the same machine. The icon installs ok, but when I click on it to run it, the whole system locks up and I have to shut down with the power button to get it back.

---

### Post by FuturePilot on 2007-08-27
> **dondad said:**
> Is there a reason that this will not work in Gutsy? I have it in Fiesty and it runs great. I have Gutsy set up as a dual boot on the same machine. The icon installs ok, but when I click on it to run it, the whole system locks up and I have to shut down with the power button to get it back.

There is one built for Gutsy in the repos already. What graphics card and driver version are you using? I've found the 100.14.11 Nvidia driver is very buggy and kept freezing on me.

---

### Post by Lapino on 2007-08-27
> **skinrock said:**
> I'm running a 64 bit version of Feisty Fawn, and got a "Wrong Architecture i386" error.  This is the second installer I've ran into this issue with.  I noticed some guys have the 64 bit version listed in their sigs, is there something I can edit to trick the installer into working?

Did you try this to install it (in terminal): ```
sudo dpkg -i --force-architecture filename.deb
```

This is not guaranteed to work and might break your system (although I had that never happen to me).

---

### Post by siralphred on 2007-08-27
> **EXCiD3 said:**
> Have you tried using the CF Installer script? Its awesome and it installs and updates Compiz Fusion for you! [http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

i have tried that before but it lacks the new screensaver and the swift shifter plugins, do u know how to get that with this installer?

---

### Post by dondad on 2007-08-27
> **FuturePilot said:**
> There is one built for Gutsy in the repos already. What graphics card and driver version are you using? I've found the 100.14.11 Nvidia driver is very buggy and kept freezing on me.

Where is it in the repos? I haven't enabled any other than the ones that are standard in gutsy. I couldn't fine it in synaptic, and apt-get does not find it either.

How do I check to see which driver I am using? The graphics card is, I think, an NVIDIA 7300 (this computer is an xps410n)

I got Feisty working fine, now for gutsy........

---

### Post by FuturePilot on 2007-08-27
> **dondad said:**
> Where is it in the repos? I haven't enabled any other than the ones that are standard in gutsy. I couldn't fine it in synaptic, and apt-get does not find it either.

How do I check to see which driver I am using? The graphics card is, I think, an NVIDIA 7300 (this computer is an xps410n)

I got Feisty working fine, now for gutsy........

Try ```
sudo apt-get install compiz-gnome-manager
```
For the driver version type ```
nvidia-settings
``` into the terminal and it will tell you what driver.

---

### Post by dondad on 2007-08-27
> **FuturePilot said:**
> Try ```
sudo apt-get install compiz-gnome-manager
```
For the driver version type ```
nvidia-settings
``` into the terminal and it will tell you what driver.

Thanks for the answer. I tried the apt-get and got this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-gnome-manager

```

For the nvidia settings:

GeForce 7300 LE
driver 100.14.11

---

### Post by FuturePilot on 2007-08-28
Oops. My fault. It should be
```
sudo apt-get install gnome-compiz-manager
```
Yeah, those drivers are buggy for me too. I would try and enable CF and the whole thing would just freeze on me.

---

### Post by kopision on 2007-08-29
The deb package is in conflict with the lunar-applet... It gave me an error message when "attempting to override: '/usr/share/icons/hicolor/icon-theme.cache', it belongs to package 'lunar-applet'", how to resolve it? Thanks~

P.S. The lunar-applet is an applet that shows a lunar calendar when click on the date on the top-right corner of the screen. It's much useful for Chinese.

---

### Post by jusmurph on 2007-08-29
Is there a deb for amd64?

---

### Post by shazan25 on 2007-08-29
> **CowzRule said:**
> Here's a deb package for it

version de 64 bits?

---

### Post by CowzRule on 2007-08-30
> **kopision said:**
> The deb package is in conflict with the lunar-applet... It gave me an error message when "attempting to override: '/usr/share/icons/hicolor/icon-theme.cache', it belongs to package 'lunar-applet'", how to resolve it? Thanks~

P.S. The lunar-applet is an applet that shows a lunar calendar when click on the date on the top-right corner of the screen. It's much useful for Chinese.
Since the error is referring to the icon cache, try changing your icon theme, then try install the deb package again. If it works, then switch back to the icons you were using.

> **jusmurph said:**
> Is there a deb for amd64?

> **shazan25 said:**
> version de 64 bits?
Sorry, I'm on a 32 bit pc so, I believe, I'm not able to build a deb for 64 bit pc's.

---

### Post by munmon on 2007-08-30
Good Evening

Installed fine. Everything's working as it should be. But I did not see any icon in the tray. Apparently it went invisible as I can access the menu by clicking the invisible fusion-icon in the tray.

Any ideas?

 NVM, I copied the usr/share/icons/hicolor/22x22/apps/fusion-icon.png and placed it inside my current icon themes.

---

### Post by gimmic on 2007-08-30
> **munmon said:**
> Good Evening

Installed fine. Everything's working as it should be. But I did not see any icon in the tray. Apparently it went invisible as I can access the menu by clicking the invisible fusion-icon in the tray.

Any ideas?

 NVM, I copied the usr/share/icons/hicolor/22x22/apps/fusion-icon.png and placed it inside my current icon themes.

Having the same problem but I'm a bit of a noob- where should I move the fusion icon when using a theme through emerald? 
Thanks~

---

### Post by Shamane on 2007-08-30
Thanks for this topic \\:D/:grin:

---

### Post by reddfox321 on 2007-08-30
> **ubername said:**
> Hi

I installed fusion-icon by both command line method and deb package. In both cases when I activate the icon (either from terminal or by selecting menu item added by deb package) my entire screen freezes. windows lose all content, go white with grey borders, panels (i.e. where Applications, Places, System etc. appear) go grey. Mouse pointer continues to move but nothing else. Have to power off to get going again.

I'm using Gutsy. The reason I wanted the icon is because I can get compiz to work fine but it doesn't use 'emerald' themes. Rather it uses those which appear from the system>preferences>appearance option. I saw that in beryl you had to switch windows-decorator to emerald, but couldn't find anything in compizsettingsmanager, so though the icon might do the trick

Can anyone help

TIA
> **ubername said:**
> Thanks

My problem is not getting the fusion-icon installed, but getting to use it without crashing the GUI. Hope you can help

TIA
> **5h4rk said:**
> I got the same problem with Feisty...

As do I. Anybody have a fix for this? The tray icon simply reboots compiz and doesn't behave like the beryl icon. :confused:
I'm using fiesty
I'm using the trevino repos
ccsm says version is 0.5.2

---

### Post by dondad on 2007-08-30
> **reddfox321 said:**
> As do I. Anybody have a fix for this? The tray icon simply reboots compiz and doesn't behave like the beryl icon. :confused:

I installed the icon in Fiesty using the .deb. It put a link to it in the applications>>system tools menu. When I run it, it puts the icon in the tray. Right clicking on it gives me the ability to select either compiz or metacity for a manager, and GTK or emerald as the decorator. I can also restart the window manager and access the emerald themes.

I mainly use it to select metacity when I am done for the day as my monitor will not go into powerdown mode in compiz.

---

### Post by dondad on 2007-08-30
> **reddfox321 said:**
> As do I. Anybody have a fix for this? The tray icon simply reboots compiz and doesn't behave like the beryl icon. :confused:

There is a different icon for gutsy. 

```

sudo apt-get install compiz-gnome-manager

```

After installation, I ran it by putting the name in the run application box. Make sure that you have the latest updates for compiz. There was an issue with lockups etc. that were fixed in the last day or so.

---

### Post by reddfox321 on 2007-08-30
> **dondad said:**
> There is a different icon for gutsy. 

```

sudo apt-get install compiz-gnome-manager

```

After installation, I ran it by putting the name in the run application box. Make sure that you have the latest updates for compiz. There was an issue with lockups etc. that were fixed in the last day or so.

I'm using fiesty

I just tried that code in terminal and it won't work
I get this error
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-gnome-manager

```

---

### Post by reddfox321 on 2007-08-30
> **dondad said:**
> I installed the icon in Fiesty using the .deb. It put a link to it in the applications>>system tools menu. When I run it, it puts the icon in the tray. Right clicking on it gives me the ability to select either compiz or metacity for a manager, and GTK or emerald as the decorator. I can also restart the window manager and access the emerald themes.

I mainly use it to select metacity when I am done for the day as my monitor will not go into powerdown mode in compiz.

I understand how its supposed to work (I switched from beryl) it just isn't doing it.

---

### Post by dondad on 2007-08-30
> **reddfox321 said:**
> I'm using fiesty

I just tried that code in terminal and it won't work
I get this error
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-gnome-manager

```

See Future pilot's post above. I copied wrong, should be
sudo apt-get install gnome-compiz-manager

It is also for Gutsy, not Fiesty.

---

### Post by munmon on 2007-08-30
> **gimmic said:**
> Having the same problem but I'm a bit of a noob- where should I move the fusion icon when using a theme through emerald? 
Thanks~

No no no. Not in the emerald theme folder. Copy that icon into your current icon theme. It should be in your home directory .icons

Eg. /home/**user**/.icons/**nuoveXT.2.1**/22x22/apps

Change the bold as your configuration. Or in the terminal

cp usr/share/icons/hicolor/22x22/apps/fusion-icon.png /home/<*username*>/.icons/<*currenticon*>/22x22/apps

That's all.

---

### Post by ceenvee703 on 2007-08-31
I'm in the same boat--the icon in the tray is invisible. I don't have an .icons folder in my home folder, though. I created one but then didn't know what to name the folder inside that folder, per your example. Sorry if I'm missing something obvious.

---

### Post by CowzRule on 2007-08-31
For those of you having problems not seeing the icon in the tray. Try resizing your panel. Right click an empty area of your panel and select Properties. Make the Size at least 26.
I have my panel at 28 and when I resized it below 26 the icon disappears. Why this happens, I don't know.

Thanks goes to Iehova
[http://ubuntuforums.org/showpost.php?p=3288345&postcount=2]("http://ubuntuforums.org/showpost.php?p=3288345&postcount=2")

---

### Post by ceenvee703 on 2007-08-31
Bingo, resizing to 28 did the trick. Thanks very much.

---

### Post by ricardoec on 2007-09-01
Sorry, but something ihas been movet at Trevino's

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  git-core: Conflicts: git (< 4.3.20-11) but 4.3.20-10 is to be installed
E: Broken packages

---

### Post by psyopper on 2007-09-02
I am using Trevino's repositories but cant seem to fine the gome-compiz-manager...

```

$ sudo aptitude install gnome-compiz-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

This almost leads me to believe it is already installed yet...

```

$ fusion-icon
bash: fusion-icon: command not found
$ gnome-compiz-manager
bash: gnome-compiz-manager: command not found
$ compiz-manager
bash: compiz-manager: command not found

```

Any ideas or help out there? 

I had this working a while back (late July), but it broke after I uninstalled and moved to Trevino's repos for 0.5.2. Previously I had installed it as "fusion-icon" and launched it with a command of the same name.

---

### Post by Inxsible on 2007-09-02
i think its compiz-gnome-manager.

Also there is a deb for fusion-icon thats on the forum somewhere

---

### Post by psyopper on 2007-09-02
> **Inxsible said:**
> i think its compiz-gnome-manager.

Also there is a deb for fusion-icon thats on the forum somewhere

```

$ sudo aptitude install compiz-gnome-manager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "compiz-gnome-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

As I recall I installed Fusion-Icon from Vorian's repositories. It doesn't appear to be there either. Is there someplace on the forum I should be snooping around to find said .deb? I tried installing it from the repository of shame, but that wanted me to essentially reinstall my entire CF set to meet it's dependencies.

---

### Post by Inxsible on 2007-09-02
Check page 1 post # 8 of this very thread. CowzRule has given a deb for the fusion icon

---

### Post by psyopper on 2007-09-02
> **Inxsible said:**
> Check page 1 post # 8 of this very thread. CowzRule has given a deb for the fusion icon

Thanks!! Got it running and had to do the panel resize. 

> **CowzRule said:**
> Here's a deb package for it

Any chance you have the source for this? With a black panel I'm not fond of the icon and would like to mess around with it and update the icon. Or is there a way to change the icon otherwise?

---

### Post by raul_ on 2007-09-02
> **reddfox321 said:**
> I'm using fiesty

I just tried that code in terminal and it won't work
I get this error
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-gnome-manager

```

It's in a different repository

---

### Post by CowzRule on 2007-09-02
> **psyopper said:**
> Thanks!! Got it running and had to do the panel resize. 



Any chance you have the source for this? With a black panel I'm not fond of the icon and would like to mess around with it and update the icon. Or is there a way to change the icon otherwise?

I think the only icon that would need to be replaced is located in:
/usr/share/icons/hicolor/scalable/apps/fusion-icon.svg
Backup the original```
sudo copy /usr/share/icons/hicolor/scalable/apps/fusion-icon.svg /usr/share/icons/hicolor/scalable/apps/fusion-icon.svg.bak
```
Copy your icon
```
cp /your/icons/location/name.extension /usr/share/icons/hicolor/scalable/apps/fusion-icon.extension
```
i.e. cp /home/cowz/icon.png /usr/share/icons/hicolor/scalable/apps/fusion-icon.png
If that doesn't work you may have to replace the fusion-icon.png in the following folders
/usr/share/icons/hicolor/22x22/apps
/usr/share/icons/hicolor/24x24/apps
/usr/share/icons/hicolor/32x32/apps
/usr/share/icons/hicolor/48x48/apps

---

### Post by psyopper on 2007-09-02
> **CowzRule said:**
> I think the only icon that would need to be replaced...

/usr/share/icons/hicolor/24x24/apps


This was the one. Thanks!!

---

### Post by DJ_Peng on 2007-09-04
> **CowzRule said:**
> Here's a deb package for it
I tried to run it form the deb but got > * Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named compizconfig
... Trying another interface
* Error: All interfaces failed, aborting!
I even tried installing it from source, specifying Python2.5 as someone posted in a comment on [here]("http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/") and it still won't work. Any suggestions?

---

### Post by cookiefreak on 2007-09-09
> **Lapino said:**
> Did you try this to install it (in terminal): ```
sudo dpkg -i --force-architecture filename.deb
```

This is not guaranteed to work and might break your system (although I had that never happen to me).



That worked perfect fo me! thanks :) 

my suggest add this to the forst post so it will be easy to find :) :KS:KS:KS:KS

---

### Post by petit.padavoine on 2007-09-22
This might already have been posted, however...
The latest & greatest version of fusion-icon uses a python setup script, setup.py
So instead of make, make install, run
chmod +x ./setup.py
./setup.py install

---

### Post by MNICY on 2007-09-22
Is there a way to get this for amd64?

---

### Post by ST.x on 2007-09-22
> **MNICY said:**
> Is there a way to get this for amd64?

^ yes.

> **Lapino said:**
> Did you try this to install it (in terminal): ```
sudo dpkg -i --force-architecture filename.deb
```This is not guaranteed to work and might break your system (although I had that never happen to me).

---

### Post by MNICY on 2007-09-22
I get this error:
```
dpkg: error processing filename.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 filename.deb

```
Probaly some simple solution ;)
i am just learning about linux, so i dont know much :lolflag:

---

### Post by petit.padavoine on 2007-09-22
No! Don't use the deb!
Just compile it as per the instructions at the beginning of the thread
download by git,
then
```

cd fusion-icon
chmod +x ./setup.py
./setup.py install

```

---

### Post by petit.padavoine on 2007-09-22
> **MNICY said:**
> I get this error:
```
dpkg: error processing filename.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 filename.deb

```
Probaly some simple solution ;)
i am just learning about linux, so i dont know much :lolflag:

filename.deb is an example.
You should replace it with the actual name of the package you downloaded.
But if I were you, I'd compile it.

---

### Post by MNICY on 2007-09-22
Ok, so i tried to do what post #3 says.i type this:
```
sudo apt-get install git git-core compiz-dev
```
i get this:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
git is already the newest version.
git-core is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  compiz-dev: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but 1:0.5.2+git20070829-0ubuntu1amaranth1 is to be installed
```

---

### Post by nikoPSK on 2007-09-23
Yes check my mini-how to on it. It's called the "fusion icon":p

---

### Post by petit.padavoine on 2007-09-24
> **MNICY said:**
> 
The following packages have unmet dependencies:
  compiz-dev: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but 1:0.5.2+git20070829-0ubuntu1amaranth1 is to be installed[/code]

You are using Amaranth's repositories, and they don't have the compiz-dev package. You're therefore installing the compiz-dev package from the official Ubuntu repository, and its version conflicts with Amaranth's version of the compiz package.

To solve this, switch to Trevino's repositories. They have the latest version of compiz-dev, which won't cause any conflicts, and they are better anyway :).

Get rid of all the compiz you have now (sorry, gotta be done...). In a terminal, run
```

sudo apt-get remove compiz* libcompizconfig*

```

Edit your sources.list. In a Terminal, run
```

gksudo gedit /etc/apt/sources.list

```

Add the following repositories at the end of the file
```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```

Close the text editor.

Add the gpg key. In a terminal, run
```

wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -

```

Update your sources and reinstall Compiz from Trevino's repositories. In a terminal, run
```

sudo apt-get update
sudo apt-get install compiz compizconfig-settings-manager libcompizconfig-backend-gconf compiz-fusion-plugins-*

```

Now you can try installing compiz-dev again.

---

### Post by nikoPSK on 2007-09-25
the lifehacker demonstration is great. :guitar:

---

### Post by davedumas0 on 2007-09-28
i have the fusion icon installed but it is not in the tray i can turn on compiz fusion with the icon in my apps menu but like i said no icon in the tray??

---

### Post by nikoPSK on 2007-09-28
> **davedumas0 said:**
> i have the fusion icon installed but it is not in the tray i can turn on compiz fusion with the icon in my apps menu but like i said no icon in the tray??

Hello, How-to mine, Shows you how to make it visible...:KS

---

### Post by davedumas0 on 2007-09-29
i did that and nothing

---

### Post by nikoPSK on 2007-09-29
you should be able to see it... Top bar thing right click then properties change the size to 26:popcorn:

---

### Post by jersoncito on 2007-09-29
Yes, is there. I had the same issue. I changed the top bar value to 30, thanks!!!

---

### Post by g0dd3ss on 2007-09-30
wooo , my panel was set to 24px wide, and my icon was invisible, changed it to 26 and it works 8-}

seems the .svg icon included in the .deb is liek, empty invisible kinda. doh.

---

### Post by nikoPSK on 2007-09-30
your welcome. :) come to my make fun of windows page! :lolflag:

---

### Post by nchase on 2007-10-12
Would it be possible to add the rotation option from the screen resolution window to this tool?

---

### Post by nikoPSK on 2007-10-12
> **nchase said:**
> Would it be possible to add the rotation option from the screen resolution window to this tool?

I could integrate an nvidia/ ATI screen option with the hepl of my friend:)

---

### Post by dmber on 2007-10-21
is there a fusion-icon for gutsy?

---

### Post by nchase on 2007-10-21
the .deb package works in gutsy.

---

### Post by estebe on 2007-10-25
I've installed gnome-compiz-manager in gutsy, but I can not see the icon tray (the bar is 32 size). 
Of course I have compiz running, and I can change everything with "advanced desktop effects settings". 

If I write gnome-compiz-manager on terminal It says "command do not find"

Can anybody help me?

Esteban.

---

### Post by nikoPSK on 2007-10-25
ummmm, if your bar is that big, mabye you can't see it. Try bar size 26

---

### Post by estebe on 2007-10-25
> **nikoPSK said:**
> ummmm, if your bar is that big, mabye you can't see it. Try bar size 26

I've tried this, but nothing!

Must put something in the sessions ini?

---

### Post by exchequer598 on 2007-10-28
> **munmon said:**
> No no no. Not in the emerald theme folder. Copy that icon into your current icon theme. It should be in your home directory .icons

Eg. /home/**user**/.icons/**nuoveXT.2.1**/22x22/apps

Change the bold as your configuration. Or in the terminal

cp usr/share/icons/hicolor/22x22/apps/fusion-icon.png /home/<*username*>/.icons/<*currenticon*>/22x22/apps

That's all.

Thanks a lot **mumon**!
Finally fixed the problem!

---

### Post by jeff419 on 2008-04-17
What about an AMD64 version?

---

### Post by Lapino on 2008-04-19
> **jeff419 said:**
> What about an AMD64 version?

There are a couple of possibilities (yes, I'm quoting myself):

> **Lapino said:**
> Did you try this to install it (in terminal): ```
sudo dpkg -i --force-architecture filename.deb
```

This is not guaranteed to work and might break your system (although I had that never happen to me).

Or you could try compiling it yourself from sourcecode (it's not that difficult and this is the solution I would recommend)

Or you could try the hardy package from over here (don't know if it will work on other versions): [http://packages.ubuntu.com/hardy/fusion-icon]("http://packages.ubuntu.com/hardy/fusion-icon"). (Better solution: just wait for hardy to be released.)

---

### Post by athost on 2008-04-30
> **jeff419 said:**
> What about an AMD64 version?

Try [http://download.tuxfamily.org/osrdebian/pool/unstable/compiz-fusion-git/](http://download.tuxfamily.org/osrdebian/pool/unstable/compiz-fusion-git/)

There's "all-deb" package which works very well :)

---

