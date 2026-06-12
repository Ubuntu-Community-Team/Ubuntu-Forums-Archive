---
title: "Dapper crashes on shutdown"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Steven_B on 2006-05-31
When I try to shut down my computer, the screen immediatly goes blank, and the computer seems to quit doing anything.  Ctrl-Alt-Backspace doesn't work, so I have just turned the computer off the "brute force" way.  I am running Dapper, and Synaptic shows me as fully up-to-date.  Has anyone else had this problem?  Is there other information that would be helpful?
Thanks!

---

### Post by givré on 2006-05-31
Are you using XGL/compiz ?

---

### Post by Kilz on 2006-05-31
[QUOTE=Steven_B]When I try to shut down my computer, the screen immediatly goes blank, and the computer seems to quit doing anything.  Ctrl-Alt-Backspace doesn't work, so I have just turned the computer off the "brute force" way.  I am running Dapper, and Synaptic shows me as fully up-to-date.  Has anyone else had this problem?  Is there other information that would be helpful?
Thanks![/QUOTE]
Im having the same problem, made a post yesterday night, no ideas or reply's yet. no xgl-compiz

---

### Post by Steven_B on 2006-05-31
No XGL/compiz here either.  I am using the fglrx drivers with a Radeon Xpress 200.

---

### Post by Kilz on 2006-05-31
[QUOTE=Steven_B]No XGL/compiz here either.  I am using the fglrx drivers with a Radeon Xpress 200.[/QUOTE]

Same. ati x200 with fglrx

---

### Post by PhilOSparta on 2006-05-31
Same thing happened to me last night.
No XGL/compiz here either. I am using the fglrx drivers with a Radeon Xpress 200.

---

### Post by carney1979 on 2006-05-31
I too am using the fglrx driver.

When I try to log out of Gnome, it all locks up.

There was a very similar problem in the recent past, but it was corrected. My fglrx driver was updated in the last few days; now the problem returns.

Anybody submit a bug report?

David

---

### Post by Rackerz on 2006-05-31
It seems to be a problem with that particular graphics card and the fglrx drivers. I've got a ATI 9800XT with fglrx drivers but I shutdown fine with the newest drivers.

---

### Post by Kilz on 2006-05-31
[QUOTE=PhilOSparta]Same thing happened to me last night.
No XGL/compiz here either. I am using the fglrx drivers with a Radeon Xpress 200.[/QUOTE]

I just figured out the problem. I rememberd yesterday that the fglrx drivers updated. Lucky fro me I had the ati-driver-installer from the 8.24.8 version. I followed [these instructions]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2") except when it says sudo dpkg -i *.deb I put in sudo dpkg --force-overwrite -i *.deb . Now everything shuts down normaly.

You can still download the drivers from ati, 
amd64 version
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.24.8-x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.24.8-x86_64.run) 

i386 version
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run)

---

### Post by lithium- on 2006-05-31
I have the same problem with the fglrx driver and a ati radeon 9800pro.
No XGL/compiz used.

After switching back to the xorg ati driver the problem is gone.

---

### Post by Kilz on 2006-05-31
[QUOTE=lithium-]I have the same problem with the fglrx driver and a ati radeon 9800pro.
No XGL/compiz used.

After switching back to the xorg ati driver the problem is gone.[/QUOTE]
I think its just a bad driver, I wonder if/how we can get it removed as an update through apt.

---

### Post by Rackerz on 2006-05-31
I don't think you can get it removed, you can only choose not to update it. 

I've got the latest driver and I don't seem to be having any troubles.

---

### Post by carney1979 on 2006-05-31
I just "downgraded" my driver back to the previous release, 6.9.0-8.24.8+2.6.15.10-2_amd64 (for the AMD64 users).

I locked it in Synaptic so it won't upgrade.

Problem solved here. No more lockups when logging out of Gnome.

When yet-another-new-version is released, I will updgrde the driver and see if it works.

David

---

