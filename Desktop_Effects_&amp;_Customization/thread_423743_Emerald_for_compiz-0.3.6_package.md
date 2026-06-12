---
title: "Emerald for compiz-0.3.6 package"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by Kevin on 2007-04-26
I was bored and looking for something to do, so I took a git snapshot of emerald, updated the patch from the compiz.org forums, updated the debian packaging rules from the emerald in the repos, and built an emerald package that works with desktop-effects, no beryl needed :)

**Disclaimer**
I'm by no means much of a programmer.  I looked through the original compiz-support patch, manually added the changes, and then commented out some sections of code that were giving me errors (hence the no blur support)  If anyone who knows more about stuff, feel free to look at the source and tell me what I did wrong :)

It seems a bit slow, no doubt my fault :)

**Installing this package will likely break beryl if you have that installed!! Not permanently though, so feel free to try it.  You'll just have to reinstall the version in the repos to fix beryl.**

That out of the way, once you install these packages, you can simply kill gtk-window-decorator and start emerald.  If you want it permanent, open up your session options, disable gtk-window-decorator, and add emerald.

The emerald-themes package in the repos still works fine with this package!

Have fun, let me know if it works.

**Build From Source**

I've included all the sources if you want to build for an architecture other than i386.  I had to put the orig.tar.gz file [here]("http://rapidshare.com/files/31736583/emerald_0.3.0_git20070426.orig.tar.gz.html") on rapidshare because its too big.... sorry.  Rapidshare apparently doesn't allow ~ characters in the name, so you'll need to rename it to emerald_0.3.0**~**git20070426.  Rename the .dsc.txt file attached to just .dsc, download the .diff.gz, and put them all in the same directory.  Then run ```
dpkg-source -x emerald_0.3.0~git20070426-0test0.dsc
cd emerald_0.3.0~git20070426
dpkg-buildpackage -rfakeroot
```

Thanks to strumluff there are now amd64 packages pre-built.  You can grab them [here!]("http://ubuntuforums.org/showpost.php?p=2690221&postcount=42")

---

### Post by schnupi on 2007-05-07
has anyone tried this yet?

one question: is this the same release as -> [http://forum.compiz.org/viewtopic.php?t=875](http://forum.compiz.org/viewtopic.php?t=875)

because the last post says something about this deb overwritting files in binutils which apparently are very important. im a newb and really love to use emerald for window borders instead of gtk2+

---

### Post by searayman on 2007-05-07
i will try it if you fix the problem of it destroying beryl.....

---

### Post by schnupi on 2007-05-07
> **searayman said:**
> i will try it if you fix the problem of it destroying beryl.....

well yea it is for compiz afterall

---

### Post by searayman on 2007-05-07
i guesse i will give it a try, do i install all 3 attacted debs? if not which ones do i install?

---

### Post by Ateo on 2007-05-07
Great work. Installs and works well.

However, when you say to disable gtk-window-decorator, this makes no sense as it is not listed in my sessions manager. Which one, exactly, did you disable?

Thanks

/edit

Scratch that. I just made a script that kills gtk-win-dec and starts emerald. I created a new startup program that points to that script. Works well. Thanks a bunch! Here is it in case anyone cares:

Open file:```
sudo gedit /usr/bin/emerald_wrapper
```
Add to file:```
#!/bin/sh
killall gtk-window-decorator
emerald
```

Save and exit. Don't forget to chmod +x that file.

---

### Post by Ateo on 2007-05-07
This might just be me, but this kills the taskbar pager..

/edit

dur. retard. it was just me. hehe. =)

---

### Post by Kevin on 2007-05-07
Hey there, nice to see some interest in it, I though it had gotten lost in the multitude of threads around here :)

The reason it might have problems with beryl is because all of the binaries are still the same.  This would not be easily fixed at all without renaming all the binaries and such.

Its not the same package as the one in the thread on compiz.org, this one is based off the emerald package in the repos, and should therefore not break anything.

About killing gtk-window-decorator, yeah, its not in the session manager anymore.  I think the command to start compiz is around in gconf somewhere, I'll have a look.  In the meantime, you can either kill gtk-window-decorator, or use the little wrapper script previiously posted.

---

### Post by schnupi on 2007-05-08
> **Ateo said:**
> Great work. Installs and works well.

However, when you say to disable gtk-window-decorator, this makes no sense as it is not listed in my sessions manager. Which one, exactly, did you disable?

Thanks

/edit

Scratch that. I just made a script that kills gtk-win-dec and starts emerald. I created a new startup program that points to that script. Works well. Thanks a bunch! Here is it in case anyone cares:

Open file:```
sudo gedit /usr/bin/emerald_wrapper
```
Add to file:```
#!/bin/sh
killall gtk-window-decorator
emerald
```

Save and exit. Don't forget to chmod +x that file.


so how do u make this startup? just add /usr/bin/emerald_wrapper to the startup list?! im a newb sry :p

---

### Post by Ateo on 2007-05-08
[QUOTE=schnupi]just add /usr/bin/emerald_wrapper to the startup list?[/QUOTE]

Yes. If that's what you named it... Don't forget to do```
$ chmod +x /usr/bin/emerald_wrapper
```

Oh and here is what I am using:```
#!/bin/sh
killall gtk-window-decorator
emerald --replace
```

---

### Post by searayman on 2007-05-08
do i have to uninstall emerald first, and again i will ask do i need to install all 3 attaced paackages?

when i go to install the first .deb it says a later version is already installed.....

---

### Post by searayman on 2007-05-08
> **searayman said:**
> do i have to uninstall emerald first, and again i will ask do i need to install all 3 attaced paackages?

when i go to install the first .deb it says a later version is already installed.....

so i tried uninstalling emerald and installign this on e ad it made me do a sudo apt-get install -f caus eit thought ti was broken... and it woudlnt let me install the other packages....

---

### Post by Ateo on 2007-05-08
Remove all emerald packages installed via synaptic. Then install the debs in this order:

1. libemeraldengine0_0.3.0~git20070426-0test0_i386.deb
2. libemeraldengine-dev_0.3.0~git20070426-0test0_i386.deb
3. emerald_0.3.0~git20070426-0test0_i386.deb

Have fun.

---

### Post by searayman on 2007-05-08
> **Ateo said:**
> Remove all emerald packages installed via synaptic. Then install the debs in this order:

1. libemeraldengine0_0.3.0~git20070426-0test0_i386.deb
2. libemeraldengine-dev_0.3.0~git20070426-0test0_i386.deb
3. emerald_0.3.0~git20070426-0test0_i386.deb

Have fun.

ok so i did all you said and installed with no errors, but i can't seem to get emerald to work....

mike@mike-desktop:~$ killall gtk-window-decorator
gtk-window-decorator: no process killed
mike@mike-desktop:~$ emerald
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"
mike@mike-desktop:~$

---

### Post by Ateo on 2007-05-08
try ```
emerald --replace
```

---

### Post by schnupi on 2007-05-08
thanks it all worked! pity the blur effect isnt workin but i ll survive that

---

### Post by searayman on 2007-05-08
ok so i just tried emrald again and got this:

mike@mike-desktop:~$ emerald
/home/mike/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:21: Unable to locate image file in pixmap_path: "Toolbar/toolbar-black.png"
/home/mike/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:24: Background image options specified without filename
/home/mike/.themes/aero-clone/gtk-2.0/gtkrc:187: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/home/mike/.themes/aero-clone/gtk-2.0/gtkrc:191: Overlay image options specified without filename

mike@mike-desktop:~$

---

### Post by Ateo on 2007-05-08
If you run emerald while emerald is running, you get a nice crash...

I really do suggest using ```
emerald --replace
```

Also, to configure compiz, use compiz settings [found here]("http://compiz.org/Ubuntu_Installation_Guide#Configuring_Compiz"). Don't use gnome-compiz-manager in synaptic (it has merely a quarter of the options compiz settings GUI has).

---

### Post by searayman on 2007-05-08
> **Ateo said:**
> If you run emerald while emerald is running, you get a nice crash...

I really do suggest using ```
emerald --replace
```

Also, to configure compiz, use compiz settings [found here]("http://compiz.org/Ubuntu_Installation_Guide#Configuring_Compiz"). Don't use gnome-compiz-manager in synaptic (it has merely a quarter of the options compiz settings GUI has).

after many crazy thigns with compiz and re-insatllign it and such i finally got this workign!!!

thansk!!!

how do i change themes with it though?

---

### Post by Ateo on 2007-05-08
System -> Preferences -> Emerald Theme Manager

---

### Post by Kevin on 2007-05-08
To answer all your questions, what Ateo said :)

But yeah, there are bound to be some bugs in this version, but it seems to be usable at least.  As the git version is adapted for compiz more, I should be able to update it.  The only problem being that compiz 0.3.6 is old now, so this might be what we get until you start using compiz 0.5.0

---

### Post by Kevin on 2007-05-08
Oh, and about gnome-compiz-manager, gnome-compiz-manager-extra actually has pretty much all of the useful settings presented much more clearly than compmiz-settings.  The only problem is the package doesn't work on feisty.  That's my next project, it should be really easy (its just dependency errors) but I'm having trouble with the build process.  Hopefully I'll figure it out soon.

---

### Post by schnupi on 2007-05-09
> **Kevin said:**
> Oh, and about gnome-compiz-manager, gnome-compiz-manager-extra actually has pretty much all of the useful settings presented much more clearly than compmiz-settings.  The only problem is the package doesn't work on feisty.  That's my next project, it should be really easy (its just dependency errors) but I'm having trouble with the build process.  Hopefully I'll figure it out soon.

Hmm interesting.. i was just about to try compiz-settings but i wasnt able to download it. i think the mirror is down. just doesnt work...

anyways, i had gnome-compiz-manager installed and it never really saved the settings and when i installed the extras it didnt work at all... at that stage of course i didnt know that it didnt work properly with feisty 8) .. now i know thanks..

---

### Post by Ateo on 2007-05-09
Kevin,

Great. I just upgraded to compiz 0.5. I tried to modify the emerald deb for this version but failed horribly (i'm pretty much new to deb's coming from an ebuild world)....

But, I'll definately be watching this thread for updates. =)

Thanks for the work dude.

/edit

Hopefully this will generate more interest in the new compiz (0.5.0). Here is where I downloaded the debs that work just fine under Feisty...
compiz, compiz-config-gnome, compiz-core, compiz-extra-plugins , compiz-gtk,  compiz-plugins, compiz-settings **FROM** [http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/) (scroll down to compiz packages)

compiz-settings **FROM** [http://compiz.org/Ubuntu_Installation_Guide#Configuring_Compiz](http://compiz.org/Ubuntu_Installation_Guide#Configuring_Compiz)

---

### Post by Kevin on 2007-05-09
Yeah, I doubt emerald will be working with compiz 0.5.0 for a little while at least.  The patch that I applied basically removes the stretch when resizing functionality that compiz doesn't have, and makes some name changes for functions contained in libdecoration.

Compiz 0.5.0 isn't that much different core-wise from 0.3.6, it adds some new plugins and there are lots of bug fixes (and introductions) but hasn't added lots of the new core functionality such as the new dbus plugin, and the updated libdecoration which should let normal emerald run fine on compiz.

I'll do my best to keep following this stuff and updating as often as I can, but I'm home from school from the summer, and this business of not having high-speed available in the country is reeeeally annoying :)  So it takes a while to upload and download sources on 56k.

---

### Post by Ateo on 2007-05-09
Hmm. Well, 0.5.0 *is* development. So I'll be rolling back to the stable 0.3 series. I updated only to compare cpu usage for a certain plugin.

Cheers.

---

### Post by Kevin on 2007-05-09
Yup, its development, but its a development release, so its not as updated as the git version.   Git has new dbus functionality, new libdecoration bindings, etc.  0.5.2 should have much more new stuff.

---

### Post by Ateo on 2007-05-11
For the record, if you're just using emerald, you don't need the libemeraldengine-dev.

---

### Post by aimran on 2007-05-11
Hey cool! Thanks for the debs. Just wish they were for x64 >_< !

By the way I have compiz listed on my update manager but I can't click on the tick next to it to install the update :| 

Anyways keep up the good work!

---

### Post by reya276 on 2007-05-11
I tried doing this but I got this error:

reya276@reya276-desktop:~$ chmod +x /usr/bin/emerald_wrapper
chmod: changing permissions of `/usr/bin/emerald_wrapper': Operation not permitted
:confused:

