---
title: "CEDEGA 6 - Brings Ubuntu Fiesty to it's knees. BUG!"
date: 2007-04-25
forum: Gaming &amp; Leisure
---

### Post by webjames on 2007-04-25
Hi, i have just tired installing Cedega 6 and it installs fine, when i go to run it, it logs me out, and then when i log back in it just freezes my entire computer!

Surly this is a bug? with cedega or Ubuntu, this article highlights an important point:

[https://bugs.launchpad.net/ubuntu/+bug/106913](https://bugs.launchpad.net/ubuntu/+bug/106913)

---

### Post by kvonb on 2007-04-25
Hmm, it works perfectly on mine.

I can even run some games that wouldn't run previously.

From the provided link: > I disagree.  No no-root app should be able to take down my desktop.

This person was obviously annoyed at the time of posting, unfortunately there are a lot of things in this world that should/should not happen but do!

What video card do you have, and which driver are you using?

I am using the official Nvidia driver from the Nvidia web-site, maybe try that.

If you have an ATI video card, then you might be out of luck, as their driver has quite a few problems from what I've read.

---

### Post by webjames on 2007-04-25
that's really weird are you using ATI or NVidia?

---

### Post by webjames on 2007-04-25
just noticed your signature i've got a 6600 something aswell.. hmm.. weird! and your on feisty?

---

### Post by webjames on 2007-04-25
how do i tell the version of the nvidia driver?

---

### Post by webjames on 2007-04-25
bump! help still need help

---

### Post by kvonb on 2007-04-25
Ooops, sorry about that, I got sidelined :).

Have a look at the file: /var/log/Xorg.0.log, you will need su privileges, so press <alt><f2> and type in:

```
gksu nautilus
```

Browse to /var/log and open that file.

Look through it for the Nvidia driver and version.

Did you install the "Restricted driver" from the System menu?  If not, then that could be the problem.

If you did install the driver, open a terminal and type this:

```
glxinfo | grep direct
```

If you get the answer "Yes", then the driver is installed correctly, if you get no reply, then you need to install or re-install the video driver.

Let me know how you went :).

---

### Post by webjames on 2007-04-26
thanks for your reply.

these are the lines of the log that seem relevent:

> (II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver 


from what i can see the driver version is: 1.0.9631 or 4.0.2 that's out of the first quoted section.

i did install the restricted driver when i click desktop effects it said i needed the restricted driver.

when i run glxinfo | grep direct i get:

> james@james-ubuntu:~$ glxinfo | grep direct
direct rendering: Yes


so that means the driver is installed correctly?

so what could be the problem? ...
i could give you more information on the error when i type cedega in the console but it locks up before i can copy it out of bash, is there a similar log on the bash output history?

thanks for you help!

---

### Post by webjames on 2007-04-26
just found this:
[http://paste.ubuntu-nl.org/14492/](http://paste.ubuntu-nl.org/14492/)

it says the error i've been experiencing:

>  RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.


---

### Post by kvonb on 2007-04-26
I'm going to have to drop the ball on this one, I've never encountered that error before.

All I can suggest is keep searching the forum and bump this thread from time to time, I'm sure it will crop up again somewhere else.

---

### Post by igknighted on 2007-04-26
Googling it came up with two hits, one an unanswered post on the cedega forum, another a post on the Mandriva forums with some replies.  It's not english.  Heres the thread if you can read this language (I can't even recognize it, tho I think it's eastern european maybe?): [http://strefamandrivy.pl/forum/viewtopic.php?p=59829&sid=c96c8110ab414e8021d5e40087caa1ff&PHPSESSID=ceb](http://strefamandrivy.pl/forum/viewtopic.php?p=59829&sid=c96c8110ab414e8021d5e40087caa1ff&PHPSESSID=ceb)...

---

### Post by webjames on 2007-04-26
well it's polish but i'm having trouble translating it! google doesn't do polish, and i can't find anyone else who does either! it looks like someone has found the answer as there as lots of :D's and :)'s going on

---

### Post by igknighted on 2007-04-26
My guess is it requires a new version of python (or rather an old one) to be installed.  Or possibly updating a symlink to point to the proper file that already exists.  But I haven't used Cedega 6 yet so I don't know.

---

### Post by webjames on 2007-04-26
ok, i have just tried cedega 5.2.3 and when i run it it comes up with this error:

> james@james-ubuntu:~$ cedega
/usr/lib/transgaming_cedega/gddb.py:19: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2371, in <module>
    Point2Play_gui_ref = Point2Play_gui( Point2Play.Point2Play( config_file) )
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 360, in __init__
    raise badConfigFile( _("Missing options %s") % e.value )
AttributeError: 'NoOptionError' object has no attribute 'value'


what am i doing wrong, i have just installed a fresh install of feisty and have installed the nvidia restricted drivers. how come it's just me having this problem?

any help would be most kind,

---

### Post by webjames on 2007-04-27
bump! anyone?

:)

---

### Post by MintabiePete on 2007-04-27
I am running Cedega  version 6.0   with  Feisty  with no problems  to speak of . I have  a Nvidia GeForce 6100   and  can  run games like  Return To Castle Wolfenstein  and  Prince of Persia  no problems , when I try to load  smaller games  like  cubis  , bejewelled  and beetle junior  , I run into problems  :) I have  not  tried any other  soft ware on it , I have  only  just  put it on , and just learning how  to use it  :)

