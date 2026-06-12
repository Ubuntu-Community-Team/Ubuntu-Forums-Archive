---
title: "Solutions to Common Gaming Problems (please sticky!)"
date: 2006-09-09
forum: Gaming &amp; Leisure
---

### Post by fatsheep on 2006-09-09
There's a lot of the same questions being asked here so I think I sticky about common gaming problems would help.  I don't consider myself the most qualified person for the job but since no one else has created one, I'm taking the initiative. :wink:  If you have a solution to a common gaming problem then please post it here and I will add it to the list. :) 

Note that this is mainly written for GNOME as that is what I use.  However, I'll be including more KDE directions as I go on so just be patient and if you use KDE then give me some pointers. :) 

**Note:**  The "terminal" is the command line interface for GNOME.  It can be found under **Applications>Accessories>Terminal**.

[COLOR="DarkRed"][SIZE="5"]
**Index:**[/SIZE][/COLOR]

[SIZE="2"]_**1.  Sound Issues**_
1.1  Making a Startup Script
1.2  How to create a custom start command for your game
1.3  A Startup Script For Enemy Territory
_**2.  Installing Games**_
2.1  .RUN Files
2.2  .SH Files
_**3.  How to Overclock a Nvidia Graphics Card**_
3.1  Installing Coolbits
3.2  Making A Startup Script[/SIZE]


[SIZE="5"]**1.  Sound Issues**[/SIZE]

If you are using regular Ubuntu (GNOME), try entering this command in the terminal before you play:

> 
sudo killall esd


If you are using Kubuntu (KDE), try entering this command before you play:

> 
sudo killall artsd


Keep in mind, when the terminal asks for your password, you will not see the results of your typing - not even * characters.  So don't worry, just type in your password and push enter and it should work. :)  

If you need to run this command a lot then it may just be easier to make a startup script.

[SIZE="3"]**1.1  Making a Startup Script**[/SIZE]

**1.**  Create a new file without an extension.  Mine is going to be called "ut2004 start" (without quotations).
**2.**  Put this as the first line: > #!/bin/bash.  This identifies your file as a bash script
**3.**  If you use Gnome (Ubuntu) then on the next line paste the command: > sudo killall esd.  If you use KDE (Kubuntu) then paste this instead:
> sudo killall artsd
**4.**  Now we want the command to start the game.  This is different from game to game, for Enemy territory it's "et", for Unreal Tournament it's "./ut2004".  If you don't know the command to start the game, try looking in your /usr/bin/ folder for a link to your game.  This folder is where the terminal gets the commands to start an application.  
**5.**  To run your script, double click on it, select "Run in Terminal", and enter your password.  Note that your keystrokes will be invisible, not even "*" characters will be displayed.  Don't worry just type your password carefully, hit enter, and the script will carry on.  If you included the command to start the game in the script then it will automatically be started.  If not then start it (duh :wink: ).

Just for reference, this is a working startup script for Unreal Tournament 2004:

> 
#!/bin/bash
sudo killall esd
./ut2004


[SIZE="3"]**1.2  How to create a custom start command for your game**[/SIZE]

If you want to create your own start command then you will need to place a link to your game in the /usr/bin/ folder.  To do this, first type this command into the terminal:

> 
gksudo nautilus


This starts nautilus (file browser) in super user mode.  Now find the executable file for your game.  Right click on it, create a link, name this link whatever you want your command to be, and place this link into your /usr/bin/ folder.  So if your link is named "nexuiz" (and points to nexuiz) then you can now go to your terminal and type nexuiz and that will start the game.  Now save your file!  Then make sure your script has permission to execute.  To do this, right click on the script, go to properties, and then select permissions.  The "Execute" box on the top row (across from "Owner") should be checked.

[SIZE="3"]**1.3  A Startup Script For Enemy Territory**[/SIZE]

Enemy Territory is a great game but unfortunately you have to run these three commands in the terminal before playing:

> 
sudo killall esd
chown user:user /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss


So, I made a startup script:

> 
#!/bin/bash
sudo killall esd
chown user:user /proc/asound/card0/pcm0p/oss
sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
et


When you run the script, it automatically automatically starts Enemy Territory with sound.

[COLOR="Red"]**NOTE:**[/COLOR] Remember to replace user:user with your own username!  For me this is fatsheep:fatsheep.

