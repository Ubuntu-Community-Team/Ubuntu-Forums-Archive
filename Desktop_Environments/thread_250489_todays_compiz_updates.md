---
title: "todays compiz updates"
date: 2006-09-04
forum: Desktop Environments
---

### Post by milkmaid on 2006-09-04
after just installing the new compiz updates, i got compiz pooping out these errors.

compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0



anybodys got experience with this? (nd knows what i can do to fix this?)
cheers.

---

### Post by tribaal on 2006-09-04
Hum todays updates broke my XGL/compiz setup as well... Hope this is fixable more or less easily :)

- trib'

---

### Post by turbojugend_gr on 2006-09-04
I also di update my system, today, but compiz runs smoothly. Did you have any restart or anything like that, or the problem occured after the update, sharp?

---

### Post by FireFly3k on 2006-09-04
I also just updated Compiz and it doesn't work anymore after a reboot :(
When I enable GL Desktop the borders of the windows dissapear, I don't get any errors and I can't find anything in log files.

I run AIGLX with Compiz. I hope there is a solution to this problem.

---

### Post by crazy___cow on 2006-09-04
I have the same problem with AIGLX and Compiz on i915.

---

### Post by kapesch on 2006-09-04
I didn't get an error directly after the update but after starting an Xgl session I found it no longer working ](*,). I don't know if its related but i am missing alot of key entries in gconf-editor under /apps/compiz.

---

### Post by erkki70 on 2006-09-04
Hi there,
Same over here, xgl + compiz on ati card (infamous IGP340M) is broken :-(
First time this happens to me after upgrading...
Hope there's a quick fix to that.

Cheers,

Erkki

---

### Post by PathSpace on 2006-09-04
Man, I'm sure glad that I noticed this thread before I updated!  I hope it's fixed soon; maybe another update will come out which fixes people's broken Compiz...

---

### Post by markthecarp on 2006-09-04
I picked up the update as well but haven't restarted Xgl/Compiz yet. At least I won't be surprised if it's broken. I won't have time to check on it this morning. I've got to labor on Labor Day. Off to make some sawdust...

-mark

---

### Post by jeremytaylor on 2006-09-04
Okay, a little googling reveals that a fair number of changes have taken place. Essentially the way all the preference are stored and edited has now been put in a neat little app called csm. 

Now to start compiz you need to run the command 
```
compiz-start
```
you can put it in startup your session. To change behaviours you now use csm. 

Now I'm not sure how all this works. I seem to have lost plugins like transset in the process and my panels are no longer pretty and translucent. So if anyone figures out what I should be doing then please let us know. 

Jeremy

---

### Post by Dinerty on 2006-09-04
Ok guys heres how I fixed my xgl/compiz after todays new updates, did abit of searching around on these forums and on compiz.net and found that the new updates use "csm" instead of gconf now:

```
compiz-start
```

then

```
chmod 755 ~/.compiz -R
```

then

```
csm
```

Configure everything to way it was before, then finally add this line to your "Sessions > Start up programs"

```
/usr/bin/compiz-start
```


**Big thanks to all the guys on here and compiz for this quick fix !

---

### Post by Mike-Bell on 2006-09-04
when I set-up the settings on csm, it are not saved. Re-opening again shows me that nothing was changed. Any ideas?

---

### Post by Dinerty on 2006-09-04
> **Mike-Bell said:**
> when I set-up the settings on csm, it are not saved. Re-opening again shows me that nothing was changed. Any ideas?

```
chmod 755 ~/.compiz -R
```

---

### Post by Mike-Bell on 2006-09-04
Greeeeeat :D ;)

---

### Post by milkmaid on 2006-09-04
yea that did the trick !
good.
thanks alot.

but indeed the panels have gotten a new look.. 
most plugins seem to be working still, however the water plugins wont, but then again ive never got them working in the first place.

---

### Post by FireFly3k on 2006-09-04
thnx Dinerty!!! =D>

---

### Post by erkki70 on 2006-09-04
Yep!
It did the trick :-)
Just need to set up everything again through the new configuration tool (csm looks good!).
Thanks all.

---

### Post by dexter on 2006-09-04
> **Dinerty said:**
> Ok guys heres how I fixed my xgl/compiz after todays new updates, did abit of searching around on these forums and on compiz.net and found that the new updates use "csm" instead of gconf now:


Thanks a lot Dinerty, got my xgl back online with this. 
I have one question though, what does this exactly do (i still need to learn a lot about linux :p):
```
chmod 755 ~/.compiz -R
```
I believe it changes the permissions in the homefolder/.compiz ?

---