---

### Post by webjames on 2007-04-27
i might reinstall feisty and see if that helps. really weird though..

---

### Post by webjames on 2007-04-27
> **MintabiePete said:**
> I am running Cedega  version 6.0   with  Feisty  with no problems  to speak of . I have  a Nvidia GeForce 6100   and  can  run games like  Return To Castle Wolfenstein  and  Prince of Persia  no problems , when I try to load  smaller games  like  cubis  , bejewelled  and beetle junior  , I run into problems  :) I have  not  tried any other  soft ware on it , I have  only  just  put it on , and just learning how  to use it  :)

how did you installed the drivers for you grfx card? i'll do it the same when i reinstall

---

### Post by MintabiePete on 2007-04-27
This Geforce 6100 card is built  in  with my  Foxconn 6100 k8ma-rs m/b  and  when I first tried  it  , I used  the native  drivers  , but it never  run much good , then I changed  the  drivers   through Automatix 2 and used the nvidia  drivers  there  , and  have  had no problems  since . Prior to that , before I even loaded  cedega  I had problems  in  firefox scrolling  and it wasnt until I used  the   nvidia drivers  in Automatix2  that  things improved  :)

---

### Post by webjames on 2007-04-27
okay, just reinstalled feisty and loaded cedega up (version 5.2.4) this is the error:
> 
/usr/lib/transgaming_cedega/gddb.py:19: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2371, in <module>
    Point2Play_gui_ref = Point2Play_gui( Point2Play.Point2Play( config_file) )
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 360, in __init__
    raise badConfigFile( _("Missing options %s") % e.value )
AttributeError: 'NoOptionError' object has no attribute 'value'


i really don't understand, it can't be a grfx problem as i haven't installed any grfx drivers. why is this not happening to other people?

---

### Post by webjames on 2007-04-27
just a thought: has anyone god latest exaile running and cedega? as exaile uses python aswell:

> [http://www.exaile.org/trac/wiki/Releases](http://www.exaile.org/trac/wiki/Releases)

maybe someone could try installing it.

thanks!

---

### Post by webjames on 2007-04-28
bump!

anyone? :)

---

### Post by kvonb on 2007-04-28
I downloaded the version of exaile you provided and went to install it.  I was too chicken to go through with it as it wanted to install a whole host of other things too and I was worried that it would stuff up my version of Cedega :).

So I took a screenshot which shows the Python version that is installed on my computer, and also the libs that exaile wants to install.

Maybe you can see some differences?

---

### Post by webjames on 2007-04-28
thanks for the screenshot, thats exactly what i had when i installed it, now i've installed exaile its put more python stuff on but i had both working in edgy and as it didn't work before i put exaile on i doubt this is the problem. i thought it worth ruling it out though. i seem to be getting no where.
i've ruled out so far:

it's not something i've installed after the feisty installation as i tried it with a new install
it's not exaile
it's not the cedega version
it did work on edgy

help?!

---

### Post by webjames on 2007-04-29
bump! 
:)
anyone? i still get the error i've posted on this thread on page2

---

### Post by EndPerform on 2007-04-29
I've checked the forums here trying to find a fix, but haven't come up with anything, so I figured I'd make a post and see if anyone has any thoughts.

