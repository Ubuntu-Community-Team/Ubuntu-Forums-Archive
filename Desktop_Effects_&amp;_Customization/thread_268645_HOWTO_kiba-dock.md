---
title: "HOWTO: kiba-dock"
date: 2006-09-30
forum: Desktop Effects &amp; Customization
---

### Post by PriceChild on 2006-09-30
[COLOR=Black][B]Get Edgy/Feisty debs here from gnomefreak: [http://gnomefreak.youmortals.com/Edgy/](http://gnomefreak.youmortals.com/Edgy/)

[SIZE=6][COLOR=Red]May Currently Be Broken
[SIZE=6][_Please use this guide instead :)_]("http://ubuntuforums.org/showthread.php?t=554127")[/SIZE]
[/COLOR][/SIZE] [/B][/COLOR]
```
sudo aptitude remove automake1.4
sudo aptitude install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool [SIZE=3]libgtop2-dev[/SIZE]
```checkinstall isn't required... and is pretty nasty... I don't like it... but it "works"ish. Use "sudo make install" instead of "checkinstall" in this guide if you want :)

Get source:
```
mkdir kiba-dock
cd kiba-dock
svn co [http://svn.kiba-dock.org/akamaru/](http://svn.kiba-dock.org/akamaru/) akamaru
svn co [http://svn.kiba-dock.org/kibadock/](http://svn.kiba-dock.org/kibadock/) kibadock
svn co [http://svn.kiba-dock.org/kibaplugins/](http://svn.kiba-dock.org/kibaplugins/) kibaplugins
svn co [http://svn.kiba-dock.org/gsetkiba/](http://svn.kiba-dock.org/gsetkiba/) gsetkiba

```Build each in turn:
(Don't forget to make the versions for each package something sensible instead of LOTS of 0.1s)
```
cd akamaru/
./autogen.sh
make
sudo checkinstall
cd ../kibadock/
./autogen.sh
make
sudo checkinstall
cd ../kibaplugins/
./autogen.sh
make
sudo checkinstall
cd ../gsetkiba/
./autogen.sh
make
sudo checkinstall
```btw just use "kiba-dock" to run.

> **abstar said:**
> if you have this error:

*kiba-dock: error while loading shared libraries: libakamaru.so.0: cannot open shared object file: No such file or directory*

just do this:

sudo ln -s /usr/local/lib/libakamaru.so.0 /usr/lib/libakamaru.so.0

because Now if you try to run kiba-dock from the terminal, you will get another error about the file 'libakamaru.so.0'. This file was installed into /usr/local/lib instead of /usr/lib.

---

### Post by jasnix on 2006-09-30
Thanks so much!

This worked perfectly.


I have attached an AMD_64 .deb as well.

---

### Post by biasquez on 2006-09-30
doesn't work for me, i see only dock without icons. i tried as .deb as tar.bz2.

---

### Post by | MM | on 2006-09-30
I don't get how to use it either, all i see is this little pixel thick line at the bottom centre of my screen, but nothing that looks like a dock :(

---

### Post by PriceChild on 2006-09-30
That's the dock guys.... it doesn't come with any as standard.

Drag some icons onto it from the menu :)

---

### Post by pau on 2006-09-30
didn't work for me...

when I try to create the deb package I get
Copying files to the temporary directory...OK

```
Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]:

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK
```

The log file is:

```
dpkg-deb - error: (upstream) version («dock») doesn't contain any digit
dpkg-deb: 1 errors in the control file
```

When I download your deb and install it, it doesn't launch because
```

(kiba-dock:26305): Gdk-WARNING **: locale not supported by Xlib

(kiba-dock:26305): Gdk-WARNING **: cannot set locale modifiers
kiba-dock: symbol lookup error: kiba-dock: undefined symbol: g_type_register_static_simple
```

Any hint??

---

### Post by pau on 2006-09-30
By the way, it starts with

```
*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "dock" does not
*** Warning: contain any digits. dpkg might not like that.
```

---

### Post by pau on 2006-09-30
ok, I found the solution... I pressed 3 and gave it a number for the version **[SIZE="3"]BUT[/SIZE]** the dock has still a black background and the icons too ](*,)

---

### Post by notarikon on 2006-09-30
I *think* you'll find the black backgrounds are due to not having compiz/xgl installed ... maybe :)

---

### Post by PriceChild on 2006-09-30
pau try installing again, i got that first time :P

> **pau said:**
> By the way, it starts with

```
*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "dock" does not
*** Warning: contain any digits. dpkg might not like that.
```
As for this... its just me having no experience with packaging :)
It'll work just fine still.

---

### Post by pau on 2006-10-01
I thnk you're right, the problem must be xgl... must it be runnig for the kiba dock to work properly? I tried to install it but no way... BTW any suggestion how to install xgl/compiz on an ati ibm thinkpad t43p? What's the difference between compiz and beryl? It's a new fork but what are the differences/avantages/disavantages etc?

---

### Post by geearf on 2006-10-01
Hello,

I wanted to try kiba-dock, but it seems to need a lot of gnome libraries, isn't there a way to have a clean Kde system with this ?

Thanks.

---

### Post by bugz0r on 2006-10-01
Will this work if I dont have XGL/Compiz?

---

### Post by Uncle Spellbinder on 2006-10-01
[*_**Edgy kiba-dock package**_*](http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package)

Deb package for Edgy. And it works GREAT! Just starting to configure it.

[[IMG]http://img480.imageshack.us/img480/5000/kibave4.th.png[/IMG]](http://img480.imageshack.us/my.php?image=kibave4.png)

---

### Post by nrayever on 2006-10-01
this damn cool!! sincerly i'm love with linux!!! long life to open source!! when i showed this fx to my brother, a mac user, he said: "just a copy of mac fx." but i reply to him: "maybe, kind, but the code it's original!"

we know that even this is new for mac, but lets make them think that they have the lastest fx...

nrayever

pd: i can't still believe that making a dv video rendering/codec/decodec on a mac, using final cut and as the codec mpeg4, takes a lot of time. and by a lot of time, i really mean a lot of time!!

---

### Post by PriceChild on 2006-10-01
> **Uncle Spellbinder said:**
> [*_**Edgy kiba-dock package**_*]("http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package")

Deb package for Edgy. And it works GREAT! Just starting to configure it.
Just pointing out i attached my Edgy package on the first post.

---

### Post by atie on 2006-10-01
I read this thread now, umm... there is a small thing added to the edgy deb linked by Uncle Spellbinder above - able to launch kiba-dock from the menu.

---

### Post by Uncle Spellbinder on 2006-10-02
> **atie said:**
> I read this thread now, umm... there is a small thing added to the edgy deb linked by Uncle Spellbinder above - able to launch kiba-dock from the menu.

Kiba Dock shows up in the applications browser, which is very nice. I even added it to USP, working great.

---

### Post by Dr. Nick on 2006-10-02
> **PriceChild said:**
> Just pointing out i attached my Edgy package on the first post.

Was yours generated by checkinstall? It installed for me but didnt work correctly, kept crashing when i added icons. I tried the deb linked in the last post and it installed more dependencies (libglitz1) that were not installed with yours, after removing your deb and using that one it works just fine.

---

### Post by brottman on 2006-10-02
I installed Kiba with the deb package here and seems to be working correctly. I have this weird blue striped box around it though. Any ideas?

---

### Post by jsage on 2006-10-02
> **brottman said:**
> I installed Kiba with the deb package here and seems to be working correctly. I have this weird blue striped box around it though. Any ideas?

This is the default dock background.  Go to your main menu, then select System Tools -> Configuration Editor.

In the editor, navigate to apps -> kiba -> options -> style.

Play here to change your settings.



have fun,
john

---

### Post by brottman on 2006-10-02
> **jsage said:**
> This is the default dock background.  Go to your main menu, then select System Tools -> Configuration Editor.

In the editor, navigate to apps -> kiba -> options -> style.

Play here to change your settings.



have fun,
john

I have the editor open but I dont see Style. Under Apps -> Kiba --> Options I only see auto_hide, geometry, and physic. Am I looking in the wrong place?

Brian

---

### Post by jsage on 2006-10-02
> **brottman said:**
> I only see auto_hide, geometry, and physic. Am I looking in the wrong place?

Brian,

If you installed from CVS, then cd to your kiba folder ( ~/kiba-dock ) and run this in a terminal window:

gconftool-2 --install-schema-file=kiba.schemas

This will populate the configuration tree.  If you installed from a deb, I don't know how to do it :-#

---

### Post by rupy on 2006-10-08
When I run: gconftool-2 --install-schema-file=kiba.schemas

It fails with:
I/O warning : failed to load external entity "kiba.schemas"
Failed to open `kiba.schemas': No such file or directory

---

### Post by llamakc on 2006-10-10
Wow. Kiba-dock is awesome. Thanks for the howto.

---

### Post by PriceChild on 2006-10-10
> **Dr. Nick said:**
> Was yours generated by checkinstall? It installed for me but didnt work correctly, kept crashing when i added icons. I tried the deb linked in the last post and it installed more dependencies (libglitz1) that were not installed with yours, after removing your deb and using that one it works just fine.
Sorry :)

---

### Post by mthaddon on 2006-10-10
> **PriceChild said:**
> That's the dock guys.... it doesn't come with any as standard.

Drag some icons onto it from the menu :)

Did that, and all the icons show as the Firefox icon (the Ubuntu default icon). I installed on my machine at work (Dapper - the one with the problems is Edgy) at it worked fine.

Any ideas?

Thanks, Tom

---

### Post by Sariel Amraphel on 2006-10-12
Well, I installed it, tried it out for about half an hour, and even though I love the idea, it's gone now.

Reasons: 
- I can't get the icons to be aligned as I want them to be
- For some reason, when I try to drag the icons to the place I want them to be, every single icon goes to the top-left corner of the screen
- If I hold my mouse over an icon for a few seconds without clicking and then take the mouse away again, every single icon bounces all over the screen

Too bad, hope it'll be better with the next release. Anyway, good job so far for making it, hope it'll get better :)

---

### Post by ayoli on 2006-10-12
actually, to keep icons order it seems we have to st dock model to *rope* but, it works strange here. icons don't stay on the bar.
another thing that would be great to have is an arrow or something like that under icons of programs already opened, and something such a task-list ability (dock opened windows that have no icons set in the docker).
I see in the feature request for kiba thread on beryl forum that these features aren't coming soon, so i keep usin kxdocker for the moment.

---

### Post by Aberrix on 2006-10-13
> **pau said:**
> ok, I found the solution... I pressed 3 and gave it a number for the version

I was having the same problem and this solved it for me as well.

---

### Post by hawks1282 on 2006-10-13
I followed your directions but when i got to  "sudo checkinstall" it said command not found.  ANy ideas on what I've done wrong
(P.S. I'm very new to Linux)

---

### Post by PriceChild on 2006-10-13
> **hawks1282 said:**
> I followed your directions but when i got to  "sudo checkinstall" it said command not found.  ANy ideas on what I've done wrong
(P.S. I'm very new to Linux)```
sudo aptitude install checkinstall
```

---

### Post by mthaddon on 2006-10-13
Any chance you can offer some wisdom on my issue? All the icons default to whatever the first icon is that I drag there. When I hover over them, I can see the "correct" icon pulsing underneath, and I've tried using the icon editor (which displays the icons correctly in the preview).

I'm using 0.1-1.2  (the i386 deb from the beryl forums, but I had the same problem with the previous version as well). 

It works fine on my work computer which runs Dapper rather than Edgy.

Thanks, Tom

---

### Post by hawks1282 on 2006-10-13
Tried sudo aptitude install checkinstall.  Now it reports that it couldn't find any package with the name checkinstall . . . 

Maybe I used the wrong/incomplete directions, i followed the procedure described in the first post of this thread.  

Thanks for the quick response though

---

### Post by hawks1282 on 2006-10-14
Never mind, i just got it.  Didn't have the deb in my sources.list file.  Thanks for the help

---

### Post by xpod on 2006-10-16
Ok..anyone fancy shoving me in the right direction??

Got beryl running fine on edgy and have tried this "how to" but am a bit stuck after the download tar.bz2 part..
I`ve not had dealings with "tar.bz" type stuff yet so after downloading to desktop OR home and trying to run those commands im just getting told "no such file or directory" after the second command.

Ive tried extracting the stuff first too but just seem to be getting nowhere.
Everything went well till i got to that stage and realised i aint had to install this way before.........

Yes this is what happens when you get to used of "automatix and synaptic" but  
if anyone would like to point out what im doing wrong OR not doing full stop i`d be ever so greatfull...

Got beryl working (mostly)so cheers for them how to`s anyway pricey.......

EDIT....typical.Just found the "deb" package which i know how to install so just need to suss out how to use it now :twisted: 
Got some blue "roller" thing for my troubles...great:rolleyes: ...lol
cheers anyway...having fun figuring configuring

sussed it:mrgreen: .....now if i could only make it rain:-k

---

### Post by calvinthomas on 2006-10-18
Has anyone managed to get the settings right so that in rope model the dock ALWAYS puts the icons down in one straight line. It only happens about 30% of the time for me after a reboot and I have to restart the dock (or change models) normally a couple of times before they are all straight!

Having said that, it does look really cool!

PriceChild out of interest are you maintaining your .deb for this? I.e. have you updated it to the very latest version (I think thats 0.113 or something like that?)

Calv

---

### Post by Keshyden on 2006-10-19
I followed this and everything worked. When I run it all I get is a black box. When I drag icons to it, it just makes the black box wider.

---

### Post by Anonii on 2006-10-19
Anyone figured out how to make it transparent, without Beryl/Compiz?

Thanks!

---

### Post by PriceChild on 2006-10-19
I'm gonna package a new deb tonight.

And you NEED a composite manager insalled to make it transparent :)

---

### Post by ayoli on 2006-10-19
> **Anonii said:**
> Anyone figured out how to make it transparent, without Beryl/Compiz?

Thanks!

use xcompmgr
```
sudo aptitude install xcompmgr
```

---

### Post by Lopsicle on 2006-10-20
How do I uninstall without it taking half my OS with it? Thank you :)

---

### Post by loell on 2006-10-21
i think life is easier with kiba without beryl/xgl

---

### Post by PriceChild on 2006-10-21
> **Lopsicle said:**
> How do I uninstall without it taking half my OS with it? Thank you :)uninstall kiba-dock?

Could you give us the terminal output?

---

### Post by ayoli on 2006-10-21
> **Lopsicle said:**
> How do I uninstall without it taking half my OS with it? Thank you :)

if installed fellowing this howto (using checkinstall) then:
```
dpkg -r kiba-dock 
```
will remove only kiba-dock.
eventually you can use gtk-orphan to remove unused libs if any left.

---

### Post by Lopsicle on 2006-10-23
Thanks PriceChild & Ayoli, but finally figured it out how to get it working (well sort of) ;) just me being impatient again :mrgreen:

---

### Post by MyNameUhBorat on 2006-10-24
I keep getting this after following the installation guide. Any ideas of what I'm doing wrong?


========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by swp6499 on 2006-10-24
hope this might help for anyone not wanting to build the package...there is a .deb package for kiba-dock here [http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package](http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package)

it works for me quite well...

---

### Post by maddog39 on 2006-11-28
All the download links are dead, can anyone please update them.

---

### Post by 4KvRMU7Nnv on 2006-11-29
I'm pissed about that too.  Beryl-project.org is down so I can't get the latest kiba-dock.  I've done it before on a previous install when the site wasn't down but now I can't.  Would be very thankful if someone uploaded their .deb that they got there. thanks!

---

### Post by telovoyagarcar on 2006-12-08
it does not work for me...
i get a black box at the bottom and the icons i add to it disappear on mouse over ...

---

### Post by sheriffdaone on 2006-12-09
Well i did what was written on the first page but when i type kiba-dock it gives a "command not found" error. So what's wrong with it, i'm using dapper also i don't have xgl on my computer. Could it be because of that?

---

### Post by Julolidine on 2006-12-10
Here's the message I get from terminal

```
got desktop file: x-nautilus-desktop:///CD-RW%2FDVD%2BRW%20Drive.volume
** Message: Cant handle Relative path
Use a programm for dragging wich sends a fullpath
xfce4-appfinder for example should work

```

Have Edgy with Beryl, but Beryl is not running....however this looks more like a gnome issue perhaps?

I get the same problem as other people, nothing is added to the bar when I drag it.  I installed from the .deb, and it claims I had no dependency issues.  I tried doing the make, but it wanted to downgrade one of my packages, so I decided against the compile.

Edit:  Heres the message from terminal when I try to install the base packages
```

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
mesa-common-dev [6.5.1+cvs20060824 (now) -> 6.5.1~20060817-0ubuntu3 (edgy)]

```

---

### Post by cruiseoveride on 2006-12-12
wats with the ugly blue background.
how do u get rid of it!

---

