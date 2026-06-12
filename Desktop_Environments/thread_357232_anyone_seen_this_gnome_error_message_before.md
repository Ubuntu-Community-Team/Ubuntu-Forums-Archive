---
title: "anyone seen this gnome error message before?"
date: 2007-02-09
forum: Desktop Environments
---

### Post by fiveryanfrenzy on 2007-02-09
When I login it takes like 5 minutes of watching a blank screen with a gray square (that turns out to be an error message but the text/button/topbar doesn't load until the login finally works) and also my theme is wrong until i open up system>pref>themes and it reverts back as soon as the theme selector pops up without me having to click anything, this is the message:

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

Anyone know how to fix this? it's really annoying waiting 5+ minutes for everything to start as one of the things that brought me to switch to linux over windows was the fast boot. (having to open theme manager up just to get the nice human theme back sucks too)

---

### Post by banditti on 2007-02-09
Try running:  

```
gnome-settings-daemon
```

---

### Post by fiveryanfrenzy on 2007-02-09
> sudo gnome-settings-daemon
You can only run one xsettings manager at a time; exiting

huh?

---

### Post by banditti on 2007-02-09
Can you check the following and let me know?

1.
/etc/hosts

and make sure there's a line:

127.0.0.1 localhost

2.
Make shure you have auto lo
/etc/network/interfaces

ifconfig to see if lo is active at startup.
ifconfig lo up to start it manually, restart gnome to see if this is the problem

---

### Post by fiveryanfrenzy on 2007-02-09
[COLOR="DarkRed"]contents of /etc/hosts...[/COLOR]
> 127.0.0.1 localhost [COLOR="DimGray"][computername][/COLOR]
127.0.1.1 [COLOR="DimGray"][computername][/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[COLOR="DarkRed"]contents of /etc/network/interfaces...[/COLOR]
> auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth1 inet dhcp

auto eth1
iface eth1 inet dhcp[COLOR="DarkRed"]
iconfig...[/COLOR]
> [COLOR="DimGray"]name@computer[/COLOR]:~$ iconfig
bash: iconfig: command not found
[COLOR="DimGray"]name@computer[/COLOR]:~$ sudo iconfig
sudo: iconfig: command not found



Also note that I think gedit stopped working from the command terminal at the same time as this, at least it takes like long periods of time to every pop up (use leafpad now because of this)

---

### Post by PriceChild on 2007-02-09
> **fiveryanfrenzy said:**
> > sudo gnome-settings-daemon
You can only run one xsettings manager at a time; exitinghuh?Could you try it without the sudo?

---

### Post by banditti on 2007-02-09
also, it is ifconfig, not iconfig.  you need that "f".

---

### Post by fiveryanfrenzy on 2007-02-10
strange update (maybe not strange) but i booted like normal expecting it to happen again and this time it booted right away and had my normal theme... but then i realized the one thing that was different: my ethernet cable was unplugged this time... could this be a clue as to what is up? (i now know i can just boot without the cable in to have it work but it still would be nice to know what is up just in case it happens again for another similar reason...)

---

### Post by banditti on 2007-02-10
That is what I was thinking with asking for the interfaces, etc.

Remove everything that is unnecessary.  For example, if you only have one nic, your interfaces should be:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


My guess is that will fix the problem.

---

### Post by fiveryanfrenzy on 2007-02-10
ok i thought about doing that but wasn't sure which ones were needed, guess the lo and the ones that i have eth0 and eth1, i'll give it a try thanks for your help

---

### Post by kaqmak on 2007-02-10
I have exactly the same problem, and after having read this thread, I have boiled down the problem to the point about issuing:
```
ifconfig lo up
```
So the problem is: Whenever I do a complete restart, followed by a crtl-alt-del reboot and login, the computer hangs and issues the mentioned error. But, if I instead type in "ifconfig lo up" in the command prompt before rebooting, there problem is no longer there. However, after having done a restart, the problem is the same.
I'm not sure what this "lo" actually is, but it seems to me that it isn't automatically set to "up".
This is despite the fact that my content of /etc/network/interfaces is
```
auto lo
iface lo inet loopback


%iface eth0 inet dhcp

%auto eth1
%iface eth1 inet dhcp

%auto eth2
%iface eth2 inet dhcp

%auto ath0
%iface ath0 inet dhcp
%wireless-essid [networkname]

%auto wlan0
%iface wlan0 inet dhcp
```

I have installed the gnome NetworkManager 0.6.3. Could this be the source of the problem?

\Kaqmak

---

### Post by banditti on 2007-02-10
It looks like your missing:

auto eth0

---

### Post by dreamsayer on 2007-03-15
> **fiveryanfrenzy said:**
> When I login it takes like 5 minutes of watching a blank screen with a gray square (that turns out to be an error message but the text/button/topbar doesn't load until the login finally works) and also my theme is wrong until i open up system>pref>themes and it reverts back as soon as the theme selector pops up without me having to click anything, this is the message:



Anyone know how to fix this? it's really annoying waiting 5+ minutes for everything to start as one of the things that brought me to switch to linux over windows was the fast boot. (having to open theme manager up just to get the nice human theme back sucks too)


I had this same problem today. I searched the forums and the net high and low, and tried all of the suggestions mentioned. Nothing worked. Typing gnome-settings-daemon in a terminal gave me a clue. There were a bunch of error messages re: label foregrounds and backgrounds.

So I logged into KDE and selected System Settings & in the Look & Feel section for Appearance, Desktop,Splash Screen & Window behavior I set all of the options contained to their defaults. I logged out of KDE and back into Gnome and Wallah!

I just happened to add KDE to my working Ubuntu system last night. I wanted to try something different. I suspect that the kpersonalizer that runs at first start may have caused this? Just a guess. I re-ran it and was playing around with the different themes. And this was after I successfully logged back and forth between Gnome and KDE without this problem.

---