### Post by Lunar_Lamp on 2006-09-04
You might want to google for help on chmod to work out what the 755 means (from memory the man-page isn't particularly helpful for that).  The man-page for the option -R is useful though:

> -R, --recursive
              change files and directories recursively


Not sure how helpful you will find this, but here is a link explaining how the numbered options work (I'm sure it makes it seem more complicated than it is though):
[http://www.catcode.com/teachmod/numeric.html](http://www.catcode.com/teachmod/numeric.html)

---

### Post by Dinerty on 2006-09-04
> **dexter said:**
> Thanks a lot Dinerty, got my xgl back online with this. 
I have one question though, what does this exactly do (i still need to learn a lot about linux :p):
```
chmod 755 ~/.compiz -R
```
I believe it changes the permissions in the homefolder/.compiz ?

Heres a nice guide about what chmod does and what them numbers mean after, basicsally the numbers determine the type of access you have to the file/directory

0 = none
7 = full

[http://www.reallylinux.com/docs/files.shtml](http://www.reallylinux.com/docs/files.shtml)

---

### Post by viraptor on 2006-09-04
Ok - csm privilages were b0rked - now it works. Kind of...
I don't know why, but compiz tray icon can't turn gl desktop on. Only today I uninstalled some old quinn package that did previous tray icon - that one worked ok.
Now it tries to start the compiz, but seems like it fails and I'm left with no manager.

---

### Post by SlugO on 2006-09-04
Is there a quick way to switch Compiz off anymore?
Except for starting compiz-tray-icon which ironically now only shuts Compiz :biggrin:

---

### Post by SmasSive on 2006-09-04
Thanks for all the tricks guys!

After bring up compiz, explanation bubbles shows ok but my "clicks" with mouse doesn't do anything! I can't open a terminal for example...

I have a ati 9500PRO with open source drivers and aiglx... anybody with the same problem?
NOTE: I disabled blur plugin.

Thanks!

---

### Post by Random Roadkill on 2006-09-04
thanks guys! it now works :D
am i right in replacing compiz-start.py with /usr/bin/compiz-start, in the session startup and removing compiz-tray-icon?

---

### Post by hexion on 2006-09-04
If you want to have previous gnome menu effect (and not that jelly-like one), simply do this:

- Open csm (or gset-compiz in previous version)
- Go to "minimize efect" (or minimize plugin in prev. version)
- In the left menu, select "Multiple Choice"
- Mark "UNKNOWN" window type

That's all ;)

---

### Post by nikopol on 2006-09-04
For some reason there was a conflic between the tray icon and the new install so I had to remove the tray icon from the startup list.

Now, however, I'm unsure how to change themes. Any ideas?

---

### Post by hexion on 2006-09-04
> **nikopol said:**
> For some reason there was a conflic between the tray icon and the new install so I had to remove the tray icon from the startup list.

Now, however, I'm unsure how to change themes. Any ideas?

Menu - System - Preferences - CGWD Themer

---

### Post by nikopol on 2006-09-04
Aha - didn't realise it had added a menu in there. Thanks.

Whilst I'm at it, any idea how to make the gnome menu, tooltips, firefox bookmarks etc behave normally (i.e. without the slow xgl maxmimise)? :D

---

### Post by hexion on 2006-09-04
> **nikopol said:**
> Aha - didn't realise it had added a menu in there. Thanks.

Whilst I'm at it, any idea how to make the gnome menu, tooltips, firefox bookmarks etc behave normally (i.e. without the slow xgl maxmimise)? :D

As I said above, you can change that behaviour here:

>  If you want to have previous gnome menu effect (and not that jelly-like one), simply do this:

- Open csm (or gset-compiz in previous version)
- Go to "minimize efect" (or minimize plugin in prev. version)
- In the left menu, select "Multiple Choice"
- Mark "UNKNOWN" window type


To deactive it completely, I think you should uncheck something in compiz plugins, but I don't know exactly where.

---

### Post by nikopol on 2006-09-04
I'd already done that tho' - it removed the slow wobble but with a little poking around I found that upping the speed (under Numeric Values) to around 2.0 removed the slowness of the menu issue.

---

### Post by SlugO on 2006-09-04
It's nice to have more options but obviously usability wasn't one of the goals of this new settings program.

Where on earth can I change what happens when I move the mouse pointer to each corner? I hate having the windows move around when I just throw the mouse pointer to the corner where my program menu is :mad:

---

### Post by Mike-Bell on 2006-09-04
I can't run the zoom feature, changing key associations and nothing. It's my problem?

---

### Post by tribaal on 2006-09-04
To change any setting with csm, you need to

```
chmod 755 ~/.compiz -R
```

This will make the directory writable, and so your changes will be saved.

Hope this helps.

- trib'

---

### Post by jeremytaylor on 2006-09-04
> **SlugO said:**
> It's nice to have more options but obviously usability wasn't one of the goals of this new settings program.

Where on earth can I change what happens when I move the mouse pointer to each corner? I hate having the windows move around when I just throw the mouse pointer to the corner where my program menu is :mad:

open csm, goto scale and then action binding. untick the actions you don't want
jeremy

---

### Post by nilrem on 2006-09-04
Hello Everyone!

I am relatively new to all this, but I had gotten the compiz stuff working on another computer, so I figured I would try it again. (Trying to convert my windows friends)

I have installed everything via the numerous HOWTOS out there; I get my little rd box in the corner to turn on or off the gl-desktop so I would assume at that point everything is working... 

Well when I enable it, my windows loose their title bar and become unmovable. Also none of the effects appear.

I tried the solution posted here but when I try to chmod that dir it tells me that the dir cannot be found.

Please help,
Thanks,
Kevin

---

### Post by tribaal on 2006-09-04
Try running "csm" once first (csm is the new configuration interface for compiz).

This will most certinly create an empty ".compiz" folder in your home dir, which you'll have to chmod, and then the changes you'll make in csm will be taken into account.

Hope this helps :)

- trib'

---

### Post by nilrem on 2006-09-04
tribaal,

ok I tried that, it brought up the compiz settings manager 0.3, but it seems to have the ie no picture picture on all the menu buttons; I then close that and run the chmod to get tthe smae resault, cannot find Dir.. 

Thanks,
nilrem

UPDATE:
I went to the terminal and typed compiz-start this error came up...

nohup: appending output to `nohup.out'
/usr/bin/compiz-start: line 21:  6788 Aborted                 nohup cgwd --replace

---

### Post by jeremytaylor on 2006-09-04
does anyone know how to set the panel transparency with csm?
thanks
Jeremy

---

### Post by spiechu on 2006-09-04
but if somebody of you is using AIGLX instead of XGL?

im using AIGLX on Radeon 9200SE. I'm tried to do as written above, but compiz crashes :/

---

### Post by ButteBlues on 2006-09-04
I tried Dinerty's instructions, but on the chmod command, I get a no Directory error.

Please help - not even rolling my compiz packages back solved this. :(

---

### Post by nilrem on 2006-09-04
ok, apperently I need a reboot then to run the directions mention above.. it works now.. and boy is she pretty.. but she's a bit slow.

My system is a 
AMD 2000xp+
1.5 gigs of ram
Radion 9200 128meg

Scrolling on a web page is acting like I'm on dialup running win 95 trying to view a page full of thumbnails.

Bringing up a menu takes a good 2 minutes. 
I turn off the settings and everything runs great, so I guess I'm asking is there any tips or posts that can help my get my pretty baby off the short bus?

Thanks,
Kevin

---

### Post by ButteBlues on 2006-09-04
UPDATE: Running compiz-start gives the following

> The application 'cgwd' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

It might just be me, but that sounds kind of... euh, bad. ^_^;

---

### Post by spiechu on 2006-09-04
it's working :) bu i still don't know how i done it :/

---

### Post by oocce on 2006-09-04
Now works!

Anybody have made "toggle"-scirpt??!

---

### Post by ButteBlues on 2006-09-04
oocce - Just use the terminal with "compiz-start" and "metacity --replace" for the time being until gnome-compiz manager is repaired.

ALSO, everyone should update to the .44 release from a few minutes ago. It fixes lots, however, on my end, it is unbearably slow. :/

---

### Post by John.Michael.Kane on 2006-09-04
a simple façade your advacating that everyone update. When the lastone  **fouled** up almost every known compiz-startup script,and theres no known working script.

---

### Post by ButteBlues on 2006-09-04
SD - The last update (.43) would not work no matter what on my system.

.44 update now runs compiz without ANY issues except for the slowness.

---

### Post by toasted on 2006-09-04
Im glad I missed that one! My compliz is still working ok  :) 
This last one came out within the hour eh?

---

### Post by ButteBlues on 2006-09-04
> **toasted said:**
> Im glad I missed that one! My compliz is still working ok  :) 
This last one came out within the hour eh?
I read about it on the compiz.net forums and updated immediately.

So yeah, about within the hour.

---

### Post by turbojugend_gr on 2006-09-04
Well at this time I noticed having the problem (after a restart).

I did this though and everything is just as before the updates. Notice excactly, no issue here, no lost modfications or anything.

First of all I use a starter to get compiz starting, by simply executing compiz-start by clicking it, for those that have compiz started at startup a reboot is needed.

Well it was as simple as: 1. starting the update manager
                          2. clicking to search for updates.
                          3. (found 3, compiz-core,compiz-plugins,another one about compiz...lol)
                          4. updating, and starting compiz (or rebooting for you).


Everything works like a grace again. Ubuntu spirit, they never sleep.....lol

---

### Post by canter690 on 2006-09-04
Has anyone noticed that the icons in csm appear broken. The General Options, Benchmark, Blur etc have a icon which looks like a simple window with a red X in it.

---

### Post by neymac on 2006-09-04
> **canter690 said:**
> Has anyone noticed that the icons in csm appear broken. The General Options, Benchmark, Blur etc have a icon which looks like a simple window with a red X in it.

It's the same way here.

---

### Post by bullgr on 2006-09-04
thanks Dinerty...
all works great again :mrgreen:

---

### Post by iam_foo on 2006-09-04
bah..you br0ke my b0x.

wtf?

:twisted:

---

### Post by PathSpace on 2006-09-04
> **iam_foo said:**
> bah..you br0ke my b0x.

wtf?

:twisted:

What do you mean?  Did you just update and it not work?

I'm REALLY paranoid about upgrading and would really like an opinion on whether or not I should.  I'm using Intel i910 with AIGLX.  

If I *do* upgrade, should I dist-upgrade (because compiz-plugins is held back on upgrade)?

---

### Post by ButteBlues on 2006-09-04
The ~/.compiz folder appears once you change any setting in csm and quit. It's new. ;)

AIGLX compiz broke earlier today, but since .44, it has worked great. I would suggest disabling blur altogether though, before hand, since Compiz lagged severely with it on.

---

### Post by PathSpace on 2006-09-04
Thanks a simple facade.  :)

I think I'll upgrade.  Here goes nothing.  :p  Lol.

---

### Post by toasted on 2006-09-04
I made the update early this morning and did the change to csm. Now there is another update called .44. Has anyone installed this update and NOT gotten very slow after?

I am holding off on that .44 update for now till more info is known

---

### Post by PathSpace on 2006-09-04
The following packages have been kept back:
  compiz-plugins

Should I force this with a dist-upgrade, or let it be?  :confused:

---

### Post by Ciego on 2006-09-04
Thanks for the timely help Dinerty.  I was just tinkering with my eye candy after the update and rebooted after that so I though I had really messed things up ....... whew.

---

### Post by PathSpace on 2006-09-04
Grr..performance is TERRIBLE now, even though I turned off "Blur."  Performance used to be quite good, too.  ](*,) ](*,) 

Any ideas??

EDIT:  Nevermind...just had to restart X.  ;) :D

---

### Post by hexion on 2006-09-04
> **PathSpace said:**
> The following packages have been kept back:
  compiz-plugins

Should I force this with a dist-upgrade, or let it be?  :confused:

Do this:
sudo aptitude install csm compiz-plugins

Then change your start script to:
compiz-start

And customize your options in csm (your options in gset-compiz won't be used anymore)

---

### Post by Freedreamer on 2006-09-04
i got this error on csm:
** ERROR **: couldn't get dbus.
aborting...
Aborted

any idea?

all is slow with these updates. I use aiglx with an intel card :(

---

### Post by beercz on 2006-09-04
> **Freedreamer said:**
> i got this error on csm:
** ERROR **: couldn't get dbus.
aborting...
Aborted

any idea?

all is slow with these updates. I use aiglx with an intel card :(
Me too :-(

Also whilst logging into my default gnome session (set up with compiz) I get a blank light blue screen ](*,) 

Help!!!

---

### Post by jimmygoon on 2006-09-04
For all of you people DIEING from Performance. TURN OFF THE BLUR PLUGINTURN OFF THE BLUR PLUGINTURN OFF THE BLUR PLUGINTURN OFF THE BLUR PLUGINTURN OFF THE BLUR PLUGINTURN OFF THE BLUR PLUGINTURN OFF THE BLUR PLUGINTURN OFF THE BLUR PLUGINTURN OFF THE BLUR PLUGINTURN OFF THE BLUR PLUGIN

I don't know why quinn sets it on as default seeing as it seems to kill many grafix card... but none the less....

TURN OFF THE BLUR PLUGIN
TURN OFF THE BLUR PLUGIN
TURN OFF THE BLUR PLUGIN

for better performance...

enjoy!

---

### Post by EnderTheThird on 2006-09-04
I got everything working now, but compiz doesn't seem to be refreshing windows correctly.  For example, window outlines, and elements within those windows (like the file menu toolbar), won't appear correctly (if they're shown at all at first) until I focus and/or move that particular window.  Any ideas for fixing this?  Also, for now I have all plugins enabled except:

Benchmark
Blur
Fade

Fade seemed to be keeping window "shadows" present after closing or minimizing them.  I'm assuming that was the problem, because it seems to have stopped after disabling it.  But this thing with the windows and their elements not refreshing correctly is kinda annoying...

---

### Post by toasted on 2006-09-04
So has anyone installed the .44 updates with no trouble?

---

### Post by zigx on 2006-09-04
> **jeremytaylor said:**
> Okay, a little googling reveals that a fair number of changes have taken place. Essentially the way all the preference are stored and edited has now been put in a neat little app called csm. 

Now to start compiz you need to run the command 
```
compiz-start
```
you can put it in startup your session. To change behaviours you now use csm. 

Now I'm not sure how all this works. I seem to have lost plugins like transset in the process and my panels are no longer pretty and translucent. So if anyone figures out what I should be doing then please let us know. 

Jeremy

my compwiz was broken as well but i added compiz-start to my session start up apps and it works fine now.

---

### Post by Uncle Spellbinder on 2006-09-04
> **toasted said:**
> So has anyone installed the .44 updates with no trouble?

No problems at all, except those I created for myself. A few glitches earlier. Disable *blur* and all is working primarily as it did before. Since gconf is no longer being used by Compiz, I have to manually add my old gconf settings to the new CSM one at a time. That's a pain. But this is, after all, alpha software. I'm quite happy. Hats off to Quinn, she's doing a hell of a job!

---

### Post by ronmarley1 on 2006-09-04
Well, got it working again.  Added compiz-start to Sessions->Startup Programs and  disabled compiz-tray-icon.  Turned off blur, and seems to be where it was, but just a tad bit slower.  I'm running aiglx on Intel 855GM on an IBM R51 ThinkPad.

---

### Post by one_stinky_bum on 2006-09-04
Sweet. Compiz on the i915 + AIGLX is now working here with Quinn's latest packages. The only question I have is how to get the default theme back... you know, the simple one with a grey border and nice simple minimize, maximize and close controls.

'piz seems snappier for me, although this update didn't fix hibernate for me (logout now works). I must say that the csm utility is quite opposite of user friendly... but I'm not complaining! 

Thanks.

---

### Post by mighel on 2006-09-04
Thats what worked for me

 went into System-Preferences-Sessions and under startup programs cg#hanged startcompiz to compiz-start like was suggested

voila

I have XGL back

 Was astounded how much I missed it:)

---

### Post by dunomous on 2006-09-05
Default snapping for me has never worked. Anyone else have this issue, or offer any fixes?

---

### Post by iam_foo on 2006-09-05
i realize this is minor.. i finally have aiglx working on lptop again..
iz there anyway to change the top of the cube back to the image i had?

ne help iz much appreciated.

tx.

:twisted:

---

### Post by dm@n on 2006-09-05
start csm from a terminal and add all your old settings there.. (cube)

Running aiglx xorg-air + compiz on my laptop intel 945, just want to add that this is more like performace when compared to Xgl (on this laptop)

---

### Post by danhm on 2006-09-05
double post, see below.

---

### Post by danhm on 2006-09-05
I am still without window borders, and none of my keyboard shortcuts seem to do anything (like ctrl+alt+click for the cube). Also, when I try to switch viewports, nothing happens.

I followed [the guide](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper) in the Unoffical ATI Linux Driver Wiki to install XGL/Compiz.

I've tried everything mentioned in this thread, but it's still not working. Any suggestions?


I have a Dell Inspiron e1505, by the way. With a Radeon X1400.

---

### Post by necr0man6er on 2006-09-05
> **EnderTheThird said:**
> I got everything working now, but compiz doesn't seem to be refreshing windows correctly.  For example, window outlines, and elements within those windows (like the file menu toolbar), won't appear correctly (if they're shown at all at first) until I focus and/or move that particular window.  Any ideas for fixing this?  Also, for now I have all plugins enabled except:

Benchmark
Blur
Fade

Fade seemed to be keeping window "shadows" present after closing or minimizing them.  I'm assuming that was the problem, because it seems to have stopped after disabling it.  But this thing with the windows and their elements not refreshing correctly is kinda annoying...

Yes, i'm having the same problem here, don't have a solution for it yet. It happened after i installed the gnome-compiz-manager and afterwards removed it.
tonight i'm going to try to remove ~/.compiz and start csm again.
Maybe there will be another update that fix this.
If anyone had the same problem and solved this, please share with us.

---

### Post by dunomous on 2006-09-05
I hate to add fluff to this thread since this may have nothing to do with it, but suppose it could be 5.10 specific? I highly doubt myself, but you never know...

---

### Post by nilrem on 2006-09-05
Ok, can someone point me in the right direction for this.. 
I just did a reinstall on this system, got everything upgraded and installed.

when I run compiz-start it gives no errors, I chmod the dir with no errors, so I would assume that everything is installed correctly.

Well I get no spfx now. no wobbly windows, no spinny cube, just some rain on my parade.

Anyone have any idea what I'm doing wrong?

TIA,
nilrem

---

### Post by toasted on 2006-09-05
This will fix the next to last update....  compliz now uses a different config tool 

[http://ubuntuforums.org/showpost.php?p=1460710&postcount=11](http://ubuntuforums.org/showpost.php?p=1460710&postcount=11)

---

### Post by beercz on 2006-09-05
> **toasted said:**
> This will fix the next to last update....  compliz now uses a different config tool 

[http://ubuntuforums.org/showpost.php?p=1460710&postcount=11](http://ubuntuforums.org/showpost.php?p=1460710&postcount=11)

Not for me:-(
See posts 63 and 64 in this thread, namely:

> i got this error on csm:
** ERROR **: couldn't get dbus.
aborting...
Aborted

---

### Post by monkeyhelper on 2006-09-05
I have a Intel 915 Chipset running AIGLX - here is how I fixed it after todays updates

1. Ensure you have the latest updates
apt-get update && apt-get upgrade

2. Ensure compiz dir is read/write'able
compiz-start
chmod 755 ~/.compiz -R
csm

3. Check System->Preferences->Sessions-Startup Programs has '/usr/bin/compiz-start' as the first entry - if not then add it and disable any other compiz start scripts you have in there

4.  Disable compiz-tray-icon in System->Preferences->Sessions-Startup Programs

5. Reboot

It looks like compiz-tray-icon (the red cube in the gnome-panel) doesn't work with the new compiz scripts, so until they fix this you can't use it to stop/start compiz/metacity -> anybody else see this problem ?


To improve performance run :

csm

and disable the blur, water effect and wobbly windows plugins (tweak to suit your settings)

---

### Post by The Pinny Parlour on 2006-09-05
I tried what was suggested and it still does not work.  This is what I get:
xxx@xxx-desktop:~$ compiz-start
gnome-window-decorator: no process killed
xxx@xxx-desktop:~$ compiz: Couldn't load plugin 'gconf'
chmod 755 ~/.compiz -R
chmod: cannot access `/home/xxx/.compiz': No such file or directory
xxx@xxx-desktop:~$ csm
xxx@xxx-desktop:~$


Any ideas on how I can get this all to work again?

I code compiz-start in terminal and the window borders disappear and that's it.  I have just updated to the latest.

---

### Post by monkeyhelper on 2006-09-05
pinny > Run csm first (I guess that creates the .compiz directory) and then chmod

---

### Post by The Pinny Parlour on 2006-09-05
ok thank you for your help.

I have restarted te PC...run csm, (which brings up a configuration window). <--Not sure what to do here so I have left it alone.

I have no idea what to do next.  I never had (or want now) compiz-start, automatically starting when the PC starts.  I just like to turn it on once in a while.  I still don't know how to kill the process yet either.    

Anyway I would like to get this working first.  I await some more suggestions.  :)

---

### Post by toasted on 2006-09-05
I havent found a way to kill it yet although I have asked both here and the compliz forum. Must be nobody knows. 

You can place the start script in your start sessions and have it on when you boot, but it doesnt sound like you want that. Hold on till you find a stop script... No other way right now I guess

---

### Post by beercz on 2006-09-05
When I do /usr/bin/compiz-start in a terminal window, I get:

> nohup: appending output to `nohup.out`
nohup: cannot run `gnome-window-decorator`: No such file or directory

The file nohup.out is empty:

However, it appears that compiz runs, my window border disappears, and I get the cube effect when I change viewports.

I can also run csm and change some effects.

However, when I log off or restart I am unable to run compiz (I end up with a coloured blank screen when I attempt to log on).

I have changed the permissions on my ~/.compiz directory to drwxr-xr-x (755).

Any idea as to how I can get compiz working again?

Thanks in advance.

---

### Post by The Pinny Parlour on 2006-09-05
Update:  Got it going, have no idea how.  

Thank you to those who have helped myself and others.

Thank you for showing me the **csm** window.  I never knew about that, I can configure the heck out of it now.  :)

---

### Post by toasted on 2006-09-05
What plug in controls the following?

Say I have a browser open and a few other things in the taskbar. When I move the mouse over the displayed window's item in the taskbar, everything dims except that window, the window moves slightly, and I cannot choose anything else till I go to that window and click it. 

Weird

I would like to turn off whatever it is....  
tia

---

### Post by ayoli on 2006-09-05
> It looks like compiz-tray-icon (the red cube in the gnome-panel) doesn't work with the new compiz scripts, so until they fix this you can't use it to stop/start compiz/metacity -> anybody else see this problem ?
you can make a little script metacity-run:
```
#!/bin/sh
kill -9 `pidof cgwd` && metacity --replace
```
then:
```
chmod a+x metacity-run
```
and create a launcher on the panel to run it, and another create launcher which should run /usr/bin/compiz-start
that's a bit ugly tweak but working. 
regards.

---

### Post by The Pinny Parlour on 2006-09-05
Just one more thing.  I used to be able to get water on command by hitting Ctrl+SuperKey, this does not work anymore.  I can get full rain drops with Shift+F9

Any ideas on how to get water on the mouse pointer?

---

### Post by toasted on 2006-09-05
> **ayoli said:**
> you can make a little script metacity-run:
```
#!/bin/sh
kill -9 `pidof cgwd` && metacity --replace
```
then:
```
chmod a+x metacity-run
```
and create a launcher on the panel to run it, and another create launcher which should run /usr/bin/compiz-start
that's a bit ugly tweak but working. 
regards.

Yes that works! Thank you
When I run the start up script again though, it the windows are all transparent (no trouble really cause when you move them they are ok)
But also, they may not behave quite the way they are supposed to. Such as you can close them but not minimize... once closed and opened again they are ok though....

Edit:
On further analysis....
I had FF and Evolution open but minimized to tray. Stopped Compliz then started. 

Stop
Both apps went open with metacity. 
minimized them again. 
started Compliz again
Both apps popped up again. 

Right clicking the app's item in taskbar showed that Evolution was still minimized even though it was displayed on the screen. Changing the state in the right click menu got everything working.

I guess then if you want to start compliz - close up the windows first is a sure fire way.

---

### Post by ayoli on 2006-09-05
i said it was a bit ugly :p
btw, it's a temp fix , i guess tray icon should work again on next updates.

---

### Post by toasted on 2006-09-05
> **ayoli said:**
> i said it was a bit ugly :p
btw, it's a temp fix , i guess tray icon should work again on next updates.

LOL

I ran the stop/start 2 or 3 times and it doesnt really like it. I paused inbetween and tried a few things.
After, things got REALLY slow and a couple of times I had processes shut down that I had to restart from a warning prompt.

The tray icon was related to gconf-editor and will have to be amended for csm now since that is the new manager. Maybe it will influence the processes directly... dunno.

There are a lot of bugs in csm... many plug ins that I try to enable/disable kills things and I have to reboot. Its annoying but hey, we are still in Alpha stage I think. At least it doesnt act like a Beta release......

---

### Post by turbojugend_gr on 2006-09-05
Well I have to post again,

for those still having problems the csm way, or for those that like an easier ,trouble & issue-free way--------->read my post on page 5, post #50, under this thread of course.

I have to mention again, it worked gracefully for me, it should for you too. I have not changed to csm neither had i lost my compiz prefs... I hope it works that way for everybody. This one is as "green user" as it get's. LOL I tried to find a more complicated way..... the devs thought otherwise though.

---

### Post by OffHand on 2006-09-05
I now use this script to toggle compiz.... well toggle... it starts compiz but it doesn't quit it. Instead it restarts compiz I think.

#!/bin/sh
if [ -f /usr/bin/cgwd ]
then
    nohup cgwd --replace &
else
    nohup gnome-window-decorator --replace &
fi

if ps -e | grep Xgl > /dev/null
then
    nohup compiz --replace dbus csm > /dev/null & exit;
else
    nohup compiz --strict-binding --indirect-rendering --replace dbus csm > /dev/null &  exit;
fi


Now my old script really worked as a toggle and I am sure the new one will be able to do that too. Also my old one had a nice graphical interface.
This is my old one. Maybe one of the smart folks knows how to make the ultimate compiz toggle script with these two  :mrgreen: 


#!/bin/bash
#
# Checks to see if process "compiz.real" is running.

pid=`ps --no-heading -C compiz.real | cut -d "?" -f1`;
if [ -n "$pid" ]; then
zenity --info --text="Turning off XGL Compiz effects. Replacing window thememanager with Metacity.";
kill -9 $pid
metacity --replace &
else
zenity --info --text="Turning on XGL Compiz wibbly wobbly windows effects";
cgwd &  compiz --replace gconf &
fi

---

### Post by ayoli on 2006-09-05
> **OffHand said:**
> I now use this script to toggle compiz.... well toggle... it starts compiz but it doesn't quit it. Instead it restarts compiz I think.

#!/bin/sh
if [ -f /usr/bin/cgwd ]
then
    nohup cgwd --replace &
else
    nohup gnome-window-decorator --replace &
fi

if ps -e | grep Xgl > /dev/null
then
    nohup compiz --replace dbus csm > /dev/null & exit;
else
    nohup compiz --strict-binding --indirect-rendering --replace dbus csm > /dev/null &  exit;
fi


Now my old script really worked as a toggle and I am sure the new one will be able to do that too. Also my old one had a nice graphical interface.
This is my old one. Maybe one of the smart folks knows how to make the ultimate compiz toggle script with these two  :mrgreen: 


#!/bin/bash
#
# Checks to see if process "compiz.real" is running.

pid=`ps --no-heading -C compiz.real | cut -d "?" -f1`;
if [ -n "$pid" ]; then
zenity --info --text="Turning off XGL Compiz effects. Replacing window thememanager with Metacity.";
kill -9 $pid
metacity --replace &
else
zenity --info --text="Turning on XGL Compiz wibbly wobbly windows effects";
cgwd &  compiz --replace gconf &
fi

your script is much prettier than mine ;) just one thing i haven't any process named compiz.real, now i've just got compiz and cgwd

