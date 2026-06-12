---
title: "Gnome 3. System Settings not available"
date: 2013-05-06
forum: Desktop Environments
---

### Post by Hodevah on 2013-05-06
Hi. 
I recently installed Gnome 3 DE on Ubuntu 13.04. It is _not_ LTS. 
I have done a search on the forums for related problems and solutions but I have not found a suitable solution to the problem I am facing currently. 

The download of Gnome 3 DE went fine. The install of it seemed to have gone fine as well. Below you can see the output of the Terminal commands that I followed to download/install this DE. I find that I cannot access the System Settings in any of the DE's I have left (after which for some unknown reason, Gnome 3's install seemed to have deleted Cinammon DE but left intact XFCE DE). I can deal with re-installing the Cinammon DE later. 

Regardless, the System Settings do start up but they do not follow through thier entirety to being fully visible/accessible. All I get is the start-up at the task bar at the top of Gnome 3. I also cannot access the System Settings on XFCE either. By being able to fully access them, I mean either via right-click on desktop or via the Activities Menu. They are of course as being _visible to being_ accessible, just not _actually accessible_. 

The same can be said of Ubuntu Tweak. Visible but not actually accessible. Starting up but not coming on fully accessible. Both of these applications are visible also througth the Applications Finder but agains not entirely accessible. 
None of these problems were present prior to the install of Gnome 3 DE. 

As a side note, in Ubuntu (fallback) the top and bottom task bars are visible but they are all whited out. This happened after the install. It was not like this before. 



 I don't think this output might be much needed but here is the output of lspci just in case:

```
user@user-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1c.7 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts XT [Radeon HD 6870]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Barts HDMI Audio [Radeon HD 6800 Series]
03:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
04:00.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:01.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:04.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:05.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:07.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
05:09.0 PCI bridge: PLX Technology, Inc. PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
07:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11)
0a:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 30)
0b:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
0c:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11)
user@user-desktop:~$ 
```

Again, just in case.

```
user@user-desktop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD BARTS
OpenGL version string:  3.0 Mesa 9.1.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```







The history output of the commands I followed to download/install Gnome 3.

```
user@user-desktop:~$ cat ~/.bash_history
sudo apt-get install myunity
sudo apt-get autoclean
autoclean
sudo apt-get autoclean
sudo apt-get autoremove
df
sudo update-grub; lsb_release-a; uname -a
sudo apt-get autoclean
sudo apt-get install localpurge
sudo apt-get install deborphan
gksudo /usr/lib/lightdm/
sudo apt-get update
sudo apt-add-repository ppa:efl/trunk
exit
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get clean
exit
sudo add-apt-repository ppa:ricotz/testing
sudo add-apt-repository:gnome3-team/gnome3
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:gnome3-team/gnome3-staging
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gnome-shell gnome-session
sudo apt-get -f install
sudo apt-get install gnome-shell
sudo apt-get install gnome-session
sudo apt-get update
exit
user@user-desktop:~$ 
```

History output

```
user@user-desktop:~$ history
    1  sudo apt-get install myunity
    2  sudo apt-get autoclean
    3  autoclean
    4  sudo apt-get autoclean
    5  sudo apt-get autoremove
    6  df
    7  sudo update-grub; lsb_release-a; uname -a
    8  sudo apt-get autoclean
    9  sudo apt-get install localpurge
   10  sudo apt-get install deborphan
   11  gksudo /usr/lib/lightdm/
   12  sudo apt-get update
   13  sudo apt-add-repository ppa:efl/trunk
   14  exit
   15  sudo add-apt-repository ppa:gnome3-team/gnome3
   16  sudo apt-get clean
   17  exit
   18  sudo add-apt-repository ppa:ricotz/testing
   19  sudo add-apt-repository:gnome3-team/gnome3
   20  sudo add-apt-repository ppa:gnome3-team/gnome3
   21  sudo add-apt-repository ppa:gnome3-team/gnome3-staging
   22  sudo add-apt-repository ppa:gnome3-team/gnome3
   23  sudo apt-get update
   24  sudo apt-get upgrade
   25  sudo apt-get install gnome-shell gnome-session
   26  sudo apt-get -f install
   27  sudo apt-get install gnome-shell
   28  sudo apt-get install gnome-session
   29  sudo apt-get update
   30  exit
   31  cat ~/.bash_history
   32  history
user@user-desktop:~$ 
```

---

### Post by Hodevah on 2013-05-07
ok. so for some reason, I don't know what I did. Some kind of update or something. But I have the System Settings up and running. Great. Now to solve the other issue about Ubuntu Tweak crashing. Much like the System Settings did.
So as far as I'm concerned. This issue is resolved except that I can't seem to find the 'SOLVED' in the thread tools.

---

