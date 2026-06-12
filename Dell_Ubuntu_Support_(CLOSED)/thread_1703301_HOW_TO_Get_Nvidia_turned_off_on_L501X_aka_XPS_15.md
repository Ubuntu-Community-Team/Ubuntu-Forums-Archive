---
title: "HOW TO: Get Nvidia turned off on L501X aka XPS 15"
date: 2011-03-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by iammeagain on 2011-03-09
Going to try and incorporate some of this in the next few weeks. [http://ubuntuforums.org/showpost.php?p=10553459&postcount=23](http://ubuntuforums.org/showpost.php?p=10553459&postcount=23)
5 classes, finals coming, work, plus a court case with in laws don't give me as much time as I would like to work on this.

No warranty etc, I'm not responsible for damages to laptop if they incur. I am figuring this out as I go as well. Just trying to be a help to the community.

First and foremost my sources for figuring this out:
[https://lists.launchpad.net/hybrid-graphics-linux/msg00450.html](https://lists.launchpad.net/hybrid-graphics-linux/msg00450.html)
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)
[http://linux-hybrid-graphics.blogspot.com/2011/02/linux-dell-xps-l501x-switching-nvidia.html]("http://linux-hybrid-graphics.blogspot.com/2011/02/linux-dell-xps-l501x-switching-nvidia.html")


[COLOR="DarkRed"][SIZE="3"]I have only tested this working on the i5 460m l501x Dell xps 15. I have been trying to make updates to make this a better set up. I have found a way to make these changed permanent. I'll update this original post later on. For now I'll provide a link to the updated post. I want the below info to be kept so that others may be able to figure out a method usable for other models.
[http://ubuntuforums.org/showpost.php?p=10754116&postcount=25](http://ubuntuforums.org/showpost.php?p=10754116&postcount=25)[/SIZE][/COLOR]



[COLOR="Blue"][SIZE="4"]Step 1[/SIZE][/COLOR]
See that both Intel and Nvidia are displayed as being used by entering this into terminal
```
 lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
```
It should read something like this:
> 00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18) (prog-if 00 [VGA controller])
02:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df1] (rev a1) (prog-if 00 [VGA controller])


[COLOR="Blue"][SIZE="4"]Step 2[/SIZE][/COLOR]
Make sure you have git installed, if  you don't enter the below command
```
 sudo apt-get install git
```

[COLOR="Blue"][SIZE="4"]Step 3[/SIZE][/COLOR]
This part comes from the linux-hybrid-graphics.blogspot.com
This gets the acpi_call.git which allows video switching. We have no need for the ./test_off.sh command since it doesn't run.
```
 
git clone http://github.com/mkottman/acpi_call.git
cd acpi_call
make
sudo insmod acpi_call.ko

```

[COLOR="Blue"][SIZE="4"]Step 4[/SIZE][/COLOR]
Instead of ./test_off.sh we use the command
```
 sh m11xr2.sh off
```
This command will be downloaded with acpi_call.git


[COLOR="Blue"][SIZE="4"]Step 5[/SIZE][/COLOR]
Check that it worked.
```
 lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
```
The output should look like this:
> 00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18) (prog-if 00 [VGA controller])
02:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df1] (rev ff) (prog-if ff)


[COLOR="MediumTurquoise"][SIZE="2"]Re-enable[/SIZE][/COLOR]
To re-enable all that is needed to run the script m11xr2.sh with on
```
 sh m11xr2.sh on
```
[COLOR="Red"][SIZE="4"]
All In One Step:[/SIZE][/COLOR]
If you want it all in one step then try this:
```

 sudo apt-get install git

 git clone http://github.com/mkottman/acpi_call.git
 cd acpi_call
 make
 sudo insmod acpi_call.ko
 sh m11xr2.sh off
 lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA

```


This is what must be run each time you boot to continue to keep Nvidia off.
```
 sudo insmod acpi_call.ko
 sh m11xr2.sh off
```