### Post by Kilz on 2006-05-31
[QUOTE=carney1979]I just "downgraded" my driver back to the previous release, 6.9.0-8.24.8+2.6.15.10-2_amd64 (for the AMD64 users).

I locked it in Synaptic so it won't upgrade.

Problem solved here. No more lockups when logging out of Gnome.

When yet-another-new-version is released, I will updgrde the driver and see if it works.

David[/QUOTE]

How do you lock things in synaptic?

---

### Post by apoclypse on 2006-05-31
I have a 9800pro and I updated have xgl (though not running all the time since I can't seem to get maya to run on it and blender crashes when i do anything funny on it such as move something :) ). Everything was workign fine yesterday and I've shtudown quite a few times as I dual boot (have to use Reason)

---

### Post by carney1979 on 2006-05-31
Left click on the package name in Synaptic, then from the menu at the top, select Package >> Lock Version.

To unlock it, just do this again.

Just a note: It seems I lost 3d acceleration when I downgraded my fglrx driver. So I "unlocked" it and upgraded again. I'd rather have 3d acceleration and the lockups, then no 3d acceleration and no lockups.

David

---

### Post by PhilOSparta on 2006-05-31
[QUOTE=carney1979]I just "downgraded" my driver back to the previous release, 6.9.0-8.24.8+2.6.15.10-2_amd64 (for the AMD64 users).


When yet-another-new-version is released, I will updgrde the driver and see if it works.

David[/QUOTE]

How does one get the previous version re-installed?
EDIT and Added: I found this out as follows.
Did a search for the ***xorg-driver-fglrx*** file and found it in 
/var/cache/apt/archives/xorg-driver-fglrx_6.9.0-8.24.8+2.6.15.10-2_amd64.deb
Then I uninstalled the xorg-driver-fglrx package in Synaptic.
Exit out of Synaptic so the install in the next step works.
Next install the previous driver by going into a terminal and entering this command:
sudo dpkg -i xorg-driver-fglrx_6.9.0-8.24.8+2.6.15.10-2_amd64.deb
This assumes that you haven't cleaned out your archives.
Next, go back into Synaptic and lock the xorg-driver-fglrx package as described earlier in this thread.
Now reboot (this should be your last lockup since the bad driver is still running!). 

This fixed my problem.

---

### Post by Kilz on 2006-05-31
[QUOTE=carney1979]Left click on the package name in Synaptic, then from the menu at the top, select Package >> Lock Version.

To unlock it, just do this again.

Just a note: It seems I lost 3d acceleration when I downgraded my fglrx driver. So I "unlocked" it and upgraded again. I'd rather have 3d acceleration and the lockups, then no 3d acceleration and no lockups.

David[/QUOTE]

Thanks for the locking info, you may want to try the ati-driver-installer method of installing the older driver I posted on the first page of this thread. I have acceleration and no lockups with the older driver using the ati-driver-installer.

---

### Post by carney1979 on 2006-06-03
Kilz:

Tried the driver in the post as well as ATI's same driver.

Works great, but still have lockups.

Right now I'm using ATI's latest commercial driver. fglrxinfo in a Gnome Terminal reports:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series Generic
OpenGL version string: 2.0.5814 (8.25.18 )

Perhaps there is a problem with my onboard graphics?

Is there a way to completely remove the driver before installing an older version? Maybe some part is being left behind when the old driver is installed.

David

---

### Post by PhilOSparta on 2006-06-03
I just installed the new version of Automatix for AMD64 and it blew away my
/var/cache/apt/archives/xorg-driver-fglrx_6.9.0-8.24.8+2.6.15.10-2_amd64.deb file and installed the new driver.  
Now I have the lockup problem back.

Even though the Syanptic had the xorg-driver-fglrx (old version) locked, the terminal shell program used by Automatix circumvented the lock.

How can I get a copy of  **xorg-driver-fglrx_6.9.0-8.24.8+2.6.15.10-2_amd64.deb** back?  It no longer resides on my machine.   
Does it reside on a repository somewhere?

---

### Post by carney1979 on 2006-06-03
Unfortunately Synaptic only locks within itself.

Using apt from a terminal or another program will cause any programs "locked" in Synaptic to be overwritten.

I have a copy of the package you need for AMD64.

Contact me at "carney1979 at gmail.com" and I will email it to you.

David

---

### Post by PhilOSparta on 2006-06-03
[QUOTE=carney1979]
I have a copy of the package you need for AMD64.

Contact me at "carney1979 at gmail.com" and I will email it to you.

David[/QUOTE]


David thanks for your offer.  

I was lucky to find the old one at the Brazil site using a Google search. 

Amazing that all the other sites were already upgraded to the new "Broken" version.    

I have not seen anywhere on this thread that a bug report was placed.  I guess I will try to get that done now.

EDIT/ADD:  I see a bug report has already been placed:
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447)
I hope they get this fixed.

