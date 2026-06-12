---
title: "Login won't start desktop"
date: 2016-11-04
forum: Desktop Environments
---

### Post by lordbah2 on 2016-11-04
When I enter my password the screen goes black for a second then goes back to the login screen. This is a 16.04 amd64 system with Nvidia GTX590 which had been working fine until I restarted this morning (hadn't restarted during the past couple weeks worth of updates). Spent a couple hours searching and trying to figure it out this morning. Some highlights:

symlink /usr/lib/gnome-session/gnome-session-check-accelerated to /bin/true allows the desktop to start, but there's no window management. (what lead to trying that was "gnome-session-check-accelerated: Helper exited with code 256" in /var/log/syslog)

Installing gnome-flashback, gnome-session-flashback, and friends gives me a widget next to my username on the login screen. If I select Metacity there, the desktop starts, with a window manager. That's what I'm running as I write this.

Uninstalling "nvidia*" didn't help. Nor did reinstalling it.
Removing any of the following didn't help: .Xauthority, .compiz-1, .compiz, .config/compiz-1.
Of course I restarted lightdm several times, and rebooted a few times.
I wasn't able to run any kind of unity reset while I couldn't login. That might work now, I'll try it tonight.

Any thoughts?

---

### Post by lordbah2 on 2016-11-04
Tried Gnome 3.22 hoping there might already be a fix, but same issue.

---

### Post by gareth-coe on 2016-11-05
I have a very similar problem.  
16.04 was working fine yesterday when I switched off normally.  Turned on the machine a few hours later & was unable to login - constantly looping back to the login screen.  I tried logging in as a guest as well, just incase I had somehow managed to alter my password but this has the same effect: black screen for about 1 second and then back to the login.  I am able to get in if I choose LXDE (yuk!) but default, gnome and ubuntu all give me "the loop".  :-(
Can anyone help us?

---

### Post by lordbah2 on 2016-11-06
Downgrading nvidia-current, nvidia-304, nvidia-opencl-icd-304, libcuda1-304 from 304.132 to 304.131 has fixed the issue for me. I used synaptic, didn't run that install shell script from Nvidia.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1639180](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1639180)

---

### Post by dheianevans on 2016-11-08
Having an issue with the .132 driver also (with Mythtv) but when I check Synaptic for the force version I see this:

* 304.132-0ubuntu0.12.04.1 (precise-updates)* and

* 295.40-0ubuntu1 (precise)*

No sign of .131

Any ideas?

---

### Post by scpatl4now on 2016-11-10
To install previous nvidia drivers

```
- CTRL+ALT+1 to console
 login
sudo apt-get remove nvidia*
sudo apt-get autoremove
sudo apt-get install nvidia-304=304.131-0ubuntu3
```

You will also need to tell it not to update with the faulty driver

```
first create a file named /etc/apt/preferences.d/local-nvidia-quirks with the following content:

Explanation: block this specifique update because of OpenGL problem with 304.132
Package: nvidia-304
Pin: version 304.132-0ubuntu0.16.04.2
Pin-Priority: -10

Explanation: block this specifique update because of OpenGL problem with 304.132
Package: nvidia-opencl-icd-304
Pin: version 304.132-0ubuntu0.16.04.2
Pin-Priority: -10
```

This was in the bug report but this is the part that solved it for me

---

### Post by teprac on 2016-11-11
scpatl4now, your solution fixed my problem.

However I created the file to block the update, when I try to copy the file to the directory I get " permission denied "

How do i get around the " permission denied " ?

---

### Post by dheianevans on 2016-11-13
[**[COLOR=#000000]scpatl4now[/COLOR]**]("https://ubuntuforums.org/member.php?u=538883"), thanks for the info.

---

### Post by kpatz on 2016-11-13
@teprac, use sudo when copying the file, such as the following (assuming you created the local-nvidia-quirks file in your home folder:```
sudo cp ~/local-nvidia-quirks /etc/apt.d/preferences.d
```Enter your password when prompted.

---