On a fresh install of Feisty, I installed Cedega 6 via the .DEB file. The GUI comes up, but has the following warning:

```
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
```


I figured it's nothing major, however, when I go to install any game, the directory in the GUI is created, but nothing happens. When I run from cedega from a terminal, I get this error in the term window:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  72 (X_PutImage)
  Serial number of failed request:  81
  Current serial number in output stream:  93
```


Cedega passes all of the system tests, so I'm pretty much stumped as to what might be going on. Any help would be appreciated!

---

### Post by zaphodbeeblebrox on 2007-04-30
Ya I got this one too

 Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.

funny thing is cedega was working fine after i upgraded to feisty then i tried to log into WoW and was getting the extremely long delay on authentication server.  I thought I might as well see what new cedega version is so i did the "force updates". Now none of the games in cedega work. When I did the last update for the gaming engine I had to reselect the burning crusade in GDDB section of config. This time however, I have had no such luck in playing with the UI to get things to work. Any ideas?

---

### Post by kvonb on 2007-05-01
webjames:


At this stage I would suggest trying to install the official nvidia driver from their website.

Have a look at this thread, but skip straight to Step2, Option2, you don't need the rest.

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Also you shouldn't need to remove the restricted drivers, so omit that from the remove line, and use the correct driver for your card.  Check [www.nvidia.com](www.nvidia.com) for the correct driver and download it.  I think pricechild also forgot to say that you will have to make the driver executable with: chmod +x Nv(TAB to autocomplete).

And do it all from a virtual terminal, write down or print out the instructions then logout of X and press <ctrl><alt><f1>.

That should get the proper driver installed, just keep your eyes open for any error messages and don't let it modify xorg.conf if there are any errors!

Good luck :).

---

### Post by webjames on 2007-05-01
just trying this now i will edit and update this post if i succeed or fail.
 
thanks for the post!

**EDIT**
Thanks for the post kvonb but unfortuntly i still get this error before my computer freezes:
> 
james@james-ubuntu:~$ cedega
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser

what a mystery, i followed the steps as you instructed.
well thanks for trying,

---

### Post by nohairleft on 2007-05-01
this problem was bugging me as well, this is how I got around it.

open a konsole

sudo apt-get --purge remove cedega-small
sudo rm .transgaming_global

Reinstall Cedega 6

All working the way it should.

---

### Post by webjames on 2007-05-01
> **nohairleft said:**
> this problem was bugging me as well, this is how I got around it.

open a konsole

sudo apt-get --purge remove cedega-small
sudo rm .transgaming_global

Reinstall Cedega 6

All working the way it should.

thanks just tried the above, however it didn't work for me. same error same computer freeze.. this is so strange, i don't know what's wrong?!

---

### Post by webjames on 2007-05-01
on the advice of [SD-Plissken]("http://ubuntuforums.org/member.php?u=36501") i am going to post the bug report and the error i get again when running cedega from the console:

Note: this is any version both 6 and 5.x.x i have tried both.

the bug report can be found here:
[https://bugs.launchpad.net/ubuntu/+bug/106913](https://bugs.launchpad.net/ubuntu/+bug/106913)

and the error i get is:
> /usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
import gddb_parser
After this the computer freezes, the mouse freezes in position, none of the shortcut keys work, i cannot start a terminal, i cannot use ctrl +atl +backspace to restart gnome, i have to pull the plug out and start again.

This is the worrying thing i think surly there must be a bug for a non-root program to lock up, disable my whole desktop.
Others having the same problem report sometimes it logs the user out, and sometimes freezes the desktop.

any help would be most appreciated, maybe it's a big in cedega but how come it crashes my computer? normally when a program crashes (on the rare occasion) i can 'force quit' it.

---

### Post by hobieone on 2007-05-01
i have no issues with cedega 6.0 on my system with an nvidia card. altho one thing that i don't think was mentioned  that will cause cedega to freeze up  is if try ans use it to play a game while you have the desktop effects turned on. found this out while messing with it . when i disable the desktop effects cedega 6.0 worked normally again

---

### Post by webjames on 2007-05-01
> **hobieone said:**
> i have no issues with cedega 6.0 on my system with an nvidia card. altho one thing that i don't think was mentioned  that will cause cedega to freeze up  is if try ans use it to play a game while you have the desktop effects turned on. found this out while messing with it . when i disable the desktop effects cedega 6.0 worked normally again

thanks for the reply, but i type cedega in the console the error mentioned above comes up then my computer freezes, i don't get any gui or anything on my screen

---

### Post by HeavyAl on 2007-05-01
I'm having a similar issue. The same message regarding gddb_parser is displayed but nothing happens - kicks me back to the command line. I'm thinking I might try rolling python back to 2.4 and see if that helps but its odd because some games actually kick off regardless of the error (Diablo 2, Age of Empires). Of course, they are really slow, but thats probably just because this is an older ati card with 32 megs of ram (works fine for native linux games and even supports compiz/beryl to a degree).

Seems the guys over at cedega aren't realy taking it very seriously .. the only thing I can find about it there is that an upgrade of gddb is needed ([http://www.transgaming.com/showthread.php?msg=68291&forum=1262&thread=68268)](http://www.transgaming.com/showthread.php?msg=68291&forum=1262&thread=68268)), but I cant find it in the repos so it must be part of some package and not something that can be installed by hand (I'm guessing part of python which is why I was thinking of rolling it back). 

If anyone else has any info on this it would be much appreciated. I love ubuntu but I'm dying for my games fix!

---

### Post by Perfect Storm on 2007-05-01
post 34 and 35 merged with this thread.

---

### Post by HeavyAl on 2007-05-01
> **webjames said:**
> thanks for the reply, but i type cedega in the console the error mentioned above comes up then my computer freezes, i don't get any gui or anything on my screen

I'm pretty sure that when he said 'desktop effects' he was talking about the compiz effects that are installed in feisty but not on by default - I've found that its hit and miss with them, sometimes a game will work regardless of whether the desktop effects are on, sometimes it wont. I've never had the whole thing lock up on me though .. sounds like a driver issue.

---

### Post by webjames on 2007-05-01
HeavyAl,
yeah the whole computer locks up, it sounds like you can get some games working. is that via the gui? i haven't even been able to accept the user agreement, it comes up once i accept, then my computer freezes, then next time i go to run it (after hard restart) it just locks up, showing the error you seem to be getting. it is really strange. when you say roll back do you mean remove the later version of python ie > 2.4 (greater than version 2.4). i run exaile and that needs 2.4. tell me if you have any luck, it's weird because a lot of people say they have no problem..
thanks for the reply.

---

### Post by Rurki on 2007-05-01
Open Cedega from a shell with:

XLIB_SKIP_ARGB_VISUALS=1 cedega

This resolved the problem for me.

---

### Post by webjames on 2007-05-02
> **Rurki said:**
> Open Cedega from a shell with:

XLIB_SKIP_ARGB_VISUALS=1 cedega

This resolved the problem for me.

thanks for the post. just started it with the line:
```
XLIB_SKIP_ARGB_VISUALS=1 cedega
```
but no luck i'm afraid still froze my computer with the same parser message that has been posted earlier.

---

### Post by EndPerform on 2007-05-02
Not sure why my original post was merged here, but I'm not experiencing a crash or lockup.  The GUI comes up fine, but when I go to install, I get a couple of errors (mentioned in my previous post, now merged here somewhere) and the game never installs, I just get an entry in the left pane of the Cedega GUI.  Been checking out the Transgaming forums, but no one really has any additional information on this.

---

### Post by webjames on 2007-05-02
> **EndPerform said:**
> Not sure why my original post was merged here, but I'm not experiencing a crash or lockup.  The GUI comes up fine, but when I go to install, I get a couple of errors (mentioned in my previous post, now merged here somewhere) and the game never installs, I just get an entry in the left pane of the Cedega GUI.  Been checking out the Transgaming forums, but no one really has any additional information on this.

your problem seems totally separate to the problem i am having. my cedega wont start and freezes my computer up.

**forum admin:** why merge these posts?

---

### Post by HeavyAl on 2007-05-02
> **webjames said:**
> HeavyAl,
yeah the whole computer locks up, it sounds like you can get some games working. is that via the gui? i haven't even been able to accept the user agreement, it comes up once i accept, then my computer freezes, then next time i go to run it (after hard restart) it just locks up, showing the error you seem to be getting. it is really strange. when you say roll back do you mean remove the later version of python ie > 2.4 (greater than version 2.4). i run exaile and that needs 2.4. tell me if you have any luck, it's weird because a lot of people say they have no problem..
thanks for the reply.

Hey James,

Wow, for some reason I missed the part where you said the setup screens actually fail for you. If you cant even accept the user agreement then cedega wont let you install the engine that makes stuff work. 

As far as the roll back is concerned, I've been looking at it a little closer and I think the gddb stuff has something to do with the games database, thus rolling back python might not have any effect. Basically I think we're going to have to wait for either the ubuntu gurus or cedega people to figure this out for us. 

Alternately, what might work is just installing cedega via cvs - that usually means compiling it from source which would force it to use whatever python version is on your system. I'm going to try this today and see what happens. I'll post back when I get some results.

---

### Post by webjames on 2007-05-03
Rafe Magnuson,

on the first install i get a chance to accept the agreement, but as soon as i do i get the freeze up, after i have accepted it (and rebooted) when i run cedega it freezes straight away with the error stated before.

---

### Post by HeavyAl on 2007-05-04
I noticed in an earlier post you mentioned having an nVidia 6600 - thats the same vid card I have.

What other hardware are you running? How about posting your xorg.conf here so we can see how your video is set up. .. you can find xorg.conf in /etc/X11/xorg.conf

---

### Post by webjames on 2007-05-04
Hey well here it is, i think we might have tracked down the source of the problem, i did think it might have been a gffx issue, and as we have the same card, and both are on feisty. did cedega work for you on edgy?

My Xorg:
> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

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
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


---

### Post by HeavyAl on 2007-05-04
Yeah, I did a search for nvidia 6600 on the forums and it look slike several people are having problems with there cards. That said, I did notice right off the bat that here: 

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
EndSection

You dont have any other settings indicating agp, pci, or anything else. Have you tried using the System/Administration/Restricted Driver Manager to install the actual nvidia restricted drivers? If not start with that.

Also, you might benefit from driconf .. I cant remember if I used it for my nvidia card or my ati card though so it might be a moot point, but if you want to try it just do this at a terminal:

```

