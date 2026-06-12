---
title: "Multi-seat Steam Remote Play Server"
date: 2020-07-22
forum: Gaming &amp; Leisure
---

### Post by joedwards32 on 2020-07-22
My wife and I like to play games together. Before kids, we had two gaming PCs with their own desks etc, but there isn't room in the house for that kind of setup these days. I decided to setup a single, dedicated gaming server based on Ubuntu 18.04 which would use the Remote Play feature of Steam to stream games to our much lower spec Ubuntu laptops. This setup has some cool benefits:

[LIST]
[*]A single home server can stream games to our:
[LIST]
[*]Laptops
[*]Samsung smart TV with Steam Controller
[/LIST]

[*]We can play where ever we want in the house so long as WiFi signal is good. The Steam server is connected via Ethernet to a 1GbE PoE switch, which in turn links to 802.11ac wireless access points throughout the house (two downstairs, one upstairs). The smart TV is also connected via Ethernet to the switch.
[*]Low power, long battery life Laptops (i3, integrated graphics) can be used to play games
[*]We also use this server as a ZFS file server and Plex media streaming server
[/LIST]

There are some obvious downsides:
[LIST]
[*]While proton under steam is good, and ever improving, gaming under GNU/Linux is still often a pain to get working. Some games will never work.
[*]Detailed knowledge of Linux is required to get two instances of steam running on one host, using different GPUs, different IPs/Ports, etc.
[/LIST]

Notes on my setup below. I chose this approach over virtualising Windows under KVM with PCI passthrough because I don't want any MS crap in the house!
[B]
Hardware[/B]

