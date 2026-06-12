---
title: "Nostromos N52 Game Pad"
date: 2005-11-07
forum: Gaming &amp; Leisure
---

### Post by cydizen on 2005-11-07
Hey Gang, 

 Just curious if anyone has successfully got this device to work in breezy... by default the system see's it as another usb keyboard, however the power of the N52 is in being able to map the n52 outside of any given game (thus you need the special drivers). I have followed generic tutorials on the sourceforge project page, as well as a how-to for Hoary, neither proved fruitful.  Perhaps I missed something obvious.  Anyone conquer this?



Regards,
Bruce

---

### Post by cydizen on 2005-11-09
bump - No one has one of these magnificent peices of gaming hardware?

---

### Post by KingBahamut on 2005-11-09
No, actually I found a more aggreeable piece of equipment Cydizen. 

[http://www.thinkgeek.com/computing/input/7a67/](http://www.thinkgeek.com/computing/input/7a67/)

I had a Nostromo for a while, got it to meanily work , but wasnt pleased with it.

---

### Post by Deekin on 2005-11-09
I have a Nostromo (which i haven't tried under Linux yet) but man alive, that KB is awesome! I didn't like the looks of it at first but it grows on you quick once you see the key layouts. The design of it reminds me of the Enterprise's bridge for some reason.

there - this will be my official geeky post for the evening.

---

### Post by professor_chaos on 2005-11-09
I have the n52 nostomos and really like it. Worked with ubuntu out of the box. Gives great erogonomic wrist support and all the buttons are exactly within comfortable reach. The only thing is they only make it for the right handed people. Go get it, you won't regret it.

---

### Post by cydizen on 2005-11-10
That Wolf Claw Keyboard is awesome, but I already have an n52.  Yes, the n52 works out of the box with breezy, but the system is only treating it as a another keyboard.  Within windows it's software allows you to remap any type of function / macro to the n52 keys. Take the scroll wheel for example, if you use it currently, the system thinks you are just scrolling the mouse wheel, but with the drivers and mapping, that can be set as another completely separate function. I am going to hack at the n52 sourceforge drivers and try to get this to work under breezy.  Once (if) I can get this to work, I will post a how-to in here. 


Regards,
Bruce

---

### Post by gentoo42 on 2005-11-14
UPDATE: 07-19-2010

Check a later post in this forum for a pystromo config:

[http://ubuntuforums.org/showpost.php?p=9609677&postcount=64]("http://ubuntuforums.org/showpost.php?p=9609677&postcount=64")

Update: 10-06-08:  looks like it may be easier to try [https://launchpad.net/pystromo](https://launchpad.net/pystromo), particularly for the newer model n52te's or whatever they are.

Thanks Raumkraut!
-------------------------

I have an N52 myself, and it is now working fine under 32 bit breezy.

You can get the drivers/config program from here:
[http://sourceforge.net/projects/nostromodriver/](http://sourceforge.net/projects/nostromodriver/)

the file you need is:
nostromo_n50-1.2.tar.gz

untar it to the directory of choice, then cd into that dir
do 
```
sudo ./configure
sudo make
sudo make install
```

i'm sure you need various development packages for this, i have a bunch installed, and am not sure which ones it relies on, if someone could try this off a fresh install that would be great.

then do the following:

```
sudo chmod 666 /dev/input/event*
nostromo_daemon
nostromo_config
```

and that should do it.  now, the problem with this is that you will have to chmod /dev/input/event* everytime  you boot, and also run nostromo_daemon.  i solved this the quick and dirty way.
in your home directory, or wherever you like, do 

```
gedit nostromostart
```

then put the following text in:

```
gksudo 'chmod 666 /dev/input/event1'
gksudo 'chmod 666 /dev/input/event2'
gksudo 'chmod 666 /dev/input/event3'
gksudo 'chmod 666 /dev/input/event4'
gksudo 'chmod 666 /dev/input/event5'
gksudo 'chmod 666 /dev/input/event6'
nostromo_daemon
```

if anyone has a better way to script that(it will prompt for password on login) please post, and i'll edit this.

save and close the file and make sure to do a:

```
chmod 777 nostromostart
```

or at least give it enough permissions to be read and executed by you(i'm just lazy and 777 is easy to remember).

Then simply go to System --> Preferences --> Sessions, click on startup programs, and add the location of your script, for example:

```
/home/username/./nostromostart
```

you need the ./ in front of your script so it will run.

That should be it, this worked for me, although I did a lot of tinkering and following various other guides on the web, so I may have left out packages you need, or anything else for that matter.  Give it a try and let me know.

---

### Post by Dirkson on 2005-11-14
I've got one of these things too. Unfortunately, I'm on a x64 platform. No drivers for me. The default isn't so bad, though- I wish one of the keys wasn't set as capslock, but other than that it works great. Still can frag to my heart's content in america's army.

---

### Post by cydizen on 2005-11-14
Hey Gentoo42, 

 Thanks for the reply... Here is the error I am getting when running sudo make..

/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status


 Any thoughts on this?


Thanks for your time,
Bruce

---

### Post by gentoo42 on 2005-11-14
I did a little checking on that, and it appears to be something with the LDFLAGS variable, heres a link with someone having a similar issue:

[http://www.linuxquestions.org/questions/showthread.php?s=&forumid=9&threadid=259063](http://www.linuxquestions.org/questions/showthread.php?s=&forumid=9&threadid=259063)

however, i wonder if it could be as simple as a missing package, do you have your kernel sources installed?
how about all the libc packages that are related?

for the kernel sources (if memory serves) just do:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

also, i in following some other guides i installed the following packages that were listed on synaps guide:

[http://www.ubuntuforums.org/showthread.php?t=53558&highlight=nostromo](http://www.ubuntuforums.org/showthread.php?t=53558&highlight=nostromo)
```

sudo apt-get install automake1.6
sudo apt-get install texinfo
sudo apt-get install libfltk1.1-dev
sudo apt-get install libgtk+2.0-directfb-udeb-dev
sudo apt-get install libxml2-dev
sudo apt-get install fluid
sudo apt-get install libxtst-dev
```

his guide is not by any means new, but he does mention that he had trouble making with anything other than automake 1.6 specifically.

---

### Post by cydizen on 2005-11-15
Okay, I cannot over state how much this community ROCKS!!

With a little manuvering, I got it working!!  gentoo42, thanks a bunch for the information.  I am going to write up an official how-to probably this weekend for it.  No worries, all credit due will be given in the how-to. 



Thanks Everyone!!


Regards,
Bruce

---

### Post by gentoo42 on 2005-11-15
Great! Glad to hear you go it working!

---

### Post by riotnerd on 2005-11-17
Runing Ubuntu 5.1 and have install all the pkg listed but    still fail on "make"
?? any clue what is wrong ??

daemon.o: In function `spawn_reader(int, int)':
daemon.cxx:(.text+0x2469): undefined reference to `pthread_create'
daemon.o: In function `main':
daemon.cxx:(.text+0x27c8): undefined reference to `pthread_create'
daemon.cxx:(.text+0x28b4): undefined reference to `pthread_create'
daemon.cxx:(.text+0x28f3): undefined reference to `pthread_join'

---

### Post by gentoo42 on 2005-11-18
hehe, did it show the smiley's in the terminal as well?  j/k.
anyway, you did do a sudo make, and not just make as your normal user right?
just glancing at those errors they look like c compiler output.   are you running a different version of gcc? also what version of automake do you have installed?

---

### Post by riotnerd on 2005-11-21
yes :) are added by the forum

yes I run ./configure and make  with the sudo 

gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)


automake (GNU automake) 1.9.5
Written by Tom Tromey <tromey@redhat.com>.

Thanks

---

### Post by Zed on 2005-11-25
I can help with the start up a little.

```
sudo gedit /etc/init.d/nostromo
```

Add:

```
#!/bin/bash

case "$1" in
    start)
        /bin/chmod 666 /dev/input/event*
        ;;
    stop)
        ;;
    restart)
        /bin/chmod 666 /dev/input/event*
        ;;
    *)
        echo "Usage: $0 {start|stop|restart}"
        exit 1
        ;;
esac

exit 0
```

Then do:

```
sudo update-rc.d nostromo defaults
```

I added nostromo_config to my System Tools menu (with the Applications Menu Editor), copying src/n50_tray.png to /usr/share/pixmaps for the icon.

Make sure you run nostromo_config once and save some sort of keymap before running nostromo_daemon -- it dies if it can't find a config file.

Then you can configure System->Preferences->Sessions->Startup Programs to just run /usr/local/bin/nostromo_daemon without having to write a separate script that chmods /dev/input/event* as well as runs nostromo_daemon.

I'm not starting nostromo_daemon in the init.d script because 1) somewhere in the relevant sourceforge forums a developer said not to run it as root -- I don't know why; 2) I don't know where it looks for config files other than ~user/.nostromorc (or if it looks anywhere else at all) and I'd rather not clutter /root with that.

Thanks for the HOWTO. I look forward to getting this working with some MAME games.

---

### Post by Zed on 2005-11-28
Oops. Disregard previous advice. There's a race condition, and it only works sometimes -- sometimes some of the event* don't get permitted and nostromo_daemon can't run. 

I'll look into a smarter way.

---

### Post by gentoo42 on 2005-11-28
that was the trouble i had writing a script to for startup, I couldn't get it to chmod all of the /dev/input/event/*, so I did each one individually.  for loop maybe? don't remember how to do that in bash off the top of my head.

oh, to riotnerd, did you try installing automake 1.6, thats what I have, looks like you are running something newer.

---

### Post by riotnerd on 2005-11-28
yes i had automake 1.6 insatlled before, but i did try uninstalling automake 1.9 , I now only have automake 1.6 and still same problem.  I hate to have to reintall the whole OS just to get the nostromo software to complie.

any clue where i should look to get it to complie.

thx

---

### Post by synap on 2005-12-05
I took care of the permissions issue by creating a file named /etc/init.d/startup.
I don&#8217;t know if this causes any sort of security concerns however, there maybe a better way to do it.

Before doing any of this, make sure you don&#8217;t already have a startup file as the following commands will over write it.  

ll /etc/init.d/startup 

If you get a *No such file or directory*, your good to go, otherwise just replace startup with some other name.


```
echo sudo chmod 666 /dev/input/event* > /etc/init.d/startup
sudo chmod a+rx /etc/init.d/startup
update-rc.d /etc/init.d/startup defaults
```

I should also note, that Juergen said in this [post](http://ubuntuforums.org/showthread.php?t=54460&highlight=nostromo) that editing the /etc/udev/permissions.d/udev.permissions file might be the way to fix it.  I haven&#8217;t tried it but it dose look like that is where the permissions are set.

---

### Post by agribah on 2006-07-05
This works on x64 as well.

---

### Post by skullcorp on 2006-11-16
This works great for me on Edgy 64-bit.  I wish it was easier to find though :\

Only dependencies I needed were:

```

sudo apt-get install libfltk1.1-dev
sudo apt-get install fluid

```

---

### Post by arron on 2007-04-23
Worked for me on Feisty, i had to use:

```
sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install automake
sudo apt-get install texinfo
sudo apt-get install libfltk1.1-dev
sudo apt-get install libgtk2.0-dev
sudo apt-get install libxml2-dev
sudo apt-get install fluid
sudo apt-get install libxtst-dev
```

Then in the nostromo dir;

```
sudo ./.configure
sudo make
sudo make install
```

Then i used the:

```
sudo /bin/chmod 666 /dev/input/event*
```

* note this only works if the controller is plugged in

Then to run the configuration:

```
 /usr/local/bin/nostromo_daemon
```

* if this does not come up with the icon in the task bar, make sure its plugged in, and then run the chmod command above again.

As well the init.d startup script above will only work if the N52 is plugged in.

This is the script i run to set it up if the N52 is pluged in after boot:

```
#! /bin/sh
#
# file to set and run nostromo at boot

#echo a message
echo "Thi script will start the Nostromo N52."
echo "Please make sure gamepad is inserted now."
read -p  "Press Enter to continue or Ctrl-c to quit." temp

##echo "Press any key to continue."
##read key

echo "Please enter in roots password to enable Nostromo N52"

#reset the input device
sudo chmod 666 /dev/input/event*

# run the app
nostromo_daemon
```

To configure the butons, run (settings saved to ~/.nostromorc):

```
/usr/local/bin/nostromo_config
```

I added both these commands to my menu, and made a small script for loading the daemon, with the chmod just before it runs, to get the image for the menu (then it will be in the default icon menu):

```
sudo cp ./src/n50_tray.png /usr/share/pixmaps
```

I'm not sure if all these installs are needed, but this worked for me on a  fresh Feisty 386 install.

---

### Post by dsnitker on 2007-04-23
did you have to install a specific C compiler?  I'm running Feisty and I'm getting a configure error stating that the compiler cannot create executables.

---

### Post by dsnitker on 2007-04-23
ok, I got everything to build, but my daemon still won't launch.  Is there a log file or something I can look at for output?  Nothing is happening for me, the config launches and my n52 is hooked up, but it doesn't seem to be working (I got input from the config, but remapping the keys did nothing).

---

### Post by dsnitker on 2007-04-23
ok I got my n52 up and running, turns out I had accidentally set my event permissions to 766 instead of 666.  works like a charm now :)

---

### Post by SmallAxe on 2007-05-06
Thanks Arron for the explicit instructions.  Got this up  and running, but I had to add the libraries through synaptic, the terminal script was leaving out libgtk2.0-dev, or one of its dependents. It's working now, though I don't have an icon, but I'm running AWN (hoping I can add the icon to the launcher???) with Beryl on Feisty.  Now if I could just get direct access to iTunes.....
Mahalo

---

### Post by Kelderkeuken on 2007-07-30
When I tried to compile the Nostromodriver from sourceforge, I was running into a dependency problem on Dapper Drake (6.06).

When I tried: **sudo apt-get install libgtk2.0-dev**
I get:```
The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
E: Broken packages
```

To fix it, I had to: **sudo aptitude install libxfixes-dev** and then choose the downgrade option (score -40).

Then I ran into the same problem already mentioned in this thread, that you have to set the permission of the events every time you reboot. The only suggestion that worked for me was the one from Synap (page 2) but the actual code didn't work for me. What I did (which is basically the same thing from what I can tell) is:

**sudo gedit /etc/init.d/startup**
Then save the file with content: **sudo chmod 666 /dev/input/event***
Then give the commands: **sudo chmod a+rx /etc/init.d/startup**
And: **sudo update-rc.d startup defaults**

(And adding the **nostromo_daemon** to your session startup if it's always plugged in anyway)

Working like a charm now, thanks for all the suggestions. This thread made it work for me.

---

### Post by arron on 2007-10-28
This works for gutsy (7.10).  I just made a little script to install it.... hope it helps!

```

#!/bin/bash

# script to setup nostromo n52

# get needed packages
sudo apt-get install build-essential linux-headers-`uname -r` automake texinfo libfltk1.1-dev libgtk2.0-dev libxml2-dev fluid libxtst-dev

# get the package
wget http://internap.dl.sourceforge.net/sourceforge/nostromodriver/nostromo_n50-1.3.tar.gz

#Unpack the package
tar xvzf nostromo_n50-1.3.tar.gz

# configure and make
cd nostromo_n50-1.3/
./configure
make
sudo make install
cd ..

# copy over icon for local use
sudo cp ./nostromo_n50-1.3/src/n50_tray.png /usr/share/pixmaps

# lets look at our config & make a default
echo "you must make a defauly .nostromorc here, save anything or it wont run!"
/usr/local/bin/nostromo_config
#or
# cp nostromorcfile ~/.nostromorc

# if it is plugged in, and a ~/.nostromorc
echo "will turn on if its plugged in!"
sudo /bin/chmod 666 /dev/input/event*
#run daemon
/usr/local/bin/nostromo_daemon

# clean it up
rm -r nostromo_n50-1.3
rm nostromo_n50-1.3.tar.gz

```

Please post your resaults.

---

### Post by Raumkraut on 2007-10-29
For anyone having problems (and even those who aren't!), I've written a more general 'input-remapper' which, as best as I can remember, now does everything that the Sourceforge/Windows Nostromo drivers do, and more. (and for any input device, not just n50/n52).
The only thing it's missing at the moment AFAIK is a GUI for editing the config/mapping files. (I'm having difficulty conceptualising how the UI would work, while still supporting all the features).

It supports key-chording, sequences and arbitrary macros, as well as remapping to and from relative (eg. mouse) and absolute (eg. joysticks) inputs.
I currently use it for one-key dodging in UT2004 (via the d-pad), and for assigning functions to those mouse buttons which Diablo 2 doesn't acknowledge. :)

If you want to give it a try (no compilation necessary!):
[https://launchpad.net/pystromo](https://launchpad.net/pystromo)

I know it works in Dapper and SLED/OpenSuse, but should work on any version/distro. It would be nice to have either confirmation or bug reports though! :D

---

### Post by Eberbachl on 2007-11-05
> **arron said:**
> This works for gutsy (7.10).  I just made a little script to install it.... hope it helps!


Please post your resaults.


Works nicely under Gutsy 7.10 AMD64 version.

Thanks ;)

Now I can play NWN with my fabulous n52

:D

---

### Post by arron on 2007-11-05
> **Eberbachl said:**
> 

Now I can play NWN with my fabulous n52

:D

Sweet, me 2!  That game rocks.  3 towns pw is very cool.

---

### Post by Xceptiona1 on 2007-11-05
each time I reboot I have to re-enter
"sudo /bin/chmod 666 /dev/input/event*"

What can I do to make that change permanent?

---

### Post by arron on 2007-11-05
Run the script i posted to run the program.  Or you can add it to a system startup script if its always plugged in.

---

### Post by Xceptiona1 on 2007-11-06
> **arron said:**
> Run the script i posted to run the program.  Or you can add it to a system startup script if its always plugged in.

I'm not certain that I understand, the script on the previous page does the complete setup of the program; Are you meaning that I add that to the startup. Wouldn't it then reinstall the program each time I login? Thank you

---

### Post by arron on 2007-11-06
Have a look at post 16 and 23 in this thread, 2 easy options there.  You should be up and gamen in no time!

---

### Post by Xceptiona1 on 2007-11-06
Thanks for the assistance, I ended up using post #16 to get the deamon to autoload. Ended up adding one step, the file /etc/init.d/nostromo needed to be chmod'ed so it would run for me. 

Thanks agagin everyone, I've been fragging folks in quake wars all night :)

---

### Post by Swarlanis on 2007-11-07
That installation script worked a treat on my Inspiron laptop. I use my N52 for just about everything on my PC, so not having access to it has been a stumbling block keeping me from full time Ubuntu use.

Thanks guys! :D


Swarlanis

---

### Post by Fritti on 2007-11-07
> **Raumkraut said:**
> For anyone having problems (and even those who aren't!), I've written a more general 'input-remapper' which, as best as I can remember, now does everything that the Sourceforge/Windows Nostromo drivers do, and more. (and for any input device, not just n50/n52).
The only thing it's missing at the moment AFAIK is a GUI for editing the config/mapping files. (I'm having difficulty conceptualising how the UI would work, while still supporting all the features).

It supports key-chording, sequences and arbitrary macros, as well as remapping to and from relative (eg. mouse) and absolute (eg. joysticks) inputs.
I currently use it for one-key dodging in UT2004 (via the d-pad), and for assigning functions to those mouse buttons which Diablo 2 doesn't acknowledge. :)

If you want to give it a try (no compilation necessary!):
[https://launchpad.net/pystromo](https://launchpad.net/pystromo)

I know it works in Dapper and SLED/OpenSuse, but should work on any version/distro. It would be nice to have either confirmation or bug reports though! :D

Heya Raumkraut,

your application works fine on my Fedora 7 box. Much appreciated, it's way easier this way than compiling a kernel driver.

One bug report I have: I need to have my /etc/input/event* chmod'ded to 666 before I can use remapper.py as a regular user, otherwise my n52 doesn't get detected. Is this because of distro differences or is your udev rules file incorrect?

Furthermore it might be wise to append some security warnings to the README (making input devices worldreadable is OK on a single user system but not on a multi user one...)

Cheers!

---

### Post by arron on 2008-01-25
I have been playen with this some more,and thought i would share my findings...

I have set it up, if the user is logged in, and plugs in the nostromo it will auto detect and automaticly run the nostromo daemon.  Here is the script, there is a little extra setup (1 file) but the info is there to do it.

Just pay attention to where you save this script and reference it in the myrules file.

The only catch is, it will not run if your not logged in, or booting up with it plugged in, then you can use the script i posted before (actually you dont need all of that, just run the nostromo_daemon, this takes care of the permissions).  Or simply unplug and replug it in.

Please let me know if this works for you.

```

#! /bin/sh
#
# file to set and run nostromo when it is plugged in

# first you need to make file /etc/udev/rules.d/85-my_rule.rules
# and put this line in there
# ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="050d", SYSFS{idProduct}=="0815", RUN="/home/user/thisscript-name"
#
# note the "RUN=" runs it once, the "RUN+=" runs it many times"
# these vender and product numbers is from the command lsusb, we can use this with other apps as well upon plugin
#
# and this needs to be run as the user xhost +local: to allow others to connect to the x server (system to start the application)
# add this to your ubuntu user startup by going System -> Preferences -> Sessions and add a new item: (*buntu check your startup scripts for the display manager)
# The text in the "quotes" is what you put in, dont include the ""'s
# Name - "Nostromo"
# Command - "xhost +local:"
# Comment - "Allow nostromo gamepad manager to be started by the system"

# now some config
USER="arron"
DAEMON="/usr/local/bin/nostromo_daemon"

# debug if needed to make sure its running
#TEMP="Running Nostromo Auto Script named $0 on "$(date)
#echo $TEMP >> /home/$USER/nostromo-auto.log

#reset the input device, needed for all users to use
chmod 666 /dev/input/event* 

# now set export to x display 0"
export DISPLAY=:0 

# run nostromo daemon as the user on thier screen
gksudo -u $USER $DAEMON        

# OR we can just run another app or script with no gui
# /home/user/bin/some-script

```

---

### Post by Raumkraut on 2008-01-26
Grr, I would've replied earlier, but the forums only today deigned to inform me of any new posts since Nov 5th. :mad:

> **Fritti said:**
> One bug report I have: I need to have my /etc/input/event* chmod'ded to 666 before I can use remapper.py as a regular user, otherwise my n52 doesn't get detected. Is this because of distro differences or is your udev rules file incorrect?

Yes, the udev .rules file in 0.5 can be incorrect because of distro differences. :) There have been a few more revisions since the release, with new .rules files, but I didn't consider the changes significant enough for another release. Maybe I'll sneakily update 0.5 to a 0.5.1 which includes the new files. :)
As best as I can tell, 666-ing the event* nodes is the simplest way of doing it on Fedora (which doesn't assign users to any collective group AFAICT).

> **Fritti said:**
> Furthermore it might be wise to append some security warnings to the README (making input devices worldreadable is OK on a single user system but not on a multi user one...)

 I'd actually already modified the readme (in unpackaged revisions) with a warning along those lines. :D

 Maybe arron should put a similar warning on his little script too. ;)

---

### Post by matthewcraig on 2008-01-26
Your post made me go dig up my old N52, just to see if it would work with Ubuntu.  Worked perfectly out of the box, with no additional software.

What does this additional software you mentioned do?  Is it to remap the keys?

I think it would be great if we could take whatever functionality was in there, write it in open source software, and get it included as an Ubuntu package.  Anyone want to post the list of features here?

Anyway, if you are reading this thread and anguishing over installing proprietary software, then know you can plug in a N52 and get the functionality of the left side of your keyboard, scroll wheel, arrow keys, and space bar, right off the bat.

Device just popped right up.  Immediately detected and usable.  Gotta love the Linux kernel.  These entries are from my log file after plugging in the device with out-of-the-box Ubuntu install:
input: Honey Bee  Nostromo SpeedPad2  as /class/input/input11
input: USB HID v1.10 Mouse [Honey Bee  Nostromo SpeedPad2 ] on usb-0000:00:10.4-3.4

---

### Post by cunning001 on 2008-04-17
I am going to jump into this as a former nostromo user that's moved (up i think) to a saitek pro gamer command unit.
Basically the same exact thing as a nostromo with a few more buttons (if you can believe it) and some other nice tweeks.
It's a sweet little game controller and as I found no luck on fixes in searches I'm guessing with a little tweaking of conifigs could be served by the app/fix for the nostromo.
I'll see what I can figure out after I digest this whole thread.

---

### Post by Jack the R on 2008-08-17
I've tried Raumkraut's scripts, but it's not working (yet).  I'm getting the errors - 

> jeremy@r1e:~/Documents/pystromo/trunk$ ./monitor.py -v
/home/jeremy/Documents/pystromo/trunk/remapper.py -m config/test.map
/home/jeremy/Documents/pystromo/trunk/remapper.py -m config/test.map -m /home/.pystromo/n52_inkscape.map
Traceback (most recent call last):
  File "/home/jeremy/Documents/pystromo/trunk/remapper.py", line 48, in <module>
    keymap = mapping.Mapper(*options.maps)
  File "/home/jeremy/Documents/pystromo/trunk/lib/config.py", line 21, in __init__
    self.load(args)
  File "/home/jeremy/Documents/pystromo/trunk/lib/mapping.py", line 122, in load
    self._loadMapSection(section)
  File "/home/jeremy/Documents/pystromo/trunk/lib/mapping.py", line 184, in _loadMapSection
    remap = ReMapping (singleInput, output)
  File "/home/jeremy/Documents/pystromo/trunk/lib/mapping.py", line 261, in __init__
    self.output = self.decode(output)
  File "/home/jeremy/Documents/pystromo/trunk/lib/mapping.py", line 314, in decode
    note = self.stringToKey(note)
  File "/home/jeremy/Documents/pystromo/trunk/lib/mapping.py", line 362, in stringToKey
    raise ValueError ('"%s" is an invalid code' % string)
ValueError: "KEY_" is an invalid code


???

Also, when I plug in my N52, before running anything, it does not play nice with Ubuntu like everyone else is reporting.  It seems to interfere with the system, or at least the regular keyboard.  Instead of typing "this" I might get something like "thhhhhhhhhhs" (typing on the regular keyboard).  

What should I do?

---

### Post by Raumkraut on 2008-08-17
Jack the R; I've posted a response to this in your Launchpad question.
I don't know about the second part though. Perhaps searching for info about generic keyboard-repeat problems would help.

BTW, thanks for posting here and prompting me to look at the launchpad page again. Darn thing wasn't set up for me to receive new-question notifications. :(

---

### Post by Jack the R on 2008-08-17
Thanks for writing this program (and solving my problem)!

The n52 isn't a toy for me, it's a business tool.  I wasn't able to use it after switching to Linux (but still, better than using Vista).  It's going to be great having the n52 in my toolbox again.

Edit - a visual aid for the configuring of Pystromo/N52 -

[img]http://www.extinctionlevelevent.com/misc/linux/pystromo/n52.png[/img]

---

### Post by Knightsky on 2008-08-18
Hey guys, been a while since I last had to ask about things. My N52 finally died, and I went out to purchase a new one...only to find that the N52 is no longer made. However, there's the N52te, with a nifty backlight feature.

Unfortunately, the drivers that I used to run the n52 before (the one from Sourceforge) doesn't work with the new device. Do we have any good workarounds for this yet?

---

### Post by Raumkraut on 2008-08-19
> **Knightsky said:**
> Unfortunately, the drivers that I used to run the n52 before (the one from Sourceforge) doesn't work with the new device. Do we have any good workarounds for this yet?

What am I, chopped liver? :D
Give my Pystromo a try: [https://launchpad.net/pystromo](https://launchpad.net/pystromo) :)

If the n52te has a different USB product ID (or even vendor) to the original n52, which it sounds like it might, you can use `lsusb` to find them out. My classic n52 is listed as "050d:0815 Belkin Components" (how very descriptive!).

---

### Post by Jack the R on 2008-10-04
Absolutely use Raumkraut's script, it's way better and easier to install.

---

### Post by imlost on 2008-10-15
> **Jack the R said:**
> Absolutely use Raumkraut's script, it's way better and easier to install.

I can vouch for that! Raumkraut's Pystromo script works FLAWLESSLY!!

Also he is VERY quick to help with problems you may be having with it!

---

### Post by arron on 2009-02-28
I have upgraded to 8.10, and the nostromo driver works well for me.  I changed a couple small things on the script i made (just version for the driver)

```

#!/bin/bash

# script to setup nostromo n52

# get needed packages
sudo apt-get install build-essential linux-headers-`uname -r` automake texinfo libfltk1.1-dev libgtk2.0-dev libxml2-dev fluid libxtst-dev

# current nostromo version
NVER="1.4"
# get the package
wget  http://internap.dl.sourceforge.net/sourceforge/nostromodriver/nostromo_n50-$NVER.tar.gz

#Unpack the package
tar xvzf nostromo_n50-$NVER.tar.gz

# configure and make
cd nostromo_n50-$NVER/
./configure
make
sudo make install
cd ..

# copy over icon for local use
sudo cp ./nostromo_n50-$NVER/src/n50_tray.png /usr/share/pixmaps

# lets look at our config & make a default
echo "you must make a defauly .nostromorc here, save anything or it wont run!"
/usr/local/bin/nostromo_config
#or
# cp nostromorcfile ~/.nostromorc

# if it is plugged in, and a ~/.nostromorc
echo "will turn on if its plugged in!"
sudo /bin/chmod 666 /dev/input/event*
#run daemon
/usr/local/bin/nostromo_daemon

# we need to add this for ubuntu 8+
XORGCONF="/etc/X11/xorg.conf"
sudo echo '' >> $XORGCONF
sudo echo '# added by arron to have n52 in hardy' >> $XORGCONF
sudo echo 'Section "ServerFlags"' >> $XORGCONF
sudo echo '	Option "AutoAddDevices" "no"' >> $XORGCONF
sudo echo '	Option "AutoEnableDevices" "no"' >> $XORGCONF
sudo echo 'EndSection' >> $XORGCONF
sudo echo '' >> $XORGCONF

# then x needs to be restarted, ctrl-alt F1 then ctrl-alt F7 should do it


# clean it up
rm -r nostromo_n50-$NVER
rm nostromo_n50-$NVER.tar.gz

```

Add this code to your script to start the daemon if needed
```

# lets run n52 if its not already runing
# check to see if its running
N52=`pgrep nostromo_daemon`
# runn nostromo setup and app if its not
if [ -z "$N52" ];
then
	gksudo -m "Setting up N52 needs root access for device permissions. Please enter in your password here:" chmod 666 /dev/input/event* 
	/usr/local/bin/nostromo_daemon
#else
	# Run something else if N52 is running
fi

```

I plan on trying out the Pystromo code this week, ive heard a few using it now and quite happy.

**NOTE** - To work on Ubuntu 8.* and up, you need to put this in your  /etc/X11/xorg.conf
This is in the above install script, you need to restart x after this
```

# added by arron to have n52 in hardy
Section "ServerFlags"
	Option "AutoAddDevices" "no" 
	Option "AutoEnableDevices" "no" 
EndSection

```

---

### Post by coolhand59 on 2009-03-01
I'm relatively new to Ubuntu, and am pretty sure I have everything almost installed correctly. When I run sudo nostromo_daemon, I get the system tray icon, and the N52 will work, but only with it's default mappings. I have created/saved a custom profile, and if I right click on system tray, it lists it there and has it selected, but stil only works with the default key maps.

Any thoughts?

Thanks

---

### Post by arron on 2009-03-08
There is a couple small snages.  Try copying my script again and running it again, there is a couple small changes.  I posted my old script where i had a couple small changes.  Nostromo app here is getting somewhat outdated, psystromo is worth a look to.

---

### Post by kaje36 on 2009-03-25
I seemed to be a little stumped with this. 
I am running 8.10, and I have tried every combination of this I can think of. unfortunately without thinking it my N52 has been plugged in for the last week before I thought about drivers for it. 

I can change the Config without a problem and get the daemon to run, and stay running. but the output of the N52 is never changed. I still just get the keyboard key output. 
I have sudo'ed the nostromo_config, and run it regularly. and the config's do come up in the task bar Icon when the daemon is running. 

I have played with Pystromo a little.. and dont like it so far. I haven't figured out how to get any of the "shift" keys to work (ie red shift, blue shift, green shift) and I do need them for what I am doing. 

does anyone have any ideas on this? 

I have tried both Version 1.3 and 1.4, I have done it manually, and with the script Aaron created

---

### Post by derdud on 2009-04-13
I'm having the same problem. I don't really understand what's wrong here. I'm running 8.10 as well. I didn't have any problems installing it. The daemon starts fine. But it won't use anything other than the default keyboard configuration.

---

### Post by kaje36 on 2009-04-13
I acualy did figure out the answer to this. and it works amazing.. I am at work so bear with me a minute. 

in the Xconf file

Section "ServerFlags"
    Option         "Xinerama" "0"
    Option         "AutoAddDevices" "false"
EndSection


I don't think my text is 100% right.. I will try to correct when I get home. so please don't copy me exact. but should point you in the right direction. ::Corected, copied directly from my Xconf file::

Oh ya.. you will need to restart X after this. a Control Alt backspace should be fine. but if it doesn't work do a full reboot. 

I don't know why the script mentioned before didn't add this in. but I manually when I was playing with Pystromo, and Nostromo works beautifully. 

for some reason I couldn't get Pystromo to load the config file. but it doesnt matter anymore.. this driver works amazing for me!

---

### Post by kaje36 on 2009-04-13
I corrected my above post with a copy from my xconf file. 

I haven't been able to get the auto-load to happen. but just running the daemon from a terminal isn't a big deal for me.. I almost never shut down, so its rare I have to run it.

---

### Post by Chriis on 2009-05-01
Hello all,

I've upgraded from Gutsy to Jaunty (fresh install)

I've installed my nostromo n50 on gutsy with the help from this thread
whitout any problem.

But now with Jaunty, i' ve tried to repeat the same install, but it doesnt work well.

when i did " sudo modprobe evdev " , it return that there is no evdev module, so i passed this step,.. this driver is compiled in the new kernel a guess,... and complete the install process to see if it would work, so..

" sudo ./configure " 
" sudo make " 
" sudo make install " 

All seem to go flawlessly,..  

" sudo nostromo_config ",.. worked well, i saved the new profile :P

" sudo nostromo_deamon" ,.. BIM! but the deamon refuse to start,...:(

In the log viewer file i receive this:

messages:
commando nostromo_daemon[3602]: Found 050d:0805 at dev 4  <---this is oki
commando nostromo_daemon[3602]: Starting reader_thread with fd=9 
commando kernel: [   59.372543] nostromo_daemon[3602]: segfault at ffffffff9f5f89e0 ip 00007f84a94b3ba8 sp 00007fffb4522c40 error 4 in libpthread-2.9.so[7f84a94ac000+17000]
commando nostromo_daemon[3607]: Removing stale pidfile.

kern.log:
commando kernel: [   59.372543] nostromo_daemon[3602]: segfault at ffffffff9f5f89e0 ip 00007f84a94b3ba8 sp 00007fffb4522c40 error 4 in libpthread-2.9.so[7f84a94ac000+17000]



Any have an idea why ?

help needed :)

thanks

chriis

---

### Post by Chriis on 2009-05-10
bump

---

### Post by kaje36 on 2009-05-11
here is a bump for ya. 

Also I started having a weird issue. everything worked fine. I installed a new motherboard. and now I have a issue with the nostromo, everything seems to work fine. but some of my key maps are messed up. I have one key mapped for example, it supposed to push Alt +6 any time I push the button. about 60% of the time it only send 6, the other 40% it does Alt+6

anyone have any ideas?

---

### Post by Chriis on 2009-05-24
bump!

---

### Post by Chriis on 2009-08-24
re-bump !

---

### Post by TherinDAoC on 2009-09-26
I know how it is to try to help computer users who have no idea what Control Panel is in Windows.  I am slowly learning Ubuntu and am totally stuck on how to make my N52 work.  Yes, it is detected and it acts like the left part of my keyboard.  In this guide ( [http://ubuntuforums.org/archive/index.php/t-948833.html](http://ubuntuforums.org/archive/index.php/t-948833.html) )  on step 18 I just get 'no such file or directory' error when I do the script that ends in output.map -vv AND in step 22 as well.

This prevents me from even trying to attempting to input custom layouts for my n52.  I would appreciate helpful walkthroughs of any help you can give me.  You should be able to email me back.  Thanks in advance.

---

### Post by arron on 2010-07-19
After a recent upgrade to LTS, the older nostromo doesnt want to compile to well.

So I tried psytromo as posted on here( [https://launchpad.net/pystromo](https://launchpad.net/pystromo) ).

Im very impressed, its is HIGHLY configurable to do just about whatever you want.  For those who still use a N50/52 give this a shout.  Supose to work well for other input devices too, and no compiling.

I did up a basic map to help figure out the main keys, just add the key you want to map it to (this basic config is the only thing i had to do a little homework on):

```

# Nostromo n52
[Device:n52]
vendor=0x050d
product=0x0815

[Map:n52]
# tab, key 1
KEY_TAB:
# q, key 2
KEY_Q:KEY_F1
# w, key 3
KEY_W:
# e, key 4
KEY_E:
# r, key 5
KEY_R:
# Shift, key 6
KEY_CAPSLOCK:
# a, key 7
KEY_A:
# s, key 8
KEY_S:
# d, key 9
KEY_D:
# f, key 10
KEY_F:
# control, key 11
KEY_LEFTSHIFT:
# z, key 12
KEY_Z:
# x, key 13
KEY_X:
# c, key 14
KEY_C:
# space, key 15
KEY_SPACE:
# orange button
KEY_LEFTALT:
# Pad up/down/left/right
KEY_UP:
KEY_DOWN:
KEY_LEFT:
KEY_RIGHT:
# scroll wheel
# up
REL_WHEEL>=
# down
REL_WHEEL<=
#click
BTN_MIDDLE: KEY_L
# LED Colors: Red=LED_NUML, Green=LED_CAPSL, Blue=LED_SCROLLL. @1=On, @0=Off
#red, green, then blue
LED_NUML
LED_CAPSL
LED_SCROLLL

```

And here is a list of the usable keys to map to.  

```

# Keys
				0: 'KEY_RESERVED',
				1: 'KEY_ESC',
				2: 'KEY_1',
				3: 'KEY_2',
				4: 'KEY_3',
				5: 'KEY_4',
				6: 'KEY_5',
				7: 'KEY_6',
				8: 'KEY_7',
				9: 'KEY_8',
				10: 'KEY_9',
				11: 'KEY_0',
				12: 'KEY_MINUS',
				13: 'KEY_EQUAL',
				14: 'KEY_BACKSPACE',
				15: 'KEY_TAB',
				16: 'KEY_Q',
				17: 'KEY_W',
				18: 'KEY_E',
				19: 'KEY_R',
				20: 'KEY_T',
				21: 'KEY_Y',
				22: 'KEY_U',
				23: 'KEY_I',
				24: 'KEY_O',
				25: 'KEY_P',
				26: 'KEY_LEFTBRACE',
				27: 'KEY_RIGHTBRACE',
				28: 'KEY_ENTER',
				29: 'KEY_LEFTCTRL',
				30: 'KEY_A',
				31: 'KEY_S',
				32: 'KEY_D',
				33: 'KEY_F',
				34: 'KEY_G',
				35: 'KEY_H',
				36: 'KEY_J',
				37: 'KEY_K',
				38: 'KEY_L',
				39: 'KEY_SEMICOLON',
				40: 'KEY_APOSTROPHE',
				41: 'KEY_GRAVE',
				42: 'KEY_LEFTSHIFT',
				43: 'KEY_BACKSLASH',
				44: 'KEY_Z',
				45: 'KEY_X',
				46: 'KEY_C',
				47: 'KEY_V',
				48: 'KEY_B',
				49: 'KEY_N',
				50: 'KEY_M',
				51: 'KEY_COMMA',
				52: 'KEY_DOT',
				53: 'KEY_SLASH',
				54: 'KEY_RIGHTSHIFT',
				55: 'KEY_KPASTERISK',
				56: 'KEY_LEFTALT',
				57: 'KEY_SPACE',
				58: 'KEY_CAPSLOCK',
				59: 'KEY_F1',
				60: 'KEY_F2',
				61: 'KEY_F3',
				62: 'KEY_F4',
				63: 'KEY_F5',
				64: 'KEY_F6',
				65: 'KEY_F7',
				66: 'KEY_F8',
				67: 'KEY_F9',
				68: 'KEY_F10',
				69: 'KEY_NUMLOCK',
				70: 'KEY_SCROLLLOCK',
				71: 'KEY_KP7',
				72: 'KEY_KP8',
				73: 'KEY_KP9',
				74: 'KEY_KPMINUS',
				75: 'KEY_KP4',
				76: 'KEY_KP5',
				77: 'KEY_KP6',
				78: 'KEY_KPPLUS',
				79: 'KEY_KP1',
				80: 'KEY_KP2',
				81: 'KEY_KP3',
				82: 'KEY_KP0',
				83: 'KEY_KPDOT',
				84: 'KEY_103RD',
				85: 'KEY_F13',
				86: 'KEY_102ND',
				87: 'KEY_F11',
				88: 'KEY_F12',
				89: 'KEY_F14',
				90: 'KEY_F15',
				91: 'KEY_F16',
				92: 'KEY_F17',
				93: 'KEY_F18',
				94: 'KEY_F19',
				95: 'KEY_F20',
				96: 'KEY_KPENTER',
				97: 'KEY_RIGHTCTRL',
				98: 'KEY_KPSLASH',
				99: 'KEY_SYSRQ',
				100: 'KEY_RIGHTALT',
				101: 'KEY_LINEFEED',
				102: 'KEY_HOME',
				103: 'KEY_UP',
				104: 'KEY_PAGEUP',
				105: 'KEY_LEFT',
				106: 'KEY_RIGHT',
				107: 'KEY_END',
				108: 'KEY_DOWN',
				109: 'KEY_PAGEDOWN',
				110: 'KEY_INSERT',
				111: 'KEY_DELETE',
				112: 'KEY_MACRO',
				113: 'KEY_MUTE',
				114: 'KEY_VOLUMEDOWN',
				115: 'KEY_VOLUMEUP',
				116: 'KEY_POWER',
				117: 'KEY_KPEQUAL',
				118: 'KEY_KPPLUSMINUS',
				119: 'KEY_PAUSE',
				120: 'KEY_F21',
				121: 'KEY_F22',
				122: 'KEY_F23',
				123: 'KEY_F24',
				124: 'KEY_KPCOMMA',
				125: 'KEY_LEFTMETA',
				126: 'KEY_RIGHTMETA',
				127: 'KEY_COMPOSE',
				128: 'KEY_STOP',
				129: 'KEY_AGAIN',
				130: 'KEY_PROPS',
				131: 'KEY_UNDO',
				132: 'KEY_FRONT',
				133: 'KEY_COPY',
				134: 'KEY_OPEN',
				135: 'KEY_PASTE',
				136: 'KEY_FIND',
				137: 'KEY_CUT',
				138: 'KEY_HELP',
				139: 'KEY_MENU',
				140: 'KEY_CALC',
				141: 'KEY_SETUP',
				142: 'KEY_SLEEP',
				143: 'KEY_WAKEUP',
				144: 'KEY_FILE',
				145: 'KEY_SENDFILE',
				146: 'KEY_DELETEFILE',
				147: 'KEY_XFER',
				148: 'KEY_PROG1',
				149: 'KEY_PROG2',
				150: 'KEY_WWW',
				151: 'KEY_MSDOS',
				152: 'KEY_COFFEE',
				153: 'KEY_DIRECTION',
				154: 'KEY_CYCLEWINDOWS',
				155: 'KEY_MAIL',
				156: 'KEY_BOOKMARKS',
				157: 'KEY_COMPUTER',
				158: 'KEY_BACK',
				159: 'KEY_FORWARD',
				160: 'KEY_CLOSECD',
				161: 'KEY_EJECTCD',
				162: 'KEY_EJECTCLOSECD',
				163: 'KEY_NEXTSONG',
				164: 'KEY_PLAYPAUSE',
				165: 'KEY_PREVIOUSSONG',
				166: 'KEY_STOPCD',
				167: 'KEY_RECORD',
				168: 'KEY_REWIND',
				169: 'KEY_PHONE',
				170: 'KEY_ISO',
				171: 'KEY_CONFIG',
				172: 'KEY_HOMEPAGE',
				173: 'KEY_REFRESH',
				174: 'KEY_EXIT',
				175: 'KEY_MOVE',
				176: 'KEY_EDIT',
				177: 'KEY_SCROLLUP',
				178: 'KEY_SCROLLDOWN',
				179: 'KEY_KPLEFTPAREN',
				180: 'KEY_KPRIGHTPAREN',
				181: 'KEY_INTL1',
				182: 'KEY_INTL2',
				183: 'KEY_INTL3',
				184: 'KEY_INTL4',
				185: 'KEY_INTL5',
				186: 'KEY_INTL6',
				187: 'KEY_INTL7',
				188: 'KEY_INTL8',
				189: 'KEY_INTL9',
				190: 'KEY_LANG1',
				191: 'KEY_LANG2',
				192: 'KEY_LANG3',
				193: 'KEY_LANG4',
				194: 'KEY_LANG5',
				195: 'KEY_LANG6',
				196: 'KEY_LANG7',
				197: 'KEY_LANG8',
				198: 'KEY_LANG9',
				200: 'KEY_PLAYCD',
				201: 'KEY_PAUSECD',
				202: 'KEY_PROG3',
				203: 'KEY_PROG4',
				205: 'KEY_SUSPEND',
				206: 'KEY_CLOSE',
				220: 'KEY_UNKNOWN',
				224: 'KEY_BRIGHTNESSDOWN',
				225: 'KEY_BRIGHTNESSUP',
				0x100: 'BTN_0',
				0x101: 'BTN_1',
				0x102: 'BTN_2',
				0x103: 'BTN_3',
				0x104: 'BTN_4',
				0x105: 'BTN_5',
				0x106: 'BTN_6',
				0x107: 'BTN_7',
				0x108: 'BTN_8',
				0x109: 'BTN_9',
				0x110: 'BTN_LEFT',
				0x111: 'BTN_RIGHT',
				0x112: 'BTN_MIDDLE',
				0x113: 'BTN_SIDE',
				0x114: 'BTN_EXTRA',
				0x115: 'BTN_FORWARD',
				0x116: 'BTN_BACK',
				0x120: 'BTN_TRIGGER',
				0x121: 'BTN_THUMB',
				0x122: 'BTN_THUMB2',
				0x123: 'BTN_TOP',
				0x124: 'BTN_TOP2',
				0x125: 'BTN_PINKIE',
				0x126: 'BTN_BASE',
				0x127: 'BTN_BASE2',
				0x128: 'BTN_BASE3',
				0x129: 'BTN_BASE4',
				0x12a: 'BTN_BASE5',
				0x12b: 'BTN_BASE6',
				0x12f: 'BTN_DEAD',
				0x130: 'BTN_A',
				0x131: 'BTN_B',
				0x132: 'BTN_C',
				0x133: 'BTN_X',
				0x134: 'BTN_Y',
				0x135: 'BTN_Z',
				0x136: 'BTN_TL',
				0x137: 'BTN_TR',
				0x138: 'BTN_TL2',
				0x139: 'BTN_TR2',
				0x13a: 'BTN_SELECT',
				0x13b: 'BTN_START',
				0x13c: 'BTN_MODE',
				0x13d: 'BTN_THUMBL',
				0x13e: 'BTN_THUMBR',
				0x140: 'BTN_TOOL_PEN',
				0x141: 'BTN_TOOL_RUBBER',
				0x142: 'BTN_TOOL_BRUSH',
				0x143: 'BTN_TOOL_PENCIL',
				0x144: 'BTN_TOOL_AIRBRUSH',
				0x145: 'BTN_TOOL_FINGER',
				0x146: 'BTN_TOOL_MOUSE',
				0x147: 'BTN_TOOL_LENS',
				0x14a: 'BTN_TOUCH',
				0x14b: 'BTN_STYLUS',
				0x14c: 'BTN_STYLUS2',

```

Must say, I am really impressed with psytromo, I should of switched a long time ago.  No compiling, just plug and play, with a little config setup for your game.  Did i mention no compiling?

---

### Post by Objekt on 2010-10-20
I read your thread with great interest, as I was recently given a Nostromo n52 and would very much like to use it with Ubuntu 10.04.

However, I am a little overwhelmed with the 32-step tutorial you linked, and haven't got all the way through it yet.

In the meantime, please clarify the mapping.  If I understand correctly, you put the key name from the bottom list next to the Nostromo button on the top list.  So a line from my mapping file might read:
```
#use n52 01 button as Escape key
KEY_TAB:KEY_ESC
```
would cause the Nostromo "01" key (top left), which is "tab" by default, to generate an "Esc" keypress instead.  Do I have that right?

Is it possible to make Pystromo do things with other input devices at the same time it is supporting the n52?

I ask because I have searched in vain for a way to program the buttons on my mouse (Logitech MX310) as keystrokes.  For example, I find it's useful to have the left auxiliary button, mapped by default as a "back" button in Firefox, perform an 'Esc' instead.  I suspect there is a fairly simple way to do so using xorg.conf, but damned if I can figure it out.

---

### Post by arron on 2010-10-20
"#use n52 01 button as Escape key
KEY_TAB:KEY_ESC"

Should put key 1 as escape button.  Skip the first part for install and just go with this:

[https://launchpad.net/pystromo](https://launchpad.net/pystromo)

The compile of the other one is older, and I have had to many problems with it.  pystromo is pretty quick and stright forward, just use my template from a couple posts ago.  should be pretty quick!

gluck

---

### Post by Objekt on 2010-10-21
Thanks for clearing that up.  And if I don't put anything after the colon, e.g.

```
#use n52 01 button as default Tab key
KEY_TAB:
```

for a button, it will perform its default function, correct?

I don't want to mess with most of the buttons, at least not yet.  Mostly I just want to program the D-pad.

Is it possible to use the Nostromo's multiple shift states with pystromo?  I would think you'd have to have 4 keymaps overall, one for each of the three shift states + one for unshifted.  I haven't felt the need for so many commands yet, but I may want to do it at some point.

Well that's really weird.  It seems that any time I'm playing music with Rhythmbox, all 3 lights on the Nostromo flash.  WTF?

---

