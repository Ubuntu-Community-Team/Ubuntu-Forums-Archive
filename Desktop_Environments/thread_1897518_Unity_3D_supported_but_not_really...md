---
title: "Unity 3D supported but not really.."
date: 2011-12-19
forum: Desktop Environments
---

### Post by davidafranklin on 2011-12-19
Hello,

I have a Toshiba M115-S3094 and have installed 11.10.
I ran the the test requirements and get a "YES" at everything (Unity 3D supported: YES)

However, I am not running 3D. I have tried several tweaks on CCSM and except a few effects that work, there is nothing like 3D, it all looks pretty blend.

Also, the entire Ubuntu is very slow. Not sure if Unity is the source or if I should go to a Gnome Classic.

I wish I could use Unity 3D, at least see what it is like. It is quite frustrating as I know my hardware supports it.

I have also downloaded all the 3rd party softwares during the install so I should have pretty much everything needed as far as drivers go.

Any suggestions? I do not want to go back to Windows :D

Thanks a lot

---

### Post by 2F4U on 2011-12-19
What are your hardware specs, what is the graphics card and which graphics driver are you using?

---

### Post by BC59 on 2011-12-19
Run this from a terminal to determine if your computer is able to run Unity 3D:
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by Frogs Hair on 2011-12-19
The test will indicate weather you can run Unity 3D , but you still may have to install a proprietary driver for the graphics card / chip from additional drivers . If you have installed the recommended driver I don't know what else to suggest . You wrote 3rd party software so I don't know if that means a driver or something else .

---

### Post by BC59 on 2011-12-19
To find if you are running Unity 3D:

```
echo $DESKTOP_SESSION
```

If the answer is _Ubuntu_ you are running Unity 3D.

---

### Post by davidafranklin on 2011-12-19
My graphic card is Intel Graphics Media Accelerator 950. The drivers I am using are the ones that came with 11/10. I visited the Intel drivers page and they recommend using the ones distributed with the Distro.

I already ran the requirement test (/usr/lib/nux/unity_support_test -p) where everything came as "YES".

Doing "echo $DESKTOP_SESSION" it says Ubuntu.

So I am no even more confused. Where is the "3D" and whatever awesome thing that Unity brings? It looks all pretty boring to me, nothing special.

---

### Post by Frogs Hair on 2011-12-19
Any settings for Unity are found in the CCSM under the Ubuntu Unity Plug-in .

---

### Post by BC59 on 2011-12-19
> **davidafranklin said:**
> My graphic card is Intel Graphics Media Accelerator 950. The drivers I am using are the ones that came with 11/10. I visited the Intel drivers page and they recommend using the ones distributed with the Distro.

I already ran the requirement test (/usr/lib/nux/unity_support_test -p) where everything came as "YES".

Doing "echo $DESKTOP_SESSION" it says Ubuntu.

So I am no even more confused. Where is the "3D" and whatever awesome thing that Unity brings? It looks all pretty boring to me, nothing special.

You are using Unity 3D. Don't expect something extraordinary, it's like unity 2D but little more fancy.

---

### Post by inobe on 2011-12-19
i don't use unity, nor do i use gnome desktops, but aren't folks able to switch to classic gnome and run compiz-settings-config?

