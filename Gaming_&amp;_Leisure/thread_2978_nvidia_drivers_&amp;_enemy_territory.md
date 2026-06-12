---
title: "nvidia drivers &amp; enemy territory"
date: 2004-11-02
forum: Gaming &amp; Leisure
---

### Post by thewax on 2004-11-02
hai,
im trying to get RTCW: Enemy Territory working on Ubuntu
since i'm pretty much a linux nYb i followed the instuctions found on
 [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)
 to install the nvidia drivers for my GF3 TI200.. (& im sure i didnt miss a step here)
afterwards, i installed ET..
now, when i try to run it, i get a black screen for a second, & after that i get my login screen again (same effect as when u press ctrl+alt+backspace)

does this mean that my x-server crashes? i do get the nvidia logo screen at startup, & all those 3D screensavers that came with ubuntu go very fluently

have no idea how to fix this :)
thx in advance

---

### Post by Dennis_k on 2004-11-02
I cant help you with ET, but i have a question.

How did you get the NVIDIA drivers to work?

I cant get them, even with sudo apt-get install nvidia-gfx

---

### Post by Enygma on 2004-11-02
To Dennis K

You need to do a little bit of configuration after you install the driver, I followed the instructions on this page and it worked out just fine.

[http://www.osnews.com/story.php?news_id=8407&page=4](http://www.osnews.com/story.php?news_id=8407&page=4)

---

### Post by rupert on 2004-11-02
i have the same problem, changing the resolution before starting the game helps for

---

### Post by im_ka on 2004-11-02
[QUOTE=thewax]
 i do get the nvidia logo screen at startup, & all those 3D screensavers that came with ubuntu go very fluently

have no idea how to fix this :)
thx in advance[/QUOTE]

then 3d acceleration probably works for you. try tuxracer for testing.

```
sudo apt-get install tuxracer
```

---

### Post by Dennis_k on 2004-11-02
[QUOTE=Enygma]To Dennis K

You need to do a little bit of configuration after you install the driver, I followed the instructions on this page and it worked out just fine.