Thanks again.=D>

---

### Post by grizzly69 on 2006-06-03
I just did a clean install of Dapper i386 on my computer (AMD64 2800) and it was fine with shutdown.
But I installed and enabled the Nvidia GLX drivers in the repository (I have a FX5900) Now when I shutdown or even log out I get the same thing all of you are experiencing. When I go to shutdown, the "Log off" sound starts looping and the display either goes blank or comes up with screwed up patterns of color.
I thought it may be a soundcard thing but now I think I have a videodriver problem. I will try several things and post here my results. I know this is mostly an "ATI" driver thread but I have the same issue without an "ATI" card.

Okay, I edited my xorg.conf file and went back to the "nv" driver with loading "dri" and "GLcore". My shutdown problem went away. It shuts down correctly. 

What do I do now? 
I really want the 3d acceleration but not shutting down correctly is probably not good for my system.

---

### Post by carney1979 on 2006-06-03
grizzly69:
 
Best of luck.
 
David

---

### Post by emoguz on 2006-06-03
[QUOTE=grizzly69]I just did a clean install of Dapper i386 on my computer (AMD64 2800) and it was fine with shutdown.
But I installed and enabled the Nvidia GLX drivers in the repository (I have a FX5900) Now when I shutdown or even log out I get the same thing all of you are experiencing. When I go to shutdown, the "Log off" sound starts looping and the display either goes blank or comes up with screwed up patterns of color.
I thought it may be a soundcard thing but now I think I have a videodriver problem. I will try several things and post here my results. I know this is mostly an "ATI" driver thread but I have the same issue without an "ATI" card.

Okay, I edited my xorg.conf file and went back to the "nv" driver with loading "dri" and "GLcore". My shutdown problem went away. It shuts down correctly. 

What do I do now? 
I really want the 3d acceleration but not shutting down correctly is probably not good for my system.[/QUOTE]

I was experiencing the same problem like many others, and I solved it by disabling the shutdown graphics. Now I made a fresh install and I cannot remember how I disabled the graphical shutdown screen. Someone help me plz if you know how to...

---

### Post by carney1979 on 2006-06-03
> I was experiencing the same problem like many others, and I solved it by disabling the shutdown graphics. Now I made a fresh install and I cannot remember how I disabled the graphical shutdown screen. Someone help me plz if you know how to... 
System >> Preferences >> Sessions >> Ask on Logout (uncheck it).

Got rid of the "graphical logout", didn't get rid of the lockup. :(

David

---

### Post by nocloud on 2006-06-03
i have this same problem and i am using KDE (kubnutu)

can anybody give me instructions on how to fix it?

my computer runs a pentium M 1.86Ghz with an ATI x300

i am using the fglrx driver that came with kubuntu, its the latest version of the driver (the buggy one)

i'm really quite new with linux so it would be really helpful if somebody leads me through how to fix this.

thanks in advance

---

### Post by binsh on 2006-06-04
This happens to me as well, on shutdown screen goes black and seems to just freeze. Unchecked ask on logout and still does same thing.

