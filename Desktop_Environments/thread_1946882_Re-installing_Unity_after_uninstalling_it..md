---
title: "Re-installing Unity after uninstalling it."
date: 2012-03-25
forum: Desktop Environments
---

### Post by Ifaistos on 2012-03-25
Hello :)

As many others have done, when I installed 11.10 on my computer I reverted back to the Gnome GUI, instead of the unfamiliar Unity GUI.

I don't know why, but I don't have Unity as one of my options when I want to log back in.

I want to have it as an option, since I want to give it a try and test it.  It seems that Unity, Dash and the HUD are going to play a major role in the future.

So is there a command line that I could use in order to reinstall Unity and have it as an option when I log-in?

I DON'T WANT TO LOOSE MY GNOME GUI, though!! Is there a way that they can co-exist?

Thank you everyone!

ps.  Is there a site, resource, link that has introductory and medium level instructional videos on Unity, that you can point me too?

---

### Post by 3Miro on 2012-03-25
You should be able to go back to Unity with:
```
sudo apt-get install ubuntu-desktop
```

You can also install Synaptic Package Manager and use it to see if "ubuntu-desktop" will uninstall any existing packages (it is unlikely, but synaptic generally gives great information).

---

### Post by jerome1232 on 2012-03-26
Did you actually remove gnome3 and install gnome2, or did you simply remove unity, and install gnome-failback?

I don't believe it's possible to have both gnome2 and gnome3 at the same time if that's what you are asking. However if your simply using a gnome-fail-back with gnome3 than yes, it's actually rather easy to get unity back (with apt-get install unity, or as suggested, apt-get install ubuntu-desktop to ensure your not missing anything from a default install)

---

### Post by Bucky Ball on 2012-03-26
Software Centre>Unity>Install. Log out, choose 'Ubuntu whatever' from the 'Sessions' pop up menu, log in ...

---

### Post by Ifaistos on 2012-03-26
Thank you all for the suggestions.

I appreciate both the command line instructions as well as the GUI guidance.
I will certainly give it a try.

Since I installed the fallback option, I guess I cannot have both desktops.. right?

Can anyone help me in pointing me to a link, resource, video where I could learn how to use unity?

Thank you all again.

---

### Post by jerome1232 on 2012-03-26
> **Ifaistos said:**
> 
Since I installed the fallback option, I guess I cannot have both desktops.. right?


Yes you can have both, just click the gear icon at your login screen to switch sessions after installing unity.

[http://fridge.ubuntu.com/2011/04/21/the-power-user%E2%80%99s-guide-to-unity/](http://fridge.ubuntu.com/2011/04/21/the-power-user%E2%80%99s-guide-to-unity/)

---

### Post by Ifaistos on 2012-03-26
Thank you very much !!

I will try it at once...

I will check the guide too ;-)

---

### Post by Ifaistos on 2012-03-26
Hello everyone :)

I followed your advice, but there seems to be a problem.
One thing that striked me as weird was the fact that when I tried to install unity again, both from the command line and the software center said that it was already installed.

So I un-installed and re-installed.  It went great.  No errors whatsoever.

When I logout though and try to log back in, I have the same options I had before.... two options for Classic Gnome (one without effects) and two others that are not Unity!  
EDIT : The two options I get is : Ubuntu and Ubuntu 2D.  Ubuntu 2D is working!  I got the Unity desktop and this is where I am typing from.  The Ubuntu option does not work.  I have a hunch that the Ubuntu option does not work because of my gfx card.  I read somewhere that Unity does not like nvidia cards.  Could that be the case?  Does anyone know what I can do?

Is there a difference between Ubuntu and Ubuntu 2D options?


When I choose the two others I log in but I see nothing.  There is only limited functionality, with just one bar at the top, with File, Edit... no programs whatsoever no other options and definitely no dock. The only thing I can do is Ctrl-Alt-Del and logout.

EDIT : as I said this "GUI" appears only on the Ubuntu option.  Ubuntu 2D option seems to be working fine.

Does anyone have any idea of what might be wrong?

Thank you all.

---

### Post by jerome1232 on 2012-03-26
The only problems with nvidia cards are the ones on laptops, I believe between gt510 to gt 540 have optimus which doesn't play well with Ubuntu, due to nvidia's drivers not having the feature.

Other than that NVidia is well supported if you install nvidia's proprietary driver. Try Logging into Ubuntu 2D and clicking the gear icon in top right, click system settings, click additional drivers and search for drivers to install. Install them reboot, then try Ubuntu (which is unity btw, hate how they named Unity "Ubuntu" and Gnome-shell "gnome")