---

### Post by Ateo on 2007-05-11
> **reya276 said:**
> I tried doing this but I got this error:

reya276@reya276-desktop:~$ chmod +x /usr/bin/emerald_wrapper
chmod: changing permissions of `/usr/bin/emerald_wrapper': Operation not permitted
:confused:

Try```
$ sudo chmod +x /usr/bin/emerald_wrapper
```

Cheers.

---

### Post by 01ago on 2007-05-12
It works fine!!!
Thanks.
Also thank Ateo for the startup script  :)

---

### Post by Tomosaur on 2007-05-15
Thanks for that, I couldn't figure out how to change my compiz theme, and now I can!

---

### Post by strumluff on 2007-05-15
Is there a method to theme the window decorations of compiz on amd64? 

Cheers all  :D

---

### Post by Kevin on 2007-05-15
yes, there is.  I included the source package, its linked to rapidshare.  All you have to do is extract the archive, enter the directory in a terminal, and execute the command ```
dpkg-buildpackage -rfakeroot
```

That'll do it if you have all the dependencies installed.  If you don't, ```
sudo apt-get install build-essential fakeroot
``` should get you the basics, and a ```
sudo apt-get build-dep compiz
``` should get you the other necessary parts.  Then execute the previous command.

It should produce a .deb package for you.  Install it, and if it works, post it to the forum to share :)

---

### Post by strumluff on 2007-05-16
Well doing ```
 sudo build-dep compiz