### Post by flapane on 2006-12-13
64bit version [http://www.dpb.org.uk/ubuntu/edgy_6.10/kiba-dock_0.1.0-1_amd64.deb](http://www.dpb.org.uk/ubuntu/edgy_6.10/kiba-dock_0.1.0-1_amd64.deb)

---

### Post by tdeboeser on 2006-12-15
Wonderful app!!! Fun, cool, usable ...

 I got my "blacked out" problem fixed.  I installed xcompmrg and then enable "Composite"

```


Section "Extensions"
#    Option         "Composite" "Disable"
    Option         "Composite" "Enable"
EndSection


``` 

to /etc/X11/xorg.conf

  BUT now I have a different problem.  Kiba-dock works well, but the apps come up without my color scheme ( WaSP 2.0 ).  I.e. Evolution  menu bars are fine but my panes and folders are basic black and white.
  I've also noticed the "icon-editor", and "gset-kiba" have no real scheme/colors/theme.  

My build is from the CVS.

Think I'll try the deb package.

Tom de

---

### Post by tdeboeser on 2006-12-18
> **tdeboeser said:**
> 

  BUT now I have a different problem.  Kiba-dock works well, but the apps come up without my color scheme ( WaSP 2.0 ).  I.e. Evolution  menu bars are fine but my panes and folders are basic black and white.
  I've also noticed the "icon-editor", and "gset-kiba" have no real scheme/colors/theme.  


Tom de

Looks like I found my problem.  My KDE GTK settings weren't happy.

Alss good now!

Tom de

---

### Post by lostelectron on 2006-12-18
Hi all,

 
   I am having a problem with Kiba-dock.
I am on Kubuntu Edgy. I installed Beryl  yesterday and it is working fine.
I installed Kiba-dock by downloading the source and ./configure make make install.
It did not work. I later installed the .deb package too.

There are 2 problems with my kiba-dock:

1. It gives funny message like :

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

2.  The command kiba-dock does not give me anything. 

<EDIT>
 The solution to both problems is as folllows:

Solution to 1. The error messages are due to wacom devices in /etc/X11/xorg.conf
Take a backup of your xorg.conf before editing and comment the following sections:

#Section "InputDevice"
# Driver "wacom"
# Identifier "stylus"
# option "Device" "/dev/wacom"# Change to
# option "Type" "stylus"
# option "ForceDevice" "ISDV4"# Tablet PC ONLY
# # /dev/input/event
# # for USB
#EndSection

#Section "InputDevice"
# Driver "wacom"
# Identifier "eraser"
# option "Device" "/dev/wacom"# Change to
# option "Type" "eraser"
# option "ForceDevice" "ISDV4"# Tablet PC ONLY
# # /dev/input/event
# # for USB
#EndSection

#Section "InputDevice"
# Driver "wacom"
# Identifier "cursor"
# option "Device" "/dev/wacom"# Change to
# option "Type" "cursor"
# option "ForceDevice" "ISDV4"# Tablet PC ONLY
# # /dev/input/event
# # for USB
#EndSection

and furher down in: Section "ServerLayout"

# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents" 

Solution to 2. This may seem dumb, but all you have to do is run populate-dock.sh
</EDIT>

---

### Post by aliyanage on 2006-12-18
Hi, 

I've installed it and the installation worked fine but when I now try to run it by typing "kiba-dock" is says that there is no file or directory... anyone who has a clue?

by the way I am running beryl, does that make a difference?

regards
aliyanage

---

### Post by habtish on 2006-12-18
First off, thanks PriceChild for the  great HowTo. .. My first CVS build I already feel like Mr smarty pants......
My question is rather simple and hopefully it has happened to some4one in here and I will get a simple solution. After adding icons to the dock, I get these Blue arrows [>>] in groups of 2-4 scattered on the screen pointing to the dock, to let me know I have added an icon i guess... problem is.. those arrows stay and they are on top of all windows...doesn't matter what I am doing.. I have the arrows covering part of my view... how can I take care of this?

---

### Post by Blario on 2006-12-22
> **Uncle Spellbinder said:**
> [*_**Edgy kiba-dock package**_*](http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package)

Deb package for Edgy. And it works GREAT! Just starting to configure it.

[[IMG]http://img480.imageshack.us/img480/5000/kibave4.th.png[/IMG]](http://img480.imageshack.us/my.php?image=kibave4.png)

ATTENTION:  Can someone please update this link.  No one viewing this thread now can download the working .deb, since beryl-project.org crashed since the original post.  Can someone please post a link to the working beryl-project.org .deb.  Thankx!

---

### Post by Blario on 2006-12-22
I have installed Kiba-dock from source, seems to be working fine, except that I can only run it as root.  When I run it as my user, nothing happens, but the process stays open.  I'm running from terminal using 'kiba-dock' ('sudo kiba-dock' for root).

This wasn't an issue at first, except that any launcher I click from the dock runs as root b/c of that.  Not cool!  I configured and made ('./configure' & 'make') as my user... are there any ideas as to why I can only run it as root?

---

### Post by PriceChild on 2006-12-22
> **Blario said:**
> ATTENTION:  Can someone please update this link.  No one viewing this thread now can download the working .deb, since beryl-project.org crashed since the original post.  Can someone please post a link to the working beryl-project.org .deb.  Thankx!I haven't a clue where you can find those.

If I were you, I would follow my instructions in the original thread and build from cvs source.

---

### Post by moclippa on 2006-12-23
**If anyone is still having problems with the odd blue background** its rather a simple fix if you guys haven't figured it out yet... Sorry haven't gone through all the pages on this topic.

in terminal type > gset-kiba

Then go to Color/Alpha

You can feel free to lower all of the settings to 0 if you want your dock to be totally transparent

Otherwise you can do what I did and switch anything that says Gnome-Dock in the Style/Misc. tab to Gradient... then mess around with the color settings just to have a nice tone in the  background, and remove the border completely by setting it to 0.

**If you are getting the black background**, either install XGL (AIGLX does not seem to work for me when I tried to replicate that issue) or, if you prefer not to... try installing xcompmgr (another window manager) to sort out your issue.

> sudo apt-get install xcompmgr

once installed

> xcompmgr to start it up.

[SIZE="1"](xcompmgr fix is borrowed from [http://www.macewan.org/2006/11/29/howto-fix-kiba-dock-black-background/)](http://www.macewan.org/2006/11/29/howto-fix-kiba-dock-black-background/))[/SIZE]

Hope that Helps.

---

### Post by FunnyLookinHat on 2006-12-24
Just a note to you [SIZE="4"]KDE[/SIZE] users out there....

You will find two other packages in the ubuntu repositories that may work much more easily for you:

ksmoothdock
and
kooldock   <---  This is a more updated version of ksmoothdock that is apparently still maintained

gl/hf   : )

---

### Post by flapane on 2006-12-24
I'll note for the next time, as it seems kiba is working wonderfully on my kde box

---

### Post by Blario on 2006-12-24
> **rupy said:**
> When I run: gconftool-2 --install-schema-file=kiba.schemas

It fails with:
I/O warning : failed to load external entity "kiba.schemas"
Failed to open `kiba.schemas': No such file or directory
For anyone still looking, the command to install the schemas from the source directory is ```
make install-schemas
``` Until I did this, none of the changes to the configuration of the dock took effect nor were saved after I restarted it.

I'm currently not using the dock, b/c it uses too many resources.  What were the names of the alternatives to kiba-dock?  something like kdocker.... or something like that.  Anyone?

---

### Post by PriceChild on 2006-12-24
Why don't people read howtos?

This was in the first post Blario!

---

### Post by Blario on 2006-12-25
> **PriceChild said:**
> Why don't people read howtos?

This was in the first post Blario!
Obviously!  Where do you think I got it from?!  Obviously ppl weren't seeing it because of all the problems they were having.  Anyways, in case you can't tell, the howto wasn't complete from the start; Hence all the problems that everyone was having.  The originally posted deb definitely doesn't work; Hence all the pleas for a working deb from the second forum admin that posted.  It was an Amateur attempt.  Of course there's nothing wrong with that, seeing that there was nothing like it before; someone has to do it; and at least it pointed people in the right direction :)

---

### Post by habtish on 2006-12-26
PriceChild, I had followed this howto to build kiba-dock from source and it was working great... as time went on, my system seemed to be lagging a lot, <top> shows a high percentage of cpu usage by x.org and kiba-dock. I was using xcomp as my conpositing engine.. not sure if anyone had faced this issue...also, even decreasing the hide area to a very low value o autohide didn't help as the dock keeps on popping out when my cursor is miles away from the dock area... this was verry annoying as you are trying to scroll down or do something else in  an open window and kiba keeps on popping up

---

### Post by ibero on 2006-12-27
I follow the steps and it's not working for me, I got:

Copying files to the temporary directory...OK
Striping ELF binaries and libraries...OK
Compressing man pages...OK
Building file list...OK
Building Debian package... FAILED!
*** Failed to build the package

Any ideas..Thanks?:-k

---

### Post by ibero on 2006-12-27
Problem solved ...

---

### Post by PriceChild on 2006-12-27
> **ibero said:**
> Problem solved ...how?

---

### Post by d3v1ant_0n3 on 2006-12-27
I'm getting an error on make - I assume it's something to do with the new clock plugin?

```
kiba-dock.c:36:24: error: kiba-clock.h: No such file or directory
kiba-dock.c: In function ‘kiba_reload’:
kiba-dock.c:370: error: dereferencing pointer to incomplete type
kiba-dock.c: In function ‘timeout_callback’:
kiba-dock.c:441: error: dereferencing pointer to incomplete type

```

---

### Post by Face2thehighfog on 2006-12-28
Everything seemed to go ok until I got to the make command.  Then I got this:

/kiba-dock.Tpo"; exit 1; fi
kiba-dock.c:36:24: error: kiba-clock.h: No such file or directory
kiba-dock.c: In function ‘kiba_reload’:
kiba-dock.c:370: error: dereferencing pointer to incomplete type
kiba-dock.c: In function ‘timeout_callback’:
kiba-dock.c:441: error: dereferencing pointer to incomplete type


Any help would be great :O)

Thanks

---

### Post by Face2thehighfog on 2006-12-28
Opps, must have missed the reply before mine.  Same prob.

---

### Post by weapon-x on 2006-12-28
hi friends i have installed the kiba i can run its a user but when i become root its shows me an error.
the error is :-
> ** Message: error while creating launcher icon: /root/Desktop/SantaClausHat_lnx.zip_FILES/SantaClausHat_lnx/icons/Hat_128x128

** Message: found unused desktop file in homdir
try to merge /root/.kiba-dock/torrents to gconf

** Message: Failed to merge unused desktop file /root/.kiba-dock/torrents. notifications: Bad key or directory name: "/apps/kiba/launchers//file": Can't have two slashes (/) in a row

** ERROR **: Failed to read config from gconf: Failed to read config from gconf: Failed to read config from gconf: Failed to read config fr
aborting...
Aborted (core dumped)


please help ](*,)

---

### Post by kevinlang21 on 2006-12-28
For me, everything works until

> make install-schemas

It gives me > GCONF_CONFIG_SOURCE= \
                gconftool-2 --makefile-install-rule files/kiba.schemas
files/kiba.schemas:419: parser error : StartTag: invalid element name
<<<<<<< kiba.schemas
 ^
files/kiba.schemas:419: parser error : StartTag: invalid element name
<<<<<<< kiba.schemas
  ^
files/kiba.schemas:419: parser error : StartTag: invalid element name
<<<<<<< kiba.schemas
   ^
files/kiba.schemas:419: parser error : StartTag: invalid element name
<<<<<<< kiba.schemas
    ^
files/kiba.schemas:419: parser error : StartTag: invalid element name
<<<<<<< kiba.schemas
     ^
files/kiba.schemas:419: parser error : StartTag: invalid element name
<<<<<<< kiba.schemas
      ^
files/kiba.schemas:419: parser error : StartTag: invalid element name
<<<<<<< kiba.schemas
       ^
make: *** [install-schemas] Error 1


---

### Post by Rashid584 on 2006-12-28
wow gettin it to accept an icon is a mission :| after about 5 tries each icon it decides itll let me add it :S

Got a better idea, copy .desktop files from /usr/share/applications(/kde) to ~/.kiba-dock :D

Only problem is you cant minimise windows to it like in OS X :( until it can do that... :(

-Rashid

---

### Post by abu_nawas on 2006-12-29
> **d3v1ant_0n3 said:**
> I'm getting an error on make - I assume it's something to do with the new clock plugin?

```
kiba-dock.c:36:24: error: kiba-clock.h: No such file or directory
kiba-dock.c: In function ‘kiba_reload’:
kiba-dock.c:370: error: dereferencing pointer to incomplete type
kiba-dock.c: In function ‘timeout_callback’:
kiba-dock.c:441: error: dereferencing pointer to incomplete type

```
i have this problem too. anyone help please...

---

### Post by PriceChild on 2006-12-29
I'm just guessing latest cvs is broken... and I don't have a working cvs so you'll just have to wait sorry.

---

### Post by d3v1ant_0n3 on 2006-12-29
I waited. It's fixed. I checked the thread on beryl-project forums.

---

### Post by chiklit on 2006-12-30
Is it supposed to look all funky like this?

---

### Post by PriceChild on 2006-12-30
> **chiklit said:**
> Is it supposed to look all funky like this?That's it :)

Drag launchers on from menus/panels to add them.

right click and change the settings with one of the options.

---

### Post by Rashid584 on 2006-12-30
yir...dunno why they made it look like that but you can customise it to how you want it. heres a shot of mine

btw i dont actually use it like that...kiba dock doesny have any taskbar functionality so i just have it on the right side as an app launcher...still need kicker at the bottom of the screen for the taskbar and k-menu...

if there was a way to get the kmenu, and OS X style tasks (screenshots or even icons) on the dock id be happy :D

(i know you can do that with kxdocker but i like kiba docks pulse mouseover effect :D and the other cwazy effects :D)

-Rashid

---

### Post by lucid on 2007-01-02
I followed the Howto to the letter and it didn't work for me...

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

---

### Post by Rashid584 on 2007-01-02
use the .deb package instead of building from source

-Rashid

---

### Post by Blario on 2007-01-02
> **weapon-x said:**
> hi friends i have installed the kiba i can run its a user but when i become root its shows me an error.
the error is :-



please help ](*,)
You shouldn't be running GUI as root.

---

### Post by Afteraffekt on 2007-01-02
I get the Black Kiba Dock up, but i cant get transparency, Iv installed compiz and try compiz  --replace and i get ,No composite extension, iv then installed xcompmgr and run the command xcompmgr and i get the same error? what have i done wrong

---

### Post by fokuslee on 2007-01-03
I have the same problem as Pau and Ibero Is the CVS broken again? 
I am building with beryl running and in gui mood does that matter? 
also my autoconf is version 2.6
some other guide use 2.16 obsolete version maybe better luck with that?
for the mean time i was able to install with the prebuilt package couple of posts up
is there a official website for kiba-dock?

PS sites to china and taiwan and japan are superslow b/c the opticfiber undersea is broken by storm
im not making this up this mite affect some of your dls

---

### Post by PriceChild on 2007-01-03
> **Rashid584 said:**
> use the .deb package instead of building from source

-RashidWhat deb?

---

### Post by kwaanens on 2007-01-04
The one listed in the first post of this thread: [http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb](http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb)

---

### Post by victorbrca on 2007-01-04
Relating a different problem.

After running ... ```
./autogen.sh
``` I'd get the msg that "libgtop" (LGTOP) was not present.

I solved it by using the .deb from the original post.


Vic.

---

### Post by Quillz on 2007-01-05
Wow! Thanks for this. Kiba-dock is by far the best docking app I've seen yet for Ubuntu.

---

### Post by albert006 on 2007-01-05
After pressing "3" and giving it version "1" it installs and works great. Thanks!

---

### Post by navneeth on 2007-01-05
What am I to make of these?

At the end of ./autogen.sh
(I didn't notice this first time and went ahead to the next step)

```
checking for LGTOP... configure: error: Package requirements (libgtop-2.0 >= 2.0.0) were not met:

No package 'libgtop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LGTOP_CFLAGS
and LGTOP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

make:

```
make: *** No targets specified and no makefile found.  Stop.

```

make install-schemas:

```
make: *** No rule to make target `install-schemas'.  Stop.

```

checkinstall:

```
Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

---

### Post by PriceChild on 2007-01-05
navneeth install libgtop-2.0 from the repos and try again.

---

### Post by navneeth on 2007-01-05
In which repo can I find this file? I think I have the uni and multiverse repos, but I get a message saying that no such package was found.

---

### Post by victorbrca on 2007-01-05
> **navneeth said:**
> In which repo can I find this file? I think I have the uni and multiverse repos, but I get a message saying that no such package was found.


> I'd get the msg that "libgtop" (LGTOP) was not present.

I solved it by using the .deb from the original post.


Vic.

Hope that helps!!!

---

### Post by navneeth on 2007-01-05
victorbrca, 
          Thanks. It worked, i.e. I now have kiba-dock installed, but since I don't have beryl, there's an ugly black border. :(

---

### Post by Shadito on 2007-01-05
Hi, the .deb works, but today in one update (0.1.1+cvs20061208+3) kiba-dock dont work ](*,) the error is:

** Message: error while creating launcher icon: msn
Fallo de segmentación (core dumped)

help please :-k

---

### Post by marijus on 2007-01-06
> **Shadito said:**
> Hi, the .deb works, but today in one update (0.1.1+cvs20061208+3) kiba-dock dont work ](*,) the error is:

** Message: error while creating launcher icon: msn
Fallo de segmentación (core dumped)

help please :-k

yep... same for me...

---

### Post by CCBalla10 on 2007-01-06
me too

---

### Post by OHardBodyO on 2007-01-07
Deb was working for me until i configured it to bounce on my over.  After that it would place everything on the top-left-corner and all the launchers are bunched together.  I set all the settings back to default but that didn't work.  I deleted the .kiba-dock folder and uninstall and reinstalled it and now im getting the following message

(kiba-dock:7806): Gdk-CRITICAL **: gdk_screen_get_monitor_geometry: assertion `monitor_num < GDK_SCREEN_X11 (screen)->num_monitors' failed

Kiba works fine if I run it as another use.  Can someone help?

---

### Post by alin4lex on 2007-01-08
alin@Home-wks:~$ cd kiba-dock
alin@Home-wks:~/kiba-dock$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.in:30: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1
alin@Home-wks:~/kiba-dock$

---

### Post by ESPOiG on 2007-01-09
i just keep getting this when i try and launch it :(

> user@ubuntu-linuxbox-2:~$ kiba-dock

(kiba-dock:23408): GLib-CRITICAL **: g_str_has_suffix: assertion `str != NULL' failed
Segmentation fault (core dumped)

what does this mean, and also i did all that was said but when i goto 'make' there is no make file, so i just used the .deb provided

---

### Post by Weav on 2007-01-09
I also get a strange error after installing kiba-dock from the deb provided:

```

steve@steve-desktop:~$ kiba-dock
kiba-dock: symbol lookup error: kiba-dock: undefined symbol: g_type_register_static_simple

```

Any ideas?

---

### Post by fokuslee on 2007-01-09
alin@Home-wks:~$ cd kiba-dock
alin@Home-wks:~/kiba-dock$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.in:30: error: possibly undefined macro: AC_PROG_LIBTOOL
If this token and others are legitimate, please use m4_pattern_allow.
See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1
alin@Home-wks:~/kiba-dock$

same error as 4lex 
the prebuilt 64deb installs but won't run 
any ideas?

---

### Post by maniacmusician on 2007-01-09
how do I get this dock to be a little more subtle? Because of its insane physics, the crazy thing bounces all around and won't even line up in a straight line; instead icons clog up and sit on top of each other; they're useless like that. So how can I get to be more subtle?

Also, can I control spacing between the icons? again due to the physics, they sometimes end up too close to each other.

Thanks.

---

### Post by PriceChild on 2007-01-09
> **maniacmusician said:**
> how do I get this dock to be a little more subtle? Because of its insane physics, the crazy thing bounces all around and won't even line up in a straight line; instead icons clog up and sit on top of each other; they're useless like that. So how can I get to be more subtle?

Also, can I control spacing between the icons? again due to the physics, they sometimes end up too close to each other.

Thanks.Right click it and change the model type from rope to something else. say spring.

Everything can be customised on the right click menu if you find "gset-kiba"

---

### Post by glotz on 2007-01-09
Now, all we need is a wiki page. :)

Any cool docks that don't need XGL/AIXGL?

---

### Post by maniacmusician on 2007-01-09
> **PriceChild said:**
> Right click it and change the model type from rope to something else. say spring.

Everything can be customised on the right click menu if you find "gset-kiba"
I know, I've tried, I just can't get the damn thing to stay still! And I didn't see any spacing options in gset.

---

### Post by biketrials on 2007-01-11
When I install kiba I'm having a problem that when the launcher is stared I can't open the system tray icon/tool. It says that the image required can't be found. Here is the error being thrown out. It would be much appreciated if anyone has any suggestions. Thanks

```
Failed to open file '/usr/bin/icons/kiba_24.png': No such file or directory
```

---

### Post by jonah1980 on 2007-01-11
[http://www.gnome-dock.org/trac](http://www.gnome-dock.org/trac)

this dock looks awesome, plus it's got the sytem tray also so no need to have anything but the dock on your desktop....

---

### Post by PriceChild on 2007-01-11
/me can't get cairo-dock working properly... Its not looking in the right home dir at present :(

---

### Post by cnphch on 2007-01-11
This install doesn't work for. Everything is fine until i type ./autogen.sh

Then i get this error message:

cnphch@cnphch-laptop:~/kiba-dock$ ./autogen.sh 
autoreconf: Entering directory `.' autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
plugins/Makefile.am:26: Libtool library used but `LIBTOOL' is undefined
plugins/Makefile.am:26:
plugins/Makefile.am:26: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/Makefile.am:26: to `configure.in' and run `aclocal' and `autoconf' again.
autoreconf: automake failed with exit status: 1
cnphch@cnphch-laptop:~/kiba-dock$

Can anyone help?

I using Dapper with Beryl

---

### Post by frotzed on 2007-01-11
I'm using edgy 6.10

when I run this line in terminal:

 cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock

I get this error:

bash: cvs: command not found


I don't know what to do about it.

---

### Post by umattu on 2007-01-11
========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
I have followed the first post to a "T" and this is all I get what have I done wrong?

---

### Post by CowzRule on 2007-01-12
> **frotzed said:**
> I'm using edgy 6.10

when I run this line in terminal:

 cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock

I get this error:

bash: cvs: command not found


I don't know what to do about it.I think you need to install "cvs" Try ```
sudo aptitude install cvs
```

---

### Post by d3v1ant_0n3 on 2007-01-12
*EDIT* never mind, misread.

---

### Post by rfdparker2002 on 2007-01-12
Mine fails at the './autogen.sh' stage, outputting:
```
checking for KIBA_DOCK... configure: error: Package requirements ("libpng                                                       xcomposite    glib-2.0                                                         gtk+-2.0                                                        cairo         pango                                                    gconf-2.0                                                       libgtop-2.0           libglade-2.0") were not met:

No package 'xcomposite' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables KIBA_DOCK_CFLAGS
and KIBA_DOCK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
I have installed xcompmgr and even prior beryl works fine with kde using either xgl or now i use the built in support of the beta nvidia drivers, yet i still get this error?

---

### Post by ZaYeR on 2007-01-12
> **cnphch said:**
> This install doesn't work for. Everything is fine until i type ./autogen.sh

Then i get this error message:

cnphch@cnphch-laptop:~/kiba-dock$ ./autogen.sh 
autoreconf: Entering directory `.' autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
plugins/Makefile.am:26: Libtool library used but `LIBTOOL' is unde```

```fined
plugins/Makefile.am:26:
plugins/Makefile.am:26: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/Makefile.am:26: to `configure.in' and run `aclocal' and `autoconf' again.
autoreconf: automake failed with exit status: 1
cnphch@cnphch-laptop:~/kiba-dock$

Can anyone help?

I using Dapper with Beryl

You need to install libtool:

```
sudo apt-get install libtool
```

---

### Post by XtremeSki2001 on 2007-01-12
> **rfdparker2002 said:**
> Mine fails at the './autogen.sh' stage, outputting:
```
checking for KIBA_DOCK... configure: error: Package requirements ("libpng                                                       xcomposite    glib-2.0                                                         gtk+-2.0                                                        cairo         pango                                                    gconf-2.0                                                       libgtop-2.0           libglade-2.0") were not met:

No package 'xcomposite' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables KIBA_DOCK_CFLAGS
and KIBA_DOCK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
I have installed xcompmgr and even prior beryl works fine with kde using either xgl or now i use the built in support of the beta nvidia drivers, yet i still get this error?

I'm getting the same error

---

### Post by unabatedshagie on 2007-01-13
Make that another one thats getting that error.

```
checking pkg-config is at least version 0.9.0... yes
checking for KIBA_DOCK... configure: error: Package requirements ("libpng xcomposite glib-2.0 gtk+-2.0 cairo pango gconf-2.0 libgtop-2.0 libglade-2.0") were not met:

No package 'xcomposite' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables KIBA_DOCK_CFLAGS
and KIBA_DOCK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by the.ant on 2007-01-13
I have a similar problem as some other posters, has anyone found a solution yet?

```

formica:~/kiba-dock$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal
autoreconf: configure.in: tracing
autoreconf: configure.in: creating directory config
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.in:30: error: possibly undefined macro: AC_PROG_LIBTOOL
     If this token and others are legitimate, please use m4_pattern_allow.
     See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1

```

EDIT: OK, installing libtool solved this, however, now I also have to problem "xcomposite not found".

---

### Post by XtremeSki2001 on 2007-01-13
I did some searching and I've found the 

```
No package 'xcomposite' found
```

error is due to me not having compiz installed.  I wanted to use Beryl with Kiba-Dock ... is that possible?

edit:  Ignore the above .. I've used [this guide ]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit") to install XGL (I have a NVIDIA card) and Compiz.  After I finish this guide, I beleive I'll be able to install Kiba-Dock

---

### Post by XtremeSki2001 on 2007-01-13
edit

---

### Post by the.ant on 2007-01-13
> **XtremeSki2001 said:**
> I did some searching and I've found the 

```
No package 'xcomposite' found
```

error is due to me not having compiz installed.  I wanted to use Beryl with Kiba-Dock ... is that possible?

edit:  Ignore the above .. I've used [this guide ]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit") to install XGL (I have a NVIDIA card) and Compiz.  After I finish this guide, I beleive I'll be able to install Kiba-Dock

Any  other solution? I tried to install compiz and did not get it running, which is the reason why I take beryl in the first place. I don't want to install to many things which I don't need, especially with things which are in constant development. 

Also, I thought that kiba was originally written for beryl. It is after all included in the beryl repositories, not in in the compiz... Or did I get that wrong?

edit: problem solved by reinstallin libxcomposite. No need to install compiz!

kiba is running now, although I have this weird blue fframe effect as well.

---

### Post by XtremeSki2001 on 2007-01-13
edit

---

### Post by XtremeSki2001 on 2007-01-13
I fixed the error I was receiving by installing all packages under libxcomposite in synaptic.

Now I'm getting this problem after the install goes fine ...

```
*** Warning: The package version "dock" does not
*** Warning: contain any digits. dpkg might not like that.

This package will be built according to these values:

0 -  Maintainer: [ root@erich-desktop ]
1 -  Summary: [ EOF ]
2 -  Name:    [ kiba-dock ]
3 -  Version: [ dock ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ kiba-dock ]
9 -  Alternate source location: [  ]

Enter a number to change any of them or press ENTER to continue:

*****************************************
**** Debian package creation selected ***
*****************************************

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]: 

erich@erich-desktop:~/kiba-dock$ cd
erich@erich-desktop:~$ kiba-dock
Segmentation fault
erich@erich-desktop:~$
```

edit:  Fixed the error.  Check page one.  Version needs to be changed from 3 to 1 .... still getting segmentation fault (RAM is fine and not the problem)

---

### Post by ajmorris on 2007-01-13
i get this when i try to run it:

kiba-dock
GTK Accessibility Module initialized
Segmentation fault (core dumped)

 Any ideas?

---

### Post by FuturePilot on 2007-01-14
Should I continue with this? Warning at the bottom.
```
sudo aptitude install cvs automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev checkinstall libglade2-dev libgtop2-dev
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Note: selecting "libglitz-glx1-dev" instead of the
      virtual package "libglitz-glx-dev"
The following NEW packages will be automatically installed:
  autoconf autotools-dev binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc
  gcc-4.0 libart-2.0-dev libatk1.0-dev libbz2-dev libc6-dev libcairo2-dev
  libcroco3-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libgl1-mesa-dev libglib2.0-dev libglitz1-dev libgsf-1-dev libidl-dev
  libmudflap0 libmudflap0-dev liborbit2-dev libpng12-dev libpopt-dev
  libstdc++6-4.0-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev
  libxml2-dev libxrandr-dev libxrender-dev linux-kernel-headers m4 make
  mesa-common-dev orbit2 x-dev x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev zlib1g-dev
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev binutils build-essential checkinstall
  cpp cpp-4.0 cvs dpkg-dev g++ g++-4.0 gcc gcc-4.0 libart-2.0-dev
  libatk1.0-dev libbz2-dev libc6-dev libcairo2-dev libcroco3-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgconf2-dev
  libgl1-mesa-dev libglade2-dev libglib2.0-dev libglitz-glx1-dev
  libglitz1-dev libgsf-1-dev libgtk2.0-dev libgtop2-dev libidl-dev
  libmudflap0 libmudflap0-dev liborbit2-dev libpango1.0-dev libpng12-dev
  libpopt-dev librsvg2-dev libstdc++6-4.0-dev libx11-dev libxau-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev
  libxi-dev libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev
  linux-kernel-headers m4 make mesa-common-dev orbit2 x-dev
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev zlib1g-dev
0 packages upgraded, 68 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.8MB of archives. After unpacking 93.5MB will be used.
Do you want to continue? [Y/n/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  mesa-common-dev x11proto-fixes-dev libglitz-glx1-dev libglitz1-dev
  libgl1-mesa-dev libxfixes-dev

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": No
Abort.

```

---

### Post by anticasper on 2007-01-14
> **the.ant said:**
> 

edit: problem solved by reinstallin libxcomposite. No need to install compiz!

kiba is running now, although I have this weird blue fframe effect as well.

how do you reinstall libxcomposite?

---

### Post by PriceChild on 2007-01-14
> **FuturePilot said:**
> Should I continue with this? Warning at the bottom.I say no... you should figure out what **dodgy** repos you've got which are trying to give you those packages.

---

### Post by FuturePilot on 2007-01-14
> **PriceChild said:**
> I say no... you should figure out what **dodgy** repos you've got which are trying to give you those packages.
How exactly would I go about doing that? Could it be a third party repo?

---

### Post by rabid9797 on 2007-01-14
do i need to be running compiz or beryl to use kiba-dock?

i keep getting this error when trying to "./autogen.sh"

```

checking for KIBA_DOCK... configure: error: Package requirements ("libpng      xcomposite                                                       glib-2.0       gtk+-2.0                                                         cairo          pango                                                    gconf-2.0              libgtop-2.0                                                      libglade-2.0") were not met:

No package 'xcomposite' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables KIBA_DOCK_CFLAGS
and KIBA_DOCK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by rabid9797 on 2007-01-14
bump

---

### Post by nlmark on 2007-01-14
try installing libxcomposite-dev

for the person who started this thread: libtool is also required

---

### Post by rabid9797 on 2007-01-14
> **nlmark said:**
> try installing libxcomposite-dev

for the person who started this thread: libtool is also required

thanks, that did it for me:D 

btw, someone already said that libtool is required, i think we just need to wait for the original poster to edit his post.

EDIT: i was able to execute autogen successfully but now im having a problem during make.

```

launcher.c: In function 'kiba_plugin_init':
launcher.c:112: error: 'laucher' undeclared (first use in this function)
launcher.c:112: error: (Each undeclared identifier is reported only once
launcher.c:112: error: for each function it appears in.)
make[2]: *** [launcher.lo] Error 1
make[2]: Leaving directory `/home/rabid9797/kiba-dock/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rabid9797/kiba-dock'
make: *** [all] Error 2

```

---

### Post by FuturePilot on 2007-01-14
Ok, I think I got rid of the warning, but now there are packages that are broken.
 libgl1-mesa-dev libglitz-glx1-dev libglitz1-dev libxfixes-dev

---

### Post by rabid9797 on 2007-01-15
bump

---

### Post by ZaYeR on 2007-01-15
> **rabid9797 said:**
> 
```

launcher.c: In function 'kiba_plugin_init':
launcher.c:112: error: 'laucher' undeclared (first use in this function)
launcher.c:112: error: (Each undeclared identifier is reported only once
launcher.c:112: error: for each function it appears in.)
make[2]: *** [launcher.lo] Error 1
make[2]: Leaving directory `/home/rabid9797/kiba-dock/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rabid9797/kiba-dock'
make: *** [all] Error 2

```

I thing that this error is quite common ... try to search answer on this page: [http://forum.beryl-project.org/viewforum.php?f=38]("http://forum.beryl-project.org/viewforum.php?f=38")
There's a lot of that ;). We must wait until kiba site will be lauched. Oh, and one more thing ... sometimes cvs are broken cuz danielb is developing kiba all the time and not everything is going like he wants.

---

### Post by rabid9797 on 2007-01-15
huzzah! its complete! i removed the entire cvs folder and started fresh, the developer must of fixed something since when i downloaded it.

attached is a working .deb of kiba-dock. (sry it says 1-1 for version, i just put whatever, i just wanted to get it done)

---

### Post by daverab on 2007-01-17
I dunno about it 'working' fully. The systray icon seems to be broken, at least for me. It complained about it not finding kiba_24.png, so I copied it manually. After that, the kiba-systray.py is trying to launch the kiba dock from /usr/bin/ and can't find it and just sorta fails. Besides that, the new taskbar item is nice. I just wish you could adjust which side of the tray the icons appear in.

---

### Post by atraylen on 2007-01-17
OMG it worked :-) thats the first time I have ever made a package... tho by tutorial,  sweet... I just upgraded to edgy eft yesterday... got beryl running quite nicely and now the kiba dock is working Thanks a million for the awesome tutorial *cheers*

---

### Post by corck on 2007-01-20
I get these errors.

```

(kiba-dock:21791): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(kiba-dock:21791): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(kiba-dock:21791): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `pixbuf != NULL' failed

(kiba-dock:21791): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(kiba-dock:21791): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed
Segmentation fault

```

someone knows how to solve it

by the way I am using kubuntu

---

### Post by corck on 2007-01-20
solved issue by using  the version from
[http://www.dpb.org.uk/ubuntu/edgy_6.10/](http://www.dpb.org.uk/ubuntu/edgy_6.10/)

pretty cool stuff

---

### Post by stijngysemans on 2007-01-20
I've got a problem with launching the kiba dock (after following the how to described on page 1)

```

xxx@xxxxx:~/kiba-dock$ kiba-dock
*** glibc detected *** kiba-dock: double free or corruption (fasttop): 0x080b47f0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75f88bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb75f8a44]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb770bb51]
kiba-dock(kiba_load_png+0x261)[0x8058581]
/usr/local/lib/kiba-dock/libclock.so(kiba_plugin_init+0x421)[0xb7308641]
kiba-dock(main+0xbbe)[0x804f6ce]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75a78cc]
kiba-dock[0x804db31]
======= Memory map: ========
08048000-0805d000 r-xp 00000000 03:01 3347667    /usr/local/bin/kiba-dock
0805d000-0805e000 rw-p 00015000 03:01 3347667    /usr/local/bin/kiba-dock
0805e000-080c0000 rw-p 0805e000 00:00 0          [heap]
b7100000-b7121000 rw-p b7100000 00:00 0 
b7121000-b7200000 ---p b7121000 00:00 0 
b72a1000-b72ab000 r-xp 00000000 03:01 81987      /lib/libgcc_s.so.1
b72ab000-b72ac000 rw-p 00009000 03:01 81987      /lib/libgcc_s.so.1
b72ac000-b72ae000 r-xp 00000000 03:01 3178622    /usr/lib/libXcomposite.so.1.0.0
b72ae000-b72af000 rw-p 00001000 03:01 3178622    /usr/lib/libXcomposite.so.1.0.0
b72bb000-b72cd000 r-xp 00000000 03:01 3227997    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b72cd000-b72ce000 rw-p 00011000 03:01 3227997    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b72ce000-b72d7000 r-xp 00000000 03:01 114703     /lib/tls/i686/cmov/libnss_files-2.4.so
b72d7000-b72d9000 rw-p 00008000 03:01 114703     /lib/tls/i686/cmov/libnss_files-2.4.so
b72d9000-b72e1000 r-xp 00000000 03:01 114705     /lib/tls/i686/cmov/libnss_nis-2.4.so
b72e1000-b72e3000 rw-p 00007000 03:01 114705     /lib/tls/i686/cmov/libnss_nis-2.4.so
b72e3000-b72f5000 r-xp 00000000 03:01 114700     /lib/tls/i686/cmov/libnsl-2.4.so
b72f5000-b72f7000 rw-p 00011000 03:01 114700     /lib/tls/i686/cmov/libnsl-2.4.so
b72f7000-b72f9000 rw-p b72f7000 00:00 0 
b72f9000-b7300000 r-xp 00000000 03:01 114701     /lib/tls/i686/cmov/libnss_compat-2.4.so
b7300000-b7302000 rw-p 00006000 03:01 114701     /lib/tls/i686/cmov/libnss_compat-2.4.so
b7305000-b730a000 r-xp 00000000 03:01 3431098    /usr/local/lib/kiba-dock/libclock.so
b730a000-b730b000 rw-p 00004000 03:01 3431098    /usr/local/lib/kiba-dock/libclock.so
b730b000-b730c000 r-xp 00000000 03:01 3195981    /usr/lib/gconv/ISO8859-1.so
b730c000-b730e000 rw-p 00001000 03:01 3195981    /usr/lib/gconv/ISO8859-1.so
b730e000-b730f000 r-xp 00000000 03:01 3211406    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b730f000-b7310000 rw-p 00000000 03:01 3211406    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b7310000-b7343000 r--p 00000000 03:01 3229218    /usr/lib/locale/en_US.utf8/LC_CTYPE
b7343000-b7344000 r--p 00000000 03:01 3229223    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7344000-b7345000 r--p 00000000 03:01 3229226    /usr/lib/locale/en_US.utf8/LC_TIME
b7345000-b741c000 r--p 00000000 03:01 3229217    /usr/lib/locale/en_US.utf8/LC_COLLATE
b741c000-b741d000 r--p 00000000 03:01 3229221    /usr/lib/locale/en_US.utf8/LC_MONETARY
b741d000-b741e000 r--p 00000000 03:01 3244122    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b741e000-b741f000 r--p 00000000 03:01 3229224    /usr/lib/locale/en_US.utf8/LC_PAPER
b741f000-b7421000 rw-p b741f000 00:00 0 
b7421000-b7430000 r-xp 00000000 03:01 81961      /lib/libbz2.so.1.0.3
b7430000-b7431000 rw-p 0000f000 03:01 81961      /lib/libbz2.so.1.0.3
b7431000-b7432000 rw-p b7431000 00:00 0 
b7432000-b7436000 r-xp 00000000 03:01 3179759    /usr/lib/libXdmcp.so.6.0.0
b7436000-b7437000 rw-p 00003000 03:01 3179759    /usr/lib/libXdmcp.so.6.0.0
b7437000-b7439000 r-xp 00000000 03:01 3179750    /usr/lib/libXau.so.6.0.0
b7439000-b743a000 rw-p 00001000 03:01 3179750    /usr/lib/libXau.so.6.0.0
b743a000-b7456000 r-xp 00000000 03:01 3179944    /usr/lib/libexpat.so.1.0.0
b7456000-b7458000 rw-p 0001c000 03:01 3179944    /usr/lib/libexpat.so.1.0.0
b7458000-b7459000 rw-p b7458000 00:00 0 
b7459000-b746c000 r-xp 00000000 03:01 3180490    /usr/lib/libz.so.1.2.3
b746c000-b746d000 rw-p 00012000 03:01 3180490    /usr/lib/libz.so.1.2.3
b746d000-b74d4000 r-xp 00000000 03:01 3179960    /usr/lib/libfreetype.so.6.3.10
b74d4000-b74d7000 rw-p 00067000 03:01 3179960    /usr/lib/libfreetype.so.6.3.10
b74d7000-b74fa000 r-xp 00000000 03:01 3179883    /usr/lib/libpng12.so.0.1.2.8
b74fa000-b74fb000 rw-p 00023000 03:01 3179883    /usr/lib/libpng12.so.0.1.2.8
b74fb000-b7525000 r-xp 00000000 03:01 3180335    /usr/lib/libpangoft2-1.0.so.0.1400.5
b7525000-b7526000 rw-p 00029000 03:01 3180335    /usr/lib/libpangoft2-1.0.so.0.1400.5
b7526000-b7556000 r-xp 00000000 03:01 3179871    /usr/lib/libcroco-0.6.so.3.0.1
b7556000-b7559000 rw-p 0002f000 03:01 3179871    /usr/lib/libcroco-0.6.so.3.0.1
b7559000-b7584000 r-xp 00000000 03:01 3178953    /usr/lib/libgsf-1.so.114.0.1
b7584000-b7587000 rw-p 0002a000 03:01 3178953    /usr/lib/libgsf-1.so.114.0.1
b7587000-b7589000 rw-p b7587000 00:00 0 
b7589000-b7590000 r-xp 00000000 03:01 114710     /lib/tls/i686/cmov/librt-2.4.so
b7590000-b7592000 rw-p 00006000 03:01 114710     /lib/tls/i686/cmov/librt-2.4.so
b7592000-b76bf000 r-xp 00000000 03:01 114694     /lib/tls/i686/cmov/libc-2.4.so
b76bf000-b76c1000 r--p 0012c000 03:01 114694     /lib/tls/i686/cmov/libc-2.4.so
b76c1000-b76c3000 rw-p 0012e000 03:01 114694     /lib/tls/i686/cmov/libc-2.4.so
b76c3000-b76c6000 rw-p b76c3000 00:00 0 
b76c6000-b76d5000 r-xp 00000000 03:01 114708     /lib/tls/i686/cmov/libpthread-2.4.so
b76d5000-b76d7000 rw-p 0000f000 03:01 114708     /lib/tls/i686/cmov/libpthread-2.4.so
b76d7000-b76d9000 rw-p b76d7000 00:00 0 
b76d9000-b776a000 r-xp 00000000 03:01 3180051    /usr/lib/libglib-2.0.so.0.1200.4
b776a000-b776b000 rw-p 00091000 03:01 3180051    /usr/lib/libglib-2.0.so.0.1200.4
b776b000-b777a000 r-xp 00000000 03:01 3178955    /usr/lib/libgtop-2.0.so.7.0.0
b777a000-b777b000 rw-p 0000f000 03:01 3178955    /usr/lib/libgtop-2.0.so.7.0.0
b777b000-b777c000 rw-p b777b000 00:00 0 
b777c000-b777e000 r-xp 00000000 03:01 114697     /lib/tls/i686/cmov/libdl-2.4.so
b777e000-b7780000 rw-p 00001000 03:01 114697     /lib/tls/i686/cmov/libdl-2.4.so
b7780000-b7783000 r-xp 00000000 03:01 3180063    /usr/lib/libgmodule-2.0.so.0.1200.4
b7783000-b7784000 rw-p 00002000 03:01 3180063    /usr/lib/libgmodule-2.0.so.0.1200.4
b7784000-b77bd000 r-xp 00000000 03:01 3180103    /usr/lib/libgobject-2.0.so.0.1200.4
b77bd000-b77be000 rw-p 00038000 03:01 3180103    /usr/lib/libgobject-2.0.so.0.1200.4
b77be000-b7884000 r-xp 00000000 03:01 3179744    /usr/lib/libX11.so.6.2.0
b7884000-b7887000 rw-p 000c5000 03:01 3179744    /usr/lib/libX11.so.6.2.0
b7887000-b78e7000 r-xp 00000000 03:01 3179855    /usr/lib/libcairo.so.2.9.2
b78e7000-b78e9000 rw-p 0005f000 03:01 3179855    /usr/lib/libcairo.so.2.9.2
b78e9000-b7921000 r-xp 00000000 03:01 3180331    /usr/lib/libpango-1.0.so.0.1400.5
b7921000-b7923000 rw-p 00037000 03:01 3180331    /usr/lib/libpango-1.0.so.0.1400.5
b7923000-b7924000 rw-p b7923000 00:00 0 
b7924000-b7928000 r-xp 00000000 03:01 3179765    /usr/lib/libXfixes.so.3.1.0
b7928000-b7929000 rw-p 00003000 03:01 3179765    /usr/lib/libXfixes.so.3.1.0
b7929000-b7931000 r-xp 00000000 03:01 3179755    /usr/lib/libXcursor.so.1.0.2
b7931000-b7932000 rw-p 00007000 03:01 3179755    /usr/lib/libXcursor.so.1.0.2
b7932000-b7934000 r-xp 00000000 03:01 3179783    /usr/lib/libXrandr.so.2.0.0
b7934000-b7935000 rw-p 00002000 03:01 3179783    /usr/lib/libXrandr.so.2.0.0
b7935000-b793c000 r-xp 00000000 03:01 3179771    /usr/lib/libXi.so.6.0.0
b793c000-b793d000 rw-p 00006000 03:01 3179771    /usr/lib/libXi.so.6.0.0
b793d000-b793f000 r-xp 00000000 03:01 3179773    /usr/lib/libXinerama.so.1.0.0
b793f000-b7940000 rw-p 00001000 03:01 3179773    /usr/lib/libXinerama.so.1.0.0
b7940000-b7947000 r-xp 00000000 03:01 3179785    /usr/lib/libXrender.so.1.3.0
b7947000-b7948000 rw-p 00006000 03:01 3179785    /usr/lib/libXrender.so.1.3.0
b7948000-b7949000 rw-p b7948000 00:00 0 
b7949000-b7955000 r-xp 00000000 03:01 3179763    /usr/lib/libXext.so.6.4.0
b7955000-b7956000 rw-p 0000c000 03:01 3179763    /usr/lib/libXext.so.6.4.0
b7956000-b797f000 r-xp 00000000 03:01 3179950    /usr/lib/libfontconfig.so.1.0.4
b797f000-b7984000 rw-p 00028000 03:01 3179950    /usr/lib/libfontconfig.so.1.0.4
b7984000-b7985000 rw-p b7984000 00:00 0 
b7985000-b798c000 r-xp 00000000 03:01 3180333    /usr/lib/libpangocairo-1.0.so.0.1400.5
b798c000-b798d000 rw-p 00006000 03:01 3180333    /usr/lib/libpangocairo-1.0.so.0.1400.5
b798d000-b79b1000 r-xp 00000000 03:01 114698     /lib/tls/i686/cmov/libm-2.4.so
b79b1000-b79b3000 rw-p 00023000 03:01 114698     /lib/tls/i686/cmov/libm-2.4.so
b79b3000-b79c8000 r-xp 00000000 03:01 3178844    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b79c8000-b79c9000 rw-p 00015000 03:01 3178844    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b79c9000-b79e1000 r-xp 00000000 03:01 3179822    /usr/lib/libatk-1.0.so.0.1213.0
b79e1000-b79e3000 rw-p 00017000 03:01 3179822    /usr/lib/libatk-1.0.so.0.1213.0
b79e3000-b79e4000 rw-p b79e3000 00:00 0 
b79e4000-b7a65000 r-xp 00000000 03:01 3179004    /usr/lib/libgdk-x11-2.0.so.0.1000.6
b7a65000-b7a68000 rw-p 00081000 03:01 3179004    /usr/lib/libgdk-x11-2.0.so.0.1000.6
b7a68000-b7b7b000 r-xp 00000000 03:01 3180478    /usr/lib/libxml2.so.2.6.26
b7b7b000-b7b80000 rw-p 00113000 03:01 3180478    /usr/lib/libxml2.so.2.6.26
b7b80000-b7b81000 rw-p b7b80000 00:00 0 
b7b81000-b7eca000 r-xp 00000000 03:01 3179005    /usr/lib/libgtk-x11-2.0.so.0.1000.6
b7eca000-b7ed0000 rw-p 00349000 03:01 3179005    /usr/lib/libgtk-x11-2.0.so.0.1000.6
b7ed0000-b7ed1000 rw-p b7ed0000 00:00 0 
b7ed1000-b7ee8000 r-xp 00000000 03:01 3180047    /usr/lib/libglade-2.0.so.0.0.7
b7ee8000-b7ee9000 rw-p 00016000 03:01 3180047    /usr/lib/libglade-2.0.so.0.0.7
b7ee9000-b7f0d000 r-xp 00000000 03:01 3181016    /usr/lib/libglitz.so.1.0.0
b7f0d000-b7f0e000 rw-p 00024000 03:01 3181016    /usr/lib/libglitz.so.1.0.0
b7f0e000-b7f3d000 r-xp 00000000 03:01 3180383    /usr/lib/librsvg-2.so.2.16.0
b7f3d000-b7f3e000 rw-p 0002f000 03:01 3180383    /usr/lib/librsvg-2.so.2.16.0
b7f3e000-b7f42000 r-xp 00000000 03:01 3180155    /usr/lib/libgthread-2.0.so.0.1200.4
b7f42000-b7f43000 rw-p 00003000 03:01 3180155    /usr/lib/libgthread-2.0.so.0.1200.4
b7f43000-b7f44000 rw-p b7f43000 00:00 0 
b7f44000-b7f8b000 r-xp 00000000 03:01 3179732    /usr/lib/libORBit-2.so.0.1.0
b7f8b000-b7f95000 rw-p 00046000 03:01 3179732    /usr/lib/libORBit-2.so.0.1.0
b7f95000-b7fc3000 r-xp 00000000 03:01 3179985    /usr/lib/libgconf-2.so.4.1.0
b7fc3000-b7fc6000 rw-p 0002e000 03:01 3179985    /usr/lib/libgconf-2.so.4.1.0
b7fc6000-b7fc7000 r--p 00000000 03:01 3229222    /usr/lib/locale/en_US.utf8/LC_NAME
b7fc7000-b7fc8000 r--p 00000000 03:01 3229216    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fc8000-b7fc9000 r--p 00000000 03:01 3229225    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fc9000-b7fca000 r--p 00000000 03:01 3229220    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fca000-b7fd1000 r--s 00000000 03:01 3196039    /usr/lib/gconv/gconv-modules.cache
b7fd1000-b7fd2000 r--p 00000000 03:01 3229219    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fd2000-b7fd4000 rw-p b7fd2000 00:00 0 
b7fd4000-b7fed000 r-xp 00000000 03:01 82138      /lib/ld-2.4.so
b7fed000-b7fef000 rw-p 00018000 03:01 82138      /lib/ld-2.4.so
bfc2c000-bfc42000 rw-p bfc2c000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)


