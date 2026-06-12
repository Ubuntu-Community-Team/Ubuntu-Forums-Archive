---
title: "How To : Compiz Fusion for ATI cards + Xgl in Feisty"
date: 2007-06-30
forum: Desktop Effects &amp; Customization
---

### Post by Mr Greencastle on 2007-06-30
*Edit: Forgot to mark this as a HOWTO, and I don't know how to change it, so...*
[I]Edit 2: Hey guys, long time no talk, I've been quite busy with my personal life, school etc, so I haven't been here in awhile.

Anyways, I'm in the midst of updating this guide, so I should have a new one that has instructions for Gutsy aswell (Using same hardware).

Mr Green.[/I]


I'm making this guide because I have seen many people lately with problems installing Beryl or Compiz Fusion with Xgl. I have taken some parts of other guides and have also contributed my own parts, just to make things easier. (Many thanks to lamalex, as I have used that guide countless times to get Feisty boxes running Beryl)

If you follow each step carefully (mostly copy/paste), I guarantee you'll be going with desktop effects in no time!

**Guide:**

After installing Feisty, make sure your system is completely updated. Paste this into a terminal:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

First step is getting your drivers set up. To do this use the Restricted Driver Manager.

```
System >> Administration >> Restricted Drivers Manager
```

Enable your ATI driver (By clicking the little box) and let it do its thing. Once finished , reboot the computer and make sure fglrx loaded correctly. There should be an icon (small and green) in the notification area telling you that you have restricted modules loaded.

Now we need to install XGL.

```
sudo apt-get install xserver-xgl
```

Good now, XGL won't load on its own so we need to write a few scripts to have it start.

```
sudo gedit /usr/local/bin/startxgl.sh
```

Now copy and paste this into the file that pops up:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

**SAVE THIS FILE!** Once its done saving, make that fire executable (like a program) by pasting this into a terminal:

```
sudo chmod a+x /usr/local/bin/startxgl.sh
```

Now we need to make a way to start that session from your login menu, paste this into a terminal:

```
sudo gedit /usr/share/xsessions/xgl.desktop
```

And paste this into the file:

```

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

Now make this script executable by pasting this into a terminal:

```
sudo chmod a+x /usr/share/xsessions/xgl.desktop
```

Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close.

The first thing we need to do is add the security key, do this by pasting into a terminal:

```

sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

Then type in:

```
sudo gedit /etc/apt/sources.list
```

This will open a file, add this to the very bottom by pasting:
```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Then save and exit.

You will need to update again, so paste into a terminal:

```
sudo apt-get update
```

[SIZE="4"]BERYL[/SIZE]
If you want Compiz Fusion - skip ahead to the Compiz Fusion section.

Now to install Beryl (and Emerald window decorator)  paste this into a terminal:

```
sudo apt-get install beryl beryl-manager beryl-core beryl-plugins beryl-settings emerald emerald-themes
```

AND VOILA! Beryl is installed, to start it simply paste this into a terminal:

```
beryl-manager
```

You may need to change the window manager, do this by right-clicking the beryl icon and selecting Beryl from the 'Select Window Manager' menu.

Then you're all set! Oh and don't forget to add this to your startup:

```
system > preferences > sessions
```

Click on 'New' and type in 'Beryl' (without quotes) for the name, and for the command type: 'beryl-manager' (again without quotes)


[SIZE="4"]COMPIZ FUSION[/SIZE]
Start by pasting this into a terminal:

```
sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes
```

AND VOILA! It is installed, add this as two separate entries in the startup sessions:
```

System >> Preferences >> Sessions
```

Click 'new' and make its name: Compiz
And make its command: compiz --replace

And make one more:
Name: Emerald
Command: emerald --replace

Now just logout, then log back in, and BOOM! Shiny desktop effects!


Hope that helped!


Mr Green

---

### Post by LouisvilleLIP on 2007-07-01
You rule.  My compiz fusion broke, and I couldn't get it fixed.  I removed the cf/emerald packages, followed this, and it's back.  Thanks for posting.

---

### Post by jw5801 on 2007-07-04
Great how-to! Needed XGL to get Avant Window Manager working and this did it.

---

### Post by jamesey on 2007-07-04
wow! this really made my desktop smooth. I was skeptical because before enabling the restricted drivers that I didn't know about the whole ubuntu experiece was a little clunky. suddenly it's way smooth and I have wobbly windows, a cube,  and a dock (AWM.)

---

### Post by jimminy_kriket on 2007-07-04
Does anyone know how to do this in xubuntu? A guide would be much appreciated.

---

### Post by cor2y on 2007-07-04
It works somewhat on my system although i thought it wasn't working because it took compiz fusion a while to load.
Also Emerald Themes do not work for me i can't switch to a new theme.
I don't know why.

---

### Post by bodhi.zazen on 2007-07-05
> **Mr Greencastle said:**
> *Edit: Forgot to mark this as a HOWTO, and I don't know how to change it, so...*

Title changed. Feel free to PM a mod if you need help. Feel free to PM me if you want the title further adjusted.

---

### Post by adityavpratap on 2007-07-05
Hi Mr. Greencastle!
I have followed your instructions and have succeeded in installing Compiz Fusion on my laptop, which is same as yours, except for the RAM which is 512 MB.
Most of the effects are working except the cube. When I pres Ctrl + Alt + Button 1 nothing happens. Any idea what may be the reason for this. Could it be the RAM?

---

### Post by cor2y on 2007-07-06
to get the rotating cube you need to enable that plugin as well as the 3d desktop cube one.

---

### Post by adityavpratap on 2007-07-07
Pardon my ignorance, but I have enabled the rotate cube plugin in the CompizConfig Settings Manager, did the same with the 3d cube one as well, still I am not getting the effect.

---

### Post by firmwire on 2007-07-07
Well earlier this afternoon I did a complete reinstall just to see if I could get Compiz fusion to work. AND I DID!!!
I used this and also 
[http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz&page=24](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz&page=24) 
and also
 [http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion+ati](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion+ati)
 as references. Everything was working like a dream. The cube...everything!!! Then I stupidly clicked on update when the screen popped up. That broke compiz and my XGL desktop.
I tried a few things and nothing work. Since I had time, I decided to just do another clean install and NOT do the updates if the screen popped up again. Well. It seems the repositories have been updated, so no matter what I do, I get a non working compiz fusion.

Is there any way to load on the repository from Before July 7th?  I noticed that some of the plugins make a reference to the 6th and not the 7th if I run compiz --replace from a xterm.
 Any suggestions? I know this is all working betas and use at your own risk... but I got it working this afternoon and then it stopped when some update was loaded this evening.

---

### Post by adityavpratap on 2007-07-07
I finally got it. Thanks to cwood6 on these forums.
He was having NVIDIA card and he suggested selecting GConf Configuration Backend in the Backend and Profiles section of CompizConfig Settings Manager.
But I found that it was already selected. So I switched to Flat File Configuration Manager and the rotating cube started working. :)

---

### Post by firmwire on 2007-07-07
adityavpratap,

So you have everything working? You didn't loose any window borders and have your windows stuck in the upper left corner of your desktop?

I have to wait until I get back home, but If I try tonight and can't get it to work, I think I will try out just plain beryl or something.

---

### Post by adityavpratap on 2007-07-07
Actually, lost window borders issue was sorted out by the following command -
$ compiz --replace -c emerald
If it still doesn't work, try to run compiz with indirect rendering

---

### Post by firmwire on 2007-07-07
adityavpratap,
Ahhh.
I will definitely try that when I get home tonight. I wish I could be working on it now!!!

So it seems that even with the update I can get things to work. Wish me luck.
I'll post my progress.

---

### Post by firmwire on 2007-07-07
BTW,

What is the best way to have compiz run indirect rendering?

And do you think that will fix the no cube problem too?

---

### Post by firmwire on 2007-07-07
Since an update last night, I lost my borders on my windows and I have no cube, and whenever I open any window, it is stuck in the upper left corner and I can't move it and I can't see any of the menu options for the window. I tried another fresh install and it didn't solve my issue. That new update didn't work well with my system, even though earlier in the day ( off a fresh install) I have everything working.

adityavpratap wrote:
> **adityavpratap said:**
> Actually, lost window borders issue was sorted out by the following command -
$ compiz --replace -c emerald
If it still doesn't work, try to run compiz with indirect rendering

Do you think this will fix my issue, once I reload again on a fresh install tonight? And what is the best way to go about running compiz with indirect rendering?

---

### Post by Primoz on 2007-07-07
Hi!

I followed these instructions, but after logging-in I could not get a clear picture
(desktop and icons are very unclear) i.e. it does not work on my computer. 
I have HP 9420 with X1600.

Do you have any suggestions? I would really be glad, because I've been trying
to enable some kind of desktop effects for quite a while.

Thanks, Primoz

---

### Post by Primoz on 2007-07-07
I am really sorry. This message was meant for another topic.

---

### Post by Primoz on 2007-07-07
Can somebody please explain how can I erase wrong posts.

---

### Post by digital_exhaust on 2007-07-07
Thank you for the guide, thank you.... Now, can someone please help me out with a dual screen setup? I need my 2880x900 love back....

---

### Post by firmwire on 2007-07-07
> **adityavpratap said:**
> Actually, lost window borders issue was sorted out by the following command -
$ compiz --replace -c emerald
If it still doesn't work, try to run compiz with indirect rendering

Tried both. No joy.

Having it not work is not frustrating me. Having it work yesterday and then not a couple of hours later, and then not getting it to work even on a fresh install....that is what is frustrating

---

### Post by Mavrik on 2007-07-08
I've succesfully installed Compiz Fusion with XGl on my Mobility Radeon X1600 and it works perfectly. However, I do have another problem: all QT windows now are really ugly. Meaning, SMPlayer and such don't receive the GTK theme, like other applications do. This problem only occurs when running XGl... is there any fix for that?

---

### Post by BL00dFox on 2007-07-08
OMG I love you! This guide worked perfectly!

Thanks

---

### Post by adityavpratap on 2007-07-08
> **firmwire said:**
> Since an update last night, I lost my borders on my windows and I have no cube, and whenever I open any window, it is stuck in the upper left corner and I can't move it and I can't see any of the menu options for the window. I tried another fresh install and it didn't solve my issue. That new update didn't work well with my system, even though earlier in the day ( off a fresh install) I have everything working.

adityavpratap wrote:


Do you think this will fix my issue, once I reload again on a fresh install tonight? And what is the best way to go about running compiz with indirect rendering? 

Ok. After a fresh install you might try 
$ compiz --indirect-rendering --replace -c emerald
I have read in one of the posts that the window problem can be set right by the indirect rendering command. Hope it works in your case.
By the way have you removed beryl from your system?

---

### Post by firmwire on 2007-07-08
Yes I had removed beryl and I tried indirect rendering also. No joy.

I ran across this, this morning. Several people have had my issue after the lastest update.

> **blackdevil said:**
> Talked to Trevinho, and the problem is that the deb isnt updated in  the script. He is apparently working on it now and the fix should be out soon hopefully.

---

### Post by firmwire on 2007-07-09
Yep! All is working now! 
Great job on getting the word out so the fix could be made!

---

### Post by adityavpratap on 2007-07-09
Congrats!!

---

### Post by naxmul on 2007-07-09
well, i have a ATI 200M, and the first time I installed it, it didn't work out correctly because it got the compiz package from the ubuntu archive, not the tuxfamily repo, and the compiz didn't work.

Second time around, I disabled the universal repo, and it worked. Mabye it was luck, or something, but hey, it works for me now. Anyone with the same problem shud try disabling the universal repo.

---

### Post by JesterDev on 2007-07-10
Just wanted to say thank you! Works perfectly, and only took a few minutes.

ATI Radeon X1300Pro

---

### Post by adwatkin19 on 2007-07-10
Hiya, this worked like a dream, i now have the uber coolness of the cube to help me switch between my desktops and my tasks, thank you so much. 

Just a quick question, how can i look at and alter the settings for this: e.g. i have heard you can put a picture on the background of the cube for when it is rotating.

thanks for any help and MASSIVE thanks for the HOW TO

Adwatkin19

---

### Post by polygone on 2007-07-12
I have recently corrected mys system to run in 1024x768 mode, using this (ATI|Rage Mobility M3 AGP 2x desktop effects) card.   When I was using 800 x 600, previously, it just kept saying it couldn't enable the effects.  Now, it attempts to, but turns the screen all white.  Will this tutorial fix that? or is my card just not able to handle it?

---

### Post by primetime on 2007-07-17
Eye Candy!

Finally I got some eye candy.  :D

Thanks alot for this guide.  Really helps out newbies like me.

Compiz Fusion running on ATI Mobility X600.

---

### Post by Creeture on 2007-07-17
> **cor2y said:**
> It works somewhat on my system although i thought it wasn't working because it took compiz fusion a while to load.
Also Emerald Themes do not work for me i can't switch to a new theme.
I don't know why.

As far as emerald themes goes, that's a pretty long-standing bug in (IIRC) GTK. I don't know why it is still broken. To fix, just bring up the Emerald Themer and a terminal window at the same time. Choose your theme in the Themer then type "emerald --replace &" in your terminal. Wash, rinse, repeat until you get the one you want.

---

### Post by Deco_21 on 2007-07-17
Try enable "Cube reflection" that will change the things ....

---

### Post by jcrow on 2007-07-17
Is anyone having issues with the skydome and other settings that don't work. I'm running the 64 bit compiz fusion using a similar method to what was posted here. I revised the session script to what was posted here with no change. I am using a flat file backend, and I added the path to the file - it has the correct ratio and it worked in desktop effects- but I can not get the skydome to display. I filed  a bug on the opencomposition website.

---

### Post by Chonnawonga on 2007-07-18
I get as far as logging out, choosing the GNOME with XGL session, and logging back in, and my screen goes nuts. Little lines all over the place. Any idea what might be wrong?

I'm running a Samsung Syncmaster 931BW at 1440x900 on an ATI Radeon 9600.

---

### Post by fjoesne on 2007-07-19
Can anyone who successfully did this with an ati x1600/x1700 show me their xorg.conf? i keep getting a blurry X and/or no direct rendering etc. I have spent 12-15 hours following different guides without success :/

I have x1700 on an ASUS f3jp.  ATI is getting on my nerves. they released their drivers the 25th of June thats good for xorg 7.1, its not like they are ahead :/ would be nice if they spent like 10 calories looking at  the beta versions :(

When I try to run xorg 7.2 with glx etc compiz complains about missing  texture_from_pixmap support. 
as far as i know the ati drivers are not made for xorg 7.2 and that requires me to go for XGL for now. 
When i enable XGL like this howto, the x is just a bunch of lines and colors that change when i move the pointer around. 
I have experimented with a few options in xorg.conf:
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "EnablePageFlip" "true"
        Option "RenderAccel" "true"
        # Option "SubPixelOrder" "NONE"
        Option "ColorTiling" "false"
        Option "DRI" "true"
EndSection
```

would really appreciate some help :)

---

### Post by Jonq on 2007-07-19
> **Chonnawonga said:**
> I get as far as logging out, choosing the GNOME with XGL session, and logging back in, and my screen goes nuts. Little lines all over the place. Any idea what might be wrong?

I'm running a Samsung Syncmaster 931BW at 1440x900 on an ATI Radeon 9600.

same here :(

---

### Post by fjoesne on 2007-07-19
Got XGL working without the mess.. i have no idea what i did. however compiz is still missing 
something.. here is the dump:
```

$ compiz --force-fglrx --replace -v
Checking for Unsupported sessions: not present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Checking for FBConfig: present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
Checking for copy texture support: Not present. 
Checking for Intel: not present. 
Checking for non power of two support: Not present. 
Checking for Composite extension: present. 
Checking for XDamage extension: present. 
Checking for XSync extension: present. 
Detected 1 screen(s)
[COLOR="Green"]Checks indicate compiz should work on your system[/COLOR]
Found GNOME desktop environment running...
Found running windows manager: metacity
Setting fallback windows manager to metacity 
Loading the ccp settings interface
Exporting:  WINDOW_MANAGER=/usr/bin/compiz 
Executing: /usr/bin/compiz.real --ignore-desktop-hints --force-fglrx --replace --sm-disable ccp 
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
[COLOR="Red"]/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display localhost:1.0[/COLOR]
Executing: metacity 

```

The 3d is working just fine with all of the builtin screensavers, as apposed to xorg. 
but i have no idea what to do with this? anyone got any idea?

---

### Post by Mr Greencastle on 2007-07-19
Are you sure you're using png as the image file?

 I think the skydome only works for with that type of format, since I was having the same problem until I changed the image to a png format.

---

### Post by Auax on 2007-07-19
Erm... where do I find restricted driver management in Kubuntu?

---

### Post by naxmul on 2007-07-19
> **Auax said:**
> Erm... where do I find restricted driver management in Kubuntu?

try doing ```
sudo restricted-manager
``` in konsole.

---

### Post by Auax on 2007-07-19
> **naxmul said:**
> try doing ```
sudo restricted-manager
``` in konsole.

THANKS!

---

### Post by Mr Greencastle on 2007-07-19
I honestly couldn't tell you anything about KDE, as I am a n00b in it. (Though I'm not very advanced anyway...)

But once KDE4 comes along, I might switch.

---

### Post by naxmul on 2007-07-19
> **Mr Greencastle said:**
> I honestly couldn't tell you anything about KDE, as I am a n00b in it. (Though I'm not very advanced anyway...)

But once KDE4 comes along, I might switch.

yeh, kde4 is gonna be awesome.

---

### Post by Auax on 2007-07-19
I've followed the instructions up to loging into the "GNOME with XGL" session... and now I get what's in this screenshot.

Also, is there a way to have compiz on KDE? I'm not a fan of Gnome.

---

### Post by jw5801 on 2007-07-20
Take a look at this [thread](http://ubuntuforums.org/showthread.php?t=481314) for KDE instructions, the instructions are the same (but with a bit more detail) once you have xgl installed. I had to find that one as I'm running 64-bit and was getting "can't find package" errors from the repos listed in this thread.

---

### Post by Auax on 2007-07-20
> **jw5801 said:**
> Take a look at this [thread](http://ubuntuforums.org/showthread.php?t=481314) for KDE instructions, the instructions are the same (but with a bit more detail) once you have xgl installed. I had to find that one as I'm running 64-bit and was getting "can't find package" errors from the repos listed in this thread.

Haha, I was sent to this thread from that one. ;T_T

---

### Post by ManOnOneWheel on 2007-07-20
> **Chonnawonga said:**
> I get as far as logging out, choosing the GNOME with XGL session, and logging back in, and my screen goes nuts. Little lines all over the place. Any idea what might be wrong?

I'm running a Samsung Syncmaster 931BW at 1440x900 on an ATI Radeon 9600.

I had this problem too make sure your xorg.conf file has this
         
Section "Extensions"
	Option		"Composite"	"0"
EndSection

because for some strange reason mine had "Composite" "Enabled" AND "Composite" "0".   I do not know if that was a result of following this guide or another, but once I removed the "Composite" "Enabled" everything worked great! Hope it fixes it for you too.

---

### Post by deezy on 2007-07-21
Thanks for the great tutorial!!! I followed this step by step from a base Ubuntu Fiesty Fawn cd and now I have Compiz Fusion working beautifully on my thinkpad T60p!!

Thanks again!!!

---

### Post by melenor on 2007-07-21
yah i followed it and when i clicked on the desktop effects it says
      "The Composite extension is not available"
how do i fix it i followed the guide exactly

i just noticed this when i luanched beryl from terminal

(gtk-window-decorator:6534): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:6534): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

no idea if this will help or not.
btw when ever i try to change the window mangaer off of compiz to beryl my screen blinks then goes, then when  i check the window manager it says meticity

---

### Post by sheds on 2007-07-31
Hello there, followed this guide and several others to get compiz running. I get the following message: 'Fatal: Failed test: non-power-of-two texture support'. The only thing that i could tell you about this is that in the step where you enable restricted drivers, i get a message that says that my hardware does not require any restricted drivers.

I've been looking with google for an answer to this but apparently not many people have run into these crossroads. It would be greatly appreciated if someone sheds some light on this problem.

---

### Post by Mr Greencastle on 2007-07-31
Are you sure you need Xgl to run Beryl or Compiz Fusion? Some ATI cards don't require it, but as I am not sure which, anyone care to elaborate?

Alos, try following this guide but skipping the installing Xgl part, and go right into installing Compiz Fusion or Beryl.

Hope that helps!

Mr Green

---

### Post by TVMA on 2007-07-31
This how to worked fantastically... Thank you

I"m running an ATI XL800 and this works great.
I used to run beryl but had to disable the updates and all that otherwise it would break, and now with it running fusion it is just simply sexy...

Thanks for taking the time on this how to.. works beautifully for me.

---

### Post by jms1277 on 2007-08-01
when i try to acess the System >> Administration >> Restricted Drivers Manager all i get is command not found if someone know how to fix it i would be most gratefull thanks

---

### Post by Doovoo on 2007-08-01
I followed this guide and it seemed to work well, but I'm getting some problems with it freezing.  I've posted about my problem [here]("http://ubuntuforums.org/showthread.php?t=515027"), but I think it's more apt that I post it here, so I'll just quote it.

> 
I'm experiencing full system freezes with compiz fusion as well. In the past, I have run Compiz and Beryl SVN with no problem whatsoever. I mean, I ran the newest plugins, enabled all settings, and it ran really smoothly with little to no performance hit. I ran these with both fglrx and ati opensource drivers, and never experienced freezes.

Just the other day, I installed Compiz Fusion (with XGL this time) and it will login, let me tinker, and all effects will work, but it will just randomly freeze when one of the effects is being employed (say I right click and get a wobbly dropdown, or try rotating the cube).

I know for a fact that it's not my system overheating, I've had my system overheat a few times before, and it does system beeps, then shuts itself down.

I'm almost positive it's not hardware related, as my hardware had no problem running the latest compiz and beryl in the past, and compiz fusion is actually supposed to use less resources. Also, even if I turn the Compiz Fusion settings down to the bare minimum, I will still get freezes.

This leads me to believe it's either a problem with Compiz Fusion itself, with the fglrx driver, or a rendering setting that's set incorrectly.

My system specs are:

ATI Radeon 9700 Pro
AMD Athlon 64 3200
512MB Ram

Also, I too have tried uninstalling Compiz Fusion and XGL and reinstalling, but to no avail.

---

### Post by nandoc on 2007-08-02
THANKS, what an awesome work, I am new with Linux, I have been reviewing many pages about Beryl, and your HOWTO is the only one that make it work flawlessly. I am now enjoying Beryl on my Diamond Viper ATI X1650 and my Samsung LCD 32" with Ubuntu 7.04. Just a few little things I had to point out on your guide:
1) sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add  -  it didn't finish, I closed the Terminal window and executed it again and did fine after that.


Once again THANKS,
Fernando

---

### Post by kalleball on 2007-08-02
when i log into gnome with xgl, it's all a bunch of lines and i can't see anything, what do i do to make it work?

---

### Post by nandoc on 2007-08-02
> **kalleball said:**
> when i log into gnome with xgl, it's all a bunch of lines and i can't see anything, what do i do to make it work?
Just Reboot if youcan't remenber where to click, just turn it off and restart