``` can't find a source package.

I downloaded your source files however I can't seem to extract them in a way so that when I run ```
dpkg-buildpackage -rfakeroot
``` it doesn't give me this output: ```
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is

```

---

### Post by Kevin on 2007-05-16
Hmm, I must have uploaded the wrong archive.  instead of downloading it on dial-up, I just uploaded a proper one.  I attached the diff.gz, .dsc, and .orig.tar.gz files now, so re-read the building from source section and that should fix it :)

---

### Post by strumluff on 2007-05-17
Still not working, 

running ```
 dpkg -x emerald_0.3.0~git20070426-0test0.dsc 
```

gives this output:

```
dpkg-deb: --extract needs a target directory.
Perhaps you should be using dpkg --install ?
```

Adding a path as the target dir is unsuccessful also with this output:

```
dpkg-deb: `emerald_0.3.0~git20070426-0test0.dsc' is not a debian format archive
```

---

### Post by Kevin on 2007-05-17
Sorry, my bad, that should be dpkg-source -x...  Fixed :)

---

### Post by strumluff on 2007-05-18
Just one more correction, that is the source file from rapidshare needs to be renamed with a ~ instead of a - after emerald_0.3.0 in order for the dpkg-source -x command to work.

Apart from that builds debs successfully, installs successfully and works a treat! Thanks a lot now I have a stable compiz and the window borders that I always wanted :P

