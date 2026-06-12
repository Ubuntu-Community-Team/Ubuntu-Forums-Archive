---
title: "compiz config not working in 7.10 gutsy"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by MusashiX2 on 2007-10-22
i am a Linux newbie, so bare with me.  i am running 7.10 gutsy gibbon with a Radeon 9800XT.  i have been trying to get Compiz Fusion to work for the past couple of hours, with not much results.  i have accomplished running XGL, and the "CompizConfig Settings Manager" now shows up under System > Preferences.  however, when i click it nothing happens.  also, the basic visual effects i had set before are not working.  no visual effects are working.  if i select "Preferences" for the Custom visual effects in System > Appearance, nothing happens (this was working before).

any help/assistance would be greatly appreciated.

---

### Post by ezak on 2007-10-22
Please paste the output of:

compiz --replace  
(run it from terminal)

- here so we can get a better understanding and diagnose what the problem could be.

---

### Post by MusashiX2 on 2007-10-22
> **ezak said:**
> Please paste the output of:

compiz --replace  
(run it from terminal)

- here so we can get a better understanding and diagnose what the problem could be.

i got :

anthony@BeBop:~$ compiz --replace  
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

putting in that command tends to make me lose the left side and top of my windows.

btw, right before i read your response i tried removing ccsm to see if it would help.  .....and it didn't.

---

### Post by jimerickso on 2007-10-22
gutsy doesn't come with ccsm by default you will have to install it. thusly:

sudo apt-get install compizconfig-settings-manager

then try clicking on the ccsm icon in system > preferences > advanced desktop effects settings. hope that helps!

---

### Post by MusashiX2 on 2007-10-22
> **jimerickso said:**
> gutsy doesn't come with ccsm by default you will have to install it. thusly:

sudo apt-get install compizconfig-settings-manager

then try clicking on the ccsm icon in system > preferences > advanced desktop effects settings. hope that helps!

i installed it, but the "Advanced Desktop Settings" option is not there.

---

### Post by MusashiX2 on 2007-10-22
i realized now that some of the tutorials and How-To guides that i followed were actually for Feisty Fawn, and not for Gutsy.  should i just wipe my hard drive with Gpart and reinstall Gutsy?  that way i can make sure i only follow directions given for the right version.

i wouldn't be losing much.  i have yet to really put anything of substance on this computer.

---

### Post by jimerickso on 2007-10-22
you coul try the following in a terminal:

/usr/bin/ccsm 

or

/usr/local/bin/ccsm

to run ccsm. depending on where you installed it.

---

### Post by Therion on 2007-10-22
See if this helps, it's what got Compiz-Fusion up and running for me:

[[COLOR="Blue"]http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion[/COLOR]]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

---

### Post by MusashiX2 on 2007-10-22
the results:

```
anthony@BeBop:~$ /usr/bin/ccsm 
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
anthony@BeBop:~$ /usr/local/bin/ccsm
bash: /usr/local/bin/ccsm: No such file or directory
```

---

### Post by MusashiX2 on 2007-10-22
> **Therion said:**
> See if this helps, it's what got Compiz-Fusion up and running for me:

[[COLOR="Blue"]http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion[/COLOR]]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")


doesn't help, because the "Advanced Desktop Effects Settings" option is not there in my Preferences folder, even though i already installed ccsm.  although i do thank you for trying to help.

---

### Post by Jojan on 2007-10-22
I'm having the same (or similar) problem. I can't enable any visual affects (System>Preferences>Apperance), I get "Desktop effects could not be enabled".

```
jojan@johan-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity
```

When first run the screen blinks once, and I can't type anthing new in the terminal without doing Ctrl + C. Then again the screen blinks once.


```
jojan@johan-laptop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for jojan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
jojan@johan-laptop:~$
```

None of the two suggested ccsm files were found.

---

### Post by oliverb4ss on 2007-10-22
I get a similar problem as the poster before me.
When I type compiz --replace, I get:

  Checking for Xgl: not present. 
  No whitelisted driver found
  aborting and using fallback: /usr/bin/metacity

I have the Advanced Desktop Effects Settings, but when choosing anything other than the "no effects" option under "Visual Effects", I get the following:
 The Composite extension is not available.