[https://www.google.com/search?aq=2&oq=ubuntu+11.10+gnome&sourceid=chrome&ie=UTF-8&q=ubuntu+11.10+gnome+classic](https://www.google.com/search?aq=2&oq=ubuntu+11.10+gnome&sourceid=chrome&ie=UTF-8&q=ubuntu+11.10+gnome+classic)

i use kde/ kubuntu, it's been a few years since my last ubuntu visit:P

---

### Post by davidafranklin on 2011-12-19
Thanks Guys, Not sure what Unity is all about in this case.
To make things even worse, my heavy windows Vista used to be much faster than Ubuntu 11.10 which does not make sense.
I hope that going to the Gnome classic I will also get some speed improvements.

---

### Post by wildmanne39 on 2011-12-19
Hi, there are things that may be able to be worked out but you have to give us time to help.

If you want extra effects and have 3d support then click on the second link in my signature to set up the cube and effects.
Thanks

---

### Post by davidafranklin on 2011-12-20
Thank, I have tried to configure ccsm following your step by step instructions  and when iI try to uncheck either the OPenGL plugin or the Composite one, it closes automatically the window and plugin remain checked. Not sure if this is a bug.

---

### Post by davidafranklin on 2011-12-20
I also do not have the icons for 3D windows or Cube Gears

---

### Post by davidafranklin on 2011-12-20
Hello,
I think I messed up something. I was trying to configure Compiz and I unchecked the Unity plugin. Then suddenly, I lost my Unity bar, all the icons.. I decided to reboot to see if that was normal. Now after the login, I only have my desktop and a menu bar on the top right (Files, Edit, View, Bookmarks and Help). I do not have access to any programs, I do not not even see any of the usual icons on the top right (Wireless, battery...). I was able to access the Apps via the help file and uninstalled compiz top see if that solved the issue. Then another reboot and same thing. So I have now just an empty screen (my desktop background) and a few useless icons on the top left. Not sure what to do from now...

---

### Post by stinkeye on 2011-12-20
> **davidafranklin said:**
> I also do not have the icons for 3D windows or Cube Gears
If you upgraded from 11.04 you may need to remove your old compiz configs.
Run one at a time.
```
rm -rf .gconf/apps/compiz*
rm -rf .cache/compizconfig-1/
rm -rf .config/compiz-1/
rm -rf .compiz*

```

---

### Post by davidafranklin on 2011-12-20
It was a fresh clean install (from Windows Vista).
Not sure how can I access the Terminal. Is there some type of "Safe Mode" maybe?

---

### Post by stinkeye on 2011-12-20
> **davidafranklin said:**
> Hello,
I think I messed up something. I was trying to configure Compiz and I unchecked the Unity plugin. Then suddenly, I lost my Unity bar, all the icons.. I decided to reboot to see if that was normal. Now after the login, I only have my desktop and a menu bar on the top right (Files, Edit, View, Bookmarks and Help). I do not have access to any programs, I do not not even see any of the usual icons on the top right (Wireless, battery...). I was able to access the Apps via the help file and **uninstalled compiz** top see if that solved the issue. Then another reboot and same thing. So I have now just an empty screen (my desktop background) and a few useless icons on the top left. Not sure what to do from now...
Is this a wubi install ...ie in Windows?
When you say you "**uninstalled compiz**", do you mean compizconfig-settings-manager or the program compiz?
Compiz is the window manager for the default "Ubuntu" session and unity is a
plugin for compiz.
Uninstall compiz and you uninstall unity.

---

### Post by davidafranklin on 2011-12-20
via the Help menyu, I was able to access the Software Center. I typed ccsm to try to access Compiz. I reached the actual software and there was a button with "Remove", this is what I did, I removed it and reboot hoping I would get back to some standard menu where I would get everything back.

---

### Post by stinkeye on 2011-12-20
Removing ccsm does nothing really. It is just a settings manager.
The settings will remain as they were before uninstalling.

To set unity to default, log in to your "Ubuntu 2d" session and from there, 
in the terminal run
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]
```
Log out and back in to the "Ubuntu" session.

---

### Post by davidafranklin on 2011-12-20
I will try tonight as I am not in from of my machine now.
I hope I will be able to get to the terminal as none of the shortcuts seem to work so not sure if Ctrl + T will.
Just in case, is there another way to get to the terminal?

---

### Post by davidafranklin on 2011-12-20
I forgot to mention (in case this could be related), I downloaded some software security updates this AM that were available.

---

### Post by stinkeye on 2011-12-20
> **davidafranklin said:**
> I will try tonight as I am not in from of my machine now.
I hope I will be able to get to the terminal as none of the shortcuts seem to work so not sure if Ctrl + T will.
Just in case, is there another way to get to the terminal?
ctrl+alt+t.....terminal

---

### Post by davidafranklin on 2011-12-20
Will try tonight. Thanks

Another thing, as I cannot reach firefox from my Ubuntu laptop, I will not be able to access this forum and copy/paste so I believe I will have to type the hard way the entire line of code into the terminal right? So loooooonnnnnnng!

gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]

---

### Post by stinkeye on 2011-12-20
That's why I suggest to log in to the "unity 2d" session.
Unity 2d is a different program from the Unity 3d compiz plugin.
The "unity 2d" session runs metacity as the window manager and should boot no problem.

See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1896565&page=2") for another thread I gave help on
with a similar problem.

---

### Post by davidafranklin on 2011-12-20
ok I see. I do not get the option when I boot but I do get the option when I log out/log In, that is what I will do. Thanks

---

### Post by stinkeye on 2011-12-20
> **davidafranklin said:**
> ok I see. I do not get the option when I boot but I do get the option when I log out/log In, that is what I will do. Thanks

Yeah, if you have auto-login enabled you wont see the login on reboots, only logouts.

---

### Post by wildmanne39 on 2011-12-20
Hi, the section you used for setting up compiz was for 11.04 you need to go a little further down the page and 11.10 is there, also there are links for resetting compiz and unity.

Please slow down and read carefully it will save you a lot of time and frustration.

Thanks

---

### Post by davidafranklin on 2011-12-20
Here is where I am, I have logged out and logged in again with Ubuntu 2D, Gnome and Gnome Classic. Whatever I choose, I get the same result: black desktop, no unity bar, no dash.. Below is actually a photo I took from my phone of what I see





So that without being successful, I tried to log in as a "guest" and this time I am able to get all the normal icons, toolbars and settings (writing this email right now). I did reinstall compiz thru the Software Center. I will now reboot and see what happens.

---

### Post by davidafranklin on 2011-12-20
So after I looged out, I logged in with my regular username and all problems remain. So I can only get to "normal" thru the Guest session. Is there anything I should do, maybe something like deleting my profile and create a new one? If yes, is there a risk of losing files?
Thanks

---

### Post by wildmanne39 on 2011-12-20
Hi, did you follow the directions in the links for 11.10 in the guide?
Thanks

---

### Post by davidafranklin on 2011-12-20
would that work if I do all the settings under the "guest" account?

---

### Post by davidafranklin on 2011-12-20
i just did:

3. Type "Cube" into the filter, now put a check mark  by "Desktop Cube". You will need to click on "Disable Desktop Wall" in  the window that opens. 
4.  Now a window opens that says "Desktop Wall provides the feature Large  Desktop which is required by the plugins Ubuntu Unity Plugin". 

No I lost everything (Unity bar, toolbar on top..). I think this is what created the problem. How do I get everything back?

The Compiz windows closed and I cannot access it anymore.

---

### Post by wildmanne39 on 2011-12-20
Hi, I no it would not.

You can log out and into the 2d as mentioned earlier or the directions at the link for resetting unity tells you how to do it when you can not access the terminal.
Thanks

---

### Post by wildmanne39 on 2011-12-20
Hi, in the process of setting up the cube it will mess up your desktop at this point but compiz should not close you should be able to continue to the next step.

Can you open a terminal by hitting ctrl+alt+t? if so type compiz into it to open it again.
Thanks

---

### Post by davidafranklin on 2011-12-21
So under Guest Ubuntu 2D, I was able to do all the settings. After logging out and in back with my username, everything is exactly the same as before, nothing has changed. Again, under my regular account user  account, I do not have access to any terminal, etc.
Any other suggestion? Is a reinstall may be needed which would be crazy for such a configuration issue.
Thanks

---

### Post by davidafranklin on 2011-12-21
would one of these steps work?

[http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values](http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values)

[http://askubuntu.com/questions/72366/how-can-i-restore-the-unity-launcher](http://askubuntu.com/questions/72366/how-can-i-restore-the-unity-launcher)

Or your reset [http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by wildmanne39 on 2011-12-21
Hi, I thought that is what you have been trying, the last link is the one in my guide for resetting compiz and unity if you read the guide carefully it referred you to it.
Thanks

---

### Post by wildmanne39 on 2011-12-21
Hi, have you made any progress if you need help post back and we will go over it step by step and see if we can get it fixed.
Thanks

---

### Post by davidafranklin on 2011-12-21
I am trying right now to run this in the terminal:


gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config

I get this answer: rm: cannot remove `/tmp/guest-jVtIMq/.config/compiz-1/compizconfig/config': No such file or directory