sudo apt-get install driconf

```

after that run driconf and make sure hyper-z is enabled. 

Finally, try running glxgears -info and post the output from the top section here .. it might be that acceleration just isnt working for some reason.

This is looking more and more like it might be a problem with the 6600 though .. I'm going to hop on over to the nvidia boards and see if anyone knows anything. I'll post back if I find anything of interest.

---

### Post by kvonb on 2007-05-04
My card is an Nvidia 6600GT, and I use the nvidia driver from the nvidia website (version 9746).

I have NEVER had any problems at all, cedega runs as well as cedega ever did.

Here is my xorg.conf if it is any help:

```
 # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

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
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"    # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"    # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"    # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 121.0
    VertRefresh     43.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by webjames on 2007-05-05
I firstly tried the restricted driver, then i installed the latest driver from NVidia myself, neither of them made cedega work, however i am running beryl nicely. i shall put the restricted driver back and do as HeavyAl recommended and post my results.

thanks for the posts guys!

---

### Post by webjames on 2007-05-05
ok so i put the ubuntu restricted drivers back on installed driconf, this is my result:

> james@james-ubuntu:~$ sudo driconf
libGL is too old.

it also pops up a messega box with a no entry symbol with:
> XDriInfo returned with non-zero exit code.
i shall try updating libgl

