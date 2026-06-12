---
title: "Run full LXDE or XFCE Desktop Headless with XVFB?"
date: 2016-03-24
forum: Desktop Environments
---

### Post by mattlach on 2016-03-24
Hey all,

I have been googling the hell out of this without finding any guides or suggestions how to do it.

I plan on setting up a rare server that requires a GUI (MythBuntu backend) inside an LXC container.   

The container - naturally - does not have a display device.  The goal is that the GUI logon screen can be displayed on a remote computer using whatever remote access process will work, VNC, X2go, X SSH tunneling, anything that will work.

The mytbuntu backend is a dedicated backend, not -obviously - intended for video playback, but it DOES need to be able to display the backend configuration interface (which for some reason is GUI based, rather than most server applications which can be configured using text config files.

Once connected remotely ideally I should be presented with the GUI logon screen, enter my credentials, and have the window manager load, just like I would on a local machine.   if I were to disconnect, I need screen-like behavior, where I can reconnect and continue my work, and when I am ready, log off the window manager.

Since there is no way to locally log in to the GUI, this precludes screen sharing setups that load after login, as you would need a local display in order to log in, before you can connect remotely.

So how do I do this?   Can I somehow edit xorg.conf and configure an xvfb display that loads every time instead of a physical display?   What remote management tools can support this behavior?   I have heard vnc4server and x2go mentioned, but I don't know if they can do what I need.

I'd appreciate any input!

Thanks,
Matt

---

### Post by TheFu on 2016-03-24
No use for xvfb at all. That is usually used/needed when lazy programmers link in X-client libraries that aren't needed/wanted on a pure server.  Oracle had a habit of doing this, as I recall when I worked for "the man".  Can't think of any other major software vender who did. 

[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) will work.  I've been using x2go for a few years now and used freenx before that.  Of course, the mythbackend needs to have X11 client libraries installed for any of this to work - that is handled with a **sudo apt-get install lxde** (no need for the full LXDE desktop).  X-Windows C/S is backwards of what most people think of for C/S.  The X-server runs on the physical machine you sit behind and the X-client application(s) run on the remote machine.  But ... when using x2go, both run on the same remote system.

Also, I should say that I've never tried this with any containers, but on virtual machines it all works just like with a real machine.  If the container has a separate IP on the subnet just like any other physical machine, I can't see any issues with this.

This stuff is standard X/Windows - which I was a developer of back in the 1990s.

KVM is better for your soul, if not for your wallet (getting paid for VMware work is nice).

Follow the normal instructions to get x2go running using a PPA - [https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative](https://www.howtoforge.com/how-to-install-x2goserver-on-ubuntu-14.04-as-vnc-alternative) or from the x2go website. Of course, you'll want ssh-keys setup before that to make life easier. x2go honors std ssh-key-based authentication. 

If you say which clients you have, I can provide other tips.  For Linux clients, the x2go-client sorta just works.  Under Windows, you'll need to load the fonts. Can't help with OSX.

Anyway - hope that all helps.  BTW, my normal desktop runs in a VM (KVM) inside a private cloud accessible through x2go from anywhere in the world with pretty much the same speed (anything above isdn is fine). Plus, since the NX protocol includes ssh-tunneling by default, you don't need a separate VPN like VNC requires to be secure.  I'm using it now to type this.

---

### Post by mattlach on 2016-03-25
Thank you, this is very helpful!

I am currently in the planning phase for a migration project.   I currently have my mythbuntu backend running in a VM Guest on my ESXi server.  For a variety of reasons I am planning on migrating over to Proxmox.   I could just make it a KVM VM guest, but I am very intrigued about the resource saving capabilities of LXC containers, especially since with all my guests, the 96GB of RAM on my server never seem to be enough!  (The dual hexacore Xeons with hyperthreading were - on the other hand - total overkill despite their low clocks, and a mistake when I built this server a few years back)

Anyway, this is a "home production server" of sorts, doing among many other things, MythTV, NAS and Firewall/Router duties, so when it goes down, the house has no TV, no internet and no one can access their files, thus necessitating some pre-planning for the migration.

I will have the house to myself for a week in mid April when I will do the full migration without annoying others, and I am trying to learn as much as possible before then!  (I'm kicking myself over that my window for migration is set to occur so shortly before the final release of 16.04, I would so much rather have done my installs on the newest LTS and had it last work a while...)

I hope you don't mind if I come back with follow-up questions as I actually start this work!

> **TheFu said:**
> 
[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) will work.  I've been using x2go for a few years now and used freenx before that.  Of course, the mythbackend needs to have X11 client libraries installed for any of this to work - that is handled with a **sudo apt-get install lxde** (no need for the full LXDE desktop).  X-Windows C/S is backwards of what most people think of for C/S.  The X-server runs on the physical machine you sit behind and the X-client application(s) run on the remote machine.  But ... when using x2go, both run on the same remote system.

This is very interesting.   I guess I had assumed that if I did an apt-get install lxde, the dependencies would automatically pull in the whole x server.

> **TheFu said:**
> 
This stuff is standard X/Windows - which I was a developer of back in the 1990s.


Yeah, while I've been primarily been running one Linux distribution or another on both my desktop and my servers since college (~16 years), I've never gotten into the advanced remote X11 ssh tunneling stuff.  I always had desktops with local X, and servers without the need for a gui at all, I just managed from the command line.  MythTV is one of those unusual beasts from a server standpoint, that requires GUI access for configuration and management.

---

### Post by TheFu on 2016-03-25
Use ssh -X userid@server.
I know that Kodi wants direct video card access, but I know it is possible to trick it into allowing remote connections instead.

I wouldn't use proxmox for a number of reasons. I'd also be cautious using any container-based solution.  You need an LTS and honestly, 14.04 container support wasn't all that great.  Plus, I wouldn't touch 16.04 until June-ish - let the big issues be solved.  Don't forget that 16.04 doesn't like Radeon cards when released. It will take a few months, assuming you want the proprietary video drivers. The F/LOSS drivers should be fine on release for everyone who isn't a gamer.

That is a monster box.  I've been doing virtualization since the late 1990s.  I've never needed more than 8G of RAM and my 16G RAM system uses most of that for disk buffers only.

At home, I won't touch server hardware - too much power-suck and too much noise.  A Core i5 for $170 easily runs 8 VMs under KVM here. Call it "production if you like.  I have 2 of those systems, each able to run everything should the other fail.  For storage providers and routers, I use real hardware - no virtualization. Last system I built was G3258 Pentium - an amazing, cheap, CPU.  Use an AMD E350 for a router.  The other systems are 1st-gen Core i5 or i7 boxes. Retired all the C2D systems last year.  OTOH, my TV recording happens using Win7 with media center inside a KVM VM.  The tuners are networked connected to attic antennas facing very different ways.  71 channels last time I scanned. 40 of those are audio-only, shopping, or religious wackos, ya'll.

I dumped ESXi about 5 yrs ago when VMware marketing decided to screw their clients over pricing. We moved all our clients off too within 6 months, over the KVM.  They've been happier. No issues and they definitely like not paying $12K/yr for their licenses. vsphere is a huge racket for small-ish companies, plus I hate how everything in the VMware-world costs between $1000 and $20K for something that should be included.  Whatever.  VMware paid the bills for a few yrs, until they got greedy (learned that from EMC, methinks).

Back on topic - I don't know if lxde pulls in the X-server libraries or not. I hope not, that doesn't make any sense, since WMs can be run remotely. Ought to be a way to view all the dependency. Searched on my "desktop" and another system and didn't find any packages for lxde or openbox - guess they are metapackages? Sorry I'm not more help.  **dpkg -f /path/to/file-version.deb Depends** will show dependencies. I had to look it up, figured posting it would help someone, a lurker perhaps?

At some point, I expect to migrate to MythTV. I've tried twice many years ago, but didn't have well-supported video capture cards, so it didn't go well. The free schedule data from MSFT is hard to give up, though it is broke since July on 1 of the systems.

Am I the only person doing a bi-annual "data center consolidation?" VM sprawl is a real thing here.  Switched to using chromebooks running Linux as my laptops. 8+ hrs of battery, 1080p, and 3 lbs is addictive.

---

### Post by mattlach on 2016-03-25
> **TheFu said:**
> Use ssh -X userid@server.
I know that Kodi wants direct video card access, but I know it is possible to trick it into allowing remote connections instead.

Well, for Kodi I plan on actually installing two GeForce GT720's in the box, forwarding the required devices to get sound and GPU out to two LXC containers respectively, and use Kodi installs inside these containers together with 10GbaseT HDMI over Ethernet and USB over Ethernet extenders as my HTPC's

It seems like a rather extreme solution, but I have found that while Intel's IGP's (as tested under Linux with a hacked Asus Chromebox) and  AMD's APU's (as tested with an A10-7850K box) work well for content played from my NAS, neither like mpeg2 streams coming from the MythTV plugin for Kodi very much, with frequent freezes and crashes, especially on lower quality streams.  Nvidia and VDPAU - however - has always worked flawlessly for me.   I ran the numbers, and figured it would be cheaper and lower power to do it virtualized inside my server with extenders, than it would be to build two new boxes around Nvidia hardware.

I tested this briefly in ESXi 6, and it works well, except for the fact that NVIDIA GPU forwarding in ESXi is an unstable mess.  After hearing lots of people successfully doing Nvidia GPU passthrough in KVM, and reading that Proxmox actively patches around Nvidia's attempts to block passthrough on their consumer GPU's, it became my primary candidate for the great migration away from my ESXi server.

> **TheFu said:**
> 
I wouldn't use proxmox for a number of reasons.

Would you mind providing some more details here?   Proxmox became my number one candidate based on the above Nvidia issue, as well as it supposedly being a good management frontend for KVM and LXC containers.  I am by no means afraid of the command line, and prefer it, but I have heard horror stories about manually managing KVM.

Any further pro/con type input you can provide here would be greatly appreciated.   While Proxmox is my front runner, I still have time left to change my mind.


> **TheFu said:**
> 
 I'd also be cautious using any container-based solution.  You need an LTS and honestly, 14.04 container support wasn't all that great.  Plus, I wouldn't touch 16.04 until June-ish - let the big issues be solved.  Don't forget that 16.04 doesn't like Radeon cards when released. It will take a few months, assuming you want the proprietary video drivers. The F/LOSS drivers should be fine on release for everyone who isn't a gamer.

Well, this is a dedicated server with no gaming pretensions what so ever.   If it weren't for my plan to run virtualized HTPC's, I wouldn't be worried about video output at all, except for the old as dirt on board Matrox chip that outputs the text console.   I have a separate bare metal rig for my Desktop.

> **TheFu said:**
> 
That is a monster box.  I've been doing virtualization since the late 1990s.  I've never needed more than 8G of RAM and my 16G RAM system uses most of that for disk buffers only.

At home, I won't touch server hardware - too much power-suck and too much noise.  A Core i5 for $170 easily runs 8 VMs under KVM here. Call it "production if you like.


Well, I completely overestimated the amount of CPU overhead I'd have with ESXi.   For a number of years I ran ESXi on an AMD FX-8120, and later FX-8350 system, but decided to upgrade to real server hardware due to being able to run registered DIMM's, and being able to exceed 32GB of RAM, the max on the 990FX platform.

RAM is still a limiting factor for me, but only because I give my FreeNAS guest so much of it (64GB).  I originally did this to follow the  FreeNAS RAM recommendations of 2GB for system plus a GB per TB of storage for ARC + plus some more ram to manage L2ARC directory.  I have realized since then that it is a little bit overkill to get it running, but I have some performance issues as it is with my ZFS pool, often skipping when playing back media, so I am reticent to drop it back down.



Other guests that use a lot of RAM are my CrashPlan backup server which - well - crashes if it doesn't have enough RAM to do the client side dedup during backup.  I'd consider this a serious limitation of the service and switch, except for the fact that it is so cheap for the unlimited plan.

The MythTV backend is finicky when RAM gets low, and any swapping can cause skips in playback, so I have given it 4GB (more than it probably needs) just to be on the safe side.

My Unifi controller guest also likes to have a decent amount of RAM to keep the mongodb stuff flowing.  pfSense only uses a GB, and I could probably get by with less.  I also have a bunch of small appliance-type VM's that have 512MB each, and am saving RAM to have enough for 2GB each for the above mentioned KODI frontends.

Between the RAM use for the guests above, and the ESXi overhead (especially with passthrough devices) I'm always chafing under my 96GB limit.  I filled the 12 available slots with 8GB RAM modules, and moving to 16GB modules is prohibitively costly.

Yeah, I experienced how bad server hardware can be when I thought I got a fantastic deal on on a 2U HP DL180 G6 being decomissioned and bought it.   That thing was a regular Jumbo jet in the noise department.   HP in their wisdom put temperature sensors in every single part of those servers, and if you use any non HP hardware the server doesn't recognize the 8 14krpm 80mm fans all spin up to max.   They should  call it the HP DL 180 G6 Dreamliner.

I learned from my mistake, but I didn't blame enterprise hardware per se, but rather decided to never buy anything pre-built again.   There is a lot of enterprise hardware I love, my switches and Unifi AP's among them, as well as my Supermicro server motherboard.  I ordered one of those popular Norco storage chassis, found a now old stock Supermicro dual socket board on eBay and salvaged the dual Xeon's and RAM from the HP server and built my current setup. With my own fans (and the optional 3x 120mm fan center barrier) and fan controllers custom built it's actually reasonable in the noise department, and completely out of earshot where it sits in the basement, unlike the Dreamliner which could be heard two floors up in my bedroom even with all the doors shut(!?)

Power use is in the same ballpark as my AMD FX-8350 system was, at about 260W at the wall, measured with my trusty Kill-A-Watt with the following hardware installed:
- 2x Xeon L5640 (hexacore, HT, 2.2Ghz base, 2.8Ghz turbo)
- 96GB Registered DDR3
- 2x LSI 9211-8i controllers in IT (HBA) mode.
- 2x onboard Intel gigabit Ethernet adapters
- One 4x Intel Pro/1000 PT Gigabit Ethernet card
- One Brocade BR1020 10gig fiber Ethernet adapter with transducer
- 12x WD Red 4TB drives
- 6x 2.5" SSD's
- 3x Gentle Typhoon 120mm fans, 2x 80mm rear exhaust fans included with case, 2x 92mm CPU fans (came with Supermicro CPU coolers)

So I'm quite happy with it.   Neither power use nor noise are extreme.  I probably did over-consolidate though (I was on a consolidation fervor when I built this setup).  It's a bit annoying that the internet goes down every time I have to do maintenance on the server.  I have on occasion considered getting a dedicated Unifi edge router, or building a dedicated pfSense box from spare parts I have laying around (AMD E350, dual port Intel NIC, some spare ram, old drive to boot) but that would just increase power use, as having PfSense running as a VM on a server that is already running anyway costs very little in power, while even a fairly efficient E350 has overhead and PSU losses that add up.   (I know the E350 is supposed to be a 18W TDP part, but my Kill-A-Watt has always measured it much MUCH higher.


> **TheFu said:**
> 
I have 2 of those systems, each able to run everything should the other fail.  For storage providers and routers, I use real hardware - no virtualization. Last system I built was G3258 Pentium - an amazing, cheap, CPU.  Use an AMD E350 for a router.  The other systems are 1st-gen Core i5 or i7 boxes. Retired all the C2D systems last year.  OTOH, my TV recording happens using Win7 with media center inside a KVM VM.  The tuners are networked connected to attic antennas facing very different ways.  71 channels last time I scanned. 40 of those are audio-only, shopping, or religious wackos, ya'll.


That seems pretty nice.   I am intrigued by the redundancy of having multiple servers, but it would never work in my desired setup where I have so many passthrough devices.  Instead I use Virtualization primarily as a means to consolidate things on to one box.

My NAS is handled by a FreeNAS guest installed on my ESXi box.  The two LSI controllers are passed through to it, and it runs my 12 WD Red's in a RAID-60 equivalent mode with two striped 6 drive RAIDz2 vdevs.  I have two mirrored 100GB Intel S3700 SSD's for my intent log/ZIL to make sync writes less punishing, and two striped 128GB Samsung 850 Pro SSD's as L2ARC cache.

I only discovered after the fact that the G3xxx series Pentiums support VT-D and ECC.   If I had known this at the time, I probably would have opted for a couple of those instead.  They are nice power sippers, and very competitively priced.

> **TheFu said:**
> 
I dumped ESXi about 5 yrs ago when VMware marketing decided to screw their clients over pricing. We moved all our clients off too within 6 months, over the KVM.  They've been happier. No issues and they definitely like not paying $12K/yr for their licenses. vsphere is a huge racket for small-ish companies, plus I hate how everything in the VMware-world costs between $1000 and $20K for something that should be included.  Whatever.  VMware paid the bills for a few yrs, until they got greedy (learned that from EMC, methinks).

I'm starting to get frustrated with ESXi for a number of reasons, including free version never getting the most recent bug and security patches, arbitrary limitations to what I can and can't do (like passing through consumer Nvidia GPU's) comparatively high RAM overhead, requiring host reboots for silly things like passthroughs, limiting me to static link bonding instead of real ling aggregation, and having to use the stinking Windows-only client on the free hypervisor.  (I actually have a Windows Virtualbox machine on my Mint 17 desktop just so I can run that stupid client)

I've been using ESXi since a few weeks after the 5.0 launch, and while I liked it at first, I have slowly grown more and more frustrated.   This migration has been a long time coming.  I'm really looking forward to it.

> **TheFu said:**
> 
Back on topic - I don't know if lxde pulls in the X-server libraries or not. I hope not, that doesn't make any sense, since WMs can be run remotely. Ought to be a way to view all the dependency. Searched on my "desktop" and another system and didn't find any packages for lxde or openbox - guess they are metapackages? Sorry I'm not more help.  **dpkg -f /path/to/file-version.deb Depends** will show dependencies. I had to look it up, figured posting it would help someone, a lurker perhaps?

I just ssh:ed in to one of my Ubuntu 14.04 server guests and did this.  Looks like you were right.  I don't see any of the full Xserver packages in this list.  (only - surprisingly - the mesa video drivers?)

```

$ sudo apt-get install lxde
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  acl at-spi2-core colord consolekit dbus-x11 dconf-gsettings-backend
  dconf-service desktop-file-utils dictionaries-common fontconfig
  fontconfig-config fonts-dejavu-core galculator gconf-service
  gconf-service-backend gconf2 gconf2-common gcr gdisk giblib1 gksu
  glib-networking glib-networking-common glib-networking-services
  gnome-keyring gpicview gsettings-desktop-schemas gtk2-engines
  gtk2-engines-pixbuf gvfs gvfs-backends gvfs-common gvfs-daemons gvfs-fuse
  gvfs-libs hicolor-icon-theme leafpad libarchive13 libasound2 libasound2-data
  libatasmart4 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatspi2.0-0
  libauthen-sasl-perl libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-glib1 libbluetooth3 libcairo-gobject2 libcairo2 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra0 libcdio-cdda1 libcdio-paranoia1
  libcdio13 libcolord1 libcolorhug1 libcroco3 libcups2 libdatrie1 libdconf1
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libegl1-mesa
  libegl1-mesa-drivers libencode-locale-perl libexif12 libfile-basedir-perl
  libfile-desktopentry-perl libfile-listing-perl libfile-mimeinfo-perl
  libfm-data libfm-extra4 libfm-gtk-data libfm-gtk4 libfm-modules libfm4
  libfont-afm-perl libfontconfig1 libfontenc1 libgbm1 libgconf-2-4
  libgcr-ui-3-1 libgd3 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgif4
  libgksu2-0 libgl1-mesa-dri libgl1-mesa-glx libglade2-0 libglamor0
  libglapi-mesa libgnome-keyring-common libgnome-keyring0 libgphoto2-6
  libgphoto2-l10n libgphoto2-port10 libgraphite2-3 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop2-7
  libgtop2-common libgudev-1.0-0 libgusb2 libharfbuzz0b libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libice6 libid3tag0 libieee1284-3
  libimlib2 libimobiledevice4 libio-html-perl libio-socket-inet6-perl
  libio-socket-ssl-perl libjasper1 libjpeg-progs libjpeg-turbo-progs
  liblcms2-2 libldb1 libllvm3.4 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzo2-2 libmad0 libmailtools-perl
  libmenu-cache-bin libmenu-cache3 libmtdev1 libmtp-common libmtp-runtime
  libmtp9 libnet-http-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnettle4
  libnotify4 libntdb1 libobrender29 libobt2 libogg0 libopenvg1-mesa
  libp11-kit-gnome-keyring libpam-ck-connector libpam-gnome-keyring
  libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangox-1.0-0 libpangoxft-1.0-0 libpciaccess0 libpixman-1-0 libplist1
  libproxy1 librsvg2-2 librsvg2-common libsane libsane-common libsecret-1-0
  libsecret-common libsm6 libsmbclient libsocket6-perl libsoup2.4-1
  libspice-server1 libstartup-notification0 libtalloc2 libtdb1 libtevent0
  libthai-data libthai0 libtxc-dxtn-s2tc0 libudisks2-0 liburi-perl libusbmuxd2
  libutempter0 libv4l-0 libv4lconvert0 libvorbis0a libvorbisfile3 libvpx1
  libvte-common libvte9 libwayland-client0 libwayland-cursor0
  libwayland-egl1-mesa libwayland-server0 libwbclient0 libwnck-common
  libwnck22 libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2
  libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util0
  libxcb-xfixes0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1
  libxft2 libxi6 libxinerama1 libxkbcommon0 libxkbfile1 libxmmsclient-glib1
  libxmmsclient6 libxmu6 libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1
  libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 lxappearance
  lxde-common lxde-core lxde-icon-theme lxdm lxinput lxmenu-data lxmusic
  lxpanel lxrandr lxsession lxsession-data lxsession-edit lxsession-logout
  lxshortcut lxterminal menu menu-xdg miscfiles notification-daemon obconf
  openbox p11-kit p11-kit-modules p7zip-full pcmanfm python-talloc python-xdg
  samba-libs scrot sound-theme-freedesktop udisks2 usbmuxd x11-common
  x11-utils x11-xkb-utils x11-xserver-utils xarchiver xbitmaps xdg-utils
  xfonts-base xfonts-encodings xfonts-utils xmms2-core xmms2-plugin-alsa
  xmms2-plugin-id3v2 xmms2-plugin-mad xmms2-plugin-vorbis xscreensaver
  xscreensaver-data xserver-common xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware xterm
Suggested packages:
  ispell aspell hunspell wordlist emacsen-common jed-extra
  gconf-defaults-service gvfs-backends-goa obex-data-server samba-common
  evince-gtk lrzip libasound2-plugins alsa-utils libdigest-hmac-perl
  libgssapi-perl libcanberra-gtk0 libcanberra-pulse cups-common libfm-tools
  nautilus-actions libgd-tools libglide3 gphoto2 gtkam libdata-dump-perl
  libjasper-runtime liblcms2-utils libcrypt-ssleay-perl ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp librsvg2-bin avahi-daemon hplip hpoj libsane-extras
  sane-utils libauthen-ntlm-perl lxlauncher lxtask xmms2-plugin-all menu-l10n
  fonts-dejavu libxml2-dev tint2 openbox-menu openbox-gnome-session
  openbox-kde-session p7zip-rar xfsprogs reiserfsprogs exfat-utils btrfs-tools
  mdadm cryptsetup-bin mesa-utils nickle cairo-5c xorg-docs-core arj lhasa rpm
  unar unrar-free gvfs-bin xfs xserver xfishtank xdaliclock xscreensaver-gl
  fortune qcam streamer gdm3 kdm-gdmcompat xfonts-100dpi xfonts-75dpi
  xfonts-scalable gpointing-device-settings touchfreeze xinput firmware-linux
  xfonts-cyrillic
Recommended packages:
  policykit-1-gnome amixer locales-all
The following NEW packages will be installed:
  acl at-spi2-core colord consolekit dbus-x11 dconf-gsettings-backend
  dconf-service desktop-file-utils dictionaries-common fontconfig
  fontconfig-config fonts-dejavu-core galculator gconf-service
  gconf-service-backend gconf2 gconf2-common gcr gdisk giblib1 gksu
  glib-networking glib-networking-common glib-networking-services
  gnome-keyring gpicview gsettings-desktop-schemas gtk2-engines
  gtk2-engines-pixbuf gvfs gvfs-backends gvfs-common gvfs-daemons gvfs-fuse
  gvfs-libs hicolor-icon-theme leafpad libarchive13 libasound2 libasound2-data
  libatasmart4 libatk-bridge2.0-0 libatk1.0-0 libatk1.0-data libatspi2.0-0
  libauthen-sasl-perl libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-glib1 libbluetooth3 libcairo-gobject2 libcairo2 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra0 libcdio-cdda1 libcdio-paranoia1
  libcdio13 libcolord1 libcolorhug1 libcroco3 libcups2 libdatrie1 libdconf1
  libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libegl1-mesa
  libegl1-mesa-drivers libencode-locale-perl libexif12 libfile-basedir-perl
  libfile-desktopentry-perl libfile-listing-perl libfile-mimeinfo-perl
  libfm-data libfm-extra4 libfm-gtk-data libfm-gtk4 libfm-modules libfm4
  libfont-afm-perl libfontconfig1 libfontenc1 libgbm1 libgconf-2-4
  libgcr-ui-3-1 libgd3 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgif4
  libgksu2-0 libgl1-mesa-dri libgl1-mesa-glx libglade2-0 libglamor0
  libglapi-mesa libgnome-keyring-common libgnome-keyring0 libgphoto2-6
  libgphoto2-l10n libgphoto2-port10 libgraphite2-3 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtop2-7
  libgtop2-common libgudev-1.0-0 libgusb2 libharfbuzz0b libhtml-form-perl
  libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libice6 libid3tag0 libieee1284-3
  libimlib2 libimobiledevice4 libio-html-perl libio-socket-inet6-perl
  libio-socket-ssl-perl libjasper1 libjpeg-progs libjpeg-turbo-progs
  liblcms2-2 libldb1 libllvm3.4 liblwp-mediatypes-perl
  liblwp-protocol-https-perl liblzo2-2 libmad0 libmailtools-perl
  libmenu-cache-bin libmenu-cache3 libmtdev1 libmtp-common libmtp-runtime
  libmtp9 libnet-http-perl libnet-smtp-ssl-perl libnet-ssleay-perl libnettle4
  libnotify4 libntdb1 libobrender29 libobt2 libogg0 libopenvg1-mesa
  libp11-kit-gnome-keyring libpam-ck-connector libpam-gnome-keyring
  libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0
  libpangox-1.0-0 libpangoxft-1.0-0 libpciaccess0 libpixman-1-0 libplist1
  libproxy1 librsvg2-2 librsvg2-common libsane libsane-common libsecret-1-0
  libsecret-common libsm6 libsmbclient libsocket6-perl libsoup2.4-1
  libspice-server1 libstartup-notification0 libtalloc2 libtdb1 libtevent0
  libthai-data libthai0 libtxc-dxtn-s2tc0 libudisks2-0 liburi-perl libusbmuxd2
  libutempter0 libv4l-0 libv4lconvert0 libvorbis0a libvorbisfile3 libvpx1
  libvte-common libvte9 libwayland-client0 libwayland-cursor0
  libwayland-egl1-mesa libwayland-server0 libwbclient0 libwnck-common
  libwnck22 libwww-perl libwww-robotrules-perl libx11-xcb1 libxatracker2
  libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0
  libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1 libxcb-util0
  libxcb-xfixes0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1
  libxft2 libxi6 libxinerama1 libxkbcommon0 libxkbfile1 libxmmsclient-glib1
  libxmmsclient6 libxmu6 libxpm4 libxrandr2 libxrender1 libxres1 libxshmfence1
  libxt6 libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 lxappearance lxde
  lxde-common lxde-core lxde-icon-theme lxdm lxinput lxmenu-data lxmusic
  lxpanel lxrandr lxsession lxsession-data lxsession-edit lxsession-logout
  lxshortcut lxterminal menu menu-xdg miscfiles notification-daemon obconf
  openbox p11-kit p11-kit-modules p7zip-full pcmanfm python-talloc python-xdg
  samba-libs scrot sound-theme-freedesktop udisks2 usbmuxd x11-common
  x11-utils x11-xkb-utils x11-xserver-utils xarchiver xbitmaps xdg-utils
  xfonts-base xfonts-encodings xfonts-utils xmms2-core xmms2-plugin-alsa
  xmms2-plugin-id3v2 xmms2-plugin-mad xmms2-plugin-vorbis xscreensaver
  xscreensaver-data xserver-common xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware xterm
0 upgraded, 333 newly installed, 0 to remove and 3 not upgraded.
Need to get 64.9 MB of archives.
After this operation, 258 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```


> **TheFu said:**
> 
At some point, I expect to migrate to MythTV. I've tried twice many years ago, but didn't have well-supported video capture cards, so it didn't go well. The free schedule data from MSFT is hard to give up, though it is broke since July on 1 of the systems.

Yeah, at some point you won't have a choice.  With WMC being dropped in Windows 10, and Microsoft's violent fervor to get everyone to upgrade and drop support WMC's days are numbered. :(

I originally went with MythTV because I wanted to use a VM Guest as the WMC server, and HTPC's as extenders, but there was no software (at least at the time, I understand there is a hack now) that supported using an actual computer as an extender.   You had to either buy a dedicated front end or an Xbox, and I wasn't about to do that.

MythTV is good, but it has some quirks.   The backend and its database are a fragile little flowers. I have automated updates turned off on it, and I image the entire drive every time I go to do updates just in case the updates break something.  I also have an automated script that runs a backup of the database on regular intervals.

I haven't had any tuner problems with it.   I've used it with both a Ceton 6 tuner external Ethernet model (which I got rid of because it wouldn't stop overheating and crashing) and now, two HD Homerun Prime 3 tuner Ethernet tuners, which work quite well.

I'd argue that the biggest downside with MythTV is that it doesn't support DRM, so any channel flagged as "Copy Once" is unwatchable. Only channels flagged "Copy freely" work.  This used to not be much of a problem, as only HBO marked their channels "Copy Once" in my area, but maybe 6 months ago all Fox channels also switched to "Copy Once" and this instantly I can't watch them anymore.  Not much of a loss for me, but the Fiance really liked the National geographic channel :(   I live in constant fear that it's going to all come crashing down with more and more channels adding "copy once" flags.

It's really dumb too, because it does nothing but hurt legitimate paying customers like myself.  The pirates still somehow succeed in easily breaking the DRM and putting the content on torrent sites within hours of it airing.  I'm assuming it has something to do with the 1998 DMCA law, that makes it a crime to break content encryption.  I guess their motivation is that the ability to criminally charge pirates if they catch them is of greater value than keeping the customers who use Free and Open Source TV watching solutions.   It's a shame.

Unfortunatly WMC has been the only software solution that supports "Copy Once" DRM, once it drops, the only remaining options will be to buy closed hardware like TiVO or use the cable companies boxes, the same thing the FCC regulation that created Cable Cards was intended to avoid in the first place.  I'm hoping the FCC plans on revisiting this at some point.


> **TheFu said:**
> 
Am I the only person doing a bi-annual "data center consolidation?" VM sprawl is a real thing here.  

What do you mean by datacenter consolidation?  Removing and combining guests?  Personally I am a sprawl increaser :p  One of the benefits of virtualization to me has been being able to isolate programs from eachother.  I know that many of the servers I have running in dedicated guests could be running in the same Linux install, but this way I get isolation between them and never have to worry about dependency collisions, and have to worry just a little bit less about security.

> **TheFu said:**
> 
Switched to using chromebooks running Linux as my laptops. 8+ hrs of battery, 1080p, and 3 lbs is addictive.

I have never quite liked laptops.  I am and will always be a desktop guy.  Full size IBM Model M clicky keyboard, full size mouse, hughe high res screens, all at an ergonomically perfect desk, nothign else will do.  I do - however - agree that hacked chrome hardware running Linux is one of the best deals in the computer world.  One of my HTPC's is a hacked Asus Chromebox running Ubuntu 14.04 with Kodi. Dual core 1.4Ghz Haswell, 2GB of RAM and 16GB SSD all for under $200 is an amazing deal, and it only pulls 12W from the wall as measured by my Kill-A-Watt when playing HD content!  (it measures ~2w-5W at idle, almost not worth shutting it off!)  The only downside has been the fact that Kodi's MythTV plugin really does not like the Intel IGP.  :(


Anyway, I have wasted way too much work time trying this and will have to stay late to complete everything I have due today now.  I really appreciate your help and input to my questions above!

---

### Post by TheFu on 2016-03-25
Don't have time to respond to everything.
a) I consider passthru a hack. Not worth my time.  I did my time patching and rebuilding kernels in the early 1990s.
b) Raspberry Pi v2 for Kodi playback devices.  Plex MS on the G3258 for content serving/transcoding.  PlexBMC addon for Kodi.
c) Fired Comcast CATV years ago when they started encrypting basic channels. Dual HDHR3 tuners in the attic with the antennas. 70+ channels.
d) Ran ZFS on Solaris machines for years. Too afraid to use it on Linux.  Then there's the need for ECC and lots-o-RAM - both raised the price beyond what I was willing to spend.  RAID1, and daily, versioned, backups here.
e) 10G in the house? When it drops to $300 for the router/switch/2 NICs, then I'll consider it. Been on GigE since before it was cheap.
f) Ubiquiti stuff is usually good and cheap.  I've deployed it a few times.  Before they existed, one of my work projects was deploying wifi to 1200+ locations.  I don't use wifi at home, except for devices that have no other way to connect.  My chromebooks use a GigE-to-USB adapter. ;) Wifi sucks, in so many ways that I'm amazed it works at all.