Athlon 64 3000+ (939)
Asus A8N32-SLI
1xXFX Geforce 7900 GT 256MB
2GB RAM
2xWD Raptor sata 74GB, single drive non raid.
WD JB120 IDE drive.
SB Audigy 2 ZS

Installed the Nvidia driver with apt.

---

### Post by grizzly69 on 2006-06-04
I was going to try disabling the graphical login, but I don't how. Does anyone? What I want to try is a text login where you have to type "startx" to get into the GUI. Maybe that might help with logouts as well.

I stripped down the graphical login to plainest it can get, but still locks up at shutdown. Although I rebooted once and got a kinda messed up screen but it did reboot okay. This only happened once.

I need to have 3D accelleration to use the programs I keep linux around for.

---

### Post by carney1979 on 2006-06-04
[grizzly69]("http://ubuntuforums.org/member.php?u=49689")

Already disabled graphical logins and tried the "startx" way.

The lockups still occur.

The problem lies solely with the latest fglrx driver, regardless of install source.

The work-arounds that work for some are just "getting around" problems with that driver and how it interacts with their particular card and the xserver.

I'd like to still encourage you to try the startx method. Maybe it will work for you....

David

---

### Post by nocloud on 2006-06-04
this might be useful:
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447)

---

### Post by grizzly69 on 2006-06-04
That link may help people with ATI videocards. But alas, I have a Nvidia FX5900.

Could someone tell me how to disable the graphical login?

---

### Post by carney1979 on 2006-06-04
> That link may help people with ATI videocards. But alas, I have a Nvidia FX5900. 
I'm becoming more and more convinced this is an "Ubuntu" problem, not a ATi or nVidia problem.

A search of the web today turned up no results of anyone else with any other Linux distro having this exact problem.

David

---

### Post by tseliot on 2006-06-04
[QUOTE=grizzly69]I just did a clean install of Dapper i386 on my computer (AMD64 2800) and it was fine with shutdown.
But I installed and enabled the Nvidia GLX drivers in the repository (I have a FX5900) Now when I shutdown or even log out I get the same thing all of you are experiencing. When I go to shutdown, the "Log off" sound starts looping and the display either goes blank or comes up with screwed up patterns of color.
I thought it may be a soundcard thing but now I think I have a videodriver problem. I will try several things and post here my results. I know this is mostly an "ATI" driver thread but I have the same issue without an "ATI" card.

Okay, I edited my xorg.conf file and went back to the "nv" driver with loading "dri" and "GLcore". My shutdown problem went away. It shuts down correctly. 

What do I do now? 
I really want the 3d acceleration but not shutting down correctly is probably not good for my system.[/QUOTE]
Read point 13 of the Problems Section of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by Kilz on 2006-06-04
[QUOTE=carney1979]I'm becoming more and more convinced this is an "Ubuntu" problem, not a ATi or nVidia problem.

A search of the web today turned up no results of anyone else with any other Linux distro having this exact problem.

David[/QUOTE]

Maybe it is, but I ended up reinstalling Dapper because I couldnt get acceleration back. On the new install I only installed the 8.24.8 driver and locked the version. I have no problems and acceleration works. If I have to keep using the old driver it isnt a problem. :D

---

### Post by grizzly69 on 2006-06-04
[QUOTE=tseliot]Read point 13 of the Problems Section of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")[/QUOTE]

Thank you ever so much.

Where you pointed me fixed my shutdown problem.

---