---

### Post by webjames on 2007-05-05
well i can't find much info on which libgl i'm meant to be using, or how you tell the version but here's some output if it helps:
```
james@james-ubuntu:~$ ldd /usr/X11R6/bin/glxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7eba000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d79000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c87000)
        libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0xb7315000)
        libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0xb7313000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb72ec000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb72de000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb72da000)
        /lib/ld-linux.so.2 (0xb7f5e000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb72d6000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb72d1000)

```

and located the libgl:
```
james@james-ubuntu:~$ sudo updatedb
james@james-ubuntu:~$ locate libGL.so
/usr/lib/libGL.so
/usr/lib/libGL.so.1.0.9755
/usr/lib/libGL.so.1
james@james-ubuntu:~$ 

```

and the current output to glxgears:

```
james@james-ubuntu:~$ glxgears -info
GL_RENDERER   = GeForce 6600 LE/PCI/SSE2
GL_VERSION    = 2.1.0 NVIDIA 97.55
GL_VENDOR     = NVIDIA Corporation

```

and FPS:

```
14136 frames in 5.0 seconds = 2827.136 FPS
16020 frames in 5.0 seconds = 3203.988 FPS
15786 frames in 5.0 seconds = 3157.081 FPS
15521 frames in 5.0 seconds = 3104.028 FPS
14883 frames in 5.0 seconds = 2976.544 FPS
15066 frames in 5.0 seconds = 3012.180 FPS
15257 frames in 5.0 seconds = 3028.037 FPS
14627 frames in 5.0 seconds = 2925.200 FPS

```

