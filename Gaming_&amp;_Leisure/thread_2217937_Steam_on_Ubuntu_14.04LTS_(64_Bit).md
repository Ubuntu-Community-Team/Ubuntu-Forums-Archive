---
title: "Steam on Ubuntu 14.04LTS (64 Bit)"
date: 2014-04-19
forum: Gaming &amp; Leisure
---

### Post by shawn-corliss on 2014-04-19
Hi All,
i just installed Ubuntu 14.04 (64 bit) and steam.
When clicking the steam icon nothing happens. 
So I opened the Terminal and ran the steam command. My output was:

kas@Sentinal67:~$ steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140418214302_1.dmp
/home/kas/.local/share/Steam/steam.sh: line 704:  5749 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Installing bootstrap /home/kas/.local/share/Steam/bootstrap.tar.xz
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/kas/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140418214304_1.dmp
/home/kas/.local/share/Steam/steam.sh: line 755:  5866 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-7b941f5e-83cf-4563-b2fa-5f85a2140418
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-7f3146a9-c986-4d1a-a555-ec3582140418

My Specs are: Ubuntu 14.04 LTS
Memory: 7.8GiB
Processor: AMD Phenom II x4 965 processor
video card: Sapphire Radeon HD 5830

I have tryed to installed all of the drivers for my video card and i not quite sure how i can find out more about this error.
Any help would be appreciated.
Scorliss

/******************************Update****************************/
I exectued the command: steam --reset  and rebooted.
Again when launching steam from the icon nothing happens.When i call steam from the terminal i get:
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140418221643_1.dmp
/home/kas/.local/share/Steam/steam.sh: line 755:  2849 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
mv: cannot stat &#8216;/home/kas/.steam/registry.vdf&#8217;: No such file or directory
Installing bootstrap /home/kas/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/kas/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140418221645_1.dmp
/home/kas/.local/share/Steam/steam.sh: line 755:  2975 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Finished uploading minidump (out-of-process): success = yes
response: CrashID=bp-5de73fd3-bf21-4c36-9992-337e92140418

Thanks again.

---

### Post by jbaerboc on 2014-04-19
Have you tried removing steam [uninstalling it] and then re-installing it either from Ubuntu Software Center, Synaptic Package Manager, or from Steam's website [download and install the .deb file by double clicking on it].

---

### Post by shawn-corliss on 2014-04-19
thanks for the reply 
 	[**[COLOR=#000000]jbaerboc[/COLOR]**]("http://ubuntuforums.org/member.php?u=1260320"). I have tryed to install steam from both the Terminal and from the Ubuntu Software Center.
I will uninstall and try from steams website.

---

### Post by shawn-corliss on 2014-04-19
jbaerboc,
that worked. I uninstalled steam and installed it from the steam website. 
Although I'm not quite sure why that worked i am now on my way to test the steam install with DOTA2.
Thanks,
Shawn

---

### Post by sniper-xxx123 on 2014-04-20
[COLOR=#ff0000][SIZE=3]Solution to install and run steam-client for Ubuntu 14.04 LTS[/SIZE][/COLOR]

Steam client need to installed with open-source video-drivers first. 
```
apt-get install steam
```
Now run steam and update it, then exit. 
Now install the properitary video-drivers and reboot.
Now launch steam-client.

---

### Post by Michael_Brown on 2014-04-26
> **sniper-xxx123 said:**
> [COLOR=#ff0000][SIZE=3]Solution to install and run steam-client for Ubuntu 14.04 LTS[/SIZE][/COLOR]

Steam client need to installed with open-source video-drivers first. 
```
apt-get install steam
```
Now run steam and update it, then exit. 
Now install the properitary video-drivers and reboot.
Now launch steam-client.

Thank you, sir!  That fixed it for me on Kubuntu 14.04 with an AMD Radeon HD 5770.

I went to Settings->Driver Manager and switched my vid driver back to the "Using X.Org x server" one.  Rebooted and ran Steam again, and this time it did its full download thing instead of giving me the Segmentation Fault error.  When it's done, I'll set the video drivers back to the fglrx-updates one.

---

### Post by beejunk on 2014-04-28
> **sniper-xxx123 said:**
> [COLOR=#ff0000][SIZE=3]Solution to install and run steam-client for Ubuntu 14.04 LTS[/SIZE][/COLOR]

Steam client need to installed with open-source video-drivers first. 
```
apt-get install steam
```
Now run steam and update it, then exit. 
Now install the properitary video-drivers and reboot.
Now launch steam-client.

I can confirm that this works.  Running Ubuntu Studio 14.04, with an AMD Radeon card.  Steam must be installed before you install the proprietary drivers, otherewise it fails.

---

### Post by alejandro-gime on 2014-07-14
Works! Thanks you!

---

### Post by Peter_Solver on 2014-07-15
When I experienced the same error, it was a graphics driver problem. I only opened the Additional Drivers, chose "Using X.Org X server (open source, tested)" driver, went to Ubuntu Software Center and installed Steam then changed the Graphic driver. It worked on my end.

---

### Post by Noah_Kemmerer on 2015-02-04
i keep getting this 

scaventa@noah-X551CAP:~$ sudo apt get steam
[sudo] password for scaventa: 
scaventa is not in the sudoers file.  This incident will be reported.

---

### Post by Noah_Kemmerer on 2015-02-04
I keep getting this 

scaventa@noah-X551CAP:~$ sudo apt get steam
[sudo] password for scaventa: 
scaventa is not in the sudoers file.  This incident will be reported.

And this 

scaventa@noah-X551CAP:~$ apt-get install steam
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by efflandt on 2015-02-05
> **Noah_Kemmerer said:**
> i keep getting this 

scaventa@noah-X551CAP:~$ sudo apt get steam
[sudo] password for scaventa: 
scaventa is not in the sudoers file.  This incident will be reported.

The original user set during install should be able to use sudo. If **scaventa** is an added user, some user that can do sudo needs to add you to group sudo so it shows up in your groups. Technically I think you are supposed to use **sudo vigr** to do that (users in a group are comma separated list with no spaces), but if only one user is on the machine at the time I have done that with **sudo nano /etc/group**.```
efflandt@XPS-8100-1404:~$ groups
efflandt adm cdrom sudo dip plugdev lpadmin sambashare
```

---

### Post by Bucky Ball on 2015-02-05
You should be using this:

```
sudo apt-get install steam
```

Welcome. This is an old thread and the original problem is solved. To improve your chances of getting help, please post a new thread detailing your issues, if you have any more problems. Thanks and good luck.

---

### Post by HeroCC on 2015-03-29
> **Noah_Kemmerer said:**
> I keep getting this 

scaventa@noah-X551CAP:~$ sudo apt get steam
[sudo] password for scaventa: 
scaventa is not in the sudoers file. This incident will be reported.

And this 

scaventa@noah-X551CAP:~$ apt-get install steam
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
This is not a problem with steam, for some reason you aren't allowed to sudo. Try this: [https://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line](https://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line)

---

