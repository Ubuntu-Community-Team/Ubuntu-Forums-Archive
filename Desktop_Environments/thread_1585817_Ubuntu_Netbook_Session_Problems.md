---
title: "Ubuntu Netbook Session Problems"
date: 2010-10-01
forum: Desktop Environments
---

### Post by bradleyshorwith on 2010-10-01
Hello. I recently installed Ubuntu after I got fed up with my Windows installation. I have used Ubuntu before (in the days of Gutsy/Hardy/and early Jaunty), and have kept up with it over the year, but I have never really had it installed on a permanent basis since. I do consider myself fairly proficient in using Ubuntu.
Now onto my problem:
I burned a CD and installed the release candidate of Maverick Netbook Edition tonight. It was a treat to see that I can choose between a Desktop and Netbook session. However, when I try to start a Netbook session, I cannot see the user interface at all, only the desktop background. Right-clicking does nothing. However, when I press ctrl-alt-delete to bring up the shut down dialog and click help, the help is displayed, along with the menubar in the top left. I do not know whats wrong and any help would be greatly appreciated.

Crappy Computer Specs:

Pentium III Processor
512MB RAM
Onboard Video
80GB IDE HD
1024x768 LCD Monitor

Thanks in advance for any help.

---

### Post by kerry_s on 2010-10-01
the new netbook interface mutter is accelerated 3d, can your vid card do that?

---

### Post by bradleyshorwith on 2010-10-01
> **kerry_s said:**
> the new netbook interface mutter is accelerated 3d, can your vid card do that?
Most likely not. Is there a way to turn off the effects?

---

### Post by bbqsandwich on 2010-10-01
If you cannot solve the netbook problem, and your goal is simply to use Ubuntu on the older hardware you specified, you might want to try Xubuntu.

Download from [here]("http://xubuntu.org/get") or in a terminal enter:

```
sudo apt-get install xubuntu-desktop
```

Log out, and when logging back in choose XCFE as your desktop environment.

Doesn't solve your problem directly but it's just a thought :)

---

### Post by bradleyshorwith on 2010-10-01
> **bbqsandwich said:**
> If you cannot solve the netbook problem, and your goal is simply to use Ubuntu on the older hardware you specified, you might want to try Xubuntu.

Download from [here]("http://xubuntu.org/get") or in a terminal enter:

```
sudo apt-get install xubuntu-desktop
```Log out, and when logging back in choose XCFE as your desktop environment.

Doesn't solve your problem directly but it's just a thought :)

Does this work for other desktop environments as well?
For example, if I install Kubuntu or another environment, will it seamlessly integrate with the login screen, allowing me to access my account using any one I want? If so, that is a really awesome feature.
But back on topic now....
This gives me a lot of info that I am happy to hear. I will mess around with other environments, but I will keep this thread marked as unsolved, as I still would like to try Ubuntu Netbook Edition.

EDIT: Is there a way to change the login screen back to the default and a way to remove entries (such as XFCE since Xubuntu is already there, etc.)?
Also could I get a list of all of the distribution packages compatible with this login feature? I think it is mighty awesome. :P Thanks in advance.

---

### Post by bradleyshorwith on 2010-10-03
Anyone?

---

### Post by ankspo71 on 2010-10-03
Hi,
Here's the most popular desktops in my opinion. 

---KDE---
kubuntu-desktop
kde-full
kde-plasma-desktop
kde-plasma-netbook
kde-standard

---Gnome---
ubuntu-desktop 
gnome 
gnome-desktop-environment
gnome-core
ubuntu-netbook

---XFCE---
xubuntu-desktop
xfce4

---Enlightenment---
e17  <-- looks futuristic to me 

---LXDE---
lubuntu-desktop
lxde

---Openbox---
openbox

There are many more, but most of the ones I left out are ultra lightweight desktops.... which would be good for servers, or very low computer specs. Do some searches for Desktop Environments and Window Managers and you will find lots of different ones to choose from. 

Keep an eye on these links, because they aren't compatible with Maverick yet. These links show you how to remove desktops so that you are only left with one. Most other desktops are so much easier to remove because they are much smaller.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by bradleyshorwith on 2010-10-04
> **ankspo71 said:**
> Hi,
Here's the most popular desktops in my opinion. 

---KDE---
kubuntu-desktop
kde-full
kde-plasma-desktop
kde-plasma-netbook
kde-standard

---Gnome---
ubuntu-desktop 
gnome 
gnome-desktop-environment
gnome-core
ubuntu-netbook

---XFCE---
xubuntu-desktop
xfce4

---Enlightenment---
e17  <-- looks futuristic to me 

---LXDE---
lubuntu-desktop
lxde

---Openbox---
openbox

There are many more, but most of the ones I left out are ultra lightweight desktops.... which would be good for servers, or very low computer specs. Do some searches for Desktop Environments and Window Managers and you will find lots of different ones to choose from. 

Keep an eye on these links, because they aren't compatible with Maverick yet. These links show you how to remove desktops so that you are only left with one. Most other desktops are so much easier to remove because they are much smaller.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
Thank you. Is there a way to change the theme of the login screen back to the default theme and to remove entries from the drop-down list without uninstalling them? I believe I've done it before but my memory is kind of hazy.

---

### Post by ankspo71 on 2010-10-04
Hi,
Here's how you add and configure plymouth themes (eg. the purple Ubuntu and blue Kubuntu splash screens)
[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

Here is a command to choose between login windows (display managers)
```
sudo /usr/sbin/update-alternatives --config x-session-manager
```
You just paste that into your terminal and it will give you a choice to choose from - GDM, KDM, XDM, etc.

Removing the desktop/session entries from the login window is not something I have ever needed to do, and I'm not able to find a tutorial for that. Without them you wouldn't be able to choose which desktop to start. I did find a man page for this though, which might help [http://manpages.ubuntu.com/manpages/lucid/man1/xsm.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/xsm.1.html)

---