how does this compare to yours?

---

### Post by webjames on 2007-05-05
after restarting and reinstalling a few things, i have managed to get driconf working, heres the output:

```
james@james-ubuntu:~$ sudo driconf
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Screen "0" is not direct rendering capable.

```

with error box:
```
Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode.
```

i am not an expert, after i click ok a gui comes up, and i'm not sure what to do.

---

### Post by webjames on 2007-05-05
well after all this i seem to have done something, i now get a white screen when i run beryl, what have i done? maybe time for another feisty reinstall!

**EDIT**
weird thing is now when i click restricted dev management it says i don't need any restricted which is obviously not true!

---

### Post by webjames on 2007-05-06
after a reinstall of feisty the first thing i did was to install cedega, and the same error comes up. beryl, and the RDM works perfectly now i've reinstalled. i think i'm going to just wait for cedega 6.1 and see if that fixes things i've spent enough time on this program and cedega's support has been absolutely useless.

my recommendation save you're money donate it to the wine project and help these guys who are doing things the right way. the money you pay does not justify the service you receive.

---

### Post by kvonb on 2007-05-06
> **webjames said:**
> after a reinstall of feisty the first thing i did was to install cedega, and the same error comes up. beryl, and the RDM works perfectly now i've reinstalled. i think i'm going to just wait for cedega 6.1 and see if that fixes things i've spent enough time on this program and cedega's support has been absolutely useless.

my recommendation save your money donate it to the wine project and help these guys who are doing things the right way. the money you pay does not justify the service you receive.

Amen to that one brother James :).

I cancelled my subscription, I was sick of getting their newsletters telling me how they had a wonderful time going to all these computer shows and staying in nice hotels, when they should have been spending the money on actually getting something other than World of Warcraft working!

Plus we have now paid for the development of the Apple version of Cedega and we still can't play any decent RTS games!

---

### Post by Breepee on 2007-05-06
There's is no Cedega for Apple...

---

### Post by kvonb on 2007-05-06
> **Breepee said:**
> There's is no Cedega for Apple...

Yes there is, it's called "Cider"

Have a look here:

