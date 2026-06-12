---
title: "can't install latest nvidia driver"
date: 2012-06-21
forum: Desktop Environments
---

### Post by bravegag on 2012-06-21
Hello,

I just put together a new Desktop and installed Ubuntu 11.10 into a SSD drive. My Desktop has a new nVidia 670 GTX card and Ubuntu won't recognize it. I see "Unknown" in the Display settings and it only sees one of my two monitors which is the main reason that prompted me to install the latest nVidia drivers. 

I downloaded the latest drivers from here:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

but the installation fails because it asks to stop the X server first. I tried doing so following the instructions from here:
[http://neelmohile.wordpress.com/2011/11/02/how-to-manually-install-latest-nvidia-drivers-on-ubuntu-oneiric-11-10/](http://neelmohile.wordpress.com/2011/11/02/how-to-manually-install-latest-nvidia-drivers-on-ubuntu-oneiric-11-10/)

but it failed because after running "***sudo service lightdm stop"  ***I see a bunch of DOS messages and no command to continue with the nVidia driver installation.

Can anyone advice what to do? 

Many TIA,
Best regards,
Giovanni

---

### Post by bogan on 2012-06-21
Hi!,** bravegag**,

After: ***'sudo service lightdm stop'*** press 'Ctrl+Alt+F1' to get a tty login prompt; login username and enter password; 'CD' to where the .run file is downloaded and run it with: ```
sudo sh NVIDIA-x86......  # you can use 'tab' to complete the filename
```**EDit**; yOU WILL PROBABLY GET AN ERROR MESSAGE THAT A SCRIPT HAS FAILED - IGNORE IT !!

Chao!,** bogan**.

---

### Post by stinkeye on 2012-06-21
Try installing from the X-updates ppa.
Latest drivers 302.17

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```


*** Note from ppa ***
> If you are uprading from one release to another with this PPA activated, please install the **ppa-purge** package and use it to downgrade everything in here beforehand. **sudo ppa-purge ppa:ubuntu-x-swat/x-updates** will do it.

---

### Post by bravegag on 2012-06-22
> **stinkeye said:**
> Try installing from the X-updates ppa.
Latest drivers 302.17

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```
*** Note from ppa ***

Excellent! thank you! I got my other Display up and running in no time :)

I preferred using apt-get so I get "Ubuntu tested drivers".

Many thanks!

---

### Post by bravegag on 2012-06-22
> **bogan said:**
> Hi!,** bravegag**,

After: ***'sudo service lightdm stop'*** press 'Ctrl+Alt+F1' to get a tty login prompt; login username and enter password; 'CD' to where the .run file is downloaded and run it with: ```
sudo sh NVIDIA-x86......  # you can use 'tab' to complete the filename
```**EDit**; yOU WILL PROBABLY GET AN ERROR MESSAGE THAT A SCRIPT HAS FAILED - IGNORE IT !!

Chao!,** bogan**.

Thank you bogan, it is good to have this choice but after thinking about it I decided to take the apt-get path, better integrated, get tested stuff at least that's my impression but I am an Ubuntu novice :)

---

### Post by bogan on 2012-06-23
Hi!, **bravegag,**

You Posted:>   I decided to take the apt-get path, better integrated, get tested stuff  at least that's my impression but I am an Ubuntu novice :smile:Fine! Glad it works for you.

But as you can see from the many Posts complaining about the results, using the Jockey/Additional Drivers route can produce an unpredictable, very confusing and disappointing outcome.
 Similarly with the apt-get path, unless you are sure of, and include the version number you want, and do not use "Nvidia-current" whose results depend on what ppa has precedence.

Personally, I prefer to use the Nvidia Download route as the results are - from my experience - predictable, and apply equally to my various Ubuntu installations - 10.04 >> 12.04, and various nvidia cards - 7650 GS >> GT520.

The only disadvantage is that a re-installation of the driver may be needed, following a kernal update, but that also is predictable and expected, taking only few minutes.

Chao!, **bogan.**

---

### Post by bravegag on 2012-06-28
> **bogan said:**
> 
...
Personally, I prefer to use the Nvidia Download route as the results are - from my experience - predictable, and apply equally to my various Ubuntu installations - 10.04 >> 12.04, and various nvidia cards - 7650 GS >> GT520.

The only disadvantage is that a re-installation of the driver may be needed, following a kernal update, but that also is predictable and expected, taking only few minutes.


Hello bogan,

I should have listened to you :( the apt-get route destroyed my installation and ended having to reinstall Ubuntu entirely.

Now I have my system up and running again without these custom PPAs but after installing the new nVidia downloaded driver as you suggested and restart I still see that the displays are not recognized, only one is recognized and appears as "Unknown". What else do I have to do to get it working?

Many TIA,
Best regards,
Giovanni

---

### Post by bogan on 2012-06-28
Hi!, bravegag,

The System Info bug that reports the Graphics as 'Unknown' and a Desktop Monitor as 'Laptop' is well known. If everything is otherwise working, don't worry about it.

If not, have you installed 'nvidia-settings' [ same version as the driver ] and run it, or 'nvidia-xconfig', from a terminal, or as 'Nvidia X Server Settings' from Dash?.

Chao!,** bogan.**

---

### Post by bravegag on 2012-06-28
Hi bogan,

Thank you very much! Separate from the "Unknown" issue, I could not see my other Display enabled and this is the root of why I needed the driver. 

Using "nvidia-xconfig" managed to see the other display and enable it as "additional x-display". Then to apply the change restarted the x-server and the additional display was enabled but with a white background and could not move additional Windows e.g. terminals into it. Then went back to "nvidia-xconfig" to see if there was a setting to just freaking make it work as dual display and switched on a setting cinematics or something like that. After restarting x-server both displays are enabled with the same background, but I am presented with a desktop with no Ubuntu system menu, no restart buttons, no access to terminal, just a silly "create new Document" Windows-like style menu and cant do anything! I tried to use the terminal shortcut Ctr-Alt-T but doesn't work :( 

Can anyone help please?

Many TIA,
Best regards,
Giovanni

---

### Post by bravegag on 2012-06-28
Just pressing the old Power button did the trick. Now I can see my two screens enabled and working with the same system menu options on the top right corner, though for one of the Displays the menu options disappear while moving the mouse down to choose the sub-menu option, keeping the mouse left clicked while moving works, is not perfect but I can live with that. 

The checkbox option I checked "to try" in "nvidia-xconfig" was the Xinerama, whatever that means!

---

### Post by bogan on 2012-06-28
Hi!,** bravegag**,

[COLOR=Blue]***Edit: This Post crossed with your latest. Glad you found a fix. Please Mark as 'Solved', if it is!***[/COLOR]

I  have never used a dual Monitor set-up in Linux, so there is not much advice I can offer specific to your problem.

Some obvious questions would be:

Have you tried booting to recovery?, or logged-in with another Username?

Do you get any error messages when running 'nvdia-settings' from a terminal?

Does /var/log/Xorg.0.log show anything indicative?  [" .0. " is a zero, not 'O'.]

Possibly use:```
 cat /var/log/Xorg.0.log | grep -e EE -e W
```Other possibility:```
 sudo apt-get remove --purge nvidia-* 
```Reboot and see if Nouveau does any different or better. [ Assuming you have not removed Nouveau.]

Good Luck.  Chao!,** bogan.**

---