---

### Post by toasted on 2006-09-05
see this link post 5 - toggle script (in progress) but it works!
[http://www.compiz.net/topic-3868-where-has-compiz-gone](http://www.compiz.net/topic-3868-where-has-compiz-gone)

```
#!/bin/bash
if ps -A | grep -e "Xgl$" > /dev/null; then
    if ps -A | grep -e "compiz$" > /dev/null; then

        if [ -f /usr/bin/cgwd ]; then
            killall cgwd
        else
            killall gnome-window-decorator
        fi

        killall compiz

        gnome-wm --replace &

    else

        if [ -f /usr/bin/cgwd ]; then
            killall cgwd
        else
            killall gnome-window-decorator
        fi

        compiz-start &

        setxkbmap -model pc104 -layout us
        xmodmap -e "keycode 22 = BackSpace Delete" &

    fi
fi
```

---

### Post by Thought_Criminal on 2006-09-05
Please forgive my stupid question, but is aiglx only for ATI cards?

I have an nvidia 6600gt and it just so happens I was going through a how-to on aiglx when my compiz crashed, I am not sure if installing aiglx or the update (or both)wrecked it.

---

### Post by Nycthbris on 2006-09-05
I updated, and fixed my configuration as stated earlier in the thread. I ran csm a few times but now when I try it all i get is:
```

XXX@XXX:~$ csm

** ERROR **: couldn't get dbus.
aborting...
Aborted
XXX@XXX:~$

```
I am running on a nvidia fx go5200 in an IBM G41 thinkpad
Any help would be great! Thanks

---

### Post by iam_foo on 2006-09-05
bleh.

everything w0rks great n0w.

tx

---

### Post by iam_foo on 2006-09-05
bleh.

everything w0rks great n0w.

tx

:twisted:

---

### Post by Jeremiah478 on 2006-09-05
Thanks this really helped get everything running again

---

### Post by Freedreamer on 2006-09-05
** ERROR **: couldn't get dbus.
aborting...
Aborted

same error....

---

### Post by r3dux on 2006-09-05
After today's updates (and admittedly, some script modification) I'm having the following issue on a Asus 5672 lappy (ATI 1400 Mobility):

I run the script to fire up compiz from a KDE session.. (because I don't really wanna run it as the one and only session atm)

[COLOR="Blue"]
#!/bin/bash
Xgl:1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer @
DISPLAY=:1
killall gnome-window-decorator
cgwd &
compiz-start --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
exec startkde
xmodmap /usr/share/xmod --rmap/xmodmap.uk -e keycode 22 = "BackSpace Delete"[/COLOR]

Running that, everything seems fine apart from the Desktop_Cube plugin, which only works to "flatten" not rotate the cube =/

However, if I replace [COLOR="Blue"]compiz-start[/COLOR] with just [COLOR="Blue"]compiz[/COLOR] in the above script the cube plugin works, though I can't see the Skydome (although it is working under "compiz-start" i.e. it's there in the background when the cube flattens). Looks like it's an issue with two sets of compiz preferences, one being broken in one way, and the second being broken in another wrt compiz/compiz-start?

I'd be very grateful if anyone could offer any help or advice on fixing this up (preferably under the new compiz-start kickoff).

BTW I've ran "chmod 755 ~./compiz -R", and although the skysphere file simple string doesn't appear in csm on closing and re-opening, it does exist in ~./compiz/csm_settings, and the keybindings to change cube <CTRL><ALT>left/right etc seem to be okay, and don't even work if I set them to other, simpler keys <CTRL>,/. etc

---

### Post by r3dux on 2006-09-05
a

---

### Post by Orta on 2006-09-05
Hello. Before the update, I had everything working smoothly. I had ClearLooks as my default theme. As a matter of fact, I never changed it since I installed Compiz/XGL, apparently Compiz just assumed the theme as I had it on my default GNOME session.

After this update, my beautiful ClearLooks vanished only to be replaced by some transparent borders along with invisible title text and minimize/maximize/close buttons. Also, all behaviour changes I made before, with gedit, are just gone, which means I'm stuck again with some annoying default effects. Yes, I do have a backup of my old settings.

How can I get my goodness back? Any ideas would be greatly appreciated. I still can't believe how poor this update was. I'm on a X700 Mobility by the way, running Dapper 6.06 LTS with the latest updates installed, on the 686 kernel.

Thanks for your help.

---

### Post by The Pinny Parlour on 2006-09-05
I just noticed there are compiz-plugins 0.15, csm 0.5 updates.

Just an earlier question:  I used to have the water ripples coming from the tip of my mouse by pressing Ctrl and SuperKey.  I know can't get that to work.  Any ideas how I can?   Normal rain drops work.   SuperKey is configured  but I think maybe csm is not set up right and that area where it indicates it may be the effect,  says disabled.  When I try to edit it, in csm, I quit and code csm again to see that my changes have not changed at all.

---

### Post by johnl on 2006-09-05
Hey guys, I have followed all the suggestions posted in this thread to get compiz (the .44 version) completely working again, but it just will not budge :( .

I have changed the permissions on the ~/.compiz directory, run csm and changed the settings, restarted X and ran compiz-start.

Here's the deal:
```

ledbettj@corgan:~$ ps aux | grep Xgl
root     11140  3.6 20.6 114748 106628 ?       RL   16:21   0:08 /usr/bin/Xgl :0 :0 -fullscreen -ac -accel xv -accel glx:pbuffer -auth /var/lib/gdm/:0.Xauth-nolisten tcp vt7
root     11141  0.5  2.7  17684 14056 tty7     RLs+ 16:21   0:01 /usr/bin/Xorg vt7 -auth /tmp/.Xgl-auth-5JTKlt -nolisten tcp :93 -terminate
ledbettj@corgan:~$ ps aux | grep compiz
ledbettj 11610  0.0  0.3   4036  2024 pts/1    S    16:23   0:00 compiz --replace
ledbettj@corgan:~$ ps aux | grep cgwd
ledbettj 11633  0.5  3.0  23964 15892 pts/1    S    16:24   0:00 cgwd --replace

```

compiz seems to be running and working, as I can right click on a window and change its opacity, brightness, etc. (although it does not seem to be following the settings in csm).

The issue is that cgwd will not decorate any windows.  There are no title bars.  The only way to move windows is to run metacity (--replace).  What happened to my totally sweet cgwd titlebars, and how can I get them back?

Thanks in advance!

---

### Post by r3dux on 2006-09-05
> **The Pinny Parlour said:**
> I just noticed there are compiz-plugins 0.15, csm 0.5 updates.

Just an earlier question:  I used to have the water ripples coming from the tip of my mouse by pressing Ctrl and SuperKey.  I know can't get that to work.  Any ideas how I can?   Normal rain drops work.   SuperKey is configured  but I think maybe csm is not set up right and that area where it indicates it may be the effect,  says disabled.  When I try to edit it, in csm, I quit and code csm again to see that my changes have not changed at all.

I can't get the ripples to work from mouse either, tho shift+F9 starts the downpour... since I also can't get csm to show up my entered + valid skydome string (tho it exists in ~/.compiz/csm_settings) - could be csm isn't working quite 100%? (even after chmod 755 -R'ing the dir?)

---

### Post by r3dux on 2006-09-05
Fixed it! Ugh! Stoopidity reigns.

Sorry to reply to myself, but here's the solution using compiz-start:

The Desktop_Cube plugin seems to not handle the cube rotation, which can be found in csm further down in the plugin list, and is for some reason disabled by default.

Tick the "Rotate Cube" check box to enable the plugin, then Robert's your Auntie's live-in lover...

i.e., Job done ;)