### Post by Thibouf on 2006-06-05
I have the same probleme , so I downgraded my drivers  but It doest not solved the probleme :( 
I tried to install directly from xorg-driver-fglrx_6.9.0-8.24.8+2.6.15.10-2_amd64.deb and also to make package with ati-driver-installer-8.24.8-x86_64.run and compile them

Both methods are working, but the system still lock-up when i shutdown X ... 
(I have  3d Accelaration only when I compile)

It was working when i was under breezy...

Does someone have an idea to make It work properly ?

---

### Post by aouie on 2006-06-07
If you are having freezes (or crashes) while shutting down (or logging out / log out / end current session) then disabling spash in the bootup / shutdown sequence should bypass the bug.
As pointed out in [a different post]("http://ubuntuforums.org/showthread.php?t=190769")
disabling splash from /boot/grub/menu.lst will bypass the shutdown freeze.
It worked for me (upgraded to Dapper, NVidia 5950, Athlon 64).
Sincerely,
Aouie

---

### Post by PhilOSparta on 2006-06-07
[QUOTE=aouie]If you are having freezes (or crashes) while shutting down (or logging out / log out / end current session) then disabling spash in the bootup / shutdown sequence should bypass the bug.
As pointed out in [a different post]("http://ubuntuforums.org/showthread.php?t=190769")
disabling splash from /boot/grub/menu.lst will bypass the shutdown freeze.
It worked for me (upgraded to Dapper, NVidia 5950, Athlon 64).
Sincerely,
Aouie[/QUOTE]

I just tried disabling splash and it didn't work. i.e. My system still locks up when doing reset etc.   It may work for NVidia boards.
I have an ATI Radeon Xpress 200.   A number of us are following a bug report [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447)
 on this problem.

If and when it gets fixed I will post here.

---

### Post by Eoin on 2006-06-07
Hello I'm having the same problem here as everyone else but reverting to the driver version as described by Kilz didn't sort it. 

Then I thought I try and reinstall and start with the older version driver from the get go, unfortunalty I'm also having troubles as described by this [thread](http://www.ubuntuforums.org/showthread.php?t=190133) (unlucky me) meaning I'd have to install the driver from the prompt. 

The trouble is a) don't know how to enable the universe section repo as needed by module-assistant and also b) not sure if the

```
fakeroot ./ati-driver-installer-<version>.run
```

step can be run from prompt as I haven't gotten that far yet :) . Anyone know how to execute either or both of these steps from the prompt?

---

### Post by carney1979 on 2006-06-09
Today's apt-get package updates included a new GDM.

Seems I can logout of Gnome now. Though untested, I assume I can also reboot and halt my machine, too.

I still get the lockups when I try to change to a VT via ctrl-alt-f1 through 6.

David

---

### Post by legrimpeur on 2006-06-09
I updated gdm but keeps on freezing on logout/reboots/shudowns...

---