I would never, ever, run a router inside a VM. Too many issues with VM security for my blood to risk that.

All I have time for today.

---

### Post by mattlach on 2016-03-25
> **TheFu said:**
> Don't have time to respond to everything.

I know what you mean, these are starting to get long!

> **TheFu said:**
> 
a) I consider passthru a hack. Not worth my time.  I did my time patching and rebuilding kernels in the early 1990s.

I agree up to a point.   It is a bit of a hack, but when I have to choose between lack of consolidation and a hack it becomes more difficult.   if I didn't have passthrough on my server, I'd have to run most of the biggest guests bare metal, which would both reduce my server needs, and increase my budget elsewhere.  I like doing as much as possible in one box!

> **TheFu said:**
> 
b) Raspberry Pi v2 for Kodi playback devices.  Plex MS on the G3258 for content serving/transcoding.  PlexBMC addon for Kodi.

Ahh,  I prefer just having my media shared on a simple NFS share, and having playback hardware that can handle anything thrown at it without the need for transcoding.   I like the concept of Raspberry pi's, cheap and simple, but I find ARM a little limiting as it is from the software / plugin availability standpoint, and wonder if the hardware really can handle some of the files I want to play.

> **TheFu said:**
> 
c) Fired Comcast CATV years ago when they started encrypting basic channels. Dual HDHR3 tuners in the attic with the antennas. 70+ channels.

