---
title: "Disabling Desktop Effects from the command line"
date: 2007-04-22
forum: Desktop Environments
---

### Post by Leslie Viljoen on 2007-04-22
Hi all

I am using Feisty.

I enabled Desktop Effects on an old NVidia GeForce2 Pro. I'm sure Ubuntu uses the newer NVidia driver which removed support for my card. Anyway, Gnome hangs completely before I even get to the login screen, so I have to start in safe mode by pushing ESC at the GRUB menu. Then I changed my driver from NVIDIA to NV again in xorg.conf. Now I can get to the Gnome login screen, but after I log in I get a blank brown screen and a moveable mouse pointer and nothing else.

How do I revert back to before enabling Desktop Effects FROM THE COMMAND LINE? I have tried dpkg-reconfigure xserver-xorg. I have also tried metacity --replace --display=localhost:0, but it says it can't connect to my x server.

I find it a bit poor that it has been so hard to fix this.

Leslie

---

### Post by Leslie Viljoen on 2007-04-22
I have now installed the proper nvidia-glx-legacy driver, but I still get the blank brown screen. From other posts I see it may be related to network or sound card drivers. Has anyone solved this?

I still think there needs to be a command line command like this: "desktop-effects-disable".

---

### Post by exvision on 2007-04-22
Hey Leslie,

I'm having the same problem.  Please let me know if you come across a solution, and I'll do the same.

Cheers.

---

### Post by exvision on 2007-04-22
Hi Leslie,

I've found a solution that works for me.

I had to add the following to xorg.conf

Section "Extensions"
            Option "Composite" "Disable"
EndSection

---

### Post by Leslie Viljoen on 2007-04-22
Alright. I have an inconvenient work-around for the problem I am having.

To recap:

1. I disabled Desktop Effects by reverting to the "nv" driver
2. I try to log in
3. Instead of the starting up icon bar, I get a blank brown screen, and eventually a greay block on the top left of the screen
4. The mouse works, but nothing else happens

To fix, I need to create a new user and use that. If I use the graphical users and groups tool to create the user, the new account has the same blank screen problem.

Here's what I do:

1. Exit my session with ctrl-alt-backspace
2. Go to command line with ctrl-alt-f1
3. Log in as my admin user
4. sudo su
5. useradd -m <new username>
6. passwd <new username>     (and set a password)
7. ctrl-alt-f7 to get back to the logon screen
8. Log in as new user

The problem is not group membership - I have verified that. It's some other secret thing that the graphical user manager does and useradd does not.

Once your new user is created you can copy your old user directory's files across.


Les

---

### Post by davidmorawski on 2007-07-14
Back from the dead...

I just enabled Desktop Effects for the first time, and it seemed to work until I enabled the "Cube" effect. This caused my entire system to hang to the point where I couldn't even stop the X server.
> **exvision said:**
> 
I had to add the following to xorg.conf

Section "Extensions"
            Option "Composite" "Disable"
EndSection
This work-around solved my problem, temporarily, but I'd like to see if I can test out Desktop Effects without the Cube effect (as I'm not sure if that will still crash).

Have there been any developments in turning off Desktop Effects from the command-line? I can no longer access System->Preferences->Desktop Effects ("The Composite extension is not available") due to adding the above lines to xorg.conf.

I feel like there should be a fairly easy way to control these options..the system preference is merely a GUI front-end for something, isn't it?


Dave

---

### Post by wevsler on 2007-07-15
Here's how I got around it. 

Go to command line with ctrl-alt-f1 - this opens a terminal
Login to the account that was enabled for desktop effects

remove the following files by typing:
rm -rf .gnome 
rm -rf .gnome2 
rm -rf .gconf 
rm -rf .gconfd 
rm -rf .metacity

This resets the entire desktop and disables desktop effects

---

### Post by skuli.arnlaugsson on 2007-09-03
rm -rf *the files listed above

Did not solve my problem.

Anyone else had this problem?

---

### Post by mollison on 2007-09-03
rm -rf *the files listed above DID solve the problem for me.

Thanks, wevsler.

---

### Post by mzungu2 on 2007-09-08
I enabled desktop effects on my only admin account (ooops) and got the previously mentioned blank screen. Could login normally with other userID's.

A solution from another thread helped me ([http://ubuntuforums.org/showthread.php?t=494947):](http://ubuntuforums.org/showthread.php?t=494947):)

I logged into failsafe terminal and uninstalled desktop effects:
sudo apt-get remove --purge compiz-core desktop-effects

At next "normal" login the blank screen was gone, and my normal desktop was back.
I haven't re-installed desktop-effects, as I don't want a menu option that enables a "blank screen". I might give it another try later - e.g. if I upgrade to a newer machine!

---

### Post by freeflyer57 on 2007-09-24
rm -rf *the files listed above worked for me! I just got my new computer and wanted to see whether or not it could handle the effects. I guess it has some work left. Thanks a lot. I thought I was a goner for sure.

---

### Post by maddentim on 2007-10-07
thanks for the instructions on removing the packages.  That did the trick.

---

### Post by Baltazar72 on 2008-05-26
I did enable some settings in compizconfig settings manager (in Ubuntu Hardy 8.04) which messed up my screen, and I could not see anything but "white" windows ... I was searching around to find an solution to "disable desktop effects" .. what worked for me was this :

You have to type this "blindfolded", but that worked for me :

Press ```
Alt+F2
``` (opens Run Application dialouge)
Type : ```
gnome-terminal
``` (this opens up the terminal window)
Type : ```
metacity --replace
``` (this disables compix)

And I was back :)

Now I could open up compizconfig settings manager, and disable the effect that caused the error, and enable Extra visual effects again .... PS: the setting caused my problems was "bicubic filter"

hope this can help somebody else.

---

