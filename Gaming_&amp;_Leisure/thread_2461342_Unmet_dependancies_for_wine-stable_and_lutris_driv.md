---
title: "Unmet dependancies for wine-stable and lutris drivers"
date: 2021-04-28
forum: Gaming &amp; Leisure
---

### Post by gordan-vrbanec-vepar on 2021-04-28
No idea what's happening, every part of this i try to install has unmet dependancies... 

When trying to install wine this happens:

I did all the steps from [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu).

When i get to the sudo apt install --install-recommends winehq-stable part i get this:

```
veprovina@Veprovina:~$ sudo apt install --install-recommends winehq-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-stable : Depends: wine-stable (= 6.0.0~focal-1)
E: Unable to correct problems, you have held broken packages.


```

I then try wine --version. Tells me this:

```
veprovina@Veprovina:~$ wine --version
it looks like wine32 is missing, you should install it.
as root, please execute "apt-get install wine32"
wine-5.0 (Ubuntu 5.0-3ubuntu1)


```

I try sudo apt-get install wine32 and i get this:

```
veprovina@Veprovina:~$ sudo apt-get install wine32
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine32:i386 : Depends: libc6:i386 (>= 2.28) but it is not going to be installed
               Depends: libwine:i386 (= 5.0-3ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Furthermore, when doing the steps from [https://github.com/lutris/docs/blob/master/InstallingDrivers.md](https://github.com/lutris/docs/blob/master/InstallingDrivers.md) to install drivers for luris:

```
veprovina@Veprovina:~$ sudo apt install libgl1-mesa-dri:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-dri:i386 : Depends: libc6:i386 (>= 2.29) but it is not going to be installed
                        Depends: libdrm-amdgpu1:i386 (>= 2.4.100) but it is not going to be installed
                        Depends: libdrm-intel1:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libdrm-nouveau2:i386 (>= 2.4.66) but it is not going to be installed
                        Depends: libdrm-radeon1:i386 (>= 2.4.31) but it is not going to be installed
                        Depends: libdrm2:i386 (>= 2.4.75) but it is not going to be installed
                        Depends: libelf1:i386 (>= 0.142) but it is not going to be installed
                        Depends: libexpat1:i386 (>= 2.0.1) but it is not going to be installed
                        Depends: libgcc-s1:i386 (>= 7) but it is not going to be installed
                        Depends: libglapi-mesa:i386 (= 21.0.3~kisak4~f) but it is not going to be installed
                        Depends: libllvm12:i386 (>= 1:9~svn298832-1~) but it is not going to be installed
                        Depends: libsensors5:i386 (>= 1:3.5.0) but it is not going to be installed
                        Depends: libstdc++6:i386 (>= 5.2) but it is not going to be installed
                        Depends: libvulkan1:i386 (>= 1.2.131.2) but it is not going to be installed
                        Depends: libzstd1:i386 (>= 1.3.2) but it is not going to be installed
                        Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

```
veprovina@Veprovina:~$ sudo apt install mesa-vulkan-drivers mesa-vulkan-drivers:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mesa-vulkan-drivers is already the newest version (21.0.3~kisak4~f).
mesa-vulkan-drivers set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mesa-vulkan-drivers:i386 : Depends: libvulkan1:i386 but it is not going to be installed
                            Depends: libc6:i386 (>= 2.29) but it is not going to be installed
                            Depends: libdrm-amdgpu1:i386 (>= 2.4.99) but it is not going to be installed
                            Depends: libdrm2:i386 (>= 2.4.89) but it is not going to be installed
                            Depends: libelf1:i386 (>= 0.142) but it is not going to be installed
                            Depends: libexpat1:i386 (>= 2.0.1) but it is not going to be installed
                            Depends: libgcc-s1:i386 (>= 7) but it is not going to be installed
                            Depends: libllvm12:i386 (>= 1:9~svn298832-1~) but it is not going to be installed
                            Depends: libstdc++6:i386 (>= 5.2) but it is not going to be installed
                            Depends: libwayland-client0:i386 (>= 1.18.0) but it is not going to be installed
                            Depends: libxcb-dri3-0:i386 (>= 1.13) but it is not going to be installed
                            Depends: libxcb-present0:i386 but it is not going to be installed
                            Depends: libxcb-randr0:i386 (>= 1.13) but it is not going to be installed
                            Depends: libxcb-sync1:i386 but it is not going to be installed
                            Depends: libxcb1:i386 (>= 1.9.2) but it is not going to be installed
                            Depends: libxshmfence1:i386 but it is not going to be installed
                            Depends: libzstd1:i386 (>= 1.3.2) but it is not going to be installed
                            Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

The only thing i CAN do is add repositories... After that, nothing else works... 

What do i do?

Here's the repositories:

```
veprovina@Veprovina:~$ sudo apt-get update
Hit:1 http://hr.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://hr.archive.ubuntu.com/ubuntu focal-updates InRelease              
Hit:3 http://hr.archive.ubuntu.com/ubuntu focal-backports InRelease            
Hit:4 http://ppa.launchpad.net/kisak/kisak-mesa/ubuntu focal InRelease         
Hit:5 https://dl.winehq.org/wine-builds/ubuntu focal InRelease                 
Hit:6 http://archive.canonical.com/ubuntu focal InRelease           
Hit:7 http://security.ubuntu.com/ubuntu focal-security InRelease
Reading package lists... Done   

```

Using Ubuntu 20.04 LTS.

---

### Post by gordan-vrbanec-vepar on 2021-04-28
Ok... So i reinstalled linux (was a fresh install anyway so no big deal), from another ISO.
Then i changed the server to US.

And now it installed wine without problems. Apparently whoever is maintaining local repositories isn't doing a good job OR i had a corrupted install... 

I'll test this for vulkan as well and if it works, mark as solved.

---

### Post by gordan-vrbanec-vepar on 2021-04-28
I was able to install lutris after all. 

The issue seemed to be either the wrong download server for repositories (Local one didn't work, i had to switch to US), OR i had a corrupted install due to corrupted ISO file. 
So, whoever is searching the forums and has this issue, try switching to a US server for downloads in software and updates, or if that doesn't work, reinstall linux.

Marked as solved!

---