If these amd64 debs will work on all other amd64 machines then i can send you the files to host if you like. Not sure if it builds generally for the architecture or for my specific machine

All thats left for you now are my thanks and please keep us posted if you find a way to get it working with 0.5 :)

Thanks again

---

### Post by Kevin on 2007-05-20
thanks, I'm uploading a source file with the correct naming now.

And yes, those packages should work on any AMD64 system.  They should be small enough to post on the forum, so it'd be great if you just attached them here!

---

### Post by strumluff on 2007-05-20
No problem, attached are the 3 amd64 packages.

---

### Post by fsSnowboard on 2007-05-23
I was just on the [Compiz forum]("http://forum.compiz.org/viewtopic.php?t=700&highlight=theme") and found out that there is now a patch to [fix the blur effect]("http://sukimashita.com/temp/10-emerald-add-decoration-blur-support-2.patch").

---

### Post by Kevin on 2007-05-23
Either way, I don't believe 0.3.6 has the new blur plugin.  If you want blur effects, you'll have to upgrade to 0.5.0

---

### Post by schnupi on 2007-05-24
> **fsSnowboard said:**
> I was just on the [Compiz forum]("http://forum.compiz.org/viewtopic.php?t=700&highlight=theme") and found out that there is now a patch to [fix the blur effect]("http://sukimashita.com/temp/10-emerald-add-decoration-blur-support-2.patch").