---

### Post by NinjaTails on 2007-08-02
I followed this guide, and I still have trouble. I have a Compaq Presario, and here are the specs:

Intel Celeron D 3.2 Ghz processor
ATI Radeon 200 XPress 128MB graphics
120GB SATA 7200RPM Hard drive
40GB IDE 5400RPM Hard drive (x2) (one is a swap drive, the other is Windows XP)
512MB RAM
HP vs15 Monitor (1024x768)
DVD-RW drive

Aaand, that's all I can think of that would be even slightly important, but I've followed this guide and two other guides, and whenever I start Beryl, the screen turns white when the restricted driver is disabled, and when enabled, it just doesn't start at all. With Compiz Fusion, it gives me this error:

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

Any help?

---

### Post by kalleball on 2007-08-02
> **nandoc said:**
> Just Reboot if youcan't remenber where to click, just turn it off and restart

well, yeah...i can log out and log in using gnome without xgl but i want it working to get compiz fusion to work =/

i'm using a ati 9800XT card and i've tried all different kinds of tutorials to get compiz fusion to work but so far...nothing =(

---

### Post by macaholic on 2007-08-02
I am having the same problem mentioned by others, when i log in the screen is all garbled.
Any one know a fix for this?

---

### Post by superbungalow on 2007-08-03
I was quite happy a few mins ago, because I managed to successfully install Xgl for the first time. But then became unhappy because after installing compiz fusion and rebooting, i got an error message about GRDRL or something like that, and couldn't start ubuntu again. Luckily, I am using wubi, so it was only about 30 mins before I got it uninstalled and re-installed. But now I have made no progress!

---

### Post by tprzepiorka on 2007-08-03
I am running an ATI 9600 Radeon. I followed the instructions to get Compiz Fusion working. I can't get compiz fusion to even start. I have no window borders and the effects aren't working. I tried to run: compiz --indirect-rendering --replace -c emerald 
I get this output:

```
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070709 and actual version is 20070708
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'
/usr/bin/compiz: line 777: 15179 Segmentation fault      (core dumped) $* 2>> $ERROUTPUT

```

Please can someone help?

---

### Post by mabovo on 2007-08-03
I upgraded my feisty installation into gutsy and tried this method on my AMD Sempron 3000+ with ATI Radeon 9600 video card. 
Results: A complete system mess. No Desktop effects even replacing metacity by emerald.
I've got some desktop effects logging with enlightment session or installing Beryl but Compiz hasn't show up here. 

After a fresh installation of gutsy alpha 3 with restricted modules enabled and using by default "ati" driver, I tried to install proprietary ATI driver 8.39.4 with "fglrx" driver and again messed with gutsy.

It seems that XGL is not compatible working with these cards (in my case the ATI Radeon 9600 and ATI Radeon 8500 both I have ).

Now after upgrade to Kernel 2.6.22.9 it seems that everything was going well but suddenly back again on problems with xorg-xserver and gdm.

Looks like a kind of conflict on gdm or xkb ??? that disable the keyboard and displays only a black screen .

---

### Post by Sudokan on 2007-08-03
Greetings,

     I have a slightly different problem. If this problem is covered elsewhere, please be kind enough to point me in the right. direction; I have been searching the forums, but i haven't hit on a helpful thread yet. It is possible I don't understand enough to ask the right questions. :-) 
    At any rate, I have followed this procedure on my laptop, which utilizes an ATI 9600 Mobility Radeon, and it works perfectly...I have all the window effects and it looks outstanding...until I try running games, like TORCS, or The Ur-Quan Masters. The game starts, and appears in a window at the upper left corner of the screen with no window controls. The default Ubuntu games work fine, however.
    Is there anyplace I can find a solution to this problem?

---

### Post by jw5801 on 2007-08-03
> **mabovo said:**
> I upgraded my feisty installation into gutsy and tried this method on my AMD Sempron 3000+ with ATI Radeon 9600 video card. 
Results: A complete system mess. No Desktop effects even replacing metacity by emerald.
I've got some desktop effects logging with enlightment session or installing Beryl but Compiz hasn't show up here. 

After a fresh installation of gutsy alpha 3 with restricted modules enabled and using by default "ati" driver, I tried to install proprietary ATI driver 8.39.4 with "fglrx" driver and again messed with gutsy.

From [this](http://ubuntuforums.org/showthread.php?t=481314) thread, on which the HowTo is almost identical, neglecting the ATi + XGL parts:
> Compiz Fusion is a very exciting new advancement in Desktop Effects. Be that as it may, Compiz Fuzion is NOT for Beginners. It is in development now, and is not stable.

**If you are testing Gutsy, do not use this guide. Compiz Fusion is available in Gutsy.**

---

### Post by naughtykid on 2007-08-03
Thank you Mr. Green. Facing a lot of troubles previously, fixed everything right after reading your post.

Thanks!

---

### Post by silent1643 on 2007-08-03
"Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close."

okay i got to the desktop, but  i couldn't make anything out once i open an application- what  now lol

i have an ati 850x AGP plat

---

### Post by paulfife on 2007-08-04
This HOWTO worked great for me! Thanks for writing it up!

I have one question about configuring the session. The new session is missing the shutdown options the default one has. Does anybody know how to get these on there?

---

### Post by superbungalow on 2007-08-04
What's the difference between typing "compiz" in the terminal to start compiz, or typing "compiz -- replace"?

---

### Post by jw5801 on 2007-08-04
```
jw5801@jw5801-laptop:~$ compiz
Compiz is already running, you should use the --replace option to override it
jw5801@jw5801-laptop:~$ metacity
Window manager warning: Screen 0 on display ":1.0" already has a window manager; try using the --replace option to replace the current window manager.
```
One cannot run a window manager while another is already active, therefore the replace option is necessary to override whatever is already running.

---

### Post by superbungalow on 2007-08-04
cool. Umm, I ran compiz --replace, and all the window borders went away, then it flashed back and they were back. Now nothing has changed, what do I do?

---

### Post by tprzepiorka on 2007-08-04
Great tutorial! I got it working after a while and now it's great! 

The only problem that I have is with aMSN, when it boots on startup the main window doesn't have window borders and I can't right click on AWN to close it. Some conversation windows also have no borders and I can't move them or anything. This is the only problem that does this.

Thanks once again for the tutorial.

---

### Post by markdjones82 on 2007-08-04
Ok, I have everything loaded, but Beryl doesn't seem to actually be working.  The manager is loaded, but I am unable to see any effects.  Any help on what to check?

I get over and over in the terminal

beryl-manager Critical can't execute beryl-xgl: Success.

It loads the manager though.

---

### Post by silent1643 on 2007-08-04
oh well, i guess i should ditch my ati card :D

---

### Post by Mr Greencastle on 2007-08-04
I have had this problem with amsn for a while, though I just use pidgin now, as I feel it has a more consistent look with everything else. I can also go on IRC and two different msn accounts at once, I like that.

As for fixing that problem, I just took the option to start it out of the sessions manager. Then I would start it after boot, hopefully that is a useful solution for you?

Mr Green

---

### Post by Phimax100 on 2007-08-05
Ok, so I went through the instructions, but when I try to launch the gnome with xgl session, I get an error message saying that it was unable to launch /usr/local/bin/startxgl.sh. Please show me a fix or another thread that would help. I have an ati x1650, and an intel processor. Thanks.

---

### Post by tprzepiorka on 2007-08-05
> **Mr Greencastle said:**
> 
As for fixing that problem, I just took the option to start it out of the sessions manager. Then I would start it after boot, hopefully that is a useful solution for you?
Mr Green

I took it off of the session manager and even if I load it after Ubuntu has fully loaded the main menu for aMSN and certain groups don't have window borders and I can't move them etc.

Are there any other ways to fix this problem?

---

### Post by silent1643 on 2007-08-05
still no fix for the problem with f-uped graphics when going into xgl desktop  mode?

---

### Post by jpereira on 2007-08-05
You might want to take a look at **[thread=518426]this thread[/thread]** on how to easily run a separate X just for a specific application, this overcoming the inability to run some 3D games in Xgl.

---

### Post by DeclanMcErlane on 2007-08-06
Wow...Thank you so much. I've been searching three days straight how to setup Beryl on my computer since I got my new Radeon 9600XT! So far this has been the only guide to have worked. Thanks again.

Declan.

---

### Post by melojo on 2007-08-06
Hello All,

This is my first post and I wanted to thank Mr Greencastle for the post it help me get compiz up and running on my Ubuntu system.  I had to add the & sign after compiz --replace &  to get it to work it may have been mentioned in the other replies I am not sure I didn't go through and read all of them.  I have used several Linux distributions and so far I like how well Ubuntu works.  Thanks again for the thread!!!

---

### Post by danieldumitru on 2007-08-06
THX for the instruction Mr Greencastle.
Will see the results in a moment.
Hope will worke.
:)
BRGDS Daniel

---

### Post by dancantong on 2007-08-06
Hi! I'm having the same problem as many reported: when entering the Gnome + XGL session the screen becomes full of lines and distorted.
I have an ATI Radeon X1300 Pro.
This is my xorg.conf if it helps:

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "es"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL SE198WF"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "DELL SE198WF"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1440x1440"     "1280x1024"     "1152x864"     "1024x768"       "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1440x1440"     "1280x1024"     "1152x864"     "1024x768"       "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1440x1440"     "1280x1024"     "1152x864"     "1024x768"       "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1440x1440"     "1280x1024"     "1152x864"     "1024x768"       "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1440x1440"     "1280x1024"     "1152x864"     "1024x768"       "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1440x1440"     "1280x1024"     "1152x864"     "1024x768"       "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option          "Composite"     "0"
EndSection

Any help will be welcome.

---

### Post by dancantong on 2007-08-06
Sorry, I was doing something wrong. I had this line in /etc/default/linux-restricted-modules-common (I put it while following another tutorial).

DISABLED_MODULES="fglrx"

I replaced it for DISABLED_MODULES= and now it works!

Thanks a lot for the tutorial.

---

### Post by danieldumitru on 2007-08-06
:)
at last is working.
I had same problem with button bars but then the the update manager showed that i have some updates available and I've made them and now is working nice as far as I've tested

---

### Post by vaulter on 2007-08-06
hello, i am having problems with the installation... i have followed the tutorial but when i login under gnome and xgl my screen just turns white... i do not know how to fix this problem any help would be greatly appreciated

---

### Post by Brian96 on 2007-08-06
I apologize if this has already been addressed, but I followed the tutorial and got it working (thanks, Mr. Greencastle), then I added a compiz --replace command to my startup applications in the "sessions" utility. The problem I have is that when I log into my regular Gnome session it is starting compiz.

1. Should this even be possible? Does this mean that my regular Gnome session is also running in XGL?
2. Is there another way to get compiz to start automatically that won't affect my other sessions?

Thanks.

---

### Post by OZTack on 2007-08-06
> **Brian96 said:**
> 
1. Should this even be possible? Does this mean that my regular Gnome session is also running in XGL?


Thanks.

On my machine, When I select a session from the log in screen, enter my name and password,

It THEN  asks me if the session change is for THIS session only or to make it default. I suspect you made the Gnome WITH XGL the default...
Next time you log in simply select the session GNOME (without the XGL) and when it askes - make THAT the default - HTH

---

### Post by OZTack on 2007-08-06
> **silent1643 said:**
> still no fix for the problem with f-uped graphics when going into xgl desktop  mode?

Heh - I know what you mean - Just installed Compiz-fusion on my desktop with a x850 Plat etc card and got it working (!)
The trick I found to solve your specific problem is :-
After following all the steps so kindly outlined, In my xorg.conf file I had 
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ATI"
	BusID		"PCI:1:0:0"
EndSection
```

It needs to be changed to :
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection
```
Reasonably smooth sailing form there.

Couple of points - 
1) REBOOT like a windows aficionado after making changes!! I know it is NOT supposed to be needed - but it seemed to sort out a lot of my problems.

2) Immediately AFTER installing compiz-fusion, changing sessions etc (AND REBOOTING) I got a notice of an update for windows decorations which I installed.
When I restarted my desktop (for got to reboot :-( ) all my decorations were missing ( ie no min max buttons etc etc).  Rebooting fixed that! ( just restarting log in did not)

AT the moment - I have wobbly windows, rotating cubes AND fire writing :guitar:

BTW I read at [the wiki]("http://wiki.cchtml.com/index.php/Troubleshooting#X800.2FX850_fan_is_very_loud_.2F_constantly_works") that there has been aknown problem with the X850 fan control. NOT sure if it has been fixed.

Let us know if the change I mentioned above helps?

[edit: spelling!]

---

### Post by dp_wiz on 2007-08-07
I've got compiz-fusion running, showing niceties BUT windows' contents are not redrawing and menu leave ghostly trail. Turning a cube helps to updatel, but that's not it expected to work, really (:

Dell 6400 with X1300.

---

### Post by markdjones82 on 2007-08-07
> **markdjones82 said:**
> Ok, I have everything loaded, but Beryl doesn't seem to actually be working.  The manager is loaded, but I am unable to see any effects.  Any help on what to check?

I get over and over in the terminal

beryl-manager Critical can't execute beryl-xgl: Success.

It loads the manager though.


Mine fixed after Beryl updated itself.  Works like a charm, great tutorial!

---

### Post by Brian96 on 2007-08-07
> **OZTack said:**
> On my machine, When I select a session from the log in screen, enter my name and password,

It THEN  asks me if the session change is for THIS session only or to make it default. I suspect you made the Gnome WITH XGL the default...
Next time you log in simply select the session GNOME (without the XGL) and when it askes - make THAT the default - HTH

Thanks, but that is what I did. I allowed the Gnome with XGL session to become default so my wife can enjoy compiz, but when I log into my "regular" Gnome, it auto-starts compiz. I can't figure out how, as the regular Gnome session should not be running XGL, and therefore compiz shouldn't even work (and it should revert back to metacity). I also don't understand why, when I added compiz --replace to my autostart applications, it had to add it to my other Gnome session as well.

---

### Post by silent1643 on 2007-08-07
> **OZTack said:**
> Heh - I know what you mean - Just installed Compiz-fusion on my desktop with a x850 Plat etc card and got it working (!)
The trick I found to solve your specific problem is :-
After following all the steps so kindly outlined, In my xorg.conf file I had 
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ATI"
	BusID		"PCI:1:0:0"
EndSection
```

It needs to be changed to :
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection
```
Reasonably smooth sailing form there.

[edit: spelling!]

my xorg config already has fglrx

here is what i have
```

Section "Device"
	Identifier	"Ati Technologies Inc R481 [Radeon X850XT-PE]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

```


the closest i have come to  getting things to look right in xgl  session is using the envy drivers - desktop looks fine but as soon as an application is launched all is lost :D

---

### Post by haricharan on 2007-08-07
thanks for the repo....works awesome!!!

---

### Post by OZTack on 2007-08-08
Hey Silent - can you list the complete contents of your xorg.conf file?
AND have you set composite to "0" in it at the end? We have the same cards AFAIK ( ATI X850 PE) and it works for me -
also check the end of you xorg.comf -
should have
```
Section "Extensions"
Option "Composite" "0"
EndSection
```

Should **not **see 

```
Section "Extensions"
Option "Composite" "Enabled"
EndSection
```

Like one of the other posters -  I had BOTH those there.... remove the "enabled" one if present.


Oh - couple other things - I guess you didn't start with a clean install - so make sure your "desktop effects" under *preferences  *is **NOT **enabled either! ( shouldn't be possible with the fglrx drivers I know....)

Keep going - Fusion is sweeeeeettt :lol:

---

### Post by melenor on 2007-08-08
I have gotton to the logon with XGL and when i logon everything is messed up, you can't read anything and everything is slanted

---

### Post by vaulter on 2007-08-08
Does anyone have any ideas on why my screen would just turn white after booting with xgl and gnome... or any ideas on how to fix the problem.  I have an ATI radeon express 200M card in a gateway laptop

---

### Post by Ripfox on 2007-08-08
[http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643)

This worked for me, same card and laptop.

---

### Post by silent1643 on 2007-08-08
> **OZTack said:**
> Hey Silent - can you list the complete contents of your xorg.conf file?


```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R481 [Radeon X850XT-PE]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 1907FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R481 [Radeon X850XT-PE]"
	Monitor		"DELL 1907FP"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

i do see this error  however in dmesg
```

[   27.882520] [fglrx:firegl_unlock] *ERROR* Process 4967 using kernel context 0


```

---

### Post by OZTack on 2007-08-09
HI SIlent -
I guess your prob is with the error message as your xorg.comf looks almost identical to mine ( same card etc etc).
I am sure you looked but perhaps   [this ]("http://ubuntuforums.org/archive/index.php/t-294670.html")thread may lead to some answers??
I will keep looking - and FWIW
this is my xorg.conf :
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "0"
EndSection
```

and the relevant part of dmesg:-

```
   15.654046] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   15.655631] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[   15.655655] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   15.664262] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.589546] [fglrx] total      GART = 130023424
[   16.589548] [fglrx] free       GART = 114032640
[   16.589549] [fglrx] max single GART = 114032640
[   16.589550] [fglrx] total      LFB  = 134086656
[   16.589551] [fglrx] free       LFB  = 104214528
[   16.589552] [fglrx] max single LFB  = 104214528
[   16.589553] [fglrx] total      Inv  = 134217728
[   16.589554] [fglrx] free       Inv  = 134217728
[   16.589555] [fglrx] max single Inv  = 134217728
[   16.589556] [fglrx] total      TIM  = 0

```

and My fglrxinfo:-
```
im@Ubuntu-tim:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 XT Platinum Edition
OpenGL version string: 2.0.6334 (8.34.8)

```
I will keep looking....

---

### Post by orangebase on 2007-08-09
I think the problem is a matter of getting the XGL session working; everything else should be fine. I had the same problem and my solution is outlined in [this post]("http://ubuntuforums.org/showthread.php?p=3158623"). Not identifcal hardware, but same situation.

My xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"SDM-HS73"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SDM-HS73"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Venerence on 2007-08-09
*great* guide! I got it working perfectly on my ASUS F3JP (Raedeon x1700).

However, I had to use the following command to get it working,
```
compiz --indirect-rendering --replace -c emerald
``` as opposed to emerald --replace and compiz --replace (as several problems have been fixed using the alternate rendering previously in the thread, it might be worth mentioning in the original post). Thanks to adit for suggesing it!

---

### Post by glosman15 on 2007-08-09
> **melenor said:**
> I have gotton to the logon with XGL and when i logon everything is messed up, you can't read anything and everything is slanted

I have this same problem, I'm using an Ati x1400 with the 8.34.8 drivers.

---

### Post by Stochastic on 2007-08-09
Hi, I just wanted to thank you for an excellent guide.  It works perfectly for my ati radeon Xpress 200M or for the first hour it seems to be working perfectly I should say (one never knows what lies ahead). :)  Oh and that's on an ubuntustudio install.

---

### Post by rinzy20 on 2007-08-10
just a quick ?, is Beryl or Compiz-fusion better? i'm running Ati M200 128meg 2.2 ghz Amd64 (32 bit Ubuntu) 1 gig ram. compizf sounds a bit finnicky

---

### Post by michael37 on 2007-08-10
For the sake of completeness.  I have Dell Laptop: Inspiron E1505 (same as 6400) with ATI x1400 card.  CompizFusion, all Desktop effects, 3D effects, etc work at 100%.    CompizFusion works extremely fast using direct rendering.  Yes, you will find that direct rendering is not supported.  Ignore this error message (**if and only if** you are using fglrx driver and Xgl server).

Feel free to use my xorg.conf as a reference.

**Required packages:**
[LIST]
[*]xorg-driver-fglrx
[*]restricted-manager
[*]xserver-xgl
[/LIST]

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Extensions"
        Option          "Composite"     "0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "false"
EndSection

Section "DRI"
        Mode    0666
EndSection

```


$ glxinfo
```

