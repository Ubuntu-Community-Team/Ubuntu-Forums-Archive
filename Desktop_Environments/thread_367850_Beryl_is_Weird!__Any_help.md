---
title: "Beryl is Weird!  Any help?"
date: 2007-02-22
forum: Desktop Environments
---

### Post by yerdon on 2007-02-22
Hey people, I just installed Beryl and I just don't get it.

It seemed that it just turned off all of the title bars on the applications.  So I cannot maximize/minimize or close a window except through keyboard or menu shortcuts.  

Am I missing something?  Why would Beryl take the borders off of the windows?  I think it must be a misconfiguration...

Thanks!

Joseph

---

### Post by louis_nichols on 2007-02-22
The reason it takes the titlebars is that it needs to replace them, but something prevents it. Try using the option "Reload window manager" in the beryl-manager right-click menu. If it doesn't work, try tweaking the settings under "Advanced beryl options"

It might be a bug, though. In which case there isn't much you can do, really. Except to wait for the developers to fix it. What version of Beryl are you using? It's not an svn one, I hope...

---

### Post by yerdon on 2007-02-22
That makes sense.  

I tried doing what you suggested, but it didn't help.  Under the Advanced Beryl Options it is all set to "Automatic".

I'm not sure what my version is, but I installed it with: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia")

Thanks again!

Joseph

---

### Post by yerdon on 2007-02-22
I think maybe I don't have any Theme chosen.  But I don't know where to do that.  I can see a bunch of themes in the "Emerald Theme Manager", but I can't seem to choose one...

Any help would be greatly appreciated!

Joseph

---

### Post by astoltz on 2007-02-22
It sounds like Emerald is not running.  right-click on the beryl-manager icon, then click on select window decorator.  From there you should be able to select Emerald.

---

### Post by naxmul on 2007-02-22
im having a problem with beryl as well. im a windows user, and wanted to give beryl a try. 
i tried [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX) and im pretty sure i didn't know what i was doing. i followed all the instructions, and now when i try to run beryl, i get something like this. the manager comes up, i restarted Gnome. ionno whats wrong. not really a linux user..........so, help a newbie out?

```
$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
$
```

---

### Post by louis_nichols on 2007-02-23
> **naxmul said:**
> im having a problem with beryl as well. im a windows user, and wanted to give beryl a try. 
i tried [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX) and im pretty sure i didn't know what i was doing. i followed all the instructions, and now when i try to run beryl, i get something like this. the manager comes up, i restarted Gnome. ionno whats wrong. not really a linux user..........so, help a newbie out?

```
$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
$
```

In your case, it looks like you don't have the NVIDIA driver installed. You can install that via synaptic then try again.

As for the OP, here's one thing to try: after starting beryl, while you don't have window borders, open a terminal window and type:

```
emerald --replace
```

If it works, good. Otherwise, it should display some error that might be helpful in solving this. Do other aspects of Beryl work? I mean, transparent windows, woblly windows...

---

### Post by yerdon on 2007-02-23
Hi, thanks for your help on this!

I tried running that command (emerald --replace), but terminal just hangs and doesn't seem to do anything.  No response and doesn't return me to the prompt...

I also tried going to the "Select Window Decorator", and the only selection was "Standard Beryl Decorator (Emerald), which was already selected.

I'm seeing some interesting features like mini-screenshots when I hold my mouse over the tabs and it does the "wobbly" thing if I click on it to minimize or maximize it.  However, I'm not seeing any transparency...

Any other suggestions?

Thanks again for your help!

Joseph

---

### Post by naxmul on 2007-02-23
i actually got beryl working so smoothly. all i had to do was log out, and switch my session. stupid me >.>

but, YAY, i got it working!!!! beryl is much much more better than those vista effects. this is awesome.

---

### Post by louis_nichols on 2007-02-23
> **yerdon said:**
> Hi, thanks for your help on this!

I tried running that command (emerald --replace), but terminal just hangs and doesn't seem to do anything.  No response and doesn't return me to the prompt...

I also tried going to the "Select Window Decorator", and the only selection was "Standard Beryl Decorator (Emerald), which was already selected.

