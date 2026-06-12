---
title: "Noob help with compiz"
date: 2009-06-30
forum: Desktop Environments
---

### Post by Traffic Cone on 2009-06-30
Now, before I begin, let me make it entirely clear that I am an idiot.

So, I just switched over from vista to Jaunty today because I got sick of windows. But after seeing all these videos on youtube showing what Compiz could do, I got jealous and wanted it. So I went on a quest to install it, doing a whole bunch of **** that I can't even remember doing now.

It wasn't untill a few moments ago that I realised that Compiz comes pre installed with Ubuntu.

I don't know what I did, but now whenever I click on **Extra** or **Normal** in the Visual Effects tab I get this: >   Desktop effects could not be enabled  
Whereas before I tried to "fix" everything I got the wobbly windows and stuff, but I didn't realize that was compiz.

Jeeze, I'm stupid.

---

### Post by andrea000 on 2009-06-30
run compiz from the terminal applications accessories terminal
and then type compiz in then post the output on here

---

### Post by Traffic Cone on 2009-06-30
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Segmentation fault
Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```


yea.... I think that "Skip Checks" thing has something to do with me screwing around with it...

---

### Post by andrea000 on 2009-06-30
how did you install your drivers?Under systems administration hardware drivers?do you have a nvidia card?

---

### Post by Traffic Cone on 2009-06-30
1. I installed (I think) through System Tools in the add/remove thing.
2. Hardwar Drivers comes up completely blank. There's nothing there.
3. Yes

---

### Post by andrea000 on 2009-06-30
ok if you know what card you have you can check to see if there is
a driver installed in synaptic.Systems administration synaptic package manager if there is one installed then get compiz check from [here]("http://ubuntuforums.org/showthread.php?t=799070").oh do you have a integrated card and did you install compiz config setting manager from synaptic if not do that you'll need that to configure compiz

---

### Post by andrea000 on 2009-06-30
did compiz check run

---

### Post by tedolivas on 2009-06-30
so I am also a new comer to ubuntu AND linux in general. I have issues which need help. I have searched the forum for a couple days and have found some. okay, so one at a time. I just installed 4.09 to dual boot on an HP computer. it has an Nvidia GeForce 6150se graphics card (chipset maybe?) and nForce 430. Acording to Nvidias website, this combo supports 3d graphics. when trying to enable compiz, it says something to the effect of compiz is not supported on this computer. ? any help? I have also instaled 4.09 as the sole OS on an ancient EMachine comp with an intel graphic chipset. it instals compiz no prob, but doesnt enable visual effect. I think that is a driver issue. I'll be completely honest, I just want the dang cube on my desktop! lol the cylinder would be even nicer! Is it possible? Can I get help? am I going to brik my comps? (probably! :) )

---

### Post by andrea000 on 2009-06-30
dont go and break your pc.first if you have not install ccsm from synaptic so have you installed the drivers from system administration hardware drivers.Do you have a integrated video card if you do you need to turn that off in the bios of your pc if it is blacklisted it could stop compiz from working the hp i have you just turn the ram down so you'll need to un blacklist it if it's a Intel and it is blacklisted.You'll need to run compiz from the terminal and maybe compiz check run compiz from the terminal first and post the output back

---

### Post by tedolivas on 2009-06-30
how do I run compiz from the terminal? I am new to linux, like 2 days experiance. I know how to get to the terminal, but what is the script? when I check drivers via admin, it says nothing, so I'm assuming that means it's running only the drivers that come with jaunty. I'd like to focus on just the HP for now, with the nvidia. for the other computer with the intel chipset, someone suggested down grading to 3.04 in another thread. I'll try that tomorrow on that computer.

---

### Post by andrea000 on 2009-06-30
sorry

go to applications accessories terminal and
then type compiz in then post the output on here

---

### Post by andrea000 on 2009-06-30
ok go to system>administration>hardware drivers and see if there
is any drivers showing there if there se click it and then click
activate.Now go to system>administration>synaptic package manager
and install compiz config setting manager.Then right click on the
desktop and change desktop background click on the tab that says
visual effects and click extra.now you need to configure compiz
and the cube with compiz config setting manager that is under
system>preferences>compiz config setting manager

---

### Post by siabost on 2009-06-30
Hi,

You seem to have the same graphics chip as I have.

As per Andrea's notes above you will have to install the nVidia driver. This normally comes up shortly after installation as a choice of three proprietary options - the most recent, version 180....., will be marked "recommended" so activate that one. You will then probably need to reboot. You can also find the option in the menu that Andrea describes if you missed it at installation time.

After that check out this link to find out how to get your spinning cubes working [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

I went through the same process and got it working in Ubuntu & Kubuntu (KDE4). The effect is smoother and even more stunning with the KDE4 desktop. 

If you are running Ubuntu (Gnome desktop)& you want to try KDE4, log out & before you log back in click on options (bottom left), select "change session" & select KDE from the choices that appear. If KDE isn't there, log back in under Gnome, go to Synaptic (Administration menu), set the left panel options so it's organised by package types, find the meta-packages & one of these will contain the Kubuntu desktop. Install - this is a fairly lengthy download but when done you will be able to choose your desktop type at login via the Options menu.

Get your Compiz working in Gnome first though.

Good Luck! ):P

---

### Post by Traffic Cone on 2009-06-30
> **andrea000 said:**
> ok if you know what card you have you can check to see if there is
a driver installed in synaptic.Systems administration synaptic package manager
I have no idea how to find out find out if there is a driver installed in Synaptic Package Manager.
> **andrea000 said:**
> 
 if there is one installed then get compiz check from [here]("http://ubuntuforums.org/showthread.php?t=799070").This is what compiz check told me:
```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```


> **andrea000 said:**
> 
oh do you have a integrated card and did you install compiz config setting manager from synaptic if not do that you'll need that to configure compiz
I believe I do have an integrated card.

I just installed compiz config setting manager. So we'll see how this goes.


And it's getting kind of confusing in here. I don't if you guys are talking to me or that other newbie.

---

### Post by andrea000 on 2009-06-30
both unless i quote one specifically that should make it a
little easier ok you have a Intel integrated card if you
have done the steps above and compiz check didn't find a
blacklisted card you can still see if your card is
blacklisted if you know what integrated card you have.but i
think the 945 is.

type this in the terminal

sudo gedit /usr/bin/compiz

then go down to were it says # blacklist based on the pci ids 
and see if your integrated card is in there.

---

### Post by Traffic Cone on 2009-06-30
My card does not appear to be in there.

I don't think it's a card problem. It was all working nice and dandy until I went in there and screwed it up.

---

### Post by andrea000 on 2009-06-30
are you in a dual boot with windows because i think all you need
to do is boot into recovery mode and fix what ever you did

---

### Post by Traffic Cone on 2009-06-30
Um, i think I am in a dual boot with windows. I got the ubuntu cd in the mail, popped it in my computer, and installed.

---

### Post by andrea000 on 2009-06-30
reboot and pick recovery mode from the list when
grub comes up and it will tell what to do

---

### Post by Traffic Cone on 2009-06-30
This may sound like a stupid question, but, recovery mode for ubuntu?

---

### Post by andrea000 on 2009-06-30
yes it will be one of the choices at start up if your dual
boot if not you can read about it and find out how to go to
it if your not [here]("https://wiki.ubuntu.com/RecoveryMode")

---

### Post by Traffic Cone on 2009-06-30
So I booted up Ubuntu in safe mode. It did it's thing then it gave me a list of options. I chose Resume Normal Boot.
And it did and here I am and nothing changed.

---

### Post by andrea000 on 2009-06-30
what are the options it gives you there should be
one to go back to the settings you have when you
installed ubuntu or the default never used recovery
or restore but it should give you something like
that

---

### Post by Traffic Cone on 2009-06-30
These are the options it gives me:

Resume - Resume normal boot
Clean - Try and make free space
dpkg - Repair broken packages
fsck - File system check
Grub - Update grub bootloader
Netroot - Drop to root shell prompt with networking
Root - Drop to root shell prompt
xfix - Try to auto repair graphic problems

---

### Post by andrea000 on 2009-06-30
dpkg but i should tell you i have never used recovery so i don't
know that much about it but if you think you broke something then dpkg may find it

---

### Post by Traffic Cone on 2009-06-30
Didn't work. All it did was tell me my system was up to date, then it removed two defunct packages and brought me back to the blue screen with all the options.

---

### Post by andrea000 on 2009-06-30
go to system preferences and compiz config setting manager
see what is checked and then check synaptic for your driver
and tell me what driver you have because it sounds like compiz
is not installed or the driver is messed up.

---

### Post by Traffic Cone on 2009-06-30
1. Under  compiz config setting manager there are a lot of things checked. Gnome Compatibility is checked, if that's what you're asking.

2. My driver is Nvidia 180.

---

### Post by karrank% on 2009-06-30
> **tedolivas said:**
> so one at a time. I just installed 4.09 to dual boot on an HP computer. it has an Nvidia GeForce 6150se graphics card (chipset maybe?) and nForce 430. Acording to Nvidias website, this combo supports 3d graphics. when trying to enable compiz, it says something to the effect of compiz is not supported on this computer. ? any help? I have also instaled 4.09 as the sole OS on an ancient EMachine comp with an intel graphic chipset. it instals compiz no prob, but doesnt enable visual effect. I think that is a driver issue. I'll be completely honest, I just want the dang cube on my desktop! lol the cylinder would be even nicer! Is it possible? Can I get help? am I going to brik my comps? (probably! :) )

I'm running a dualboot w/ xpsp3 and hardy 8.04 on an emachines w/ a 6150se chipset (integrated graphics). It will run compiz, but JUST BARELY. Half the time the display will tear then lock up and I'll have to reboot or hard reset. It doesn't brick anything to try, just wastes your precious time. If ya gotta have the cube, upgrade your GPU.

---

### Post by karrank% on 2009-06-30
> **Traffic Cone said:**
> These are the options it gives me:

Resume - Resume normal boot
Clean - Try and make free space
dpkg - Repair broken packages
fsck - File system check
Grub - Update grub bootloader
Netroot - Drop to root shell prompt with networking
Root - Drop to root shell prompt
xfix - Try to auto repair graphic problems

Try using xfix option yet?

---

### Post by Traffic Cone on 2009-06-30
Yes, it doesn't do anything.

I think this is a driver problem. In the Visual Effects tab, if I click on Normal or Extra or Custom, it searches for drivers, then stops and says: "Desktop effects could not be enabled"

---

### Post by karrank% on 2009-06-30
right, not very specific, is it? :D

try running compiz-check?

also-

look at forlong's blog--access that from the great dektop effects FAQ sticky.

 helped me a lot

also specific hardware lists would help

---

### Post by Traffic Cone on 2009-06-30
compiz-check:
```

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

