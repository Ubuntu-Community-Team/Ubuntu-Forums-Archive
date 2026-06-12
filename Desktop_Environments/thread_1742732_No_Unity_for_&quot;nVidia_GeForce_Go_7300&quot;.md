---
title: "No Unity for &quot;nVidia GeForce Go 7300&quot;?"
date: 2011-04-29
forum: Desktop Environments
---

### Post by chrismyers on 2011-04-29
Hi guys,

I just installed 11.04.

Upon first boot I get the message that Unity will not run on my hardware - I expected that because I need to install the nVidia drivers via "Additional Drivers".

However, after installing the nVidia driver & rebooting, Unity still does not run.

Does anyone know if Unity is unsupported for "nVidia GeForce Go 7300" or do I need to switch it on somehow?

Regards,

Chris.

P.S.

My laptop is a Lenovo 3000 N200 (0769-B4G)

---

### Post by otherethe on 2011-04-29
> **chrismyers said:**
> Hi guys,

I just installed 11.04.

Upon first boot I get the message that Unity will not run on my hardware - I expected that because I need to install the nVidia drivers via "Additional Drivers".

However, after installing the nVidia driver & rebooting, Unity still does not run.

Does anyone know if Unity is unsupported for "nVidia GeForce Go 7300" or do I need to switch it on somehow?

Regards,

Chris.

P.S.

My laptop is a Lenovo 3000 N200 (0769-B4G)
Have you tryed the files from nvidia.com?