[http://www.osnews.com/story.php?news_id=8407&page=4](http://www.osnews.com/story.php?news_id=8407&page=4)[/QUOTE]

Thats not the problem, the problem is getting the NVIDIA driver.

When i boot in rescuemode, you auto login as sudo / root.
When i give the sudo apt-get install nvidia-gfx i get an message saying that the nvidia driver is not found and a part of an other package.

---

### Post by thewax on 2004-11-02
[QUOTE=Dennis_k]Thats not the problem, the problem is getting the NVIDIA driver.

When i boot in rescuemode, you auto login as sudo / root.
When i give the sudo apt-get install nvidia-gfx i get an message saying that the nvidia driver is not found and a part of an other package.[/QUOTE]

yeah, first time i did "apt-get install nvidia-gfx" i got some error message too (not sure if it is the same though), try this:
first run "apt-get update"
then try again "apt-get install nvidia-gfx"

edit: oh & offc, if you cant use apt-get, you can always download the linux drivers manually at nvidia.com (altough i never managed to manually install them :x)

---

### Post by thewax on 2004-11-02
[QUOTE=im_ka]then 3d acceleration probably works for you. try tuxracer for testing.

```
sudo apt-get install tuxracer
```[/QUOTE]

this code doesnt work: says "couldnt find packet tuxracer" (or something like that, i have the dutch version :p)

---

### Post by thewax on 2004-11-02
[QUOTE=rupert]i have the same problem, changing the resolution before starting the game helps for[/QUOTE]

& this doesnt work either
i still return to the login screen

---

### Post by thewax on 2004-11-03
^^ up ^^

---

### Post by plasmo on 2004-11-03
probli your sources.list is still default
if u want to open up multiverse / universe
```
sudo gedit /etc/apt/sources.list
``` 
and uncomment the other links.

then do a 
```
sudo apt-get update
sudo apt-cache search nvidia
``` 

hope that helps  [-o<

---

### Post by ulrich on 2004-11-03
@thewax

please open a console and run 'et' from the console.
then post the output here.

optionally post the output of /var/log/XFree86.0.log

---

### Post by walking is still honest on 2004-11-19
i have the exact same problem, tried the drivers off of nvidia.com, still happens. 3d accel is definately there, it shows in stuff like chromium and xscreensaver. the x log just said that it quit cause it caught a signal 11. as for et, its really hard to see what the output is when the symptom is that you get a black screen, followed by x crashing. 

one thing i noticed is that rivafb is compiled in as a module, which can cause problems with the nvidia module. but as this is an 800mhz p3, a kernel recompile will be one of the last things i try ;-)

anyways, any help would be greatly appreciated.

---

### Post by walking is still honest on 2004-11-19
ok, i dist-upgraded to hoary, and then switched from xfree to xorg, and it seems to work fine now other then fscking up my resolution when i quit. i dont know if its a problem with a warty package, or xfree, or just the current planetary positions, but thats what i did and it works now.

---

### Post by thewax on 2004-11-23
[QUOTE=plasmo]probli your sources.list is still default
if u want to open up multiverse / universe
```
sudo gedit /etc/apt/sources.list
``` 
and uncomment the other links.

then do a 
```
sudo apt-get update
sudo apt-cache search nvidia
``` 

hope that helps  [-o<[/QUOTE]

i did this
(the following lines were uncommented: 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
)

now when i apt-cache search something i get:
W: could not find [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages (/var/lib/apt/li sts/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 unknown file / folder)
(translated to english, i have dutch ubuntu)

---

### Post by p!=f on 2004-11-23
[QUOTE=thewax]
now when i apt-cache search something i get:
W: could not find [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/universe Packages (/var/lib/apt/li sts/archive.ubuntu.com_ubuntu_dists_warty_universe_binary-i386_Packages) - stat (2 unknown file / folder)
[/QUOTE]
```

sudo apt-get update

```

---

### Post by thewax on 2004-11-23
[QUOTE=p!=f]```

sudo apt-get update

```[/QUOTE]

yeah :)
thx
solved it already, clicking the search button can help lots ;)
gonna update distro too, see if i can get et to work..

---

### Post by thewax on 2004-11-23
[QUOTE=walking is still honest]switched from xfree to xorg, and it seems to work fine now[/QUOTE]

upgraded dist too, how do i switch to xorg?

---

### Post by p!=f on 2004-11-23
[QUOTE=thewax]upgraded dist too, how do i switch to xorg?[/QUOTE]
If you upgraded from Warty to Hoary you already have xorg installed and running.
Try to run
```

 * 17:10:14 * pef @ agonicus *
[~] > dpkg -l xserver-xorg
ii  xserver-xorg             6.8.1-1ubuntu3           the X.Org X server

```

---

### Post by Grenshad on 2004-11-25
same problem for me :-(

---

### Post by Bitchcassidy on 2004-11-30
pour tux, tu dois rajouter les bonnes sources dans ton /etc/apt/sources.list

---

### Post by DDL on 2004-12-14
Hi,
I have experience the same problem using warty.
I solve this problem by removing nvidia drivers providing in warty deb package  and by installing the latest nvidia linux drivers found in nvidia website.

Don't forget to remove DRI and Glcore and add GLX in Xfree configuration file as explain in nvidia linux drivers documentation.
In order to perform nvidia linux drivers installation, the linux hearders for your current kernel and gcc debs need to be install first.
Regards,
DDL 8-) 

[QUOTE=thewax]hai,
im trying to get RTCW: Enemy Territory working on Ubuntu
since i'm pretty much a linux nYb i followed the instuctions found on
 [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)
 to install the nvidia drivers for my GF3 TI200.. (& im sure i didnt miss a step here)
afterwards, i installed ET..
now, when i try to run it, i get a black screen for a second, & after that i get my login screen again (same effect as when u press ctrl+alt+backspace)

does this mean that my x-server crashes? i do get the nvidia logo screen at startup, & all those 3D screensavers that came with ubuntu go very fluently

have no idea how to fix this :)
thx in advance[/QUOTE]

---

### Post by DDL on 2004-12-17
I like to understand why it didn't work using warty and ubuntu deb nvidia drivers.
So I have restart a fresh ubuntu warty install using the deb nvidia drivers.
I have reinstall enemy territory and I have start to play with the XF86Config-4 config file.

I have try few stuff, and finally I have found a solution.

My XF86Config-4 config file was initialy setup with the following lines.

SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

Whereas my desktop was setup to 1280x1024. 
And I have found the following line in the xfree log file:

(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200

By modifying the XF86Config-4 config file to:

SubSection "Display"
		Depth		24
		Modes	       "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

I disable the "1600x1200" virtual screen size and it now works using a fresh warty install without upgrading to hoary.
ET seems not working while using a virtual screen size higher than the deskstop screen size.

Someone to confirm ?

DDL  8-)

---

### Post by thewax on 2004-12-21
[QUOTE=DDL]I like to understand why it didn't work using warty and ubuntu deb nvidia drivers.
So I have restart a fresh ubuntu warty install using the deb nvidia drivers.
I have reinstall enemy territory and I have start to play with the XF86Config-4 config file.

I have try few stuff, and finally I have found a solution.

My XF86Config-4 config file was initialy setup with the following lines.

SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

Whereas my desktop was setup to 1280x1024. 
And I have found the following line in the xfree log file:

(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200

By modifying the XF86Config-4 config file to:

SubSection "Display"
		Depth		24
		Modes	       "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

I disable the "1600x1200" virtual screen size and it now works using a fresh warty install without upgrading to hoary.
ET seems not working while using a virtual screen size higher than the deskstop screen size.

Someone to confirm ?

DDL[/QUOTE]

GREAT!! you've fixed it!! thx alot man!! :-D
only thing that should be mentionned is that you need to run it as root (sudo et), otherwise you get some error "could not write to blabla"

you should add this solution to the ubuntu wiki :-D 

also, the frames per second difference between enemy territory on win2k and linux is HUGE :shock:
hurray for linux! (altho it can be a bitch sometimes :p)

---

### Post by nikopol on 2004-12-29
I've been wanting to install the new NVidia drivers but for some reason init 3 keeps X running. 

How am I supposed to install these drivers under Ubuntu (BTW it doesn't like init 1 either ;( )

---

### Post by TravisNewman on 2004-12-30
sudo /etc/init.d/gdm stop

that'll bring you to a pure command line

When you're done:
sudo /etc/init.d/gdm start

---

### Post by nikopol on 2004-12-30
[QUOTE=panickedthumb]sudo /etc/init.d/gdm stop

that'll bring you to a pure command line

When you're done:
sudo /etc/init.d/gdm start[/QUOTE]

Thanks mate  :D

---

### Post by TravisNewman on 2004-12-30
yelcome :)

---

### Post by nikopol on 2005-01-05
well I've got the video solved but I'm getting
/dev/dsp device does not exist 
though it does!

Any simple solution to this?

---

### Post by crane on 2005-01-05
[QUOTE=nikopol]well I've got the video solved but I'm getting
/dev/dsp device does not exist 
though it does!

Any simple solution to this?[/QUOTE]

Just wondering, is this an X error or Enemy Territory  error?

---

### Post by nikopol on 2005-01-06
I'm thinking it's more with the sound daemons used/required in Ubuntu. It seems like it doesn't like esd or something...

---

### Post by chascon on 2005-01-07
or a simplier solution rather than the drastic excersise of deleting gdm is simple to press cntrl-alt-F1 (any of F1-F6) to get to a console.  Log in, and from there do your thing.

Uninstalling GDM, is way to harsh.

---

### Post by nikopol on 2005-01-25
[QUOTE=chascon]or a simplier solution rather than the drastic excersise of deleting gdm is simple to press cntrl-alt-F1 (any of F1-F6) to get to a console.  Log in, and from there do your thing.

Uninstalling GDM, is way to harsh.[/QUOTE]
 I've updated to Hoary and the /deb/dsp problem has dissapeared. Not sure what went on there but it's working now...

---

### Post by fng on 2005-01-26
[QUOTE=DDL]ET seems not working while using a virtual screen size higher than the deskstop screen size.

Someone to confirm ?

DDL  8-)[/QUOTE]

Yep,  this solution worked when i helped a friend getting ET to work on nvidia.

---

### Post by DDL on 2005-01-27
Thx

---

### Post by theerga on 2005-05-24
I'm a pretty big noob but where is the file i need to edit to get it to run

---

### Post by appeltje on 2007-05-21
I got the same problem...I like what I see about the virtual screen but I cant seem to find the XF68Config-4 (or something like that) anywhere...pls help xD

EDIT: OW never mind, just found it at some wiki: [http://wiki.linuxquestions.org/wiki/XF86Config](http://wiki.linuxquestions.org/wiki/XF86Config) (although mine was called xorg.config)
(man never ending source of info xD)

---

