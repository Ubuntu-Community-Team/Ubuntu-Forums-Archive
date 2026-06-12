---
title: "Multimonitor management"
date: 2007-12-26
forum: Desktop Environments
---

### Post by Aqualung on 2007-12-26
Alright, Ive decided to give Gutsy a try. Ive been told it supports multiple monitors--which Ive been running for 7 years now. (Please tell me it does, does it? No multimonitor support is a deal breaker as far as I am concerned...)

The big question: is there a multi monitor management SW for Ubuntu? ...And I mean something comparable to Real Time Softs [Ultramon]("http://www.realtimesoft.com/ultramon/")? Or does Gutsy/Gnome/KDE do that natively? Its damn hard to work with multiple monitors w/o some management software... One needs taskbars on each monitor, to say the least...

---

### Post by thefirstM on 2007-12-26
Gutsy theoretically has better support for multi-monitor environments than any previous version of Ubuntu, since it now uses xRandR 1.2.  However, I have never personally had the chance to try this.  You could always boot the LiveCD and enable it there and see if it works the way you like.

---

### Post by Aqualung on 2007-12-27
> **thefirstM said:**
> Gutsy theoretically has better support for multi-monitor environments than any previous version of Ubuntu, since it now uses xRandR 1.2.  However, I have never personally had the chance to try this.  You could always boot the LiveCD and enable it there and see if it works the way you like.

Thank you, this looks encouraging. Anybody else been using Ubuntu with dual/multiple monitors? How do you manage your monitors?

---

### Post by thefirstM on 2007-12-27
If somebody wants to send me a 19" widescreen flat-panel monitor with 2ms response time and 3000:1 contrast ratio, I would be more than glad to try out Gutsy's multi-monitor capabilities.:lolflag:

---

### Post by Prodromoi on 2007-12-27
I actually got my twin-monitor arrangement working properly yesterday after a few previous initial failures.  And having got it all sorted, I'm very pleased with the way it works.

If it's of any help to you, the key points in what I did were:
Enable the proprietory Nvidia graphics card driver.  (It got downloaded automatically, but enabling required manual intervention.)
Run nvidia-settings from the terminal.
Select TwinView from within the settings GUI.
I opted to have two separate X windows, one for each screen.  I found this the most preferable option and the one most similar to (actually, somewhat better than) my previous WinXP setup.

Of course, if you're using a non-Nvidia card this might not help you much, but there you go...

---

### Post by chewearn on 2007-12-27
I was soo hoping that gusty will have better dual monitor support, and it does, only it don't go far enough to be useful.  I have nvidia with two displays; I must have spent too many hours tweaking the damn thing.

---

### Post by thefirstM on 2007-12-27
See?  I was wrong.  I never had the chance to try it for myself....

---

### Post by Aqualung on 2007-12-27
> **Prodromoi said:**
> I actually got my twin-monitor arrangement working properly yesterday after a few previous initial failures.  And having got it all sorted, I'm very pleased with the way it works.

If it's of any help to you, the key points in what I did were:
Enable the proprietory Nvidia graphics card driver.  (It got downloaded automatically, but enabling required manual intervention.)
Run nvidia-settings from the terminal.
Select TwinView from within the settings GUI.
I opted to have two separate X windows, one for each screen.  I found this the most preferable option and the one most similar to (actually, somewhat better than) my previous WinXP setup.

Of course, if you're using a non-Nvidia card this might not help you much, but there you go...

Thank you, that *is* very encouraging, as I have an nVidia card too. I may need some more detail on the above steps though, as I am a complete beginner Linux-wise. You seem to be much more savvy so far.

Otherwise, how does it seem to you compared to UltraMon? Do you have taskbars on each monitor? Does each window have buttons thatll allow sending them to the other monitor? How about wallpaper: can you have a wallpaper that spans both monitors?

Thanks

---

### Post by Prodromoi on 2007-12-27
Well, I'll try.  I still class myself as a Linux newbie too though!

The card I have is the PCI-E 7300LE.

Go to System > Admin > Restricted Drivers Manager.  In there you should (hopefully) have an entry for "NVIDIA accelerated graphics drivers (latest cards)".  If this has not been enabled, then enable it.  (And I think you have to restart your machine having done so.  It will tell you.) **

Once done, you might want to go to System > Preferences > Screen Resolution or 
System > Admin > Screens and Graphics and play with the settings to get things looking how you want.  (Do make sure you make a note of any settings before you change them, just in case!)  

Once that's done, open a terminal window and type:
sudo nvidia-settings (followed by your password when asked for it)
You should get an Nvidia configuration window appear.

The only changes I needed to make in this panel were under "X Server Display Configuration".  It's pretty self-explanatory to be honest...
The most important setting to change (well, for me) was the "Configure" button.  I found that the options for "Separate X Screen" with Xinerama enabled were most suitable for me.  This gives two independent windows, each with their own task bars.  You may find you prefer a different set up.  


**  If the Nvidia driver package hasn't been installed automatically then you'll need to get it.  I'm not sure how to do this manually, but someone else will doubtless know.


Good luck.  Hope this helps...

PS. As for the wallpaper, don't know... haven't tried.  If you have success setting it up, you tell us...!

---

### Post by chewearn on 2007-12-27
> **Prodromoi said:**
> PS. As for the wallpaper, don't know... haven't tried.  If you have success setting it up, you tell us...!

1. If you use twinview, the wallpaper will span to both screens.  Technically, you can create a wallpaper with two pictures (of the right size) side-by-side, so each picture appeared in each screen, respectively.

2. If you use separate X screen, the same wallpaper will be repeated for each screen.

3. If you use separate X screen, and your desktop is gnome, there is a 2 second lag when opening any window/menu, which is annoying.  The solution is to run two instance of compiz.  As a (happy) consequence of that, you can assign different skydome image for each screen (under 3D cube) (if you make your 3D cube fully transparent, then the skydome becomes your background).

---

### Post by Prodromoi on 2007-12-27
> **AstalaVista said:**
> 3. If you use separate X screen, and your desktop is gnome, there is a 2 second lag when opening any window/menu, which is annoying.  

I've got a pretty standard Ubuntu 7.10 install, so I'm running Gnome as the desktop.  I have no delay in opening any windows or menus.  Menus open instantly and windows take only a fraction of a second.  I'm not aware of running dual copies of compiz.  (I certainly didn't arrange to do so!)

---

### Post by chewearn on 2007-12-27
> **Prodromoi said:**
> I've got a pretty standard Ubuntu 7.10 install, so I'm running Gnome as the desktop.  I have no delay in opening any windows or menus.  Menus open instantly and windows take only a fraction of a second.  I'm not aware of running dual copies of compiz.  (I certainly didn't arrange to do so!)

Here is the thread where it was discussed; maybe it doesn't happen for all cases, and you are the luck ones :)
[http://ubuntuforums.org/showthread.php?t=536045](http://ubuntuforums.org/showthread.php?t=536045)

---

### Post by Prodromoi on 2007-12-28
For attention of thread starter, I've just edited my post with the details of how I have my screens set up - if you're still having troubles, have another look and hopefully the clarifications I've made will help.

---

### Post by Aqualung on 2008-01-05
Check out this post: [http://ubuntuforums.org/showpost.php?p=991449&postcount=7](http://ubuntuforums.org/showpost.php?p=991449&postcount=7). Awesome! Now, if we could only get those windows to switch monitors with a click of a mouse button, that would be smashing!

---