---

### Post by davidafranklin on 2011-12-21
Now I am trying the UNity Reset lines and then reboot

---

### Post by davidafranklin on 2011-12-21
first answer in the terminal is:

guest-jVtIMq@david-Satellite-M115:~$ unity --reset
WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values

(metacity:6304): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:6304): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:6304): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:6304): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Processing upgrade com.canonical.unity.unity.01.upgrade
profile: unity
number: 1
domain: com.canonical.unity
Initializing put options...done
Initializing text options...done
Initializing staticswitcher options...done
Initializing unitymtgrabhandles options...done
Initializing snap options...done
Initializing scaleaddon options...done
Initializing place options...done
Initializing opacify options...done
Initializing expo options...done
Initializing resize options...done
Initializing colorfilter options...done
Initializing decor options...done
Initializing copytex options...done
Initializing resizeinfo options...done
Initializing wobbly options...done
Initializing workarounds options...done
Initializing thumbnail options...done
Initializing regex options...done
Initializing cube options...done
Initializing kdecompat options...done
Initializing imgpng options...done
Initializing debugspew options...done
Initializing blur options...done
Initializing gtkloader options...done
Initializing ring options...done
Initializing switcher options...done
Initializing ezoom options...done
Initializing shift options...done
Initializing grid options...done
Initializing dbus options...done
Initializing opengl options...done
Initializing unityshell options...done
Initializing screenshot options...done
Initializing vpswitch options...done
Initializing imgsvg options...done
Initializing inotify options...done
Initializing detection options...done
Initializing winrules options...done
Initializing zoom options...done
Initializing annotate options...done
Initializing wall options...done
Initializing gnomecompat options...done
Initializing imgjpeg options...done
Initializing mag options...done
Initializing mousepoll options...done
Initializing water options...done
Initializing commands options...done
Initializing animation options...done
Initializing scale options...done
Initializing move options...done
Initializing bailer options...done
Initializing obs options...done
Initializing clone options...done
Initializing compiztoolbox options...done
Initializing session options...done
Initializing fade options...done
Initializing composite options...done
Initializing rotate options...done
Initializing neg options...done
Initializing core options...done
Completed upgrade com.canonical.unity.unity.01.upgrade
Processing upgrade com.canonical.unity.unity.02.upgrade
profile: unity
number: 2
domain: com.canonical.unity
Completed upgrade com.canonical.unity.unity.02.upgrade
compiz (expo) - Warn: failed to bind image to texture