[size="5"]**2.  Installing Games**[/size]

[COLOR="Red"]**NOTE:**[/COLOR] The instructions in this section will work for most game installer but just incase you run into a different type of installer then take a look at **[How To Install ANYTHING in Ubuntu](http://monkeyblog.org/ubuntu/installing/)**.

All that is required for a typical game installer to run is proper execution permissions. To give it permission to execute, simply right click on the installer, select *properties*, now select the *permissions* tab.  Check the "Execute" box on the first row (across from "Owner").  Below shows a file with permission to execute.  

[img]http://img236.imageshack.us/img236/6146/permissionsts3.jpg[/img]

**To run the installer, simple double click on the file and select "Run in Terminal".**

[COLOR="Red"]**NOTE:**[/COLOR] If you get a message saying something to degree of "*You do not have the proper permissions to perform this action*", then you  need to run it under *super user mode*.  The easiest way to do this is to open up a terminal, type "sudo " (make sure you have a space infront) and then drag and drop your installer file into the terminal window.    Now hit enter and the installer will run with super user permissions.

[size="5"]**3.  How to Overclock a Nvidia Graphics Card**[/size]

For this you are obviously going to need the nvidia drivers.  In dapper the easiest way to do this is to through a useful tool called [automatix](http://www.getautomatix.com/).  So before you read on, make sure you have the Nvidia drivers installed.

[SIZE="3"]**3.1  Installing Coolbits**[/SIZE]

Coolbits will provide an easy to use overclocking utility inside nvidia-settings (typically you can access this through *Applications > System Tools > NVIDIA Settings*).  Here's how to install it:

Open up a terminal.  Type in this command:

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg_backup.conf

This backs up our xorg.conf file before we make our changes to it.  If we have any problems we can just revert to our backup with this command:

> sudo cp /etc/X11/xorg_backup.conf /etc/X11/xorg.conf

Now for the actual editing:

> sudo gedit /etc/X11/xorg.conf

Now search for a section that begins with:

> Section "Device"

Mine looks like this:

> Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection


Your's may look different depending on what graphics card you have.  We need to add the following text to enable coolbits:

> Option "Coolbits"   "1"

Here's what my section looks like after I have enabled coolbits:

> Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
    **Option "Coolbits"   "1"**
EndSection

Now save the file!  Go into NVIDIA Settings, there should be a clock frequency tab:

[img]http://img66.imageshack.us/img66/9748/coolbitswm5.jpg[/img]

Just configure your settings, hit apply and your done... until you restart.  Unfortunately there is not an option in coolbits to retain overclocking settings after a reboot so your settings are lost... unless you make a startup script:

[size="3"]**3.2  Making A Startup Script**[/size]

First, create a file without an extension, I'm going to name mine "nvidia_overclock".  Now paste this text into your file:

> 
#!/bin/bash
nvidia-settings -a GPUOverclockingState=1 -a 
GPU2DClockFreqs=**<GPU>**,**<MEM>** -a GPU3DClockFreqs=**<GPU>**,**<MEM>**


A **<GPU>** tag signifies the clock frequency of your graphics card's core.  A **<MEM>** tag signifies the clock frequency of the memory.  We are going to have the replace these with the actual values desired.  As you may have guessed, the first set of tags is for 2d, the second set is for 3d.  Here's what my script looks like after I am done editing:

> 
#!/bin/bash
nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=**300,1000** -a GPU3DClockFreqs=**550,1050**


**Save your file!**  Then, right click on it, go to properties.  Now select "permissions" and check all boxes.  Your script is now ready to rumble.  If you double click on it and select "Run In Terminal" it will apply your desired overclocking settings.  However, I am far to lazy to go through that routine every time I boot up so I will show you how to make it run automatically.  

Go to *System>Preferences>Sessions*.  Now select the "Startup Programs" tab.  Click "Add" and then "Browse".  Now find your script and select "Open" from the bottom left.  Our script will now be executed automatically at bootup.  Restart just to make sure and if you have any trouble contact me. :)

---

### Post by Sp00ne on 2006-09-10
Damn this is helpful.

---

### Post by simplyw00x on 2006-09-10
That startup script doesn't need the echo command; that can be placed in /etc/environment instead. Otherwise, helpful, thanks.

---

### Post by 3rdalbum on 2006-09-10
You don't really need the "sudo killall esd". If you go into the Sound control panel and turn off software mixing, that does the same thing. If you don't mind not having the launcher sounds in Gnome, you can leave ESD turned off all the time.

Or, you can do:
```
sudo apt-get install esound-clients
```. Then, when launching a game (let's call it "coolgame.run"), you would type:

```
esddsp coolgame.run
```

---

### Post by crane on 2006-09-10
Pretty good suggestions. although it should be stated then these commands are not always needed.
 I can run ET, Quake3, Quake4, UT2K4, and others without disabling esd.
Everyone should try runningt he game first, then use these commands if the problems occurs.
 Good Idea to start such a list. You should create a static page for the list  as well. This is likely to get lost in the posts if not stickied.

---

### Post by fatsheep on 2006-09-11
> **Sp00ne said:**
> Damn this is helpful.

Thanks. :) 

> **simplyw00x said:**
> That startup script doesn't need the echo command; that can be placed in /etc/environment instead. Otherwise, helpful, thanks.

Just to make sure I understand you correctly, you mean I can replace this line:

> sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

with this?

> sudo "et.x86 0 0 direct" > /etc/environment

Are there any benefits in doing it this way compared to the above or is it just an alternative method?

> **3rdalbum said:**
> You don't really need the "sudo killall esd". If you go into the Sound control panel and turn off software mixing, that does the same thing. If you don't mind not having the launcher sounds in Gnome, you can leave ESD turned off all the time.

Or, you can do:
```
sudo apt-get install esound-clients
```. Then, when launching a game (let's call it "coolgame.run"), you would type:

```
esddsp coolgame.run
```

I have turned off software mixing in the sound control panel.  So I should no longer need to use the "sudo killall esd" command?  And also, just out of curiosity, what is ESD?  And why does it cause so many problems for games?

> **crane said:**
> Pretty good suggestions. although it should be stated then these commands are not always needed.
 I can run ET, Quake3, Quake4, UT2K4, and others without disabling esd.
Everyone should try runningt he game first, then use these commands if the problems occurs.
 Good Idea to start such a list. You should create a static page for the list  as well. This is likely to get lost in the posts if not stickied.

I will make a static page on the Ubuntu wiki if there is not already something like this there.  If one already exists hopefully I can add to it. :wink:

---

### Post by simplyw00x on 2006-09-12
> Just to make sure I understand you correctly, you mean I can replace this line:
No, you can place
```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```
in the file /etc/environment

The advantage of this is that you can run et from the console without a launcher script or a long command.

---

### Post by christhemonkey on 2006-09-12
ESD is the gnome software sound mixing daemon.

It causes problems as it hogs the sound device, so no other playback can use it.
ALSA with dmix does not do this, so this is the solution i like to use.

---

### Post by Lord Illidan on 2006-09-12
You are also forgetting artsd, the KDE equivalent of esd. I hate it meself..

killall artsd

---

### Post by fatsheep on 2006-09-12
> **simplyw00x said:**
> No, you can place
```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```
in the file /etc/environment

The advantage of this is that you can run et from the console without a launcher script or a long command.

I tried this and I lost sound in ET.

Remvoing the echo line and running chown on /proc/asound/card0/pcm0p/oss fixed it.

> ESD is the gnome software sound mixing daemon.

It causes problems as it hogs the sound device, so no other playback can use it.
ALSA with dmix does not do this, so this is the solution i like to use.

I'm not exactly sure what a software sound mixing daemon is but when I turn off ESD in the sound panel I lose all sound.  How do you use ALSA with dmix solution?

---

### Post by fatsheep on 2006-09-13
I have updated original post with some more info including the better way to install a .run file (graphically).  I don't want to give the wrong idea that everything in Ubuntu must be done via the command line.  Also I added a little tid bit on How to create a custom start command for your game and some the equivalent to the killall esd command for KDE users (killall artsd) as suggested by Lord Illidan.

A sticky would be very nice but I will continue to add content here regardless.

---

### Post by Lord Illidan on 2006-09-13
Getting better.

People also complain of speed issues while running games. Most often it is because of another process hogging up the cpu or RAM.

1. Just pause the game.
2. Press CTRL - ALT -F1 or CTRL - ALT - F2.
3. Enter username and password.
4. Run ```
top
``` in the terminal, and see which process is consuming the most..if it is your game, don't worry, if not...
5.Note down the process ID of the offending process. It is the number to the left.
6.Press q or control - c to quit top.
7.Type ```
kill processid
```, substituting the number you got from step 5.
8.Press CTRL-ALT-F7 to go back to your game!

Also, try logging in failsafe from gdm/kdm to run games...avoid loading KDE and GNOME.

---

### Post by rokknroll on 2006-09-13
you can also use chmod 700 *scriptname* to make the script executable from bash

---

### Post by KhaaL on 2006-09-13
great guide, solved my problems

+1 vote for stickie!

---

### Post by feest on 2006-09-14
just want to thank you for having my sound running on et :)

---

### Post by fatsheep on 2006-09-17
[COLOR="Red"]**Update:**[/COLOR]  I have just added Section 3 which goes through the process of overclocking a NVIDIA Graphics Card in coolbits.  The one problem with coolbits is that overclocking settings must be reapplied everytime you shut down your computer.  The second part of Section 3 shows you how to make a script that will automatically restore our desired overclocking settings at bootup.

---

### Post by fatsheep on 2006-09-19
**Updated!**  Fixed some errors in the "Making a Startup Script" section and I have redone section two to include all common game installers instead of just the .RUN format.  :)