Yeah, I'd do the same, if not for the Fiance.  She's into a lot of channels that I cant get OTA.   How may of those 70+ channels are different local affiliates of the same three letter broadcasters from different localities with the same content?  :p

> **TheFu said:**
> 
d) Ran ZFS on Solaris machines for years. Too afraid to use it on Linux.  Then there's the need for ECC and lots-o-RAM - both raised the price beyond what I was willing to spend.  RAID1, and daily, versioned, backups here.

Yeah, and that's why I'm always running up against RAM limitations.   Hardware RAID has some real flexibility limitations though.  I do realtime offsite backups using crashplan, but I worry that if I ever lost it all it would take months to download all my data again :p   I don't like the idea of having no redundancy during rebuild in case of a disk failure, which rules out RAID5.   Use RAID1 mirroring for smaller things where the space efficiency cost is less harsh, but RAID6 is really what I prefer.

> **TheFu said:**
> 
e) 10G in the house? When it drops to $300 for the router/switch/2 NICs, then I'll consider it. Been on GigE since before it was cheap.

Yeah, well, it's not switched.   I got a great deal on these BR-1020 adapters and the transducers and fiber was cheap from TheFiberStore so I ran a single dedicated storage line between my main workstation and my file server just to speed some file operations up a bit.    It's 10gig on a ghetto budget.