Screen geometry changed:
   0x0x1280x800

Starting unity-window-decorator

(unity-window-decorator:6390): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:6390): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:6390): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(unity-window-decorator:6390): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
DEBUG 2011-12-21 18:30:59 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1280 h=800
Setting Update "autoraise"
Setting Update "autoraise_delay"
Setting Update "maximize_window_key"
Setting Update "minimize_window_key"
Setting Update "show_desktop_key"
Setting Update "toggle_window_maximized_key"
Setting Update "toggle_window_shaded_key"
Setting Update "fullscreen_visual_bell"
Setting Update "run_command_terminal_key"
WARN  2011-12-21 18:31:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-12-21 18:31:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-12-21 18:31:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-12-21 18:31:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-12-21 18:31:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-12-21 18:31:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-12-21 18:31:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-12-21 18:31:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-12-21 18:31:56 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-12-21 18:31:56 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory

---

### Post by davidafranklin on 2011-12-21
then it crashed. Reboot and still same problems so back to guest account. I entered the following  lines in th terminal:

guest-aVom0v@david-Satellite-M115:~$ 
guest-aVom0v@david-Satellite-M115:~$ sudo service lightdm restart
sudo: unable to change to sudoers gid: Operation not permitted
guest-aVom0v@david-Satellite-M115:~$ sudo service gdm restart
sudo: unable to change to sudoers gid: Operation not permitted
guest-aVom0v@david-Satellite-M115:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM x86/MMX/SSE2
OpenGL version string:  1.4 Mesa 7.11

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
guest-aVom0v@david-Satellite-M115:~$ lshw -c video
WARNING: you should run this program as super-user.
^CI (sysfs)  
guest-aVom0v@david-Satellite-M115:~$ 


Now, stuck again!

---

### Post by wildmanne39 on 2011-12-21
Hi, for the unity reset you will keep getting errors, just let it run for about three minutes then reboot.

