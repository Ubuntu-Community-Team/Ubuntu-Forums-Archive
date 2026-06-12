---
title: "Fly box fly, list of (un)coventional improvements"
date: 2011-12-17
forum: Desktop Environments
---

### Post by dentaku65 on 2011-12-17
Hi,

here a list of improvements for your box.
[COLOR="Red"]Be aware of the potential disaster the [COLOR="DarkRed"]rm -rf[/COLOR] command can cause to your system! (Iowan)[/COLOR]

Works perfect on Ubuntu Lucid and Xubuntu Oneiric; both machines in my case are very with low profile hardware; an old Laptop and "new" netbook :)

**Make some performance tests**
**ADSL Speed**
For the ADSL connectivity go to:
[http://www.speedtest.net/](http://www.speedtest.net/)
and track down the values

**Interface environment**
Download GtkPerf for the Gnome/XFCE
```
sudo apt-get install gtkperf
```
Execute:
```
gtkperf
```
and track down the values (basically time)

**NOTE**
Please, for practicality of this "guide", I suggest to install gedit in order to follow the commands indicated if you are not an experienced user and if you are not in Gnome environment.
```
sudo apt-get install gedit
``` 

**1) Decrease the number of available consoles**
Edit:
```
sudo gedit /etc/default/console-setup
```
Find this value:
> ACTIVE_CONSOLES="/dev/tty[1-6]"
Replace with this value:
> ACTIVE_CONSOLES="/dev/tty[1-2]"
Save. Exit
Two virtual consoles are fairly enough for a personal machine.

**2) Improve system and network via sysctl.conf**
Save the original sysctl.conf
```
sudo mv /etc/sysctl.conf /etc/sysctl.conf.ORIGINAL
```
Create an empty sysctl.conf
```
sudo gedit /etc/sysctl.conf
```
And paste the following (in [COLOR="Red"]red[/COLOR] values only for notebook/netbook):
> ##Improve system
#Improve memory
vm.swappiness=10

#File/folder browsing speed
vm.vfs_cache_pressure=50

#Set maximum amount of memory allocated to shm to 256MB
kernel.shmmax = 268435456

#(default 499)
vm.dirty_writeback_centisecs = 1500
 
#(default 10)
vm.dirty_ratio = 20
 
#(default 5)
vm.dirty_background_ratio = 10
 
#(default 0)
[COLOR="Red"]vm.laptop_mode = 5[/COLOR]
## End improve system

## Improve Network and tweak broadband
net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
## End improve Network and tweak broadband
Save. Exit. Load the values to the system permanently:
```
sudo sysctl -p
```

**3) Optimize UI and browsing experience**
Discover your hostname, type in terminal:
```
hostname
```
The output will be:
> *<your_host_name>*
Save your /etc/hosts file:
```
sudo mv /etc/hosts /etc/hosts.ORIGINAL
```
Create a new /etc/hosts file:
```
sudo gedit /etc/hosts
```
And write as follow:
> 127.0.0.1	localhost *<your_host_name>*
127.0.1.1	localhost *<your_host_name>*
Save. Exit.

**4) Improve system with tmpfs (reduce I/O on disks)**
Reboot the system. In [COLOR="Red"]red[/COLOR] extreme settings.
Delete all temp stuff
```
sudo rm -rf /tmp
```
```
[COLOR="Red"]sudo rm -rf /var/tmp[/COLOR]
```
```
[COLOR="Red"]sudo rm -rf /var/log[/COLOR]
```
Create new temp stuff:
```
sudo mkdir /tmp
```
```
[COLOR="Red"]sudo mkdir /var/tmp[/COLOR]
```
```
[COLOR="Red"]sudo mkdir /var/log[/COLOR]
```
Edit /etc/fstab
```
sudo gedit /etc/fstab
```
And add at the end of the file the following:
> #tmpfs
tmpfs /tmp     tmpfs defaults,noatime,mode=1777 0 0
[COLOR="Red"]tmpfs /var/log tmpfs defaults,noatime,mode=1777 0 0[/COLOR]
[COLOR="Red"]tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0[/COLOR]
Save. Exit. Load tmpfs temp areas:
```
sudo mount -a
```
The extreme settings are referring to the fact that if you need the history of your logs (/var/log) you will loose them at every reboot; for /var/tmp I'm not so sure that is ideal for some stuff from KDE environment and/or KDE application (some hints needed).

**5) Move Flash cache in tmpfs**
If you complete the step 4), move Flash temporary files in tmpfs.
Close your browser, open a terminal and go to your home dir:
```
cd $HOME
```
Delete Flash stuff:
```
rm -fr .macromedia
```
```
rm -fr .adobe
```
Symlink Flash stuff:
```
sudo ln -s /tmp .macromedia
```
```
sudo ln -s /tmp .adobe
```
Done.

**6) Firefox hotfix**
Edit/create /etc/firefox/firefoxrc file
```
sudo gedit /etc/firefox/firefoxrc
```
And write as follow:
> #Set pulseaudio as audio wrapper for Firefox 
[COLOR="Red"]FIREFOX_DSP="padsp"[/COLOR]
#Fix Firefox ARGB visual (flash) 
export XLIB_SKIP_ARGB_VISUALS=1
#Disable PANGO in Firefox 
export MOZ_DISABLE_PANGO=1
Save. Exit. Please, if you are not using Pulseaudio system comment out the [COLOR="Red"]red[/COLOR] line (#)

**7) Use OpenDNS or Google DNS with DHCP**
Edit /etc/dhcp/dhclient.conf
```
sudo gedit /etc/dhcp/dhclient.conf
```
Add the following at the end of the file:
```
#OpenDNS
#prepend domain-name-servers 208.67.222.222, 208.67.220.220;

#Google DNS
[COLOR="Green"]prepend domain-name-servers 8.8.8.8, 8.8.4.4;[/COLOR]
```
Save. Exit. In green the DNS choose (GoogleDNS); you can comment it and uncomment the OpenDNS one, or you can comment both of them and use your provider DNS. Reboot needed upon any DNS change in order to get them operative.

**end) Reboot the system**

At this point you can try initial performance tests and compare the results.

Enjoy!

---

### Post by squaregoldfish on 2011-12-18
It would be helpful if you said what all these changes do, so we can decide what may or may not be appropriate for our specific systems. That and the fact that making a load of fundamental system changes without knowing what it is you're doing is generally a bad idea.

Steve.

---

### Post by dentaku65 on 2011-12-18
> **squaregoldfish said:**
> It would be helpful if you said what all these changes do, so we can decide what may or may not be appropriate for our specific systems. That and the fact that making a load of fundamental system changes without knowing what it is you're doing is generally a bad idea.

Steve.

Hi Steve,
as I said at the beginning of the post these optimizations are basically for low profile hardware (like my machines); none of these tweaks are in a way "fundamental" for the system except for point 4) that it is a little bit "advanced"; all of them can be quickly reverted. If you need some other specs on the points exposed just ask.

kr,
Den

---