---

### Post by KhaaL on 2006-09-25
I have one question now that I've started to game seriously on linux :p

How do you run, for instance music from VLC and have the sound from the game still intact?

---

### Post by fatsheep on 2006-09-25
That might be a bit tricky.  In my experience, GNOME's sound drivers tend to have the most trouble when there are two applications w/ sound open at the same time.  For example, if I'm watching google videos on firefox and listening to some music at the same time, the sound on the google videos can get cut off.  What happens when you run music in VLC and a game at the same time?

---

### Post by KhaaL on 2006-09-26
> **fatsheep said:**
> That might be a bit tricky.  In my experience, GNOME's sound drivers tend to have the most trouble when there are two applications w/ sound open at the same time.  For example, if I'm watching google videos on firefox and listening to some music at the same time, the sound on the google videos can get cut off.  What happens when you run music in VLC and a game at the same time?

Well what happens is that I only head the output of VLC, and the game is pretty much muted (running ut2004 here). I also did try and aoss'ing ut2k4, but that results in about 1 sec sound delay and that doesn't really help in a fast paced FPS. i also tried to run ut2k4 normally and run aoss mocp but it gave the error that the device was busy. 

Hehe, I'm really trying hard to find a way here but haven't had sucess yet...

---

### Post by fatsheep on 2006-09-26
Sorry I can't help you there. :(   However, if you do find a solution please post back here so I can add it to the list.  I'd be interested and I'm sure everyone else would as well.