---

### Post by andnobodyslept on 2006-09-05
Hey all,
I've been trying to follow the advice in this thread but to no luck. The only thing I have been able to do is get back to metacity. The problem that keeps happening to me is that when I have compiz running my processor is maxed out and everything runs really slowly. Useing some of the advice I've seen so far I can get it to run normally but I don't have any of the headerbars, and can only run one application at a time. Does anyone have any ideas, I'm useing i810 Intel inegrated. Or does anyone one know of a possible update that is comming along?
Thanks

---

### Post by The Pinny Parlour on 2006-09-05
> **r3dux said:**
> I can't get the ripples to work from mouse either, tho shift+F9 starts the downpour... since I also can't get csm to show up my entered + valid skydome string (tho it exists in ~/.compiz/csm_settings) - could be csm isn't working quite 100%? (even after chmod 755 -R'ing the dir?)

Will try later:
[http://www.compiz.net/topic-3959-how-get-water-ripples-not-rain](http://www.compiz.net/topic-3959-how-get-water-ripples-not-rain)

---

### Post by Nokia on 2006-09-06
From my own experience with a Dell Inspiron 6400 laptop equiped with ATI Mobility Radeon X1400 HyperMemory. Besides doing the > chmod 755 ~/.cgwd -R thing running **csm** and **compiz-start**was not enough. I had to remove/disable **/usr/bin/startcompiz** from System-Preferences-Sessions-StartupPrograms and instead of  adding there > /usr/bin/compiz-start one must use > /usr/bin/compiz-start **--replace**. After doing all that everything went back to normal. 
My understanding is that there are more than one instalation posibilities of XGL right now, as shown by various HowTO's on Ubuntu forums'. Mine seems to be the one who runs XGL as a stand-alone server. Hope someone will benefit from my input here :)

