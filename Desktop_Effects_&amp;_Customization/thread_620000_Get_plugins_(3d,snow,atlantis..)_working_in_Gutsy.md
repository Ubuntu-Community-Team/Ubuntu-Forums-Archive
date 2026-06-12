---
title: "Get plugins (3d,snow,atlantis..) working in Gutsy"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by Onay on 2007-11-22
Woo first script here it goes...

I made a simple script that allows you to install some plugins not in Compiz 0.6.1 (the one that came with Gutsy Gibbon 7.10). It will allow you to get the following plugins working.

- 3d windows: Windows jump off cube when rotating
- Atlantis2: Fish, sharks, and dolphins swim inside your cube
- Anaglyph: For use with 3d glasses
- Freewins: Rotate windows freely
- Photowheel: Mini cube inside your desktop cube to display pictures
- Screensaver: Random effects to use as a screensaver
- Snow: Have snow fall

Note that this requires you to have all correct graphics card drivers installed and a working compiz fusion install that comes with Gutsy. Some plugins (i.e. snow) require an extra step to get them working, or may involve some disclaimers after installed.

Just download the tar and untar it to your desktop or home folder. Then do the following command
```
cd plugins
sudo chmod 755 plugins.sh
```
to change to it's directory. Then to use it just do
```
./plugins.sh
```
Let me know what else I can add/install

All information has been taken from 
[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

---

### Post by nicesocks on 2007-11-22
i appreciate this, however...

i'm not able to download your tar file.  any help there?
and don't even get me started on that other page you link in the bottom of your post.  i tried what they explained and was horribly lost.

can you tell i'm green?  ^_^v

---

### Post by Onay on 2007-11-22
Are you using firefox? You should just be able to click on it to download it, then I can explain what to do afterwords.

After you download it, most likely to your desktop if you have everything set the way it comes, then you just right click on the file and click "Extract Here". There should be a folder that appears on your desktop called "plugins".

In your terminal (Applications->Accessories->Terminal) type in the following code, line by line, pressing enter between each line to execute that command...
```
cd ~/Desktop/plugins
sudo chmod 755 plugins.sh
```
In that code you change directories to the one you extracted, then you make the shell file executable.

Hope that helps. Any other feedback would be great.

---

### Post by mikedomo on 2007-11-22
thanks very much i will publish in many forums about ubuntu i have..

---

### Post by Eion on 2007-11-23
Worked like a charm!  Thanks!

---

### Post by Znort_Ubern00b on 2007-11-23
will they work with feisty...am really new to this and don't want to mess anything up...

---

### Post by maxfact on 2007-11-23
@onay

yuor script is fantastic 
yuo are the my friends 
very very good job :guitar:

---

### Post by andref on 2007-11-23
very, very nice script

thanks so much!


mmm, and for unistall some plugins?

---

### Post by Znort_Ubern00b on 2007-11-23
it doesn't work...nothing has happened at all followed your instructions to T but nothing...

---

### Post by Onay on 2007-11-23
Uninstall script? I can probably do that...

Here's what you need to do to uninstall any of them

Using 3d windows as an example
```
cd ~/compiz/**3d**
sudo make uninstall
```

Here's the folder names for the plugins that you'd change out with [b]3d[b]

- Atlantis2: **atlantis2-0.6**
- Anaglyph: **anaglyph-0.6**
- Freewins: **freewins-0.3-0.6**
- Photowheel: **photowheel**
- Screensaver: **screensaver**
- Snow: **snow**
- Autumn: **cd .autumn**

This is intended for the 0.6.1 install of Gutsy's Compiz. I'm upgrading compiz right now to 0.6.2 and seeing if the plugins still work.

---

### Post by Onay on 2007-11-23
Okay, I just installed the latest compiz core and other libraries that the update manager requested. Apparently I'm now using 0.6.3 when I do

compiz --version

All new plugins are working and there seems to be now problems.

---

### Post by nicesocks on 2007-11-23
ok.  so the other night i tried to download the file, but it must not have been hosted yet.

today i can download the file --no problem.  so that was resolved.  however, i can't get your code to work. i type in ```
cd ~/Desktop/plugins
``` and this is my result: ```
bash: cd: /home/nicesocks/Desktop/plugins: No such file or directory
```

i've tried this both with the file still tared and untared.  no luck.  any help there? as i'd love to have my windows hover and some snowflakes fall.

---

### Post by Onay on 2007-11-23
Make sure you downloaded the .tar.gz file to the desktop, then select "Extract Here" by right-clicking on the file. Then re do the commands.

My guess is that you're downloading it to the wrong location (not the desktop) so you may have to alter the commands if you're not doing those exact directions.

---

### Post by Apple.boi on 2007-11-23
that was awesome thank you for the script. i was doing it in root [sudo -i] so it was returning an error but i did it over without root, and it worked. once again THANKS A BUNCH!
also do i need to keep the compiz folder in my home directory after the install.

---

### Post by maxfact on 2007-11-24
@onay
excuse but one question
can i traslate in languages of italy yuor script for the installation of plugin?

Because members of forum ubuntu-it can use the plugin of compiz whit yuor script
i write yuor name of creator this file

excuse for my english is very ugly

---

### Post by ulisesrangel on 2007-11-24
hi,
i try your script but give me and error

------------------------------------------------------------------------
  Choose a plugin that you'd like to install
  [1] 3d Windows
  [2] Atlantis2
  [3] Anaglyph
  [4] Freewins
  [5] Photowheel
  [6] Screensaver
  [7] Snow
  [8] Falling Leaves
--> 1
--07:55:29--  [http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3](http://gitweb.opencompositing.org/?p=fusion/plugins/3d;a=snapshot;h=db3c51d6c5c0df268fc1ec29a4264ef3d21dbbb3)
           => `/tmp/3d.tar.gz'
Resolving gitweb.opencompositing.org... 195.114.19.35
Connecting to gitweb.opencompositing.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]

    [   <=>                               ] 10,295        24.13K/s             