If it does not fix it follow the directions on this page and make sure that compiz and unity are both still installed and reinstall ubuntu desktop with this command.
```
sudo apt-get install ubuntu-desktop 
```
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
Thanks

---

### Post by stinkeye on 2011-12-21
You have to be logged in as your normal user.
Either in 2d or 3d unity.
Guest account is limited.
> Temporary session with restricted privileges
Once in a while a friend, family member, or colleague may want to borrow your computer. The Ubuntu Guest Session feature provides a convenient way, with a high level of security, to lend your computer to someone else. The feature is available to any regular user when logged in.
To launch a guest session, click your name in the menu bar and select Guest Session. This will lock the screen for your own session and start the guest session. A guest cannot view the home folders of other users, and by default any saved data or changed settings will be removed/reset at logout. It means that each session starts with a fresh environment, unaffected by what previous guests did.

---

### Post by davidafranklin on 2011-12-21
i am able to access the terminal from my account with CTRL ALT T, but i cannot paste the codes that I can access from my guest account. i am going to type manually the unistall as it is a short one

---

### Post by stinkeye on 2011-12-21
> **davidafranklin said:**
> i am able to access the terminal from my account with CTRL ALT T, but i cannot paste the codes that I can access from my guest account. i am going to type manually the unistall as it is a short one

The 2d session is working isn't it.
You can do it from there.

---

### Post by davidafranklin on 2011-12-21
It is still running but I already have my toolbars back from my regular user account so seems to be working.
I will wait another 2 mn, stop the script and do the gdm restart, reboot and cross my fingers. Will keep you posted

---

### Post by wildmanne39 on 2011-12-21
Hi, yes please let us know and tell us what exactly worked for you.
Thanks

---

### Post by davidafranklin on 2011-12-21
so after the Unity reset from my account, I waited about 5mn and I stopped the script CTRL + C and it  froze. I reboot under Unity 3D and everything is back to normal. I have not typed "sudo service gdm restart" and I think I do not need it.

For newbies like me, I think the key solution was to acces the Terminal from my user. CTRL + T did not work (my mistake), only CTLR + ALT + T (of course the right way!).

As you have to type manually the code, luclily it is very short (unity --reset).

Now I will try to follow again step by step the configuration.

Thanks again everyone for your help!

---

### Post by wildmanne39 on 2011-12-21
Hi, that is great to hear, I am wondering if you have a problem with your compiz it should not close when you said it did, but if you are going to try again make sure you use the section of the guide for 11.10.
Thanks

---

### Post by davidafranklin on 2011-12-21
I just tried to reconfigure. As soon as you select the "desktop Cube" and disable the plugings (4. Now a window opens that says "Desktop Wall provides the feature Large  Desktop which is required by the plugins Ubuntu Unity Plugin". Now  disable the "Ubuntu Unity Plugin". ), this is when all starts to mess up.

I lost everything. I quickly typed again the Unity reset code and everything came back but maybe there is something not right with that step in the tutorial.

Also not sure if thismatter but I do not have an option anywhere fro ""3D Windows". I do have the rotate, cube and gears though

---

### Post by wildmanne39 on 2011-12-21
Hi, as I said before it does mess up the desktop at that stage because the unity plugin is disabled but if you continue on and follow the directions everything should work fine.

Type 3d into the search filter and it should find it if not then something is wrong with your compiz.
Thanks

---

### Post by davidafranklin on 2011-12-21
I cannot follow the process as I soon as I disable the Unity plugin, compiz disappears and I cannot access it again unless there is maybe a way to access from the terminal.

Typing 3d shows "no matches found". I am not going to worry about this as Unity 3D does not seem top be a big thing anyway.

---

### Post by wildmanne39 on 2011-12-21
Hi, yes it sounds like not all of compiz is installed or it has a bug in it, I am using the cube with all the effects listed in the guide and more so I know it works but the problem is that there are so many configurations that while it works for most people it will not work for all and I am sorry about that.
Thanks

---

### Post by davidafranklin on 2011-12-21
This is a great guide. I guess If I am able to get the 3D windows in Compiz in the future, most likely it is because things will be ok. Until then, I am not going to mess up with it anymore!

Good job!

---