```

---

### Post by bandoba on 2007-01-20
> **corck said:**
> solved issue by using  the version from
[http://www.dpb.org.uk/ubuntu/edgy_6.10/](http://www.dpb.org.uk/ubuntu/edgy_6.10/)

pretty cool stuff

I am having same problem. But I don't see package for i386. Does anybody know how I can resolved this problem or where can I get working package. I tried package from rabid9797 posted in few posts above but it has same issue.

---

### Post by inzpektor on 2007-01-21
Hi.  I've been looking for a dock-app like kiba-dock since hoary (a long time).  Great, I found it in the internet-jungle at last.  I've downloaded and installed the debian-package that rabid9797 posted (#141).

However, if I launch kiba-dock without parameters, the icons appear in black&white, and then they start swirling around like sprite-shows in old C=64 demos.  They continue to do that until I kill the app.

If I launch the app with --enable-tray, I get a segmentation-fault.

I'm running Beryl, and help is greatly appreciated :-)

---

### Post by timbounceback on 2007-01-25
Attached is kiba-dock (w/ the latest cvs at the time of writing for i386, for anyone who doesn't feel like building it from source:D .

---

### Post by Efrain Valles on 2007-01-26
How did you go around the 
 kiba-dock: symbol lookup error: kiba-dock: undefined symbol: g_type_register_static_simple

I'm stuck there

---

### Post by Kateikyoushi on 2007-01-27
I gave it a try but no go.

```
(kiba-dock:20780): GLib-CRITICAL **: g_str_has_suffix: assertion `str != NULL' failed

```