07:55:30 (24.07 KB/s) - `/tmp/3d.tar.gz' saved [10295]

convert   : 3d.xml.in -> build/3d.xml
bcop'ing  : build/3d.xml -> build/3d_options.h/bin/sh: --header=build/3d_options.h: not found
make: *** [build/3d_options.h] Error 127
-------------------------------------------------------------------------------------

:confused:

---

### Post by andref on 2007-11-24
> **Onay said:**
> Uninstall script? I can probably do that...

Here's what you need to do to uninstall any of them

Using 3d windows as an example
```
cd ~/compiz/**3d**
sudo make uninstall
```

Here's the folder names for the plugins that you'd change out with [b]3d[b]

- Atlantis2: **atlantis2-0.6**
- Anaglyph: **anaglyph-0.6**
- Freewins: **freewins-0.3-0.6**
- Photowheel: **photowheel**
- Screensaver: **screensaver**
- Snow: **snow**
- Autumn: **cd .autumn**

This is intended for the 0.6.1 install of Gutsy's Compiz. I'm upgrading compiz right now to 0.6.2 and seeing if the plugins still work.

thank you (for the unistall's instruction)

i like so much this pluging very good work

ciao ciao!

---

### Post by nicesocks on 2007-11-25
**Onay**, this still isn't working for me.  i've downloaded the plugins.tar.gz file.  it's on my desktop because that's where firefox has, and still does, download files to.  that is hardly an issue.

i extracted the files to the desktop.  i have one folder called images that has a snowflake image in it. i have another tar.gz. file called autumn, i extracted that and put all those leaf images in the snowflake image folder for now.  and there is a plugins.sh file that is also there.

attached is an image of my desktop with the downloaded files rocking out on where they are supposed to be.  yet i'm still getting that "No such file or directory" error.  with all this information, you could possibly point me in the right direction even better.

---

### Post by Onay on 2007-11-25
> **maxfact said:**
> @onay
excuse but one question
can i traslate in languages of italy yuor script for the installation of plugin?

Because members of forum ubuntu-it can use the plugin of compiz whit yuor script
i write yuor name of creator this file

excuse for my english is very ugly

Of course you can. I really take no credit for this, I found this information on the compiz forums and I decided to make it a bit more user friendly, plus learn a bit about scripting at the same time.

> **Apple.boi said:**
> that was awesome thank you for the script. i was doing it in root [sudo -i] so it was returning an error but i did it over without root, and it worked. once again THANKS A BUNCH!
also do i need to keep the compiz folder in my home directory after the install.

If you plan on uninstalling any of the plugins, I recommend keeping the folder. Otherwise you can remove them. My advice is keep the folder for a little while just to make sure the plugins don't cause your compiz to crash or anything bad that might force you to have to uninstall them.

> **nicesocks said:**
> **Onay**, this still isn't working for me.  i've downloaded the plugins.tar.gz file.  it's on my desktop because that's where firefox has, and still does, download files to.  that is hardly an issue.

i extracted the files to the desktop.  i have one folder called images that has a snowflake image in it. i have another tar.gz. file called autumn, i extracted that and put all those leaf images in the snowflake image folder for now.  and there is a plugins.sh file that is also there.

attached is an image of my desktop with the downloaded files rocking out on where they are supposed to be.  yet i'm still getting that "No such file or directory" error.  with all this information, you could possibly point me in the right direction even better.

Make a new folder called **plugins** on your desktop and put the 2 folders and the .sh file that you extracted into it, then it should work fine. You may also have to run the **chmod 755** command on the .sh file again if you get an error that returns something like "file cannot be executed". Hope that helps

---

### Post by Majora26 on 2007-11-25
ooh! Thanks so much! I was looking for these for a while! yey snow!!!

---

### Post by informixtc on 2007-11-25
screensaver doesn't compile well:

> 
convert   : screensaver.xml.in -> build/screensaver.xml
bcop'ing  : build/screensaver.xml -> build/screensaver_options.h
bcop'ing  : build/screensaver.xml -> build/screensaver_options.c
schema    : build/screensaver.xml -> build/compiz-screensaver.schema
compiling : matrix.cpp -> build/matrix.lo
compiling : rotatingcube.cpp -> build/rotatingcube.loIn file included from screensaver_internal.h:9,
                 from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
build/screensaver_options.h:15:27: error: compiz-common.h: No such file or directory
build/screensaver_options.h:17: error: 'COMPIZ_BEGIN_DECLS' does not name a type
screensaver_internal.h:37: error: expected constructor, destructor, or type conversion before 'extern'
rotatingcube.cpp: In member function 'virtual void ScreenRotatingCube::preparePaintScreen(int)':
rotatingcube.cpp:75: error: 'displayPrivateIndex' was not declared in this scope
make: *** [build/rotatingcube.lo] Error 1
compiling : rotatingcube.cpp -> build/rotatingcube.loIn file included from screensaver_internal.h:9,
                 from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
build/screensaver_options.h:15:27: error: compiz-common.h: No such file or directory
build/screensaver_options.h:17: error: 'COMPIZ_BEGIN_DECLS' does not name a type
screensaver_internal.h:37: error: expected constructor, destructor, or type conversion before 'extern'
rotatingcube.cpp: In member function 'virtual void ScreenRotatingCube::preparePaintScreen(int)':
rotatingcube.cpp:75: error: 'displayPrivateIndex' was not declared in this scope
make: *** [build/rotatingcube.lo] Error 1



anyone having the same problem?

SOLUTION:

Solved the problem by removing an older installation of bcop 
removed it from /usr/local/bin/bcop and reinstall the new one from the ubuntu repository (compiz-bcop)

prior to reinstallation also removed /usr/local/share/pkgconfig/bcop.pc (don't know if that helped, but reinstall solved the problem)

---

### Post by Jose Catre-Vandis on 2007-11-25
Great script.

No snow textures, I'll go find some.

Found some here:

[http://www.anykeysoftware.co.uk/compiz/plugins/snow.tar.gz](http://www.anykeysoftware.co.uk/compiz/plugins/snow.tar.gz)

---

### Post by Odd-rationale on 2007-11-25
Wow! Thanks a lot. You saved my day!

---

### Post by Onay on 2007-11-25
> **Jose Catre-Vandis said:**
> Great script.

No snow textures, I'll go find some.

Found some here:

[http://www.anykeysoftware.co.uk/compiz/plugins/snow.tar.gz](http://www.anykeysoftware.co.uk/compiz/plugins/snow.tar.gz)

Yeah, I made it so that the script copied them over to /usr/share/ccsm/images

You just have to tell the snow plugin where the image is. I added a short bit of instructions at the end of the script after running the snow plugin installer

---

### Post by misterlogan on 2007-11-25
> **Onay said:**
> Yeah, I made it so that the script copied them over to** /usr/share/ccsm/images**

You just have to tell the snow plugin where the image is. I added a short bit of instructions at the end of the script after running the snow plugin installer

left mine in /home/pictures, im still not used to how this is layed out :(

how does the screensaver plugin work? its showing in the compiz options but the gnome screensavers are still on instead

---

### Post by AndrewGene on 2007-11-25
I get this when trying to install photowheel...any ideas?

```
 build/photo_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from photo.c:44:
build/photo_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
photo.c:48: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
make: *** [build/photo.lo] Error 1
compiling : photo.c -> build/photo.loIn file included from photo.c:44:
build/photo_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from photo.c:44:
build/photo_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
photo.c:48: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
make: *** [build/photo.lo] Error 1
  
```

---

### Post by Lothas on 2007-11-26
Ok, something isn't working properly here. (although, nice job!)
I installed some of the plugins and most of them worked pretty nicely. The "bug" I've encountered so far is that even if you change the settings with Compiz manager, they won't be saved or they won't have any effect on the plugins. For example, I changed the number of big fish, like sharks and such to 0 and increased the small fish size to the max but I still got the same image. I also couldn't set key bindings to some of the plugins which is even more annoying. Any idea?

---

### Post by mrmiserable on 2007-11-26
this is just as easy and more plugins

[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

---

### Post by Lothas on 2007-11-26
Forget about my earlier post. Restarting compiz fixed the problem and now it's working properly.

BTW, It would be pretty cool if someone would develop a new plugin or just a set of textures for Autumn or Snow so we could have matrix code falling instead of leaves or flakes. I know this has been done with xwinwrap and such but this could be even better. Or I could just be talking nonsense.

---

### Post by subs on 2007-11-26
thnx man

---

### Post by ash4ever on 2007-11-26
:)Works great

---

### Post by iladw on 2007-11-26
Hi.
Great work thanks for the plugin.

I have this question and I thank anyone willing to help.

All works fine except the image of the snowflake. At the end of the installation it says that I have to copy a string and put it in the manager.

I copy the string -> goto compiz manager -> snow extras -> Textures -> Add -> Paste the link and click ok. Nothing happens - I have the image of the snowflake(it doesn't matter where is, does it?) but I can only see white cubes as a snow.

---

### Post by andref on 2007-11-26
well, i'd the same problem

you have to go to the plugin Snow and after open the tab Textures and so change the images' adress with ```
/usr/share/ccsm/images/snowflake.png
```, now your snow will go properly.

ciao ciao!

---

### Post by iladw on 2007-11-26
Yes I did so - no result though.
Here's how it looks:
[IMG]http://img219.imageshack.us/img219/7151/screenshot2nt5.jpg[/IMG]
And the effect:
[IMG]http://img216.imageshack.us/img216/7183/screenshotrb4.jpg[/IMG]

---

### Post by andref on 2007-11-26
but you have the image in the directory?

try to copy the file that i've update in the your directory

---

### Post by iladw on 2007-11-26
It has been there since begging >
[IMG]http://img216.imageshack.us/img216/832/screenshotqq7.jpg[/IMG]

---

### Post by andref on 2007-11-26
mmm, strange...

when i've installed the plugin i had the same problem only square around the screen, but i don't remember what i do for it...

i think that i only change the images adress...

---

### Post by iladw on 2007-11-26
Thanks anyway Andref. I'll look for a solution.

---

### Post by Lothas on 2007-11-26
Hi, I had the same problem. Try restarting compiz (ctrl+alt+backspace would be the easiest way).

---

### Post by jstableford on 2007-11-26
Awesome script - good work! You are my hero

---

### Post by vdb007 on 2007-11-26
Hi,

I am new to Ubuntu 7.10. ..I have installed this ./plugin.sh script, my ? is how do I run 3d effects and cool stuff such having a cube screen and the rotation feature. Any suggestions/tricks would be appreciated from this forum.

Thanks !
 Van
 (Vancouver, Canada)

---

### Post by Jose Catre-Vandis on 2007-11-26
Still no snow, even with the textures I found :)  (I previously installed Autumn from a seperate post, which works fine, and is based on snow??

Also Photowheel kills my setup (I run with "no desktop" and load images into Compiz for seperate wallpapers on different workspaces

---

### Post by schlox on 2007-11-26
Hi all,

Although I made everything correct (I think)  I can't have the snow or 3D cube. Well, I have some fancy effects but not everything that can be seen in this video:

> [http://www.youtube.com/watch?v=bYsxaMyFV2Y](http://www.youtube.com/watch?v=bYsxaMyFV2Y)

I can switch the windows with mouse roller, I am able to use alt+WindowsButton+tab combination but still not able to have sides of the cube and 3D windows which are 3D cascaded.

I have compiz version of 0.6.1 and using nVidia GeForce 6800 with 256 mb and I have all the necessary plugin mentioned at the first post. 

On the other hand, when I write the command compiz to Terminal, the output is:

> 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:00c8 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1920x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


and then it doesn't go any further. maybe my not being able to use those 3D cube with snow has something related to the thing inside the Quoted text? 

Helps will be appreciated. Sorry if I am making funny and/or nonsense explanations. I am using linux only for 3 days.

Cheers,
Schlox

---

### Post by santiagoward2000 on 2007-11-26
I'm having a problem with **freewins**. When it is enabled and I click on the *Quit* button, the screen dims as usual but the Window with all the options to Restart, Turn off, etc never appears. I know the window is actually there, because I accidentally got to click on *Log off*, but I can't see it. Has anyone else experienced this problem?

---

### Post by iladw on 2007-11-27
Thanks Lothas, it worked. Apparently it needed some restart.

---

### Post by Lothas on 2007-11-27
No problem, glad to be on the helping side for once :)

---

### Post by BujarM on 2007-11-27
I installed the script,
i enabled the plugins in the menager
and yet when i turn the cube
non of them work
why?

---

### Post by schlox on 2007-11-27
> **BujarM said:**
> I installed the script,
i enabled the plugins in the menager
and yet when i turn the cube
non of them work
why?


Hi my friend. Yesterday, I had the same problem. I asked it but unfortunately my question seemed to be so silly that, I didn't receive any answers. 

Anyways, I solved it by my self, now teaching you how to do. 

Go to :  system->preferences->advanced desktop effects settings

If you can not find that it means you need to install compiz configurations which can be done by the following command:
```
sudo apt-get install compizconfig-settings-manager
```

Then again 
Go to :  system->preferences->advanced desktop effects settings
or
also can be run by code ```
ccsm
``` from the Terminal.


Then you should be seeing advanced desktop effects settings. So, at that screen, you have lots of options. For example if you want to see falling leafs on your screen, just go to Extras click in to the box of Autumn and then just press the key combination:
> windows button(called SUPER at compiz menu) + F11

To stop it, press the same combination again. In order to learn all different effects and to see how to trigger them, just click on any Icon Name and look into details.

Here you go. If you have any questions, don't think that it would be stupid or something. As a 4 day linux user, I surely can assist you.

Hope it is usefull

Cheers,
Schlox

---

### Post by Onay on 2007-11-27
Thanks, my apologies, but I figured that if you're a user and are aware that there are extra plugins to be installed, then you probably have the settings manager and know a little bit about configuring the system.

This thread is not meant to show how to install compiz fusion and ccsm, but rather just how to install these unsupported, albeit fun, plugins.

---

### Post by babygirl on 2007-12-07
It has been difficult to find "extra" screen savers like freesaver.com does for windows. It's not a huge problem as  Linux default screensavers are better than some of the good ones I found online for windows. My real driving force is the basic fact that Linux graphics put windows to pure shame.

Anyone know where I can get extra screensavers for Ubuntu 7.10 Gusty? I tried the others listed here but no good.

---

### Post by spyd4r on 2007-12-12
Awesome job!! 


Thanks

---

### Post by tdlofcc on 2007-12-12
YOU .. are the man :)

Cheers m8. All works like a charm.

Now I can have myself a white christmas :D

---

### Post by lilkeith07 on 2007-12-13
Thanks! I got everything to install correctly and everything works except for the Anaglyph. How do I enable it? I have it checked in the Compiz-Manager but I don't know what to do from there.

Edit:Never mind I got it working

---

### Post by funnypanks on 2007-12-15
anyone know how to use this on 64 bit gutsy? compiz crashes when i select snow from ccsm

---

### Post by linuxbubbles on 2007-12-15
hi, I'm a newbie in Linux, got on gutsy gibbon (7.10) a few days ago and on the run from MS Windows.
 your script works fine for [COLOR="Navy"]anaglyph[/COLOR] and [COLOR="Navy"]freewins[/COLOR] even if i dunno what they do (have tried, nothing happened.) but what is really frustrating is that the main feature that I have been trying to install since the beginning ,[COLOR="Sienna"]3d[/COLOR] and [COLOR="Sienna"]atlantis[/COLOR], still will not show up in the damned CCSM menu. :mad:
i am despairing... it is about the 7th time i tried to make them work and can't get it right. have done about all the "howto"s on the subject, i get errors when trying to make and make install the package an I'd really appreciate some help with getting these plugins to work for me.

---

### Post by Saponsky09 on 2007-12-18
Hey thanks for the script! But I tried following the instructions in the link you gave: [http://forum.compiz-fusion.org/showthread.php?t=5303]("http://forum.compiz-fusion.org/showthread.php?t=5303")
And I followed all the instructions but just for installing the Screensaver plugin, everything worked fine for the plugin but when I restarted Compiz and cssm my desktop background image is now missing (now I have a black background instead) and I try to open my file browser and it's not working. Any help please?!

---

### Post by dan1_m1 on 2007-12-19
This script is grate :guitar:
Thank you

---

### Post by Flare183 on 2007-12-19
Use emerald --replace to fix the window title bar problem. Like this:
```
emerald --replace
```

Press Alt-F2, then type it in.
For kubuntu, click k-menu, run application. And then type it in.

:guitar:     :KS

---

### Post by dbzkid on 2007-12-19
the question i have is will i beable to see the plugins (and edit them) in the "advanced configuration settings" (something like this)

---

### Post by jryprt on 2007-12-21
> **Onay said:**
> Woo first script here it goes...

I made a simple script that allows you to install some plugins not in Compiz 0.6.1 (the one that came with Gutsy Gibbon 7.10). It will allow you to get the following plugins working.

- 3d windows: Windows jump off cube when rotating
- Atlantis2: Fish, sharks, and dolphins swim inside your cube
- Anaglyph: For use with 3d glasses
- Freewins: Rotate windows freely
- Photowheel: Mini cube inside your desktop cube to display pictures
- Screensaver: Random effects to use as a screensaver
- Snow: Have snow fall

Note that this requires you to have all correct graphics card drivers installed and a working compiz fusion install that comes with Gutsy. Some plugins (i.e. snow) require an extra step to get them working, or may involve some disclaimers after installed.

Just download the tar and untar it to your desktop or home folder. Then do the following command
```
cd plugins
sudo chmod 755 plugins.sh
```
to change to it's directory. Then to use it just do
```
./plugins.sh
```
Let me know what else I can add/install

All information has been taken from 
[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

Works Great used post 1 & 3
here is post #3
Are you using firefox? You should just be able to click on it to download it, then I can explain what to do afterwords.

After you download it, most likely to your desktop if you have everything set the way it comes, then you just right click on the file and click "Extract Here". There should be a folder that appears on your desktop called "plugins".

In your terminal (Applications->Accessories->Terminal) type in the following code, line by line, pressing enter between each line to execute that command...
Code:

cd ~/Desktop/plugins
sudo chmod 755 plugins.sh

In that code you change directories to the one you extracted, then you make the shell file executable.

---

### Post by jimbob on 2007-12-22
Thanks for this - works great.  Now I finally have a selection under effects in my CCSM that says '3D windows' like I had in Beryl.

---

### Post by rainai2k7 on 2008-01-08
cool!!  thanks for this!

---

### Post by stathis21 on 2008-01-08
in the end of installation it tels me 
Choose a plugin that you'd like to install
  [1] 3d Windows
  [2] Atlantis2
  [3] Anaglyph
  [4] Freewins
  [5] Photowheel
  [6] Screensaver
  [7] Snow
  [8] Falling Leaves
-->

what sould i do now???

---

### Post by jimbob on 2008-01-08
Put in the number of the plugin and hit enter, that's all I did.  If you want more than one I guess you could separate them by commas.  In my case all I wanted was 3D  windows.  Matter of fact I don't even know what most of the others are.

After the program exited, I looked in the CCSM and there it was so I selected it and had my 3D windows.

---

### Post by stathis21 on 2008-01-09
ok...i thought i pressed 1 and nothing happened...but now its ok...
the only think i wanted was atlantis...but it doesn't work
it tells me that

--> 2
--16:56:55--  [http://gitweb.compiz-fusion.org/?p=users/smspillaz/atlantis2-0.6;a=snapshot;h=d50d17bcdef5a025699e6b1bc0d604a98d1b74b2;sf=tgz](http://gitweb.compiz-fusion.org/?p=users/smspillaz/atlantis2-0.6;a=snapshot;h=d50d17bcdef5a025699e6b1bc0d604a98d1b74b2;sf=tgz)
           => `/tmp/atlantis2.tar.gz'
&#917;&#973;&#961;&#949;&#963;&#951; &#964;&#959;&#965; gitweb.compiz-fusion.org... 195.114.19.35
Connecting to gitweb.compiz-fusion.org|195.114.19.35|:80... &#963;&#965;&#957;&#948;&#941;&#952;&#951;&#954;&#949;[COLOR="Red"](connected)[/COLOR].
&#919; &#945;&#943;&#964;&#951;&#963;&#951; &#947;&#953;&#945; HTTP &#963;&#964;&#940;&#955;&#952;&#951;&#954;&#949;, &#945;&#957;&#945;&#956;&#959;&#957;&#942; &#945;&#960;&#940;&#957;&#964;&#951;&#963;&#951;&#962;[COLOR="Red"](waiting for answer)[/COLOR]... 403 Forbidden
16:56:55 &#931;&#934;&#913;&#923;&#924;&#913;[COLOR="Red"](error) [/COLOR]403: Forbidden.

cd: 98: can't cd to /home/stathis/compiz/atlantis2-0.6
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
NOTE: By default, this plug-in uses too many system resources because of the number of models loaded. You might want to consider lowering some of the numbers in ccsm->Effects->Cube Atlantis->Numbers.


sorry but some words are written in greek...and for my poor English...

---

### Post by jryprt on 2008-01-09
> **stathis21 said:**
> ok...i thought i pressed 1 and nothing happened...but now its ok...
the only think i wanted was atlantis...but it doesn't work
it tells me that

--> 2
--16:56:55--  [http://gitweb.compiz-fusion.org/?p=users/smspillaz/atlantis2-0.6;a=snapshot;h=d50d17bcdef5a025699e6b1bc0d604a98d1b74b2;sf=tgz](http://gitweb.compiz-fusion.org/?p=users/smspillaz/atlantis2-0.6;a=snapshot;h=d50d17bcdef5a025699e6b1bc0d604a98d1b74b2;sf=tgz)
           => `/tmp/atlantis2.tar.gz'
&#917;&#973;&#961;&#949;&#963;&#951; &#964;&#959;&#965; gitweb.compiz-fusion.org... 195.114.19.35
Connecting to gitweb.compiz-fusion.org|195.114.19.35|:80... &#963;&#965;&#957;&#948;&#941;&#952;&#951;&#954;&#949;[COLOR="Red"](connected)[/COLOR].
&#919; &#945;&#943;&#964;&#951;&#963;&#951; &#947;&#953;&#945; HTTP &#963;&#964;&#940;&#955;&#952;&#951;&#954;&#949;, &#945;&#957;&#945;&#956;&#959;&#957;&#942; &#945;&#960;&#940;&#957;&#964;&#951;&#963;&#951;&#962;[COLOR="Red"](waiting for answer)[/COLOR]... 403 Forbidden
16:56:55 &#931;&#934;&#913;&#923;&#924;&#913;[COLOR="Red"](error) [/COLOR]403: Forbidden.

cd: 98: can't cd to /home/stathis/compiz/atlantis2-0.6
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
NOTE: By default, this plug-in uses too many system resources because of the number of models loaded. You might want to consider lowering some of the numbers in ccsm->Effects->Cube Atlantis->Numbers.


sorry but some words are written in greek...and for my poor English...

Try [This guide](http://ubuntuforums.org/showthread.php?p=4079057#post4079057) do the first 3 codes then go to the plugin you want then its 5 steps to get .

---

### Post by jwatne on 2008-01-14
Thank you for this excellent post.  I am very much enjoying playing with the new "toys", especially the 3D windows -- which is the search that brought me to this page initially.

---

### Post by legolas_w on 2008-01-14
Hi
thank you for your tutorial. I completely installed all plugins by using your tutorial but I have a problem which i described here.

I followed your instruction and it is possible that i miss some step or make some mistake during the process and now I faced a big problem, my CCSM (compiz configuration setting manager) is locked and i can not edit anything in  it, I attached the image in order to show you more about the problem, can you please let me know what step i made wrong or what should i do to take the control back?

Thanks

---

### Post by Millhouse13 on 2008-02-07
wow, worked really great. I had may of those already installed but none worked before, and now everyone works like a charm. thanks a LOT.

---

### Post by oderus on 2008-04-12
Awesome job dude! Amazing for your first script.

I installed snow and autumn without a hitch.

Cheers!!

---

### Post by NSF12345 on 2008-04-14
Nice script. the script appears to run great..thanks!!

only problem are.. snowflakes (all i get is white squares but im guessin thats due to my graphics. no worries)

Antlantis 2, cant seem to enable this feature?

Photowheel. doesnt want to show any photo's even though iv told it which photo's to look at

Freewins. When is this meant to initiate?

and screensaver. left it for over a 3 minutes (its set to 1) but doesnt want to start working?

any ideas with these? thanks

---

### Post by thepossiblehuman on 2008-04-18
Great post!  Thanks.

---

### Post by dr_james2k on 2008-04-27
Can anybody else get these working in 8.04?

[solved]
I found a good guide here for Hardy Heron users: [http://forum.compiz-fusion.org/showthread.php?t=8214](http://forum.compiz-fusion.org/showthread.php?t=8214)

---

### Post by jefflam1200 on 2008-06-04
how come i get this?

           => `/tmp/atlantis2.tar.gz'
Resolving gitweb.compiz-fusion.org... 195.114.19.35
Connecting to gitweb.compiz-fusion.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
23:38:13 ERROR 403: Forbidden.

tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
cd: 98: can't cd to /home/jeff/compiz/atlantis2-0.6
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
NOTE: By default, this plug-in uses too many system resources because of the number of models loaded. You might want to cons
ider lowering some of the numbers in ccsm->Effects->Cube Atlantis->Numbers.
jeff@jeff-laptop:~/Desktop/plugins$

---

### Post by marcoandrossana on 2008-06-26
I downloaded but it didn't work. :(

---

### Post by itsvan on 2008-06-28
hi,im running UBUNTU 8.04 Hardy Heron,,and even though most of my desktop effects are working some are not,,most noticeable the one i want to use THE 3D windows effect,,the one where when your rotating the cube, you can see the windows pop up and stuff,,and if possible it be cool to add other new features what can i do?

---

### Post by borlosky on 2008-07-01
scrip worked great, i have the options in my compiz settings manager, but won't let me enable the new plugins. When i check the new plugins (snow, atlantis, screensaver, photowheel, snow globe, etc...) they will only stay checked for about 2 seconds then the check mark dissapears???

---

### Post by compiz4eva on 2008-07-02
did u ever get that fixed yet? i have the same problem. everytime i check atlantis, snow, photowheel, 3d windows and a few other plugins, it stays checked 4 like 2 seconds and boom its not working again.

---

### Post by borlosky on 2008-07-02
No, still having same problem. only stays checked for a couple seconds, and then goes away

---

### Post by ldgregory on 2008-07-03
I've got the same issue. It only seems to affect 3D Windows and Fireflies. All the rest work as expected.

I used to have 3D Windows working under Fiesty. Upgraded to Hardy and have never gotten them working again.

---

### Post by the guitarist on 2008-07-04
hi there ...

i used the script and installed all the plugins but there're 2 plugins that i'm dying to use :

1- stack switch
2- the shelf or the shelf-dock plugin

is it possible to install them? and if yes..HOW CAN I DO THAT?

---

### Post by borlosky on 2008-07-08
> **borlosky said:**
> scrip worked great, i have the options in my compiz settings manager, but won't let me enable the new plugins. When i check the new plugins (snow, atlantis, screensaver, photowheel, snow globe, etc...) they will only stay checked for about 2 seconds then the check mark dissapears???

I was finally able to get all plugins working fine. Here's how I did it:

1: went to add/remove from Applications menu, removed all compiz related software

2: went to Synaptic package manager and COMPLETELY Removed ALL compiz related software

3: Followed steps located here: [http://www.xs4all.nl/~mgj1/compiz_git.htm](http://www.xs4all.nl/~mgj1/compiz_git.htm)

4: Logged out, then back in. all working fine now!!:KS (all my previous keybindings were saved however, so very little configuration was needed other than just checking the new options)

---

