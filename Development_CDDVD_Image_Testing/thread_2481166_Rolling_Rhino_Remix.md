---
title: "Rolling Rhino Remix"
date: 2022-11-20
forum: Development CD/DVD Image Testing
---

### Post by #&amp;thj^% on 2022-11-20
I'm curious how many seasoned Ubuntu users would be interested in a rolling Ubuntu release. I've been prodding in fun with a few folks for a while now and it seems like a good thing is happening.
> Rolling Rhino Remix is an unofficial Ubuntu flavour which converts the Ubuntu operating system into a rolling release Linux distribution by tracking the devel series.
A rolling release distribution is a Linux distribution which receives continuous package updates, and as such there are no major updates (unlike Ubuntu's current release model where there is clear progression between versions). A rolling release model offers new and experienced users a new way to utilise their desktop PC, without the hassle of major upgrades.
More here: [https://rollingrhino.org/](https://rollingrhino.org/)
I've been on it for a few short days now and It seems to be quite sane. (From a testers view)
New users will find it very confusing. Out of ten New to Linux and Ubuntu 8 of them threw in the towel. ;)
6 out 6 old timers found it useful.
I'm a Rolling advocate, and for the most part 95% of my systems run rolling models. So I'm partial.
TIP: I'll use a minimal install that takes care of un-loading Snaps and Snapd, unless you choose Gnome then you will get them back, or if you would prefer them add them yourself.
```
cat /etc/os-release
PRETTY_NAME="Rolling Rhino Remix"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04 (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy

```
Sources will change to:
```
 Active apt repos in: /etc/apt/sources.list
    1: deb http://us.archive.ubuntu.com/ubuntu/ devel main restricted
    2: deb http://us.archive.ubuntu.com/ubuntu/ devel-updates main restricted
    3: deb http://us.archive.ubuntu.com/ubuntu/ devel universe
    4: deb http://us.archive.ubuntu.com/ubuntu/ devel-updates universe
    5: deb http://us.archive.ubuntu.com/ubuntu/ devel multiverse
    6: deb http://us.archive.ubuntu.com/ubuntu/ devel-updates multiverse
    7: deb http://us.archive.ubuntu.com/ubuntu/ devel-backports main restricted universe multiverse
    8: deb http://security.ubuntu.com/ubuntu devel-security main restricted
    9: deb http://security.ubuntu.com/ubuntu devel-security universe
    10: deb http://security.ubuntu.com/ubuntu devel-security multiverse
  Active apt repos in: /etc/apt/sources.list.d/eddie.website.list
    1: deb http://eddie.website/repository/apt stable main
  Active apt repos in: /etc/apt/sources.list.d/nordvpn.list
    1: deb https://repo.nordvpn.com/deb/nordvpn/debian stable main
  Active apt repos in: /etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-conkymanager2-jammy.list
    1: deb https://ppa.launchpadcontent.net/ubuntuhandbook1/conkymanager2/ubuntu/ jammy main


```[B]
AGAIN this a pre-release[/B] so I wouldn't use it as a production system
EDIT: I need to mention as of this date11/20/2022 ZFS option will break the installer

---

### Post by #&amp;thj^% on 2022-11-21
Ok I may have to come back and eat crow, but for now I'm truly impressed.
Explanation, I have revved this from jammy to lunar,
```
cat /etc/os-release
PRETTY_NAME="Ubuntu Lunar Lobster (development branch)"
NAME="Ubuntu"
VERSION_ID="23.04"
VERSION="23.04 (Lunar Lobster)"
VERSION_CODENAME=lunar
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=lunar
LOGO=ubuntu-logo

```
 all important applications are solid, I've even installed yet another package-manager>> Pacstall is an AUR-like package manager for Ubuntu and Ubuntu-based systems, and we have worked closely with the Pacstall developers to integrate it into our distribution. Pacstall brings the experience of the Arch User Repository directly to Ubuntu and Ubuntu-based systems with an ever-growing number of user-maintained packages. still ticking right along. [https://pacstall.dev/packages?page=0&size=25&sortBy=default&sort=asc&filter=&filterBy=name](https://pacstall.dev/packages?page=0&size=25&sortBy=default&sort=asc&filter=&filterBy=name)
> How does it work then?

Pacstall takes in files known as pacscripts (similar to PKGBUILDs) that contain the necessary contents to build packages, and builds them into executables on your system.

Why is this any different than any other package manager?

Pacstall uses the stable base of Ubuntu but allows you to use bleeding edge software with little to no compromises, so you don't have to worry about security patches or new features.
```
 pacstall -L
firefox-deb

```

```
apt policy firefox
firefox:
  Installed: 105.0+build2-0ubuntu0.20.04.1
  Candidate: 1:1snap1-0ubuntu3
  Version table:
     1:1snap1-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu devel/main amd64 Packages
 *** 105.0+build2-0ubuntu0.20.04.1 100
        100 /var/lib/dpkg/status

```
```
pacstall -H
Usage: pacstall [-h] [-V] {-I,-S,-R,-D,-A,-U,-L,-Up,-Qi,-T} [-P] [-K] [-B]

An AUR inspired package manager for Ubuntu.

Commands:
	-I, --install <package>
		Install a package.
	-S, --search <package>
		Search for a package.
	-R, --remove <package>
		Remove a package.
	-D, --download <package>
		Download a pacscript.
	-A, --add-repo <repo>
		Add a repository.
	-U, --update [user] [branch]
		Update Pacstall.
	-L, --list
		List all installed packages.
	-Up, --upgrade
		Upgrade all installed packages.
	-Qi, --query-info <package>
		Query information about a package.
	-T, --tree <package>
		Display a tree graph of a package.

Options:
	-P, --disable-prompts
		Disable prompts.
	-K, --keep
		Keep the build files.
	-B, --build-only
		Build the deb but do not install.
	-V, --version
		Display the version number.
	-h, --help
		Display this help message.

Helpful links:
	https://github.com/pacstall/pacstall
		Official Pacstall GitHub page.
	https://github.com/pacstall/pacstall-programs/issues
		If you find a broken package, create an issue here.
	https://github.com/pacstall/pacstall/releases/latest
		Link to the latest release of Pacstall.

```
Note:It will not Version upgrade without user intervention, so you can stay with jammy until it upgrade's to lunar naturally.
Current summary: I'm liking this and hope it gains enough people to keep it going.
I also find everything straight forward.
**My only down side to this is the "ZFS" option on install still breaks the installer. I've submitted various reports and logs to triage this. **

---

### Post by #&amp;thj^% on 2022-11-23
I think this will be a keeper, I just can't seem to break it.
I'm putting this to the acid test, upgrading to Lunar after a couple of days testing and then back to Jammy.
```
cat /etc/os-release
PRETTY_NAME="Rolling Rhino Remix"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04 (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy


```
Specs (short):
```
 inxi -SzGz -j
System:
  Kernel: 6.0.8-060008-generic arch: x86_64 bits: 64 Desktop: Xfce v: 4.17.1
    Distro: Ubuntu 22.04 (Jammy Jellyfish)
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 515.65.01
  Device-2: AMD Renoir driver: amdgpu v: kernel
  Device-3: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: amdgpu,nvidia
    unloaded: fbdev,modesetting,nouveau,vesa dri: radeonsi
    gpu: amdgpu,nvidia,nvidia-nvswitch resolution: 1: N/A 2: 1920x1080~120Hz
  API: OpenGL v: 4.6 Mesa 22.2.1 renderer: RENOIR (renoir LLVM 15.0.2 DRM
    3.48 6.0.8-060008-generic)
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile

```

---

### Post by #&amp;thj^% on 2023-02-13
Updated from November 23rd, 2022
Today Mon Feb 13 01:42:50 PM MST 2023
Still rock solid**
[s]FTR, If your using zfs-root anything higher than kernel version " 5.19.0-21-generic " will break zfs mods[/s]
Kernel: 6.2.0-19-generic now works for all zfs-root, and encryption.
```
>> inxi -Fxzy
System:
  Kernel: 5.19.0-21-generic arch: x86_64 bits: 64 compiler: N/A Desktop: Xfce
    v: 4.18.1 Distro: Ubuntu 23.04 (Lunar Lobster)
Machine:
  Type: Laptop System: LENOVO product: 82B5 v: Lenovo Legion 5 15ARH05
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN
    serial: <superuser required> UEFI: LENOVO v: EUCN37WW date: 04/14/2022
Battery:
  ID-1: BAT0 charge: 57.1 Wh (100.0%) condition: 57.1/60.0 Wh (95.2%)
    volts: 17.2 min: 15.4 model: Celxpert L19C4PC0 status: full
  Device-1: hidpp_battery_0 model: Logitech Marathon Mouse/Performance Plus
    M705 charge: 55% (should be ignored) status: discharging
CPU:
  Info: 6-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: MT MCP arch: Zen 2 rev: 1 cache: L1: 384 KiB L2: 3 MiB L3: 8 MiB
  Speed (MHz): avg: 1432 high: 1639 min/max: 1400/3000 boost: enabled cores:
    1: 1400 2: 1400 3: 1400 4: 1396 5: 1400 6: 1400 7: 1397 8: 1400 9: 1639
    10: 1523 11: 1409 12: 1420 bogomips: 71869
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] vendor: Lenovo
    driver: nvidia v: 525.78.01 arch: Turing bus-ID: 01:00.0
  Device-2: Syntek Integrated Camera type: USB driver: uvcvideo bus-ID: 1-3:2
  Display: x11 server: X.Org v: 1.21.1.6 driver: X: loaded: nvidia
    gpu: nvidia,nvidia-nvswitch resolution: 1: 1920x1080~120Hz 2: N/A
  API: OpenGL v: 4.6.0 NVIDIA 525.78.01 renderer: NVIDIA GeForce GTX 1650
    Ti/PCIe/SSE2 direct render: Yes
Audio:
  Device-1: NVIDIA driver: snd_hda_intel v: kernel bus-ID: 4-1.2.1:5
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor vendor: Lenovo driver: N/A
    bus-ID: 06:00.5
  Device-3: AMD Family 17h/19h HD Audio vendor: Lenovo driver: snd_hda_intel
    v: kernel bus-ID: 06:00.6
  Device-4: DisplayLink UOEOS Laptop Dock type: USB
    driver: cdc_ncm,snd-usb-audio
  Sound API: ALSA v: k5.19.0-21-generic running: yes
  Sound Server-1: PulseAudio v: 16.1 running: no
  Sound Server-2: PipeWire v: 0.3.65 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Lenovo driver: r8169 v: kernel port: 1000 bus-ID: 03:00.0
  IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter>
  Device-2: Intel Wi-Fi 6 AX200 driver: iwlwifi v: kernel bus-ID: 04:00.0
  IF: wlp4s0 state: down mac: <filter>
  IF-ID-1: enx70b3d55c01b3 state: up speed: 1000 Mbps duplex: half
    mac: <filter>
  IF-ID-2: nordlynx state: unknown speed: N/A duplex: N/A mac: N/A
Bluetooth:
  Device-1: Intel AX200 Bluetooth type: USB driver: btusb v: 0.8 bus-ID: 3-3:5
  Report: hciconfig ID: hci0 rfk-id: 0 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
RAID:
  Device-1: bpool type: zfs status: ONLINE level: linear raw: size: 1.88 GiB
    free: 1.19 GiB zfs-fs: size: 1.75 GiB free: 1.07 GiB
  Components: Online: 1: nvme1n1p3
  Device-2: rpool type: zfs status: ONLINE level: linear raw: size: 232 GiB
    free: 172 GiB zfs-fs: size: 224.81 GiB free: 164.81 GiB
  Components: Online: 1: nvme1n1p4
Drives:
  Local Storage: total: raw: 9.56 TiB usable: 9.55 TiB used: 24.87 GiB (0.3%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVLB256HBHQ-000L2
    size: 238.47 GiB temp: 36.9 C
  ID-2: /dev/nvme1n1 vendor: Western Digital model: PC SN730
    SDBQNTY-256G-1001 size: 238.47 GiB temp: 32.9 C
  ID-3: /dev/sda type: USB vendor: Western Digital model: WD40NDZW-11BHVS1
    size: 3.64 TiB
  ID-4: /dev/sdb type: USB vendor: Western Digital model: WD Blue SN570 500GB
    size: 465.76 GiB
  ID-5: /dev/sdc type: USB vendor: Seagate model: ST500VT001-1K6142
    size: 465.76 GiB
  ID-6: /dev/sdf type: USB vendor: Western Digital model: WD50NDZW-11A8JS1
    size: 4.55 TiB
Partition:
  ID-1: / size: 171.08 GiB used: 6.27 GiB (3.7%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx
  ID-2: /boot size: 1.63 GiB used: 571.8 MiB (34.3%) fs: zfs
    logical: bpool/BOOT/ubuntu_eo0rsx
  ID-3: /boot/efi size: 511 MiB used: 12.2 MiB (2.4%) fs: vfat
    dev: /dev/nvme0n1p1
  ID-4: /var/log size: 164.93 GiB used: 120.2 MiB (0.1%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/var/log
Swap:
  ID-1: swap-1 type: partition size: 2 GiB used: 0 KiB (0.0%)
    dev: /dev/nvme1n1p2
Sensors:
  System Temperatures: cpu: 47.5 C mobo: N/A gpu: nvidia temp: 38 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 462 Uptime: 7m Memory: 7.63 GiB used: 3.43 GiB (45.0%)
  Init: systemd target: graphical (5) Compilers: gcc: 12.2.0 Packages: 2224
  Shell: Bash v: 5.2.15 inxi: 3.3.24

```
```
>> inxi -p
Partition:
  ID-1: / size: 171.07 GiB used: 6.27 GiB (3.7%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx
  ID-2: /boot size: 1.63 GiB used: 571.8 MiB (34.3%) fs: zfs
    logical: bpool/BOOT/ubuntu_eo0rsx
  ID-3: /boot/efi size: 511 MiB used: 12.2 MiB (2.4%) fs: vfat
    dev: /dev/nvme0n1p1
  ID-4: /home/me size: 180.55 GiB used: 15.74 GiB (8.7%) fs: zfs
    logical: rpool/USERDATA/me_glr5ju
  ID-5: /root size: 164.81 GiB used: 1.2 MiB (0.0%) fs: zfs
    logical: rpool/USERDATA/root_glr5ju
  ID-6: /srv size: 164.81 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/srv
  ID-7: /usr/local size: 164.81 GiB used: 256 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/usr/local
  ID-8: /var/games size: 164.81 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/var/games
  ID-9: /var/lib size: 166.85 GiB used: 2.05 GiB (1.2%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/var/lib
  ID-10: /var/lib/AccountsService size: 164.81 GiB used: 128 KiB (0.0%)
    fs: zfs logical: rpool/ROOT/ubuntu_eo0rsx/var/lib/AccountsService
  ID-11: /var/lib/NetworkManager size: 164.81 GiB used: 256 KiB (0.0%)
    fs: zfs logical: rpool/ROOT/ubuntu_eo0rsx/var/lib/NetworkManager
  ID-12: /var/lib/apt size: 164.89 GiB used: 85 MiB (0.1%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/var/lib/apt
  ID-13: /var/lib/dpkg size: 164.86 GiB used: 51.5 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/var/lib/dpkg
  ID-14: /var/log size: 164.92 GiB used: 120.2 MiB (0.1%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/var/log
  ID-15: /var/mail size: 164.81 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/var/mail
  ID-16: /var/snap size: 164.81 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/var/snap
  ID-17: /var/spool size: 164.81 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/var/spool
  ID-18: /var/www size: 164.81 GiB used: 128 KiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_eo0rsx/var/www
  ID-19: swap-1 size: 2 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/nvme1n1p2

```
```
>> inxi -r
Repos:
  Active apt repos in: /etc/apt/sources.list
    1: deb http://archive.ubuntu.com/ubuntu devel main restricted
    2: deb http://archive.ubuntu.com/ubuntu devel-updates main restricted
    3: deb http://archive.ubuntu.com/ubuntu devel universe
    4: deb http://archive.ubuntu.com/ubuntu devel-updates universe
    5: deb http://archive.ubuntu.com/ubuntu devel multiverse
    6: deb http://archive.ubuntu.com/ubuntu devel-updates multiverse
    7: deb http://archive.ubuntu.com/ubuntu devel-backports main restricted universe multiverse
    8: deb http://archive.ubuntu.com/ubuntu devel-security main restricted
    9: deb http://archive.ubuntu.com/ubuntu devel-security universe
    10: deb http://archive.ubuntu.com/ubuntu devel-security multiverse
  Active apt repos in: /etc/apt/sources.list.d/archive_uri-https_download_sublimetext_com_-lunar.list
    1: deb https://download.sublimetext.com/ apt/stable/
  Active apt repos in: /etc/apt/sources.list.d/cappelikan-ubuntu-ppa-lunar.list
    1: deb https://ppa.launchpadcontent.net/cappelikan/ppa/ubuntu/ lunar main
  Active apt repos in: /etc/apt/sources.list.d/eddie.website.list
    1: deb http://eddie.website/repository/apt stable main
  Active apt repos in: /etc/apt/sources.list.d/mozillateam-ubuntu-ppa-lunar.list
    1: deb https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu/ lunar main
  Active apt repos in: /etc/apt/sources.list.d/nordvpn.list
    1: deb https://repo.nordvpn.com//deb/nordvpn/debian stable main
  Active apt repos in: /etc/apt/sources.list.d/paelzer-ubuntu-lp-1968131-swtpm-rndfile-lunar.list
    1: deb https://ppa.launchpadcontent.net/paelzer/lp-1968131-swtpm-rndfile/ubuntu/ jammy main
  Active apt repos in: /etc/apt/sources.list.d/pipewire-debian-ubuntu-pipewire-upstream-lunar.list
    1: deb https://ppa.launchpadcontent.net/pipewire-debian/pipewire-upstream/ubuntu/ jammy main
  Active apt repos in: /etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-conkymanager2-lunar.list
    1: deb https://ppa.launchpadcontent.net/ubuntuhandbook1/conkymanager2/ubuntu/ jammy main

```
EDIT: **From Nov 20 2022 to 4-6-2023 Still rock solid**

---