cool thanks i'd love to try it out but how do i apply a .patch file? i read the forum posting and it said it worked with 0.36 but didnt do a great job at explaining how to apply the patch

---

### Post by Kevin on 2007-05-24
Well, you can try seeing if it works by adding it to the debian/patches directory of my source package, then just following the same directions to compile from source.  But likely it will give you errors, as I don't believe that patch still applies cleanly.  You'll need to look through the patch file, figure out where there is stuff added, add it manually, and create a patch that way likely.  That's the way I did it for my patch.

If no one gets anywhere on it, I can look into it when I have time, but for now I'm on dialup until September, and don't have much time.  ( who's idea is it to make summer jobs more work than school? )

---

### Post by schnupi on 2007-05-25
> **Kevin said:**
> Well, you can try seeing if it works by adding it to the debian/patches directory of my source package, then just following the same directions to compile from source.  But likely it will give you errors, as I don't believe that patch still applies cleanly.  You'll need to look through the patch file, figure out where there is stuff added, add it manually, and create a patch that way likely.  That's the way I did it for my patch.

If no one gets anywhere on it, I can look into it when I have time, but for now I'm on dialup until September, and don't have much time.  ( who's idea is it to make summer jobs more work than school? )


ermm... yea the blur problem really isnt that much of a problem.. thanks though:)

---

### Post by Elcoco on 2007-05-25
I was able to get everything working except emerald, it gives this error if I run emerald-> emerald: Could not acquire decoration manager selection on screen 0 display ":0.0", and if i run emerald --replace it just hangs and never does anything. any ideas?

---

### Post by strumluff on 2007-05-26
> **Elcoco said:**
> I was able to get everything working except emerald, it gives this error if I run emerald-> emerald: Could not acquire decoration manager selection on screen 0 display ":0.0", and if i run emerald --replace it just hangs and never does anything. any ideas?

did you kill gtk-window-manager?

```
 killall gtk-window-manager
```

before you run emerald

---

### Post by dmoney on 2007-05-28
Thanks. This works great.

Also, the easiest way to get emerald to start instead of gtk-window-decorator is to replace the command in compiz's config. There are two ways:


1) Using gconf-editor:

Open a terminal or a run prompt and type:
```
gconf-editor
```

Open apps > compiz > plugins > decoration and change the command setting to:
```

emerald --replace
```
...and **IMPORTANT** uncheck the mipmap setting.

2) Using compiz-settings-manager:
If you have compiz-settings-manager installed, browse to System > Preferences > Compiz Settings Manager

Click on the decoration button and replace :
```
Command: gtk-window-decorator
```
with:
```

emerald --replace
```

And **IMPORTANT** uncheck the mipmap setting. For some reason, the command will fail to load if you do not.


Logout and back in and emerald should start up on its own. This saves gtk-window-decorator from loading in the first place...should make logging into your session a little smoother.

---

### Post by strumluff on 2007-05-28
Nice idea man, wasn't aware of a decorator variable in the compiz config :rolleyes:

---

### Post by schnupi on 2007-05-28
hmm it doesnt seem to work for me for some reason even though ur method makes sense

---

### Post by dmoney on 2007-05-28
> **schnupi said:**
> hmm it doesnt seem to work for me for some reason even though ur method makes sense

Did you uncheck mipmap?