Will check again a later version.

---

### Post by bvanaerde on 2007-01-27
Everything seems to be working quite fine...
I just followed the guide in the first post. Had to change the version (as it was not a number), but apart from that, it works really great.

When changing the model (rope, wobbly, spring for all), it crashes, but the changes are saved.
So when I restart the program, it has the selected model.

---

### Post by joel_gil on 2007-01-27
hi everyone

i installed all packages and everything correctly

but when i run "kiba-dock" in only opens the folder where it got installed...

so then i tryed to run specifyin the file (which btw installed on my personal folder) /home/me/kiba-dock/dock/kiba-dock

and nothin happened -___-

any ideas what might be happenin?

hope someone can help me 

thanks in advance

---

### Post by birujiano on 2007-01-27
***[COLOR="Sienna"]I have the same problem, please help [/COLOR][!](http://www.girlsbcn.net)[!](http://www.girlsbcn.es)[!](http://www.girlsbcn.com.es)***

---

### Post by thedrifterthor on 2007-01-28
Hey, it works perfectly for me, except that when I close the terminal that was open to start it, kiba dock closes as well. Any ideas?

---

### Post by joel_gil on 2007-01-28
pleeeeease heeelp, ive been lookin around different forums for this but no one has an answers, can somebody help please?

p.d. my problem is a few quotes above

---

### Post by kwaanens on 2007-01-29
> **thedrifterthor said:**
> Hey, it works perfectly for me, except that when I close the terminal that was open to start it, kiba dock closes as well. Any ideas?

That's how terminal started apps are supposed to work. Try alt+f2 and start it.

- Ketil

---

### Post by ujmyhn on 2007-01-30
Ok, I have no idea what all those commands were, but I had to do make-install (per README file) after all those.  Also, it looked like garbage:

[http://img262.imageshack.us/img262/9865/kibadockgarbagetq4.jpg](http://img262.imageshack.us/img262/9865/kibadockgarbagetq4.jpg)

...but that's probably because I don't know what I'm doing.

---

### Post by bvanaerde on 2007-01-30
> **ujmyhn said:**
> Ok, I have no idea what all those commands were, but I had to do make-install (per README file) after all those.  Also, it looked like garbage:

[http://img262.imageshack.us/img262/9865/kibadockgarbagetq4.jpg](http://img262.imageshack.us/img262/9865/kibadockgarbagetq4.jpg)

...but that's probably because I don't know what I'm doing.

It doesn't look nice when you don't have Beryl installed ;)

---

### Post by ockie on 2007-01-31
Hi Guys, anybody had problem with starting kiba-dock comand like mine below?

*symbol lookup error: /usr/local/lib/kiba-dock/libtaskbar.so: undefined symbol: gdk_screen_get_window_stack*

Any ideas for the solution? 

Thanks A lot before

---

### Post by fiveryanfrenzy on 2007-02-01
command "kiba-dock" not found... ???

---

### Post by hamster_billy on 2007-02-01
That's what I got too.

---

### Post by hamster_billy on 2007-02-01
sudo make install
then it works.

---

### Post by zetsumei on 2007-02-06
i get an error when trying to sudo checkinstall, it says

Building Debian package... FAILED!

*** Failed to build the package

---

### Post by PenguinLuva on 2007-02-07
> **hamster_billy said:**
> sudo make install
then it works.

Your method doesn't work for me. I type in "kiba-dock" and the command isn't found. I use sudo make install and bash says there is no rule to make install. Help please! I've installed kiba-dock but don't know how to run it!

---

### Post by Choad on 2007-02-07
this thing is hillarious!!!!

---

### Post by Ptero-4 on 2007-02-17
Two questions. I don`t have compiz/xgl (can`t make it work) and I`m using xfwm4 as compositing manager, Does kiba-dock work if I use xfwm4 instead of xcompmgr? And Is there any taskbar module? If there is, can it be disabled, how?

---

### Post by BOBSONATOR on 2007-02-20
Hey guys, when you are successful, please post your settings here [http://ubuntuforums.org/showthread.php?t=365718](http://ubuntuforums.org/showthread.php?t=365718)

DankE!

---

### Post by NOSintake on 2007-02-20
> **zetsumei said:**
> i get an error when trying to sudo checkinstall, it says

Building Debian package... FAILED!

*** Failed to build the package

same here, when i check it, i get this:
dpkg-deb - error: (upstream) version (`dock') doesn't contain any digits
dpkg-deb: 1 errors in control file
/var/tmp/TXqFaXTCdUleBmfFFWfrl/dpkgbuild.log (END) 


ive tried install kiba dock several times now, and i cant get it to work right when i check the install

---

### Post by NOSintake on 2007-02-20
ok, i fixed my problem from before, but it still has the black background. ive read that you have to have beryl install, and for all i know, i installed it correctly. is there anyway to check to see if it isnt install correctly? i have an ati x1400 video card if that makes a difference

---

### Post by NOSintake on 2007-02-21
nevermind, i got it to work. had to revert to beryl 0.1.99

---

### Post by naseem on 2007-02-23
hy I just installed it on feisty but it loocks strange, instead of the icons it shows up small preview of opened window and if I clik on the bar and try to open kiba-utils > icon edit I get this error message in a pop up window: This problem report does not apply to a packaged program. (/usr/bin/kiba-icon-editor.py) I installed with sudo make install, since sudo checkinstall did not make it start (I do have chekinstall installed)

---

### Post by freakavoid on 2007-02-23
Hi,

is anyone else experiencing problems with the autohide function?
When I start kiba-dock it works okey but after I launch a program it never hides again.

---

### Post by Botunda on 2007-02-23
> **bvanaerde said:**
> It doesn't look nice when you don't have Beryl installed ;)

Yeah but how do **I** get beryl installed. I have the specs below on the laptop and i can't seem to find a driver that works. Or at least instructions to work! Prolly just a issue between chair and keyboard but still.

---

### Post by naseem on 2007-02-24
same froblem as freakavoid , i did somethin wrong or the kiba is buggy
I put it to autohide but if lounch a prog it doesn't hide anymore, also some icons do show in proper size but ones clicked they get resized smaller??? strange

I installed with make install, chekinstall did not work, Id like to remove it completly, and maybe retry installation, please help me or post a usefull link , thanks!

---

### Post by Andy0 on 2007-02-26
Yep CVS server currently down, gnomefreeks .deb not working properly -> PrinceChild knows

---

### Post by kelbizzle on 2007-02-28
> **Andy0 said:**
> Yep CVS server currently down, gnomefreeks .deb not working properly -> PrinceChild knows

Thanks for that I won't even bother with it. I saw the videos on google though it looks sweet.

---

### Post by amaan on 2007-02-28
i installed kiba-dock but the background of the dock shows all these weird blue and red lines, how do i make that go away?

---

### Post by Pirate742 on 2007-03-01
so is the server coming back up? or just give up :-/ looked really neat

---

### Post by amaan on 2007-03-01
this is what i get when i run kiba-dock, i've tried restarting several times (it does nothing) also tried reinstalling a couple of time also no luck. i'm running ubuntu 6.10 and beryl

check out the screenshot

---

### Post by hoagie on 2007-03-01
I get the same. Let's wait until it gets fixed, hopefully.

---