Ether way here try this Download one of these
[http://www.nvidia.com/object/linux-display-ia32-270.41.06-driver.html](http://www.nvidia.com/object/linux-display-ia32-270.41.06-driver.html) for 32bit systems
[http://www.nvidia.com/object/linux-display-amd64-270.41.06-driver.html](http://www.nvidia.com/object/linux-display-amd64-270.41.06-driver.html) for 64bit systems

after you get it saved move it to your desktop and rename it n.run just so you can type it faster later

after you've done that hold down ctrl alt press f2 key Login then type in sudo stop gdm *Enter*
Once you've done that type in cd Desktop *enter*
now type in sudo sh n.run
Once you install tell it to confg for you after it's closed type in sudo start gdm

---

### Post by chrismyers on 2011-04-29
Thanks for your reply [otherethe]("http://ubuntuforums.org/member.php?u=1165821")

I haven't needed to use nVidia's drivers since Breezy Badger (or was it Dapper), so to be honest, I'd forgotten about doing that, but I gave it a try.

Oops... It failed to install properly & trashed X - Have you successfully installed nVidia's drivers on 11.04?

Anyway. Rather than unpick the driver from the kernel, I just reinstalled from scratch - Still no Unity.

Anybody have any other ideas?

Cheers.

---

### Post by numeeja on 2011-04-29
I've just got Unity working on my Acer 9003 with nVidia GeForce Go 7300

To follow the steps I took for this:

Log off to get to the login screen

On the logon screen select your user account, in the drop-down at the bottom select Ubuntu Classic (no effects) and then log in as normal

Go to System -> Additional Drivers, deactivate the current nVidia Driver and Restart

Login, Go to System -> Additional Drivers, and activate the "Experimental 3D Support for nVidia cards" driver which should be listed. Restart again

When you see the the login box, select your account and select 'ubuntu' in the drop-down, then login.

You should then (hopefully) see the unity desktop

---

### Post by Gone fishing on 2011-04-29
Same problem with G72 [GeForce 7300 LE]. This is a problem with both the 64 and the 34bit versions. It isn't just Unity, tty is scrambled and you can't run classic gnome with desktop effects.

I very disappointed.

How is the experimental open-source driver?

---

### Post by Krytarik on 2011-04-29
Please see this earlier thread on how to use Unity with a GeForce Go 7300/7400 card and the proprietary Nvidia driver:
[http://ubuntuforums.org/showthread.php?t=1741566](http://ubuntuforums.org/showthread.php?t=1741566)

Hope it helps!

---

### Post by chrismyers on 2011-04-29
OK thanks for your help guys. I got it working.

I used the "Experimental nVidia Drivers"

I did:

sudo nano /etc/environment

and added this line:

UNITY_FORCE_START=1

I am unsure of the wisdom of forcing the startup of Unity. My system may be unstable - time will tell.

Thanks again.

---

### Post by Krytarik on 2011-04-29
> **chrismyers said:**
> 
I am unsure of the wisdom of forcing the startup of Unity. My system may be unstable - time will tell.
The worst thing that may happen is that the Unity plugin crashes, which can happen in a non-forced case as well. After all, it's just a plugin of Compiz', and you wouldn't expect any wider-ranging damage from any other of its plugins as well. Even not if the whole Compiz crashes.

---

### Post by pietermeurs on 2011-05-02
> **chrismyers said:**
> OK thanks for your help guys. I got it working.

I used the "Experimental nVidia Drivers"

I did:

sudo nano /etc/environment

and added this line:

UNITY_FORCE_START=1

I am unsure of the wisdom of forcing the startup of Unity. My system may be unstable - time will tell.

Thanks again.

thanks for this tip Chris! It now also works fine with me on my Lenovo 3000 n200. One question though, does it make the fan of your laptop work more?

---

### Post by chrismyers on 2011-05-02
> **pietermeurs said:**
> One question though, does it make the fan of your laptop work more?

Occasionally it does! Though it is running cold at the moment.

I believe it is whilst playing a flash video in Firefox, but I'm not certain just yet.

Let me know what you discover.

---

### Post by linux_dream on 2011-05-13
I'm currently having the same problem. (see: [http://ubuntuforums.org/showthread.php?t=1756818&highlight=unity+nouveau&page=2](http://ubuntuforums.org/showthread.php?t=1756818&highlight=unity+nouveau&page=2))

From what I've understood from this thread, it's a problem with the nvidia drivers.
So I erased them (from Ubuntu software center) and I installed the "nouveau"'s one from the Ubuntu software center.

I added the line "UNITY_FORCE_START=1" in the /etc/environment file.

When I restart my computer I see no Unity stuff and I have no taskbar.
Screenshot can be seen on the uploaded picture...

Any hope for me?

EDIT: For some reason the picture fails to upload.  It's basically my background with my icons, mouse pointer and no taskbar.

---

### Post by Krytarik on 2011-05-14
linux_dream, please see if this troubleshooting guide helps you:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Greetings.

---

### Post by linux_dream on 2011-05-14
> **Krytarik said:**
> linux_dream, please see if this troubleshooting guide helps you:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Greetings.
Well thanks but I'm unsure if I should try this way.  
If I erase back the line "UNITY_FORCE_START=1" in the environment file, I get my taskbar (although no effects of compiz and nothing from Emerald and with graphics bugs like I can't open youtube videos in full screen mod or some pixels sometime messes up in my task bar) and I can access most of what my Ubuntu have.

I was thinking about a way to enable the use of the drivers of Nouveau as I doubt I'm using them currently.  If I can do that, I'm almost sure a restart would already fix my graphics bugs and if I add the line "UNITY_FORCE_START=1" in the environment file I'm almost sure I could get a working Unity.  
So to me it's a matter of enabling the Nouveau drivers (or installing them correctly.  I only installed them from the Ubuntu Software Center and removed the nvidia ones).

Right now my /etc/X11/xorg.conf contains a line "nv" instead of "nvidia", otherwise I can't even load fully Ubuntu, it freezes right at start so that I can't even open a terminal (not even left click+create something) so I'm somehow confused about what I must do there since I modified it.  

I just don't know where to head now.

---

### Post by beew on 2011-05-14
To get Unity and 3d desktop effects with the nouveau driver you need to install the package libg1-mesa-dri-experimental from Synaptic. Just install the package and reboot and it should work.

A warning: I find that the computer freezes sometimes and need a hard reboot with the nouveau driver (cursor still moves but clicking doesn't do anything) This happens with both 10.10 and 11.04. I have no problem with the Proprietary driver in 10.10 (haven't tried it in 11.04) My Nvidia card is G105M.

---

### Post by Krytarik on 2011-05-14
I guess you will already have installed the package *beew* is referring to.

But try moving your xorg.conf to a backup location or just rename it, since it will probably still contain some options specific to the proprietary "nvidia" driver.

And "nv" refers to the lowest level, non-3D-capable driver, "nouveau" would be the correct name. Try without any xorg.conf first.

If that doesn't work, reconfigure the mentioned package to possibly create a proper xorg.conf:
```
sudo dpkg-reconfigure libgl1-mesa-dri-experimental
```If that fails to do so, put the previous xorg.conf back into place, replace "nv" by "nouveau" and try to remove the options specific to the proprietary driver.

---

### Post by linux_dream on 2011-05-14
Actually I do not have installed the package libg1-mesa-dri-experimental.  In synaptic there appear to be 2 packages with this name.  Which one should I install?

---

### Post by linux_dream on 2011-05-14
Ok I installed one and the other was installed automatically too.  I modified the xorg.conf file with the line "nouveau" instead of "nvidia" or "nv".
I restarted.  I couldn't even load Ubuntu or the terminal.  There was some text in like a terminal and with a [fail] part.  All other parts had [OK] and it stopped to load at some points.

What I did was enter recovery mod and type "sudo nvidia-xconfig" to back my xorg.conf file.

Now I have a resolution I'm not able to change (640x480) instead of 1360x768 so it's a big pain to even write here.   
I changed back the xorg.conf file to "nv" since it's the only one that doesn't freeze until now.

Is there any hope remaining for my case?

---

### Post by linux_dream on 2011-05-14
I just tried "sudo dpkq-reconfigure libgl-mesa-dri-experimental" but I get the message that it isn't installed...

I really need help.  First solve this resolution problem and then continue with drivers/Unity please.  I even had to remove icons in my taskbar for the menu to appear (so small resolution that all the bar was overloaded with icons).

---

### Post by linux_dream on 2011-05-14
Here is my xorg.conf file:
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Krytarik on 2011-05-14
I just checked the package name, it's actually "libgl1-mesa-dri-experimental".

However, your xorg.conf doesn't include any options specific for the proprietary driver.

But try renaming/moving it anyway. If that just leads to the "nv" driver being loaded again, try the reconfigure thing.

You can check what driver is running with:
```
lshw -c video
```

---

### Post by linux_dream on 2011-05-14
How to move xorg.conf?  It's in read only I think.  Anyway it's already messed up (it used to be a short file and when I typed "sudo nvidia-xconfig" I totally messed it up as you can see and now my resolution is stuck on 640x480.  If you know how I can get back my resolution you'd make me a big favor.


I tried to check out what driver I'm using and I get:
isaac@isaac-desktop:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: G71 [GeForce 7300 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d1000000-d1ffffff memory:c0000000-cfffffff memory:d0000000-d0ffffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
isaac@isaac-desktop:~$ 


And about "libgl1-mesa-dri-experimental", I installed it.  If I change the line "nvidia" of the xorg.conf into "nouveau" then I can't load Ubuntu desktop nor terminal, as I said in a previous post.

---

### Post by linux_dream on 2011-05-14
isaac@isaac-desktop:~$ sudo dpkq-reconfigure libgl1-mesa-dri-experimental
[sudo] password for isaac: 
sudo: dpkq-reconfigure: command not found
isaac@isaac-desktop:~$


EDIT: Just tried with dpkg, seems to have worked... now I think I have to restart.
Well I opened the xorg.conf and nothing seems to have changed...
What to do now?  I'm totally stuck.

---

### Post by Krytarik on 2011-05-14
Then just delete the xorg.conf with:
```
sudo rm /etc/X11/xorg.conf
```
Also notice that it's "dpk[COLOR=Blue]**g**[/COLOR]-...", not "dpk**[COLOR=Red]q[/COLOR]**-...".

---

### Post by linux_dream on 2011-05-14
Ok thanks.  I just removed the file.  I'll try a restart.

---

### Post by linux_dream on 2011-05-14
Loaded the desktop (without taskbars) with a proper resolution but all frozen.
I tried to modify the xorg.conf in a terminal (in the recovery mod) but there was no such file so it created an empty one.
I typed "sudo nvidia-xconfig" to back the file up and then I modified it to change the nvidia line into nv.  I did "startx" and I'm here with this small resolution again at the same point.


What should I do now?

---

### Post by linux_dream on 2011-05-14
I'm desperate guys!  I need to get back to a normal resolution first...  Please someone help me for that!

---

### Post by Krytarik on 2011-05-14
Maybe it wasn't such a good idea to install "libgl1-mesa-dri-experimental" manually.

Try this:
- Remove it again:
```
sudo apt-get purge libgl1-mesa-dri-experimental
sudo apt-get autoremove
```- Remove the xorg.conf again.
- Install the "experimental" driver through "Additional Drivers".

If that doesn't work any better, try upgrading the "nouveau" driver through Xorg-Edgers' PPA, it offers more recent drivers than the offical repos. Notice that this would upgrade a lot of other packages as well.
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```If you need/want to remove those PPA and downgrade the concerning packages again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```

---

### Post by linux_dream on 2011-05-14
Thanks for your help Krytarik.
I've removed what you told me to, but what do you mean by "Install the "experimental" driver through "Additional Drivers".".  
Where exactly?  Where can I find additional drivers, what is their names exactly?

---

### Post by Krytarik on 2011-05-14
Unfortunately, I haven't seen a screenshot or detailed description of how it looks like in Natty's "Additional Drivers" GUI. But the driver is definitely named "experimental".

Where you find "Additional Drivers" obviously depends on if you are running Unity or classic Gnome, but you can just
- press Alt+F2
- enter:
```
jockey-gtk
```

---

### Post by linux_dream on 2011-05-14
Thanks again.
I'm having a problem: error message when doing jockey-gtk.
I took a screenshot.

---

### Post by Krytarik on 2011-05-14
So, I take you are running classic Gnome. Then just take the menu way:
"System -> Administration -> Additional Drivers".

---

### Post by linux_dream on 2011-05-14
> **Krytarik said:**
> So, I take you are running classic Gnome. Then just take the menu way:
"System -> Administration -> Additional Drivers".
I don't have anything like Additional Drivers.
The closest thing I find is "Nvidia X server settings".  I can't take a screenshot because the "print" key doesn't seem to work while in a menu.

---

### Post by Krytarik on 2011-05-14
(Re)install the package "jockey-gtk":
```
sudo apt-get install --reinstall jockey-gtk
```
Then check again.

---

### Post by linux_dream on 2011-05-14
Wow thank you.  Now I see it.
Well I have another problem.
It says I'm not using any drivers even though there is a green bubble with the latest drivers of Nvidia.
With my current resolution it's impossible to go down.  I can't see anything else than what the uploaded picture shows.
What should I do?

Edit: I could resize the window a very bit, just enough to read that the driver is activated but NOT in use.

---

### Post by Krytarik on 2011-05-14
Hmm, no "experimental" driver there to choose. But you may try the "nvidia-173" first, since quite a lot of users seem to have issues with the "nvidia-current" of Natty currently. You should be able to move the window upwards by using Alt+LeftClick -> move, in order to get to the buttons at the lower end.

---

### Post by linux_dream on 2011-05-14
Ok done.  I have enabled it, but it says the drivers aren't in use.  Probably because of the modified xorg.conf file?  I must put back the line "nvidia"?  
Right now I have horrible graphics, taking a screenshot so yuo can see by yourself:

---

### Post by linux_dream on 2011-05-14
Wow.  Modified back the xorg.conf.
I rebooted and now I can load Unity without any freeze!
But I still don't have Emerald working.
When I minimize the window of firefox, I can't see it in my task bar...  Is this normal?
I also lost my taskbar I used to have in the bottom of the screen.


I'd like to install the "nouveau" drivers instead of old Nvidia... how can I do that?

BUT THANK YOU, NOW I HAVE MY RESOLUTION BACK :D

---

### Post by Krytarik on 2011-05-14
Create a fresh proper xorg.conf for the proprietary driver:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```Then reboot/relogin.

Then check with the previously stated command what driver is running.

If the "nvidia" driver is running, you can also save your desired resolution into the xorg.conf:
- go to "System -> Administration -> NVIDIA X Server Settings"
- click at "X Server Display Configuration" on the left side
- check/choose your desired configuration
- click at "Save to X Configuration File"
- enter your password when asked for it
- choose replace, not merge!

EDIT: You figured to get back your resolution in the meantime. But you should follow that anyway. Backup your current xorg.conf before you do so.

---

### Post by linux_dream on 2011-05-14
I should do what you just said?  
I'll join a screenshot of my Ubuntu.
Is that ok or I must do 
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate 












?

---

### Post by Krytarik on 2011-05-14
> **linux_dream said:**
> 
But I still don't have Emerald working.
The current Emerald package in the official repos of Natty doesn't work with the current version of Compiz. But you could try to compile it yourself:
[http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/](http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/)
> **linux_dream said:**
> 
When I minimize the window of firefox, I can't see it in my task bar...  Is this normal?
I also lost my taskbar I used to have in the bottom of the screen.
Add "Window List" to your panel:
- right-click at your panel
- choose "Add To Panel"
- select "Window List"
- click at "Add"
> **linux_dream said:**
> 
I'd like to install the "nouveau" drivers instead of old Nvidia... how can I do that?

To do so
- remove the xorg.conf
- install "libgl1-mesa-dri-experimental" again
- add/upgrade through Xorg-Edgers' PPA
- reboot/relogin

EDIT: So, now you are running Unity. The instructions for the "Window List" only applies to classic Gnome. In Unity you have the combined launchers at the side panel.

---

### Post by linux_dream on 2011-05-14
> **Krytarik said:**
> The current Emerald package in the official  repos of Natty doesn't work with the current version of Compiz. But you  could try to compile it yourself:
[http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/](http://abz89.wordpress.com/2011/05/02/how-to-fix-emerald-in-ubuntu-11-04/)
Ok I will try that.  I tried the first step but this didn't erase emerald (didn't find it).
> Add "Window List" to your panel:
- right-click at your panel
- choose "Add To Panel"
- select "Window List"
- click at "Add"
I right clicked everywhere I could but this didn't do anything.
> 
To do so
- remove the xorg.conf
- install "libgl1-mesa-dri-experimental" again
- add/upgrade through Xorg-Edgers' PPA
- reboot/relogin

EDIT: So, now you are running Unity. The instructions for the "Window  List" only applies to classic Gnome. In Unity you have the combined  launchers at the side panel.
What do you mean by "- add/upgrade through Xorg-Edgers' PPA" and by   "Window List".  Do you mean now I don't have "system, applications,  etc?"

---

### Post by Krytarik on 2011-05-14
> **linux_dream said:**
> Ok I will try that.  I tried the first step but this didn't erase emerald (didn't find it).
Just follow the rest of the steps.
> **linux_dream said:**
> 
I right clicked everywhere I could but this didn't do anything.See below the very last quote.
> **linux_dream said:**
> 
What do you mean by "- add/upgrade through Xorg-Edgers' PPA"
That refers to my earlier post #27:
[http://ubuntuforums.org/showthread.php?p=10815828#post10815828](http://ubuntuforums.org/showthread.php?p=10815828#post10815828)
> **linux_dream said:**
> and by   "Window List".  Do you mean now I don't have "system, applications,  etc?"
That refers to the middle part, about the "Window List" applet in classic Gnome. I'm not sure if you were meaning classic Gnome or Unity when you posted the respective question.

Regarding the "classic" menus, since you are running Unity currently, you don't have those. See the very last link in my signature to get a grip on Unity. If you want to run classic Gnome instead, choose "Ubuntu Classic" as the "Session" option at the bottom of the login screen after clicking at your username.

EDIT: Since the website is currently not available, see here instead: [https://wiki.ubuntu.com/Unity](https://wiki.ubuntu.com/Unity)

---

### Post by linux_dream on 2011-05-14
First, thanks so much for everything and your patience!
> **Krytarik said:**
> Just follow the rest of the steps.
Ok I did.  Seems like all the installation worked.  But it still doesn't work (I mean I don't have my windows as I used to have.  Maybe I have to reinstall compiz, etc.)
> See below the very last quote.Ok.
> That refers to my earlier post #27:
[http://ubuntuforums.org/showthread.php?p=10815828#post10815828](http://ubuntuforums.org/showthread.php?p=10815828#post10815828)
Ok, I'm going to take care of that.  I just had a froze (had to reset the hard way).  My desktop froze after leaving the power saving mod.
  
  > If you want to run classic Gnome instead, choose "Ubuntu Classic" as the "Session" option at the bottom of the login screen after clicking at your username.
[https://wiki.ubuntu.com/Unity](https://wiki.ubuntu.com/Unity)
I'm not interested in the classic mod for now, but anyway I clicked on my username and there's only "chat accounts, diffusion accounts, about me" options.

---

### Post by linux_dream on 2011-05-14
I just followed all your steps in order to install the nouveau drivers.  All worked well but now when I go into Additional drivers, I don't see any other drivers than the 2 nvidias.  
The one with a green bubble shows "The driver is habilited but currently NOT in use".

How can I know what drivers I'm using?  And why doesn't it appear in the list?

---

### Post by Krytarik on 2011-05-14
> **linux_dream said:**
> 
Ok I did.  Seems like all the installation worked.  But it still doesn't work (I mean I don't have my windows as I used to have.  Maybe I have to reinstall compiz, etc.)
Are you maybe referring to the missing menu bars? That's another new feature.
Are the titlebars/borders of non-maximized windows correct?
Did you set the correct theme in "Emerald Theme Manager"?
> **linux_dream said:**
> 
Ok, I'm going to take care of that.  I just had a froze (had to reset the hard way).  My desktop froze after leaving the power saving mod.
  That may be related to a bug in "gnome-screensaver". There are a number of issues currently.
  > **linux_dream said:**
> 
I'm not interested in the classic mod for now, but anyway I clicked on my username and there's only "chat accounts, diffusion accounts, about me" options.
That wasn't the login screen, you need to log out to choose a different session option.
> **linux_dream said:**
> I just followed all your steps in order to install the nouveau drivers.  All worked well but now when I go into Additional drivers, I don't see any other drivers than the 2 nvidias.
"Additional Drivers" was used to show only proprietary drivers until Natty. And since the "experimental" driver wasn't offered to you by it, it doesn't list it now as well.
 > **linux_dream said:**
> How can I know what drivers I'm using?  And why doesn't it appear in the list?
Like I said before:
```
lshw -c video
```

---

### Post by linux_dream on 2011-05-14
> **Krytarik said:**
> Are you maybe referring to the missing menu bars? That's another new feature.
Are the titlebars/borders of non-maximized windows correct?
Did you set the correct theme in "Emerald Theme Manager"?

I am referring to the border of non maximized windows (and even some maximized windows, like firefox).  The cross to close the window is supposed to be like the one of windows 7 and all the border of the windows too.  I have set this theme in Emerald once again, even tried other themes I have.  None seem to work.  I never had menus.  I will take a screenshot if I can and upload.
  > That may be related to a bug in "gnome-screensaver". There are a number of issues currently.
  
That wasn't the login screen, you need to log out to choose a different session option.
"Additional Drivers" was used to show only proprietary drivers until Natty. And since the "experimental" driver wasn't offered to you by it, it doesn't list it now as well.
 Ok thanks.
> Like I said before:
```
lshw -c video
```Whoops, sorry I forgot it was in this thread.
Well it shows I'm still using nvidia:
isaac@isaac-desktop:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: G71 [GeForce 7300 GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d1000000-d1ffffff memory:c0000000-cfffffff memory:d0000000-d0ffffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
isaac@isaac-desktop:~$

---

### Post by Krytarik on 2011-05-14
- You know, you need to run Emerald somehow to make it ...well... run. Set "CompizConfig Settings Manager -> Window Decoration -> Command" to "emerald --replace". You can also run that through the Alt+F2 dialog to test/restart it.

- Did you remove the xorg.conf before installing "libgl1-mesa-dri-experimental"? Seems not so. Now just rename it. Then reboot and see if the "nouveau" driver gets loaded. If not, do the reconfigure step again. Did you already upgrade through Xorg-Edgers' PPA?

---

### Post by linux_dream on 2011-05-14
> **Krytarik said:**
> - You know, you need to run Emerald somehow to make it ...well... run. Set "CompizConfig Settings Manager -> Window Decoration -> Command" to "emerald --replace". You can also run that through the Alt+F2 dialog to test/restart it.
Hmm I can't find it anymore.  I mean CompizConfig settings manager.  I think I had it...
> - Did you remove the xorg.conf before installing "libgl1-mesa-dri-experimental"? Seems not so. Now just rename it. Then reboot and see if the "nouveau" driver gets loaded. If not, do the reconfigure step again. Did you already upgrade through Xorg-Edgers' PPA?
You're right I didn't.  I first installed "libgl1-mesa-dri-experimental", then I removed (erased) xorg.conf.
I rebooted like 3 times now and I still have no xorg.conf file.  
About upgrating through Xorg-Edgers' PPA, yes I did following your command in a previous post.

---

### Post by linux_dream on 2011-05-14
By the way it seems each time I open Compiz, my upper task bar messes up.  It's all yellow now and the Unity left bar doesn't pop up anymore.  I can't press any button in firefox like closing the window or get back.  Last time I rebooted and at start all is ok.  It's Compiz that ruins it.

---

### Post by linux_dream on 2011-05-15
I fixed Emerald's problem.  
Now the nouveau driver problem remains.
So I must do >  Did you remove the xorg.conf before installing  "libgl1-mesa-dri-experimental"? Seems not so. Now just rename it. Then  reboot and see if the "nouveau" driver gets loaded. If not, do the  reconfigure step again. Did you already upgrade through Xorg-Edgers'  PPA? 	.  I can't rename xorg.conf since I have no such file.  
So I must go to the reconfigure step again... what is is that, I forgot?

---

### Post by Krytarik on 2011-05-15
> **linux_dream said:**
> 
So I must go to the reconfigure step again... what is is that, I forgot?
Like I stated in post #15:
[http://ubuntuforums.org/showthread.php?p=10813386#post10813386](http://ubuntuforums.org/showthread.php?p=10813386#post10813386)
```
sudo dpkg-reconfigure libgl1-mesa-dri-experimental
```If that doesn't create an xorg.conf, modify a hopefully backed up one for it.
You might also run "nvidia-xconfig" once more therefore.

---

### Post by linux_dream on 2011-05-15
Ok I did sudo nvidia-xconfig and then 
sudo dpkg-reconfigure libgl1-mesa-dri-experimental.

Now I must modify it by changing nvidia by nouveau?  And nothing else?  
In post 15 you wrote " try to remove the options specific to the proprietary driver.".
Not sure what to do now.

---

### Post by Krytarik on 2011-05-15
You should really follow my instructions one after another, and also respect the conditionals. But yeah, just replace "nvidia" by "nouveau" for a start, then post the xorg.conf so that I can check if there are any options specific to the proprietary driver.

---

### Post by linux_dream on 2011-05-15
> **Krytarik said:**
> You should really follow my instructions one after another, and also respect the conditionals. But yeah, just replace "nvidia" by "nouveau" for a start, then post the xorg.conf so that I can check if there are any options specific to the proprietary driver.
I understand, I'm just confused and never had such a big problem with Ubuntu.

Ok I modified the xorg.conf.  It is now like that:
-------------------------------------------------------------------
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nouveau"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
--------------------------------------------------------------------------------

Should I modify it again?  And then restart?  For example does the "VendorName "NVIDIA Corporation has some effects?
Thanks once again for your patience.

---

### Post by Krytarik on 2011-05-15
> **linux_dream said:**
> 
Should I modify it again?  And then restart?  For example does the "VendorName "NVIDIA Corporation has some effects?

No, it's fine, there are again no options specific to the proprietary driver in there. So, just try a reboot/relogin.

---

### Post by linux_dream on 2011-05-15
I tried to end the session.  It didn't work so I had to hard reboot.  Then it didn't load and left me with a terminal-like screen with lots of lines.  
One of them was *Stopping automatic crash report generation            [fail]
and the last line was *Stopping Userspace bootspalsh                         [OK]

I had to hard reboot, enter recovery mod, backup the xorg.conf and reboot (startx rebooted with a frozen desktop).

Hmm what do I do now?

---

### Post by Krytarik on 2011-05-15
Try skipping the boot splash by removing the boot option "splash" by following the instructions here:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You can also try some of the other options listed there.

Also try removing the "DPMS" option from your xorg.conf.

---

### Post by linux_dream on 2011-05-15
> **Krytarik said:**
> Try skipping the boot splash by removing the boot option "splash" by following the instructions here:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You can also try some of the other options listed there.

Also try removing the "DPMS" option from your xorg.conf.
Ok, please tell me if what I think is correct.

First, I type gksudo gedit /etc/default/grub in a terminal.  Then I modify the line "Grub_CMDLINE_LINUX_DEFAULT="quiet splash" into "Grub_CMDLINE_LINUX_DEFAULT="quiet splash nomodset".

Then I do 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=[COLOR=Red]\"[/COLOR]Linux[COLOR=Red]\"[/COLOR]" in a terminal or in the file I'm modifying?

And then I update grub.  
Is that ok?

---

### Post by Krytarik on 2011-05-15
Try the on-boot modification first, to see if it works.

Also, try removing "splash" first, like I said.

---

### Post by linux_dream on 2011-05-16
I've no idea what is the on boot modification nor how to remove the splash option.  I've checked in the link you gave me, read through it and still can't figure out what to do.  I've also done ctrl+F, "remove", "splash" but this didn't help.

---

### Post by Dalmose on 2012-05-30
It's working for me, but I have problems using the scale and the expose funktions in compiz with hot corners.  Its working, but the hot corner funktion is automately disabled after reboot.
Can you help me solve this.

---