### Post by brickhead20 on 2006-06-10
I have the same problem (woo) ATI Radeon XPRESS 200 (or whatever it is) and the fglrx driver installed for Dapper. Beggers on the shutdown, black screen, and Ctrl+alt+f1 or whatever terminal locks it up. Praying for it to be solved completely, soon! Scared its gunna stuff up the drives or something. Used to work on Breezy :(

---

### Post by RaZoR1394 on 2006-06-10
I also have lockups when changing VT, shutting down, rebooting or logging out. However on Gentoo I can at least shut down/reboot the computer although the screen goes black. I have an ATI X850XT and I'm on Ubuntu Dapper. I updated to the newest GDM but it didn't change anything and I've set AlwaysRestartServer to true. The latest ATI driver was supposed to fix this problem but it only has for some. Obviously ATI just sucks as usual, that's why I'm switching it to an nVidia, they've always worked like a charm for me.:mad:

However Gentoo was worse as the computer locked up randomly with it.

---

### Post by RaZoR1394 on 2006-06-13
If you have a flat panel with both a DVI and a VGA input try using the VGA one. That worked as a temporary workaround for me until the new ATI drivers arrive/ I get myself an Nvidia card with proper GNU/Linux support.

---

### Post by jrasith on 2006-06-16
I am also expirencing this problem, I have a Geforce FX 5900 Ultra, I have all of the latest updates (using 2.6.15-k7 kernel). Anyone have any ideas as to if a fix is being worked on? I am assuming this is an Ubuntu bug because it's happening to both ATI and NVIDIA users...

Peace;
-Joshua

---

### Post by David Valentine on 2006-06-22
Just to keep this going, I too am having this problem on an ATI Radeon Xpress 200.  I did the downgrade and package locking, but missed one of the packages and its subsequent "upgrade" sent me back to mesa.org land.  I gave up and decided to stay with the current ATI fglrx drivers, but am hoping this will be resolved soon.

---

### Post by Nrvnqsr on 2006-06-22
now I find this **VERY** funny, I have both a Compaq Presario M2000 CTO laptop and a HP Pavilion a1330e CTO desktop with both ATI X200m Express, ***but*** the laptop shut downs right, but not the desktop. And I have kernel 2.6.15.23 on both I used Knoppix on both and it reports to have the same chipsets

---

### Post by 3zrael on 2006-06-23
I didn't read all the 5 pages... but...
...may I suggest you to try this?

Uncomment this line:

# TerminateServer=true

in /usr/share/config/kdm/kdmrc

---

### Post by Eoin on 2006-06-26
I just noticed that ATI have released a new Linux Driver, I'm not sure if this has made its way into Ubuntu yet. Can anyone confirm if this solves the problem, I have to reinstall Ubuntu myself to check?

---

### Post by Icarus315 on 2006-06-27
edit:

/etc/kde3/kdm/kdmrc

then in the [Shutdown] section add

TerminateServer=true

This fixes the shutdown/restart freezing problem with an Ati card installed for me.

This only applies for Kubuntu 6.06 (which I'm using) I guess since kdmrc is a KDE config file.

---

### Post by Eoin on 2006-06-28
[QUOTE=Eoin]I just noticed that ATI have released a new Linux Driver, I'm not sure if this has made its way into Ubuntu yet. Can anyone confirm if this solves the problem, I have to reinstall Ubuntu myself to check?[/QUOTE]

Hi I know its silly to be quoting myself but I just wanted to point out that the new driver hasn't found its way into the Ubuntu packages yet. I also wanted to ask does anyone know of an easy way to check online what driver version is in apt? Booting the live cd every now and again to check is a bit tedoius :) .

---

### Post by laachlaan on 2006-06-28
I have a new Intel Dual 64 machine, with a fresh install of Dapper.

My motherboard is: ASUS P5LD2-VM

Pentium 4/Pentium D,
Socket 775,
Intel 945G, 
mATX,  
1066MHz FSB - SKU: P5LD2VM

I get this same problem - everything is fine, unless I try to log out, reboot, or shutdown and then I get a frozen black screen with a couple little squares on it. Removing splash (as mentioned in point 13: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")) succeeded in removing the small squares (video garbage) but it still froze.

---

### Post by fitzman49 on 2006-06-30
I have made a howto on the new drivers.  As far as I can tell, My system has not frozen yet and I'm running an Xpress 200m.

Heres a link to the page I made:[http://ubuntuforums.org/showthread.php?t=204910&highlight=fglrx]("http://ubuntuforums.org/showthread.php?t=204910&highlight=fglrx")

---

### Post by chambis on 2006-07-03
[QUOTE=Eoin]Hi I know its silly to be quoting myself but I just wanted to point out that the new driver hasn't found its way into the Ubuntu packages yet. I also wanted to ask does anyone know of an easy way to check online what driver version is in apt? Booting the live cd every now and again to check is a bit tedoius :) .[/QUOTE]

I think that typing
" sudo apt-cache search +your driver name *not version+ "
will do the trick

---

### Post by wazoo on 2006-07-03
I have the same problem, with the new nvidia drivers. For me, the fix was easy: uninstall the latest nvidia driver (nvidia-glx), and choose the "nvidia-glx-legacy" driver. The fonts aren't as crisp. But it fixed the problem.

---

### Post by elpresidente on 2006-07-08
> **laachlaan said:**
> I have a new Intel Dual 64 machine, with a fresh install of Dapper.

My motherboard is: ASUS P5LD2-VM

Pentium 4/Pentium D,
Socket 775,
Intel 945G, 
mATX,  
1066MHz FSB - SKU: P5LD2VM

I get this same problem - everything is fine, unless I try to log out, reboot, or shutdown and then I get a frozen black screen with a couple little squares on it. Removing splash (as mentioned in point 13: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")) succeeded in removing the small squares (video garbage) but it still froze.


I have the same hardware and am experiencing the exact same problem. I have tried removing the splash, no luck here. Was setting this computer up for the wife to switch her to Linux. I'm afraid there'll be no chance of that if I can't get it to reboot/logout without freezing.

---

### Post by elpresidente on 2006-07-08
I attempted to install Breezy and dist-upgrade to Dapper - no luck as it freezes in Breezy also. I did ctrl-alt-F1 to console (before actually logging in - just after boot) and sudo killall gdm, which causes freeze but dump a bunch of nonsense (to me at least) to screen ending with a kernel panic message.

I must get this working. Otherwise, I stand little chance in converting my home into a totally linux "shop" (Wife, son, myself and arcade machine in the future). Frankly, I'm surprised to find such a glaring bug.

---

### Post by elpresidente on 2006-07-09
I'm actually installing Suse right now. I want to know if this is an Ubuntu problem or a Linux problem.

---

### Post by elpresidente on 2006-07-09
Back to Xubuntu now. First, I boot up. Then ctrl-alt-F1 to get to terminal (before logging into gnome). At term sudo killall gdm freezes pc but not before spitting and error of:

[   186.628027] Unable to handle kernel paging request

This doesn't mean anything to me. Can anyone offer a suggestion based on this error?

---

### Post by elpresidente on 2006-07-09
Using Vesa fixes it. No longer freezing after switching to Vesa driver. I'll be ordering an nvidia card asap. Too bad the integrated adapter didn't work. I'm sure it will get sorted out eventually.

---

### Post by traveller on 2006-07-09
I have the same problem since yesterday I think -perhaps soon after having installed the nVidia drivers for my Thinkpad. The screen becomes black but the computer shuts down/restarts without any difficulty at all. I don't have any further problems to report.

---

### Post by absurdist on 2006-07-09
> **laachlaan said:**
> I have a new Intel Dual 64 machine, with a fresh install of Dapper.

My motherboard is: ASUS P5LD2-VM

Pentium 4/Pentium D,
Socket 775,
Intel 945G, 
mATX,  
1066MHz FSB - SKU: P5LD2VM

I get this same problem - everything is fine, unless I try to log out, reboot, or shutdown and then I get a frozen black screen with a couple little squares on it. Removing splash (as mentioned in point 13: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")) succeeded in removing the small squares (video garbage) but it still froze.

I have this problem too.  I can't logout, shutdown or restart.  Shutdown from the command-line doesn't work either.  Sometimes instead of the squares on the black screen I get the kubuntu logo with an empty status bar...and nothing happens.
My setup:
ASUS P5P800-VM
Pentium D - 830
integrated graphics - intel 865G, i810 driver

Pretty much everything else works though.

---

### Post by RaZoR1394 on 2006-07-14
Yes, the workaround is either to use D-SUB (VGA) instead of DVI or switch to VESA. Unfortunately my card doesn't work with VESA and I really need DVI so I'm really at a loss here. 8.26.18 doesn't make any difference neither. This needs to get sorted out ASAP. I wouldn't recommend anyone to buy an ATI card. It's imho a GIANT mistake.

---

### Post by absurdist on 2006-07-14
My chipset is supposed to be [vesa compatible]("http://support.intel.com/support/graphics/sb/CS-010487.htm"), but using vesa as driver crashes X on login.  VGA also doesn't work.
](*,)

---

### Post by Eoin on 2006-07-15
Vesa doesn't work for me either, yet it does work for every other distro I've tried. Personally I think the problem could be with X.org v7.0 as this is the first time I've used a distro which includes it.

---

### Post by RaZoR1394 on 2006-07-19
> **Eoin said:**
> Vesa doesn't work for me either, yet it does work for every other distro I've tried. Personally I think the problem could be with X.org v7.0 as this is the first time I've used a distro which includes it.

Same here. Vesa works on at least 5 other distros I've tried but not on Ubuntu :(.

---

### Post by Eoin on 2006-07-29
Just tried out the latest 8.27.10 drivers, it still freezes :( . BTW I'm not sure if I mentioned this before but I'm using the x86_64 version of Ubuntu.

---

### Post by RaZoR1394 on 2006-07-29
> **Eoin said:**
> Just tried out the latest 8.27.10 drivers, it still freezes :( . BTW I'm not sure if I mentioned this before but I'm using the x86_64 version of Ubuntu.


Same here and I'm also using x86_64. What specs do you have like card, kernel version and so on? Are you using DVI with a flatpanel? I think I'm gonna try the 2.6.17 kernel. Maybe it will work. I'm amazed that such a popular distro as Ubuntu uses 2.6.15.

---

### Post by Eoin on 2006-07-29
I'm tested on a fresh install so I believe thats kernel 2.6.15. And yep I'm using DVI, I have a dual screen setup one DVI one Analog running on a Radeon X800 Series.

I can appreciate that its nearly impossible to support all hardware but this problem seems to be quite a major one affecting numerous people. It would be nice if an official source would acknowledge the problem and say if they're trying to sort it out :) .

---

### Post by RaZoR1394 on 2006-07-29
> **Eoin said:**
> I'm tested on a fresh install so I believe thats kernel 2.6.15. And yep I'm using DVI, I have a dual screen setup one DVI one Analog running on a Radeon X800 Series.

I can appreciate that its nearly impossible to support all hardware but this problem seems to be quite a major one affecting numerous people. It would be nice if an official source would acknowledge the problem and say if they're trying to sort it out :) .

Please add your description of your problem on the bug report :) -> [http://ati.cchtml.com/show_bug.cgi?id=239](http://ati.cchtml.com/show_bug.cgi?id=239) . If you have a x800 AGP card you could try the r300 open source driver ([http://megahurts.dk/rune/r300_status.html](http://megahurts.dk/rune/r300_status.html)).

---

### Post by Eoin on 2006-07-30
Thanks for link, I'd added a comment to that report. Unfortunatly I'm running a PCI-E card so can't give those drivers a try. I think I'm going to try x86 Ubuntu just to see if it'll work.

---

### Post by Eoin on 2006-08-01
Actually x86 worked perfectly with the packaged fglrx driver. Unfortunatly while the live-cd ran grand the network was incorrectly configured with for the installation :mad: .

---

### Post by erusan on 2006-08-01
**@jrasith**

I'm using the same video card you are, and I'm having the shutdown problems, as well.  Actually, xorg in general seems to be having issues.  Are you having problems restarting your X session (ctrl+alt+backspace)?

---

### Post by RaZoR1394 on 2006-08-20
Believe it or not, the issue is still present with the new 8.28.8 drivers.

---

### Post by Steven_B on 2006-08-24
After several updates to GDM and fglrx, I am able to shut down the computer.  However, it commonly crashed with a white screen when logging out.
Adding AlwaysRestartServer=true to /etc/gdm/gdm.conf seemed to make the problem go away.  I haven't tried it enough to be 100% sure, but is OK so far.

---

### Post by RaZoR1394 on 2006-08-26
I gave up, went and bought a 7900gtx 512MB. Damn, what a relief. Everything just works like a charm just like my other Nvidia cards.

---

### Post by LTrickey on 2006-08-31
> **Icarus315 said:**
> edit:

/etc/kde3/kdm/kdmrc

then in the [Shutdown] section add

TerminateServer=true

This fixes the shutdown/restart freezing problem with an Ati card installed for me.

This only applies for Kubuntu 6.06 (which I'm using) I guess since kdmrc is a KDE config file.

This resolved shutdown problem for me too. I am also using Kubuntu, KDE 3.5.4   with a Radeon 9500 Pro... Was locking up hard at shutdown with blank screen prior this fix... Thankyou

---