> **TheFu said:**
> 
f) Ubiquiti stuff is usually good and cheap.  I've deployed it a few times.  Before they existed, one of my work projects was deploying wifi to 1200+ locations.  I don't use wifi at home, except for devices that have no other way to connect.  My chromebooks use a GigE-to-USB adapter. ;) Wifi sucks, in so many ways that I'm amazed it works at all.

Yeah, I strongly prefer anything wired over Wifi.  More reliable, secure and faster with lower latencies, low overhead and full duplex.   I keep it around for phones, tablets and laptops though.   That being said, I just upgraded to a Unifi AC AP and at 5Ghz they are really starting to perform quite nicely.  Too bad 5ghz doesn't penetrate walls as well as 2.4Ghz.

> **TheFu said:**
> 
I would never, ever, run a router inside a VM. Too many issues with VM security for my blood to risk that.

I had that concern at first, but then I passed the WAN Ethernet adapter through to my pfSense guest.   I figured to any attempted breach it would look exactly the same as a physical host.   I would never expose a vswitch to the outside world though.

> **TheFu said:**
> 
All I have time for today.

Ditto!

---

### Post by TheFu on 2016-03-25
I don't like having all my eggs in 1 basket running alpha-quality code (like VGA passthru).  OTOH, I don't need 10 baskets either.  I have 2 baskets for VMs, 2 R-pis for media playback, a monster laptop that never leaves home anymore and a chromebook running Ubuntu Server + openbox that I use for almost everything and a router that faces the internet for my subnet there, plus a few internal only cheap routers and switches for networking here. Power use is less than 200W in my home office, ignoring the monitors.  R-pis are less than 2W each.  

