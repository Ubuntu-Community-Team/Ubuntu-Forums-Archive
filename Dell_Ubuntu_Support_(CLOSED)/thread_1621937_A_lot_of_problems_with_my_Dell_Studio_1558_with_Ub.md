---
title: "A lot of problems with my Dell Studio 1558 with Ubuntu 10.10"
date: 2010-11-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abreudy on 2010-11-14
Hello There, this is my first message in the forum and I hope somebody could help me, 'cause I've searched a lot without success.

I've been using ubuntu since 8.04 with no mayor problems, I just bought a brand new Studio 1558 and installed Ubuntu 10.10 on it, but now I have a lot of issues:

* I can´t control the Screen Brightness
* If I disconnect the laptop charger, it last from 5 to 10 minutes and suddenly the system freezes and doesn't respond
* Since the moment I turn it on, the system start showing this message in the log viewer:

Nov 14 21:24:29 abreudy-laptop kernel: [18978.993972] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded

-----------------------------------------------------------

I'm really worried because when the system freezes I have to turn the computer off in a bad way by holding the power button (wich is really harmful for the hardware)

I'll be really glad if somebody could help me with one or all of this problems.

Thanks,

abreudy
Dominican Republic

---

### Post by Rackstar on 2011-01-20
Hey,

I'm experiencing the same freezes as you do.

Did you find a way to stop them?

I tried flashing my BIOS to the latest A11 and upgrading my ATI driver, but I still suffer from these lockups. (I read a lot of complaints about this laptop, also on Windows machines)

---

### Post by Rackstar on 2011-01-20
Hey,

I'm experiencing the same freezes as you do.

Did you find a way to stop them?

I tried flashing my BIOS to the latest A11 and upgrading my ATI driver, but I still suffer from these lockups. (I read a lot of complaints about this laptop, also on Windows machines)

---

### Post by Shirahama Kenichi on 2011-04-01
I got this problem to, its really terrible, i love KDE and like to use Ubuntu as the underlying system, but its really frustrating needing to restart your system often.

The symptoms mine computer has is simply getting so slow that working on the notebook is not possible and i need to reboot and sometime it freezes to.

I reported a bug but this problem doesn’t seem to be taking serious because it got immediately labeled as opinion which it isn’t as its a real problem and under Windows 7 I never had it. 

I hope it is fixed in the next release because if mine computer keeps being like this under Kubuntu then I rather use Windows 7 which isn’t a bad operating system at all.

---

### Post by aravindprince on 2011-04-19
looks like i too will be joining the group in facing this sick problem!!! same case happened in my system! :confused: the screen freezes and also during the initial startup the screen gets scrambled too...hoping that somebody could help.
This Dell 1558 machine definitely isn't supporting Ubuntu...

---

### Post by Shirahama Kenichi on 2011-04-25
I was just testing the latest (K)ubuntu 11.04 beta and at first everything looked good like always but after awhile my notebook just suddenly shutdown.

I'm not sure if thats because i was doing a update process or that same problem still occurs, anyway i'm going give a test ride from usb stick and will not install until im sure.

---

### Post by IWantFroyo on 2011-04-25
Try checking your BIOS, and upping the chipset voltage (the sudden shutdowns/reboots). Try using the pci=noacpi boot option as well.

---

### Post by Shirahama Kenichi on 2011-04-25
I'm going test that, but i don't think there is option to up the chipset voltage.

---

### Post by Shirahama Kenichi on 2011-04-26
lmsensors/radeon-pci-0200/temp1 

Shows high temp off more then 203 Fahrenheit, I guess that's why computer because unstable and will shutdown in the end, the temp is keep going up.

So i have found the cause.

---

### Post by Shirahama Kenichi on 2011-04-30
Hello guys,

When i bought mine Dell Studio 1558 on 16 february 2010 I do remember Kubuntu 9.10 was working just fine on it, no problems like here are reported.

Everything worked fine, i even used it in class with virtualbox and later with VMware.

I remember in 9.10 the sound wouldnt work so u needed edit a file:

You just need to edit the alsa-base.conf file. To do that run this command in the terminal-

    sudo gedit /etc/modprobe.d/alsa-base.conf

Then add this line to the file-

    options snd-hda-intel model=dell-m6

Save the file and restart your laptop. This should solve the problem. You should start getting sound now.

I might be interesting first test the LTS, i'm not sure but i think i used the LTS under this notebook to without problems, it might just be case that in 10.10 they broke something and not fixed it yet in 11.04.

Also i not know how to use no pci=noacpi boot option, if there could be explained how boot the live usb from that then I could test that.

---

### Post by Shirahama Kenichi on 2011-04-30
I was trying fedora and instead off installing it I was searching on internet if there where problems know with Fedora with this notebook and yes there where, awhole bug report about same problems we are experience.

[https://bugzilla.redhat.com/show_bug.cgi?id=624212](https://bugzilla.redhat.com/show_bug.cgi?id=624212)

It said somewhere you would need use pcie_aspm=off as boot option.

---

### Post by Shirahama Kenichi on 2011-05-15
Hello, I saw Dell released a bios update for this notebook, so I have flashed my bios, I wonder if it also will help with problem we have with this notebook under Linux.

The newest bios version is A12.

---

### Post by Shirahama Kenichi on 2011-05-17
I think this problem has to do with fact that notebook doesn't cool enough, i have had sudden shutdowns with my experiments with osx86 and with various Linux distro's.

It seems come down to a cooling issue, I guess cooling under Windows 7 happens perhaps abit better, but it looks general problem, because when giving the notebook more airflow seems to help cool more.

So I think using a notebook cooler pad would help solving this problem, because i have found out is definitely a cooling probably and because notebook gets to hot its results in slowdown and freezes and in end shutdowns.

The strange thing is with Windows 7 it just keeps running, but its obvious after trying to give notebook more airflow that's its a cooling issue.

---

### Post by ~!geek!~ on 2011-07-11
Guys,
About the problem with shutdowns : After upgrading the bios to newer version might solve your problems. Saw the problem of shutdowns on dell website faq somewhere.

About the problem of freezing thing on battery: 
A package named pm-utils is (probably) causing this problem. You may downgrade pm-utils to the version available for ubuntu lucid lynx by following the link: 
[http://www.robertbeal.com/1248/ubuntu-10101104-freezing-battery-power](http://www.robertbeal.com/1248/ubuntu-10101104-freezing-battery-power)

Don't forget to lock the version in synaptic manager to stop it from updating with other updates.

That's it for now!!!

---