And I've been reading forlongs blog... a lot. I'm not sure if anyone has ever had this problem before.

Is there a way I can just start Ubuntu over from scratch? That'd fix this problem, right?

---

### Post by karrank% on 2009-06-30
> **Traffic Cone said:**
> compiz-check:
```

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

And I've been reading forlongs blog... a lot. I'm not sure if anyone has ever had this problem before.

Is there a way I can just start Ubuntu over from scratch? That'd fix this problem, right?

Reinstall? sure, an easy solution, especially if you just started out and don't have a lot of critical data/settings. I've done that a few times with Ubuntu until settling on Hardy---MANY more times with Winblows.

---

### Post by Traffic Cone on 2009-06-30
So how do I reinstall Ubuntu, now?

---

### Post by Mia1990 on 2009-06-30
do you have nvidia setting manager installed.if you want to reinstall and you dual boot you'll need to put your hard drive partitions back together again just put the ubuntu cd in and it will let you resize your windows partition.

---

### Post by karrank% on 2009-06-30
> **Mia1990 said:**
> do you have nvidia setting manager installed.if you want to reinstall and you dual boot you'll need to put your hard drive partitions back together again just put the ubuntu cd in and it will let you resize your windows partition.

what she said:D
 
think it's gksudo-nvidia settings in the terminal 

or alternately you could use envy ng

but yeah, I think I remember just popping in the cd again and following the prompts.

---

### Post by Traffic Cone on 2009-06-30
What if I just used the entire disk? I don't care about my Vista dual boot.


Also, I've been trying to my partitions, but it won't let me for some reason. It let me when I initialy install Ubuntu, but not now...

---

### Post by sidious1741 on 2009-06-30
I Greatly support your decision, welcome to linux.  I remember when I started how hard it was to get used to.  Now It's just as familiar as Windows (I've only used It for half a year i think).  I'd like to give you some starting tips.

Alt-F2 Is the run command.
Alt-F2 then type synaptic to run my favorite ubuntu feature of all.  Just type a discription of what program you want and download it.
gedit = windows notepad

---

### Post by theidkman on 2009-06-30
Did you also install Advanced Desktop Effects Settings (ccsm)?

---

### Post by Traffic Cone on 2009-06-30
> **theidkman said:**
> Did you also install Advanced Desktop Effects Settings (ccsm)?
Yes.

---

### Post by karrank% on 2009-07-01
> **Traffic Cone said:**
> What if I just used the entire disk? I don't care about my Vista dual boot.


Also, I've been trying to my partitions, but it won't let me for some reason. It let me when I initialy install Ubuntu, but not now...

I like having the dual boot option; (a very few) certain things I need to tweak around the household require Windows. 

Others maybe not so much.

To access your partitions I believe you must run the live cd to access the partition editor (gparted in hardy, don't know the name in Jaunty)

---

### Post by Mia1990 on 2009-07-01
You can reinstall using your entire disk by just putting the cd in and booting into parted and in the options selecting use entire disk.as far as dual booting you don't need to do that for just one or two programs use wine for them or you can also use virtualization.virtual box is a good choice if you would like to go that way.

---

### Post by karrank% on 2009-07-01
> **Mia1990 said:**
> You can reinstall using your entire disk by just putting the cd in and booting into parted and in the options selecting use entire disk.as far as dual booting you don't need to do that for just one or two programs use wine for them or you can also use virtualization.virtual box is a good choice if you would like to go that way.

Having so little experience with Linux & CLI in general, I don't have enough time to explain to other users in my household much more than "just click on Windows at the boot screen prompt!" 

Baby steps :p

---

### Post by siabost on 2009-07-01
Hi Traffic Cone,

Reading through all your posts again you seem to have an integrated Intel 9.... series graphics chip.

In another post u say you have the nVidia 180... graphics driver installed. One will not work with the other, but in any case the system seems to be uploading the Intel driver.

For Compiz to work fully the driver will have to be capable of 3D Graphics acceleration. If you are getting rendering = none in the tests u have tried then this is a strong indication that it is not enabled or the loaded driver is not capable of it.

Re-installing Ubuntu will reset any changes you have made and should be a case of doing as you did the first time u installed. If u ensure u have a wired connection to the Internet via your Ethernet Network card Ubuntu will access it during the install to get any updates it requires.

Once your install is done and you have rebooted wait a while & Ubuntu will notify you that more updates are available. Follow the prompts and wait till your system is fully updated - this can take a while. 

Reboot when it's finished updating then check your system to see what you have in the way of 3D drivers/support (see some of the tests mentioned by others in previous posts).

There is more info available on Intel graphics at [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) but heed the warning at the top of the post!

Good luck!

---

### Post by tedolivas on 2009-07-05
i installed hardy yesterday on an old comp and everything has went smoothly...untill now. I have ccsm installed and extra visual effects enabled. cube works just fine. when trying to check out the cylinder and sphere effect i realized there is no reflection and deformation addon in ccsm, just a reflection addon. any ideas why? I am pretty new to linux. Installed jaunty on a new comp lastweek.

---

### Post by Po|tergeist on 2009-09-01
To be honest I have had this problem a few times installing new plugins from GIT. Once in awhile compiz will crash and it says I cannot enable desktop effects. Although I did install emerald and had instability problems with it so I removed it and reverted back to metacity as some of the same themes have been ported if you search through gnome-look.org's site. 

The most common thing to do other than compiz-check is to use this command in the terminal : "compiz --replace" and if you want to restart the window decorator you might try "metacity --replace" or "emerald --replace" depending on whatever you use. 

I have also found that sometimes I cannot enable my desktop effects and the problem may be related to a compiz plugin or could also be related to compiz itself. Things you might want to check out are "/usr/bin/compiz-decorator" and also "/usr/bin/compiz-manager"
If you have not altered either of those files I would not worry too much about it but it could also just be a bug in compiz if it is a development version and not a stable branch version of compiz. In fact if you are using anything that is developmental and not stable branch this is always a possibility. I have found this out the hard way. Often times I just keep trying to re-enable it from the console with the "compiz --replace" command or from the run box by hitting alt+f2 and then typing "compiz -- replace" or "compiz --replace &" into the run box. Another thing to look at is that sometimes the appearances > desktop effects settings do not respond well for some reason and possibly this could be something to do with compiz. My advice when in doubt is to check all of those things and then if none of it works you should try to reboot, log back in, and try to re-enable normal desktop effects first as some vid cards seem to not let you just jump right to advanced or custom effects which is something I think is related to memory handling on the card perhaps or it may be related to compiz... either way I have fixed the same problem on my machine many times by just rebooting and keep playing with the desktop effects settings radio buttons in that that under Appearance settings. If you have installed any type of new plugin that might be unstable and are getting this result you might try to start with normal desktop effects settings and enable the plugins one at a time manually and skip the newest one you installed and see if the same thing happens again. If it does not then odds are high that the newly installed plugin may be the culprit and you may want to uninstall it or simply leave it disabled. These are just ideas that have worked for me but I thought I would pass them on.

---