name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6334 (8.34.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

```

---

### Post by silent1643 on 2007-08-10
great stuff
i used this [link]("http://ubuntuforums.org/showthread.php?t=115104") as a potential fix for my dmesg error

but couldn't seem to get it working 100% - had HAL errors and had to reinstall HAL-Info to get rid of the message...

next step i used
```

sudo dpkg-reconfigure xserver-xorg 
```


and well i guess i just screwed everything up from there lol

anyway no biggie on fresh install, i think im just going to get another vid card for 70 bucks or something :D thanks for the help

---

### Post by ayoli on 2007-08-10
i didn't take time to read all pages (there are many already ;)) so waht i gonna say may have already sai by someone else.
I think the original poster should add a step just before compiz-fusion install to avoid conflicts with original compiz installed by default with feisty.
Before apt-get install compiz and other package do:
```
sudo apt-get remove compiz-core desktop-effects
```

---

### Post by ahchong on 2007-08-11
YO!!!. i was relief that i can install it with no problem..
wel, now there is 1 problem.. my mozilla kept shut down by it oWN!!!
please help me..

---

### Post by melenor on 2007-08-11
I am still having a problem i get to the step where it says to reboot to see if the desktop with XGL worked and when i log on everything is messed up.

---

### Post by mrwasabi on 2007-08-11
I got this error after starting beryl-manager from the terminal:

 Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

(emerald:6504): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed


Now what? BTW I forgot to mention I have the ATI X850XT video card on an Athlon 64 system.

---

### Post by ayoli on 2007-08-11
> **mrwasabi said:**
> I got this error after starting beryl-manager from the terminal:

 Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

(emerald:6504): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed


Now what? BTW I forgot to mention I have the ATI X850XT video card on an Athlon 64 system.

I guess that means you're running xorg as X server, but you need XGL as X server for ati cards.
Did you install XGL as described in the first post and logout/ select XGL session then login ?

---

### Post by mrwasabi on 2007-08-11
No I did not log out then back in, I did and now it works, however I'm getting an error with the updater regarding Compiz!!! Here's the message I get:
[B]
Not all updates can be installed[/B]
Run a partial upgrade to install as many updates as possible.
This can be caused by:
A previous upgrade that didn't complete.
Unofficial software packages not supported by Ubuntu.
Normal changes of a pre-release version of Ubuntu.

That's the end of the error message, now what? Do I have to start over because I launched beryl-manager before rebooting? TIA

Also I got this error during the install when the added repo was updating:
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems


WTF!

---

### Post by ayoli on 2007-08-11
> **mrwasabi said:**
> 
Also I got this error during the install when the added repo was updating:
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

copy/paste this in a terminal:
```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```
and then this:
```
sudo apt-get update && sudo apt-get upgrade
```
does it help ?

---

### Post by mrwasabi on 2007-08-11
Oh man thank you!!!!!!!!!!!!!!!! Well what I did was uninstall everything due to my NOT rebooting per the instructions, lesson learned. Thanks again for the quick responses guys, much appreciated!



MW
:popcorn:

---

### Post by mrwasabi on 2007-08-11
Argh, when I launch beryl-manager from the terminal I get this completely new error:

(emerald:7074): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

?

---

### Post by VAsHachiRoku on 2007-08-13
Worked perfect with my ATI 9800XT.

Just need to get my resolution up to 1280x1024

---

### Post by ba5e on 2007-08-13
When I load the Gnome session with XGL, I get screen corruption!! what can I dO?

---

### Post by mudpuddlestones on 2007-08-13
k, so I'm at wits end, and I've read numerous threads and this one  entirely but I cant get compiz to run. I followed said instructions to a t, twice actually: once from a fresh install.

Specs: ATI x700
dual heads, Big Window

Symptoms:
1.maximizing windows spreads the window across both monitors, with center lying somewhere in between the heads

2. A nifty little error that has pooped(yes pooped) on the Apps/Places/System Bar :
Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

3.CompizConfSettingsManager doesn't open.

4. For kicks I tried to enable Desktop effects by System>Preferences>EnableDE which politely returns the error:
Failed to execute child process "gtk-window-decorator" (No such file or directory)

5. workspaces icon moves the little orange thingys around when I drag windows around the desktop.   

      I'm sure there's more but this is what I know.

Relevant xorg.conf:

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "0x0+0x0"
	BusID       "PCI:1:0:0"
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

I have no problems starting from scratch(reinstall). Soooo. really would love to play with the effects. I know a little but not a lot: A lot seems to be mean so I'm learning a little better.

Please help me save my computer from jumping out this third story window.](*,)

---

### Post by adityakavoor on 2007-08-15
thanks a ton :popcorn:

---

### Post by darkhacker902 on 2007-08-15
I get to here:

```
Code:

sudo chmod a+x /usr/share/xsessions/xgl.desktop

Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close. 
```

and when i log out and back in, I get an extremely jumbled desktop. I cant make anything out :( so i have to log out and change the session back to gnome.

---

### Post by mudpuddlestones on 2007-08-15
I had the same problem and then I reinstalled Ubuntu got past the Login issue  but then Compiz wouldn't run, I installed auto updates the next day and it works weird(rebooted). maybe you'll have the same luck(def. luck in my case)...I hope, cause it's madness. Now I have Compiz, but cant get Blender to run without crashing, which is a BIG problem for me .

---

### Post by BucKao on 2007-08-16
I had the same problem yesterday with the jumbled screen during an XGL login session.  I was running the latest ATI drivers that I DL'd from their website.  So I wiped everything clean, re-installed Ubuntu, and this time I just opened the Restricted Drivers Manager, and enabled the ATI driver listed there (at which point it began downloading the driver, presumably from the Feisty repositories).  I then rebooted, installed Compiz Fusion, set up the XGL session, logged out and back into the XGL session, and everything was fine.  Compiz then worked great.

From this experience, it seemed like the problem was related to the version of the ATI driver I was using, but I suppose something else could have been going on behind the scenes that I couldn't see.  Hope this helps someone.

BTW, my ATI card is an X1950Pro.

---

### Post by pupdawg on 2007-08-16
It's been months since I've been able to get my X1600 working under Feisty... with the new ATI drivers 8.40.4 they now work with 3D Accel... Yea... Finally I can use Compiz... wait... now XGL give me a screen full of garbage.  Damn :(

Ok I'll quit bitching.

So I've been through this whole thread and there are many with the XGL corruption issue but there is zero info towards a solution.   I'm going to mess around and see what I can figure out and report back if I get anything worth reporting.

---

### Post by pupdawg on 2007-08-16
Ok for all of you with the screen corruption try removing fglrx module from /etc/default/linux-restricted-modules-common

This worked for me with a ATI X1600 PCIe 512MB and the new fglrx 8.40.4 and now I have XGL, Compiz Fusion 5.2 , and no screen corruption.  :)

> **pupdawg said:**
> It's been months since I've been able to get my X1600 working under Feisty... with the new ATI drivers 8.40.4 they now work with 3D Accel... Yea... Finally I can use Compiz... wait... now XGL give me a screen full of garbage.  Damn :(

Ok I'll quit bitching.

So I've been through this whole thread and there are many with the XGL corruption issue but there is zero info towards a solution.   I'm going to mess around and see what I can figure out and report back if I get anything worth reporting.

---

### Post by thecobraeffect on 2007-08-16
I just installed xgl+compiz fusion on my computer, but now my resolution is only 1024x768. It was 1680x1050 before. My xorg.conf didn't change at all. Any ideas?

Here's my xorg.conf for reference.
```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes	"1680x1050" "1024x768"	"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes	"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes	"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes	"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes	"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes	"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

### Post by LordMau on 2007-08-16
Combining instuction from this [thread]("http://ubuntuforums.org/showthread.php?t=481314&highlight=ati+feisty") [re:use of amaranth's repos] and this thread's instruction are the following observation:

[a] original config using xgl + trevinos repos:

[LIST]
[*]The flip-3D window effect is included.
[*]Focus rules aren't really followed specifically with USP which is always underneath other windows in spite being specified as above in the focus rules.
[*]Also similar focus problem with conky this time with regards to being set as ignored all the time, it was still being minimized using the show desktop.
[*] No need to install Emerald, fusion came with a default window decorator that showed immediately.
[/LIST]

[b] after using the  amaranth repos
[LIST]
[*]flip-3D not included in  the plugins, gained fire annotation tool.
[*]Focus rules are much better implemented, ***USP is now consistently on top of all windows.*** * see edit 1
[*]Conky now being ignored by show desktop as required.
[*]No window decorators at first start! Needed to install emerald, and then add the emerald --replace command to my autostart. Also when I use the theme selector the highlighted theme does not get applied asap as I had been accustomed from beryl before. Instead I need to log-out or restart the X server to see the new selected theme. Such a bother this!
[/LIST]

*EDIT 1 [8/18/07]: >sigh< the better focus behaviour is now lost again. USP frequently appears under other windows now. suggested solutions are welcome.*

---

### Post by StevenEpic on 2007-08-16
excuse me. im anew with ubuntu. and i tried installing XGL but i couldnt get past this step
> Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close.
it loaded the desktop, but it looked all scrambled and bad. can anyone help?

---

### Post by darkhacker902 on 2007-08-16
> **pupdawg said:**
> Ok for all of you with the screen corruption try removing fglrx module from /etc/default/linux-restricted-modules-common

This worked for me with a ATI X1600 PCIe 512MB and the new fglrx 8.40.4 and now I have XGL, Compiz Fusion 5.2 , and no screen corruption.  :)Nope. Didnt work. I still get a very jumbled screen. And for those of you that suggested re installing. Not an option. I finally configured my wifi, and will not re install, because I cant lose that :P

---

### Post by xIke on 2007-08-16
Add be to the line of people with garbled x1600 graphics.  I'd really like a solution if someone has one.

---

### Post by Madrigal77 on 2007-08-16
I get the following error trying to install compiz fusion. When I type in this code:

> sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes

I get this error:

> blair@blair-desktop:~$ sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

Any ideas what I'm doing wrong?

---

### Post by macaholic on 2007-08-16
For me garbled screen garblization is fixed by a Ctrl alt backspace (restart xserver)

---

### Post by xIke on 2007-08-16
Madrigal7: I had the same problem, check this thread: [http://ubuntuforums.org/showthread.php?t=517858]("http://ubuntuforums.org/showthread.php?t=517858")

---

### Post by xIke on 2007-08-16
> **macaholic said:**
> For me garbled screen garblization is fixed by a Ctrl alt backspace (restart xserver)

Same here.  I'd like to know why that's necessary though.  If I knew what it was about restarting x that fixed it, maybe I could prevent this annoying and ugly problem.

---

### Post by boob11 on 2007-08-16
thnax :)

---

### Post by LordMau on 2007-08-17
Another quirk: programs that require gksudo (ex synaptic) when first run under compiz greys out the background the show the admin password prompt. After entering the password instead of showing the expected window the screen just shows the gryaed out background. Even shifting workspaces has no effect, giving the effect that the session has hung. However Ctrl-Q works and the program quits restoring normal behaviour. Subsequent running of the same program is then normal.

So it appears compiz is unable to show the correct window after a gksudo prompt. Is there a fix for this behaviour?

---

### Post by hvc123 on 2007-08-17
hey all i got everyting running ok except i run compiz --replace and loads of plugins load in the terminal but bugger all happens to my effects...


ahhhhh

---

### Post by blenderfish on 2007-08-17
I tried this How-To, and when I try to log into the XGL session, my screen shows a very distorted desktop.  Everything is horizontally striped beyond recognition.  Any ideas?  I am running Feisty on an IBM z61m with an ATI x1400 video card.

---

### Post by xIke on 2007-08-17
> **blenderfish said:**
> I tried this How-To, and when I try to log into the XGL session, my screen shows a very distorted desktop.  Everything is horizontally striped beyond recognition.  Any ideas?  I am running Feisty on an IBM z61m with an ATI x1400 video card.

Man you're lucky.  I just got done fixing the same problem last night (though I have a better video card- x1600 :P).  The problem is that it's using the generic mesa drivers instead of the ati-restricted drivers.  If you haven't already, login with a safe setup (plain gnome), go to System:Administration:Restricted Drivers Manager, and enable the ATI drivers.  If this doesn't work, then you hosed your system a little bit (like I did), but I can suggest more fixes.

---

### Post by darkhacker902 on 2007-08-17
> **xIke said:**
> Man you're lucky.  I just got done fixing the same problem last night (though I have a better video card- x1600 :P).  The problem is that it's using the generic mesa drivers instead of the ati-restricted drivers.  If you haven't already, login with a safe setup (plain gnome), go to System:Administration:Restricted Drivers Manager, and enable the ATI drivers.  If this doesn't work, then you hosed your system a little bit (like I did), but I can suggest more fixes. Ok the Drivers are enabled, I reinstalled fglrx and the such, but still jumbled Session.

Here is my fglrx output:


> $ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

---

### Post by xIke on 2007-08-17
You haven't tried to use Envy to install video drivers have you?  I did that and it really messed things up.

By the way, there's a mob of us on irc where you might get help faster.
irc.freenode.net
#ubuntu or #ubuntu-effects

---

### Post by freshspinach on 2007-08-18
I followed this HowTo and when I came back into Feisty, I couldn't manage my windows...i can't resize or minimize. every window opens on the top left corner of my screen and is stuck there...can i uninstall this compiz if i'm screwed? and how?

---

### Post by maharbA on 2007-08-18
> i can't resize or minimize. every window opens on the top left corner of my screen and is stuck there

Same here. Try holding Alt and dragging your windows around -- that works for me (it's also helpful if windows get thrown above the screen for whatever reason)
and Alt+F4 will close the active widow.

When I type "emerald --replace" in a terminal it says "Segmentation fault (core dumped)"
so I'm guessing Emerald is the problem (no window borders)

Any help appreciated.

PS: Great how-to, though. This is the closest I've come so far -- and everything else in CF is working nicely.

---

### Post by maharbA on 2007-08-18
UPDATE:

I was messing with CompizConfig settings manager (nothing important -- opacify, negative, etc.) when everything seemed to freeze (ack!) I restarted X and Metacity came on. There were system updates, so I installed them. Then I ran (in Terminal) "compiz --replace" and I'm back to CF with no borders, the I type "emerald --replace" and IT WORKS!!! yay

I don't know what did it, and I hope it keeps working, but I'm very happy right now.

---

### Post by pacsum on 2007-08-18
everything is working nice except I can't see the the close, maximize, minimize buttons on the windows, what do I have to do?

---

### Post by dinostabOMG on 2007-08-19
> Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close.

I'm kind of a noob. I didn't understand this part. When I log out, all I can do is log back in or turn off the computer... is there something I'm missing here?

Also, those two files I edited with gedit... they were supposed to be blank on opening them, right?

Edit: nebermind,I really am a noob. It's under options.

---

### Post by OZTack on 2007-08-19
@ pacsum
> everything is working nice except I can't see the the close, maximize, minimize buttons on the windows, what do I have to do?

You SHOULD be notified that there is an update available - can't remember what ir was - to do with window 'decorations' though - you d/l that and restart X and all will be ggod IIRC...

Do an update check....

---

### Post by michael37 on 2007-08-19
> **pacsum said:**
> everything is working nice except I can't see the the close, maximize, minimize buttons on the windows, what do I have to do?

You don't have window decorations.  A common solution is to install emerald and use it for the window decorator manager.

The command is 
```
compiz --replace -c emerald

```
Search forums for many threads on this issue.

---

### Post by flierman on 2007-08-19
Hey there!

I have unisnatlled Ubunto 6 times and almost gave up, the guide works all the way to Compiz. When installed and relogging on npthing happens. Just an error code that some package is broken.

The compiz packages are broken packages...someonw knows what to do Update or what?

---

### Post by XTREEM|RAGE on 2007-08-19
i'm to the point i need to update before i can install compiz or beryl, but i have 1 problem and that is i get an error while updating:

```

Fetched 14.4kB in 0s (24.7kB/s)
Reading package lists... Done
W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

```


And i also cant(auto) update anymore, it says : The error message was: 'Error: BrokenCont>0'

How can i fix this?? :D

--Edit--
I fixed it with the reposity of this nice site :D [http://ubuntuforums.org/showthread.php?t=481314&highlight=how+to+install+compiz+fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=how+to+install+compiz+fusion)

---

### Post by flierman on 2007-08-19
I actually got it to work for the first time in 7 installations..fantastic. When I got the error of packages at startup I updated Compiz and it works!

But i get an error with the themes of some kind!

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

Someone knows how to update them to same?

---

### Post by 0MG on 2007-08-19
This is the first time I have ever gotten Compiz/Beryl going under Ubuntu with this video card. Have my baby. Now.:guitar:

---

### Post by narkee on 2007-08-19
Everything was going great for me, until I got to the point where I logged out, logged back in, and had to do this :

```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

which gave me this output:

```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
--22:53:50--  http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... failed: Connection refused.
gpg: no valid OpenPGP data found.
```

Any help?
Thanks in advance for the great HOWTO

---

### Post by Parms on 2007-08-20
> **narkee said:**
> Everything was going great for me, until I got to the point where I logged out, logged back in, and had to do this :

```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

which gave me this output:

```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
--22:53:50--  http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... failed: Connection refused.
gpg: no valid OpenPGP data found.
```

Any help?
Thanks in advance for the great HOWTO

I'm also stuck at that point, I've tried 3 times.  I also tried the log out part. Am I suppose to click the box in the upper right corner that has the restart, shut down options, and log out there? When I log out from there I just get a black screen.

I need help with the security key, the copy/paste will not work. Also getting the same error as above.

---

### Post by butcher99 on 2007-08-20
When doing the ati updates in SUDO  and writing the startxgl.sh file I get this error
Could not save the file /usr/local/bin/startxgl.sh.   I am assuming that this means I do not have enough admin abilities to do so.   
  What do I need to do to get these privileges?
 TIA
jim

---

### Post by DownTown22 on 2007-08-20
Big thanks for the "How To"!
Worked like a charm on my fiance's Toshiba laptop with an ATI 200M graphics card.
And with the latest Compiz Fusion update, things are running much, much better.

Now I just can't wait to get it running on my home computer!

\\:D/

---

### Post by Parms on 2007-08-20
> **DownTown22 said:**
> Big thanks for the "How To"!
Worked like a charm on my fiance's Toshiba laptop with an ATI 200M graphics card.
And with the latest Compiz Fusion update, things are running much, much better.

Now I just can't wait to get it running on my home computer!

\\:D/

Hmmm... thats the same card I have. I've followed this guide but can't seem to get the compiz-fusion part to install.

I get the error.. compizconfig-manager not found!!

can you tell me the steps that you took leading off from.. 
Logging in with XGL-Gnome (I can do this now)

---

### Post by Parms on 2007-08-21
OK... it seems like everyone is having issues, but there is something people arn't telling us!! Lol. Because compiz is never found or installed. If someone wouldn't mind a picture by picture instruction that would help. I'm into the Gnome with XGL.. Also when I try the purge nothing happens. 

I've started from scratch, and up too the part where I'm logged into Gnome with XGL...

Please help with something up to date.. Because all these how-to guides are not working. 
Purging doesn't work, because nothing was installed (I guess)
When I'm suppose to use other repositories where do I get them? None of these guides explain that. It just says copy and paste theres, but when I try to get to compiz it says not found.

also tried
sudo get install compiz (and all the other ones)
says they are not found or not installable.

I used the command line the terminal told me to when I typed in compiz --replace

Errrr.. I don't mean to be rude or anything, it's just frustrating that people are getting this to work with no problems and I'm getting a problem every step of the way. Also how are some people getting good installs on these guides when I don't get anything installed.

Says not found, or uninstallable

---

### Post by DownTown22 on 2007-08-21
Alrighty, I assume you can log in to the XGL session?  While loading up, your cursor should be an "X".  If so, we should be good to get Compiz-Fusion up and running.

At this point it's a good idea to remove any Compiz related packages you may have installed already.

```
sudo apt-get --purge remove compiz* libcompizconfig*

```
Now, press **ALT+F2**, type: gksudo "gedit /etc/apt/sources.list" and press "Run".

Now, add the following three lines to the end of the file:
```
# compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

```

Save and close that file.  Now we need to get the key.  So, open a termal and enter:
```
gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add -

```

Now that we have all that out of the way, we can get around to installing Compiz-Fusion!
Run another update:
```
sudo apt-get update

```

In a terminal, enter the following:
```
 sudo apt-get install compiz compiz-gnome compiz-plugins compizconfig-settings-manager libcompizconfig-backend-gconf compiz-fusion-plugins-extra

```

For now, I wouldn't add compiz --replace to your sessions, just in case something goes wonky.  Instead, press **ALT+F2** and enter compiz --replace.
You should be up and running.  If not, post away.

---

### Post by markdjones82 on 2007-08-21
fglrx had an update last night from the OS that I ran and when I rebooted, it messed up the video. As soon as I login with XGL the screen has horizontal lines over everything and it does not show up properly.  I am unable to read anything on the screen, but graphics do show up.

Now, if I choose gnome without xgl everything shows up fine. I believe something happened with the driver or XGL.  Is there a way to roll back any updates?  If anyone can assist please shoot me a PM thanks!

---

### Post by DownTown22 on 2007-08-21
Just realized I forgot to mention in my original post that I used this "How To" as well as the guide found here:

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

---

### Post by davidonabus on 2007-08-21
hi there.

I followed this to a T.. however, when I login all I see is my desktop (or something vaguely resembling my desktop) distorted.  I can see distorted representations of all the buttons/icons, etc. on the desktop..  but when I say they're distorted, I mean they're REALLY distorted.  A mess of colors and lines.

I am using a Sapphire Radeon X1550 AGP.

Any suggestions would be GREATLY appreciated!  thanks guys.

David

My FGLRXINFO shows :

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6650 (8.39.4)

My LSPCI shows :
00:00.0 Host bridgename of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6650 (8.39.4)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_element_array, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer, 
    GL_ATI_separate_stencil, GL_ATI_shader_texture_lod, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object, 
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3, 
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7187
01:00.1 Display controller: ATI Technologies Inc Unknown device 71a7
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:09.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
02:0c.0 Ethernet controller: Digital Equipment Corporation DECchip 21041 [Tulip Pass 3] (rev 21)

And my GLXINFO shows :

---

### Post by LordMau on 2007-08-22
> **Mr Greencastle said:**
> 
<snip>
```
sudo gedit /usr/local/bin/startxgl.sh
```

Now copy and paste this into the file that pops up:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

**SAVE THIS FILE!** Once its done saving, make that fire executable (like a program) by pasting this into a terminal:

```
sudo chmod a+x /usr/local/bin/startxgl.sh
```
<snip>Mr Green

May I suggest to add on these instructions for those people who have smaller fonts than normal when using XGL, refer to this post:

> **mahnoosh said:**
> Here is the step by step Installation Guide of XGL/Beryl for ATI XPRESS 200 Integrated Graphics

<snip>
If you have a problem with your fonts appearing tiny, you may need to add the -dpi 96 flag to the Xgl call:

```
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer **-dpi 96** &
```
<snip>

It certainly helped mine. The original thread **[COLOR="Red"][here.]("http://ubuntuforums.org/showthread.php?p=2030190")[/COLOR]** refered to Edgy installation but this bit applies to feisty as well.

---

### Post by XTREEM|RAGE on 2007-08-22
After an yesterday update i cant get compiz running anymore

```
compiz --replace
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070815
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'
```

[http://ubuntuforums.org/showthread.php?p=3232485&posted=1#post3232485](http://ubuntuforums.org/showthread.php?p=3232485&posted=1#post3232485) i have did some thngs on the compiz forum but it didnt work. I this just an update issue? that i need to w8 on the avail package or something?

---

### Post by Dark Star on 2007-08-22
Thanks for the guide .. My friends will be benefitted by this :)

---

### Post by Zero Prime on 2007-08-22
> **XTREEM|RAGE said:**
> After an yesterday update i cant get compiz running anymore

```
compiz --replace
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070815
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'
```

[http://ubuntuforums.org/showthread.php?p=3232485&posted=1#post3232485](http://ubuntuforums.org/showthread.php?p=3232485&posted=1#post3232485) i have did some thngs on the compiz forum but it didnt work. I this just an update issue? that i need to w8 on the avail package or something?

Your not the only one.  I even uninstalled it and reinstalled it to no avail.  I'm having to run Beryl right now.  One thing I though was odd about the update is that I didn't have Beryl installed at the time but the update manager installed beryl core along with a few other beryl related components.

---

### Post by michael37 on 2007-08-22
> **LordMau said:**
> May I suggest to add on these instructions for those people who have smaller fonts than normal when using XGL, refer to this post:



It certainly helped mine. The original thread **[COLOR="Red"][here.]("http://ubuntuforums.org/showthread.php?p=2030190")[/COLOR]** refered to Edgy installation but this bit applies to feisty as well.

I disagree with this approach.  I use the Xgl command without the "dpi" option.  As a result, I get 
```

$ xdpyinfo | grep resolution
  resolution:    100x100 dots per inch

```
and then, I click on System/Preferences/Font.  On the Font window, click on "Details" on the lower right.  In the new window that opens, select the font resolution to match your xdpyinfo output.

---

### Post by Deived on 2007-08-24
This HOWTO was a great help.  I got it working great, but with 1 issue...

The 3D cube and everything works fine, but I can't change any settings.  I tried changing the emerald theme but it stayed the same.  I am able to do the...```
emerald --replace
```to restart it with the update.  I prefer not to go that route for now so I just disabled emerald from launching when the the sessions starts.  
The problem that I'm having though is that I can't change the compiz settings either.  Ex...  I change the cube setting "Opacity When Not Rotating" to zero and turn off "Transparency Only On Mouse Rotate" so that my desktop could be always transparent, but nothing changes.  It also stays the same when I log out and back in.  When I try ```
compiz --replace
``` it just locks up.  Here's what my .xsession-errors shows.  Hope this helps.
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "deived"
/etc/gdm/Xsession: Beginning session setup...
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SESSION_MANAGER=local/david-laptop:/tmp/.ICE-unix/7257
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
evolution-alarm-notify-Message: Setting timeout for 66038 1188000000 1187933962
evolution-alarm-notify-Message:  Fri Aug 24 17:00:00 2007

evolution-alarm-notify-Message:  Thu Aug 23 22:39:22 2007

Initializing gnome-mount extension

(gnome-panel:7334): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)

(gnome-panel:7334): Wnck-WARNING **: Unhandled action type (nil)
```

Anyone?

---

### Post by LordMau on 2007-08-24
> **michael37 said:**
> I disagree with this approach.  I use the Xgl command without the "dpi" option.  As a result, I get 
```

$ xdpyinfo | grep resolution
  resolution:    100x100 dots per inch

```
and then, I click on System/Preferences/Font.  On the Font window, click on "Details" on the lower right.  In the new window that opens, select the font resolution to match your xdpyinfo output.

For GNOME users may be usefull, but pretty useless for pure Xubuntu users (may even other alternative DES as there no such item (System/Preferences/Font). So I "disagree" with this approach also! :lolflag:

---

### Post by praveenmarkandu on 2007-08-24
for some odd reason my compiz settings dont save. i followed this guide to the letter. basically by just copy and pasting. my emerald settings save though. before i reinstalled ubuntu, my compiz could load the plugins on the fly. whats wrong with mine now?

=========edit==============
fixed it, had to install the compiz gconf thing. weird that it reallies on gconf settings.

---

### Post by streetsurfer on 2007-08-24
sweet the instructions worked perfectly although I have a quick question about the direct rendering.
Im using an ati x1600 pro

GLXINFO comes up with the following

```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 1.2 (2.0.6334 (8.34.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

Is there anyway to get it to render directly? Cos it seems like this is the problem with getting any 3D games to run properly without screwed up textures. :(
Thanks in advanced.

---

### Post by Deived on 2007-08-24
> **praveenmarkandu said:**
> for some odd reason my compiz settings dont save. i followed this guide to the letter. basically by just copy and pasting. my emerald settings save though. before i reinstalled ubuntu, my compiz could load the plugins on the fly. whats wrong with mine now?

=========edit==============
fixed it, had to install the compiz gconf thing. weird that it reallies on gconf settings.

Do you remember what the full package name was?  I see gconf in the package manager, but it says nothing about compiz.  Is that it?

---

### Post by praveenmarkandu on 2007-08-24
> **Deived said:**
> Do you remember what the full package name was?  I see gconf in the package manager, but it says nothing about compiz.  Is that it?

libcompiz-backend-gconf
yay! i helped someone today. my day was not totally wasted :) thanks

---

### Post by Deived on 2007-08-24
> **praveenmarkandu said:**
> libcompiz-backend-gconf
Thanks!  I'll give it a shot tonight.
> yay! i helped someone today. my day was not totally wasted :) thanks
Great feeling isn't it :KS

---

### Post by .exe on 2007-08-25
Thanks a mill for this guide. It took me a loooong time to get Beryl working on my own with an ATI, and I wasn't able to reprodce it on another install till you came along.

---

### Post by ocean223 on 2007-08-26
Thanks!!!!!:KS:lolflag: Works perfectly ATI 9600 XT.
Only nuked my box once when I first tried this about three weeks ago.

---

### Post by maclac on 2007-08-26
Hi all,

I have just installed my first copy of Ubuntu (ultimate 1.4 if you need to know) on my laptop (dual booting with vista) and Im trying to follow the tutorial on this thread for  getting compiz to work (using my laptops ati x1400)

My problem is that when I do the 
" sudo apat-get install xserver-xgl"
 bit it asks me for a password and Im unable to type anything in.

Again Im a complete newb here, can anyone help me out??

Cheers

Malc

(also - a bit offtopic but does anyone know where I can find the option to switch of my touchpads "tap to click" option (hate that feature of mousepads) and bring back the scroll feature??)

---

### Post by DownTown22 on 2007-08-26
Yeah, when you type your password, nothing will show up on the screen, but trust me, your password is being entered.

And make sure your code is:

sudo apt-get install xserver-xgl

(noticed yours says **apat-get** )

---

### Post by [Alsharifi] on 2007-08-26
wow thanx for this how to it is the only one that ever worked with my comp!!!!


one more question how can i get the cube to rotate when i hold in my little scroll wheel on my mouse,cant seem to find how to do that in the compiz setting manager

---

### Post by super.rad on 2007-08-27
Just a quick question, could anyone tell me if this guide will work for Debian Etch?

---

### Post by Tosa on 2007-08-27
Could someone rewrite this howto for KDE?

Regards

---

### Post by bdoe on 2007-08-27
> **davidonabus said:**
> I followed this to a T.. however, when I login all I see is my desktop (or something vaguely resembling my desktop) distorted.  I can see distorted representations of all the buttons/icons, etc. on the desktop..  but when I say they're distorted, I mean they're REALLY distorted.  A mess of colors and lines.

I am using a Sapphire Radeon X1550 AGP.

Any suggestions would be GREATLY appreciated!  thanks guys.
I had the exact same problem (using ATI Radeon 9700 Mobility).  Followed the instructions to the letter, but as soon as I logged into my XGL on Gnome session, all hell broke loose!  This was with both the original restricted drivers and with the updated fglrx drivers.  I ended up removing fglrx, went back to the Mesa drivers, and reloaded Beryl.

I did manage to get Gnome on XGL working once (I changed something in xorg.conf, but I can't recall anymore what it was).  However, I had no DRI anymore.

Is there any particular advantage to using fglrx drivers at all?  It seemed horribly sluggish to me compared to the Mesa drivers, and fglrx with glx seemed to make the whole system horribly unstable.  Since I have Beryl working well with AIGLX, is it okay to install Compiz Fusion using AIGLX as well?

---

### Post by dougfractal on 2007-08-27
Can you use my diagnostic tool as it will tell me lots of things about your setup.

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```

please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by bdoe on 2007-08-27
I ran the script, though I have no idea what "Ubuntu Name" is...

I'm running a straight Gnome session.  XGL on Gnome totally screws up my screen.

Script results attached.

---

### Post by bdoe on 2007-08-27
Okay, I managed to get XGL to work.  Apparently, I had to completely reboot the computer instead of just logging out.  2D rendering is absolutely *terrible* (I'm typing twice as fast as the screen can display what I typed).

Attaching another copy of that script output.

---

### Post by dougfractal on 2007-08-27
Q> I have no idea what "Ubuntu Name" is...
A. bdoe


I'm was missing xgl stuff in my script 

follow this guide for xgl
[http://ubuntuforums.org/showthread.php?t=482773&highlight=xserver-xgl](http://ubuntuforums.org/showthread.php?t=482773&highlight=xserver-xgl)

then setup the new repos
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
 
amaranth's is more stable than Treviño's. (I think)

---

### Post by SparksLP on 2007-08-27
[SIZE="2"]I keep getting this error message every time I try to install Compiz....

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator but it is not installable
E: Broken packages

What should I do? I'm running an AMD 64 bit machine, 64 bit Ubuntu, and an ATI Card.[/SIZE]

---

### Post by dougfractal on 2007-08-27
Hi bdoe
from [http://vorian.org/?p=82#comment-615](http://vorian.org/?p=82#comment-615)
> I have an ati 9800 pro card and use the radeon driver insted of fglrx.
Very stable and fast. And I do not need xgl.

your compiz are old.

SparksLP  run my above script, as I think your repos haven't been updated.

---

### Post by dodgem on 2007-08-28
Grrr... i tried this on a newly created login to see if i could get it to work and i did!! :)

But for some reason i can't login using the Gnome with XGL session on my normal account.  I get an error that the session lasted less than 10 seconds, and the detail was:

 Cannot create server lock file : /tmp/.X1-lock

I've tried completely removing Compiz and Emerald and following the instructions again on my usual login, and deleting the old user that i initially set it up on.  The only thing i haven't done is to resave the 3 files that were created/editted since they were exactly as they should be.

Any suggestions?  I was really happy to have it working until i realised that it only worked on the one session...

(I did have to remove my restricted driver and reinstall it to get rid of a corrupt desktop, but once that was done it worked fine on the other login.)

---

### Post by DownTown22 on 2007-08-28
I had that exact same problem after I ran an update on my Compiz Fusion.  And it worked again after I started all over from the beginning of the HowTo.  Removed everything I installed and then did the whole HowTo again.  Then it worked perfectly!

---

### Post by dodgem on 2007-08-28
I was a little hasty in my cry for help it seems :)

I logged on with my usual login and removed the restricted drivers there.  Restarted, reinstalled the restricted drivers and restarted again, and now everything is shiny!! 

Thanks for the HowTo =D>

---

### Post by kubilaycan on 2007-08-29
hi i tried to follow the steps here but and everything worked until i tried to install compiz fusion. i have xgl now and i am able to login using gnome with xgl.

i get this error message:

Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.5.2~git20070827+3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compizconfig-settings-manager_0.5.2~git20070827+3v1ubuntu0_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compizconfig-settings-manager_0.5.2~git20070827+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

i am using feisty with radeon 9600xt

thx

---

### Post by kubilaycan on 2007-08-29
yeah ok regarding my previous post. i hope you had a good laugh at it. you can disregard it as it was a simple process of redownloading the package.. 

you can call me noob saibot.

oh yeah and by the way it all works now!

---

### Post by michael37 on 2007-08-29
> **kubilaycan said:**
> hi i tried to follow the steps here but and everything worked until i tried to install compiz fusion. i have xgl now and i am able to login using gnome with xgl.

i get this error message:

Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.5.2~git20070827+3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compizconfig-settings-manager_0.5.2~git20070827+3v1ubuntu0_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compizconfig-settings-manager_0.5.2~git20070827+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

i am using feisty with radeon 9600xt

thx

This is not an Xgl or ATI problem.  This is a problem with your package management.

Run these commands:

```

sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update

and then

sudo apt-get install compizconfig-settings-manager

```

---

### Post by gavinjb on 2007-08-29
Hi,

I have just installed XGL (I rebooted to make sure), but when I try to login I get a complete mess of a screen, only answer was ctrl + Alt +backspace.

I noticed a post in this topic, it mentioned running Xinfo, I have run this and attached the file, can anyone help.

I almost forgot I am running an ATI Mobility Radeon X1400, which is too my knowledge not supported by the Open Source driver which is a pity as I understnad with this driver it is easy to install Compiz, so I am using the ATI Driver.

Thanks,

---

### Post by michael37 on 2007-08-29
> **gavinjb said:**
> Hi,

I have just installed XGL (I rebooted to make sure), but when I try to login I get a complete mess of a screen, only answer was ctrl + Alt +backspace.

I noticed a post in this topic, it mentioned running Xinfo, I have run this and attached the file, can anyone help.

I almost forgot I am running an ATI Mobility Radeon X1400, which is too my knowledge not supported by the Open Source driver which is a pity as I understnad with this driver it is easy to install Compiz, so I am using the ATI Driver.

Thanks,

Try display 1: instead of 0:, it works better with ATI fglrx.  More info [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by michael37 on 2007-08-29
> **michael37 said:**
> Try display 1: instead of 0:, it works better with ATI fglrx.  More info [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

I'm sorry, I gave you utterly useless advice.  The Xorg log you included is from Xorg, not from Xgl and it misled me.  Look in /var/log, there should be file named smth like Xorg.94.log in addtion to Xorg.0.log.  Could you please post that log?

---

### Post by gavinjb on 2007-08-29
Thanks,

I was just thinking, I had set Display = 1, I have attached the log file.

Gavin

---

### Post by gavinjb on 2007-08-29
sorry, forgot to attach file.

---

### Post by dougfractal on 2007-08-29
you have  #'ed Amaranth repo infavour for Treviño's.
Amaranth is the ubuntu CF maintainer.   Treviño is a CF pioneer who brings much to ubuntu. But i recommend Amaranth.




also remove nvidia-kernel-common
and It look as if you used Envy

you could remove fglrx with envy
and install fglrx from ubuntu.


from [https://help.ubuntu.com/community/Beryl/ATI/Feisty](https://help.ubuntu.com/community/Beryl/ATI/Feisty)
> If when you login, 'grep EE /var/log/Xorg.1.log', returns:

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

You can fix this by adding at the bottom of /etc/X11/xorg.conf

Section "ServerFlags"
Option "AIGLX" "off"
EndSection 

---

### Post by michael37 on 2007-08-29
> **gavinjb said:**
> sorry, forgot to attach file.

Your X is configured fine as well as the rest of your system.  I am not sure why the system doesn't work in the way you configured it.  I recommend carefully rolling back the changes you made earlier (you used Method A with startxgl.sh script) and instead apply [Method B](https://help.ubuntu.com/community/CompositeManager/Xgl#head-0e4ffce2a76cdb03b8dbd57642f13fac385afef0) (with "If you have ATI with fglrx drivers" detail) which IMHO has a more foolproof method of starting Xgl nested with Xorg.

---

### Post by michael37 on 2007-08-29
> **gavinjb said:**
> Thanks,

I was just thinking, I had set Display = 1, I have attached the log file.

Gavin

Another thought: comment out two lines in your /etc/X11/xorg.conf:
```

 	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"

```

I doubt it will make much difference, but you can always enable them when everything else works.

---

### Post by pegwole on 2007-08-30
I have an odd issue, I followed this tutorial exactly, when i logged into the Gnome XGL session, the button Gnome panel was there for a sec, then it was gone.  The top panel is stoll there, i can put it where the bottom one was, but if I make a new panel and try to put it on the bottom, it only suts above the bottom like it's on top of the old one but the old one is not there.  If i right click it gives me the usual desktop options, not the Gnome panel options.  It's not been set to autohide either.  Any ideas on this one?

---

### Post by gavinjb on 2007-08-30
> **michael37 said:**
> Another thought: comment out two lines in your /etc/X11/xorg.conf:
```

 	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"

```

I doubt it will make much difference, but you can always enable them when everything else works.

Thanks,

I have tried turning both these options off and Method B and in both cases I still get the corrupted screen, any ideas.

I have also noticed that since playing around with these settings Ubuntu stops for 2-3 minutes during boot (when progress bar is just under 50%) and it is now taking much longer to boot.

---

### Post by michael37 on 2007-08-30
> **gavinjb said:**
> Thanks,

I have tried turning both these options off and Method B and in both cases I still get the corrupted screen, any ideas.

I have also noticed that since playing around with these settings Ubuntu stops for 2-3 minutes during boot (when progress bar is just under 50%) and it is now taking much longer to boot.

With Method B, Gnome always runs Xgl.  As I said, IMO this is a cleaner option.  Do you get a login screen for your username?  Is it "clean" or "corrupted" (btw, what exactly does "corrupted" mean?)

I am beginning to infer that you may have a broken fglrx driver.  So, I recommend  following the earlier suggestion to uninstall Envy fglrx and install the Ubuntu fglrx using the "restricted manager driver".  I have the same ATI Mobility x1400, and it works fine for me.

In short, I would remove Envy's driver, uninstall Envy, and then uninstall (maybe even with -purge, not sure about that) and then reinstall the following packages from Ubuntu **restricted** repository:
[INDENT]
xorg-driver-fglrx
linux-restricted-modules-2.6.20-16-generic
*(optional)*fglrx-control[/INDENT]

---

### Post by dougfractal on 2007-08-30
in Xorg.0.log.tar.gz post [http://ubuntuforums.org/showpost.php?p=3276418&postcount=202](http://ubuntuforums.org/showpost.php?p=3276418&postcount=202)

you had this > (EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

in your xorg.conf you did not have > Section "ServerFlags"
Option "AIGLX" "off"
EndSection

Is this still true?

michael37> In short, I would remove Envy's driver, uninstall Envy, and then uninstall (maybe even with -purge, not sure about that) and then reinstall the following packages from Ubuntu restricted repository:


    xorg-driver-fglrx
    linux-restricted-modules-2.6.20-16-generic

**I agree**, Envy is useful for the latest cards and ubuntu repos aren't that old.

---

### Post by gavinjb on 2007-08-30
Not sure if it was uninstalling the driver etc... with -purge or making the changes to xorg.conf, but Xgl seems to be working now 

```

gavin@gblaptop:~$ ps -e | grep Xgl
 6910 ?        00:00:20 Xgl

```

Only problem is that when I run compiz --replace I lose all the buttons from the top of windows (close etc), I tried running Preferences - CompizConfig Settings Manager but nothing opens.

Thanks,


Gavin,

---

### Post by dougfractal on 2007-08-30
Almost there ;-)

> sudo apt-get install --reinstall libwnck*
sudo apt-get install --reinstall libwnck*
aptitude search libwnck
> 
aptitude search  ~icompiz  -F "%20p %10v %10V %20d"
I can't tell if you've got Amaranth or Treviño's compiz, I think 1:0.5.5~gi... is Treviño. use Amaranth which would be 1:0.5.2+gi.....

from above
> you have #'ed Amaranth repo infavour for Treviño's.
Amaranth is the ubuntu CF maintainer. Treviño is a CF pioneer who brings much to ubuntu. But i recommend Amaranth.


[COLOR="Gray"]try  emerald (This is more a work around)
>  sudo apt-get install emerald libemeraldengine0

emerald --replace & # from compiz
compiz --replace -c emerald &   # from metacity
metacity --replace # back to old style gnome[/COLOR]


run the script again
```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```

please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by gavinjb on 2007-08-30
> 
emerald --replace & # from compiz
compiz --replace -c emerald & # from metacity
metacity --replace # back to old style gnome


After running this I can run CompizConfig Settings Manager, but still not much luck with compiz.

I re-enabled Amaranth repo and update manager gave me a whole host of compiz updates, so it looks like I am back on his Compiz.

Here is a list of the compiz packages

```

gavin@gblaptop:~$ aptitude search ~icompiz -F "%20p %10v %10V %20d"
compiz                       1:0.5.5~gi 1:0.5.5~gi OpenGL window and compositing
compiz-core                  1:0.5.5~gi 1:0.5.5~gi OpenGL window and compositing
compiz-fusion-plugins-extra  0.5.2+git2 0.5.2+git2 Collection of extra plugins f
compiz-fusion-plugins-main   0.5.2-0ubu 0.5.2-0ubu Collection of plugins from Op
compiz-fusion-plugins-unoffi 0.0.2~git2 <none>     Collection of UNOFFICIAL fusi
compiz-gnome                 1:0.5.5~gi 1:0.5.5~gi OpenGL window and compositing
compiz-plugins               1:0.5.5~gi 1:0.5.5~gi OpenGL window and compositing
compizconfig-settings-manage 0.5.2+git2 0.5.2+git2 Compiz configuration settings
libcompizconfig-backend-gcon 0.5.2+git2 0.5.2+git2 Settings library for plugins 
libcompizconfig0             0.5.2-0ubu 0.5.2-0ubu Settings library for plugins 
python-compizconfig          0.5.2-0ubu 0.5.2-0ubu Compiz configuration system b
gavin@gblaptop:~$ 
```

Thanks,


Gavin,

---

### Post by dougfractal on 2007-08-30
Somethings still not right about your packages. It as if your sources.list hasn't updated.

I followed this guide [http://fosswire.com/2007/08/11/compizfusion-updated-guide-for-ubuntu-704/](http://fosswire.com/2007/08/11/compizfusion-updated-guide-for-ubuntu-704/)

note there is an typo,  missing *
> sudo apt-get --purge remove compiz* libcompizconfig*****

this is what my  **sudo apt-get install compiz compizconfig-settings-manager** looks like
> The following extra packages will be installed:
  compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
  python-compizconfig
The following NEW packages will be installed
  compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-gnome compiz-plugins compizconfig-settings-manager
  libcompizconfig-backend-gconf libcompizconfig0 python-compizconfig
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 3814kB of archives.
After unpacking 14.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  compiz-core compiz-plugins libcompizconfig0 libcompizconfig-backend-gconf
  compiz-gnome compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz
  python-compizconfig compizconfig-settings-manager
Install these packages without verification [y/N]? y
Get: 1 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main compiz-core 1:0.5.2-0ubuntu3~ppa4 [186kB]
Get: 2 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main compiz-plugins 1:0.5.2-0ubuntu3~ppa4 [277kB]
Get: 3 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main libcompizconfig0 0.5.2-0ubuntu1~ppa2 [52.2kB]
Get: 4 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main libcompizconfig-backend-gconf 0.5.2+git20070813-0ubuntu1~ppa1 [31.1kB]
Get: 5 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main compiz-gnome 1:0.5.2-0ubuntu3~ppa4 [168kB]
Get: 6 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main compiz-fusion-plugins-main 0.5.2-0ubuntu2~ppa1 [508kB]
Get: 7 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main compiz-fusion-plugins-extra 0.5.2+git20070817-0ubuntu1~ppa1 [2046kB]
Get: 8 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main compiz 1:0.5.2-0ubuntu3~ppa4 [29.5kB]
Get: 9 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main python-compizconfig 0.5.2-0ubuntu1~ppa1 [27.9kB]
Get: 10 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main compizconfig-settings-manager 0.5.2+git20070814-0ubuntu1~ppa1 [488kB]
Fetched 3814kB in 7s (477kB/s)                                                 
Selecting previously deselected package compiz-core.
(Reading database ... 232832 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_1%3a0.5.2-0ubuntu3~ppa4_i386.deb) ...
Selecting previously deselected package compiz-plugins.
Unpacking compiz-plugins (from .../compiz-plugins_1%3a0.5.2-0ubuntu3~ppa4_i386.deb) ...
Selecting previously deselected package libcompizconfig0.
Unpacking libcompizconfig0 (from .../libcompizconfig0_0.5.2-0ubuntu1~ppa2_i386.deb) ...
Selecting previously deselected package libcompizconfig-backend-gconf.
Unpacking libcompizconfig-backend-gconf (from .../libcompizconfig-backend-gconf_0.5.2+git20070813-0ubuntu1~ppa1_i386.deb) ...
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.5.2-0ubuntu3~ppa4_i386.deb) ...
Selecting previously deselected package compiz-fusion-plugins-main.
Unpacking compiz-fusion-plugins-main (from .../compiz-fusion-plugins-main_0.5.2-0ubuntu2~ppa1_i386.deb) ...
Selecting previously deselected package compiz-fusion-plugins-extra.
Unpacking compiz-fusion-plugins-extra (from .../compiz-fusion-plugins-extra_0.5.2+git20070817-0ubuntu1~ppa1_i386.deb) ...
Selecting previously deselected package compiz.
Unpacking compiz (from .../compiz_1%3a0.5.2-0ubuntu3~ppa4_all.deb) ...
Selecting previously deselected package python-compizconfig.
Unpacking python-compizconfig (from .../python-compizconfig_0.5.2-0ubuntu1~ppa1_i386.deb) ...
Selecting previously deselected package compizconfig-settings-manager.
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.5.2+git20070814-0ubuntu1~ppa1_all.deb) ...
Setting up compiz-core (0.5.2-0ubuntu3~ppa4) ...
Setting up compiz-plugins (0.5.2-0ubuntu3~ppa4) ...
Setting up libcompizconfig0 (0.5.2-0ubuntu1~ppa2) ...

Setting up libcompizconfig-backend-gconf (0.5.2+git20070813-0ubuntu1~ppa1) ...
Setting up compiz-gnome (0.5.2-0ubuntu3~ppa4) ...

Setting up compiz-fusion-plugins-main (0.5.2-0ubuntu2~ppa1) ...
Setting up compiz-fusion-plugins-extra (0.5.2+git20070817-0ubuntu1~ppa1) ...
Setting up compiz (0.5.2-0ubuntu3~ppa4) ...
Setting up python-compizconfig (0.5.2-0ubuntu1~ppa1) ...
Setting up compizconfig-settings-manager (0.5.2+git20070814-0ubuntu1~ppa1) ...


---

### Post by michael37 on 2007-08-30
> **gavinjb said:**
> Not sure if it was uninstalling the driver etc... with -purge or making the changes to xorg.conf, but Xgl seems to be working now 
Gavin,
I wage this was the driver change.

[quote=gavinjb]
I re-enabled Amaranth repo and update manager gave me a whole host of compiz updates, so it looks like I am back on his Compiz.

Here is a list of the compiz packages[/quote]
The 0.5.5 compiz packages come from Trevino (download.tuxfamily.org).  Remove his repos from your **/etc/apt/sources.list** and then run **sudo apt-get update**.

---

### Post by gavinjb on 2007-08-31
> 
The 0.5.5 compiz packages come from Trevino (download.tuxfamily.org). Remove his repos from your /etc/apt/sources.list and then run sudo apt-get update.


Last night I disabled these sources (I have not removed them completly yet), reloaded synaptic and then did an update, but as you can see from above it has kept some of these packages, would removing the repro completly make a difference?

Thanks,

---

### Post by Magneticgravity on 2007-08-31
When i click on 'Restricted Drivers Manager' it says 'Your hardware does not need any restricted drivers.'

Could i use this guide instead?
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by dougfractal on 2007-08-31
I've automated the guide [http://fosswire.com/2007/08/11/compizfusion-updated-guide-for-ubuntu-704/](http://fosswire.com/2007/08/11/compizfusion-updated-guide-for-ubuntu-704/)

1) activate sudo
```
sudo echo "activate sudo"
```

2) run script
```
sudo apt-get --purge remove compiz* libcompizconfig0 libdecoration0
sudo apt-get remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev
#sudo gedit /etc/apt/sources.list
# autofix sources.list
sudo sed -i '/3v1deb.*eyecandy/d' /etc/apt/sources.list   #  remove Treviño's Ubuntu Repository
sudo sed -i '/ppa.dogfood.launchpad.net\/amaranth/d' /etc/apt/sources.list  #  remove amaranth Ubuntu Repository
echo "# Amaranth compiz Ubuntu Repository  (unsigned)
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse" | sudo tee -a /etc/apt/sources.list   #   add amaranth Ubuntu Repository

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager
```

3) check install
```
aptitude search ~icompiz -F "%20p %10v %10V %20d"
```

4) run compiz
```

compiz --replace &
ccsm
```

4)  sort any probs
>prefeneces>reset to defaults
>General Option>Desktop Size> Horizontal Virtual Size>4

---

### Post by gavinjb on 2007-08-31
Removing and re-installing compiz seems to have fixed the problem, thanks for all the help to everyone.

One quick question, I have used an effect before (in KDE on a different distro), where when you move the cursor into the top right corner of the screen it shows all the windows you have open side by side and you can then click on one, does anyone know what this effect is called and how I can enable it.

---

### Post by dougfractal on 2007-08-31
**Magneticgravity**  I've looked at a few of your posts trying to find out what you have, but I ain't got a clue :confused:

run this script tell me what you've got
```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by dougfractal on 2007-08-31
> Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
these are used for video playback .  please re-enable.

> One quick question, I have used an effect before (in KDE on a different distro), where when you move the cursor into the top right corner of the screen it shows all the windows you have open side by side and you can then click on one, does anyone know what this effect is called and how I can enable it.
I know what you mean,  I can't find it. It may reappear in another update maybe.

---

### Post by michael37 on 2007-08-31
> **dougfractal said:**
> I know what you mean,  I can't find it. It may reappear in another update maybe.

It's called Scale Windows.

---

### Post by 3ark on 2007-08-31
Thank you so much for this. I have tried several times over the past month without success. I was starting to think it was impossible on my card (the seemingly infamous ATI 200M). I followed your guide and it worked great! Cheers. :)

---

### Post by michael37 on 2007-08-31
> **dougfractal said:**
> I've automated the guide [http://fosswire.com/2007/08/11/compizfusion-updated-guide-for-ubuntu-704/](http://fosswire.com/2007/08/11/compizfusion-updated-guide-for-ubuntu-704/)



Could you please add steps for uninstalling and reinstalling the libdecoration0 together with other compiz packages, esp since most people have issues with window decorations.

---

### Post by dougfractal on 2007-09-01
> **michael37 said:**
> Could you please add steps for uninstalling and reinstalling the libdecoration0 together with other compiz packages, esp since most people have issues with window decorations.

I'm unclear what you mean.
as those steps are already in.

---

### Post by zenrov on 2007-09-01
The instructions worked just fine, thank you :). But I seem to have a problem changing the settings. When i go to the "CompizConfig Setting Manager" and click on any of the options, the window disappears. The default animation stays active, but I can't seem to change the settings.

---

### Post by michael37 on 2007-09-01
> **dougfractal said:**
> I'm unclear what you mean.
as those steps are already in.

[http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217) does not have steps for uninstalling libdecoration

---

### Post by dougfractal on 2007-09-02
> **michael37 said:**
> [http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217) does not have steps for uninstalling libdecoration

Thanks for being persistent.   Added  libdecoration0 to the purge.

or here as single line 
```
sudo apt-get install --reinstall libdecoration0
```

---

### Post by shadycuz on 2007-09-02
I get an error

levi@levi-server:~$ sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
levi@levi-server:~$

---

### Post by [Alsharifi] on 2007-09-02
did u miss this step?

put this in your source list

```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

---

### Post by shadycuz on 2007-09-02
> **'[Alsharifi] said:**
> did u miss this step?

put this in your source list

```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Nope, double and trippled check, and ill even do it again =)

What else could be the problem? hmm.. btw I have had linux for less then a week.

---

### Post by shadycuz on 2007-09-02
> **'[Alsharifi] said:**
> did u miss this step?

put this in your source list

```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

I ran the update command but I only copyied the end so you could see that it is finding the eye cand packages

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages
Fetched 11B in 1s (11B/s)
Reading package lists... Done
levi@levi-server:~$ sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
levi@levi-server:~$ sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
levi@levi-server:~$         

any sugestions?

---

### Post by dougfractal on 2007-09-02
There are several different paths to  Compiz install that don't mix.


This one is for Amaranth repo and removes Treviño's.
*Amaranth is the ubuntu CF maintainer. Treviño is a CF pioneer who brings much to ubuntu. But i recommend Amaranth.*


> **dougfractal said:**
> I've automated the guide [http://fosswire.com/2007/08/11/compizfusion-updated-guide-for-ubuntu-704/](http://fosswire.com/2007/08/11/compizfusion-updated-guide-for-ubuntu-704/)

1) activate sudo
```
sudo echo "activate sudo"
```

2) run script
```
sudo apt-get --purge remove compiz* libcompizconfig0 libdecoration0
sudo apt-get remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev
#sudo gedit /etc/apt/sources.list
# autofix sources.list
sudo sed -i '/3v1deb.*eyecandy/d' /etc/apt/sources.list   #  remove Treviño's Ubuntu Repository
sudo sed -i '/ppa.dogfood.launchpad.net\/amaranth/d' /etc/apt/sources.list  #  remove amaranth Ubuntu Repository
echo "# Amaranth compiz Ubuntu Repository  (unsigned)
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse" | sudo tee -a /etc/apt/sources.list   #   add amaranth Ubuntu Repository

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager
```

3) check install
```
aptitude search ~icompiz -F "%20p %10v %10V %20d"
```

4) run compiz
```

compiz --replace &
ccsm
```