P.S. Just a reminder: I'm not a linux expert, but I'm learning ;)

---

### Post by aussiedini on 2006-09-06
> **Nokia said:**
> From my own experience with a Dell Inspiron 6400 laptop equiped with ATI Mobility Radeon X1400 HyperMemory. Besides doing the  thing running **csm** and **compiz-start**was not enough. I had to remove/disable **/usr/bin/startcompiz** from System-Preferences-Sessions-StartupPrograms and instead of  adding there  one must use . After doing all that everything went back to normal. 
My understanding is that there are more than one instalation posibilities of XGL right now, as shown by various HowTO's on Ubuntu forums'. Mine seems to be the one who runs XGL as a stand-alone server. Hope someone will benefit from my input here :)

P.S. Just a reminder: I'm not a linux expert, but I'm learning ;)

Thanks Nokia, the last line, --replace was the one bit of the puzzle missing. Now it works

---

### Post by Nokia on 2006-09-06
Glad to be of assistance. :)

---

### Post by tribunal on 2006-09-06
Try to use compiz-themer again and restart compiz
After changing some params using CSM, I had to select theme again and restart compiz
And of course, check your ~/.compiz is writeable for usual user
This compiz is so unclean ](*,)

---

### Post by Nokia on 2006-09-06
For those in need to resolve this mater via SSH on for a needy friend, here's the same thing done in CLI. :)
> cd .config/autostart/ && ls -al 