---

### Post by nowshining on 2007-09-15
I know this is Almost a year old - Really Really close to the Bday of the OPs post 1st post, well ty, the overclocking settings I was having trouble with and the rest of the forums and even nvidias didn't explain it well and never said to to create a script and once I read you post - well the part for overclocking - well it worked, ty ty.. :)

---

### Post by lkjoel on 2011-08-27
Thanks for the tutorial! I was able to overclock my graphics card with it.
I have a GeForce 6200 (yeah, pretty old), and I found that the maximum safe setting (for 2D and 3D) is:
GPU: 400MHZ
Memory: 620MHZ

---

### Post by PNDK on 2011-08-28
Wow great share many thanks :P
[RIGHT][SIZE=1][COLOR=white]Online key store, pc game store, pc game seller onlinecdkeyseller.com[/COLOR][/SIZE][/RIGHT]

---

### Post by MaximB on 2011-08-28
> **lkjoel said:**
> Thanks for the tutorial! I was able to overclock my graphics card with it.
I have a GeForce 6200 (yeah, pretty old), and I found that the maximum safe setting (for 2D and 3D) is:
GPU: 400MHZ
Memory: 620MHZ

Gravedigger ?! were is CK / AI ???
:D

P.S
Generally I would avoid using old tutorials for new distros

---

### Post by lkjoel on 2011-08-28
I don't really need a graphics card, except for speeding up my system. I'm not a gamer (except if you count light cycles) ;-).

---