[http://www.transgaming.com/index.php?module=ContentExpress&file=index&func=display&ceid=24](http://www.transgaming.com/index.php?module=ContentExpress&file=index&func=display&ceid=24)

---

### Post by HeavyAl on 2007-05-06
You know, I think I'm at the same point as you two - I'm just going to wait for 6.1 and see if some of these issues get fixed. I tried Wine with a few older games and it worked just fine so I guess it will suffice for the time being. And the fact that wine works where cedega does not is a good indicator to me that something in cedega is broken.

---

### Post by webjames on 2007-05-06
HeavyAl, 
thats what i don't understand:
transgaming took wine, charged for it, made a gui, and managed to break it!!

---

### Post by hikaricore on 2007-05-06
I can't believe someone posted a launchpad bug based on cedega...  doesn't transgaming offer you folks any technical support?

I mean you are paying them for something right?

---

### Post by webjames on 2007-05-07
> **hikaricore said:**
> I can't believe someone posted a launchpad bug based on cedega...  doesn't transgaming offer you folks any technical support?

I mean you are paying them for something right?

apparently not.

---

### Post by HeavyAl on 2007-05-07
Yeah, their support is rather lacking considering its a paid product. I've had much better experiences with simply perusing the forums here for fixes then anything I've gotten from the people at Cedega.

Somehow I did manage to get Cedega to work to some degree but its a painful road that ends up at the command line more often than not .. I can run some games by running the installer using cedega at the command line and then importing the actual executable link into the cedega front end. Still, some games, notably Oblivion which requires shader 2.0 support simply dont run - not even an error message returned - I can start them from the cl and the drive will churn for a few seconds then it just kicks me back to the prompt. 

I've let my Cedega license lapse and am now just using cedega cvs for some stuff (Dungeon Siege 2, and a couple other less intense games) but I might think about paying for it again if they get their support act together.

---

### Post by flapane on 2007-05-09
I installed cedega6, too, but it says
/home/flapane/.cedega/.winex_ver/winex-6.0/winex/bin/wine: can't exec '"/media/sdb1/Programmi/Maxis/SimCity 3000 World Edition/Apps/SC3U_crk.exe"': error=21

on every game...
I googled and error=21 is referring to some special option in fstab, but I can't understand which one...
any help?

---

### Post by HeavyAl on 2007-05-09
Sorry, but I gave up and went back to WINE! 

That said, I looked into your error and as you say, one way to get rid of the error is to edit /etc/fstab .. but that appears to actually be more of a bandaid rather than an actual fix. The problem is that the file system that you are trying to run the game from has no executable permissions. What you probably want to do is install the game a writeable drive - say a new directory in your home folder for example - and run it from there.

If you're sure you want to run it from its current location all you have to do is edit the above mentioned file and change anything in it that says no-exec to exec.

---

### Post by flapane on 2007-05-10
the ntfs partition is already on exec...
the funny thing is that I could run games this winter (i wonder with cedega5.2)...

---

### Post by webjames on 2007-05-11
> **flapane said:**
> the ntfs partition is already on exec...
the funny thing is that I could run games this winter (i wonder with cedega5.2)...

i would not recommended using an ntfs partition

---

### Post by flapane on 2007-05-11
the games are installed and currently played in windows...
i would not do a double installation

---

### Post by thom_raindog on 2007-06-09
*bump*

I may not be the OP, but I have a problem looking a lot like this one.
My desktop may not freeze, but I can't use cedega either, because it throws
```
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser

```
on startup.

Transgaming forum are - as usual - of no help.

---

### Post by citizenr on 2007-06-10
this is because of python 2.5, cedega advises to downgrate to 2.4, but ?I cant do it under feisty, even with 2.4 installed uninstalling 2.5 marks half the packages ffor removal :/

---

### Post by thom_raindog on 2007-06-10
Well, I got that worked out by installing 2.4 and then changing the file
/usr/bin/cedega

to say python2.4 in the very last line as opposed to python.

but if that actually solves our problems, or just stoped the error from showing.. who knows..
I certainly didn't let me run WoW on Cedega

---

### Post by citizenr on 2007-06-10
sadly you are right :(
with python 2.5 jagged Alliance 2 ver1.13 runs the starting screen, displays logo and then 
"ERROR
Press RETURN to continue"
presing return returns you to command line, this is with 
```
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
```

after modding last line to python2.4 like you did all I get is 
```
rasz@capek:/gry/Jagged Alliance 2 Gold$ cedega ja2.exe
 F1 2007-06-11 02:47:18,261 WARNING Optical drive detection: No optical drives found - dbus/hal may not be correctly configured.
rasz@capek:/gry/Jagged Alliance 2 Gold$

```

so python is only one of the things that dont work in Feisty now, but Cedega did work in feisty before, at least 1-2 months before (I remember playing jagged alliance)

---

### Post by thom_raindog on 2007-06-11
Looking through posts with problems in Feisty on the Transgaming Forums I would assume it started around april, since a lot of problems were reported around then.. that would indicate Feisty always had problems...

I am honestly tempted to try edgy again, just to see if that works.

Funny thing: Even now some people out there use Feisty and Cedega and are happy.. so why?

---

### Post by citizenr on 2007-06-11
I reinstalled cedega, reinstalled JA2 and it works now .. just like windows lol :)
funny thing that ja2 worked under wine before reinstall, but didnt in cedega
that python bug is only affecting cedega game database, so its not critical

---

### Post by thom_raindog on 2007-06-12
Well, that leaves the question: Why does WoW do nothing for me under cedega, no matter what I do....

---

### Post by dragonphyre on 2007-06-23
Did the uninstall, did not work for me. Took me FOREVER to get the binary-blob drivers working--so i'm NOT uninstalling them.

I get this error message as well:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  72 (X_PutImage)
  Serial number of failed request:  81
  Current serial number in output stream:  93
```

---

