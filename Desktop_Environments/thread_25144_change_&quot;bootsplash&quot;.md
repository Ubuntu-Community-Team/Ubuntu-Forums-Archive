---
title: "change &quot;bootsplash&quot;"
date: 2005-04-09
forum: Desktop Environments
---

### Post by brujoquizz on 2005-04-09
Hello, 

I'm a new linux user. Is there any way to  change the "bootsplash" (I don't know if it is called like this). I mean, when Ubuntu is starting commands appear saying the things that are loading and if they are OK or they fail. Is there a way to change this commands for a "splash" with a progress bar? (as it is in windows for example).

Thanks!!

---

### Post by ubuntu_demon on 2005-04-09
[QUOTE=brujoquizz]Hello, 

I'm a new linux user. Is there any way to  change the "bootsplash" (I don't know if it is called like this). I mean, when Ubuntu is starting commands appear saying the things that are loading and if they are OK or they fail. Is there a way to change this commands for a "splash" with a progress bar? (as it is in windows for example).

Thanks!![/QUOTE]
 there are a couple of nice splashimages here :
[http://sleepybuddha.sl.funpic.de/ubuntu/](http://sleepybuddha.sl.funpic.de/ubuntu/)

download the ones you like and after this just do this :
$ sudo mkdir /boot/grub/images
go to the directory of the downloaded bootsplashfiles and do this :
$ mv *.xpm.gz /boot/grub/images/

you can install grubconf by :
$ sudo apt-get install grubconf

and start grubconf :
$ sudo grubconf

And now you just select that you want a bootsplash and select the file.


And set the splashimage file you like using grubconf

---

### Post by jonny on 2005-04-09
This doesn't quite work, as grubconf isn't in the Hoary repositories.  The alternative, editing grub's configuration files directly, isn't really a smart move for inexperienced users - inexpert changes can render a system unbootable, although you can always recover with a rescue CD if you know what you're doing.

To install grubconf, download the .deb file from [here](http://ruslug.rutgers.edu/~mcgrof/grubconf/grubconf-0.5.1-debian/), put it on your desktop and enter (in a terminal window, of course):```
sudo dpkg -i ~/Desktop/grubconf_0.5.1-4_i386.deb
```Although you'll then be able to find  a menu option for grubconf, it doesn't work; start the program with sudo grubconf.

---

### Post by ubuntu_demon on 2005-04-09
[QUOTE=jonny]This doesn't quite work, as grubconf isn't in the Hoary repositories.  The alternative, editing grub's configuration files directly, isn't really a smart move for inexperienced users - inexpert changes can render a system unbootable, although you can always recover with a rescue CD if you know what you're doing.

To install grubconf, download the .deb file from [here](http://ruslug.rutgers.edu/~mcgrof/grubconf/grubconf-0.5.1-debian/), put it on your desktop and enter (in a terminal window, of course):```
sudo dpkg -i ~/Desktop/grubconf_0.5.1-4_i386.deb
```Although you'll then be able to find  a menu option for grubconf, it doesn't work; start the program with sudo grubconf.[/QUOTE]
 I see. Aprerently I had grubconf still installed from warty :-D

there's also a package called grub-splashimages which provides some splashimages

---

### Post by Joh_ on 2005-04-09
I actually don't think this is what he was after. I think he wants a splash showing while ubuntu boots, not in the back of grub. ;)

I think what you're after is [USplash](http://wiki.nanofreesoft.org/index.php/UsplashHowDoesItWork). It shows a nice splash with a progress bar while booting.

To install it, do this:
[list=1]
[*]Create a folder on your desktop named **usplash**
[*]Download the [usplash deb file](http://kalatlug.nanofreesoft.org/Projects/usplash/snapshots/usplash_0.1preview_i386.deb), the [lib++dfb deb file](http://kalatlug.nanofreesoft.org/Projects/usplash/libraries/lib++dfb/lib++dfb-0.91_22-1_i386.deb) and the [libdirectfb deb file](http://kalatlug.nanofreesoft.org/Projects/usplash/libraries/libdirectfb/libdirectfb-0.9-22_0.9.22-1_i386.deb) into your newly created directory
[*]Open a terminal and run this: **sudo dpkg -i ~/Desktop/usplash/*.deb** . This will install and configure usplash for you
[*]Delete the usplash folder on the desktop (optional)
[/list] 

And that's really all that should be needed. At least that's all I needed to do. :)

**EDIT//** libdirectfb-0.9-22 apparantly wasn't in the repositories sorry about that. =/

Also, if you are like me and are using kubuntu, you might want to [use this](http://www.kde-look.org/content/show.php?content=22714).

---

### Post by jonny on 2005-04-09
[QUOTE=Joh_]**sudo apt-get install libdirectfb-0.9-22**
[/QUOTE]What repositories do you have enabled?  I'd like to try this but have nothing later than 0.9-20 available in my sources.

On an unrelated note, you can easily create your own background image for grub once you have grubconf installed.  Open your picture in the Gimp, resize it to 640x480 pixels (Image --> Scale image)  and restrict it to 14 colours (Image --> Mode --> Indexed).  Save it as a .xpm file, and then use grubconf to link to it.

---

### Post by Joh_ on 2005-04-09
[QUOTE=jonny]What repositories do you have enabled?  I'd like to try this but have nothing later than 0.9-20 available in my sources.

On an unrelated note, you can easily create your own background image for grub once you have grubconf installed.  Open your picture in the Gimp, resize it to 640x480 pixels (Image --> Scale image)  and restrict it to 14 colours (Image --> Mode --> Indexed).  Save it as a .xpm file, and then use grubconf to link to it.[/QUOTE]
I've just got the standard ones, main, restricted and universe and multiverse. :)

---

### Post by Joh_ on 2005-04-09
Now that I think of it, I might have downloaded libdirectfb-0.9-22 from the same place as the other files. If you really can't find it in the repositories, download this one instead and place it with the others before installing them. :)

[http://kalatlug.nanofreesoft.org/Projects/usplash/libraries/libdirectfb/libdirectfb-0.9-22_0.9.22-1_i386.deb](http://kalatlug.nanofreesoft.org/Projects/usplash/libraries/libdirectfb/libdirectfb-0.9-22_0.9.22-1_i386.deb)

---

### Post by timczer on 2005-04-09
The libdirectfb-0.9-22 can be downloaded from the usplash web site.  It isn't in the repositories.

---

### Post by Joh_ on 2005-04-09
[QUOTE=timczer]The libdirectfb-0.9-22 can be downloaded from the usplash web site.  It isn't in the repositories.[/QUOTE]
So I noticed, sorry about that. I have edited my post so it should all be fine now.

---

### Post by ioliver on 2005-04-10
I've installed usplash, but at both boot time and shutdown I lose the picture. My monitor complains that the signal is out of range (it maxes out at 1280x1024 at 70Hz).

Any idea where on this forum usplash can be discussed now that the hoary development section is closed?

Thanks

Ian

---

### Post by brujoquizz on 2005-04-10
Very very very very pleased!!  :-D  :-D  :-D 

I downloaded a couple of packages that usplash ask me for:

- libstdc++6  from  [http://packages.ubuntu.com/hoary/base/libstdc++6](http://packages.ubuntu.com/hoary/base/libstdc++6)

- gcc-4.0-base  from  [http://packages.debian.org/experimental/devel/gcc-4.0-base](http://packages.debian.org/experimental/devel/gcc-4.0-base)

and the usplash works very good.

Where can I download differents splash screens?¿?  :-D  :-D  :-D 

Thank you very much!!

---

### Post by ioliver on 2005-04-10
Hmmm, I tried vga=792 using a VGA lead rather than DVI, and it works.

So I guess my problem is that -
Hoary final with,
kernel option vga=792,
on a Saphire Radeon 7000 (aka 7000 VE),
connected to a AG Neovo F-419 via DVI,
gives a blank screen, 1) During boot, 2) during shutdown, 3) on different virtual consoles while running.  Display is fine while X is in control. The monitor reports "Input signal out of range".

I guess there is no point reporting this on bugzilla until the Ubuntu usplash project is underway for Breezy?

Ian

---

### Post by Goshawk on 2005-04-10
Wait... there is a lot of confusion about "usplash" and sory for that.. i'm the guilty.
What you are using now is an old 0.1preview i think while a 0.1 relase is ready but not relased.
The problem is that we can't relase it because "usplash" is a project thought by ubuntu developers and when i started to build the program that you call "usplash" there was, like now, no any official code of usplash, bu just an idea, so i caleld it usplash.. now we are waiting for ubuntu developer's consensus to relase it. (it is not a splashboot only for ubuntu but for any system-v like systems).
We are discussion in these days if it's the case of change the name of the program...

but go to your problem:
Usplash, or better, this program uses framebuffer, you have to add (it is added automatically) the correspondent vga= where the value is an integer like 792 (792 for 1024*768, that is native resolution, all compatible vesa resolutions are compatible).

---

### Post by XDevHald on 2005-04-10
What if you don't have grubconf?

I get the following error when trying to install grubconf...

Package grubconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grubconf has no installation candidate

---

### Post by ioliver on 2005-04-11
I have the vga=792 on my kernel boot line and it's this that's causing problems.

no "vga-792" and my monitor works with VGA or DVI.
"vga=792" and my monitor works with VGA but with the DVI lead I get the blank screen and "Signal out of range" error.

I guess the kernel's framebuffer stuff can't handle a Radeon 7000 with a DVI connection.

Ian

---

### Post by Goshawk on 2005-04-11
I don't know yet how to handle a DVI connector, I'll study about that, thanks for the feedback... and if you will get a framebuffer please say me how you did that:
Usplash, that is now renamed as Splashy (wiki.nanofreesoft.org) just work if a framebuffer is active, and if you get it you will have Splashy....

---