You should see amongst other files **compiz-start.desktop** and **startcompiz.desktop**. 

Now run > vi compiz-start.desktop and add the missing [--replace] in **Exec=/usr/bin/compiz-start** line. It should look like this: **Exec=/usr/bin/compiz-start --replace**.

If someone has the **startcompiz.desktop** in the above mentioned directory/folder, make sure the the following line in the file looks like that: > X-GNOME-Autostart-enabled=**false**

---

### Post by hfdragon on 2006-09-06
> **hexion said:**
> Menu - System - Preferences - CGWD Themer

Strange, I don't have this menu ... am I the only one to have this problem ?

---

### Post by Nokia on 2006-09-06
> sudo apt-get install cgwd cgwd-themes cgwd-themes-extra
And there's no problem whatsoever ;)

---

### Post by hellfried on 2006-09-06
honestly i have tried my best to follow this thread and come away utterly confused. after updating the compiz upgrades 2 days ago (the one with csm), i have been getting error messages when i boot into dapper gnome (see attachments). the second screen capture is of my start up programs in sessions. i have disabled compiz-start.py (which was there when i first installed compiz) and /user/bin/compiz-start. the latest addition is the /user/bin/compiz-start --replace line which i added minutes ago following the instructions given in an earlier post. despite this i am still getting the same error messages when i reboot my pc. any ideas?

i am running compzi/xgl in dapper and my graphics card is a gecube ati x550pro.

---

### Post by Nokia on 2006-09-06
I don't have **compiz-start.py** in my StartUp Programs, but my guess is that you are not using the XGL-standalone server instalation, so there might be a chance that the .py should be left **enabled**.

---

### Post by toasted on 2006-09-06
> **hellfried said:**
> honestly i have tried my best to follow this thread and come away utterly confused. after updating the compiz upgrades 2 days ago (the one with csm), i have been getting error messages when i boot into dapper gnome (see attachments). the second screen capture is of my start up programs in sessions. i have disabled compiz-start.py (which was there when i first installed compiz) and /user/bin/compiz-start. the latest addition is the /user/bin/compiz-start --replace line which i added minutes ago following the instructions given in an earlier post. despite this i am still getting the same error messages when i reboot my pc. any ideas?

i am running compzi/xgl in dapper and my graphics card is a gecube ati x550pro.

Try disabling the compiz-start.py

What is that anyway, a custom script you installed?

Depending on how your compiz is installed also disable the
 /usr/bin/compiz-start --replace

---

### Post by hellfried on 2006-09-06
> **toasted said:**
> Try disabling the compiz-start.py

What is that anyway, a custom script you installed?

Depending on how your compiz is installed also disable the
 /usr/bin/compiz-start --replace

compiz-start.py is already disabled and so is /usr/bin/compiz-start because both of them caused the same error message. after adding and enabling /usr/bin/compiz-start --relace i still get the errors.

a few weeks ago i installed compiz/xgl by following this link : [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) (the second howto) and later i decided that i need that cool litte compiz icon sitting in my panel. so i followed this thread ([http://www.compiz.net/viewtopic.php?pid=11734](http://www.compiz.net/viewtopic.php?pid=11734)) and thats how i got compiz-start.py in my startup programs.

---

### Post by Nokia on 2006-09-06
> **Nokia said:**
> I don't have **compiz-start.py** in my StartUp Programs, but my guess is that you are not using the XGL-standalone server instalation, so there might be a chance that the .py should be left **enabled**.Did you try that ?

---

### Post by ayoli on 2006-09-06
i also had updatenotifier, gnome-volume-manager errors at start up after update two days ago, but since i've updated this morning i havent got these messages anymore.
btw, csm is quite unstable and alpha, and ofently crashes compiz.

---

### Post by The Pinny Parlour on 2006-09-06
So has anyone installed compiz-plugins 0.15 and CSM 0.5??

What is your accessment?


Cheers,

---

### Post by Nokia on 2006-09-06
IMO, the best thing to do would be, for a particular case, to stick with one "conception". I see you've installed XGL based on Compiz tutorials. I would recomend seeking/looking for help in the same threads used for a particular instalation, because as we've seen already, there's more then one road in accomplishing something, and guessing who went where and on which hop he might be stuck is extremely difficult and time-consuming.

@**Pinny** Yes. Running csm 0.5 and compiz-plugins 0.**16**

---

### Post by toasted on 2006-09-06
How do you tell what your plugins version is? 
My csm is 0.4
I dont see updates.....  were they released in compiz forum or something?

---

### Post by Nokia on 2006-09-06
Synaptic. See Settings-Preferences-ColumnAndFonts and check **Installed-Version** and **Available-Version**

---

### Post by The Pinny Parlour on 2006-09-06
> **Nokia said:**
> 

@**Pinny** Yes. Running csm 0.5 and compiz-plugins 0.**16**

Thanks mate.  0.16?  Will have to go getting that now I will.  :)

---

### Post by ayoli on 2006-09-06
> **toasted said:**
> How do you tell what your plugins version is? 
My csm is 0.4
I dont see updates.....  were they released in compiz forum or something?

mine is 0.5 from [www.beerorkid.com](www.beerorkid.com) repository.

---

### Post by toasted on 2006-09-06
When I check update manager there are no updates. Synaptic shows updates for compiz to .45 and plugins to .16

Why dont they show in update manager? (confused on how this works I guess)

Are these the same updates???

Edit... nevermind they show up in update manager now LOL

---

### Post by Nokia on 2006-09-06
Yes. Use Synaptic next time ;)

---

### Post by toasted on 2006-09-06
Alrighty then!
Wo whats up with the paint brushes?
All they seem to do is check the box, they dont even uncheck it....

---

### Post by btboudreaux on 2006-09-06
since I updated compiz, I have these godaweful ugly shadows everywhere. It makes it almost unusable. I tried turning it off in csm but it doesn't seem to work. Has anyone else had this problem and knows how to fix it?

---

### Post by Nokia on 2006-09-06
You might find an answer in the last couple of pages in this thread.

---

### Post by ayoli on 2006-09-06
> **btboudreaux said:**
> since I updated compiz, I have these godaweful ugly shadows everywhere. It makes it almost unusable. I tried turning it off in csm but it doesn't seem to work. Has anyone else had this problem and knows how to fix it?

try to change or edit the theme you're using with cgwd themer (in menu system > preferences, or hit alt+F2 and type in: **gcompizthemer -i**)

---

### Post by blacksea on 2006-09-06
I go to system/preference/session/startup/programe   change compiz-icon-tray to compiz-start  
compiz work again but the compiz-icon in the panel disapear 
have any body know how to fix this pro

---

### Post by Nokia on 2006-09-06
Go back and add compiz-icon-tray. Leave compiz-start unchanged.

---

### Post by toasted on 2006-09-06
The compiz icon tray is no longer used though! 
I would leave it turned off to avoid confusion

Type csm in a terminal to config compliz

---

### Post by ayoli on 2006-09-06
> **blacksea said:**
> I go to system/preference/session/startup/programe   change compiz-icon-tray to compiz-start  
compiz work again but the compiz-icon in the panel disapear 
have any body know how to fix this pro
there's no more tray icon for the moment. i fyou need it to swap between compiz and metacity see previous posts in this thread, you'll find scripts which do that, use csm to set prefs.