---

### Post by schnupi on 2007-05-28
yap but it wasnt checked in the first place

---

### Post by dmoney on 2007-05-28
> **schnupi said:**
> yap but it wasnt checked in the first place

Odd. Make sure there's nothing in Sessions calling gtk-window-decorator or anything else. Then try killing gtk-window-decorator and restarting X to and see if that does it.

Edit: on reboot this doesn't seem to work...just when on logout and back in. gtk-window-decorator is being called somewhere else. need to find out where that is and replace the command. I'll look around and repost in here.

---

### Post by dmoney on 2007-05-29
Moving /usr/bin/gtk-windowdecorator to gtk-window-decorator.old and making a symlink for /usr/bin/emerald to /usr/bin/gtk-window-decorator does the trick for now.

```

cd /usr/bin
sudo mv gtk-window-decorator gtk-window-decorator.old
sudo ln -s emerald gtk-window-decorator

```

---

### Post by nullwert on 2007-05-29
Well, just wanted to mention that I have been experiencing the same problems as dmoney after having installed the amd64 packages from above.

Edit:
> His workaround fixed it finally. (Thanks, btw. :) ) Still, I'd like to know too what is starting gtk-window-manager before the gconf-settings take effect. I couldn't find it yet. If anyone is having an idea, please post. Thanks.

Well, I was over-enthusiastic, it seems. The quote is my unedited posting, now I have to admit that it seems Emerald had been loading, but not quite correctly. Main problem being that I could not change themes, Emerald Theme Manager would not respond. Also other Compiz settings seemed to change when using the Emerald workaround, like suddenly very dark shadows in Compiz or Window Shadows disappearing completely (Compiz ran though, since the Wobbly effect still worked.) I give up for the moment, hope someone has an idea.

---

### Post by strumluff on 2007-05-29
I have had absolutely no problems with Emerald on my amd64 system. Emerald doesn't switch themes when you select them from the theme manager, but all you have to do is use ```
emerald --replace
``` and the decorations will switch to the selected theme. 
I haven't had time to try these load workarounds yet, still using a startup script to kill gtk-window-decorator before loading emerald. When I get a chance to play around I'll post back my results.

---

### Post by timpisti on 2007-05-30
I'm newbie too, I just ask, that emerald deb packages on the first page are updated with 'blur-support-patch', what I found here:
[http://forum.compiz.org/viewtopic.php?t=700&postdays=0&postorder=asc&start=0]("http://forum.compiz.org/viewtopic.php?t=700&postdays=0&postorder=asc&start=0")?
Except that blur effect, everything goes fine & nice!

---

### Post by nullwert on 2007-05-30
Guess I finally figured what's happened yesterday. Obiously my fiddling around with Compiz/Emerald settings somehow can lead to changes in gconf Compiz settings. That's why suddenly desktop effects disappeared. What exactly has caused this I don't know.

As the total noob I still am it also took some time for me to understand that you must take care to add Compiz addons in gconf in the correct order or they will not be displayed/saved at all. That confused me as well quite some time... :roll:

Now using a startup script running the kill gtk-window-decorator + emerald --replace works just fine.

Thanks to strumluff to mention I had to run emerald --replace again for loading a new skin.

Still I'd like to know what is causing gtk-window-decorator to be loaded in the first place. Is it because of the compiz wrapper:

```

$man compiz

DESCRIPTION
       compiz  is  a wrapper around the real compiz.real binary that automati&#8208;
       cally sets up everything needed to properly run compiz on a Debian sys&#8208;
       tem.

       In  order  to use the X server’s accelerated indirect rendering (AIGLX)
       capabilities, the wrapper will call compiz.real with the necessary com&#8208;
       mand-line arguments.

       If  the package compiz-gtk is installed, the wrapper will automatically
       start the gtk-window-decorator.

```

But deselecting compiz-gtk package in Synaptic will try to uninstall compiz completely... (remember: me = noob ;-) ) Also the part with gtk-window-decorator seems to be commented out anyway if I read the code in /usr/bin/compiz correctly.

---