CPU: AMD Ryzen 7 2700 Processor
MEM: Corsair 32GB Vengeance LPX DDR4 2400MHz RAM/Memory Kit 2 x 16GB
MOB: ASUS PRIME AMD Ryzen X470-PRO
GPU: 2 x Gigabyte GV-RXVEGA64GAMING OC-8GD Radeon RX Vega 64 8 GB Graphics Card
PSU: Corsair 1000 Watt RMx Fully Modular RM1000X ATX PSU/Power Supply
CHS: Corsair CC-9011077-WW Carbide Series 100R
SSD: Samsung 860 QVO 1TB 2.5&#8221; SATA
HDD: 3 x 3TB SATA
DSP: 2 x [HDMI dummy plug, Headless Ghost, Display Emulator]([https://www.amazon.co.uk/gp/product/B072PV6K8J/](https://www.amazon.co.uk/gp/product/B072PV6K8J/))

[B]Install
[/B]

[LIST]
[*]Install Ubuntu minimal 18.04
[*]Upgrade Kernel to at least 4.18 to get newer AMDGPU drivers than in the stock 4.15 kernel. Radeon RX Vega performance wasn't great on 4.15.
[/LIST]

[B]Networking
[/B]

[LIST]
[*]Install bridge utilities
[/LIST]
```
sudo apt-install bridge-utils net-tools
```


[LIST]
[*]Setup bridging, we'll need this later for network namespaces.
[/LIST]
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto br0
iface br0 inet static
        address 192.168.0.2
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 8.8.8.8
        bridge_ports enp6s0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

[B]Multi-Seat
[/B]

[LIST]
[*]Show current single seat configuration
[/LIST]
```
loginctl seat-status seat0
```

[LIST]
[*]Define a second seat, "seat1", and attach graphics and sound devices to it:
[/LIST]
```

sudo loginctl attach seat1 /sys/devices/pci0000:00/0000:00:03.2/0000:0b:00.0/0000:0c:00.0/0000:0d:00.0/drm/card1
sudo loginctl attach seat1 /sys/devices/pci0000:00/0000:00:03.2/0000:0b:00.0/0000:0c:00.0/0000:0d:00.1/sound/card1

```

[LIST]
[*]Reboot. Should have two independant seats now.
[*]Add two users for running steam, one per seat, and configure auto logon. Unfortunately gdm3 has no native support for this so we are going to use lightdm instead:
[/LIST]
```

sudo groupadd steam
sudo adduser steam-user1
sudo adduser steam-user2
sudo usermod -a -G steam,nopasswdlogin steam-user1
sudo usermod -a -G steam,nopasswdlogin steam-user2

sudo apt install lightdm

# switch default to lightdm when prompted

#e:/etc/lightdm/lightdm.conf.d/10-autologin.conf
[Seat:seat0]
autologin-user=steam-user1

[Seat:seat1]
autologin-user=steam-user2

```

[LIST]
[*]su as each user, disable screen lock and enable vino VNC server
[/LIST]
```

gconftool --set --type=bool /desktop/gnome/lockdown/disable_lock_screen true
gconftool --set --type=bool /desktop/gnome/remote_access/enabled true

```
[LIST]
[*]Reboot. Should auto login each session. You can verify with loginctl:
[/LIST]
```

loginctl

   SESSION        UID USER             SEAT             TTY             
        c1       1001 steam-user1      seat0            tty1            
        c2       1002 steam-user2      seat1            tty1            

```

**Namespaces**

_Network_

We want to run steam in each seat at the same time. Steam wants to bind to all network interfaces on specific ports to enable streaming, this means that normally you can't stream from two instances of steam on the same host. Network Namespaces can be used to limit steam to only specific network interfaces.


[LIST]
[*]This script will create a network namespace per seat
[/LIST]
```

#e:/usr/local/bin/network-namespace.sh
#!/bin/bash
# Create network namespaces
ip netns add steam-user1
ip netns add steam-user2

# Create veth interfaces
ip link add veth0a type veth peer name veth0b
ip link add veth1a type veth peer name veth1b

# Add veths to bridge to physical network
brctl addif br0 veth0a
brctl addif br0 veth1a

# Add veths to network namespaces
ip link set veth0b netns steam-user1
ip link set veth1b netns steam-user2

# Configure loopback
ip netns exec steam-user1 ip link set dev lo up
ip netns exec steam-user1 ip -4 addr add 127.0.0.1 dev lo
ip netns exec steam-user2 ip link set dev lo up
ip netns exec steam-user2 ip -4 addr add 127.0.0.1 dev lo

# Configure IPs
ip netns exec steam-user1 ifconfig veth0b 192.168.0.4/24 up
ip netns exec steam-user2 ifconfig veth1b 192.168.0.5/24 up

# Configure routing
ip netns exec steam-user1 route add default gw 192.168.0.1
ip netns exec steam-user2 route add default gw 192.168.0.1

# Up bridge interfaces
ifconfig veth0a up
ifconfig veth1a up

```
[LIST]
[*]Make it executable
[/LIST]
```

chmod 744 /usr/local/bin/network-namespace.sh

```

[LIST]
[*]Create a systemd unit file
[/LIST]
```

#e:/etc/systemd/system/network-namespace.service
[Unit]
After=network.target

[Service]
ExecStart=/usr/local/bin/network-namespace.sh

[Install]
WantedBy=multiuser.target

```
[LIST]
[*]Enable service
[/LIST]
```

chmod 664 /etc/systemd/system/network-namespace.service
systemctl daemon-reload
systemctl enable network-namespace.service
reboot

```

[LIST]
[*]Allow users to execute commands within the established network namespaces
[/LIST]
```

#e:/etc/sudoers.d/steam
%steam ALL=(ALL) NOPASSWD: /bin/ip netns exec steam-user1 su steam-user1 *
%steam ALL=(ALL) NOPASSWD: /bin/ip netns exec steam-user2 su steam-user2 *

```

_Filesystem_

Steam also puts lock files, etc, into /tmp/. This can prevent multiple Steam processes from launching the same game at the same time, despite running under different steam and linux accounts.

To remedy this, we can use polyinstantiation to provide dedicated /tmp/ directories to each of our seats.


[LIST]
[*]Configure namespace for /tmp/, only for the users steam-user1, steam-user2 - indicated by "~" at the start of the user definition
[/LIST]
```

#e:/etc/security/namespace.conf
/tmp    /tmp-inst/              user    ~steam-user1,steam-user2

```
[LIST]
[*]Make the /tmp-inst/ directory
[/LIST]
```

mkdir /tmp-inst/
chmod 000 /tmp-inst/

```
[LIST]
[*]Configure PAM to polyinstantiate, addthe following line
[/LIST]
```

#e:/etc/pam.d/common-session
session         required        pam_namespace.so unmnt_remnt

```
[LIST]
[*]Reboot to apply these changes
[/LIST]

**Steam**

[LIST]
[*]Install steam
[*]Inside each seat run
[/LIST]
```

sudo ip netns exec $USER su $USER -c -- /usr/games/steam

```
[LIST]
[*]Pop the above in a script and set that script to launch automatically when you log in
[/LIST]

**GPU overheating**

In some games, particularly on hot days, the GPUs shutdown after reaching their thermal threshold. Tweak GPU fans to run full throttle as soon as temperature rises. Don't care about noise.

```

sudo apt-get -y install python3-pip
pip3 install amdgpu-fan

```

```

#e:/etc/amdgpu-fan.yml
# -[temp(*C), speed(0-100%)]
speed_matrix:
- [0, 0]
- [25, 25]
- [30, 55]
- [35, 55]
- [40, 100]

cards:
 - card0
 - card1

```

```

#e:/etc/systemd/system/amdgpu-fan.service
[Unit]
Description=amdgpu fan controller

[Service]
ExecStart=/usr/local/bin/amdgpu-fan
Restart=always

[Install]
WantedBy=default.target

```

```

systemctl daemon-reload
systemctl enable amdgpu-fan
systemctl start amdgpu-fan

```

---

### Post by TheFu on 2020-07-22
I didn't see any question.  Perhaps this was a How-To guide and belongs in that sub-forum?

---

### Post by joedwards32 on 2020-07-22
Yep! Intended as a guide.

---