I'm seeing some interesting features like mini-screenshots when I hold my mouse over the tabs and it does the "wobbly" thing if I click on it to minimize or maximize it.  However, I'm not seeing any transparency...

Any other suggestions?

Thanks again for your help!

Joseph

OK. Those mini windows mean beryl is working. They are thumbnails. Now, why wouldn't it load emerald?... :-k the frustrating thing is I had the exact same problem once and I don't remember how I fixed it. I can't reproduce it either...

I have an idea. It's a long shot, but worth trying. Please go to System>Preferences>Sessions then choose the tab Current session and make a screenshot of it and post it here, Please make sure that the whole list of applications is visible.

---

### Post by yerdon on 2007-02-23
Here is is.  Thanks for your help!

Joseph

---

### Post by louis_nichols on 2007-02-23
OK. It is as I suspected. Now, I think this should work: see that entry 'metacity' over there?. Select it, then click "Remove" and then "Apply".

After this, right click on the beryl icon in the system tray and select "Reload window decorator" and/or "Reload window manager" (the first one should be enough, though)

---

### Post by yerdon on 2007-02-23
Hmmm.  I see what you mean, unfortunately it wasn't that.  When I switch "Select Window Manager" back to Beryl, the "Metacity" entry disappears.

Now, this is what it looks like.  Is it missing something for Emerald?

Thanks!

Joseph

---

### Post by louis_nichols on 2007-02-23
Yes. I wasn't very attentive the first time. It is pretty obvious from your first screenshot that metacity runs as the window manager. Emerald doesn't show up in session manager for me either.

Unwillingly, I managed to replicate your situation. I killed and restarted my window manager so many times in so many ways that at one point emerald didn't start. I solved that by right-clicking beryl icon and selecting "reload window decorator". I dunno if that will work for you, though.

---

### Post by louis_nichols on 2007-02-23
I just noticed another thing that could be the problem

When you open Beryl settings manager, there is a tab called "Visual effects", which contains an option called "Window decoration". That should be checked.

---

### Post by Nano Geek on 2007-02-23
If you have a nvidia card and if you are using the non-opensource drivers, run this command.```
sudo nvidia-xconfig --add-argb-glx-visuals
```Then hit **<CTRL><ALT><Backspace>** and log back in again. That should fix your problem.

---

### Post by yerdon on 2007-02-23
Hi, I tried both suggestions and still nothing.  

I noticed that the last suggestion edited the "/etc/X11/xorg.conf" file.  Is there any other file that might be misconfigured?  

Is there a way for somebody to export the Beryl settings and then have me import them?

Any other ideas?

Thanks,

Joseph

---

### Post by Nano Geek on 2007-02-23
Here are my settings, but I'm not sure that Beryl setting are your problem. To import the settings use the Import button on the lower lefthand corner of the Beryl Settings Manager.

---

### Post by shareMenaPeace on 2007-02-23
Could someone tell  me please how i know which nvidia driver i have (closed or open?).
I used envy install script.

I run fine with beryl but just want to know how i find out which driver i have actually.

Thanks

---

### Post by yerdon on 2007-02-24
Thanks for that.  I imported the settings, but it didn't help, as you thought.

Any other ideas anybody?  Why would I be missing the borders on my windows?  How can I tell if Emerald is actually loaded and running in addition to Beryl?  Or are they the same thing?

Thanks!

Joseph

---

### Post by Nano Geek on 2007-02-24
You could try reinstalling the nvidia driver using```
sudo apt-get build-dep nvidia-glx
``` Going to the [Nvidia driver site]("http://www.nvidia.com/object/unix.html") and downloading the driver, hiting <CTRL><ALT>F1, login, typing ```
sudo /etc/init.d/gdm stop
```then running the downloaded file with ```
sudo sh /path/to/the/file/NVIDIA-Linux-x86-1.0-version#-pkg1.run
```
Run ```
sudo nvidia-xconfig --add-argb-glx-visuals
```
Then restart

---