Edit2: I added a script for when booting to disable Nvidia. [http://ubuntuforums.org/showpost.php?p=10545919&postcount=15](http://ubuntuforums.org/showpost.php?p=10545919&postcount=15)
       I want to incorporate adding this module into the kernel on boot, hopefully in the next few weeks.
Edit1: It seems to work as expected now that I have checked my battery usage. I can see when I'm idle and using m11xr2 off the normal drain is 1.3W. Once I turn m11xr2 on the power usage jumps to 1.6W or higher and will not drop down to 1.3W again until I turn it off once more. I don't know the nitty gritty but I'll try to look at the code used.
Edit0: It appears the script for turning it off must be run each time you boot up. Should probably look into putting this as part of my boot up sequence

No warranty, I'm not responsible for damages to laptop if they incur. I am figuring this out as I go as well. Just trying to be a help to the community.

---

### Post by iammeagain on 2011-03-09
If someone could please give me info on how to check my overall power usage that would be great. I really want to verify this is helping battery life without having to just sit here with it off and on.

---

### Post by svast on 2011-03-09
> **iammeagain said:**
> If someone could please give me info on how to check my overall power usage that would be great. I really want to verify this is helping battery life without having to just sit here with it off and on.

I guess 'powertop' is your friend

---

### Post by Slave2Metal on 2011-03-09
From terminal you can use this to check before and after module load
```
grep rate /proc/acpi/battery/BAT0/state
```

or
```
cat /proc/acpi/battery/BAT0/state

```

and to see if your module loaded.  If its loaded, then your card should be off.
```
lsmod | grep m11xr2
```

---

### Post by iammeagain on 2011-03-09
That powertop worked great since it reloaded without me having to sit there and run it each time. I can see when I'm idle and using m11xr2 off the normal drain is 1.3W. Once I turn m11xr2 on the power usage jumps to 1.6W or higher and will not drop down to 1.3W again until I turn it off once more.

@Slave2Metal
The script I believe just turns off the card. It doesn't stay loaded or used after that. so instead of lsmod | grep m11xr2
I was using 
```
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA

```
Which reads out the info on my two VGA controllers and tells me which are being accessed.

```
lsmod | grep m11xr2
```
Didn't print anything for me. What should I have expected with that one?

---

### Post by Slave2Metal on 2011-03-09
This is the output I get, telling me that the module is loaded.  Plus the increase in battery life.  I have been trying to get a script to run this at boot, with no luck.  So I'm loading it manually for the time being.  The implementations are just different.  Yours might be acpi_call instead of m11, I dunno.
```

XPS:~$ lsmod | grep m11xr2hack
m11xr2hack              1737  0 
```> **iammeagain said:**
> That powertop worked great since it reloaded without me having to sit there and run it each time. I can see when I'm idle and using m11xr2 off the normal drain is 1.3W. Once I turn m11xr2 on the power usage jumps to 1.6W or higher and will not drop down to 1.3W again until I turn it off once more.

@Slave2Metal
The script I believe just turns off the card. It doesn't stay loaded or used after that. so instead of lsmod | grep m11xr2
I was using 
```
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA

```Which reads out the info on my two VGA controllers and tells me which are being accessed.

```
lsmod | grep m11xr2
```Didn't print anything for me. What should I have expected with that one?

---

### Post by iammeagain on 2011-03-09
I really don't get the use of the lsmod | grep It just seems to give some info on the size of the module. That doesn't tell power drain. 

Are you running an XPS L501X as well? Because I don't see m11xr2hack listed anywhere in my lsmod if I just load all of it. All I see is the acpi_call.

I haven't attempted a boot up script yet. But it needs my password to go into sudo. I'm not sure of a secure way to do this.

---

### Post by iammeagain on 2011-03-09
I am still learning this as I go. I see that insmod - install loadable kernel module. It only loads for the one session though. Could I just permanently install it in some way? Or is that got to do with custom kernel crud? Because if I could permanently add that then a small script to run the m11xr2.sh wouldn't be hard at all to make.

---

### Post by Slave2Metal on 2011-03-09
I believe you are correct about the kernel crud.  The information I was going by, is from the fedora forums to disable the card on an alienware m11xr2.  I can load it manually, but no such luck getting the script to work.  I'm researching vga switcheroo and kernel mode setting now.  The lsmod wont tell power drain.  It tells you if the module is loaded.  Have you checked out the thread at fedora forums?

Yes, I am trying to get this to work on an xps 15.

Collaborating with someone that has a vested interest may be they way to go.  I'm pretty much stumped and cannot figure out what's missing,either in my process or the instructions.
[http://forums.fedoraforum.org/showpo...0&postcount=39]("http://forums.fedoraforum.org/showpost.php?p=1402470&postcount=39")
[http://forums.fedoraforum.org/showpo...4&postcount=45]("http://forums.fedoraforum.org/showpost.php?p=1402584&postcount=45")

---

### Post by iammeagain on 2011-03-09
I have not seen this fedora thread, can you throw me a link?

---

### Post by Slave2Metal on 2011-03-09
Links in post #9.

---

### Post by Slave2Metal on 2011-03-10
This thread might be more informative.
[http://forum.notebookreview.com/linux-compatibility-software/553945-help-new-linux-user-out-m11x-r2.html](http://forum.notebookreview.com/linux-compatibility-software/553945-help-new-linux-user-out-m11x-r2.html)

---

### Post by iammeagain on 2011-03-10
I see what they are doing there. They are including the acpi_call.ko and the m11xr2.sh off together in the make file so that one command will turn off the Nvidia. Where the way I am going about it allows someone to turn the Nvidia on and off but must run more commands. 

That post 45 one looks as though they are putting it into the kernel so that it loads with the system to automatically keep Nvidia off. Which would be what I would prefer. That is what I want to figure out how to do. I'll need to look more closely at that one.


Got a bit distracted on this, went and made a funfetti cake for a little bit. :D
Now gonna watch some TV while I half look at how to accomplish this.

---

### Post by iammeagain on 2011-03-10
I'm trying to read through [This]("http://forums.fedoraforum.org/showthread.php?t=248837&page=3") thread. Its very in depth. I'm gonna have to take a bit of time to sort it all out. Especially since it won't all apply to our model since its for that alienware m11x.

---

### Post by iammeagain on 2011-03-10
This isn't the best setup, but it is how I am running this temporarily. I made a script to run the script to turn off the Nvidia card.
My script looks like this.
```
#!/bin/sh
#Turns off Nvidia card.

 cd acpi_call
 sudo insmod acpi_call.ko
 sh m11xr2.sh off

```

I named it NvidiaOff.sh

I then used System ==> Preferences ==> Startup Applications

I made a new entry. Named it Nvidia Off and for the Command section I entered
```
gksudo bash /home/taylor/NvidiaOff.sh
```

It needs my root access in order to run the script, so it prompts me as I login. Which isn't too annoying compared to opening a terminal to do it all manually.

---

### Post by Slave2Metal on 2011-03-10
> **iammeagain said:**
> This isn't the best setup, but it is how I am running this temporarily. I made a script to run the script to turn off the Nvidia card.
My script looks like this.
```
#!/bin/sh
#Turns off Nvidia card.

 cd acpi_call
 sudo insmod acpi_call.ko
 sh m11xr2.sh off

```I named it NvidiaOff.sh

I then used System ==> Preferences ==> Startup Applications

I made a new entry. Named it Nvidia Off and for the Command section I entered
```
gksudo bash /home/taylor/NvidiaOff.sh
```It needs my root access in order to run the script, so it prompts me as I login. Which isn't too annoying compared to opening a terminal to do it all manually.

I'll be damned.  Thanks!  That was a heck of a lot easier than what I was trying to do.  Here's what mine looks like.  
```
#!/bin/sh
#Turns off Nvidia card.

 cd acpi_call
 sudo insmod m11xr2hack.ko

```

---

### Post by Slave2Metal on 2011-03-10
Now that I think about it, why in the hell wouldn't that same script work in rc.local?  I tried it, but it wouldn't work.  But if it did, there wouldn't be a need to give admin privileges.

---

### Post by iammeagain on 2011-03-13
[http://ubuntuforums.org/showthread.php?t=1579444&page=3](http://ubuntuforums.org/showthread.php?t=1579444&page=3)
Post 23 had some interesting links. I don't have time to give them a full look at. I'm going to try within the next few weeks. Pretty much similar optimus system have some much sleeker setups than our hack job scripts.

---

### Post by iammeagain on 2011-03-14
So far I used this to add the module to the boot time. So the script can be run without any root privileges.


```
cp acpi_call.ko /lib/modules/`uname -r`/kernel/drivers/acpi/
depmod
```

```
sudo gedit /etc/modules
```
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
acpi_call


Taken from here: [http://robbyx.net/blog/?p=190#codesyntax_4](http://robbyx.net/blog/?p=190#codesyntax_4)

Now I just need to read through and see how it is different for loading the script part. I guess I could just have that script run the same way I did the previous script through the startup application.


What I am trying right now is:


```
sudo su
cd /etc/init.d/
gedit nvdown
```

I pasted this in:

> #!/bin/sh
# Based on m11xr2hack by George Shearer

if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

acpi_call () {
    echo "$*" > /proc/acpi/call
    cat /proc/acpi/call
}


case "$1" in
off)
    echo NVOP $(acpi_call "\_SB.PCI0.P0P2.PEGP.NVOP 0 0x100 0x1A {255,255,255,255}")
    echo _PS3 $(acpi_call "\_SB.PCI0.P0P2.PEGP._PS3")
;;
on)
    echo _PS0 $(acpi_call "\_SB.PCI0.P0P2.PEGP._PS0")
;;
*)
    echo "Usage: $0 [on|off]"
;;
esac



```
sudo su
cd /etc/init.d/
update-rc.d nvdown defaults 98 02
```

I tested it with:
```
bash /etc/init.d/nvdown off

```

I guess these things need to be done as well at the end. This came from the above link as well.
> 
Last but not least, blacklist the nouveau driver (reported to create instability when playing with acpi_call). Create a file named /etc/modprobe.d/blacklist-nvidia.conf with this content:

```
blacklist nouveau
blacklist nvidia
```
And regenerate the initramfs image for the current kernel:

```
update-initramfs -u
```

I haven't tried this yet, I am just giving updates as I try it out.

---

### Post by Slave2Metal on 2011-03-14
> **iammeagain said:**
> So far I used this to add the module to the boot time. So the script can be run without any root privileges.


```
cp acpi_call.ko /lib/modules/`uname -r`/kernel/drivers/acpi/
depmod
``````
sudo gedit /etc/modules
```
Taken from here: [http://robbyx.net/blog/?p=190#codesyntax_4](http://robbyx.net/blog/?p=190#codesyntax_4)

Now I just need to read through and see how it is different for loading the script part. I guess I could just have that script run the same way I did the previous script through the startup application.
I'm not following, too thick in the head I guess.  So the script that was used in the startup application is still running?  The above commands are enabling you to load the module without a password?

---

### Post by iammeagain on 2011-03-15
Correct, it is loading without the need for a password at boot. I added more to the previous post. Not all of it is tried out to be working yet.

---

### Post by kornfan71 on 2011-03-27
This is a great guide! It works great, and seems to decrease the load on the battery.

However, it does seem to cause an intermittent issue where the screen can become "snowy," like an antenna TV that has a less-than-perfect signal. I have to reboot to get it back to normal. Anyone else have this issue? :confused:
(I'm using Kubuntu right now, but I think it happened in Ubuntu as well.)

Thanks!

---

### Post by iammeagain on 2011-04-10
Sorry for the late reply. Just started a new quarter at school. I have not gotten this snowy issue you mentioned. I have run linux for long periods of time as well, using the whole extended battery's power. I don't have Kubuntu installed. I have heard that the optimus is even less compatible with KDE than Gnome. I don't remember the details on why.

Any particular programs you run a lot that you can see a correlation with possibly causing the problem.

---

### Post by kornfan71 on 2011-04-10
No, I don't really notice any programs causing it. It's only sporadic, and doesn't happen often, so I'm probably not going to worry about it...

Hopefully Linux gets better graphics switching support in the future, though. :D

---

### Post by iammeagain on 2011-05-01
[COLOR="RoyalBlue"]This is a bit cleaned up and revised. I am using this on 11.04 now and without any problems yet. [/COLOR]

Use this to add the module to the boot time. So the script can be run without any root privileges.


```

git clone http://github.com/mkottman/acpi_call.git
cd acpi_call
make
cp acpi_call.ko /lib/modules/`uname -r`/kernel/drivers/acpi/
depmod
sudo gedit /etc/modules
```
Add this line to /etc/modules:
> acpi_call


This next step creates a file named nvdown to turn the Nvidia off and on. use the same code from m11xr2hack by George Shearer. (Which is listed right below.)

```
sudo su
cd /etc/init.d/
gedit nvdown
```
The code to paste into this file is:
> #!/bin/sh
# Based on m11xr2hack by George Shearer

if ! lsmod | grep -q acpi_call; then
echo "Error: acpi_call module not loaded"
exit
fi

acpi_call () {
echo "$*" > /proc/acpi/call
cat /proc/acpi/call
}


case "$1" in
off)
echo NVOP $(acpi_call "\_SB.PCI0.P0P2.PEGP.NVOP 0 0x100 0x1A {255,255,255,255}")
echo _PS3 $(acpi_call "\_SB.PCI0.P0P2.PEGP._PS3")
;;
on)
echo _PS0 $(acpi_call "\_SB.PCI0.P0P2.PEGP._PS0")
;;
*)
echo "Usage: $0 [on|off]"
;;
esac



Run this afterwards

```

update-rc.d nvdown defaults 98 02
gedit /etc/modprobe.d/blacklist-nvidia.conf
```

Place this into the blacklist-nvidia.conf:
> blacklist nouveau
blacklist nvidia

Lastly run this

```
update-initramfs -u
```

Now this will turn off and on the Nvidia card, respectively:
```
bash /etc/init.d/nvdown off

```
```
bash /etc/init.d/nvdown on

```

If you want it to turn off right when you log into Ubuntu then follow this part:

GO to System ==> Preferences ==> Startup Applications
Click Add

Name: Nvidia Off
Command: bash /etc/init.d/nvdown off
Comment: Turns Nvidia Off

Click Add
Now whenever you login it should automatically turn off the Nvidia card to save you battery life.

If you still want to take advantage of 3d capabilities you will need to do the below. The Xorg still thinks that the Nvidia card is usable so we must get rid of all its traces.
```
sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```
A restart and all should be good. 

Battery life should be awesome, it was estimating 5.5hrs on my 9 cell. I didn't time it since I was rebooting and trying to get minecraft running as well, but it definitely was close to the estimated time. =D

---

### Post by iammeagain on 2011-05-01
A new issue I am having is that the opengl does not seem to function for me. 

When I try to run glxgears, I get the error:
```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

``` 

glxinfo gives
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
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

```

It appears it may be from disabling the nvidia and not completely unistalling it. See [here]("http://www.linuxquestions.org/questions/linux-hardware-18/xlib-extension-glx-missing-on-display-0-0-a-200313/")

Gonna mess with this now. From here down will be different updates on the status of my attempts.
Edit1:
I can't install Nvidia drivers so I thought I may give intel drivers a shot. This is what I have dug up so far. Unsure how to install them though. [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)
[http://intellinuxgraphics.org/2011Q1.html](http://intellinuxgraphics.org/2011Q1.html)
Edit2:
I tried to force load glx by adding glx "load" to the xorg.conf
That just caused my screen to black out at boot.
Edit3:
I want to try install installing the X.org edgers PPA like what was done here, but I am unsure how.
[Here]("http://ubuntuforums.org/showthread.php?t=1657319")



:::::SOLVED:::::

I got this solved through this method:
```
sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```

Which came from here:
[http://ubuntuforums.org/showthread.php?t=1301433&highlight=GLX+missing+display](http://ubuntuforums.org/showthread.php?t=1301433&highlight=GLX+missing+display)

---

### Post by iammeagain on 2011-05-02
I know I'm making multiple posts in a row which is frowned upon, but this is more new info pertaining to this subject I thought others might find useful.

It is possible to make use of the CUDA cores through non graphical application. I'm not sure if this could be used while it is disabled as a vga controller. Thats an try for another day but here are the links if anyone is interested. Read the first one first. The second is a related link they supplied.
[https://lists.launchpad.net/hybrid-graphics-linux/msg00460.html](https://lists.launchpad.net/hybrid-graphics-linux/msg00460.html)
[http://ubuntuforums.org/showthread.php?t=1625433](http://ubuntuforums.org/showthread.php?t=1625433)

---

### Post by shevek. on 2012-01-11
@iammeagain, your solution in #26 works like charm :D  

I have a Dell Inspiron N5110, with Optimus. Brand new, it had just 2h of battery life. I did:

[LIST=1]
[*]For disabling the nvidia the solution of #1 didn't work for me, so I used the standard [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)  or better, the solution of [http://robbyx.net/blog/?p=190](http://robbyx.net/blog/?p=190) (section #3 about nvidia) that includes how to insert the whole thing in the startup. The solution is for an Asus, but the only difference is that in the "nvdown" script, I had to include the module that works for me (specified after executing test_off.sh), in my case _SB.PCI0.PEG0.PEGP._OFF
[*]For enabling 3D acceleration with the Intel, I had the same prob specified in #26 and the solution of the end of that post worked perfectly (don't worry if it deletes the package "ubuntu-desktop", it's a useless meta-package).
[/LIST]
Now the laptop gives more than 3h battery life, 3D acceleration works and (as a side effect) Jupiter works in my Unity top bar. Thanks a lot everyone!

PS: For newcomers, nice compiled info in the thread [http://ubuntuforums.org/showthread.php?t=1657660&page=1](http://ubuntuforums.org/showthread.php?t=1657660&page=1)

---

### Post by coderus on 2012-01-20
@shevek. @iammeagain hi! i have similar N5110 laptop with ubuntu 11.10
i followed your steps, acpi fine, thanks, but
```
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```
[s]says "E: Internal Error, No file name for libgl1-mesa-dri"
any solution, please?[/s]

:::SOLVED:::
solved with
```
apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:i386 libgl1-mesa-dri:amd64 xserver-xorg-core
```
after reboot glx working, yahoo))

---

### Post by Lekensteyn on 2012-01-20
acpi_call has now been deprecated in favor of bbswitch. Bumblebee 3.0 replaces Ironhide and works with bbswitch: [http://askubuntu.com/q/36930/6969](http://askubuntu.com/q/36930/6969)

---

### Post by lahirurane on 2013-03-23
Hi i m new to ubuntu. 
I tried the code 

```
 sudo insmod acpi_call.ko
 sh m11xr2.sh off
```

and i get an error

sh: 0: Can't open m11xr2.sh

---