---

### Post by toasted on 2006-09-06
> **ayoli said:**
> there's no more tray icon for the moment. i fyou need it to swap between compiz and metacity see previous posts in this thread, you'll find scripts which do that, use csm to set prefs.

Actually there can be if you want to do some work

Credit to cyberorg
[http://www.compiz.net/topic-1170-3.html](http://www.compiz.net/topic-1170-3.html)

> 
1. Download the script, rename it to compiz-start.py and place it in /usr/bin or any of your bin path. 

2. chmod +x /path/to/compiz-start.py

3. Download logo file and place it in /usr/share/compiz/logo24.png
(right click - save image)

4. You need the very latest compiz-quinn packages for this to work. Make sure you have cgwd in your bin path (/usr/bin/cgwd or equal) make sure it has executable permission.

5. If you are using packages from opensuse compiz-quinn repository, do not download this, as it is already in the package all set up.

6. Now it will run cgwd by default if available. If cgwd is not available it will start gwd.

For all the folks who didnt know, cgwd probably works with compiz vanilla too, so does this script.


Add /usr/bin/compiz-start.py  in your system/sessions/startup programs
disable any other startup scripts you have in there

---

### Post by drpolish on 2006-09-07
In the beginning of the week, i was greeted with a new compiz update which destroyed my compiz love and i had to set it up again. This time, its payback.

Today, as of Sept 07, i updated compiz again expecting to see this fixed automatically. this didnt happen - my compiz got raped and now compiz-start doesnt work. if anyone can help, please do - i just updated like a half hour ago and i have to use metacity for now.

Im looking at a way to fix it, im expecting that it's compiz-start. However, im also on an AIGLX/i915 laptop.

---

### Post by devan on 2006-09-07
same thing happened to me.. did an update last night. and my shadows started working again after the update. today, i did another update about 10 minutes ago and compiz = broke.

this is getting pretty frustrating but I guess it can be expected

i'll keep posted if i find a fix.

---

### Post by noneofthem on 2006-09-07
I have got the same problem. Compiz was broken, I fixed it with start-compiz and todays update (7SEP) destroyed it again! What can I do?

Help, please!

Thanks

---

### Post by machuidel on 2006-09-07
noneofthem,

It just got fixed. Do another update && upgrade. The new "compiz-plugins" will fix it ;)

I have another problem. The System -> Quit screen does not show up and freezes the screen.
How can I get the System -> Quit screen to show up again?

---

### Post by bin2hex on 2006-09-07
I agree, just updated and mine is now working again 

(intel gfx card and AIGLX)

---

### Post by ayoli on 2006-09-07
> **machuidel said:**
> 
I have another problem. The System -> Quit screen does not show up and freezes the screen.
How can I get the System -> Quit screen to show up again?

i have thois problem too, quit window isnt visible but is here, when ou can see it screen is also freeze so that's normal. i've tried a "guess clk" to position of halt button and it has worked !! :)
btw there is another solution, hit: ctrl+alt+backspace will restart x and show gdm screen from where you can halt/reboot.
hope it will be fixed soon.

---

### Post by patrickfromspain on 2006-09-07
I have the same problems.. today's updates broke compiz :( And I'm on AMD64.. so updates take longer to hit the repos XD

---

### Post by gmclachl on 2006-09-07
I thought it had broken mine as well. However there is a script installed in /usr/bin called compiz-start. Using that works.

 George

---

### Post by Nokia on 2006-09-07
/me thinks those guys developing compiz should take a moment and reconsider this updating frenzy which although well intended lacks a thorough testing methodology which causes a lot a people great annoyances - all this spoiling in the end the whole concept. It would be best to go for maximum stability than chasing the latest improvements. On the other hand, the rest of us, could wait a bit longer and not go for the latest updates when there are no security  issues at stake. The more and more complex an OS becomes these days, the more chances  that a particular update might spoil something else and wreck the whole system. We've had our share of serious problems with Ubuntu in the last couple of weeks, starting with the broken Xserver update, and the sad thing is tha when something goes wrong, no one will make a clear distinction between the faulty program and the linux distro. They'll just complain that linux broke their box and a helping friend will praise Windows for the lack of problems and ease of use. That's very annoing,IMO

Please forgive the offtopic.

---

### Post by bin2hex on 2006-09-07
While I agree to the extent that Ive spent much of the last two weeks with a nonAIGLX system (after it being stable for months) and it has been frustrating, but lest not forget this is a bleeding edge technology and most of the time when it fails it drops us back to what we had before - a working desktop but with no groovy candy.

The recent changes have been for the better IMHO, my AIGLX seems a little faster and more polished when not broken ;-)  ) and the addition of themes is a real bonus - lets give those guys our support and say thanks for their hard work.

---

### Post by Nokia on 2006-09-07
I totally agree with you. However, nobody said anything about not giving credit to those hardworking developers, but having bleeding edge technology that damages the system's stability and reliability is worse than having the same latest bleeding edge tech but built with stability/reliability in mind and with less often but more reliable updates. :)

---

### Post by bin2hex on 2006-09-07
Indeed, I agree that it certainly seems that a little more testing could be used here. At the moment I feel so nervous when I see compiz updates and I dont think thats a good place to be.

Stability is  undoubtably more important that the latest tweak here and there, totally agree. I just dont want the developers to get disheartened when they see long threads like this. I accept no one is knocking them here, Im just trying to see it from their side

Thank god we have our candy back :cool: (well most of us)

---

### Post by Dinerty on 2006-09-07
If people are having problems with the 7th Sept 2006 updates then download the new update available now, it will solve the problems of xgl/compiz going mad again :)

---

### Post by APGunner on 2006-09-07
i installed sept 7 updates and it just messed up the fix i had for the other updates.

---

### Post by JerMe on 2006-09-07
> **Nokia said:**
> /me thinks those guys developing compiz should take a moment and reconsider this updating frenzy which although well intended lacks a thorough testing methodology which causes a lot a people great annoyances - all this spoiling in the end the whole concept. It would be best to go for maximum stability than chasing the latest improvements. On the other hand, the rest of us, could wait a bit longer and not go for the latest updates when there are no security  issues at stake.

Do you need a big red sign that says, "**[COLOR="Red"]USE AT YOUR OWN RISK[/COLOR]**" to know that compiz is very experimental software?  The devs never asked you to use their software and then criticize their calls on what code gets released.  This isn't a release candidate, nor a beta.  Compiz is still a work in progress and it's not often that something goes terribly wrong.  When something breaks, it breaks.  Big deal, visit the forum and wait for the next update.  The devs of course are going for "maximum stability" as well as "chasing the latest improvements".  Without the large testing base, xgl/aiglx/compiz wouldn't be developing at the rate it is now.  However we shouldn't be complaining about a bad update to the extent you are.

> The more and more complex an OS becomes these days, the more chances  that a particular update might spoil something else and wreck the whole system. We've had our share of serious problems with Ubuntu in the last couple of weeks, starting with the broken Xserver update, and the sad thing is tha when something goes wrong, no one will make a clear distinction between the faulty program and the linux distro. They'll just complain that linux broke their box and a helping friend will praise Windows for the lack of problems and ease of use. That's very annoing,IMO

This is what prompted me to reply.  You go even more on a tangent and complain about new linux users switching to Windows because of a software issue.  Why would you include that in a compiz thread unless you're assosiating the use of **experimental** software with new Ubuntu users?  Please don't tell me that you're assuming that new linux users are installing compiz, and that if compiz breaks, they'll go back to Windows.  "I just got this Ubuntu thing, and my wobbly windows won't wobble anymore... so I'm going to back to XP."

We all take a risk when we run bleeding edge packages.  If you don't like things breaking on you, then **don't use experimental software**.

With that said, **/usr/bin/compiz-start** fixed it for me, and running **csm** app got my skydome and other preferences working once again.  A standard startup script and a GUI settings manager are welcome over the sea of different start up scripts (thefuture? wtf?) and wading through gconf-editor keys.

---

### Post by shamrock_uk on 2006-09-07
Yeah, I must say that I prefer bleeding edge development like this. The risks of breakage are outweighed by getting wonderful little utilities like *csm* as soon as possible :)

The very latest update (downloaded at 23:50 GMT) fixed *compiz-start* returning a segmentation fault for anyone else who has the same problem.

---

### Post by dentaku65 on 2006-09-07
Fixed now with the last dist-upgrade! :cool: 