4)  sort any probs
>prefeneces>reset to defaults
>General Option>Desktop Size> Horizontal Virtual Size>4

---

### Post by mindtrick on 2007-09-02
Thanks I've successfully installed Compiz Fusion but I cannot change my theme with Emerald theme manager. I see the theme list and the previews but themes do not change when I click on them. Is there any other way to change themes, or did the process change. I haven't used Emerald for a long time.

---

### Post by michael37 on 2007-09-02
> **mindtrick said:**
> Thanks I've successfully installed Compiz Fusion but I cannot change my theme with Emerald theme manager. I see the theme list and the previews but themes do not change when I click on them. Is there any other way to change themes, or did the process change. I haven't used Emerald for a long time.

I suspect you may not be using emerald! Try running
```

ps -ef | grep -i emerald

```
to convince yourself that emerald process is actually running.

If not, run 
```

emerald --replace

```

---

### Post by wsx123 on 2007-09-02
I can't get into restricted drivers.

---

### Post by shadycuz on 2007-09-02
UPDATE!

I got xgl and compiz working right. I was playing around for a couple of hours. So I started onto my next task, running cs:s in wine. It crashed so i rebooted.

Now when i login on my gnome xsession i get a error about being logged in 10 secs and what not.

Here is my xsession crash file. Please help =(

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "levi"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/levi-server:/tmp/.ICE-unix/29789

(gnome-session:29789): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(gnome-panel:29855): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Initializing gnome-mount extension
Window manager warning: Log level 16: Unable to locate theme engine in module_path: "murrine",

(nautilus:29856): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(nm-applet:29895): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
/usr/bin/restricted-manager:243: GtkWarning: Unable to locate theme engine in module_path: "murrine",
  xml = gtk.glade.XML("/usr/share/restricted-manager/manager.glade")

(update-notifier:29875): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(search:29872): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
evolution-alarm-notify-Message: Setting timeout for 78456 1188864000 1188785544
evolution-alarm-notify-Message:  Mon Sep  3 20:00:00 2007

evolution-alarm-notify-Message:  Sun Sep  2 22:12:24 2007

Debug: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1875 (alarm_queue_init)
alarm-queue.c:218 (queue_midnight_refresh) - Refresh at Mon Sep  3 20:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/levi/.evolution/calendar/local/system 
alarm-notify.c:456 (alarm_notify_add_calendar) file:///home/levi/.evolution/calendar/local/system - Calendar Open Async... 0x6bcac0
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:456 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x6c46a0
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/levi/.evolution/tasks/local/system 
alarm-notify.c:456 (alarm_notify_add_calendar) file:///home/levi/.evolution/tasks/local/system - Calendar Open Async... 0x6c9620
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/levi/.evolution/memos/local/system 
alarm-notify.c:456 (alarm_notify_add_calendar) file:///home/levi/.evolution/memos/local/system - Calendar Open Async... 0x6d2a60
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x6cb690: Received at thread 44048940
alarm-queue.c:2008 (alarm_queue_add_async) - 0x6c46a0
alarm-queue.c:560 (load_alarms_for_today) - From Sun Sep  2 22:12:26 2007
 to Sun Sep  2 22:12:26 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6cb690: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/levi/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/levi/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/levi/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2057 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x6c0330: Received at thread 44048940
alarm-queue.c:2008 (alarm_queue_add_async) - 0x6bcac0
alarm-queue.c:560 (load_alarms_for_today) - From Sun Sep  2 22:12:26 2007
 to Sun Sep  2 22:12:26 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6c0330: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x6d2f70: Received at thread 44048940
alarm-queue.c:2008 (alarm_queue_add_async) - 0x6c9620
alarm-queue.c:560 (load_alarms_for_today) - From Sun Sep  2 22:12:26 2007
 to Sun Sep  2 22:12:26 2007

alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6d2f70: Replied to GUI thread
alarm-notify.c:349 (alarm_msg_received) - 0x6c90e0: Received at thread 440Debug: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
Debug: Loading Beagle.Util.Conf+SearchingConfig from searching.xml

(evolution-alarm-notify:29889): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(gnome-cups-icon:29898): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(firefox-bin:29954): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(firefox-bin:29973): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(swiftfox-bin:29992): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(swiftfox-bin:29992): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(swiftfox-bin:29992): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(swiftfox-bin:29992): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(swiftfox-bin:29992): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(swiftfox-bin:29992): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(nautilus:30248): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(gedit:30266): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
```

---

### Post by wsx123 on 2007-09-03
> **dougfractal said:**
> There are several different paths to  Compiz install that don't mix.


This one is for Amaranth repo and removes Treviño's.
*Amaranth is the ubuntu CF maintainer. Treviño is a CF pioneer who brings much to ubuntu. But i recommend Amaranth.*


i tried the above and below is the message 
i received
manny@manny-laptop:~$ ccsmChecking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity
Tried reinstalling, now if I try to logout and change session to gnome with xgl I get a plain desktop background and nothing loads-then the login screen comes back up. If I log in using gnome I get the option to use 4 desktops in 2D in the lower right screen area?

---

### Post by dougfractal on 2007-09-03
Tell me about your setup
```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by Paches363 on 2007-09-03
Im getting the same problem others have been getting, were i log out and log back in, Gnome with XGL and the screen has the default login wallpaper and it dose that for a couple sec then goes back to the log in screen. Nothing happens when i login on normal Gnome . Im useing an AMD system with a X1600 ATI card. can anyone point me in the right direction?

---

### Post by wsx123 on 2007-09-03
file is attached, if that ones not right let me know-there is another also.

---

### Post by gundumfx on 2007-09-03
well  how did this make my desktop shiny

---

### Post by dougfractal on 2007-09-03
wsx123
your card is ATI Technologies Inc Radeon Mobility M6 LY  don't use Xgl.
You are under 9500 threshhold for the fglrx driver.
> **Vaan said:**
> Many thanks [dougfractal]("http://ubuntuforums.org/member.php?u=230202")! I now have direct rendering working again. Everything is back like it used to be, desktop effects and everything.

This makes me wonder if your solution will help out the others in this thread.


Okay if you have an ATi card below the 9500 series (such as the 9200) then try and follow these steps and let us know your results.

Open up a terminal window and type these commands:
```

sudo apt-get remove fglrx*
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri

```After you've finished running the previous commands type this in your console/terminal window:
```

sudo dpkg-reconfigure xserver-xorg

```The blue xerver configuration should show up. For the x server driver select **ati**. Next just continue to follow the directions (when you get to the screen resolution area make sure to select your resolution(s) using the spacebar, when done press enter) and after it's all done press **ctrl alt backspace** to restart the X11 display.

After you login back to the desktop open up a terminal window again. Type in:
```

glxinfo

```Near the top you should see something that says:
```

direct rendering: YES/NO

```It should say Yes. If it says No that means either something went wrong, or this solution did not work for you.

If it is Yes, then your display driver should be configured properly and you can enable Desktop Effects and play your games and such.

---

### Post by dougfractal on 2007-09-03
Paches363 need to see your errors

try and login  Xgl(fails)
[ctrl+alt+f1]
**cat .xsession-errors | head -150 > xglerrors.txt**
[ctrl+alt+f7]
login  and post xglerrors.txt

---

### Post by wsx123 on 2007-09-03
Well I made it up to the point of hitting ctrl alt backspace, then I get error messages failed to load. Now my computer won't boot up. I'm at a black screen that made it up to running local boot scripts-OK and it's stuck there.I used all the default settings.

---

### Post by cldmello on 2007-09-03
I dont know how many were able to follow these steps without a glitch, but to me it seems like there is a step missing in the how-to which kinda didnt work for me. I use an AMD64 version of Feisty Fawn and we need some modification to the step that updates the sources. 

For Feisty/AMD64: 

Add the following lines to the /etc/apt/sources.list file:

> deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64

Note the post-fix amd64. 

After that, run the following commands on the terminal:

> gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add - 

Now, you can continue with the How-To as above and you should be good :)