### Post by amaan on 2007-03-01
ubuntu admins come to our aid :( we can't run kiba :(

---

### Post by PriceChild on 2007-03-01
Use the packages detailed at the top of the original post until kiba people sort things out.

---

### Post by DrZeus on 2007-03-01
I tried installing a .deb package, and had that same problem.  Lets all stick to avant-window-nav until this gets sorted.  kiba looks really promising, so lets wait and see.

---

### Post by amaan on 2007-03-01
yea i'm using the one posted at the beginning of this thread, it works perfectly except for the background being blue stripes

can't wait to get kiba running properly :)

---

### Post by magli on 2007-03-02
I am also having the same problem - it comes up with a blue-lined background, as seen in amaan's screenshot.

I also thought I should mention that after installing the .deb - it wouldn't run.. there was an error stating that libglitz was missing.

Installing libglitz1 fixed this.. but this should clearly be dependency, and get installed automatically by apt.

---

### Post by BaLtO on 2007-03-02
Looks like we all have the same problem of getting blue-line background, by using the .deb package on the front page, hopefully the problem would be solve soon.

I want to get kiba-dock working well.

---

### Post by wataboutbob on 2007-03-02
Same problem with the blue background here. Having said that... somehow I'm kinda used to having a regular panel with transparency autohide. Seems way more useful than kiba to me. Wouldn't mind trying kiba once its fixed though - nice eye candy to show off to the windows people.

---

### Post by jeonunh on 2007-03-02
Whenever I type kiba-dock in terminal or alt-f2 it just doesn't do anything.  I don't get an error message or anything.  In terminal it just hangs at a cursor...... any ideas?

---

### Post by STREETURCHINE on 2007-03-03
i have run into a problem here
any one know what is happening

```
rex@rex-desktop:~$ sudo aptitude remove automake1.4
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
rex@rex-desktop:~$ sudo aptitude install cvs automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev checkinstall libglade2-dev libxcomposite-dev libtool libgtop2-dev
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Note: selecting "libglitz-glx1-dev" instead of the
    virtual package "libglitz-glx-dev"
The following NEW packages will be automatically installed:
  libart-2.0-dev libbz2-dev libcroco3-dev libgl1-mesa-dev libglitz1-dev
  libgsf-1-dev libidl-dev liborbit2-dev libxml2-dev mesa-common-dev orbit2
  x11proto-composite-dev
The following NEW packages will be installed:
  cvs libart-2.0-dev libbz2-dev libcroco3-dev libgconf2-dev libgl1-mesa-dev
  libglade2-dev libglitz-glx1-dev libglitz1-dev libgsf-1-dev libgtop2-dev
  libidl-dev liborbit2-dev librsvg2-dev libxcomposite-dev libxml2-dev
  mesa-common-dev orbit2 x11proto-composite-dev
0 packages upgraded, 19 newly installed, 0 to remove and 0 not upgraded.
Need to get 4172kB of archives. After unpacking 14.7MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://au.archive.ubuntu.com dapper/main cvs 1:1.12.9-17 [1442kB]
Get:2 http://security.ubuntu.com dapper-security/main libgsf-1-dev 1.13.99-0ubuntu2.1 [223kB]
Get:3 http://www.beerorkid.com dapper/main x11proto-composite-dev 1:0.3-0ubuntu2 [3748B]
Get:4 http://www.beerorkid.com dapper/main libxcomposite-dev 1:0.3-0ubuntu1 [12.2kB]
Get:5 http://www.beerorkid.com dapper/main mesa-common-dev 6.5.1+cvs20060824 [173kB]
Get:6 http://www.beerorkid.com dapper/main libgl1-mesa-dev 6.5.1+cvs20060824 [47.7kB]
Get:7 http://security.ubuntu.com dapper-security/main libgtop2-dev 2.14.1-0ubuntu1.1 [100kB]
Get:8 http://www.beerorkid.com dapper/main libglitz1-dev 0.5.6-0ubuntu1 [86.3kB]Get:9 http://www.beerorkid.com dapper/main libglitz-glx1-dev 0.5.6-0ubuntu1 [31.1kB]
Get:10 http://au.archive.ubuntu.com dapper/main libart-2.0-dev 2.3.17-1 [77.0kB]Get:11 http://au.archive.ubuntu.com dapper/main libbz2-dev 1.0.3-0ubuntu2 [32.3kB]
Get:12 http://au.archive.ubuntu.com dapper/main libcroco3-dev 0.6.1-1build1 [138kB]
Get:13 http://au.archive.ubuntu.com dapper/main libidl-dev 0.8.6-0ubuntu4 [100kB]
Get:14 http://au.archive.ubuntu.com dapper/main liborbit2-dev 1:2.14.0-0ubuntu1 [446kB]
Get:15 http://au.archive.ubuntu.com dapper/main libgconf2-dev 2.14.0-1ubuntu2 [252kB]
Get:16 http://au.archive.ubuntu.com dapper/main libxml2-dev 2.6.24.dfsg-1ubuntu1 [641kB]
Get:17 http://au.archive.ubuntu.com dapper/main libglade2-dev 1:2.5.1-2ubuntu2 [126kB]
Get:18 http://au.archive.ubuntu.com dapper/main librsvg2-dev 2.14.4-0ubuntu1 [150kB]
Get:19 http://au.archive.ubuntu.com dapper/universe orbit2 1:2.14.0-0ubuntu1 [91.4kB]
Fetched 4172kB in 1m41s (41.0kB/s)
Preconfiguring packages ...
Selecting previously deselected package x11proto-composite-dev.
(Reading database ... 98335 files and directories currently installed.)
Unpacking x11proto-composite-dev (from .../x11proto-composite-dev_1%3a0.3-0ubuntu2_all.deb) ...
Selecting previously deselected package libxcomposite-dev.
Unpacking libxcomposite-dev (from .../libxcomposite-dev_1%3a0.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package cvs.
Unpacking cvs (from .../cvs_1%3a1.12.9-17_i386.deb) ...
Selecting previously deselected package libart-2.0-dev.
Unpacking libart-2.0-dev (from .../libart-2.0-dev_2.3.17-1_i386.deb) ...
Selecting previously deselected package libbz2-dev.
Unpacking libbz2-dev (from .../libbz2-dev_1.0.3-0ubuntu2_i386.deb) ...
Selecting previously deselected package libcroco3-dev.
Unpacking libcroco3-dev (from .../libcroco3-dev_0.6.1-1build1_i386.deb) ...
Selecting previously deselected package libidl-dev.
Unpacking libidl-dev (from .../libidl-dev_0.8.6-0ubuntu4_i386.deb) ...
Selecting previously deselected package liborbit2-dev.
Unpacking liborbit2-dev (from .../liborbit2-dev_1%3a2.14.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgconf2-dev.
Unpacking libgconf2-dev (from .../libgconf2-dev_2.14.0-1ubuntu2_i386.deb) ...
Selecting previously deselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_6.5.1+cvs20060824_all.deb) ...
Selecting previously deselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_6.5.1+cvs20060824_i386.deb) ...
Selecting previously deselected package libxml2-dev.
Unpacking libxml2-dev (from .../libxml2-dev_2.6.24.dfsg-1ubuntu1_i386.deb) ...
Selecting previously deselected package libglade2-dev.
Unpacking libglade2-dev (from .../libglade2-dev_1%3a2.5.1-2ubuntu2_i386.deb) ...Selecting previously deselected package libglitz1-dev.
Unpacking libglitz1-dev (from .../libglitz1-dev_0.5.6-0ubuntu1_i386.deb) ...
Selecting previously deselected package libglitz-glx1-dev.
Unpacking libglitz-glx1-dev (from .../libglitz-glx1-dev_0.5.6-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgsf-1-dev.
Unpacking libgsf-1-dev (from .../libgsf-1-dev_1.13.99-0ubuntu2.1_i386.deb) ...
Selecting previously deselected package libgtop2-dev.
Unpacking libgtop2-dev (from .../libgtop2-dev_2.14.1-0ubuntu1.1_i386.deb) ...
Selecting previously deselected package librsvg2-dev.
Unpacking librsvg2-dev (from .../librsvg2-dev_2.14.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package orbit2.
Unpacking orbit2 (from .../orbit2_1%3a2.14.0-0ubuntu1_i386.deb) ...
Setting up x11proto-composite-dev (0.3-0ubuntu2) ...
Setting up libxcomposite-dev (0.3-0ubuntu1) ...
Setting up cvs (1.12.9-17) ...

Setting up libart-2.0-dev (2.3.17-1) ...
Setting up libbz2-dev (1.0.3-0ubuntu2) ...

Setting up libcroco3-dev (0.6.1-1build1) ...
Setting up libidl-dev (0.8.6-0ubuntu4) ...
Setting up liborbit2-dev (2.14.0-0ubuntu1) ...
Setting up libgconf2-dev (2.14.0-1ubuntu2) ...

Setting up mesa-common-dev (6.5.1+cvs20060824) ...
Setting up libgl1-mesa-dev (6.5.1+cvs20060824) ...
Setting up libxml2-dev (2.6.24.dfsg-1ubuntu1) ...
Setting up libglade2-dev (2.5.1-2ubuntu2) ...

Setting up libglitz1-dev (0.5.6-0ubuntu1) ...
Setting up libglitz-glx1-dev (0.5.6-0ubuntu1) ...
Setting up libgsf-1-dev (1.13.99-0ubuntu2.1) ...

Setting up libgtop2-dev (2.14.1-0ubuntu1.1) ...

Setting up librsvg2-dev (2.14.4-0ubuntu1) ...
Setting up orbit2 (2.14.0-0ubuntu1) ...
rex@rex-desktop:~$ cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
cvs checkout: CVS password file /home/rex/.cvspass does not exist - creating a new file
PAM authenticate error: Authentication failure
cvs checkout: authorization failed: server metascape.afraid.org rejected access to /cvsroot for user anonymous
cvs checkout: used empty password; try "cvs login" with a real password
rex@rex-desktop:~$  cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
cvs checkout: CVS password file /home/rex/.cvspass does not exist - creating a new file
PAM authenticate error: Authentication failure
cvs checkout: authorization failed: server metascape.afraid.org rejected access to /cvsroot for user anonymous
cvs checkout: used empty password; try "cvs login" with a real password
rex@rex-desktop:~$ cd kiba-dock
bash: cd: kiba-dock: No such file or directory
rex@rex-desktop:~$


```

---

### Post by Quickdood on 2007-03-03
I got the blue stripes too! I will keep an eye on this thread for updates!

---

### Post by amaan on 2007-03-04
still nothing? damnit lol

---

### Post by BaLtO on 2007-03-05
I using old one which I found from
[http://forum.beryl-project.org/viewtopic.php?f=38&t=165](http://forum.beryl-project.org/viewtopic.php?f=38&t=165)

And it works quite well, the blue stripes can be changed away from the settings.

---

### Post by bg1256 on 2007-03-05
Here's an older deb package from link above. Worked like a charm for me.

---

### Post by xPo on 2007-03-06
I cant run kiba-dock.

It appears an error or sth:

"kiba-dock: symbol lookup error: /usr/local/lib/kiba-dock/libtaskbar.so: undefined symbol: gdk_screen_get_window_stack"

I dont know what is it.

---

### Post by bg1256 on 2007-03-07
Do you have the dependencies met?

---

### Post by ditikos on 2007-03-08
Here is something else -- I am using XFCE (xubuntu). I am having the blue stripes problem, but when I run gset-kiba there is no save button -- so there is no save for my new options. I am using the deb file from page 1. Is there a new one, or something else to fix it?

I can't find the source to compile it myself :(

---

### Post by popkub on 2007-03-09
> **xPo said:**
> I cant run kiba-dock.

It appears an error or sth:

"kiba-dock: symbol lookup error: /usr/local/lib/kiba-dock/libtaskbar.so: undefined symbol: gdk_screen_get_window_stack"

I dont know what is it.

Same me I don't know how to fix it?

---

### Post by dyntryx on 2007-03-11
**To everyone with the "blue stripe" problem!...**

If you would read the forum, people are saying they fixed it using [the package]("http://ubuntuforums.org/attachment.php?attachmentid=26702&d=1173154935") [bg1256]("http://ubuntuforums.org/member.php?u=164206") posted in [this thread]("http://ubuntuforums.org/showpost.php?p=2254017&postcount=194").  However, please note this is not the newest version.

The [reason for this problem]("http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=128.0") seems to be that the packages provided in [Treviño's Beryl-SVN Ubuntu Repository]("http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/") are trying to run the latest kiba-dock with outdated libraries.

Personally, I got kiba-dock working by simply using the package provided at [Treviño's Beryl-SVN Ubuntu Repository]("http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/"), **before** the newest one.  I assume this package probably still works with the older kiba-dock libraries, and therefore it loads correctly.  You can grab that package [here]("http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/kiba-dock_0.1.1+svn20070222+3v1ubuntu0_i386.deb").  Also note that this is not the newest version, either.

Good luck, guys. :)

---

### Post by insert_name_here on 2007-03-15
I installed from the original svn from the first post.  I got this error: 

kiba-dock: error while loading shared libraries: libakamaru.so.0: cannot open shared object file: No such file or directory

What do I do?  I am running Edgy, with Beryl 0.2.0 with XGL.

---

### Post by PriceChild on 2007-03-15
Hmmm I can't figure this out...

*sticks a warning back up*

---

### Post by insert_name_here on 2007-03-15
Ohhh good.  :(

It's OK tho, because I found of the binaries that worked.  I _believe_ it was kiba-dock_0.1-1.2_i386.deb

---

### Post by Mohammad_Khalid_Hussain on 2007-03-16
Hey if it isnt much trouble for you, I would like you to help me with this problem.

I did exactly everything as you said except FOR the version naming thing which I didnt know how to do so i left that out,(just naming anyway rite?)

Then when i type "kiba-dock" i get this error saying that it cant find it.
[http://img379.imageshack.us/img379/5044/screenshotix5.png](http://img379.imageshack.us/img379/5044/screenshotix5.png)

Help me pls

---

### Post by b3n87 on 2007-03-16
the SVN server seems to be working now?

ive followed the guide but getting the following error

kiba-dock: symbol lookup error: kiba-dock: undefined symbol: cairo_glitz_surface_create


anyone else had any more luck?

---

### Post by yachi on 2007-03-17
> **b3n87 said:**
> the SVN server seems to be working now?

ive followed the guide but getting the following error

kiba-dock: symbol lookup error: kiba-dock: undefined symbol: cairo_glitz_surface_create


anyone else had any more luck?i got the same error:sad:

---

### Post by bchan90 on 2007-03-19
i get this error when i try running "kiba-dock"

> (kiba-dock:29175): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed

(kiba-dock:29175): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed

(kiba-dock:29175): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed
Segmentation fault (core dumped)

i would really appreciate any help, been tryin to figure out the problem for a while.

---

### Post by fakie_flip on 2007-03-20
> **PriceChild said:**
> Just pointing out i attached my Edgy package on the first post.

I don't see the deb. Where is it? I see one link in the first post. There are debs, but not kiba-dock. I tried the hot-babes deb and that is nice.

---

### Post by b3n87 on 2007-03-21
theres just been an update for kiba-dock and its plugins
but i still get the 

Illegal instruction (core dumped)


error message


i used to have it working as a windows task bar on an older version but cant remember which version
anyone got any advice or error messages?
im pretty keen to get this working again

---

### Post by abstar on 2007-03-24
if you have this error:

*kiba-dock: error while loading shared libraries: libakamaru.so.0: cannot open shared object file: No such file or directory*

just do this:

sudo ln -s /usr/local/lib/libakamaru.so.0 /usr/lib/libakamaru.so.0

because Now if you try to run kiba-dock from the terminal, you will get another error about the file 'libakamaru.so.0'. This file was installed into /usr/local/lib instead of /usr/lib.

---

### Post by Perfect Storm on 2007-03-25
> **abstar said:**
> if you have this error:

*kiba-dock: error while loading shared libraries: libakamaru.so.0: cannot open shared object file: No such file or directory*

just do this:

sudo ln -s /usr/local/lib/libakamaru.so.0 /usr/lib/libakamaru.so.0

because Now if you try to run kiba-dock from the terminal, you will get another error about the file 'libakamaru.so.0'. This file was installed into /usr/local/lib instead of /usr/lib.


Works!

Edit: too fast saying it works, after I made reboot I get a Segmentation fault (core dumped)

---

### Post by dudeness3 on 2007-03-25
I got it to work, but everything is black accept the taskbar and dock, any ideas?

---

### Post by Perfect Storm on 2007-03-25
You need to install and running beryl.

---

### Post by PriceChild on 2007-03-26
> **Artificial Intelligence said:**
> You need to install and running beryl.or compiz, xcompmgr etc...

---

### Post by CanBert on 2007-03-28
Built er today and black screen then eventually crashes -- wait for a fix I guess

---

### Post by Jens Johansson on 2007-03-28
I get this error when I try to start kiba-dock



> failed to load /usr/lib/kiba-dock/liblauncher.so
/usr/lib/kiba-dock/liblauncher.so: undefined symbol: kiba_exec
*** glibc detected *** kiba-dock: double free or corruption (out): 0x08089448 ***


and then some thing about backtrace, then at the end "Aborted (core dumped)"

---

### Post by CanBert on 2007-03-28
The Kiba-Dock checkinstall fails on me that is why I am having no luck --

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/canbert/kiba-dock/kibadock/src'
make[2]: Entering directory `/home/canbert/kiba-dock/kibadock/src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'kiba-dock' '/usr/local/bin/kiba-dock'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/canbert/kiba-dock/kibadock/src'
make[1]: Leaving directory `/home/canbert/kiba-dock/kibadock/src'
Making install in include
make[1]: Entering directory `/home/canbert/kiba-dock/kibadock/include'
make[2]: Entering directory `/home/canbert/kiba-dock/kibadock/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/kiba-dock" || mkdir -p -- "/usr/local/include/kiba-dock"
 /usr/bin/install -c -m 644 'kiba-dock.h' '/usr/local/include/kiba-dock/kiba-dock.h'
 /usr/bin/install -c -m 644 'kiba-geometry.h' '/usr/local/include/kiba-dock/kiba-geometry.h'
 /usr/bin/install -c -m 644 'kiba-object.h' '/usr/local/include/kiba-dock/kiba-object.h'
 /usr/bin/install -c -m 644 'kiba-plugin.h' '/usr/local/include/kiba-dock/kiba-plugin.h'
 /usr/bin/install -c -m 644 'kiba-render.h' '/usr/local/include/kiba-dock/kiba-render.h'
 /usr/bin/install -c -m 644 'kiba-x11.h' '/usr/local/include/kiba-dock/kiba-x11.h'
 /usr/bin/install -c -m 644 'kiba-settings.h' '/usr/local/include/kiba-dock/kiba-settings.h'
 /usr/bin/install -c -m 644 'kiba-sys.h' '/usr/local/include/kiba-dock/kiba-sys.h'
make[2]: Leaving directory `/home/canbert/kiba-dock/kibadock/include'
make[1]: Leaving directory `/home/canbert/kiba-dock/kibadock/include'
Making install in gset-kiba
make[1]: Entering directory `/home/canbert/kiba-dock/kibadock/gset-kiba'
make[1]: *** No rule to make target `gset-kiba.desktop', needed by `all-am'.  Stop.
make[1]: Leaving directory `/home/canbert/kiba-dock/kibadock/gset-kiba'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

---

### Post by FuZ3 on 2007-03-29
Yeah I'm having the same problem. Can anyone help?

---

### Post by sixfoottallrabbit on 2007-04-03
**EDIT**

Now when I run the second autogen.sh I get:

No package 'akamaru' found

I'm sure I installed the first package properly...

---

### Post by 5ER on 2007-04-06
I also get segmentation fault when trying to launch the kiba-dock.
Anyone fixing this soon?
I did everything like the step-by-step said.

> **sixfoottallrabbit said:**
> **EDIT**

Now when I run the second autogen.sh I get:

No package 'akamaru' found

I'm sure I installed the first package properly...
Try to install devel package (development, those name-dev packages)
If it does not help, you can still remove it.

---

### Post by mikibg on 2007-04-07
> **bg1256 said:**
> Here's an older deb package from link above. Worked like a charm for me.

yep work for me 2 ....page 20 for link

---

### Post by dominicd on 2007-04-10
> **5ER said:**
> I also get segmentation fault when trying to launch the kiba-dock.
Anyone fixing this soon?
I did everything like the step-by-step said.


I have the same error. I've tried all sorts of things now but still no luck >.<

---

### Post by dominicd on 2007-04-10
> **dominicd said:**
> I have the same error. I've tried all sorts of things now but still no luck >.<

This is what I'm getting.

```
Starting program: /usr/local/bin/kiba-dock 
[Thread debugging using libthread_db enabled]
[New Thread 47811278048368 (LWP 30035)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 47811278048368 (LWP 30035)]
kiba_plugin_init (dock_widget=<value optimized out>, plugin=0x629940)
    at sysinfo.c:580
580       sysinfo->cpu_frequency = kiba_sys_get_cpu_frequency ();

```

So in the Gset-kiba I disabled sysinfo and now it launches but it's reeaally buggy and not useable. 

Somehow it managed to screw up beryl...

---

### Post by IitachiI on 2007-04-12
im getting this error (Reading database ... 127033 files and directories currently installed.)
Unpacking gsetkiba (from .../gsetkiba_1-1_amd64.deb) ...
dpkg: error processing /home/panda/Desktop/kiba-dock/gsetkiba/gsetkiba_1-1_amd64
.deb (--install):
 trying to overwrite `/usr/local/bin/gset-kiba', which is also in package kibado
ck
Errors were encountered while processing:
 /home/panda/Desktop/kiba-dock/gsetkiba/gsetkiba_1-1_amd64.deb
/var/tmp/CenYeqUbmNcljhhhGlMSV/dpkginstall.log (END) hoping someone can help =(

---

### Post by Sdr4wkc4b on 2007-04-12
getting this error at the get source step:
bash: svn: command not found

---

### Post by tehpopa on 2007-04-12
I'm trying to get this installed and I'm running into a snag. Here's the error I get:

> checking for GSET_KIBA... configure: error: Package requirements ("akamaru >= 0.1 kiba-dock >= 0.1") were not met:

No package 'akamaru' found
No package 'kiba-dock' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GSET_KIBA_CFLAGS
and GSET_KIBA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I'm sure the others are configured, I did everything according the the OP of this thread. I am kind of lost from here. Any help or points in the right direction would be amazingly appreciated. Thanks guys.

---

### Post by hype on 2007-04-13
Hi, just followed the How-to. After starting kiba-dock from terminal , i get this error:
```
@kiba-dock 
kiba-dock: symbol lookup error: kiba-dock: undefined symbol: cairo_glitz_surface_create

```

I have gltiz packages installed (dev too)
Any idea how to solve that?

---

### Post by insert_name_here on 2007-04-14
Sdr4wkc4b, you need to install subversion.

a simple 'sudo apt-get install subversion' should do the trick.

--------------------------------------------------------------------------

I just tried the tutorial again, and I get the same error as litachil.  

Trying the page 20 .deb starts kiba-dock, but when I try to add any icons, it segfaults, giving no error besides 'Segmentation Fault (core dumped)

---

### Post by abstar on 2007-04-15
hi guys
  i just wondering how to uninstall the kiba-dock based on this method of installation?

thanks

---

### Post by Gifty85 on 2007-04-15
Hi guys!

Do you know how to lock the dock to the desktop?

Thanks in advance!

---

### Post by Sdr4wkc4b on 2007-04-16
> **insert_name_here said:**
> Sdr4wkc4b, you need to install subversion.

a simple 'sudo apt-get install subversion' should do the trick.

--------------------------------------------------------------------------

I just tried the tutorial again, and I get the same error as litachil.  

Trying the page 20 .deb starts kiba-dock, but when I try to add any icons, it segfaults, giving no error besides 'Segmentation Fault (core dumped)

Thanks i got further now, but at the make step i get another error which translates to: cannot find a makefile or target.

---

### Post by lotacus on 2007-04-17
Don't know if it's alread been posted, so if it has, forgive me.

There seems to be a problem with beryl and kiba-dock, that when beryl is loaded, then kiba-dock loaded, it seems to endlessly spin the cube. I am not sure which app is the culprit, but I hope there is an updated kiba-dock package out there somewhere, or perhaps a work-around.

---

### Post by SPYvsSPY on 2007-04-18
i've installed kiba-dock, all the levels were just fine , no errors, installed the .deb package after , all goes OK,

but when i type kiba-dock, it says command unkown
and i havent seen any kiba-dock file

any help ?

---

### Post by dominicd on 2007-04-19
> **lotacus said:**
> Don't know if it's alread been posted, so if it has, forgive me.

There seems to be a problem with beryl and kiba-dock, that when beryl is loaded, then kiba-dock loaded, it seems to endlessly spin the cube. I am not sure which app is the culprit, but I hope there is an updated kiba-dock package out there somewhere, or perhaps a work-around.

Indeed, somehow it screwed up my beryl really bad... Took me a while to get things back to normal, for me it's no kiba-dock until I have plenty of time to fix any problems it might cause.

---

### Post by lotacus on 2007-04-19
I found what the problem was... at least in my case. I had "Computer" on the dock, and the cube always spun endlessly when I opened "Computer" from the dock. 

So I looked at the short cut settings in kiba-settings and it displayed this: nautilus --no-desktop computer:

Through a little trial, I removed all instances so that it looked like this:

nautilus computer:

I then launched "Computer" from Kiba-dock and the cube didn't spin!  However, there was a hitch, when I closed the "Computer" window, Kiba-Dock had the triangle notification still on the icon indicating the app was still launched.  Clicking on the icon did not launch "Computer". The only option was to close kiba-dock and relaunch it.

If I turned off "Spin Cube" in beryl settings manager with the unmodified "Computer" settings, the cube won't spin.

I think the line: --no-desktop is the culprit as I think it tries to interact with all the virtual desktops by trying to reveal the window on all virtual desktops, giving it focus, which would make the cube spin endlessly.

I havn't found a workable solution yet without sacrificing a feature, so I don't have "Computer" on the dock.

---

### Post by thelostarc on 2007-04-21
Every time i am trying to use the debien package.. it is telling the package is corrupted :( what to do?

---

### Post by thelostarc on 2007-04-21
In the akamaru folder ./autogen.sh is working.. but in the other folders i am facing problems:
In kibadock folder there are three sub directories: branches, tags and trunk. There is autogen.sh in trunk. I used that, then typed in "make" and it gave me following msg:
******************************************************************8
user@ubuntu:~/kiba-dock/kibadock/trunk$ make
/bin/sh ./config.status --recheck
/bin/sh: Can't open ./config.status
make: *** [config.status] Error 2
********************************************************************
Can anyone please help?

I tried to download the .deb file uploaded by jasnix... it is telling me that the package is corrupted :(

---

### Post by lotacus on 2007-04-23
I just checked out the CVS and built from that.

check this wiki out strait from kiba-dock.org

[http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock)

---

### Post by chakkaradeep on 2007-04-23
> **kwaanens said:**
> The one listed in the first post of this thread: [http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb](http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb)

This worked perfect in feisty ! Now this is called DOCK ! (no Cairo-dock, no kde docks :) )

I have attached my screen shot.

I am able to add only .desktop files i think. I tried dragging the Computer Icon in desktop and the volumes, but they were not ready to sit in the dock :)

---

### Post by mikibg on 2007-04-24
chakkaradeep use same but no KIBA ICON ......??????????

---

### Post by chakkaradeep on 2007-04-24
> **mikibg said:**
> chakkaradeep use same but no KIBA ICON ......??????????

I didnt quiet get what you are telling. Can you please explain a bit? :(

---

### Post by mikibg on 2007-04-24
no kiba icon in panel and when you want to swichoff kiba ...how you do that

---

### Post by chakkaradeep on 2007-04-24
> **mikibg said:**
> no kiba icon in panel and when you want to swichoff kiba ...how you do that

Oh..I didnt get any icon, I kill by doing **sudo killall kiba-dock** :( 

I installed the deb package !

---

### Post by mikibg on 2007-04-24
lol ....same here.....i install some deb before...and kiba icon was in panel but this is best deb for ubutu ...and no icon !!!! 
lmao

[http://img217.imageshack.us/img217/6697/screenshotsl2.png](http://img217.imageshack.us/img217/6697/screenshotsl2.png)

---

### Post by chakkaradeep on 2007-04-24
> **mikibg said:**
> lol ....same here.....i install some deb before...and kiba icon was in panel but this is best deb for ubutu ...and no icon !!!! 
lmao

Got it !

right click kiba-dock-->Kiba utils-->systray

now you can quit :)

---

### Post by mikibg on 2007-04-24
LoL icon now in panel .....tq :guitar:

---

### Post by paul.maddox on 2007-04-24
Is there any way to have a "Run Application..." launcher in the kiba dock, like you can in the gnome panels?

---

### Post by phantommaggot on 2007-04-24
ok, so i instlled kibadock using this 

[http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock)

im using edgy

anyways

how do i make it keep running after i close the terminal i used to open it?

and why wont beryl work right when its open?
like, the cube wont rotate with the mouse unless i use the keyboard keys,  the center button wont work at all...

---

### Post by blamecanada on 2007-04-24
Hold ALT-F2 and type the command in there. You can set it as a startup by going to system>Preferences>Sessions>Startup

---

### Post by phantommaggot on 2007-04-24
hey, thanks man.. 

it still crashes lol.. either way, ill get it working with a fresh install in about a month. 

thats when i decide weather not i want 7.04.. lol

---

### Post by MageMasher on 2007-04-25
I can't seem to be able drag'n'drop anything on to it, its just two little bits of pixels at the bottom (if I rotate my cube in beryl I can see it hiding just underneath my desktop). If I drag any icons from a kde program it just pops a menu up from kdesktop to add it there instead, but if I drag an icon from a GTK program (like inkscape) I get animated arrows appear near the dock. The icon still doesn't attach itself to the dock, do I need to be running Gnome for it to work properly or is their a KDE workaround? Or am I just doing something wrong :(

---

### Post by Muppeteer on 2007-04-26
> **MageMasher said:**
> I can't seem to be able drag'n'drop anything on to it, its just two little bits of pixels at the bottom (if I rotate my cube in beryl I can see it hiding just underneath my desktop). If I drag any icons from a kde program it just pops a menu up from kdesktop to add it there instead, but if I drag an icon from a GTK program (like inkscape) I get animated arrows appear near the dock. The icon still doesn't attach itself to the dock, do I need to be running Gnome for it to work properly or is their a KDE workaround? Or am I just doing something wrong :(

I had the same problem....

You need to create a shortcut on the desktop (easiest way) and drag it into ~/.kiba-dock/launcher

This folder is hidden, so you'll need to show hidden files or just use the teminal :) 

Hope that works for ya :guitar:

---

### Post by rabid9797 on 2007-04-29
hey guys,

i used this repo install to install kiba-dock

[http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock)

and everything installed fine, but when i start kiba-dock i just get a black bar across the bottom of the screen. i have beryl and emerald installed, adn they are working correctly. 

any ideas on what i can do?

---

### Post by rabid9797 on 2007-04-29
bump :(

---

### Post by Fireblend on 2007-04-29
Maybe if you right-click the beryl icon and select reload window manager?

---

### Post by rabid9797 on 2007-04-29
nope, didn't work

---

### Post by rabid9797 on 2007-04-30
=\

---

### Post by Fidelity on 2007-04-30
Im getting the same problem

It might have someting to do with this:

** Message: cant load file /home/james/.kiba-dock/config into buffer notificatio                 ns: Failed to open file '/home/james/.kiba-dock/config': No such file or directo                 ry

---

### Post by rabid9797 on 2007-05-01
i had a problem with that, but i actually just went to the kiba-dock site and recomplied from source and everything worked.

---

### Post by Fidelity on 2007-05-01
Following the instructions in the first post, I can do ./autogen.sh once, but in the other folders it wont work, it says:

bash: ./autogen.sh: No such file or directory

I did everything correctly and i'm sure of it. Please help, I really want kiba dock :(

---

### Post by Perfect Storm on 2007-05-02
Some of them are in /src or similar try check it, it might be in a sub dir.

---

### Post by Muppeteer on 2007-05-03
I'm trying to install the svn version after a clean install but i keep failing dependencies and i don't know where to get them. 

```
checking for KIBA_DOCK... configure: error: Package requirements ("akamaru >= 0.1 glib-2.0 >= 2.8.0 gobject-2.0 gnome-desktop-2.0 >= 2.8 gtk+-2.0 >= 2.8.0 cairo >= 1.0.0 pango >= 1.10.0 pangocairo >= 1.10.0") were not met:

```

Aren't these major parts of Ubuntu? gnome-desktop, gtk? Anybody know what i can do?

---

### Post by tyboon on 2007-05-05
i did the first step... and i got this...
> hvasss@hvasss-desktop:~$ sudo aptitude remove automake1.4
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  beryl-core beryl-manager beryl-plugins beryl-plugins-data 
  beryl-plugins-unsupported-data beryl-settings beryl-settings-bindings 
  emerald libberyldecoration0 libberylsettings0 
The following packages have been kept back:
  beryl beryl-plugins-unsupported 
0 packages upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
hvasss@hvasss-desktop:~$ sudo aptitude install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Note: selecting "libglitz-glx1-dev" instead of the
      virtual package "libglitz-glx-dev"
The following packages have been automatically kept back:
  beryl-core beryl-manager beryl-plugins beryl-plugins-data 
  beryl-plugins-unsupported-data beryl-settings beryl-settings-bindings 
  emerald libberyldecoration0 libberylsettings0 
The following NEW packages will be automatically installed:
  autoconf autotools-dev g++ g++-4.1 libart-2.0-dev libatk1.0-dev 
  libbz2-dev libcairo2-dev libcroco3-dev libexpat1-dev libfontconfig1-dev 
  libfreetype6-dev libgl1-mesa-dev libglib2.0-dev libglitz1-dev 
  libgsf-1-dev libice-dev libidl-dev libltdl3 libltdl3-dev liborbit2-dev 
  libpng12-dev libpopt-dev libsm-dev libstdc++6-4.1-dev libx11-dev 
  libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev 
  libxft-dev libxi-dev libxinerama-dev libxml2-dev libxrandr-dev 
  libxrender-dev mesa-common-dev orbit2 x11proto-composite-dev 
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev 
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev 
  x11proto-xinerama-dev xlibmesa-gl-dev xtrans-dev zlib1g-dev 
The following packages have been kept back:
  beryl beryl-plugins-unsupported 
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev build-essential fakeroot g++ g++-4.1 
  libart-2.0-dev libatk1.0-dev libbz2-dev libcairo2-dev libcroco3-dev 
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgconf2-dev 
  libgl1-mesa-dev libglade2-dev libglib2.0-dev libglitz-glx1-dev 
  libglitz1-dev libgsf-1-dev libgtk2.0-dev libgtop2-dev libice-dev 
  libidl-dev libltdl3 libltdl3-dev liborbit2-dev libpango1.0-dev 
  libpng12-dev libpopt-dev librsvg2-dev libsm-dev libstdc++6-4.1-dev 
  libtool libx11-dev libxau-dev libxcomposite-dev libxcursor-dev 
  libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev 
  libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev mesa-common-dev 
  orbit2 x11proto-composite-dev x11proto-core-dev x11proto-fixes-dev 
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev 
  x11proto-xext-dev x11proto-xinerama-dev xlibmesa-gl-dev xtrans-dev 
  zlib1g-dev 
0 packages upgraded, 63 newly installed, 0 to remove and 12 not upgraded.
Need to get 24.1MB of archives. After unpacking 80.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-core-dev 7.0.10-1 [86.3kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libice-dev 2:1.0.3-1build1 [55.9kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libsm-dev 2:1.0.2-1build1 [25.6kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxau-dev 1:1.0.3-1 [15.5kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxdmcp-dev 1:1.0.2-1 [19.8kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-input-dev 1.4.1-1 [15.4kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-kb-dev 1.0.3-2ubuntu1 [27.0kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main xtrans-dev 1.0.3-1 [69.2kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libx11-dev 2:1.1.1-1ubuntu3 [8685kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-xext-dev 7.0.2-5ubuntu1 [42.2kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-xext-dev 7.0.2-5ubuntu1   
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-fixes-dev 1:4.0-0.1ubuntu2 [5662B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxfixes-dev 1:4.0.3-1 [12.1kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-composite-dev 1:0.3.1-1ubuntu2 [4432B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxcomposite-dev 1:0.3.1-1 [9516B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-render-dev 2:0.9.2-4ubuntu1 [6960B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxrender-dev 1:0.9.1-3 [24.4kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxcursor-dev 1:1.1.8-1 [30.6kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxext-dev 2:1.0.3-1build1 [81.5kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libexpat1-dev 1.95.8-3.4build1 [129kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main zlib1g-dev 1:1.2.3-13ubuntu4 [407kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libfreetype6-dev 2.2.1-5ubuntu1 [640kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libfontconfig1-dev 2.4.2-1ubuntu1 [344kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxft-dev 2.1.12-1 [60.7kB]    
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxi-dev 2:1.1.0-1build1 [67.7kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-xinerama-dev 1.1.2-4ubuntu1 [5424B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxinerama-dev 2:1.0.1-4build1 [4196B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main x11proto-randr-dev 1.2.1-1 [28.6kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxrandr-dev 2:1.2.0-3ubuntu1 [27.5kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main autoconf 2.61-3 [448kB]         
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main autotools-dev 20060920.1 [61.1kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main automake1.9 1.9.6+nogfdl-3ubuntu1 [388kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libstdc++6-4.1-dev 4.1.2-0ubuntu4 [1632kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main g++-4.1 4.1.2-0ubuntu4 [2581kB] 
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main g++ 4:4.1.2-1ubuntu1 [1428B]    
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main build-essential 11.3 [6974B]    
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main fakeroot 1.5.10ubuntu2 [99.4kB] 
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libart-2.0-dev 2.3.17-1 [77.0kB]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libglib2.0-dev 2.12.11-0ubuntu1 [536kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libatk1.0-dev 1.18.0-0ubuntu1 [112kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libbz2-dev 1.0.3-6build1 [31.9kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libpng12-dev 1.2.15~beta5-1 [172kB]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libcairo2-dev 1.4.2-0ubuntu1 [507kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libcroco3-dev 0.6.1-1build1 [138kB]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libpopt-dev 1.10-3build1 [38.3kB]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libidl-dev 0.8.7-0.1ubuntu2 [102kB]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main liborbit2-dev 1:2.14.7-0ubuntu1 [459kB]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libgconf2-dev 2.18.0.1-0ubuntu1 [271kB]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libpango1.0-dev 1.16.2-0ubuntu1 [355kB]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libgtk2.0-dev 2.10.11-0ubuntu3 [2590kB]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxml2-dev 2.6.27.dfsg-1ubuntu3 [672kB]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libglade2-dev 1:2.6.0-3 [129kB] 
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main mesa-common-dev 6.5.2-3ubuntu7 [174kB]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libgl1-mesa-dev 6.5.2-3ubuntu7 [24.6kB]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main xlibmesa-gl-dev 1:7.2-0ubuntu11 [25.6kB]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libglitz1-dev 0.5.6-1 [85.2kB]  
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libglitz-glx1-dev 0.5.6-1 [30.6kB]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libgsf-1-dev 1.14.3-1ubuntu2 [228kB]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libgtop2-dev 2.14.8-0ubuntu1 [104kB]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libltdl3 1.5.22-4 [168kB]       
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libltdl3-dev 1.5.22-4 [356kB]   
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main librsvg2-dev 2.16.0-0ubuntu2 [159kB]
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libtool 1.5.22-4 [328kB]        
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe orbit2 1:2.14.7-0ubuntu1 [99.1kB]
Fetched 24.1MB in 5m53s (68.1kB/s)                                              
Extracting templates from packages: 100%
Selecting previously deselected package x11proto-core-dev.
(Reading database ... 108087 files and directories currently installed.)
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.10-1_all.deb) ...
Selecting previously deselected package libice-dev.
Unpacking libice-dev (from .../libice-dev_2%3a1.0.3-1build1_i386.deb) ...
Selecting previously deselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.0.2-1build1_i386.deb) ...
Selecting previously deselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.3-1_i386.deb) ...
Selecting previously deselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.0.2-1_i386.deb) ...
Selecting previously deselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_1.4.1-1_all.deb) ...
Selecting previously deselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.3-2ubuntu1_all.deb) ...
Selecting previously deselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.0.3-1_all.deb) ...
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.1.1-1ubuntu3_i386.deb) ...
Selecting previously deselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_1.95.8-3.4build1_i386.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3-13ubuntu4_i386.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.2.1-5ubuntu1_i386.deb) ...
Selecting previously deselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.4.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package x11proto-render-dev.
Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.9.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.1-3_i386.deb) ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.1.12-1_i386.deb) ...
Selecting previously deselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.2.1-1_all.deb) ...
Selecting previously deselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package autoconf.
Unpacking autoconf (from .../autoconf_2.61-3_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20060920.1_all.deb) ...
Selecting previously deselected package automake1.9.
Unpacking automake1.9 (from .../automake1.9_1.9.6+nogfdl-3ubuntu1_all.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.5.10ubuntu2_i386.deb) ...
Selecting previously deselected package libart-2.0-dev.
Unpacking libart-2.0-dev (from .../libart-2.0-dev_2.3.17-1_i386.deb) ...
Selecting previously deselected package libglib2.0-dev.
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.12.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package libatk1.0-dev.
Unpacking libatk1.0-dev (from .../libatk1.0-dev_1.18.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libbz2-dev.
Unpacking libbz2-dev (from .../libbz2-dev_1.0.3-6build1_i386.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.15~beta5-1_i386.deb) ...
Selecting previously deselected package libcairo2-dev.
Unpacking libcairo2-dev (from .../libcairo2-dev_1.4.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libcroco3-dev.
Unpacking libcroco3-dev (from .../libcroco3-dev_0.6.1-1build1_i386.deb) ...
Selecting previously deselected package libpopt-dev.
Unpacking libpopt-dev (from .../libpopt-dev_1.10-3build1_i386.deb) ...
Selecting previously deselected package libidl-dev.
Unpacking libidl-dev (from .../libidl-dev_0.8.7-0.1ubuntu2_i386.deb) ...
Selecting previously deselected package liborbit2-dev.
Unpacking liborbit2-dev (from .../liborbit2-dev_1%3a2.14.7-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgconf2-dev.
Unpacking libgconf2-dev (from .../libgconf2-dev_2.18.0.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_6.5.2-3ubuntu7_all.deb) ...
Selecting previously deselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb) ...
Selecting previously deselected package xlibmesa-gl-dev.
Unpacking xlibmesa-gl-dev (from .../xlibmesa-gl-dev_1%3a7.2-0ubuntu11_all.deb) ...
Selecting previously deselected package libglitz1-dev.
Unpacking libglitz1-dev (from .../libglitz1-dev_0.5.6-1_i386.deb) ...
Selecting previously deselected package libglitz-glx1-dev.
Unpacking libglitz-glx1-dev (from .../libglitz-glx1-dev_0.5.6-1_i386.deb) ...
Selecting previously deselected package libxml2-dev.
Unpacking libxml2-dev (from .../libxml2-dev_2.6.27.dfsg-1ubuntu3_i386.deb) ...
Selecting previously deselected package libgsf-1-dev.
Unpacking libgsf-1-dev (from .../libgsf-1-dev_1.14.3-1ubuntu2_i386.deb) ...
Selecting previously deselected package libgtop2-dev.
Unpacking libgtop2-dev (from .../libgtop2-dev_2.14.8-0ubuntu1_i386.deb) ...
Selecting previously deselected package libltdl3.
Unpacking libltdl3 (from .../libltdl3_1.5.22-4_i386.deb) ...
Selecting previously deselected package libltdl3-dev.
Unpacking libltdl3-dev (from .../libltdl3-dev_1.5.22-4_i386.deb) ...
Selecting previously deselected package libpango1.0-dev.
Unpacking libpango1.0-dev (from .../libpango1.0-dev_1.16.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libtool.
Unpacking libtool (from .../libtool_1.5.22-4_i386.deb) ...
Selecting previously deselected package orbit2.
Unpacking orbit2 (from .../orbit2_1%3a2.14.7-0ubuntu1_i386.deb) ...
Setting up x11proto-core-dev (7.0.10-1) ...
Setting up libice-dev (1.0.3-1build1) ...
Setting up libsm-dev (1.0.2-1build1) ...
Setting up libxau-dev (1.0.3-1) ...
Setting up libxdmcp-dev (1.0.2-1) ...
Setting up x11proto-input-dev (1.4.1-1) ...
Setting up x11proto-kb-dev (1.0.3-2ubuntu1) ...
Setting up xtrans-dev (1.0.3-1) ...
Setting up libx11-dev (1.1.1-1ubuntu3) ...
Setting up libexpat1-dev (1.95.8-3.4build1) ...

Setting up zlib1g-dev (1.2.3-13ubuntu4) ...
Setting up libfreetype6-dev (2.2.1-5ubuntu1) ...

Setting up libfontconfig1-dev (2.4.2-1ubuntu1) ...
Setting up x11proto-render-dev (0.9.2-4ubuntu1) ...
Setting up libxrender-dev (0.9.1-3) ...
Setting up libxft-dev (2.1.12-1) ...
Setting up x11proto-randr-dev (1.2.1-1) ...
Setting up x11proto-xinerama-dev (1.1.2-4ubuntu1) ...
Setting up autoconf (2.61-3) ...

Setting up autotools-dev (20060920.1) ...
Setting up automake1.9 (1.9.6+nogfdl-3ubuntu1) ...

Setting up fakeroot (1.5.10ubuntu2) ...

Setting up libart-2.0-dev (2.3.17-1) ...
Setting up libglib2.0-dev (2.12.11-0ubuntu1) ...
Setting up libatk1.0-dev (1.18.0-0ubuntu1) ...
Setting up libbz2-dev (1.0.3-6build1) ...

Setting up libpng12-dev (1.2.15~beta5-1) ...
Setting up libcairo2-dev (1.4.2-0ubuntu1) ...
Setting up libcroco3-dev (0.6.1-1build1) ...
Setting up libpopt-dev (1.10-3build1) ...
Setting up libidl-dev (0.8.7-0.1ubuntu2) ...
Setting up liborbit2-dev (2.14.7-0ubuntu1) ...
Setting up libgconf2-dev (2.18.0.1-0ubuntu1) ...

Setting up mesa-common-dev (6.5.2-3ubuntu7) ...
Setting up libgl1-mesa-dev (6.5.2-3ubuntu7) ...
Setting up xlibmesa-gl-dev (7.2-0ubuntu11) ...
Setting up libglitz1-dev (0.5.6-1) ...
Setting up libglitz-glx1-dev (0.5.6-1) ...
Setting up libxml2-dev (2.6.27.dfsg-1ubuntu3) ...
Setting up libgsf-1-dev (1.14.3-1ubuntu2) ...

Setting up libgtop2-dev (2.14.8-0ubuntu1) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up libltdl3-dev (1.5.22-4) ...
Setting up libpango1.0-dev (1.16.2-0ubuntu1) ...
Setting up libtool (1.5.22-4) ...
Setting up orbit2 (2.14.7-0ubuntu1) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-xext/x11proto-xext-dev_7.0.2-5ubuntu1_all.deb:](http://us.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-xext/x11proto-xext-dev_7.0.2-5ubuntu1_all.deb:) Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]
hvasss@hvasss-desktop:~$ 
I also have beryl locked into 0.20 version cause i run on xgl-gnome....What now...?
Should i procced...?What about the error i got from the server...
Thanx...:)

---

### Post by Perfect Storm on 2007-05-06
Rerun the proceed again, it happens sometimes that connecting to server fail.

---

### Post by [SbReGo&gt; on 2007-05-06
i got this...
> checking pkg-config is at least version 0.9.0... yes
checking for GSET_KIBA... configure: error: Package requirements ("akamaru >= 0.1 kiba-dock >= 0.1") were not met:

No package 'kiba-dock' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GSET_KIBA_CFLAGS
and GSET_KIBA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


i dunno how to get around this,, 
one more: i dont see any configure files and anything to compile in these 2 dir (this could be the motive of the above error!!??!)
cd ../kibadock/
./autogen.sh
make
sudo checkinstall
cd ../kibaplugins/
./autogen.sh
make
sudo checkinstall

for both i got this:
root@ubuntulan:/usr/local/src/kiba-dock/akamaru# cd ../kibadock/
root@ubuntulan:/usr/local/src/kiba-dock/kibadock# ./autogen.sh
bash: ./autogen.sh: no file or directory

gimme some , please!

]S>

---

### Post by Perfect Storm on 2007-05-06
There's a subfolder in each so you have to eg. cd ../kibaplugins/<folder name>

---

### Post by [SbReGo&gt; on 2007-05-06
yes tnx AI, very quick response 
i got it by myself, anyway
now have to face this:
> 
root@ubuntulan:/usr/local/src/kiba-dock/kibaplugins/trunk# ./autogen.sh prefix=/usr/
bla bla bla.. 
[...]until
checking for sys/time.h... yes
./configure: line 20423: syntax error near unexpected token `0.35.0'
./configure: line 20423: `IT_PROG_INTLTOOL(0.35.0)'


same for other dir. . . 

i ve noticed that at a certain point of the configuring process this came out :
> Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).


but i dont know how to treat this advice.. 

there s some minimum requirements i have to consider befor installing this or what?
i foun d i should have:

# ntltoolsize --->installed 
# gnome-desktop ----->installed
# Cairo 1.2.0 (optional) --->?
# Librsvg > 2.14.4 (optional) --->?
# Glitz >= 0.5.3 (opzionale)--->?
# Xorg with Composite Extension anabled --->?
# Composite Manager (xcompmgr, kcompmgr, beryl, compiz)--->Beryl up&working
# memory plug-in require libgtop --->?
# bin plug-in require libgnomevfs --->?

how can i know iif all this suff are installed?

tnx again 

[S>

---

### Post by Perfect Storm on 2007-05-07
Check them in synaptic would be easist

---

### Post by [SbReGo&gt; on 2007-05-07
what about the errors?

should they disappear asa i have installed items above?

Please, spend as more word as you can as i am very new on the tux world .. so, to understand a short sentence take to me a day ! 
tnx 
hope to be able to start this addon sooooon ! 

[S>

---

### Post by Perfect Storm on 2007-05-07
It's hard to say as kiba-dock is in early alpha stage and can be highly unstable or completly broken.

But you can try, just don't get the hopes up to high,

```
sudo aptitude install libgnomevfs2-dev libcairo2-dev librsvg2-dev libxcomposite-dev libgtop2-dev
```

---

### Post by [SbReGo&gt; on 2007-05-07
I am almost there...
step by step .. 

I ve understood tht error are due to a non-updated library ...
I had the inittool of older version so i got this error: `IT_PROG_INTLTOOL(0.35.0)'
after updating this i went beyond..
just  a little, to find this:
> 
checking for GNOME_DESKTOP... configure: error: Package requirements (gnome-desktop-2.0 >= 2.8) were not met:

No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
  
I think tht Gnome an important part of the Desktop graphic environment (as it is the environment itself) but i dont know how to find out the installed version.

dpkg -l gnome-desktop does not find anything.

how can i get over this condition ? gnome-desktop-2.0 >= 2.8
I saw gnome-desktop come with the release 2.18 . . . what should I aptitude install to meet this requirement?

many tnx AI, you r definitely my tutor... seem so . :D

best
[S>

---

### Post by Perfect Storm on 2007-05-07
Try with 
```
sudo aptitude install libgnome-desktop-dev
```

---

### Post by [SbReGo&gt; on 2007-05-07
yes, i got it (by myself) but you answer is correct! :D

now i have it up & running .. i am happy now! ;)

The problem was only to prepare the environment. asa I have it done with newer libs .. it compiled easily .. :D .. 
pretty cool!

what s next? :P
tnx AI for ur support! 

PS: maybe this is not the right place to ask for .. but .. when I start beryl .. the  frame of the windows disappear.. so i have to move them by pressing ALT+ mouse click .. any suggestion?

cheers!
[S>

---

### Post by Perfect Storm on 2007-05-08
> **'[SbReGo> said:**
> 
PS: maybe this is not the right place to ask for .. but .. when I start beryl .. the frame of the windows disappear.. so i have to move them by pressing ALT+ mouse click .. any suggestion?



```
sudo nvidia-xconfig --add-argb-glx-visuals
```

should do it (if you use nvidia card), then restart X (ctrl+alt+backspace)

---

### Post by [SbReGo&gt; on 2007-05-08
yes, i have nvidia card.. 
also this working! 

gr8
[S>

---

### Post by Bart Ellebaut on 2007-05-09
I've done all them codes to install the kiba dock, but I don't see anything.
I haven't downloaded any deb files because the top link is broken.
Do I have to download anything?
and what do you mean with: typ kiba-dock to run? type in terminal? I get command not found

thx

---

### Post by galileo99 on 2007-05-14
ive alien a rpm pakage of kiba dock. installation when fine, when i execute kiba-dock i get a blue oval on the screen. where do i get the correct plugins, i think i have the wrong ones... tks

---

### Post by TheRingmaster on 2007-05-15
I have installed all that was required and I just can't seem to get kiba-dock started. I installed it from the [kiba-dock wiki for ubuntu feisty]("http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock#Ubuntu"). This is what it says when I try to start kiba-dock from the terminal.

> $ kiba-dock
Illegal instruction (core dumped)
and this is what the terminal says if I try to open gset-kiba.
> $ gset-kiba
** Message: Failed to open Launcher Directory /home/jeffrey/.kiba-dock/launcher/
otification: Error opening directory '/home/jeffrey/.kiba-dock/launcher/': No such file or directory

*** glibc detected *** gset-kiba: double free or corruption (fasttop): 0x081b8b70 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73bf7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb73c2e30]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb74e6131]
gset-kiba(get_launcher_combobox+0xb5)[0x804d835]
gset-kiba(create_widgets+0x5bd)[0x804fe8d]
gset-kiba(main+0x1c5)[0x804cea5]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb736debc]
gset-kiba[0x804cb21]
======= Memory map: ========
08048000-08057000 r-xp 00000000 03:01 4129449    /usr/bin/gset-kiba
08057000-08058000 rw-p 0000e000 03:01 4129449    /usr/bin/gset-kiba
08058000-081c6000 rw-p 08058000 00:00 0          [heap]
b6b00000-b6b21000 rw-p b6b00000 00:00 0 
b6b21000-b6c00000 ---p b6b21000 00:00 0 
b6c0e000-b6c19000 r-xp 00000000 03:01 491584     /lib/libgcc_s.so.1
b6c19000-b6c1a000 rw-p 0000a000 03:01 491584     /lib/libgcc_s.so.1
b6c25000-b6ca2000 r--p 00000000 03:01 4359983    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6ca2000-b6ca4000 r-xp 00000000 03:01 4276316    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6ca4000-b6ca5000 rw-p 00001000 03:01 4276316    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6ca5000-b6cab000 r--s 00000000 03:01 5685327    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6cab000-b6cac000 r--s 00000000 03:01 5685355    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b6cac000-b6caf000 r--s 00000000 03:01 5685343    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b6caf000-b6cb0000 r--s 00000000 03:01 5685349    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b6cb0000-b6cb1000 r--s 00000000 03:01 5685330    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b6cb1000-b6cb5000 r--s 00000000 03:01 5685324    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6cb5000-b6cb6000 r--s 00000000 03:01 5685312    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6cb6000-b6cb8000 r--s 00000000 03:01 5685317    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b6cb8000-b6cba000 r--s 00000000 03:01 5685305    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b6cba000-b6cbb000 r--s 00000000 03:01 5685320    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b6cbb000-b6cbd000 r--s 00000000 03:01 5685328    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b6cbd000-b6cc3000 r--s 00000000 03:01 5685318    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6cc3000-b6cc5000 r--s 00000000 03:01 5685344    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6cc5000-b6cc7000 r--s 00000000 03:01 5685341    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b6cc7000-b6ccf000 r--s 00000000 03:01 5685347    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6ccf000-b6cd5000 r--s 00000000 03:01 5685301    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6cd5000-b6cd6000 r--s 00000000 03:01 5685310    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6cd6000-b6ced000 r--s 00000000 03:01 5685322    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b6ced000-b6cef000 r--s 00000000 03:01 5685345    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6cef000-b6cf5000 r--s 00000000 03:01 5685339    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6cf5000-b6cf8000 r--s 00000000 03:01 5685316    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b6cf8000-b6cfc000 r--s 00000000 03:01 5685299    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6cfc000-b6cfe000 r--s 00000000 03:01 5685659    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6cfe000-b6cff000 r--s 00000000 03:01 5685353    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b6cff000-b6d00000 r--s 00000000 03:01 5685350    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b6d00000-b6d01000 r--s 00000000 03:01 5685335    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b6d01000-b6d02000 r--s 00000000 03:01 5685306    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b6d02000-b6d03000 r--s 00000000 03:01 5685714    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b6d03000-b6d06000 r--s 00000000 03:01 5685332    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b6d06000-b6d0b000 r--s 00000000 03:01 5685713    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b6d0b000-b6d0d000 r--s 00000000 03:01 5685298    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b6d0d000-b6d0e000 r--s 00000000 03:01 5685351    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b6d0e000-b6d10000 r--s 00000000 03:01 5685303    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b6d10000-b6d11000 r--s 00000000 03:01 5685329    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b6d11000-b6d16000 r--s 00000000 03:01 5685323    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b6d16000-b6d1a000 r--s 00000000 03:01 5685300    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b6d1a000-b6d1c000 r--s 00000000 03:01 5685321    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b6d1c000-b6d1f000 r--s 00000000 03:01 5685313    /var/cache/fontconfig/61c830dfac3fd78a12Aborted (core dumped)


---

### Post by Izobalax on 2007-05-15
> **TheRingmaster said:**
> I have installed all that was required and I just can't seem to get kiba-dock started. I installed it from the kiba-dock wiki for ubuntu feisty. This is what it says when I try to start kiba-dock from the terminal.
I'm getting ***exactly*** the same here. 

/izo

---

### Post by TheRingmaster on 2007-05-15
> **Izobalax said:**
> I'm getting ***exactly*** the same here. 

/izo
anyone know what the problem is here??

---

### Post by TheRingmaster on 2007-05-16
bump

---

### Post by TheRingmaster on 2007-05-17
*bump*

---

### Post by fakie_flip on 2007-05-17
Is anyone ever going to create a deb for kiba-dock?

---

### Post by amadeus266 on 2007-05-20
Has anyone else had kiba-dock running and noticed cpu usage running at a constant 50-70 percent?

---

### Post by GabrielaG on 2007-05-20
The Kiba-dock web page is been updated, you can found instructions and how to install there, look at the wiki:

[http://www.kiba-dock.org/]("http://www.kiba-dock.org/")

---

### Post by Znupi on 2007-05-26
I tried installing kiba-dock but failed when ./autogen.sh-ing kibadock. This is the error:
```

checking for GNOME_DESKTOP... configure: error: Package requirements (gnome-desktop-2.0 >= 2.8) were not met:

```
(Feisty Fawn user here). Anyway, I've abandoned the idea of kiba-dock, and want to remove it. But, I've gotten to compile akamaru. Can I shift-delete everything or did it install things outside it's directory?

---

### Post by marq on 2007-05-30
i cant seem to get it to work

:~/kiba-dock/kibadock$ ./autogen.sh
bash: ./autogen.sh: No such file or directory

i dont know what im doing wrong it's exactly copy and pasted, 
it's probly really dumb but i just dont get it

---

### Post by cenora on 2007-05-30
Do we have to mkdir in a special location ??

cenora@USB-Ubuntu:/usr/share/kiba-dock/kibadock$ sudo ./autogen.sh 
sudo: ./autogen.sh: command not found
cenora@USB-Ubuntu:/usr/share/kiba-dock/kibadock$

---

### Post by cenora on 2007-05-30
Oops!

Sorry for last post. The complete instalation instruction is at the website:
[http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock)

With THIS installation procedure, the thing WORKS !!!:p

Regards,

---

### Post by shawndw on 2007-06-01
when i try the following command
```

./autogen.sh

```
i get an error message that says
```

checking for intltool...
***Error***: You must have intltool installed to compile akamaru

```
am i doing something wrong

---

### Post by mich83 on 2007-06-01
> **shawndw said:**
> when i try the following command
```

./autogen.sh

```
i get an error message that says
```

checking for intltool...
***Error***: You must have intltool installed to compile akamaru

```
am i doing something wrong


sudo aptitude install intltool

---

### Post by Mardok45 on 2007-06-05
> **flapane said:**
> 64bit version [http://www.dpb.org.uk/ubuntu/edgy_6.10/kiba-dock_0.1.0-1_amd64.deb](http://www.dpb.org.uk/ubuntu/edgy_6.10/kiba-dock_0.1.0-1_amd64.deb)

Thank you for uploading that package, but I got a problem:

When I try to run it by typing kaiba-dock in the terminal, it just sits there doing nothing.  I'm running Beryl too if that has anything to do with it.

EDIT: Okay, after logging off and back on, now it just returns "command not found".

---

### Post by TheRingmaster on 2007-06-05
> **Mardok45 said:**
> Thank you for uploading that package, but I got a problem:

When I try to run it by typing kaiba-dock in the terminal, it just sits there doing nothing.  I'm running Beryl too if that has anything to do with it.

EDIT: Okay, after logging off and back on, now it just returns "command not found".
make sure you are spelling it right. It is "kiba-dock" not "kaiba-dock".

---

### Post by Mardok45 on 2007-06-06
> **TheRingmaster said:**
> make sure you are spelling it right. It is "kiba-dock" not "kaiba-dock".

Woops, that was a typo on just this post, I know I typed kiba-dock in the terminal.

---

### Post by wataboutbob on 2007-06-08
strange... sudo aptitude couldn't find any packages when I search for "kiba" despite adding the source to the repo. Is the repo broken again?

---

### Post by qwertydimasol on 2007-06-08
Hello im totaly new to Linux and have no ideo whats were :) 
i tryed to install dock but i get this message after i type ./autogen.sh


checking for intltool...
***Error***: You must have intltool installed to compile akamaru

Any help :confused: Were can i get this initool thing :)

---

### Post by WaeV on 2007-06-08
try a sudo apt-get install (program)

except without parentheses

---

### Post by Alucard-sama on 2007-06-10
whenever i try to run the autogen script for kibadock it tells me i havnt got gnome-desktop-2.0 installed
i tried installing this package and i can't
any help?

---

### Post by shazm on 2007-06-11
hmmm
I get this error


checking for intltool...
***Error***: You must have intltool installed to compile akamaru

---

### Post by dannymichel on 2007-06-11
[FONT="Trebuchet MS"][SIZE="3"]I'm so sorry if I'm not following, but I found this kiba-dock 64 bit .deb for my 64bit OS and ran it, I types "kiba-dock" in the terminal to run it and nothing is happening.
Can someone **PLEASE** tell me how to install and run this on a 64 bit Ubuntu OS with Beryl installed?[/SIZE][/FONT]

---

### Post by dannymichel on 2007-06-12
The icons aren't crisp.
Is this how kiba-dock is supposed to look?

---

### Post by H.E. Pennypacker on 2007-06-13
Straight from Kiba-dock's website:

```

   1.  Open a Terminal Window.
   2. Type the following:

# sudo gedit /etc/apt/sources.list

   1. If you are using Edgy (6.10) version: Add the following lines to the end of the file:

deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn

   1. If you are using Feisty (7.04) version: Add the following lines to the end of the file:

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

   1. Save and Exit Gedit.
   2. Run from the same terminal window:

# wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
# sudo apt-get update
# sudo apt-get install kiba-dock
# sudo apt-get install kiba-dock-dev
# sudo apt-get install kiba-plugins


```

---

### Post by dannymichel on 2007-06-13
How do I get these icons to be crisp?

---

### Post by bertlacy on 2007-06-13
Question...

Do you have to have Beryl up and running to use kiba-dock?

---

### Post by Irti on 2007-06-14
checking for GTK... yes
checking for GNOME_DESKTOP... configure: error: Package requirements ( gnome-desktop-2.0 >= 2.8 ) were not met:

No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_DESKTOP_CFLAGS
and GNOME_DESKTOP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


i tried searching for gnome-desktop-2.0 everywhere.........no luck.......where to get it from.......????????

---

### Post by shazm on 2007-06-14
i do not know what "Build each in turn:" means

---

### Post by dannymichel on 2007-06-14
What's up with the fact that my icons are not as crisp as AWN icons?

---

### Post by Spike-X on 2007-06-17
When trying to build kiba-plugins:

```
launcher.c: In function 'kiba_launcher_set_object_surface':
launcher.c:452: error: 'KibaObject' has no member named 'bg_svg_handle'
launcher.c:452: error: 'KibaLauncherIcon' has no member named 'bg_svg_handle'
launcher.c:453: error: 'KibaObject' has no member named 'fg_svg_handle'
launcher.c:453: error: 'KibaLauncherIcon' has no member named 'fg_svg_handle'
make[3]: *** [launcher.lo] Error 1
make[3]: Leaving directory `/home/spike-x/kiba-plugins/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/spike-x/kiba-plugins/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/spike-x/kiba-plugins'
make: *** [all] Error 2

```

Gah!

---

### Post by hardyn on 2007-06-17
> **dannymichel said:**
> What's up with the fact that my icons are not as crisp as AWN icons?

they are probably being scaled up... you likely need larger icons to defeat the fussiness.

---

### Post by arashiko28 on 2007-06-17
Thanks a lot, this was the easiest of all instructions to install kiba-dock, how ever, after i installed it, the screen turned black and i couldn't see my documents, until i quited the program.... please help!!!!:confused: i'm learning to use ubuntu and all that implies linux alone](*,)](*,)](*,)

---

### Post by arsenic23 on 2007-06-17
*( If someone already said this then let me apologize for being redundant. )*

Just a heads up, if your using the Beryl in the official repositories then you may want to avoid updating Beryl from the repos listed in this thread.  I used the Beryl out of this repo:
> deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

and found it to be a fair bit more buggy then the one in the official repository, specifically when manually resizing windows.  In the long run I ended up commenting out the above, and removing and reinstall Beryl and the two lib files it uses as well as its configuration directory.

*Your milage may vary of course.

---

### Post by Confusedalot on 2007-06-21
um whats this mean? after i put
./autogen.sh
i get
checking for intltool...
***Error***: You must have intltool installed to compile akamaru
Where do i get intltool from

---

### Post by d_xtremw on 2007-06-27
i got that same error. go to package master and install the intltool package.

Now I got a new problem.. 1st the ./autogen.sh file isnt being found in the kibadock folder. i had to go look for it in another folder called trunks. and after i found it. the make command wuldnt run:S:S

---

### Post by t3soro on 2007-06-28
> **Confusedalot said:**
> um whats this mean? after i put
./autogen.sh
i get
checking for intltool...
***Error***: You must have intltool installed to compile akamaru
Where do i get intltool from

sudo apt-get install intltool

---

### Post by CLI-Linux on 2007-06-28
```

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.in: 28: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: aclocal failed with exit status: 1

```

I got this far.  Anybody care to take a guess?

---

### Post by waggygee on 2007-07-07
I am trying to get Kiba-dock. But I get this along the way

georg@georg-desktop:~/kiba-dock/kibaplugins$ ./autogen.sh
bash: ./autogen.sh: No such file or directory
georg@georg-desktop:~/kiba-dock/kibaplugins$ 

What should I do?

---

### Post by $teF on 2007-07-11
> **CLI-Linux said:**
> ```

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.in: 28: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: aclocal failed with exit status: 1

```

I got this far.  Anybody care to take a guess?

I seem to have the same problem!

---

### Post by nerdmods on 2007-07-12
I know everyone has been having issues getting this installed and running, after trying all the steps in here, and the kiba-dock wiki I decided to uninstall everything via synaptic package manager, then install kiba-dock from there, worked like a charm. Everything is up and running fine. No worries, just added the Startup item of kiba-dock and everything loads. :) Thanks to everyone for putting me on the right track though.

---

### Post by mitch0319 on 2007-07-14
I don't know if anybody else had that but the folder kibadock does not contain the autogen.sh file... need some help with that if possible
thank you

---

### Post by jimminy_kriket on 2007-07-14
I have the same problem, its in the trunk folder, at least one is in there, not sure if its the proper one. I couldnt get it to work anyways.

"May Currently Be Broken" i guess...

---

### Post by ziofil on 2007-07-15
> **nerdmods said:**
> I know everyone has been having issues getting this installed and running, after trying all the steps in here, and the kiba-dock wiki I decided to uninstall everything via synaptic package manager, then install kiba-dock from there, worked like a charm. Everything is up and running fine. No worries, just added the Startup item of kiba-dock and everything loads. :) Thanks to everyone for putting me on the right track though.

I couldn't find the package using synaptics... How did you find it?

---

### Post by ziofil on 2007-07-16
Done, I added trevino's repos. Akamaru works quite bad, though... Very slow...

---

### Post by Oldbones on 2007-07-17
```

cd akamaru/
./autogen.sh
make
sudo checkinstall
cd ../kibadock/
./autogen.sh
make
sudo checkinstall
cd ../kibaplugins/
./autogen.sh
make
sudo checkinstall
cd ../gsetkiba/
./autogen.sh
make
sudo checkinstall
```


Everything was working fine for the first directory.  Then, when going to the next directory
**./autogen.sh** command gave this error

oldbones@ChumBucket:~/kiba-dock/kibadock$ ./autogen.sh
bash: ./autogen.sh: No such file or directory

I assume I deleted it because it worked perfectly when going through the initial steps of the kiba doc code.  but how?

BTW, I love my system.   thanks for your time.

---

### Post by elixirofLIFE on 2007-07-19
omega@ubuntu:~/kiba-dock/akamaru$ cd
omega@ubuntu:~$ intltool
bash: intltool: command not found




I got errs. Any one help :((

---

### Post by sc0rn77 on 2007-07-22
i think kiba-dock was removed from those webpages (u can find the on kiba-dock official webpage) and thats why they cant be found on the synaptic or through sudo apt-get install kiba-dock. Anyone have any other ideas?

---

### Post by Myzrael on 2007-07-24
I have one problem. FIxed must depency problems but I have a new one now. 

checking for GNOME_DESKTOP... configure: error: Package requirements (gnome-desktop-2.0 >= 2.8) were not met:

No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_DESKTOP_CFLAGS
and GNOME_DESKTOP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.




How to fix that one? I'm running Ubuntu Feisty 64bit with GNOME.

---

### Post by Depressed Man on 2007-07-25
sudo apt-get install libgnome-desktop-dev

For the gnome-desktop 2.0

---

### Post by Arasa on 2007-07-26
I had kiba dock working fine, then I installed compiz fusion via trevinos repository. I can see he had some kiba stuff in there which I used to update mine. During that sessionI had the dock working fine. Reboot and its gone. I click to start and it doesn't appear. I can see it the process manager but not on the screen. :confused:

So, do I need to start off compiz fusion first, then start kiba? Or is there something else I'm missing? Someone said about updating libraries as 3v1's are not the latest? Or just use the .deb in page 20 of this thread?

Anyone else using compiz fusion wanna post how they got it all working together please.

---

### Post by Depressed Man on 2007-07-26
I use to use 3v1's but I don't think they've been updated in a while. Couldn't build it either, but where is this .deb your talking about?

---

### Post by pnoque on 2007-07-27
I got this:

> checking for GSET_KIBA... configure: error: Package requirements ("akamaru >= 0.1 kiba-dock >= 0.1") were not met:

No package 'akamaru' found
No package 'kiba-dock' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GSET_KIBA_CFLAGS
and GSET_KIBA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

pnoque@nixlinuxbox:~/kiba-dock/gsetkiba$ make
make: *** No targets specified and no makefile found.  Stop.


Any ideas?

---

### Post by Yagran on 2007-07-27
> **Oldbones said:**
> ```

cd akamaru/
./autogen.sh
make
sudo checkinstall
cd ../kibadock/
./autogen.sh
make
sudo checkinstall
cd ../kibaplugins/
./autogen.sh
make
sudo checkinstall
cd ../gsetkiba/
./autogen.sh
make
sudo checkinstall
```


Everything was working fine for the first directory.  Then, when going to the next directory
**./autogen.sh** command gave this error

oldbones@ChumBucket:~/kiba-dock/kibadock$ ./autogen.sh
bash: ./autogen.sh: No such file or directory

I assume I deleted it because it worked perfectly when going through the initial steps of the kiba doc code.  but how?

BTW, I love my system.   thanks for your time.

I also had this problem but its a simple fix. obviously the dir structure has changed slightly since this was written. use these commands instead:

```

cd akamaru/
./autogen.sh
make

cd ../kibadock/trunk/
./autogen.sh
make

cd ../kibaplugins/trunk/
./autogen.sh
make

cd ../gsetkiba/
./autogen.sh
make

```

hope that helps!

---

### Post by Depressed Man on 2007-07-27
Anyone know how to remove kiba -dock completly? I tried to install the SVN with the help of a script which ended in a horrible horrible accident. Now I can't remove it with the script (it thinks the SVN file isn't there) but when I try to install it (it says it already exists) and I already deleted the SVN folders.

I'm thinking I need to delete all traces of it. Does anyone know how to do it?

---

### Post by borimrr on 2007-07-28
> **H.E. Pennypacker said:**
> Straight from Kiba-dock's website:

```

   1.  Open a Terminal Window.
   2. Type the following:

# sudo gedit /etc/apt/sources.list

   1. If you are using Edgy (6.10) version: Add the following lines to the end of the file:

deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn

   1. If you are using Feisty (7.04) version: Add the following lines to the end of the file:

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

   1. Save and Exit Gedit.
   2. Run from the same terminal window:

# wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
# sudo apt-get update
# sudo apt-get install kiba-dock
# sudo apt-get install kiba-dock-dev
# sudo apt-get install kiba-plugins


```

After I do this I run it and it gives me an error: ```
kiba-dock
Error: Unable to open dir /home/marcos/.kiba-dock/config_schemas
notifications: Error opening directory '/home/marcos/.kiba-dock/config_schemas'
No such file or directory
```
It gives me a plain black bar on the bottom that is 3-4 times taller than it should be. When I do sudo kiba-dock the bar is at normal size but plain black. I went to the folder and all I see is a "config" file but no "config_schemas" any ideas what might be wrong?

---

### Post by Depressed Man on 2007-07-28
The black bar is caused by not running a Windows manager like Beryl, Compiz, or Compiz Fusion. Though there's one you can run that provides the basic requirement without the fanciness of the ones I listed (but I don't know it's name).

---

### Post by andrewsomething on 2007-07-29
> **Depressed Man said:**
> Anyone know how to remove kiba -dock completly? I tried to install the SVN with the help of a script which ended in a horrible horrible accident. Now I can't remove it with the script (it thinks the SVN file isn't there) but when I try to install it (it says it already exists) and I already deleted the SVN folders.

I'm thinking I need to delete all traces of it. Does anyone know how to do it?

Are you saying you compiled it from source and then deleted the source file? It's unclear what you did. Maybe post a link to the directions you followed....

---

### Post by jcrnan on 2007-07-29
Does this actually work? I'm using Feisty Fawn with Gnome, an Intel gfx and Compiz Fusion.

---

### Post by Arasa on 2007-07-30
Quote:
Originally Posted by H.E. Pennypacker  
Straight from Kiba-dock's website:


Code:
   1.  Open a Terminal Window.
   2. Type the following:

# sudo gedit /etc/apt/sources.list

   1. If you are using Edgy (6.10) version: Add the following lines to the end of the file:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

   1. If you are using Feisty (7.04) version: Add the following lines to the end of the file:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

   1. Save and Exit Gedit.
   2. Run from the same terminal window:

# wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
# sudo apt-get update
# sudo apt-get install kiba-dock
# sudo apt-get install kiba-dock-dev
# sudo apt-get install kiba-plugins 

After I do this I run it and it gives me an error: 
Code:
kiba-dock
Error: Unable to open dir /home/marcos/.kiba-dock/config_schemas
notifications: Error opening directory '/home/marcos/.kiba-dock/config_schemas'
No such file or directoryIt gives me a plain black bar on the bottom that is 3-4 times taller than it should be. When I do sudo kiba-dock the bar is at normal size but plain black. I went to the folder and all I see is a "config" file but no "config_schemas" any ideas what might be wrong?



I get the exact same error. It was working fine before I put compiz fusion on, this is clearly related. 

Does anyone have a fix or a sure fire way of getting the latest kiba-dock on compiz fusion?

---

### Post by mont on 2007-07-30
download the svn from sourceforge, its working!

---

### Post by Depressed Man on 2007-07-30
> **andrewsomething said:**
> Are you saying you compiled it from source and then deleted the source file? It's unclear what you did. Maybe post a link to the directions you followed....

I used the EasyKiba script that was on the forums. It downloads the SVNs and automates the process of ./autogen.sh, make, and sudo make install. 

It errored out but it seemed to leave Kiba in a somewhat working condition. But I wanted to redo it. So I deleted the SVN files and tried to use the script to install again. However it reports the SVN is still installed and to use update. So I tried update and it says it can't find the files. And I can't remove it with the script too since it doesn't report it's existence. But Kiba dock has to be installed somewhere since I can use it.

So I'm just trying to remove all traces of Kiba Dock and manually installing it from the new SVN location at sourceforge. But I don't know where all the Kiba dock files are.

Edit: Here's the link to the instructions (well script I used). [http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=274.0](http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=274.0)

---

### Post by mikibg on 2007-07-31
[[IMG]http://img295.imageshack.us/img295/8792/screenshot1kj1.th.png[/IMG]](http://img295.imageshack.us/my.php?image=screenshot1kj1.png)

---

### Post by keenish27 on 2007-07-31
> **Arasa said:**
> Quote:
Originally Posted by H.E. Pennypacker  
Straight from Kiba-dock's website:


Code:
   1.  Open a Terminal Window.
   2. Type the following:

# sudo gedit /etc/apt/sources.list

   1. If you are using Edgy (6.10) version: Add the following lines to the end of the file:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

   1. If you are using Feisty (7.04) version: Add the following lines to the end of the file:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

   1. Save and Exit Gedit.
   2. Run from the same terminal window:

# wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
# sudo apt-get update
# sudo apt-get install kiba-dock
# sudo apt-get install kiba-dock-dev
# sudo apt-get install kiba-plugins 

After I do this I run it and it gives me an error: 
Code:
kiba-dock
Error: Unable to open dir /home/marcos/.kiba-dock/config_schemas
notifications: Error opening directory '/home/marcos/.kiba-dock/config_schemas'
No such file or directoryIt gives me a plain black bar on the bottom that is 3-4 times taller than it should be. When I do sudo kiba-dock the bar is at normal size but plain black. I went to the folder and all I see is a "config" file but no "config_schemas" any ideas what might be wrong?



I get the exact same error. It was working fine before I put compiz fusion on, this is clearly related. 

Does anyone have a fix or a sure fire way of getting the latest kiba-dock on compiz fusion?

I did this and this is the error i get

Error: Unable to open dir /home/keen/.kiba-dock/config_schemas
notifications: Error opening directory '/home/keen/.kiba-dock/config_schemas': No such file or directory
Error (plugin.c @ line 670):
        '/usr/lib/kiba-dock/liblauncher.so' is not loadable
Segmentation fault (core dumped)


any ideas?

---

### Post by WIGGMPk on 2007-07-31
> **keenish27 said:**
> I did this and this is the error i get

Error: Unable to open dir /home/keen/.kiba-dock/config_schemas
notifications: Error opening directory '/home/keen/.kiba-dock/config_schemas': No such file or directory
Error (plugin.c @ line 670):
        '/usr/lib/kiba-dock/liblauncher.so' is not loadable
Segmentation fault (core dumped)


any ideas?

Try creating the folder its asking for:


mkdir ~/.kiba-dock/config_schemas


If it yells at you, then try just:

mkdir ~/.kiba-dock

First then:

mkdir ~/.kiba-dock/config_schemas




Hope this helps. I believe Seg Faults are casued when its trying to write outside of its assigned place or something in that nature lol..

---

### Post by keenish27 on 2007-07-31
thanks!  worked like a charm!  kiba dock is running perfectly now

---

### Post by keenish27 on 2007-07-31
well, it works as long as i keep the terminal open, is there way to have this run without keeping the terminal open?

---

### Post by keenish27 on 2007-07-31
ok, well i have it running now, but i may be a bit slow here.  how do i add launchers to it...i want ot add firefox but i don't know how

EDIT: i have it on the dock now...dunno how i did, but i did

---

### Post by fotakis on 2007-07-31
Hello keenish27, when you say it works like a charm, is it working smoothly? And are you using compiz-fussion debs from the tuxfamily repos?

I can't get it work so I would like some input

Best Regards,
Fotis

---

### Post by keenish27 on 2007-07-31
fotakis,

when i said works like a charm i mean its running smooth and perfect.

as for what repos i'm using, i honestly have no idea.  i'm very new to linux (second day) and i just followed this guide to get ubuntu running

[http://ubuntuforums.org/showthread.php?t=399913&highlight=dell+6400](http://ubuntuforums.org/showthread.php?t=399913&highlight=dell+6400)

when i was finished i already had beryl installed and went from there.  i hope this helps you.

---

### Post by WIGGMPk on 2007-08-01
> **keenish27 said:**
> well, it works as long as i keep the terminal open, is there way to have this run without keeping the terminal open?

Yes, you can set your session to automatically run it when GNOME starts.

Here's how:

System > Preferences > Sessions:

Startup Programs Tab:

New > Name: Kiba-Dock > Command: kiba-dock

Click Ok, Session Options tab > Save Current Session.


Hope that helps.

Fotakis, there is a wiki that might able to help you. If your running on amd64 you'll have to use the SVN.

[http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock)

---

### Post by fotakis on 2007-08-01
Hello WGGMK,

I followed that guide but the dock is way too buggy, it gets stuck alot, and akamaru is just not working. 

I gave the the debs from kiba-dock.org a try and the same, I compiled my own and the same, so I assumed that its compiz-fussion's fault instead. I will just have to wait for newer releases on the repos.

Best Regards,
Fotis

BTW My Specs-
Feisty 32-bit
GeForce 7600 GT  Using 1.0-9755 drivers

---

### Post by AyuReady1989 on 2007-08-01
I REALY REALLY REALLY NEED SOMEONES HELP thanks in advanced my kiba-dock is sooo slow i cant click anything when the icons are moving this happens when i enable physics

---

### Post by rne1223 on 2007-08-02
Hi...I'm kinda new to Festy (linux in general) and I was wandering how can I install intltool because it is giving me this error when I'm trying to ./autogen.sh:

checking for intltool...
***Error***: You must have intltool installed to compile akamaru

Could some please help me. Thanks

---

### Post by Arasa on 2007-08-02
I have been trying like crazy to get kiba to work on compiz fusion to no avail.. Used keen's approach, made the dir, and nothing, I mean nothing happens..

All I can say is switch to AWN, far more stable, less resource hungry and is actually better looking, just lacking physics engine, but who cares when it works..

AWN is the way to go.

---

### Post by vexorian on 2007-08-03
Hey, I actually saw the title of this thread and instead of trying the method described I just looked through synaptic if there was a package and there was, although it could be one of the repositories I added.

I tried it and I like it better than AWN, its clock is better it got a very cool show desktop button with that it tops AWN in functionality by ages (IMHO)

Regarding compiz fusion, I didn't really get any issues, so I am not sure what's the problem.

---

### Post by Kabezon on 2007-08-05
Well, I installed, first time I ran it with alt+f2, but nothing happened. Then, I tried oppening it from Applications>Accessories>Kiba-Dock and nothing happened. Finally, I tried from terminal  but I get this error:

> Error (dialog.c @ line 209):
        Failed to load Plugins from /usr/local/lib/kiba-dock!
Please install the Plugins and Kiba under the same Prefix
FATAL (main.c @ line 1270):
        Failed to load Plugins


OK , no big deal, just  sudo apt-get install kiba-plugins, right? well, I get this error when I do so:

> E: Couldn't find package kiba-plugins

OK... so I open the Synaptic Package Manager and search of Kiba, NOTHING! ZERO! How can this be? o.o  My repos seem to be OK also so... I'm out of ideas... So what can I do? Is there anotherway to install the plugins? I don't think so o.O 

PS: If I'm doing anything noobish, forgive me, I am a noob, just 2 weeks using Linux ^^

---

### Post by Jak08 on 2007-08-05
Well I did the synaptic seach and got it, it might be that it is from the eyecandy repository though.

I don't think I like it as well as AWN though, it is a bit of a resource hog, and it was a little buggy from the few minutes I played with it.

---

### Post by vexorian on 2007-08-05
> OK... so I open the Synaptic Package Manager and search of Kiba, NOTHING! ZERO! How can this be? o.o My repos seem to be OK also so... I'm out of ideas... So what can I do? Is there anotherway to install the plugins? I don't think so o.O

PS: If I'm doing anything noobish, forgive me, I am a noob, just 2 weeks using Linux ^^
__________________

I guess it is no coincidence that Jak08 could do and he also knew of AWN, it seems that I got Kiba-dock from Treviño's SVN repositories.

---

### Post by Jak08 on 2007-08-05
I suppose I might as well just give you the shortcut to get that repository, I am borrowing from Vorian's post in the How To: Compiz Fusion on Ubuntu 7.04

First type this into the terminal
```
sudo gedit /etc/apt/sources.list
```

And then add this at the bottom of the list
     for i386
```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

    for amd64
```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
```

Add the key 
```
gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add -
```

Update your system
```
sudo apt-get update
sudo apt-get upgrade
```

There shameful copying over. Now search synaptic again and see if anything new pops up for you. :)

---

### Post by santiagoward2000 on 2007-08-05
Hi everyone, I've been playing winth kiba for some time, and have a few questions.
1) I'm a xubuntu user, is there any way to activate the menu and trash plugins in kiba using xfce?
2) All my icons disappear when I turn physics on, does anyone know why?
Thanks!

---

### Post by Kabezon on 2007-08-05
I hate the repositories, No idea what could've gone wrong :S

---

### Post by santiagoward2000 on 2007-08-20
> **santiagoward2000 said:**
> 2) All my icons disappear when I turn physics on, does anyone know why?

Hey, I get to make this work (sorta...) It seems I have to set all options to default before starting kiba. Then I can fool around with physics with no problem.
Any way, this is kind of annoying, can anyone help me with this problem?
Thanks!

---

### Post by squidmaster on 2007-09-01
been trying like crazy to make this work in 7.04 but one of the kiba SVN is down.

---

### Post by Perfect Storm on 2007-09-02
If you don't mind not getting  the latest of the latest (development release that is).

You can use this:

#### Kiba Dock #### 
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy 
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

---

### Post by Depressed Man on 2007-09-03
> **squidmaster said:**
> been trying like crazy to make this work in 7.04 but one of the kiba SVN is down.

You sure your getting it from sourceforge right? They have a new SVN location. I don't know how far back Trevino's repos actually is though...

---

### Post by boob11 on 2007-09-03
Thnax

---

### Post by dmitryf on 2007-09-06
Where i can find amd64 package?

---

### Post by linuxisgod on 2007-09-17
ok im am sooo ******* lost can some 1 type up an exact way step by step on how to get it to work the write way

---

### Post by mattgaunt on 2007-09-19
Heres my little how to that got everything working for me

[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

---

### Post by liamwithers on 2007-09-21
It all works perfectly apart from i get a black bit above the dock! How do I remove this? I don't think my pc will run Compiz. Can I still remove it?

---

### Post by 127.0.0.1 on 2007-09-25
the kiba-dock new svn is:
 [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk) kiba

hope i helped! :)

---

### Post by ralvynl on 2007-10-01
> It all works perfectly apart from i get a black bit above the dock! How do I remove this? I don't think my pc will run Compiz. Can I still remove it?

Same Problem here, any ideas?

---

### Post by distroman on 2007-10-01
> **ralvynl said:**
> Same Problem here, any ideas?
Maybe xcompmgr wil do the trick, not sure, you tell me, just remember reading about it. ;-)
[http://ubuntuforums.org/showthread.php?t=506803&highlight=xcompmgr+kiba](http://ubuntuforums.org/showthread.php?t=506803&highlight=xcompmgr+kiba)

---

### Post by Gourgi on 2007-10-10
> **mattgaunt said:**
> Heres my little how to that got everything working for me

[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

it worked , thanks

---

### Post by mattgaunt on 2007-10-18
no probs gourgi

---

### Post by messiah89 on 2007-10-20
so i kiba works perfect but its set to appear below stuff but it still appears ontop of everything except fullscreen apps, can i fix this?

---

### Post by B3n3v3nt3 on 2007-10-21
I've just installed it and runs perfectly, the thing is, I wanted to add the trash icon into it and I don't know how. I've enabled the Trash Icon in the settings but it doesn't appear. Any help would be much appreciated.

---

### Post by mattgaunt on 2007-10-22
B3n3v3nt3 - I have found that with kiba-dock and many other dock programs that the applets aren't focused anywhere near as much as the dock itself and i have tried kiba-dock and avant - window - navigator and both have had their own issues

So unfortunately its all trial and error and deciding which one you like best or whether u want it at all

Matt

---

### Post by luedi on 2007-10-25
hello people,

i also installed kiba-dock.
after some trouble because of differnet config / plugin paths i finally got it to run.
now i start the dock with this line:

 kiba-dock --config-file '/home/max/kiba-dock/kiba-dock/config.h' --plugin-path '/home/max/kiba-dock/kiba-plugins'

now there's a blue transparent triangle at the bottom edge. physics cannot be activated.
icons be dropped an the dock but don't appear on it.

here's the command prompt log:
```
root@laptop-max:~/kiba-dock/kiba-dock# kiba-dock --config-file '/home/max/kiba-dock/kiba-dock/config.h' --plugin-path '/home/max/kiba-dock/kiba-plugins' --verbose
Info Message (main.c @ line 1121):
        Kiba was build with Akamaru support

Info Message (main.c @ line 1128):
        Kiba was build with SVG support

Info Message (main.c @ line 1138):
        Kiba was build without GLITZ support

Info Message (main.c @ line 1154):
        Kiba was build without SDL support

Misc Message (main.c @ line 1167):
        Initiall RSVG Library

Info Message (main.c @ line 1006):
        Kiba Window was created

Info Message (main.c @ line 1008):
        Kiba Dock was created

Misc Message (main.c @ line 1223):
        Loading Plugins from /home/max/kiba-dock/kiba-plugins...

Misc Message (main.c @ line 1237):
        Plugins loaded


```]

please, does anyone know whats going on??

thanks

---

### Post by luedi on 2007-10-26
well... it works now!

i uninstalled the whole thing and reinstalled it in the standard directory.
no it runs fine and without path modifiers.

thanks anyway.

---

### Post by boast on 2007-12-13
> **Lopsicle said:**
> Thanks PriceChild & Ayoli, but finally figured it out how to get it working (well sort of) ;) just me being impatient again :mrgreen:

how?

---

### Post by UrBaNAcID on 2008-01-07
I know i should read the whole thread but i didnt feel like reading 38 pages of comments ... My Kiba dock was working perfectly for about a month and a half. Im not having any major issues but for some reason i am unable to add any new launchers to it.. It just stopped on its own .. Anyone else having this problem if so how can i resolve this because its driving me nuts.. Thanks

---

### Post by xjgnsdof on 2008-03-16
This works in Xubuntu 7.10. I have, however, had a problem with autohide. When the dock is in autohide mode and I close a window, the dock shuts down. I don't know if it's a problem on my end. Does anyone else have this problem?

EDIT: It was a problem on my end. In Xubuntu, there's an option to save the session for the next login. That is, everything that ran in the last session will run again. I also set kiba-dock to autostart. Thus, if I selected the option of saving the session for the next login, then kiba-dock would start once because of the session save and again because of my setting it to autostart. To remedy this, I just removed kiba-dock from autostarting, opting instead to just save my session for next login. This has fixed the problem above in Xubuntu 7.10.

---

### Post by shottie on 2008-03-16
Once Kiba and plugins are installed how would you make the icon move freely as in some of the videos?

---

### Post by CJay554 on 2008-04-09
a more recent rep of kiba-dock

[http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock#Dependencies](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock#Dependencies)

---

### Post by yoshimitsuspeed on 2008-04-10
If it helps I spent hours trying to get this to work on my 64 bit sys with no sucess. There is some trouble with the plugins. I found a workaround but didn't get it to work. 
I found a how to for Cairo dock and it took a matter of minutes and I love it. 
I would love to try kiba-dock at somepoint but if you are looking for something about as good and much easier check this out. 
[http://ph.ubuntuforums.com/showthread.php?t=613087](http://ph.ubuntuforums.com/showthread.php?t=613087)
I don't know if it's been mentioned here, I didn't get all the way through the thread.

---

### Post by mandriva9786 on 2008-06-13
I tryed KibaDock but it would not let me install the deb. it said to check the permissions and i did i should be able to open it but i cant.

---

### Post by coolediz on 2008-07-01
how i can close it?

---