Plex doesn't transcode anything for the Raspberry Pis here by default.  Low Res stuff is SW rendered and hidef is either h.264 which has HW support for decoding or mpeg2 (very rarely) which I will manually tell plex to transcode to h.264/aac.  Needed the plex transcoding for a Chromecast that someone gave me as an xmas present a few years ago.  That device is a complete waste without Plex to transcode.  It only plays 1 format and I don't have that in any of the media here.  h.264/aac.  It can't handle DTS, DD, DD+ in AC3 containers. Useless.  Plus it locks up my android devices when trying to use it on the road.

A travel overseas 6-8 weeks a year, so having a lite, cheap, laptop is mandatory.  Over time, I found even a 15in Dell to be a monster and slowly migrated to a 13inch chromebook with 1080p. It is a $400 ultrabook to me. Some things suck, but 3lbs and 1080p is amazing for that price.  I miss my $600 1440p Dell laptop from 2005-ish. Why did screen resolutions go the wrong way all these years?  Marketing. Crap.

Anyway, I can respect your decisions and had I remained employed longer, may have been willing to spend money.  Many of my peers do/did.

TV - there aren't any duplicate channels. Even the PBS channels are different, though 1 is from the big metro area and the other is the "state" PBS.  All the subchannels for OTA are different - some aren't on CATV at all. Guess the federal requirement only applies to the primary channel. Some of the 2nd-5th subchannels are great background noise when I work from home.