- Colin

---

### Post by wsx123 on 2007-09-03
I'm thinking fresh Ubuntu install and forget the Desktop effects=I have tried several posts to get this to work and none turn out well.

---

### Post by dougfractal on 2007-09-03
wsx123,  did you boot into session "Gnome" or "Gnome with Xgl" ?
I don't think you card works with xgl.


I notice in your xorg.0.log  it looks as if agp X1
add **Option          "AGPMode"        "4"** 

looking at [http://www.free3d.org/](http://www.free3d.org/)  someone had 857 fps  wqith radeon driver
Xorg should autodetect the best settings but you can false them

sudo nano /etc/X11/xorg.conf
```
Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility M6 LY"      
        Driver          "ati"
        Option          "AGPMode"        "8"  # 1  2 4
        Option          "AccelMethod"    "XAA" #either XAA or EXA. only "XAA" is supported for some of the cards with "experimental" 3d acceleration
        Option          "ColorTiling"    "on"
        Option          "EnablePageFlip" "true" #only works with accelmethod "XAA"
 #       Option          "AccelDFS"       "true" #seemed to speed things up using EXA acceleration
  #      Option          "TripleBuffer"   "true" #This *might* help if you use something like Beryl and have slow video playback.
 #       Option          "DynamicClocks"  "on"   #This is for laptop users, it saves energy when in battery mode.

  #      Option          "DMAForXv"       "true" #This can speed up movie playback but can in rare cases case instability
        Option          "GARTSize"       "64"   #This is the size of the "GART" that xorg will use.
        Option "NoAccel" "false"    
        BusID           "PCI:1:0:0"

```EndSection

---

### Post by Paches363 on 2007-09-03
> **dougfractal said:**
> Paches363 need to see your errors

try and login  Xgl(fails)
[ctrl+alt+f1]
**cat .xsession-errors | head -150 > xglerrors.txt**
[ctrl+alt+f7]
login  and post xglerrors.txt


It dosent give me enough time to type in the ca .xsession..... stuff infact i have to do my login then it will go back to the log in screen then when i log in again and do the Alt Crtl F1 i have to then put in my password or half of it before it restarts again. is there any way of lengthening the time it gives me to input all my stuff and the command?

*edit also the  Ctrl alt F7 thing did nothing*

---

### Post by danhm on 2007-09-04
I was running Beryl perfectly (using this same howto, but from awhile back), until I decided to install Compiz-Fusion. Anyway, upon trying to use Fusion, it won't work. There aren't any borders around the windows if I select Emerald (in beryl-manager), and if I revert back to GTK Window Decorator, Compiz freezes if has to do an effect (such as woobly windows). If I try to use Beryl, same thing. I guess my driver went crazy somewhere, because it's trying to do stuff on the wrong screen.

```

dan@dan-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)

dan@dan-laptop:~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: ATI Mobility Radeon X1400

```

How do I tell it to use :1.0 for direct rendering? Will that fix it? If not, what do I have to do?

---

### Post by dougfractal on 2007-09-04
Paches363 need to see your errors

try and login  Xgl(fails)
returns to login screen
[ctrl+alt+f1]   #  go to CLI
login in text ver.
**cat .xsession-errors | head -150 > xglerrors.txt**
[ctrl+alt+f7]    #  back to GUI
login  and post xglerrors.txt

---

### Post by dougfractal on 2007-09-04
danhm Tell me about your setup

This script collects loads of info about your setup then tarballs it.

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by danhm on 2007-09-04
> **dougfractal said:**
> danhm Tell me about your setup

This script collects loads of info about your setup then tarballs it.

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)


Here are my results.

---

### Post by wsx123 on 2007-09-04
I never had an option to reboot. I tried turning off and on, The video is all messed up and I get an error that the x server failed to load-it is not detecting my screen,mouse etc....and It won't boot up.

---

### Post by dougfractal on 2007-09-04
wsx123  I'm sorry its gone belly up.

Options 1)  Install Gutsy, with your card it should starts straight into CF  (Gusty is Beta ware)

2)  [ctrl-alt+F1]
login
sudo dpkg-reconfigure xserver-xorg 
sudo reboot

3)  here is a testx script which allows you to expeirment with a copy of xorg.conf
[http://ubuntuforums.org/showpost.php?p=3157811&postcount=167](http://ubuntuforums.org/showpost.php?p=3157811&postcount=167)

---

### Post by ramasdf123 on 2007-09-04
For some reason, I only have one desktop!, plugins seem to be working but not the 4 desktops.  some1 help?

---

### Post by markdjones82 on 2007-09-04
Hey guys everything was working fine and then my OS updated at one point.  After reboot, I tried to load Desktop with XGL and it is all jumbled on login.  The screen has horizontal lines all over it and I am unsure what happened.  I think fglrx may have updated, but I'm unsure.  I can login without XGL and everything looks fine.  It just seems my XGL broke.  Anyone able to help?  Please send me a PM if you can assist.  Thanks.

I am  running an ATI 1650 Pro and everything ran fine until the update.

---

### Post by Paches363 on 2007-09-04
> **dougfractal said:**
> Paches363 need to see your errors

try and login  Xgl(fails)
returns to login screen
[ctrl+alt+f1]   #  go to CLI
login in text ver.
**cat .xsession-errors | head -150 > xglerrors.txt**
[ctrl+alt+f7]    #  back to GUI
login  and post xglerrors.txt

Nothing happened and i typed it exactly as you put it. but i did get into that part where i have no time limit. Is it creating the Text file somewhere other than the desktop?

---

### Post by MrBlack88 on 2007-09-04
I am a total linux newbie who decided to try Ubuntu because of 2 things.  The cool looking xgl effects, and I'm fed up with Windows Vista.  I've got Ubuntu 7.04 installed using this guide 

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) 

and then tried using this guide 

[http://ubuntuforums.org/showthread.php?t=488385&highlight=ati](http://ubuntuforums.org/showthread.php?t=488385&highlight=ati) 

to get xgl installed.  That part was successful and I was able to turn on desktop effects under System > Preferences.  But when I try to install Beryl or Compiz-fusion that's when the problems start.  This has been my 4th attempt.  I've tried a couple of other how-to guides to no avail.  

Here's my system information:

AMD Turion 64 Mobile Technology MT-32 1.80GHz

1GB PC3200 RAM

100GB 5400 RPM NB HD

ATI RX480M +ATI SB 400 chipset

RADEON x700 GPU W/128MB VRAM

I don't know what the following information means but I hope it's helpful. 

> Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility X700 (PCIE)"
--
Section "Device"
        Identifier      "aticonfig-Device[0]"
--
        Option          "Composite"     "0"
EndSection


> Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700
OpenGL version string: 1.2 (2.0.6334 (8.34.8))
OpenGL extensions:


> (==) AIGLX enabled
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering


> 
ii  compiz                                     0.5.5~git20070904+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070904+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2~git20070902+3v1ubuntu1           Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-main                 0.5.2~git20070903+3v1ubuntu1           Collection of Compiz Fusion plugins for Comp
ii  compiz-gnome                               0.5.5~git20070904+3v1ubuntu0           OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.5~git20070904+3v1ubuntu0           OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20070903+3v1ubuntu0          Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig0                           0.5.2~git20070904+3v1ubuntu0           Settings library for plugins - Compiz Fusion
ii  libdecoration0                             0.5.5~git20070904+3v1ubuntu0           Compiz window decoration library
ii  python-compizconfig                        0.5.2~git20070903+3v1ubuntu0           Python bindings for the Compiz Configuration

Any help would be much appreciated.  Thanks.

---

### Post by vincentvee on 2007-09-04
still having problems.....beryl-manager is installed but when i select beryl window manager it fails and falls back to metacity
anyone know why??

---

### Post by dynamethod on 2007-09-05
well ive done everything, ive got beryl all running but.... its made absolutly no difference in terms of special effects to the desktop, and like the last post when i try select window manager and try beryl, it just flickers a bit then go's back to the metacity.... absolutley stuck

ive got a samsung syncmaster 931 B @1280x1024
ATI Radeon X800 XT 256mb


im totally stuck :S

i got this too

compiz --replace -c emerald
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

??

---

### Post by ignignokt00 on 2007-09-05
Thanks for the howto, worked perfectly :)