### Post by TimJBart on 2007-02-24
> **asjdfwejqrfjcvm msz34rq33 said:**
> If you have a nvidia card and if you are using the non-opensource drivers, run this command.```
sudo nvidia-xconfig --add-argb-glx-visuals
```Then hit **<CTRL><ALT><Backspace>** and log back in again. That should fix your problem.

I LOVE YOU I LOVE YOU I LOVE YOU

Thank you very much this fixed my problem.   I now have maximize, minimize and themes!!!  whoooooooooo

---

### Post by astoltz on 2007-02-24
> **shareMenaPeace said:**
> Could someone tell  me please how i know which nvidia driver i have (closed or open?).
I used envy install script.

Open a terminal and put in:```
cat /proc/driver/nvidia/version | grep NVIDIA

```

---

### Post by Rippy on 2007-02-24
Hi, I'm having the identical problem. There's a black border around my windows, and whenever I maximize or minimize a window my taskbars go white, and I need to blindly feel around for the beryl icon (try places until the rollover for beryl shows up) to reset it.

The difference is, I have an ATI radeon 9200 pro, so reinstalling the drivers isn't going to work for me.

I followed this guide for setting up my drivers (using the open-source one):
[https://help.ubuntu.com/community/RadeonDriver#head-7e2283943de094f4c373154f2e8178bfa9374050](https://help.ubuntu.com/community/RadeonDriver#head-7e2283943de094f4c373154f2e8178bfa9374050)

And looked over this guide, adding the device option found about halfway down the page which says is to fix window border problems for ATI users (yeah, got my hopes up when I added it, but it didn't help):
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX)

Any ideas?

Thanks!

-Rippy

Edit: basically, it just doesn't handle transparency. For example, opacity-related effects just fade to black instead of becoming transparent.

---

### Post by yerdon on 2007-02-26
> **asjdfwejqrfjcvm msz34rq33 said:**
> You could try reinstalling the nvidia driver using```
sudo apt-get build-dep nvidia-glx
``` Going to the [Nvidia driver site]("http://www.nvidia.com/object/unix.html") and downloading the driver, hiting <CTRL><ALT>F1, login, typing ```
sudo /etc/init.d/gdm stop
```then running the downloaded file with ```
sudo sh /path/to/the/file/NVIDIA-Linux-x86-1.0-version#-pkg1.run
```
Then restart

I followed these instructions, and this is what happened:

Everything went well until I attempted to install the NVIDIA driver.  It loads and then tells me:

No precompiled kernel interface was found to match your kernel; would you like the installer to attemp to download a kernel interface for you kernel from the ftp site ([ftp://download.invidia.com)?](ftp://download.invidia.com)?)

I answer "Yes".  It apparently looks and then comes back with:  

No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel.

I press "OK" and it "builds the kernel module".  Then it tells me:

WARNING: nvidia-installer was forced to guess the X library path 'usr/lib' and X module path '/usr/lib/xorg/modules'; these paths were not queryable from the system.  If X fails to find the NVIDIA X driver module, please install the 'pkg-config' utility and the X.Org SDK/development package for your distribution and reinstall the driver.

It then asks me if I would like to run the nvidia-xconfig utility to update my configuration.  I say Yes.  It tells me that the install was completed successfully.  

I then enter "sudo /etc/init.d/?dm restart and log back in.  I can tell that the new driver is in place because the NVIDIA screen looks very different.  The colors and the screen all look better now. However, I still have the same problem I was having all along with not seeing the borders around the windows when Beryl is loaded.

Worse yet, when I restart the computer, I get an error:

Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?

I say "yes" and it shows me some sort of a log.  The first error I see is:

Error: API mismatch: the NVIDIA kernel module has the version 1.0-7184, this X module has the version 1.0-9746.  Please make sure that the kernel module and all NVIDIA driver components have the same version.  The rest of the errors seem to be related to this one.

The only way around it, is to say "no" to seeing the log several times and then it will return me to the command prompt.  I log in and run "sudo modprobe -r nvidia" to unload all nvidia drivers and then I can run "sudo /etc/init.d/?dm restart" which restarts the GUI.  But obviously my driver installation is hopelessly messed up.

If I revert to the legacy version of the driver (7184) and restart the computer, it runs fine - but on the legacy driver.

What can I do to completely clean out all components of the legacy driver?  

Or is there anything else I should be doing?

Thanks for all your help!

Joseph

---

### Post by hyuganet on 2007-02-26
I'm having similar problems. I was getting the no menubar problem, and I tried a number of things like --add-argb-glx-visuals but no avail. Since I had a fairly fresh install of Edgy, I decided to do an update, and in the process xorg was updated. Now whenever Beryl launches, X is restarted. This is getting really frustrating. Anyone able to help?

---

### Post by Leeghoofd on 2007-02-26
I'm not sure if this post is of any use to anyone here, but I have had the same problem with beryl under PCLINUXOS, weird thing is that bery is working under ubuntu without any flaws.

I was able to solve this problem by switching an underlying graphic support. In PClinuxos you had two options:
XGL
AIGLX (recommended) 

Now it ownly worked with XGL for me ( dont ask me why ) 

For ubuntu there appears to be two installation manuals: 

[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

Check the link and see if there is anything usefull for you there. Good luck !

---

### Post by yerdon on 2007-02-26
No luck with that.  If I choose XGL instead of Automatic, it freezes me up.

Anyway, I'm pretty sure that I somehow have two versions of the NVIDIA driver installed on my system.  Does anybody know what I can do to clean out the Legacy drivers (and possibly Kernel) completely from my system?

---

### Post by Nano Geek on 2007-02-26
> **yerdon said:**
> No luck with that.  If I choose XGL instead of Automatic, it freezes me up.

Anyway, I'm pretty sure that I somehow have two versions of the NVIDIA driver installed on my system.  Does anybody know what I can do to clean out the Legacy drivers (and possibly Kernel) completely from my system?Try ```
sudo apt-get remove --purge nvidia-kernel-common
```restart, and repeat my above steps.

---

### Post by yerdon on 2007-02-26
> **asjdfwejqrfjcvm msz34rq33 said:**
> Try ```
sudo apt-get remove --purge nvidia-kernel-common
```restart, and repeat my above steps.

Beautiful.  This worked.  Thanks!

Now I'm back with my original question.  When I run Beryl as the "Window Manager", my windows do not have a border.  

I'm now sure that I have the most updated NVIDIA drivers, so that isn't the issue.

Any other things to try?

---

### Post by Nano Geek on 2007-02-26
> **yerdon said:**
> Beautiful.  This worked.  Thanks!

Now I'm back with my original question.  When I run Beryl as the "Window Manager", my windows do not have a border.  

I'm now sure that I have the most updated NVIDIA drivers, so that isn't the issue.

Any other things to try?I forgot one more thing. Do```
 sudo nvidia-xconfig --add-argb-glx-visuals
```reboot, and try again.

---

### Post by rainwalker on 2007-02-26
If all else fails, you could re-install Beryl. I used the guide at [https://help.ubuntu.com/community/BerylOnEdgy](https://help.ubuntu.com/community/BerylOnEdgy) and everything works for me.

---

### Post by yerdon on 2007-02-27
> **asjdfwejqrfjcvm msz34rq33 said:**
> I forgot one more thing. Do```
 sudo nvidia-xconfig --add-argb-glx-visuals
```reboot, and try again.

THAT WAS WHAT IT TOOK! 

Thank you to you and everyone who offered support.  This looks awesome!

Joseph

---

### Post by Nano Geek on 2007-02-27
Your welcome

---

### Post by Catholicnerd on 2007-03-11
> **louis_nichols said:**
> I just noticed another thing that could be the problem

When you open Beryl settings manager, there is a tab called "Visual effects", which contains an option called "Window decoration". That should be checked.

That's what finally did it for me!

---

### Post by Claywell on 2007-03-13
Just wanted to say thanks.  Been having a time with Beryl, then found this thread and now everything is working well.

---

### Post by nalmeth on 2007-04-22
> **yerdon said:**
> THAT WAS WHAT IT TOOK! 

Thank you to you and everyone who offered support.  This looks awesome!

Joseph
That did it for me too. Fixed missing emerald after enabling beryl.

---

