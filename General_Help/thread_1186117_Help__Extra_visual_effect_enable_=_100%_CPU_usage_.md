---
title: "Help : Extra visual effect enable = 100% CPU usage play movie with decent ardware"
date: 2009-06-13
forum: General Help
---

### Post by ubfu on 2009-06-13
Really need help with it.
I had posted with similar problem but can't edit much the title. 
[http://ubuntuforums.org/showthread.php?t=1184558](http://ubuntuforums.org/showthread.php?t=1184558)

Ubuntu 8.04
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
AMD2 4000+ 2.10 GHz

Install Ati driver manually from the website.

Really Need help.

---

### Post by QIII on 2009-06-13
Which driver did you install?  

Catalyst?

I know Catalyst 9.5 won't perform correctly in distributions earlier than Jaunty because of changes in X.

---

### Post by ubfu on 2009-06-13
I am using CCC 9.5 on ubuntu 8.04 Hardy 

How do you set the details

Location: Portland, OR
Beans: 229
Ubuntu 9.04 Jaunty Jackalope

---

### Post by QIII on 2009-06-13
Odd.

Just tried to edit settings and found I couldn't.

I hadn't had any need to, since things have been working well.

I'd check on my other box, but it doesn't have an ATI card.

I'm looking for an answer...

---

### Post by QIII on 2009-06-13
Never mind.

Yes, I can make adjustments (WHEW!)

Open the Catalyst Control Center.

Click on Display Manger.

There should be a box for "Desktop Area".  You should be able to select a resolution.

Let me know what happens.

---

### Post by QIII on 2009-06-13
OK.

Went and reviewed your other thread, and the CCC may not be what you need to do.

You are really getting whacked on several processes in top.

Are you running vino-server (remote desktop viewer) by chance?  Cruising the bugs, I found several cases where people said that making sure they had it off dropped their cpu usage by xorg.

What happens when you switch from compiz to metacity?

---

### Post by ubfu on 2009-06-13
My desktop area resolution was set to 1152x864 and the refresh rate to preferred.

I did went back to some point.Long reading hope you wouldn't mind.Sorry and thank you .

1.When finish install ubuntu , checking for updates , the top bar request me to update the Ati open source driver.I wanted to update it to fix the fan speed which running  100%.
2.Download and install the Ati open source driver at the hardware section.
3.Reboot but it still doesn't fix the fan speed.

4.Remove the Ati open source driver.Reboot
5.Went to Ati driver website , download the latest software choosing linux ubuntu.Downloaded the CCC 9.5 .deb.
6.Follow the instruction pdf files to install.Did that.Reboot , getting blank screen.

7.No choice , no Gui all totally black screen , have to Press reset button on my pc.
8.Follow other ubuntu forum instruction to restore the xorg.
9.Went and search google and ubuntu forum for better installation on hardy.Following the wiki setting 
[http://wiki.cchtml.com/index.php/Ubu...Install_Method](http://wiki.cchtml.com/index.php/Ubu...Install_Method)
and 
[http://wiki.cchtml.com/index.php/Ubu...river_Manually](http://wiki.cchtml.com/index.php/Ubu...river_Manually)

10.Reboot again.And finally it fix the fan speed.
11.Set the visual effect to Normal.Install codes to play avi or mpeg.
12.It use all the cpu usage.Once I play more than 20 sec , all of other folder icon getting to grey out.[http://ubuntuforums.org/showthread.php?t=1184558](http://ubuntuforums.org/showthread.php?t=1184558)

13.Once I double click for full screen.The whole ubuntu blank out agian.I have to press reset button again on my pc.
14.Went back and search for google but no help.Listen to one of the forum user to disable the visual effect to none.
15.Set it and it works.Cpu usage stay under 40% when watching movie.

16.Most of the forum here don't have problem visual effect + movie and their hardware is way under mine.
17.Using AMD 64 x2 2.0Ghz and Ati HD 3870 , which will be a decent hardware or middle range.Shouldn't be having any graphic problem.


Now I am think it doesn't even use my graphic card GPU to process output.It maybe using my onboard graphic card chipset which build in with my motherboard AMD690G.

Thank you ver much for reading.I hope someone could help me out. :)

---

### Post by gradinaruvasile on 2009-06-13
Have tried to downgrade your catalyst drivers to 9.4?
9.5 is for the newer kernels (ubuntu 9.04) as far as i know.

[COLOR="Red"]It maybe using my onboard graphic card chipset which build in with my motherboard AMD690G.
[/COLOR]
Ummm.. did u plug your monitor in the add on video cards port? If so, u use the add on card.
open a terminal and type

glxgears

Wait a couple of seconds until it gives you 2-3 fps rating lines
How much is it?

---

### Post by ubfu on 2009-06-13
I did plugin to the graphic card at the video card port.
I though of using onboard graphic card because I saw someone where that Ati got hybrid chipset which will switch to onboard if it doesn't need any gpu intensive usage.

The driver which I am using downloaded from here.I am downloading CCC 9.4 right now.[http://support.amd.com/us/gpudownload/linux/9-4/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/9-4/Pages/radeon_linux.aspx)
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

So , should I remove it ?
There are 3 things wanted to ask .

1.How to clean uninstall/remove the Ati driver ? worry it'll stuck on the registry.Does Ubuntu got the same system like window xp ? Sorry newbie , just install few days ago

2.Can kindly guide me on installing the Ati driver manually ? downloading with .run .The manual doesn't mention about ubuntu.Worry it need to install differently with Ubuntu
3.If I get blank screen with no Gui , whether ubuntu could auto restart or somehow goes to the command line to type restart.? I remember reading if Gui crash pressing ( I'm not sure which keyboard button ) can exit the gui and run at command line.

Can kindly teach me how to do it too.

Thank you very much.

---

### Post by 3rdalbum on 2009-06-13
ATI drivers don't properly support video playback or OpenGL (3D) applications while using a composited desktop like Compiz. Intel and Nvidia drivers don't have this problem.

If you're going to be using Linux for a long time, I'd recommend buying an Nvidia graphics card. They are more reliable, have better performance in their drivers, and support accelerated video playback (VDPAU, it allows the graphics card to take on most of the video playback responsibility and your CPU can rest).

---

### Post by ubfu on 2009-06-13
> **3rdalbum said:**
> ATI drivers don't properly support video playback or OpenGL (3D) applications while using a composited desktop like Compiz. Intel and Nvidia drivers don't have this problem.

If you're going to be using Linux for a long time, I'd recommend buying an Nvidia graphics card. They are more reliable, have better performance in their drivers, and support accelerated video playback (VDPAU, it allows the graphics card to take on most of the video playback responsibility and your CPU can rest).

But I see there are a lot of forum member using Ati.

So what I should do now ? Need help

---

### Post by gradinaruvasile on 2009-06-13
No registry in linux...

The installer includes an uninstall script too...
So

put the .bin in an empty directory
create a subdirectory
open the .bin s directory in terminal (with cd /path/to/bin/)

type
./ati-driver-installer-9-3-x86.x86_64.run --extract./subdirectory
where subdirectory is the one is created before (short name, lowercase letters only)
This command will extract the content of the installer in the specified folder.

cd subdirectory
sudo ./fglrx-uninstall.sh
sudo dpkg-reconfigure -phigh xserver-xorg

reboot


Install

back in terminal to the directory (the red letters differ from version to version)- just use the filename u have there

chmod +x ati-driver-installer-9-[COLOR="Red"]4-x86[/COLOR].x86_64.run
./ati-driver-installer-9-[COLOR="Red"]4-x86[/COLOR].x86_64.run --buildpkg Ubuntu/hardy

copy the resulting deb packages to a folder and cd to it in terminal
and type

sudo dpkg -i *

this way u will have native packages installed that can be removed from synaptic/apt-get

---

### Post by ubfu on 2009-06-13
> **gradinaruvasile said:**
> No registry in linux...

The installer includes an uninstall script too...
So

put the .bin in an empty directory
create a subdirectory
open the .bin s directory in terminal (with cd /path/to/bin/)

type
./ati-driver-installer-9-3-x86.x86_64.run --extract./subdirectory
where subdirectory is the one is created before (short name, lowercase letters only)
This command will extract the content of the installer in the specified folder.

cd subdirectory
sudo ./fglrx-uninstall.sh
sudo dpkg-reconfigure -phigh xserver-xorg

reboot


Install

back in terminal to the directory (the red letters differ from version to version)- just use the filename u have there

chmod +x ati-driver-installer-9-[COLOR="Red"]4-x86[/COLOR].x86_64.run
./ati-driver-installer-9-[COLOR="Red"]4-x86[/COLOR].x86_64.run --buildpkg Ubuntu/hardy

copy the resulting deb packages to a folder and cd to it in terminal
and type

sudo dpkg -i *

this way u will have native packages installed that can be removed from synaptic/apt-get

I don't quite understand.Where to find the .bin and what .bin mention to me to put into the folder ?

Sorry newbie

---

### Post by ubfu on 2009-06-13
I had tried with Ati CCC 9.4 still no luck.It hang when playing any movie.

Anyone please , really need help.

---

### Post by QIII on 2009-06-13
Don't know where to go from here.

I have an ATI card and driver.  I've had absolutely no problems with video playback or 3D applications while using Compiz.

Hang in there.

I would think SOMEONE would have an idea.

You might be able to find something like a work around here ...

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

---

### Post by ubfu on 2009-06-14
I am not sure it's bug but when I enable the visual effect to Normal.Every player I use just use up 100% cpu usage.

If it's really a bug , should other forum user have it ? 8.04 has release since last year .Should at lease have 1 person facing this common error.

Enable Visual Effect + video media (any program) = 100% cpu usage.
Ubuntu 8.04 + CCC 9.4 or 9.5 also the same.

Anyone can teach me how to debug or error log on showing how and which file it utilize 100% ?

---

### Post by gradinaruvasile on 2009-06-14
> **ubfu said:**
> I don't quite understand.Where to find the .bin and what .bin mention to me to put into the folder ?

Sorry newbie

the .bin is the binary installer u downloaded from atis site. 
Sorry i should have said [COLOR="Red"].run[/COLOR] The file name is something like ati-driver-installer-9-4-x86.x86_64.run

---

### Post by ubfu on 2009-06-14
> **gradinaruvasile said:**
> the .bin is the binary installer u downloaded from atis site. 
Sorry i should have said [COLOR="Red"].run[/COLOR] The file name is something like ati-driver-installer-9-4-x86.x86_64.run

Is ok , I did remove the Ati 9.5 and resinstall CCC 9.4 but still no luck.

It still doesn't get along with visual effct + any video media playing.

It just jump up to 100% usage.And it's the xorg process.
So I have no luck.

I was wondering , At window there are .Dll and registry to store and keep track of files location but what kind of system did Ubuntu using ?

I would like to learn more.Thank you.
So hoping I can find out my problem.

---

### Post by ubfu on 2009-06-15
How does ubuntu runs ? how does it keep track of files and path location ? 

How to do graphical error and debug log ? I really wanted to fix the problem.
:(

---

### Post by ubfu on 2009-06-16
> **ubfu said:**
> How does ubuntu runs ? how does it keep track of files and path location ? 

How to do graphical error and debug log ? I really wanted to fix the problem.
:(

I hope someone will guide me through on producing error logs

---

### Post by ubfu on 2009-06-25
What other error log or log file I need to include on the bug 
Any help guys ?:(
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/390995](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/390995)

---

### Post by ubfu on 2009-07-10
A temporary fix solution.Setting the video output to others like 
x11 or gl.

vx have problem with Ati driver.So set other will work.

---