It all worked in Feisty.
Any ideas how to make it work here?

---

### Post by Helbo15 on 2007-10-22
> **oliverb4ss said:**
> I get a similar problem as the poster before me.
When I type compiz --replace, I get:

  Checking for Xgl: not present. 
  No whitelisted driver found
  aborting and using fallback: /usr/bin/metacity

I have the Advanced Desktop Effects Settings, but when choosing anything other than the "no effects" option under "Visual Effects", I get the following:
 The Composite extension is not available.

It all worked in Feisty.
Any ideas how to make it work here?


I get the exat same error message and would allso love to know what it means should I install anything more or is it cause I have a old radeon 9800 pro ?

---

### Post by MusashiX2 on 2007-10-22
ok, i just reinstalled Gutsy Gibbon.  fresh start, back to square one.  

i need tutorials on Compiz Fusion, and after i get that working i need to setup my dual monitors.  anybody know how or got links?

---

### Post by michael37 on 2007-10-22
> **MusashiX2 said:**
> i am a Linux newbie, so bare with me.  i am running 7.10 gutsy gibbon with a Radeon 9800XT.  i have been trying to get Compiz Fusion to work for the past couple of hours, with not much results.  i have accomplished running XGL, and the "CompizConfig Settings Manager" now shows up under System > Preferences.  however, when i click it nothing happens.  also, the basic visual effects i had set before are not working.  no visual effects are working.  if i select "Preferences" for the Custom visual effects in System > Appearance, nothing happens (this was working before).

any help/assistance would be greatly appreciated.


You have an ATI card.  Try my howto in [thread=569654]this thread[/thread].

---

### Post by MusashiX2 on 2007-10-22
> **michael37 said:**
> You have an ATI card.  Try my howto in [thread=569654]this thread[/thread].


DUDE!  OMG!  it works great now.  thank you so much.  any idea on where i should look for help with setting up my dual monitors?

---

### Post by michael37 on 2007-10-22
> **MusashiX2 said:**
> DUDE!  OMG!  it works great now.  thank you so much.  any idea on where i should look for help with setting up my dual monitors?

Glad it helped.  Make sure you make a backup of your file /etc/X11/xorg.conf so you can use it later if the dual-monitor setup doesn't pan out.

The dual-monitor support is best managed by the aticonfig command, e.g.

aticonfig --initial=dual-head

is a good place to start.  I haven't found really good webpages on the aticonfig, so

man aticonfig 

is your best friend.

Keep in mind, messing with dual-monitors may occasionally break the 3D effects.  That's an unfortunate limitations of relatively poor driver support of ATI video cards by AMD/ATI.  If that happens, bite the bullet and switch back to gorgeous 3D albeit with a single monitor (simply restore the xorg.conf that you kept and it will be as peachy as it is now)

---

### Post by govna on 2007-10-22
i just installed the ubuntu 7.10 and it was suppose to come with a default compiz but it did not. i have installed compizconfig settings manager but none of the effects are working. and also i have tried to set the settings in the appearance window to custom but it was giving me an error. and it asked me to enable my graphics card which i did but then the screen got really messed up. 
Graphics card is: nvidia geforce 7100

COULD ANYBODY HELP ME PLEASE

thank you

---

### Post by michael37 on 2007-10-22
> **govna said:**
> i just installed the ubuntu 7.10 and it was suppose to come with a default compiz but it did not. i have installed compizconfig settings manager but none of the effects are working. and also i have tried to set the settings in the appearance window to custom but it was giving me an error. and it asked me to enable my graphics card which i did but then the screen got really messed up. 
Graphics card is: nvidia geforce 7100

COULD ANYBODY HELP ME PLEASE

thank you

