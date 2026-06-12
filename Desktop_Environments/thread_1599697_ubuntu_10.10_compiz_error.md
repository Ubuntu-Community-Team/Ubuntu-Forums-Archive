---
title: "ubuntu 10.10 compiz error"
date: 2010-10-18
forum: Desktop Environments
---

### Post by ardunarda on 2010-10-18
hello everyone. I am recently upgrade my ubuntu from 10.04 to 10.10. I love to 10.10 because it recognize my touch pad and it is very smooth. Anyway couple of days ago when open my laptop only desktop background picture showed up. Then i looked forums i solve this problem with uninstalling compiz from command window. Now i want to install compiz but when i thype "compiz" in terminal its output like this
```
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing move options...done
Initializing resize options...done
Initializing place options...done
compiz (core) - Error: Couldn't load plugin 'decoration'
ardun@ardun-K50IN:~$ 

```
Then tile bar of the all windows disappear. Also i can not install compiz-fusion-plugins extra. Error is 
```
sudo aptitude install compiz-fusion-plugins-extra
[sudo] password for ardun: 
The following NEW packages will be installed:
  compiz-fusion-plugins-extra{b} 
0 packages upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
Need to get 0B/3,645kB of archives. After unpacking 10.5MB will be used.
The following packages have unmet dependencies:
  compiz-fusion-plugins-extra: Depends: compiz-core-abiversion-20091102 which is a virtual package.
Internal error: found 2 (choice -> promotion) mappings for a single choice.
Internal error: found 2 (choice -> promotion) mappings for a single choice.
Internal error: found 2 (choice -> promotion) mappings for a single choice.
Internal error: found 2 (choice -> promotion) mappings for a single choice.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     compiz-fusion-plugins-extra [Not Installed]        



Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```
Also when i try to change visual effect of background i get error
"Desktop effects could not be enabled"
My laptop is asus K50IN graphic card is nvdia g102m. Thank you for reading

---

### Post by ardunarda on 2010-10-18
any help i have surfed on forums but i cant find the solution

---

### Post by ardunarda on 2010-10-18
also here is the my output of the compiz-check

```
 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C79 [GeForce G102M] (rev b1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

---

### Post by Cavsfan on 2010-10-18
I had this exact same problem. Let me see if I can find where I put what I did to correct it.

---

### Post by Cavsfan on 2010-10-18
I believe I found the solution by adding compiz-core from here:

[[COLOR=blue]_http://packages.ubuntu.com/maverick/compiz-core-abiversion-20091102_[/COLOR]]("http://packages.ubuntu.com/maverick/compiz-core-abiversion-20091102")

See if that doesn't fix it. It took me forever to find the solution.

---

### Post by Cavsfan on 2010-10-18
Then I believe I added this through Synaptic: **libcompizconfig0** and it is dependant on compiz-core.

---

### Post by ardunarda on 2010-10-18
thank for your attention. I downloaded deb file at ur first post uninstall my installed compiz-core then installed downloaded deb file. Then i go to synaptic for installation of libcompizconfig0 when it is installed synaptic said that compiz-core have to be upgraded in order to install libcompiz i select yes for this. Now nothing is changed i still can not use compiz-fusion. But what i do not understand actually compiz was run in my laptop first i installed ubuntu 10.10 i do not what is change since then

---

### Post by ardunarda on 2010-10-18
by the way [https://launchpad.net/~compiz/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~compiz/+archive/ppa?field.series_filter=maverick) at the latest update compiz five weeks ago 
Failed to build: amd64 is written is it any relevance between my situation

---

### Post by Cavsfan on 2010-10-18
This is a tough one. I should have made better notes as to what I did to fix it.
When I enter **compiz --version** in terminal I see **compiz 0.8.6**.

What version is your compiz?

---

### Post by ardunarda on 2010-10-18
0.9 is it default for 10.10

---

### Post by Cavsfan on 2010-10-18
Try this as it installs compiz-core before the extras.

First enter this: ```
sudo apt-get purge compiz*
```Then I would reboot before the next step just to make sure.

```
sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core  compiz-fusion-plugins-main compiz-fusion-plugins-extra  compizconfig-backend-gconf

```And that looks a lot like what I did to fix mine. Hope this helps!

---

### Post by Cavsfan on 2010-10-18
OK. I finally figured this out. Version 9 doesn't currently work on Maverick. There are bugs submitted on that. If you still want to use it - get rid 
of those 2 compiz ppa lines in your sources list. They will pull in the version 9 and it will not work. I opened Synaptic entered "compiz" in the 
top right and removed everything that began with compiz. Then I rebooted.

Without the compiz PPAs in my source list, I entered the "sudo apt-get install ...." command from my previous post. It installed a bunch 
of stuff and removed others and presented a list of stuff it recommended 
sudo apt-get compizconfig-settings-manager simple-cssm

And it had a list of things to remove via "sudo apt-get autoremove" once I did all of that I was back to being able to use compiz. But, now the min. max. close buttons are back on the left.
Emerald windows manager was also removed.

So, the bottom line is you have to use 8.6 version for now.

---

### Post by ardunarda on 2010-10-18
i did exactly what u said but when i type ur second command to terminal i get this ```
ardun@ardun-K50IN:~$ sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core  compiz-fusion-plugins-main compiz-fusion-plugins-extra  compizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-core is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 compiz-fusion-plugins-extra : Depends: compiz-core-abiversion-20091102
E: Broken packages

```
anyway i am very pleased to ur effort this remembers me why i use ubuntu

---

### Post by Cavsfan on 2010-10-18
Just refer to my previous post and get rid of those ppas in your source list. I messed it up just like it was when I first installed 10.10 (Like your install is).
And now I have it back to version 8.6 which works. :P

I just enter "compiz" in Synaptic and everything is back to being installed except "fusion Icon", which I installed from there.
I also had to install Emerald from there too or else I could not see min max close buttons. I also like the fusion icon in Cairo Dock 
as I can click on Reload WM to correct any problems with the buttons at the top.

If you are interested in Cairo Dock and do not have that installed go here:
[[COLOR=blue]_http://www.glx-dock.org/_[/COLOR]]("http://www.glx-dock.org/")

But, you should be able to enter "cairo-dock" in Synaptic and get it there. But, I did add a PPA from that website to my sources list.
For future updates.

If this fixes your Compiz, please mark this thread as resolved.

---

### Post by ardunarda on 2010-10-18
i erase all compiz from my source list but still when i want to install them it is installed version 0.9 again anyway i want to than you a lot like i said in my previous post that is why i am using ubuntu. I can wait compiz developer fix this error i think this is not take too much have nice day

---

### Post by Cavsfan on 2010-10-18
If you take the ppas out of your source list (which I think you did) and remove all compiz stuff.
You also have to purge the compiz stuff too.

Check in Synaptic for any thing starting with compiz un-install everything and then reboot.

Then enter 
```
sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core  compiz-fusion-plugins-main compiz-fusion-plugins-extra  compizconfig-backend-gconf
```It should install version 8.6 and you should be good to go. Then go back into Synaptic and enter compiz at the top right and install anything that 
did not get installed and it should work. It did for me.

---

