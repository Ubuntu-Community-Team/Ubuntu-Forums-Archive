---
title: "/boot full but can't update due to broken package 20.04"
date: 2021-01-26
forum: Desktop Environments
---

### Post by Deanobats on 2021-01-26
Hey all,
I'm going round in circles here. I can't update linux-image-5.4.0-64-generic from the Updates GUI. I don't get a helpful message, only 'cannot copy extracted data'.  It turns out that /boot is close to being full. In previous updates when I ran into this I usually just: 

apt-get autoremove --purge to get rid of old kernels. However, this time around I get:

$ Unmet dependencies. Try 'apt --fix-broken install'

I do this, but as boot is full it fails as 'no space left on device'.

Any suggestions of a way forward?

Ta!

---

### Post by ActionParsnip on 2021-01-26
What is the output of:
```

uname -a; lsb_release -a; dpkg -l | grep linux-image

```

autoremove doesn't remove old kernels. It removes packages that have been orphaned during uninstalls. If the kernels are still on your system it won't uninstall them for you. That's not what that command does. Please read the apt man pages for more details.

---

### Post by Deanobats on 2021-01-26
I was going by [https://askubuntu.com/questions/1253347/how-to-easily-remove-old-kernels-in-ubuntu-20-04-lts](https://askubuntu.com/questions/1253347/how-to-easily-remove-old-kernels-in-ubuntu-20-04-lts) but now I notice there are some comments about autoremove not working.

Output is (and there are a lot of old kernels!)

[FONT=monospace][COLOR=#000000]$ uname -a; lsb_release -a; dpkg -l | grep linux-image [/COLOR]
Linux fiftyacre-ThinkPad-X230 5.4.0-62-generic #70-Ubuntu SMP Tue Jan 12 12:45:47 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux 
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 20.04.1 LTS 
Release:        20.04 
Codename:       focal 
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-101-generic                4.15.0-101.102                              amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-106-generic                4.15.0-106.107                              amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-108-generic                4.15.0-108.109                              amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-109-generic                4.15.0-109.110                              amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-111-generic                4.15.0-111.112                              amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-112-generic                4.15.0-112.113                              amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-115-generic                4.15.0-115.116                              amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-117-generic                4.15.0-117.118                              amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-118-generic                4.15.0-118.119                              amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-121-generic                4.15.0-121.123                              amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-20-generic                 4.15.0-20.21                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-22-generic                 4.15.0-22.24                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-23-generic                 4.15.0-23.25                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-24-generic                 4.15.0-24.26                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-29-generic                 4.15.0-29.31                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-30-generic                 4.15.0-30.32                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-33-generic                 4.15.0-33.36                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-34-generic                 4.15.0-34.37                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-36-generic                 4.15.0-36.39                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-38-generic                 4.15.0-38.41                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-39-generic                 4.15.0-39.42                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-42-generic                 4.15.0-42.45                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-43-generic                 4.15.0-43.46                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-44-generic                 4.15.0-44.47                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-45-generic                 4.15.0-45.48                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-46-generic                 4.15.0-46.49                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-47-generic                 4.15.0-47.50                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-48-generic                 4.15.0-48.51                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-50-generic                 4.15.0-50.54                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-51-generic                 4.15.0-51.55                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-52-generic                 4.15.0-52.56                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-54-generic                 4.15.0-54.58                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-55-generic                 4.15.0-55.60                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-58-generic                 4.15.0-58.64                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-60-generic                 4.15.0-60.67                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-62-generic                 4.15.0-62.69                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-64-generic                 4.15.0-64.73                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-65-generic                 4.15.0-65.74                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-66-generic                 4.15.0-66.75                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-69-generic                 4.15.0-69.78                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-70-generic                 4.15.0-70.79                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-72-generic                 4.15.0-72.81                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-74-generic                 4.15.0-74.84                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-76-generic                 4.15.0-76.86                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-88-generic                 4.15.0-88.88                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-91-generic                 4.15.0-91.92                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-96-generic                 4.15.0-96.97                                amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-4.15.0-99-generic                 4.15.0-99.100                               amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-51-generic                  5.4.0-51.56                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-52-generic                  5.4.0-52.57                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-53-generic                  5.4.0-53.59                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-54-generic                  5.4.0-54.60                                 amd64        Signed kernel image generic [/COLOR]
rc  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-56-generic                  5.4.0-56.62                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-58-generic                  5.4.0-58.64                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-59-generic                  5.4.0-59.65                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-60-generic                  5.4.0-60.67                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-62-generic                  5.4.0-62.70                                 amd64        Signed kernel image generic [/COLOR]
iU  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-generic                           5.4.0.64.67                                 amd64        Generic Linux kernel image

Would apt-get --purge and then the kernel number work?
[/COLOR]
[/FONT]

---

### Post by ActionParsnip on 2021-01-26
OK, we can clean this up with:
```

sudo dpkg -P `dpkg -l grep linux-image | grep ^rc | awk {'print $2'}`

```
Does that clear up /boot some? if not then run:
```

sudo apt-get --purge remove linux-image-5.4.0-52-generic linux-image-5.4.0-53-generic  linux-image-5.4.0-54-generic linux-image-5.4.0-58-generic linux-image-5.4.0-59-generic
sudo apt-get --purge autoremove
sudo apt-get clean

```

---

### Post by Deanobats on 2021-01-26
[FONT=monospace]Thanks for your help.

The first option generates:

[FONT=monospace][COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#ff5454]**error:**[/COLOR][COLOR=#000000] --purge needs at least one package name argument

And the second option generates:

[FONT=monospace][COLOR=#000000]sudo apt-get --purge remove linux-image-5.4.0-52-generic linux-image-5.4.0-53-generic  linux-image-5.4.0-54-generic linux-image-5.4.0-58-generic linux-ima[/COLOR]
ge-5.4.0-59-generic 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
You might want to run 'apt --fix-broken install' to correct these. 
The following packages have unmet dependencies. 
 linux-image-generic : Depends: linux-image-5.4.0-64-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-52-generic : Depends: linux-image-5.4.0-52-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-52-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-53-generic : Depends: linux-image-5.4.0-53-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-53-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-54-generic : Depends: linux-image-5.4.0-54-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-54-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-58-generic : Depends: linux-image-5.4.0-58-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-58-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-59-generic : Depends: linux-image-5.4.0-59-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-59-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-64-generic : Depends: linux-image-5.4.0-64-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-64-generic but it is not going to be installed 
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
[/FONT][/COLOR]


[/FONT] [/FONT]

---

### Post by ActionParsnip on 2021-01-26
Sorry, typo
```

sudo dpkg -P `dpkg -l | grep linux-image | grep ^rc | awk {'print $2'}`

```

also please give the output of:
```

sudo apt --fix-broken install

```

---

### Post by Deanobats on 2021-01-26
well that sure cleaned up a lot of kernels!

Now [FONT=monospace][COLOR=#000000]$ uname -a; lsb_release -a; dpkg -l | grep linux-image gives:

[FONT=monospace][COLOR=#000000]No LSB modules are available. [/COLOR]
Distributor ID: Ubuntu 
Description:    Ubuntu 20.04.1 LTS 
Release:        20.04 
Codename:       focal 
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-52-generic                  5.4.0-52.57                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-53-generic                  5.4.0-53.59                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-54-generic                  5.4.0-54.60                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-58-generic                  5.4.0-58.64                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-59-generic                  5.4.0-59.65                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-60-generic                  5.4.0-60.67                                 amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.4.0-62-generic                  5.4.0-62.70                                 amd64        Signed kernel image generic [/COLOR]
iU  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-generic                           5.4.0.64.67                                 amd64        Generic Linux kernel image[/COLOR]

and [/FONT]
[/COLOR][/FONT]sudo apt --fix-broken install

gives:

[FONT=monospace][FONT=monospace][COLOR=#000000]Reading package lists... Done
[/COLOR]
Building dependency tree        
Reading state information... Done

Correcting dependencies... Done

The following packages were automatically installed and are no longer required:

  adobe-flash-properties-gtk diffstat libcommon-sense-perl libevent-core-2.1-6 libgeos-3.6.2 libjson-xs-perl libllvm10 libtypes-serialiser-perl python-pypdf2 python3-defer python3-scour

  scour

Use 'sudo apt autoremove' to remove them.

The following additional packages will be installed:

  linux-image-5.4.0-64-generic linux-modules-5.4.0-64-generic

Suggested packages:

  fdutils linux-doc | linux-source-5.4.0 linux-tools

The following NEW packages will be installed

  linux-image-5.4.0-64-generic linux-modules-5.4.0-64-generic

0 to upgrade, 2 to newly install, 0 to remove and 0 not to upgrade.

39 not fully installed or removed.

Need to get 0 B/23.4 MB of archives.

After this operation, 85.1 MB of additional disk space will be used.

Do you want to continue? [Y/n] Y

(Reading database ... 506124 files and directories currently installed.)

Preparing to unpack .../linux-modules-5.4.0-64-generic_5.4.0-64.72_amd64.deb ...

Unpacking linux-modules-5.4.0-64-generic (5.4.0-64.72) ...

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing archive /var/cache/apt/archives/linux-modules-5.4.0-64-generic_5.4.0-64.72_amd64.deb (--unpack):
[/COLOR]
 cannot copy extracted data for './boot/System.map-5.4.0-64-generic' to '/boot/System.map-5.4.0-64-generic.dpkg-new': failed to write (No space left on device)

No apport report written because the error message indicates a disk full error

                                                                              [COLOR=#000000]**dpkg-deb:**[/COLOR][COLOR=#ff5454]**error:**[/COLOR][COLOR=#000000] paste subprocess was killed by signal (Broken pipe)
[/COLOR]
Preparing to unpack .../linux-image-5.4.0-64-generic_5.4.0-64.72_amd64.deb ...

Unpacking linux-image-5.4.0-64-generic (5.4.0-64.72) ...

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing archive /var/cache/apt/archives/linux-image-5.4.0-64-generic_5.4.0-64.72_amd64.deb (--unpack):
[/COLOR]
 cannot copy extracted data for './boot/vmlinuz-5.4.0-64-generic' to '/boot/vmlinuz-5.4.0-64-generic.dpkg-new': failed to write (No space left on device)

No apport report written because the error message indicates a disk full error

                                                                              [COLOR=#000000]**dpkg-deb:**[/COLOR][COLOR=#ff5454]**error:**[/COLOR][COLOR=#000000] paste subprocess was killed by signal (Broken pipe)
[/COLOR]
Errors were encountered while processing:

 /var/cache/apt/archives/linux-modules-5.4.0-64-generic_5.4.0-64.72_amd64.deb

 /var/cache/apt/archives/linux-image-5.4.0-64-generic_5.4.0-64.72_amd64.deb

[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]



I'm still getting a disk full error on /boot

If I

[FONT=monospace][COLOR=#000000]df -h[/COLOR]

I get 
  [FONT=monospace][COLOR=#000000]/dev/sda1                     704M  688M     0 100% /boot[/COLOR]

So despite the purge of kernels, /boot still reports as full (even after reboot). Odd!
[/FONT]


[/FONT][/FONT][/FONT]

---

### Post by ActionParsnip on 2021-01-26
OK, we can kill more kernels with:
```

sudo apt-get --purge remove linux-image-5.4.0-52-generic linux-image-5.4.0-53-generic linux-image-5.4.0-54-generic linux-image-5.4.0-58-generic linux-image-5.4.0-59-generic
sudo apt-get --purge autoremove
sudo apt-get clean

```

If you run:
```

df -h | grep boot

```
Is there space free now?

---

### Post by Deanobats on 2021-01-26
Thanks for your continued help - much appreciated! This is where it gets infuriating....

[FONT=monospace][COLOR=#000000]sudo apt-get --purge remove linux-image-5.4.0-52-generic linux-image-5.4.0-53-generic linux-image-5.4.0-54-generic linux-image-5.4.0-58-generic linux-imag[/COLOR]
e-5.4.0-59-generic 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
You might want to run 'apt --fix-broken install' to correct these. 
The following packages have unmet dependencies. 
 linux-image-generic : Depends: linux-image-5.4.0-64-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-52-generic : Depends: linux-image-5.4.0-52-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-52-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-53-generic : Depends: linux-image-5.4.0-53-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-53-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-54-generic : Depends: linux-image-5.4.0-54-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-54-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-58-generic : Depends: linux-image-5.4.0-58-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-58-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-59-generic : Depends: linux-image-5.4.0-59-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-59-generic but it is not going to be installed 
 linux-modules-extra-5.4.0-64-generic : Depends: linux-image-5.4.0-64-generic but it is not going to be installed or 
                                                 linux-image-unsigned-5.4.0-64-generic but it is not going to be installed 
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

I'm back to the unmet dependencies when I try to purge!
[/FONT]

---

### Post by SeijiSensei on 2021-01-26
Try running "sudo apt --fix-broken install" again.

---

### Post by ajgreeny on 2021-01-26
So far nobody has asked why you have a separate /boot partition which is generally totally unnecessary unless you are using an encrypted system or LVM partitioning.

That aside, you may find it easiest to use synaptic to remove some of the older kernels; it makes like a lot simpler when searching for all the packages associated with the kernel itself as you can search using just the version number, eg, 5.4.0-52 in the search box and then show all that's installed of that version by clicking on the first small column of the right hand pane (with an S in the header), to bring all those installed to the top of the list, as shown in my screenshot. 
It is then a few clicks to completely remove all of them.
Note that my image is for a kernel version you are running at present so use only your own list of versions that you want removed.

Try doing the same for all the old kernels you want to remove then you should be fine and able to add the 5.4.0-64 kernel that so far has not had space to be installed.

In spite of what is said in post #2, ***sudo apt autoremove*** does often solve this problem and remove all but the last two kernel versions, and has done so now for a few years.  However apt needs a lot of headroom to perform and with /boot too full that headroom was not available, hence your difficulty.

I suggest in future that whenever a new kernel is available you install it and then immediately run ***sudo apt autoremove*** to make sure all older unwanted versions are removed.

---

### Post by Deanobats on 2021-01-26
Thanks for your help everyone, I got there eventually. I ended up with a bit of a hybrid approach. I used part of the solution posted here:

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

It was because /boot was full. So what I did was:

```
[FONT=monospace][COLOR=#000000]sudo dpkg --purge linux-image-5.4.0-52-generic linux-image-extra-5.4.0-52-generic[/COLOR]


[/FONT]
```

That got rid of the oldest kernel, then:

```
[FONT=monospace][COLOR=#000000]sudo apt-get --purge remove linux-image-5.4.0-52-generic linux-image-5.4.0-53-generic linux-image-5.4.0-54-generic linux-image-5.4.0-58-generic linux-imag[/COLOR]e-5.4.0-59-generic


[/FONT]
```

Which worked without the dependency problem for some reason. Now /boot is half full and I'm on the latest kernel.

Thanks for your suggestions.

---

### Post by ajgreeny on 2021-01-26
So now is a very good time to run command ```
sudo apt autoremove --purge
``` which will get rid of all the other related packages that are no longer needed, eg, the ***linux-header, linux-modules*** and ***linux-tools*** packages that you may have had installed.
They may have automatically been removed when you uninstalled the kernels but it's worth running that command every so often anyway.

---

### Post by grahammechanical on 2021-01-26
For information purposes: Software Updater installs kernels and marks them so that they can be removed by the autoremove command. In fact software Updater will automatically remove older kernels as it installs a newer kernel.

Even when we use the terminal we get information about packages and kernels that are no longer required along with advice to run apt autoremove to get rid of them. Manually installed kernels do not get removed in the same way.

Regards

---

### Post by ActionParsnip on 2021-01-26
[https://askubuntu.com/questions/620266/how-does-apt-decide-how-many-old-kernels-to-keep](https://askubuntu.com/questions/620266/how-does-apt-decide-how-many-old-kernels-to-keep)

Explains how autoremove does and doesn't remove old kernels. I personally prefer to manually keep on top of this manually. I've made scripts to check there aren't lots of kernels on my systems too. Having a small /boot really doesn't do any favours and storage isn't a massive premium as in the early days of Linux.

---

### Post by Deanobats on 2021-01-27
I don't know if 
sudo apt autoremove --purge

will remove kernels that have been manually updated.

If I use
```

[FONT=monospace][COLOR=#000000]apt-mark showmanual 'linux-image-.*'[/COLOR][/FONT]
```[FONT=monospace]

I get

[FONT=monospace][COLOR=#000000]linux-image-5.4.0-60-generic

while with
```

[FONT=monospace][COLOR=#000000]apt-mark showauto 'linux-image-.*' [/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000] 

I get

[FONT=monospace][COLOR=#000000]linux-image-5.4.0-62-generic
[/COLOR]linux-image-5.4.0-64-generic
linux-image-generic

I don't know if autoremove will remove the manually updated kernels or not.


[/FONT][/COLOR][/FONT][/COLOR][/FONT][/FONT]

---

