---
title: "Gnome desktop not working with tablet PC/stylus"
date: 2014-03-03
forum: Desktop Environments
---

### Post by tools4toni on 2014-03-03
[B]1). I installed Ubuntu 13.10 on a Fujitsu T4220 - tablet PC.  All worked fine with the stylus.  No screen rotation.
[/B]
I cannot easily work with the new Default Desktop (I want dropdown menus - the old style desktop).  The new icon setup scroll bar is hard to work with a stylus or regular laptop touch pad. So...
 
[B]2). What I did, and the unwanted result:
I installed the Gnome desktop. I got great old setup - [/B]I have been using Ubuntu on my desktop since v.7.0. [B]- the menus I wanted, the familiar apps and it recognizes my Bluetooth hardware.  Unwanted: now the Stylus is not recognized.

[/B][B]3).  Questions:  
If I uninstall Gnome - is there a way to have dropdown menus with the new interface?
What in the Gnome desktop disabled my Stylus?
How do I get screen rotation?[/B]

*Now remember: I have been using Ubuntu on my desktop since v.7.0 when I say...Desperate confession - If I had a Windows install disk, I would use it.  I had to replace the hard drive. ***At least with crappy Windows I would have** **screen rotation support, stellar character recognition, and stylus function.***

Any suggestions or information is appreciated.  Caveat:  I am not tech literate, so I would need Step By Step for Dummies if you give me tech suggestions.  My options do not seem promising.   
Thank you

---

### Post by grahammechanical on 2014-03-03
I have not tested this with 13.10 but I know it is there with Ubuntu+Unity 14.04 when it is released.

In the Software Centre we can search for gnome flashback or gnome-session-flashback. That will install and give two additional options at login - Gnome Flashback (with Compiz) and Gnome Flashback (with Metacity).

Either of those will give you the menus that you desire. Whether the stylus will still work is anybody's guess. If we use Gnome Flashback (with Compiz) we also need to install Compiz Configuration Settings Manager to make modifcations such as increasing the number of work spaces.

If we use Gnome Flashback (with Metacity) and there is only one workspace then a right click of the icon at the right side of the bottom panel will give us a Preferences/Properties option that will gives us the ability to increase the number of workspaces.

I have not tried any of this in 13.10 But it might take away the need for Gnome desktop.

Regards.

---

### Post by tools4toni on 2014-03-03
Thank you!  A more thourough response, and far quicker, than I had anticipated.  I will print it out and investigate. 
 
I found the Gnome Flashback in Synaptic - I am going to uninstall Gnome and try it. [I]I was wrong:  it is just a session manager.
[/I]

Again, many thanks.

---

### Post by tools4toni on 2014-03-03
What is the Default Desktop for U.v.13.10 called?

---

### Post by tools4toni on 2014-03-03
Sorry - more...I thought that I had read that people got full tablet functionality, including rotation, with Ubuntu?  And the Bluetooth - U.v.13.10 not recognizing my hardware, but Gnome does.  Odd.

Just trying to figure this out.  Thank you.

---

### Post by grahammechanical on 2014-03-03
At the moment there are two kinds of Ubuntu under development. The usual desktop/laptop machine type of Ubuntu, which we thought you had installed. And Ubuntu Touch for phones and tablets. There are plans to converge the Ubuntu Touch code base into the desktop code base so that there is just one Ubuntu code base. In fact it has been decided to change the name of Ubuntu touch to just Ubuntu. Which really does make it confusing.

There is where you can find out about Ubuntu Touch. Check out the Devices page and see if your device is listed and you may find a link on how to install Ubuntu Touch to the device. The downside to all of this is that it will not be the Gnome user interface but Unity 8 but it will be touch enabled even when running as a desktop OS.

[https://wiki.ubuntu.com/Touch/Install](https://wiki.ubuntu.com/Touch/Install)

Ubuntu for phones is at version 1 and it is based upon Ubuntu 13.10 code and is optimised for phones. Work is being done to bring Ubuntu for phones up to version 1.5 at which point it will be optimised for tablets and will be based upon Ubuntu 14.04 code. The plane is to have convergence to the desktop complete by the release of Ubuntu 14.10 or 15.04 at the latest.

As regards screen rotation, have you tried going to System Settings>Displays? You may see an option for rotation there. But I think that this feature may be affected by the video driver. If I use a proprietary video driver then Displays become inactive and I have to use the proprietary driver settings utility that was installed with the driver. I am using Nouveau the open source video driver and Displays is active and I have an option to set the screen rotation to Normal, Anticlockwise, Clockwise, 180 Degrees.

Regards.

---

### Post by tools4toni on 2014-03-04
Thanks again.  To clarify for me - I installed Ubuntu 13.10 onto my LAPTOP, not a tablet - I wrote that part wrong.  It is a laptop that converts to a tablet by turning the screen and laying it flat, over the keyboard.  It is the same Ubuntu disk that I installed on my desktop.

I will reread what you wrote and look into the points you provided.

---

### Post by tools4toni on 2014-03-12
:D  I solved it!  I used Synaptic to install Ubuntu Touch without removing Gnome Desktop.  Some of the packages could not install, but they are multimedia related.  Don't care about those.  I don't have screen rotation, but the stylus works.

I have the best of both.

Thank you for all the info.

---

### Post by nadalex on 2014-09-05
Has anyone got Rotation working on the Fujitsu?
Looking for a thread on that.
I'm using a T901 and have pen but no rotation, in Gnome and Unity.

---

