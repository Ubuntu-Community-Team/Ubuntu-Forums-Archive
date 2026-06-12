---
title: "After fresh install have a couple of error"
date: 2019-05-29
forum: Desktop Environments
---

### Post by xendistar2 on 2019-05-29
I have done a fresh install of Xubuntu 19.04 and have a couple of issue that I have not been able to resolve.

After the install I ran an update and I now have a package that will not install Linux-Firmware, it gives the following error

E: /var/cache/apt/archives/linux-firmware_1.178.1_all.deb: cannot copy extracted data for './lib/firmware/iwlwifi-7260-7.ucode' to '/lib/firmware/iwlwifi-7260-7.ucode.dpkg-new': unexpected end of file or stream.

Secondly, The time is wrong on my PC, it is one hour behind, I have tried manually changing the time, I have tried setting the time using hwclock on the cli, I have setup ntp and told xubuntu to use ntp to sync the time but my pc still sits 1 hour behind. My Time zone is Europe London

Thirdly, when I right click on a file to get the context menu, it has a scroll up and down option, is there an option to do away with this and have a fixed length menu please

If anybody can please advise the best way to resolve any of the above I would appreciate it.

Thanks in advance

---

### Post by #&amp;thj^% on 2019-05-29
Sounds like a rename problem:
"sudo dpkg -i --force-overwrite <filename>"
So I think this "should" work for your case:
```

sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-firmware_1.178.1_all.deb
```
We only do one question per thread>>>>but to set your time:
Use timedatectl

```
sudo timedatectl set-timezone <timeszone>
```

Examples:

    Timezone as EST

    ```
sudo timedatectl set-timezone EST
```

    Timezone as UTC

    ```
sudo timedatectl set-timezone UTC
```

    Listing all valid Timezones

    ```
timedatectl list-timezones
```

This command is perfect for automation scripts since it doesn't require any user interaction while compared to any given answer based on dpkg-reconfigure tzdata

---

### Post by xendistar2 on 2019-05-29
> **1fallen said:**
> Sounds like a rename problem:
"sudo dpkg -i --force-overwrite <filename>"
So I think this "should" work for your case:
```

sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-firmware_1.178.1_all.deb
```
We only do one question per thread>>>>but to set your time:
<snip>

When I tried I get the following:

```
mit@andora:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-firmware_1.178.1_all.deb(Reading database ... 196107 files and directories currently installed.)
Preparing to unpack .../linux-firmware_1.178.1_all.deb ...
Unpacking linux-firmware (1.178.1) over (1.178) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/linux-firmware_1.178.1_all.deb (--install):
 cannot copy extracted data for './lib/firmware/iwlwifi-7260-7.ucode' to '/lib/firmware/iwlwifi-7260-7.ucode.dpkg-new': unexpected end of file or stream

```

Thanks for the additional information, I will try it and reply with new threads if I have further issue

---

### Post by #&amp;thj^% on 2019-05-29
Well this is kind of a nukular approach>>>but try this, and post back the results if any.
**[COLOR="#FF0000"]**Warning**[/COLOR]** to have proper back-ups in place before proceeding.
```
sudo rm -rf /lib/firmware/iwlwifi-7260-7.ucode.dpkg-new
```

---

### Post by xendistar2 on 2019-05-29
OK the file is still listed in synaptics to be installed but at least now I can unselect it, just need to remember to make sure I do not select it in the future.

Would it be worth downloading the individual file from somewhere and installing it manually or just wait until the next version is released?

---

### Post by #&amp;thj^% on 2019-05-29
Well let it install this time, lets see what happens.

---

### Post by xendistar2 on 2019-05-30
> **1fallen said:**
> Well let it install this time, lets see what happens.

Got the same error

```
E: /var/cache/apt/archives/linux-firmware_1.178.1_all.deb: cannot copy extracted data for './lib/firmware/iwlwifi-7260-7.ucode' to '/lib/firmware/iwlwifi-7260-7.ucode.dpkg-new': unexpected end of file or stream
```

---

### Post by xendistar2 on 2019-05-31
Here a more detail of the failure to install

```


(Reading database ... 198211 files and directories currently installed.)
Preparing to unpack .../linux-firmware_1.178.1_all.deb ...
Unpacking linux-firmware (1.178.1) over (1.178) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/linux-firmware_1.178.1_all.deb (--unpack):
 cannot copy extracted data for './lib/firmware/iwlwifi-7260-7.ucode' to '/lib/firmware/iwlwifi-7260-7.ucode.dpkg-new': unexpected end of file or stream

```

---

### Post by #&amp;thj^% on 2019-05-31
Well we now know how to fix it.
As to your prior question>>"**Would it be worth downloading the individual file from somewhere and installing it manually?** "
It would end the same I'm afraid.:(>>>I would just pin it not to install, unless you need it, and if that's the case I don't have a solution for that .(Sorry my friend :()
EDIT: You did run apt clean first.
```
sudo apt clean && sudo apt autoremove
```

---