---

### Post by dougfractal on 2007-09-05
> **MrBlack88 said:**
> I am a total linux newbie who decided to try Ubuntu because of 2 things.  The cool looking xgl effects, and I'm fed up with Windows Vista.  I've got Ubuntu 7.04 installed using this guide 

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) 

and then tried using this guide 

[http://ubuntuforums.org/showthread.php?t=488385&highlight=ati](http://ubuntuforums.org/showthread.php?t=488385&highlight=ati) 

to get xgl installed.  That part was successful and I was able to turn on desktop effects under System > Preferences.  But when I try to install Beryl or Compiz-fusion that's when the problems start.  This has been my 4th attempt.  I've tried a couple of other how-to guides to no avail.  

Here's my system information:

AMD Turion 64 Mobile Technology MT-32 1.80GHz

1GB PC3200 RAM

100GB 5400 RPM NB HD

ATI RX480M +ATI SB 400 chipset

RADEON x700 GPU W/128MB VRAM

I don't know what the following information means but I hope it's helpful. 
.

Thanks for giving useful info.


Edit:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/136598](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/136598)
from this it seems that a script has been included to start Xgl automatically. 
check
> cat /etc/X11/Xsession.d/00xserver-xgl_start-server
ls /etc/X11/Xsession.d/
So no need to use "gnome XGL"  

If you want the old way back
> sudo mv /etc/X11/Xsession.d/00xserver-xgl_start-server /etc/X11/Xsession.d/15xserver-xgl_start-server
END