Try to enable restricted driver per [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by sbrody88 on 2007-10-22
> **Jojan said:**
> I'm having the same (or similar) problem. I can't enable any visual affects (System>Preferences>Apperance), I get "Desktop effects could not be enabled".

```
jojan@johan-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity
```

I got this exact same error - exactly.  Down to the PCIID.  Anyone have any suggestions for this?

---

### Post by michael37 on 2007-10-22
> **govna said:**
> i just installed the ubuntu 7.10 and it was suppose to come with a default compiz but it did not. i have installed compizconfig settings manager but none of the effects are working. and also i have tried to set the settings in the appearance window to custom but it was giving me an error. and it asked me to enable my graphics card which i did but then the screen got really messed up. 
Graphics card is: nvidia geforce 7100

COULD ANYBODY HELP ME PLEASE

thank you

> **sbrody88 said:**
> I got this exact same error - exactly.  Down to the PCIID.  Anyone have any suggestions for this?

You have a blacklisted device, which means developers don't think Compiz with all 3D effects can run on your hardware.  You think otherwise?  Try searching for directions about the blacklisted devices in Tutorials and Tips category.  And make sure you read all disclaimer before overwriting the safety configuration preventing you from running Compiz.

---

### Post by michael37 on 2007-10-22
> **MusashiX2 said:**
> DUDE!  OMG!  it works great now.  thank you so much.  any idea on where i should look for help with setting up my dual monitors?

Ah! Finally, found a good guide on the aticonfig command

[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)

---

### Post by MusashiX2 on 2007-10-23
> **michael37 said:**
> Ah! Finally, found a good guide on the aticonfig command

[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)

wow!  more great information.  thanks, dude.  you're awesome!  :biggrin: \\:D/

so here is a stupid question (for anybody who knows, not just michael37)..... i backed up the xorg.conf file, so if i **** something up i just replace it with the backed up one and everything will go back to the way i had it?  is it kind of like a system restore?

---

### Post by nealeneale on 2007-10-23
same problem here. first time ive used linux so extreme noob here. ccsm wont even open. before i installed any compiz the default wobbly windows cube etc all worked. now nothing works. Intel Mobile 915gm/910gml is my graphics card, using a hp tc4200 and getting the tablet working is another story.

can anyone hold my hand and guide me to sorting the compiz out

[HTML]neale@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format[/HTML]

```
neale@ubuntu:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
neale@ubuntu:~$ 

```

---

### Post by nealeneale on 2007-10-23
bump

just a point in the right direction would be much appreciated

---

### Post by ajadams2 on 2007-10-23
My laptop is a T60p with an ATI FireGL v5250 graphics card. I had to verify that I was using fglrx instead of vesa/ati/radeon.  I am not sure if the package it will break something else though.
My error message:
[HTML]Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity[/HTML]

The solution that worked for me.  Can't promise that it will work for everyone.
[HTML] sudo apt-get install xserver-xgl[/HTML]

---

### Post by michael37 on 2007-10-24
> **ajadams2 said:**
> My laptop is a T60p with an ATI FireGL v5250 graphics card. I had to verify that I was using fglrx instead of vesa/ati/radeon.  I am not sure if the package it will break something else though.
My error message:
[HTML]Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity[/HTML]

The solution that worked for me.  Can't promise that it will work for everyone.
[HTML] sudo apt-get install xserver-xgl[/HTML]

Good suggestion, but incredibly dangerous.  It works ONLY for ATI video cards and ONLY for Gutsy.

---

### Post by michael37 on 2007-10-24
> **nealeneale said:**
> bump

just a point in the right direction would be much appreciated

You gotta help us bro.  For example, what version are you running?

---

### Post by craigyjack on 2007-10-24
> **govna said:**
> i just installed the ubuntu 7.10 and it was suppose to come with a default compiz but it did not. i have installed compizconfig settings manager but none of the effects are working. and also i have tried to set the settings in the appearance window to custom but it was giving me an error. and it asked me to enable my graphics card which i did but then the screen got really messed up. 
Graphics card is: nvidia geforce 7100

COULD ANYBODY HELP ME PLEASE

thank you

first off, make sure you have a 3D nvidia driver. Easist way is to use the ubuntu nvidia driver in restricted drivers manager (System>>ADministration>>Restricted Drivers Manager) and make sure the nvidia driver is in use. If this does not work, then you can download the newest nvidia driver from nvidia.com, and install it. if you need help installing it, you can contact me further.

compiz does come installed. you need to activate it in System>>Preferences>>Appearance in the Visual Effects tab. click the full-fleged one (the third option)

Now you have basic compiz, but if you want to use all the features you will need to use CompizConfig Settings Manager. you already have installed that.
NOW, in order to get compiz to recognize the settings in the CCSM, you will need to run compiz with this command
```
compiz --replace ccp &
```
ccp is the item that lets compiz communicate with CCSM and get your settings from CCSM. by default in ubuntu, compiz gets its setting from gconf.
dont ask me why ubuntu did it this way, idk, it is very confusing for end users, because CCSM is a commonly used compiz settings manager (and very nice) (rather than gconf to use to all the settings).

---

### Post by craigyjack on 2007-10-24
> **MusashiX2 said:**
> wow!  more great information.  thanks, dude.  you're awesome!  :biggrin: \\:D/

so here is a stupid question (for anybody who knows, not just michael37)..... i backed up the xorg.conf file, so if i **** something up i just replace it with the backed up one and everything will go back to the way i had it?  is it kind of like a system restore?

for x-server messing around yes, it is like that. any changes you make to x server using the atiutility, or manual editing of the xorg.conf file, can be fixed by replacing your backup xorg.conf to the one your messed up while tinkering.
i believe this is even easier now because of bullet-proof-x, you'll still get a graphical x server even if you mess it up, then you can replace the conf file and go back.

just to be clear, that is only system restore for the x windowing server. if you messing around with something else, like other unrelated system files, this wont have anything to do with it, so its not a system restore as in your whole computer, just the x windowing server.

---

### Post by frontieruk on 2007-10-24
> **craigyjack said:**
> first off, make sure you have a 3D nvidia driver. Easist way is to use the ubuntu nvidia driver in restricted drivers manager (System>>ADministration>>Restricted Drivers Manager) and make sure the nvidia driver is in use. If this does not work, then you can download the newest nvidia driver from nvidia.com, and install it. if you need help installing it, you can contact me further.

compiz does come installed. you need to activate it in System>>Preferences>>Appearance in the Visual Effects tab. click the full-fleged one (the third option)

Now you have basic compiz, but if you want to use all the features you will need to use CompizConfig Settings Manager. you already have installed that.
NOW, in order to get compiz to recognize the settings in the CCSM, you will need to run compiz with this command
```
compiz --replace ccp &
```
ccp is the item that lets compiz communicate with CCSM and get your settings from CCSM. by default in ubuntu, compiz gets its setting from gconf.
dont ask me why ubuntu did it this way, idk, it is very confusing for end users, because CCSM is a commonly used compiz settings manager (and very nice) (rather than gconf to use to all the settings).

I have a similar problem running 7.10, I have an nvidia 6150 (not great I know) and have installed the latest Nvidia drivers via the restricted drivers manager, but running compiz gives this output:-
[I]Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0240 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1360x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
[/I]

Any suggestions on resolving this?

---

### Post by nealeneale on 2007-10-24
> **michael37 said:**
> You gotta help us bro.  For example, what version are you running?

gutsy? i ****** it big time last night, going to do a fresh install tonight. tried that suggestion that is incredibly dangerous and only works for ati cards before i knew it was dangerous and strictly ati

---

### Post by michael37 on 2007-10-24
> **nealeneale said:**
> gutsy? i ****** it big time last night, going to do a fresh install tonight. tried that suggestion that is incredibly dangerous and only works for ati cards before i knew it was dangerous and strictly ati

Hehe well, you have an Intel video card and you followed suggestion that does not work with Intel drivers... so you knew... good luck with a fresh install :)

Follow [ this quick guide](https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy) to enable AIGLX (a very complex technical term which explains how you will have 3D effects displayed) and then Compiz should work fine.

If still need help, reply in this thread and attach your /etc/X11/xorg.conf file.

---

### Post by michael37 on 2007-10-24
> **frontieruk said:**
> I have a similar problem running 7.10, I have an nvidia 6150 (not great I know) and have installed the latest Nvidia drivers via the restricted drivers manager, but running compiz gives this output:-
[I]Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0240 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1360x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
[/I]

Any suggestions on resolving this?

This is a warning not an error.  You compiz should be working just fine.

---