I haven't bought a video card in over a decade. Last one was an nvidia 430GT ... guess it is ina Core i5 (VM + storage server) here ... not connected to a monitor. ;)

Have a good weekend. Allergy season has hit here - the cars are covered in green pollen.  Pollen count today  here is: 3720 - they actually do pollen forecasting here.  Some of my friends will be locked indoors until the next rain to avoid ... er ... dying.  These are people who get the shots every fall and spring when pollen goes crazy here.  The rest of the year and for the lead in months they use OTC medicine.

---

### Post by grahammechanical on 2016-03-26
There are long posts in this thread. I have not read everything and that is because I do not understand most of it. But you mentioned Linux containers (LXC) and your regret that 16.04 is released after your window of opportunity for rebuilding the home server has closed. There are a couple of things that I think might be helpful to you.

1) This series of blog posts by one of main Canonical developers of LXD/LXC

[https://www.stgraber.org/2016/03/11/lxd-2-0-blog-post-series-012/](https://www.stgraber.org/2016/03/11/lxd-2-0-blog-post-series-012/)

2) This comment about installing LXD/LXC in the third blog

> All new releases of LXD get uploaded to the Ubuntu development  release within a few minutes of the upstream release. That package is  then used to seed all the other source of packages for Ubuntu users.


 If you are using the Ubuntu development release (16.04), you can simply do:

```
sudo apt install lxd
```

If you are running Ubuntu 14.04, we have backport packages available for you with:

 ```
sudo apt -t trusty-backports install lxd
```
[https://www.stgraber.org/2016/03/15/lxd-2-0-installing-and-configuring-lxd-212/](https://www.stgraber.org/2016/03/15/lxd-2-0-installing-and-configuring-lxd-212/)

It seems that LXD/LXC development work is done on the 16.04 development release (xenial xerus). And I can tell you from personal experience of running xenial that it is pretty stable. 

Based on my little experiments with LXC I can confirm that machines (like mine) that cannot run a VM will run Linux containers with hardly any negative effect on system resources.

Regards.

---

### Post by mattlach on 2016-04-05
> **TheFu said:**
> 
I wouldn't use proxmox for a number of reasons.

I'm starting to get closer to my migration window and need to make some final decisions pretty soon.

Is there any chance you can delve a little bit on this statement?   What are the reasons?  What would you suggest instead?  KVM running in an Ubuntu install?  I've heard horrible things about manually managing the KVM environment, which is why I was leaning towards Proxmox, but granted that was a long time ago. Maybe things have improved since then?

---

### Post by TheFu on 2016-04-05
You'll have to do your own research on proxmox.  It wasn't for us. 

There is a trade-off between more complete solutions and using lots of other tools with anything like this.  How would I automate VM creation?  Point-n-click gets old. What decisions did the proxmox team make "for most people" that don't apply to your situation?  Is there clustering robust enough? What about their storage solution?  What are the security issues?  LVM and backup control? Sometimes you don't want to do it their way for certain reasons.

Run proxmox for a month, see what you like and what you don't like.

I've never created a KVM VM manually. Always use a front-end to libvirt.  There are many options for that.  Last time I manually made a VM was with Xen around 2009-ish. [https://libvirt.org/apps.html](https://libvirt.org/apps.html)

I have manually tweaked settings in the libvirt XML, but that is rare after everything is up and working. virsh edit can be nice for a quick VM modification.

If you need large groups of people able to manage the VMs, look at something like oVirt.

I'm deploying a UniFi this weekend at a client. Planned to use the android app for setup, only a few nodes for a small space. Will that work?

---

### Post by mattlach on 2016-04-05
> **TheFu said:**
> You'll have to do your own research on proxmox.  It wasn't for us. 

There is a trade-off between more complete solutions and using lots of other tools with anything like this.  How would I automate VM creation?  Point-n-click gets old. What decisions did the proxmox team make "for most people" that don't apply to your situation?  Is there clustering robust enough? What about their storage solution?  What are the security issues?  LVM and backup control? Sometimes you don't want to do it their way for certain reasons.

Run proxmox for a month, see what you like and what you don't like.

I've never created a KVM VM manually. Always use a front-end to libvirt.  There are many options for that.  Last time I manually made a VM was with Xen around 2009-ish. [https://libvirt.org/apps.html](https://libvirt.org/apps.html)

I have manually tweaked settings in the libvirt XML, but that is rare after everything is up and working. virsh edit can be nice for a quick VM modification.

If you need large groups of people able to manage the VMs, look at something like oVirt.

Thank you for that information!

I have been reading published information about Proxmox for months now in preparation, but I always find I learn much more by trying to understanding other peoples likes and dislikes about a solution than I do by reading published information out there.   Some thigns you never learn until you actually sit downand start playing with the software.   I'm trying to minimize any surprises.

I'll be minimizing my risk by keeping a backup of my ESXi datastore and imaging my boot drive so I can always go back if I need to if I encounter somethign I just can't solve.

> **TheFu said:**
> 
I'm deploying a UniFi this weekend at a client. Planned to use the android app for setup, only a few nodes for a small space. Will that work?

Unfortunately I can't provide much input on the use of the android app.   The only way I've set these up is with either a local bare metal server, or a local virtual machine running the controller.

From the documentation, it might work well, but might also pose some problems.   You need to have at least firmware 3.4.4.3231 on the AP for the app to work with it.   Depending on how long the AP sat in inventory at the distributor you ordered it from, it may have a lower shipping firmware, in which case you either need to manually flash it via SSH or tftp which can be a pain, or first upgrade the AP using a working Unifi controller (without adopting it).

[This](https://community.ubnt.com/t5/UniFi-Wireless/APP-INFO-UniFi-EasySetup-Beta-with-support-for-all-UniFi-APs/td-p/1383396) is the only information I could find.

---

### Post by TheFu on 2016-04-05
Thanks for looking. Appears the unifi stuff is all for newer models.  This was for a small biz and they don't want to spend the extra money for better signaling - $60 was it.  Can't say that I blame them.  Only 2.4Ghz radio, so not one of the models listed in that link.  I'll test it here before taking it out ... hopefully the app works.

I treat android as a hostile environment, so I'm willing to load programs/tools on it that I wouldn't touch my real systems.  Won't even use Android for email - too many non-secure issues with the architecture.  Any device that lets the network override OS security settings is a bad thing in my book.  Don't really want AT&T/T-mobile/Verizon controlling the security of my devices, but I'm not willing to spend the $1K+ (heard about some a few yrs ago) for a model that is locked down to prevent their access.

Sounds like this thread is done. Good luck.

---

### Post by mattlach on 2016-04-05
> **TheFu said:**
> Thanks for looking. Appears the unifi stuff is all for newer models.  This was for a small biz and they don't want to spend the extra money for better signaling - $60 was it.  Can't say that I blame them.  Only 2.4Ghz radio, so not one of the models listed in that link.  I'll test it here before taking it out ... hopefully the app works.

I treat android as a hostile environment, so I'm willing to load programs/tools on it that I wouldn't touch my real systems.  Won't even use Android for email - too many non-secure issues with the architecture.  Any device that lets the network override OS security settings is a bad thing in my book.  Don't really want AT&T/T-mobile/Verizon controlling the security of my devices, but I'm not willing to spend the $1K+ (heard about some a few yrs ago) for a model that is locked down to prevent their access.

Sounds like this thread is done. Good luck.

Yeah, we are getting pretty far off the original topic.

Another thing you could try, is setting up a Unifi controller in a guest off-site, set up the AP, and then bring it in, and plug it in.

The business won't have the ability to change said/password/settings, but...

As far as Android goes, it has ita weaknesses.   I feel pretty comfortable eith it for what I do, but I use only Nexus devices which get more frequent security patches.   I'm also on Google's Fi network.   Google's data mining for advertising purposes is the evil I know, (and in the grand scheme of things isn't THAT evil) compared to the other carriers which are the evils I don't know.

---

### Post by mattlach on 2016-04-05
I hope this thread stays open though.

I might have follow up questions when I get around to doing the headless window manager install!  :p

---

### Post by mattlach on 2016-04-05
> **mattlach said:**
> Yeah, we are getting pretty far off the original topic.

Another thing you could try, is setting up a Unifi controller in a guest off-site, set up the AP, and then bring it in, and plug it in.

The business won't have the ability to change said/password/settings, but...

As far as Android goes, it has ita weaknesses.   I feel pretty comfortable eith it for what I do, but I use only Nexus devices which get more frequent security patches.   I'm also on Google's Fi network.   Google's data mining for advertising purposes is the evil I know, (and in the grand scheme of things isn't THAT evil) compared to the other carriers which are the evils I don't know.

Or better yet, just run a guest on your laptop, install the controller there, set it up,and then leave

---

### Post by naisanza on 2016-04-29
I've been searching for the past two weeks for running full Desktop GUI's inside a headless Ubuntu server as well

---

### Post by mattlach on 2016-04-29
> **naisanza said:**
> I've been searching for the past two weeks for running full Desktop GUI's inside a headless Ubuntu server as well

I meant to stop back in here and thank TheFu, but didn't get around to it until now :p

His solution (in post 2, most notably the link to the guide on how to install x2go) worked like a charm for me.

---