You card is supported by the open source ATI driver [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
```

sudo echo "activate  sudo"
```

```
sudo apt-get remove xorg-driver-fglrx xserver-xgl

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-glx xserver-xorg-video-ati
#sudo rm /etc/X11/Xsession.d/00xserver-xgl_start-server && touch /etc/X11/Xsession.d/00xserver-xgl_start-server   # i'm unsure about this bit
sudo dpkg-reconfigure xserver-xorg
```

This should take  your xorg.conf back to start.

```
sudo reboot
```

your computer should reboot , then login to the normal "Gnome" session.


start compiz
```
compiz --replace &
ccsm
```

If this works can you post the new **xinfo.tgz**
if it doesn't ... sorry.





sudo

---

### Post by Apothysis on 2007-09-05
When I input this as the second final command for installing Compiz Fusion according to this guide;
> sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes
I get the following from my Terminal;
> Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070904+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
What should I do?

Nevermind I just got past that. However, when I run "compiz --replace" I get;
> Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
I ran this command because I just logged in and out but the effects aren't working.

---

### Post by dougfractal on 2007-09-05
Apothysis
whats your card info

use script found here

[http://ubuntuforums.org/showpost.php?p=3306728&postcount=251](http://ubuntuforums.org/showpost.php?p=3306728&postcount=251)

---

### Post by Apothysis on 2007-09-05
> **dougfractal said:**
> Apothysis
whats your card info

use script found here

[http://ubuntuforums.org/showpost.php?p=3306728&postcount=251](http://ubuntuforums.org/showpost.php?p=3306728&postcount=251)

Do you want the .tar-file?

To put it simple, I've got an ATI Mobility X1400.

Edit: Could this have anything to do with the fact that I cannot run Desktop Effects? It says that the composite extention isn't available.

---

### Post by dougfractal on 2007-09-05
Apothysis grep "AIGLX error" /var/log/Xorg.0.log
> (EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
this seems to be a common error of the last few days.

There has been an update to xserver-xgl that makes startxgl.sh obsolete.

You have a good setup and frame rate don't do anything drastic.

try the "gnome" session ** not **"xgl" at login

---

### Post by Apothysis on 2007-09-05
> **dougfractal said:**
> Apothysis grep "AIGLX error" /var/log/Xorg.0.log

this seems to be a common error of the last few days.

There has been an update to xserver-xgl that makes startxgl.sh obsolete.

You have a good setup and frame rate don't do anything drastic.

try the "gnome" session ** not **"xgl" at login

I just began using Ubuntu. How do I make it run Gnome again instead of XGL?

---

### Post by dougfractal on 2007-09-05
> **Mr Greencastle said:**
> 
Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close.

edit: *  sorry I was rushing around, I put in the wrong quote.*

 Logout, click sessions and chose GNOME

---

### Post by Apothysis on 2007-09-05
> **dougfractal said:**
> if you have a file ......

Read your edit. I did what you said, still get the same error, no effects.

---

### Post by dougfractal on 2007-09-05
> **Apothysis said:**
> I removed everything inside the files, seeing as how they were empty from the start. I still get the same error, and no effects.

from apothysisxinfo/xgl.txt
> /usr/share/xsessions/xgl.desktop
[Desktop Entry]
Encoding=UTF-8
Name=**GNOME with XGL**
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application


-rwxr-xr-x 1 root root 219 2007-09-05 19:13 /usr/local/bin/startxgl.sh
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie
exec dbus-launch --exit-with-session gnome-session"

you emptied these?  

sudo mv /usr/share/xsessions/xgl.desktop /usr/share/xsessions/xgl.desktop.old

Logout, click sessions and chose GNOME

---

### Post by Apothysis on 2007-09-05
> **dougfractal said:**
> from apothysisxinfo/xgl.txt


you emptied these?  

sudo mv /usr/share/xsessions/xgl.desktop /usr/share/xsessions/xgl.desktop.old

Logout, click sessions and chose GNOME
Same thing. :( It couldn't have anything to do with drivers could it? I have the ones that came with the installation disk (or perhaps it came with the updates, but yeah I haven't downloaded the latest from ATi).

---

### Post by dougfractal on 2007-09-05
The thing is you have direct rendering and 4000+FPS glxgears, so I don't think its a driver thing.

You can disable AIGLX and the compositing extension by amending your /etc/X11/xorg.conf like this:. 

> echo 'Section "ServerFlags" 
      Option "AIGLX" "off" 
EndSection' | sudo tee -a /etc/X11/xorg.conf

restart x


In the next few day fglrx 8.41 will be released which has significant improvements for many cards.
[http://www.phoronix.com/scan.php?page=article&item=821&num=1](http://www.phoronix.com/scan.php?page=article&item=821&num=1)

---

### Post by PPPP on 2007-09-05
Believe it or not, I breezed through all 28 pages of this thread hoping I can find some help. 

My problem is that I don't have the titlebar of my windows.  All the effects are there but I can't move windows by dragging the titlebar because it's not there.  I have emerald running.    I don't think I ran across anyone who posted here that have a definitive way of solving the titlebar missing phenomenon? 

I have attached the tar.gz.

Oh forgot to mention I'm using amaranth's repo:
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse

---

### Post by Apothysis on 2007-09-06
> **dougfractal said:**
> The thing is you have direct rendering and 4000+FPS glxgears, so I don't think its a driver thing.

You can disable AIGLX and the compositing extension by amending your /etc/X11/xorg.conf like this:. 



restart x


In the next few day fglrx 8.41 will be released which has significant improvements for many cards.
[http://www.phoronix.com/scan.php?page=article&item=821&num=1](http://www.phoronix.com/scan.php?page=article&item=821&num=1)

Is it supposed to work now? Because I still get the same error. Could it have anything at all to do with my Desktop Effects not booting up? Isn't it supposed to be enabled?

---

### Post by Jadd on 2007-09-06
Thanks for this guide, now desktop effects finally work!

I did have one problem though, log out all of a sudden gave me a blank black screen, and the computer became unresponsive. Solution (found elsewhere): System -> Administration -> Login window, check Restart the Xserver with each login.

Oh, and to make sure the cube enables properly, before enabling desktop effects, right-click on your workspace switcher, click properties, and changer number of workspaces to 4.

---

### Post by Apothysis on 2007-09-06
Okay, so I'm trying Beryl now. It installed fine, but when I run GNOME with XGL (session), it gets stuck. It tries to load it but then everything just goes down, or not working. And when I run in regular gnome I have no borders. Why?

I'm not abled to get to the desktop in Gnome with XGL simply. But when I run regular Gnome, and attempt "beryl-manager", I get this;

> **************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

The thing that caught my attention is "Checking for non power of two texture support: failed".

Edit: Okay now this is really pissing me off. I noticed that Desktop Effects uninstalled itself, so I installed it again (along with the compiz additions), but it won't work. When I hit "Enable Desktop Effects", it loads for a short while and then gives me "Desktop Effects failed to load". This happends on both Gnome XGL and regular. Although I can barely read what happends in Gnome XGL, the screen is all wavy and blurred, impossible to read, but I got my way to Desktop Effects.

And, what is this thing with the texture support? It seems to want something with GLX, but that's an Nvidia-function. I have ATi Mobility Radeon X1400.

---

### Post by rhart211 on 2007-09-06
Okay, so thanks for the great tutorial. I was able to get compiz to work on my laptop that has a ATI Moblity Radeon X300. However, if I logout and log back in, the screen is covered with a bunch of lines, similar to the problems that are decribed by a lot poeple. However, if I restart the computer, and log in, I don't have this problem.
What do I have to do fix the logout and log back in problem?
Thanks

---

### Post by hiebert on 2007-09-06
I'm trying to use this guide, but it seems like i can't update my drivers anymore. I'm allways getting this error message

```
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

It happens with Synaptic and with "add/remove" too.. Could someone help me?

I asked the same question in this thread [http://ubuntuforums.org/showthread.php?t=542975](http://ubuntuforums.org/showthread.php?t=542975) but I'm getting nothing ](*,)

---

### Post by vincentvee on 2007-09-06
this worked for me, but if you wanna hear the story then read on
used this tutorial, had to set session default to gnome XGL, but still had problems, i decided that after i got home from work i would use the method from the docs pages.
anyways, got home from work booted the thing and all of a sudden the install started to work as expected....dunno why it just worked so i'm leavin it as it is, anyone have any idea why it wouldn't work at first?

---

### Post by parradux on 2007-09-06
This screwed everything up. How would I go about removing this thing in its entirety?

---

### Post by dougfractal on 2007-09-07
> **PPPP said:**
> Believe it or not, I breezed through all 28 pages of this thread hoping I can find some help. 

My problem is that I don't have the titlebar of my windows.  All the effects are there but I can't move windows by dragging the titlebar because it's not there.  I have emerald running.    I don't think I ran across anyone who posted here that have a definitive way of solving the titlebar missing phenomenon? 


I've found that this problem can be caused by a ccsm error


**ccsm**
>preferences>reset to defaults
>General Option>Desktop Size> Horizontal Virtual Size>4


You also have the "(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)"  in your Xorg.0.log

 [https://bugs.launchpad.net/ubuntu/+s...gl/+bug/136598](https://bugs.launchpad.net/ubuntu/+s...gl/+bug/136598)
from this it seems that a script has been included to start Xgl automatically.
check
**cat /etc/X11/Xsession.d/00xserver-xgl_start-server**
So no need to use "gnome XGL"

If that script is there Xgl will start by selecting "Gnome" session at login.

If you then choose to select "Gnome with Xgl" you will be launching Xgl twice.

---

### Post by dougfractal on 2007-09-07
> **Apothysis said:**
> Okay, so I'm trying Beryl now. It installed fine, but when I run GNOME with XGL (session), it gets stuck. It tries to load it but then everything just goes down, or not working. And when I run in regular gnome I have no borders. Why?

You are almost there
I've found that this problem can be caused by a ccsm error

ccsm
>preferences>reset to defaults
>General Option>Desktop Size> Horizontal Virtual Size>4
>+++++ anything else you want




> **Apothysis said:**
> 
I'm not abled to get to the desktop in Gnome with XGL simply. But when I run regular Gnome, and attempt "beryl-manager", I get this;

The thing that caught my attention is "Checking for non power of two texture support: failed".

Edit: Okay now this is really pissing me off. I noticed that Desktop Effects uninstalled itself, so I installed it again (along with the compiz additions), but it won't work. When I hit "Enable Desktop Effects", it loads for a short while and then gives me "Desktop Effects failed to load". This happends on both Gnome XGL and regular. Although I can barely read what happends in Gnome XGL, the screen is all wavy and blurred, impossible to read, but I got my way to Desktop Effects.

And, what is this thing with the texture support? It seems to want something with GLX, but that's an Nvidia-function. I have ATi Mobility Radeon X1400.
[B]
Desktop Effects[/B] was part of the original April feisty install superseded by CF.
Stick with CF.

Its odd that you get the AIGLX thing.

---

### Post by Apothysis on 2007-09-07
Okay, I finally got Compiz Fusion and Emerald running! However, if you look at the attached image, you will see what I am talking about. Also, I have got the wrong keyboard format running (It is supposed to be 105 se but its running 101 us), how do I adjust this?

Also, I just noticed that when I run emerald --replace my computer laggs out and the terminal gives me several copies of the same error.
> (emerald:25126): Wnck-WARNING **: Unhandled action type (nil)
If I just exit the terminal all my borders dissapear and emerald does not work.

---

### Post by PPPP on 2007-09-07
> **dougfractal said:**
> I've found that this problem can be caused by a ccsm error


**ccsm**
>preferences>reset to defaults
>General Option>Desktop Size> Horizontal Virtual Size>4


You also have the "(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)"  in your Xorg.0.log

 [https://bugs.launchpad.net/ubuntu/+s...gl/+bug/136598](https://bugs.launchpad.net/ubuntu/+s...gl/+bug/136598)
from this it seems that a script has been included to start Xgl automatically.
check
**cat /etc/X11/Xsession.d/00xserver-xgl_start-server**
So no need to use "gnome XGL"

If that script is there Xgl will start by selecting "Gnome" session at login.

If you then choose to select "Gnome with Xgl" you will be launching Xgl twice.

Thanks a lot dougfractal! Changing the settings in ccsm did it!  But now emerald doesn't seem to be working because I can't change theme.  No matter which one i choose the title bar stays the same.  The effects are there though.  How do I get it to work? 

I'm sure emerald is running:ps -ef|grep emerald
23240 23134  0 23:28 ?        00:00:00 emerald --replace
23343     1 28 23:28 ?        00:00:14 emerald-theme-manager -i
23419 23395  0 23:29 pts/0    00:00:00 grep emerald

Also, I'm not sure how to change this within ccsm.  If i have a few windows opened, if I click on the back one, there is an animation of the windows sliding.  How do I change it/turn it off?

Edit:
Animations plugin, Focus Effect. -> changed to wave

and reloaded emerald with "emerald --replace&"...but is there are more permanent fix where I don't have to run this command each time I want to make a change in the theme?

---

### Post by ortwein on 2007-09-08
I think my machine is recognizing my old Intel integrated graphics (my newer card, and the one I'm using now, is an ATI)  Thus, each time I select system...administration....restricted drivers manager, it tells me my hardware doesn't need any restricted drivers...so how do I change my settings over to the ATI card?

---

### Post by dougfractal on 2007-09-08
> **ortwein said:**
> I think my machine is recognizing my old Intel integrated graphics (my newer card, and the one I'm using now, is an ATI)  Thus, each time I select system...administration....restricted drivers manager, it tells me my hardware doesn't need any restricted drivers...so how do I change my settings over to the ATI card?

you might have to set it in the Bios.

lspci -nn | grep -i vga

---

### Post by hristo on 2007-09-08
if someone is kind enough to take time out of their day to help me, step by step, figure out how to install XGL, that would be awesome. im new to linux ubuntu, just installed it by myself last weekend. i got beryl to work all by myself, but im getting stuck on XGL. i have an ATI video card. im almost 100% sure that XGL will work on my system... i just need a step by step analysis of how to get that done.  

thank you in advance : )

---

### Post by dougfractal on 2007-09-08
Supported Cards [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)
ie Cards newer than 9200

I'm making this guide because I have seen many people lately with problems installing  Compiz Fusion with Xgl. I have taken some parts of other guides and have also contributed my own parts, just to make things easier. 

If you follow each step carefully (mostly copy/paste), I guarantee you'll be going with desktop effects in no time!
[B]
Guide:[/B]

After installing Feisty, make sure your system is completely updated. Paste this into a terminal:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

First step is getting your drivers set up. To do this use the Restricted Driver Manager.

[B]
System >> Administration >> Restricted Drivers Manager[/B]

Enable your ATI driver (By clicking the little box) and let it do its thing. After a reboot there should be an icon (small and green) in the notification area telling you that you have restricted modules loaded.

Now we need to install XGL.
```
sudo apt-get install xserver-xgl
```
Good now, XGL won't load on its own so we need to write a few scripts to have it start.
DO NOT DO THIS IN GUTSY xgl starts by default when xserver-xgl is installed

```
echo "Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie=\"\$(xauth -i nextract - :0 | cut -d ' ' -f 9)\"
xauth -i add :1 . \"\$cookie\"
exec dbus-launch --exit-with-session gnome-session" | sudo tee /usr/local/bin/startxgl.sh
sudo sed -i -e "1i#!/bin/sh" /usr/local/bin/startxgl.sh
sudo chmod a+x /usr/local/bin/startxgl.sh
#Now we need to make a way to start that session from your login menu
echo "[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application" | sudo tee /usr/share/xsessions/xgl.desktop
```

END GUTSY NOTICE

**COMPIZ FUSION**

Then copy paste in:
```

echo 'deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse\n' | sudo tee -a /etc/apt/sources.list
```

You will need to update again, so paste into a terminal:
```
sudo apt-get update
```
Now to install Compiz-Fusion  CompizConfig-Settings-Manager Emerald window decorator paste this into a terminal:

```
sudo apt-get install compiz compizconfig-settings-manager emerald
```

AND VOILA! It is installed

Test compiz
```
compiz --replace &
```
or
**[Alt]+[F2] compiz --replace**

Now add this as two separate entries in the startup sessions:

**System >> Preferences >> Sessions**

Click 'new' and make its name: Compiz
And make its command: **compiz --replace**

And make one more:
Name: Emerald
Command: **emerald --replace**

Now **Reboot **, then log back in, and BOOM! Shiny desktop effects!


Hope that helped!


(Thanks Mr Green, this is almost a direct copy [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385))

[B]
Quick Guide:[/B]

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install xorg-driver-fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.ati
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
echo 'Section "ServerFlags" 
\tOption "AIGLX" "off"
EndSection' | sudo tee -a /etc/X11/xorg.conf
sudo apt-get install xserver-xgl
echo "Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie=\"\$(xauth -i nextract - :0 | cut -d ' ' -f 9)\"
xauth -i add :1 . \"\$cookie\"
exec dbus-launch --exit-with-session gnome-session" | sudo tee /usr/local/bin/startxgl.sh
sudo sed -i -e "1i#!/bin/sh" /usr/local/bin/startxgl.sh
sudo chmod a+x /usr/local/bin/startxgl.sh
#Now we need to make a way to start that session from your login menu
echo "[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application" | sudo tee /usr/share/xsessions/xgl.desktop
echo 'Section "Extensions"
    Option "Composite" "0"
EndSection' sudo tee -a /etc/X11/xorg.conf    # is this necessary?
echo 'deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
deb-src http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse\n' | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install compiz compizconfig-settings-manager emerald

echo "Reboot: sudo reboot"
```

**Revert to Xorg driver**

If (for any reason) the fglrx install fails, you can revert to the Xorg driver by executing

```
sudo apt-get remove xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
sudo dpkg-reconfigure xserver-xorg
#and selecting the "ati" driver,
```

Removing Xgl
```
sudo apt-get remove xserver-xgl
sudo rm /usr/share/xsessions/xgl.desktop /usr/local/bin/startxgl.sh
```

---

### Post by dougfractal on 2007-09-08
> **Apothysis said:**
> Okay, I finally got Compiz Fusion and Emerald running! However, if you look at the attached image, you will see what I am talking about. Also, I have got the wrong keyboard format running (It is supposed to be 105 se but its running 101 us), how do I adjust this?

>> System >> preferences >> keyboard

Strange display
can you send a new ******xinfo.tar.gz


> **Apothysis said:**
> Also, I just noticed that when I run emerald --replace my computer laggs out and the terminal gives me several copies of the same error.
If I just exit the terminal all my borders dissapear and emerald does not work.

emerald --replace&
or [alt]+[F2] emerald --replace

---

### Post by hristo on 2007-09-08
when i go to System >> Administration >> Restricted Drivers Manger   i get a window that says ¨Your hardware does not need any restricted drivers.¨

what does that mean?

---

### Post by Apothysis on 2007-09-08
> **dougfractal said:**
> >> System >> preferences >> keyboard

Strange display
can you send a new ******xinfo.tar.gz

The screenshot I attached shows the issue off more. This is what I see after fire painting "example" on my desktop. The trails look like particles, don't they? Same thing with the cube animation. I see trails after the cube, like how I moved it and such.

---

### Post by hiebert on 2007-09-08
> **dougfractal said:**
> I've found that this problem can be caused by a ccsm error


**ccsm**
>preferences>reset to defaults
>General Option>Desktop Size> Horizontal Virtual Size>4


You also have the "(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)"  in your Xorg.0.log

 [https://bugs.launchpad.net/ubuntu/+s...gl/+bug/136598](https://bugs.launchpad.net/ubuntu/+s...gl/+bug/136598)
from this it seems that a script has been included to start Xgl automatically.
check
**cat /etc/X11/Xsession.d/00xserver-xgl_start-server**
So no need to use "gnome XGL"

If that script is there Xgl will start by selecting "Gnome" session at login.

If you then choose to select "Gnome with Xgl" you will be launching Xgl twice.

I don't understand this ccsm thing.. (sorry, I'm new to ubuntu) Could you explain it for me? I'm not getting the titlebars and when i enable my desktop effects at 
system > preferences > desktop effects  all my workspaces disappear.. I'm getting the effects, but i got no titlebar as i mentioned before.. I'm starting with "gnome with xgl" session

---

### Post by PPPP on 2007-09-09
> **hiebert said:**
> I don't understand this ccsm thing.. (sorry, I'm new to ubuntu) Could you explain it for me? I'm not getting the titlebars and when i enable my desktop effects at 
system > preferences > desktop effects  all my workspaces disappear.. I'm getting the effects, but i got no titlebar as i mentioned before.. I'm starting with "gnome with xgl" session

I think what he meant was go to Applications -> Accessories -> Terminal.  Then type in ccsm.

From there you can do the setting he suggested.  That got my titlebar back :)

---

### Post by dougfractal on 2007-09-09
**Apothysis**

I think you might have a Treviño's packages.  switch  to Amaranth 

*Amaranth is the ubuntu CF maintainer. Treviño is a CF pioneer who brings much to ubuntu. But i recommend Amaranth.*

please visit this guide
[http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)

Your FPS is down. I notice you've installed the latest fglxr drivers,  with 8.34 your where getting 4000+ FPS (glxgears is a crude benchmark test)

please add AIGLX OFF to xorg.conf
> echo 'Section "ServerFlags" 
\tOption "AIGLX" "off"
EndSection' | sudo tee -a /etc/X11/xorg.conf

**hiebert**> I don't understand this ccsm thing.. (sorry, I'm new to ubuntu) 
I use terminal most of the time, its quick easy and precise.  Just **drag my code into terminal**.I uses >>Applications>>Example  type  format to indicate a GUI action. 
So drag Applications -> Accessories -> Terminal into your Top Panel for easy use.
[Alt]+[F2] == quick run

---

### Post by Apothysis on 2007-09-09
> **dougfractal said:**
> **Apothysis**

I think you might have a Treviño's packages.  switch  to Amaranth 

*Amaranth is the ubuntu CF maintainer. Treviño is a CF pioneer who brings much to ubuntu. But i recommend Amaranth.*

please visit this guide
[http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)

Your FPS is down. I notice you've installed the latest fglxr drivers,  with 8.34 your where getting 4000+ FPS (glxgears is a crude benchmark test)

please add AIGLX OFF to xorg.conf

I had my hopes up for this, but still! The same thing, wow this sucks. :(

---

### Post by dougfractal on 2007-09-09
It may be that you have a very special card.
or you just mucked up the install some how.  It can be very annoying when thing don't work.
I can only help if you keep sending updated data (****xinfo.tar.gz)  you can ofcourse just  give up and wait for Gutsy next month.

---

### Post by Apothysis on 2007-09-09
Yeah :( Though if it doesn't work with Gutsy I might just go nuts and pay for a new card.. :(

---

### Post by ironflippy on 2007-09-10
> **thecobraeffect said:**
> I just installed xgl+compiz fusion on my computer, but now my resolution is only 1024x768. It was 1680x1050 before. My xorg.conf didn't change at all. Any ideas?

Here's my xorg.conf for reference.
```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes	"1680x1050" "1024x768"	"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes	"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes	"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes	"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes	"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes	"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

I'm also getting this problem (same video card, the 9800pro). Did you figure out how to fix it? Here's my xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"6 7"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"7"
	Option		"ButtonMapping"		"1 2 3 4 5 6 7"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Radeon 9800Pro"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"AOC Spectrum"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9800Pro"
	Monitor		"AOC Spectrum"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by ayhuna on 2007-09-10
[QUOTE=Apothysis;3314929]When I input this as the second final command for installing Compiz Fusion according to this guide;

I get the following from my Terminal;

What should I do?

Nevermind I just got past that. However, when I run "compiz --replace" I get;

How did you get past the above error?

---

### Post by Apothysis on 2007-09-10
> **ayhuna said:**
> [QUOTE=Apothysis;3314929]When I input this as the second final command for installing Compiz Fusion according to this guide;

I get the following from my Terminal;

What should I do?

Nevermind I just got past that. However, when I run "compiz --replace" I get;

How did you get past the above error?
If I remember correctly I removed the packages completely from the list (because I had "old" packages on the computer) in Synaptic Package Manager. Thus I was allowed to re-download them again and install them successfully. At least that's what I think I remember.

Also, I just got past my error. It's not a permanent solution, but more of a way that makes it work, and I no longer get those rips all over the screen. What I did was that I used the Fire Painting tool, sized it down to "0.100" which made it impossible to see. And as long as the effect stayed there (and since it can't be seen, it doesn't annoy me), everything flowed on perfectly. :D But once I deleted the fire painting (with Shift + Super + C) the image almost made me threw up, pixelboxes everywhere. :D

---

### Post by Wilden on 2007-09-12
Did all this, got compwiz working, except now Azureus wont work now. It loads up, opens the window, then disappears, I have no idea why. Help would be appreciated.

---

### Post by dougfractal on 2007-09-12
> **Wilden said:**
> Did all this, got compwiz working, except now Azureus wont work now. It loads up, opens the window, then disappears, I have no idea why. Help would be appreciated.

[B]
Compiz Fusion for ATI cards + Xgl in Feisty? [/B] better to start a new thread

---

### Post by dbkungfu on 2007-09-13
phew almost execute ...

sudo apt-get remove xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx
sudo dpkg-reconfigure xserver-xorg
#and selecting the "ati" driver,

as suggested by dougfractal

after 2 days of struggling with the distorted lines in gnome xgl on my new ATI x9150, I resolved it by installing the xorg fglrx driver using synapsis. Initial installed the AMD release driver 8.4x, *damn it*

my system , AM2 dual core, ATI x1950 pro 256mb, samsung 19", MSI K9N ultra (570 chipset)

---

### Post by cncf1985 on 2007-09-17
Thank you, I have been trying to get this working for a while and it has all started to come to life.  Thanks

---

### Post by nystud162 on 2007-09-21
> **cor2y said:**
> It works somewhat on my system although i thought it wasn't working because it took compiz fusion a while to load.
Also Emerald Themes do not work for me i can't switch to a new theme.
I don't know why.

Im not sure if you can do this with compiz fusion, but install beryl manager in the terminal.

I had the same problem on my Presario V2000.

```
sudo apt-get install beryl-manager
```
Press alt-F2 and run beryl manager.
if your window manager changes just switch back over to compiz by right clicking on the red diamond on the upper right hand side of your screen and going to select window manager. Then go to the emerald theme manager by right clicking on the red diamond. Then choose your theme you want to switch over to (it wont work). Then finally, right click on the red diamond again and reload the Window Decorator and your new theme should be displayed. You have to do this everytime that you want to change your theme.

---

### Post by playami on 2007-09-21
Sorry  but  i get this error messege

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extensio

Waht  do i do ?

---

### Post by TedGarvin on 2007-09-22
Thank you.  This guide worked great for my rig.  This was my 5th try at Compiz-Fusion and I was removing it from my system when I ran across your guide and gave it one last try.  Now I have no crashes, I have titlebars all the time, and it runs at startup.  Great job.

EDIT:  3 seconds after I wrote this, Compiz crashed, so I  put a launcher right on a panel, so I can get it going again quickly.

---

### Post by meindian523 on 2007-09-22
> **adwatkin19 said:**
> Hiya, this worked like a dream, i now have the uber coolness of the cube to help me switch between my desktops and my tasks, thank you so much. 

Just a quick question, how can i look at and alter the settings for this: e.g. i have heard you can put a picture on the background of the cube for when it is rotating.

thanks for any help and MASSIVE thanks for the HOW TO

Adwatkin19

Dunno whether adwatkin is still watching this thread,but here goes.....

you can put a pic in the background of the rotating cube by opening CCSM

System>>Preferences>>CCSM

Open the desktop cube plugin dialog,open the appearance tab and click on skydome,provide the path to the image you want as the background to the rotating cube and VOILA!The background image you are talking about is officially called the skydome,BTW.....8)

---

### Post by WolfLust on 2007-09-22
Did everything this topic mentioned, after I re-logged in the graphics  are slow, and I lost my windows' borders.
clicking on CompizConfiguration Settings Manager doesn't start it.
typing ccsm in the terminal gives me: 

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'



The only way I got my windows borders was by doing: metacity --replace
which gave me:
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


Any advice?

---

### Post by dougfractal on 2007-09-22
**playam  & WolfLust**

Can you run my script so that I can see more about you card.
run this script. (copy and paste into terminal)
```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)


**meindian523**  the ATi Radeon XPRESS 200M Series gives many people diffuclty can you  send me also your script output cheers ;-)

---

### Post by WolfLust on 2007-09-22
Thank you for the fast reply.
kindly find the attached file to this message below.

---

### Post by dougfractal on 2007-09-22
source.list
> # compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

you have  Treviño's and amaranth's :-(  Choose only one. I recomend  amaranth.

rememmber to purge compiz the reinstall

I have an update howto here.
[http://ubuntuforums.org/showpost.php?p=3332218&postcount=288](http://ubuntuforums.org/showpost.php?p=3332218&postcount=288)

Xorg.0.log
> (EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

```
echo 'Section "ServerFlags" 
\tOption "AIGLX" "off"
EndSection' | sudo tee -a /etc/X11/xorg.conf
```


If this fixes it can you send the updated xinfo.tgz

---

### Post by WolfLust on 2007-09-22
Ok i removed:

# compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

now what?

it is all really too slow.

---

### Post by WolfLust on 2007-09-22
How do I purge?

So what I need to do is to apt-get update
purge
re-install and restart?

---

### Post by dougfractal on 2007-09-22
For compiz 
read this to purge the old
[http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)


Have restarted X as you should have DRI now? 
check logs with

> cat /var/log/Xorg.0.log | grep "(EE)" 

checK DRI
with 
> glxinfo | head -4

---

### Post by WolfLust on 2007-09-22
I did what's posted on the link, and now X wouldn't start.

I did the revert to x steps and got it up again, but the windows borders still don't show.

I re-attached the zip in case it's helpful.

Please help.

---

### Post by WolfLust on 2007-09-22
glxinfo | head -4
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI

cat /var/log/Xorg.0.log | grep "(EE)"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom


I will read the purging topic now and update. Thanks for the reply.

---

### Post by dougfractal on 2007-09-22
Ok your in ati driver mode.

Did this 
> sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install xorg-driver-fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.ati
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
echo 'Section "ServerFlags" 
\tOption "AIGLX" "off"
EndSection' | sudo tee -a /etc/X11/xorg.conf

or this step 
> First step is getting your drivers set up. To do this use the Restricted Driver Manager.


System >> Administration >> Restricted Drivers Manager

Enable your ATI driver (By clicking the little box) and let it do its thing. After a reboot there should be an icon (small and green) in the notification area telling you that you have restricted modules loaded.
break X

aptitude search ~icompiz
> compiz                       1:0.5.5~gi 1:0.5.5~gi OpenGL window and compositing
compiz-core                  1:0.5.5~gi 1:0.5.5~gi OpenGL window and compositing
compiz-fusion-plugins-extra  0.5.2+git2 0.5.2+git2 Collection of extra plugins f
compiz-fusion-plugins-main   0.5.2+git2 0.5.2+git2 Collection of plugins from Op
compiz-gnome                 1:0.5.5~gi 1:0.5.5~gi OpenGL window and compositing
compiz-plugins               1:0.5.5~gi 1:0.5.5~gi OpenGL window and compositing

You still have a miss match  should all be   0.5.2+gi....

errors in sources.list
sudo gedit /etc/apt/sources.list

remove duplicates
> deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse\n
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse\n

Your original fglrx looked fine you where just missing the
> Section "ServerFlags" 
\tOption "AIGLX" "off"
EndSection' 
in  /etc/X11/xorg.conf


sgnlfive  has a similar setup to you
unfortuntly I don't think he's using compiz just WoW.
 [http://ubuntuforums.org/showpost.php?p=3398799&postcount=31](http://ubuntuforums.org/showpost.php?p=3398799&postcount=31)

**sudo synaptic** is a useful tool for sorting out packages

But you not far off.

---

### Post by WolfLust on 2007-09-22
I think I fixed the duplicate in resources issue, anything left that I can do to fix it?

Thank you again

---

### Post by dougfractal on 2007-09-22
Are you

up to date
**apt-get update** 
**apt-get upgrade**
enabled your fglrx card
grep fglrx /etc/X11/xorg.conf
glxinfo | head -4

if yes
how is your 
cat /etc/X11/xorg.conf

Just try the changes and keep sending your xinfo.tgz

do you have a backup for xorg.conf.
(your be pleased to know that the Gutsy has the thing called BulletProofX so that X never fails.

---

### Post by WolfLust on 2007-09-22
Well at least ccsm is now opening, none of the plugins are working though.

glxinfo | head -4
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI


I also attached my xorg.conf file.

Thank you so much for your support.

---

### Post by WolfLust on 2007-09-22
One more thing, when I do: sudo apt-get upgrade 

I get:

Need to get 0B/185kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  compiz-core
Install these packages without verification [y/N]? y
(Reading database ... 141222 files and directories currently installed.)
Preparing to replace compiz-core 1:0.5.2+git20070829-0ubuntu1amaranth1 (using .../compiz-core_1%3a0.5.2+git20070829-0ubuntu1amaranth1_i386.deb) ...
Unpacking replacement compiz-core ...
Setting up compiz-core (0.5.2+git20070829-0ubuntu1amaranth1) ...

But nothing happens, it says in the updates list, and it doesn't seem to install it

---

### Post by dougfractal on 2007-09-22
> packages cannot be authenticated amaranth what's to make it clear that they are not official feisty release.


Why no fglrx?

What is really interesting is that you have DRI with an "ati" driver ;-) 

what happens
compiz --replace &

metacity --replace &  # to return to gnome

---

### Post by WolfLust on 2007-09-22
I tried ompiz --replace & and lost all my window borders

metacity --replace & # returned me to gnome as you said.

what can I do to make it happen? :s

---

### Post by dougfractal on 2007-09-22
You are almost there
I've found that this problem can be caused by a ccsm error

**ccsm**
>preferences>reset to defaults
>General Option>Desktop Size> Horizontal Virtual Size>4
>+++++ anything else you want

---

### Post by WolfLust on 2007-09-22
restart or compiz --replace to test if that works? 

thank you for your patience

---

### Post by Talthalra on 2007-09-22
I get this message

E: Couldn't find package compizconfig-settings-manager

When I run this portion

sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes


Any ideas?

---

### Post by dougfractal on 2007-09-23
**WolfLust**
> restart or compiz --replace to test if that works? 
  i'm unclear wht you mean.

I recomend just trying things out.
just be more careful if you use **sudo** commands 

[B] 
Talthalr[/B]a  can you post the xinfo.tgz output from this script.
[http://ubuntuforums.org/showpost.php?p=3408855&postcount=310](http://ubuntuforums.org/showpost.php?p=3408855&postcount=310)

---

### Post by WolfLust on 2007-09-23
Nothing works yet, I still get no window borders unless I do: metacity --replace

and I still have compiz-core amaranth cannot be authenticated.

Any advice please?

---

### Post by dougfractal on 2007-09-23
here some things to try, even to repeat.

**ccsm**
>preferences>reset to defaults
>General Option>Desktop Size> Horizontal Virtual Size>4
>+++++ anything else you want

> Window Decoration :Enable

sudo apt-get install emerald
emerald --replace &

gtk-window-decorator --replace &

sudo apt-get install --reinstall libdecoration0


also see
and try these earlier posts

sudo apt-get install compizconfig-settings-manager
sudo apt-get install --reinstall libwnck*
sudo apt-get install --reinstall libdecoration0

---

### Post by haZZe08 on 2007-09-24
i got this code in terminal

Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070921+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close.

cant find it in there

---

### Post by Holy Knight on 2007-09-24
Does this HOWTO apply to Kubuntu?

---

### Post by stalinheredia on 2007-09-24
I did everything and it went through fine, but when i try to execute "compiz --replace" it gives me this error..
 compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

Please help. I will really appreciate your help. Thanks in advance

---

### Post by meindian523 on 2007-09-24
> **dougfractal said:**
> **playam  & WolfLust**

**meindian523**  the ATi Radeon XPRESS 200M Series gives many people diffuclty can you  send me also your script output cheers ;-)
Sorry for late reply,but here.....

---

### Post by dougfractal on 2007-09-24
**haZZe08  **

I recommend amaranth repos
[http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)

to sort out apt-get 
try **sudo apt-get remove compiz-gnome**

report the whole log if this fails

DO NOT DO THIS IN GUTSY xgl starts by default when xserver-xgl is installed

Code:

> echo "Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie=\"\$(xauth -i nextract - :0 | cut -d ' ' -f 9)\"
xauth -i add :1 . \"\$cookie\"
exec dbus-launch --exit-with-session gnome-session" | sudo tee /usr/local/bin/startxgl.sh
sudo sed -i -e "1i#!/bin/sh" /usr/local/bin/startxgl.sh
sudo chmod a+x /usr/local/bin/startxgl.sh
#Now we need to make a way to start that session from your login menu
echo "[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application" | sudo tee /usr/share/xsessions/xgl.desktop

END GUTSY NOTICE

---

### Post by dougfractal on 2007-09-24
**meindian523**  Thanks.
 ____________________________

> **Holy Knight said:**
> Does this HOWTO apply to Kubuntu?

If you follow this 
[http://ubuntuforums.org/showpost.php?p=3332218&postcount=288](http://ubuntuforums.org/showpost.php?p=3332218&postcount=288)
**>> Quick Guide**

then do this

```
sudo sed -i -e 's/dbus-launch --exit-with-session gnome-session/startkde/' /usr/local/bin/startxgl.sh
```


In other word replace **dbus-launch --exit-with-session gnome-session** with **startkde** in the /usr/local/bin/startxgl.sh

---

### Post by S.S.S.P5 on 2007-09-25
i get to here...

First step is getting your drivers set up. To do this use the Restricted Driver Manager.

Code:

System >> Administration >> Restricted Drivers Manager

and the terminal says that ...

bash: System: command not found


help!!! im getting frusterated, ive been working on this for a week!!!! aaargh radeon rv280

---

### Post by dougfractal on 2007-09-25
GUI menu
**not** command line
System >> Administration >> Restricted Drivers Manager

---

### Post by techno-wiz on 2007-09-29
> **Talthalra said:**
> I get this message

E: Couldn't find package compizconfig-settings-manager

When I run this portion

sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes


Any ideas?

I have the same problem. I also don't see it in synaptic but I do see a gnome-compiz-manager. Should we install this one instead?

---

### Post by techno-wiz on 2007-09-29
I found the answer to this problem. This was on a Toshiba A215-S4697 laptop with a AMD Turion 64 processor. The compiz repository for amd64 needs to be "eyecandy-amd64" instead of just "eyecandy".

---

### Post by maluka on 2007-09-30
after i chose GNOME with XGL is get this error message:

> Xsession: unable to launch "/usr/bin/startxgl.sh" X Session --
"/usr/bin/startxgl.sh" not found ; falling back to default session

i have a Macbook Pro 2.16GHz Core Duo

edit: i'm using feisty!

---

### Post by Martje_001 on 2007-09-30
Thanx! My FPS is 12 times higher now :D

---

### Post by dougfractal on 2007-09-30
> **maluka said:**
> after i chose GNOME with XGL is get this error message:



i have a Macbook Pro 2.16GHz Core Duo

edit: i'm using feisty!

Edit:   you have a typo.
sudo gedit /usr/share/xsessions/xgl.desktop

change 
Exec=/usrl/bin/startxgl.sh
to
Exec=/usr/local/bin/startxgl.sh



[COLOR="Gray"]can you post the output
[B]ls -l  /usr/bin/startxgl.sh
cat /usr/bin/startxgl.sh
[/B]


should fix with  this
```
echo "Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie=\"\$(xauth -i nextract - :0 | cut -d ' ' -f 9)\"
xauth -i add :1 . \"\$cookie\"
exec dbus-launch --exit-with-session gnome-session" | sudo tee /usr/local/bin/startxgl.sh
sudo sed -i -e "1i#!/bin/sh" /usr/local/bin/startxgl.sh
sudo chmod a+x /usr/local/bin/startxgl.sh
```[/COLOR]

---

### Post by maluka on 2007-09-30
thanks for coming back so quickly!

there is no type unfortunately. i get:

> Exec=/usr/local/bin/startxgl.sh

after ls -l /usr/bin/startxgl.sh
cat /usr/bin/startxgl.sh i get:

> maluka@ubuntu:~$ ls -l /usr/bin/startxgl.sh
-rwxr-xr-x 1 root root 129 2007-09-25 03:44 /usr/bin/startxgl.sh
maluka@ubuntu:~$ cat /usr/bin/startxgl.sh
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session
maluka@ubuntu:~$ 


---

### Post by dougfractal on 2007-09-30
> **maluka said:**
> thanks for coming back so quickly!

there is no type unfortunately. i get:


ls -l /usr/share/xsessions/
cat /usr/share/xsessions/x*.desktop

---

### Post by maluka on 2007-09-30
i get:

> maluka@ubuntu:~$ ls -l /usr/share/xsessions/
total 20
-rw-r--r-- 1 root root 2948 2007-04-11 04:53 gnome.desktop
-rw-r--r-- 1 root root 3932 2007-09-25 19:32 kde.desktop
-rw-r--r-- 1 root root  148 2007-01-28 18:30 openbox.desktop
-rwxr-xr-x 1 root root  115 2007-09-30 16:40 xgl.desktop
-rw-r--r-- 1 root root  115 2007-09-30 16:33 xgl.desktop~
maluka@ubuntu:~$ cat /usr/share/xsessions/x*.desktop
[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application


---

### Post by OliverN on 2007-09-30
thank you so much for all of this. I had this working until I decided to try the new ati drivers. Big mistake, I realize that now. I used Envy to download and install, but when logging into my xgl session, my screen looked like [this]("http://www.flickr.com/photos/9439659@N07/1436448830/").
So I uninstalled the drivers and I uninstalled Envy, but after repeating your how-to my xgl session still looks mashed up!

This is probably why: When I try to update after adding tuxfamily to my sources list, my terminal tells me it can't fetch the package because [COLOR="Red"]zip2: (stdin) is not a bzip2 file.[/COLOR] and [COLOR="Red"]the sub-process bzip2 returned an error code(2)[/COLOR]
What to do about that? As you can tell, I haven't got all that much experience with ubuntu.

---

### Post by carloslosgrande on 2007-10-01
[FONT="Comic Sans MS"]I've been trying off and on to get this stuff working since Feisty came out. Never had any luck.
Got a friend onto Ubuntu and his laptop had the cube spinning around on his first attempt. Aaarrgh.

Today, I saw this, a bit of mucking about and, at last, I have a spinning cube!
Thank you for a very simple and easy to use (just like me) HowTo.:guitar:
> compiz --indirect-rendering --replace -c emerald gets me some borders.

But basically I've got the basics and now I'll play around with getting the rest, I hope.

btw, I've got an ATI Radeon X600 PCI card.
Previously whenever I enabled 'restricted drivers' it killed OpenOffice, not now.:)

oh, I had to run the install commands a few times before I got all the repos in. Especially with this added to end > --fix-missing[/FONT]

---

### Post by M.G. on 2007-10-01
> **Mr Greencastle said:**
> *Edit: Forgot to mark this as a HOWTO, and I don't know how to change it, so...*

I'm making this guide because I have seen many people lately with problems installing Beryl or Compiz Fusion with Xgl. I have taken some parts of other guides and have also contributed my own parts, just to make things easier. (Many thanks to lamalex, as I have used that guide countless times to get Feisty boxes running Beryl)

If you follow each step carefully (mostly copy/paste), I guarantee you'll be going with desktop effects in no time!

**Guide:**

After installing Feisty, make sure your system is completely updated. Paste this into a terminal:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

First step is getting your drivers set up. To do this use the Restricted Driver Manager.

```
System >> Administration >> Restricted Drivers Manager
```

Enable your ATI driver (By clicking the little box) and let it do its thing. Once finished , reboot the computer and make sure fglrx loaded correctly. There should be an icon (small and green) in the notification area telling you that you have restricted modules loaded.

Now we need to install XGL.

```
sudo apt-get install xserver-xgl
```

Good now, XGL won't load on its own so we need to write a few scripts to have it start.

```
sudo gedit /usr/local/bin/startxgl.sh
```

Now copy and paste this into the file that pops up:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

**SAVE THIS FILE!** Once its done saving, make that fire executable (like a program) by pasting this into a terminal:

```
sudo chmod a+x /usr/local/bin/startxgl.sh
```

Now we need to make a way to start that session from your login menu, paste this into a terminal:

```
sudo gedit /usr/share/xsessions/xgl.desktop
```

And paste this into the file:

```

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

Now make this script executable by pasting this into a terminal:

```
sudo chmod a+x /usr/share/xsessions/xgl.desktop
```

Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close.

The first thing we need to do is add the security key, do this by pasting into a terminal:

```

sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

Then type in:

```
sudo gedit /etc/apt/sources.list
```

This will open a file, add this to the very bottom by pasting:
```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Then save and exit.

You will need to update again, so paste into a terminal:

```
sudo apt-get update
```

[SIZE="4"]BERYL[/SIZE]
If you want Compiz Fusion - skip ahead to the Compiz Fusion section.

Now to install Beryl (and Emerald window decorator)  paste this into a terminal:

```
sudo apt-get install beryl beryl-manager beryl-core beryl-plugins beryl-settings emerald emerald-themes
```

AND VOILA! Beryl is installed, to start it simply paste this into a terminal:

```
beryl-manager
```

You may need to change the window manager, do this by right-clicking the beryl icon and selecting Beryl from the 'Select Window Manager' menu.

Then you're all set! Oh and don't forget to add this to your startup:

```
system > preferences > sessions
```

Click on 'New' and type in 'Beryl' (without quotes) for the name, and for the command type: 'beryl-manager' (again without quotes)


[SIZE="4"]COMPIZ FUSION[/SIZE]
Start by pasting this into a terminal:

```
sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes
```

AND VOILA! It is installed, add this as two separate entries in the startup sessions:
```

System >> Preferences >> Sessions
```

Click 'new' and make its name: Compiz
And make its command: compiz --replace

And make one more:
Name: Emerald
Command: emerald --replace

Now just logout, then log back in, and BOOM! Shiny desktop effects!


Hope that helped!


Mr Green

=====================================================

OK... It had been a while that I've been trying to reinstall Beryl or Compiz and everytime I had different issues. This forum helped a lot. First I did have some problems with Beryl, such as losing window's borders when I run Beryl or Compiz wouldn't do anything no matter I used it with --replace or other options. But when I logged on to my laptop this morning everything started working fine !!!! I hope it stays like this.... Thanks again... U :guitar:

---

### Post by carloslosgrande on 2007-10-01
[FONT="Comic Sans MS"]When I restarted this morning it was back to not working, so I ran > compiz --replace -c emerald and it all came back.:)
I've now changed the sessions command to reflect this and I'll see if that works.

Also, is it possible to have more than 4 sides on the cube?
Some apps can't be resized (frostwire) - how to fix?
I liked the borders I had prior to this, is there any way I can have them back?:([/FONT]

---

### Post by miteshanand1729 on 2007-10-01
if i install both compiz and beryl then can it create a problem..???

---

### Post by benlooi on 2007-10-03
Hi all!

Thanks for all the info sharing. This is a great forum which is helpful to all who come in. Just thought I give something back, though it's a small contribution.

I was having little success in getting compiz fusion to work on my Dell Vostro 1000. Followed the instructions to a "T" and yet still hitting walls. some errors I get are:
handler already registered...blah blah blah = "org"
compizconfig-settings-manager not found.

Surfed the web and finally after hours of trying the problem lies in my installed feisty. Its a amd64 version. So, those of you with the same amd64 linux do remember to add '-amd64" to the end of the source. I've cut and pasted the portion in the original howto below. Notice the last line. It should work.

**********
Then type in:


Code:
sudo gedit /etc/apt/sources.listThis will open a file, add this to the very bottom by pasting:

Code:
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64
***********

Good luck!

PS: I still have problems with XGL though. When I log off, I get a black screen and hangs. Have to hard-reboot before seeing the login screen again. No biggie.

ben
singapore

---

### Post by Gogleion on 2007-10-03
hello,

I am using an ati radeon x1650 Pro and amd 3200+ CPU and whenever I try to install beryl, it crashes.

---

### Post by Staind2b on 2007-10-04
Hello, I am completely new to Linux, and I need your help, please.

I'm trying to install ATI drivers using the "easy method". When I click on the restricted device manager it just comes up with the message "The hardware does not need any restricted drivers." I'm using a ATI Radeon X800 XL video card.

I've tried doing it the manual way, but when i try to start up Ubuntu after all the changes, a message comes up saying something to the effect of the X-server is configured incorrectly, and it shows me how it's been configured.

I'm running a virtual console using VMware Workstation 6. Does this make a difference compared to running ubuntu off of its own partition?

In short, is running ubuntu in the virtual console the reason why the restricted device manager comes up with that message, and the manual way of install the ATI drivers don't work?
If it's not then what is, and how do I fix this?

I want to try compiz fusion, but I need the drivers installed.  Any help will be greatly appreciated.

Thanks,

Staind2b

---

### Post by carloslosgrande on 2007-10-05
[FONT="Comic Sans MS"]Ok, putting  > compiz --indirect-rendering --replace -c emerald in sessions doesn't make any difference, I still need to do this in terminal every time I restart or login.

Also the windows thing is still the same. Terminal has a border, [COLOR="Blue"]none of the others do, which is a little annoying.[/COLOR].

I can resize some windows - VLC, sys monitor, files n folders, but others - web, Amarok, Frostwire, OpenOffice, Terminal, no way.

Cannot move an app from 1 window to another.

XGL uses quite a lot of cpu, average 10%, is that usual?

And I'd really like more than 4 windows as I always have more apps than that running at any one time. A cube has 6 sides, why not add the top and bottom to the standard spin list?

I'm wondering whether the compiz in Gutsy will resolve these issues?[/FONT]

---

### Post by Dark_X on 2007-10-05
> **Staind2b said:**
> Hello, I am completely new to Linux, and I need your help, please.

I'm trying to install ATI drivers using the "easy method". When I click on the restricted device manager it just comes up with the message "The hardware does not need any restricted drivers." I'm using a ATI Radeon X800 XL video card.

I've tried doing it the manual way, but when i try to start up Ubuntu after all the changes, a message comes up saying something to the effect of the X-server is configured incorrectly, and it shows me how it's been configured.

I'm running a virtual console using VMware Workstation 6. Does this make a difference compared to running ubuntu off of its own partition?

In short, is running ubuntu in the virtual console the reason why the restricted device manager comes up with that message, and the manual way of install the ATI drivers don't work?
If it's not then what is, and how do I fix this?

I want to try compiz fusion, but I need the drivers installed.  Any help will be greatly appreciated.

Thanks,

Staind2b

I have heard that this will not work on virtual consoles.  Also, are you using the drivers from the restricted drivers manager or downloading them from the ATI site?  I suggest that you avoid using the ones from their site.

---

### Post by mikoblink on 2007-10-06
i have notebook with amd x2 1.6, ati Xpress 1150 and 4G Ram.

i follow the step of this site:
[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)
 i followed the step and no error occur. but in the end my interface still be the same, no changing such as no cube, no blur, no water effect, etc. :(

i also conf the session to load on start up. but still cant run compiz. :confused :confused:

please help, thanks... :)

---

### Post by ebullient on 2007-10-08
Hopefully I didn't miss this if anyone had a similar problem.

Anyway, I'm running two monitors with big desktop.  Tried the how-to, tried various other fixes, and I still get this error when trying to log into XGL:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "landis"
/etc/gdm/Xsession: Beginning session setup...

Fatal server error:
no screens found

(gnome-session:15803): Gtk-WARNING **: cannot open display: 
```

I'm running Feisty on a 9800 Pro and fglrx is (should be) installed correctly.  Here is my xorg:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option      "VendorName" "ATI Proprietary Driver"
	Option      "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option      "VideoOverlay" "on"
	Option      "Enable PrivateBackZ" "yes"
	Option      "HSync2" "75"
	Option      "VRefresh2" "75"
	Option      "PairModes" "1280x1024+1024x768"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

I have a feeling that its the display number in the startup script, but I don't know where all to change it.  Either that or changing it doesn't work, I've tried changing it to Display=:0 according to the Xgl guide, this gets me into Gnome but xgl doesn't start (running compiz from the terminal shows the failed test: texture_from_pixmap support error).  I've tried changing every :1 to :0 and that doesn't seem to work either (same error when running compiz).  Note that I've attempted to run two monitors at different resolutions on this so if you see something related to that I've messed up I'm all ears.

Any help greatly appreciated.

---

### Post by skipb on 2007-10-08
Thanks! This worked perfectly for me.

---

### Post by zw0rk on 2007-10-08
I've done everything using this HOWTO. Compiz runs, i have dekstop effects.. But, if i try to start glx_gears - X hangs and i need to kill him with Ctrl-Alt-BS. And CPU load is about 60-90% every time i activate plugin (e.g. Cube, or dragging window and so on). Is this normal?

```

desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6747 (8.40.4)

m57@m57-desktop:~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 1.2 (2.0.6747 (8.40.4))

```

---

### Post by ebullient on 2007-10-08
I got it working, huzzah!

Now I still have problems.  Opening windows like terminal or firefox take far too long.  Seems like it opens it the old metacity way with the translucent sort of square that zooms out then the window is drawn, then draws it the compiz fusion way with any sort of animation you have setup (the window isn't actually drawn till the end of the animation).  Its annoying but liveable till I can fix it.  Update: It's only when I'm launching an app from a panel launcher object.  When launching from the menu or from the desktop it works fine.

The other thing is getting two monitors going.  I've done this with an nvidia card and you had to do it as one big desktop.  So far I've only been able to get dual head with two separate x-servers which doesn't work at all.

Finally, now my sound card doesn't work!

Pretty though.  If anyone has any thoughts, I'd appreciate it.

---

### Post by Dean_Harryman on 2007-10-09
I followed the steps, but when I get to where it says to log ot.... I get a solid black screen....and the only way to get back is to restart....

am I haveing a major problem? how do I fix?

I also get this error at the last terminal entry : E: Couldn't find package compizconfig-settings-manager

---

### Post by VoidOfNothingness on 2007-10-09
Just wanted to drop a line to say that this guide worked like a charm... Thanks a lot!:cool:

---

### Post by usmanlinux on 2007-10-10
first of all great guide..

just need some additonal guidence. i can get it all working with out using restricted drivers.. but when i do it with the restricted drivers i get nothing.

graphics are better when using the restricted drivers.. any insight?

i have a dell ispirion with a ati redeon x300 video PCI-express video. with 1.5gb memory.

thanks in advance.

---

### Post by winginit_118CL on 2007-10-10
I just want to start by saying thank you for writing this guide.  Very easy to read and understand, even as a Linux newbie like myself.  I began the process from step 1.  The XGL install went smoothly, but when I went to use ```
sudo gedit /usr/local/bin/startxgl.sh
``` I got the response ```
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

```

I am running an ATI Radeon Xpress 200m, I have the restricted drivers enabled.  From here, I am stuck since my Linux experience is extremely limited.  Any feedback/instructions/advice/insults would be greatly appreciated.

---

### Post by dougfractal on 2007-10-10
Upgrade to gutsy.  Its one week early but you will avoid the  rush.

CF is default. xgl starts by default if xserver-xgl is installed.

> sudo echo "activate sudo"
then
> 
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo upgrade-manager -d

[B]
winginit_118CL[/B]
Thats a strange error for root to have!
are you fully upto date?


> sudo apt-get upgrade && apt-get dist-upgrade

try this
> sudo -s
whoami    # should say root
gedit /usr/local/bin/startxgl.sh

That should work but upgrade to gutsy ;-)

---

### Post by Dynamo5565 on 2007-10-10
your guide was great!:) But how do you get beryl if you have compiz fusion ? thanks so much Dynamo

---

### Post by barkej on 2007-10-10
Thanks! This worked great.

---

### Post by winginit_118CL on 2007-10-10
Yep, I'm fully up to date, logged in as root and I still get the same result.  I'll upgrade to gutsy here in a bit and see if I can get everything to work under that.  Thanks for the suggestions.

---

### Post by carloslosgrande on 2007-10-12
[FONT="Comic Sans MS"]Updates have fixed my last outstanding problems. I now have window borders and can resize at will. Its also no longer necessary to enter 'compiz --replace -c emerald' in the terminal every restart.:)
to Mr Greencastle - a terrific howto!:guitar:
to Compiz - Beryl people - thanks very much.:guitar:

ATI Radeon X600 pci card running just fine[/FONT]

---

### Post by winginit_118CL on 2007-10-12
So I ended up getting through the procedure.  Went smooth and Beryl is apparently working.  A few display issues:

1. When I switch Beryl on as my window manager, all my window borders disappear.  Can't maximize, minimize, resize, etc.

2.  When entering text into this posting box, none of the text I type is displayed.  Had to switch back to Gnome window manager to post this.

Edit: Also tried switching managers to compiz, but that really slowed performance and produced several small graphical problems, i.e. small outllines of where closed windows once were.

Second edit: Disregard.  Rebooted and everything works as advertised.  I'm such a newbie, hahaha.  Thanks for the great guide!!

---

### Post by iLoVe.cF- on 2007-10-14
this works just amazing so far, thanks, :D

---

### Post by medcl on 2007-10-16
cools thx

---

### Post by barabuss on 2007-10-16
I know that Compiz Fusion is installed by default in Ubuntu 7.10, but I cannot find it in Kubuntu 7.10. How can I install it in Kubuntu?  Also, how do I install KDM theme manager?  I know these are probably easy questions for most people in these forums but I am very new to Linux and really need a step by step guide.

---

### Post by tonym53 on 2007-10-16
followed your post worked like a dream thanks for your help
i had a ati x1600 grarhics card,i also used envy to install drivers

---

### Post by Martin_sensei on 2007-10-18
Hello!

I followed this guide to the letter, and got compiz fusion running fine!  It looks very crisp and runs like a dream... for one user.

So I switched users to a desktop user and the machine locked completely.  I restarted the machine and logged on as the same desktop user (choosing the GNOME + XGA session ) and logged in sucessfully, however when I tried to enable desktop effects the dialog froze and I couldn't log off and couldn't get the effects working for this use.

Do I need to reconfigure anything for this second user?  Does the user need to be an administrator to use desktop effects?  Please help I feel so close to having ubuntu running perfectly!

---

### Post by kay.one on 2007-10-18
Hi, i followed your instruction compiz works now, but the problem is that my suspend doesn't work anymore, i have 7.10 Final, with an ATI X1400 in a Thinkpad T60.  any ideas on how to fix this.

---

### Post by dgrafix on 2007-10-19
Hi, i followed this and i now have a 3d cube and all effects in Gnome XGL session.

However, its broken my default gnome session and is exactly the same as the XGL one (starts with all effects). By broken I mean i no longer get direct rendering (which is a requirement of mine). I want to be able to have a second session with the default direct 3D enabled and one for the eyecandy.

---

### Post by scorpio_digit on 2007-10-19
Is there a reason I can't get the driver from the Restricted Drivers Manager to install? It worked before when I installed Feisty, now it wont. The only thing I can think of that I changed is the size of my swap partition.

---

### Post by hrvooje on 2007-10-23
> **dgrafix said:**
> Hi, i followed this and i now have a 3d cube and all effects in Gnome XGL session.

However, its broken my default gnome session and is exactly the same as the XGL one (starts with all effects). By broken I mean i no longer get direct rendering (which is a requirement of mine). I want to be able to have a second session with the default direct 3D enabled and one for the eyecandy.

login into your default gnome session, open terminal and in your home directory do this:

```
sudo mkdir .config/xserver-xgl
```

and than in this folder make a empty file named "disable" :

```
sudo gedit disable
```

save and close file, logout and login in default gnome session without xgl and with direct rendering

---

### Post by jammer84 on 2007-10-23
Thanks this worked a treat to get my pc working. I have an FSC Scaleo H with an ATI Radeon x1600 Pro. 

Have been trying for a while and this worked flawlessly.

Cheers

---

### Post by mate84 on 2007-10-28
Hello,
I have a Dell vostro 1000 laptop with ATI 1150. In the restricted drivers manager I got this error: xorg-driver-fglrx is missing and after when I install it I get this information: fix broken packages first. And in the terminal:
mate@mate-laptop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed. You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
mate@mate-laptop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for mate:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages
mate@mate-laptop:~$

At the moment I have large icons.....
Can anybody help me?

---

### Post by michael37 on 2007-10-30
> **mate84 said:**
> Hello,
I have a Dell vostro 1000 laptop with ATI 1150. In the restricted drivers manager I got this error: xorg-driver-fglrx is missing and after when I install it I get this information: fix broken packages first. And in the terminal:
mate@mate-laptop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed. You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
mate@mate-laptop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for mate:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages
mate@mate-laptop:~$

At the moment I have large icons.....
Can anybody help me?

Sounds like you have half-broken Feisty and half-broken Gutsy.  Beats me how you got here.

---

### Post by vcinfio on 2007-10-31
hey everyone i keep having the same problem i have tried mutlitple times to fix

1. i have added the Trevino repo's
2. i am running Ubuntu 7.04
3. ATI-200M Graphics Card
4. AMD Turion 64

when i try to install the compiz package listed in one of the early posts, this always pops up in the terminal

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compizconfig-settings-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compizconfig-settings-manager has no installation candidate

```

why is it missing from the repo?? can someone please help

Thanks

---

### Post by mahehellraiser on 2007-11-06
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity



this is wat i am getting.....compiz not working when i login ..and i typed compiz --replace..but getting the above erors.

---

### Post by ryanrich on 2007-11-10
Thank you so much for this guide, it's working perfectly now!

---

### Post by melzanis on 2007-11-12
Ok I have done everything that this howto has told me. However when I got and run the update in the terminal I get the following error message:

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems

then if I try to install beryl I get this error message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  emerald: Depends: libemeraldengine0 but it is not going to be installed
           Depends: libwnck18 (>= 2.15.90) but it is not installable
E: Broken packages

can someone please help me

---

### Post by 213374U on 2007-11-14
Okay, couldn't get this thing working, when I try to enable desktop effects I get this

```
Failed to start child process "gtk-window-decorator"(no such directory)
```

Also, Compiz settings manager does nothing when clicked. Any suggestions?

---

### Post by 213374U on 2007-11-14
Scratch that, did some toying and found a few broken packages during the update. Did the windows border fix and now enjoying the 3D effects. Thanks to the OP

---

### Post by Zerol on 2007-11-14
zerol@zerol-laptop:~$ sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra emerald emerald-themes
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager


This has got something to do with repositories right? How do I get it..

I already checked everything under "Downloadable from Internet" and change the server to United States because it was set to Netherlands.. files were added but still it couldnt find the package.. DAMN

---

### Post by matchstick on 2007-11-14
everything is working except for the emerald-themes and ccsm.  The emerald-themes said it was out of date or broken so i did everything but, and it works, just have an ugly maroon theme.  Any help on this?

as far as ccsm if i run it from terminal i get this error
```
aclark@aclark-laptop:~$ ccsm

Traceback (most recent call last):

  File "/usr/bin/ccsm", line 45, in <module>

    idle = ccm.IdleSettingsParser(context)

  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__

  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>

  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin

AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

aclark@aclark-laptop:~$ 


```

and if i try to run from menu nothing starts.

thanks for the help in advance

---

### Post by boob11 on 2007-11-22
thnx

---

### Post by BLTicklemonster on 2007-11-30
> **firmwire said:**
> Well earlier this afternoon I did a complete reinstall just to see if I could get Compiz fusion to work. AND I DID!!!
I used this and also 
[http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz&page=24](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz&page=24) 
and also
 [http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion+ati](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion+ati)
 as references. Everything was working like a dream. The cube...everything!!! Then I stupidly clicked on update when the screen popped up. That broke compiz and my XGL desktop.
I tried a few things and nothing work. Since I had time, I decided to just do another clean install and NOT do the updates if the screen popped up again. Well. It seems the repositories have been updated, so no matter what I do, I get a non working compiz fusion.

Is there any way to load on the repository from Before July 7th?  I noticed that some of the plugins make a reference to the 6th and not the 7th if I run compiz --replace from a xterm.
 Any suggestions? I know this is all working betas and use at your own risk... but I got it working this afternoon and then it stopped when some update was loaded this evening.

I did an update and still can't use any thing from the visual effects at all.

---

### Post by anfractuosities on 2007-12-03
Right after I installed compiz in gusty, nexiuz and any other fps will not display correctly.  It is very small and distorted. No detail at all, and very dark.  I really cant see atall  Also, after a few restarts, my resolution changed to default as did my moniter.  I have manually changed my moniter and it is now fine, but even games like planet penguin racer are not displaying correctly.  Mainly, in fullscreen the game is not full screen but centered, in the case of PPR it is off center and unplayable.

any ideas?

I have ati 1600 running flgrx.
x64

---

### Post by anfractuosities on 2007-12-03
Well, I just discoverd that the problem almost surely is opengl related.  When I installed warsow, and tried to play it it said "youre opengl installation does not support direct rendering", which isnt true, And that I" should install the propraity driver" which I have, but now seems to not be working...


K, so I uninstalled XGL in synaptic and now it works fine, except cpiz desktop effects do not.

---

### Post by bballplay344 on 2007-12-06
your post was awesome, however..

Once i re logged in after your directions, all my effects worked beautifully.  As soon as a rebooted my computer however, none of them work, and actually, everything run incredibly choppy and slow unless i sign in under just the gnome session. 


Any ideas as to why this is since it was working so nice for a little??

THanks.

---

### Post by jaymill on 2007-12-14
I installed everything as told to, but when I go and log out and try gnome with Xgl, my desktop is all fubared. I can kinda see where everything is, but the graphics are wayy messed up. I have the exact same laptop as you, so any help would be appreciated. Thanks!

---

### Post by Jeenyus on 2007-12-14
I got to the point where you had to Log Out, and when I logged out, there was nothing but a black screen!!  Anyone have any suggestions?

---

### Post by Fzero on 2007-12-16
I can't access the GPG security key. Problem Solved.

---

### Post by Mostlyharmless42 on 2007-12-19
I followed this guide, but I can't get compiz to run properly.  When i run compiz --replace i get this output
```
jred42@ubuntu:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'

```

I also loose my window boarders and when I run emerald it says "segmentation error (core dumped)

Any help would be nice.

---

### Post by Casual Fan on 2007-12-23
Great post, Thanks!

---

### Post by epitaph123 on 2007-12-28
when i pasted the beryl install terminal command, it could not find beryl to install it

---

### Post by Thug14 on 2008-01-15
thnx a lot

---

### Post by SIXAXIS on 2008-02-08
This xserver-xgl setting makes my computer extremely laggy and does not help with the effects. It still says "Desktop effects could not be enabled". I also ran the check skip compiz test and it says the XGL is not found and my card is not a whitelisted card. It doesn't say anything about my card or driver being blacklisted so it should work somehow. BTW, my card is an ATI Radeon XPRESS 200M with the current ATI propreitory drivers enabled in the Restricted Drivers Manager.

---

### Post by saguinus on 2008-03-04
This worked for me. I'm running ATI Mobility Radeon 9600.
Thank you for this nice guide !! :)

---

### Post by ADBD on 2008-03-14
I did this and now everything is screwed up! how can I undo this
EDIT: I don't even have ATI card if that matters...

---

### Post by Brian96 on 2008-05-02
Is this workaround still necessary to get Compiz working in Hardy with the fglrx driver? This problem has me shopping for an nVidia card for my next machine, but if ATI has gotten their act (and their support) together a little better I could be persuaded to consider ATI cards as well.

---

