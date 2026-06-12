---
title: "Steam won't open on 16.04"
date: 2016-10-15
forum: Gaming &amp; Leisure
---

### Post by westparkgirl on 2016-10-15
I'm new to Ubuntu and am just trying to learn the ropes...my husband finally convinced me to install it on my laptop :P  
So, I installed Steam on my computer and it won't open.  It just flashes blue for a minute then stops.  I have no idea what is wrong and no clue how to figure it out.  Any help would be really appreciated.  And, please use as simple instructions as possible since I'm a newbie.
Thanks :mrgreen:

---

### Post by deadflowr on 2016-10-15
*Thread moved to **Gaming & Leisure**.*

---

### Post by oldrocker99 on 2016-10-16
Did you install Steam from the website or from the Ubuntu repositories? Installing from the repositories is the only way to get Steam running. If you did install Steam from the website, try this:

```
sudo apt-get install synaptic
```
Run Synaptic and search for steam. When it comes up, right-click the box and select "complete removal."

Then, ```
sudo apt-get install steam
``` and you should be OK. If you **did** install it from the repositories, uninstall it the same way and also remove the hidden .steam folder in your home directory, then install Steam from the terminal again.

Good luck!

---

### Post by westparkgirl on 2016-10-16
Thank you so much for your clear answer.  I followed your steps (I did install Steam from the website), but when I put in the code   sudo apt-get install steam   I got this message:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by oldos2er on 2016-10-16
Close Synaptic, then re-run the command. There can only be one package manager front-end (i.e. apt-get or Synaptic) open at a time.

---

### Post by westparkgirl on 2016-10-16
Ok, so I did that. It installed..thank you ;)  But, it still won't open.  When I try to open it now, it pulses black for a minute and shuts back down.

---

### Post by oldrocker99 on 2016-10-17
OK, try this:```
steam
```

Post the results here.

---

### Post by westparkgirl on 2016-10-17
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
[2016-10-17 11:46:21] Startup - updater built Oct 13 2016 00:47:16
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)

---

### Post by oldrocker99 on 2016-10-17
OK, an X error suggests a graphics problem. What is you graphics chip? Post the results of```
lspci | grep VGA
```

---

### Post by westparkgirl on 2016-10-17
Ok.  Here is what I got:

01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)

---

### Post by oldrocker99 on 2016-10-17
OK, you might be in luck, if you haven't yet installed the nVidia drivers. Do this first:```
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update
```


Then you can install one of several nVidia drivers from within Synaptic. I sincerely hope this works for you.

---

### Post by westparkgirl on 2016-10-18
So, I did what you said.  It all seemed to install.  I went into Synaptic and installed a Nvidia driver.  When I tried to run Steam again, it installed updates then the message "glXChooseVisual failed"  Any idea what happened?  Did I install the wrong driver?  There are a pile of them there.  I typed   <ubuntu-drivers devices | grep recommended>    into the terminal and it told me      < driver   : nvidia-370 - third-party free recommended>      so, that's the one I installed..

---

### Post by westparkgirl on 2016-10-18
Just an update to what I did.  When I tried to use my computer this morning, it refused to go past the login screen.  So, I googled the problem and found out it was a problem with my driver.  I used ctrl - alt - F1  and put in a code to purge Nvidia...at least that's what I think it meant, haha.  Anyway, it worked and I'm able to use my computer again.  But, clearly I did something wrong when I installed the driver.  I have no idea where I'm at now....

---

### Post by oldrocker99 on 2016-10-18
Hmmm. I use 3.70 myself with no problems. Try this and see (gulp) if it works:```
sudo apt-get purge nvidia
```

Then try installing 3.70 again.

Best of luck to you. And don't ever be afraid of asking questions here. These forums are a **community**, and virtually everything you need to know is to be found here.

---

### Post by westparkgirl on 2016-10-18
Ok.  I did that code.  Thank you :)  Before I try the driver again, which one do I install?  Is it nvidia-370  or   nvidia-370-dev   ?

---

### Post by exsheeple on 2016-10-18
Im getting the same error.  Here's what I got:
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4250]

---

### Post by exsheeple on 2016-10-18
> **oldrocker99 said:**
> OK, try this:```
steam
```

Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

---

### Post by oldrocker99 on 2016-10-19
> **westparkgirl said:**
> Ok.  I did that code.  Thank you :)  Before I try the driver again, which one do I install?  Is it nvidia-370  or   nvidia-370-dev   ?

You donn't need the -dev driver; that's for programmers and advanced users. You just need the 3.70 driver.

It looks like your problem might just be solved (polishes fingernails)! If it is, please mark this thread as [SOLVED].

---

### Post by oldrocker99 on 2016-10-19
I'm not an ATI users, but you do have a newer chipset. This may just help you (driver link):[http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx).

Good luck and keep the results coming.

---

### Post by westparkgirl on 2016-10-19
I really appreciate all your help.  I tried installing the driver again.  It messed up my computer even worse.  I got stuck in a login loop again and purging nvidia didn't help.  I tried some codes that I found online to fix it, but things went from bad to worse.  In the end, my computer refused to boot.  It just got stuck on the purple ubuntu screen.  So, I finally gave up and wiped ubuntu and installed Linux Mint Cinnamon.  So far, I'm liking this OS better overall.  But, I'm afraid to try to install any drivers again.  I'm thinking of just giving up on using Steam on my computer.

---

### Post by exsheeple on 2016-10-19
[IMG]http://cloud.1158pm.info/images/steamerror.png[/IMG]
When ran the command steam.real in the terminal I got the above error message

---

### Post by oldrocker99 on 2016-10-19
steamui.so can be found in ```
~/.local/share/Steam/ubuntu12_32/
```

as well as in ```
~/.steam/ubuntu12_32/
```

If Steam can't find it, and it is in both directories, it is a bigger problem, which may be a questionable Steam installation. You can try deleting the /home/username/.steam folder (easiest to use a file manager to do this) and restart Steam. It **should** load the latest version, and you'll have to reinstall your games. Hate to be the bearer of bad news...

---

### Post by exsheeple on 2016-10-19
after removing the .steam folder, I restart Steam.  I get the Steam Install Agreement.  I click Ok.  The agreement disappears and nothing happens.  Heres the output from the terminal:

gamebuntu@gamebuntu-one:~$ steam
Repairing installation, linking /home/gamebuntu/.steam/steam to /home/gamebuntu/.local/share/Steam
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

---

### Post by ezlovin on 2017-04-20
Hey, i was wondering if someone could help me im knew to all this i read all the other post. None helped so i thought u could help me. When i double click steam its pops up on my task bar blue then after 1 min it goes and nothing!
steam
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

---

### Post by Perfect Storm on 2017-04-21
> **ezlovin said:**
> Hey, i was wondering if someone could help me im knew to all this i read all the other post. None helped so i thought u could help me. When i double click steam its pops up on my task bar blue then after 1 min it goes and nothing!
steam
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

See if this help: [https://askubuntu.com/questions/541343/problems-with-libgl-fbconfigs-swrast-through-each-update](https://askubuntu.com/questions/541343/problems-with-libgl-fbconfigs-swrast-through-each-update)

---

### Post by ralphsvd on 2017-06-09
Hi I get the same error (00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8610G])

Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

Do I have any hopes to get steam to work? or I will have to get a better computer?

---