---

### Post by Ifaistos on 2012-03-27
I am now in Unity 2D.
I press the Dash and type driver...

I get the options that you see on attached screenshot...

What do you think I should do, if there is anything I could do..

Thanks

ps.  btw... I like Unity, now that I know how to use it!!  It's growing on me...

---

### Post by Bucky Ball on 2012-03-27
Well, the other driver looks like the updates to the driver you're using so I would be tempted to give that a go but have no idea of the result. At own risk. Hopefully someone else can chime in.

---

### Post by Ifaistos on 2012-03-27
Ok I tried that.
I am now using the updated drivers....  Unfortunately no result... I still don't get the Unity 3d GUI.

2D seems to be working fine though with these drivers as well.

btw.. What's the difference between 2D and 3D?  Better graphics? Animations?

Any other ideas as to what I could do to enable the 3D GUI?

Thanks :-)

---

### Post by jerome1232 on 2012-03-27
Unity 3d has more customization options, more of the drawing gets offloaded to your gpu so technically it should be faster than unity 2d. I'm sure it has some functionality that 2d does not have.

How did you re-install unity exactly? I would try installing ubuntu-desktop just to insure your not missing something important.

Check nvidia-settings to ensure your install is ACTUALLY using their driver. (if it's not it should bring up a dialog box to warn you that the nvidia driver isn't in use)

Other than that I'm out of idea's.

---

### Post by Ifaistos on 2012-03-27
To tell you the truth I don't think I ever uninstalled Unity.  I just installed the fallback GUI, and never touched Unity ever since, since I didn't like it at all.... I felt that it didn't give me enough options, .. which I now don't believe...

So to be on the safe side, I went to the Software center a couple of days ago, unistalled unity, and then reinstalled it...  I don't think that it made any difference...

However now I issued the following on the terminal and I got this result...

evans@DeepBlack:~$ sudo apt-get install ubuntu-desktop
[sudo] password for evans: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ubuntu-desktop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,786 B of archives.
After this operation, 61.4 kB of additional disk space will be used.
Get:1 [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) oneiric/main ubuntu-desktop amd64 1.245 [3,786 B]
Fetched 3,786 B in 0s (11.3 kB/s)   
Selecting previously deselected package ubuntu-desktop.
(Reading database ... 259802 files and directories currently installed.)
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.245_amd64.deb) ...
Setting up ubuntu-desktop (1.245) ...
evans@DeepBlack:~$

I hope that this will make a difference... 
I will reboot and let's you know...


EDIT : Nope :(  It didn't work.  I get the exact same desktop with the icons, and the menu bar.. but no launcher, dash or anything...

How do I make sure that that my install is using the nvidia drivers?  Could you please direct me?

Thanks

---

### Post by jerome1232 on 2012-03-27
dash, search for nvidia, click on nvidia x server setttings, it should list a driver version on it's main screen, if your not using the driver it should give you a warning dialog or something.

You can also check with lshw, it should list your driver as nvidia, if it says Nouveau then you are not using nvidia's driver and that is our problem.

```
sudo lshw -C video
```


If it turns out you are not using nvidia's driver, it should be solved by running nvidia-xconfig, and a reboot.

```
sudo nvidia-xconfig
```

edit:

you can also try reseting unitys configuration by dropping to a tty (ctrl+alt+f1) and running the command below
```
unity --reset
sudo service lightdm restart
```

---

### Post by Ifaistos on 2012-03-27
ok ... Here are the results...


evans@DeepBlack:~$ sudo lshw -C video
[sudo] password for evans: 
  *-display               
       description: VGA compatible controller
       product: [GeForce GT 440]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:ec00(size=128) memory:feb80000-febfffff
evans@DeepBlack:~$ 


I also attached the screen from my nvidia settings... I am not an expert.. but I think that I do use the drivers... right?

---

### Post by jerome1232 on 2012-03-27
Drivers are correct, see my the edit portion of my last post for my last idea. Somewhere on this forum is a unity troubleshooting thread, I'm trying to find it.

---

### Post by Ifaistos on 2012-03-27
IT WORKED !!! yeah !!!

Unity --reset did the trick...

Now I am working through the 3D Unity, and it is indeed faster... plus it can do some stuff that the 2D couldn't.  eg.  I can move the launcher items out and in from the launcher.. I am sure I can find more...

Thank you, thank you, thank you !!

---