[http://yep.it/?bnm0t6](http://yep.it/?bnm0t6)

---

### Post by ybisk on 2006-09-07
Hi, 
I'm Running the newest updates I have the compiz-tray-icon disabled but it loads anyway, and when i try to start compiz by any form, be it 

/usr/bin/compiz-start
/usr/bin/compiz-start --replace

or the icon

all borders flicker and then metacity returns, any thoughts?


/usr/bin/compiz-start --replace

returns:
nohup: appending output to `nohup.out'

which contains:

cgwd: Connection Error (Unable to determine the address of the message bus)
7092: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" fa$
This is normally a bug in some application using the D-BUS library.
7092: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" fa$
This is normally a bug in some application using the D-BUS library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...

** (cgwd:7547): WARNING **: Cannot open pixmap: help
** (cgwd:7547): WARNING **: Cannot open pixmap: menu
** (cgwd:7547): WARNING **: Cannot open pixmap: shade
** (cgwd:7547): WARNING **: Cannot open pixmap: unshade
** (cgwd:7547): WARNING **: Cannot open pixmap: above
** (cgwd:7547): WARNING **: Cannot open pixmap: unabove
** (cgwd:7547): WARNING **: Cannot open pixmap: sticky
** (cgwd:7547): WARNING **: Cannot open pixmap: unsticky


Any help, would be much appreciated, thanks

---

### Post by toasted on 2006-09-07
Depends on when you updated. Best to check for updates again.... the earlier ones today may have had troubles

---

### Post by ybisk on 2006-09-08
I have all the most current updates and still nothing

when I use 

the tray icon all title bars flash and then return to metacity

/usr/bin/start-compiz --replace 
crashes:
gnome-volume-manager
update-notifier

/usr/bin/start-compiz
crashes:
evolution-alarm-notify
gnome-power-manager

the latter two also create the nohub.out

---

### Post by ayoli on 2006-09-08
did you :
```
chmod -R 0755 ~/.compiz
``` and then run ```
/usr/bin/csm
``` and ```
/usr/bin/gcompizthemer
```

---

### Post by ButteBlues on 2006-09-08
ybisk - The new startup command is COMPIZ-START, not start-compiz.

======

The Compiz Manager has returned!

$ sudo apt-get install compiz-manager

In the Startup tab of Session Properties, remove /usr/bin/compiz-start. Then add /usr/bin/compiz-manager. THIS WILL STILL START COMPIZ BY DEFAULT, however, the tray icon will work (and if compiz crashes, it'll auto-throw you back into metacity or kwin) again. DO NOT INSTALL GNOME-COMPIZ-MANAGER!!! It is a package of gandalfn's that's made for the Edgy compiz-aiglx packages and does not work with Quinn's packages.

---

### Post by ybisk on 2006-09-08
Re: Ayoli

I did take those steps, saw that process posted previously




Re: a simple façade

I used that command but it spat the same error output at me
also, using the tray icon compiz-manager, I just flash until metacity returns



Is this something I just have screwed up or is this something where if I just  wait paciently eventually an update will miraculously fix?

---

### Post by PathSpace on 2006-09-08
> **a simple façade said:**
> ybisk - The new startup command is COMPIZ-START, not start-compiz.

======

The Compiz Manager has returned!

$ sudo apt-get install compiz-manager

In the Startup tab of Session Properties, remove /usr/bin/compiz-start. Then add /usr/bin/compiz-manager. THIS WILL STILL START COMPIZ BY DEFAULT, however, the tray icon will work (and if compiz crashes, it'll auto-throw you back into metacity or kwin) again. DO NOT INSTALL GNOME-COMPIZ-MANAGER!!! It is a package of gandalfn's that's made for the Edgy compiz-aiglx packages and does not work with Quinn's packages.

Hey, thanks for that info about compiz-manager.  :mrgreen:

---

### Post by beercz on 2006-09-14
Finally got compiz to work again - it was damn fiddly but I managed it.  It is sooooo slow though (even with blur turned off), that I am not using it at the moment.  It ran just fine prior to these updates.

---

### Post by ButteBlues on 2006-09-14
> **beercz said:**
> Finally got compiz to work again - it was damn fiddly but I managed it.  It is sooooo slow though (even with blur turned off), that I am not using it at the moment.  It ran just fine prior to these updates.
Yeah - these last updates are slow on Edgy Aiglx too. :(

---

### Post by ayoli on 2006-09-15
yep, true here also, but unchecking "reflection" plugin make it work a bit faster.

---

### Post by Nokia on 2006-09-15
compiz is broken, again. Window controls are gone, and for a strange reason something keeps changing to another value the chmod 755 ~.compiz/ -R command. 
ls -l ~.compiz/ returns 755 for cgwd/ and 644 for csm_settings. Any ideas anyone ?

---

### Post by ButteBlues on 2006-09-15
$ sudo chmod 75 ~/.compiz -R

THat's the command you want.

---

### Post by Nokia on 2006-09-16
If you mean 755 I already did that prior to posting here, with and without sudo, having the same result. If, by any chance, there's no typo and you really mean 75 which leaves the owner rights --- please explain. Bottom line is, either way I get the same result.

---

### Post by ayoli on 2006-09-16
i haven't update yet, my compiz works and when i check the perms on .compiz dir:
```
[10:37:32@ayoli.zone]:~ >$ ls -l ~/.compiz/
total 12
drwxr-xr-x 2 ayoli users 4096 2006-08-24 01:23 cgwd
-rw-r--r-- 1 ayoli users 1219 2006-09-16 10:16 csm_settings
drwxr-xr-x 3 ayoli users 4096 2006-07-30 08:51 themes
```
i have the same as you, so that must not be your problem
what is your compiz version ?

---

### Post by Nokia on 2006-09-16
My compiz version is 0.0.13.54-0ubuntu1. However, here's what it's missing in my ls -l: >  ls -l ~/.compiz/
total 8
drwxr-xr-x 2 nokia nokia 4096 2006-09-16 00:53 cgwd
-rwxr-xr-x 1 nokia nokia  827 2006-09-16 01:34 csm_settings

---

### Post by ayoli on 2006-09-16
looks like you miss a theme dir in it, maybe try to run gcompizthemer and set a theme.

---

### Post by Nokia on 2006-09-16
been there, done that :|

---

### Post by ayoli on 2006-09-16
i've just run apt-get dist-upgrade which did upgrade linux-image, linux-restricted-modules compiz (.54) compiz-core, compiz-plugins (.31), cgwd (.69) and did a total reboot.
it just works fine ! i have borders and even it seems to run smoothly than before

---

### Post by toasted on 2006-09-16
> **ayoli said:**
> i've just run apt-get dist-upgrade which did upgrade linux-image, linux-restricted-modules compiz (.54) compiz-core, compiz-plugins (.31), cgwd (.69) and did a total reboot.
it just works fine ! i have borders and even it seems to run smoothly than before

I updated yesterday and got the kernel update (686), Are you running 386 kernel?

---

### Post by ayoli on 2006-09-16
> **toasted said:**
> I updated yesterday and got the kernel update (686), Are you running 386 kernel?

yep

---

### Post by gommle on 2006-09-16
I updated today and fiddled around with some plugins. Now the Cube isnt working at all. Desktop planes work tough. (Quinnstorm)

---

### Post by gottferdamnt on 2006-09-16
Same thing for me  :(

---

### Post by ayoli on 2006-09-16
> **gommle said:**
> I updated today and fiddled around with some plugins. Now the Cube isnt working at all. Desktop planes work tough. (Quinnstorm)

cube won't work with desktop plane, uncheck desktop plane if you want to use cube

---

### Post by gottferdamnt on 2006-09-16
OK It works

---

### Post by Anouar on 2006-09-24
Well when i try to install compiz with 
```
sudo apt-get install compiz
```

i Get 
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
E: Broken packages

```

I am busy for a week to insall my 3d desktop, but it still does not work.

can anyone help me?

---

### Post by toasted on 2006-09-24
> **Anouar said:**
> Well when i try to install compiz with 
```
sudo apt-get install compiz
```

i Get 
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
E: Broken packages

```

I am busy for a week to insall my 3d desktop, but it still does not work.

can anyone help me?

Compiz-Quinn is in a transition period. The project has been forked and will soon be released as Beryl. The release has not happened yet and the repos are in a state of transition so what you need may or may not be there. Best thing to do is wait for what is projected to be a day or two then try it again.

Check here too for news:
[http://www.compiz.net/index.html](http://www.compiz.net/index.html)

---

### Post by ayoli on 2006-09-24
edit: oops :p, deleted

---

### Post by Anouar on 2006-09-24
well guys, is there not a alternative. I mean i don't like waiting :D :razz:

---

