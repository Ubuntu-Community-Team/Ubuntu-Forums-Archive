---
title: "How to install Debian 7 &quot;Wheezy&quot; testing with LXDE"
date: 2012-07-04
forum: Debian
---

### Post by Lyfang on 2012-07-04
Hi, Ubuntu has improve usability for novice users compared to Debian? Difference between Debian and Ubuntu: Ubuntu easy to use but bloated? Debian More resource efficient but for experienced Linux users?

Is done at your own risk & I take no responsibility for any loss or damage. / Görs på egen risk & jag tar inget ansvar för förlust eller skada. (sentence in Swedish)

"Kind of" step-by-step installation, Internet connection required for a "complete" system
1. Download & install debian-testing-i386-xfce+lxde-CD-1.iso with or without an Internet connection
2. Open Root-terminal: leafpad /etc/apt/sources.list
3. Backup old sources.list, replace all sources with following & save to /etc/apt/sources.list: 

deb [http://ftp.se.debian.org/debian/](http://ftp.se.debian.org/debian/) wheezy main contrib non-free
deb-src [http://ftp.se.debian.org/debian/](http://ftp.se.debian.org/debian/) wheezy main contrib non-free
deb [http://security.debian.org/](http://security.debian.org/) wheezy/updates main contrib non-free
deb-src [http://security.debian.org/](http://security.debian.org/) wheezy/updates main contrib non-free
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) experimental main

4. Open Root-terminal (or LXTerminal with su command): 
ifconfig eth0 up
dhclient eth0
apt-get update && apt-get upgrade

See also: [http://manual.aptosid.com/en/sys-admin-apt-en.htm#apt-upgrade](http://manual.aptosid.com/en/sys-admin-apt-en.htm#apt-upgrade)

5. Network management
Open Root-terminal: apt-get install network-manager-gnome

leafpad /etc/X11/Xsession
Add line, save & reboot: exec ck-launch-session dbus-launch wm

(Emergency only NetworkManager workaround, run as a privileged process. Open Root-terminal: nm-applet or nm-connection-editor)

6. Shutdown/reboot button doesn't show up? 
Open Root-terminal: apt-get install lightdm

Change default display manager to "lightdm".

Root-terminal: leafpad /etc/lightdm/lightdm.conf

greeter-hide-users=true to 
#greeter-hide-users=true

#autologin-user= to
autologin-user=USERNAME

7. Graphical package management
Open Root-terminal: apt-get install synaptic

8. Need a web browser?
Open Root-terminal: apt-get install iceweasel
Or, reminder experimental, is done at your own risk (as usual):
apt-get update && apt-get install -t experimental iceweasel

9. Open Iceweasel & download Google Chrome web browser [https://www.google.com/chrome](https://www.google.com/chrome)
Install Google Chrome from the Root-terminal:
[http://www.math.utah.edu/lab/unix/unix-commands.html#cd](http://www.math.utah.edu/lab/unix/unix-commands.html#cd)
dpkg -i google-chrome-stable_current_i386.deb

Alternative way, open Root-terminal:
wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -
sh -c 'echo "deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main" >> /etc/apt/sources.list.d/google.list'

Details of Google's google-chrome.list:
/etc/apt/sources.list.d/google-chrome.list

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
     
Open Root-terminal:
apt-get install google-chrome-stable 
Or, reminder is done at your own risk (as usual):     
apt-get install google-chrome-beta  
apt-get install google-chrome-unstable

"new versions of the Flash Player browser plugin for Linux will only be available as part of Google Chrome." - [http://www.pcworld.com/businesscenter/article/250455/for_flash_on_linux_chrome_will_be_users_only_choice.html](http://www.pcworld.com/businesscenter/article/250455/for_flash_on_linux_chrome_will_be_users_only_choice.html)

Google Chrome tracking & if you're concerned use Chromium instead!

See also: Re: Chromium Flash Pepper on precise, how? [http://ubuntuforums.org/showpost.php?p=12072504&postcount=13](http://ubuntuforums.org/showpost.php?p=12072504&postcount=13)

8. Java with IcedTea
Open Root-terminal: apt-get install icedtea-6-plugin

9. Time synchronization via Internet
Open Root-terminal: apt-get install ntp

10. LibreOffice office productivity suite
Open Synaptic, search for LibreOffice & install the "libreoffice" metapackage.

Install from repositories with a GUI: Synaptic Package Manager 
Install .deb packages from Root-terminal: dpkg -i

"Installation of binary packages from unknown sources is strongly discouraged!" - [http://dev.carbon-project.org/debian/wine-unstable/](http://dev.carbon-project.org/debian/wine-unstable/)

---

### Post by WasMeHere on 2012-07-04
Interesting :KS

Har du jämfört din installation jämfört med Knoppix och Linux Mint Debian?

Having fun finding out :-)

Olle

---

### Post by Lyfang on 2012-07-05
If I have compared installation to Knoppix and Linux Mint Debian? They have different target groups: Debian is targeted at both server & desktop(?). Knoppix & Linux Mint Debian for the desktop.

---

### Post by Perfect Storm on 2012-07-05
Moved to Other OS/Distro Talk.

---

### Post by WasMeHere on 2012-07-05
> **Lyfang said:**
> If I have compared installation to Knoppix and Linux Mint Debian? They have different target groups: Debian is targeted at both server & desktop(?). Knoppix & Linux Mint Debian for the desktop.

I mean: What is different in ***your*** install (according to post #1) and those distros? What are you giving priority, and what are you skipping?

---

### Post by Lyfang on 2012-07-08
> **Olle Wiklund said:**
> I mean: What is different in ***your*** install (according to post #1) and those distros? What are you giving priority, and what are you skipping?

My installation creates a fast system. It's fast! To be honest the main priority was to get everything working at the beginning, but I'm really satisfied with the result. I'm using the Btrfs file system. Caution however, don't try this file system on production machines without fear of dealing with problems. Currently the Btrfs file system is under heavy development, so is btrfsck (for file system checking).
 ```
dmesg | grep btrfs
``` [    3.373001] btrfs: disk space caching is enabled 
 [   11.988479] btrfs: disk space caching is enabled 
 
 Beware with Debian testing, software can stop working, the system can break. You get newer packages with testing (& unstable). I'm writing this on an experimental package: Iceweasel (web browser).

 ```
iceweasel --version 
``` Mozilla Iceweasel 13.0.1
  
 Linux Mint Debian Edition (LMDE) has a simplified installation process compared to my installation. LMDE comes with the Adobe Flash Player plugin pre-installed. 
  
 Knoppix is designed for running as a Live CD or Live USB. I tried Knoppix long time ago. I would recommend to create a Live USB in persistent mode, since otherwise you won't be able to save anything to it.

---

### Post by WasMeHere on 2012-07-11
> **Lyfang said:**
> My installation creates a fast system. It's fast! To be honest the main priority was to get everything working at the beginning, but I'm really satisfied with the result ...
 
 Beware with Debian testing, software can stop working, the system can break. You get newer packages with testing (& unstable) ...
 Linux Mint Debian Edition (LMDE) has a simplified installation process compared to my installation. LMDE comes with the Adobe Flash Player plugin pre-installed ... 
  
 Knoppix is designed for running as a Live CD or Live USB. I tried Knoppix long time ago. I would recommend to create a Live USB in persistent mode, since otherwise you won't be able to save anything to it.

I guess you mean fast on a [fairly] new computer, for example fast booting, fast loading of programs and HD video playing without problems :-)

I agree about LMDE. Out of the box it can do what most people need. But I have tried a recent version of Knoppix. Today it is more than a good live system with excellent hardware detection for portability and rescue etc. I have installed it in an ancient desktop with a 400 MHz CPU and 192 MB RAM (regular installation, not frugal with a loop-mounted file for persistence). And it works really well.

But as you wrote: 'Beware with Debian testing' unless you know enough to fix it, or can wait until in will be patched via new updates. So Ubuntu or an Ubuntu based system might be better for daily use.

---

### Post by ratcheer on 2012-07-11
If you want bleeding edge Debian with LXDE, Siduction Linux is very nice.

[http://siduction.org](http://siduction.org)

Tim

---

### Post by Lyfang on 2012-07-16
Thanks Olle for sharing your experiences of using Knoppix & LMDE! 
> **Olle Wiklund said:**
> But as you wrote: 'Beware with Debian testing' unless you know enough to fix it, or can wait until in will be patched via new updates. So Ubuntu or an Ubuntu based system might be better for daily use.
**Analysing my experience using Debian 7 "Wheezy" testing by reflecting the bugs or other issues:**
   
• [libreoffice: terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException' because of wrong profile permissions (link) ]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=619263")
•[ Windows 7 SP1 upgrade – error 0x800f0a12 and the solution (link)]("http://www.arch-ed.dk/windows-7-sp1-upgrade-error-0x800f0a12-and-the-solution/")
 • Problem changing locales and language settings.
• VirtualBox dkms package problem related for the need of installing a Linux header or similar.
• Need to run as root to access USB drives from VirtualBox.
• Cannot connect to WIFI:

```
ifconfig wlan0 up
```SIOCSIFFLAGS: Operation not possible due to RF-kill

• NTFS-3G driver high CPU usage.
• Microphone doesn't work with Skype 4.0.0.7. Audacity 2.0.1 recording with my inbuilt microphone in the laptop doesn't work either.
```
cat /proc/asound/version
```Advanced Linux Sound Architecture Driver Version 1.0.24.
```
uname -a
```Linux debian 3.2.0-3-686-pae #1 SMP Thu Jun 28 08:56:46 UTC 2012 i686 GNU/Linux&#65279;

I also want to learn how to use Reportbug or Reportbug-NG (GUI).

Experiencing problems with different packages due to Debian Testing constantly changing. I still like testing & the feeling of an OS "making progress", a rolling-release distro. However in Debian stable severe bugs are often fixed & hence the most serious types of bugs avoided.

---

### Post by Lyfang on 2012-12-12
**Is done at your own risk and I take no responsibility for any loss or damage (as usual).** Time to update the distro? Beaware that it can break at any point. Open Root-terminal (or LXTerminal with su command): 
```
apt-get update && apt-get upgrade
```

---

### Post by Chdslv on 2012-12-12
Actually, there is no risk using the Debian Wheezy testing, as it is already rock solid. Ubuntu is made out of the same Debian Wheezy.

---

### Post by deadflowr on 2012-12-12
> **Chdslv said:**
> Actually, there is no risk using the Debian Wheezy testing, as it is already rock solid. Ubuntu is made out of the same Debian Wheezy.

That's just not true.
Of course there is risk. Debian testing still gets newer packages, and will continue to get newer packages until they decide what they have will become the new stable.
But yes like Ubuntu, it is quite stable. And like Ubuntu, it is not risk-free.

---

### Post by Chdslv on 2012-12-13
> **deadflowr said:**
> That's just not true.
Of course there is risk. Debian testing still gets newer packages, and will continue to get newer packages until they decide what they have will become the new stable.
But yes like Ubuntu, it is quite stable. And like Ubuntu, it is not risk-free.

The only risk being that you may have to reinstall, if something goes wrong. :)
And the whole thing could be wheezy...

---

### Post by Chdslv on 2012-12-14
Could you please post the link to download debian-testing-i386-xfce+lxde-CD-1.iso?

---

### Post by Lyfang on 2012-12-14
> **Chdslv said:**
> Could you please post the link to download debian-testing-i386-xfce+lxde-CD-1.iso?
                                   I would recommend to download debian-testing-amd64-lxde-CD-1.iso (64-bit, without 4GB limit) from [http://cdimage.debian.org/cdimage/weekly-builds/amd64/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/amd64/iso-cd/) or debian-testing-i386-lxde-CD-1.iso (32-bit for older CPUs) from [http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/)  
 
 Further explanation: I'll get you an answer as close as possible. The debian-testing-i386-xfce+lxde-CD-1.iso file is no longer available for download. Debian testing changes very often and these images are produced every week. But you can download debian-testing-i386-lxde-CD-1.iso (there's also debian-testing-i386-xfce-CD-1.iso).
 
 Since this is about Debian: The official Debian system uses free licenses and keeps nonfree software out. But users are still free to download non-free software.

---

### Post by Lyfang on 2012-12-19
I know Debian "testing" is not the same as "unstable". But according to the [aptosid Manuals - APT-Guide]("http://aptosid.com/manual/en/sys-admin-apt-en.htm") the right way is to:
**dist-upgrade - The Steps**
[COLOR="Red"]NEVER EVER do a dist-upgrade nor upgrade whilst in X[/COLOR]
Always check Current Warnings on the aptosid main web site. The warnings are there for a reason due to the very nature of unstable (Debian sid), which also updates 4 times per day.
Log out of KDE.
Go to Textmode by doing Ctrl+Alt+F1
logon as root,
and then type:
```
init 3
apt-get update
apt-get dist-upgrade
apt-get clean
init 5 && exit
```
[COLOR="red"]NEVER DIST-UPGRADE [or UPGRADE] with adept, synaptic or aptitude:
If you do not go to init 3, well tough for you, you have been warned![/COLOR]

---

### Post by claudecat on 2012-12-19
Hehe - the aptosid folks are a bit "careful". While it's certainly advisable to dist-upgrade outside of X, as a practical matter it will almost never cause a problem. I've been running aptosid (and testing for that matter) for years now and have never once had a problem when using synaptic to upgrade (equivalent to dist-upgrade). The only time to be careful is when an entire DE upgrade (KDE or Gnome) is in the process of being added to the repos - best to wait until it's all there.

---

### Post by Lyfang on 2012-12-25
> **deadflowr said:**
> That's just not true.
Of course there is risk. Debian testing still gets newer packages, and  will continue to get newer packages until they decide what they have  will become the new stable.
But yes like Ubuntu, it is quite stable. And like Ubuntu, it is not risk-free.

> **Chdslv said:**
> The only risk being that you may have to reinstall, if something goes wrong. :)
And the whole thing could be wheezy...

  Not what the average home users expect. In *unstable* and *testing* a simple upgrade can break anything (of the packages). *testing* does receive security updates but can still have hidden bugs. *stable* has been much better tested. But some think *stable* has really outdated packages. I mostly prefer to have newer packages than what *stable* has to offer. Maybe there’s a lack of developers, time and resources? *stable*,* testing* or *unstable*? It depends on what the computer is used for.

---

### Post by Lyfang on 2013-03-23
Still running on the same testing installation!

About the experimental packages
"Warning: This package is from the experimental distribution. That means it is likely unstable or buggy, and it may even cause data loss. Please be sure to consult the changelog and other possible documentation before using it."

Mozilla Iceweasel 19.0.2 and Lightspark 0.7.2-1 (YouTube works) experimental packages run great for me. Not experimental package but proprietary Skype 4.1.0.20 cannot connect. I couldn’t install LibreOffice 4 experimental packages.

Is done at your own risk & I take no responsibility for any loss or damage. 

Ubuntu kernel on Debian Wheezy works. Download and install from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc3-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc3-raring/)

Open Root-terminal (or LXTerminal with su command): 
dpkg -i linux-headers-3.9.0-030900rc3_3.9.0-030900rc3.201303171935_all.deb

dpkg -i linux-headers-3.9.0-030900rc3-generic_3.9.0-030900rc3.201303171935_i386.deb

dpkg -i linux-image-3.9.0-030900rc3-generic_3.9.0-030900rc3.201303171935_i386.deb

dpkg -i linux-image-extra-3.9.0-030900rc3-generic_3.9.0-030900rc3.201303171935_i386.deb

update-grub

uname -a
Linux debian 3.9.0-030900rc3-generic #201303171935 SMP Sun Mar 17 23:44:49 UTC 2013 i686 GNU/Linux

linux-image-extra contained extra drivers which I needed for my Acer Aspire One. The generic kernel gave me only screen resolution of 800x600. Extra gave me correct 1024x600.

---

### Post by Lyfang on 2013-06-15
My friend has an older computer and runs Debian 7 "Wheezy" stable with LXDE (dual-boot Wheezy and Windows XP). But with an older computer with an integrated graphics card, Skype 4.2.0.11 shows a blue screen when making a video call. Not a blue screen of death but blue video. When I make a video call I can place a window above my video picture and the blue video disappears. I can still see my friends picture without a problem on this old computer then. CPU usage is still 100% when I make a video call.I have also installed Kdenlive but I had problems importing videos since Kdenlive could not import videos when some folders included åäö (Swedish letters).lshw (hardware lister) command:  

  *-display             description: VGA compatible controller             product: 82865G Integrated Graphics Controller             vendor: Intel Corporation             physical id: 2             bus info: pci@0000:00:02.0             version: 02             width: 32 bits             clock: 33MHz             capabilities: pm vga_controller bus_master cap_list rom             configuration: driver=i915 latency=0             resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff ioport:efa8(size=8)   

  *-cpu          description: CPU          product: Intel(R) Celeron(R) CPU 2.66GHz          vendor: Intel Corp.          physical id: 400          bus info: cpu@0          version: 15.4.1          serial: 0000-0F41-0000-0000-0000-0000          slot: Microprocessor          size: 2666MHz          capacity: 3600MHz          width: 32 bits          clock: 533MHz          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr          configuration: id=0 

 My friend liked Ubuntu since it was quite easy to use. I had to install XScreeenSaver on Debian in order to change the screensaver.

---

### Post by monkeybrain2012 on 2013-06-15
> **deadflowr said:**
> That's just not true.
Of course there is risk. Debian testing still gets newer packages, and will continue to get newer packages until they decide what they have will become the new stable.
But yes like Ubuntu, it is quite stable. And like Ubuntu, it is not risk-free.

"Testing" is pretty old anyway. It is not like you are getting the latest and greatest (in the sense of Arch), packages in testing are only "less old". Ubuntu LTS is based on testing, but otherwse it is based on Debian unstable (but smoothing it up for ordinary desktop users, Debian unstable is really rough and seems to aim at testers)

Generally I don't really see the point of LXDE, if anyone wants Debian stable or testing he/she can just install Debain. It is not that hard to set up (unstable is a different matter)

---

### Post by Lyfang on 2013-07-10
Using Debian unstable (sid) with Openbox installed. Great for those with skills needed. Is done at your own risk and I take no responsibility for any loss or damage (as usual).

# Start LXDE if Openbox is set by default and if you feel LXDE is needed
```
exec startlxde
```

# Changed GRUB_DEFAULT to boot Windows as default, rare thing but sometimes necessary
```
sudo nano /etc/default/grub
```
GRUB_DEFAULT=1

```
sudo update-grub
```
# Autostart applications when Openbox starts
```
leafpad ~/.config/openbox/autostart 
```
# Planning to move this to Xorg instead of using xrandr
# Warning! Don't forget to set the right resolution and refresh rate
xrandr --output VGA-0 --mode 1920x1080 --rate 60 &
(sleep 10s && nmcli con up id tele2) &
# Application is executed X seconds after the script is run
# Besides the point: If you realize why (you can only be young once ... with no ill intentions)
(sleep 20s && chromium [http://zoosk.com/](http://zoosk.com/)) &
(sleep 55s && chromium [http://badoo.com/](http://badoo.com/)) &
(sleep 65s && chromium [http://gmail.com](http://gmail.com)) &
(sleep 75s && chromium [https://facebook.com/](https://facebook.com/)) &
(sleep 85s && chromium [http://awarenessact.com/user/login/](http://awarenessact.com/user/login/)) &
(sleep 105s && chromium [http://happypancake.com/](http://happypancake.com/)) &
(sleep 110s && transmission-gtk) &
# Note: chromium at 50s added +5 seconds after zoosk.com when my connection was being throttled by my Internet provider
# I use lxrandr to manually turn off laptop screen and use external monitor only
(sleep 120s && lxrandr) &

# Installing Google Chrome
```
sudo apt-get install libcurl3
```
# Find the directory of the Google Chrome installer
```
sudo dpkg -i google-chrome-stable_current_amd64.deb
```
# Set default browser
```
sudo update-alternatives --config x-www-browser
```

# It's good to know these commands as well
```
sudo apt-get update && sudo apt-get upgrade
sudo dpkg-reconfigure gdm3
sudo shutdown -h now
```
# Sets up a cron job that will periodically send in statistics
```
sudo dpkg-reconfigure popularity-contest
sudo popularity-contest
```

---

### Post by Lyfang on 2013-07-10
Using Debian unstable (sid) with Openbox installed. Great for those with skills needed. Is done at your own risk and I take no responsibility for any loss or damage (as usual).

# Start LXDE if Openbox is set by default and if you feel LXDE is needed
```
exec startlxde
```

# Changed GRUB_DEFAULT to boot Windows as default, rare thing but sometimes necessary
```
sudo nano /etc/default/grub
```
GRUB_DEFAULT=1

```
sudo update-grub
```
# Autostart applications when Openbox starts
```
leafpad ~/.config/openbox/autostart 
```
# Planning to move this to Xorg instead of using xrandr
# Warning! Don't forget to set the right resolution and refresh rate
xrandr --output VGA-0 --mode 1920x1080 --rate 60 &
(sleep 10s && nmcli con up id tele2) &
# Application is executed X seconds after the script is run
# Besides the point: If you realize why (you can only be young once ... with no ill intentions)
(sleep 20s && chromium [http://zoosk.com/](http://zoosk.com/)) &
(sleep 55s && chromium [http://badoo.com/](http://badoo.com/)) &
(sleep 65s && chromium [http://gmail.com](http://gmail.com)) &
(sleep 75s && chromium [https://facebook.com/](https://facebook.com/)) &
(sleep 85s && chromium [http://awarenessact.com/user/login/](http://awarenessact.com/user/login/)) &
(sleep 105s && chromium [http://happypancake.com/](http://happypancake.com/)) &
(sleep 110s && transmission-gtk) &
# Note: chromium at 50s added +5 seconds after zoosk.com when my connection was being throttled by my Internet provider
# I use lxrandr to manually turn off laptop screen and use external monitor only
(sleep 120s && lxrandr) &

# Installing Google Chrome (Pepper Flash Player included)
```
sudo apt-get install libcurl3
```
# Find the directory of the Google Chrome installer
```
sudo dpkg -i google-chrome-stable_current_amd64.deb
```
# Set default browser
```
sudo update-alternatives --config x-www-browser
```

# It's good to know these commands as well
```
sudo apt-get update && sudo apt-get upgrade
sudo dpkg-reconfigure gdm3
sudo shutdown -h now
```
# Sets up a cron job that will periodically send in statistics
```
sudo dpkg-reconfigure popularity-contest
sudo popularity-contest
```

---

### Post by Lyfang on 2013-12-02
Hi! I'm currently running Ubuntu 13.10 with LXDE (on that computer which I wrote: "My installation creates a fast system. It's fast!"). It doesn't run well however on Ubuntu with Unity. I'm not the only one with this problem:

"For the last few weeks, unity and/or compiz has been crazy slow on both my computers with Intel graphics, alt+tab can take 2-3 seconds to complete.!" - [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1187500](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1187500)

I love Debian, but since Ubuntu has tools to install printers and has better support for restricted formats, that makes computing easier. With Ubuntu you have less to worry about if you are a computer novice.

---

### Post by sudodus on 2013-12-02
Are you running LXDE with some tweaks?

Have you compared it to Lubuntu or Xubuntu?

> I love Debian, but since Ubuntu has tools to install printers and has  better support for restricted formats, that makes computing easier. With  Ubuntu you have less to worry about if you are a computer novice. 				

This is true. There are advantages and disadvantages with Debian and Ubuntu, and with other distros as well :-D

---

### Post by Lyfang on 2014-01-20
No tweaks at all. Only a modified autostart file. I prefer using OpenBox. I can start LXDE from the Terminal at any time. LXDE will provide maximum comfort.

---

### Post by Lyfang on 2014-05-28
Same installation(!) working great with small flaws. Debian Sid works faster than Windows 7 on this computer, it's not mine. Dual-booting works great.
 
lsb_release -a 
```
No LSB modules are available. 
Distributor ID:    Debian 
Description:    Debian GNU/Linux unstable (sid) 
Release:    unstable 
Codename:    sid 
```
cat /etc/debian_version 
```
jessie/sid 
```
leafpad ~/.config/openbox/autostart 
```
# in future moving to Xorg instead of using xrandr 
xrandr --output VGA-0 --mode 1920x1080 --rate 60 & 
# using LXDE 
(sleep 2s && exec startlxde) & 
#nmcli doesn't work after sudo apt-get update && sudo apt-get upgrade 
#(sleep 20s && nmcli con up id tele2) & 
# application_description and is executed X seconds after the script is run. 
(sleep 30s && iceweasel) & 
#lxrandr to turn of laptop screen and use external monitor isn't needed with LXDE 
#(sleep 65s && lxrandr) & 
```
gksudo leafpad /etc/default/grub 
```
#changed boot order after upgrade from 6 to 2 to boot Windows default.
GRUB_DEFAULT=2 
```
sudo update-grub

I installed and ran BleachBit. Skipping wipe free disk space, good to run however for privacy.

---

### Post by Lyfang on 2014-10-13
I'm impressed of how long I could run the same installation on this computer with dual-boot Debian Sid/Windows 7. However the "option1ttyUSB0: option_instat_callback: error -2" is making me unable to connect to the Internet on Linux. 
```
[  304.692989] usb1-3: USB disconnect, device number 3
[  304.693494]option1 ttyUSB0: GSM modem (1-port) converter now disconnected fromttyUSB0
[  304.693554]option 1-3:1.0: device disconnected
[  304.693952]option1 ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed.(-19)
[  304.693965]option1 ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed.(-19)
[  304.693972]option1 ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed.(-19)
[  304.693979]option1 ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed.(-19)
[  304.697320]option1 ttyUSB1: GSM modem (1-port) converter now disconnected fromttyUSB1
[  304.697374]option 1-3:1.1: device disconnected
[  304.697829]option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed.(-19)
[  304.697840]option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed.(-19)
[  304.697847]option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed.(-19)
[  304.697853]option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed.(-19)
[  304.704670]option1 ttyUSB2: GSM modem (1-port) converter now disconnected fromttyUSB2
[  304.704735]option 1-3:1.2: device disconnected
[  304.707444]qmi_wwan 1-3:1.3 wwan0: unregister 'qmi_wwan' usb-0000:00:13.5-3,WWAN/QMI device
[  312.332121] usb1-3: new high-speed USB device number 4 using ehci-pci
[  312.466788] usb1-3: New USB device found, idVendor=12d1, idProduct=1505
[  312.466806] usb1-3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[  312.466813] usb1-3: Product: HUAWEI Mobile
[  312.466819] usb1-3: Manufacturer: Huawei Technologies
[  312.475047]usb-storage 1-3:1.0: USB Mass Storage device detected
[  312.480263] scsi8: usb-storage 1-3:1.0
[  313.360935] usb1-3: USB disconnect, device number 4
[  321.708183] usb1-3: new high-speed USB device number 5 using ehci-pci
[  321.843392] usb1-3: New USB device found, idVendor=12d1, idProduct=1506
[  321.843408] usb1-3: New USB device strings: Mfr=4, Product=3, SerialNumber=0
[  321.843415] usb1-3: Product: HUAWEI Mobile
[  321.843421] usb1-3: Manufacturer: Huawei Technologies
[  321.851245]option 1-3:1.0: GSM modem (1-port) converter detected
[  321.851549] usb1-3: GSM modem (1-port) converter now attached to ttyUSB0
[  321.851860]option 1-3:1.1: GSM modem (1-port) converter detected
[  321.852484] usb1-3: GSM modem (1-port) converter now attached to ttyUSB3
[  321.852740]option 1-3:1.2: GSM modem (1-port) converter detected
[  321.852971] usb1-3: GSM modem (1-port) converter now attached to ttyUSB4
[  321.856859]qmi_wwan 1-3:1.3: cdc-wdm0: USB WDM device
[  321.858297]qmi_wwan 1-3:1.3 wwan0: register 'qmi_wwan' at usb-0000:00:13.5-3,WWAN/QMI device, 00:a0:c6:00:00:00
[  321.859785]usb-storage 1-3:1.5: USB Mass Storage device detected
[  321.868142] scsi9: usb-storage 1-3:1.5
[  321.868754]usb-storage 1-3:1.6: USB Mass Storage device detected
[  321.876078]scsi10 : usb-storage 1-3:1.6
[  322.869825] scsi9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI:0
[  322.882068] scsi10:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0ANSI: 2
[  322.889688] sr1:scsi-1 drive
[  322.891184] sr9:0:0:0: Attached scsi CD-ROM sr1
[  322.895270] sr9:0:0:0: Attached scsi generic sg2 type 5
[  322.897882] sd10:0:0:0: Attached scsi generic sg3 type 0
[  322.909045] sd10:0:0:0: [sdb] Attached SCSI removable disk
[ 329.147169] option1 ttyUSB0: option_instat_callback: error -2

```

---

