---
title: "How to have a custom Grub2 menu that is maintenance free"
date: 2012-10-25
forum: Documentation and Community Wiki Discussions
---

### Post by Cavsfan on 2012-10-25
If you just use Ubuntu or dual boot/multi boot Ubuntu with Debian, Mint, Arch, Fedora, openSUSE, Windows, etc. this will give you all the information to create a custom background, fonts colors and menu that never needs modified.
You can also choose the default OS and the timeout before the default OS is selected. That will never need changing even when a new kernel is installed in any Linux system. 

It has been updated for UEFI/GPT partitioned systems.

The only time you would need to modify anything is if you get bored with the background picture, font colors or if you install/remove/re-install an operating system.

The Wiki evolved from this thread: [[COLOR=blue]_How to: Create a Customized GRUB2 Screen that is Maintenance Free._[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1542338")

There are several examples of what your screen could look like.

There is a link in the bottom of the Wiki that links back to this thread to post questions, comments, problems, etc.

All Linux systems are pretty much the same as far as customizing grub goes but, Arch is a little different see here for [Arch Linux]("https://ubuntuforums.org/showthread.php?t=2298744").

Grub has gotten much simpler and you should find that it is easier to customize. The Wiki has been updated with the ability to boot into the backup kernel.

[COLOR=#333333][FONT=Ubuntu]If you choose not to have that ability,  just omit that part and go with 2 entries per system instead of the three in the Wiki.[/FONT][/COLOR]

---

### Post by dino99 on 2012-10-25
hey you made a good job, clearly explained, thanks.  :P:P
thats kind of wiki have a place into "tutorials & tips" subforum.

---

### Post by Cavsfan on 2012-10-25
> **dino99 said:**
> hey you made a good job, clearly explained, thanks.  :P:P
thats kind of wiki have a place into "tutorials & tips" subforum.

You're welcome. 
Didn't you get the message:
[http://ubuntuforums.org/showthread.php?t=2074191](http://ubuntuforums.org/showthread.php?t=2074191)

"the forum will be closed completely to posting after a transitional period." :razz:

---

### Post by Cavsfan on 2012-10-26
Here is my current Grub2 menu on Quantal Quetzal 12.10.
I have 2 Lucid installs, a Precise Pangolin install, a Quantal Quetzal install and Windows 7.
I leave the default on Windows 7 for my wife in case the PC reboots.
Even when new kernels are installed in any Ubuntu, the default still is Windows 7. 
The normal font color is yellow and highlight is white.

[[IMG]http://ompldr.org/tZzE5Mw[/IMG]]("http://ompldr.org/vZzE5Mw")

Feel free to post your custom grub2 menu if you have used my wiki to make it. :)

---

### Post by Cavsfan on 2012-10-29
I installed 3 more systems - Lucid, Precise and Quantal on separate partitions to keep the grub files generic in case anyone needs a copy of the original file.

I got an upgrade to grub and it gave me some errors. Luckily I had a copy of **05_debian_theme** to fix the error.

I had to edit fstab every time I installed another system as it would pull all of the swap partitions into fstab.
There is a section on editing fstab when installing or reinstalling Ubuntu in the wiki in my signature in section 1.7.

It would be very difficult to maneuver the long menu without customizing it as I have.
Here is what my grub2 screen currently looks like with 7 operating systems:

[[IMG]http://ompldr.org/tZzJpNg[/IMG]]("http://ompldr.org/vZzJpNg")

Here is the output of **sudo blkid**:

```
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Lucid" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" 
/dev/sda3: UUID="2a80f59e-e7c3-418e-aab2-ab5d19255a2f" TYPE="swap" 
/dev/sda5: LABEL="Precise" UUID="3b8b1954-24e6-4a5e-9074-70a1a94ed4be" TYPE="ext4" 
/dev/sda6: UUID="82c51b29-023f-4964-99b6-67b45a49527f" TYPE="swap" 
/dev/sda7: LABEL="Quantal" UUID="b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a" TYPE="ext4" 
/dev/sda8: UUID="69ac3efc-8a8a-4056-89e0-59bb81c2f468" TYPE="swap" 
/dev/sda9: LABEL="Lucid-Generic" UUID="109c11d0-71e3-41a4-87da-9e81535499a5" TYPE="ext4" 
/dev/sda10: UUID="24aa8c8b-53dc-4ecc-852b-ff2c25c8b342" TYPE="swap" 
/dev/sda11: LABEL="Precise-Generic" UUID="50104efb-d918-45a9-985e-a70c60e87ac0" TYPE="ext4" 
/dev/sda12: UUID="139390a6-2fe1-4ff2-b650-88ae3b0586c1" TYPE="swap" 
/dev/sda13: UUID="580e8c62-78ce-44a2-93e3-ccebd37c3acc" TYPE="ext4" LABEL="Quantal-Generic" 
/dev/sda14: UUID="ec3048b8-c644-435a-93bb-08bb4975d0db" TYPE="swap" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs"
```

They are easy to recognize since they have all been labeled as explained in 1.6 of the wiki.

I will try to put the generic grub files on the wiki but, if any one needs a copy of something let me know and I will post the contents of the file here.

---

### Post by bogan on 2012-10-29
HI!, **Cavsfan**,

I see your latest Grub menu is still using Grub v1.98-1: I thought grub 2 was 1.99.

With Quantal 12.10 Grub Customizer is a disaster, and I get no recovery options, so I am tempted to try your method; I have studied it with interest in the past, but have not tried it out, as Grub Customer did what I needed.

Will it work with Grub 2 v2.00 ??  which has files very different from previous versions.

Edit:  I use the following to see what my grub menu will look like : will it work with your system ? ```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```Currently mine shows like this:  ```
0    ature_menuentry_id}
     1    _id_option=
     2    _id_option=
     3    entry_id_option
     4    Ubuntu  3.5.0-18 Linux 12.1 (on sda10)
     5    Memory test (memtest86+)
     6    Ubuntu Quantal (12.10) (on USB)
     7    Ubuntu 12.04.1 LTS (12.04)
     8    Ubuntu 12.10 (12.10)
     9    Ubuntu 12.04.1 LTS (12.04)
    10    Ubuntu 12.04.1 LTS (12.04)
    11    Windows 7 (loader) (on /dev/sda1)
    12    Ubuntu 3.2.0-33pae (12.04.1) ( on sda5)
```I have no idea what the first three entries mean, the first [Number 4] and the last, I renamed in grub Customer; entry 6 I( edited in /boot/grub/grub,cfg; whilst entries 7,9, & 10 are spurious duplicates of the sda5 entry, created by update-grub & Grub Customizer

Chao!, **bogan.**

---

### Post by Cavsfan on 2012-10-29
> **bogan said:**
> HI!, **Cavsfan**,

I see your latest Grub menu is still using Grub v1.98-1: I thought grub 2 was 1.99.

With Quantal 12.10 Grub Customizer is a disaster, and I get no recovery options, so I am tempted to try your method; I have studied it with interest in the past, but have not tried it out, as Grub Customer did what I needed.

Will it work with Grub 2 v2.00 ??  which has files very different from previous versions.

Edit:  I use the following to see what my grub menu will look like : will it work with your system ? ```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```Currently mine shows like this:  ```
0    ature_menuentry_id}
     1    _id_option=
     2    _id_option=
     3    entry_id_option
     4    Ubuntu  3.5.0-18 Linux 12.1 (on sda10)
     5    Memory test (memtest86+)
     6    Ubuntu Quantal (12.10) (on USB)
     7    Ubuntu 12.04.1 LTS (12.04)
     8    Ubuntu 12.10 (12.10)
     9    Ubuntu 12.04.1 LTS (12.04)
    10    Ubuntu 12.04.1 LTS (12.04)
    11    Windows 7 (loader) (on /dev/sda1)
    12    Ubuntu 3.2.0-33pae (12.04.1) ( on sda5)
```I have no idea what the first three entries mean, the first [Number 4] and the last, I renamed in grub Customer; entry 6 I( edited in /boot/grub/grub,cfg; whilst entries 7,9, & 10 are spurious duplicates of the sda5 entry, created by update-grub & Grub Customizer

Chao!, **bogan.**

Hi **bogan**!

Replace that old command with this one:
```
grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
```
I got that from **drs305** just in case you thought I was smart enough to come up with it myself! :)
Not sure why but, that old one doesn't even work in Lucid any more!
However neither can see what is in the submenus of the default grub menu.
The submenus came with grub 1.99 I believe.

Here is the output of that command on my system and it looks just like the picture:
```
     0    menuentry "Lucid Lynx" {
     1    menuentry "Lucid Lynx (Recovery Mode)" {
     2    menuentry "Lucid Lynx Generic" {
     3    menuentry "Lucid Lynx Generic (Recovery Mode)" {
     4    menuentry "Precise Pangolin 12.04" {
     5    menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     6    menuentry "Precise Pangolin Generic 12.04" {
     7    menuentry "Precise Pangolin 12.04 Generic (Recovery Mode)" {
     8    menuentry "Quantal Quetzel 12.10" {
     9    menuentry "Quantal Quetzel 12.10 (Recovery Mode)" {
    10    menuentry "Quantal Quetzel Generic 12.10" {
    11    menuentry "Quantal Quetzel 12.10 Generic (Recovery Mode)" {
    12    menuentry "Windows 7" {
```

That picture is on Lucid and it uses grub 1.98, I believe Maverick Meerkat and anything after that and before Quantal uses grub 1.99.
Quantal uses grub 2.00.

The wiki is broken down into Lucid at the top (1.3 in the table of contents) and Maverick and later towards the bottom (1.4).
There are just a couple of differences between 1.99 and 2.00 in 05_debian_theme.
Pretty much everything else is the same.
Grub 1.99 gives an erroneous error when selecting windows but, still goes into windows.
Grub 2.00 does not give any error when selecting windows which is why I am glad Precise is getting grub 2.0 in January. At least that is what I heard.

The wiki is a lot more straight forward than that How to. It became pretty convoluted and it was closed for editing. The Forum's policy is How Tos should be in wiki format.

So, be sure and use the wiki on the first post of this thread or in my signature (green links).
Let me know what you think and if you use it post your grub menu when you are done. :)

Thanks for the post! :D

---

### Post by Cavsfan on 2012-10-30
Here is my current grub2 menu customized on Precise grub 1.99:

[[IMG]http://ompldr.org/tZzJ5cg[/IMG]]("http://ompldr.org/vZzJ5cg")

The normal font color is yellow and the highlight font color is white.

---

### Post by Cavsfan on 2012-10-30
Here is my current grub2 menu customized on Quantal grub 2.00:

[[IMG]http://ompldr.org/tZzJ5cw[/IMG]]("http://ompldr.org/vZzJ5cw")

The normal font color is cyan and the highlight font color is light-red.

---

### Post by bogan on 2012-10-30
Hi!, **Cavsfan**,

Thanks for your response, Post #7, for some reason my subscription advisory did not pick it up.

In Quantal with grub 2.00 and Grub Customizer 3,  the 'old command' showed exactly what was displayed on the screen, apart from the first three odd extra bits.

Weirdly, the 'new command', you suggested, shows not  only what is displayed, but in addition, it shows the entries complete with part of the script for each:```
alan@alan-MS-7616:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0    menuentry "Ubuntu  3.5.0-18 Linux 12.1 (on sda10)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-b5aab3a2-0086-4a12-9276-46bb5a615038
     1    menuentry "Memory test (memtest86+)" {
     2    menuentry "Ubuntu 12.10 (12.10)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-cee38717-6980-4485-a047-124edb4d5a23
     3    menuentry "Ubuntu Quantel (12.10) on USB" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7608b1e5-b5ea-4563-ad94-8cf496b9f95f
     4    menuentry "Ubuntu 3.5.0-18 (12.10) on sdb7 External" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7608b1e5-b5ea-4563-ad94-8cf496b9f95f
     5    menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os $menuentry_id_option 'osprober-chain-CC9240F39240E394
     6    menuentry "Ubuntu 3.2.0-33pae (12.04.1) ( on sda5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a8ecbe4f-fc2d-40a1-b261-1b62d74e7130
alan@alan-MS-7616:~$ 
```Line 2 is actually the entry for the USB OS and line 3, labelled 'USB', is actually a duplicate of the sda5 entry line6, which is very confusing.

I have had this problem of duplicate entries for some time and Posted about it but got no response; Grub customizer adds them on Saving the configuration.

As far as I can see, to use your system, I would need to start with virgin installations of all the OSs, none of them having run Grub Customizer, as the duplicates get copied from one OS to another by update-grub.

Chao!, **bogan.**

---

### Post by Cavsfan on 2012-10-30
> **bogan said:**
> Hi!, **Cavsfan**,

Thanks for your response, Post #7, for some reason my subscription advisory did not pick it up.

In Quantal with grub 2.00 and Grub Customizer 3,  the 'old command' showed exactly what was displayed on the screen, apart from the first three odd extra bits.

Weirdly, the 'new command', you suggested, shows not  only what is displayed, but in addition, it shows the entries complete with part of the script for each:```
alan@alan-MS-7616:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0    menuentry "Ubuntu  3.5.0-18 Linux 12.1 (on sda10)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-b5aab3a2-0086-4a12-9276-46bb5a615038
     1    menuentry "Memory test (memtest86+)" {
     2    menuentry "Ubuntu 12.10 (12.10)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-cee38717-6980-4485-a047-124edb4d5a23
     3    menuentry "Ubuntu Quantel (12.10) on USB" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7608b1e5-b5ea-4563-ad94-8cf496b9f95f
     4    menuentry "Ubuntu 3.5.0-18 (12.10) on sdb7 External" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-7608b1e5-b5ea-4563-ad94-8cf496b9f95f
     5    menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os $menuentry_id_option 'osprober-chain-CC9240F39240E394
     6    menuentry "Ubuntu 3.2.0-33pae (12.04.1) ( on sda5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a8ecbe4f-fc2d-40a1-b261-1b62d74e7130
alan@alan-MS-7616:~$ 
```Line 2 is actually the entry for the USB OS and line 3, labelled 'USB', is actually a duplicate of the sda5 entry line6, which is very confusing.

I have had this problem of duplicate entries for some time and Posted about it but got no response; Grub customizer adds them on Saving the configuration.

As far as I can see, to use your system, I would need to start with virgin installations of all the OSs, none of them having run Grub Customizer, as the duplicates get copied from one OS to another by update-grub.

Chao!, **bogan.**

Hi **bogan**!

It's likely to be your /etc/fstab that is causing the multiple entries.
I mention this in 1.7 of the wiki.
In terminal enter **sudo blkid** to get your paritions and UUIDs.

In my case I just have an ext4 partition mounted at / and a swap file for each system so only 2 entries appear in my fstab.

```
cavsfan@cavsfan-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=a162dc8a-e4df-4b79-b4c3-524761ff7ae1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=2a80f59e-e7c3-418e-aab2-ab5d19255a2f none            swap    sw              0       0
```Just make sure your fstab is correct according to **blkid**.

If you want copies of all of the grub files I can give them to you. Just let me know what Ubuntu you need it for.
It looks like Quantal Quetzal 12.10 is that correct. No use doing a total install just to get new grub files.

I installed the 3 Ubuntus I have again just to keep the grub files untouched in case someone needed them like you.

I will login to my generic Quantal install and post copies of all the grub files and you can just copy and paste them into the contents of your grub files.
That should allow you to "start over".
:)

---

### Post by bogan on 2012-10-30
Hi!, Cavsfan,

Thanks again.  I am not sure what to look for in /etc/fstab, it looks much like yours except there is a entry for /home, and for some reason it also lists the Swap from the 12.10 USB, but not the one from 12.10 sdb7 [perhaps the later was not mounted].```
alan@alan-MS-7616:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
[Text deleted]
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda10 during installation
UUID=b5aab3a2-0086-4a12-9276-46bb5a615038 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda11 during installation
UUID=adc771a1-313c-47ae-8725-3c89b89bbfa2 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a74af1d9-f7f9-4453-97e7-b9e3f370dca4 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=9a74bb15-1215-4774-8419-f2908ee62d2e none            swap    sw              0       0
alan@alan-MS-7616:~$
```I  have one virgin 12.10 installation in which I deliberately did  not run Grub Customizer, so it would be 12.04.1 for which I might need  the grub files.

Presumably I will need to replace the files in  all the other installations, as they interact; as well as deleting all  the Grub Customizer files.

Chao!, bogan.

---

### Post by Cavsfan on 2012-10-30
Here is how the original grub files as in /etc/grub.d/ appear:
```
cavsfan@cavsfan-MS-7529:~$ cd /etc/grub.d/
cavsfan@cavsfan-MS-7529:/etc/grub.d$ ls -l
total 72
-rwxr-xr-x 1 root root  7541 Oct 14 13:36 [COLOR=Green]00_header[/COLOR]
-rwxr-xr-x 1 root root  5488 Oct  4 05:30 [COLOR=Green]05_debian_theme[/COLOR]
-rwxr-xr-x 1 root root 10891 Oct 14 13:36 [COLOR=Green]10_linux[/COLOR]
-rwxr-xr-x 1 root root 10258 Oct 14 13:36 [COLOR=SeaGreen]20_linux_xen[/COLOR]
-rwxr-xr-x 1 root root  1688 Oct 11 10:10 [COLOR=Green]20_memtest86+[/COLOR]
-rwxr-xr-x 1 root root 10976 Oct 14 13:36 [COLOR=Green]30_os-prober[/COLOR]
-rwxr-xr-x 1 root root  1426 Oct 14 13:36 [COLOR=Green]30_uefi-firmware[/COLOR]
-rwxr-xr-x 1 root root   214 Oct 14 13:36 [COLOR=Green]40_custom[/COLOR]
-rwxr-xr-x 1 root root   216 Oct 14 13:36 [COLOR=Green]41_custom[/COLOR]
-rw-r--r-- 1 root root   483 Oct 14 13:36 README

```I would think **/etc/default/grub** might be one you need:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```**/etc/grub.d/05_debian_theme**:
```
#!/bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2010  Alexander Kurtz <kurtz.alex@googlemail.com>
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

# Include the GRUB helper library for grub-mkconfig.
. /usr/share/grub/grub-mkconfig_lib

# We want to work in /boot/grub/ only.
test -d /boot/grub; cd /boot/grub

# Set the location of a possibly necessary cache file for the background image.
# NOTE: This MUST BE A DOTFILE to avoid confusing it with user-defined images.
BACKGROUND_CACHE=".background_cache"

set_default_theme(){
    # Set a monochromatic theme for Ubuntu.
    echo "${1}set menu_color_normal=white/black"
    echo "${1}set menu_color_highlight=black/light-gray"

    if [ -e /lib/plymouth/themes/default.grub ]; then
        sed "s/^/${1}/" /lib/plymouth/themes/default.grub
    fi
}

module_available(){
    local module
    for module in "${1}.mod" */"${1}.mod"; do
        if [ -f "${module}" ]; then
            return 0
        fi
    done
    return 1
}

set_background_image(){
    # Step #1: Search all available output modes ...
    local output
    for output in ${GRUB_TERMINAL_OUTPUT}; do
        if [ "x$output" = "xgfxterm" ]; then
            break
        fi
    done

    # ... and check if we are able to display a background image at all.
    if ! [ "x${output}" = "xgfxterm" ]; then
        return 1
    fi

    # Step #2: Check if the specified background image exists.
    if ! [ -f "${1}" ]; then
        return 2
    fi

    # Step #3: Search the correct GRUB module for our background image.
    local reader
    case "${1}" in
        *.jpg|*.JPG|*.jpeg|*.JPEG) reader="jpeg";;
        *.png|*.PNG) reader="png";;
        *.tga|*.TGA) reader="tga";;
        *) return 3;; # Unknown image type.
    esac

    # Step #4: Check if the necessary GRUB module is available.
    if ! module_available "${reader}"; then
        return 4
    fi

    # Step #5: Check if GRUB can read the background image directly.
    # If so, we can remove the cache file (if any). Otherwise the backgound
    # image needs to be cached under /boot/grub/.
    if is_path_readable_by_grub "${1}"; then
        rm --force "${BACKGROUND_CACHE}.jpeg" \
            "${BACKGROUND_CACHE}.png" "${BACKGROUND_CACHE}.tga"
    elif cp "${1}" "${BACKGROUND_CACHE}.${reader}"; then
        set -- "${BACKGROUND_CACHE}.${reader}" "${2}" "${3}"
    else
        return 5
    fi

    # Step #6: Prepare GRUB to read the background image.
    if ! prepare_grub_to_access_device "`${grub_probe} --target=device "${1}"`"; then
        return 6
    fi

    # Step #7: Everything went fine, print out a message to stderr ...
    echo "Found background image: ${1}" >&2

    # ... and write our configuration snippet to stdout. Use the colors
    # desktop-base specified. If we're using a user-defined background, use
    # the default colors since we've got no idea how the image looks like.
    # If loading the background image fails, use the default theme.
    echo "insmod ${reader}"
    echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
    if [ -n "${2}" ]; then
        echo "  set color_normal=${2}"
    fi
    if [ -n "${3}" ]; then
        echo "  set color_highlight=${3}"
    fi
    if [ -z "${2}" ] && [ -z "${3}" ]; then
        echo "  true"
    fi
    echo "else"
    set_default_theme "  "
    echo "fi"
}

# Earlier versions of grub-pc copied the default background image to /boot/grub
# during postinst. Remove those obsolete images if they haven't been touched by
# the user. They are still available under /usr/share/images/desktop-base/ if
# desktop-base is installed.
while read checksum background; do
    if [ -f "${background}" ] && [ "x`sha1sum "${background}"`" = "x${checksum}  ${background}" ]; then
        echo "Removing old background image: ${background}" >&2
        rm "${background}"
    fi
done <<EOF
648ee65dd0c157a69b019a5372cbcfea4fc754a5  debian-blueish-wallpaper-640x480.png
0431e97a6c661084c59676c4baeeb8c2f602edb8  debian-blueish-wallpaper-640x480.png
968ecf6696c5638cfe80e8e70aba239526270864  debian-blueish-wallpaper-640x480.tga
11143e8c92a073401de0b0fd42d0c052af4ccd9b  moreblue-orbit-grub.png
d00d5e505ab63f2d53fa880bfac447e2d3bb197c  moreblue-orbit-grub.png
f5b12c1009ec0a3b029185f6b66cd0d7e5611019  moreblue-orbit-grub.png
EOF

# Include the configuration of desktop-base if available.
if [ -f "/usr/share/desktop-base/grub_background.sh" ]; then
    . "/usr/share/desktop-base/grub_background.sh"
fi

# First check whether the user has specified a background image explicitly.
# If so, try to use it. Don't try the other possibilities in that case
# (#608263).
if [ -n "${GRUB_BACKGROUND+x}" ]; then
    set_background_image "${GRUB_BACKGROUND}" || set_default_theme
    exit 0
fi

# Next search for pictures the user put into /boot/grub/ and use the first one.
for background in *.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga *.TGA; do
    if set_background_image "${background}"; then
        exit 0
    fi
done

# Next try to use the background image and colors specified by desktop-base.
if set_background_image "${WALLPAPER}" "${COLOR_NORMAL}" "${COLOR_HIGHLIGHT}"; then
    exit 0
fi

# Finally, if all of the above fails, use the default theme.
set_default_theme
```**/etc/grub.d/10_linux**
```
#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"

. "${datarootdir}/grub/grub-mkconfig_lib"

export TEXTDOMAIN=grub
export TEXTDOMAINDIR="${datarootdir}/locale"

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr 'A-Z' 'a-z' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || uses_abstraction "${GRUB_DEVICE}" lvm; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

GRUBFS="`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2>/dev/null || true`"

if [ x"$GRUBFS" = x ]; then
    GRUBFS="$(stat -f --printf=%T / || true)"
fi

case x"$GRUBFS" in
    xbtrfs)
    rootsubvol="`make_system_path_relative_to_its_root /`"
    rootsubvol="${rootsubvol#/}"
    if [ "x${rootsubvol}" != x ]; then
        GRUB_CMDLINE_LINUX="rootflags=subvol=${rootsubvol} ${GRUB_CMDLINE_LINUX}"
    fi;;
    xzfs)
    rpool=`${grub_probe} --device ${GRUB_DEVICE} --target=fs_label 2>/dev/null || true`
    bootfs="`make_system_path_relative_to_its_root / | sed -e "s,@$,,"`"
    LINUX_ROOT_DEVICE="ZFS=${rpool}${bootfs}"
    ;;
esac

title_correction_code=

for word in $GRUB_CMDLINE_LINUX_DEFAULT; do
  if [ "$word" = splash ]; then
    GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT \$vt_handoff"
  fi
done

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  type="$3"
  args="$4"

  if [ -z "$boot_device_id" ]; then
      boot_device_id="$(grub_get_device_id "${GRUB_DEVICE}")"
  fi
  if [ x$type != xsimple ] ; then
      case $type in
      recovery)
          title="$(gettext_printf "%s, with Linux %s (recovery mode)" "${os}" "${version}")" ;;
      *)
          title="$(gettext_printf "%s, with Linux %s" "${os}" "${version}")" ;;
      esac
      if [ x"$title" = x"$GRUB_ACTUAL_DEFAULT" ] || [ x"Previous Linux versions>$title" = x"$GRUB_ACTUAL_DEFAULT" ]; then
      replacement_title="$(echo "Advanced options for ${OS}" | sed 's,>,>>,g')>$(echo "$title" | sed 's,>,>>,g')"
      quoted="$(echo "$GRUB_ACTUAL_DEFAULT" | grub_quote)"
      title_correction_code="${title_correction_code}if [ \"x\$default\" = '$quoted' ]; then default='$(echo "$replacement_title" | grub_quote)'; fi;"
      grub_warn "$(gettext_printf "Please don't use old title \`%s' for GRUB_DEFAULT, use \`%s' (for versions before 2.00) or \`%s' (for 2.00 or later)" "$GRUB_ACTUAL_DEFAULT" "$replacement_title" "gnulinux-advanced-$boot_device_id>gnulinux-$version-$type-$boot_device_id")"
      fi
      echo "menuentry '$(echo "$title" | grub_quote)' ${CLASS} \$menuentry_id_option 'gnulinux-$version-$type-$boot_device_id' {" | sed "s/^/$submenu_indentation/"
  else
      echo "menuentry '$(echo "$os" | grub_quote)' ${CLASS} \$menuentry_id_option 'gnulinux-simple-$boot_device_id' {" | sed "s/^/$submenu_indentation/"
  fi      
  echo "recordfail" | sed "s/^/$submenu_indentation/"
  if [ x$type != xrecovery ] ; then
      save_default_entry | sed -e "s/^/\t/"

      echo "    gfxmode \$linux_gfx_mode" | sed "s/^/$submenu_indentation/"
  fi

  echo "    insmod gzio" | sed "s/^/$submenu_indentation/"

  if [ x$dirname = x/ ]; then
    if [ -z "${prepare_root_cache}" ]; then
      prepare_root_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE} | sed -e "s/^/\t/")"
    fi
    printf '%s\n' "${prepare_root_cache}" | sed "s/^/$submenu_indentation/"
  else
    if [ -z "${prepare_boot_cache}" ]; then
      prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
    fi
    printf '%s\n' "${prepare_boot_cache}" | sed "s/^/$submenu_indentation/"
  fi
  if [ x$type != xsimple ]; then
    message="$(gettext_printf "Loading Linux %s ..." ${version})"
    sed "s/^/$submenu_indentation/" << EOF
    echo    '$(echo "$message" | grub_quote)'
EOF
  fi
  if test -d /sys/firmware/efi && test -e "${linux}.efi.signed"; then
    sed "s/^/$submenu_indentation/" << EOF
    linux    ${rel_dirname}/${basename}.efi.signed root=${linux_root_device_thisversion} ro ${args}
EOF
  else
    sed "s/^/$submenu_indentation/" << EOF
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  fi
  if test -n "${initrd}" ; then
    # TRANSLATORS: ramdisk isn't identifier. Should be translated.
    if [ x$type != xsimple ]; then
      message="$(gettext_printf "Loading initial ramdisk ...")"
      sed "s/^/$submenu_indentation/" << EOF
    echo    '$(echo "$message" | grub_quote)'
EOF
    fi
    sed "s/^/$submenu_indentation/" << EOF
    initrd    ${rel_dirname}/${initrd}
EOF
  fi
  sed "s/^/$submenu_indentation/" << EOF
}
EOF
}

machine=`uname -m`
case "x$machine" in
    xi?86 | xx86_64)
    list=`for i in /boot/vmlinuz-* /vmlinuz-* /boot/kernel-* ; do
                  if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
              done` ;;
    *) 
    list=`for i in /boot/vmlinuz-* /boot/vmlinux-* /vmlinuz-* /vmlinux-* /boot/kernel-* ; do
                  if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
         done` ;;
esac

case "$machine" in
    i?86) GENKERNEL_ARCH="x86" ;;
    mips|mips64) GENKERNEL_ARCH="mips" ;;
    mipsel|mips64el) GENKERNEL_ARCH="mipsel" ;;
    arm*) GENKERNEL_ARCH="arm" ;;
    *) GENKERNEL_ARCH="$machine" ;;
esac

prepare_boot_cache=
prepare_root_cache=
boot_device_id=
title_correction_code=

cat << 'EOF'
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
EOF

# Use ELILO's generic "efifb" when it's known to be available.
# FIXME: We need an interface to select vesafb in case efifb can't be used.
if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
  echo "set linux_gfx_mode=$GRUB_GFXPAYLOAD_LINUX"
else
  cat << EOF
if [ "\${recordfail}" != 1 ]; then
  if [ -e \${prefix}/gfxblacklist.txt ]; then
    if hwmatch \${prefix}/gfxblacklist.txt 3; then
      if [ \${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
EOF
fi
cat << EOF
export linux_gfx_mode
if [ "\${linux_gfx_mode}" != "text" ]; then load_video; fi
EOF

# Extra indentation to add to menu entries in a submenu. We're not in a submenu
# yet, so it's empty. In a submenu it will be equal to '\t' (one tab).
submenu_indentation=""

is_first_entry=true
while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  case $linux in
    *.efi.signed)
      # We handle these in linux_entry.
      list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
      continue
      ;;
  esac
  gettext_printf "Found linux image: %s\n" "$linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" "initrd-${version}.gz" \
       "initrd-${version}" "initramfs-${version}.img" \
       "initrd.img-${alt_version}" "initrd-${alt_version}.img" \
       "initrd-${alt_version}" "initramfs-${alt_version}.img" \
       "initramfs-genkernel-${version}" \
       "initramfs-genkernel-${alt_version}" \
       "initramfs-genkernel-${GENKERNEL_ARCH}-${version}" \
       "initramfs-genkernel-${GENKERNEL_ARCH}-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done

  config=
  for i in "${dirname}/config-${version}" "${dirname}/config-${alt_version}" "/etc/kernels/kernel-config-${version}" ; do
    if test -e "${i}" ; then
      config="${i}"
      break
    fi
  done

  initramfs=
  if test -n "${config}" ; then
      initramfs=`grep CONFIG_INITRAMFS_SOURCE= "${config}" | cut -f2 -d= | tr -d \"`
  fi

  if test -n "${initrd}" ; then
    gettext_printf "Found initrd image: %s\n" "${dirname}/${initrd}" >&2
  elif test -z "${initramfs}" ; then
    # "UUID=" and "ZFS=" magic is parsed by initrd or initramfs.  Since there's
    # no initrd or builtin initramfs, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  if [ "x$is_first_entry" = xtrue ]; then
    linux_entry "${OS}" "${version}" simple \
    "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}"

    submenu_indentation="\t"
    
    if [ -z "$boot_device_id" ]; then
    boot_device_id="$(grub_get_device_id "${GRUB_DEVICE}")"
    fi
    # TRANSLATORS: %s is replaced with an OS name
    echo "submenu '$(gettext_printf "Advanced options for %s" "${OS}" | grub_quote)' \$menuentry_id_option 'gnulinux-advanced-$boot_device_id' {"
  fi

  linux_entry "${OS}" "${version}" advanced \
              "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}"
  if [ "x${GRUB_DISABLE_RECOVERY}" != "xtrue" ]; then
    if [ -x /lib/recovery-mode/recovery-menu ]; then
      linux_entry "${OS}" "${version}" recovery \
          "recovery nomodeset ${GRUB_CMDLINE_LINUX}"
    else
      linux_entry "${OS}" "${version}" recovery \
          "single nomodeset ${GRUB_CMDLINE_LINUX}"
    fi
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
  is_first_entry=false
done

# If at least one kernel was found, then we need to
# add a closing '}' for the submenu command.
if [ x"$is_first_entry" != xtrue ]; then
  echo '}'
fi

echo "$title_correction_code"
```

**/etc/grub.d/30_os-prober**
```
#! /bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"

export TEXTDOMAIN=grub
export TEXTDOMAINDIR="${datarootdir}/locale"

. "${datarootdir}/grub/grub-mkconfig_lib"

found_other_os=

make_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
    if [ "x${1}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
	verbose=
      else
	verbose=" --verbose"
      fi

      if [ "x${1}" = "x0" ] ; then
	cat <<EOF
if [ "x\${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
	cat << EOF
if [ "x\${timeout}" != "x-1" ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
  fi
}

adjust_timeout () {
  if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
    make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
    echo else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
    echo fi
  else
    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
  fi
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
  adjust_timeout
  exit 0
fi

if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
  # missing os-prober and/or linux-boot-prober
  adjust_timeout
  exit 0
fi

OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
if [ -z "${OSPROBED}" ] ; then
  # empty os-prober output, nothing doing
  adjust_timeout
  exit 0
fi

osx_entry() {
    found_other_os=1
    if [ x$2 = x32 ]; then
        # TRANSLATORS: it refers to kernel architecture (32-bit)
	bitstr="$(gettext "(32-bit)")"
    else
        # TRANSLATORS: it refers to kernel architecture (64-bit)
	bitstr="$(gettext "(64-bit)")"
    fi
    # TRANSLATORS: it refers on the OS residing on device %s
    onstr="$(gettext_printf "(on %s)" "${DEVICE}")"
        cat << EOF
menuentry '$(echo "${LONGNAME} $bitstr $onstr" | grub_quote)' --class osx --class darwin --class os \$menuentry_id_option 'osprober-xnu-$2-$(grub_get_device_id "${DEVICE}")'  {
EOF
	save_default_entry | sed -e "s/^/\t/"
	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
	cat << EOF
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ \$do_resume = 0 ]; then
           xnu_uuid ${OSXUUID} uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           if [ /kernelcache -nt /System/Library/Extensions ]; then
              $1 /kernelcache boot-uuid=\${uuid} rd=*uuid
           else
              $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
              if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
                xnu_mkext /System/Library/Extensions.mkext
              else
                xnu_kextdir /System/Library/Extensions
              fi
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
EOF
}

used_osprober_linux_ids=

wubi=

for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

  gettext_printf "Found %s on %s\n" "${LONGNAME}" "${DEVICE}" >&2

  case ${BOOT} in
    chain)

      case ${LONGNAME} in
	Windows*)
	  if [ -z "$wubi" ]; then
	    if [ -x /usr/share/lupin-support/grub-mkimage ] && \
	       /usr/share/lupin-support/grub-mkimage --test; then
	      wubi=yes
	    else
	      wubi=no
	    fi
	  fi
	  if [ "$wubi" = yes ]; then
	    echo "Skipping ${LONGNAME} on Wubi system" >&2
	    continue
	  fi
	  ;;
      esac

      found_other_os=1
	  onstr="$(gettext_printf "(on %s)" "${DEVICE}")"
      cat << EOF
menuentry '$(echo "${LONGNAME} $onstr" | grub_quote)' --class windows --class os \$menuentry_id_option 'osprober-chain-$(grub_get_device_id "${DEVICE}")' {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"

      case ${LONGNAME} in
	Windows\ Vista*|Windows\ 7*|Windows\ Server\ 2008*)
	;;
	*)
	  cat << EOF
	drivemap -s (hd0) \${root}
EOF
	;;
      esac

      cat <<EOF
	chainloader +1
}
EOF
    ;;
    linux)
      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
      prepare_boot_cache=
      boot_device_id=
      is_first_entry=true
      title_correction_code=
      OS="${LONGNAME}"

      for LINUX in ${LINUXPROBED} ; do
        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"

        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

	if [ "${LROOT}" != "${LBOOT}" ]; then
	  LKERNEL="${LKERNEL#/boot}"
	  LINITRD="${LINITRD#/boot}"
	fi

	if [ -z "${prepare_boot_cache}" ]; then
	  prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
	  [ "${prepare_boot_cache}" ] || continue
	fi

	found_other_os=1
	onstr="$(gettext_printf "(on %s)" "${DEVICE}")"
	recovery_params="$(echo "${LPARAMS}" | grep 'single\|recovery')" || true
	counter=1
	while echo "$used_osprober_linux_ids" | grep 'osprober-gnulinux-$LKERNEL-${recovery_params}-$counter-$boot_device_id' > /dev/null; do
	    counter=$((counter+1));
	done
	if [ -z "$boot_device_id" ]; then
	    boot_device_id="$(grub_get_device_id "${DEVICE}")"
	fi
	used_osprober_linux_ids="$used_osprober_linux_ids 'osprober-gnulinux-$LKERNEL-${recovery_params}-$counter-$boot_device_id'"

	if [ "x$is_first_entry" = xtrue ]; then
            cat << EOF
menuentry '$(echo "$OS" | grub_quote)' --class gnu-linux --class gnu --class os \$menuentry_id_option 'osprober-gnulinux-simple-$boot_device_id' {
EOF
	    save_default_entry | sed -e "s/^/\t/"
	    printf '%s\n' "${prepare_boot_cache}"
	    cat <<  EOF
	linux ${LKERNEL} ${LPARAMS}
EOF
            if [ -n "${LINITRD}" ] ; then
          cat << EOF
	initrd ${LINITRD}
EOF
            fi
        cat << EOF
}
EOF
	    echo "submenu '$(gettext_printf "Advanced options for %s" "${OS}" | grub_quote)' \$menuentry_id_option 'osprober-gnulinux-advanced-$boot_device_id' {"
	    is_first_entry=false
	fi
	title="${LLABEL} $onstr"
        cat << EOF
	menuentry '$(echo "$title" | grub_quote)' --class gnu-linux --class gnu --class os \$menuentry_id_option 'osprober-gnulinux-$LKERNEL-${recovery_params}-$boot_device_id' {
EOF
	save_default_entry | sed -e "s/^/\t\t/"
	printf '%s\n' "${prepare_boot_cache}" | sed -e "s/^/\t/"
	cat <<  EOF
		linux ${LKERNEL} ${LPARAMS}
EOF
        if [ -n "${LINITRD}" ] ; then
            cat << EOF
		initrd ${LINITRD}
EOF
        fi
        cat << EOF
	}
EOF
	if [ x"$title" = x"$GRUB_ACTUAL_DEFAULT" ] || [ x"Previous Linux versions>$title" = x"$GRUB_ACTUAL_DEFAULT" ]; then
	    replacement_title="$(echo "Advanced options for ${OS}" | sed 's,>,>>,g')>$(echo "$title" | sed 's,>,>>,g')"
	    quoted="$(echo "$GRUB_ACTUAL_DEFAULT" | grub_quote)"
	    title_correction_code="${title_correction_code}if [ \"x\$default\" = '$quoted' ]; then default='$(echo "$replacement_title" | grub_quote)'; fi;"
	    grub_warn "$(gettext_printf "Please don't use old title \`%s' for GRUB_DEFAULT, use \`%s' (for versions before 2.00) or \`%s' (for 2.00 or later)" "$GRUB_ACTUAL_DEFAULT" "$replacement_title" "gnulinux-advanced-$boot_device_id>gnulinux-$version-$type-$boot_device_id")"
	fi
      done
      if [ x"$is_first_entry" != xtrue ]; then
	  echo '}'
      fi
      echo "$title_correction_code"
    ;;
    macosx)
      OSXUUID="`${grub_probe} --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
      osx_entry xnu_kernel 32
      osx_entry xnu_kernel64 64
    ;;
    hurd)
      found_other_os=1
      onstr="$(gettext_printf "(on %s)" "${DEVICE}")"
      cat << EOF
menuentry '$(echo "${LONGNAME} $onstr" | grub_quote)' --class hurd --class gnu --class os \$menuentry_id_option 'osprober-gnuhurd-/boot/gnumach.gz-false-$(grub_get_device_id "${DEVICE}")' {
EOF
      save_default_entry | sed -e "s/^/\t/"
      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
      mach_device="`echo "${grub_device}" | sed -e 's/(\(hd.*\),msdos\(.*\))/\1s\2/'`"
      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
      case "${grub_fs}" in
	*fs)	hurd_fs="${grub_fs}" ;;
	*)	hurd_fs="${grub_fs}fs" ;;
      esac
      cat << EOF
	multiboot /boot/gnumach.gz root=device:${mach_device}
	module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
			--multiboot-command-line='\${kernel-command-line}' \\
			--host-priv-port='\${host-port}' \\
			--device-master-port='\${device-port}' \\
			--exec-server-task='\${exec-task}' -T typed '\${root}' \\
			'\$(task-create)' '\$(task-resume)'
	module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
}
EOF
    ;;
    *)
      echo -n "  "
      # TRANSLATORS: %s is replaced by OS name.
      gettext_printf "%s is not yet supported by grub-mkconfig.\n" "${LONGNAME}" >&2
    ;;
  esac
done

adjust_timeout
```

---

### Post by Cavsfan on 2012-10-30
> **bogan said:**
> Hi!, Cavsfan,

Thanks again.  I am not sure what to look for in /etc/fstab, it looks much like yours except there is a entry for /home, and for some reason it also lists the Swap from the 12.10 USB, but not the one from 12.10 sdb7 [perhaps the later was not mounted].```
alan@alan-MS-7616:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
[Text deleted]
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda10 during installation
UUID=b5aab3a2-0086-4a12-9276-46bb5a615038 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda11 during installation
UUID=adc771a1-313c-47ae-8725-3c89b89bbfa2 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a74af1d9-f7f9-4453-97e7-b9e3f370dca4 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=9a74bb15-1215-4774-8419-f2908ee62d2e none            swap    sw              0       0
alan@alan-MS-7616:~$
```I  have one virgin 12.10 installation in which I deliberately did  not run Grub Customizer, so it would be 12.04.1 for which I might need  the grub files.

Presumably I will need to replace the files in  all the other installations, as they interact; as well as deleting all  the Grub Customizer files.

Chao!, bogan.

**Bogan**,
You should only have whatever is for the system you are logged into in **fstab**.
It looks like you have 2 swaps and you should only have one. If you originally set it up with / and home, you should have those 2 plus the swap file for that system.

You should also not have that [Text deleted] comment as it does not have # before it.
As I installed each additional system fstab pulled in all of the swap files and I had to edit it **gksu gedit /etc/fstab** each time.

Labelling the partition is especially helpful when you have multiple systems.
It is mentioned in 1.6 of the wiki but, here is the command:
**sudo tune2fs -L Quantal /dev/sda7**
You can probably use the files I posted above. Let me know if you need anything else.

Ciao!

---

### Post by bogan on 2012-10-31
Hi!, **Cavsfan**,

I copy/pasted the contents of /etc/fstab and Posted it, [after deleting the text paragraph to make it smaller - the  " [Text deleted]" was my addition -.

This morning after reading your two Posts, I went to /etc/fstab in all the Ubuntu installations on this computer and found most of them had 3 or 4 extra swap entries, which I deleted. 

Edit. Some of them were for partitions on HDDisks that no longer exist!

It will be interesting to see if it makes any difference.

Running the 'new command' on an OS that had not run grub Customizer worked correctly, showing all the Alternative options and partition labels. 

Could you please explain the command "[B]sudo tune2fs -L Quantal /dev/sda7" 
[/B]Where, in what file does it place the title?
Does it have to be run from each of the Os to be titled?
Will it work in the standard Grub2 +Grub Customizer set-up? or only with your system?

I guess I need to study your Wiki in more detail.

Chao!,** bogan**.

.

---

### Post by Cavsfan on 2012-10-31
> **bogan said:**
> Hi!, **Cavsfan**,

I copy/pasted the contents of /etc/fstab and Posted it, [after deleting the text paragraph to make it smaller - the  " [Text deleted]" was my addition -.

This morning after reading your two Posts, I went to /etc/fstab in all the Ubuntu installations on this computer and found most of them had 3 or 4 extra swap entries, which I deleted. 

Edit. Some of them were for partitions on HDDisks that no longer exist!

It will be interesting to see if it makes any difference.

Running the 'new command' on an OS that had not run grub Customizer worked correctly, showing all the Alternative options and partition labels. 

Could you please explain the command "[B]sudo tune2fs -L Quantal /dev/sda7" 
[/B]Where, in what file does it place the title?
Does it have to be run from each of the Os to be titled?
Will it work in the standard Grub2 +Grub Customizer set-up? or only with your system?

I guess I need to study your Wiki in more detail.

Chao!,** bogan**.

.

That is exactly what happened to me: each time I installed or  reinstalled a Ubuntu the fstab for that installation would contain the  old original swap file, 
the new one and all of the swap files from every  other Ubuntu on my machine.

This is why I thought it necessary to add that info in 1.7 of the wiki.

The label command **drs305** also gave me. It makes partitions easier to identify rather than looking at a UUID.
Here his my output of **sudo blkid**:
```
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Lucid" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" 
/dev/sda3: UUID="2a80f59e-e7c3-418e-aab2-ab5d19255a2f" TYPE="swap" 
/dev/sda5: LABEL="Precise" UUID="3b8b1954-24e6-4a5e-9074-70a1a94ed4be" TYPE="ext4" 
/dev/sda6: UUID="82c51b29-023f-4964-99b6-67b45a49527f" TYPE="swap" 
/dev/[COLOR=Red]sda7[/COLOR]: LABEL="[COLOR=Red]Quantal[/COLOR]" UUID="b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a" TYPE="ext4" 
/dev/sda8: UUID="69ac3efc-8a8a-4056-89e0-59bb81c2f468" TYPE="swap" 
/dev/sda9: LABEL="Lucid-Generic" UUID="109c11d0-71e3-41a4-87da-9e81535499a5" TYPE="ext4" 
/dev/sda10: UUID="24aa8c8b-53dc-4ecc-852b-ff2c25c8b342" TYPE="swap" 
/dev/sda11: LABEL="Precise-Generic" UUID="50104efb-d918-45a9-985e-a70c60e87ac0" TYPE="ext4" 
/dev/sda12: UUID="139390a6-2fe1-4ff2-b650-88ae3b0586c1" TYPE="swap" 
/dev/sda13: UUID="580e8c62-78ce-44a2-93e3-ccebd37c3acc" TYPE="ext4" LABEL="Quantal-Generic" 
/dev/sda14: UUID="ec3048b8-c644-435a-93bb-08bb4975d0db" TYPE="swap" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs" 
```As you can see Quantal is installed on /dev/sda7 and the above command was used to add the label.
Since it must be run as sudo, it can be run from any installation.

Example: sudo tune2fs -L {label} {devicename}.

So, when I login to Lucid for example, I see a partition (drive) named Precise, Quantal, etc.
It would probably just show the UUID otherwise. Which would make it a lot more difficult to identify.

---

### Post by bogan on 2012-10-31
Hi!, **Cavsfan**,

WoW! "**sudo tune2fs -L Quantal /dev/sda7" ** looks like just what I need, the problem with duplicates is made worse because they just say: eg"Ubuntu 12.10 (12.10)", and the only way to know which of three 12.10s on the computer, each refer to, is to use 'e' edit in the Grub Menu and check out the 'hd1:msdos7' entry in the script.

Similarly in Grub Customizer, there is no telling which is which, as the entries do not stay in the same order in the menu.

One more question: in: 'sudo tune2fs -L {label} {devicename}', can the 'label' have spaces in it? & if so, must the label be in quotes? For instance: "Quantal on USB". Or should I add a hyphen as you have used?

I do not think I need the Grub files, as when Grub Customer replaces them with Proxy versions, the originals are saved in a 'proxifiedScripts' folder, but without their numbers.

At the moment, things are not going well: the USB 12.10 with no GC, which previously was exempt from the duplicates problem, has suddenly produced two duplicates in its own grub menu, and two duplicates of its entries have appeared in the grub menu of my main Ubuntu OS: Whilst the grub menu of 11.10 has no less than 24 entries, where there should only be seven [ or 12 with recoveries] and my main OS had 34!.

For the moment I have fixed things by editing /boot/grub/grub.cfg in my main OS, but of course, that will not survive a kernal update or update-grub.

Sorry to be such a persistent nuisance.

Chao!,** bogan**.

---

### Post by Cavsfan on 2012-10-31
> **bogan said:**
> Hi!, **Cavsfan**,

WoW! "**sudo tune2fs -L Quantal /dev/sda7" ** looks like just what I need, the problem with duplicates is made worse because they just say: eg"Ubuntu 12.10 (12.10)", and the only way to know which of three 12.10s on the computer, each refer to, is to use 'e' edit in the Grub Menu and check out the 'hd1:msdos7' entry in the script.

Similarly in Grub Customizer, there is no telling which is which, as the entries do not stay in the same order in the menu.

One more question: in: 'sudo tune2fs -L {label} {devicename}', can the 'label' have spaces in it? & if so, must the label be in quotes? For instance: "Quantal on USB". Or should I add a hyphen as you have used?

I do not think I need the Grub files, as when Grub Customer replaces them with Proxy versions, the originals are saved in a 'proxifiedScripts' folder, but without their numbers.

At the moment, things are not going well: the USB 12.10 with no GC, which previously was exempt from the duplicates problem, has suddenly produced two duplicates in its own grub menu, and two duplicates of its entries have appeared in the grub menu of my main Ubuntu OS: Whilst the grub menu of 11.10 has no less than 24 entries, where there should only be seven [ or 12 with recoveries] and my main OS had 34!.

For the moment I have fixed things by editing /boot/grub/grub.cfg in my main OS, but of course, that will not survive a kernal update or update-grub.

Sorry to be such a persistent nuisance.

Chao!,** bogan**.

I think the label command will work with spaces if you put quotes around the text. I would just use **sudo tune2fs -L "Quantal on USB" /dev/sda7** and that will work.
As a matter of fact I believe the quotes work better.
I just changed all my generic installs with spaces in between. And that is how they appear when I click on Places.
```

/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Lucid" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" 
/dev/sda3: UUID="2a80f59e-e7c3-418e-aab2-ab5d19255a2f" TYPE="swap" 
/dev/sda5: LABEL="Precise" UUID="3b8b1954-24e6-4a5e-9074-70a1a94ed4be" TYPE="ext4" 
/dev/sda6: UUID="82c51b29-023f-4964-99b6-67b45a49527f" TYPE="swap" 
/dev/sda7: LABEL="Quantal" UUID="b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a" TYPE="ext4" 
/dev/sda8: UUID="69ac3efc-8a8a-4056-89e0-59bb81c2f468" TYPE="swap" 
/dev/sda9: LABEL="Lucid Generic" UUID="109c11d0-71e3-41a4-87da-9e81535499a5" TYPE="ext4" 
/dev/sda10: UUID="24aa8c8b-53dc-4ecc-852b-ff2c25c8b342" TYPE="swap" 
/dev/sda11: LABEL="Precise Generic" UUID="50104efb-d918-45a9-985e-a70c60e87ac0" TYPE="ext4" 
/dev/sda12: UUID="139390a6-2fe1-4ff2-b650-88ae3b0586c1" TYPE="swap" 
/dev/sda13: UUID="580e8c62-78ce-44a2-93e3-ccebd37c3acc" TYPE="ext4" LABEL="Quantal Generic" 
/dev/sda14: UUID="ec3048b8-c644-435a-93bb-08bb4975d0db" TYPE="swap" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs"
```Never used the grub-customizer myself. I have always preferred my way which **ranch hand** taught me.
He is a pretty smart guy with Ubuntu and Linux!

Other than making a couple mods to 2-3 files the big thing is **/etc/grub.d/06_custom** (saved from 40_custom).

Here is the contents of my 06_custom file in Quantal and it displays what I want it to display with no exceptions.

```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04, Quantal Quetzal 12.10 and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Lycid Lynx 10.04" {
    set root=([COLOR=Red]hd0,2[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda2[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Lycid Lynx 10.04 (Recovery Mode)" {
    set root=([COLOR=Red]hd0,2[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda2[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Lycid Lynx Generic 10.04" {
    set root=([COLOR=Red]hd0,9[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda9[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Lycid Lynx Generic 10.04 (Recovery Mode)" {
    set root=([COLOR=Red]hd0,9[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda9[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04" {
    set root=([COLOR=Red]hd0,5[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda5[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=([COLOR=Red]hd0,5[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda5[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Precise Pangolin Generic 12.04" {
    set root=([COLOR=Red]hd0,11[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda11[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin Generic 12.04 (Recovery Mode)" {
    set root=([COLOR=Red]hd0,11[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda11[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10" {
    set root=([COLOR=Red]hd0,7[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda7[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
    set root=([COLOR=Red]hd0,7[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda7[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Quantal Quetzal Generic 12.10" {
    set root=([COLOR=Red]hd0,13[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda13[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal Generic 12.10 (Recovery Mode)" {
    set root=([COLOR=Red]hd0,13[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=Red]sda13[/COLOR] ro single
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='([COLOR=Red]hd0,1[/COLOR])'
    search --no-floppy --fs-uuid --set [COLOR=Red]1CFC7A8DFC7A60C6[/COLOR]
    chainloader +1
}
```Other than changing what is in red, you would just change what is between the quotes to whatever you want 
because you will be the only one that sees it.

Then making it executable **sudo chmod +x /etc/grub.d/06_custom** and 
then **sudo update-grub** of course.

And you are not a nuisance! You *wouldn't* believe how long it took me to work up the courage to make these changes to my machine!
But, I am glad I did. You see my screen above and they are the same on all three installs. The **06_custom** file above matches what is displayed on my pictures above.
Since I am leaving the generic installs untouched but, they still are bootable from where my grub is installed.
I have customized all three Ubuntus for the wiki but, I have my boot grub2 on Lucid which is on a primary partition.

EDIT: In answer to your question, I would get all the grub files back to their original state before I tried my method. 
I don't think my method will work on files that have been customized by grub-customizer.
If you need anything other than what I already posted above just let me know.

---

### Post by Cavsfan on 2012-10-31
After you get all of your grub files back to default.

First enter this in terminal to create the font. You will see errors but, it will still work:

```
sudo grub-mkfont --output=/boot/grub/DejaVuSansMono.pf2 \
--size=24 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf

```Here are my files on Quantal with the changes/additions in red:
**gksu gedit /etc/default/grub**
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=[COLOR=Red]12[/COLOR]
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=[COLOR=Red]60[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[COLOR=Red]GRUB_FONT=/boot/grub/DejaVuSansMono.pf2 [/COLOR]

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'[COLOR=Red]
GRUB_GFXMODE=1920x1200-24[/COLOR]

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```The red 12 indicates the default which is the 13 line down (windows 7) for my wife.
```

cavsfan@cavsfan-desktop:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0    menuentry "Lucid Lynx" {
     1    menuentry "Lucid Lynx (Recovery Mode)" {
     2    menuentry "Lucid Lynx Generic" {
     3    menuentry "Lucid Lynx Generic (Recovery Mode)" {
     4    menuentry "Precise Pangolin 12.04" {
     5    menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     6    menuentry "Precise Pangolin Generic 12.04" {
     7    menuentry "Precise Pangolin 12.04 Generic (Recovery Mode)" {
     8    menuentry "Quantal Quetzel 12.10" {
     9    menuentry "Quantal Quetzel 12.10 (Recovery Mode)" {
    10    menuentry "Quantal Quetzel Generic 12.10" {
    11    menuentry "Quantal Quetzel 12.10 Generic (Recovery Mode)" {
    [COLOR=Red]12[/COLOR]    menuentry "Windows 7" {
```I have a 60 second timeout because I am slow sometimes and need that time. Then there is my screen resolution 1920x1200-24 (24 is color bit depth).
Then there is also the font line that has to be added.

You must [COLOR=Red]move[/COLOR] 1 picture that is the resolution of your screen into **/boot/grub/**.
**sudo cp picture.jpg /boot/grub/** The picture will not display unless it is precisely as specified by [COLOR=Red]GRUB_GFXMODE[/COLOR] above.

The following is dependant on finding that picture in that directory. It can be a .png .jpg .tga or .jpeg picture.

**/etc/grub.d/05_debian_theme**
(just 2 lines added after line 108:)

```
#!/bin/sh
set -e

# grub-mkconfig helper script.
# Copyright (C) 2010  Alexander Kurtz <kurtz.alex@googlemail.com>
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

# Include the GRUB helper library for grub-mkconfig.
. /usr/share/grub/grub-mkconfig_lib

# We want to work in /boot/grub/ only.
test -d /boot/grub; cd /boot/grub

# Set the location of a possibly necessary cache file for the background image.
# NOTE: This MUST BE A DOTFILE to avoid confusing it with user-defined images.
BACKGROUND_CACHE=".background_cache"

set_default_theme(){
    # Set a monochromatic theme for Ubuntu.
    echo "${1}set menu_color_normal=white/black"
    echo "${1}set menu_color_highlight=black/light-gray"

    if [ -e /lib/plymouth/themes/default.grub ]; then
        sed "s/^/${1}/" /lib/plymouth/themes/default.grub
    fi
}

module_available(){
    local module
    for module in "${1}.mod" */"${1}.mod"; do
        if [ -f "${module}" ]; then
            return 0
        fi
    done
    return 1
}

set_background_image(){
    # Step #1: Search all available output modes ...
    local output
    for output in ${GRUB_TERMINAL_OUTPUT}; do
        if [ "x$output" = "xgfxterm" ]; then
            break
        fi
    done

    # ... and check if we are able to display a background image at all.
    if ! [ "x${output}" = "xgfxterm" ]; then
        return 1
    fi

    # Step #2: Check if the specified background image exists.
    if ! [ -f "${1}" ]; then
        return 2
    fi

    # Step #3: Search the correct GRUB module for our background image.
    local reader
    case "${1}" in
        *.jpg|*.JPG|*.jpeg|*.JPEG) reader="jpeg";;
        *.png|*.PNG) reader="png";;
        *.tga|*.TGA) reader="tga";;
        *) return 3;; # Unknown image type.
    esac

    # Step #4: Check if the necessary GRUB module is available.
    if ! module_available "${reader}"; then
        return 4
    fi

    # Step #5: Check if GRUB can read the background image directly.
    # If so, we can remove the cache file (if any). Otherwise the backgound
    # image needs to be cached under /boot/grub/.
    if is_path_readable_by_grub "${1}"; then
        rm --force "${BACKGROUND_CACHE}.jpeg" \
            "${BACKGROUND_CACHE}.png" "${BACKGROUND_CACHE}.tga"
    elif cp "${1}" "${BACKGROUND_CACHE}.${reader}"; then
        set -- "${BACKGROUND_CACHE}.${reader}" "${2}" "${3}"
    else
        return 5
    fi

    # Step #6: Prepare GRUB to read the background image.
    if ! prepare_grub_to_access_device "`${grub_probe} --target=device "${1}"`"; then
        return 6
    fi

    # Step #7: Everything went fine, print out a message to stderr ...
    echo "Found background image: ${1}" >&2

    # ... and write our configuration snippet to stdout. Use the colors
    # desktop-base specified. If we're using a user-defined background, use
    # the default colors since we've got no idea how the image looks like.
    # If loading the background image fails, use the default theme.
    echo "insmod ${reader}"
    echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
    [COLOR=Red]echo " set color_normal=cyan/black"
    echo " set color_highlight=light-red/black"[/COLOR]
    if [ -n "${2}" ]; then
        echo "  set color_normal=${2}"
    fi
    if [ -n "${3}" ]; then
        echo "  set color_highlight=${3}"
    fi
    if [ -z "${2}" ] && [ -z "${3}" ]; then
        echo "  true"
    fi
    echo "else"
    set_default_theme "  "
    echo "fi"
}

# Earlier versions of grub-pc copied the default background image to /boot/grub
# during postinst. Remove those obsolete images if they haven't been touched by
# the user. They are still available under /usr/share/images/desktop-base/ if
# desktop-base is installed.
while read checksum background; do
    if [ -f "${background}" ] && [ "x`sha1sum "${background}"`" = "x${checksum}  ${background}" ]; then
        echo "Removing old background image: ${background}" >&2
        rm "${background}"
    fi
done <<EOF
648ee65dd0c157a69b019a5372cbcfea4fc754a5  debian-blueish-wallpaper-640x480.png
0431e97a6c661084c59676c4baeeb8c2f602edb8  debian-blueish-wallpaper-640x480.png
968ecf6696c5638cfe80e8e70aba239526270864  debian-blueish-wallpaper-640x480.tga
11143e8c92a073401de0b0fd42d0c052af4ccd9b  moreblue-orbit-grub.png
d00d5e505ab63f2d53fa880bfac447e2d3bb197c  moreblue-orbit-grub.png
f5b12c1009ec0a3b029185f6b66cd0d7e5611019  moreblue-orbit-grub.png
EOF

# Include the configuration of desktop-base if available.
if [ -f "/usr/share/desktop-base/grub_background.sh" ]; then
    . "/usr/share/desktop-base/grub_background.sh"
fi

# First check whether the user has specified a background image explicitly.
# If so, try to use it. Don't try the other possibilities in that case
# (#608263).
if [ -n "${GRUB_BACKGROUND+x}" ]; then
    set_background_image "${GRUB_BACKGROUND}" || set_default_theme
    exit 0
fi

# Next search for pictures the user put into /boot/grub/ and use the first one.
for background in *.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga *.TGA; do
    if set_background_image "${background}"; then
        exit 0
    fi
done

# Next try to use the background image and colors specified by desktop-base.
if set_background_image "${WALLPAPER}" "${COLOR_NORMAL}" "${COLOR_HIGHLIGHT}"; then
    exit 0
fi

# Finally, if all of the above fails, use the default theme.
set_default_theme
```The custom menu entries will display at the top and after you are comfortable that they work 
then you can make the rest of the files unexecutable as in 1.5 of the wiki.

---

### Post by bogan on 2012-11-01
Hi!, **Cavsfan**,

I must have misunderstood you, as I thought using the "tune2fs -L" command would change the entry names in grub menu [ & in grub Customizer]. Big disappointment!!

The changes do show up in 'blkid' and in the left-hand Bookmarks list in Desktop Manager, - which is a great advantage - and also in Gparted, but strangely do not show up in Windows Disk manager.

I have reverted all the installations in this computer  which had grub Customer and the results are that the grub menus now show the entries I expect, without any duplicates.

The duplicates are still there, however, and the 'new' grep menu entry command shows them in addition to those that actually display. which is rather disconcerting. 
EDIT: I was wrong, the duplicates are there, but they are hidden in the Advanced Options sub-menus.

I have not altered the /etc/default/grub files and my grub backgrounds images are unchanged. Nor have I actually removed the Grub Customizer installlations, I have done just what Daniel Richter instructed in the GC 'How To'.

So I am all ready to take the plunge.

Chao!, bogan.

---

### Post by bogan on 2012-11-02
Hi!, **Cavsfan**,

1. Major query on your Wiki,"Making the custom Grub2 Menu entries", versions after Lucid. 
For Lucid this does not apply as there is no 'echo' line, but it emphasises the first 5 lines must not be changed.

"Editing /etc/grub.d/40_custom:" section.
Instructions say: "first entry copied & pasted below the 5 lines above."

Example shows the 'echo' line as line2 between'#/bin/sh' and 'exec tail -n +3 $0'

2. Which UIID to use for Windows?
Your 'blkid' shows a single ntfs entry without a label, and the text says "You can see Windows is on sda1," whereas mine shows two entries, the first labeled "System Reseved" and the second "Boot".

Though Windows is actually on the Boot partition I checked the existing Grub menu script and the Windows entry shows the UUID of System Reserved being set. So I have done the same, as I understand it, the Windows bootloader is on the reserved partition, so that is what mus be set.

AFAIK. The separate System partition was introduced with Windows Vista, and is standard, perhaps not in XP.

3. Minor point: The illustration of blkid output with labels, is before the instruction for putting labels in. I found this very confusing at first reading, as my blkid showed partition labels yours did not, and no Linux labels, which yours displayed.

When I first tried the 'tune2fs -L' command I got a message about 'no magic number, could not find file system', not labeled.

All changes made except making the grub files not executeable and I am about to reboot and see what the result is.

Edit: The result was a disaster! This is what I got fromsudo update-grub:```
 root@alan-MS-7616:~# update-grub
Generating grub.cfg ...
Found background: /home/alan/Pictures/Lake_mapourika_NZ.tga
Found background image: /home/alan/Pictures/Lake_mapourika_NZ.tga
Found linux image: /boot/vmlinuz-3.5.0-18-generic
Found initrd image: /boot/initrd.img-3.5.0-18-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 12.10 (12.10) on /dev/sda10
Found Windows Recovery Environment (loader) on /dev/sda4
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda5
Found Ubuntu 12.10 (12.10) on /dev/sdb7
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 127
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.done
root@alan-MS-7616:~# 
```I am attaching my 06_custom file, I cannot see anything wrong other than that the (hd0,1) in the Windows entry is between single quotes as your is. [ I commented out the 'echo' line after this error.]

*How can I tell what file the error in line 127 was found?*
Edit2: Line 127 in /boot/grub/grub.cfg was the 'echo' line, with it commented out, sudo update-grub ran as above, but without errors.

Chao!, [B]bogan.

[/B]The file would not upload, said: 'invalid file'**: **maybe  permissions were wrong- so here it is:```
 #!/bin/sh
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
# echo "Adding Ubuntu Oneiric 10.10, Precise 12.04.1, Quantal 12.10 and Windows 7" >&2
menuentry "Quantal 12.10 USB sdc2" {
    set root=(hd2,2)
        linux /vmlinuz root=/dev/sdc2 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal 12.10 USB sdc2 (Recovery)" {
    set root=(hd2,2)
        linux /vmlinuz root=/dev/sdc2 ro single
        initrd /initrd.img
}
menuentry "Windows 7 on sda2" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set CC9240F39240E394
    chainloader +1
}
menuentry "Quantal 12.10 sda10" {
    set root=(hd0,10)
        linux /vmlinuz root=/dev/sda10 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal 12.10 sda10 (Recovery)" {
    set root=(hd0,10)
        linux /vmlinuz root=/dev/sda10 ro single
        initrd /initrd.img
}
menuentry "Quantal 12.10 EXT sdb7" {
    set root=(hd1,7)
        linux /vmlinuz root=/dev/sdb7 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal 12.10 EXT sdb7 (Recovery)" {
    set root=(hd1,7)
        linux /vmlinuz root=/dev/sdb7 ro single
        initrd /initrd.img
}
menuentry "Precise 11.10 sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise 11.10 sda5 (Recovery)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}  

```

---

### Post by bogan on 2012-11-02
Hi!, **Cavsfan**,

First the good news: The new menu entries are AOK.

The new Windows menu entry works correctly, no error messages and no problems.

The bad news is: None of the Ubuntu entries work.

The sda10 & sda5 entries both  say: 'No such partition', the others say: '"/vmlinuz not found".
Edit: Altering it to "/boot/vmlinuz" did not help, nor did adding the suffix '-3.5.0-18-generic'.
All the Ubuntu entries say: "Error: need to load the kernal first"

I am going to try altering (hd0,5) to (hd0,msdos5) & enclosing it in single quotes like the Windows entry.
Edit: neither changed anything.

Any advice earnestly awaited.

My guess is the Syntax error was because the alteration to the tail line was for the echo line to be line 2, or is it in the echo line itself.
Chao!,** bogan**.

---

### Post by Cavsfan on 2012-11-03
> **bogan said:**
> 
```
 #!/bin/sh
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
[COLOR=Red]#[/COLOR] echo "Adding Ubuntu Oneiric 10.10, Precise 12.04.1, Quantal 12.10 and Windows 7" >&2
menuentry "Quantal 12.10 USB sdc2" {
    set root=(hd2,2)
        linux /vmlinuz root=/dev/sdc2 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal 12.10 USB sdc2 (Recovery)" {
    set root=(hd2,2)
        linux /vmlinuz root=/dev/sdc2 ro single
        initrd /initrd.img
}
menuentry "Windows 7 on sda2" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set CC9240F39240E394
    chainloader +1
}
menuentry "Quantal 12.10 sda10" {
    set root=(hd0,10)
        linux /vmlinuz root=/dev/sda10 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal 12.10 sda10 (Recovery)" {
    set root=(hd0,10)
        linux /vmlinuz root=/dev/sda10 ro single
        initrd /initrd.img
}
menuentry "Quantal 12.10 EXT sdb7" {
    set root=(hd1,7)
        linux /vmlinuz root=/dev/sdb7 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal 12.10 EXT sdb7 (Recovery)" {
    set root=(hd1,7)
        linux /vmlinuz root=/dev/sdb7 ro single
        initrd /initrd.img
}
menuentry "Precise 11.10 sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise 11.10 sda5 (Recovery)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}  

```

Enter **gksu gedit /etc/grub.d/06_custom** and remove the red # above and then enter **sudo update-grub**  then the file should look similar to the one below:

```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04, Quantal Quetzal 12.10 and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Lycid Lynx 10.04" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
```

The **exec tail -n +4 $0** says to execute the 4th line from the top which should be a menuentry line.
Since your echo command is commented out, the 4th line in your file is the set statement after the menuentry.

See if that fixes it. It should.

---

### Post by bogan on 2012-11-03
Hi!,** Cavsfan**,

You Posted: > Enter **gksu gedit /etc/grub.d/06_custom** and remove the red # above and then enter **sudo update-grub**  then the file should look similar to the one below:I did as you suggested, and, as I expected, that brought back the Syntax error in Line 127.;
The echo line copied from the Wiki is : 
> **echo "Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04, Quantal Quetzal 12.10 and Windows 7"[COLOR=Red] >&2[/COLOR] **Whereas from your Post is: 
> echo [COLOR=Red]**1>&2 **[/COLOR]"Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04, Quantal Quetzal 12.10 and Windows 7"Adding the '1' to the last phrase, to make it:"xxxx Windows 7" 1>&2", still gave the Syntax error. 
Placing the echo line as line 2 and putting the '1>&2' after 'echo', deleting the last phrase, got rid of the Syntax error.

Despite the apparent logic of your  explanation, that is not what happened. The first entry was, and  still is, correct.

At present, after the above changes, the part of /boot/grub/grub.cfg that is produced is: ```
### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above. 
menuentry "Quantal 12.10 USB sdc2" {
    set root='hd2,2'
        linux /vmlinuz root=/dev/sdc2 ro quiet splash
        initrd /initrd.img
}
```Before, with the echo line commented out after the three text lines, it was printed out, but the first line " This file xxxxxx" was ommited.; note that the content of the echo line is not reproduced

[COLOR=RoyalBlue]The menu display remains the same andnone of the Ubuntu entries will  work, behaving exactly as described in my last Post.[/COLOR]

Chao!, **bogan**.

---

### Post by bogan on 2012-11-03
Hi!, **Cavsfan**,

I should, perhaps, have mentioned that I have, for safety's sake, conducted what I regard as an experiment, in the 12.10 installation in a SanDisk USB, which has its own Grub active when booted to USB from the Bios boot menu.

Of course, when the USB 12.10 is booted from the grub menu of my primary OS, sda10, the USB Grub menu also appears.

I did not see that this matters  - and still do not see how it should make any difference - but clearly it does, because........

I have copy/pasted the 06_custom file from the USB, unchanged, to /etc/grub.d of sd10 and, Lo & Behold !!, all the entries work.

The only queer thing is that the Recovery entries boot directly to a root prompt without displaying a Recovery menu.

So the question is: WHY?? and, What alterations are needed to get the USB Ubuntu to recognise the partitions in sda, and find the vmlinuz & initrd.img files? - which are there in /boot/ of the USB, as well as all the other OS's.

Chao!,** bogan**.

---

### Post by Cavsfan on 2012-11-03
> **bogan said:**
> Hi!, **Cavsfan**,

I should, perhaps, have mentioned that I have, for safety's sake, conducted what I regard as an experiment, in the 12.10 installation in a SanDisk USB, which has its own Grub active when booted to USB from the Bios boot menu.

Of course, when the USB 12.10 is booted from the grub menu of my primary OS, sda10, the USB Grub menu also appears.

I did not see that this matters  - and still do not see how it should make any difference - but clearly it does, because........

I have copy/pasted the 06_custom file from the USB, unchanged, to /etc/grub.d of sd10 and, Lo & Behold !!, all the entries work.

The only queer thing is that the Recovery entries boot directly to a root prompt without displaying a Recovery menu.

So the question is: WHY?? and, What alterations are needed to get the USB Ubuntu to recognise the partitions in sda, and find the vmlinuz & initrd.img files? - which are there in /boot/ of the USB, as well as all the other OS's.

Chao!,** bogan**.

I thought that maybe you had grub on the USB drive and maybe that would not work and I do not expect that it will work.
Did you install grub on sd10 **sudo grub-install /dev/sd10** ?

For this to work, you have to have grub installed along with the picture and everything else on the same partition.

The Wiki assumes that you have untouched grub files and that you copy and paste *exactly* as stated in the wiki.
Then when you enter **sudo update-grub** it changes the files a bit as you see them. Like when you look at **06_custom**; it is no longer like it says in the wiki because Grub2 has **changed** it.
My Quantal install is somewhat finicky when I boot into recovery mode also. A lot of times it just hangs and I have to press the reset button. 
I have had to boot up a couple of times to get it to work correctly. Not really sure when the last time I got into Quantal Recovery but, it should work.

On Lucid and Precise Recover work no problem - just Quantal doesn't always work. 
I am not real fond of Quantal but, I keep it for the Grub2 version 2.00 and to support it for the wiki.

Here is my entire output of **sudo grub-mkconfig** on Quantal:

```
cavsfan@cavsfan-MS-7529:~$ sudo grub-mkconfig
[sudo] password for cavsfan: 
Generating grub.cfg ...
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="12"

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

insmod part_msdos
insmod ext2
set root='hd0,msdos7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a
else
  search --no-floppy --fs-uuid --set=root b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a
fi
if loadfont /boot/grub/DejaVuSansMono.pf2 ; then
  set gfxmode=1920x1200-24
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=60
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='hd0,msdos7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a
else
  search --no-floppy --fs-uuid --set=root b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a
fi
Found background image: nature-hd-wallpaper_1920x1200.jpg
insmod jpeg
if background_image /boot/grub/nature-hd-wallpaper_1920x1200.jpg; then
 set color_normal=cyan/black
 set color_highlight=light-red/black
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
Adding Ubuntu Lucid Lynx 10.04, Precise Pangolin 12.04, Quantal Quetzal 12.10 and Windows 7
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Lycid Lynx 10.04" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
menuentry "Lycid Lynx 10.04 (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro single
        initrd /initrd.img
}
menuentry "Lycid Lynx Generic 10.04" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash
        initrd /initrd.img
}
menuentry "Lycid Lynx Generic 10.04 (Recovery Mode)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro single
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}
menuentry "Precise Pangolin Generic 12.04" {
    set root=(hd0,11)
        linux /vmlinuz root=/dev/sda11 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin Generic 12.04 (Recovery Mode)" {
    set root=(hd0,11)
        linux /vmlinuz root=/dev/sda11 ro single
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro single
        initrd /initrd.img
}
menuentry "Quantal Quetzal Generic 12.10" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal Generic 12.10 (Recovery Mode)" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro single
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```As you can see that does not resemble my **06_custom** file at all.

---

### Post by bogan on 2012-11-03
Hi!, **Cavsfan**,

You Posted: > The Wiki assumes that you have untouched grub files and that you copy and paste exactly as stated in the wiki.
Then when you enter sudo update-grub it changes the files a bit as you see them. Like when you look at 06_custom; it is no longer like it says in the wiki because Grub2 has changed it. And: > As you can see [ in output of **sudo grub-mkconfig** ]that does not resemble my **06_custom** file at all.     We do not seem to be on the same wavelength.

My Grub files [ in both sda10 & sdc2 } are certainly not untouched but I don't think the alterations in any way affect the operation of your system. I did "copy and paste exactly as stated in the wiki."

I only altered the 'Labels' and 'hdx,x' and 'sdxX' entries. The error in the 'echo' line is in the Wiki.

Running 'sudo update-grub' has not altered the contents of my 06_custom file at all.

As far as I can see, the part of 'sudo grub-mkconfig' concerned, is exactly the same as the 06_custom file in Wiki, other than it has many more entries. The same thing applies to the relevant entries in /boot/grub/grub.cfg. > Did you install grub on sd10 **sudo grub-install /dev/sd10** ? I did not need to, grub2 was already installed in sda10 as my main OS.

What I do not understand is that from sda10 your system can find Windows, sda5, sdb7, & sdc2, in Internal HDD, External sata/usb HDD, & Sandisk USB; and from the USB sdc2 can find Windows, & sdb7, but not sda10 or sda5.

Are you saying, in effect, that there is no way to get your system to work from a bootable external drive with its own grub2 installed?.

Chao!,** bogan.**

---

### Post by Cavsfan on 2012-11-03
> **bogan said:**
> Hi!, **Cavsfan**,

You Posted:  And: We do not seem to be on the same wavelength.

My Grub files are certainly not untouched but I don't think the alterations in any way affect the operation of your system. I did "copy and paste exactly as stated in the wiki."

I only altered the 'Labels' and 'hdx,x' and 'sdxX' entries. The error in the 'echo' line is in the Wiki.

Running 'sudo update-grub' has not altered the contents of my 06_custom file at all.

As far as I can see, the part of 'sudo grub-mkconfig' concerned, is exactly the same as the 06_custom file in Wiki, other than it has many more entries. The same thing applies to the relevant entries in /boot/grub/grub.cfg.  I did not need to, grub2 was already installed in sda10 as my main OS.

What I do not understand is that from sda10 your system can find Windows, sda5, sdb7, & sdc2, in Internal HDD, External sata/usb HDD, & Sandisk USB; and from the USB sdc2 can find Windows, & sdb7, but not sda10 or sda5.

Are you saying, in effect, that there is no way to get your system to work from a bootable external drive with its own grub2 installed?.

Chao!,** bogan.**

You were correct about the echo line and I have fixed the Wiki.
Check it out now. I believe I have it correct.

I have no idea if one could add this customization to a USB drive but, I also don't understand why you would want to.

I really prefer to have my grub installed on a primary partition instead of logical ones let alone if I had a USB drive connected.
Grub-rescue is not something I like to see.

I have my grub installed on Lucid and will keep it there except to test until I upgrade that to Precise but, I have until April '13 to do so.

---

### Post by Cavsfan on 2012-11-03
**Bogan**, I just tried Quantal Recovery on my custom system and it did not go any where. It just displayed a bunch of stuff and stopped.

So, I went to my Quantal generic where the grub is untouched and installed grub there.

I booted into Recovery after that and the menu did come up but, when I selected Failsafe mode, it said something about the files would 
be read only and mounted according to fstab and then stopped. It would not do any thing so I had to press reset. 
While there I double checked fstab and it was correct.
Luckily I made it back into my Lucid install to install grub.

So, this custom grub in Quantal does not permit failsafe mode and apparently neither does generic Quantal.

I didn't try any other options but that must be a bug in Quantal Recovery.

Edit: You can also label partitions in GParted by clicking on the partition and then label. 

**Ciao**!

---

### Post by bogan on 2012-11-04
Hi!, **Cavsfa**n,

Thanks for your last two responses, you Posted:>  I have no idea if one could add this customization to a USB drive but, I also don't understand why you would want to.The USB is my emergency backup, its Grub has entries for not only the OS's on this computer but also my other desktop.

SO, if any of the horrifying crashes I read about in the Forum, occurred  to me - so far, at least, I have never had one that prevented me accessing at least one of the Ubuntu OS's - I can do so by Bios booting to the USB in either computer.

As long as Grub Customizer was working OK - despite the nuisance of duplicate entries - I was able to rename the entries in the menu so I knew which of ten entries was which.

With GC messing up things in 12.10 and applying name changes I made to the wrong entries, the arrangement, both on my main OS, sda10, and the USB became chaotic, with up to 24 entries all saying: "Ubuntu  12.10 ( 12.10)" without any sdaX mention.

That is why I decided to try your system, so I could have sensible, meaning-full labels, without having to re-edit '/boot/grub/grub.cfg' every time anything altered, or 'update-grub' was run.

The normal 12.10 boot to Recovery goes to a drop down menu in Read only mode,; the option to drop to a terminal goes to a root prompt requiring a root password.

With the two  I tried in the custom entries, they went to a text display quite different to any I have previously seen, including a line that said: " system will be reset to Read/Write in the following recovery sequence" [ or words to that effect ] and then went direct to a root text terminal prompt - without needing to login or give a password -```
 service lightdm start
``` then went to the normal greeter login screen.

I will check out the other recovery boot entries and see if I get anything like you reported.

Chao!,** bogan.**

---

### Post by bogan on 2012-11-04
Hi!, **Cavsfan**,

I have tried out the recovery entries in both my main & USB Quantal OS's, both the standard & the 06_custom versions.

Without going into details I can only say there is a disconcerting unpredictability about the results.

Generally, the custom entries on the USB do not work, [  as already reported ] whilst those in the main, sda10, OS, work, also as already described, ending just after the " boot scripts.   [done]" lines with a root prompt, but no recovery menu.  On one occaision I got a momentary error message before the boot text, and on another It hung up after the " set Swap sda6" line, two lines on from the' boot script'  lines. 'Alt+ REIBUS' produced its usuall shut down messages but did not close.

The 'normal' grub menu recovery entries in both OS's ran normally to Recovery Menus and the 'Drop to root shell' options all gave root terminal prompts not requiring log-in or password. { I did not get the demand for a root password that I had had previously.}

There were several discrepancies in the exact point in the boot text dislplay at which it went to the Menu window, and in the behaviour after entering 'reboot' from the prompt. Sometimes it flashed the GUI log-in screen, or a window saying it was 'in fail safe low res', most times merely a blank screen.

But mostly it returned to the Recovery Menu window and hung there for 40 seconds or so, before breaking up and quitting.

I did not actually try the Failsafe option in the menu, but I will do so and edit this accordingly.
EDIT: The results of trying Recovery>FailSafe were complex, so I am Posting it separately.

Chao!,** bogan**.

---

### Post by stinkeye on 2012-11-04
Hi Cavsfan, 
thanks for the wiki.
Changed the plymouth background to black as well, for a much nicer boot.

---

### Post by bogan on 2012-11-04
Hi!, **Cavsfan,**

The results of trying Recovery>FailSafe were complex so I am Posting it separately.

Choosing failsafe from the 'normal', 'Ubuntu', grub menu items, in both sda10 and the USB, showed 'fsck' and its results, but then hung with a flashing cursor.

I then remembered I had seen this before, and found a workround: Press 'Ctrl+c' +'Return' and after 20 seconds or so it goes to a continued text display and then to the GUI log-in screen..

Doing the same with the 12.04.1 recovery entry, had a different result, it gave a full screen of a different text display, including 'Fatal Server error' & 'No Screen found', ending with " Server exited with error '1'" [ or some such message ] and again hung there.

Once again:   Pressing: 'Ctrl+c' + 'Return' caused it to exit to a normal GUI login screen, despite all the warnings.

I have no idea how to tell if the GUI is actually in 'FailSafe' or not, it appears quite normal to me and 'echo $DESKTOP_SESSION' gives: "ubuntu" as usual.

The other OS's, for some reason,  I was unable to test, as the recovery options are hidden in the 'Advanced Options' entry and selecting that entry, instead of showing the recovery entry, as the others did,  merely returned to a different Grub menu, still showing the 06_custom entries, but below the old grub1,99 entries, without the  'Advanced Options'.   Dont Ask!

Chao!,** bogan.**

---

### Post by Cavsfan on 2012-11-04
> **stinkeye said:**
> Hi Cavsfan, 
thanks for the wiki.
Changed the plymouth background to black as well, for a much nicer boot.

You're welcome! :) Since the custom  menuentries are now correct for grub 1.99 and 2.00 perhaps you'd like to add them.
They will initially appear at the top and if you don't like them you can just make **06_custom** unexecutable and you are back to normal. 

> **bogan said:**
> I then remembered I had seen this before, and found a workround: Press 'Ctrl+c' +'Return' and after 20 seconds or so it goes to a continued text display and then to the GUI log-in screen...

I could not successfully get into safe mode in recovery on either installation of Quantal. I don't like special work arounds for things that should just work.

As I stated I like LTS versions and just have Quantal on here for the grub version 2.00 and for the wiki.
Thanks for getting me to realize I did have that echo command incorrect in the wiki. :)

---

### Post by bogan on 2012-11-04
Hi!, Cavsfan,

This Recovery business is going from very strange to downright weird!

I mentioned that in Quantal, the Grub menu was correct with the 0_6custom entries at the top and the 'normal' grub2.00 entries, including Additional Options, for each, below.

Whilst the main OS Quantal, sda10, Additional Options entry, and some others, worked as expected when selected, showing the standard and recovery entries, [plus some duplicates]; which, when 'e' was pressed showed the correct scripts; the one for Quantal on the external HDD, sdb7, did not.

It displayed what at first sight looked like the 0_6custom entries at the top and the 'pre-grub 2.00' grub2 entries, excluding Additional Options or recovery options, for each, below; and that is what I reported.

However, on further examination, I find I missed an obvious error: all the entries - except Windows & Memtest - both new custom, and old 'normal entries, had the correct Labels, but the same suffix added: " on sdb7".

Pressing 'e' showed all the entries had scripts for sdb7 and all were of the 'normal' grub2 type, not the shortened version used in the Wiki.

Whereas the 'normal' entries mostly had the files in the last two lines identified as eg. /boot/vmlinuz-3.5.0-18-generic, in the 06_custom entries the last two lines were as in the Wiki, without the suffixes or UIID's.

Just to make things even weirder: when I selected the "Quantal sda10 on sb7" entry with 'Enter' or 'Ctrl+x' from the script, it actually booted into the Quantal on the USB. Furthermore it did so bypassing the usb's own Grub menu! 

Whereas the "Precise 12.04.1 on sb7" did boot into 12.04.1 on sb7, but in a very low-res display.

The same thing happened with sda5, all the entries had sdb5 suffixes and scripts.

Chao!, a bewildered bogan.

---

### Post by Cavsfan on 2012-11-05
> **bogan said:**
> Hi!, Cavsfan,

This Recovery business is going from very strange to downright weird!

I mentioned that in Quantal, the Grub menu was correct with the 0_6custom entries at the top and the 'normal' grub2.00 entries, including Additional Options, for each, below.

Whilst the main OS Quantal, sda10, Additional Options entry, and some others, worked as expected when selected, showing the standard and recovery entries, [plus some duplicates]; which, when 'e' was pressed showed the correct scripts; the one for Quantal on the external HDD, sdb7, did not.

It displayed what at first sight looked like the 0_6custom entries at the top and the 'pre-grub 2.00' grub2 entries, excluding Additional Options or recovery options, for each, below; and that is what I reported.

However, on further examination, I find I missed an obvious error: all the entries - except Windows & Memtest - both new custom, and old 'normal entries, had the correct Labels, but the same suffix added: " on sdb7".

Pressing 'e' showed all the entries had scripts for sdb7 and all were of the 'normal' grub2 type, not the shortened version used in the Wiki.

Whereas the 'normal' entries mostly had the files in the last two lines identified as eg. /boot/vmlinuz-3.5.0-18-generic, in the 06_custom entries the last two lines were as in the Wiki, without the suffixes or UIID's.

Just to make things even weirder: when I selected the "Quantal sda10 on sb7" entry with 'Enter' or 'Ctrl+x' from the script, it actually booted into the Quantal on the USB. Furthermore it did so bypassing the usb's own Grub menu! 

Whereas the "Precise 12.04.1 on sb7" did boot into 12.04.1 on sb7, but in a very low-res display.

The same thing happened with sda5, all the entries had sdb5 suffixes and scripts.

Chao!, a bewildered bogan.

Bogan, have you taken a look at the fstab on each install. When several of my fstabs had multiple entries of the swap file it displayed the normal grub menu as if everything was installed on sda2 and when I chose Lucid (which is on sda2) it booted into a low-res display.
It seems that grub reads fstab.

I am thinking that the problems you mention are limited to Quantal. I never have had any problems whatsoever with anything before Quantal.
My Quantal install is finicky at times. Sometimes I have to logout and back in a couple of times before Compiz doesn't break at login.
But, that always fixes it.
I definitely hope it is not grub 2.00 that is causing the problems, it seems to work great.

---

### Post by bogan on 2012-11-05
Hi!, Cavsfan,

I just checked out all the fstab files on this computer, the only one that had an extra swap entry was the Quantal on the USB, which has not been involved in these recent recovery explorations.

I deleted the one  on the internal HDD, sda6, and ran```
 sudo update-grub
``` on both the usb and sda10, my main Quantal OS. It made no difference to the incorrect entries in the  'Advcanced Options' affected. 

I think the following may shed some light on your problem with recovery with Quantal; on the other hand it complicates things more than ever, so perhaps not.

AFAIK. up to, but not including, Precise, grub2 v 1.98 & 1.99 used 'single' as the boot option in the grub menu script for booting to recovery, as you do in your Wiki. 
Whereas, grub2 v2.00 uses 'recovery nomodeset'.

Calling a Quantal OS from grub2 installed in a Quantal OS using 'single', boots directly into a Root text terminal prompt, without showing a Recovery menu.

Doing so, using 'recovery nomodeset' boots to a  Recovery menu. [ I presume the 'nomodeset' is precautionary, rather the necessary, as it seems to make no difference, at least on my set-up.

What happens if that is done calling a Quantal OS from grub v 1.99 on other OS's, I do not know, and there are obvious complex possibilities with the other combinations.

Of all the combinations I have tried, the only thing I can say, with any certainty, is that in none of them did the 'Failsafe mode' menu selection work, wihout exception it showed a 'xserver fatal error' and hung up, - but wait about 40 seconds and it went direct to the GUI login screen.

Do you know how to tell if the system is in 'Failsafe' or not? 

'echo $RUNLEVEL' gives no output; presumably 'cat var/run/utmp' should show something, but it looks like garbage to me, whilst: 'cat /var/log/wtmp' is even worse; 'telinit' does not  seem to have an option to report its current value.

---

### Post by Cavsfan on 2012-11-07
I tried this yesterday and my custom entry for Quantal recovery did not go anywhere. It just hung.
I just changed "**ro single**" to "**ro recovery nomodeset**" sudo update-grub and rebooted and that brought up a root shell prompt which I could login to by entering "login" first.
So I guess that is better than just hanging. **I added that to the wiki so that at least a root shell login appears**.

But, not the normal recovery menu that I would like to see.

I installed grub on my generic (default grub 2.00) Quantal install and booted into Recovery and there was a normal menu but,
when I selected failsafe graphics mode, a box popped up and it said it was switching to a read-only mode and would attach anything in fstab.

But, when I hit enter it just hung. I to press reset to reboot.
So, the problem is with Quantal itself. It will not go into failsafe graphics mode no matter what.

Thanks **Bogan**! :)

---

### Post by Cavsfan on 2012-11-08
Through experience I have learned that it is best if you restore these  custom files to their original state prior to upgrading Ubuntu versions.
So, in the Community Wiki in my signature I have added how to do so and provided a link with the original file contents.
They can be copied and pasted into the files and Grub2 will be back to it's original state.

---

### Post by Cavsfan on 2012-11-14
Using the label command **tune2fs** as mentioned in the wiki comes in handy.

This is the output of **sudo blkid**;
```
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Lucid" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" 
/dev/sda3: UUID="2a80f59e-e7c3-418e-aab2-ab5d19255a2f" TYPE="swap" 
/dev/sda5: LABEL="Precise" UUID="3b8b1954-24e6-4a5e-9074-70a1a94ed4be" TYPE="ext4" 
/dev/sda6: UUID="82c51b29-023f-4964-99b6-67b45a49527f" TYPE="swap" 
/dev/sda7: LABEL="Quantal" UUID="b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a" TYPE="ext4" 
/dev/sda8: UUID="69ac3efc-8a8a-4056-89e0-59bb81c2f468" TYPE="swap" 
/dev/sda9: LABEL="Lucid Generic" UUID="109c11d0-71e3-41a4-87da-9e81535499a5" TYPE="ext4" 
/dev/sda10: UUID="24aa8c8b-53dc-4ecc-852b-ff2c25c8b342" TYPE="swap" 
/dev/sda11: LABEL="Precise-Generic" UUID="50104efb-d918-45a9-985e-a70c60e87ac0" TYPE="ext4" 
/dev/sda12: UUID="139390a6-2fe1-4ff2-b650-88ae3b0586c1" TYPE="swap" 
/dev/sda13: LABEL="Quantal-Generic" UUID="580e8c62-78ce-44a2-93e3-ccebd37c3acc" TYPE="ext4" 
/dev/sda14: UUID="ec3048b8-c644-435a-93bb-08bb4975d0db" TYPE="swap" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs" 

```BTW I labeled the Windows 7 C: drive from within Windows.

Here is what the benefit is when looking at the drives in Ubuntu 12.04 Gnome Classic:

[[IMG]http://ompldr.org/tZ2FpaQ[/IMG]]("http://ompldr.org/vZ2FpaQ")

I think otherwise you would be looking at their UUIDs.

---

### Post by bogan on 2012-11-15
Hi!, **Cavsfan,**

I set up your system in my main computer, and, for some unknown reason, 'tune2fs' limited any Labels to 16 characters, truncating anything longer.

I also discovered why I had problems with a combination of internal HDD, external eSata /usb HDD and an USB Sandisk.

When I set things up the SanDisk was sdb, the eSata HDD was sdc. and the Ubuntu on the internal HDD was sde.

Later, when I started up again, I plugged the USB [ for safety ] into a socket on the back panel, instead of one on the front, [ as it had been ].

That must have been connected to an USB hub with a higher priority, with the result that when booted, the USB SanDisk  was sda, the eSata was sde, and the HDD was sdf.

So while the orthodox system still worked using disk ID's, your system could not find the partitions it was looking for.

In other words it is essential that all drives are plugged in to the same sockets as when set-up.

The sdx's I am stating from memory, so they may not be entirely correct, but you will get the idea.

Incidently, a bit off topic, I have Posted in several threads a warning about the 310 nvidia driver with 6xxx & 7xxx series cards:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Chao!, **bogan**.

---

### Post by Cavsfan on 2012-11-16
> **bogan said:**
> Hi!, **Cavsfan,**

I set up your system in my main computer, and, for some unknown reason, 'tune2fs' limited any Labels to 16 characters, truncating anything longer.

I also discovered why I had problems with a combination of internal HDD, external eSata /usb HDD and an USB Sandisk.

When I set things up the SanDisk was sdb, the eSata HDD was sdc. and the Ubuntu on the internal HDD was sde.

Later, when I started up again, I plugged the USB [ for safety ] into a socket on the back panel, instead of one on the front, [ as it had been ].

That must have been connected to an USB hub with a higher priority, with the result that when booted, the USB SanDisk  was sda, the eSata was sde, and the HDD was sdf.

So while the orthodox system still worked using disk ID's, your system could not find the partitions it was looking for.

In other words it is essential that all drives are plugged in to the same sockets as when set-up.

The sdx's I am stating from memory, so they may not be entirely correct, but you will get the idea.

Incidently, a bit off topic, I have Posted in several threads a warning about the 310 nvidia driver with 6xxx & 7xxx series cards:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Chao!, **bogan**.

Thanks for that info **bogan**! I can imagine that if you did something to alter the partitions that could cause chaos.
I don't really suggest using any USB drives but, if you do I suggest always plugging them back in the same place they 
were initially plugged in if you have included them in this customization.

I have one USB drive - a 1TB drive which I use for backup. I never unplug it and it always has power.
It is formatted NTFS so it works well with both windows and Ubuntu. 
My PC just goes to sleep or suspends after an hour of no use.

About the Nvidia drivers, I have not added any drivers to any of my installs except Lucid. 
With Lucid it was a piece of cake but, I have not been successful with any other version of Ubuntu at upgrading the driver.

I tried the xswat ppa on Precise and that ended in a clean install. Thankfully that was on a test install.
But, I learned my lesson: as you said the xswat ppa works for some and not for others.
It only takes one time for me.  I have a Geforce 9800 GT.
:)

---

### Post by Cavsfan on 2012-11-16
Something else I found out is that when you re-install a Ubuntu or install more than one, the **fstab** pulls in the ext4 where it *was* installed as 
well as where it is now installed. Every swapfile gets pulled into **fstab** also.

If you have multiple Ubuntus like I do (6) that makes the boot menu look really bad after initially installing a 2nd, 3rd or re-installing any of them.
My default grub2 menu after installing Precise and Quantal had everything on sda2 where my good Lucid install is. I knew something was weird from 
that. It said Lucid was on sda2, Precise was on sda2, Quantal was on sda2!

Luckily after cleaning up all of the **/etc/fstab** files on each and every one, they all point to the correct partitions now.

That is also mentioned in the wiki - cleaning up fstab.

---

### Post by Cavsfan on 2012-11-19
> **bogan said:**
> I set up your system in my main computer, and, for some unknown reason, 'tune2fs' limited any Labels to 16 characters, truncating anything longer.

I looked at the man page for **tune2fs** and it mentions a 16 character limit. 
Although it mentioned ext2 file systems, I believe it still holds true.

I also don't think it likes spaces but, am not absolutely certain.
My "Quantal-Generic" label kept disappearing.
Not sure if it was caused by a space or not but, it has stuck for quite a while now.

I initially thought there was a limit on partitions you could label but, I don't think that is true either.

---

### Post by oldfred on 2012-11-19
It gets more confusing with gpt(GUID). Now there are two labels. One is the gpt partition and the other is the file system.

My older Maverick label or MAVERICK gpt partition label. I now use the same label for both as I do not know for sure which tools show which label.

---

### Post by bogan on 2012-11-19
Hi!, **Cavsfan**,

The first time I tried 'tune2fs' it allowed me to use "Quantal 12.10 EXT sdb7 Recovery"- 30 Characters - the second time only 16, that's why I mentioned it.

The only partitions it would not let me Label were the Swaps, and empty Partitions, it complained it could not find a file system.
[ATTACH]227411[/ATTACH]

Edit: I have not had any problems with spaces, as long as I use double quotes to enclose the whole Label, though I did not use any in the Screenshot.

Chao!, **bogan**.

---

### Post by Cavsfan on 2012-11-19
I see what you mean **oldfred** with the 2 labels. I noticed that you can also label the partitions in GParted as well as with the command.

And **bogan** I see you are right. I labeled my one partition "Lucid Generic" with a space and it took.
EDIT: I didn't know that you had tried 30 characters. I looked in Lucid and in Quantal at the man page and it mentioned 16 char limit.

I labelled Quantal-Generic a dozen times and each time it would disappear for some reason that I didn't understand.
So, I kept re-labelling it and I guess at some point it gave up and took the label. :D

You can see how my partitions are all labelled on page 4 post #40 and here is what they look like in GParted:

[ATTACH]227412[/ATTACH]

---

### Post by Cavsfan on 2012-11-20
The old How To that this thread has evolved from is now closed.
It has links pointing to this thread.

The old How to had some errors in it, which I could not fix because of the change in policy.
However the Wiki in my signature and on the 1st post of this thread works _very well_ on all versions of grub2.
I have had Debian Squeeze installed and it worked well with that too.

Feel free to post any screenshots of your custom grub2 screens, questions, problems or any thing else concerning the WIki here.

---

### Post by ChinaJustin on 2012-11-25
Cavsfan,

Glad to see you got the previous thread up into a Wiki. VERY nice, and much easier to read/understand, that's for sure!

Just did the process on my dual-boot Windows 7 / Linux Mint 13, and have a question on some of the menu entries.

Currently, when I boot, my grub shows my normal Linux and Linux recovery mode options, a previous kernel option, Windows 7, and then three other Windows 7 options: one for the recovery environment (which I want to keep) on sda4, one that points to the small "SYSTEM" partition on sda1 but still boots into Windows 7 directly when I select it, and one that points to sda2 (so basically a repeat of my custom entry for Windows 7). I want to get rid of those last two but keep the recovery environment option. Is there any way to do that?

Here's my blkid output:

```
/dev/sda1: LABEL="System" UUID="E034F94D34F92766" TYPE="ntfs" 
/dev/sda2: LABEL="TI106231W0C" UUID="32FC2690FC264E83" TYPE="ntfs" 
/dev/sda4: LABEL="HDDRECOVERY" UUID="38F653DCF6539948" TYPE="ntfs" 
/dev/sda5: UUID="2f60dfb5-580e-4508-a50c-345a04aed051" TYPE="ext4" 
/dev/sda6: UUID="6e9ac2d0-0427-43ca-90ab-24656665b14d" TYPE="swap" 
/dev/sda7: LABEL="Data" UUID="C61606BE1606B00B" TYPE="ntfs" 
/dev/sdb1: LABEL="MyPassport" UUID="16DC46E5DC46BF2D" TYPE="ntfs" 

```And my custom_06 file:

```
#!/bin/sh
echo 1>&2 "Adding LinuxMint Maya and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "LinuxMint 13 - Maya" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "LinuxMint 13 - Maya (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro single
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 32FC2690FC264E83
    chainloader +1
}
```And then when I ran that grep command I saw a few posts back, here's the output:
```

0    menuentry "LinuxMint 13 - Maya" {
     1    menuentry "LinuxMint 13 - Maya (Recovery Mode)" {
     2    menuentry "Windows 7" {
     3    menuentry 'Linux Mint 13 Cinnamon 64-bit, 3.2.0-33-generic (/dev/sda5)
     4    menuentry 'Linux Mint 13 Cinnamon 64-bit, 3.2.0-33-generic (/dev/sda5) -- recovery mode
     5    submenu "Previous Linux versions" {
     6    menuentry 'Linux Mint 13 Cinnamon 64-bit, 3.2.0-32-generic (/dev/sda5)
     7    menuentry 'Linux Mint 13 Cinnamon 64-bit, 3.2.0-32-generic (/dev/sda5) -- recovery mode
     8    menuentry 'Linux Mint 13 Cinnamon 64-bit, 3.2.0-23-generic (/dev/sda5)
     9    menuentry 'Linux Mint 13 Cinnamon 64-bit, 3.2.0-23-generic (/dev/sda5) -- recovery mode
    10    menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    11    menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    12    menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {

```So I want to get rid of 10 and 11 but not 12. If I chmod -x the os_prober, I'm afraid it'll get rid of the WRE option. Am I right? And if so, is there a way, again, to get rid of 10 and 11 but keep 12? I'm thinking I could do another entry like my Windows 7 one, just change the uuid and the root, but what about the search and chainloader commands? Anything extra I would need to put in since it's a recovery environment?

---

### Post by oldfred on 2012-11-25
Are you sure you want to keep 12. That is the vendor recovery which erases your entire drive. Best never to accidentally run it.

Both Windows and the Vendor call there partitions recovery. I really consider the 100MB  Windows the boot/repair partition. And you can delete that if you have a separate Windows repairCD and can boot directly in the Windows main c: drive.

Once you make a set of vendor recovery DVDs you do not even need the Vendor recovery and it is better to have a backup of Windows.

I suggest backing up grub.cfg. And copy any additional entries you want into 40 custom or where you want then. Then turn off os-prober. You can turn it back on if you want it to find a new install, copy an entry and then turn off again. 

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

### Post by ChinaJustin on 2012-11-26
I guess I don't need to keep 12. I made a Recovery Environment CD already if I really needed it, and I made the Toshiba Recovery Discs (with its wonderful bloatware) already, too. I just like to keep those partitions on their out of general principle and redundancy.

I'll just go ahead and take os_prober out of the equation. Hadn't thought about the fact I already have the discs if necessary. Thanks, oldfred!

---

### Post by Cavsfan on 2012-11-26
Thanks **oldfred** for pointing that out! 

Right **ChinaJustin**. I believe making **10_linux** and **30_os-prober** both unexecutable and then **sudo update-grub** should do it.
This is from 1.5 in the Wiki - Final changes.
You can always login to recovery and make them executable if needed.

Also don't forget to label the drives as mentioned in 1.6 of the Wiki.

You can see an example of how that looks like on page 4 post #40 of this thread.

---

### Post by ChinaJustin on 2012-11-28
Yeah, I just tried the labeling thing... but it's weird:

```
/dev/sda1: LABEL="System" UUID="E034F94D34F92766" TYPE="ntfs" 
/dev/sda2: LABEL="TI106231W0C" UUID="32FC2690FC264E83" TYPE="ntfs" 
/dev/sda4: LABEL="HDDRECOVERY" UUID="38F653DCF6539948" TYPE="ntfs" 
/dev/sda5: UUID="14812599-e129-4ed1-8bca-ed5743b08254" TYPE="ext4" LABEL="Maya" 
/dev/sda6: UUID="6e9ac2d0-0427-43ca-90ab-24656665b14d" TYPE="swap" 
/dev/sda7: LABEL="Data" UUID="C61606BE1606B00B" TYPE="ntfs" 

```

So it put my "Maya" label way out at the end... and when I tried doing the tune2fs on sda2 (to change it from the letters/numbers to "Windows 7"), it gave me:

```
tune2fs 1.42 (29-Nov-2011)
tune2fs: Bad magic number in super-block while trying to open /dev/sda2
Couldn't find valid filesystem superblock.

```

Any way to get the label at the FRONT, and what does that error message mean? Any way to get it to work?

---

### Post by Cavsfan on 2012-11-28
> **ChinaJustin said:**
> Yeah, I just tried the labeling thing... but it's weird:

```
/dev/sda1: LABEL="System" UUID="E034F94D34F92766" TYPE="ntfs" 
/dev/sda2: LABEL="TI106231W0C" UUID="32FC2690FC264E83" TYPE="ntfs" 
/dev/sda4: LABEL="HDDRECOVERY" UUID="38F653DCF6539948" TYPE="ntfs" 
/dev/sda5: UUID="14812599-e129-4ed1-8bca-ed5743b08254" TYPE="ext4" LABEL="Maya" 
/dev/sda6: UUID="6e9ac2d0-0427-43ca-90ab-24656665b14d" TYPE="swap" 
/dev/sda7: LABEL="Data" UUID="C61606BE1606B00B" TYPE="ntfs" 

```So it put my "Maya" label way out at the end... and when I tried doing the tune2fs on sda2 (to change it from the letters/numbers to "Windows 7"), it gave me:

```
tune2fs 1.42 (29-Nov-2011)
tune2fs: Bad magic number in super-block while trying to open /dev/sda2
Couldn't find valid filesystem superblock.

```Any way to get the label at the FRONT, and what does that error message mean? Any way to get it to work?

The label normally displays on the right soon after you enter the label  command and subsequently will show on the left, but that doesn't matter. It will only show up that way in the terminal. 
The important thing is that it will be labeled inside Mint.

You can enter **man tune2fs** in terminal and it will show the options.
However it only mentions labeling ext2 files systems.

The only things you can label with this command are ext4 partitions. You cannot label swapfiles or Windows partitions from outside of Windows.

In Windows I clicked on Computer and then C drive and properties and labeled my C drive "C:". 
Here is the output of my **sudo blkid**:
```
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Lucid" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" 
/dev/sda3: UUID="2a80f59e-e7c3-418e-aab2-ab5d19255a2f" TYPE="swap" 
/dev/sda5: LABEL="Precise" UUID="3b8b1954-24e6-4a5e-9074-70a1a94ed4be" TYPE="ext4" 
/dev/sda6: UUID="82c51b29-023f-4964-99b6-67b45a49527f" TYPE="swap" 
/dev/sda7: LABEL="Quantal" UUID="b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a" TYPE="ext4" 
/dev/sda8: UUID="69ac3efc-8a8a-4056-89e0-59bb81c2f468" TYPE="swap" 
/dev/sda9: LABEL="Lucid Generic" UUID="109c11d0-71e3-41a4-87da-9e81535499a5" TYPE="ext4" 
/dev/sda10: UUID="24aa8c8b-53dc-4ecc-852b-ff2c25c8b342" TYPE="swap" 
/dev/sda11: LABEL="Precise-Generic" UUID="50104efb-d918-45a9-985e-a70c60e87ac0" TYPE="ext4" 
/dev/sda12: UUID="139390a6-2fe1-4ff2-b650-88ae3b0586c1" TYPE="swap" 
/dev/sda13: LABEL="Quantal-Generic" UUID="580e8c62-78ce-44a2-93e3-ccebd37c3acc" TYPE="ext4" 
/dev/sda14: UUID="ec3048b8-c644-435a-93bb-08bb4975d0db" TYPE="swap" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs"
```

---

### Post by oldfred on 2012-11-28
For a neater display, you can do this - but you have to post in code tags to make it preserve format:

```
fred@fred-Precise:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    (not mounted)  04B05B70B05B6768
/dev/sda2  ext3    backup   /mnt/backup    13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdb2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdb3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdb4  ext4    MavData  (not mounted)  431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdc1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdc2  ntfs    Shared   /mnt/shared    44332FD360AA9657
/dev/sdc4  ext2    bios_gpt (not mounted)  bbda6045-bb8a-4666-8bd4-04b3945ca581
/dev/sdc5  ext4    Karmic   (not mounted)  117412d5-2dbe-4011-8aec-ae310d1ee6c7
/dev/sdc6  ext3    Data     /mnt/data      a55e6335-616f-4b10-9923-e963559f2b05
/dev/sdc7  ext4    LUCID    (not mounted)  5e25282c-9c54-45df-9e79-514011e98648
/dev/sdc8  ext4    Test     (not mounted)  af29c61a-34e9-48eb-9c94-afcb4bb61582
/dev/sdc9  vfat    OLDG     (not mounted)  F6A6-705D
/dev/sdc10 ext4    newhome  (not mounted)  b8a7e331-a716-4ac1-bf58-6ac515606c6d
/dev/sdc11 swap             <swap>         09367687-86d1-4fd0-9b81-2787d3196159
/dev/sdc12 ext4    Puppy    (not mounted)  07e2a08d-37ca-4cf1-877b-f02b0eabcbca
/dev/sdc13 ext4    natty    (not mounted)  318fd41e-4210-4960-a0d9-ee9b48388d69
/dev/sdc14 ext4    kubuntu  (not mounted)  0b3034c1-d991-45f5-a7ea-9265125e6b05
/dev/sdc15 swap             <swap>         2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9
/dev/sdc16 ext4    oneiric  (not mounted)  63d146fd-1c63-4b31-95c5-ab52e2892283
/dev/sdc17 ext4    server   (not mounted)  63045773-e42a-46eb-9e96-b93428542527
/dev/sdc18 ext4             (not mounted)  117e0c31-7e16-4e8b-90b7-a3c688a34f26
/dev/sdd1  vfat    EFI      (not mounted)  7B30-5ACA
/dev/sdd3  ext4    Precise  /              adc013e9-a23d-4a36-849b-3faeac005667
/dev/sdd4  ext4    Quantal  (not mounted)  94e634d0-39fb-4994-a685-8ee34747a240
fred@fred-Precise:~$ 



```

---

### Post by Cavsfan on 2012-11-28
Sweet! Thanks for that tip **Oldfred**! I'll make note of that!

**ChinaJustin**, check out this picture. This is the main benefit of using the label command:

[img]http://ompldr.org/vZ2FpaQ[/img]

---

### Post by Cavsfan on 2012-11-28
This is what **sudo blkid -c /dev/null -o list** produces for me. What am I doing wrong? Does it have to be edited in a text editor first?
```
device                                                                           fs_type         label            mount point                                                                          UUID
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                                                                                ntfs                  C:                     (not mounted)                                                                                                1CFC7A8DFC7A60C6
/dev/sda2                                                                                                ext4                  Lucid                  /                                                                                                            a162dc8a-e4df-4b79-b4c3-524761ff7ae1
/dev/sda3                                                                                                swap                                         <swap>                                                                                                       2a80f59e-e7c3-418e-aab2-ab5d19255a2f
/dev/sda5                                                                                                ext4                  Precise                (not mounted)                                                                                                3b8b1954-24e6-4a5e-9074-70a1a94ed4be
/dev/sda6                                                                                                swap                                         (not mounted)                                                                                                82c51b29-023f-4964-99b6-67b45a49527f
/dev/sda7                                                                                                ext4                  Quantal                (not mounted)                                                                                                b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a
/dev/sda8                                                                                                swap                                         (not mounted)                                                                                                69ac3efc-8a8a-4056-89e0-59bb81c2f468
/dev/sda9                                                                                                ext4                  Lucid Generic          (not mounted)                                                                                                109c11d0-71e3-41a4-87da-9e81535499a5
/dev/sda10                                                                                               swap                                         (not mounted)                                                                                                24aa8c8b-53dc-4ecc-852b-ff2c25c8b342
/dev/sda11                                                                                               ext4                  Precise-Generic        (not mounted)                                                                                                50104efb-d918-45a9-985e-a70c60e87ac0
/dev/sda12                                                                                               swap                                         (not mounted)                                                                                                139390a6-2fe1-4ff2-b650-88ae3b0586c1
/dev/sda13                                                                                               ext4                  Quantal-Generic        (not mounted)                                                                                                580e8c62-78ce-44a2-93e3-ccebd37c3acc
/dev/sda14                                                                                               swap                                         (not mounted)                                                                                                ec3048b8-c644-435a-93bb-08bb4975d0db
/dev/sdb1                                                                                                ntfs                  Fantom                 /media/Fantom                                                                                                78B8D1A1B8D15DE6

```

---

### Post by bogan on 2012-11-28
Hi!, cavsfan,

It worked for me, and I did not do anything out of the ordinary [ Edit: Other than having to fiddle with the Terminal size to get a readable display. My first attempt had a display similar to yours but not so exagerated]:```
 alan@alan-MS-7616:~$ sudo blkid -c /dev/null -o list
device          fs_type  label     mount point         UUID
--------------------------------------------------------------------------------------------
/dev/sda1       ntfs     System Reserved (not mounted) CC9240F39240E394
/dev/sda2       ntfs     Boot      (not mounted)       A8D04A41D04A15CA
/dev/sda4       ntfs               (not mounted)       368837118836CF5D
/dev/sda5       ext4     Precise-sda5 (not mounted)    a8ecbe4f-fc2d-40a1-b261-1b62d74e7130
/dev/sda6       swap               <swap>              a74af1d9-f7f9-4453-97e7-b9e3f370dca4
/dev/sda7       vfat               (not mounted)       CB27-6560
/dev/sda8       ext4     Home-sda5 (not mounted)       0a1beb1a-9c4b-45f7-a35b-a2689cf63a5d
/dev/sda9       vfat               (not mounted)       CC02-1DAF
/dev/sda10      ext4     Quantal-sda10 /               b5aab3a2-0086-4a12-9276-46bb5a615038
/dev/sda11      ext4     Home-sda10 /home              adc771a1-313c-47ae-8725-3c89b89bbfa2
/dev/sdb1       ntfs     Simulator (not mounted)       20D6C693D6C6691C
/dev/sdb2       ntfs     Backup    (not mounted)       CE5C7F585C7F3A73
/dev/sdb5       ext4     Home-sdb7 (not mounted)       390eaeec-0d84-4599-99e0-b2a770f9e61c
/dev/sdb6       ext4               (not mounted)       2d70c299-9315-45e6-85ad-3464c794f407
/dev/sdb7       ext4     Quantal-EXT-sdb7 (not mounted) 7608b1e5-b5ea-4563-ad94-8cf496b9f95f
/dev/sdb8       ext4               (not mounted)       8222255f-143c-4e48-8127-66cc43237a8c
/dev/sdc1       ntfs     Switch    /media/alan/Switch  3EB698C5B6987ED9
/dev/sdc2       ext4     Quantal-USB-sdc2 /media/alan/Quantal-USB-sdc2 cee38717-6980-4485-a047-124edb4d5a23
/dev/sdc3       swap               (not mounted)       9a74bb15-1215-4774-8419-f2908ee62d2e
alan@alan-MS-7616:~$ 
```Running 12.10.[ Unlabelled partitions are empty.]

Chao!, **bogan**.

---

### Post by oldfred on 2012-11-28
You seem to have a lot of extra spaces. I do not edit. Did it look ok in terminal before copying? 

My post is just as is, but over the versions blkid has changed. What version of Ubuntu are you running. Mine is Precise. 

Maybe somewhere I added something but oldfred certainly does not remember. Your output looks the same except for all the extra spaces.

---

### Post by bogan on 2012-11-28
HI!, **cavsfan**,

My Post #58 edited.

Try altering the Terminal size, or using a Terminal, if you were using a full screen Console.

Were you using Lucid ?

Chao!, **bogan.**

---

### Post by Cavsfan on 2012-11-28
Yeah, it has to be the terminal size. I have a 28' monitor and had it full screen at the time.
Let me see what I can do.

OK that was it. Check this out:

```
cavsfan@cavsfan-desktop:~$ sudo blkid -c /dev/null -o list
[sudo] password for cavsfan: 
device                         fs_type     label        mount point                        UUID
--------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                      ntfs        C:           (not mounted)                      1CFC7A8DFC7A60C6
/dev/sda2                      ext4        Lucid        /                                  a162dc8a-e4df-4b79-b4c3-524761ff7ae1
/dev/sda3                      swap                     <swap>                             2a80f59e-e7c3-418e-aab2-ab5d19255a2f
/dev/sda5                      ext4        Precise      (not mounted)                      3b8b1954-24e6-4a5e-9074-70a1a94ed4be
/dev/sda6                      swap                     (not mounted)                      82c51b29-023f-4964-99b6-67b45a49527f
/dev/sda7                      ext4        Quantal      (not mounted)                      b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a
/dev/sda8                      swap                     (not mounted)                      69ac3efc-8a8a-4056-89e0-59bb81c2f468
/dev/sda9                      ext4        Lucid Generic (not mounted)                     109c11d0-71e3-41a4-87da-9e81535499a5
/dev/sda10                     swap                     (not mounted)                      24aa8c8b-53dc-4ecc-852b-ff2c25c8b342
/dev/sda11                     ext4        Precise-Generic (not mounted)                   50104efb-d918-45a9-985e-a70c60e87ac0
/dev/sda12                     swap                     (not mounted)                      139390a6-2fe1-4ff2-b650-88ae3b0586c1
/dev/sda13                     ext4        Quantal-Generic (not mounted)                   580e8c62-78ce-44a2-93e3-ccebd37c3acc
/dev/sda14                     swap                     (not mounted)                      ec3048b8-c644-435a-93bb-08bb4975d0db
/dev/sdb1                      ntfs        Fantom       /media/Fantom                      78B8D1A1B8D15DE6
cavsfan@cavsfan-desktop:~$ 

```We'll have to keep the terminal size in mind I guess. It looks good now.

Thanks! :)

---

### Post by oldfred on 2012-11-28
>  I have a 28' monitor 

I thought I had a good sized monitor as my vision is not that great, but a 28 foot (28' ) monitor.  :P

---

### Post by Cavsfan on 2012-11-29
> **oldfred said:**
> I thought I had a good sized monitor as my vision is not that great, but a 28 foot (28' ) monitor.  :P

HA! Typo - 28 inch monitor! I guess not even this monitor helps my vision!  :D

EDIT: I meant to say that yes I was using Lucid.

---

### Post by Cavsfan on 2012-12-15
I added Raring Ringtail 13.04 as the 8th system on my Grub2 menu.

[[IMG]http://ompldr.org/tZ3BpcQ[/IMG]]("http://ompldr.org/vZ3BpcQ")

It uses Grub version 2.00 just like Quantal Quetzal.

The normal login to Raring gives a quick shell logon screen but, quickly goes into Raring.

The Recovery option takes you to a shell login prompt.

```
grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
```
Returns:
```
     0	menuentry "Lycid Lynx 10.04" {
     1	menuentry "Lycid Lynx 10.04 (Recovery Mode)" {
     2	menuentry "Lycid Lynx Generic 10.04" {
     3	menuentry "Lycid Lynx Generic 10.04 (Recovery Mode)" {
     4	menuentry "Precise Pangolin 12.04" {
     5	menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     6	menuentry "Precise Pangolin Generic 12.04" {
     7	menuentry "Precise Pangolin Generic 12.04 (Recovery Mode)" {
     8	menuentry "Quantal Quetzal 12.10" {
     9	menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
    10	menuentry "Quantal Quetzal Generic 12.10" {
    11	menuentry "Quantal Quetzal Generic 12.10 (Recovery Mode)" {
    12	menuentry "Raring Ringtail 13.04" {
    13	menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
    14	menuentry "Windows 7" {
```

It always defaults to 14 Windows 7 so in case of a reboot my wife is good to go with Windows 7.

---

### Post by Cavsfan on 2012-12-16
BTW, when I installed Raring Ringtail 13.04, it pulled in 6 other swapfiles into **/etc/fstab**.
So, it had the partition my ext4 was on and 7 swapfiles; the right one and the 6 from the other Ubuntus on my system.

This is why I mentioned this in section 1.7 of the wiki.

---

### Post by Cavsfan on 2012-12-16
I changed my Grub2 picture and I also noticed that in the Grub2 documentation that **drs305** had written that black 
can be used as a color without it making the font transparent.
So, black/black is acceptable but, only if you have a background image. If you have no image, the font will be transparent or invisible.

The wiki has been updated to reflect the above.
These are _not_ the most ideal colors, but it shows that black can be used when an image is present.

This is with **color_normal=black/black**
and **color_highlight=light-green/black**.

[[IMG]http://ompldr.org/tZ3B6eA[/IMG]]("http://ompldr.org/vZ3B6eA")

---

### Post by Cavsfan on 2012-12-17
OK, this is the last one for a while. I am not very good at matching backgrounds to colors but, I believe this one looks pretty good.  :)

[[img]http://ompldr.org/tZ3FkdA[/img]](http://ompldr.org/vZ3FkdA)

The font colors are **color_normal=cyan/black**
and **color_highlight=light-cyan/black**

---

### Post by Cavsfan on 2013-01-06
Added a link at the bottom of the wiki to link back to this thread to post questions, etc.

---

### Post by Cavsfan on 2013-01-08
Got rid of the extra systems and cleaned it up a bit but, I still like this background.
This is on Grub 2.00 on Raring Ringtail 13.04.
I just have the 5 OS's on it now.

[[img]http://ompldr.org/taDI4aA[/img]](http://ompldr.org/vaDI4aA)

---

### Post by Cavsfan on 2013-01-13
I learned from **cariboo907** that you can have one single swapfile for all of your Ubuntus.
So, I simplified my partitions and gained some room at the same time.

```
cavsfan@cavsfan-MS-7529:~$ sudo blkid
[sudo] password for cavsfan: 
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Lucid" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4"
[COLOR=Red]/dev/sda3: UUID="2a80f59e-e7c3-418e-aab2-ab5d19255a2f" TYPE="swap" [/COLOR]
/dev/sda5: LABEL="Precise" UUID="3b8b1954-24e6-4a5e-9074-70a1a94ed4be" TYPE="ext4" 
/dev/sda6: LABEL="Quantal" UUID="b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a" TYPE="ext4" 
/dev/sda7: LABEL="Raring" UUID="a6b7ac97-488f-4e87-b6af-247fcbf6df77" TYPE="ext4" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs"
```I had to edit each **/etc/stab** file and get the swap file to point to **sda3** and the **UUID** above  and everything is good.

Just don't make the same mistake I made by not moving my grub to my main Ubuntu on sda2 which was untouched.
I had grub installed on Raring and after deleting swapfiles, resizing/moving  partitions, upon reboot I was looking at grub recovery :(
I recovered with my Lucid live CD pretty easily but, it would have been easier if I had thought before hand. :p


[[IMG]http://ompldr.org/taDI4aA[/IMG]]("http://ompldr.org/vaDI4aA")

---

### Post by ChinaJustin on 2013-01-26
(I accidentally posted this... well, somewhere else. I received two answers: 1) Check the Mint forums (by a mod :p) and 2) to use a different UUID in my grub.cfg. But now I'm copying and pasting HERE since I'm sure I'll get better answers. And this is where I meant it to go to begin with! ;))

Just did a clean install of Linux Mint Nadia (based on Ubuntu 12.10) and  tried setting up my Grub 2.00 menu as normal. But ran into two  problems:

1) When I run 'update-grub', I do not get the echo line from my  06_custom file. Also related to this problem is that my Grub menu items  are the standard ones, and **not** the labels I wanted (i.e. "Windows Vista (/bootloader) on sdax" as opposed to just "Windows Vista").
2) When I **chmod -x** the os_prober file and run **update-grub**,  it only "finds" my Vista partition. Now, I only have the kernel that  came installed with LM 14, but I don't remember my only having one  installed kernel being an issue before; as I recall, even with just one  kernel it recognized and added the appropriate entry to the Grub menu.  But now, if I run **ubdate-grub** and reboot, I just see my Vista partition.

Here is my 06_custom file:

     ```

#!/bin/sh 
echo 1>&2 "Adding Linux Mint and Windows Vista" 
exec tail -n +4 $0 
# This file provides an easy way to add custom menu entries.  Simply type the 
# menu entries you want to add after this comment.  Be careful not to change 
# the 'exec tail' line above.  
menuentry "Linux Mint 14 - Nadia" {
     set root=(hd0,2)
         linux /vmlinuz root=/dev/sda2 ro quiet splash
         initrd /initrd.img 
} 
menuentry "Linux Mint 14 - Nadia (Recovery Mode)" {
     set root=(hd0,2)
         linux /vmlinuz root=/dev/sda2 ro single
         initrd /initrd.img 
} 
menuentry "Windows Vista" {
     insmod ntfs
     set root='(hd0,1)'
     search --no-floppy --fs-uuid --set 32C2B4EDC2B4B707
     chainloader +1 
}

```Ideas?

---

### Post by oldfred on 2013-01-26
Grub2 2.00 it seems does not work with the old commands with echo. Actually the original post was to use a terminal's echo command to add lines to 40_custom and somehow that got picked up as part of what to post into 40_custom, so users copied & pasted it into their custom grub files. Old versions of grub tolerated various things but now it does not.

Remove the echo line.

first lines should just be:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```

---

### Post by ChinaJustin on 2013-01-26
oldfred,

Thanks. So that takes care of any "echo"-ing that can be customized, but what about the issue of the "menuentry" not getting picked up on the grub update?

---

### Post by oldfred on 2013-01-27
I used the same 40_custom thru several versions of Ubuntu/grub. But then with 1.99 it stopped working. It actually reported an error and wrote a backup grub.cfg file. It turned out I had a missing } and one stanza was always missing, but it was for something I had stopped booting and never really missed. 
So any typo now can cause issues.

Are entries in grub.cfg?

---

### Post by Cavsfan on 2013-01-27
> **ChinaJustin said:**
> oldfred,

Thanks. So that takes care of any "echo"-ing that can be customized, but what about the issue of the "menuentry" not getting picked up on the grub update?

Here is my 06_custom file on Grub 2.00 in Ubuntu Quantal Quetzel 12.10:

```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Quantal Quetzal 12.10 and Windows 7"
[COLOR=Red]exec tail -n +4 $0[/COLOR]
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Quantal Quetzal 12.10" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro single
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}
```The [COLOR=Red]exec tail -n +4 $0[/COLOR] line tells it to execute the 4th line from the top which is the 1st menuentry line.
You will only see the echo output from line 2 when you enter **sudo update-grub** in terminal.
It will list your picture and the echo line on line 2.
The menuentry lines are only what will display on your grub menu.

See this post by **Drs305** on the old tutorial thread [[COLOR=blue]_here_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=12034165&postcount=121").
(this is when grub 1.99 came out)

---

### Post by ChinaJustin on 2013-01-27
> **Cavsfan said:**
> The [COLOR=Red]exec tail -n +4 $0[/COLOR] line tells it to execute the 4th line from the top which is the 1st menuentry line.
You will only see the echo output from line 2 when you enter **sudo update-grub** in terminal.
It will list your picture and the echo line on line 2.
The menuentry lines are only what will display on your grub menu.


According to oldfred, though, 2.00 doesn't do "echo" lines anymore:

[QUOTE=oldfred]
Grub2 2.00 it seems does not work with the old commands with echo.
[/QUOTE]

Are you saying it does for you, Cavsfan? Because it's not working for me, either.

Also, let me clarify from my previous post (#71):

When I run **update-grub** and then reboot my system, my menu entries on the grub menu **do not** reflect the changes I made in the 06_custom file as posted in post #71.

I don't really care about the "echo" command, because that's really just something for me to see and "ooo" and "ahh" at. But I really do want the menu entries to reflect what I want them to.

Also, why would **"chmod -x**"-ing the os_prober file and running **update-grub** only find my Vista partition and not my base LinuxMint kernels? (I only have the kernels from the clean install: no updates).

EDIT: OK, so apparently, I forgot to **chmod +x** my 06_custom file.  After reading oldfred's question about whether the entries were even in  the grub.cfg file or not, I found that they weren't. I thought that I  HAD done the **chmod +x** command, so either it didn't take... or I  didn't do it. For the sake of my sanity and personal image, I'm saying  it didn't take. :wink:

---

### Post by oldfred on 2013-01-27
I do not see an error. But my 40_customs have always had +3?

A while back there were some issues with extra spaces at an end of line or the end of the file. Impossible to visually tell if that is an issue or not anymore.

If you have turned off os-prober then only entires you have added in your 06 or 40 custom will be added. Is you 06_custom have execute bit set?

       In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

       sudo chmod 755 /etc/grub.d/06_custom
or
sudo chmod a+x /etc/grub.d/06_custom

Did you check your grub.cfg to see if boot stanza are there?

---

### Post by Cavsfan on 2013-01-27
> **ChinaJustin said:**
> OK, so apparently, I forgot to **chmod +x** my 06_custom file. 

That will do it every time! I thought that may be the problem. ChinaJustin if you recall you were the one asking the question about why the [COLOR=Red]exec tail -n +3 $0[/COLOR] line did not work with the echo lines on every entry.
That is when Drs305 stepped in and told us that when grub went to 1.99 

This is from Lucid - grub 1.98:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
echo "Lucid Lynx 10.04" >&2 
cat << EOF
    menuentry "Lucid Lynx 10.04" {
    set root=(hd0,2)
    linux /vmlinuz root=/dev/sda2 ro quiet splash
    initrd /initrd.img
}
EOF

```Which as Drs305 said changed to this in grub 1.99 and 2.00.
Changing the 3 to 4 and adding the echo line as the 2nd line causes the first executable line to be the 4th line down (the 1st menuentry).
Or you could leave it a 3 and leave out the echo as you stated since you are the only one to see it when you type **sudo update-grub** in terminal is fine too.

```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Lucid Lynx and Windows 7"
exec tail -n [COLOR=Red]+4[/COLOR] $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
[s]echo "Lucid Lynx 10.04" >&2[/s]
[s]cat << EOF[/s]
    [COLOR="Red"]menuentry[/COLOR] "Lucid Lynx 10.04" {
    set root=(hd0,2)
    linux /vmlinuz root=/dev/sda2 ro quiet splash
    initrd /initrd.img
}
[s]EOF[/s]
[s]echo "Lucid Lynx 10.04 (Recovery Mode)" >&2[/s]
[s]cat << EOF[/s]
    menuentry "Lucid Lynx 10.04 (Recovery Mode)" {
    set root=(hd0,2)
    linux /vmlinuz root=/dev/sda2 ro single
    initrd /initrd.img
}
[s]EOF[/s]
[s]echo "Windows 7 Loader" >&2[/s]
[s]cat << EOF[/s]
    menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1cfc7a8dfc7a60c6
    chainloader +1
}
[s]EOF[/s]

```

**Oldfred**, at that time all I had installed was Lucid with grub 1.98 so I was not keeping up with the times like I should have been.
**Bogan** pointed out that my tutorial was wrong and when that finally got through my thick head, I fixed it.
So, the new wiki is a lot better as it splits it between grub 1.98, 1.99 and 2.00.
I need to update it with the grub versions instead of the Ubuntu versions because they can change but, the grub version is what is important.
But, come April grub 1.98 will be a thing of the past.

The reason I say to save 40_custom as 06_custom is that even when you have 10_linux and 30_os-prober executable, the custom display will be on top and be static.
If you save the 40_custom file, the custom entries will be on the bottom and change when the other 2 files are made executable.

Now I have 4 Ubuntu versions installed so I can at least try to keep up. :)

---

### Post by Cavsfan on 2013-02-15
I upgraded my main install Lucid Lynx 10.04 LTS to Precise Pangolin 12.04.2 LTS yesterday.
It upgraded Grub from version 1.98 to 1.99.  I didn't restore my default grub but, I did take the installers version of every file it asked about.

When you have edited a file it asks if you want to keep your version or take the installers version.
Of course to get the full benefits of version 1.99 I took the installers version of **/etc/default/grub** and **/etc/grub.d/05_debian_theme**.

When it automatically did the update-grub command I seen an error on line 59 message and it would not have been bootable as it was.

When it asked to reboot to complete the upgrade I said no (n).

I then made my 06_custom file unexecutable: **sudo chmod -x /etc/grub.d/06_custom** and of course **sudo update-grub** and I got no errors.

So then I knew it was safe to reboot.
The customized 06_custom file from grub 1.98 _**will not work**_ with grub version 1.99 so I had to edit it like the wiki says for grub versions 1.99 and 2.00.

They only real operational difference I notice with grub 1.99 is when I select Windows 7 (or probably any windows os), I see an erroneous error:
```
Error: No argument specified.  

Press any key to contiue...
```which means nothing and you can just wait or press enter and it will go into windows just fine.

So, I guess the most important things are when doing an upgrade to a newer version of grub it to accept the installers versions of any file is asks about and also make 06_custom unexecutable.
You _**must**_ do this before you reboot if you see that grub has an error or it probably will boot with a grub rescue prompt.

---

### Post by Cavsfan on 2013-02-16
Added some info in the Introduction which is underlined about what to do if you do not restore your grub files
before upgrading from one version of Ubuntu  to another if the grub files are updated to another version.

---

### Post by bogan on 2013-02-16
Hi!, **Cavsfan**,

Pity I did not see your Yesterday's Post, before I updated/upgraded 12.04.1 to 12.04.2.

As my grub menus were already so corrupted, and I was doing a clean format & install, I did not think it mattered. Besides, I had forgotten your similar advice in the original 'How To'.

In fact I made a real snafu of it anyway, I had used 'tune2fs' to label the partitions, and got them the wrong way round; root & home!!

So I formatted the old home and installed 12.04.2 on it, and the new home went on top of 12.04.1.

It is a wonder any of it worked. The new Grub Menu had 69 entry lines, but the first 22 were OK !! Though it included two 12.04.2 entries, one for sda5 & the other for sda8. The later seemed to be perfectly normal. See my Post:
[http://ubuntuforums.org/showthread.php?t=2116405](http://ubuntuforums.org/showthread.php?t=2116405)

So I have reformatted both and reinstalled; now the new 12.04.2 Grub Menu has 88 entries, all except the first two are corrupt, but all are displayed.

Edit: I just checked the 12.04.2 fstab, and it had a extra swap entry which I deleted, & ran 'update-grub, but it made no difference.

But at least the Grub menus in my two 12.10 partitions are use-able, and apparently visually correct, as far as I have checked and tried them.

This despite the following command showing 43 entry lines when only the first 20 are displayed, the rest being corrupted. ```
grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
``` Do you know whether, if I delete the /boot/grub/grub.cfg file completely, a new one will be created by 'update-grub' ?, or should I delete only the corrupt text, leaving the skeleton file in place.??

Chao!,** bogan**.

---

### Post by oldfred on 2013-02-16
@bogan
If you keep going will you get an infinite number of entries?

The update grub always creates a new grub.cfg except when I had a typo in my 40_custom. Then it gave an error and wrote it with a different name something like grub.cfg.err.

I have so many old installs on several drives that I have to turn os-prober off. Then I add my own entries into 40_custom. I also learned from Ranch Hand, but cavsfan did a good job on documenting how to boot a partition not a specific kernel.

---

### Post by bogan on 2013-02-16
Hi!, **oldfred**,

I have run 'update-grub' 8 or 9 times since reinstalling and it has stuck at 88 lines.

There has been a conflict for a long time, ever since 12.10 was released and Grub Customizer could not handle the Additional Options sub-menus, and Grub 2.00 does not seem to like multiple Grubs in multiple drives, especially when three are running Grub 2.00 on different drives, and another is running Grub 1.99.

I saw a comment that Grub 2 does not check the hardware, but reads the already existing files and duplicates them. [I think from DRS305?]

At one stage, before the 12.04.2 snafu, I could only get into my external HDD, by Booting from BIOS to the UsbStick and using the Grub Menu there to boot into the Ext HDD.

At least that problem seems to have gone away.

Edit: I did not turn off os_prober as Cavsfan's system would not boot to external installations, it could not find the initial boot files and complained it needed a kernal to be installed first.
Chao!, **bogan**.

---

### Post by Cavsfan on 2013-02-16
> **oldfred said:**
> I also learned  from Ranch Hand, but Cavsfan did a good job on documenting how to boot a  partition not a specific kernel.

Thanks! :) When all of this made sense to me I asked Ranch Hand if he thought it would be a good idea to make a tutorial out of the concept and he thought it would. 
So I did it. It was actually a good thing it went to wiki as it had become convoluted and the wiki is fairly clear.
It will become much better after April when Grub 1.98 is no longer supported.

Through experience we learned that the custom entry will boot the last installed kernel and not the latest numbered kernel.

> **bogan said:**
> Hi!, **oldfred**,

I have run 'update-grub' 8 or 9 times since reinstalling and it has stuck at 88 lines.

There has been a conflict for a long time, ever since 12.10 was released and Grub Customizer could not handle the Additional Options sub-menus, and Grub 2.00 does not seem to like multiple Grubs in multiple drives, especially when three are running Grub 2.00 on different drives, and another is running Grub 1.99.

I saw a comment that Grub 2 does not check the hardware, but reads the already existing files and duplicates them. [I think from DRS305?]

At one stage, before the 12.04.2 snafu, I could only get into my external HDD, by Booting from BIOS to the UsbStick and using the Grub Menu there to boot into the Ext HDD.

At least that problem seems to have gone away.

Edit: I did not turn off os_prober as Cavsfan's system would not boot to external installations, it could not find the initial boot files and complained it needed a kernal to be installed first.
Chao!, **bogan**.

Bogan,
Leaving the 06_custom file executable will give you all of your original (custom) entries at the top plus the ones that display from 10_linux and 30_os-prober.
That will double (at least) the entries. 
My main concern was that upgrading from Lucid Lynx with Grub 1.98 to Precise Pangolin with Grub 1.99 was that the 06_custom file will not work with Grub 1.99.
As you well know. You are the one that got me to fix the tutorial. I was complacent with only Lucid Lynx 10.04 LTS installed on my PC and did not know that grub changed.
Drs305 originally pointed out the difference. Since then I have had each of the latest Ubuntus installed. 

I did not restore the default grub files as my own instructions said to do either. 

What alarmed me was after everything was upgraded to Precise and it did update-grub it said there was an error on line 59.
So, when it asked me to press Y to reboot, I knew that would end up bad. I pressed n instead and knew I had better fix it first.
I made 06_custom unexecutable and the output of update-grub then did not return any errors.
Then I rebooted. Everything was fine.
That is when I realized the vast difference between 06_custom in Grub 1.98 and 1.99.
I cheated a bit though as I had another Precise install and simply copied that over and edited it.

So, I guess if nothing else _always_ accept the installer's version of all of the grub files so that you benefit from the newer version but, _make sure you make 06_custom unexecutable_.
Then there should be no problems upon upgrading.

Drs305 also helped me partition my drive so that I could have this many installs and that was pretty tedious.
I had used Windows 7, Ubuntu Lucid, my swap and the extended partition as my 4 physical partitions.  
I did not know how to move more of the space from my windows partition over to the extended partition until Drs305 helped me.

This command is virtually worthless unless you have a 06_custom but, here is what I have: 

```
cavsfan@cavsfan-desktop:~$ cat /etc/grub.d/06_custom | grep menuentry | awk '{ print $1 " " $2 " " $3 }' | nl --starting-line-number=0
     0    menuentry "Precise Pangolin
     1    menuentry "Precise Pangolin
     2    menuentry "Lucid Lynx
     3    menuentry "Lucid Lynx
     4    menuentry "Precise Pangolin2
     5    menuentry "Precise Pangolin2
     6    menuentry "Quantal Quetzal
     7    menuentry "Quantal Quetzal
     8    menuentry "Raring Ringtail
     9    menuentry "Raring Ringtail
    10    menuentry "Windows 7"

```So, my main install is Precise at the top. I'll keep Lucid until April 13th. The 2nd Precise will become what ever the next version of Ubuntu is.
Then the order will be resequenced.  What is so cool about it is that the partitions may be all out of sequence but,
with the 06_custom file you can make them appear in any order you want. :D

---

### Post by bogan on 2013-02-17
HI!, **Cavsfan,**

Thanks for your response, I thought I should Post the actual GrubMenu grep output,as the pattern is clear. This from the Grub of my main hdd 12.10 having just altered the 'Titles' in its 06_custom file.

The actual 12.10 Grub Boot menu displays only the first 20 lines; whereas the 12.04.2 Grub 1.99-2ubuntu displays all of them, plus a lot more and garbage besides.```
:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0    menuentry "Quantal sda10" {
     1    menuentry "Quantal sda10 (Recovery)" {
     2    menuentry "Windows 7 on sda1" {
     3    menuentry "Quantal USB sdc2" {
     4    menuentry "Quantal USB sdc2 (Recovery)" {
     5    menuentry "Quantal EXT sdb7" {
     6    menuentry "Quantal EXT sdb7 (Recovery)" {
     7    menuentry "Precise 12.04.2 sda8" {
     8    menuentry "Precise 12.04.2 sda8 (Recovery)" {
     9    menuentry 'Ubuntu
    10    submenu 'Advanced options for Ubuntu
    11    menuentry 'Ubuntu, with Linux 3.5.0-24-generic
    12    menuentry 'Ubuntu, with Linux 3.5.0-24-generic (recovery mode)
    13    menuentry "Memory test (memtest86+)" {
    14    menuentry "Memory test (memtest86+, serial console 115200)" {
    15    menuentry 'Windows 7 (loader) (on /dev/sda1)
    16    menuentry 'Windows Recovery Environment (loader) (on /dev/sda4)
    17    menuentry 'Ubuntu 12.04.2 LTS (12.04)
    18    submenu 'Advanced options for Ubuntu 12.04.2 LTS (12.04)
    19    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (on /dev/sda8)
    20    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode) (on /dev/sda8)
  
 [ from EXT HDD sdb7, note titles are previous versions]

   21    menuentry 'Ubuntu 12.10 (12.10)
    22    submenu 'Advanced options for Ubuntu 12.10 (12.10)
    23    menuentry 'Quantal 12.10 USB sdc2 (on /dev/sdb7)
    24    menuentry 'Quantal 12.10 USB sdc2 (Recovery) (on /dev/sdb7)
    25    menuentry 'Quantal 12.10 sda10 (on /dev/sdb7)
    26    menuentry 'Quantal 12.10 sda10 (Recovery) (on /dev/sdb7)
    27    menuentry 'Quantal 12.10 EXT sdb7 (on /dev/sdb7)
    28    menuentry 'Quantal 12.10 EXT sdb7 (Recovery) (on /dev/sdb7)
    29    menuentry 'Precise 11.10 sda5 (on /dev/sdb7)
    30    menuentry 'Precise 11.10 sda5 (Recovery) (on /dev/sdb7)
    31    menuentry 'Ubuntu (on /dev/sdb7)
    32    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (on /dev/sdb7)
    33    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode) (on /dev/sdb7)
    34    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sdb7)
    35    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sdb7)
  
  [ from EXT _USB_ sdc2, note it has no 06-custom file]
  
    36    menuentry 'Ubuntu 12.10 (12.10)
    37    submenu 'Advanced options for Ubuntu 12.10 (12.10)
    38    menuentry 'Ubuntu (on /dev/sdc2)
    39    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (on /dev/sdc2)
    40    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode) (on /dev/sdc2)
    41    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sdc2)
    42    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sdc2)
    43    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sdc2)
:~$ 
```Nearly all of the entries with spurious '(on /dev/sdxX)' suffixes are corrupt inside and lead to 'initramfs' prompt hang ups, or no kernal found errors.

LInes 29 & 30 are ancient relics of an overlong night session.

I do not know if this clears things up a bit, or makes it even more obscure.

Chao!, **bogan.**

---

### Post by oldfred on 2013-02-17
If you are only seeing 20 lines is that video mode for grub.

And then do you have that little tiny arrow aat the lower right side of the box? That says you have more entries & can scroll down?

---

### Post by bogan on 2013-02-17
Hi!,** oldfred**,

Thanks for the suggestion.

My Grub is set to 1920x1080 and the grub box fills it except for an inch or so all round.

The20 lines - actually 21, as displayed - fills about a quarter of the box and there is no 'Little Arrow' visible.

I am not complaining - far from it - the rest of the 48 are effectively garbage.

Chao!, **bogan**.

---

### Post by Cavsfan on 2013-02-17
> **bogan said:**
> HI!, **Cavsfan,**

Thanks for your response, I thought I should Post the actual GrubMenu grep output,as the pattern is clear. This from the Grub of my main hdd 12.10 having just altered the 'Titles' in its 06_custom file.

The actual 12.10 Grub Boot menu displays only the first 20 lines; whereas the 12.04.2 Grub 1.99-2ubuntu displays all of them, plus a lot more and garbage besides.```
:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0    menuentry "Quantal sda10" {
     1    menuentry "Quantal sda10 (Recovery)" {
     2    menuentry "Windows 7 on sda1" {
     3    menuentry "Quantal USB sdc2" {
     4    menuentry "Quantal USB sdc2 (Recovery)" {
     5    menuentry "Quantal EXT sdb7" {
     6    menuentry "Quantal EXT sdb7 (Recovery)" {
     7    menuentry "Precise 12.04.2 sda8" {
     8    menuentry "Precise 12.04.2 sda8 (Recovery)" {
     9    menuentry 'Ubuntu
    10    submenu 'Advanced options for Ubuntu
    11    menuentry 'Ubuntu, with Linux 3.5.0-24-generic
    12    menuentry 'Ubuntu, with Linux 3.5.0-24-generic (recovery mode)
    13    menuentry "Memory test (memtest86+)" {
    14    menuentry "Memory test (memtest86+, serial console 115200)" {
    15    menuentry 'Windows 7 (loader) (on /dev/sda1)
    16    menuentry 'Windows Recovery Environment (loader) (on /dev/sda4)
    17    menuentry 'Ubuntu 12.04.2 LTS (12.04)
    18    submenu 'Advanced options for Ubuntu 12.04.2 LTS (12.04)
    19    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (on /dev/sda8)
    20    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode) (on /dev/sda8)
  
 [ from EXT HDD sdb7, note titles are previous versions]

   21    menuentry 'Ubuntu 12.10 (12.10)
    22    submenu 'Advanced options for Ubuntu 12.10 (12.10)
    23    menuentry 'Quantal 12.10 USB sdc2 (on /dev/sdb7)
    24    menuentry 'Quantal 12.10 USB sdc2 (Recovery) (on /dev/sdb7)
    25    menuentry 'Quantal 12.10 sda10 (on /dev/sdb7)
    26    menuentry 'Quantal 12.10 sda10 (Recovery) (on /dev/sdb7)
    27    menuentry 'Quantal 12.10 EXT sdb7 (on /dev/sdb7)
    28    menuentry 'Quantal 12.10 EXT sdb7 (Recovery) (on /dev/sdb7)
    29    menuentry 'Precise 11.10 sda5 (on /dev/sdb7)
    30    menuentry 'Precise 11.10 sda5 (Recovery) (on /dev/sdb7)
    31    menuentry 'Ubuntu (on /dev/sdb7)
    32    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (on /dev/sdb7)
    33    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode) (on /dev/sdb7)
    34    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sdb7)
    35    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sdb7)
  
  [ from EXT _USB_ sdc2, note it has no 06-custom file]
  
    36    menuentry 'Ubuntu 12.10 (12.10)
    37    submenu 'Advanced options for Ubuntu 12.10 (12.10)
    38    menuentry 'Ubuntu (on /dev/sdc2)
    39    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (on /dev/sdc2)
    40    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode) (on /dev/sdc2)
    41    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sdc2)
    42    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sdc2)
    43    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sdc2)
:~$ 
```Nearly all of the entries with spurious '(on /dev/sdxX)' suffixes are corrupt inside and lead to 'initramfs' prompt hang ups, or no kernal found errors.

LInes 29 & 30 are ancient relics of an overlong night session.

I do not know if this clears things up a bit, or makes it even more obscure.

Chao!, **bogan.**

Bogan,
I have found along with **Drs305's** help that when you re-install a Ubuntu it leaves **/etc/fstab** with more than one entry.
It will have where the ext4 was initially installed and where it is currently installed.
It also repeats swap files as well if you have more than one.

An admin here told me I just need one swap file and every time I install it will pick that swap file up.
So, I no longer have trouble with multiple swap files in fstab.

That would explain why it says everything is on sdb7 and sdc2. 
Not quite sure which fstab but, it is probably the install you are reporting these entries from.

So, I would start checking /etc/fstab files.
A simple way to check is with cat:

```
cavsfan@cavsfan-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=a162dc8a-e4df-4b79-b4c3-524761ff7ae1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=2a80f59e-e7c3-418e-aab2-ab5d19255a2f none            swap    sw              0       0

```You can even check fstab files on other installs:
This is while in Precise looking at Quantal:
```
cavsfan@cavsfan-desktop:~$ cat /media/Quantal/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=2a80f59e-e7c3-418e-aab2-ab5d19255a2f none            swap    sw              0       0

```

Hope this helps.

---

### Post by bogan on 2013-02-17
Hi!, **Cavsfan**,

Thanks for the response.

I was mind-full from our previous exchange of the need to check fstab, and I checked them all . Only the fstab of the newest install had an extra 'Swap', which I deleted, the other entries were all OK.

As previously, doing so did not change the Additional Option entries being suffixed by  spurious (on /dev/sdb7) or (on/dev/sdc2) suffixes, the scripts inside are also corrupted with altered hdxX -msdosX and sdxX values.

I worked out the answer to the puzzle of the 21 line display, out of 44:

The 21 lines includes 13 actual working Ubuntu OS entries, the rest are 4 Additional Option sub-menu lines and 4 Windows & Memtest lines.

The 44 include those, but also the expanded Additional Option sub-menus, and this is where the errors show up:

The base 12.10 and the new 12.04.2 expand correctly giving two lines each, normal & recovery; one shows the same pair, but adds three other entries, whilst the last shows, in addition, the whole list from the '06_custom' file in the external HDD, sdb7.

I am going to deactivate the '06-custom in sdb7, which I do not use - I can not boot from it directly - and see what difference it makes.

Chao!, **bogan**.

---

### Post by Cavsfan on 2013-02-17
> **bogan said:**
> Hi!, **Cavsfan**,

Thanks for the response.

I was mind-full from our previous exchange of the need to check fstab, and I checked them all . Only the fstab of the newest install had an extra 'Swap', which I deleted, the other entries were all OK.

As previously, doing so did not change the Additional Option entries being suffixed by  spurious (on /dev/sdb7) or (on/dev/sdc2) suffixes, the scripts inside are also corrupted with altered hdxX -msdosX and sdxX values.

I worked out the answer to the puzzle of the 21 line display, out of 44:

The 21 lines includes 13 actual working Ubuntu OS entries, the rest are 4 Additional Option sub-menu lines and 4 Windows & Memtest lines.

The 44 include those, but also the expanded Additional Option sub-menus, and this is where the errors show up:

The base 12.10 and the new 12.04.2 expand correctly giving two lines each, normal & recovery; one shows the same pair, but adds three other entries, whilst the last shows, in addition, the whole list from the '06_custom' file in the external HDD, sdb7.

I am going to deactivate the '06-custom in sdb7, which I do not use - I can not boot from it directly - and see what difference it makes.

Chao!, **bogan**.

Glad you are getting it figured out! Let me know how it goes.

---

### Post by bogan on 2013-02-18
Hi!, Cavsfan,

As I proposed, I deactivated the 06_custom file in the external HDD sb7 12.10 installation, and deleted the spurious entries in /boot/grub/grub.cfg, before running 'update-grub'.

I then went round all the installations and deleted similar files in each before running each 'update-grub' in turn.
This resulted in reducing the number of grub menu entries in 12.10, from 44 to 34, and those in 12.04.2 from 88 to 64, though of the latter, only the first few entries are normal and usable, the rest are single lines and either end at: "class os {" or " menuentries option-id".[ or something like that.]

Best of all it has got rid of the historical old entries for OS's & Partitions that no longer exist, and most of the duplicate entries. So that is a great improvement.

The spurious '( on /dev/sdxX)' suffixes still occur in the Additional Options sub-menus, but they have no effect; though the altered partition references, in the scripts, cause problems, I just have to remember which work and which need editing.

It seems clear that the combination of grub 1.99 & 2.00 with multiple drives, results in 12.04 being unable to handle the new sub-menus.

Chao!, **bogan**.

---

### Post by Cavsfan on 2013-02-19
> **bogan said:**
> It seems clear that the combination of grub 1.99 & 2.00 with multiple drives, results in 12.04 being unable to handle the new sub-menus.

Bogan, 
I am glad you are getting your system sorted out. The custom grub file does not look at any sub-menus.

The only way a sub-menu would display is if you have 10_linux executable.

It only looks at whatever you put in 06_custom which can only contain the latest installed kernel on each Ubuntu.
I do not believe that grub versions interfere with each other on other OSs.
If you have grub installed on your Precise install, your PC should be using Grub 1.99 and every OS should be looked at by the Grub that is installed on Precise.

If you have your grub installed on Quantal or Raring then Grub 2.00 will be in control. There is very little difference between 1.99 and 2.00 that I have found.

The one thing is the error (erroneous) when I select Windows 7. I just press enter or wait and it goes into Windows fine.

I remember Drs305 trying to help get rid of that erroneous error but, since he did not have any windows os, we did not get there from here.

But, what I am saying is that when you login to another Ubuntu that _does not_ have the grub installed on and enter sudo update-grub it does not effect the grub that appears at boot.

---

### Post by offgridguy on 2013-02-19
Interesting thread, I will have to try this, Thanks.

---

### Post by Cavsfan on 2013-02-19
> **offgridguy said:**
> Interesting thread, I will have to try this, Thanks.

You are welcome. :D Just a couple of things: when you get to the part that says to edit **/etc/grub.d/40_custom** be sure and save it as **/etc/grub.d/06_custom**, leaving **/etc/grub.d/40_custom** as is. 
Then make it executable and remember to enter **sudo update-grub**.

This way you have not really made any drastic changes. The custom menu will display at the top and all of the normal boot entries will display below that.

When you have made absolute sure everything works as expected in the custom section, then make **/etc/grub.d/20_memtest86+**, **/etc/grub.d/10_linux** and **/etc/grub.d/30_os-prober** unexecutable.

Then you will have a nice custom screen that appears at boot time and you never have to change it unless you want to or you add or remove a Ubuntu or another OS.
Or if you upgrade to another version of Ubuntu and the Grub version changes. The wiki has that covered too.
It works with Ubuntu, Debian, Mint, all Windows OSs and probably others.

---

### Post by bogan on 2013-02-19
Hi!, Cavsfan,

Thanks for your elucidation, I was aware of the facts and implications of what you describe, and that, by keeping 30_os-prober executable i was going against your advice.

I did so because the 06_custom entries for OS's on disks other than the host, would not work, giving ' the kernal must be installed first' or 'initrd file not found' messages.

You Posted:> But, what I am saying is that when you login to another Ubuntu that _does not_ have the grub installed on and enter sudo update-grub it does not effect the grub that appears at boot.     I agree that that is what is supposed to be the case, but the reverse is not the case if both  have their 30_os-prober files executable:
When 'sudo update-grub' is entered in a Ubuntu that does have grub installed on it, but does not have control, and that grub configuration is altered, the next time 'sudo update-grub' is entered in the Ubuntu that does have control, the changes to the non-controlling grub **will** be reflected in the grub that appears at boot, [And, of course, in the /boot/grub/grub.cfg files in both.]

That at least is my experience with both of my Desktop computers and is reflected in the improvement in the displayed menus following my described editing exercise.

it is also inevitable whilst grub takes its data from other drives from their existing files, rather than addressing the hardware & firmware. [Apologies if that is the wrong terminology, and for the convoluted sentences.]

Chao!, bogan,

---

### Post by Cavsfan on 2013-02-19
> **bogan said:**
> Hi!, Cavsfan,

Thanks for your elucidation, I was aware of the facts and implications of what you describe, and that, by keeping 30_os-prober executable i was going against your advice.

I did so because the 06_custom entries for OS's on disks other than the host, would not work, giving ' the kernal must be installed first' or 'initrd file not found' messages.

You Posted:I agree that that is what is supposed to be the case, but the reverse is not the case if both  have their 30_os-prober files executable:
When 'sudo update-grub' is entered in a Ubuntu that does have grub installed on it, but does not have control, and that grub configuration is altered, the next time 'sudo update-grub' is entered in the Ubuntu that does have control, the changes to the non-controlling grub **will** be reflected in the grub that appears at boot, [And, of course, in the /boot/grub/grub.cfg files in both.]

That at least is my experience with both of my Desktop computers and is reflected in the improvement in the displayed menus following my described editing exercise.

it is also inevitable whilst grub takes its data from other drives from their existing files, rather than addressing the hardware & firmware. [Apologies if that is the wrong terminology, and for the convoluted sentences.]

Chao!, bogan,

Bogan,
Thanks for that explication.  It does make sense that **sudo update-grub** would have an effect on **30_os-prober** and/or **10_linux** as well as the grub.cfg file when other drives with Ubuntus installed on them are involved.  
As update-grub would definitely have to examine those other drives and include what it finds.

I was just thinking about the **06_custom** file by itself along with only one drive. It cannot be altered by another Ubuntu.
I have edited another Ubuntu's **06_custom** file but, I knew that executing **sudo update-grub** would have to be performed while in that OS.

You must have a fairly prodigious system with so many installations.
I only have a 500GB drive with all of my systems on it. I have a 1TB USB drive but, I only use it for backing my windows 7 installation up which is done automatically once per week.
Of course I also use it to backup my Ubuntus if I need to re-install.

So, I guess you have your Grub all corrected now pointing to the right installs?

---

### Post by bogan on 2013-02-20
Hi!, Cavsfan,

You Posted: > So, I guess you have your Grub all corrected now pointing to the right installs?I wish!

The 06_custom entries now, and the other entries on the main OS grub menu, are all Ok, and the Additional Options sub menus are mostly correct. All the entries are OK in the USB stick.

The two 12.04 OS's on the Internal HDD are only correct for the host OS , Windows, & Mem test; the rest, all 58 of them, are garbage. An example of what they produce is this:```
>   65    menuentry "Precise 12.04.2 sda8 (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 
    66    menuentry "Precise 12.04.2 sda8 (Recovery) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 
    67    menuentry "Ubuntu (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 
    68    menuentry "Ubuntu, with Linux 3.5.0-24-generic (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 
    69    menuentry "Ubuntu, with Linux 3.5.0-24-generic (recovery mode) (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 
```However, as the only time I use those grubs is following a kernal or grub update, I can live with that.

In all this, two of the things  I have learnt are perhaps important enough to pass on in the Wicki:

First:
With multiple OS's on multiple drives capable of being booted from Bios boot selection, **only the main OS** should have** 06_custom** files activated, to avoid confusion. Especially if a drive is on a mobile HDD or USB stick,used with multiple computers.
This is because the 'sdxX' mount settings alter according to which drive is selected to boot from. For example: my USB back-up OS stick, can be sda, sdc, or sdf.

Second:
The 'spurious' suffixes on groups of menu entries, eg ( on sdb7) are not spurious at all, they tell you from which partition Grub got the data in that section, they do not have any effect on operation.

Chao!, **bogan.**

---

### Post by Cavsfan on 2013-02-20
Thanks Bogan. I'll try to incorporate that 1st one into the wiki when I can.
I don't really understand the 2nd one.

I have always been of the opinion that your main install should have the grub installed on it. 
But, because Precise uses Grub 1.99 which gives that error when selecting windows, 
I installed my grub on Quantal Quetzal 10.10 install which uses grub 2.00.

This is just my opinion but, I believe one should keep it simple and have all of your installs on one drive.

However having said that it is totally up to each individual but, perhaps this custom Grub setup may not 
be for those as yourself who have usb sticks, etc. connected with operating systems installed on them.

But, what would you have if you made all of your **06_custom** files unexecutable and **10_linux** and **30_os-prober** files executable? 
I believe you said it would be a huge mess.
That is not the fault of this wiki's effects. Didn't you say you had used grub-customizer and have things left over from that?
It would seem to be an inherent problem to Ubuntu/Linux having a combination of hard drives, usb sticks, etc. with many Ubuntus installed on them 

I have a 500GB drive: about 300GB is used by windows 7, about 60 or 80GB for my main Precise install and approximately 20GB set aside for each of my other 4 Ubuntus.
I could even free up more from my windows partition if I wanted.

But, I don't use all 5 Ubuntus. I have them installed so I can *try* to keep up with the wiki.
So, why have so many installs?  That is a rhetorical question but, you see my point.

---

### Post by bogan on 2013-02-21
Hi!, **Cavsfan**,

You Posted:```
 So, why have so many installs? 
```In order to answer forum queries with info relevant to the OP's actual situation, and in order to back-up and to transfer data from one computer to another,  which are not on the same network, and without Internet or Cloud.

I agree that I am sure some of my problems resulted from Grub Customizer not being able to deal with the Grub2 Additional Options sub-menus. I have not tried the latest version of GC - too risky.

The one thing I really do not understand is that some of the corruption was from entries for OS's and partitions that have not existed for months, if not years.

If I had a choice, I would only have Grub on the main OS of the main HDD and the USB; but I do not have that choice as kernal updates reinstall and update the Grub in the OS being updated.

Chao!, **bogan.**

---

### Post by oldfred on 2013-02-21
I always turn off os-prober and just use my own 40_custom. But I do not boot into my other installs often, and most of them I have set to install to sda, but my BIOS boots from sdc, so any reinstall to sda does not matter.

But someone posted that if you uncheck (with spacebar) all entries, grub will not reinstall to any MBR. I have not tried it.

       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

    
       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

---

### Post by bogan on 2013-02-21
Hi!, **oldfred,**

You Posted: > But someone posted that if you uncheck (with spacebar) all entries, grub will not reinstall to any MBR. I have not tried it.Does that mean 'uncheck all entries' in sudo dpkg-reconfigure grub-pc?.

If so, would one not have to run 'sudo dpkg-reconfigure grub-pc' from every OS installed, except the one selected as Main?

Even then, I would have thought that an update to Grub, or a kernal update, would still upset things, as it does not give an option to choose where grub is to go.

Chao!, **bogan**.

---

### Post by oldfred on 2013-02-21
It is every other install that you would have to run the dpkg command. You can check where grub will reinstall.

This is my laptop so it does not show much.

```
fred@A105-Precise:~$ sudo debconf-show grub-pc
[sudo] password for fred: 
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* [COLOR=Red]grub-pc/install_devices: /dev/disk/by-id/ata-FUJITSU_MHV2160BT_PL_NY07T6A28HNP[/COLOR]
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10

```

---

### Post by Cavsfan on 2013-02-21
> **bogan said:**
> Hi!, **Cavsfan**,

You Posted:```
 So, why have so many installs? 
```In order to answer forum queries with info relevant to the OP's actual situation, and in order to back-up and to transfer data from one computer to another,  which are not on the same network, and without Internet or Cloud.

I agree that I am sure some of my problems resulted from Grub Customizer not being able to deal with the Grub2 Additional Options sub-menus. I have not tried the latest version of GC - too risky.

The one thing I really do not understand is that some of the corruption was from entries for OS's and partitions that have not existed for months, if not years.

If I had a choice, I would only have Grub on the main OS of the main HDD and the USB; but I do not have that choice as kernal updates reinstall and update the Grub in the OS being updated.

Chao!, **bogan.**

I understand Bogan, I was not trying to come off as being indifferent to your situation.
I hope you get it all sorted out.

> **oldfred said:**
> I always turn off os-prober and just use my own 40_custom. But I do not boot into my other installs often, and most of them I have set to install to sda, but my BIOS boots from sdc, so any reinstall to sda does not matter.

But someone posted that if you uncheck (with spacebar) all entries, grub will not reinstall to any MBR. I have not tried it.

       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

    
       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

Thanks Oldfred for the commands. I don't want to attempt the first command.
The second didn't return anything I could understand but the third command returned where my grub is installed (sda7 Quantal) although I am on Raring: :D

```
cavsfan@cavsfan-MS-7529:~$ sudo debconf-show grub-pc
[sudo] password for cavsfan: 
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-Hitachi_HDP725050GLA360_GEA534RJ04DU5A
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10
cavsfan@cavsfan-MS-7529:~$ sudo grub-probe -t device /boot/grub
/dev/sda7
cavsfan@cavsfan-MS-7529:~$ 
```

---

### Post by bogan on 2013-02-21
@**oldfred**,  Thanks for that.

Hi!, **Cavsfan**,

You Posted: > But, what would you have if you made all of your **06_custom** files unexecutable and **10_linux** and **30_os-prober** files executable? 
I believe you said it would be a huge mess.I was not in anyway intending to imply that your Wicki was in anyway the cause of any of my 'huge mess'.

On the contrary it now fully serves the function for which I installed it: to give labels to the device launchers, and to identify the device entries in the Grub menu.

The problems I had with it - at first - were a function of my multible drives and the resulting changes in the Mount names the various OS's were given depending on which Boot drive was selected in Bios, and which Ports removable drives were plugged into. Once I had sorted that out and deactivated all but the Main OS **06_custom**, it worked faultlessly.

The answer to your question is that with all the ** 06_custom** files deactivated I get a fully useable menu with 12.10, but which has two disadvantages: 
First: ubuntu entries apear as just: "Ubuntu" or Ubuntu 12.04.2 or 12.10", and it is necessary to open the Additional submenu to tell which is which, if more than one installation of the same version exists.

Second, some of the submenus have extra entries below the normal three, and some of them work, some do not, for reasons I do not understand; for example, one boots to the main 12.10 OS, but with a very low-res screen, too big for the display, which can not be scrolled to access things, and no GLX, so no launchers or panels.

But as those extra entries are redundant I can just ignore them, now that I have reduced the irritating 'huge mess' to a slight itch. Though the 12.04 menu is still only functional for the first Ubuntu, Memtest & Windows. 

Thanks for putting up with my tortuous explanations.

Chao!, **bogan.**

---

### Post by Cavsfan on 2013-02-22
> **bogan said:**
> @**oldfred**,  Thanks for that.

Hi!, **Cavsfan**,

You Posted: I was not in anyway intending to imply that your Wicki was in anyway the cause of any of my 'huge mess'.

On the contrary it now fully serves the function for which I installed it: to give labels to the device launchers, and to identify the device entries in the Grub menu.

The problems I had with it - at first - were a function of my multible drives and the resulting changes in the Mount names the various OS's were given depending on which Boot drive was selected in Bios, and which Ports removable drives were plugged into. Once I had sorted that out and deactivated all but the Main OS **06_custom**, it worked faultlessly.

The answer to your question is that with all the ** 06_custom** files deactivated I get a fully useable menu with 12.10, but which has two disadvantages: 
First: ubuntu entries apear as just: "Ubuntu" or Ubuntu 12.04.2 or 12.10", and it is necessary to open the Additional submenu to tell which is which, if more than one installation of the same version exists.

Second, some of the submenus have extra entries below the normal three, and some of them work, some do not, for reasons I do not understand; for example, one boots to the main 12.10 OS, but with a very low-res screen, too big for the display, which can not be scrolled to access things, and no GLX, so no launchers or panels.

But as those extra entries are redundant I can just ignore them, now that I have reduced the irritating 'huge mess' to a slight itch. Though the 12.04 menu is still only functional for the first Ubuntu, Memtest & Windows. 

Thanks for putting up with my tortuous explanations.

Chao!, **bogan.**

No problem Bogan! Take care and I hope you are able to manage all of your installations now,

---

### Post by Cavsfan on 2013-02-25
The community wiki to create a custom Grub2 menu may be down part of the day on Feb 28th.
The same day the forum will be down part of the day. I need to make some minor changes, which should not take very long.
:popcorn:

---

### Post by Cavsfan on 2013-02-26
I almost made a huge mistake the other day. I wanted to delete my 2nd Precise install.
So, I had Gparted up and was about to delete sda5. Then a stroke of luck occurred. ;) I realized I would be looking at grub rescue if I completed that operation.

At least I believe that is what would have happened.

My grub was installed on Quantal sda7 and the partitions would have all resequenced if I deleted sda5.

So I just formatted sda5 as ext4 instead preserving the partition sequence. :D

Then I just had to edit /etc/grub.d/06_custom and removed a couple of menuentries.
I also remembered to edit /etc/default/grub and subtracted the default line number by 2.

I am learning. :D

---

### Post by von Stalhein on 2013-02-27
> **Cavsfan said:**
> I almost made a huge mistake the other day. I wanted to delete my 2nd Precise install.

*snip snip snip*

I am learning. :D

Good!!!!

I am a huge fan of learning, and have done it many a time. In this case I'm more than happy for you to "learn" first and then tell us!!!
):P

---

### Post by Cavsfan on 2013-02-28
I just edited the comunity wiki section 4 to refer to the grub version number vs. the Ubuntu version. I will clean it up a lot more replacing 
Ubuntu version with Grub version in April when support for Oneiric Ocelot Ubuntu 11.10 and Lucid Lynx Ubuntu 10.04.4 LTS are dropped.
Then it will be just Grub version 1.99 which Precise Pangolin 12.04 LTS uses and Grub version 2.00 which everything after that uses.
There is only minor differences between Grub version 1.99 and Grub version 2.00.

---

### Post by Cavsfan on 2013-03-13
With today's update of grub-pc in Raring, I accepted the installer's  version (which one should always do to get the full benefit of the  update) of **/etc/default/grub** and **/etc/grub.d/05_debian_theme** and then modified them again.
In **05_debian_theme** the font colors moved from after line [COLOR=#ff0000]108[/COLOR] to after line [COLOR=#ff0000]114[/COLOR].

If you ever encounter an error while either the system is updating grub or you enter **sudo update-grub** you should make the **06_custom** file unexecutable and then make **10_linux** and **30_os-prober** executable.
[B]sudo chmod -x /etc/grub.d/06_custom
sudo chmod +x /etc/grub.d/10_linux
sudo chmod +x /etc/grub.d/30_os-prober
[/B]
Always remember to enter **sudo update-grub** or the changes will not  take effect. You do not want to re-boot with an error coming from grub.  If you do you will probably be looking at grub recovery.
Then make the changes to the updated files.
Since Raring is still pre-release I will not update the community wiki until it is released in April.

---

### Post by ChinaJustin on 2013-03-14
Hey, Cavsfan:

OK, so I'm using Mint 13 which has Grub 1.99.

I just updated the kernel, because this laptop I'm using has had some random hardware glitches, and I'm hoping that it was simply the older kernel version that comes with LM13.

But, just in case the newer kernel borked my system, I chmod -x'd the 10_linux file, installed the new kernel, then ran update-grub. Now, when Grub comes up, I have:

Linux Mint 13
Linux Mint 13 (recovery)
Windows 7
Linux Mint Maya (and then the new kernel version)
Linux Mint Maya (new kernel) (recovery)
Previous versions of Linux
(when you select the above, you get:)
Linux Mint Maya (previous kernel)
Linux Mint Maya (previous kernel) (recovery)

Now, the first two LM 13 entries are the new kernel, which is working fine so far. My questions are:

1) Is there any way to NOT have the second set of LM entries? I mean, my custom menu already gives me the newest kernel version, no need to have redundant entries for it. However, I do want to keep the entries for the previous kernels just in case.
2) How can I move the previous kernels so that they're all on the first/main menu (i.e. not have the "Previous versions of Linux" menu choice)?

---

### Post by Cavsfan on 2013-03-14
> **ChinaJustin said:**
> Hey, Cavsfan:

OK, so I'm using Mint 13 which has Grub 1.99.

I just updated the kernel, because this laptop I'm using has had some random hardware glitches, and I'm hoping that it was simply the older kernel version that comes with LM13.

But, just in case the newer kernel borked my system, I chmod -x'd the 10_linux file, installed the new kernel, then ran update-grub. Now, when Grub comes up, I have:

Linux Mint 13
Linux Mint 13 (recovery)
Windows 7
Linux Mint Maya (and then the new kernel version)
Linux Mint Maya (new kernel) (recovery)
Previous versions of Linux
(when you select the above, you get:)
Linux Mint Maya (previous kernel)
Linux Mint Maya (previous kernel) (recovery)

Now, the first two LM 13 entries are the new kernel, which is working fine so far. My questions are:

1) Is there any way to NOT have the second set of LM entries? I mean, my custom menu already gives me the newest kernel version, no need to have redundant entries for it. However, I do want to keep the entries for the previous kernels just in case.
2) How can I move the previous kernels so that they're all on the first/main menu (i.e. not have the "Previous versions of Linux" menu choice)?

Enter in terminal **cd /etc/grub.d/** and then enter **ls -l** and you should see what is executable.
I'm pretty sure the other entries are coming from **/etc/grub.d/30_os-prober** - chmod -x that file too. **gksu chmod -x /etc/grub.d/30_os-prober**
As the **06_custom** file contains only what you put in it and displays only what you put between the quote marks. Also it can only contain the most recent kernel and it's recovery.
If you only have the **06_custom **file executable, you will never see "Previous versions of Linux", etc.

---

### Post by ChinaJustin on 2013-03-14
Yeah, my bad. I meant 30_os-prober. Fingers got ahead of my brain!

But see, I *want* the entries showing my **previous** kernels, just not the current one (since again, that's in my customized menu already). Is there any way to do that?

And I want ALL entries showing on the FIRST menu. Or are previous versions ALWAYS on a separate menu, while all other installs are on the main menu?

For example, here's what I want:

Linux Mint 13 *(which is the current kernel obviously from my 06_custom file)*
Linux Mint 13 (recovery)
Windows 7
Linux Mint 13 *(previous kernel, **not** kernel from the above)*
Linux Mint 13 *(same, but with "recovery")*
*and then however many more kernels I may install*

And that's it ... no "Previous Linux Versions" or anything. Your example of all your installs shows **no** "Previous Versions" selection. I'm assuming that that is because they are separate installs, NOT different kernels? And that if you had other kernels listed, they, too, would show up on some "Previous Versions" selection?

---

### Post by Cavsfan on 2013-03-14
> **ChinaJustin said:**
> Yeah, my bad. I meant 30_os-prober. Fingers got ahead of my brain!

But see, I *want* the entries showing my **previous** kernels, just not the current one (since again, that's in my customized menu already). Is there any way to do that?

And I want ALL entries showing on the FIRST menu. Or are previous versions ALWAYS on a separate menu, while all other installs are on the main menu?

For example, here's what I want:

Linux Mint 13 *(which is the current kernel obviously from my 06_custom file)*
Linux Mint 13 (recovery)
Windows 7
Linux Mint 13 *(previous kernel, **not** kernel from the above)*
Linux Mint 13 *(same, but with "recovery")*
*and then however many more kernels I may install*

And that's it ... no "Previous Linux Versions" or anything. Your example of all your installs shows **no** "Previous Versions" selection. I'm assuming that that is because they are separate installs, NOT different kernels? And that if you had other kernels listed, they, too, would show up on some "Previous Versions" selection?

Actually, there is no way to display previous kernels and have them selectable. I have never needed to get to an older kernel although I have always kept the 2 newest kernels. 
If I did I would temporarily make 10_linux or in your case 30_os-prober executable. Then when finished I would make them unexecutable.
The whole point of the "Custom Grub2 Menu" was to display the most recently installed kernel for each Ubuntu or Linux OS and recovery for that kernel plus a WIndows entry if you have one.

If you want the other kernels to display you will have to leave 30_os-prober in the mix. There is no other way around it.

---

### Post by ChinaJustin on 2013-03-14
Fair enough. And I'm guessing the selectable "second" menu of "Previous Linux Versions" (wherein all additional kernels are shown) is set, too? No way to get it all onto just one page of the menu?

---

### Post by Cavsfan on 2013-03-14
> **ChinaJustin said:**
> Fair enough. And I'm guessing the selectable "second" menu of "Previous Linux Versions" (wherein all additional kernels are shown) is set, too? No way to get it all onto just one page of the menu?

There is no way that I see to get previous kernels as in the submenus to display in this custom menu. How many times do you need to boot into older kernels anyway? I can't recall once myself.

---

### Post by oldfred on 2013-03-14
In root there is the link to the current kernel, but there is also a like to the most previous kernel.

Link in / :
 initrd.img.old
Viewing properties of link with my system I see this:
/boot/initrd.img-3.2.0-37-generic

But I have never need that link, as I would not normally want to boot older kernel.

---

### Post by Moose on 2013-03-14
Instead of going through all of this tedious crap, why don't you just install Super Boot Manager and use it to install Burg? It has a themes repository with some pretty decent themes, all easily editable.

---

### Post by oldfred on 2013-03-15
I do not believe burg is maintained. Last update was Oct 2010.

---

### Post by Cavsfan on 2013-03-15
> **oldfred said:**
> But I have never needed that link, as I would not normally want to boot older kernel.

My point exactly Oldfred! I have never needed or wanted to boot into an older kernel.

> **Moose said:**
> Instead of going through all of this tedious crap, why don't you just install Super Boot Manager and use it to install Burg? It has a themes repository with some pretty decent themes, all easily editable.

If you think this is tedious, it is not for you. BTW, no one is forcing you to use this method. I simply wanted a way to have the default line be static; not dynamic. Which is precisely what this method does.

> **oldfred said:**
> I do not believe burg is maintained. Last update was Oct 2010.

As Oldfred mentions burg is not maintained. Maybe use Grub Customizer. See how that works out for you.

---

### Post by deadflowr on 2013-03-15
Yep, this thread is about customizing the grub2 boot menu.
If you want to trick out your theme, look here:

[http://ubuntuforums.org/showthread.php?t=1823915&highlight=grub+themes](http://ubuntuforums.org/showthread.php?t=1823915&highlight=grub+themes)

---

### Post by Cavsfan on 2013-03-15
> **deadflowr said:**
> Yep, this thread is about customizing the grub2 boot menu.
If you want to trick out your theme, look here:

[http://ubuntuforums.org/showthread.php?t=1823915&highlight=grub+themes](http://ubuntuforums.org/showthread.php?t=1823915&highlight=grub+themes)

That is good. Drs305 is a friend of mine. Not sure who will maintain that thread though as he is now retired.

This method customizes the Grub2 selections, changes the font, font size, font colors and adds a background pitcture.
Here is my most recent Grub picture for Precise Pangolin 12.04 LTS. I had the same one on all my installs but, that was confusing so I did this.

[[IMG]http://ompldr.org/taHJwaQ[/IMG]]("http://ompldr.org/vaHJwaQ/Precise-grub-small.JPG")

The beauty is that no matter what kernels get installed on any of the 4 Ubuntus, the default line will never ever change.
This method may appear to be daunting but, it comes down to what is in one file **/etc/grub.d/06_custom** and a couple of other minor changes that need to be made.

---

### Post by deadflowr on 2013-03-15
> **Cavsfan said:**
> That is good. Drs305 is a friend of mine. Not sure who will maintain that thread though as he is now retired.

This method customizes the Grub2 selections, changes the font, font size, font colors and adds a background pitcture.
Here is my most recent Grub picture for Precise Pangolin 12.04 LTS. I had the same one on all my installs but, that was confusing so I did this.

[[IMG]http://ompldr.org/taHJwaQ[/IMG]]("http://ompldr.org/vaHJwaQ/Precise-grub-small.JPG")

The beauty is that no matter what kernels get installed on any of the 4 Ubuntus, the default line will never ever change.
This method may appear to be daunting but, it comes down to what is in one file **/etc/grub.d/06_custom** and a couple of other minor changes that need to be made.

I think grubthemeartist has done a good job of keeping up with newer themes on that thread.
I agree the custom menu setup is a great thing.
I have a precise, and kubuntu precise, a quantal, and a raring (plus a windows xp) on my system, and without utilizing the custom file, finding the right distro took some special attention to kernel versions.
Now all distros are well defined, and I click far less to boot.
And simplfied booting is what it's supposed to be about.
Themes and fonts and backgrounds, though nice, aren't nearly as important to me as getting into the OS want I quickly.

---

### Post by Cavsfan on 2013-03-15
> **deadflowr said:**
> I agree the custom menu setup is a great thing.
I have a precise, and kubuntu precise, a quantal, and a raring (plus a windows xp) on my system, and without utilizing the custom file, finding the right distro took some special attention to kernel versions.
Now all distros are well defined, and I click far less to boot.
And simplfied booting is what it's supposed to be about.
Themes and fonts and backgrounds, though nice, aren't nearly as important to me as getting into the OS want I quickly.

This method does exactly that: allows you to get to the OS of your choice quickly.

How much easier is hitting enter or moving the cursor up or down with the arrow keys to get to the OS of your choice?
This thread is about **How to have a custom Grub2 menu that is maintenance free**.

If your not going to post questions, etc. *_pertaining to this thread_* I suggest you create your own thread.

---

### Post by deadflowr on 2013-03-15
> [COLOR=#000000]This thread is about [/COLOR]**How to have a custom Grub2 menu that is maintenance free.**

Got it.
Here's a question.
Last night, I decided to see about adding a menuentry for the .old file in the root directory, as oldfred mentioned.
It works fine, but I get the same message when hitting enter as I do booting into windows.

You know, that whole something something, press enter to continue thing.
```
menuentry "Good Kernel" {    set root=(hd0,1)
        linux /vmlinuz.old root=/dev/sda1 ro quiet splash
        initrd /boot/initrd.img.old
}
```
 
Do you think I'd have to do anything to the entry to avoid that?

---

### Post by oldfred on 2013-03-15
I get that error also on several of my newer installs. It slows boot but other than that I have not determined what the issue is. I thought for a while is was search for UUID line, but you so not have search in your entry, just a device setting.

---

### Post by Cavsfan on 2013-03-16
> **deadflowr said:**
> Got it.
Here's a question.
Last night, I decided to see about adding a menuentry for the .old file in the root directory, as oldfred mentioned.
It works fine, but I get the same message when hitting enter as I do booting into windows.

You know, that whole something something, press enter to continue thing.
```
menuentry "Good Kernel" {    set root=(hd0,1)
        linux /vmlinuz.old root=/dev/sda1 ro quiet splash
        initrd /boot/initrd.img.old
}
```
 
Do you think I'd have to do anything to the entry to avoid that?

> **oldfred said:**
> I get that error also on several of my newer installs. It slows boot but other than that I have not determined what the issue is. I thought for a while is was search for UUID line, but you so not have search in your entry, just a device setting.

That erroneous error is mentioned in the wiki in Section 4.6 when selecting Windows:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Selecting_Windows_from_Grub_1.99](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Selecting_Windows_from_Grub_1.99)

Is that the error you are talking about?

You can either wait or just press enter again and it goes ahead and does it.

I haven't seen it when selecting anything but Windows myself.
That is the only thing I don't like about Grub version 1.99. Grub 1.98 and 2.00 do not get that error.

---

### Post by oldfred on 2013-03-16
That is the error I get on some of my boots, but it is not Windows.

I think it is my desktop boot from 12.04 to 12.10 both on my SSD. But I have to check and cannot do that until next week. (in Fla on laptop).

---

### Post by deadflowr on 2013-03-16
Yep, grub 1.99.

grub 2.00 runs it as normal as the rest of the entries.

At this point it's more of an academic curiosity then a necessity.

Normally, I'd pull a Joe Dirt and say, "Why does it do that? well cuz it just does."  

But my interest in it was little above normal.

It's doubtful that I'll ever boot into it (knock on wood for the stable kernels), but maybe someone who needs/wants an older kernel can glean something from it.

---

### Post by Cavsfan on 2013-03-17
> **oldfred said:**
> That is the error I get on some of my boots, but it is not Windows.

I think it is my desktop boot from 12.04 to 12.10 both on my SSD. But I have to check and cannot do that until next week. (in Fla on laptop).

Only selecting Windows 7 gives me that error. Selecting the other Ubuntu versions never has.

> **deadflowr said:**
> Yep, grub 1.99.

grub 2.00 runs it as normal as the rest of the entries.

At this point it's more of an academic curiosity then a necessity.

Normally, I'd pull a Joe Dirt and say, "Why does it do that? well cuz it just does."  

But my interest in it was little above normal.

It's doubtful that I'll ever boot into it (knock on wood for the stable kernels), but maybe someone who needs/wants an older kernel can glean something from it.

I guess it would be logical for initrd.img.old and vmlinuz.old to provide the ability to boot into the previously installed kernel and that is fine if anyone wants to incorporate that into their menu.
But, I will leave that out of my wiki. I have never had the need to boot into an older kernel and if I did I would boot into recovery and make the appropriate files 10_linux or 30_os-prober executable.

---

### Post by Cavsfan on 2013-03-17
Thanks **deadflowr** for figuring this out.

**ChinaJustin**, this should work on Mint as well. I'm not going to try this myself, but **deadflowr** has and it worked.
Here would be the **06_custom** file for Grub 1.99 with just Precise and Windows or Mint and Windows as the text just displays whatever you desire:

```
#!/bin/sh
echo 1>&2 "Adding Precise Pangolin 12.04 Newest Kernel, Precise Pangolin 12.04 Previous Kernel and Windows"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Precise Pangolin 12.04 Newest Kernel" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 Newest Kernel (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro single
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 Previous Kernel" {
    set root=(hd0,2)
        linux /vmlinuz.old root=/dev/sda2 ro quiet splash
        initrd /initrd.img.old
}
menuentry "Precise Pangolin 12.04 Previous Kernel (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz.old root=/dev/sda2 ro single
        initrd /initrd.img.old
}
menuentry "Windows" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}
```

With the only difference being ".old" at the end. I am not going to add this to the wiki but, feel free to add it to your custom grub if you want to.
You can see here from the symlinks how it should technically work:

```
cavsfan@cavsfan-desktop:/$ ls -l | grep "initrd";ls -l | grep "vmlinuz"
drwxr-xr-x   2 root root  4096 Feb  7 10:57 initrd
lrwxrwxrwx   1 root root    33 Feb 19 15:35 initrd.img -> /boot/initrd.img-3.2.0-38-generic
lrwxrwxrwx   1 root root    33 Feb 14 15:52 initrd.img.old -> /boot/initrd.img-3.2.0-37-generic
lrwxrwxrwx   1 root root    29 Feb 19 15:35 vmlinuz -> boot/vmlinuz-3.2.0-38-generic
lrwxrwxrwx   1 root root    29 Feb 14 15:52 vmlinuz.old -> boot/vmlinuz-3.2.0-37-generic
```

---

### Post by Cavsfan on 2013-03-19
The previous post from Precise which describes how to be able to boot into the previous kernel appears to only hold true for Precise, maybe Grub 1.99.
I have been in Lucid, Quantal  and Raring and the boot files all pointed to the same most recently installed kernel.
In Raring this is what it shows:

```
cavsfan@cavsfan-MS-7529:~$ cd /
cavsfan@cavsfan-MS-7529:/$ ls -l | grep "initrd";ls -l | grep "vmlinuz"
lrwxrwxrwx   1 root root    32 Mar 19 14:29 [COLOR=#ff0000]initrd[/COLOR].img -> boot/[COLOR=#ff0000]initrd[/COLOR].img-3.5.0-26-generic
lrwxrwxrwx   1 root root    33 Mar 19 14:29 [COLOR=#ff0000]initrd[/COLOR].img.old -> /boot/[COLOR=#ff0000]initrd[/COLOR].img-3.5.0-26-generic
lrwxrwxrwx   1 root root    29 Mar 19 14:29 [COLOR=#ff0000]vmlinuz[/COLOR] -> boot/[COLOR=#ff0000]vmlinuz[/COLOR]-3.5.0-26-generic
lrwxrwxrwx   1 root root    29 Mar 19 14:29 [COLOR=#ff0000]vmlinuz[/COLOR].old -> boot/[COLOR=#ff0000]vmlinuz[/COLOR]-3.5.0-26-generic

```

Even the vmlinuz.old file points to the 26 kernel. You can play around with this if you want, but I am not going to invest any more time dealing with older kernels.
This may be why "ro single" will work for recovery on Grub 1.98 and 1.99 but, recovery on Grub 2.00 requires "ro recovery nomodeset" on the recovery line. (Thanks to **Bogan** for finding this out.)
I have never needed to boot into an older kernel so I am going to let this die right here. :KS

---

### Post by xraynetcontrol on 2013-03-21
awesome, thank you very much for this!

---

### Post by Cavsfan on 2013-03-21
> **xraynetcontrol said:**
> awesome, thank you very much for this!

You are welcome! :)

---

### Post by Cavsfan on 2013-03-23
I installed Linux Cinnamon 14 Nadia and incorporated it into the menu. It also uses Grub 2.00 and worked well with this guide.
I'll post a screenshot later. :)

---

### Post by Cavsfan on 2013-03-24
The only real difference in Linux Mint Grub I found is that you have to make **/etc/grub.d/06_mint_theme** unexecutable in order to get the font colors from **/etc/grub.d/05_debian_theme** to work.
Or else you will have your font colors at the bottom but, the menu colors will be white.

---

### Post by Cavsfan on 2013-03-24
There are times when you have to be able to see where things in Grub are coming from and you can do that by looking at the output of **sudo grub-mkconfig **but, sometimes the output is too long to show in terminal. 
I entered **sudo grub-mkconfig > mkconfig-output** to produce an output that can then be opened with gedit to view. It saved to my home directory.

---

### Post by Cavsfan on 2013-03-24
Here is my latest custom grub2 menu on Linux Mint Grub version 2.00:

[[IMG]http://ompldr.org/taHZieg[/IMG]]("http://ompldr.org/vaHZieg/DSCN2584-s.JPG")

That is the same Grub version as Quantal Quetzal 12.10 has I believe.
I like the dark pictures with the cyan fonts. :)

---

### Post by Cavsfan on 2013-04-15
One final custom Grub2 screen with Lucid Lynx before it's EOL on May 9th.
This time they are all in sequence even though they are not in sequence on the partitions. ;)

[[IMG]http://ompldr.org/taTN0bg[/IMG]]("http://ompldr.org/vaTN0bg/DSCN2586small.JPG")


```
cavsfan@cavsfan-MS-7529:~$ sudo blkid
[sudo] password for cavsfan: 
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Precise" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" 
/dev/sda3: UUID="2a80f59e-e7c3-418e-aab2-ab5d19255a2f" TYPE="swap" 
/dev/sda5: LABEL="Linux Mint" UUID="b796e378-c9dd-4557-825b-5d5687197609" TYPE="ext4" 
/dev/sda6: LABEL="Quantal" UUID="4d6a25ba-5a4b-4da4-8ae1-9939bc6b6b4c" TYPE="ext4" 
/dev/sda7: LABEL="Raring" UUID="331d2bf4-1749-435a-a218-1c90dee537db" TYPE="ext4" 
/dev/sda8: LABEL="Lucid" UUID="570f351d-6da3-4540-86b6-e12a400f7f44" TYPE="ext4" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs" 
```

---

### Post by Cavsfan on 2013-04-25
The wiki will be down for a few minutes to update it with Raring Ringtail 13.04 which was released today.

Finished. Just made a few changes in the **Editing /etc/grub.d/05_debian_theme** section.

---

### Post by Cavsfan on 2013-04-26
After installing the final release of Raring Ringtail 13.04 yesterday I was perplexed in that I could not get a picture to work.
It would be listed in the output of **sudo update-grub** but neither the picture or the font colors would show up at boot time.

The font colors listed after line 114 in **/etc/grub.d/05_debian_theme** are dependent on the picture being found in **/boot/grub/** and the picture was there.

I ended up this morning just using another picture that I had previously used. So, I do not know why some pictures work and others will not.

But, that is the case.

---

### Post by Cavsfan on 2013-05-10
I will have to work on the wiki today to remove the parts about Grub 1.98 from Lucid Lynx which reached EOL yesterday May 9th 2013.

---

### Post by fantab on 2013-05-10
I have found particularly pictures with extension .jpeg don't work, while .jpg and .png work. Atleast for me .jpeg doesn't work.

Thanks for the great WIKI...

---

### Post by Cavsfan on 2013-05-10
I believe I have it updated correctly. There is just one reference to Lucid and that is an old example picture of a grub2 screen.
As for the recovery line sometimes **ro single** works and sometimes **ro recovery nomodeset** is what it takes.

---

### Post by Cavsfan on 2013-05-10
Added Saucy to the mix.  :D

[[IMG]http://ompldr.org/taWQ4bw[/IMG]]("http://ompldr.org/vaWQ4bw/grub with saucy.jpg")

---

### Post by von Stalhein on 2013-05-14
> **Cavsfan said:**
> Added Saucy to the mix.  :D

[[IMG]http://ompldr.org/taWQ4bw[/IMG]]("http://ompldr.org/vaWQ4bw/grub with saucy.jpg")

Round here we call that "[lairising]("http://www.encyclo.co.uk/define/Lairising")", but keep at it, you're going OK :-)

---

### Post by Cavsfan on 2013-05-14
> **Cavsfan said:**
> Added Saucy to the mix.  :D

[[IMG]http://ompldr.org/taWQ4bw[/IMG]]("http://ompldr.org/vaWQ4bw/grub with saucy.jpg")

> **von Stalhein said:**
> Round here we call that "[lairising]("http://www.encyclo.co.uk/define/Lairising")", but keep at it, you're going OK :-)

Ha! Good one! :D Just wanted to show it could be done even on Saucy. Saucy is just like Raring with the **05_debian-theme**

Trust me the green colors look better here than it probably does in that picture. It has light-green as the highlight color and green as normal color to match the Matrix green backgound.

---

### Post by Cavsfan on 2013-05-20
> **fantab said:**
> I have found particularly pictures with extension .jpeg don't work, while .jpg and .png work. Atleast for me .jpeg doesn't work.

Thanks for the great WIKI...

Sorry **fantab**! I didn't see your post until now. You are welcome! When I installed Raring after final release I worked for 2 hours on trying to get a .jpg picture to work. 
It was the exact size of my screen, it showed up when I did **sudo update-grub** but, yet it would not appear at bootup. And the font colors are dependent on that picture 
being found in **05_debian_theme** or neither the picture or the font colors show.

I tried editing it with Gimp more than once. I eventually gave up and used a picture that I had used before and viola it worked like a charm!

Don't know why some pics do not work but, I have experienced the same thing you did and the code says all picture types will work:

```
    # Step #3: Search the correct GRUB module for our background image.
    local reader
    case "${1}" in
        *.jpg|*.JPG|*.jpeg|*.JPEG) reader="jpeg";;
        *.png|*.PNG) reader="png";;
        *.tga|*.TGA) reader="tga";;
        *) return 3;; # Unknown image type.
    esac 
```

So, technically a .jpeg or a .JPEG picture *should* work. Not sure why they sometimes do not. I always use .jpg files myself.

On a side note, this appears to be a complicated "how to" when you first glance at it but, really all you need to know is whether your system is on **sda3** or **sda7**, etc. and that is about it.
So, it is really simple once you have done it once or twice.

I have customized the Grub on all 5 of my Linux OSs and occaisionally switch between Ubuntus with this: **sudo grub-install /dev/sda** on the one I want to show. ;)

---

### Post by fantab on 2013-05-21
Sometimes the images that are not working, work if I change the 'color depth' to something like 8 Bit and changing color mode to 'RGBA' for .jpg and .jpeg. But sometimes even that doesn't help. On Fedora, I was having a similar problem when using a custom Lightdm background and I couldn't get the image I wanted; then got some pointer that I should change the layer transparency by adding 'Alpha Channel'. And it worked. I tried to do the same with images that won't work with GRUB... It didn't work.

So I guess, that its some internal property of the image itself that causes the issue. 

My two cents...

---

### Post by Cavsfan on 2013-05-21
> **fantab said:**
> So I guess, that its some internal property of the image itself that causes the issue.

I agree! Some pictures will work while others won't no matter what you do to them. Sort of perplexing but, once I found another picture 
that did work I lost interest in determining why the other would not work. :)

---

### Post by Cavsfan on 2013-05-21
It appears omploader is down and has been for the past few days. If they don't come back soon, I'll put the pictures on another hosting site.

The possible font colors picture I will put on the other site first.

---

### Post by Cavsfan on 2013-05-22
Since omploader doesn't appear to be coming back I have to replace 4 pictures on this so it may be down for a bit.

---

### Post by Cavsfan on 2013-05-22
I am finished with updating the pictures. I put them on the Community Wiki site so they won't disappear again.

Sorry if I inconvenienced anyone. :)

---

### Post by fantab on 2013-05-23
I have a question related to Grub2 but not related to Ubuntu, specifically.

I dual boot Ubuntu and Arch. I don't install Grub in Arch and let Ubuntu-Grub load it. Yesterday, however I was forced to install Arch-Grub because I had to append some kernel parameters and I couldn't do so without /etc/default/grub. Anyways.

I have been trying to customize Grub Menu, nothing much, just background picture and font colors. Arch-Grub does NOT use /etc/grub.d/05_debian_theme, we have to edit /etc/default/grub for all the changes. So far so good. However, when I change font colors only the box and the text within it is affected and not the text outside the box. By outside text I mean the one on top-center which reads Grub version and below which gives instructions on how to use the menu. 

I am sure there is another entry somewhere which specifies font-color for the text outside the box. I can't seem to find it. I have looked in /boot/grub, /etc/default/grub and /etc/grub.d/ but I am yet to find it. Since there is no 05_debian_theme I am having a tough time figuring it out. I'd be grateful if I can be pointed in a right direction.

---

### Post by Cavsfan on 2013-05-23
> **fantab said:**
> I have a question related to Grub2 but not related to Ubuntu, specifically.

I dual boot Ubuntu and Arch. I don't install Grub in Arch and let Ubuntu-Grub load it. Yesterday, however I was forced to install Arch-Grub because I had to append some kernel parameters and I couldn't do so without /etc/default/grub. Anyways.

I have been trying to customize Grub Menu, nothing much, just background picture and font colors. Arch-Grub does NOT use /etc/grub.d/05_debian_theme, we have to edit /etc/default/grub for all the changes. So far so good. However, when I change font colors only the box and the text within it is affected and not the text outside the box. By outside text I mean the one on top-center which reads Grub version and below which gives instructions on how to use the menu. 

I am sure there is another entry somewhere which specifies font-color for the text outside the box. I can't seem to find it. I have looked in /boot/grub, /etc/default/grub and /etc/grub.d/ but I am yet to find it. Since there is no 05_debian_theme I am having a tough time figuring it out. I'd be grateful if I can be pointed in a right direction.

I have no idea how to change the fonts in Arch Linix but, this link looks promising:

[https://wiki.archlinux.org/index.php/GRUB#Background_image_and_bitmap_fonts](https://wiki.archlinux.org/index.php/GRUB#Background_image_and_bitmap_fonts)

See the part about **Menu colors** on that page. It looks like the font colors go in **/etc/default/grub** and are then generated with this command: **grub-mkconfig -o /boot/grub/grub.cfg**
However I can not test that but, it looks like it should work.

If you wanted to move control of grub back to Ubuntu all you would need to do is login to Ubuntu and enter **sudo grub-install /dev/sda** (sda is whatever hard drive your Ubuntu partition is installed on).

---

### Post by Cavsfan on 2013-05-23
> **fantab said:**
> I have a question related to Grub2 but not related to Ubuntu, specifically.

I dual boot Ubuntu and Arch. I don't install Grub in Arch and let Ubuntu-Grub load it. Yesterday, however I was forced to install Arch-Grub because I had to append some kernel parameters and I couldn't do so without /etc/default/grub. Anyways.

I have been trying to customize Grub Menu, nothing much, just background picture and font colors. Arch-Grub does NOT use /etc/grub.d/05_debian_theme, we have to edit /etc/default/grub for all the changes. So far so good. However, when I change font colors only the box and the text within it is affected and not the text outside the box. By outside text I mean the one on top-center which reads Grub version and below which gives instructions on how to use the menu. 

I am sure there is another entry somewhere which specifies font-color for the text outside the box. I can't seem to find it. I have looked in /boot/grub, /etc/default/grub and /etc/grub.d/ but I am yet to find it. Since there is no 05_debian_theme I am having a tough time figuring it out. I'd be grateful if I can be pointed in a right direction.

I have no idea how to change the fonts in Arch Linix but, this link looks promising:

[https://wiki.archlinux.org/index.php/GRUB#Background_image_and_bitmap_fonts](https://wiki.archlinux.org/index.php/GRUB#Background_image_and_bitmap_fonts)

See the part about **Menu colors** on that page. It looks like the font colors go in **/etc/default/grub** and are then generated with this command: **grub-mkconfig -o /boot/grub/grub.cfg**
However I can not test that but, it looks like it should work.

If you wanted to move control of grub back to Ubuntu all you would need to do is login to Ubuntu and enter **sudo grub-install /dev/sda** (sda is whatever hard drive your Ubuntu partition is installed on).

---

### Post by Cavsfan on 2013-05-23
> **fantab said:**
> I have a question related to Grub2 but not related to Ubuntu, specifically.

I dual boot Ubuntu and Arch. I don't install Grub in Arch and let Ubuntu-Grub load it. Yesterday, however I was forced to install Arch-Grub because I had to append some kernel parameters and I couldn't do so without /etc/default/grub. Anyways.

I have been trying to customize Grub Menu, nothing much, just background picture and font colors. Arch-Grub does NOT use /etc/grub.d/05_debian_theme, we have to edit /etc/default/grub for all the changes. So far so good. However, when I change font colors only the box and the text within it is affected and not the text outside the box. By outside text I mean the one on top-center which reads Grub version and below which gives instructions on how to use the menu. 

I am sure there is another entry somewhere which specifies font-color for the text outside the box. I can't seem to find it. I have looked in /boot/grub, /etc/default/grub and /etc/grub.d/ but I am yet to find it. Since there is no 05_debian_theme I am having a tough time figuring it out. I'd be grateful if I can be pointed in a right direction.

I have no idea how to change the fonts in Arch Linix but, this link looks promising:

[https://wiki.archlinux.org/index.php/GRUB#Background_image_and_bitmap_fonts](https://wiki.archlinux.org/index.php/GRUB#Background_image_and_bitmap_fonts)

See the part about **Menu colors** on that page. It looks like the font colors go in **/etc/default/grub** and are then generated with this command: **grub-mkconfig -o /boot/grub/grub.cfg**
However I can not test that but, it looks like it should work.

If you wanted to move control of grub back to Ubuntu all you would need to do is login to Ubuntu and enter **sudo grub-install /dev/sda** (sda is whatever hard drive your Ubuntu partition is installed on).

---

### Post by fantab on 2013-05-23
Thanks Cavsfan. But I know all that. The problem is after I have changed the font color in /etc/default/grub, like I said, **only the box outline and the menu inside changes but NOT the text outside the box**. **And also the sub-menus remain unchanged**. I have even tried to create and add 05_Arch_theme based on 05_Debian_theme, but it does not help either. Wonder what patches Ubuntu/Debian apply to Grub. I will keep trying until eventually I re-install Ubuntu-Grub. This is the first time I have used Grub from any other Distro.

Thanks again...

---

### Post by Cavsfan on 2013-05-23
> **fantab said:**
> Thanks Cavsfan. But I know all that. The problem is after I have changed the font color in /etc/default/grub, like I said, **only the box outline and the menu inside changes but NOT the text outside the box**. **And also the sub-menus remain unchanged**. I have even tried to create and add 05_Arch_theme based on 05_Debian_theme, but it does not help either. Wonder what patches Ubuntu/Debian apply to Grub. I will keep trying until eventually I re-install Ubuntu-Grub. This is the first time I have used Grub from any other Distro.

Thanks again...

You are welcome!

It was sort of a shot in the dark but, it looked good from here. :)

Good luck!

---

### Post by fantab on 2013-05-23
Well it turns out that the solution was as simple as creating a new file /etc/grub.d/01_theme with the following script:

```
#!/bin/sh
cat << EOF
    set color_normal=dark-gray/black
    set color_highlight=cyan/black
EOF
```

... and making it executable.

It has given me some ideas about Ubuntu too... :wink:

Regards...

---

### Post by Cavsfan on 2013-05-23
> **fantab said:**
> Well it turns out that the solution was as simple as creating a new file /etc/grub.d/01_theme with the following script:

```
#!/bin/sh
cat << EOF
    set color_normal=dark-gray/black
    set color_highlight=cyan/black
EOF
```

... and making it executable.

It has given me some ideas about Ubuntu too... :wink:

Regards...

Sweet! :guitar: I am glad you found a solution. I know absolutely nothing about Arch although I have a spare partition. :)
But, I have enough trouble keeping up with the 6 operating systems I already have as it is! 
I prefer Precise 12.04 LTS and keep the others mainly for Grub updates for this wiki.
I have Mint 14 installed but, it is either based on Quantal Quetzal 12.10 or vice versa. Even many of the sources have "Quantal" in the name.

---

### Post by Cavsfan on 2013-05-23
A light picture with blue normal and black highlight font colors.

[ATTACH=CONFIG]242949[/ATTACH]


```
echo " set color_normal=blue/black"
echo " set color_highlight=black/black"
```

---

### Post by Cavsfan on 2013-05-29
I couldn't take that light theme for very long. I just basically wanted to prove to myself that with a background picture you could use black/black as either the normal or highlight font.
I prefer darker pictures/fonts.
Here is my current Grub2 screen on Raring:

[ATTACH=CONFIG]243241[/ATTACH]

---

### Post by Bashing-om on 2013-05-29
Hey people;

I am unable to effect any change to the grub boot menu. No changes made in /etc/default/grub or to any of the scripts in /etc/grub.d are reflected in the boot menu.
After going around and around with this for a week, I am at my wit's end and looking for advise.
I am triple booting -> raring, ubuntu 12.04 and lubuntu 12.04;
raring is a MINIMAL install with xfce4 for the desktop environment fairly fresh install and this is my initial boot menu item that goaded me to attempt to change the boot menu: Choosing to use Cavsfab's excellent wiki guide:
> ubuntu' --class ubuntu --class gnu-linux --class gnu --class
ubuntu, with linux 3.8.0-21-generic  os   'gnulin->
--class ubuntu --class gnu-linux --> 
Initially I was not able to update the kernel, however I now have kernel 3.8.0-22-generic installed:
> sysop@1304mini:~$ uname -r
3.8.0-22-generic
sysop@1304mini:~$

After following the guide; here is my results and system set up:
my /boot/grub/grub.cfg ->
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="${saved_entry}"


if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi


export menuentry_id_option


if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}


function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}


function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}


insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
else
  search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
fi
if loadfont /boot/grub/DejaVuSansMono.pf2 ; then
  set gfxmode=1600x900
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
else
  search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
fi
insmod tga
background_image -m stretch /usr/share/images/grub/050817-N-3488C-028.tga
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
else
  search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
fi
insmod tga
if background_image /usr/share/images/grub/050817-N-3488C-028.tga; then
 set color_normal=cyan/black
 set color_highlight=light-cyan/black
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "RaRing 13.04" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "     RaRing 13.04 (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "LUBU12.04" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "     LUBU12.04 (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro single
        initrd /initrd.img
}
menuentry "ubie12.04" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet splash
        initrd /initrd.img
}
menuentry "     ubie12.04 (Recovery Mode)" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro single
        initrd /initrd.img
}


### END /etc/grub.d/06_custom ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
    else
      search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
    fi
    linux    /boot/vmlinuz-3.8.0-22-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
    menuentry 'Ubuntu, with Linux 3.8.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-22-generic-advanced-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        else
          search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        fi
        echo    'Loading Linux 3.8.0-22-generic ...'
        linux    /boot/vmlinuz-3.8.0-22-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-22-generic-recovery-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        else
          search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        fi
        echo    'Loading Linux 3.8.0-22-generic ...'
        linux    /boot/vmlinuz-3.8.0-22-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-21-generic-advanced-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        else
          search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        fi
        echo    'Loading Linux 3.8.0-21-generic ...'
        linux    /boot/vmlinuz-3.8.0-21-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-21-generic-recovery-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        else
          search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        fi
        echo    'Loading Linux 3.8.0-21-generic ...'
        linux    /boot/vmlinuz-3.8.0-21-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-21-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 12.04.2 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
    else
      search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
    fi
    linux /vmlinuz root=/dev/sda7
    initrd /initrd.img
}
submenu 'Advanced options for Ubuntu 12.04.2 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img.old
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-41-generic--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /boot/vmlinuz-3.2.0-41-generic root=/dev/sda7
        initrd /boot/initrd.img-3.2.0-41-generic
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-43-generic--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /boot/vmlinuz-3.2.0-43-generic root=/dev/sda7
        initrd /boot/initrd.img-3.2.0-43-generic
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-44-generic--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /boot/vmlinuz-3.2.0-44-generic root=/dev/sda7
        initrd /boot/initrd.img-3.2.0-44-generic
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img.old
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz.old--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz.old root=/dev/sda7
        initrd /initrd.img.old
    }
}


menuentry 'Ubuntu 12.04.2 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
    else
      search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
    fi
    linux /boot/vmlinuz-3.2.0-44-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro
    initrd /boot/initrd.img-3.2.0-44-generic
}
submenu 'Advanced options for Ubuntu 12.04.2 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
    menuentry 'Ubuntu, with Linux 3.2.0-44-generic (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-44-generic--5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-44-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro
        initrd /boot/initrd.img-3.2.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-44-generic (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-44-generic-root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset-5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-44-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-43-generic (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-43-generic--5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-43-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro
        initrd /boot/initrd.img-3.2.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-43-generic (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-43-generic-root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset-5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-43-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-41-generic (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-41-generic--5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-41-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro
        initrd /boot/initrd.img-3.2.0-41-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-41-generic (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-41-generic-root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset-5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-41-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-41-generic
    }
}


### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```
my /etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=saved
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#28may13-quiet splash removed from following line: 29may13 - ZFR.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
#28may13 font changed to the following
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2 
#28may13=image backgrounding added
GRUB_BACKGROUND=/usr/share/images/grub/050817-N-3488C-028.tga
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#28may13-GFXMODE enabled (uncommented) and resolution changed from 640x480
GRUB_GFXMODE=1600x900


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
``` 

My system set up from "blkid" :
```

/dev/sda1: LABEL="1304mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1304mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1204" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1304mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="ubie1204" UUID="5bae8c40-b15d-42f8-9fc9-0cf087f338d4" TYPE="ext4" 

```

The prerequisite image file exist and is installed to /usr/share/images/grub/ ;
I have removed grub from the lubuntu install on sda7 --- grub remains installed on ubuntu 12.04 sdc1;
Resolution mode 1600x900 verified by grub's "vbeinfo";
Numerous times rewritten the grub.cfg file ("sudo update-grub');
 
Hours and hours spent trolling sites to understand why/what is failing, been over and over the scrips and guidance, perceiving no errors, making some change - update grub - reboot.... no change at all to grub's boot menu.

For sure /boot/grub/grub/cfg is executing, else would not have a boot menu at all (???) as /boot/grub/grub.cfg supposedly executes upon boot-up ! 
-------
Request advise on what I am not seeing and/or overlooking ! ;
What can I do to see the execution process of /boot/grub/grub.cfg, How can I verify that the variables in the script are "set" ?

Why can I not effect a change in the boot grub menu ??[INDENT=2]
help and guidance is muchly appreciated [/INDENT]

---

### Post by bogan on 2013-05-30
Hi!,[B] Bashing_om,
[/B]
Without going through your boot/grub/grub.cfg file in detail, it looks to me that your are editing the files in one installation, say Raring, whilst the grub menu and boot sequence are controlled by grub in another installation, probably 12.04 on another drive. Edit: The last command in this Post will tell you what is actually the current state.

If that is the case, what you need to do is to boot the drive and installation you want to be in control and run:```
sudo grub-install /dev/sdx # where 'sdx' is the drive in operation, not the partition
sudo update-grub
sudo reboot:
```To confirm the installation had no error: ```
sudo grub-install --recheck /dev/sdx
```

You may also need to run ```
sudo grub-install --root-directory=/mnt /dev/sdx # or:
sudo grub-install grub-pc # space-bar to select drive, tab to OK, enter to accept
sudo debconf-show grub-pc # will show you full details.
```Chao!,** bogan.**

---

### Post by Bashing-om on 2013-05-30
@ bogan, Hi !

Appreciate the input. and the assist even more.... But, I am aware of and have done so MANY times... 'Nother grub as primary had occurred to me and I removed grub from my Lubuntu install in sda7, Since my last go-around with sda1 [raring](what I want as primary) after running the grub install routine for sda, I have not gone back and did any thing on the sda7 (lubuntu) or sdc1 (ubuntu) installations.
bk
After going round and a-round with - not able to effect a change to the booting grub menu - I am frustrated and continue to be mystified ! My thinking process has become cloudy and missfocused. So, I appreciate a fresh perspective on this one !

What I am currently considering is:
Backup the present /boot/grub/grub.cfg file;
Make a "custom" menu entry in that grub/cfg file (prepared to have to get back in the system via other means), reboot to see if THAT has an effect.
And/or -- not knowing if the capability yet exists this early in the boot process -- see if I can put an echo statement to redirect output to a file (nice if I can figure out how to get the variable contents to this file).

I am going to run through the process again, and will advise.
[INDENT=2]
again, thanks

[/INDENT]

---

### Post by Bashing-om on 2013-05-30
@ bogan ... Wow
The "grub-install grub-pc" returned an error ! The only error I have encountered to this time !
> sysop@1304mini:~$ sudo grub-install /dev/sdaInstallation finished. No error reported.
sysop@1304mini:~$ sudo grub-install grub-pc 
[sudo] password for sysop: 
/usr/sbin/grub-probe: error: cannot find a GRUB drive for grub-pc.  Check your device.map.
sysop@1304mini:~$ 

For some past reason I have a copy of "device.map"... maybe I have erroneously removed it. (???)

Hey Back to checking on what is happening with the "device.map"

Next:
> sysop@1304mini:~$ sudo update-grub
Generating grub.cfg ...
Found background: /usr/share/images/grub/050817-N-3488C-028.tga
Found background image: /usr/share/images/grub/050817-N-3488C-028.tga
What do you want to boot up, Billy
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sda7
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sdc1
done
sysop@1304mini:~$ sudo grub-install grub-pc 
/usr/sbin/grub-probe: error: cannot find a GRUB drive for grub-pc.  Check your device.map.[INDENT=2]
I'll be back 
 [/INDENT]

---

### Post by Bashing-om on 2013-05-30
et all ; My current sloppyation:
Remove, purge and (re-)install of grub ->
Get to "configuring grub-pc" screen and select "ok" ->
"configuring grub-pc" application -> no choice is accepted: as below
>                                                                            &#9474;   &#9474; You chose not to install GRUB to any devices. If you continue, the boot     &#9474;  
 &#9474; loader may not be properly configured, and when this computer next starts   &#9474;  
 &#9474; up it will use whatever was previously in the boot sector. If there is an   &#9474;  
 &#9474; earlier version of GRUB 2 in the boot sector, it may be unable to load      &#9474;  
 &#9474; modules or handle the current configuration file.                           &#9474;  
 &#9474;                                                                             &#9474;  
 &#9474; If you are already using a different boot loader and want to carry on       &#9474;  
 &#9474; doing so, or if this is a special environment where you do not need a boot  &#9474;  
 &#9474; loader, then you should continue anyway. Otherwise, you should install      &#9474;  
 &#9474; GRUB somewhere.                                                             &#9474;  
 &#9474;                                                                             &#9474;  
 &#9474; Continue without installing GRUB?                                           &#9474;  
 &#9474;                                                                             &#9474;  
 &#9474;                     <Yes>                        <No>                       &#9474;  
 &#9474;                                                                             &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
so what I did: ->sysop@1304mini:~$ "sudo grub-install --root-directory=/mnt /dev/sda"
> Installation finished. No error reported.
sysop@1304mini:~$
then:"sudo update-grub"
> sysop@1304mini:~$ sudo update-grub
Generating grub.cfg ...
What do you want to boot up, Billy
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sda7
Found Ubuntu 12.04.2 LTS (12.04) on /dev/sdc1
done
sysop@1304mini:~$ 


And now I am backing out of all open aps, and rebooting to see if any affects.


Presently after reboot -> no change to grub's booting menu. and ->
"debconf-show:"
> sysop@1304mini:~$ sudo debconf-show grub-pc 
[sudo] password for sysop: 
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices:
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
  grub2/linux_cmdline:
* grub-pc/install_devices_empty: true
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
  grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10
sysop@1304mini:~$ 


Please compare an output on a known stable system to mine; 4 of the entries in my output are "suspect" to me.
---------------
Right now I just do not know;
1. dd out my boot sector and try again ?
2. Is because I did not (re-)install grub onto my sda7 install of lubuntu the cause of this effect ?
3. Some how is my grub on sdc -ubuntu 12,04 - an issue ? How ? it is not mounted !// albeit in past attempts I did mount all my systems and run the "update-grub" routine, could this have complicated my sloppyation in that this corrupted my boot sector on sda ?
-------------

I would certainly appreciate any insight and guidance on a remedy/[INDENT=2]
with all due respect

[/INDENT]

---

### Post by Cavsfan on 2013-05-30
Let me see if I can come up with what you need to do.

---

### Post by Cavsfan on 2013-05-30
> **Bashing-om said:**
> Hey people;

It's not really *people* although I appreciate help from others like Bogan and Oldfred.

If you want Raring to be your default you need to boot into Raring and enter **sudo grub-install /dev/sda** and **sudo update-grub**.

Place a single picture the size of your resolution in **/boot/grub/**. It can contain only 1 picture and if you want to change it, you have to remove the other one while making the change.
It can be any type of picture file as the code looks for the existance of a background file in **05_debian_theme** looks like this:

```
	case "${1}" in
		*.jpg|*.JPG|*.jpeg|*.JPEG) reader="jpeg";;
		*.png|*.PNG) reader="png";;
		*.tga|*.TGA) reader="tga";;
		*) return 3;; # Unknown image type.
	esac
```

Be aware that some pictures just do not work. They will be listed in the output of sudo update-grub but they will not show at boot time. It has happened to me and I just chose another picture.
By having a picture there you can set your font colors in **etc/grub.d//05_debian_theme** after line 114 (See the **Editing /etc/grub.d/05_debian_theme** part in the wiki)

You know never make any changes to **/boot/grub/grub.cfg** right.

Make these changes to your /etc/default/grub file **gksudo gedit /etc/default/grub**
Delete this line from the file [COLOR=#FF0000]GRUB_BACKGROUND=/usr/share/images/grub/050817-N-3488C-028.tga[/COLOR]

I do not know what "saved" means by GRUB_DEFAULT=saved
I have mine set to a number based on the output of this command:

This command reads the bootable lines which are only the contents of **/etc/grub/06_custom** as that is all I have executable.
```
cavsfan@cavsfan-MS-7529:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl
     1	menuentry "Precise Pangolin 12.04" {
     2	menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     3	menuentry "Quantal Quetzal 12.10" {
     4	menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
     5	menuentry "Raring Ringtail 13.04" {
     6	menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
     7	menuentry "Saucy Salamander 13.10" {
     8	menuentry "Saucy Salamander 13.10 (Recovery Mode)" {
     9	menuentry "Linux Mint 14 Nadia" {
    10	menuentry "Linux Mint 14 Nadia (Recovery Mode)" {
    11	menuentry "Windows 7" {

```

This is the output of my sudo blkid:
```
cavsfan@cavsfan-MS-7529:~$ sudo blkid
[sudo] password for cavsfan: 
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Precise" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" 
/dev/sda3: UUID="e14dc02e-6ea8-4c95-b4d0-9dc04d32294d" TYPE="swap" 
/dev/sda5: LABEL="Linux-Mint" UUID="b796e378-c9dd-4557-825b-5d5687197609" TYPE="ext4" 
/dev/sda6: LABEL="Quantal" UUID="4d6a25ba-5a4b-4da4-8ae1-9939bc6b6b4c" TYPE="ext4" 
/dev/sda7: LABEL="Saucy" UUID="89642e6f-ee35-49b7-b34b-c2f1b9871f42" TYPE="ext4" 
/dev/sda8: LABEL="Raring" UUID="21fd827b-a771-4e96-9311-5ad11382d6f1" TYPE="ext4" 
/dev/sda9: LABEL="Extra" UUID="e5387ae4-6423-4d97-b08b-9f2d31e235a2" TYPE="ext4" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs"
``` 

Here is what my **/etc/grub/06_custom** file looks like on Raring:

```
cavsfan@cavsfan-MS-7529:~$ cat /etc/grub.d/06_custom
#!/bin/sh
echo 1>&2 "Adding Ubuntu Precise Pangolin 12.04, Quantal Quetzal 12.10, Raring Ringtail 13.04, Saucy Salamander 13.10, Linux Mint 14 Nadia and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Precise Pangolin 12.04" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Raring Ringtail 13.04" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro quiet splash
        initrd /initrd.img
}
menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Saucy Salamander 13.10" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "Saucy Salamander 13.10 (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Linux Mint 14 Nadia" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Linux Mint 14 Nadia (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}
```

I hope this gets you back up and I'll check tomorrow on your progress.
Thanks Bogan for your help!

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]Cavsfan;
Thank you for your time and effort. In regards to your last directive I have complied. Starting with a "clean" slate, making the edits; the result remains that my boot grub menu remains unchanged.
This is not to imply that there is any fault in your excellent tutorial. It boils down to I have a fault in my system and to this time I have not isolated it.
I presently do not have the knowledge to find this fault, though I keep pressing on.
Background:
Recently I had Ubuntu 10.04 standard desk-top install, ubuntu 12.04 standard desk-top install and lubuntu 12.04 standard desk-top install;
all booting with no issue on a standard grub menu.

At 10.04's EOL I prepared to end 10.04 and set up for whatever I was going to install in it's place.
GParted: deleted all the 10.04 partitions, and in their place I made 3 smaller partitions to house 13.04 and at that time I decided to do a "minimal"install.
The new install went with out an issue, smooth as one would want;
Rebooted: The grub boot menu in respect to the new raring install was presented in an unfamiliar syntax, but still worked to boot raring up.
installed xorg, xfce4 for the DE - no issue
installing google-chrome I encountered "authentication" issues, found there had been no .Xauthority file generated nor was the XAUTHORITY variable set. I worked through that;
Found I could not run a graphical application with root's access, installing "gksudo" resolved that one.

Now I am back to fixing the grub boot menu ...have been at this for a few weeks and nothing I do effects that boot menu.
The boot menu is fully functional, just no indication of which kernel I am booting.
Kinda pleased with my install of 13.04 ...got all ,less the menu, set up and I feel good about it. Now I feel good about my system and all I do and can do with it... a bit of pride perhaps on my part -> but while I was trying to doctor my boot menu, how bout the eye candy to show it off ??

I am unable to change anything on the grub boot menu from what was the initial setting when installed. And yes I am in a serious learning mode. I have done lots of homework to the point that I want to know how /boot/grub/grub.cfg is parsed as well as what tools I can make at my disposal to understand what is not taking place.

/boot/grub/grub.cfg is supposed to be executed at boot up, but is it ? (for 1 question)
"sudo apt-get install grub"'s install wizard balks at a destination device, and certain lines in "debconf's" output I wonder about (more homework); do I need to zero out the disk's boot sector and (re-)install (for 2nd question)
--------
This is where I stand now with my newly generated grub.cfg file:
[/COLOR]```
## DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"


if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi


export menuentry_id_option


if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}


function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}


function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}


insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
else
  search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
fi
if loadfont /boot/grub/DejaVuSansMono.pf2 ; then
  set gfxmode=1600x900
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
else
  search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
fi
insmod tga
if background_image /boot/grub/050817-N-3488C-028.tga; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "RaRing 13.04" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "     RaRing 13.04 (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "LUBU12.04" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "     LUBU12.04 (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro single
        initrd /initrd.img
}
menuentry "ubie12.04" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet splash
        initrd /initrd.img
}
menuentry "     ubie12.04 (Recovery Mode)" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro single
        initrd /initrd.img
}


### END /etc/grub.d/06_custom ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
    else
      search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
    fi
    linux    /boot/vmlinuz-3.8.0-22-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
    menuentry 'Ubuntu, with Linux 3.8.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-22-generic-advanced-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        else
          search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        fi
        echo    'Loading Linux 3.8.0-22-generic ...'
        linux    /boot/vmlinuz-3.8.0-22-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-22-generic-recovery-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        else
          search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        fi
        echo    'Loading Linux 3.8.0-22-generic ...'
        linux    /boot/vmlinuz-3.8.0-22-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-21-generic-advanced-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        else
          search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        fi
        echo    'Loading Linux 3.8.0-21-generic ...'
        linux    /boot/vmlinuz-3.8.0-21-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-21-generic-recovery-3a47f1f1-ed1f-4134-b6aa-be101a7d97b4' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        else
          search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
        fi
        echo    'Loading Linux 3.8.0-21-generic ...'
        linux    /boot/vmlinuz-3.8.0-21-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-21-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 12.04.2 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
    else
      search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
    fi
    linux /vmlinuz root=/dev/sda7
    initrd /initrd.img
}
submenu 'Advanced options for Ubuntu 12.04.2 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img.old
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-41-generic--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /boot/vmlinuz-3.2.0-41-generic root=/dev/sda7
        initrd /boot/initrd.img-3.2.0-41-generic
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-43-generic--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /boot/vmlinuz-3.2.0-43-generic root=/dev/sda7
        initrd /boot/initrd.img-3.2.0-43-generic
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-44-generic--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /boot/vmlinuz-3.2.0-44-generic root=/dev/sda7
        initrd /boot/initrd.img-3.2.0-44-generic
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz root=/dev/sda7
        initrd /initrd.img.old
    }
    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz.old--4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        else
          search --no-floppy --fs-uuid --set=root 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
        fi
        linux /vmlinuz.old root=/dev/sda7
        initrd /initrd.img.old
    }
}


menuentry 'Ubuntu 12.04.2 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
    else
      search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
    fi
    linux /boot/vmlinuz-3.2.0-44-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro
    initrd /boot/initrd.img-3.2.0-44-generic
}
submenu 'Advanced options for Ubuntu 12.04.2 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
    menuentry 'Ubuntu, with Linux 3.2.0-44-generic (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-44-generic--5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-44-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro
        initrd /boot/initrd.img-3.2.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-44-generic (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-44-generic-root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset-5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-44-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-43-generic (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-43-generic--5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-43-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro
        initrd /boot/initrd.img-3.2.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-43-generic (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-43-generic-root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset-5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-43-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-41-generic (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-41-generic--5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-41-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro
        initrd /boot/initrd.img-3.2.0-41-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-41-generic (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-41-generic-root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset-5bae8c40-b15d-42f8-9fc9-0cf087f338d4' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        else
          search --no-floppy --fs-uuid --set=root 5bae8c40-b15d-42f8-9fc9-0cf087f338d4
        fi
        linux /boot/vmlinuz-3.2.0-41-generic root=UUID=5bae8c40-b15d-42f8-9fc9-0cf087f338d4 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-41-generic
    }
}


### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```
The contents of /boot/grub/
```



sysop@1304mini:~$ ls -la /boot/grub/
total 996
drwxr-xr-x 5 root root   4096 May 30 19:22 .
drwxr-xr-x 3 root root   4096 May 28 22:02 ..
-rw-r--r-- 1 root root 814353 Jan 26 17:09 050817-N-3488C-028.tga
-rw-r--r-- 1 root root 142763 May 27 14:39 DejaVuSansMono.pf2
drwxr-xr-x 2 root root   4096 May 19 11:04 fonts
-rw-r--r-- 1 root root    699 May 30 14:04 gfxblacklist.txt
-r--r--r-- 1 root root  21363 May 30 19:22 grub.cfg
-rw-r--r-- 1 root root   1024 May 30 19:31 grubenv
drwxr-xr-x 2 root root  12288 May 30 18:40 i386-pc
drwxr-xr-x 2 root root   4096 May 30 18:40 locale
sysop@1304mini:~$ 
```

Note there is no device.map file generated.... huh ? (this be question 3)

Forum questions are to be like dead men "one to the box" but my three questions I consider all related to a single issue -> why can I not alter the boot grub menu ?[INDENT=2]
all help remains hugely appreciated.[/INDENT]

---

### Post by Cavsfan on 2013-05-31
You definitely do not want to install Grub 1 with this command **sudo apt-get install grub**.
What is the output of this on Raring: **grub-install -v**.

It should look like this:

```
cavsfan@cavsfan-MS-7529:~$ grub-install -v
grub-install (GRUB) 2.00-13ubuntu3

```

Always make sure you enter **sudo update-grub** after you have made *any* changes to any of the grub files.
Keep in mind that when you get down to have just what is in your **06_custom** file displaying at bootup the most recently installed kernel is what you will boot up with.
It is not the highest number but, the most recently installed kernel.

Can you post the contents of your **/etc/grub.d/06_custom** file?
Can you also post the output of this command 
```
grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl
```

I noticed that in Precise 12.04 you have 3 kernels. You only need to retain two so you could enter this while in Precise:
This is not critical but, it will free up about 200+MB of disk space.
```
sudo apt-get purge linux-headers-3.2.0-41 linux-headers-3.2.0-41-generic linux-image-3.2.0-41-generic
```

---

### Post by bogan on 2013-05-31
Hi!, Bashing_om,

The output from: 'sudo debconf-show grub' in my sda Raring, is identical except for the two lines in your Post that have an asterisk in front:
> * grub-pc/install_devices:
  ...
* grub-pc/install_devices_empty: [COLOR=#ff0000]true[/COLOR] Those two lines in mine are: > * grub-pc/install_devices:[COLOR=#ff0000] /dev/disk/by-id/ata-SanDisk_SDSSDP128G_130372403160[/COLOR]
...
  grub-pc/install_devices_empty:[COLOR=#0000ff] false [/COLOR] Note, the second does not have an asterisk.

I would take this, plus the error message you got from: ```
~$ sudo grub-install grub-pc 
[sudo] password for sysop: 
/usr/sbin/grub-probe: error: cannot find a GRUB drive for grub-pc.  Check your device.map.
``` means that grub-pc {ie Grub 2.00} is not installed, or not properly installed. in the Raring installation.
[ I assume you have tried: ' sudo apt-get install --reinstall grub-pc'.] The error is because grub-install is expecting to get a destination in the form: "/deb/sdx" and is supposed to ask for one, presumably it does not get that far, as it cannot find Grub-pc.

I cannot answer your three 'Why & How?' questions, but I know I had very similar problems to yours with my installations using multiple drives,   including USB/eSata removable ones, and they became so complex that in the end I had to give up on Cavsfan's system.

I probably did not explain sufficiently my notion of what is preventing you from altering the Grub Menu displayed by default.

Suppose that sdc drive is set in Bios/AEFFI as the priority default boot device, and the Linux installed in sdc has a grub set to boot to Raring in sda by default { made more complex by your /etc/default/grub default being set to "saved" } The result would appear to be the same as if booted from the grub in sda, but any alteration of the grub files there, would have no effect on the default behaviour.

As an instance, if I boot from my USB stick Raring I get a grub menu that includes the Raring on sdc, an external HDD; and it boots to it OK.
 Whereas, when booted to Raring on the SSD [ sda ], although 'update-grub' finds the Raring on sdc, it does not appear in the grub Menu that sda displays. Similarly Cavsfan's system does not allow sdc's Raring to boot, as it produces an sdc  identity error, hangs there for about a minute, and then boots into the last set default boot choice; though how it decides which that will be, I have no idea.

For these and other reasons I make  sure that each of my Linux grub menus has a different Menu Background, so I am never in doubt as to which grub is in control.

It would be interesting to know what happens if you select in BIos  to boot from sdc and alter the /etc/default/grub file there and reboot similarly, and also as you have previously done. Is there any difference?

@ Cavsfan.
AFAIK: 'grub-defalt=saved' means default is whatever was last selected. EG: if the first entry is Raring and the third is Windows, and Windows is selected and booted; if on reboot it is left to default, Windows will again boot up; not Raring that might be expected.

Edit; Note the following from /boot/grub/grub.cfg:> if [ "${prev_saved_entry}" ]; then
   set saved_entry="${prev_saved_entry}"   
save_env saved_entry   
set prev_saved_entry=   save_env prev_saved_entry 
  set boot_once=true 
fi 

  function savedefault {   
if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"     
save_env saved_entry
   fi Chao!,** bogan** { Second Posting, first attempt this morning did not appear in the Forum. }

---

### Post by Bashing-om on 2013-05-31
@[COLOR=#000000]Cavsfan ; The info you requested.

[/COLOR]1) output of "grub-install -v":
```
grub-install (GRUB) 2.00-13ubuntu3
```
2) My crrent /etc/grub.d/o6.custom :
```
#!/bin/shecho 1>&2 "What do you want to boot up, Billy"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "RaRing 13.04" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "     RaRing 13.04 (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "LUBU12.04" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "     LUBU12.04 (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro single
        initrd /initrd.img
}
menuentry "ubie12.04" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet splash
        initrd /initrd.img
}
menuentry "     ubie12.04 (Recovery Mode)" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro single
        initrd /initrd.img
}

```
3) output of grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl
```



     1    menuentry "RaRing 13.04" {
     2    menuentry "     RaRing 13.04 (Recovery Mode)" {
     3    menuentry "LUBU12.04" {
     4    menuentry "     LUBU12.04 (Recovery Mode)" {
     5    menuentry "ubie12.04" {
     6    menuentry "     ubie12.04 (Recovery Mode)" {
     7    menuentry 'Ubuntu
     8    submenu 'Advanced options for Ubuntu
     9    menuentry 'Ubuntu, with Linux 3.8.0-22-generic
    10    menuentry 'Ubuntu, with Linux 3.8.0-22-generic (recovery mode)
    11    menuentry 'Ubuntu, with Linux 3.8.0-21-generic
    12    menuentry 'Ubuntu, with Linux 3.8.0-21-generic (recovery mode)
    13    menuentry 'Ubuntu 12.04.2 LTS (12.04)
    14    submenu 'Advanced options for Ubuntu 12.04.2 LTS (12.04)
    15    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)
    16    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)
    17    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)
    18    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)
    19    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)
    20    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)
    21    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)
    22    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)
    23    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)
    24    menuentry 'Ubuntu 12.04.2 LTS (12.04) (on /dev/sda7)
    25    menuentry 'Ubuntu 12.04.2 LTS (12.04)
    26    submenu 'Advanced options for Ubuntu 12.04.2 LTS (12.04)
    27    menuentry 'Ubuntu, with Linux 3.2.0-44-generic (on /dev/sdc1)
    28    menuentry 'Ubuntu, with Linux 3.2.0-44-generic (recovery mode) (on /dev/sdc1)
    29    menuentry 'Ubuntu, with Linux 3.2.0-43-generic (on /dev/sdc1)
    30    menuentry 'Ubuntu, with Linux 3.2.0-43-generic (recovery mode) (on /dev/sdc1)
    31    menuentry 'Ubuntu, with Linux 3.2.0-41-generic (on /dev/sdc1)
    32    menuentry 'Ubuntu, with Linux 3.2.0-41-generic (recovery mode) (on /dev/sdc1)



```
And a new thank you for assisting me in this matter.

bk

@ bogan Thanks to you also, I am presently suffering from info overload, lemme have some time to digest and assimilate.
Too much info and having some difficulty differentiating old info from new as applied to grub2 vice versions <1.99 as well as "legacy". -But, they all parse some file somewhere to some end - ![INDENT=2]
later, when I have all my ducks in a row

[/INDENT]

---

### Post by Cavsfan on 2013-05-31
> **Bashing-om said:**
> 
```
#!/bin/shecho 1>&2 "What do you want to boot up, Billy"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "RaRing 13.04" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
```


Edit that first line and break it into 2 lines:
**gksudo gedit /etc/grub.d/06_custom**
Make it look like this:
```
#!/bin/sh
echo 1>&2 "What do you want to boot up, Billy"
```

Then enter sudo-update grub.

the "+4" in the exec tail line means that it will start execution at the 4th line.

In my 06_custom file:
```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Precise Pangolin 12.04, Quantal Quetzal 12.10, Raring Ringtail 13.04, Saucy Salamander 13.10, Linux Mint 14 Nadia and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Precise Pangolin 12.04" {
```

The 4th executable line in my file is "menuentry", which is correct however the 4th line in your file is "set root=(hd0,1)" which will cause problems.

As Bogan said your default being "saved" may be just fine. I perfer setting mine to a static number. I have mine set to 10 (windows 7) for my wife in case the pc reboots.

See if that doesn't fix your whole problem and let me know.

---

### Post by Bashing-om on 2013-05-31
@ bogan and Cavsfan :

Success ! Long story short, see my conclusion.


bogan;
I agree that grub2 must not be "properly" installed at this time.
Ok, what can I do to insure that it is properly installed: (?) I have seen docs where it is recommended that the primary grub be installed to one's primary booting system (in my case raring)MBR, and that grub on the secondary systems be installed to the root partition -vice MBR's boot sector. Now this conflicts with docs that direct that grub should be installed to that MBR boot sector.
Presently I have raring (sda1/root) installed to the MBR boot sector, that "might" be corrupted.
Attempts to (re-)install grub have been in-effectual, in that the install wizard cannot be forced to install to any location; installing grub manually to a designated location does complete with "no reported errors". However that work-around does not resolve the underlying issue.
 
Lubuntu 12.04(sda7) I have "removed purged grub" and have not (re-)installed
ubuntu 12.04 (sdc1) Grub installed onto the MBR sector. (allowing me to boot up in the event of serious problems in sda)--I have seen documentation that it is not required on the secondary system ( highly doubt that !)but ??


Now this begs the question...os-prober...looking for operating systems, if no grub is installed at all on a seconday system, does it drive os-prober nuts ? -> where should grub be installed to, on the seconday OS --in my case - Lubuntu on sda7.


Changing the boot order in bios: No, that had not occurred to me, will try it and see what results, and advice back to the thread on what results.


-by the way, it helps tremendously to have someone to discuss this matter with, It forces my thoughts into some kind of order, saving me from the choas I am presntly expreiencing !-


         My high regards

conclusion:

Presently the boot grub menu is working as desired and expected - bogan, your voice of experience shouts loudly now in my ears.
For years I had "thought" that I was booting this system from the 1st hard drive (my hard drives are all from the same manufacturer and all the same size -> nomenclature in bios of the drives are all the same),
- Taking your advise I re-arranged the boot order anyway; rebooted and I had a comprehensible boot menu ! 
- Then taking a slight risk I installed grub-pc on the lubuntu (sda7) install and directed grub to be installed in sda -> update-grub ;
- Then rebooted into raring -> (re-)install grub for sda from this install -> update-grub ->
- Reboot and much to fulfill my hopes and a wonder to behold was my splash screen with the desired boot options as desired !
- Ran grub-mkdevicemap and device.map has been generated....

As all is working now I am going to take the attitude - if it ain't broke, don't fix it ! -
As I now have a working system (again) my questions have receeded in precedence , such that I can pursue them at leisure.[INDENT]
Thank you again for coming to my aid in my time of need
[/INDENT]

@ Cavsfan; The guidance and confirmation you provided was instrumental ! Just being sure of my foundation was a big help.
( 06_custom's line was an error in transitioning - xfce4/xterm into google-chrome for the forum )

 I do appreciate your time and care; your devotion increases my devotion.
--------------------
pending yall's closing remarks to mark this thread as closed and over with.[INDENT=2]
my best regards
 [/INDENT]

---

### Post by Cavsfan on 2013-06-01
Glad you got it sorted out and working well. :)

---

### Post by Cavsfan on 2013-06-03
You could have this:

[IMG]http://i.imgur.com/d0UqsFC.jpg[/IMG]

Or you could have this:

[IMG]http://i.imgur.com/K1rTT1A.jpg[/IMG]

It is totally up to you. ;)

---

### Post by deadflowr on 2013-06-03
^ I prefer the latter, as the only benefit of the former is the realization of how many kernels I would have.
If I set a small boot partition, I'd pay closer attention the kernels I have.But alas, I don't have a small boot partition and even if I did, I'm certain I'd be proactive in cleaning up old kernels.

---

### Post by Cavsfan on 2013-06-03
> **deadflowr said:**
> ^ I prefer the latter, as the only benefit of the former is the realization of how many kernels I would have.
If I set a small boot partition, I'd pay closer attention the kernels I have. But alas, I don't have a small boot partition and even if I did, I'm certain I'd be proactive in cleaning up old kernels.

I agree! :D I have so many things installed on this PC that without this way of customizing the grub menu I would be lost! I too have enough trouble keeping only 2 kernels on each OS.
I'll install a kernel and reboot then forget which one I was in last. Yesterday I found one system I had 4 kernels still installed. I had to delete 2 of them. I only keep all of these installs to keep up with the grub versions.

That was sort of a trick question any way! :D Kind of like "do you want something lame or do you want something cool?" ;)

Thanks for the reply **deadflowr**! :)

Plus if you look at the first picture it looks like every install is on each partition. Strange! **sudo bklid **and I know which partitions my installs are on and sdax is all you really need to know to get this working.
It looked really difficult to me at first but, then the more and more I looked at it the simpler it got.

---

### Post by Bashing-om on 2013-06-03
Pardon me in the event I am interjecting; 

Adhering to  [COLOR=#000000]Cavsfan's method has greatly simplified my booting experiences, and the added eye candy is "soothing".

Simpler is better ! Alterations to the boot menu are "no big deal". --> 
I appreciate a better way to do "anything".
[/COLOR][INDENT][COLOR=#000000]
just my opinion

[/COLOR][/INDENT]

---

### Post by Cavsfan on 2013-06-04
> **Bashing-om said:**
> Pardon me in the event I am interjecting; 

Adhering to  [COLOR=#000000]Cavsfan's method has greatly simplified my booting experiences, and the added eye candy is "soothing".

Simpler is better ! Alterations to the boot menu are "no big deal". --> 
I appreciate a better way to do "anything".
[/COLOR][INDENT][COLOR=#000000]
just my opinion

[/COLOR][/INDENT]


Thank you **Bashing-om**! I agree simpler is always better. :D

---

### Post by Cavsfan on 2013-06-16
FYI:
If you are tired of gedit opening two tabs when you enter **gksudo gedit *filename*** someone posted this workaround on the bug report.

I noticed that gedit opens two tabs on every install on my box (in my signature) and it is annoying.

So, this is what was on the bug report that I cannot seem to readily find right now. BTW this also works very well until a fix is released.

**Paddy Landau** found that **gksudo gksudo gedit *finename*** was a workaround and someone came up with a script that will work so you do not need to enter **gksudo** twice.

Enter **gedit ~/.bashrc** or find this hidden file in your home directory and edit it and add the following:

```
# gksudo gedit opening 2 tabs fix
gksudo ()
{
 if [ "$1" = "gedit" ]
 then
  shift
  gksudo gksudo gedit "$@"
 else
  command gksudo "$@"
 fi
}
```

Edit: This has supposedly been resolved with gedit 3.7 or greater.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy gedit
gedit:
  Installed: 3.8.3-0ubuntu3
  Candidate: 3.8.3-0ubuntu3
  Version table:
 *** 3.8.3-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Cavsfan on 2013-07-19
Here is one on Saucy 13.10:

[IMG]http://i.imgur.com/vYOgf3A.jpg[/IMG]

---

### Post by Cavsfan on 2013-08-16
If any one is using this on Saucy 13.10, todays update to grub-pc, etc. changed where the font color lines go. They are now after **line 117**.
As I have probably mentioned more than once, it it recommended to accept the installers version instead of keeping your modified version of the files.

```
cavsfan@cavsfan-MS-7529:~$ grub-install -v
grub-install (GRUB) 2.00-17ubuntu1
```

It updated **/etc/grub.d/05_debian_theme** as well as **/etc/default/grub**.

I made the changes to those 2 files before I rebooted.

[ATTACH=CONFIG]245412[/ATTACH]

---

### Post by Cavsfan on 2013-09-24
New Grub2 screen for Raring Ringtale 13.04:

[IMG]http://i.imgur.com/bx1J8GR.jpg[/IMG]

It's been hard for me to get away from light-cyan for highlight font color and cyan for normal font color. Since I have mainly dark pictures. ;)

---

### Post by Cavsfan on 2013-10-17
I will be editing this wiki adding 2 lines to cover Saucy 13.10 since it was released today.
Shouldn't take long. ;)

---

### Post by Cavsfan on 2013-10-17
Finished updating the wiki. 
Happy Ubuntuing :)

---

### Post by Cavsfan on 2013-10-18
Grub2 screen on Saucy Salamander 13.10 after install of final release:

[IMG]http://i.imgur.com/QP1iq72.jpg[/IMG]

---

### Post by Cavsfan on 2013-10-31
A new Grub screen for Quantal:

[IMG]http://i.imgur.com/xNt92dp.jpg[/IMG]

---

### Post by von Stalhein on 2013-11-06
Nice work Cavsfan!

So, if you select Win7 the scorpion strikes???? :D

I'm in withdrawal, my Ubuntu box died a while ago & every other machine here runs Win. 
Saving the bikkies to build a new one & lurking in these forums for a fix is my sad existence atm :P

---

### Post by Cavsfan on 2013-11-06
> **von Stalhein said:**
> Nice work Cavsfan!

So, if you select Win7 the scorpion strikes???? :D

I'm in withdrawal, my Ubuntu box died a while ago & every other machine here runs Win. 
Saving the bikkies to build a new one & lurking in these forums for a fix is my sad existence atm :P

Thanks :)

Good luck! I need to get a backup laptop or something myself as soon as I can.

---

### Post by Cavsfan on 2013-11-13
A new Grub2 screen for Trusty Tahr 14.04:

[IMG]http://i.imgur.com/ACNTh8l.jpg[/IMG]

---

### Post by jnmjr on 2013-11-21
Hi Cavsfan, you were refered to me as the one to possibly help solve my problem, I would like to remove the rectangular border from the grub2  menu. I've done quite a bit of searching, lots of posts on customizing  menu but nothing on removing just the border. I have a nice image and the border takes away from it. Any help would be greatly appreciated. Thx in advance.

---

### Post by Cavsfan on 2013-11-21
> **jnmjr said:**
> Hi Cavsfan, you were refered to me as the one to possibly help solve my problem, I would like to remove the rectangular border from the grub2  menu. I've done quite a bit of searching, lots of posts on customizing  menu but nothing on removing just the border. I have a nice image and the border takes away from it. Any help would be greatly appreciated. Thx in advance.

I have never thought about removing the rectangular border. Let me see what I can find.

---

### Post by fantab on 2013-11-21
> **Cavsfan said:**
> I have never thought about removing the rectangular border. Let me see what I can find.

I will look forward to it.
Also is there a way to align grub menu list to the center? I would be great if we could move the list from the current left to center or right alignment, if the background image demands so.

Regards...

---

### Post by Cavsfan on 2013-11-21
> **fantab said:**
> I will look forward to it.
Also is there a way to align grub menu list to the center? I would be great if we could move the list from the current left to center or right alignment, if the background image demands so.

Regards...

I actually do not see where the rectangular border comes from. Although I  can imagine it is used to position the menu items and all that is  displayed at boot time. So, if you could remove the border you  might have other problems.
In the past when I have had a nice picture  that I wanted to use and it didn't work as well as I had wanted I would  either edit the picture via gimp or select another picture for my grub  screen.
You really have to tailor the picture to the grub menu and not vice versa  and the font colors as well, e.g. you have to have light font colors for a dark background picture etc.

If you notice all I have never used are pictures without words; just basic pictures. I also do not see a way to move the menu selections to the middle of the screen.
In Section 4 there is a Links section that will lead you to additional information about Grub2 and that page has a Links section at the bottom which leads to more Grub information.
Feel free to research it and good luck! :)

---

### Post by fantab on 2013-11-21
Yeah, even I select background pics with grub menu layout in mind. Also I have my Grub for 3 seconds, and I feel what we have is pretty good. 
I have done my share of research with regards to aligning menu list to center but couldn't find anything interesting, so far.

---

### Post by Cavsfan on 2013-11-21
> **fantab said:**
> Yeah, even I select background pics with grub menu layout in mind. Also I have my Grub for 3 seconds, and I feel what we have is pretty good. 
I have done my share of research with regards to aligning menu list to center but couldn't find anything interesting, so far.

The border positioning has to be used to parse down the screen for the placement of everything on there. It becomes scrollable if it gets past the end of your screen.
I have a big monitor and have rarely seen that but I have seen it. I have my timeout set to 60 seconds because sometimes my mind wanders or I leave the room before I make the selection.
I have 7 OSs on here and need the time to make up my mind where I'm going lol. :)

---

### Post by jeremy1701 on 2013-12-04
I seem to be having an issue whereby I am unable to update grub. I was instructed to post the original query here to seek further assistance. 

[http://ubuntuforums.org/showthread.php?t=2191652](http://ubuntuforums.org/showthread.php?t=2191652)

The command update-grub does not seem to have any affect on the grub menu. Any suggestions on how to proceed?

---

### Post by Cavsfan on 2013-12-04
> **jeremy1701 said:**
> I seem to be having an issue whereby I am unable to update grub. I was instructed to post the original query here to seek further assistance. 

[http://ubuntuforums.org/showthread.php?t=2191652](http://ubuntuforums.org/showthread.php?t=2191652)

The command update-grub does not seem to have any affect on the grub menu. Any suggestions on how to proceed?

Try this: enter in terminal **sudo grub-install /dev/sda** that is if your grub needs to be on sda, which would be your primary drive, It should just say "installation finished with no errors."
Then enter **sudo update grub** and if the output is not right post the output here. I'll see if I can help.

What does it list when you enter this in terminal?

grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0

```
cavsfan@cavsfan-MS-7529:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0    menuentry "Precise Pangolin 12.04" {
     1    menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     2    menuentry "Quantal Quetzal 12.10" {
     3    menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
     4    menuentry "Raring Ringtail 13.04" {
     5    menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
     6    menuentry "Saucy Salamander 13.10" {
     7    menuentry "Saucy Salamander 13.10 (Recovery Mode)" {
     8    menuentry "Trusty Tahr 14.04" {
     9    menuentry "Trusty Tahr 14.04 (Recovery Mode)" {
    10    menuentry "Linux Mint 13 Nadia" {
    11    menuentry "Linux Mint 13 Nadia (Recovery Mode)" {
    12    menuentry "Windows 7" {
```

---

### Post by jeremy1701 on 2013-12-04
Output of each commad is below. 

```
$  grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0  menuentry 'Kubuntu
     1  submenu 'Advanced options for Kubuntu
     2  menuentry 'Kubuntu, with Linux 3.11.0-14-generic
     3  menuentry 'Kubuntu, with Linux 3.11.0-14-generic (recovery mode)
     4  menuentry 'Kubuntu, with Linux 3.11.0-12-generic
     5  menuentry 'Kubuntu, with Linux 3.11.0-12-generic (recovery mode)
     6  menuentry "Windows UEFI bkpbootmgfw.efi" {
     7  menuentry "Windows Boot UEFI loader" {
     8  menuentry "EFI/toshiba/Boot/bootmgfw.efi" {
     9  menuentry "Windows Boot Manager (UEFI on /dev/sda2)" --class windows --class os {
    10  menuentry 'System setup
```


```
$ sudo grub-install /dev/sda
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0004,2003,2001,2002
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-72-E4-4B) 
Boot0003* EFI Network 0 for IPv4 (00-8C-FA-72-E4-4B) 
Boot0004* Windows Boot Manager
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0000,0004,2003,2001,2002
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-72-E4-4B) 
Boot0003* EFI Network 0 for IPv4 (00-8C-FA-72-E4-4B) 
Boot0004* Windows Boot Manager
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0000* kubuntu
Installation finished. No error reported.

```

```
$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
```

---

### Post by Cavsfan on 2013-12-04
> **jeremy1701 said:**
> Output of each commad is below. 

```
$  grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0  menuentry 'Kubuntu
     1  submenu 'Advanced options for Kubuntu
     2  menuentry 'Kubuntu, with Linux 3.11.0-14-generic
     3  menuentry 'Kubuntu, with Linux 3.11.0-14-generic (recovery mode)
     4  menuentry 'Kubuntu, with Linux 3.11.0-12-generic
     5  menuentry 'Kubuntu, with Linux 3.11.0-12-generic (recovery mode)
     6  menuentry "Windows UEFI bkpbootmgfw.efi" {
     7  menuentry "Windows Boot UEFI loader" {
     8  menuentry "EFI/toshiba/Boot/bootmgfw.efi" {
     9  menuentry "Windows Boot Manager (UEFI on /dev/sda2)" --class windows --class os {
    10  menuentry 'System setup
```


```
$ sudo grub-install /dev/sda
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0004,2003,2001,2002
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-72-E4-4B) 
Boot0003* EFI Network 0 for IPv4 (00-8C-FA-72-E4-4B) 
Boot0004* Windows Boot Manager
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0000,0004,2003,2001,2002
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-72-E4-4B) 
Boot0003* EFI Network 0 for IPv4 (00-8C-FA-72-E4-4B) 
Boot0004* Windows Boot Manager
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0000* kubuntu
Installation finished. No error reported.

```

```
$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
```

OK, I see 2 things wrong: 
1. You must not have the custom file executable. I would recommend editing **/etc/grub.d/40_custom** and then saving it as **06_custom** because the purpose of this grub customization is to have a static menu that only changes when you want it to. Having it in **06_custom** means it will always be on top.
Make sure **40_custom** is not executable **sudo chmod -x /etc/grub.d/40_custom** and after you have saved **06_custom** make it executable **sudo chmod +x /etc/grub.d/06_custom**.
2. You do not have a picture in **/boot/grub/**. Make sure you have a picture that matches your resolution and copy it there via **sudo cp somepicture.jpg /boot/grub/**
Then enter **sudo update-grub** and you should notice a difference.

This is what I see in the output of **sudo update-grub**:
```
cavsfan@cavsfan-MS-7529:/etc/grub.d$ sudo update-grub
Generating grub.cfg ...
[COLOR=#ff0000]Found background image: smoke_skull_light_green_black_10640_1920x1200.jpg[/COLOR]
[COLOR=#ff0000]Adding Ubuntu Precise Pangolin 12.04, Quantal Quetzal 12.10, Raring Ringtail 13.04, Saucy Salamander 13.10, Trusty Tahr 14.04, Linux Mint 13 Nadia and Windows 7[/COLOR]
Found linux image: /boot/vmlinuz-3.12.0-5-generic
Found initrd image: /boot/initrd.img-3.12.0-5-generic
Found linux image: /boot/vmlinuz-3.12.0-4-generic
Found initrd image: /boot/initrd.img-3.12.0-4-generic
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sda2
Found Ubuntu 12.10 (12.10) on /dev/sda6
Found Ubuntu 13.10 (13.10) on /dev/sda7
Found Ubuntu 13.04 (13.04) on /dev/sda8
Found Linux Mint 13 Maya (13) on /dev/sda9
done

```

That is with everything but 20_memtest86+ executable. Let's see what difference those 2 changes make. It should make what is in red appear in the output.

---

### Post by jeremy1701 on 2013-12-04
Thanks for the info above. Unfortunately, making those changes seems to have no effect as well. I tried purging and re-installing grub using the live 13.10 disc, still nothing has changed. Here is new output:

[http://paste.ubuntu.com/6522428/](http://paste.ubuntu.com/6522428/)

---

### Post by fantab on 2013-12-04
> **jeremy1701 said:**
> Thanks for the info above. Unfortunately, making those changes seems to have no effect as well. I tried purging and re-installing grub using the live 13.10 disc, still nothing has changed. Here is new output:

[http://paste.ubuntu.com/6522428/](http://paste.ubuntu.com/6522428/)

Did you use an image as suggested? Did it appear as Grub menu background when you did "update-grub"?

---

### Post by jeremy1701 on 2013-12-05
Success!! In addition to the edits to /etc/default/grub, I had to add savedefault to each menu entry in vim /etc/grub.d/25_custom. 

*Note: Updated original post*

---

### Post by Cavsfan on 2013-12-05
> **jeremy1701 said:**
> Thanks for the info above. Unfortunately, making those changes seems to have no effect as well. I tried purging and re-installing grub using the live 13.10 disc, still nothing has changed. Here is new output:

[http://paste.ubuntu.com/6522428/](http://paste.ubuntu.com/6522428/)

All I see in the 06_custom file is this:
```
### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
### END /etc/grub.d/06_custom ###
```

I do not see that you have any picture in **/boot/grub/**. The fact that grub finds a picture in that location lets you add font colors in **05_debian_theme**. If there is no picture you cannot have colored fonts.
I seen that you wanted to have a default OS that it will boot to and with the menuentries in **06_custom**, you can control that in **/etc/default/grub** where it says **GRUB_DEFAULT=0** (this starts at 0 for the first line,1 for the second line,2 for the 3rd line etc.).

Here is a copy of my 06_custom file modify it to suit your needs by changing the partitions in red on the first example and the text between the quotes then save it and make it executable by **sudo chmod +x /etc/grub.d/06_custom** in terminal.
Then be sure to enter **sudo update-grub** for the changes to take effect, Then you should see the picture listed and the echo output listed.
I have my default set to 12 for the 13th entry.

```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Precise Pangolin 12.04, Quantal Quetzal 12.10, Raring Ringtail 13.04, Saucy Salamander 13.10, Trusty Tahr 14.04, Linux Mint 13 Nadia and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Precise Pangolin 12.04" {
    set root=([COLOR="#FF0000"]hd0,2[/COLOR])
        linux /vmlinuz root=/dev/[COLOR="#FF0000"]sda2[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Raring Ringtail 13.04" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro quiet splash
        initrd /initrd.img
}
menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Saucy Salamander 13.10" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "Saucy Salamander 13.10 (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Linux Mint 13 Nadia" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash
        initrd /initrd.img
}
menuentry "Linux Mint 13 Nadia (Recovery Mode)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}
```

---

### Post by Cavsfan on 2013-12-05
> **jeremy1701 said:**
> Success!! In addition to the edits to /etc/default/grub, I had to add savedefault to each menu entry in vim /etc/grub.d/25_custom. 

*Note: Updated original post*

With the entries in 06_custom as in my previous post you don't need savedefault. You can control the line number in **/etc/default/grub**.

Here is a copy of mine:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=12
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=60
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2 

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1200-24

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Cavsfan on 2013-12-05
Then with your menu entries in **06_custom** you will not need **25_custom** and you should make it unexecutable **sudo chmod -x /etc/grub.d/25_custom** and then **sudo update-grub**.

---

### Post by Cavsfan on 2013-12-05
Here is my output:
```
cavsfan@cavsfan-MS-7529:~$ sudo update-grub
[sudo] password for cavsfan: 
Generating grub.cfg ...
Found background image: smoke_skull_light_green_black_10640_1920x1200.jpg
Adding Ubuntu Precise Pangolin 12.04, Quantal Quetzal 12.10, Raring Ringtail 13.04, Saucy Salamander 13.10, Trusty Tahr 14.04, Linux Mint 13 Nadia and Windows 7
done
```

---

### Post by jeremy1701 on 2013-12-05
Hi Cavsfan,
You are correct about making the entries in 06_custom. They did work in that location, however remember the last OS booted did not. I re-ran Boot Repair from 13.10 live disc as suggested by fantab. This effectively removed the 06_custom file and replaced it with 25_custom (again). 

Thanks for all of your assistance. I will try to add the image now. My main issue was booting the previous OS. 

How do I know the resolution of my grub screen?

---

### Post by fantab on 2013-12-05
The resoultion should be same as your monitor/graphics card that you have set.

---

### Post by jeremy1701 on 2013-12-05
Awesome! Grub image is working. Looks great. Thanks again for all the assistance!

---

### Post by Cavsfan on 2013-12-05
> **jeremy1701 said:**
> Hi Cavsfan,
You are correct about making the entries in 06_custom. They did work in that location, however remember the last OS booted did not. I re-ran Boot Repair from 13.10 live disc as suggested by fantab. This effectively removed the 06_custom file and replaced it with 25_custom (again). 

Thanks for all of your assistance. I will try to add the image now. My main issue was booting the previous OS. 

How do I know the resolution of my grub screen?

```
cavsfan@cavsfan-MS-7529:~$ xdpyinfo  | grep dimensions
  [COLOR=#ff0000]dimensions[/COLOR]:    1920x1200 pixels (508x318 millimeters)

```

---

### Post by Cavsfan on 2013-12-05
> **jeremy1701 said:**
> Awesome! Grub image is working. Looks great. Thanks again for all the assistance!

You are very welcome. Thank you for checking out my wiki. I was hoping it didn't have anything to do with EFI.
You should be able to get a screen just like the ones in my examples. And control the default in **/etc/default/grub** with **GRUB_DEFAULT=number**
And what is great is you never have to change that unless you remove or add an OS. That the main purpose of this wiki to make it "maintenance free".

Here you can see the number to put there by entering this in terminal:

```
cavsfan@cavsfan-MS-7529:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0	menuentry "Precise Pangolin 12.04" {
     1	menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     2	menuentry "Quantal Quetzal 12.10" {
     3	menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
     4	menuentry "Raring Ringtail 13.04" {
     5	menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
     6	menuentry "Saucy Salamander 13.10" {
     7	menuentry "Saucy Salamander 13.10 (Recovery Mode)" {
     8	menuentry "Trusty Tahr 14.04" {
     9	menuentry "Trusty Tahr 14.04 (Recovery Mode)" {
    10	menuentry "Linux Mint 13 Nadia" {
    11	menuentry "Linux Mint 13 Nadia (Recovery Mode)" {
    12	menuentry "Windows 7" {

```

I have mine set to Windows 7 (12) for my wife in case it reboots or something.

Good luck! :)

---

### Post by Cavsfan on 2014-01-09
I just noticed that in Trusty Tahr 14.04 the font is in a different directory. So, to produce the font enter this:
```
sudo grub-mkfont --output=/boot/grub/DejaVuSansMono.pf2 \
 --size=24 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
```

and it will still give these meaningless messages as before:
```
Unknown gsub font feature 0x63636d70 (ccmp)
Unknown gsub font feature 0x646c6967 (dlig)
Unsupported substitution flag: 0x9
Unsupported substitution flag: 0x9
Unknown gsub font feature 0x6c6f636c (locl)
Unknown gsub font feature 0x6c6f636c (locl)
Unsupported substitution flag: 0x9

```

The wiki will be updated when Trusty Tahr is at final release.

---

### Post by Cavsfan on 2014-01-09
New picture on Trusty Tahr 14.04 with cyan as normal font colors and white as highlight. 
grub-install (GRUB) 2.00-22

[[IMG]http://en.zimagez.com/miniature/grub2-20.jpg[/IMG]]("http://en.zimagez.com/zimage/grub2-20.php")

---

### Post by Cavsfan on 2014-01-16
Minimal 

[[IMG]http://en.zimagez.com/miniature/20140115170656.jpg[/IMG]]("http://en.zimagez.com/zimage/20140115170656.php")

---

### Post by Cavsfan on 2014-01-24
Since Raring Ringtail Ubuntu 13.04 reaches it's End of Life Date on January 27th I am going to pull that part out of the wiki. [https://lists.ubuntu.com/archives/ubuntu-security-announce/2014-January/002367.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2014-January/002367.html)
It shouldn't take too long. I hope this doesn't inconvenience any one.

---

### Post by Cavsfan on 2014-01-24
I just left the pictures with Raring as examples. But, the Raring Ringtail part of the wiki is now gone.

---

### Post by Cavsfan on 2014-01-30
Grub 2.2 beta on Trusty Tahr 14.04:

[[IMG]http://en.zimagez.com/miniature/20140130153140.jpg[/IMG]]("http://en.zimagez.com/zimage/20140130153140.php")

---

### Post by Cavsfan on 2014-03-24
New screenie on Trusty:

[[IMG]http://en.zimagez.com/miniature/20140324102316.jpg[/IMG]]("http://en.zimagez.com/zimage/20140324102316.php")

It is a black cat but I believe the black is overwhelmed by the blue therefore it's more of a blue cat. :)

---

### Post by Cavsfan on 2014-04-17
I just updated the wiki. I only changed editing **/etc/grub.d/05_debian_theme**.
I took out Quantal Quetzel 12.10 since it reaches EOL this month and added Trusty Tahr 14.04 as it was released today.

I left references to other version in it just for the examples. There is no real difference between Saucy Salamander 13.10 and Trusty Tahr 14.04.

Cheers :)

---

### Post by Cavsfan on 2014-05-01
New screeny with Utopic Unicorn 14.10 added. Ironically this background is my Grub2 bootup screen, my login screen to Ubuntu Trusty Tahr 14.04 and my background on Trusty. :)

[[IMG]http://en.zimagez.com/miniature/20140501grub2.jpg[/IMG]]("http://en.zimagez.com/zimage/20140501grub2.php")

---

### Post by Cavsfan on 2014-05-22
In Linux Mint 17 with the grub version that Trusty uses 2.02~beta2-9 they have an additional grub file **/etc/grub.d/06_mint_theme** which controls the font colors in the box around the menu as well as the menu itself.
That is if there is a picture in **/boot/grub/**. Or if there's no picture the font sizes and font colors will not be used and the screen will be as default.
You can either make it unexecutable - **sudo chmod -x /etc/grub.d/06_mint_theme** and put the fonts both normal and highlight in **/etc/grub.d/05_debian_theme** or you can tailor both to suit your needs.

Here I used both: making the highlight color in the menu red and leaving the normal color white and in **05_debian_theme**, which controls just the top and bottom in this case, I made it light-cyan and cyan.

[[IMG]http://en.zimagez.com/miniature/20140522151808.jpg[/IMG]]("http://en.zimagez.com/zimage/20140522151808.php")

---

### Post by Cavsfan on 2014-06-29
Since systemd comes installed on Utopic Unicorn 14.10 (development release) I included a line to boot using systemd instead of the default upstart.

[[IMG]http://en.zimagez.com/miniature/20140629115939.jpg[/IMG]]("http://en.zimagez.com/zimage/20140629115939.php")

I added this option in **/etc/grub.d/06_custom**:
```
menuentry "Utopic Unicorn 14.10 systemd (Devel Branch)" {
    set root=(hd[COLOR=#ff0000]0,5[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=#ff0000]sda5[/COLOR] ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
```

Just change what is in red to match the partion your Utopic install is on; mine is on hard disk 1, partition 5.

I also changed the green line in my signature to point to this thread as the 1st post has the link to the actual wiki. I thought that would be easier.
Systemd seems to have better bootup times and is possibly a little more stable *YMMV.*

---

### Post by Cavsfan on 2014-07-27
I just updated the Community Wiki by removing Quantal Quetzal 12.10, Raring Ringtail 13.04 and Saucy Salamander 13.10 as they are no longer supported.
I also added Trusty Tahr 14.04, Mint 13 Maya and Mint 17 Quina to the **06_custom** file. I just need to update the pictures now.

Plus I changed the link in my signature a while back to point to this thread. You can get to the Wiki via the green link in the 1st post of this thread.
I thought that would make it simpler.

---

### Post by Taal_Mahret on 2014-08-09
I noticed a few screenshots on google image search that show the menu itself moved from its default screen location.  Is this manually configurable or can programs such as grub customizer do this as well?

---

### Post by Cavsfan on 2014-08-09
> **Taal_Mahret said:**
> I noticed a few screenshots on google image search that show the menu itself moved from its default screen location.  Is this manually configurable or can programs such as grub customizer do this as well?

I do not know of any way to move the menu from it's default location. The font size can be changed but I haven't even tried that.
Here is where I got the font command to make the font for grub: [http://ubuntuforums.org/showthread.php?t=1195275&page=29&p=8764581#post8764581](http://ubuntuforums.org/showthread.php?t=1195275&page=29&p=8764581#post8764581)
I believe I have seen when the menu is longer than the screen size that it is scrollable.

See the FYI at the bottom about the **--size=** part. I'm not familiar with grub customizer either so I couldn't say what it can or can't do.

It might be that this was on another Linux OS besides Ubuntu or Mint. Mint 17 Qiana comes with a **/etc/grub.d/06_mint_theme** file which has the font colors for the menu and the highlighted option.
Ubuntu only uses special font colors if a picture is found in **/boot/grub/** also where the font exists after it is created.

---

### Post by Cavsfan on 2014-08-28
You tell me which is better this - default:
[[IMG]http://en.zimagez.com/miniature/defaultgrub.jpg[/IMG]]("http://en.zimagez.com/zimage/defaultgrub.php")

Or this - custom:
[[IMG]http://en.zimagez.com/miniature/customgrub.jpg[/IMG]]("http://en.zimagez.com/zimage/customgrub.php")

I had to customize it just to get it to let me login to anything other than the top option Utopic Mate 14.10.
When I tried the bottom Linux Mint 17 on the default grub, which says it's on sda8 and it is. It took me to a Mint 17 screen with 4 dots that would never go to the login screen.
So finally I pressed Alt+Cntl+F1 to login CLI and when I did it displayed 12.04.5 :p.
I installed the grub while I was there **sudo grub-install /dev/sda** and then **sudo reboot** and sure enough the grub was on Precise 12.04.5.

That allowed me to boot to Mint 17 and install the grub there which is what the 2nd picture is.

I just don't see how the default even works when you have multiple systems on the computer. I have 7 right now.
I even checked the /etc/fstab file on both systems and it was correct.

---

### Post by Bashing-om on 2014-08-28
Cavsfan; Hi ! once more;

I do prefer the "customised" version.
I to continue to struggle with how I prefer to boot multiple operating systems across multiple hard drives. It is a learning process and I do make up some interesting situations.
When all said and done, your method is the more pleasing and easy-ist to maintain.

My contemplated next adventure is booting 14.10 from .iso in grub.

[INDENT][INDENT][INDENT]oh happy days
[/INDENT][/INDENT][/INDENT]

---

### Post by Cavsfan on 2014-08-28
> **Bashing-om said:**
> Cavsfan; Hi ! once more;

I do prefer the "customised" version.
I to continue to struggle with how I prefer to boot multiple operating systems across multiple hard drives. It is a learning process and I do make up some interesting situations.
When all said and done, your method is the more pleasing and easy-ist to maintain.

My contemplated next adventure is booting 14.10 from .iso in grub.[INDENT][INDENT][INDENT]oh happy days
[/INDENT]
[/INDENT]
[/INDENT]


Hi! Thanks for the kind words! :D I didn't think anyone would answer that question.
I never came up with this idea. I got it from Ranch Hand and then Drs305 helped out a lot too. Ranch hand told me how to do it and it took me probably a month or two before I understood it enough to try it.
Then the more I looked at it the easier it got. I still have to refer the the Wiki but a lot is in memory.

When I noticed what I stated at the bottom of my post about trying to get to Mint 17 via the default and it "looked like Mint 17" but was really Precise 12.04 pretty much cinches the whole proposition.
When it comes down to it since grub has evolved there is very little that you have to do. Making the initial 06_custom file would be the biggest challenge me thinks. 

But drop a picture into /boot/grub and when grub finds it there it uses the picture and special fonts with the colors. It has to be the simplest and fault free method out there.

Good luck on that next adventure! :D

---

### Post by fantab on 2014-09-16
Is it possible to create a 'sub-menu' in 40_custom?

---

### Post by oldfred on 2014-09-16
I have not tried a sub-menu, but back to help from drs305

       Grub 1.99 Submenus
[http://ubuntuforums.org/showthread.php?t=1739336h](http://ubuntuforums.org/showthread.php?t=1739336h)

    

@bashing-om
```
menuentry "Ubuntu 14.10 Utopic ISO 64bit Daily" {
    set isofile="/iso/utopic-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

Note I have mulitiple drives and the grub I boot is always hd0, and the drive I then have my ISO folder on is hd2 and happens to be gpt partitioned so I have to tell it that. You may have to use msdos.

Also hidden away in one of drs305's mega-threads on booting was the reference to using configfile in grub. So I use that in my grub 40_custom and create a configfile menu entry in the ISO folder.

I added this to the top as my own reminder (in 40_custom without #):

# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
# }

I really like configfile, as every time I would edit 40_custom I would forget the sudo update-grub and have to reboot again. Editing text file livecdimage.cfg is just auto loaded with changes.

---

### Post by Cavsfan on 2014-09-16
> **fantab said:**
> Is it possible to create a 'sub-menu' in 40_custom?

I have never tried to create a sub-menu; never seen a reason to.  The wiki says to save **40_custom** as **06_custom** so it appears on the very top whether **10_linux**, **20_memtest86+** and **30_os-prober** are executable or not.

It will only boot to the latest installed kernel. If you wanted to boot to an older kernel you would need to install grub on that partition and make **10_linux** executable.
Here is my **06_custom** file (I can boot to Utopic 14.10 and Utopic Mate 14.10 with upstart or systemd just by selecting the menu option for it):

[PHP]#!/bin/sh
echo 1>&2 "Adding Precise Pangolin 12.04, Trusty Tahr 14.04, Utopic Unicorn 14.10, Utopic Unicorn 14.10 Mate, Mint 13 Nadia, Mint 17 Quina and Windows 7"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Precise Pangolin 12.04 LTS" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 LTS (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 LTS" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet splash
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 LTS (Recovery Mode)" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 (devel branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 systemd (Devel Branch)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 (devel branch) (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 Mate (devel branch)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 Mate systemd (Devel Branch)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
menuentry "Utopic Unicorn 14.10 Mate (devel branch) (Recovery Mode)" {
    set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Mint 13 Nadia" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "Mint 13 Nadia (Recovery Mode)" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Mint 17 Qiana LTS" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro quiet splash
        initrd /initrd.img
}
menuentry "Mint 17 Qiana LTS (Recovery Mode)" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}[/PHP]

You can see a picture of what it looks like a few posts back. I have my grub installed on Mint 17 Quina because it has a **06_mint_theme** file to make the box around the menu and the menu itself a different color than the top and bottom.
On Ubuntu you can only have 2 colors.

You could leave it as is but without adding the 2nd echo line (above) that you control, and leave the +3 instead of changing it to +4 but then you will only see this when you update grub:
The echo line is meant just for listing the contents of **06_custom** and is for your benefit only.
(The +3 says to start execution at the 3rd line down, the +4 says to start execution at the 4th line down). This I learned from Drs305. 

```
cavsfan@cavsfan-MS-7529:~$ sudo update-grub
[sudo] password for cavsfan: 
Generating grub configuration file ...
Found background image: Nobody_likes_me.jpg
done
```

**40_custom** file as default: 

[PHP]#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.[/PHP]

---

### Post by fantab on 2014-09-16
[QUOTE=Cavsfan]I have never tried to create a sub-menu; never seen a reason to.[/QUOTE]

I want to create two submenus: one to put all Ubuntu stuff, like 'Previous linux', 'Recovery' (I have both 14.04 & 14.10(devel). I was thinking of only one submenu for both versions of ubuntu...
And one submenu for 'utilities' like, memtest, isos, and knoppix.
Just to keep the main menu as consise as possible.

By the way, I use grub from Archlinux. I have not added Arch entries to 40_custom.. and this gives me a 'submenu' for Arch...
I don't have os-prober installed. If I install it I will have two Ubuntu submenus for each version. I want only one submenu for both. And I'd still need one for 'utilities'.
Since it is difficult to NOT install grub with Ubuntu install, I have Ubuntu grubs in PBR. All my HDDs are 'msdos' still.

I tested adding a submenu but it didn't work:

```
submenu 'Ubuntu 14.04 - Recovery
menuentry 'Ubuntu 14.04 - Previous
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root=(hd1,msdos2)
        search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hin$
        linux   /boot/vmlinuz-3.13.0-35-generic root=UUID=94797b8a-xxxx-4x6c-8xc8-be93axxxxxdb ro $
        initrd  /boot/initrd.img-3.13.0-35-generic
```

which results in:

```
$ update-grub
Generating grub configuration file ...
Found background: /boot/grub/grubbg5.png
Found linux image: /boot/vmlinuz-linux-lts
Found initrd image: /boot/initramfs-linux-lts.img
Found fallback initramfs image: /boot/initramfs-linux-lts-fallback.img
error: $.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 204
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
```

I have searched the net but I haven't found anything meaningful regarding creating submenu in 40_custom.
So I wondered if it is even possible to have one... However the following had made me optimistic:

```
[COLOR=Blue]**submenu "My ISOs" {**[/COLOR]
menuentry "Natty_test.iso
isofile=natty-desktop-amd64.iso        
loopback loop (hd1,6)/iso/$isofile        
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
menuentry 'ISO SystemRescue   sdb5-vm'                     {
isofile=systemrescuecd-x86-2.0.1.iso
loopback loop (hd1,5)/$isofile
linux (loop)/isolinux/rescue64 setkmap=us isoloop=/$isofile
initrd (loop)/isolinux/initram.igz
}

```

I'll have to explore this more on the weekend perhaps....

Regards

---

### Post by oldfred on 2014-09-17
Instead of sub menu I use the configfile. That becomes one permanent entry in 40_custom. And then the file in another location looks like standard grub entries but is just a file.

See #232 above.

Or search for configfile in this long thread.
[http://ubuntuforums.org/archive/index.php/t-1549847.html](http://ubuntuforums.org/archive/index.php/t-1549847.html)

---

### Post by Cavsfan on 2014-09-17
> **fantab said:**
> I want to create two submenus: one to put all Ubuntu stuff, like 'Previous linux', 'Recovery' (I have both 14.04 & 14.10(devel). I was thinking of only one submenu for both versions of ubuntu...
And one submenu for 'utilities' like, memtest, isos, and knoppix.
Just to keep the main menu as consise as possible.

> **oldfred said:**
> Instead of sub menu I use the configfile. That becomes one permanent entry in 40_custom. And then the file in another location looks like standard grub entries but is just a file.

See #232 above.

Or search for configfile in this long thread.
[http://ubuntuforums.org/archive/index.php/t-1549847.html](http://ubuntuforums.org/archive/index.php/t-1549847.html)

I'm not sure how to create submenus nor do I wish to include them in this wiki if a way is found to create them. 
Again this wiki is about keeping it simple and saving **40_custom** as **06_custom**.
But good luck in your pursuits. :)

A few posts back it was proven to me that when you install several systems (I have 7) the default grub does not work very well.
I selected Linux Mint 17 Qiana at the bottom on /dev/sda8, which was correct and the screen went to display Mint 17 with the dots moving across the screen till the cows came home. :p
I had to press Cntl+Alt+F1 to login to tty and then seen I was in Precise which I cannot explain.
I have one swap file and the /etc/fstab entries were all correct. I literally had to install grub on Precise (that is customized) just to get it to boot to the OS I wanted.

Then I was able to get to Mint 17 Qiana to install it there.

---

### Post by oldfred on 2014-09-17
Os-prober finds 10 Ubuntu and XP in my system and I do not have any issues with grub.

But I have to turn off os-prober as soon as I install or it takes forever as it has to scan 4 drives and all those installs. I do have different grub boot loaders in every MBR, but default boot from SSD and now 14.04. Many of the installs are obsolete, but I do not currently need space and just overwrite an old install with a new one when I want to test something.

But grub does remember where it was originally installed and will reinstall to that location on a major update.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by Cavsfan on 2014-09-17
> **oldfred said:**
> Os-prober finds 10 Ubuntu and XP in my system and I do not have any issues with grub.

But I have to turn off os-prober as soon as I install or it takes forever as it has to scan 4 drives and all those installs. I do have different grub boot loaders in every MBR, but default boot from SSD and now 14.04. Many of the installs are obsolete, but I do not currently need space and just overwrite an old install with a new one when I want to test something.

But grub does remember where it was originally installed and will reinstall to that location on a major update.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc

[COLOR=#ff0000]Edit: Duh me! It does tell the hard drive but I only have one. The other is a USB drive that I use to backup stuff to.[/COLOR] This renders much of what I've posted moot. #-o

That's odd as I cannot use the default grub. I don't think I tried booting to windows 7 via 30_os-prober but the Linux systems were incorrect although I didn't test each of them. 
One was proof enough for me to get back into one of the customized grubs because I know they work. (I wish I had an SSD, hopefully on my next system.)

I'm not sure about that command. Here is what it output:
```
cavsfan@cavsfan-MS-7529:~$ sudo debconf-show grub-pc 
[sudo] password for cavsfan: 
  grub-pc/mixed_legacy_and_grub2: true
  grub2/kfreebsd_cmdline:
  grub2/linux_cmdline_default: quiet splash
  grub-pc/install_devices_failed_upgrade: true
  grub2/linux_cmdline:
  grub-pc/timeout: 10
  grub-pc/disk_description:
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed: false
  grub2/device_map_regenerated:
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/install_devices_disks_changed:
  grub-pc/hidden_timeout: true
  grub-pc/install_devices_empty: false
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD5003ABYX-01WERA2_WD-WMAYP6803321
  grub-pc/partition_description:
```

I cannot tell what /dev/disk/by-id/ata-WDC_WD5003ABYX-01WERA2_WD-WMAYP6803321 is. But, it looks like some sort of identifier of my entire 500GB drive.
It is a Western Digital WD RE4 WD5003ABYX 500GB 7200 RPM hard drive.
```
cavsfan@cavsfan-MS-7529:~$ sudo blkid
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" PARTUUID="a55f55ec-01" 
/dev/sda2: LABEL="Precise" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" PTTYPE="dos" PARTUUID="a55f55ec-02" 
/dev/sda3: UUID="e14dc02e-6ea8-4c95-b4d0-9dc04d32294d" TYPE="swap" PARTUUID="a55f55ec-03" 
/dev/sda5: LABEL="Utopic" UUID="7c76d1de-7439-4b55-b587-898f104235da" TYPE="ext4" PARTUUID="a55f55ec-05" 
/dev/sda6: LABEL="Trusty" UUID="d3281f82-3582-4081-b4d7-4769a2f427c5" TYPE="ext4" PARTUUID="a55f55ec-06" 
/dev/sda7: LABEL="Mint-Maya" UUID="77cf61db-2e8b-4531-9594-80f35ad4dc69" TYPE="ext4" PARTUUID="a55f55ec-07" 
/dev/sda8: LABEL="Mint-Quina" UUID="673f25f0-6149-4da7-98f8-4ebfe08a2188" TYPE="ext4" PARTUUID="a55f55ec-08" 
/dev/sda9: LABEL="Utopic-Mate" UUID="9c1694e3-0a35-4cf2-9c74-4103abce882f" TYPE="ext4" PARTUUID="a55f55ec-09" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs" PARTUUID="f87b4c9a-01"
```

Grub was initially installed on the partition that Precise is on. Then with Drs305's help and as I gained knowledge about all of this I added more logical partitions.
On my system whenever grub is updated to a newer version it installs the grub on the partition that is being updated and updates it there but does not touch any other install.
I then boot into the one I want my grub installed and install it there.

Whenever I have had any grub update it installs to the partition that I am currently on. I have never seen it install to a different partition and I don't see how it could.

And as far as submenus and booting to a previous kernel etc. we have already been through that. I got one to work with the newest kernel and one for the previous kernel.
But since this is using symlinks as soon as a new kernel was installed it messed up. So, I dropped that idea.

That is why I say I'm not venturing into that territory because this wiki about customizing the grub menu is meant to keep it simple. 
I think that was Ranch Hand's intention. I got his OK before I created the first how to and then the wiki.

---

### Post by oldfred on 2014-09-17
Since partitions & UUIDs change the install drive is the model & serial number of the drive. 
And one or two that posted with installs to partitions showed p1 or p2 for which partition grub was then installed into.
And each and every install may have the same entry, and on grub updates that grub is then installed to MBR. As long as only your working install has the MBR you are ok.  

You can in other installs blank out the entry with this, just un-select all entries:
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, tab & enter to accept, do not normally choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by Cavsfan on 2014-09-17
> **oldfred said:**
> Since partitions & UUIDs change the install drive is the model & serial number of the drive. 
And one or two that posted with installs to partitions showed p1 or p2 for which partition grub was then installed into.
And each and every install may have the same entry, and on grub updates that grub is then installed to MBR. As long as only your working install has the MBR you are ok.  

You can in other installs blank out the entry with this, just un-select all entries:
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, tab & enter to accept, do not normally choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

I'm sorry but I think maybe I spouted to much and posted it before I realized what you were really saying.
I only have one hard drive, so there is no problem here. It remains on that hard drive. 
Although for about 3-4 versions of Ubuntu I had to turn my USB drive off or it would either hang forever or try to install grub to that drive. 
I think that problem was solved when I installed Trusty; I didn't even have to turn the USB drive off and it wanted to install to sda which is what I wanted.
So, I guess they have made improvements.

---

### Post by fantab on 2014-09-18
I got it.

Here:
```

submenu 'Ubuntu 14.04 - options' [COLOR=#008000]$menuentry_id_option 'gnulinux-advanced-[/COLOR][COLOR=#008000]947xxxxx-610f-4xxx-87c8-bexxxxx0eedb[/COLOR][COLOR=#008000]' {
[/COLOR]menuentry 'Ubuntu 14.04 - Previous'[COLOR=#008000] --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-35-generic-advanced-[/COLOR][COLOR=#008000][COLOR=#008000]947xxxxx-610f-4xxx-87c8-bexxxxx0eedb[/COLOR]'[/COLOR] {
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root=(hd1,msdos2)
        search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  947xxxxx-610f-4xxx-87c8-bexxxxx0eedb
        linux   /boot/vmlinuz-3.13.0-35-generic root=UUID=947xxxxx-610f-4xxx-87c8-bexxxxx0eedb ro 
        initrd  /boot/initrd.img-3.13.0-35-generic
    }
menuentry 'Ubuntu 14.04 - Recovery'[COLOR=#008000] --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-35-generic-advanced-[/COLOR][COLOR=#008000][COLOR=#008000]947xxxxx-610f-4xxx-87c8-bexxxxx0eedb[/COLOR]'[/COLOR] {
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root=(hd1,msdos2)
        search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  947xxxxx-610f-4xxx-87c8-bexxxxx0eedb
        linux   /boot/vmlinuz-3.13.0-35-generic root=UUID=947xxxxx-610f-4xxx-87c8-bexxxxx0eedb ro recovery nomodeset
        initrd  /boot/initrd.img-3.13.0-35-generic
    }
}

```

I was not adding the --class... and there were some syntax errors which I corrected from relooking a grub.cfg in Ubuntu and grub manual:
```
**submenu** *title  [--class=class …] [--users=users]  [--unrestricted] [--hotkey=key]  { menu entries … }*
```
I have discovered one more thing... 'update-grub' was also including entries from /etc/grub.d/40_custom.bak and I ended up with dual entries from both 40_custom and 40_custom.bak...
I removed 40_custom.bak from /etc/grub.d and grub menu looks great.
I'll post a screenshot soon.

---

### Post by oldfred on 2014-09-18
Grub processes any file starting with two digits and an underscore that is executeable. 
Either turn execute bit off or put bak at beginning of name. Then you can keep it it /etc/grub.d if you want.

I keep my backups & copies of 40_custom in a folder in /home so my rsync backup of /home automatically gets that file also.

---

### Post by Cavsfan on 2014-09-18
> **fantab said:**
> I got it.

Here:
```

submenu 'Ubuntu 14.04 - options' [COLOR=#008000]$menuentry_id_option 'gnulinux-advanced-[/COLOR][COLOR=#008000]947xxxxx-610f-4xxx-87c8-bexxxxx0eedb[/COLOR][COLOR=#008000]' {
[/COLOR]menuentry 'Ubuntu 14.04 - Previous'[COLOR=#008000] --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-35-generic-advanced-[/COLOR][COLOR=#008000][COLOR=#008000]947xxxxx-610f-4xxx-87c8-bexxxxx0eedb[/COLOR]'[/COLOR] {
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root=(hd1,msdos2)
        search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  947xxxxx-610f-4xxx-87c8-bexxxxx0eedb
        linux   /boot/vmlinuz-3.13.0-35-generic root=UUID=947xxxxx-610f-4xxx-87c8-bexxxxx0eedb ro 
        initrd  /boot/initrd.img-3.13.0-35-generic
    }
menuentry 'Ubuntu 14.04 - Recovery'[COLOR=#008000] --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-35-generic-advanced-[/COLOR][COLOR=#008000][COLOR=#008000]947xxxxx-610f-4xxx-87c8-bexxxxx0eedb[/COLOR]'[/COLOR] {
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root=(hd1,msdos2)
        search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  947xxxxx-610f-4xxx-87c8-bexxxxx0eedb
        linux   /boot/vmlinuz-3.13.0-35-generic root=UUID=947xxxxx-610f-4xxx-87c8-bexxxxx0eedb ro recovery nomodeset
        initrd  /boot/initrd.img-3.13.0-35-generic
    }
}

```

I was not adding the --class... and there were some syntax errors which I corrected from relooking a grub.cfg in Ubuntu and grub manual:
```
**submenu** *title  [--class=class …] [--users=users]  [--unrestricted] [--hotkey=key]  { menu entries … }*
```
I have discovered one more thing... 'update-grub' was also including entries from /etc/grub.d/40_custom.bak and I ended up with dual entries from both 40_custom and 40_custom.bak...
I removed 40_custom.bak from /etc/grub.d and grub menu looks great.
I'll post a screenshot soon.

I cannot see that being maintenance free. You have hard coded the kernel numbers and I believe the UUIDs. You will have to change it every time a new kernel gets installed.
So that would seem to defeat the purpose of this wiki which is: once you make the changes you _never_ have to touch grub again unless you install another system on another partition or remove one.

Oldfred is right all you have to do is **sudo chmod -x <file-name>** to make it unexecutable and then **sudo update-grub** of course and it will be taken out of the mix.

When you enter this in terminal the green files will be the executable ones.

```
cavsfan@cavsfan-MS-7529:~$ ls -l /etc/grub.d/*
-rwxr-xr-x 1 root root  9424 Jan 29  2014 [COLOR=#008000]/etc/grub.d/00_header[/COLOR]
-rwxr-xr-x 1 root root  6141 Apr  1 17:21 [COLOR=#008000]/etc/grub.d/05_debian_theme[/COLOR]
-rwxr-xr-x 1 root root  2752 Sep 16 09:38 [COLOR=#008000]/etc/grub.d/06_custom[/COLOR]
-rw-r--r-- 1 root root 11611 Jul 24 13:39 /etc/grub.d/10_linux
-rwxr-xr-x 1 root root 10418 Jul 24 13:39 [COLOR=#008000]/etc/grub.d/20_linux_xen[/COLOR]
-rw-r--r-- 1 root root  1992 Mar  6  2014 /etc/grub.d/20_memtest86+
-rw-r--r-- 1 root root 11692 Apr 11 06:51 /etc/grub.d/30_os-prober
-rwxr-xr-x 1 root root  1416 Jan 29  2014 [COLOR=#008000]/etc/grub.d/30_uefi-firmware[/COLOR]
-rwxr-xr-x 1 root root   214 Jan 29  2014 [COLOR=#008000]/etc/grub.d/40_custom[/COLOR]
-rwxr-xr-x 1 root root   216 Jan 29  2014 [COLOR=#008000]/etc/grub.d/41_custom[/COLOR]
-rw-r--r-- 1 root root   483 Jan 29  2014 /etc/grub.d/README
```

Let us know how it goes as new kernels are added.

---

### Post by fantab on 2014-09-22
> I cannot see that being maintenance free. You have hard coded the kernel  numbers and I believe the UUIDs. You will have to change it every time a  new kernel gets installed.

```
menuentry '[COLOR=#a52a2a]Ubuntu 14.04[/COLOR] [COLOR=#a52a2a](sdb2)[/COLOR]' {
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root=(hd1,msdos2)
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  /dev/sdb2
    linux /vmlinuz root=/dev/sdb2 ro  quiet splash $vt_handoff
    initrd /initrd.img
}

**submenu** [COLOR=#a52a2a]'Ubuntu 14.04 - options[/COLOR]' $menuentry_id_option 'gnulinux-advanced-/dev/sdb2' {
menuentry '[COLOR=#a52a2a]Ubuntu 14.04 - Previous[/COLOR]' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-35-generic-advanced-/dev/sdb2' {
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root=(hd1,msdos2)
        search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  /dev/sdb2
        linux   /boot/vmlinuz-3.13.0-35-generic root=/dev/sdb2 ro 
        initrd  /boot/initrd.img-3.13.0-35-generic
    }
menuentry '[COLOR=#a52a2a]Ubuntu 14.04 - Recovery[/COLOR]' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux advanced-/dev/sdb2' {
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root=(hd1,msdos2)
        search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  /dev/sdb2
        linux /vmlinuz root=/dev/sdb2 ro recovery nomodeset
        initrd /initrd.img
    }
}

menuentry "[COLOR=#a52a2a]Windows 7 Ultimate (sda1)[/COLOR]" {
    insmod part_msdos
    insmod ntfs
    insmod search_fs_uuid
    insmod ntldr     
    search --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 A4387A7C387A4D74
    ntldr /bootmgr
}

**submenu** '[COLOR=#a52a2a]ISO & Utilities[/COLOR]' $menuentry_id_option 'gnulinux-advanced-/dev/sdb3' {
menuentry '[COLOR=#a52a2a]LMDE-201403-cinnamon-dvd-64bit[/COLOR]' {
    set isofile='/boot/iso/linuxmint-201403-cinnamon-dvd-64bit.iso'
    loopback loop $isofile
    linux (loop)/live/vmlinuz boot=live config fromiso=/dev/sdb3/$isofile
    initrd (loop)/live/initrd.img
    }
menuentry "[COLOR=#a52a2a]GParted Live[/COLOR]" {
      set isofile="/boot/iso/gparted-live-0.19.1-4-amd64.iso"
      loopback loop $isofile
      linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
      initrd (loop)/live/initrd.img
    }
}

menuentry "[COLOR=#a52a2a]System shutdown[/COLOR]" {
    echo "System shutting down..."
    halt
}

menuentry "[COLOR=#a52a2a]System restart[/COLOR]" {
    echo "System rebooting..."
    reboot
}


```

I prefer to use UUIDS... and its working either ways... Any particular reason why hard coding UUIDS is not recommended?

The only entry that is not working as expected is the "System shutdown".... 
When I try to shutdown the echo message is displayed and thats it, It just sits there. Any ideas?

Edit: added 'Gparted Live' to the 40_custom.

---

### Post by oldfred on 2014-09-22
I think maintenance free would be no hard coded kernels and just using links.

And I think UUIDs would be better, but I have used device. And devices do give me issues. I skipped a port when installing drives. So drive that is sda is always sda, but if I plug in a flash drive it is sde, but when I reboot the flash drive is sdb and every other drive has moved one letter. UUIDs have not changed. 
And which drive's version of grub I boot from is always hd0, so that can change drive order, so I cannot just copy a 40_custom into every install or have to pay attention to which drive grub is installed into. 
Basically why I usually suggest grub be on same drive as its install, just for consistency.

---

### Post by Cavsfan on 2014-09-23
> **fantab said:**
> ```
menuentry '[COLOR=#a52a2a]Ubuntu 14.04[/COLOR] [COLOR=#a52a2a](sdb2)[/COLOR]' {
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root=(hd1,msdos2)
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  /dev/sdb2
    linux /vmlinuz root=/dev/sdb2 ro  quiet splash $vt_handoff
    initrd /initrd.img
}

**submenu** [COLOR=#a52a2a]'Ubuntu 14.04 - options[/COLOR]' $menuentry_id_option 'gnulinux-advanced-/dev/sdb2' {
menuentry '[COLOR=#a52a2a]Ubuntu 14.04 - Previous[/COLOR]' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-35-generic-advanced-/dev/sdb2' {
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root=(hd1,msdos2)
        search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  /dev/sdb2
        linux   /boot/vmlinuz-3.13.0-35-generic root=/dev/sdb2 ro 
        initrd  /boot/initrd.img-3.13.0-35-generic
    }
menuentry '[COLOR=#a52a2a]Ubuntu 14.04 - Recovery[/COLOR]' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux advanced-/dev/sdb2' {
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root=(hd1,msdos2)
        search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos2 --hint-efi=hd1,msdos2 --hint-baremetal=ahci1,msdos2  /dev/sdb2
        linux /vmlinuz root=/dev/sdb2 ro recovery nomodeset
        initrd /initrd.img
    }
}

menuentry "[COLOR=#a52a2a]Windows 7 Ultimate (sda1)[/COLOR]" {
    insmod part_msdos
    insmod ntfs
    insmod search_fs_uuid
    insmod ntldr     
    search --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 A4387A7C387A4D74
    ntldr /bootmgr
}

**submenu** '[COLOR=#a52a2a]ISO & Utilities[/COLOR]' $menuentry_id_option 'gnulinux-advanced-/dev/sdb3' {
menuentry '[COLOR=#a52a2a]LMDE-201403-cinnamon-dvd-64bit[/COLOR]' {
    set isofile='/boot/iso/linuxmint-201403-cinnamon-dvd-64bit.iso'
    loopback loop $isofile
    linux (loop)/live/vmlinuz boot=live config fromiso=/dev/sdb3/$isofile
    initrd (loop)/live/initrd.img
    }
menuentry "[COLOR=#a52a2a]GParted Live[/COLOR]" {
      set isofile="/boot/iso/gparted-live-0.19.1-4-amd64.iso"
      loopback loop $isofile
      linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
      initrd (loop)/live/initrd.img
    }
}

menuentry "[COLOR=#a52a2a]System shutdown[/COLOR]" {
    echo "System shutting down..."
    halt
}

menuentry "[COLOR=#a52a2a]System restart[/COLOR]" {
    echo "System rebooting..."
    reboot
}


```

I prefer to use UUIDS... and its working either ways... Any particular reason why hard coding UUIDS is not recommended?

The only entry that is not working as expected is the "System shutdown".... 
When I try to shutdown the echo message is displayed and thats it, It just sits there. Any ideas?

Edit: added 'Gparted Live' to the 40_custom.

I agree with Oldfred UUIDs do not change so that part is good but, you have a hardcoded kernel version and that will bomb when a new kernel is installed.
Unless of course you edit the file every time a new kernel is added. Which goes against the purpose of this Wiki ===> once you create it, you never have to touch it again... ever... period. 

The only time you should ever have to edit the custom file is if you add or remove a system.

Why not do a shutdown from within 14.04? I've never added a menu line to shutdown myself. It's a boot up menu.

Time will tell. Get back to us when a new kernel is added and let us know if this still works without editing it. ;)

---

### Post by Cavsfan on 2014-09-23
For the last several days I have been trying to come up with a way to add the custom grub menu to Utopic Mate Remix 14.10 but had been hitting roadblocks at every turn.
It would not see the background picture or the font colors; only the bigger font size. Which by itself was kind of cool but still not what I wanted.

I think I may have tamed the beast though and will post the results in the near future. :)

---

### Post by fantab on 2014-09-23
> ...you have a hardcoded kernel version
How else can we set up a previous kernel boot without mentioning/hardcoding the previous working kernel? 
My present 'Ubuntu 14.04 - Previous' entry shows the present kernel as I don't yet have an older kernel- I had removed those earlier.

As for the 'Shutdown' entry... It comes in handy if by mistake I 'restart' when I actually wanted to shutdown... The shutdown entry would help me shutdown from the grub itself, which otherwise I had to do it from the Lightdm-greeter.

---

### Post by Cavsfan on 2014-09-24
> **fantab said:**
> How else can we set up a previous kernel boot without mentioning/hardcoding the previous working kernel? 
My present 'Ubuntu 14.04 - Previous' entry shows the present kernel as I don't yet have an older kernel- I had removed those earlier.

As for the 'Shutdown' entry... It comes in handy if by mistake I 'restart' when I actually wanted to shutdown... The shutdown entry would help me shutdown from the grub itself, which otherwise I had to do it from the Lightdm-greeter.

The necessity to edit grub every time a new kernel is added defeats the whole purpose of this Community Wiki. This Wiki is all about making the changes and never no matter what needing to change a single thing.
Let me give you a little background: Sometime before July 30th, 2010 I had been talking to Ranch Hand on this forum. He was *very* knowledgeable about grub.

I explained to him that I was frustrated with having to edit the default line every time a new kernel got added. I like to have my default set to Windows 7 for my wife just in case the system reboots or something.
Windows 7 happens to be the last line on default grub and I would set that in **/etc/default/grub** but when a new kernel got added, the default line would move one up from Windows 7.
So, with every kernel I had to edit **/etc/default/grub** and that was a pain.
That is when he explained to me how to make this so that once you edit it you never have to touch it again. 
I started with Ubuntu 9.04 Jaunty Jackalope and that was the first version we made a custom menu for. It looked ominous at first but the more I looked at it the simpler it became.

I have never once had to boot into an old kernel, but if I did I would boot into that Ubuntu and install grub there if it were not already installed on that partition.
Then I would enter **sudo chmod +x /etc/grub.d/10_linux && sudo update grub** and then reboot, do what ever required me to boot to the older kernel and then enter the same commands I just mentioned only with a plus sign instead of a minus sign.

I set my GRUB_TIMEOUT=60 in **/etc/default/grub** to give myself lots of time to choose what I'm going to do. I'm kind of slow sometimes or I may walk away and that provides extra time to do what I wanted to do.

But, hard coding anything that needs to be edited for any reason is what I got away from years ago.

You can do what you want. That is what is great about Ubuntu. You don't have to use this method; you could use grub-customizer or a variety of other options.
But, I only know this one method and it has worked great even now with Ubuntu Utopic 14.10 and so I'm sticking with it.

---

### Post by Cavsfan on 2014-09-24
Man I did not realize how behind the times I am. :oops:

Even back on grub 1.99 you could set the font colors outside the box and have different colors for the box and everything inside the box.

All of this time I had been advocating going with a 2 color grub menu with this in /etc/grub.d/05_debian_theme:

```
echo " set color_normal=light-cyan/black" 
echo " set color_highlight=cyan/black
```

When you could have this and go with 3 colors - one outside the box and a normal color for the box and a highlight color inside the box.

```
echo " set color_normal=cyan/black"
echo " set menu_color_normal=yellow/black"
echo " set menu_color_highlight=red/black"
```

I finally figured out how to do this in Ubuntu Utopic Mate remix 14.10 and it's not like the other versions at all. I will update the Wiki soon.

Here is the custom grub menu with the colors above on Mate:

[[IMG]http://en.zimagez.com/miniature/20140924143821.jpg[/IMG]]("http://en.zimagez.com/zimage/20140924143821.php") [[IMG]http://en.zimagez.com/miniature/20140924143846.jpg[/IMG]]("http://en.zimagez.com/zimage/20140924143846.php")

And here is one on Precise with grub 1.99:

[[IMG]http://en.zimagez.com/miniature/20140924125302.jpg[/IMG]]("http://en.zimagez.com/zimage/20140924125302.php") [[IMG]http://en.zimagez.com/miniature/20140924125148.jpg[/IMG]]("http://en.zimagez.com/zimage/20140924125148.php") 


So, you can either go with 2 colors or 3 colors. :)

---

### Post by Cavsfan on 2014-09-30
Utopic Unicorn with grub version 2.02~beta2-14:

[[IMG]http://www.zimagez.com/miniature/20140930113614.jpg[/IMG]]("http://www.zimagez.com/zimage/20140930113614.php")

I'll try to update the wiki as soon as I can. However sometimes real life interferes. ;)

---

### Post by Cavsfan on 2014-10-02
This has to be the coolest grub screen I've made so far or even seen. This is on Trusty.

The timeout is set to 60 seconds and I find myself looking at it for a while when it boots up just because it is so cool. :lol:

[[IMG]http://en.zimagez.com/miniature/20141001122252.jpg[/IMG]]("http://en.zimagez.com/zimage/20141001122252.php")

---

### Post by fantab on 2014-10-16
> **Cavsfan said:**
> Man I did not realize how behind the times I am. :oops:

Even back on grub 1.99 you could set the font colors outside the box and have different colors for the box and everything inside the box.

All of this time I had been advocating going with a 2 color grub menu with this in /etc/grub.d/05_debian_theme:

```
echo " set color_normal=light-cyan/black" 
echo " set color_highlight=cyan/black
```

When you could have this and go with 3 colors - one outside the box and a normal color for the box and a highlight color inside the box.

```
echo " set color_normal=cyan/black"
echo " set menu_color_normal=yellow/black"
echo " set menu_color_highlight=red/black"
```

So, you can either go with 2 colors or 3 colors. :)

Nice discovery Cavsfan! I have tried the three color menu and it works beautifully. Thanks.

*A glitch*: Remember I have created 'submenus'? Well, **the three color menu scheme does not apply correctly to sub-menus on my system**.

I have the following in *01_theme* (I am testing this on Arch Linux):
```
set color_normal=light-red/black
set menu_color_normal=light-gray/black
set menu_color_highlight=light-red/black
```

However, when it enter a 'submenu' theme colors are as following:
```
set color_normal=light-red/black
set color_highlight=dark-gray/light-gray
```

EDIT:
[Screenshot1]("http://i.imgur.com/7v4mFgw.jpg") (showing the three color menu).
[Screenshot2]("http://i.imgur.com/S3JaSPv.jpg") (shows the glitch in submenu).
(My apologies for the bad picture quality but I hope you'll see what I am saying).

If I use the older two-color menu theme, the setting is applied uniformly to both menu and submenus, but NOT when three color scheme is applied.

Can you confirm this and offer a solution or a workaround?

Regards...

---

### Post by Cavsfan on 2014-10-17
> **fantab said:**
> Nice discovery Cavsfan! I have tried the three color menu and it works beautifully. Thanks.

*A glitch*: Remember I have created 'submenus'? Well, **the three color menu scheme does not apply correctly to sub-menus on my system**.

I have the following in *01_theme* (I am testing this on Arch Linux):
```
set color_normal=light-red/black
set menu_color_normal=light-gray/black
set menu_color_highlight=light-red/black
```

However, when it enter a 'submenu' theme colors are as following:
```
set color_normal=light-red/black
set color_highlight=dark-gray/light-gray
```

EDIT:
[Screenshot1]("http://i.imgur.com/7v4mFgw.jpg") (showing the three color menu).
[Screenshot2]("http://i.imgur.com/S3JaSPv.jpg") (shows the glitch in submenu).
(My apologies for the bad picture quality but I hope you'll see what I am saying).

If I use the older two-color menu theme, the setting is applied uniformly to both menu and submenus, but NOT when three color scheme is applied.

Can you confirm this and offer a solution or a workaround?

Regards...

I mentioned that I do not support the submenu concept. I would go with the 2 color theme if that is what works.
Feel free to figure out a solution on your own as submenus are not a part of this custom grub wiki.

Sorry, but adding submenus defeats the purpose of keeping the custom grub menu simple.

Regards

EDIT: You could look at the files in **/etc/grub.d/** and see if one of them sets any additional font colors. 
For example in Linux Mint there is a file **/etc/grub.d/06_mint_theme** that controls these font colors:
> menu_color_normal
menu_color_highlight

If that file is executable and you have the 3 colors setup in **/etc/grub.d/05_debian_theme**, the menu colors in will overwritten by the colors that are defined in **/etc/grub.d/06_mint_theme**.

I'm not familiar with Arch Linux but it may be similar to Linux Mint.

---

### Post by fantab on 2014-10-17
> **Cavsfan said:**
> I mentioned that I do not support the submenu concept. I would go with the 2 color theme if that is what works.
Feel free to figure out a solution on your own as submenus are not a part of this custom grub wiki.

Sorry, but adding submenus defeats the purpose of keeping the custom grub menu simple.

Regards

EDIT: You could look at the files in **/etc/grub.d/** and see if one of them sets any additional font colors. 
For example in Linux Mint there is a file **/etc/grub.d/06_mint_theme** that controls these font colors:


If that file is executable and you have the 3 colors setup in **/etc/grub.d/05_debian_theme**, the menu colors in will overwritten by the colors that are defined in **/etc/grub.d/06_mint_theme**.

I'm not familiar with Arch Linux but it may be similar to Linux Mint. I am not trying spoil your wiki or its purpose. 
(However I must add that having submenu is neither complicated nor does it need maintainence).

Thanks...

---

### Post by Cavsfan on 2014-10-18
> **fantab said:**
> I am not trying spoil your wiki or its purpose. 
(However I must add that having submenu is neither complicated nor does it need maintainence).

Thanks...

You may have misinterpreted my intentions. My wiki is not about having submenus but your not about to spoil it. 
That is what is great about Ubuntu. Everyone can modify or adjust anything they want in Ubuntu. 
You can take my idea or someone else's idea and modify it to suit your needs. It's all free here.

I did however provide some help in the Edit I posted. Did you find any additional grub files that could be setting that caused the third color to be wrong?

You did say > Can you confirm this and offer a solution or a workaround? 

But as I've stated I don't work with submenus and cannot possibly over any solution or workaround for your problem. That was the gist of my point.

You can enter this in terminal to produce the output of grub as it is produced by the command **sudo update-grub**.

```
sudo grub-mkconfig
```
That will produce a listing in terminal. If that listing is too long in order to be able to scroll back to the beginning you can have the output be in text format so you can view it later.
This will put a text file, the name is of your choosing in your home directory of the output of the command:
```
sudo grub-mkconfig > textfile-name
```

That may help point you in the direction of where that color is being set.

---

### Post by Cavsfan on 2014-10-23
I finished updating the Community Wiki with several things I've wanted to add and some I've wanted to remove.

I also added Utopic Unicorn 14.10 and the ability to add custom lines to boot Utopic with Upstart (default) and Systemd.
(If you encounter any problems booting with systemd and need to file a bug report be sure to add tag **systemd-boot** to the bug).

If I've made any errors point them out and I will fix them.

---

### Post by Cavsfan on 2014-10-24
It took me a long time, several days to figure out how to get [SIZE=2]_**Utopic Mate 14.10**_[/SIZE] to work with this custom grub menu.

In **/etc/grub.d/05_debian_theme**:

The first line below is line 165 and you place the 3 font colors after that line - nothing else will work.

```
    if set_background_image "${background}"; then
    echo " set color_normal=cyan/black"
    echo " set menu_color_normal=yellow/black"
    echo " set menu_color_highlight=red/black"
```

Also the font is in a different location for Mate here is the correct command to use _only_ for Mate:

```
sudo grub-mkfont --output=/boot/grub/DejaVuSansMono.pf2 \
 --size=24 /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
```

These are the only differences between regular Ubuntu and Ubuntu Mate to get it to work.

---

### Post by Cavsfan on 2014-10-24
Still haven't figured out how to get Utopic Mate working after installing it from a new ISO. I got the developmental version working fine.
The development system had this file which the final version doesn't have **/etc/grub.d/99_force_text_mode**. I tried copying it over but that didn't make the picture appear.

The font colors appear but they are a bit oversized. Still working on it.....

---

### Post by Cavsfan on 2014-10-25
I finally figured out it was the font that prevented the picture from showing at boot. The font is in a different location than it is on regular Ubuntu or Mint, possibly others.
I added that to the other difference mentioned in post [_#258_]("http://ubuntuforums.org/showthread.php?t=2076205&page=26&p=13150813#post13150813") above.

Here is what it looks like. Not too sure about the colors or the picture just wanted to prove that it could be done.

[[img]http://en.zimagez.com/miniature/20141025101442.jpg[/img]](http://en.zimagez.com/zimage/20141025101442.php)

Here is what the default grub menu looked like on Mint. And again initially I selected Mint Qiana 17 and it displayed the Qiana screen with the 4 green dots but would never go any where.
I brought up a tty screen and it showed I was in Precise 12.04.5. 

[[img]http://en.zimagez.com/miniature/20141023145610.jpg[/img]](http://en.zimagez.com/zimage/20141023145610.php)

---

### Post by Cavsfan on 2014-11-03
I just added the things for Utopic Mate Remix 14.10 from post #258 to the wiki for the font creation command  and the location where the font colors are specified.
I had a hard time finding a picture that would work. I think the first 3 I tried did not work but the 4th one did. So, if the picture does not show at boot, try another one.

---

### Post by Cavsfan on 2014-11-21
Turns out when I specified things for only Utopic Mate, they were actually meant for Utopic period and I believe all versions afterwards.

The font is now in a different location and the font colors too. I'll try to correct that as soon as I can.

I just customized Vivid Gnome and it was the same as Utopic.

---

### Post by Cavsfan on 2014-11-21
I went ahead and made the changes. Let me know if you find any errors. :)

---

### Post by Cavsfan on 2014-11-21
A screenie of Vivid Vervet 15.04 grub with the following colors:
```
        echo " set color_normal=red/black"
        echo " set menu_color_normal=black/black"
        echo " set menu_color_highlight=yellow/black"
```

[[IMG]http://en.zimagez.com/miniature/20141121165159.jpg[/IMG]]("http://en.zimagez.com/zimage/20141121165159.php")

---

### Post by Cavsfan on 2014-12-22
A screenshot of my latest menu:

[[IMG]http://en.zimagez.com/miniature/20141222105041.jpg[/IMG]]("http://en.zimagez.com/zimage/20141222105041.php")

It doesn't do justice looking at that picture compared to what the screen actually looks like. I'd have to use flash to get a better picture but that makes a big bright spot on the picture.

I got rid of a few systems: Mint 13 and Utopic Unicorn, leaving LTS versions, the developmental version Vivid Vervet 15.04 and of course windows.
I remember having one Ubuntu and Windows 7 on here. Having more than one is so much better as you can copy stuff back and forth across partitions.

I tried to put this blue circle picture on Precise but it would not work. I tried copying the one from that screen on Trusty and also downloaded a new one but neither would work.

All I got was the font sizes and black and white font colors. But when I did get one to work the background, the font colors and everything came together.

So a lot depends on that picture. Just because the output of **sudo update-grub** lists the picture name does not mean it will show at boot time.
Sometimes you just have to find another picture. Been there many times.

---

### Post by Cavsfan on 2014-12-23
Re-installed Vivid Vervet 15.04 on the 18th and got an update to grub today so I thought I'd customize it. The first picture I tried worked amazingly.

I used these colors:
```
        echo " set color_normal=cyan/black"
        echo " set menu_color_normal=black/black"
        echo " set menu_color_highlight=red/black"
```

So, with black as the normal menu color it is hard to see in the picture but not really hard to see on the screen.

[[IMG]http://en.zimagez.com/miniature/20141223110606.jpg[/IMG]]("http://en.zimagez.com/zimage/20141223110606.php")

---

### Post by Cavsfan on 2014-12-26
A much better looking menu on Vivid, which is also my wallpaper:

[[IMG]http://www.zimagez.com/miniature/20141226135835.jpg[/IMG]]("http://www.zimagez.com/zimage/20141226135835.php")

Colors:

```
        echo " set color_normal=light-green/black"
        echo " set menu_color_normal=yellow/black"
        echo " set menu_color_highlight=white/black"
```

---

### Post by Cavsfan on 2015-01-16
Ubuntu Vivid Vervet 15.04 is going to have **upstart** as the default startup daemon and **systemd** will be available as an option.

[_upstart description._]("http://en.wikipedia.org/wiki/Upstart")

[_systemd description._]("http://freedesktop.org/wiki/Software/systemd/")

[_Explanation of the difference between using upstart and systemd._]("https://wiki.ubuntu.com/SystemdForUpstartUsers#High-level_startup_concept")

[_There is a way to make systemd default and upstart as the option permanently._]("https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch")

If you choose to make systemd default you have to remember to enter **sudo update-grub** after installing the **systemd-sysv** package.
Or else the change will not take effect until either the next kernel installation, which performs **sudo update-grub** or when you enter it in terminal.

If you leave upstart as default and want an option on your grub menu to boot with systemd this would be the menuentries in **/etc/grub.d/06_custom**:

```
menuentry "Vivid Vervet 15.04" {
    set root=(hd[COLOR=#FF0000]0,9[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a9[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 systemd" {
    set root=(hd[COLOR=#ff0000]0,9[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a9[/COLOR] ro quiet splash init=/lib/systemd/systemd
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 (Recovery Mode)" {
    set root=(hd[COLOR=#ff0000]0,9[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a9[/COLOR] ro recovery nomodeset
        initrd /initrd.img
}
```

If you make the permanent switch to make systemd default and want an option to boot into upstart this would be the menuentries in **/etc/grub.d/06_custom**:

```
menuentry "Vivid Vervet 15.04" {
    set root=(hd[COLOR=#ff0000]0,9[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a9[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 upstart" {
    set root=(hd[COLOR=#ff0000]0,9[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a9[/COLOR] ro quiet splash init=/sbin/upstart
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 (Recovery Mode)" {
    set root=(hd[COLOR=#ff0000]0,9[/COLOR])
        linux /vmlinuz root=/dev/sd[COLOR=#ff0000]a9[/COLOR] ro recovery nomodeset
        initrd /initrd.img
}
```

Of course change the red part to match your hard disk and partition that Vivid Vervet 15.05 is installed on and enter **sudo update-grub** to make these changes "stick".

---

### Post by watchpocket on 2015-01-31
I used grub-customizer (version 4.0.6) recently to try to change the order of the grub2 menu.  Now when I run ***sudo update-grub*** at the command-line, I get syntax errors.  Before I try to do anything more to set up my grub2, I'd like to fix this, but I'm not sure where to start.  

I have three 1-terabyte drives.  I'm running Ubuntu MATE 14.04.1 on /dev/sda1/ and Ubuntu 12.04.5 Precise on /dev/sdb1.  

/dev/sdc is newly installed (with no OS on it) and will be for data files. On 14.04 I have GNU GRUB version 2.02~beta2-9ubuntu1.

Here is the output of ***sudo update-grub***, when run from within 14.04: 

```
Generating grub configuration file ...
Found theme: /boot/grub/themes/ubuntu-mate/theme.txt
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sdb1
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sdb1
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
error: syntax error.
error: Incorrect command.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 637
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
```

The only file I have -- among all of /etc/default/grub, /etc/grub.d/* and /boot/grub/* -- that has 637 lines in it is the uneditable [COLOR=#0000ff]**/boot/grub/grub.cfg.new .**[/COLOR]
(It's 687 lines long and I can post it if needed.)  There** is** a **[COLOR=#0000ff]/boot/grub/grub.cfg[/COLOR]** file, but it's only 514 lines.

Here's my /etc/default/grub file:
```
  1 # If you change this file, run 'update-grub' afterwards to update
  2 # /boot/grub/grub.cfg.
  3 # For full documentation of the options in this file, see:
  4 #   info -f grub -n 'Simple configuration'
  5 
  6 GRUB_DEFAULT="Ubuntu 14.04"
  7 #GRUB_HIDDEN_TIMEOUT="0"
  8 GRUB_HIDDEN_TIMEOUT_QUIET="true"
  9 GRUB_TIMEOUT="10"
 10 GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
 11 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 12 GRUB_CMDLINE_LINUX="persistent"
 13 
 14 # Uncomment to enable BadRAM filtering, modify to suit your needs
 15 # This works with Linux (no patch required) and with any kernel that obtains
 16 # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
 17 #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
 18 
 19 # Uncomment to disable graphical terminal (grub-pc only)
 20 #GRUB_TERMINAL="console"
 21 
 22 # The resolution used on graphical terminal
 23 # note that you can use only modes which your graphic card supports via VBE
 24 # you can see them in real GRUB with the command `vbeinfo'
 25 #GRUB_GFXMODE="640x480"
 26 
 27 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
 28 #GRUB_DISABLE_LINUX_UUID="true"
 29 
 30 # Uncomment to disable generation of recovery mode menu entries
 31 #GRUB_DISABLE_RECOVERY="true"
 32 
 33 # Uncomment to get a beep at grub start
 34 #GRUB_INIT_TUNE="480 440 1"
 35 
 36 GRUB_SAVEDEFAULT="false"
 37 GRUB_THEME="/boot/grub/themes/ubuntu-mate/theme.txt"
 38 export GRUB_COLOR_NORMAL="light-gray/black"
 39 export GRUB_COLOR_HIGHLIGHT="magenta/black"
 40 
 41 GRUB_FONT="/boot/grub/unicode.pf2"
```

I'll continue to read up on GRUB2, but thanks for ideas how to fix this in the meantime.

---

### Post by deadflowr on 2015-02-01
You could post the error line that the grub.cfg.new has, which should give us an idea of what's wrong.
The line is the 637 line, so either copy that line from a text editor, (gedit has a quick option --ctrl + I to go to a line)
or post the output from 
```
sed -n '637p' /boot/grub/grub.cfg.new
``` 
for us to look at.

---

### Post by watchpocket on 2015-02-01
Sure.  Here are lines 618 through 645 of my **[COLOR=#0000ff]/boot/grub/grub.cfg.new[/COLOR]** file.  Line number 637 I've bolded and made red here.  Thanks.

```
618 }
619 menuentry "Ubuntu, with Linux 3.13.0-39-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recove    ____ry-1742aa67-b8ce-45d2-94ca-05e3579f7e2f' {
620 *.......*.......recordfail
621 *.......*.......load_video
622 *.......*.......insmod gzio
623 *.......*.......insmod part_msdos
624 *.......*.......insmod ext2
625 *.......*.......set root='hd0,msdos1'
626 *.......*.......if [ x$feature_platform_search_hint = xy ]; then
627 *.......*.......  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1742aa67-b8ce-45d2-94ca-05e3579f7e2f
628 *.......*.......else
629 *.......*.......  search --no-floppy --fs-uuid --set=root 1742aa67-b8ce-45d2-94ca-05e3579f7e2f
630 *.......*.......fi
631 *.......*.......echo*...'Loading Linux 3.13.0-39-generic ...'
632 *.......*.......linux*../boot/vmlinuz-3.13.0-39-generic root=UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f ro recovery nomodeset persistent
633 *.......*.......echo*...'Loading initial ramdisk ...'
634 *.......*.......initrd*./boot/initrd.img-3.13.0-39-generic
635 }
636 }
**637 [COLOR=#ff0000]function gfxmode {[/COLOR]**
638 *.......set gfxpayload="${1}"
639 *.......if [ "${1}" = "keep" ]; then
640 *.......*.......set vt_handoff=vt.handoff=7
641 *.......else
642 *.......*.......set vt_handoff=
643 *.......fi
644 }
645 if [ "${recordfail}" != 1 ]; then

```

---

### Post by oygle on 2015-02-01
I have added a windows XP HDD, and want to use it with Kubuntu, so needed to modify grub.

Have followed the instructions from post #1 in this thread and gone through and made changes as indicated at [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

The following is before the changes ...

> 
$ **grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0 **
     0  menuentry 'Ubuntu
     1  submenu 'Advanced options for Ubuntu
     2  menuentry 'Ubuntu, with Linux 3.13.0-45-generic
     3  menuentry 'Ubuntu, with Linux 3.13.0-45-generic (recovery mode)
     4  menuentry 'Ubuntu, with Linux 3.13.0-44-generic
     5  menuentry 'Ubuntu, with Linux 3.13.0-44-generic (recovery mode)
     6  menuentry 'Ubuntu, with Linux 3.13.0-43-generic
     7  menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)
     8  menuentry 'Memory test (memtest86+)
     9  menuentry 'Memory test (memtest86+, serial console 115200)
$ 
$ **sudo blkid**
[sudo] password for **********: 
/dev/sda1: UUID="b36b92dd-0621-4eeb-95f0-08cce5ef0a31" TYPE="ext4" 
/dev/sda2: UUID="82e48eb2-0c33-4696-9154-d921da42bbd2" TYPE="swap" 
/dev/sda3: UUID="eb961b0b-f288-40c1-80bc-708e08614b4b" TYPE="ext4" 
/dev/sdb1: UUID="8EFC2D0BFC2CEF61" TYPE="ntfs" 


and the following after the changes to /etc/grub.d/06_custom

> 
$ **sudo chmod +x /etc/grub.d/06_custom**
[sudo] password for **********: 
$ **sudo update-grub2**
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
done

but now there is no recovery mode options ??  Also, if I select the win XP option from grub, it tries to boot, but just keeps booting. (I think that is a windows display driver problem, as the Win xp HDD came from another computer). Here is /etc/grub.d/06_custom

```

#!/bin/sh
exec tail -n +4 $0
echo 1>&2 "Adding Trusty Tahr 14.04 and Windows XP Pro"
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Trusty Tahr 14.04" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows XP Pro" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8EFC2D0BFC2CEF61
    chainloader +1
}
```

The (new) grub menu has the additional option I wanted, but I don't have the option to boot with another kernel. Also, there is a 'Ubuntu' option there ??

---

### Post by Cavsfan on 2015-02-01
> **watchpocket said:**
> I used grub-customizer (version 4.0.6) recently to try to change the order of the grub2 menu.  Now when I run ***sudo update-grub*** at the command-line, I get syntax errors.  Before I try to do anything more to set up my grub2, I'd like to fix this, but I'm not sure where to start.  

I have three 1-terabyte drives.  I'm running Ubuntu MATE 14.04.1 on /dev/sda1/ and Ubuntu 12.04.5 Precise on /dev/sdb1.  

/dev/sdc is newly installed (with no OS on it) and will be for data files. On 14.04 I have GNU GRUB version 2.02~beta2-9ubuntu1.

Here is the output of ***sudo update-grub***, when run from within 14.04: 

```
Generating grub configuration file ...
Found theme: /boot/grub/themes/ubuntu-mate/theme.txt
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sdb1
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sdb1
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
error: syntax error.
error: Incorrect command.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 637
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
```

The only file I have -- among all of /etc/default/grub, /etc/grub.d/* and /boot/grub/* -- that has 637 lines in it is the uneditable [COLOR=#0000ff]**/boot/grub/grub.cfg.new .**[/COLOR]
(It's 687 lines long and I can post it if needed.)  There** is** a **[COLOR=#0000ff]/boot/grub/grub.cfg[/COLOR]** file, but it's only 514 lines.

Here's my /etc/default/grub file:
```
  1 # If you change this file, run 'update-grub' afterwards to update
  2 # /boot/grub/grub.cfg.
  3 # For full documentation of the options in this file, see:
  4 #   info -f grub -n 'Simple configuration'
  5 
  6 GRUB_DEFAULT="Ubuntu 14.04"
  7 #GRUB_HIDDEN_TIMEOUT="0"
  8 GRUB_HIDDEN_TIMEOUT_QUIET="true"
  9 GRUB_TIMEOUT="10"
 10 GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
 11 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 12 GRUB_CMDLINE_LINUX="persistent"
 13 
 14 # Uncomment to enable BadRAM filtering, modify to suit your needs
 15 # This works with Linux (no patch required) and with any kernel that obtains
 16 # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
 17 #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
 18 
 19 # Uncomment to disable graphical terminal (grub-pc only)
 20 #GRUB_TERMINAL="console"
 21 
 22 # The resolution used on graphical terminal
 23 # note that you can use only modes which your graphic card supports via VBE
 24 # you can see them in real GRUB with the command `vbeinfo'
 25 #GRUB_GFXMODE="640x480"
 26 
 27 # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
 28 #GRUB_DISABLE_LINUX_UUID="true"
 29 
 30 # Uncomment to disable generation of recovery mode menu entries
 31 #GRUB_DISABLE_RECOVERY="true"
 32 
 33 # Uncomment to get a beep at grub start
 34 #GRUB_INIT_TUNE="480 440 1"
 35 
 36 GRUB_SAVEDEFAULT="false"
 37 GRUB_THEME="/boot/grub/themes/ubuntu-mate/theme.txt"
 38 export GRUB_COLOR_NORMAL="light-gray/black"
 39 export GRUB_COLOR_HIGHLIGHT="magenta/black"
 40 
 41 GRUB_FONT="/boot/grub/unicode.pf2"
```

I'll continue to read up on GRUB2, but thanks for ideas how to fix this in the meantime.

> **watchpocket said:**
> Sure.  Here are lines 618 through 645 of my **[COLOR=#0000ff]/boot/grub/grub.cfg.new[/COLOR]** file.  Line number 637 I've bolded and made red here.  Thanks.

```
618 }
619 menuentry "Ubuntu, with Linux 3.13.0-39-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recove    ____ry-1742aa67-b8ce-45d2-94ca-05e3579f7e2f' {
620 *.......*.......recordfail
621 *.......*.......load_video
622 *.......*.......insmod gzio
623 *.......*.......insmod part_msdos
624 *.......*.......insmod ext2
625 *.......*.......set root='hd0,msdos1'
626 *.......*.......if [ x$feature_platform_search_hint = xy ]; then
627 *.......*.......  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  1742aa67-b8ce-45d2-94ca-05e3579f7e2f
628 *.......*.......else
629 *.......*.......  search --no-floppy --fs-uuid --set=root 1742aa67-b8ce-45d2-94ca-05e3579f7e2f
630 *.......*.......fi
631 *.......*.......echo*...'Loading Linux 3.13.0-39-generic ...'
632 *.......*.......linux*../boot/vmlinuz-3.13.0-39-generic root=UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f ro recovery nomodeset persistent
633 *.......*.......echo*...'Loading initial ramdisk ...'
634 *.......*.......initrd*./boot/initrd.img-3.13.0-39-generic
635 }
636 }
**637 [COLOR=#ff0000]function gfxmode {[/COLOR]**
638 *.......set gfxpayload="${1}"
639 *.......if [ "${1}" = "keep" ]; then
640 *.......*.......set vt_handoff=vt.handoff=7
641 *.......else
642 *.......*.......set vt_handoff=
643 *.......fi
644 }
645 if [ "${recordfail}" != 1 ]; then

```

OK, here is what I would do: boot into 14.04 and make sure that grub there is controlling your system by entering **sudo grub-install /dev/sda** 
Then use gparted to make sure that the boot flag is not also set on sdb where you have 12.04 installed. If the boot flag is checked on sdb uncheck it and click apply and close gparted.
Then edit your /etc/default/grub file **gksudo gedit /etc/default/grub** and change GRUB_DEFAULT= to a number. The menu entries start at 0 so If you wanted the first entry to be default enter 0 without quotes.
For now just change it to 2 without quotes there. Which will be Mate 14.04 as default. You can always change it later.

Delete persistent on the GRUB_CMDLINE_LINUX= line so it just has double quotes like this GRUB_CMDLINE_LINUX="".

If you have a picture in /boot/grub/ enter this GRUB_GFXMODE=1920x1200-24 in place of #GRUB_GFXMODE="640x480".
(with the same size resolution as your monitor. Mine is 1920x1200 and the 24 means 24 bit depth color.)
HD pictures are usually 24 bit but not always and sometimes you have to try more than one picture. 
If the picture is listed in the output when you enter sudo update-grub but does not appear at boot time try another picture.

Then comment out lines 36 through 39 and remove the quotes from line 42 on your font line.
Then save that file.

Then create or edit a 06_custom file and you can create one if it doesn't exist by entering **gksudo gedit /etc/grub.d/06_custom **
Then copy the contents of this into that text file:
[PHP]#!/bin/sh
echo 1>&2 "Adding Precise Pangolin 12.04 and Trusty Tahr Mate 14.04"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Precise Pangolin 12.04" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro single
        initrd /initrd.img
}
menuentry "Trusty Tahr Mate 14.04" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 Mate (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}
[/PHP]

Then save it and enter **sudo chmod +x /etc/grub.d/06_custom ** to make it executable.

Then enter **gksudo gedit /etc/grub.d/05_debian_theme +117** to enter the font colors. (The +117 will put you at line 117. you need to put the font colors on line 118 for Trusty.
You can have 3 colors: 
[LIST=1]
[*]A color (color_normal)  for the words at top and bottom of the screen. 
[*]A normal menu color (menu_color_normal) for the box surrounding the menu and the menu entries themselves. 
[*]Then a color for the selected line (menu_color_highlight) where the cursor is 
[/LIST]
Like this:
```
117    echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
118    echo " set color_normal=magenta/black"
119    echo " set menu_color_normal=yellow/black"
120    echo " set menu_color_highlight=red/black"
```

Then most important before you reboot enter **sudo update-grub** or **sudo update-grub2** either one works.
If you forget that then none of the changes will appear when you reboot.

That should work and give you the ability to boot into either system.
If you have problems it should not be anything drastic.
 I will be gone some of the day tomorrow but will be here in the afternoon.

This will at least show the menu entries created above on top of any other menu entries you have.

You do know that the link to the wiki is on the 1st post in this thread in green right?

---

### Post by Cavsfan on 2015-02-01
> **oygle said:**
> I have added a windows XP HDD, and want to use it with Kubuntu, so needed to modify grub.

Have followed the instructions from post #1 in this thread and gone through and made changes as indicated at [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

The following is before the changes ...
> $ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
0 menuentry 'Ubuntu
1 submenu 'Advanced options for Ubuntu
2 menuentry 'Ubuntu, with Linux 3.13.0-45-generic
3 menuentry 'Ubuntu, with Linux 3.13.0-45-generic (recovery mode)
4 menuentry 'Ubuntu, with Linux 3.13.0-44-generic
5 menuentry 'Ubuntu, with Linux 3.13.0-44-generic (recovery mode)
6 menuentry 'Ubuntu, with Linux 3.13.0-43-generic
7 menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)
8 menuentry 'Memory test (memtest86+)
9 menuentry 'Memory test (memtest86+, serial console 115200)
$
$ sudo blkid
[sudo] password for **********:
/dev/sda1: UUID="b36b92dd-0621-4eeb-95f0-08cce5ef0a31" TYPE="ext4"
/dev/sda2: UUID="82e48eb2-0c33-4696-9154-d921da42bbd2" TYPE="swap"
/dev/sda3: UUID="eb961b0b-f288-40c1-80bc-708e08614b4b" TYPE="ext4"
/dev/sdb1: UUID="8EFC2D0BFC2CEF61" TYPE="ntfs" 


and the following after the changes to /etc/grub.d/06_custom
[QUOTE]$ sudo chmod +x /etc/grub.d/06_custom
[sudo] password for **********:
$ sudo update-grub2
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
done 


but now there is no recovery mode options ??  Also, if I select the win XP option from grub, it tries to boot, but just keeps booting. (I think that is a windows display driver problem, as the Win xp HDD came from another computer). Here is /etc/grub.d/06_custom

```

#!/bin/sh
exec tail -n +4 $0
echo 1>&2 "Adding Trusty Tahr 14.04 and Windows XP Pro"
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Trusty Tahr 14.04" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows XP Pro" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8EFC2D0BFC2CEF61
    chainloader +1
}
```

The (new) grub menu has the additional option I wanted, but I don't have the option to boot with another kernel. Also, there is a 'Ubuntu' option there ??[/QUOTE]

Look at what I have posted above in reply to watchpocket. That should get you pretty close and if not see what you can fix and let me know what happens.
I will be gone until tomorrow afternoon. But, I should be able to help you then.

Here is the contents of my /etc/default/grub file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

[COLOR=#ff0000]GRUB_DEFAULT=9
#GRUB_HIDDEN_TIMEOUT=0[/COLOR]
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=60
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_FONT=/boot/grub/DejaVuSansMono.pf2 

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1200-24

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

cheers

---

### Post by oygle on 2015-02-01
Thanks [Cavsfan]("http://ubuntuforums.org/member.php?u=889820"). I checked with kde partition manager and de/sda1 (Kubuntu 14.04) **AND** dev/sdb1 (Win xp pro) have the boot flag set. I'm very hesitant to check the flag off for dev/sdb1 because I'm having problems booting into XP at present. Apparently one cannot simply take an XP hard drive and place it into another computer and have it work. I checked your grub file to mine with Beyond Compare, and apart from code to do with display/fonts, there are these 4 lines

```
GRUB_DEFAULT=9
#GRUB_HIDDEN_TIMEOUT=0
GRUB_TIMEOUT=60
```

the default grub file I have is

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_TIMEOUT=10
```

The grub screen that now appears is as follows ..

The 3 options I have in /etc/grub.d/06_custom
Ubuntu
Advanced options for Ubuntu
memory test ....
memory test ....
Microsoft Windows XP Professional (on dev/sdb1)

After modifying, here is the /etc/default/grub

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=2
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=60
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1
```

---

### Post by watchpocket on 2015-02-01
A thousand thanks for the detailed response, Cavsfan. 

I made all of your suggestions exactly as you outlined them, double-checked everything (and will now triple-check) **but** I get the same syntax error messages when I **sudo update-grub**.  Except that what was line 637 in the error message -- that same  [COLOR=#ff0000]**function gfxmode {**[/COLOR]  line --  is now line 667.  

And there appears to be no change to my grub menu. I read the wiki, am reading it again, also reading the manual at [https://www.gnu.org/software/grub/manual/grub.html](https://www.gnu.org/software/grub/manual/grub.html).  

For what it's worth: ```
rj@rjbox:~$ grub-install -v
grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
rj@rjbox:~$ 
```
"i386-pc platform" -- I'm assuming that's right for my 64-bit desktop machine, since that was what you said to enter.

Also:
```
rj@rjbox:~$ sudo debconf-show grub-pc
[sudo] password for rj: 
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/kopt_extracted: false
  grub-pc/disk_description:
  grub-pc/hidden_timeout: true
  grub2/device_map_regenerated:
  grub-pc/chainload_from_menu.lst: true
  grub2/linux_cmdline_default: quiet splash
  grub2/kfreebsd_cmdline:
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices_disks_changed:
  grub-pc/install_devices_empty: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/timeout: 10
* grub-pc/install_devices: /dev/disk/by-id/ata-ST31000528AS_9VP1JVMB-part1
  grub-pc/partition_description:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/linux_cmdline:
  grub-pc/install_devices_failed: false
rj@rjbox:~$ 
```

Thanks again for the detailed attention.

---

### Post by oygle on 2015-02-01
> **watchpocket said:**
> [Moderator, please delete this post. Connection problems caused posting in triplicate, my apologies.]

I _think_ you can just do a "Report post' ; bottom left hand corner.

---

### Post by oygle on 2015-02-02
The grub menu is working okay (attached), but I need to get rid of lines 3,4 and 7, and have the options of booting to previous kernel/s.

**/etc/grub.d/06_custom**

```
#!/bin/sh
exec tail -n +4 $0
echo 1>&2 "Adding Trusty Tahr 14.04 and Windows XP Pro"
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Trusty Tahr 14.04" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "Trusty Tahr 14.04 (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows XP Pro" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8EFC2D0BFC2CEF61
    chainloader +1
}
```

---

### Post by oldfred on 2015-02-03
This shows grub will reinstall automatically to partition one on the drive. That should not have the part 1 at end, so it installs to the MBR.
> 
grub-pc/install_devices: /dev/disk/by-id/ata-ST31000528AS_9VP1JVMB-part1


#to get grub2 to remember where to reinstall on updates:
 sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

If you installed grub-customizer, be sure to uninstall it. And it creates its own scripts. Often best way to uninstall is a total purge of grub, copy/backup scripts folder and reinstall grub-pc package. If you have manually edited any scripts be sure to save/backup those first.

To see if you have grub customizer scripts.
ls -lha /etc/grub.d

Best not to mix grub customizer and manual edits of grub scripts. If customizer works that is fine, but if not purge customizer and manually edit grub. I prefer the manual edit as then you know what changes are taking place.

---

### Post by Cavsfan on 2015-02-03
> **watchpocket said:**
> A thousand thanks for the detailed response, Cavsfan. 

I made all of your suggestions exactly as you outlined them, double-checked everything (and will now triple-check) **but** I get the same syntax error messages when I **sudo update-grub**.  Except that what was line 637 in the error message -- that same  [COLOR=#ff0000]**function gfxmode {**[/COLOR]  line --  is now line 667.  

And there appears to be no change to my grub menu. I read the wiki, am reading it again, also reading the manual at [https://www.gnu.org/software/grub/manual/grub.html](https://www.gnu.org/software/grub/manual/grub.html).  

For what it's worth: ```
rj@rjbox:~$ grub-install -v
grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
rj@rjbox:~$ 
```
"i386-pc platform" -- I'm assuming that's right for my 64-bit desktop machine, since that was what you said to enter.

Also:
```
rj@rjbox:~$ sudo debconf-show grub-pc
[sudo] password for rj: 
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/kopt_extracted: false
  grub-pc/disk_description:
  grub-pc/hidden_timeout: true
  grub2/device_map_regenerated:
  grub-pc/chainload_from_menu.lst: true
  grub2/linux_cmdline_default: quiet splash
  grub2/kfreebsd_cmdline:
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices_disks_changed:
  grub-pc/install_devices_empty: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/timeout: 10
* grub-pc/install_devices: /dev/disk/by-id/ata-ST31000528AS_9VP1JVMB-part1
  grub-pc/partition_description:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/linux_cmdline:
  grub-pc/install_devices_failed: false
rj@rjbox:~$ 
```

Thanks again for the detailed attention.

You're welcome! Sorry I didn't reply sooner but I've had some issues with real life come up. My monitor is also going bad but got one on the way tomorrow.

What Oldfred posted is right. You should purge grub-customizer if you are going to manually edit the grub files, which is recommended as you know what you have.
Mixing the 2 is what is causing you problems I believe.

I said to enter **sudo grub-install /dev/sda** on the system that you want to have controlling grub. We can point you to how to eliminate the other grub from interfering once all is fine.
It will say "Installing for i386-pc platform." even on a 64 bit system. That is normal

With a small v this is what I get too. capital V returns the version (below). This is on Trusty too.
```
cavsfan@cavsfan-desktop:~$ grub-install -v
grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
```

```
cavsfan@cavsfan-desktop:~$ grub-install -V
grub-install (GRUB) 2.02~beta2-9ubuntu1
```

But, your main problem is mixing grub-customizer with manual editing the grub files. 
As a matter of fact the problem you have is coming from grub-customizer.

---

### Post by Cavsfan on 2015-02-03
> **oygle said:**
> The grub menu is working okay (attached), but I need to get rid of lines 3,4 and 7, and have the options of booting to previous kernel/s.

**/etc/grub.d/06_custom**

```
#!/bin/sh
exec tail -n +4 $0
echo 1>&2 "Adding Trusty Tahr 14.04 and Windows XP Pro"
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "[COLOR=#ff0000]Trusty Tahr 14.04[/COLOR]" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "[COLOR=#ff0000]Trusty Tahr 14.04 (Recovery Mode)[/COLOR]" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "[COLOR=#ff0000]Windows XP Pro[/COLOR]" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8EFC2D0BFC2CEF61
    chainloader +1
}
```


If you too are also using grub-customizer you need to purge that before it messes anything up. Manual grub entries are easier and never need modifying unless you change partitions.
Actually the first three lines are good and coming from **/etc/grub.d/06_custom** see the red lines match the first three lines in your picture.
The other ones are what you want to get rid of.

If you are confident that the top line boots to Trusty and the 3rd line boots to Windows XP, then you need to make the other files that put those extra menu entries un-executable Like this:

**sudo chmod -x /etc/grub.d/20_memtest86+** will make memtest unexecutable and will not show in the menu. 
 **sudo chmod -x /etc/grub.d/10_linux** will make the list of kernels not display. 
 **sudo chmod -x /etc/grub.d/30_os-prober** will make any Windows or Debian, etc. entries not display. 
 Then _always_ enter **sudo update-grub** when finished making changes. 
Then reboot and you should be good to go. 

But if you can boot into XP with the 3rd line you should remove the boot flag from sdb. Only 1 drive should have the boot flag set and it will not prevent XP from booting.
Do this and get back to me.

---

### Post by watchpocket on 2015-02-03
> **oldfred said:**
> 
 sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64


I'll need grub-pc for amd64, I think (instead of grub-efi-amd64), since my machine is 64-bit, but BIOS, not UEFI.

> If you installed grub-customizer, be sure to uninstall it.

I did install it in my Ubuntu MATE 14.04.  I'm definitely going to uninstall grub-customizer at the first chance I have to get back to this project (I'll be traveling for a week starting tomorrow & I'm writing this now from my workplace Windows box).  I had no idea that grub-customizer messes things up so easily.

> And it creates its own scripts. Often best way to uninstall is a total purge of grub, copy/backup scripts folder and reinstall grub-pc package. If you have manually edited any scripts be sure to save/backup those first.

I most likely -will- do a total purge of grub (after backing up everything in /etc/grub.d), because none of what I've done with grub (per Cavsfan's suggestions) has effected any change at all, and also partly because it looks like I may currently be running grub for i386 instead of for amd64.  

But, a question: if I purge grub, I'm guessing I'll need to reinstall it *immediately* after purging, and without rebooting or shutting down, or else I won't be able to boot (although the 1.98 or 1.99  legacy grub that I have on /dev/sdb that's part of my Ubuntu 12.04.5 install might take over the booting process.  (Wait, no, that probably won't happen because I unchecked the boot flag for /dev/sdb with gparted, per Cavsfan's advice.)

> To see if you have grub customizer scripts.
ls -lha /etc/grub.d

I definitely have scripts in /etc/grub.d -- but how do I tell which scripts were created with grub-customizer and which weren't?

> Best not to mix grub customizer and manual edits of grub scripts. If customizer works that is fine, but if not purge customizer and manually edit grub. I prefer the manual edit as then you know what changes are taking place.

I also prefer editing the scripts manually, for complete control (& no mysterious additions of new entries not put there by me), as long as I'm reasonably sure I know what I'm doing.  Thank you for the clarifications.

---

### Post by oygle on 2015-02-03
Have done as per your instructions ..

```
$ sudo chmod -x /etc/grub.d/20_memtest86+
$ sudo chmod -x /etc/grub.d/10_linux
$ sudo chmod -x /etc/grub.d/30_os-prober
$ sudo update-grub
Generating grub configuration file ...
done
$ 
```

Hmm, that 3rd option doesn't boot to windows. I now remember that the last option worked...

```
$ sudo chmod +x /etc/grub.d/30_os-prober
$ sudo update-grub
Generating grub configuration file ...
Found Microsoft Windows XP Professional on /dev/sdb1
done
$ 

```

Now I assume I don't actually need that third line in **/etc/grub.d/06_custom**

---

### Post by watchpocket on 2015-02-03
> **Cavsfan said:**
> You're welcome! Sorry I didn't reply sooner but I've had some issues with real life come up. My monitor is also going bad but got one on the way tomorrow.

Sounds exactly like my situation.  I have to be away for a week and one of my two Hanns-G monitors has been seriously flaking.  (What monitor did you get, if I may ask?  I was going to order an identical Hanns-G replacement, but I think those guys may be out of business -- or nearly so -- from a multi-million $$$ fine they got for price-fixing.)

> What Oldfred posted is right. You should purge grub-customizer if you are going to manually edit the grub files, which is recommended as you know what you have.
Mixing the 2 is what is causing you problems I believe.

Right.  grub-customizer messed things up from the start, when I just did the one thing of trying to change the menu order.

> I said to enter **sudo grub-install /dev/sda** on the system that you want to have controlling grub. We can point you to how to eliminate the other grub from interfering once all is fine.
It will say "Installing for i386-pc platform." even on a 64 bit system. That is normal

I think I did do that, but will do it again after purging grub-customizer. 

One thing about i386 is that it appears here <[http://packages.ubuntu.com/lucid/grub-pc](http://packages.ubuntu.com/lucid/grub-pc)> that there is (or was) a grub-pc available for amd64 as well as i386.  Granted that this page is for an old version of grub-pc -- grub-pc 1.98-1ubuntu5.  If there is a current version of grub-pc for amd64 (as opposed to one for i386), should I use the amd64 version, or does it not matter?  Or maybe the new grub makes no such distinction.

> With a small v this is what I get too. capital V returns the version (below). This is on Trusty too.
```
cavsfan@cavsfan-desktop:~$ grub-install -v
grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
```

```
cavsfan@cavsfan-desktop:~$ grub-install -V
grub-install (GRUB) 2.02~beta2-9ubuntu1
```


Hmm.  I totally  wrongly invoked the small-v in that command.

> But, your main problem is mixing grub-customizer with manual editing the grub files. 
As a matter of fact the problem you have is coming from grub-customizer.

Thank you so much for your help.  grub is a somewhat complex animal and it's so great to receive the clear thinking from both of you gentlemen. I'll report back with results asap (probably in a week or so, sooner if possible).

---

### Post by Cavsfan on 2015-02-04
> **watchpocket said:**
> I'll need grub-pc for amd64, I think (instead of grub-efi-amd64), since my machine is 64-bit, but BIOS, not UEFI.

No matter if you have a 32 bit or 64 bit system you will get that message. 
I just executed the command on Vivid Vervet 15.05 and here's the output:

```
cavsfan@cavsfan-MS-7529:~$ sudo grub-install /dev/sda
[sudo] password for cavsfan: 
[COLOR=#ff0000]Installing for i386-pc platform.[/COLOR]
Installation finished. No error reported.

cavsfan@cavsfan-MS-7529:~$ sudo update-grub
Generating grub configuration file ...
Found background image: milky_way_sky-wide.jpg
Adding Precise Pangolin 12.04, Trusty Tahr 14.04, Vivid Vervet 15.04 (devel branch), Mint 17 Rebecca and Windows 7
done
```

Here is what my grub screen looks like: 

[[img]http://www.zimagez.com/miniature/20150201141509.jpg[/img]](http://www.zimagez.com/zimage/20150201141509.php)

> **oygle said:**
> Have done as per your instructions ..

```
$ sudo chmod -x /etc/grub.d/20_memtest86+
$ sudo chmod -x /etc/grub.d/10_linux
$ sudo chmod -x /etc/grub.d/30_os-prober
$ sudo update-grub
Generating grub configuration file ...
done
$ 
```

Hmm, that 3rd option doesn't boot to windows. I now remember that the last option worked...

```
$ sudo chmod +x /etc/grub.d/30_os-prober
$ sudo update-grub
Generating grub configuration file ...
Found Microsoft Windows XP Professional on /dev/sdb1
done
$ 

```

Now I assume I don't actually need that third line in **/etc/grub.d/06_custom**

Could you post the output of **sudo blkid -c /dev/null -o list**.
And also the results of **sudo grub-mkconfig** with only **30_os-prober** executable.

If it's too long to be able to get to the top of it in terminal pipe it to a text file like this:
**sudo grub-mkconfig > <text-file-name>** I'll leave it up to you what to name it but replace <text-file-name> with sonething like grub-output.
I'd like to see why that entry in **06_custom** doesn't work while the one produced by **30_os-prober** when **sudo update-grub** is executed.

---

### Post by Cavsfan on 2015-02-04
> **watchpocket said:**
> I most likely -will- do a total purge of grub (after backing up everything in /etc/grub.d), because none of what I've done with grub (per Cavsfan's suggestions) has effected any change at all, and also partly because it looks like I may currently be running grub for i386 instead of for amd64.  

But, a question: if I purge grub, I'm guessing I'll need to reinstall it *immediately* after purging, and without rebooting or shutting down, or else I won't be able to boot (although the 1.98 or 1.99  legacy grub that I have on /dev/sdb that's part of my Ubuntu 12.04.5 install might take over the booting process.  (Wait, no, that probably won't happen because I unchecked the boot flag for /dev/sdb with gparted, per Cavsfan's advice.)



I definitely have scripts in /etc/grub.d -- but how do I tell which scripts were created with grub-customizer and which weren't?



Thank you for the clarifications.

If you purge grub-customizer it should remove the script it created but just so you know what is in /etc/grub.d/ here is the contents of my directory:
```
cavsfan@cavsfan-desktop:~$ cd /etc/grub.d/
cavsfan@cavsfan-desktop:/etc/grub.d$ ls -l
total 84
-rwxr-xr-x 1 root root  9424 Apr 11  2014 [COLOR="#33cc66"]00_header[/COLOR]
-rwxr-xr-x 1 root root  6193 Oct  1 11:20 [COLOR="#33cc66"]05_debian_theme[/COLOR]
-rwxr-xr-x 1 root root  1861 Jan 10 07:01 [COLOR="#33cc66"]06_custom[/COLOR]
-rw-r--r-- 1 root root 11608 Apr 11  2014 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11  2014 [COLOR="#33cc66"]20_linux_xen[/COLOR]
-rw-r--r-- 1 root root  1992 Mar 12  2014 20_memtest86+
-rw-r--r-- 1 root root 11692 Apr 11  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11  2014 [COLOR="#33cc66"]30_uefi-firmware[/COLOR]
-rwxr-xr-x 1 root root   214 Apr 11  2014 [COLOR="#33cc66"]40_custom[/COLOR]
-rwxr-xr-x 1 root root   216 Apr 11  2014 [COLOR="#33cc66"]41_custom[/COLOR]
-rw-r--r-- 1 root root   483 Apr 11  2014 README

```

My grub has been customized and the green files are the only ones executable. But that is for later. The files should match what you have after you've re-installed grub.

As good a way as any to purge grub and re-install it would be to do this; (and you definitely want to complete all the steps before rebooting!!!)
I'm in Trusty and this is what grub files I have installed:
```
cavsfan@cavsfan-desktop:~$ dpkg -l | grep grub
ii  grub-common                                           2.02~beta2-9ubuntu1                                 amd64        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                                 0.6                                                 amd64        GRUB gfxpayload blacklist
ii  grub-pc                                               2.02~beta2-9ubuntu1                                 amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                           2.02~beta2-9ubuntu1                                 amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                                          2.02~beta2-9ubuntu1                                 amd64        GRand Unified Bootloader (common files for version 2)
```

So **sudo apt-get purge grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common** from terminal should do the trick.

Then you most definitely want to re-install before doing anything else:

**sudo apt-get install grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common** 

Then if you don't see it perform **sudo grub-install /dev/sda** then enter it manually and then enter **sudo update-grub** and you should be back to the normal default grub.

Again just ignore that i386 message as it does it on every system 32 bit or 64 bit.

Then you can peruse the wiki to customize your grub.

---

### Post by Cavsfan on 2015-02-05
BTW oygle, is there any reason you're hanging on to Windows XP since it has gone past it's EOL?

Read option 1 here: [http://windows.microsoft.com/en-us/windows/end-support-help](http://windows.microsoft.com/en-us/windows/end-support-help)

Here's a bit from that site: ".... it’ll become five times more vulnerable to security risks and viruses, which means you could get hacked and have your personal information stolen."

---

### Post by watchpocket on 2015-02-14
So I've purged grub-customizer, its files and proxy files and anything with that name, including its PPA in software sources. And I purged *all *the grub files and re-installed per suggestions above.

So far all is going well with the customization of my grub and right now I'm customizing menuentries in /etc/grub.d/40_custom, to be saved as /etc/grub.d/06_custom.  (I'll first remove my current 06_custom file that you made, Cavsfan).

Meanwhile, a quick question: 

In the wiki there's this:
```

menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro [COLOR=#ff0000]**single**[/COLOR]
        initrd /initrd.img
}
```

Is the word "**single**" where it is (instead of "**recovery nomodeset**") because this recovery-mode entry is for Precise Pangolin (as opposed to another version of Ubuntu or another distro)? 

Or is it there because this is the *first recovery-mode entry in the list*, and "**single**" goes where it is only in that first recovery-mode entry, and "**recovery nomodeset**" goes in the place of "**single**" for all *subsequent* recovery mode menuentries?  (I'm guessing the latter, but it would be good to confirm.)  

Or neither?  Or does it matter?  Maybe this was discussed in the wiki but if so, I missed it.  

(So if I have Trusty as the first menu entry, and Trusty-recovery-mode as the second menu entry, should I have "**single**" or "**recovery nomodeset**" to the right of "**ro**" in this  particular recovery-mode entry?

Oh, I also do not have a "**memtest86+**" file in /etc/grub.d/ -- I have a feeling it should be there (I see it on various pictures of grub-screen menus).  If so, how is it generated or where would I otherwise copy text into it from?

Thank you for any clarification and thanks for all of your and others' work on grub.

---

### Post by watchpocket on 2015-02-14
Actually, I realize now that it doesn't matter because I'm going to leave Precise as my first menu entry anyway (and Precise recovery mode as my 2nd), so that when I want to boot into Precise, I can simply bring up the grub menu and hit <ENTER> without having to use the arrow-keys to move up or down anywhere.   

[EDIT -- Minor correction to the above: I see that once grub is displayed, the default menu entry (in my case, #2) is already highlighted, so to choose Precise (which is not the default), I do in fact need to arrow-up and then press <ENTER>.]

I have Trusty as default with the GRUB_DEFAULT setting in /etc/default/grub.

I think I'll leave **memtest86+** out of the menu, I don't think I need it, unless someone comes up with a good reason why it should be there.

I'd like to have the grub menu not show at all until I hit a key, but it seems to want to display even with GRUB_TIMEOUT=0 and GRUB_HIDDEN_TIMEOUT=10.

Pic attached, colors are: ```
118 echo " set color_normal=light-blue/black"
119 echo " set menu_color_normal=light-gray/black"
120 echo " set menu_color_highlight=white/light-blue"
```[ATTACH=CONFIG]259993[/ATTACH]
(This pic taken with my phone doesn't quite do justice to the background image, which is darker than it appears here.  The brownish colors at left & right only appear in this pic.)

---

### Post by Cavsfan on 2015-02-15
> **watchpocket said:**
> Actually, I realize now that it doesn't matter because I'm going to leave Precise as my first menu entry anyway (and Precise recovery mode as my 2nd), so that when I want to boot into Precise, I can simply bring up the grub menu and hit <ENTER> without having to use the arrow-keys to move up or down anywhere.   

[EDIT -- Minor correction to the above: I see that once grub is displayed, the default menu entry (in my case, #2) is already highlighted, so to choose Precise (which is not the default), I do in fact need to arrow-up and then press <ENTER>.]

I have Trusty as default with the GRUB_DEFAULT setting in /etc/default/grub.

I think I'll leave **memtest86+** out of the menu, I don't think I need it, unless someone comes up with a good reason why it should be there.

I'd like to have the grub menu not show at all until I hit a key, but it seems to want to display even with GRUB_TIMEOUT=0 and GRUB_HIDDEN_TIMEOUT=10.

Pic attached, colors are: ```
118 echo " set color_normal=light-blue/black"
119 echo " set menu_color_normal=light-gray/black"
120 echo " set menu_color_highlight=white/light-blue"
```[ATTACH=CONFIG]259993[/ATTACH]
(This pic taken with my phone doesn't quite do justice to the background image, which is darker than it appears here.  The brownish colors at left & right only appear in this pic.)

The **quiet splash** is for any version's normal boot line. The **ro single** is _*only*_ for Precise's recovery boot line.  Later versions have **recovery nomodeset** on the recovery boot line.

A forum user [_bogan_]("http://ubuntuforums.org/member.php?u=1017537") once pointed the difference in recovery lines to me.

If you want Precise to be your default menu line, edit **/etc/default/grub** and make **GRUB_DEFAULT=0**. The entries start at 0 like this: 0,1,2,3...

**grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0** entered in terminal will show you this.

If you're happy with the top custom entries, make **/etc/grub.d/30_os-prober** unexecutable and enter **sudo update-grub** and you will only see the custom entries.
I have never had a need for **memtest86+**. I have also never had the need to boot into an older kernel than the latest. 
If you ever find a reason to you can just make **30_os-prober** executable again and then **sudo update-grub**, reboot and you have that option back. 
But if you want a nice clean menu the former is the way to go.

I also know of no way to make the menu only appear if you press a key.

---

### Post by watchpocket on 2015-02-15
> **Cavsfan said:**
> The **quiet splash** is for any version's normal boot line. The **ro single** is _*only*_ for Precise's recovery boot line.  Later versions have **recovery nomodeset** on the recovery boot line.

Thanks -- I thought this might be the case.

>  [ . . . ]The entries start at 0 like this: 0,1,2,3...

**grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0** entered in terminal will show you this.

The output of that  command reminds me that I have far too many old kernels.  I'd like to get rid of all but **-45** and **-44**, but I'm not sure how to do that.  (Do folks generally leave all these old kernels laying around?  Seems like unneccessary cruft.)

> If you're happy with the top custom entries, make **/etc/grub.d/30_os-prober** unexecutable and enter **sudo update-grub** and you will only see the custom entries.

Actually, I'm seeing the custom entries, plus a fifth line ("Ubuntu") and a sixth line ("Advanced options for Ubuntu").  This is fewer lines than appeared before making that change, but I didn't expect to see them.  A title like "Ubuntu" -- without even a version number (though I know this is Trusty) -- is kind of useless.  If it has to remain, I'd like to add the version number to the title, if possible.  Then I'll be done.

> I also know of no way to make the menu only appear if you press a key.

That's OK -- I need the grub menu to appear so I can choose between booting to Trusty or Precise.

---

### Post by watchpocket on 2015-02-15
.

---

### Post by Bashing-om on 2015-02-16
watchpocket; Hello;

I also am a student of grub, fascinating little process that it is.

> 
The output of that command reminds me that I have far too many old kernels. I'd like to get rid of all but -45 and -44, but I'm not sure how to do that. (Do folks generally leave all these old kernels laying around? Seems like unneccessary cruft.)


Removing old kernels. If you do not need/want them then YES remove them . The system will not second guess what you want. It is at your discretion to remove them.
'apt-get autoremove' has been re-vamped in later releases to do this, I do not know that it is back ported to precise, and a lot depends on the kernel that is installed.
Try and see if this works for you:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get autoremove

```
else; to remove the old precise kernels will resort to 'apt-get --purge remove linux-image-XXXX ; generic, and headers too.

many prefer to use 'synaptic' to remove the old kernels.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by watchpocket on 2015-02-16
Before I do that, I just want to make sure: Does any functioning depend on the presence of old kernels?  In other words, are new kernels built upon previous ones in any way?  (Or do they -include- the functionality of a previous one?) 

So if I remove an old kernel, there's nothing about doing that that will make the latest kernel lose any functionality, correct? Don't new kernels entirely replace old ones?

---

### Post by watchpocket on 2015-02-16
I wrote, above:

*Actually, I'm seeing the custom entries, plus a fifth line ("Ubuntu")  and a sixth line ("Advanced options for Ubuntu").  This is fewer lines  than appeared before making that change, but I didn't expect to see  them.  A title like "Ubuntu" -- without even a version number (though I  know this is Trusty) -- is kind of useless.  If it has to remain, I'd  like to add the version number to the title, if possible.  Then I'll be  done.*

I forgot to add that I can't figure out how I would make that change.  Edits from within the grub menu are not saved.  How or in which file would I be able to edit the title of non-custom menu entries?

---

### Post by Bashing-om on 2015-02-16
watchpocket; Well;

The most important is what kernel you are presently booting:
```

uname -r

```

Ideally you want to keep the latest kernel, and one other for a back up. All others can be safely removed IF you are not booting with one of those old kernels.

When all done removing kernels, even though the routine is scripted, does not hurt a thing and is cheap insurance to look at what grub does individually:
```

sudo update-grub

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Cavsfan on 2015-02-16
I agree with Bashing-om but I don't use auto-remove because I don't trust it to remove all parts of the kernel.
I keep all of my kernels on a text file and delete one when one is added keeping two.

Here is my (quite long) text file for Precise:
```
Upgraded Lucid Lynx 10.04 LTS to Precise Pangolin 12.04 LTS 
(linux-headers-generic linux-image-generic get updated with each new kernel install)

sudo apt-get purge linux-headers-3.2.0-37 linux-headers-3.2.0-37-generic linux-image-3.2.0-37-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic linux-image-3.2.0-38-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-39 linux-headers-3.2.0-39-generic linux-image-3.2.0-39-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-40 linux-headers-3.2.0-40-generic linux-image-3.2.0-40-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-41 linux-headers-3.2.0-41-generic linux-image-3.2.0-41-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-43 linux-headers-3.2.0-43-generic linux-image-3.2.0-43-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-44 linux-headers-3.2.0-44-generic linux-image-3.2.0-44-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-45 linux-headers-3.2.0-45-generic linux-image-3.2.0-45-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-48 linux-headers-3.2.0-48-generic linux-image-3.2.0-48-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-49 linux-headers-3.2.0-49-generic linux-image-3.2.0-49-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-51 linux-headers-3.2.0-51-generic linux-image-3.2.0-51-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-52 linux-headers-3.2.0-52-generic linux-image-3.2.0-52-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-53 linux-headers-3.2.0-53-generic linux-image-3.2.0-53-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-54 linux-headers-3.2.0-54-generic linux-image-3.2.0-54-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-56 linux-headers-3.2.0-56-generic linux-image-3.2.0-56-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-57 linux-headers-3.2.0-57-generic linux-image-3.2.0-57-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-58 linux-headers-3.2.0-58-generic linux-image-3.2.0-58-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-59 linux-headers-3.2.0-59-generic linux-image-3.2.0-59-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-60 linux-headers-3.2.0-60-generic linux-image-3.2.0-60-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-61 linux-headers-3.2.0-61-generic linux-image-3.2.0-61-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-63 linux-headers-3.2.0-63-generic linux-image-3.2.0-63-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-64 linux-headers-3.2.0-64-generic linux-image-3.2.0-64-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-65 linux-headers-3.2.0-65-generic linux-image-3.2.0-65-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-67 linux-headers-3.2.0-67-generic linux-image-3.2.0-67-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-68 linux-headers-3.2.0-68-generic linux-image-3.2.0-68-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-69 linux-headers-3.2.0-69-generic linux-image-3.2.0-69-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-70 linux-headers-3.2.0-70-generic linux-image-3.2.0-70-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-72 linux-headers-3.2.0-72-generic linux-image-3.2.0-72-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-74 linux-headers-3.2.0-74-generic linux-image-3.2.0-74-generic    - purged.

sudo apt-get purge linux-headers-3.2.0-75 linux-headers-3.2.0-75-generic linux-image-3.2.0-75-generic

sudo apt-get purge linux-headers-3.2.0-76 linux-headers-3.2.0-76-generic linux-image-3.2.0-76-generic
```

I guess I don't trust auto-remove because it only wants to remove a piece of the kernel and leave the other pieces.
Definitely on Precise like Bashing-om mentioned.

Here is my text file for Vivid: (versions after Precise added some extra parts as you're probably aware of)
```
linux-generic linux-headers-generic linux-image-generic

sudo apt-get purge linux-headers-3.18.0-9 linux-headers-3.18.0-9-generic linux-image-3.18.0-9-generic linux-image-extra-3.18.0-9-generic    deleted

sudo apt-get purge linux-headers-3.18.0-11 linux-headers-3.18.0-11-generic linux-image-3.18.0-11-generic linux-image-extra-3.18.0-11-generic    deleted

sudo apt-get purge linux-headers-3.18.0-12 linux-headers-3.18.0-12-generic linux-image-3.18.0-12-generic linux-image-extra-3.18.0-12-generic    deleted

sudo apt-get purge linux-headers-3.18.0-13 linux-headers-3.18.0-13-generic linux-image-3.18.0-13-generic linux-image-extra-3.18.0-13-generic
```

This wil also show you which kernels you have installed too:
```
cavsfan@cavsfan-MS-7529:~$ **dpkg -l | grep linux**
ii  libselinux1:amd64                                    2.3-2                                      amd64        SELinux runtime shared libraries
ii  libv4l-0:amd64                                       1.6.0-2                                    amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                 1.6.0-2                                    amd64        Video4linux frame format conversion library
ii  linux-firmware                                       1.141                                      all          Firmware for Linux kernel drivers
ii  linux-generic                                        3.18.0.13.13                               amd64        Complete Generic Linux kernel and headers
ii  [COLOR=#ff0000]linux-headers-3.18.0-13[/COLOR]                              3.18.0-13.14                               all          Header files related to Linux kernel version 3.18.0
ii  [COLOR=#ff0000]linux-headers-3.18.0-13-generic[/COLOR]                      3.18.0-13.14                               amd64        Linux kernel headers for version 3.18.0 on 64 bit x86 SMP
ii  linux-headers-generic                                3.18.0.13.13                               amd64        Generic Linux kernel headers
ii  [COLOR=#ff0000]linux-image-3.18.0-13-generic[/COLOR]                        3.18.0-13.14                               amd64        Linux kernel image for version 3.18.0 on 64 bit x86 SMP
ii  [COLOR=#ff0000]linux-image-extra-3.18.0-13-generic[/COLOR]                  3.18.0-13.14                               amd64        Linux kernel extra modules for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-generic                                  3.18.0.13.13                               amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                 3.18.0-13.14                               amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu4                       all          base package for ALSA and OSS sound systems
ii  pptp-linux                                           1.7.2-7                                    amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                             3:6.03~pre18+dfsg-1ubuntu1                 amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                                      3:6.03~pre18+dfsg-1ubuntu1                 all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu5                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                           2.25.2-4ubuntu1                            amd64        Miscellaneous system utilities

```

The red shows the parts that can be removed. You never want to remove linux-generic, linux-headers-generic or linux-image-generic.

I have searched and searched for who in this forum showed me this method but cannot find them. It was in their signature I'm pretty sure.
Here is a way to remove all previous kernels except the current one and there is a very important dry run flag so you can see what it will do before you actually do it.

This has the ***--dry-run*** switch to see what it would do:
```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e  `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)"  | xargs sudo apt-get --dry-run remove
```

Then if you're happy with the output and what will be deleted run this command without the ***--dry-run*** switch:

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e  `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)"  | xargs sudo apt-get -y purge
```

I found this on this page step 6: [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

I ran it and since I have only one kernel it did not offer to delete anything. But I do like that ***--dry-run*** switch. :)

---

### Post by Cavsfan on 2015-02-16
> **watchpocket said:**
> Before I do that, I just want to make sure: Does any functioning depend on the presence of old kernels?  In other words, are new kernels built upon previous ones in any way?  (Or do they -include- the functionality of a previous one?) 

So if I remove an old kernel, there's nothing about doing that that will make the latest kernel lose any functionality, correct? Don't new kernels entirely replace old ones?

Nothing depends on previous kernels. I usally keep two but currently have just the latest. I have never in my 5-6 years dealing with Ubuntu had to boot into an old kernel.

> **watchpocket said:**
> I wrote, above:

*Actually, I'm seeing the custom entries, plus a fifth line ("Ubuntu")  and a sixth line ("Advanced options for Ubuntu").  This is fewer lines  than appeared before making that change, but I didn't expect to see  them.  A title like "Ubuntu" -- without even a version number (though I  know this is Trusty) -- is kind of useless.  If it has to remain, I'd  like to add the version number to the title, if possible.  Then I'll be  done.*

I forgot to add that I can't figure out how I would make that change.  Edits from within the grub menu are not saved.  How or in which file would I be able to edit the title of non-custom menu entries?

As I mentioned, if you can boot into 12.04 and 14.04 just fine with the custom entries in **/etc/grub.d/06_custom** then make **/etc/grub.d/10_linux** and **/etc/grub.d/30_os-prober** unexecutable with these commands:

```
sudo chmod -x /etc/grub.d/10_linux && sudo chmod -x/etc/grub.d/30_os-prober && sudo update-grub
```

Reboot and you will only see the custom entries, which is the purpose of this wiki.

---

### Post by Cavsfan on 2015-02-16
Here is what my grub screen looked like awhile back: I've since changed just the picture.

[[IMG]http://www.zimagez.com/miniature/20141226135835.jpg[/IMG]]("http://www.zimagez.com/zimage/20141226135835.php")

---

### Post by watchpocket on 2015-02-16
I've never seen this before, but doing a ```

sudo chmod -x /etc/grub.d/10_linux
```

returns this: ```
chmod: /etc/grub.d/10_linux: new permissions are rw-r-xr-x, not rw-r--r--
```

Darned if that file does *not* want to completely un-executable itself.

---

### Post by watchpocket on 2015-02-16
Just to say I was able to purge all my old kernels with that long command.  On Trusty, I purged everything except the current kernel (**...-45**). For some reason that command didn't purge 3.13.0**-39**, so I just purged that one individually with no ill effects.

On Precise, I decided not to use the long command and purged individually.  I left **-45**, **-44**, **memtest86+**, and anything with the name "trusty" in it.  During the purge process, two items that were deleted gave a slightly scary warning that they were active in the current kernel.  They were my nvidea driver and an nvidea updates file (which drivers btw on trusty made everything weird, so I'm using the free nouveau driver there).  So before re-booting, I just went into synaptic and made sure to mark those 2 items for re-install, then hit apply.  I re-booted into Precise and all was well.  

I'll now refrain from hijacking this grub thread (speaking of which, that non-un-executability still has me scratching my head) with side-talk of old kernels.  Thanks loads Cavsfan and bashing-om (great name, btw).

---

### Post by Bashing-om on 2015-02-16
watchpocket; Well,

Final cleanup:
```

dpkg -l | grep linux-

```
Those packages marked 'rc', 
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command.
where the state is 'rc', the package is removed, but the config files are not removed:
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```


I expect now
[INDENT][INDENT][INDENT]distinct aroma of a rose
[/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2015-02-16
This is both the commands run In trusty (not precise):

```
--> dpkg -l | grep linux-                                                                                       pts/1  Monday  2015-02-16  20:51:31 
ii  linux-firmware                                        1.127.11                                                all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.45.52                                            amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-45                               3.13.0-45.74                                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                       3.13.0-45.74                                            amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.45.52                                            amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.45.52                                            amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-45.74                                            amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                    all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                    all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                    amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

Do I really want to remove all of the below?  These are all config files with ".rc" at the end?   (That must be what the "rc" in each file's far left column indicates. Btw, what does the "ii" refer to in the left column above?)

```
--> dpkg -l |grep "^rc"                                                                                         pts/1  Monday  2015-02-16  20:54:09 
rc  dkms                                                  2.2.0.3-1.1ubuntu5.14.04                                all          Dynamic Kernel Module Support Framework
rc  lib32gcc1                                             1:4.9.1-0ubuntu1                                        amd64        GCC support library (32 bit Version)
rc  libc6-i386                                            2.19-0ubuntu6.5                                         amd64        Embedded GNU C Library: 32-bit shared libraries for AMD64
rc  libcuda1-331                                          331.113-0ubuntu0.0.4                                    amd64        NVIDIA CUDA runtime library
rc  libcuda1-331-updates                                  331.113-0ubuntu0.0.4                                    amd64        NVIDIA CUDA runtime library
rc  libcuda1-346                                          346.35-0ubuntu1~system76~14.04.2                        amd64        NVIDIA CUDA runtime library
rc  libvdpau1:amd64                                       0.7-1                                                   amd64        Video Decode and Presentation API for Unix (libraries)
rc  ocl-icd-libopencl1:amd64                              2.1.3-4                                                 amd64        Generic OpenCL ICD Loader
rc  packagekit                                            0.8.12-1ubuntu5                                         amd64        Provides a package management service
rc  screen-resolution-extra                               0.17.1                                                  all          Extension for the GNOME screen resolution applet
rc  unity-webapps-common                                  2.4.17+14.04.20140416-0ubuntu1                          all          Unity WebApp integration scripts
rc  unity-webapps-launchpad                               2.4.16+13.10.20130924.2-0ubuntu1                        all          Unity Webapp for Launchpad
```

---

### Post by Bashing-om on 2015-02-16
watchpocket; Hey:

In respect to 'rc' packages, I would remove them ..
'rc' mark is (r)emoved but (c)onfig files remain.
'ii' mark is (i)install [desired] (i)nstalled [Status].

Do:
```

dpkg -l "linux-image*"

``` for instance; and see the header of the output for an explanation of what the 1st column's 4 possible indices mean ( here we are only discussing 2 of those fields) .

[INDENT][INDENT]so much to know about the package manager - wonder to behold
[/INDENT][/INDENT]

---

### Post by watchpocket on 2015-02-16
> **Bashing-om said:**
> watchpocket; Hey:
In respect to 'rc' packages, I would remove them ..

Done.  

There are, however, 2 possibly curious files in my root dir (where everything else is a directory): an "initrd.img" file -- an "18.3 MiB Link to Raw disk image" (looking at its properties, its Link target is "boot/initrd.img-3.13.0-45-generic); and a "vmlinuz" file, a "5.5 MiB Link to unknown".  Looking at its properties, its Link target is "boot/vmlinuz-3.13.0-45-generic".)  

They both link to files in the /boot dir.  Should I assume it's OK that they're there in / ?  I guess the "link to unknown" part bothers me a bit, but maybe it shouldn't.  I do notice that these same link files are in the root dir of both my Trusty and my Precise.

> 'rc' mark is (r)emoved but (c)onfig files remain.
'ii' mark is (i)install [desired] (i)nstalled [Status].

Do:
```

dpkg -l "linux-image*"

``` for instance; and see the header of the output for an explanation of what the 1st column's 4 possible indices mean ( here we are only discussing 2 of those fields) .
Wow.  Very interesting and _*very*_ helpful.
> so much to know about the package manager - wonder to behold
Truly!  Thank you!

---

### Post by Cavsfan on 2015-02-17
> **watchpocket said:**
> I've never seen this before, but doing a ```

sudo chmod -x /etc/grub.d/10_linux
```

returns this: ```
chmod: /etc/grub.d/10_linux: new permissions are rw-r-xr-x, not rw-r--r--
```

Darned if that file does *not* want to completely un-executable itself.

That is odd. Are you sure you are not logged into a restricted account?

Enter this in terminal **sudo cat /etc/group | grep <your user name>** and make sure you're in sudo group.

```
cavsfan@cavsfan-MS-7529:~$ sudo cat /etc/group | grep cavsfan
adm:x:4:syslog,cavsfan
cdrom:x:24:cavsfan
[COLOR=#FF0000]sudo[/COLOR]:x:27:cavsfan
dip:x:30:cavsfan
plugdev:x:46:cavsfan
lpadmin:x:114:cavsfan
cavsfan:x:1000:
sambashare:x:130:cavsfan
```

 

If so try this: (give owner root read/write, group and others read only and non executable.)
**sudo chmod 644 /etc/grub.d/10_linux** likewise with **sudo chmod 644 /etc/grub.d/30_os-prober** if you have not already got that unexecutable.

If that does not do the trick try this:
in terminal enter **gksudo nautilus** and enter your password

Then maneuver to **/etc/grub.d/** and then right click on **10_linux** and go to properties. 
Then click the middle tab Permissions.
Uncheck the Execute box at the bottom. 
Also do the same to **30_os-prober** and **20_memtest86+** if that's needs to be done.
Then close nautilus.

Then in terminal:
 
Enter **cd /etc/grub.d/**
Then enter **ls -l** 


It should show **10_linux**, **20_memtest86+** and **30_os-prober** as white meaning not executable, while green means executable.

Then of course enter **sudo update-grub** and see if just the custom entries apear in the list.
It should list the picture name you have in **/boot/grub/** and show what you have put on the 2nd line of **/etc/grub.d/06_custom** between the quotes and nothing else.

---

### Post by Cavsfan on 2015-02-17
That is a nice little command to remove the config files Bashing-om. 
I might try that on Precise as I probably have tons of those there. The above is on Vivid with few config files hanging.

I always do **sudo apt-get purge <package-name>** to remove the config files and the package instead of **sudo apt-get remove <package-name>**, which will leave the config files.
But, we can't control what is auto removed.

---

### Post by watchpocket on 2015-02-17
> **Cavsfan said:**
> [ . . . ]
If so try this: (give owner root read/write, group and others read only and non executable.)
**sudo chmod 644 /etc/grub.d/10_linux** likewise with **sudo chmod 644 /etc/grub.d/30_os-prober** if you have not already got that unexecutable.

If that does not do the trick 
[ . . . ]

It did the trick.  It was only that file that was being stubborn, and that last command made it unexecutable.  So I **sudo upgrade-grub**'d and re-booted to see that I now finally have just the custom entries in the grub menu. My god, you're a lifesaver. I bow to you.

My /etc/group read-out btw was indentical to yours.  I think I'm done with grub questions now, though I still don't understand why changing permissions from sudo didn't work.  Superuser itself must not have had full write permissions.  Thanks again for all this problem-solving.

---

### Post by Cavsfan on 2015-02-17
> **Cavsfan said:**
> 
                 [ . . . ]
If so try this: (give owner root read/write, group and others read only and non executable.)
**sudo chmod 644 /etc/grub.d/10_linux** likewise with **sudo chmod 644 /etc/grub.d/30_os-prober** if you have not already got that unexecutable.

If that does not do the trick 
[ . . . ]

> **watchpocket said:**
> It did the trick.  It was only that file that was being stubborn, and that last command made it unexecutable.  So I **sudo upgrade-grub**'d and re-booted to see that I now finally have just the custom entries in the grub menu. My god, you're a lifesaver. I bow to you.

My /etc/group read-out btw was identical to yours.  I think I'm done with grub questions now, though I still don't understand why changing permissions from sudo didn't work.  Superuser itself must not have had full write permissions.  Thanks again for all this problem-solving.

You are very welcome! :) Glad you got the problem solved and now have a custom grub menu. :popcorn:
Now you will never have to do anything unless you remove or add another Linux system. It will always boot into the latest kernel and it will never let you down.

Feel free at any time to post a question about this custom grub wiki here.

You can change pictures as you please, just remove the one you have as it looks for the first one it finds.

You can also change the font colors to match the picture too. Some times it gets boring and time for a change with the picture and colors. 

Cheers :)

---

### Post by watchpocket on 2015-02-17
And a whole lot more, it appears.  There's always [this]("https://www.gnu.org/software/grub/manual/grub.html#Theme-file-format") to dig into for getting *really* fancy. ;)

---

### Post by Bashing-om on 2015-02-18
watchpocket; Hey;

I somehow missed this:
> 
There are, however, 2 possibly curious files in my root dir (where everything else is a directory): an "initrd.img" file -- an "18.3 MiB Link to Raw disk image" (looking at its properties, its Link target is "boot/initrd.img-3.13.0-45-generic); and a "vmlinuz" file, a "5.5 MiB Link to unknown". Looking at its properties, its Link target is "boot/vmlinuz-3.13.0-45-generic".) 

The link to "unknown" just is not right.
Is it still present ?
let's look:
```

ls -al /
ls -al /boot

```
where I expect only 4 symlinks (2 current - vmlinuz & initrd.img and 2 for XXX.old - ) that they point to valid files in '/boot' .

when things are not as I expect
[INDENT][INDENT][INDENT]I do get into my learning mode
[/INDENT][/INDENT][/INDENT]

---

### Post by Cavsfan on 2015-02-18
> **watchpocket said:**
> And a whole lot more, it appears.  There's always [this]("https://www.gnu.org/software/grub/manual/grub.html#Theme-file-format") to dig into for getting *really* fancy. ;)

Feel free to delve into that. I'm keeping this wiki as simple as I can though. It already scares some people away. 
But, once you understand what you have to do it gets a lot simpler and there are only a few steps to the process.

I say if it aint broke why fix it? ;)

---

### Post by Cavsfan on 2015-02-18
> **Bashing-om said:**
> watchpocket; Hey;

I somehow missed this:

The link to "unknown" just is not right.
Is it still present ?
let's look:
```

ls -al /
ls -al /boot

```
where I expect only 4 symlinks (2 current - vmlinuz & initrd.img and 2 for XXX.old - ) that they point to valid files in '/boot' .

when things are not as I expect[INDENT][INDENT][INDENT]I do get into my learning mode
[/INDENT]
[/INDENT]
[/INDENT]


They must be valid or else watchpocket would not be able to boot into those systems as the custom grub uses those symlinks.
At least the one that points to the most currently installed kernel.

---

### Post by Bashing-om on 2015-02-18
@Cavsfan; Agreed;

> **Cavsfan said:**
> They must be valid or else watchpocket would not be able to boot into those systems as the custom grub uses those symlinks.
At least the one that points to the most currently installed kernel.

Just to make sure things a tidy.


[INDENT][INDENT]clean is clean
[/INDENT][/INDENT]

---

### Post by watchpocket on 2015-02-18
> **Bashing-om said:**
> 
The link to "unknown" just is not right.
Is it still present ?
let's look:
```

ls -al /
ls -al /boot

```
where I expect only 4 symlinks (2 current - vmlinuz & initrd.img and 2 for XXX.old - ) that they point to valid files in '/boot' .


In Precise: ```
--> ls -la /  
total 116
 4 drwxr-xr-x  26 root root  4096 Feb 11 01:22 ./
 4 drwxr-xr-x  26 root root  4096 Feb 11 01:22 ../
 4 drwxr-xr-x   2 root root  4096 Jul 18  2014 .rpmdb/
 4 drwxr-xr-x   2 root root  4096 Feb 11 01:22 bin/
 4 drwxr-xr-x   4 root root  4096 Feb 16 18:56 boot/
 4 drwxr-xr-x   2 root root  4096 Jan 11  2014 cdrom/
 0 drwxr-xr-x  15 root root  4380 Feb 18 13:28 dev/
12 drwxr-xr-x 152 root root 12288 Feb 18 13:28 etc/
 4 drwxr-xr-x   3 root root  4096 Jan 11  2014 home/
 0 lrwxrwxrwx   1 root root    33 Feb 11 01:22 initrd.img -> boot/initrd.img-3.13.0-45-generic
 0 lrwxrwxrwx   1 root root    33 Jan 16 14:30 initrd.img.old -> boot/initrd.img-3.13.0-44-generic
 4 drwxr-xr-x  26 root root  4096 Feb 16 18:32 lib/
 4 drwxr-xr-x   2 root root  4096 Feb  3 14:16 lib32/
 4 drwxr-xr-x   2 root root  4096 Feb  3 14:16 lib64/
16 drwx------   2 root root 16384 Jan 11  2014 lost+found/
 4 drwxr-xr-x   2 root root  4096 Feb 16 22:24 media/
 4 drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt/
 4 drwxr-xr-x   4 root root  4096 Jul  6  2014 opt/
 0 dr-xr-xr-x 201 root root     0 Feb 18 13:27 proc/
 4 drwx------  13 root root  4096 Feb 16 18:32 root/
 0 drwxr-xr-x  21 root root   820 Feb 18 13:28 run/
12 drwxr-xr-x   2 root root 12288 Feb 11 22:29 sbin/
 4 drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux/
 4 drwxr-xr-x   2 root root  4096 Aug 20  2013 srv/
 0 dr-xr-xr-x  13 root root     0 Feb 18 13:27 sys/
 4 drwxrwxrwt   8 root root  4096 Feb 18 13:48 tmp/
 4 drwxr-xr-x  11 root root  4096 Dec 14 18:48 usr/
 4 drwxr-xr-x  13 root root  4096 Feb 17 01:05 var/
 0 lrwxrwxrwx   1 root root    30 Feb 11 01:22 vmlinuz -> boot/vmlinuz-3.13.0-45-generic
 0 lrwxrwxrwx   1 root root    30 Jan 16 14:30 vmlinuz.old -> boot/vmlinuz-3.13.0-44-generic

--> lf /boot    
total 58368
    4 drwxr-xr-x  4 root root     4096 Feb 16 18:56 ./
    4 drwxr-xr-x 26 root root     4096 Feb 11 01:22 ../
 3444 -rw-------  1 root root  3525141 Dec 16 19:55 System.map-3.13.0-44-generic
 3444 -rw-------  1 root root  3525572 Jan 15 15:46 System.map-3.13.0-45-generic
 1140 -rw-r--r--  1 root root  1164720 Dec 16 19:55 abi-3.13.0-44-generic
 1140 -rw-r--r--  1 root root  1164967 Jan 15 15:46 abi-3.13.0-45-generic
  164 -rw-r--r--  1 root root   165757 Dec 16 19:55 config-3.13.0-44-generic
  164 -rw-r--r--  1 root root   165757 Jan 15 15:46 config-3.13.0-45-generic
    4 drwxr-xr-x  3 root root     4096 Feb 16 18:56 extlinux/
   12 drwxr-xr-x  3 root root    12288 Feb 16 19:03 grub/
18484 -rw-r--r--  1 root root 18920653 Jan 16 14:31 initrd.img-3.13.0-44-generic
18484 -rw-r--r--  1 root root 18927341 Feb 16 18:34 initrd.img-3.13.0-45-generic
  176 -rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
  176 -rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
 5764 -rw-------  1 root root  5896992 Dec 16 19:55 vmlinuz-3.13.0-44-generic
 5764 -rw-------  1 root root  5898624 Jan 15 15:46 vmlinuz-3.13.0-45-generic


```

---

### Post by watchpocket on 2015-02-18
> **Bashing-om said:**
> 
let's look:
```

ls -al /
ls -al /boot

```
where I expect only 4 symlinks (2 current - vmlinuz & initrd.img and 2 for XXX.old - ) that they point to valid files in '/boot' .


And in Trusty:```
~$ ls -la /
total 108
drwxr-xr-x  24 root root  4096 Feb 17 02:09 .
drwxr-xr-x  24 root root  4096 Feb 17 02:09 ..
drwxr-xr-x   2 root root  4096 Feb 17 14:03 bin
drwxr-xr-x   3 root root  4096 Feb 16 17:40 boot
drwxrwxr-x   2 root root  4096 Jan 19 00:27 cdrom
drwxr-xr-x  15 root root  4220 Feb 18 14:06 dev
drwxr-xr-x 140 root root 12288 Feb 18 14:06 etc
drwxr-xr-x   3 root root  4096 Jan 19 00:27 home
lrwxrwxrwx   1 root root    33 Jan 30 15:14 initrd.img -> boot/initrd.img-3.13.0-45-generic
drwxr-xr-x  24 root root  4096 Feb 17 02:09 lib
drwxr-xr-x   2 root root  4096 Feb 17 02:09 lib64
drwxr-xr-x   2 root root  4096 Feb 17 02:09 libx32
drwx------   2 root root 16384 Jan 19 00:24 lost+found
drwxr-xr-x   3 root root  4096 Jan 19 13:59 media
drwxr-xr-x   2 root root  4096 Apr 10  2014 mnt
drwxr-xr-x   3 root root  4096 Jan 25 00:59 opt
dr-xr-xr-x 191 root root     0 Feb 18 14:06 proc
drwx------   8 root root  4096 Feb 17 13:30 root
drwxr-xr-x  24 root root   840 Feb 18 14:07 run
drwxr-xr-x   2 root root 12288 Feb 12 21:49 sbin
drwxr-xr-x   2 root root  4096 Nov  5 08:16 srv
dr-xr-xr-x  13 root root     0 Feb 18 14:06 sys
drwxrwxrwt   6 root root  4096 Feb 18 14:06 tmp
drwxr-xr-x  12 root root  4096 Feb 17 02:09 usr
drwxr-xr-x  13 root root  4096 Nov 11 10:11 var
lrwxrwxrwx   1 root root    30 Jan 30 15:14 vmlinuz -> boot/vmlinuz-3.13.0-45-generic
~$ 
~$ ls -la /boot
total 29604
drwxr-xr-x  3 root root     4096 Feb 16 17:40 .
drwxr-xr-x 24 root root     4096 Feb 17 02:09 ..
-rw-r--r--  1 root root  1164967 Jan 13 15:12 abi-3.13.0-45-generic
-rw-r--r--  1 root root   165748 Jan 13 15:12 config-3.13.0-45-generic
drwxr-xr-x  5 root root     4096 Feb 17 13:34 grub
-rw-r--r--  1 root root 19217318 Feb 12 01:16 initrd.img-3.13.0-45-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3389258 Jan 13 15:12 System.map-3.13.0-45-generic
-rw-------  1 root root  5814112 Jan 13 15:12 vmlinuz-3.13.0-45-generic
~$ 
```

If something is wrong here, it may be why I'm seeing that half the time when I log into Trusty (Ubuntu-MATE) I get to the logo (before the login screen) with 5 dots below it that turn from green to white, left to right. Half the time after the dots turn white, it hangs and I have to re-boot with the reset button.  

(The code above is looking at the root dir from in the terminal. The only place where I see "5.5 MiB Link to unknown" is beside the vmlinuz file, in the "Type" column, when looking at the root dir in the Ubuntu-MATE "Caja" file-viewer (MATE's equivalent of Nautilus.  There are other files in other dirs that the file-viewer also seems not to recognize their type and so has "unknown" for, e.g. a binary file or any other kind of file it seems not to recognize.)

---

### Post by Cavsfan on 2015-02-18
> **watchpocket said:**
> In Precise: ```
--> ls -la /  
total 116
 4 drwxr-xr-x  26 root root  4096 Feb 11 01:22 ./
 4 drwxr-xr-x  26 root root  4096 Feb 11 01:22 ../
 4 drwxr-xr-x   2 root root  4096 Jul 18  2014 .rpmdb/
 4 drwxr-xr-x   2 root root  4096 Feb 11 01:22 bin/
 4 drwxr-xr-x   4 root root  4096 Feb 16 18:56 boot/
 4 drwxr-xr-x   2 root root  4096 Jan 11  2014 cdrom/
 0 drwxr-xr-x  15 root root  4380 Feb 18 13:28 dev/
12 drwxr-xr-x 152 root root 12288 Feb 18 13:28 etc/
 4 drwxr-xr-x   3 root root  4096 Jan 11  2014 home/
 0 lrwxrwxrwx   1 root root    33 Feb 11 01:22 initrd.img -> boot/initrd.img-3.13.0-45-generic
 0 lrwxrwxrwx   1 root root    33 Jan 16 14:30 initrd.img.old -> boot/initrd.img-3.13.0-44-generic
 4 drwxr-xr-x  26 root root  4096 Feb 16 18:32 lib/
 4 drwxr-xr-x   2 root root  4096 Feb  3 14:16 lib32/
 4 drwxr-xr-x   2 root root  4096 Feb  3 14:16 lib64/
16 drwx------   2 root root 16384 Jan 11  2014 lost+found/
 4 drwxr-xr-x   2 root root  4096 Feb 16 22:24 media/
 4 drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt/
 4 drwxr-xr-x   4 root root  4096 Jul  6  2014 opt/
 0 dr-xr-xr-x 201 root root     0 Feb 18 13:27 proc/
 4 drwx------  13 root root  4096 Feb 16 18:32 root/
 0 drwxr-xr-x  21 root root   820 Feb 18 13:28 run/
12 drwxr-xr-x   2 root root 12288 Feb 11 22:29 sbin/
 4 drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux/
 4 drwxr-xr-x   2 root root  4096 Aug 20  2013 srv/
 0 dr-xr-xr-x  13 root root     0 Feb 18 13:27 sys/
 4 drwxrwxrwt   8 root root  4096 Feb 18 13:48 tmp/
 4 drwxr-xr-x  11 root root  4096 Dec 14 18:48 usr/
 4 drwxr-xr-x  13 root root  4096 Feb 17 01:05 var/
 0 lrwxrwxrwx   1 root root    30 Feb 11 01:22 vmlinuz -> boot/vmlinuz-3.13.0-45-generic
 0 lrwxrwxrwx   1 root root    30 Jan 16 14:30 vmlinuz.old -> boot/vmlinuz-3.13.0-44-generic

--> lf /boot    
total 58368
    4 drwxr-xr-x  4 root root     4096 Feb 16 18:56 ./
    4 drwxr-xr-x 26 root root     4096 Feb 11 01:22 ../
 3444 -rw-------  1 root root  3525141 Dec 16 19:55 System.map-3.13.0-44-generic
 3444 -rw-------  1 root root  3525572 Jan 15 15:46 System.map-3.13.0-45-generic
 1140 -rw-r--r--  1 root root  1164720 Dec 16 19:55 abi-3.13.0-44-generic
 1140 -rw-r--r--  1 root root  1164967 Jan 15 15:46 abi-3.13.0-45-generic
  164 -rw-r--r--  1 root root   165757 Dec 16 19:55 config-3.13.0-44-generic
  164 -rw-r--r--  1 root root   165757 Jan 15 15:46 config-3.13.0-45-generic
    4 drwxr-xr-x  3 root root     4096 Feb 16 18:56 extlinux/
   12 drwxr-xr-x  3 root root    12288 Feb 16 19:03 grub/
18484 -rw-r--r--  1 root root 18920653 Jan 16 14:31 initrd.img-3.13.0-44-generic
18484 -rw-r--r--  1 root root 18927341 Feb 16 18:34 initrd.img-3.13.0-45-generic
  176 -rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
  176 -rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
 5764 -rw-------  1 root root  5896992 Dec 16 19:55 vmlinuz-3.13.0-44-generic
 5764 -rw-------  1 root root  5898624 Jan 15 15:46 vmlinuz-3.13.0-45-generic


```

> **watchpocket said:**
> And in Trusty:```
~$ ls -la /
total 108
drwxr-xr-x  24 root root  4096 Feb 17 02:09 .
drwxr-xr-x  24 root root  4096 Feb 17 02:09 ..
drwxr-xr-x   2 root root  4096 Feb 17 14:03 bin
drwxr-xr-x   3 root root  4096 Feb 16 17:40 boot
drwxrwxr-x   2 root root  4096 Jan 19 00:27 cdrom
drwxr-xr-x  15 root root  4220 Feb 18 14:06 dev
drwxr-xr-x 140 root root 12288 Feb 18 14:06 etc
drwxr-xr-x   3 root root  4096 Jan 19 00:27 home
lrwxrwxrwx   1 root root    33 Jan 30 15:14 initrd.img -> boot/initrd.img-3.13.0-45-generic
drwxr-xr-x  24 root root  4096 Feb 17 02:09 lib
drwxr-xr-x   2 root root  4096 Feb 17 02:09 lib64
drwxr-xr-x   2 root root  4096 Feb 17 02:09 libx32
drwx------   2 root root 16384 Jan 19 00:24 lost+found
drwxr-xr-x   3 root root  4096 Jan 19 13:59 media
drwxr-xr-x   2 root root  4096 Apr 10  2014 mnt
drwxr-xr-x   3 root root  4096 Jan 25 00:59 opt
dr-xr-xr-x 191 root root     0 Feb 18 14:06 proc
drwx------   8 root root  4096 Feb 17 13:30 root
drwxr-xr-x  24 root root   840 Feb 18 14:07 run
drwxr-xr-x   2 root root 12288 Feb 12 21:49 sbin
drwxr-xr-x   2 root root  4096 Nov  5 08:16 srv
dr-xr-xr-x  13 root root     0 Feb 18 14:06 sys
drwxrwxrwt   6 root root  4096 Feb 18 14:06 tmp
drwxr-xr-x  12 root root  4096 Feb 17 02:09 usr
drwxr-xr-x  13 root root  4096 Nov 11 10:11 var
lrwxrwxrwx   1 root root    30 Jan 30 15:14 vmlinuz -> boot/vmlinuz-3.13.0-45-generic
~$ 
~$ ls -la /boot
total 29604
drwxr-xr-x  3 root root     4096 Feb 16 17:40 .
drwxr-xr-x 24 root root     4096 Feb 17 02:09 ..
-rw-r--r--  1 root root  1164967 Jan 13 15:12 abi-3.13.0-45-generic
-rw-r--r--  1 root root   165748 Jan 13 15:12 config-3.13.0-45-generic
drwxr-xr-x  5 root root     4096 Feb 17 13:34 grub
-rw-r--r--  1 root root 19217318 Feb 12 01:16 initrd.img-3.13.0-45-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3389258 Jan 13 15:12 System.map-3.13.0-45-generic
-rw-------  1 root root  5814112 Jan 13 15:12 vmlinuz-3.13.0-45-generic
~$ 
```

If something is wrong here, it may be why I'm seeing that half the time when I log into Trusty (Ubuntu-MATE) I get to the logo (before the login screen) with 5 dots below it that turn from green to white, left to right. Half the time after the dots turn white, it hangs and I have to re-boot with the reset button.

I don't see anything wrong here. You only customized one install right? Where you entered **sudo grub-install /dev/sdX** (X being a or b for which hard drive it is 1 or 2).

Could you post the contents of 06_custom from the system that grub is customized on like this **cat /etc/grub.d/06_custom**

Also **cat /etc/fstab** and **sudo blkid** as well?

---

### Post by Bashing-om on 2015-02-18
watchpocket; Welp; ....

Precise install looks good .
The trusty install, ya took out the backup kernel, -44, I honestly do not know that to be the factor or not. Let's await the next kernel update/install and see what results ( or if ya want can install the -44 kernel) ===>>
But, I think that is a subject for a new thread. Let's not deviate too far from Cavsfan's topic !
For now, rather then doing that bad bad bad hard reset:
The elephants !
[http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)
[http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes](http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes)
My sequence ctl+alt+sysrq+ rseiub ( Raising Skinny _Elephants_ Is Utterly Boring); others exist. To reboot, replace the 'b' with 'o' to turn Off.

[INDENT][INDENT]if I knew everything
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2015-02-18
Will post more late tonight or tomorrow, time to shut down and get into my office where I can only post from a windows machine. Meanwhile see recent edit at the bottom of my previous post, thanks.

---

### Post by Cavsfan on 2015-02-18
> **watchpocket said:**
> Will post more late tonight or tomorrow, time to shut down and get into my office where I can only post from a windows machine. Meanwhile see recent edit at the bottom of my previous post, thanks.

I am in Trusty and my kernel links look the same as yours:
```
cavsfan@cavsfan-desktop:/$ ls -l | grep -e "initrd" -e "vmlinuz"
lrwxrwxrwx   1 root root    33 Jan 30 17:41 initrd.img -> boot/initrd.img-3.13.0-45-generic
lrwxrwxrwx   1 root root    33 Jan 13 15:07 initrd.img.old -> boot/initrd.img-3.13.0-44-generic
lrwxrwxrwx   1 root root    30 Jan 30 17:41 vmlinuz -> boot/vmlinuz-3.13.0-45-generic
lrwxrwxrwx   1 root root    30 Jan 13 15:07 vmlinuz.old -> boot/vmlinuz-3.13.0-44-generic
```

```
cavsfan@cavsfan-desktop:/$ cd /boot
cavsfan@cavsfan-desktop:/boot$ ls -l | grep -e "initrd" -e "vmlinuz"
-rw-r--r-- 1 root root 19203798 Jan 13 15:21 initrd.img-3.13.0-44-generic
-rw-r--r-- 1 root root 19213826 Jan 30 17:43 initrd.img-3.13.0-45-generic
-rw------- 1 root root  5814496 Dec 15 20:17 vmlinuz-3.13.0-44-generic
-rw------- 1 root root  5814112 Jan 13 15:12 vmlinuz-3.13.0-45-generic
```

I see no need for you to re-install the 3.13.0-44-generic kernel and most probably you can't do it if you wanted to.
But if you did, it would become the one you boot from, which is not what you want. Newer kernels have updates in them such as security fixes etc.

It is the latest kernel that is installed that you will boot from and not the highest numbered kernel. 

So, the question will be in which Ubuntu Precise or Trusty that grub is installed on. 
Also the contents of **sudo blkid** and **06_custom** on that system as well as the **/etc/fstab** files on both systems.

But, when you do that hard reset to restart your computer, then are you able to get into Trusty Mate normally?

---

### Post by watchpocket on 2015-02-18
> **Cavsfan said:**
> I don't see anything wrong here. You only customized one install right?

That's right.  I did not touch (and have never tried to modify) my Precise's grub, which is version 1.99 "legacy" grub.  The other day, for just a second, I found it alarming that, while I was in Trusty's grub, at the grub command-line, I entered "exit" and was immediately put into the older 1.99 purple-backgrounded Precise grub menu.  But then I thought, "what did I expect?  I just ***exited *** Trusty's grub (the newer "2.02~beta2-9ubuntu1" grub)*. *

Just to say again that the word "unknown" only appeared under "type" in the file-viewer, not when looking at the same directories in the terminal.

> Where you entered **sudo grub-install /dev/sdX** (X being a or b for which hard drive it is 1 or 2).

Oh, it was definitely on dev/sda where Trusty is.

> Could you post the contents of 06_custom from the system that grub is customized on like this **cat /etc/grub.d/06_custom**

Also **cat /etc/fstab** and **sudo blkid** as well?

I'll do this by or before 3:50 tomorrow (Thursday) afternoon.

---

### Post by watchpocket on 2015-02-18
> **Bashing-om said:**
> 
The trusty install, ya took out the backup kernel, -44,

That was deliberate.

> I honestly do not know that to be the factor or not.

I'm guessing no, or Cavsfan wouldn't have OK'd it.

>  . . . or if ya want can install the -44 kernel) ===>>

Mm, I probably wouldn't do that.  I do have both the -45 and -44 kernels on Precise.

> For now, rather then doing that bad bad bad hard reset:
The elephants !
[http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses)
[http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes](http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes)
My sequence ctl+alt+sysrq+ rseiub ( Raising Skinny _Elephants_ Is Utterly Boring); others exist. To reboot, replace the 'b' with 'o' to turn Off.

***I can't believe I've never heard of this until now.***  Thank you! 

No more using re-set -- I always got a vaguely bad feeling having to do that.

---

### Post by Bashing-om on 2015-02-18
watchpocket; :)

All good.
> 
I can't believe I've never heard of this until now. Thank you! 

See what hanging out in the right places gets you .

[INDENT][INDENT]The Forum
[INDENT][INDENT][INDENT]knowledge abounds
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2015-02-18
> **Cavsfan said:**
> It is the latest kernel that is installed that you will boot from and not the highest numbered kernel.

Good to know.

> So, the question will be in which Ubuntu Precise or Trusty that grub is installed on.

New grub (v2.02) is on Trusty. That's the one I modified.  Old grub (v1.99) is on Precise.

> Also the contents of **sudo blkid** and **06_custom** on that system as well as the **/etc/fstab** files on both systems.

Will post asap (tomorrow -- Thursday -- afternoon).

> But, when you do that hard reset to restart your computer, then are you able to get into Trusty Mate normally?

Yes.  But the freeze is happening almost every other boot-in (to Trusty, not Precise). Doing a re-set login after the freeze does not produce a freeze again. Only when booting normally. I'd say about every third or fourth attempt to boot.

---

### Post by watchpocket on 2015-02-18
> **Bashing-om said:**
> 
My sequence ctl+alt+sysrq+ rseiub ( Raising Skinny _Elephants_ Is Utterly Boring); others exist. 

But why <ctl> along with the <alt> and <SysRq> keys?  The wikipedia entry you linked to says:

[LIST=1]
[*][COLOR=#0000cd][I]Hold down the Alt and SysRq (Print Screen) keys.
[/I][/COLOR] 
[*][COLOR=#0000cd]*While holding those down, type the following keys in order, several seconds apart: REISUB*[/COLOR] 
[*][COLOR=#0000cd]*Computer should reboot.*[/COLOR] 
[/LIST]
 and nothing about holding down <ctl>.  
Also, any particular reason for the order*** r-s-e-i-u-b*** instead of*** r-e-i-s-u-b*** ?  Is it just that you prefer the "Raising Skinny Elephants Is Utterly Boring" as a mnemonic device as opposed to remembering that "reisub" is "busier" spelled backwards?

---

### Post by watchpocket on 2015-02-19
> **Cavsfan said:**
> 
Also the contents of **sudo blkid** and **06_custom** on that system as well as the **/etc/fstab** files on both systems.

First, here is the output of all three of the above commands entered in **Trusty**:
```
~$ ***sudo blkid***
/dev/sda1: LABEL="UbuntuMATE-14.04" UUID="1742aa67-b8ce-45d2-94ca-05e3579f7e2f" TYPE="ext4" 
/dev/sda2: UUID="a88c33fd-88b5-43b2-92f6-457430d206fd" TYPE="swap" 
/dev/sdb1: LABEL="Ubuntu-12.04.5" UUID="4d4f7665-f633-4409-82f9-af43d0143823" TYPE="ext4" 
/dev/sdb2: UUID="106dae89-e837-4063-9f9c-bcdeae4b2d5a" TYPE="swap" 
/dev/sdc1: LABEL="WeirdBeard" UUID="c801726e-7a01-4963-989a-38482e6658cf" TYPE="ext4"
``` 

```

~$ ***cat /etc/grub.d/06_custom***
#!/bin/sh
echo 1>&2 "Adding Ubuntu-MATE 14.04 (Trusty Tahr) and Ubuntu 12.04 (Precise Pangolin)"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu-MATE 14.04 (Trusty Tahr)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "Ubuntu-MATE 14.04 (Trusty Tahr) (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}

```

```
~$ ***cat /etc/fstab***
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=106dae89-e837-4063-9f9c-bcdeae4b2d5a none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=a88c33fd-88b5-43b2-92f6-457430d206fd none            swap    sw              0       0

```



Now here are the contents of my ***/etc/fstab*** file on **Precise**:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4d4f7665-f633-4409-82f9-af43d0143823 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=106dae89-e837-4063-9f9c-bcdeae4b2d5a none            swap    sw              0       0

```

Thanks for offering to look at these.

---

### Post by Cavsfan on 2015-02-19
> **watchpocket said:**
> First, here is the output of all three of the above commands entered in **Trusty**:
```
~$ ***sudo blkid***
/dev/sda1: LABEL="UbuntuMATE-14.04" UUID="1742aa67-b8ce-45d2-94ca-05e3579f7e2f" TYPE="ext4" 
/dev/sda2: UUID="a88c33fd-88b5-43b2-92f6-457430d206fd" TYPE="swap" 
/dev/sdb1: LABEL="Ubuntu-12.04.5" UUID="4d4f7665-f633-4409-82f9-af43d0143823" TYPE="ext4" 
/dev/sdb2: UUID="106dae89-e837-4063-9f9c-bcdeae4b2d5a" TYPE="swap" 
/dev/sdc1: LABEL="WeirdBeard" UUID="c801726e-7a01-4963-989a-38482e6658cf" TYPE="ext4"
``` 

```

~$ ***cat /etc/grub.d/06_custom***
#!/bin/sh
echo 1>&2 "Adding Ubuntu-MATE 14.04 (Trusty Tahr) and Ubuntu 12.04 (Precise Pangolin)"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu-MATE 14.04 (Trusty Tahr)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "Ubuntu-MATE 14.04 (Trusty Tahr) (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}

```

```
~$ ***cat /etc/fstab***
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=1742aa67-b8ce-45d2-94ca-05e3579f7e2f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=106dae89-e837-4063-9f9c-bcdeae4b2d5a none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=a88c33fd-88b5-43b2-92f6-457430d206fd none            swap    sw              0       0

```



Now here are the contents of my ***/etc/fstab*** file on **Precise**:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4d4f7665-f633-4409-82f9-af43d0143823 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=106dae89-e837-4063-9f9c-bcdeae4b2d5a none            swap    sw              0       0

```

Thanks for offering to look at these.

You really only need one swap file for all of your Ubuntu systems. 
Actually you do not even need one if you have at least 4GB RAM and do not wish to use the hibernate feature.
I don't really need one myself but I set up a 1GB swap file that I use for all 4 systems (12.04, 14.04, 15.04 and Mint 17) 

The first thing on 14.04 Mate is to edit fstab **gksudo gedit /etc/fstab**
Change the UUID for sdb1 and the swap file on sdb2 to match the output of blkid as shown in red.
[U]Just copy and paste the contents below into your **/etc/fstab** file on 14.04 Mate and save it.
[/U]
This is the most likely cause of your problems booting into Mate.

Or decide which single swap file you want to keep and make the UUID match the one you choose on the /etc/fstab file on both 14.04 Mate and Precise 12.04.
But since you have them on two different drives I guess one on each is fine. Just remember that if you change any partitions fstab has to be edited.

```
~$ ***cat /etc/fstab***
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=[COLOR=#ff0000]4d4f7665-f633-4409-82f9-af43d0143823[/COLOR] /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=[COLOR=#FF0000]106dae89-e837-4063-9f9c-bcdeae4b2d5a[/COLOR] none            swap    sw              0       0

```

Your /etc/grub.d/06_custom file on 14.04 Mate should look like this and you can copy this into that file:

```

~$ ***cat /etc/grub.d/06_custom***
#!/bin/sh
echo 1>&2 "Adding Ubuntu-MATE 14.04 (Trusty Tahr) and Ubuntu 12.04 (Precise Pangolin)"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu-MATE 14.04 (Trusty Tahr)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}
menuentry "Ubuntu-MATE 14.04 (Trusty Tahr) (Recovery Mode)" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro quiet splash
        initrd /initrd.img
}
menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro single
        initrd /initrd.img
}

```

You could put Precise first to keep them in numerical order but that is up to you and you would have to edit  /etc/default/grub if you wanted to change default systems.
Of course don't forget **sudo update-grub** after all of the edits are completed.

I would be best if you could edit the Precise /etc/fstab file from Trusty Mate. Just right click on the file and then click copy and paste that into terminal.
It will look something like this: **gksudo gedit [COLOR=#ff0000]file://[/COLOR]/media/cavsfan/Precise/etc/fstab** just make sure you remove the characters in red.
Or if you can't get that to work see if you can boot into Precise and do it there.

_Copy the contents below into the file on Precise as both UUIDs are wrong at present:_

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=[COLOR=#ff0000]1742aa67-b8ce-45d2-94ca-05e3579f7e2f[/COLOR] /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=[COLOR=#ff0000]a88c33fd-88b5-43b2-92f6-457430d206fd[/COLOR] none            swap    sw              0       0

```

Once these steps are accomplished you should have no need for **/etc/grub.d/30_os-prober** to be executable and you will have a truly custom grub. :)

Just make sure you can boot into both Trusty and Precise from the custom lines first.

---

### Post by watchpocket on 2015-02-19
I've made no changes just yet --I have a couple of questions before I go ahead with the changes.  

> **Cavsfan said:**
> You really only need one swap file for all of your Ubuntu systems.

Is that one swap file best put on my Trusty drive or my Precise drive? Or does it not matter which? 

 I have 8GB of ram.  I never use the hibernate. Right now I have a 20GB swap partition on each of the two drives. Each drive is a one-terabyte drive,  and each has only one ext4 partition, plus (at the moment) the one 20GB swap partition.

Since I've recently read that the old rule of having swapspace of just over double your amount of ram is obsolete (and was true mainly in the days when much smaller amounts of ram were used), I'll most likely keep just one swapfile for use with all 3 of my drives (per your suggestion) and reduce its size from 20GB to 10GB or even 9GB.  (I previously had assumed that every drive had to have its own swap partition, or swap files.)

But -- what about the occasional situation where you've got Google Earth and 2 or 3 other super-hog programs open? Though it might happen very infrequently, my entire 8GB of ram *could* get filled up on that rare occasion, no?  And I'd be glad I have that 9 or 10GB of ram, yes?  Or maybe this is all just overkill.

Also, I have the **Swapspace** "Dynamic swapspace manager" program (v. 1.10-4) installed on both drives (on the advice of a post by oldfred that I can't find that discusses the wisdom of having one large partition on your drive and using this program with little or no swap partition space).  I've sometimes wondered since installing it whether that program might interfere in any way, or make irrelevant, my allotted swap partitions.

> The first thing on 14.04 Mate is to edit fstab **gksudo gedit /etc/fstab**

First off, you're saying that I need to change ***both*** my **Trusty**[COLOR=#0000cd] /etc/fstab[/COLOR] file _***and***_ my **Precise** [COLOR=#0000cd]/etc/fstab[/COLOR] file, per your examples, correct?

> Change the UUID for sdb1 and the swap file on sdb2 to match the output of blkid as shown in red.

Just to be clear, the Precise drive UUID ends with **823**, and the UUID for the Precise **swap partition** ends in **d5a**, according to the output of ***sudo blkid*** , when I enter that command in Trusty. 

What puzzles me a bit is that it looks to me from the examples as if you're saying to put the **Precise** UUID and the **Precise** **swap** UUID into the [COLOR=#0000cd]/etc/fstab[/COLOR] file in **Trusty**.

Likewise, you say to put what appears to me to be the UUIDs for Trusty into the **Precise** [COLOR=#0000cd]/etc/fstab[/COLOR] file. 

I just want to double-check that this is correct, and that it shouldn't be the other way around, exactly the reverse.  

> Or decide which single swap file you want to keep and make the UUID  match the one you choose on the /etc/fstab file on both 14.04 Mate and  Precise 12.04.

This is where I'd expect that in the Trusty [COLOR=#0000cd]/etc/fstab[/COLOR] I'd have the UUID for the Trusty drive's main partition (sda1) as shown in ***blkid*** (which UUID ends with **e2f**) along with the UUID of the one swap partition I decide to keep (say the one the Precise drive at sdb2, which UUID ends with **d5a**).

And that in the Precise [COLOR=#0000cd]/etc/fstab[/COLOR], I'd have the UUID for the Precise drive's main partition (sdb1) as shown in ***blkid*** (which UUID ends with **823**) along with the **same **swap partition UUID as above (the one ending with **d5a**).  Does that make sense, or do I have it backwards with respect to the (non-swap) UUIDs?

> But since you have them on two different drives I guess one on each is  fine. 

If I only need one swap partition, and it will work with all 3 of my drives, I'll (a) get rid of the other swap partition; and (b) reduce the size of the one I keep from the un-needed 20GB size to something like 9 or 10GB (which I'm beginning to gather that this may also be an unnecessarily large swap-partition size).

Thanks for your indulgence.

---

### Post by Cavsfan on 2015-02-19
> **watchpocket said:**
> I've made no changes just yet --I have a couple of questions before I go ahead with the changes.  

[QUOTE=Cavsfan;13231341]You really only need one swap file for all of your Ubuntu systems.

Is that one swap file best put on my Trusty drive or my Precise drive? Or does it not matter which? 

 I have 8GB of ram.  I never use the hibernate. Right now I have a 20GB swap partition on each of the two drives. Each drive is a one-terabyte drive,  and each has only one ext4 partition, plus (at the moment) the one 20GB swap partition.

Since I've recently read that the old rule of having swapspace of just over double your amount of ram is obsolete (and was true in the days when much smaller amounts of ram were used), I'll most likely keep just one swapfile for use with both drives (per your suggestion) and reduce its size from 20GB to 10GB or even 9GB.  (I previously had assumed that every drive had to have its own swap partition, or swap files.)

But -- what about the occasional situation where you've got Google Earth and 2 or 3 other super-hog programs open? Though it might happen very infrequently, my entire 8GB of ram *could* get filled up on that rare occasion, no?  And I'd be glad I have that 9 or 10GB of ram, yes?  Or maybe this is all just overkill.

Also, I have the **Swapspace** "Dynamic swapspace manager" program (v. 1.10-4) installed on both drives (on the advice of a post by oldfred that I can't find that discusses the wisdom of having one large partition on your drive and using this program with little or no swap partition space).  I've sometimes wondered since installing it whether that program might interfere in any way, or make irrelevant, my alloted swap partitions.

> The first thing on 14.04 Mate is to edit fstab **gksudo gedit /etc/fstab**

First off, you're saying that I need to change ***both*** my **Trusty**[COLOR=#0000cd] /etc/fstab[/COLOR] file _***and***_ my **Precise** [COLOR=#0000cd]/etc/fstab[/COLOR] file, per your examples, correct?

> Change the UUID for sdb1 and the swap file on sdb2 to match the output of blkid as shown in red.                      

Just to be clear, the Precise drive UUID ends with **823**, and the UUID for the Precise **swap partition** ends in **d5a**, according to the output of ***sudo blkid*** , when I enter that command in Trusty. 

What puzzles me a bit is that it looks to me as if you're saying to put the **Precise** UUID and the **Precise** **swap** UUID into the [COLOR=#0000cd]/etc/fstab[/COLOR] file in **Trusty**.

Likewise, you say to put what appears to me to be the UUIDs for Trusty into the **Precise** [COLOR=#0000cd]/etc/fstab[/COLOR] file. 

I just want to double-check that this is correct, and that it shouldn't be the other way around, exactly the reverse.

Thanks for your indulgence.[/QUOTE]

I believe that is exactly what I am saying: copy and paste the contents of the two fstabs that I corrected for you into the files and copy and past the 06_custom file I corrected and you shall be right as rain as the lady on The Matrix once said. :p 
Your current fstab files are exactly backwards. Look at the output of blkid and compare that to your fstab files and you will see.

The **/etc/fstab** files do not get updated when you move stuff around and that is why these changes are needed.
The **sudo blkid** output does not lie and is accurate. 
An even better way to use that command is **sudo blkid -c /dev/null -o list** but you will need to resize terminal not full but bigger than normal small size.

But that's not really important. What is important is that the UUIDs in fstab match the UUIDs from blkid.
This is what I got from your blkid:
```
[COLOR=#ff0000]/dev/sda1: UbuntuMATE-14.04 UUID="1742aa67-b8ce-45d2-94ca-05e3579f7e2f" 
/dev/sda2: UUID="a88c33fd-88b5-43b2-92f6-457430d206fd" TYPE="swap" 

/dev/sdb1: Ubuntu-12.04.5 UUID="4d4f7665-f633-4409-82f9-af43d0143823" 
/dev/sdb2: UUID="106dae89-e837-4063-9f9c-bcdeae4b2d5a" TYPE="swap" [/COLOR]
```

So this, what you see in red is correct while your fstab files are not. 
You can double check again if you want but I spent many hours today checking and double checking myself and I believe I have it right.

I am slow and do not like making mistakes so be sure you do double check my results but the fstab records are lying to you and blkid is never wrong.
I just double and triple checked and I believe my fstabs and 06_custom files are all correct so you can just copy and paste when you feel satisfied that I am correct.

I know that the Precise code is correct as I copied it from my 06_custom file and changed it to point to drive 2 partition 1.

And about the swap files. I feel that would be better suited for a new thread under general help. I'm not going to get into that on this wiki thread.

But, do let me know if this fixes your problems booting into both Trusty and Precise from the custom entries.

---

### Post by watchpocket on 2015-02-19
> **Cavsfan said:**
> [ . . . ] but I spent many hours today checking and double checking myself and I believe I have it right.

And I do appreciate that.  

I'm sure you're right, and I will make the changes tonight when I get home.

The source of my confusion was that I simply overlooked or wasn't paying attention to these comment lines in the fstab files telling me what's what & where it belongs:
```

# / was on /dev/sdb1 during installation 
# swap was on /dev/sdb2 during installation

```
Apologies for that.  I will let you know if the booting problem is fixed.

---

### Post by watchpocket on 2015-02-20
So I've made the changes and, so far at least, all appears well with booting (I only had the hangs booting into Trusty, not Precise).  I'll know for sure in a day or two.

The problem is that from the minute I did ***sudo upgrade-grub*** after changing the Trusty fstab file, I no longer had ( and do not now have) a way to mount Precise from Trusty or vice-versa.
I saw right away that in the "Places" menu, the item "Ubuntu 12.04" was missing.  Same thing when logged into Precise, "Ubuntu 14.04" is missing from the Precise "Places" menu.  My third drive of course is still listed in Places.

Looking in gparted, the keys in **/dev/sdb** are beside **sdb2** "linux-swap", instead of beside **sdb1**, the ext4 partition, where in **sda** and **sdc** the keys are beside the ext4 partition (though sdc of course doesn't have a swap partition).

Looking in the Disks util, it shows /dev/sda1 as mounted and /dev/sda2 (swap) as "Not Active".  And it shows /dev/sdb1 as "Not Mounted" and /dev/sdb2 swap as "Active."

Here is the trusty /etc/fstab file, I cut/pasted exactly:

```

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=4d4f7665-f633-4409-82f9-af43d0143823 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=106dae89-e837-4063-9f9c-bcdeae4b2d5a none            swap    sw              0       0

```It seems I need to take another step with this to finish. Thanks.

---

### Post by Cavsfan on 2015-02-20
> **watchpocket said:**
> So I've made the changes and, so far at least, all appears well with booting (I only had the hangs booting into Trusty, not Precise).  I'll know for sure in a day or two.

The problem is that from the minute I did ***sudo upgrade-grub*** after changing the Trusty fstab file, I no longer had ( and do not now have) a way to mount Precise from Trusty or vice-versa.
I saw right away that in the "Places" menu, the item "Ubuntu 12.04" was missing.  Same thing when logged into Precise, "Ubuntu 14.04" is missing from the Precise "Places" menu.  My third drive of course is still listed in Places.

Looking in gparted, the keys in **/dev/sdb** are beside **sdb2** "linux-swap", instead of beside **sdb1**, the ext4 partition, where in **sda** and **sdc** the keys are beside the ext4 partition (though sdc of course doesn't have a swap partition).

Looking in the Disks util, it shows /dev/sda1 as mounted and /dev/sda2 (swap) as "Not Active".  And it shows /dev/sdb1 as "Not Mounted" and /dev/sdb2 swap as "Active."

Here is the trusty /etc/fstab file, I cut/pasted exactly:

```

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=4d4f7665-f633-4409-82f9-af43d0143823 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=106dae89-e837-4063-9f9c-bcdeae4b2d5a none            swap    sw              0       0

```It seems I need to take another step with this to finish. Thanks.

You are welcome. I'm a little slow these days so I wanted to make sure I was telling you correctly about the fstabs. I have no idea why the other drive would dis-mount.

I have only a 500GB drive and a 1TB USB drive which both mount when I boot into any of my Linux systems every time.
Here is my gparted from Precise sda:

[ATTACH=CONFIG]260108[/ATTACH]

sdb:

[ATTACH=CONFIG]260109[/ATTACH] 

Let me know how it turns out.

---

### Post by watchpocket on 2015-02-20
Since I do need the drive I'm not logged into to mount, for right now I may temporarily revert to my previous fstabs.  I'm going to dig further into the overall problem, or rather, the specific problem of the drives not mounting, and ask about this in other forums and look around on stack exchange, ask ubuntu, etc.

You've gone beyond the call of duty and I'm not going to keep taking up your time.  I've learned a lot and really appreciate it.  Going forward I'll continue to look at this thread for learning more about grub. Thanks again for all the help. :)

---

### Post by Cavsfan on 2015-02-20
> **watchpocket said:**
> Since I do need the drive I'm not logged into to mount, for right now I may temporarily revert to my previous fstabs.  I'm going to dig further into the overall problem, or rather, the specific problem of the drives not mounting, and ask about this in other forums and look around on stack exchange, ask ubuntu, etc.

You've gone beyond the call of duty and I'm not going to keep taking up your time.  I've learned a lot and really appreciate it.  Going forward I'll continue to look at this thread for learning more about grub. Thanks again for all the help. :)

OK good luck! However, your fstabs should match the UUIDs in the output of blkid. I think the problem is more with the reason both drives do not automatically mount.
I don't see how correcting the fstab files would cause that but, I hope you find your solution.

I gave it my best shot and you are welcome! :)

---

### Post by Cavsfan on 2015-03-07
Installed Vivid Mate 15.04 and the first picture I found worked like a charm.
Booting with systemd as default with the option to use upstart.

I could have used better colors but they'll do for the time being.

[[IMG]http://en.zimagez.com/miniature/20150307081900.jpg[/IMG]]("http://en.zimagez.com/zimage/20150307081900.php")

That is with magenta for normal, yellow for menu and red for highlight menu. 
I'll probably change them but they look fairly good in the mean time. 

Pink is for breast cancer awareness anyway and I like magenta. ;)

---

### Post by Cavsfan on 2015-04-03
Decided to do new installs and get my disk in order. 

I have Windows 7, Linux Mint 17.1 and Ubuntu Trusty Mate 14.04 on physical partitions.

The swap file and a 15 GB partition for developmental releases (currently Vivid Mate 15.05) are on logical partitions.

[[IMG]http://en.zimagez.com/miniature/20150403092541.jpg[/IMG]]("http://en.zimagez.com/zimage/20150403092541.php")

I went with these colors:

```
echo " set color_normal=red/black"
echo " set menu_color_normal=cyan/black"
echo " set menu_color_highlight=light-cyan/black"
```

---

### Post by Cavsfan on 2015-04-19
I'm hoping to simplify this wiki a lot when Vivid Vervet 15.04 is released by cutting out a lot of extraneous things that should not be in it. I realize I got a little too wordy in many places.

Vivid Vervet 15.04 will be very different that past versions as it will come with systemd as default with an option to use upstart.

Also I should have put editing **/etc/default/grub** after the creation/update portion of the custom grub entries in **/etc/grub.d/06_custom** as that makes more sense.

Any way hopefully it will be a lot easier to understand. Hindsight is always better than foresight. :)

---

### Post by von Stalhein on 2015-04-21
Thanks for all your hard work Cavsfan, I for one certainly appreciate it and I know I'm not alone.

---

### Post by Cavsfan on 2015-04-21
> **von Stalhein said:**
> Thanks for all your hard work Cavsfan, I for one certainly appreciate it and I know I'm not alone.

You are very welcome! It's nice to hear when someone appreciates the wiki! Judging from the amount of views many people use it, but I don't know.

I know that some people may get intimidated first looking at it. I did myself when Ranch Hand first showed me this method of customizing grub.

It took me a few days before I was ready to take the plunge. Hopefully I will able to simplify it more so that it is a lot less intimidating.

Precise 12.04 is unique with it's 2 grub entries one for normal and one for recovery but every version after that until Utopic is the same.

Vivid will have a normal systemd boot that is just like the rest of the normal boot entries along with an option to boot with upstart and that will have a special part to it.
The recovery line will be just like the other systems.

---

### Post by von Stalhein on 2015-04-22
Yes, I've skimmed over a couple of articles about systemd but I need to put some time in and get my head around it.

I used to spend hours on conky configs, compiz, cli stuff and other tweaks but when a PC died a while back I subsisted on a Win work laptop using it mainly for email etc.

I re-purposed an old-ish mobo and cpu to get back into Ubuntu but lost about 14 months "practice" so have been a bit out of the loop. The first thing I did do was tart up the GRUB screen :p

How do you get shots of the screen - is it just via phone camera or similar or is there another method?

---

### Post by Cavsfan on 2015-04-22
> **von Stalhein said:**
> Yes, I've skimmed over a couple of articles about systemd but I need to put some time in and get my head around it.

I used to spend hours on conky configs, compiz, cli stuff and other tweaks but when a PC died a while back I subsisted on a Win work laptop using it mainly for email etc.

I re-purposed an old-ish mobo and cpu to get back into Ubuntu but lost about 14 months "practice" so have been a bit out of the loop. The first thing I did do was tart up the GRUB screen :p

How do you get shots of the screen - is it just via phone camera or similar or is there another method?

Glad to hear your back! That is also the first thing I do - get the grub menu looking nice. 

Yes, the only way to get a picture of the grub screen is to take a picture. I use my phone most of the time and upload it to my PC via wifi. My phone takes 3264x2448 pictures. 

Something else I'm going to try to add to the wiki is something I learned not too long ago. 

That is if you have multiple Linux systems and do not like for grub to be installed on each system during installation or during an update to grub you can simply install the system's grub to the PBR on the systems you do not want to control grub. E.G. install grub to PBR /dev/sda4 instead of MBR /dev/sda like normal. 

Then you have one system that will retain control of your grub and when other systems have their grub updated, it has zero effect on your main system's grub.

I was constantly, after an update to grub on one system, going to the sytem I wanted to be in control and issuing a **sudo grub-install /dev/sda** command from there.

This prevents the need for doing that. So your grub menu never changes or moves around on you. You just have to remember which system your grub is installed on.

---

### Post by oldfred on 2015-04-22
I also have installed to partition but found these also, have not tried any yet.

 This launches the installer program (Ubiquity) with an option (-b) to not install a boot loader from live installer in live mode:
In the Terminal window, type ubiquity -b. 

      
 Better  install to PBR core.img alone
[https://wiki.archlinux.org/index.php/Grub#Generate_core.img_alone](https://wiki.archlinux.org/index.php/Grub#Generate_core.img_alone)

---

### Post by Cavsfan on 2015-04-22
> **oldfred said:**
> I also have installed to partition but found these also, have not tried any yet.

 This launches the installer program (Ubiquity) with an option (-b) to not install a boot loader from live installer in live mode:
In the Terminal window, type ubiquity -b. 

      
 Better  install to PBR core.img alone
[https://wiki.archlinux.org/index.php/Grub#Generate_core.img_alone](https://wiki.archlinux.org/index.php/Grub#Generate_core.img_alone)

Thank you for that information oldfred! :D

---

### Post by von Stalhein on 2015-04-23
> You just have to remember which system your grub is installed on.
Yes. Having seen your GRUB screen over a period I would think that could be an issue sometimes ;) 

Although you do have the pics to fall back on!

I spent most of last night trying to set up a VPN using SoftEther - I think I may leave it another day. 
The chook is in the oven and the bread is baking!!

I will post a pic of my screen after the next boot - there's only 2 systems but I reckon the pic is OK :)

---

### Post by von Stalhein on 2015-04-23
[ATTACH=CONFIG]261488[/ATTACH]

Hope it comes up OK.

A Bali farm terrace from a coffee farm on the hill above it.

Yes, I need to change the text colour :-)

---

### Post by Cavsfan on 2015-04-23
> **von Stalhein said:**
> [ATTACH=CONFIG]261488[/ATTACH]

Hope it comes up OK.

A Bali farm terrace from a coffee farm on the hill above it.

Yes, I need to change the text colour :-)

Nice but where is the custom entries? Have you just not gotten around to it?

You could post the output of **sudo blkid -c /dev/null** here and I could set it up for you if you'd like.

Oh I guess you did find an old hard drive. Windows XP is no longer supported so I'd be careful with that or not run it at all.

[http://www.microsoft.com/en-us/windows/enterprise/end-of-support.aspx](http://www.microsoft.com/en-us/windows/enterprise/end-of-support.aspx)

---

### Post by Cavsfan on 2015-04-25
Vivid Vervet 15.04 was released Thursday April 23rd. Only 2 flavors got upstart as an option with systemd as default. The rest just got systemd only.


[LIST=1]
[*]Ubuntu - upstart 
[*]Kubuntu 
[*]Xubuntu - upstart 
[*]Lubuntu 
[*]Ubuntu Gnome 
[*]Ubuntu Mate 
[/LIST]

So until I can get this added to the wiki and rewrite most of it here is what custom entries look like:

If you are using Ubuntu or Xubuntu:

```
menuentry "Vivid Vervet Mate 15.04 Mate" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Vivid Vervet Mate 15.04 Mate Upstart" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash [COLOR=#ff0000]init=/sbin/upstart[/COLOR]
        initrd /initrd.img
}
menuentry "Vivid Vervet Mate 15.04 Mate (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
```

If you are using the others, it's just the regular enteries:

```
menuentry "Vivid Vervet Mate 15.04 Mate" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Vivid Vervet Mate 15.04 Mate (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
```

---

### Post by von Stalhein on 2015-04-27
Hello Cavsfan,
Yes, well aware of XP issues but I have a lot of  legacy gaming stuff and some old uni DOS programs I use from time to  time.
 I very rarely boot to it atm as the GPU in this box is very  underpowered so gaming is not really an option.

Thanks for that offer, only have the 2 OS'es so it's not a big drama.

> /dev/sda1: LABEL="DSK1_VOL1" UUID="01C3D871F965AC80" TYPE="ntfs" PARTUUID="960c960c-01"
/dev/sdc1: UUID="d69eeee0-eb0b-459d-9f3b-5ed5191247ff" TYPE="ext4" PARTUUID="9fa5e4ea-01"
/dev/sdc5: UUID="6f05285e-1d92-4f10-8ebd-172e0096c890" TYPE="swap" PARTUUID="9fa5e4ea-05"
/dev/sdb5: LABEL="Disk 2" UUID="A83CB1173CB0E18C" TYPE="ntfs" PARTUUID="a3f79c20-05"
/dev/sdd1: LABEL="SeagateExternal" UUID="6EC484A1C4846D61" TYPE="ntfs" PARTUUID="c75b1e2d-01"
/dev/sde1: LABEL="Vistaback" UUID="445CA27758215EB1" TYPE="ntfs"
/dev/sde2: LABEL="Ubuntback" UUID="4B7B4D5000549C38" TYPE="ntfs"



[LIST]
[*]Disk 1 is the XP drive
[*]SDC1 carries Vivid
[*]Disk 2 is data (mainly Win games, music)
[*]SDD1 is a Seagate external HDD
[*]Vistaback and Ubuntuback are on another external HDD. The SDE1 Vista backup is my daughter's laptop and the SDE2 Ubuntuback is the backup of the machine since Feisty.
[/LIST]

---

### Post by Cavsfan on 2015-04-27
> **von Stalhein said:**
> Hello Cavsfan,
Yes, well aware of XP issues but I have a lot of  legacy gaming stuff and some old uni DOS programs I use from time to  time.
 I very rarely boot to it atm as the GPU in this box is very  underpowered so gaming is not really an option.

Thanks for that offer, only have the 2 OS'es so it's not a big drama.

```
/dev/sda1: LABEL="DSK1_VOL1" UUID="01C3D871F965AC80" TYPE="ntfs" PARTUUID="960c960c-01"
/dev/sdc1: UUID="d69eeee0-eb0b-459d-9f3b-5ed5191247ff" TYPE="ext4" PARTUUID="9fa5e4ea-01"
/dev/sdc5: UUID="6f05285e-1d92-4f10-8ebd-172e0096c890" TYPE="swap" PARTUUID="9fa5e4ea-05"
/dev/sdb5: LABEL="Disk 2" UUID="A83CB1173CB0E18C" TYPE="ntfs" PARTUUID="a3f79c20-05"
/dev/sdd1: LABEL="SeagateExternal" UUID="6EC484A1C4846D61" TYPE="ntfs" PARTUUID="c75b1e2d-01"
/dev/sde1: LABEL="Vistaback" UUID="445CA27758215EB1" TYPE="ntfs"
/dev/sde2: LABEL="Ubuntback" UUID="4B7B4D5000549C38" TYPE="ntfs"                      
```


[LIST]
[*]Disk 1 is the XP drive 
[*]SDC1 carries Vivid 
[*]Disk 2 is data (mainly Win games, music) 
[*]SDD1 is a Seagate external HDD 
[*]Vistaback and Ubuntuback are on another external HDD. The SDE1 Vista backup is my daughter's laptop and the SDE2 Ubuntuback is the backup of the machine since Feisty. 
[/LIST]


Here is all you need I believe for your custom file:
```
#!/bin/sh
echo 1>&2 "Adding Vivid Vervet 15.04 and Windows XP"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Vivid Vervet 15.04" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet splash
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 Upstart" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro quiet splash init=/sbin/upstart
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 (Recovery Mode)" {
    set root=(hd2,1)
        linux /vmlinuz root=/dev/sdc1 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows XP" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01C3D871F965AC80
    chainloader +1
}
```

The upstart entry is only if you have installed vanilla Ubuntu with Unity or Xubuntu, otherwise delete that menu entry.

Just save that file as **/etc/grub.d/06_custom** and then make it executable - **sudo chmod +x /etc/grub.d/06_custom**

Then of course **sudo update-grub** and when you enter that it should list "Adding Vivid Vervet 15.04 and Windows XP" in the output.

When you are satisfied that both or all three menu selections work to your satisfaction.

Enter 
[LIST=1]
[*]**sudo chmod -x /etc/grub.d/20_memtest86+** 
[*]**sudo chmod -x /etc/grub.d/10_linux** 
[*]**sudo chmod -x /etc/grub.d/30_os-prober** 
[*]**sudo update-grub** 
[/LIST]
Then you should just see "Adding Vivid Vervet 15.04 and Windows XP" only in the output of **sudo update-grub**.

Then if you want to leave Vivid systemd as the default line you don't need to do anything but if you want another line 
edit **/etc/default/grub** and change the GRUB_DEFAULT=N N being the number you want to have as default. It starts at 0,1,2,3 etc.

Enter this in terminal and you will see the numbers that could go there.

grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0

Cheers mate and let me know how this works for you. :)

---

### Post by von Stalhein on 2015-04-28
How did it work?

Perfectly!!! You little beauty! 
Hang on, an issue. When I select items 2 or 3 I get "Partition not found" so I must've stuffed up something in your elegantly simple instructions.

> user@user:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0    menuentry "Vivid Vervet 15.04" {
     1    menuentry "Vivid Vervet 15.04 Upstart" {
     2    menuentry "Vivid Vervet 15.04 (Recovery Mode)" {
     3    menuentry "Windows XP" {

Lovely to be back in the program though!

Will go again from the start and report back.

Hmm, now if I select menu entry 0 I get the same problem. This means my only working OS from the GRUB menu atm is XP.
Not. Good.

I can get into Vivid by changing the {hd2,1} to {hd1,1} and then the 'ol ctrl-x

---

### Post by von Stalhein on 2015-04-28
(later)
XP will boot but I still need to change the hd# in GRUB to get back into Vivid.

Have been through the Wiki but I'm not seeing the no doubt obvious remedy.

---

### Post by Cavsfan on 2015-04-28
> **von Stalhein said:**
> How did it work?

Perfectly!!! You little beauty! 
Hang on, an issue. When I select items 2 or 3 I get "Partition not found" so I must've stuffed up something in your elegantly simple instructions.

```
user@user:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed  's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0    menuentry "Vivid Vervet 15.04" {
     1    menuentry "Vivid Vervet 15.04 Upstart" {
     2    menuentry "Vivid Vervet 15.04 (Recovery Mode)" {
     3    menuentry "Windows XP" {                      

```
Lovely to be back in the program though!

Will go again from the start and report back.

Hmm, now if I select menu entry 0 I get the same problem. This means my only working OS from the GRUB menu atm is XP.
Not. Good.

I can get into Vivid by changing the {hd2,1} to {hd1,1} and then the 'ol ctrl-x

From the output of blkid Vivid is on /dev/sdc1, which *should* equate to hd2,1 since the first drive letter sd[COLOR=#ff0000]c[/COLOR]1 equates to 2 as the numbering starts at 0 (a),1 (b),2 (c), etc.
Then sdc[COLOR=#ff0000]1[/COLOR] points to partition 1 of that hard drive c.

This makes no sense but try editing the custom file - **gksudo gedit /etc/grub.d/06_custom** and changing the three places where hd2,1 is to hd1,1.
That would point to HD2, Partition 1 but let me know what happens.

Did you enter **sudo blkid** or **sudo blkid -c /dev/null** ? The later is supposed to be more correct I believe.

Edit: Make sure you enter **sudo update-grub** afterwards.

---

### Post by oldfred on 2015-04-28
I have had lots of issues of drive order. It does not match the mounted system drive order.
I normally booted from sdc or sdd with my older system. And drives were in SATA port order on motherboard. But I must have skipped a port as if I plugged in a flash drive it became hd2 (usually unless boot drive) and sdb.

And boot drive is always hd0. So when I boot from sdd drive that is hd0, then drive that was sda would be hd1. But then depending on whether flash drive was plugged in it would be hd2 or my normal internal sdb would be. 
Same sort of issue when using sdc as boot drive. Then it was hd0.

---

### Post by Cavsfan on 2015-04-28
> **oldfred said:**
> I have had lots of issues of drive order. It does not match the mounted system drive order.
I normally booted from sdc or sdd with my older system. And drives were in SATA port order on motherboard. But I must have skipped a port as if I plugged in a flash drive it became hd2 (usually unless boot drive) and sdb.

And boot drive is always hd0. So when I boot from sdd drive that is hd0, then drive that was sda would be hd1. But then depending on whether flash drive was plugged in it would be hd2 or my normal internal sdb would be. 
Same sort of issue when using sdc as boot drive. Then it was hd0.

Thanks a lot! I was hoping you would see this and step in. So, if hd1,1 works for sdc1, I guess you have to just roll with it? That is exactly what von Stalhein is experiencing.

I have one 500GB HD partitioned into 4 physical partitions: sda1 is windows 7, sda2 is Mint 17.1 Rebecca, sda3 is Trusty 14.04 using FB all the time, the 4th being the extended partition.

Then there is a sda5 which is Vivid Mate (and will be the next developmental version) and my swap is on sda6. Sdb1 is my 1TB USB Phantom drive. 
When I plug in my 5GB USB thumb drive it becomes sdc1. Luckily they stay in that same order.

I could see disconnecting drives that are in the grub menu or connecting drives that are not in the grub menu causing problems.

---

### Post by Bashing-om on 2015-04-28
Guys;

At one time I also experienced my drives changing .
I found mapping the drives solved it for me:
see:
```

man grub-mkdevicemap

```
You can determine what GRUB thinks your disk devices are by running:
```

sudo grub-mkdevicemap --device-map=device.map

```
Which will create the file; To see the contents of that created file:
```

cat device.map

```
//
The device.map file is located in /boot/grub/ It isn't required but can be used in Grub 2. 

[INDENT][INDENT]there are those times
[INDENT][INDENT][INDENT]ya got to give the system a bit of help
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by von Stalhein on 2015-04-29
Yes, interesting. ```
 cat device map 
``` gives 
```
(hd0)    /dev/disk/by-id/ata-ST3120026AS_3JT308HS
(hd1)    /dev/disk/by-id/ata-ST3120026AS_3JT3SE3N
(hd2)    /dev/disk/by-id/ata-ST3250410AS_6RY57G1E

```

So, in the above:
(hd0) would be the XP disk
(hd1) would be the Vivid disk
(hd2) would be the data disk (carries all windows games, music etc,)

I think!

I'm also getting a kernel load error ```
 [  0.619398] ACPI PCC probe failed starting version 219
``` which from my reading is harmless. 
That wasn't there before I changed the GRUB commands but a kernel update came through earlier that evening so I'm putting it down to that.

Thanks all!!!

---

### Post by Cavsfan on 2015-04-29
> **Bashing-om said:**
> Guys;

At one time I also experienced my drives changing .
I found mapping the drives solved it for me:
see:
```

man grub-mkdevicemap

```
You can determine what GRUB thinks your disk devices are by running:
```

sudo grub-mkdevicemap --device-map=device.map

```
Which will create the file; To see the contents of that created file:
```

cat device.map

```
//
The device.map file is located in /boot/grub/ It isn't required but can be used in Grub 2.[INDENT][INDENT]there are those times[INDENT][INDENT][INDENT]ya got to give the system a bit of help
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for that information!

> **von Stalhein said:**
> Yes, interesting. ```
 cat device map 
``` gives 
```
(hd0)    /dev/disk/by-id/ata-ST3120026AS_3JT308HS
(hd1)    /dev/disk/by-id/ata-ST3120026AS_3JT3SE3N
(hd2)    /dev/disk/by-id/ata-ST3250410AS_6RY57G1E

```

So, in the above:
(hd0) would be the XP disk
(hd1) would be the Vivid disk
(hd2) would be the data disk (carries all windows games, music etc,)

I think!

I'm also getting a kernel load error ```
 [  0.619398] ACPI PCC probe failed starting version 219
``` which from my reading is harmless. 
That wasn't there before I changed the GRUB commands but a kernel update came through earlier that evening so I'm putting it down to that.

Thanks all!!!

Don't worry about that message:
```
 [  0.619398] ACPI PCC probe failed starting version 219
```
Everyone gets that booting up I'm pretty sure. At least I've seen it for the past several months even before final release.

So, if Vivid is indeed on hd1 (2nd) drive instead of sdc1 (3rd) drive as it first appeared. 

That would explain why when you edited the grub line it succussfully booted into Vivid.

Just change your file like this:

**gksudo gedit /etc/grub.d/06_custom** and replace it with this:

```
#!/bin/sh
echo 1>&2 "Adding Vivid Vervet 15.04 and Windows XP"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Vivid Vervet 15.04" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro quiet splash
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 Upstart" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro quiet splash init=/sbin/upstart
        initrd /initrd.img
}
menuentry "Vivid Vervet 15.04 (Recovery Mode)" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows XP" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01C3D871F965AC80
    chainloader +1
}
```

And of course **sudo update-grub** to make the changes stick. Then you should be good to go.

Let me know if this solves your problem.

---

### Post by Cavsfan on 2015-05-05
Well, I think I finally cleaned the wiki up enough that it should be easier to understand and work with.

I also added Vivid Vervet and whether you installed vanilla Ubuntu with Unity or Xubuntu there are commands to boot with systemd as the default and upstart as an option.
If you installed any other version you will only have systemd unless you install upstart manually. They appropriate custom entries are there for either situation.

Let me know if I left anything out or made any mistakes. I left the same pictures there as they are only examples.
I hope to add some new pictures soon.

Regards...

---

### Post by von Stalhein on 2015-05-06
Hi Cavsfan,
Sorry for the delay, life keeps getting in the way. 
I couldn't remember whether I'd completed all the steps in your last post so I went through them again last night and rebooted the box for the first time in 6 days.

And got this :)

[ATTACH=CONFIG]261797[/ATTACH]

Pretty annoying.

I mucked around with Hirens but eventually found a Precise disc and got to a live cd situation. 
Before trying the sequence again I used boot-repair which gave me a menu with all the kernels on this box. These were all appended under the Vivid menu. From a repair option I did a repair & then a reboot.
I thought I may have needed to chmod the rest of the files as above and that was why the busybox error occurred but I don't think that was the case as I made sure the same sequence for both choices was completed.
I went through all the commands for the second choice again above being careful not to omit any.

That just got me back to the above black screen again which caused me to have to repeat the live cd process :p

So I then tried the original file you parsed for me and it worked perfectly.

I have no idea why, but I obviously stuffed something up in the cmd process with the second mod. However, I did reboot a couple of times during that process without the busybox error occurring so it's a bit confusing.

It's ages since I've had to do a recovery so it took a while to remember some steps and alternatives, but I've had plenty of practice now!!

Thanks again  ):P :popcorn:

---

### Post by Cavsfan on 2015-05-06
> **von Stalhein said:**
> Hi Cavsfan,
Sorry for the delay, life keeps getting in the way. 
I couldn't remember whether I'd completed all the steps in your last post so I went through them again last night and rebooted the box for the first time in 6 days.

And got this :)

[ATTACH=CONFIG]261797[/ATTACH]

Pretty annoying.

I mucked around with Hirens but eventually found a Precise disc and got to a live cd situation. 
Before trying the sequence again I used boot-repair which gave me a menu with all the kernels on this box. These were all appended under the Vivid menu. From a repair option I did a repair & then a reboot.
I thought I may have needed to chmod the rest of the files as above and that was why the busybox error occurred but I don't think that was the case as I made sure the same sequence for both choices was completed.
I went through all the commands for the second choice again above being careful not to omit any.

That just got me back to the above black screen again which caused me to have to repeat the live cd process :p

So I then tried the original file you parsed for me and it worked perfectly.

I have no idea why, but I obviously stuffed something up in the cmd process with the second mod. However, I did reboot a couple of times during that process without the busybox error occurring so it's a bit confusing.

It's ages since I've had to do a recovery so it took a while to remember some steps and alternatives, but I've had plenty of practice now!!

Thanks again  ):P :popcorn:

You are welcome!
So, you did get it corrected?

---

### Post by von Stalhein on 2015-05-06
> **Cavsfan said:**
> You are welcome!
So, you did get it corrected?

Yep, all good now.

---

### Post by Cavsfan on 2015-05-06
My first grub screen on Wily Werewolf 15.04.

I like this blue circle wallpaper pretty much. 
It has these font colors:

```
echo " set color_normal=cyan/black"
echo " set menu_color_normal=yellow/black"
echo " set menu_color_highlight=red/black"
```

[[IMG]http://en.zimagez.com/miniature/20150506171543.jpg[/IMG]]("http://en.zimagez.com/zimage/20150506171543.php")

---

### Post by Cavsfan on 2015-05-07
> **Cavsfan said:**
> You are welcome!
So, you did get it corrected?

> **von Stalhein said:**
> Yep, all good now.

Fantastical! Glad to hear that! I guess we posted about the same time so I did not see this until today.

---

### Post by Cavsfan on 2015-07-08
I actually got Arch Linux installed and added to my custom entries. I just looked at the grub.cfg file and figured out how to do it and it worked. ;)

```
menuentry "Arch Linux" {
    set root=(hd0,3)
        linux /boot/vmlinuz-linux root=/dev/sda3 rw quiet
        initrd /boot/initramfs-linux.img
}
```

This will boot Arch Linux believe it or not.

Something else I have come to understand (at least on non-SSD drives) is that grub only recognizes 4 partitions whether they are physical or if 3 are physical and the 4th is an extended partition.
It will recognize the 1st logical partition but beyond that it fails to see the rest. I've been though my share of multiple OSs and how Grub2 reacts to them.

So, my 5th logical partition appears to be on /dev/sda7 or that is what grub shows at bootup but if you edit the line this is pointing to the correct partition **set root=(hd0,7)**.
But the line below that has **/dev/sda2** and that will appear on every subsequent partition after the 4th one. 
So without a custom grub I have to edit that line and change it to sda7 to boot intot that system. Otherwise you boot into what is on partition sda2 in tty mode.

Arch is quite the system to get installed but once you do it is sweet. ):P

---

### Post by von Stalhein on 2015-07-14
I courageously did it in VirtualBox :p
Undecided on whether it's the way to go as a main dist though!

---

### Post by Cavsfan on 2015-07-14
> **von Stalhein said:**
> I courageously did it in VirtualBox :p
Undecided on whether it's the way to go as a main dist though!

I think it's a little harder than on VirtualBox but I know nothing about VirtualBox.

That is great though! :D The more you get into it the better you'll like it. Took me about 2 weeks before I got my mouse wheel to scroll but finally got that working.

It is truly a custom system that only has what you put on it. I just went with Xcfe as my DE and love it. Nothing else compares.

Here is a screenie of my Arch Linux custom grub screen. I finally figured out how to add a picture for the background.

[[IMG]http://en.zimagez.com/miniature/20150714111241.jpg[/IMG]]("http://en.zimagez.com/zimage/20150714111241.php")

---

### Post by von Stalhein on 2015-07-15
Yes, definitely harder than putting it on a "real" partition!
If something goes' wrong you can just hose the install in the sandbox and start again.

It's certainly highly customisable and as you have no doubt sussed contains some tricks for the unwary, especially where it mightn&#8217;t be obvious what dependencies are required for some packages!

Enjoyable working though these things. When it's in VirtualBox you can afford to be brave :-)  And, nice pic BTW!

---

### Post by Cavsfan on 2015-07-15
> **von Stalhein said:**
> Yes, definitely harder than putting it on a "real" partition!
If something goes' wrong you can just hose the install in the sandbox and start again.

It's certainly highly customisable and as you have no doubt sussed contains some tricks for the unwary, especially where it mightn’t be obvious what dependencies are required for some packages!

Enjoyable working though these things. When it's in VirtualBox you can afford to be brave :-)  And, nice pic BTW!

Thank you! 
Yes installing Arch Linux involves installing the DVD/CD and then you have a text based environment until you get the system installed. 
It took me about a week or more to get to where I could add a DE which I chose Xcfe.
I tried gnome, gnome-flashback-session, cinnamon and non of them worked; they had really big icons for everything and then it took me another 2 weeks before I got compiz and emerald working well.

I purged gnome, gnome-flashback-session, cinnamon which ended up purging xcfe4 and xcfe4-goodies so I re-installed them and everything was back to normal.

Surprisingly I could not boot into Arch except through my custom entry. Everything else failed.

---

### Post by Cavsfan on 2015-07-17
What I'm currently using to boot Arch Linux in 06_custom:

```
menuentry "Arch Linux" {
    set root=(hd0,3)
        linux /boot/vmlinuz-linux root=/dev/sda3 rw quiet
        initrd /boot/initramfs-linux.img
}
menuentry "Arch Linux (Recovery Mode)" {
    set root=(hd0,3)
        linux /boot/vmlinuz-linux root=/dev/sda3 rw single
        initrd /boot/initramfs-linux.img
}
```

There's a fallback and lts kernel but I left them out and this works just fine. :)

---

### Post by Cavsfan on 2015-08-02
If any one has installed Arch Linux and is insterested in getting a custom grub screen like the one I am currently using in post [_#366_]("http://ubuntuforums.org/showthread.php?t=2076205&page=37&p=13320921#post13320921").
Just let me know and I'll explain how I did it.

There is no **/etc/grub.d/05_debian_theme** file in Arch.

---

### Post by Cavsfan on 2015-08-24
If there is any Arch Linux users who multi-boot and want to try this out, if you haven't already figured out how.

Most of what is done is in **/etc/default/grub** as there is no **05_debian_theme** file in Arch.

That, a **06_custom** file and a picture is all that is needed.

I created it and then less than a half hour later it was put in the dustbin (trash). I guess they prefer everything to be in their wiki format, which I just cannot do at this point.

[https://bbs.archlinux.org/viewtopic.php?id=200995](https://bbs.archlinux.org/viewtopic.php?id=200995)

Also, there is a different way they update grub rather than **sudo update-grub**.

In Arch Linux you enter **sudo grub-mkconfig -o /boot/grub/grub.cfg**

---

### Post by QDR06VV9 on 2015-08-24
There used to be a nice how to for Arch and custom grub configs but I can't find it ATM will post back after I try to get a hold
of couple of friends.
> [COLOR=#000000]Also, there is a different way they update grub rather than [/COLOR]**sudo update-grub**[COLOR=#000000].[/COLOR]

You mean
```
[FONT=Consolas]# grub-mkconfig -o /boot/grub/grub.cfg[/FONT]
```:p
Kind Regards

---

### Post by Cavsfan on 2015-08-24
> **runrickus said:**
> There used to be a nice how to for Arch and custom grub configs but I can't find it ATM will post back after I try to get a hold
of couple of friends.

>  [COLOR=#000000]Also, there is a different way they update grub rather than [/COLOR]**sudo update-grub**[COLOR=#000000].[/COLOR]

You mean
```
[FONT=Consolas]# grub-mkconfig -o /boot/grub/grub.cfg[/FONT]
```:p
Kind Regards

Indeed! They have no update-grub command that I know of. I have seen grub-customizer but nothing like this method. I was surprised but pleased when I got Arch customized. ;)

I also installed all the rest of the Linux systems in the PBR so it doesn't get wiped out by an update to a grub on another partition. 

How to do that, which I learned from Kansasnoob, Zika and some others in this forum is on 1.8 of the wiki right here  [_If you multiboot mutiple Linux installs and want one Grub to control all of your OSs_]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#If_you_multiboot_mutiple_Linux_installs_and_want_one_Grub_to_control_all_of_your_OSs")

Also through the years, at least on my system grub does not recognize anything past the 4 partition. 
The 4th partion can even be the first logical partition with the 4th and last physical being the extended partition.

But it will never get the 5th partition correct and I have Arch, Mint, 2 Ubuntus and Windows 10 on my system. 
So, the 5th partion "looks" like it will boot into the selected system but will end up in the 1st Linux partition in tty mode.

You can tell by what it says in tty mode. So, in addition to this being Kool, it is effective as well if you have more than 4 systems.

---

### Post by oldfred on 2015-08-24
That grub command in Arch is really the same. In grub legacy it also was sudo update-grub.

```
fred@trusy-ar:~$ whereis update-grub
update-grub: /usr/sbin/update-grub /usr/share/man/man8/update-grub.8.gz
fred@trusy-ar:~$ cat /usr/sbin/update-grub
#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"
fred@trusy-ar:~$ 

```

---

### Post by Cavsfan on 2015-08-25
> **oldfred said:**
> That grub command in Arch is really the same. In grub legacy it also was sudo update-grub.

```
fred@trusy-ar:~$ whereis update-grub
update-grub: /usr/sbin/update-grub /usr/share/man/man8/update-grub.8.gz
fred@trusy-ar:~$ cat /usr/sbin/update-grub
#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"
fred@trusy-ar:~$ 

```

Yes, I guess in Arch they just did not create the script.
I had run grub-mkconfig just to produce the output of grub in a text file before. So it makes sense that it would work.

---

### Post by von Stalhein on 2015-10-23
Just updated to 15.10 and can't make the grub update name that dist - i.e. it remains as Vivid after a sudo update-grub

Before I go fiddling and give myself another intensive "learning experience", what's the obvious thing I'm missing here?

---

### Post by Cavsfan on 2015-10-24
> **von Stalhein said:**
> Just updated to 15.10 and can't make the grub update name that dist - i.e. it remains as Vivid after a sudo update-grub

Before I go fiddling and give myself another intensive "learning experience", what's the obvious thing I'm missing here?

```
gksudo gedit /etc/grub.d/06_custom 
```

That is where your custom entries should be. 

That is where you change them and whatever you put between the quotes at the top as well as in each menu entry is what will display after a sudo update-grub.

---

### Post by Cavsfan on 2015-10-24
I'll be editing the wiki today to get Utopic out as it's past EOL and Wily Werewolf 15.10 in it.

---

### Post by Cavsfan on 2015-10-24
I updated the wiki adding Wily Werewolf 15.10. Let me know if there you see any errors.

---

### Post by von Stalhein on 2015-10-26
> **Cavsfan said:**
> ```
gksudo gedit /etc/grub.d/06_custom 
```

That is where your custom entries should be. 

That is where you change them and whatever you put between the quotes at the top as well as in each menu entry is what will display after a sudo update-grub.

Thanks Cavsfan, awesome!

---

### Post by Cavsfan on 2015-10-26
> **von Stalhein said:**
> Thanks Cavsfan, awesome!

Glad I could help! :)

---

### Post by Cavsfan on 2015-10-27
Thought it was time to post a new screenie of grub.

[[IMG]http://en.zimagez.com/miniature/20151027143535.jpg[/IMG]]("http://en.zimagez.com/zimage/20151027143535.php")

It's the same picture because I like how the cyan and red look with that background.

---

### Post by Cavsfan on 2015-11-19
@oldfred,
I did finally notice that there is an update-grub in Arch in the AUR.

But, on Arch I'm keeping everything default so I didn't install it.

---

### Post by Cavsfan on 2016-02-01
If you have your customized grub on Xenial Xerus 16.04, with today's update to grub-pc the font location changed in **/etc/grub.d/05_debian_theme**.

Instead of the font colors going after line 165, it's back up to after line 122:

122   echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then" 
123   echo " set color_normal=light-red/black" 
124   echo " set menu_color_normal=cyan/black" 
125   echo " set menu_color_highlight=red/black"

---

### Post by Cavsfan on 2016-03-19
Just 3 OSs on my system now.

[[IMG]http://www.zimagez.com/miniature/20160229163727.jpg[/IMG]]("http://www.zimagez.com/zimage/20160229163727.php")

---

### Post by Cavsfan on 2016-04-08
Finally a new pic on Arch Linux with white at the top and bottom, cyan as the normal color (box and inside the box) and red as the highlighted color.
Although that is hard to see from the picture; that is what it is.

[[IMG]http://en.zimagez.com/miniature/20160408161917.jpg[/IMG]]("http://en.zimagez.com/zimage/20160408161917.php")

---

### Post by von Stalhein on 2016-04-11
Nice job Cavsfan :D Keep up the good work!

---

### Post by Cavsfan on 2016-04-11
> **von Stalhein said:**
> Nice job Cavsfan :D Keep up the good work!

Thank you kindly! :D

---

### Post by Cavsfan on 2016-04-25
I'm unable to edit the wiki right now so until that issue is resolved, I just post the only change that is necessary for 16.04.

It was from a previous post up the page a little.

[http://ubuntuforums.org/showthread.php?t=2076205&page=39&p=13432553#post13432553](http://ubuntuforums.org/showthread.php?t=2076205&page=39&p=13432553#post13432553)

I still need to add to the wiki newly released 16.04 and remove 15.04 as it's past EOL.

---

### Post by Cavsfan on 2016-04-26
I was finally able to fix the wiki to remove Vivid Vervet 15.04 and add Xenial Xerus 16.04 LTS.

Please let me know if you find any errors or problems. 

I left out upstart with 16.04 because I was never able to successfully use it anyway.
Systemd is the way of the future and upstart will likely be phased out in the near future.

Kind regards :)

---

### Post by von Stalhein on 2016-04-27
The only issue I encountered was that for some reason the upgrade borked keyboard and mouse capability in GRUB.

I was able to re-enable through the BIOS in the Integrated Peripherals table, in the USB menu - weird!

I will fiddle with my text colour though as when not highlighted (cyan) it's white & hard to see. 

First world problems!

BTW - what&#8217;s the best way to screenshot the GRUB screen?

---

### Post by Cavsfan on 2016-04-27
> **von Stalhein said:**
> The only issue I encountered was that for some reason the upgrade borked keyboard and mouse capability in GRUB.

I was able to re-enable through the BIOS in the Integrated Peripherals table, in the USB menu - weird!

I will fiddle with my text colour though as when not highlighted (cyan) it's white & hard to see. 

First world problems!

BTW - what’s the best way to screenshot the GRUB screen?

I take a picture with my phone's camera and upload it to my pc via wifi.

I created an account on [http://en.zimagez.com/](http://en.zimagez.com/)
That way you can edit or delete pictures if you're logged in.
I upload them there and it gives you the forum code for posting in this forum.

Grub first looks for the 1st picture it finds in **/boot/grub/** then it will find your colors in **/etc/grub.d/05_debian_theme** after line 122.

If there is no picture it will not use those colors you have setup. And not all pictures work, sometimes I've had to try more than one, but rarely.

---

### Post by von Stalhein on 2016-04-29
Cheers for that - I'll fiddle with the text. Thanks for the image hosting link, I'll give it a go - will probably use the phone as I don't have a wifi card in the Canon - yet :-)

GRUB finds the pic so nothing is wrong there AFAIK.

---

### Post by Cavsfan on 2016-04-29
> **von Stalhein said:**
> Cheers for that - I'll fiddle with the text. Thanks for the image hosting link, I'll give it a go - will probably use the phone as I don't have a wifi card in the Canon - yet :-)

GRUB finds the pic so nothing is wrong there AFAIK.

Good mate! :) I was going to ask you if you ever got it fixed and looking good.

Let me know if you need anything or when you get it done.

---

### Post by Cavsfan on 2016-07-01
I seriously cannot understand why anyone would use the default grub.

I added another install of Xubuntu 16.04 just for the halibut :P and everytime it adds a kernel through updates, I wait about 2-3 minutes on it updating grub (default).
It does this twice every time a new kernel is added. 
The long wait occurs after it finds the kernels (/etc/grub.d/10_linux) and before the other OSs are updated (/etc/grub.d/30_os-prober)

I ***have to*** customize this thing because once done it goes through an update-grub in about 2 seconds.
Lets see 2-3 minutes or 2 seconds; I'll take 2 seconds.

Cheers

---

### Post by Cavsfan on 2016-07-19
I'm finding that PNG pictures work a lot better than JPG pictures. I tried to grow a JPG picture in pixel size with GIMP and while it listed the pic in the output of update-grub, it would not show at boot.
So, I got frustrated, did some research and seen where someone had posted that PNG pictures work better with Grub in Arch.

So, I took that same picture in GIMP and exported it as a PNG file and viola it worked like it should have. ;)

It has to work better in any distro...

---

### Post by Cavsfan on 2016-07-19
Forgot to mention that nano is probably the best editor as you can just enter **sudo nano /etc/default/grub** etc.

Cntl+Shift+V will paste whatever is on your clipboard just like it does in terminal.
You can copy stuff from gedit, mousepad or whatever text editor you use and paste it into the file.

But, **gksudo gedit *file*** or **gksudo mousepad *file***, etc. works too. Whatever floats your boat. :p

---

### Post by Cavsfan on 2016-07-25
Newest screenshot:

[[IMG]http://en.zimagez.com/miniature/20160725175516.jpg[/IMG]]("http://en.zimagez.com/zimage/20160725175516.php")

---

### Post by von Stalhein on 2016-07-26
Not a lot going on here Cavsfan :)

[[url=http://imgur.com/x5GgnsU][img]http://i.imgur.com/x5GgnsUm.jpg[/img]]("http://imgur.com/x5GgnsU")[/URL]

---

### Post by Cavsfan on 2016-07-26
> **von Stalhein said:**
> Not a lot going on here Cavsfan :)

[[IMG]http://i.imgur.com/x5GgnsUm.jpg[/IMG]]("http://imgur.com/x5GgnsU")

Nice! I see you have XP still. I was using Vista and hated it.
Then I got in on testing Windows 7 and my son showed me where I could get a full install ISO for cheap.
Which I installed and then in the last 6 months he showed me that I could upgrade to Windows 10 for free.

I could live without windows easily but, I like to keep up with it so I can help a family member or a friend.
Plus my wife uses it at work.

Looking good though and thanks for posting a screenshot! :)

---

### Post by von Stalhein on 2016-07-27
Cheers!
I only have XP in the list as this machine is a Frankenstein of old parts and that OS is on an old HDD from about 2003. In the near future I'm hoping to build something with some serious grunt but funds are tight!

I'm running Arch & Fedora in a VM but don't have the space to "promote" any more OS's to GRUB atm.

The image is that of rice paddy terraces taken from a [civet coffee]("https://en.wikipedia.org/wiki/Kopi_Luwak") farm in Bali, where we visited a couple of years ago.

---

### Post by Cavsfan on 2016-07-27
> **von Stalhein said:**
> Cheers!
I only have XP in the list as this machine is a Frankenstein of old parts and that OS is on an old HDD from about 2003. In the near future I'm hoping to build something with some serious grunt but funds are tight!

I'm running Arch & Fedora in a VM but don't have the space to "promote" any more OS's to GRUB atm.

The image is that of rice paddy terraces taken from a [civet coffee]("https://en.wikipedia.org/wiki/Kopi_Luwak") farm in Bali, where we visited a couple of years ago.

I totally understand. I've had this machine since 2009 and have replaced the HD and a bunch of fans including the CPU fan, plus the monitor.
But, that's about it and I'm hoping it'll hang on a couple more years.

That's a long way to go for a good cup of coffee. :D Nice image though!

Kind regards

---

### Post by Cavsfan on 2016-08-01
I just edited the Wiki to add that you can use whatever type editor you are best suited with near the top.

I also added the different types of picture types that Grub2 accepts: *.jpg, *.jpeg, *.png and *.tga pictures. But, PNG pictures seem to work the best.

Cheers

---

### Post by Cavsfan on 2016-09-25
If any one is interested, Yaketty Yak 16.10 grub customization is identical to Xenial Xerux 16.04.

I installed it yesterday and while going through the installation process, I noticed it stayed on "running 'update-grub'" for about 5 minutes. 
So, before I installed the kernel that was in the update queue, I customized, rebooted and then installed the kernel.

Once customized it flies through update-grub in about one second. It seems to hang while probing for other operating systems, namely Windows 10 and Arch Linux.
It may not take that long on your system, but I *had* to do it myself since I'm on an old SATA drive with no SSD but, one of these days...

---

### Post by Cavsfan on 2016-10-17
I just updated the wiki to include Yakkety Yak 16.10 and also removed Wily Werewolf 15.10.

When I removed 15.10 I also removed the code for using upstart. 

Systemd is the way of future anyway.

---

### Post by Cavsfan on 2016-11-10
My latest Grub screen with all Arch entries. Although it is on Arch, it could be on any Linux distro that I've used so far:

[[IMG]http://www.zimagez.com/miniature/20161025132409.jpg[/IMG]]("http://www.zimagez.com/zimage/20161025132409.php")

---

### Post by von Stalhein on 2016-11-10
I've spent an hour looking through the wiki(s), my directories and the web but I can't find/remember how I customised the terminal output when running ```
sudo update-grub
```
It outputs the distributions as it adds them to the GRUB menu. :(

---

### Post by Cavsfan on 2016-11-11
> **von Stalhein said:**
> I've spent an hour looking through the wiki(s), my directories and the web but I can't find/remember how I customised the terminal output when running ```
sudo update-grub
```
It outputs the distributions as it adds them to the GRUB menu. :(

Not sure what you are asking. **sudo update-grub** will update the **/boot/grub/grub.cfg** file and the boot entries based on what is executable in **/etc/grub.d/** like **06_custom**.

If you have customized the grub and have **/etc/grub.d/06_custom** not executable, then those entries will not show up at boot time.
Make it executable by this command:
```
sudo chmod +x /etc/grub.d/06_custom 
``` 

Then **sudo update-grub** should list the custom entries above all of the other entries. Then when you are good with the way they work make these files unexecutable:
```
sudo chmod -x/etc/grub.d/10_linux
sudo chmod -x/etc/grub.d/30_os-prober

```
and once again **sudo update-grub** and it should list only your picture that you are using and what you have between the quotes in the 2nd line of **/etc/grub.d/06_custom**.

BTW, PNG pictures work much better than JPG.

I hope this is what you needed.

---

### Post by von Stalhein on 2016-11-15
Hi Cavsfan - yep that was it.

I have a little message in the start of that bash file that echoes what's actually going on and I'd upgraded to 16.10 & hadn't tidied it up.
Cheers!! ):P

---

### Post by Cavsfan on 2016-11-15
> **von Stalhein said:**
> Hi Cavsfan - yep that was it.

I have a little message in the start of that bash file that echoes what's actually going on and I'd upgraded to 16.10 & hadn't tidied it up.
Cheers!! ):P

Great! I thought that might be it. 
Cheers! ):P

---

### Post by Cavsfan on 2016-11-15
Just for an explanation of why you do edit the custom file even though it says not to. 
It's because you add an echo line to list your systems or else all you would see is the picture listed e.g. **/boot/grub/picture.png** in the output of **sudo update-grub**.  

The file originally contains this:
```
#!/bin/sh
exec tail -n [COLOR=#ff0000]+3[/COLOR] $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
```

The +3 in the 2nd line means to start execution at the 3rd line.

But, after adding the line listing the systems it needs to be changed to +4 so it will start execution at the 4th line.
```
#!/bin/sh
echo 1>&2 "Adding Arch Linux, Xubuntu Xenial Xerus 16.04 LTS, Xubuntu Yakkety Yak 16.10, Xubuntu Zesty Zapus 17.04 and Windows 10"
exec tail -n [COLOR=#ff0000]+4[/COLOR] $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
```

The 4th line would be the 1st menuentry line.

---

### Post by Cavsfan on 2017-03-03
I got bored...

[[IMG]http://en.zimagez.com/miniature/20170222163033.jpg[/IMG]]("http://en.zimagez.com/zimage/20170222163033.php")

---

### Post by Cavsfan on 2017-03-07
Installed Zesty Zapus 17.04 and customized the grub on it.

For those brave enough to have your custom grub on 17.04, the 16.04 and 16.10 method is exactly the same.

Zesty does appear to be working pretty well. I installed Xubuntu of course.

---

### Post by von Stalhein on 2017-03-08
Does one need to be "very" brave to use 17.04 Cavsfan?? :P

---

### Post by Cavsfan on 2017-03-08
> **von Stalhein said:**
> Does one need to be "very" brave to use 17.04 Cavsfan?? :P

Not sure, it seems to be pretty good, but it's just a nine month release. I prefer to have my grub on an LTS or I have mine now on Arch Linux.
Haven't kept up with it until now. I'm sure it would be OK as long as one is prepared if something happens.

---

### Post by von Stalhein on 2017-03-09
Cheers! I tend to update every release but do a clean install every second one.
A bigger priority is updating this box to the 20th C :-)
Keep up the good work!

---

### Post by Cavsfan on 2017-03-09
> **von Stalhein said:**
> Cheers! I tend to update every release but do a clean install every second one.
A bigger priority is updating this box to the 20th C :-)
Keep up the good work!

Ha! Thank you kindly! :)

---

### Post by Cavsfan on 2017-04-19
My newest Grub menu on Zesty Zapus 17.04:

[[IMG]http://en.zimagez.com/miniature/20170419165958.jpg[/IMG]]("http://en.zimagez.com/zimage/20170419165958.php")


If you can't tell it has these colors in /etc/grub.d/05_debian_theme:
```
    echo " set color_normal=yellow/black"
    echo " set menu_color_normal=cyan/black"
    echo " set menu_color_highlight=red/black"
```

---

### Post by von Stalhein on 2017-05-17
Hello Cavsfan - I want to change the font colours on my screen as they are hard to see on the background.

The wiki says to replace the lines from #122 but mine is a bit different (or is it??) :p

From line #116 in my **/etc/grub.d/05_debian_theme **file:
```

echo "insmod ${reader}"
    echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
    if [ -n "${2}" ]; then
        echo "  set color_normal=${2}"
    fi
    if [ -n "${3}" ]; then
        echo "  set color_highlight=${3}"
    fi
    if [ -z "${2}" ] && [ -z "${3}" ]; then
        echo "  true"
    fi
    echo "else"
    set_default_theme "  "
    echo "fi"
}
```

So, does that all gets scrubbed and replaced with:

```
echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
echo " set color_normal=cyan/black"
echo " set menu_color_normal=yellow/black"
echo " set menu_color_highlight=red/black"
```

My colours would be different but I've used the wiki example.
Thanks!

---

### Post by Cavsfan on 2017-05-22
> **von Stalhein said:**
> Hello Cavsfan - I want to change the font colours on my screen as they are hard to see on the background.

The wiki says to replace the lines from #122 but mine is a bit different (or is it??) :p

From line #116 in my **/etc/grub.d/05_debian_theme **file:
```

echo "insmod ${reader}"
[COLOR=#ff0000]    echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"[/COLOR]
    if [ -n "${2}" ]; then
        echo "  set color_normal=${2}"
    fi
    if [ -n "${3}" ]; then
        echo "  set color_highlight=${3}"
    fi
    if [ -z "${2}" ] && [ -z "${3}" ]; then
        echo "  true"
    fi
    echo "else"
    set_default_theme "  "
    echo "fi"
}
```

So, does that all gets scrubbed and replaced with:

```
[COLOR=#ff0000]echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"[/COLOR]
echo " set color_normal=cyan/black"
echo " set menu_color_normal=yellow/black"
echo " set menu_color_highlight=red/black"
```

My colours would be different but I've used the wiki example.
Thanks!

Hi von Stalhein!
I don't know why but, I am not getting notifications that you posted this.

But, the answer to your question is that you just insert the 3 lines below the red line that is line 122.
Do not remove anything, just add those 3 lines as the colors you want to see.

Here is my **/etc/grub.d/05_debian_theme** starting with line 121 (the red lines below are lines 123, 124 and 125):
```
    echo "insmod ${reader}"
    echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
    [COLOR=#ff0000]echo " set color_normal=black/black"
    echo " set menu_color_normal=blue/black"
    echo " set menu_color_highlight=red/black"[/COLOR]
    if [ -n "${2}" ]; then
        echo "  set color_normal=${2}"
    fi
    if [ -n "${3}" ]; then
        echo "  set color_highlight=${3}"
    fi
    if [ -z "${2}" ] && [ -z "${3}" ]; then
        echo "  true"
    fi
    echo "else"
    set_default_theme "  "
    echo "fi"
```

This is on Xenial Xerus 16.04 but, 17.04 is identical to 16.10 about customizing the grub.

---

### Post by von Stalhein on 2017-05-23
Awesome Cavsfan, thanks & please excuse my denseness :-)

---

### Post by Cavsfan on 2017-05-23
> **von Stalhein said:**
> Awesome Cavsfan, thanks & please excuse my denseness :-)

Glad you got it sorted out! No one is perfect my friend! 

Looking at some of these files is overwhelming even to me but, I've just played around with them enough to find where to put the colors at to get them to work. :)

Cheers Mate!

---

### Post by Cavsfan on 2017-06-27
I have always had a DVI to HDMI cable. The DVI end plugged into the Nvidia GeForce 9800 GT card and the HDMI end plugged into the LED monitor in my 10 year old PC.

I have always had to use the increased size of the font in Grub2 for it to look correct. 

However, I replaced a fan in my PC a few days ago and noticed that the Nvidia card also had an HDMI port, so I used an HDMI to HDMI cable and plugged it into the Nvidia card for the 1st time ever.

I turn the thing on and the font was very large and I had to scroll up and down to see which option I needed.
I commented out the **GRUB_FONT** line in the **/etc/default/grub** file and then it looked normal again.

I know for sure at one time this was necessary but, with some of the new technology, which I am not using all of yet, it appears that this part has changed and the Grub font is normally bigger than it used to be.

Have I been missing that point all this time - that using an HDMI cable negates the need for a larger font in Grub2?

---

### Post by Cavsfan on 2017-06-28
Fresh install on older computer Xubuntu Zesty Zapus 17.04 default grub update time **_5 minutes and 30 seconds_**:
With Arch Linux, Xubuntu Xenial Xerus 16.04 LTS, Xubuntu Zesty Zapus 17.04, [COLOR=#000000][FONT=&quot]Xubuntu[/FONT][/COLOR] Artful Aardvark 17.10 and Windows 10 also installed on it.
```
cavsfan@cavsfan-Le-Beast:/etc/grub.d$ lsa
total 100
drwxr-xr-x   2 root root  4096 Jun 28 21:50 .
drwxr-xr-x 147 root root 12288 Jun 28 21:29 ..
-rwxr-xr-x   1 root root  9783 Mar 30 17:45 [COLOR=#006400]00_header[/COLOR]
-rwxr-xr-x   1 root root  6258 Nov  1  2016 [COLOR=#006400]05_debian_theme[/COLOR]
-rwxr-xr-x   1 root root  2299 Jun 28 21:50 [COLOR=#006400]06_custom[/COLOR]
-rwxr-xr-x   1 root root 12676 Mar 30 17:45 [COLOR=#006400]10_linux[/COLOR]
-rwxr-xr-x   1 root root 11281 Mar 30 17:45 [COLOR=#006400]20_linux_xen[/COLOR]
-rwxr-xr-x   1 root root  1992 Jan 28  2016 [COLOR=#006400]20_memtest86+[/COLOR]
-rwxr-xr-x   1 root root 12059 Mar 30 17:45 [COLOR=#006400]30_os-prober[/COLOR]
-rwxr-xr-x   1 root root  1418 Mar 30 17:45 [COLOR=#006400]30_uefi-firmware[/COLOR]
-rwxr-xr-x   1 root root   214 Mar 30 17:45 [COLOR=#006400]40_custom[/COLOR]
-rwxr-xr-x   1 root root   216 Mar 30 17:45 [COLOR=#006400]41_custom[/COLOR]
-rw-r--r--   1 root root   483 Mar 30 17:45 README
```
It stopped and took the most time after 20_memtest86+ displayed.
```
cavsfan@cavsfan-Le-Beast:/etc/grub.d$ date && sudo update-grub && date
Wed Jun 28 [COLOR=#B22222]22:11:15[/COLOR] EDT 2017
Generating grub configuration file ...
Adding Arch Linux, Xubuntu Xenial Xerus 16.04 LTS, Xubuntu Zesty Zapus 17.04, [COLOR=#000000][FONT=&quot]Xubuntu[/FONT][/COLOR] Artful Aardvark 17.10 and Windows 10
Found linux image: /boot/vmlinuz-4.10.0-24-generic
Found initrd image: /boot/initrd.img-4.10.0-24-generic
Found linux image: /boot/vmlinuz-4.10.0-19-generic
Found initrd image: /boot/initrd.img-4.10.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 on /dev/sda1
Found Arch Linux on /dev/sda2
Found Ubuntu 16.04.2 LTS (16.04) on /dev/sda4
Found Ubuntu 17.04 (17.04) on /dev/sda6
done
Wed Jun 28 [COLOR=#b22222]22:14:38[/COLOR] EDT 2017
```

After customization 2 seconds:
```
cavsfan@cavsfan-Le-Beast:/etc/grub.d$ sudo chmod -x 10_linux
cavsfan@cavsfan-Le-Beast:/etc/grub.d$ sudo chmod -x 20_memtest86+
cavsfan@cavsfan-Le-Beast:/etc/grub.d$ sudo chmod -x 30_os-prober
cavsfan@cavsfan-Le-Beast:/etc/grub.d$ lsa
cavsfan@cavsfan-Le-Beast:/etc/grub.d$ lsa
total 100
drwxr-xr-x   2 root root  4096 Jun 28 21:50 .
drwxr-xr-x 147 root root 12288 Jun 28 21:29 ..
-rwxr-xr-x   1 root root  9783 Mar 30 17:45 [COLOR=#006400]00_header[/COLOR]
-rwxr-xr-x   1 root root  6258 Nov  1  2016 [COLOR=#006400]05_debian_theme[/COLOR]
-rwxr-xr-x   1 root root  2299 Jun 28 21:50 [COLOR=#006400]06_custom[/COLOR]
-rw-r--r--   1 root root 12676 Mar 30 17:45 10_linux
-rwxr-xr-x   1 root root 11281 Mar 30 17:45 [COLOR=#006400]20_linux_xen[/COLOR]
-rw-r--r--   1 root root  1992 Jan 28  2016 20_memtest86+
-rw-r--r--   1 root root 12059 Mar 30 17:45 30_os-prober
-rwxr-xr-x   1 root root  1418 Mar 30 17:45 [COLOR=#006400]30_uefi-firmware[/COLOR]
-rwxr-xr-x   1 root root   214 Mar 30 17:45 [COLOR=#006400]40_custom[/COLOR]
-rwxr-xr-x   1 root root   216 Mar 30 17:45[COLOR=#006400] 41_custom[/COLOR]
-rw-r--r--   1 root root   483 Mar 30 17:45 README
```
```
cavsfan@cavsfan-Le-Beast:/etc/grub.d$ date && sudo update-grub && date
Wed Jun 28 [COLOR=#b22222]22:16:45[/COLOR] EDT 2017
Generating grub configuration file ...
Adding Arch Linux, Xubuntu Xenial Xerus 16.04 LTS, Xubuntu Zesty Zapus 17.04, [COLOR=#000000][FONT=&quot]Xubuntu[/FONT][/COLOR] Artful Aardvark 17.10 and Windows 10
done
Wed Jun 28 [COLOR=#b22222]22:16:47[/COLOR] EDT 2017
```

---

### Post by deadflowr on 2017-06-29
You can use time like
```
time sudo update-grub
```
(Or at least I can)

---

### Post by Cavsfan on 2017-06-29
> **deadflowr said:**
> You can use time like
```
time sudo update-grub
```
(Or at least I can)

Thanks. I tried that and it didn't work. I just tried typing in time and it gave an error, so I went with date, which did work.

I dist-upgraded a fresh 17.04 install to a 17.10 install just now and do not know if that made any difference or not. But, it works now.

But, I at first just made my 06_custom executable because I could see grub would be updated and didn't want to go through the wait time.
Since that is all I did, it was slow so I thought I would time it like that. 5 and a half minutes versus 2 seconds; I'll take the 2 seconds any day of the week.

It's likely that on newer, faster computers perhaps with SSDs the time is not a factor but, for me now it most definitely is.

---

### Post by Cavsfan on 2017-07-19
Grub has gotten much more simple to customize over the last few Ubuntu versions. The Wiki has been noted with some * where entries are no longer required.

Now, you just need to basically drop a desktop sized picture - PNG works best into **/boot/grub/** and then add your colors to **/etc/grub.d/05_debian_theme**.

Create a file with your custom boot entries in **/etc/grub.d/06_custom**

Change your default boot line in **/etc/default/grub** (if you do not want the 1st one) and change the timeout (if you prefer something other than 10 seconds).

Update-grub and your are basically ready to go.

---

### Post by von Stalhein on 2017-07-21
Gee whiz Cavsfan, not having to spend hours chasing up obscure settings and avoiding screens and screens of cli work is going to upset the purists!!!
:lolflag:

---

### Post by Cavsfan on 2017-07-22
:lolflag:> **von Stalhein said:**
> Gee whiz Cavsfan, not having to spend hours chasing up obscure settings and avoiding screens and screens of cli work is going to upset the purists!!!

I guess you can still got through all of that if you want. But, when I went to using an HDMI to HDMI cable the letters were [SIZE=5]HUGE[/SIZE] and I had to comment the fonts out.
Then I discovered a few other things by accident that weren't needed with the newer versions of Grub.

:lolflag:

 I haven't gotten to look at Arch Linux grub but, Ubuntu grub definitely works without as much fiddling. :popcorn:

---

### Post by Cavsfan on 2017-07-28
I installed Artful Aardvark 17.10 a few days ago and as default, the fonts were big just like making the old fonts were with my non-HDMI cable.
So, I just edited **/etc/default/grub**, set the default, the timeout and that was it.
I then copied my **06_custom** file into /etc/grub.d/, made it executable and made these other 3 files unexecutable.
```
cavsfan@cavsfan-Le-Beast:/etc/grub.d$ lsa | grep -e "10_l" -e "20_m" -e "30_o"
-rw-r--r--   1 root root 12676 Jul  5 18:23 10_linux
-rw-r--r--   1 root root  1992 Jan 28  2016 20_memtest86+
-rw-r--r--   1 root root 12059 Jul  5 18:23 30_os-prober

```

**sudo update-grub** and bam I had everything but, the picture and colored fonts.

On older computers like mine that just have 4 partitions and logical partitions, grub does not see past the physical partitions.
So, to login to Zesty Zapus 17.04, which is on a logical partition sda6, it had it as sda4 and to boot into it I had to edit that boot line.

But, I don't have to any longer. ;)

---

### Post by Cavsfan on 2017-07-30
I spent a few hours today cleaning this wiki up: removing much of the unnecessary wording, the outdated material and hopefully simplified the whole thing.

I have to remove the one old outdated grub screenshot and add some newer ones and I think that is about all that is left.

If you get a chance take a look at it and see if it is cleaner and simpler to work with.

Also, feel free to post pictures of your grub screen. I use my phone camera, then upload it to my pc and post it on [http://en.zimagez.com/](http://en.zimagez.com/)

That site seems to be pretty stable. I have a login and can view pictures I've posted before. I know whatever site I used to post pics on vanished.

Here is my latest grub screen on Artful Aardvark 17.10:
 
[[img]http://en.zimagez.com/miniature/20170730134559.jpg[/img]](http://en.zimagez.com/zimage/20170730134559.php)

Regards

---

### Post by Bashing-om on 2017-07-30
Cavsfan; Hey ...

You do good work ,, Looks fine to me - simple and straight forward .

[INDENT][INDENT]when you are good
[INDENT][INDENT][INDENT]you are good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2017-07-30
I like to add a spacer line for separation if types of systems, my ISO files as configfile, and reboot or shutdown from grub in my 40_custom.
Although one time in testing the number to boot with, I tried to boot a spacer line. That did not too well.. 

```
# spacer line
menuentry " " {
set root= 
}

menuentry 'Live ISOs on SSD' {
configfile (hd0,5)/livecdimage.cfg
} 

menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 

# spacer line
menuentry " " {
set root=
}

menuentry "System restart" {
echo "System rebooting..."
insmod reboot
reboot
} 

menuentry "System shutdown" {
      echo "System shutting down..."
      insmod halt
      halt
}
```

---

### Post by Cavsfan on 2017-07-31
> **Bashing-om said:**
> Cavsfan; Hey ...

You do good work ,, Looks fine to me - simple and straight forward .[INDENT][INDENT]when you are good[INDENT][INDENT][INDENT]you are good
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thank you for looking it over! I had gotten way too wordy and there was so much unneeded junk in there I had to take it out.

Now, hopefully it is as straight forward as it can get and more people will use it because it is so simple now. 
I seen where in many places it could be confusing but, that should be gone now.

Now to add more up to date screenshots...

---

### Post by Cavsfan on 2017-07-31
> **oldfred said:**
> I like to add a spacer line for separation if types of systems, my ISO files as configfile, and reboot or shutdown from grub in my 40_custom.
Although one time in testing the number to boot with, I tried to boot a spacer line. That did not too well.. 

```
# spacer line
menuentry " " {
set root= 
}

menuentry 'Live ISOs on SSD' {
configfile (hd0,5)/livecdimage.cfg
} 

menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 

# spacer line
menuentry " " {
set root=
}

menuentry "System restart" {
echo "System rebooting..."
insmod reboot
reboot
} 

menuentry "System shutdown" {
      echo "System shutting down..."
      insmod halt
      halt
}
```

That's pretty nice. I might try that spacer menuentry sometime. Just curious as to why you use 40_custom as it would be on the bottom?

My son is going to sell me his 3 year old PC soon. He has a friend that is building him an even better one.

This is an i7 5th or 6th gen with 16GB memory, several SSDs and a 2 1TB SATA drive setup I believe in Raid 1. It boots up in about ~3 seconds.
He has an Nvidia GeForce GTX 1080 Ti, which he plans to sell because I'm not a gamer like he is.
Still much better than this nearly 10 year old PC i'm working from. It has been good to me though. I've just had to replace a few fans, including the CPU fan and the HD.

I expect my knowledge about the newer stuff will grow then.

I'v never shut it down except to clean it out or when severe storms passed by. I just put it in suspend mode or sleep on Windows 10.

I believe now I could make entries for the 2 kernels most people keep on Ubuntu but, why?

In 8-10 years of dealing with Linux I have not seen the need to boot into an older kernel not even once.
I don't care to have that many choices and have to scroll down to see them.

---

### Post by Bashing-om on 2017-07-31
Cavsfan; Hey; 

I throw my 2 cents in here .
> 
I believe now I could make entries for the 2 kernels most people keep on Ubuntu but, why?

In 8-10 years of dealing with Linux I have not seen the need to boot into an older kernel not even once.
I don't care to have that many choices and have to scroll down to see them.


1) The way I tend to mess around; there have been a number of times I was glad I kept an old booting kernel around :)
2) Many times I have assisted in re-installing a graphic's driver that is broke upon a new kernel install. Nice to have a fall back.
3) There are those times a new kernel just is not happy with the hardware; whereas the old kernel is fine - awaiting a kernel update ! 
4) Just having a back up for what ever might happen - is a good thing -> cheap insurance.

2 kernels. recovery kernels and maybe "upstart"  Though I have not touched upstart since the advent of systemd .

[INDENT]never can tell
[INDENT][INDENT][INDENT]what might happen[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Cavsfan on 2017-07-31
> **Bashing-om said:**
> Cavsfan; Hey; 

I throw my 2 cents in here .


1) The way I tend to mess around; there have been a number of times I was glad I kept an old booting kernel around :)
2) Many times I have assisted in re-installing a graphic's driver that is broke upon a new kernel install. Nice to have a fall back.
3) There are those times a new kernel just is not happy with the hardware; whereas the old kernel is fine - awaiting a kernel update ! 
4) Just having a back up for what ever might happen - is a good thing -> cheap insurance.

2 kernels. recovery kernels and maybe "upstart"  Though I have not touched upstart since the advent of systemd .[INDENT]never can tell[INDENT][INDENT][INDENT]what might happen[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


OK, I'll have to add that. People will have the option to add it or not; simple choice. But, choices are nice from what I gather. :)

I tried it once and failed but, I've come a long way since then. I managed to customize the Arch Linux grub which is somewhat different but, not that much. 
I tried to do that and couldn't figure it out at first then came back after a while and did it.
It seems like over the years my knowledge of Grub has grown, along with the input from others. I've learned a thing or two from **oldfred**.

LoL! I'm using Vivaldi now, an offshoot of Chrome I understand. I love it. But, control b will make something bold posting in the forum and it also brings up a tab with Bookmarks in it, so it does both.
But, I believe it uses less memory than Firefox. I use it in Windows 10 too as I've seen a pop-up warning me to close Firefox because I'm getting low on memory (I only have 4GB).
Pretty sad when I only have a spreadsheet and Firefox open. :p

If it was just me I'd do away with Windows but, I still have some uses for it, like helping friends with their problems, so it stays...

---

### Post by Cavsfan on 2017-07-31
@[COLOR=#000000]Bashing-om, check the Wiki now. I've added the ability to boot into the backup kernel.

I edited the 1st post and mentioned that as well as mentioned that it should be easier now.

See what you think.[/COLOR]

---

### Post by Bashing-om on 2017-07-31
Cavsfan; well ...
Hummm ...
> 
menuentry "Xubuntu Xenial Xerus 16.04 LTS (backup kernel)" {
    set root=(hd0,2)
        linux /vmlinuz.old root=/dev/sda2 ro [color=red]recovery nomodeset[/color]
        initrd /initrd.img.old

I would not think that we want a recovery console or to defeat kernel mode setting (nomodeset) on our back up kernel .
It is great that you advise there are choices !

Overall, though - looking better alla the time .

[INDENT][INDENT]like fine wine
[INDENT][INDENT][INDENT]get better with time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Cavsfan on 2017-08-01
> **Bashing-om said:**
> Cavsfan; well ...
Hummm ...

> [COLOR=#000000]*menuentry "Xubuntu Xenial Xerus 16.04 LTS (backup kernel)" {*[/COLOR]
[COLOR=#000000]*set root=(hd0,2)*[/COLOR]
[COLOR=#000000]*linux /vmlinuz.old root=/dev/sda2 ro *[/COLOR][COLOR=red]*recovery nomodeset*[/COLOR]
[COLOR=#000000]*initrd /initrd.img.old*[/COLOR]

I would not think that we want a recovery console or to defeat kernel mode setting (nomodeset) on our back up kernel .
It is great that you advise there are choices !

Overall, though - looking better alla the time .[INDENT][INDENT]like fine wine[INDENT][INDENT][INDENT]get better with time
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for pointing that error out. I fixed it as well as a couple of other things I spotted.
It should be good to go now but, let me know if you see anything else. I appreciate you taking the time to look at it.
I want nothing less than perfection on something as important as the Grub menu.

I was going to try it on Artful but, there I currently have only one kernel.
So, I got on Xenial and tried the backup kernel and it worked great.

Then later I got on Zesty and tried it there; it worked there too. So, I'd say it's good and will boot into the backup kernel.

Just now when I tried to boot into Artful I accidentally selected the backup kernel and it gave an error but, at least it just said press any key and took me back to the menu to select the right one.

So, :guitar:

Now, I just need to add some current example pictures.

---

### Post by Bashing-om on 2017-08-01
Cavsfan; Uh Huh /

Looking good .

You have no idea how many times and places I recommend your method(s). Yeah we want it right and the simpler the better .

But
[INDENT][INDENT]we do not knock what works :)
[/INDENT][/INDENT]

---

### Post by Cavsfan on 2017-08-01
> **Bashing-om said:**
> Cavsfan; Uh Huh /

Looking good .

You have no idea how many times and places I recommend your method(s). Yeah we want it right and the simpler the better .

But[INDENT][INDENT]we do not knock what works :)
[/INDENT]
[/INDENT]


Well, thank you very much! I really appreciate that! :)

---

### Post by Cavsfan on 2017-08-09
OK, so I finally added some new pictures to the Wiki with some current versions. 

I even found what I had always been meaning to add - the "Back to top" links.

See what you think. Did I get the "Back to top" links in the proper places?

Cheers

---

### Post by Bashing-om on 2017-08-09
Cavsfan; Yepper .

Look'n good . The - "Back to top" links  are a nice touch and are functional . The link makes it so much easier for someone to make sure their thoughts are in order :)

[INDENT]just goes to show - no matter how good
[INDENT][INDENT][INDENT]can always be better
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Cavsfan on 2017-08-09
> **Bashing-om said:**
> Cavsfan; Yepper .

Look'n good . The - "Back to top" links  are a nice touch and are functional . The link makes it so much easier for someone to make sure their thoughts are in order :)[INDENT]just goes to show - no matter how good[INDENT][INDENT][INDENT]can always be better
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for taking a good look at it for me! :) 

I hope the word gets around that's it's much, much simpler to do now.

I tried my best to change it to a logical order that one can follow in sequence. 
Before you had to jump around from here to there and back, etc.

BTW, I found that the default Grub takes a long time updating when it's looking at **/etc/grub.d/30_os-prober**.
Probably because my system is so old and there often are 3 to 5 systems on it. It takes 3-5 minutes at that point for me.
It's torturous for me to go through a kernel installation where it updates Grub twice.
But, once customized it takes 2-3 seconds to update.

---

### Post by Cavsfan on 2017-08-22
[s]I just discovered something interesting about recovery mode. I had the 17.10 alpha installed on a partition and accidentally installed the nVidia driver, which I knew would not work, so I tried to cancel it.

That did not work so, I tried recovery mode, dropped to a root shell and since it is read only I could not purge the nVidia driver, etc. so I edited the grub line and made it read/write. That worked like it should have in the first place.

So, I updated the Wiki for the Recovery line to be **rw** instead of **ro**. 

I do not know why you would want to boot into recovery mode read-only when you are trying to fix your system; seems odd to me.
If you do not know what you are doing, you should not be in recovery mode in the first place, if that is why it is read only.

But, this sure saved me from doing another install of Artful 17.10. Plus why have to go through the process of editing the grub line to change it from ro to rw?

Win win I do believe....[/s]

If you find yourself needing to use recovery mode to drop to a root shell and do not have access to make the necessary updates, do this:
edit the recovery line at boot time and change the **ro recovery nomodeset** to **rw recovery nomodeset** so it will be a temporary change.

That will accomplish what you need.

---

### Post by oldfred on 2017-08-22
I thought it was read only so you could run fsck.
And does not recovery mode give a menu anymore, it used to have a menu with several options including command line with Internet, or continue booting, plus others?

---

### Post by Cavsfan on 2017-08-22
> **oldfred said:**
> I thought it was read only so you could run fsck.
And does not recovery mode give a menu anymore, it used to have a menu with several options including command line with Internet, or continue booting, plus others?

Thanks for the reply! 

Yes, it gives you the menu. The first item is normal boot and there are several others just as it has been normally. 
I did not see a command line with internet, only an option to get the network started, then it comes back to that menu; this alpha failed to get the network started but, I didn't need that.
But, when I selected the option to drop to a root shell and purge the nVidia files I had installed it gave me errors because I was in read-only mode.

I tried to cancel out of installing them but, it was too late and 17.10 will not boot up with an nVidia driver installed this early.

Not sure why you would want to be in read/only mode to run fsck or how being in read/write mode could hurt that either.

But, when dropping to a root shell to fix your system read only mode will not allow it.

Arch Linux uses read/write mode for every boot option, I just made the recovery mode read/write mode because there is no problem during a normal boot in Ubuntu.

Do you foresee a problem booting into recovery mode in read/write mode?

---

### Post by oldfred on 2017-08-22
With fsck the partition must be unmounted, so that may be the same as ro?
Otherwise I do not know.

---

### Post by Cavsfan on 2017-08-22
> **oldfred said:**
> With fsck the partition must be unmounted, so that may be the same as ro?
Otherwise I do not know.

Thanks, I'll check into it.

---

### Post by Cavsfan on 2017-08-22
> **oldfred said:**
> With fsck the partition must be unmounted, so that may be the same as ro?
Otherwise I do not know.

Thank you very much for jumping on that so quick and pointing out that which I did not think of. 
That is not a good idea what I was doing, maybe just for the fsck part but, that is enough to stop it.

I corrected the Wiki and post [#446]("https://ubuntuforums.org/showthread.php?t=2076205&page=45&p=13678930#post13678930") to say to change the ro to rw ONLY at boot time and ONLY for that one purpose.

I've learned my lesson about making decisions based on Alpha systems. I tried it on Zesty 17.04 and got the same thing; it was sort of iffy.
But, when I went to Xenial Xerus 16.04.3 it really showed me that it was the wrong thing to do.

Thanks again! :)

---

### Post by Bashing-om on 2017-08-22
Cavsfan; Uh Huh /

Concur that mounting the file system r/w is not a good thing to contemplate.
Even in the normal boot it is initially mounted ro .
```

cat /proc/cmdline
cat /var/log/Xorg.0.log | grep -i "command line"

```
Only remounted as rw after initramfs completes (??) .

[INDENT][INDENT]got to be a reason it is done this way
[/INDENT][/INDENT]

---

### Post by Cavsfan on 2017-08-22
> **Bashing-om said:**
> Cavsfan; Uh Huh /

Concur that mounting the file system r/w is not a good thing to contemplate.
Even in the normal boot it is initially mounted ro .
```

cat /proc/cmdline
cat /var/log/Xorg.0.log | grep -i "command line"

```
Only remounted as rw after initramfs completes (??) .[INDENT][INDENT]got to be a reason it is done this way
[/INDENT]
[/INDENT]


Thanks for confirming that!

---

### Post by Cavsfan on 2017-09-23
This is so easy to do now, I just installed Ubuntu 17.10 and customized it from memory. I've never done that before.

---

### Post by Cavsfan on 2018-02-07
I deleted the part that contained this as both the new and backup kernels are in the Grub menu now.

> **Just in Case**

[COLOR=#333333][FONT=Ubuntu]If you need to access an older kernel or for any reason need to see the regular menu entries. 
(If you are multi-booting more than one Ubuntu and the one you want to see the other kernels is not where your Grub is installed. 
Login to that Ubuntu and if it is not possible to get into the system normally, Recovery for that system will do the job. 
Choose "root console" from the Recovery menu.) 
Enter **sudo grub-install /dev/sda** (where sda is the disk it is installed on) **sudo blkid -c /dev/null** will show the correct one if it is not known. [/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Enter this: 
**sudo chmod +x /etc/grub.d/10_linux && sudo update-grub** and/or 
**sudo chmod +x /etc/grub.d/30_os-prober && sudo update-grub**, reboot and the menu entries will be restored.[/FONT][/COLOR]

---

### Post by Cavsfan on 2018-03-16
Since the previous website I had pictures on went down. Here is a new one with my current and latest grub screen:

[[img]http://i.imgur.com/WGaf0xtl.jpg[/img]](https://imgur.com/WGaf0xt)

---

### Post by Cavsfan on 2018-03-16
I just added Restart and Shutdown as the bottom two options in the 06_custom file in Section [1.4.3]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries").

---

### Post by von Stalhein on 2018-03-22
> **Cavsfan said:**
> I just added Restart and Shutdown as the bottom two options in the 06_custom file in Section [1.4.3]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries").  Thanks Cavsfan, appreciate your work!

---

### Post by Cavsfan on 2018-03-24
> **Cavsfan said:**
> I just added Restart and Shutdown as the bottom two options in the 06_custom file in Section [1.4.3]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries").

> **von Stalhein said:**
> Thanks Cavsfan, appreciate your work!

You are most welcome!

---

### Post by Cavsfan on 2018-03-29
You gotta love Ubuntu Grub as it has 3 different colors. Arch Linux is cool but, it only has 2 colors.

This is on my new Bionic Beaver 18.04 install.

And I can attest to the fact that the picture is what makes Grub use the colors because yesterday I initially forgot to copy a picture to /boot/grub/ and the colors were black and white.
Once I added the picture, the colors appeared. 

[[IMG]http://i.imgur.com/4x43scIl.jpg[/IMG]]("https://imgur.com/4x43scI")

---

### Post by cecilpierce on 2018-04-02
How can I add Burg boot loader to Bionic Beaver ?

---

### Post by cecilpierce on 2018-04-02
How can I add Burg boot loader to Bionic Beaver ?

Sorry for the repost 1

---

### Post by oldfred on 2018-04-02
Burg has not been supported for years. Best not to use it.
If using BIOS, this thread is your best source for grub configuration.

If you have a newer (last 5 years) hardware and it will be UEFI. And and installs should be UEFI.
Then you can use rEFInd boot manager which also is a gui.
 [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) 

New UEFI systems have their own boot manager (menu).
Grub is both the boot manager and boot loader for most Linux systems.

---

### Post by Cavsfan on 2018-04-22
@oldfred, I'm slowly coming to the conclusion that an UEFI computer cannot be customized in the same manor as Legacy MBR partitioning allowed.

I've got a newer computer and have everything installed on a 480GB SSD UEFI - Windows 10, Arch Linux and Xubuntu 16.04 so far and the Xubuntu kernels are named differently.
Instead of the generic names:
**linux /vmlinuz**
**initrd /initrd.img**

In EFI they are:
[B]linux /boot/vmlinuz-4.13.0-38-generic
****interd /boot/initrd.img-4.13.0-38-generic[/B]

This would require editing the custom entries every time a new kernel gets installed, which is the exact opposite reason this idea came about. There is a whole lot more than just the kernel names it appears too.

What do you think?

---

### Post by Dennis N on 2018-04-22
> This would require editing the custom entries every time a new kernel gets installed, which is the exact opposite reason this idea came about... 

Just a comment (pardon me for butting in before oldfred).

/vmlinuz and /initrd.img are just symbolic links to the newest kernel, and they function the same regardless of whether you installed under UEFI or BIOS. So that should be no problem, at least when sticking with Ubuntu flavors or Linux Mint. 

Other distros (like Fedora) don't use these symbolic links but it is still possible to have a maintainance free system including those on a UEFI system. I don't think it's always possible with BIOS. So advantage to UEFI.

---

### Post by oldfred on 2018-04-22
+1 on Dennis N's comments.

I am still using 40_custom as you and Ranch Hand recommened way back when. And now I only have UEFI.

I turn off os-prober and use 40_custom to boot other installs.
The issue I have with Ubuntu's version of grub is that it is hard coded to "ubuntu" throughout. Other versions of grub seem to use this:
efi_distributor = bootloader_id; I did see a bug report long time ago where someone wanted an entry for Kubuntu so that modified grub like this from:
install_efi_ubuntu_flavours.patch
       efi_distributor = bootloader_id;
+      if (strcmp (efi_distributor, "kubuntu") == 0)
+    efi_distributor = "ubuntu";
       switch (platform)

I do not understand the c code, but they replace Ubuntu with Kubuntu.

I have wanted different distributors so I could directly boot more than one Ubuntu directly from UEFI. But all install to one ESP or /EFI/ubuntu.

---

### Post by Cavsfan on 2018-04-22
> **Dennis N said:**
> Just a comment (pardon me for butting in before oldfred).

/vmlinuz and /initrd.img are just symbolic links to the newest kernel, and they function the same regardless of whether you installed under UEFI or BIOS. So that should be no problem, at least when sticking with Ubuntu flavors or Linux Mint. 

Other distros (like Fedora) don't use these symbolic links but it is still possible to have a maintainance free system including those on a UEFI system. I don't think it's always possible with BIOS. So advantage to UEFI.

> **oldfred said:**
> +1 on Dennis N's comments.

I am still using 40_custom as you and Ranch Hand recommened way back when. And now I only have UEFI.

I turn off os-prober and use 40_custom to boot other installs.
The issue I have with Ubuntu's version of grub is that it is hard coded to "ubuntu" throughout. Other versions of grub seem to use this:
efi_distributor = bootloader_id; I did see a bug report long time ago where someone wanted an entry for Kubuntu so that modified grub like this from:
install_efi_ubuntu_flavours.patch
       efi_distributor = bootloader_id;
+      if (strcmp (efi_distributor, "kubuntu") == 0)
+    efi_distributor = "ubuntu";
       switch (platform)

I do not understand the c code, but they replace Ubuntu with Kubuntu.

I have wanted different distributors so I could directly boot more than one Ubuntu directly from UEFI. But all install to one ESP or /EFI/ubuntu.

Boy, that is some good news! Thanks Dennis for the comments. I thought this Wiki was going to become obsolete with EFI Boot.

 @oldfred, those are also encouraging words! When I first installed Xubuntu 16.04 LTS, the grub would not even boot back into Xubuntu for some reason.

Luckily, in BIOS, I was able to change it to Arch_grub and it booted just fine into anything.

I'll work on it some more and see if I can come with what needs done for EFI, this stuff is Greek to me. :P

But, that which doesn't kill you, makes you stronger! :lolflag:

---

### Post by oldfred on 2018-04-23
I quickly learned to backup ESP - efi system partition.
Each install of Ubuntu overwrites the previous install in ESP. But it is only 3 lines as configfile to find full grub.cfg in your install. So now I often just manually edit to correct UUID & partition.
But editing ESP requires changes or use of live flash drive, I know try to remember to change setting while still in live installer, but some newer versions do not let install user 999 edit anything else.

In fstab is a setting on mounting ESP. With 14.04 it was defaults, but now they change it to 'umask=0077' or no permissions. I may change settings back to that, as I assume it is for security. With defaults any user in your system could change settings since with FAT32 only ownership & permissions are set at mounting. But I keep finding many times I want to change, backup or edit something in ESP. Note that Boot-Repair also changes to defaults so it can edit settings.

After my last install of bionic and with fstab permissions set so I can access it.
       sudo cp -a /boot/efi/EFI/ubuntu/ /boot/efi/EFI/bionic
sudo cp -a /boot/efi/EFI/ubuntu_bu/grub.cfg /boot/efi/EFI/ubuntu/grub.cfg 

```
fred@Asusz97:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

I installed Fedora, more just to see difference with grub2 than for any other reason. When I installed Fedora to sdb I told it to install grub to ESP on sdb which I do with Ubuntu, but Ubuntu never does. I was presently surprised that Fedora's grub2 did install to ESP on sdb. but it has full grub.cfg embedded in the .efi boot file and some caution on how to reinstall grub or grub2 defaults to a different configuration than Fedora's default.I prefer that Ubuntu's grub.cfg is separate.

---

### Post by Cavsfan on 2018-04-23
> **oldfred said:**
> I quickly learned to backup ESP - efi system partition.
Each install of Ubuntu overwrites the previous install in ESP. But it is only 3 lines as configfile to find full grub.cfg in your install. So now I often just manually edit to correct UUID & partition.
But editing ESP requires changes or use of live flash drive, I know try to remember to change setting while still in live installer, but some newer versions do not let install user 999 edit anything else.

In fstab is a setting on mounting ESP. With 14.04 it was defaults, but now they change it to 'umask=0077' or no permissions. I may change settings back to that, as I assume it is for security. With defaults any user in your system could change settings since with FAT32 only ownership & permissions are set at mounting. But I keep finding many times I want to change, backup or edit something in ESP. Note that Boot-Repair also changes to defaults so it can edit settings.

After my last install of bionic and with fstab permissions set so I can access it.
       sudo cp -a /boot/efi/EFI/ubuntu/ /boot/efi/EFI/bionic
sudo cp -a /boot/efi/EFI/ubuntu_bu/grub.cfg /boot/efi/EFI/ubuntu/grub.cfg 

```
fred@Asusz97:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

I installed Fedora, more just to see difference with grub2 than for any other reason. When I installed Fedora to sdb I told it to install grub to ESP on sdb which I do with Ubuntu, but Ubuntu never does. I was presently surprised that Fedora's grub2 did install to ESP on sdb. but it has full grub.cfg embedded in the .efi boot file and some caution on how to reinstall grub or grub2 defaults to a different configuration than Fedora's default.I prefer that Ubuntu's grub.cfg is separate.

Thanks for all of that information. I'm brain dead today, I'll definitely make notes and re-read that tomorrow.

You should see the way you have to do grub-install on Arch, it isn't to a simple drive like /dev/sda.

It is like this:
```
grub-install --target=x86_64-efi --efi-directory=/boot/grub/x86_64-efi/ --bootloader-id=ArchLinux
```

---

### Post by oldfred on 2018-04-23
That is the full grub command, I think other installs build the command by adding the parameters they want. 
I have used that type of command to just install grub to a smaller flash drive with just ISO so I could boot the ISO with grub. But now normally do a full install as larger flash drives are now relatively inexpensive.

---

### Post by Cavsfan on 2018-04-24
I guess I've got a lot to learn about this EFI stuff. I've noticed over the last few years that you have developed a lot of knowledge about EFI.

I'll probably be checking out the link in your signature A LOT! :)

---

### Post by Cavsfan on 2018-04-24
> **oldfred said:**
> I quickly learned to backup ESP - efi system partition.
Each install of Ubuntu overwrites the previous install in ESP. But it is only 3 lines as configfile to find full grub.cfg in your install. So now I often just manually edit to correct UUID & partition.
But editing ESP requires changes or use of live flash drive, I know try to remember to change setting while still in live installer, but some newer versions do not let install user 999 edit anything else.

In fstab is a setting on mounting ESP. With 14.04 it was defaults, but now they change it to 'umask=0077' or no permissions. I may change settings back to that, as I assume it is for security. With defaults any user in your system could change settings since with FAT32 only ownership & permissions are set at mounting. But I keep finding many times I want to change, backup or edit something in ESP. Note that Boot-Repair also changes to defaults so it can edit settings.

After my last install of bionic and with fstab permissions set so I can access it.
       sudo cp -a /boot/efi/EFI/ubuntu/ /boot/efi/EFI/bionic
sudo cp -a /boot/efi/EFI/ubuntu_bu/grub.cfg /boot/efi/EFI/ubuntu/grub.cfg 

```
fred@Asusz97:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

I installed Fedora, more just to see difference with grub2 than for any other reason. When I installed Fedora to sdb I told it to install grub to ESP on sdb which I do with Ubuntu, but Ubuntu never does. I was presently surprised that Fedora's grub2 did install to ESP on sdb. but it has full grub.cfg embedded in the .efi boot file and some caution on how to reinstall grub or grub2 defaults to a different configuration than Fedora's default.I prefer that Ubuntu's grub.cfg is separate.

Glad I read this thoroughly before I installed Bionic on this computer! You're saying to backup the contents of **/boot/efi/EFI/ubuntu/** which would include the **/boot/efi/EFI/ubuntu/grub.cfg** file.
So, what is the 2nd copy statement for? Copying the one you want to boot with back into that folder?

What is the problem with the **/boot/efi/EFI/ubuntu/** folder being written over with each subsequent install of Ubuntu?
Sounds like the grub in control moves to the next installation like normal but, this is different somehow?

Possibly the making copies of that **ubuntu** folder and simply copying the one you want to boot from into it negates the need to do a grub-install on the system you want to boot from?

Well, that's 5 questions and if we were playing 20 questions I'd have 15 more. :P

Thanks for sharing!

---

### Post by Dennis N on 2018-04-24
> What is the problem with the /boot/efi/EFI/ubuntu/ folder being written over with each subsequent install of Ubuntu?
Sounds like the grub in control moves to the next installation like normal but, this is different somehow?

No it's not different. And it's only a problem if you want to continue using the previous Ubuntu to boot by default. I'm not concerned by this since I use a non-Ubuntu OS (Manjaro) to boot by default and its ESP files don't get overwritten by anything.  
> Possibly the making copies of that ubuntu folder and simply copying the one you want to boot from into it negates the need to do a grub-install on the system you want to boot from?
Saving it and copying it back just saves you from editing the grub.cfg file in the ESP. You can choose not to save and restore the old ubuntu folder (or its grub.cfg). Just use the terminal and edit the newly-installed grub.cfg in the ESP to be like the old one.

---

### Post by oldfred on 2018-04-24
I have several copies of my ESP.
I copy most of it to the ESP on sdb.
I also copy my main working install to another folder in my ESP, so I have both the versions of grub & grub.cfg or anything else in it.
I usually end up using the newest vesion's shimx64.efi or grubx64.efi, but older versions grub.cfg. So far no issues with version of grub in ESP and rest of grub configuration files in an install.
So I just edit grub.cfg or copy back the grub.cfg from my other folder.

```
fred@Asusz97:~$ ll /boot/efi/EFI
total 44
drwxr-xr-x 11 root root 4096 Sep  6  2017 ./
drwxr-xr-x  4 root root 4096 Dec 31  1969 ../
drwxr-xr-x  2 root root 4096 Apr 15  2016 asus_ar/
drwxr-xr-x  2 root root 4096 May  9  2017 Boot/
drwxr-xr-x  2 root root 4096 Aug 28  2017 debian/
drwxr-xr-x  3 root root 4096 Sep 26  2016 mate/
drwxr-xr-x  2 root root 4096 Apr 23  2015 trusty/
drwxr-xr-x  3 root root 4096 Feb 19 12:53 ubuntu/
drwxr-xr-x  2 root root 4096 Sep  6  2017 ubuntu_mate/
drwxr-xr-x  2 root root 4096 Jul 31  2017 xenial/
drwxr-xr-x  2 root root 4096 Aug 16  2016 yakkety/

```
My other system has bionic folder, so not shown here.

---

### Post by Cavsfan on 2018-04-25
Ok, I see this a little more clearly now.
I also have Arch Linux, which I installed after Windows 10.

So on Arch this is what I have (I backed up the ubuntu folder to xenial while in Xenial, like you recommended.
```
[cavsfan@ArchLinux ~]$ ls /boot/EFI/
[COLOR="#0000FF"]Arch_grub[/COLOR]  [COLOR="#0000FF"]Boot [/COLOR] [COLOR="#0000FF"]Microsoft[/COLOR]  [COLOR="#0000FF"]ubuntu[/COLOR]  [COLOR="#0000FF"]xenial[/COLOR]
```

So this would be the way to install grub to a ubuntu partition. If needed after the initial install.
```
grub-install --target=x86_64-efi --efi-directory=/boot/grub/x86_64-efi/ --bootloader-id=ubuntu
```

---

### Post by Cavsfan on 2018-04-25
I've got so much to do. New hardware requires special treatment it would appear. 
I have a Soundblaster Audigy 5/Rx sound card, which Arch picked up on but, It isn't the default and getting that solved is one trick I need to do.

I need to get that sound card working on Xubuntu Xenial Xerus 16.04 plus a lot of other stuff on that system like resizing the conkys to fit this ginormous monitor.
Think the sound card works some places and not others on that system too.

Also need to play around with the grub so I can get that figured out for this wiki.

Then tomorrow Bionic Beaver 18.04 LTS is released, so installing that and then the same thing as above on that system.

There is not enough time in the day...

---

### Post by Cavsfan on 2018-04-25
One good thing about EFI boot is that I totally messed my grub up in Arch and could not boot into anything.

So, on the old computer I was downloading an ISO so I could do a live boot repair, then suddenly realized maybe that was not necessary.

I rebooted and got into BIOS and changed the boot to the Ubuntu grub and it worked.
It had no way to get into Arch because it got an error on **30_os-prober** so I was able to copy my custom grub file from Arch into Xubuntu 16.04.
(The custom grub file is really identical to the regular grub entries just in my order - for now.)

I ran update-grub and it didn't get any errors this time.

Rebooted via BIOS into the Ubuntu grub and selected Arch and I was back in.

It was already set to default boot with Arch grub so I recovered the easy way.

---

### Post by oldfred on 2018-04-25
It is one advantage of UEFI, that you in effect have the equivalent of many MBRs all on one drive.
Each folder in ESP can be a different boot entry. And that is where I wish I could rename different Ubuntu flavors or even different test Ubuntu installs to boot from UEFI, not just grub.
Those booting other distributions than can from UEFI boot menu boot any of them directly.

UEFI is a boot manager/menu, grub is a boot menu & boot loader. So you have two menus to choose from.

---

### Post by Cavsfan on 2018-04-29
I installed Bionic Beaver 16.04 LTS and the grub got everything but part of the Arch Linux kernel correct.
The last 2 lines in Xubuntu:
```
    linux /vmlinuz-linux root=/dev/sdc5 rw quiet
    initrd /intel-ucode.img

```

It put the Microcode img but it left off the initramfs Arch img:
```
    linux /vmlinuz-linux root='/dev/sdc5' rw  quiet
    initrd /intel-ucode.img [COLOR=#0000ff]/initramfs-linux.img[/COLOR]
```

Good thing I had the lts kernel installed as it does not use the Microcode img and it got that one right.

---

### Post by Roger_Williams on 2018-05-07
On my laptop I’m multi-booting Ubuntu, Kubuntu and Kali. Ubuntu is my main OS and runs on my internal while Kubuntu and Kali are on seperate external SSDs. My problem is that Kubuntu and Ubuntu are labelled as “Ubuntu” in the Grub menu. I want to edit it to distinguish between the two. I read the Wiki a bit and I think below is what I want to do to get them labelled properly. Am I correct?

> **Cavsfan said:**
> I installed 3 more systems - Lucid, Precise and Quantal on separate partitions to keep the grub files generic in case anyone needs a copy of the original file.

I got an upgrade to grub and it gave me some errors. Luckily I had a copy of **05_debian_theme** to fix the error.

I had to edit fstab every time I installed another system as it would pull all of the swap partitions into fstab.
There is a section on editing fstab when installing or reinstalling Ubuntu in the wiki in my signature in section 1.7.

It would be very difficult to maneuver the long menu without customizing it as I have.
Here is what my grub2 screen currently looks like with 7 operating systems:

[[IMG]http://ompldr.org/tZzJpNg[/IMG]]("http://ompldr.org/vZzJpNg")

Here is the output of **sudo blkid**:

```
/dev/sda1: LABEL="C:" UUID="1CFC7A8DFC7A60C6" TYPE="ntfs" 
/dev/sda2: LABEL="Lucid" UUID="a162dc8a-e4df-4b79-b4c3-524761ff7ae1" TYPE="ext4" 
/dev/sda3: UUID="2a80f59e-e7c3-418e-aab2-ab5d19255a2f" TYPE="swap" 
/dev/sda5: LABEL="Precise" UUID="3b8b1954-24e6-4a5e-9074-70a1a94ed4be" TYPE="ext4" 
/dev/sda6: UUID="82c51b29-023f-4964-99b6-67b45a49527f" TYPE="swap" 
/dev/sda7: LABEL="Quantal" UUID="b5fc902c-0bf0-45b3-95a1-29f3c46dfe6a" TYPE="ext4" 
/dev/sda8: UUID="69ac3efc-8a8a-4056-89e0-59bb81c2f468" TYPE="swap" 
/dev/sda9: LABEL="Lucid-Generic" UUID="109c11d0-71e3-41a4-87da-9e81535499a5" TYPE="ext4" 
/dev/sda10: UUID="24aa8c8b-53dc-4ecc-852b-ff2c25c8b342" TYPE="swap" 
/dev/sda11: LABEL="Precise-Generic" UUID="50104efb-d918-45a9-985e-a70c60e87ac0" TYPE="ext4" 
/dev/sda12: UUID="139390a6-2fe1-4ff2-b650-88ae3b0586c1" TYPE="swap" 
/dev/sda13: UUID="580e8c62-78ce-44a2-93e3-ccebd37c3acc" TYPE="ext4" LABEL="Quantal-Generic" 
/dev/sda14: UUID="ec3048b8-c644-435a-93bb-08bb4975d0db" TYPE="swap" 
/dev/sdb1: LABEL="Fantom" UUID="78B8D1A1B8D15DE6" TYPE="ntfs"
```

They are easy to recognize since they have all been labeled as explained in 1.6 of the wiki.

I will try to put the generic grub files on the wiki but, if any one needs a copy of something let me know and I will post the contents of the file here.

---

### Post by oldfred on 2018-05-07
I do have issues with my entires. I had USB SSD installed & flash drive and all my hd0, became hd2. I had to experiment to see which was correct.

This is my 40_custom:

```
fred@Xenial_z97:~$ cat /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Xenial on sdb3" {
    set root=(hd1,gpt3)
        linux /vmlinuz root=/dev/sdb3 ro quiet splash
        initrd /initrd.img
}

menuentry "Bionic 18.04 on sda7 configfile" {
configfile (hd0,gpt7)/boot/grub/grub.cfg 
}

menuentry "Bionic 18.04 on sda7" {
    set root=(hd0,gpt7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}


menuentry "Bionic 18.04 on SSD" {
    set root=(hd3,gpt3)
        linux /vmlinuz root=/dev/sdc3 ro quiet splash
        initrd /initrd.img
}

menuentry "Artful 17.10 on sdb9" {
    set root=(hd1,gpt9)
        linux /vmlinuz root=/dev/sdb9 ro quiet splash
        initrd /initrd.img
}

menuentry "Ubuntu 9 on sdb8" {
    set root=(hd1,gpt10)8
        linux /vmlinuz root=/dev/sdb8 ro quiet splash
        initrd /initrd.img
}


menuentry "Mate 16.10 on sdb10" {
    set root=(hd1,gpt10)
        linux /vmlinuz root=/dev/sdb10 ro quiet splash
        initrd /initrd.img
}


menuentry "USB SSD on sdc3" {
    set root=(hd2,gpt3)
        linux /vmlinuz root=/dev/sdc3 ro quiet splash
        initrd /initrd.img
}

# spacer line
menuentry " " {
set root= 
}

menuentry 'Live ISOs on SSD' {
configfile (hd0,5)/livecdimage.cfg
} 

menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 

# spacer line
menuentry " " {
set root=
}

menuentry "System restart" {
echo "System rebooting..."
insmod reboot
reboot
} 

menuentry "System shutdown" {
      echo "System shutting down..."
      insmod halt
      halt
}

# Boot whatever is in the CD drive
menuentry "CD on (cdrom/dvd)" {
    set root=(cd0)
    chainloader /EFI/BOOT/grubx64.efi

```

---

### Post by Roger_Williams on 2018-05-07
Thank you this will help so much &#128516;

> **oldfred said:**
> I do have issues with my entires. I had USB SSD installed & flash drive and all my hd0, became hd2. I had to experiment to see which was correct.

This is my 40_custom:

```
fred@Xenial_z97:~$ cat /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Xenial on sdb3" {
    set root=(hd1,gpt3)
        linux /vmlinuz root=/dev/sdb3 ro quiet splash
        initrd /initrd.img
}

menuentry "Bionic 18.04 on sda7 configfile" {
configfile (hd0,gpt7)/boot/grub/grub.cfg 
}

menuentry "Bionic 18.04 on sda7" {
    set root=(hd0,gpt7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}


menuentry "Bionic 18.04 on SSD" {
    set root=(hd3,gpt3)
        linux /vmlinuz root=/dev/sdc3 ro quiet splash
        initrd /initrd.img
}

menuentry "Artful 17.10 on sdb9" {
    set root=(hd1,gpt9)
        linux /vmlinuz root=/dev/sdb9 ro quiet splash
        initrd /initrd.img
}

menuentry "Ubuntu 9 on sdb8" {
    set root=(hd1,gpt10)8
        linux /vmlinuz root=/dev/sdb8 ro quiet splash
        initrd /initrd.img
}


menuentry "Mate 16.10 on sdb10" {
    set root=(hd1,gpt10)
        linux /vmlinuz root=/dev/sdb10 ro quiet splash
        initrd /initrd.img
}


menuentry "USB SSD on sdc3" {
    set root=(hd2,gpt3)
        linux /vmlinuz root=/dev/sdc3 ro quiet splash
        initrd /initrd.img
}

# spacer line
menuentry " " {
set root= 
}

menuentry 'Live ISOs on SSD' {
configfile (hd0,5)/livecdimage.cfg
} 

menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 

# spacer line
menuentry " " {
set root=
}

menuentry "System restart" {
echo "System rebooting..."
insmod reboot
reboot
} 

menuentry "System shutdown" {
      echo "System shutting down..."
      insmod halt
      halt
}

# Boot whatever is in the CD drive
menuentry "CD on (cdrom/dvd)" {
    set root=(cd0)
    chainloader /EFI/BOOT/grubx64.efi

```

---

### Post by Roger_Williams on 2018-05-07
Running the commands what I could find is the following shown below. Ubuntu was install in UEFI mode and I'm pretty sure Kubuntu was as well. So I'm guessing that sda2 is Kubuntu. How do I figure out the drive number though? Like here how you have "set root=(hd1,gpt3)".Yes I am a noob. Ubuntu and Kubuntu use the entire disk they are installed on while Kali has a swap. I'm pretty sure I have everything setup but I've commented out the changes I made to the 06_custom until I know that it's all correct.

Ubuntu: /dev/sdb2
Kali: /dev/sdd1

 /dev/sda1: UUID="1B0A-70B6" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="e7732e71-000a-43a6-b259-327d87412d3a"


/dev/sda2: UUID="e9c24939-98c7-4af4-9431-e9f7c3772a40" TYPE="ext4" PARTUUID="7b19e85f-63c4-4927-b7c7-c419fd17db6b"


/dev/sdb1: UUID="EA33-3A4D" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="3d2c10dd-1e64-4c6a-b8e1-f0adbb541229"


Ubuntu /dev/sdb2: UUID="b66785e3-d995-470a-98c7-7fa86297e40f" TYPE="ext4" PARTUUID="8f2a7053-4205-4d22-a38d-e9c0d93a64d7"


/dev/sdc1: PARTUUID="3653f0a2-01"


Kali /dev/sdd1: UUID="9e01f911-304a-43b2-b188-afa894dee1ba" TYPE="ext4" PARTUUID="a0a68dd4-01"


/dev/sdd5: UUID="75bc88c8-16a8-4d5b-bda1-532b7cdd6640" TYPE="swap" PARTUUID="a0a68dd4-05"

---

### Post by oldfred on 2018-05-07
Drives should match how once booted they become devices. Or hd0 should be sda.
But UEFI or BIOS may see drives differently. Maybe due to timing?
I thought drives were enumerated by UEFI/BIOS by SATA port order. But I try to use SATA0 as first port. But then when I plug a flash drive as sdc, on reboot it is hd0. But may be sdc or sda?

Depending on what extra flash drive(s) I have plugged in, I often have to manually edit the custom boot entries that use hd0. They my be hd1 or hd2 even. Same with sdb that should be hd1, may then be hd2. And then if I unplug flash drive and reboot, it is back to hd0.

Or sometimes you just have to experiment, when grub gives error message. It usually goes back to grub menu, so you can try again.

If not a removable drive, I probably should be using UUID as the set root command.
This is what UEFI uses in its grub to find full grub using configfile.

```
fred@Xenial_z97:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
#search.fs_uuid 8c92557f-cc60-438b-b1ea-ffea0adf0a1a root hd0,gpt7 
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

---

### Post by deadflowr on 2018-05-07
> My problem is that Kubuntu and Ubuntu are labelled as &#8220;Ubuntu&#8221; in the Grub menu. I want to edit it to distinguish between the two. I read the Wiki a bit and I think below is what I want to do to get them labelled properly. Am I correct?
The partition label and the grub name are different.
(But it's really helpful to rename the partition labels though anyway)
As that makes is much easier to know which partition is which.
Refer to the wiki on how to actually set the customized grub names for each install.
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries")

Edit: nevermind last page didn't load so I was reading this post as if the last post
[https://ubuntuforums.org/showthread.php?t=2076205&page=16&p=13764313#post13764313]("https://ubuntuforums.org/showthread.php?t=2076205&page=16&p=13764313#post13764313")

I also took awhile.

---

### Post by oldfred on 2018-05-07
from my notes, I have renamed like this (really old note).

 sudo nano -B /etc/default/grub
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR="Xubuntu-12.04-amd64 Precise"
sudo update-grub 

But with newer versions & UEFI, it will add a new UEFI folder with that name, if short enough and valid characters for UEFI entry (not like one above). And I got a separate UEFI entry. But the new folder it created had grubx64.efi which internally was hard coded to find the configfile grub in /EFI/ubuntu. Or it did not really work.

---

### Post by Cavsfan on 2018-05-08
Thank you these will help me too as I have not gotten UEFI grub down at all.

I use **tune2fs** to label my partitions even UEFI partitions. It is already installed.

```
sudo tune2fs -L "ArchLinux" /dev/sdc5
sudo tune2fs -L "Xenial" /dev/sdc6
sudo tune2fs -L "Bionic" /dev/sdc7
```

This worked for me. You do not need quotes around a single word, I just left them there. 
But, you definitely do with something like "Bionic Beaver" but, I'd still suggest adding a dash in there to be able to copy across partitions.

A space in the label will prevent that.

---

### Post by Roger_Williams on 2018-05-09
OK so I ran lshw -class disk and this is what I got. I've marked the disks with which Distro it's running. I'm looking at the bus info and thinking for example scsi@4:0.0.0 would be set root=(hd4,x) does that sound about right? My 40_custom is pasted below let me know if I've got the right idea? Also my next problem is knowing what to put as the x number in (hd0,x) for example.

```
Kali
====  
description: SCSI Disk
       product: SATAWire
       vendor: Apricorn
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdd
       version: 1.08
       serial: 1352095FFF5B
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512 signature=a0a68dd4

Kubuntu
=======
  *-disk
       description: SCSI Disk
       vendor: Apricorn
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 0128
       serial: P577492-DDBX-902
       size: 119GiB (128GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=6 guid=cf2bfe61-5fcc-4e35-a516-32ae68398ede logicalsectorsize=512 sectorsize=512

Ubuntu
======
  *-disk
       description: ATA Disk
       product: TOSHIBA MQ01ABD1
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3D
       serial: 86GNT7OPT
       size: 931GiB (1TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=929e1ceb-b32d-429c-9cff-137b042579b5 logicalsectorsize=512 sectorsize=4096

  *-cdrom
       description: DVD-RAM writer
       product: DVD+-RW DU-8A5LH
       vendor: PLDS
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 6D11
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc


```
```
#menuentry "Bionic Beaver" {
#    set root=(hd0,x)
#        linux /vmlinuz root=/dev/sda2 ro quiet splash
#        initrd /initrd.img
#}

#menuentry "Bionic K" {
#    set root=(hd2,gptx)
#        linux /vmlinuz root=/dev/sdb2 ro quiet splash
#        initrd /initrd.img
#}

#menuentry "Kali" {
#    set root=(hd4,x)
#        linux /vmlinuz root=/dev/sdd1 ro quiet splash
#        initrd /initrd.img
#}

menuentry "System restart" {
echo "System rebooting..."
insmod reboot
reboot
} 

menuentry "System shutdown" {
      echo "System shutting down..."
      insmod halt
      halt
}
```

---

### Post by oldfred on 2018-05-09
Your x is the partition number. 

But because of my issues on drive changing depending on whether flash drive and/or external SSD are plugged in or not, the hdX, my hd0 may be hd1 or hd2 depending on where UEFI has assigned drive.

It seems I have two different installs in third partitions on different drives, so once when drive order was not correct, I booted my old 14.04 install. Still booted. :)

---

### Post by Roger_Williams on 2018-05-09
> **oldfred said:**
> Your x is the partition number. 

But because of my issues on drive changing depending on whether flash drive and/or external SSD are plugged in or not, the hdX, my hd0 may be hd1 or hd2 depending on where UEFI has assigned drive.

It seems I have two different installs in third partitions on different drives, so once when drive order was not correct, I booted my old 14.04 install. Still booted. :)

OK I think I'm ok with the drives just wanted a second opinion. I'm not so sure about the partitions. I know with Ubuntu there's sda1 and sda2 and Ubuntu is on sda2 so does that mean I put (hd0,2) or how do I know if it's gpt? would I put gpt2 then? lol I'm such a noob when it comes to Linux. Ubuntu and Kubuntu are installed in EUFI but Kali is Bios mode. Ubuntu and Kubuntu use the whole drive while Kali has a swap partition. I guess I'll just try it and I could always boot to live and undo if I needed to anyway lol.

---

### Post by oldfred on 2018-05-09
If all systems are not in same boot mode, you cannot boot from grub, only from UEFI.
Some systems may require you to also turn on/off UEFI or legacy/BIOS/CSM boot modes to match how installed system is to boot.

UEFI & BIOS write hardware data differently to hard drive for operating system to use. So they are not compatible. Or once you start booting in one mode you cannot switch. But you can boot directly from UEFI.

This will show if gpt or not, may show dos, or msdos.
sudo parted -l

---

### Post by Roger_Williams on 2018-05-09
> **oldfred said:**
> If all systems are not in same boot mode, you cannot boot from grub, only from UEFI.
Some systems may require you to also turn on/off UEFI or legacy/BIOS/CSM boot modes to match how installed system is to boot.

UEFI & BIOS write hardware data differently to hard drive for operating system to use. So they are not compatible. Or once you start booting in one mode you cannot switch. But you can boot directly from UEFI.

This will show if gpt or not, may show dos, or msdos.
sudo parted -l

I installed Kali before I installed Ubuntu and Kubuntu. As it is I know Ubuntu and Kubuntu boot from UEFI for sure. I'm a noob but my machine powers on it asks for the bios password then it boots to the Ubuntu grub where I can select Ubuntu, Kubuntu or Kali and they all boot. In the past my UEFI was turned off so I had to hit F12 to get the UEFI boot menu and choose ubuntu. I turned UEFI on but secure boot off and it has been booting the way I described above since then. 
I opened /boot/grub/grub.cfg in gedit and I searched through and found that Kubuntu was hd2,gpt2, Kali was hd3,msdos3 but I didn't look for Ubuntu. I rebooted and Ubuntu doesn't work but Kubuntu booted up no problems. I have to get a few days use out of Kubuntu so I'm leaving it at that for now. After that I will get back into it and figure out Ubuntu. Then my last step is to figure out how to get rid of the system menu entries that are being pulled from grub.cfg

---

### Post by Roger_Williams on 2018-05-10
OK I was going about this too complicated. I took it back to simple methods. I removed the custom menu and edited the /boot/grub/grub.cfg. I did a find and looked for Ubuntu. I only changed the 18.04 on sdb2. I know you're not supposed to edit it but I'm litterally adding one letter. I made the changes and on reboot BAM it shows Ubuntu and Kubuntu YAY! lol

---

### Post by Cavsfan on 2018-05-10
> **oldfred said:**
> Your x is the partition number. 

But because of my issues on drive changing depending on whether flash drive and/or external SSD are plugged in or not, the hdX, my hd0 may be hd1 or hd2 depending on where UEFI has assigned drive.

It seems I have two different installs in third partitions on different drives, so once when drive order was not correct, I booted my old 14.04 install. Still booted. :)

> **Roger_Williams said:**
> OK I think I'm ok with the drives just wanted a second opinion. I'm not so sure about the partitions. I know with Ubuntu there's sda1 and sda2 and Ubuntu is on sda2 so does that mean I put (hd0,2) or how do I know if it's gpt? would I put gpt2 then? lol I'm such a noob when it comes to Linux. Ubuntu and Kubuntu are installed in EUFI but Kali is Bios mode. Ubuntu and Kubuntu use the whole drive while Kali has a swap partition. I guess I'll just try it and I could always boot to live and undo if I needed to anyway lol.

You could try **lsblk** or **lsblk -fs** - that will definitely give you the partitions.

Also **sudo blkid** too.

Me, I'm stuck between a rock and a hard place. I have Grub installed on Arch Linux and of course Arch handles everything differently than Ubuntu or any Debian distro.
And I can switch where I'm booting from with BIOS temporarily but, it's not that easy to do a grub-install with EFI because it's not just a simple **sudo grub install /dev/sda** etc.

I'm on Xenial 16.04 right now.

I did get a working custom boot menuentry for Windows 10 though:
```
menuentry "Microsoft Windows 10 UEFI/GPT" {
    insmod part_gpt
    insmod fat
    set root='hd2,gpt1'
    insmod search_fs_uuid
    insmod chain
    search --no-floppy --fs-uuid --set=root 688D-126B
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

```

Of course everything points to the [COLOR=#000000][FONT=&amp]EFI system partition[/FONT][/COLOR] sdc1, while Windows 10 is actually on sdc3
```
cavsfan@cavsfan-Xenial-Xerus:~$ sudo blkid | grep sdc
/dev/sdc1: UUID="688D-126B" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="3c1b6d6f-8a24-43da-b595-8c304ceee48d"
/dev/sdc3: UUID="C4968A52968A44C0" TYPE="ntfs" PARTLABEL="Windows_10" PARTUUID="345c85f4-bce7-4bc7-bbe0-db03eb319cad"
/dev/sdc4: UUID="701AE4631AE427B4" TYPE="ntfs" PARTUUID="1e337754-b45d-45a5-a971-b8cdcae8a002"
/dev/sdc5: UUID="ad60d57b-f7b9-4a83-8ce0-74382d2e3281" TYPE="swap" PARTLABEL="Basic data partition" PARTUUID="3a259867-656d-41ed-9931-cf15a3bd0148"
/dev/sdc6: LABEL="ArchLinux" UUID="bbca28b2-503e-4dc8-9850-c54bd0492da8" TYPE="ext4" PARTLABEL="Arch_Linux" PARTUUID="5312b771-0835-4957-80a6-9a8a7107f24a"
/dev/sdc7: LABEL="Xenial" UUID="c0a5062e-6847-44a0-9f4e-cfbb7292b037" TYPE="ext4" PARTLABEL="Xenial_Xerus" PARTUUID="57075798-adb7-4590-ae23-6a75d976c3c1"
/dev/sdc8: LABEL="Bionic" UUID="21cf477b-a314-4691-85f6-256e6209d5d9" TYPE="ext4" PARTLABEL="Bionic_Beaver" PARTUUID="c4e0fdc9-7eac-4661-a7c6-c5a00c9a46fc"
/dev/sdc9: UUID="f716b510-b16b-4fd0-b89f-ea86e90c2533" TYPE="ext4" PARTLABEL="Basic data partition" PARTUUID="ac30cd57-1b77-4924-ba8c-7bc94c8f961b"
/dev/sdc2: PARTLABEL="Microsoft reserved partition" PARTUUID="49992d5b-79cd-4934-a12f-11782bb345bd"

```

I am getting closer though.

PS: I just now seen there were more posts on the next page. This UEFI stuff is trying to say the least.

---

### Post by Cavsfan on 2018-05-13
@oldfred
So, I installed my Grub on Bionic Beaver 18.04 with this difficult command: 
```
sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi/EFI/ubuntu --bootloader-id=ubuntu
```

I don't think that is the same on everyone's system, although I could be wrong.

But, I have not been able to customize the Xubuntu entry for 18.04:

This is the only thing that will work:
```
menuentry 'Ubuntu 18.04 LTS, with Linux 4.15.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-20-generic-advanced-21cf477b-a314-4691-85f6-256e6209d5d9' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  21cf477b-a314-4691-85f6-256e6209d5d9
    else
      search --no-floppy --fs-uuid --set=root 21cf477b-a314-4691-85f6-256e6209d5d9
    fi
    echo    'Loading Linux 4.15.0-20-generic ...'
        linux    /boot/vmlinuz-4.15.0-20-generic root=UUID=21cf477b-a314-4691-85f6-256e6209d5d9 ro  quiet splash $vt_handoff
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-4.15.0-20-generic
}

```

I do know that it meets the IF criteria so I could take all of the stuff around the 2nd line of the if statement out but, that's still a mess.

If I try something like this:
```
menuentry "Ubuntu 18.04 LTS custom entry" {
    set root=(hd2,gpt8)
        linux /vmlinuz.old root=/dev/sdc8 ro quiet splash
        initrd /initrd.img
}

```
The system will tell me it cannot find (hd2,gpt8) and says to load the kernel first.
I've tried parens and quotes and neither work.

---

### Post by oldfred on 2018-05-13
Why are you using gpt8, your boot stanza shows gpt7?

I think you are just using the full command for grub-install. With Ubuntu it is a script that assigns all the variables.

---

### Post by Cavsfan on 2018-05-13
> **oldfred said:**
> Why are you using gpt8, your boot stanza shows gpt7?

I think you are just using the full command for grub-install. _With Ubuntu it is a script that assigns all the variables_.

What is the normal grub-install line for Ubuntu? Just **sudo grub-install /dev/gpt8** (for Bionic)?

gpt7 is Xenial gpt8 is Bionic but, it gives this error if I try to boot that custom entry with either 7 or 8:
> error: disk 'hd2.gpt8' not found
error: you need to load the kernel first

This perplexes me also: the Arch boot line points to gpt1 "EFI system partition" just as Windows 10 does.
Only the UUID on the linux /vmlinuz like points to the Arch partition, everything else is just like the Windows boot entry.
Here is the disk:
```
cavsfan@cavsfan-Bionic-Beaver:~$ sudo blkid | grep sdc
[sudo] password for cavsfan: 
/dev/sdc1: UUID="[COLOR=#0000ff]688D-126B[/COLOR]" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="3c1b6d6f-8a24-43da-b595-8c304ceee48d"
/dev/sdc2: PARTLABEL="Microsoft reserved partition" PARTUUID="49992d5b-79cd-4934-a12f-11782bb345bd"
/dev/sdc3: UUID="C4968A52968A44C0" TYPE="ntfs" PARTLABEL="[COLOR=#0000ff]Windows_10[/COLOR]" PARTUUID="345c85f4-bce7-4bc7-bbe0-db03eb319cad"
/dev/sdc4: UUID="701AE4631AE427B4" TYPE="ntfs" PARTUUID="1e337754-b45d-45a5-a971-b8cdcae8a002"
/dev/sdc5: UUID="ad60d57b-f7b9-4a83-8ce0-74382d2e3281" TYPE="[COLOR=#0000ff]swap[/COLOR]" PARTLABEL="Basic data partition" PARTUUID="3a259867-656d-41ed-9931-cf15a3bd0148"
/dev/sdc6: LABEL="ArchLinux" UUID="[COLOR=#b22222]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR]" TYPE="ext4" PARTLABEL="[COLOR=#0000ff]Arch_Linux[/COLOR]" PARTUUID="5312b771-0835-4957-80a6-9a8a7107f24a"
/dev/sdc7: LABEL="Xenial" UUID="c0a5062e-6847-44a0-9f4e-cfbb7292b037" TYPE="ext4" PARTLABEL="[COLOR=#0000ff]Xenial_Xerus[/COLOR]" PARTUUID="57075798-adb7-4590-ae23-6a75d976c3c1"
/dev/sdc8: LABEL="Bionic" UUID="21cf477b-a314-4691-85f6-256e6209d5d9" TYPE="ext4" PARTLABEL="[COLOR=#0000ff]Bionic_Beaver[/COLOR]" PARTUUID="c4e0fdc9-7eac-4661-a7c6-c5a00c9a46fc"
/dev/sdc9: UUID="f716b510-b16b-4fd0-b89f-ea86e90c2533" TYPE="ext4" PARTLABEL="Basic data partition" PARTUUID="ac30cd57-1b77-4924-ba8c-7bc94c8f961b"
```

But, here are the first 2 menuentries in 30_os-prober:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/[COLOR=#0000ff]sdc1[/COLOR])' --class windows --class os $menuentry_id_option 'osprober-efi-[COLOR=#0000ff]688D-126B[/COLOR]' {
    insmod part_gpt
    insmod fat
    set root='hd2,[COLOR=#0000ff]gpt1[/COLOR]'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,[COLOR=#0000ff]gpt1[/COLOR] --hint-efi=hd2,[COLOR=#0000ff]gpt1[/COLOR] --hint-baremetal=ahci2,[COLOR=#0000ff]gpt1[/COLOR]  [COLOR=#0000ff]688D-126B[/COLOR]
    else
      search --no-floppy --fs-uuid --set=root [COLOR=#0000ff]688D-126B[/COLOR]
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
menuentry 'Arch Linux (rolling) (on /dev/[COLOR=#0000ff]sdc6[/COLOR])' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-[COLOR=#b22222]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR]' {
    insmod part_gpt
    insmod fat
    set root='hd2,[COLOR=#0000ff]gpt1[/COLOR]'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,[COLOR=#0000ff]gpt1[/COLOR] --hint-efi=hd2,[COLOR=#0000ff]gpt1[/COLOR] --hint-baremetal=ahci2,gpt1  [COLOR=#0000ff]688D-126B[/COLOR]
    else
      search --no-floppy --fs-uuid --set=root [COLOR=#0000ff]688D-126B[/COLOR]
    fi
    linux /vmlinuz-linux root=UUID=[COLOR=#b22222]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR] rw quiet
    initrd  /intel-ucode.img
}
```

Here is the entire /boot/grub/grub.cfg _**without**_ the custom entries (grub installed on Bionic):
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi


if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi


export menuentry_id_option


if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}


if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd2,gpt8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt8 --hint-efi=hd2,gpt8 --hint-baremetal=ahci2,gpt8  21cf477b-a314-4691-85f6-256e6209d5d9
else
  search --no-floppy --fs-uuid --set=root 21cf477b-a314-4691-85f6-256e6209d5d9
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=60
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=60
  fi
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_gpt
insmod ext2
set root='hd2,gpt8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt8 --hint-efi=hd2,gpt8 --hint-baremetal=ahci2,gpt8  21cf477b-a314-4691-85f6-256e6209d5d9
else
  search --no-floppy --fs-uuid --set=root 21cf477b-a314-4691-85f6-256e6209d5d9
fi
insmod png
if background_image /boot/grub/band-2560x1440.png; then
 set color_normal=yellow/black
 set menu_color_normal=cyan/black
 set menu_color_highlight=red/black
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=1
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-21cf477b-a314-4691-85f6-256e6209d5d9' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt8 --hint-efi=hd2,gpt8 --hint-baremetal=ahci2,gpt8  21cf477b-a314-4691-85f6-256e6209d5d9
    else
      search --no-floppy --fs-uuid --set=root 21cf477b-a314-4691-85f6-256e6209d5d9
    fi
        linux    /boot/vmlinuz-4.15.0-20-generic root=UUID=21cf477b-a314-4691-85f6-256e6209d5d9 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.15.0-20-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-21cf477b-a314-4691-85f6-256e6209d5d9' {
    menuentry 'Ubuntu, with Linux 4.15.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-20-generic-advanced-21cf477b-a314-4691-85f6-256e6209d5d9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt8 --hint-efi=hd2,gpt8 --hint-baremetal=ahci2,gpt8  21cf477b-a314-4691-85f6-256e6209d5d9
        else
          search --no-floppy --fs-uuid --set=root 21cf477b-a314-4691-85f6-256e6209d5d9
        fi
        echo    'Loading Linux 4.15.0-20-generic ...'
            linux    /boot/vmlinuz-4.15.0-20-generic root=UUID=21cf477b-a314-4691-85f6-256e6209d5d9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 4.15.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-20-generic-recovery-21cf477b-a314-4691-85f6-256e6209d5d9' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt8 --hint-efi=hd2,gpt8 --hint-baremetal=ahci2,gpt8  21cf477b-a314-4691-85f6-256e6209d5d9
        else
          search --no-floppy --fs-uuid --set=root 21cf477b-a314-4691-85f6-256e6209d5d9
        fi
        echo    'Loading Linux 4.15.0-20-generic ...'
            linux    /boot/vmlinuz-4.15.0-20-generic root=UUID=21cf477b-a314-4691-85f6-256e6209d5d9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-20-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sdc1)' --class windows --class os $menuentry_id_option 'osprober-efi-688D-126B' {
    insmod part_gpt
    insmod fat
    set root='hd2,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt1 --hint-efi=hd2,gpt1 --hint-baremetal=ahci2,gpt1  688D-126B
    else
      search --no-floppy --fs-uuid --set=root 688D-126B
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
menuentry 'Arch Linux (rolling) (on /dev/sdc6)' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-bbca28b2-503e-4dc8-9850-c54bd0492da8' {
    insmod part_gpt
    insmod fat
    set root='hd2,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt1 --hint-efi=hd2,gpt1 --hint-baremetal=ahci2,gpt1  688D-126B
    else
      search --no-floppy --fs-uuid --set=root 688D-126B
    fi
    linux /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw quiet
    initrd  /intel-ucode.img
}
submenu 'Advanced options for Arch Linux (rolling) (on /dev/sdc6)' $menuentry_id_option 'osprober-gnulinux-advanced-bbca28b2-503e-4dc8-9850-c54bd0492da8' {
    menuentry 'Arch Linux (on /dev/sdc6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-linux--bbca28b2-503e-4dc8-9850-c54bd0492da8' {
        insmod part_gpt
        insmod fat
        set root='hd2,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt1 --hint-efi=hd2,gpt1 --hint-baremetal=ahci2,gpt1  688D-126B
        else
          search --no-floppy --fs-uuid --set=root 688D-126B
        fi
        linux /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw quiet
        initrd    /intel-ucode.img /initramfs-linux.img
    }
    menuentry 'Arch Linux (Fallback) (on /dev/sdc6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-linux--bbca28b2-503e-4dc8-9850-c54bd0492da8' {
        insmod part_gpt
        insmod fat
        set root='hd2,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt1 --hint-efi=hd2,gpt1 --hint-baremetal=ahci2,gpt1  688D-126B
        else
          search --no-floppy --fs-uuid --set=root 688D-126B
        fi
        linux /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw quiet
        initrd /initramfs-linux-fallback.img
    }
    menuentry 'Arch Linux (on /dev/sdc6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-linux--bbca28b2-503e-4dc8-9850-c54bd0492da8' {
        insmod part_gpt
        insmod fat
        set root='hd2,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt1 --hint-efi=hd2,gpt1 --hint-baremetal=ahci2,gpt1  688D-126B
        else
          search --no-floppy --fs-uuid --set=root 688D-126B
        fi
        linux /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw quiet
        initrd /intel-ucode.img
    }
    menuentry 'Arch Linux, with Linux linux (on /dev/sdc6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-linux--bbca28b2-503e-4dc8-9850-c54bd0492da8' {
        insmod part_gpt
        insmod fat
        set root='hd2,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt1 --hint-efi=hd2,gpt1 --hint-baremetal=ahci2,gpt1  688D-126B
        else
          search --no-floppy --fs-uuid --set=root 688D-126B
        fi
        linux /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw quiet
        initrd /intel-ucode.img
    }
    menuentry 'Arch Linux, with Linux linux (fallback initramfs) (on /dev/sdc6)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-linux--bbca28b2-503e-4dc8-9850-c54bd0492da8' {
        insmod part_gpt
        insmod fat
        set root='hd2,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt1 --hint-efi=hd2,gpt1 --hint-baremetal=ahci2,gpt1  688D-126B
        else
          search --no-floppy --fs-uuid --set=root 688D-126B
        fi
        linux /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw quiet
        initrd /initramfs-linux-fallback.img
    }
}


menuentry 'Ubuntu 16.04.4 LTS (16.04) (on /dev/sdc7)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  c0a5062e-6847-44a0-9f4e-cfbb7292b037
    else
      search --no-floppy --fs-uuid --set=root c0a5062e-6847-44a0-9f4e-cfbb7292b037
    fi
    linux /boot/vmlinuz-4.13.0-41-generic.efi.signed root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-4.13.0-41-generic
}
submenu 'Advanced options for Ubuntu 16.04.4 LTS (16.04) (on /dev/sdc7)' $menuentry_id_option 'osprober-gnulinux-advanced-c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
    menuentry 'Ubuntu (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.13.0-41-generic.efi.signed--c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  c0a5062e-6847-44a0-9f4e-cfbb7292b037
        else
          search --no-floppy --fs-uuid --set=root c0a5062e-6847-44a0-9f4e-cfbb7292b037
        fi
        linux /boot/vmlinuz-4.13.0-41-generic.efi.signed root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-4.13.0-41-generic
    }
    menuentry 'Ubuntu, with Linux 4.13.0-41-generic (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.13.0-41-generic.efi.signed--c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  c0a5062e-6847-44a0-9f4e-cfbb7292b037
        else
          search --no-floppy --fs-uuid --set=root c0a5062e-6847-44a0-9f4e-cfbb7292b037
        fi
        linux /boot/vmlinuz-4.13.0-41-generic.efi.signed root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-4.13.0-41-generic
    }
    menuentry 'Ubuntu, with Linux 4.13.0-41-generic (upstart) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.13.0-41-generic.efi.signed--c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  c0a5062e-6847-44a0-9f4e-cfbb7292b037
        else
          search --no-floppy --fs-uuid --set=root c0a5062e-6847-44a0-9f4e-cfbb7292b037
        fi
        linux /boot/vmlinuz-4.13.0-41-generic.efi.signed root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro quiet splash $vt_handoff init=/sbin/upstart
        initrd /boot/initrd.img-4.13.0-41-generic
    }
    menuentry 'Ubuntu, with Linux 4.13.0-41-generic (recovery mode) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.13.0-41-generic.efi.signed-root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro recovery nomodeset-c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  c0a5062e-6847-44a0-9f4e-cfbb7292b037
        else
          search --no-floppy --fs-uuid --set=root c0a5062e-6847-44a0-9f4e-cfbb7292b037
        fi
        linux /boot/vmlinuz-4.13.0-41-generic.efi.signed root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro recovery nomodeset
        initrd /boot/initrd.img-4.13.0-41-generic
    }
    menuentry 'Ubuntu, with Linux 4.13.0-39-generic (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.13.0-39-generic.efi.signed--c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  c0a5062e-6847-44a0-9f4e-cfbb7292b037
        else
          search --no-floppy --fs-uuid --set=root c0a5062e-6847-44a0-9f4e-cfbb7292b037
        fi
        linux /boot/vmlinuz-4.13.0-39-generic.efi.signed root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-4.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 4.13.0-39-generic (upstart) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.13.0-39-generic.efi.signed--c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  c0a5062e-6847-44a0-9f4e-cfbb7292b037
        else
          search --no-floppy --fs-uuid --set=root c0a5062e-6847-44a0-9f4e-cfbb7292b037
        fi
        linux /boot/vmlinuz-4.13.0-39-generic.efi.signed root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro quiet splash $vt_handoff init=/sbin/upstart
        initrd /boot/initrd.img-4.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 4.13.0-39-generic (recovery mode) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.13.0-39-generic.efi.signed-root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro recovery nomodeset-c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  c0a5062e-6847-44a0-9f4e-cfbb7292b037
        else
          search --no-floppy --fs-uuid --set=root c0a5062e-6847-44a0-9f4e-cfbb7292b037
        fi
        linux /boot/vmlinuz-4.13.0-39-generic.efi.signed root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro recovery nomodeset
        initrd /boot/initrd.img-4.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-124-generic (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-124-generic--c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  c0a5062e-6847-44a0-9f4e-cfbb7292b037
        else
          search --no-floppy --fs-uuid --set=root c0a5062e-6847-44a0-9f4e-cfbb7292b037
        fi
        linux /boot/vmlinuz-4.4.0-124-generic root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-4.4.0-124-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-124-generic (upstart) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-124-generic--c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  c0a5062e-6847-44a0-9f4e-cfbb7292b037
        else
          search --no-floppy --fs-uuid --set=root c0a5062e-6847-44a0-9f4e-cfbb7292b037
        fi
        linux /boot/vmlinuz-4.4.0-124-generic root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro quiet splash $vt_handoff init=/sbin/upstart
        initrd /boot/initrd.img-4.4.0-124-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-124-generic (recovery mode) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-4.4.0-124-generic-root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro recovery nomodeset-c0a5062e-6847-44a0-9f4e-cfbb7292b037' {
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt7 --hint-efi=hd2,gpt7 --hint-baremetal=ahci2,gpt7  c0a5062e-6847-44a0-9f4e-cfbb7292b037
        else
          search --no-floppy --fs-uuid --set=root c0a5062e-6847-44a0-9f4e-cfbb7292b037
        fi
        linux /boot/vmlinuz-4.4.0-124-generic root=UUID=c0a5062e-6847-44a0-9f4e-cfbb7292b037 ro recovery nomodeset
        initrd /boot/initrd.img-4.4.0-124-generic
    }
}


set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

---

### Post by oldfred on 2018-05-13
It looks like Arch puts some boot files into the ESP?

This works for me (as long as flash drive is not plugged in and then drive is hd1)

```
menuentry "Ubuntu 18.04 Bionic (on /dev/sda4)" {
    set root=(hd0,gpt4)
        linux /vmlinuz root=/dev/sda4 ro quiet splash
        initrd /initrd.img
}

```

---

### Post by Cavsfan on 2018-05-14
> **oldfred said:**
> It looks like Arch puts some boot files into the ESP?

This works for me (as long as flash drive is not plugged in and then drive is hd1)

```
menuentry "Ubuntu 18.04 Bionic (on /dev/sda4)" {
    set root=(hd0,gpt4)
        linux /vmlinuz root=/dev/sda4 ro quiet splash
        initrd /initrd.img
}

```

I guess Arch does. I backed up Xenial and Bionic so here is the folder:
```
root@cavsfan-Bionic-Beaver:/boot/efi/EFI# ls
[COLOR=#0000ff]Arch_grub  bionic  Boot  Microsoft  ubuntu  xenial[/COLOR]

```

I'll give that a try.

So, on Ubuntu a simple **sudo grub-install /dev/sdc** will work? I know it does not work on Arch, It requires the long command:
```
sudo grub-install --target=x86_64-efi --efi-directory=/boot/EFI/Arch_grub --bootloader-id=Arch_grub
```

---

### Post by oldfred on 2018-05-14
If you look at this the standard grub-install has the many option parameters.
man grub-install
info grub-install.

I have in my notes many versions of grub-install with different parameters, but most are example of just installing grub to a flash drive, so I can just boot ISO, creating my own grub.cfg to loopmount the ISOs.

---

### Post by Cavsfan on 2018-05-16
> **oldfred said:**
> If you look at this the standard grub-install has the many option parameters.
man grub-install
info grub-install.

I have in my notes many versions of grub-install with different parameters, but most are example of just installing grub to a flash drive, so I can just boot ISO, creating my own grub.cfg to loopmount the ISOs.

Thanks! I'll have to look at that.
I tried:
```
menuentry "Ubuntu 16.04 Xenial (on /dev/sdc7)" {
    set root=(hd2,gpt7)
        linux /vmlinuz root=/dev/sdc7 ro quiet splash
        initrd /initrd.img
}
```
And
```
menuentry "Ubuntu 18.04 Bionic (on /dev/sdc8)" {
    set root=(hd2,gpt8)
        linux /vmlinuz root=/dev/sdc8 ro quiet splash
        initrd /initrd.img
}
```

```
cavsfan@cavsfan-Xenial-Xerus:~$ sudo blkid | grep sdc
[sudo] password for cavsfan: 
/dev/sdc1: UUID="688D-126B" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="3c1b6d6f-8a24-43da-b595-8c304ceee48d"
/dev/sdc3: UUID="C4968A52968A44C0" TYPE="ntfs" PARTLABEL="Windows_10" PARTUUID="345c85f4-bce7-4bc7-bbe0-db03eb319cad"
/dev/sdc4: UUID="701AE4631AE427B4" TYPE="ntfs" PARTUUID="1e337754-b45d-45a5-a971-b8cdcae8a002"
/dev/sdc5: UUID="ad60d57b-f7b9-4a83-8ce0-74382d2e3281" TYPE="swap" PARTLABEL="Basic data partition" PARTUUID="3a259867-656d-41ed-9931-cf15a3bd0148"
/dev/sdc6: LABEL="ArchLinux" UUID="bbca28b2-503e-4dc8-9850-c54bd0492da8" TYPE="ext4" PARTLABEL="Arch_Linux" PARTUUID="5312b771-0835-4957-80a6-9a8a7107f24a"
/dev/sdc7: LABEL="Xenial" UUID="4c61d35a-0e87-463e-b98b-f196bb4b8082" TYPE="ext4" PARTLABEL="Xenial_Xerus" PARTUUID="57075798-adb7-4590-ae23-6a75d976c3c1"
/dev/sdc8: LABEL="Bionic" UUID="21cf477b-a314-4691-85f6-256e6209d5d9" TYPE="ext4" PARTLABEL="Bionic_Beaver" PARTUUID="c4e0fdc9-7eac-4661-a7c6-c5a00c9a46fc"
/dev/sdc9: LABEL="Spare" UUID="f716b510-b16b-4fd0-b89f-ea86e90c2533" TYPE="ext4" PARTLABEL="Basic data partition" PARTUUID="ac30cd57-1b77-4924-ba8c-7bc94c8f961b"
/dev/sdc2: PARTLABEL="Microsoft reserved partition" PARTUUID="49992d5b-79cd-4934-a12f-11782bb345bd"
```


I still got the error message:
> error: disk 'hd2.gpt7' not found
error: you need to load the kernel first
press any key to continue...

> error: disk 'hd2.gpt8' not found
error: you need to load the kernel first
press any key to continue...

---

### Post by oldfred on 2018-05-16
When you look at drives in grub, is hd2 the correct drive?
When I have flash drive plugged in my hd0 becomes hd1, and I just edit in grub when it errors like that.

The menu entry looks correct, but error is with a period, not comma? hd2.gpt8'

---

### Post by Cavsfan on 2018-05-16
> **oldfred said:**
> When you look at drives in grub, is hd2 the correct drive?
When I have flash drive plugged in my hd0 becomes hd1, and I just edit in grub when it errors like that.

The menu entry looks correct, but error is with a period, not comma? hd2.gpt8'

That was probably just me typing because I could not take a screenshot.

I'll try it again tomorrow morning. I had to re-install Xubuntu 16.04 because my previous install became worthless for some reason. I have spent all day on that.
Probably something I did but, I don't know, figured I didn't have much in it but I am formatting my USB sticks to ext4 instead of fat32. I've had numerous problems with windows line feeds at the end of some files.
Only VI shows the ^M (windows line end).

This is looking much better and of course I had to change the UUID for it in my current "custom" grub.
So, I'm really hoping that I can do the boot line like I used to.

---

### Post by oldfred on 2018-05-16
I only use ext4 on my full install or data partitions on flash drives.
All UEFI bootable installers must have a FAT32 formatted with boot flag to be the ESP. Normal installer is also the ESP as it has /EFI/Boot/bootx64.efi for UEFI boot, but also has syslinux for BIOS boot. 

Have not used Windows files for anything for years.
I use nano or gedit. Starting to use medit also.

My install to a SSD takes 10 Min. Only full installs to a flash drive take a while. And I have one flash drive that was extremely slow. Still experimenting with that one. Not sure if flash drive, 18.04, or some other issue.

---

### Post by Cavsfan on 2018-05-17
I just thought I'd format it as ext4 to copy stuff from linux to linux.

But, I added these 2 entries to 40_custom just to see if it worked.
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu 16.04 Xenial (on /dev/sdc7)" {
    set root=(hd2,gpt7)
        linux /vmlinuz root=/dev/sdc7 ro quiet splash
        initrd /initrd.img
}
menuentry "Ubuntu 18.04 Bionic (on /dev/sdc8)" {
    set root=(hd2,gpt8)
        linux /vmlinuz root=/dev/sdc8 ro quiet splash
        initrd /initrd.img
}
```

I got this different error and I took a picture to be sure what it said.
> error: disk 'hd2,gpt7' not found.
alloc magic is broken at 0xc43e2300: c432ab40
Aborted. Press any key to exit


I then pressed enter I believe and the grub on Xenial (where it is currently installed since installation yesterday).
Which took me back to the grub screen and I selected to option to go into Bionic and got a similar error:
> error: disk 'hd2,gpt8' not found.
alloc magic is broken at 0x907c4300: 9070cb40
Aborted. Press any key to exit

I do not know where those numbers after "at" are coming from.
Here again are my partitions with blkid:
```
cavsfan@cavsfan-Xenial-Xerus:~$ sudo blkid | grep sdc
[sudo] password for cavsfan: 
/dev/sdc1: UUID="688D-126B" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="3c1b6d6f-8a24-43da-b595-8c304ceee48d"
/dev/sdc2: PARTLABEL="Microsoft reserved partition" PARTUUID="49992d5b-79cd-4934-a12f-11782bb345bd"
/dev/sdc3: UUID="C4968A52968A44C0" TYPE="ntfs" PARTLABEL="Windows_10" PARTUUID="345c85f4-bce7-4bc7-bbe0-db03eb319cad"
/dev/sdc4: UUID="701AE4631AE427B4" TYPE="ntfs" PARTUUID="1e337754-b45d-45a5-a971-b8cdcae8a002"
/dev/sdc5: UUID="ad60d57b-f7b9-4a83-8ce0-74382d2e3281" TYPE="swap" PARTLABEL="Basic data partition" PARTUUID="3a259867-656d-41ed-9931-cf15a3bd0148"
/dev/sdc6: LABEL="ArchLinux" UUID="bbca28b2-503e-4dc8-9850-c54bd0492da8" TYPE="ext4" PARTLABEL="Arch_Linux" PARTUUID="5312b771-0835-4957-80a6-9a8a7107f24a"
/dev/sdc7: LABEL="Xenial" UUID="4c61d35a-0e87-463e-b98b-f196bb4b8082" TYPE="ext4" PARTLABEL="Xenial_Xerus" PARTUUID="57075798-adb7-4590-ae23-6a75d976c3c1"
/dev/sdc8: LABEL="Bionic" UUID="21cf477b-a314-4691-85f6-256e6209d5d9" TYPE="ext4" PARTLABEL="Bionic_Beaver" PARTUUID="c4e0fdc9-7eac-4661-a7c6-c5a00c9a46fc"
/dev/sdc9: LABEL="Spare" UUID="f716b510-b16b-4fd0-b89f-ea86e90c2533" TYPE="ext4" PARTLABEL="Basic data partition" PARTUUID="ac30cd57-1b77-4924-ba8c-7bc94c8f961b"


```
This time I press escape and am looking at the grub screen on Arch Linux! :confused:

So, I am lost.

---

### Post by oldfred on 2018-05-17
The address is a hex address of the error.

A search says it could be memory errors, grub errors, or you have one install as 32 bit and one 64 bit?
I have had totally different versions of grub2 from Ubuntu, but not sure then if you are using versions of grub2 from other distributions and there may just be enough difference to cause issues?

---

### Post by Cavsfan on 2018-05-18
> **oldfred said:**
> The address is a hex address of the error.

A search says it could be memory errors, grub errors, or you have one install as 32 bit and one 64 bit?
I have had totally different versions of grub2 from Ubuntu, but not sure then if you are using versions of grub2 from other distributions and there may just be enough difference to cause issues?

I make sure I download the 64 bit ISO and everything on my computers have always been 64 bit.
Grub version on Ubuntu (the ones being currently maintained) are mostly the same with a few exceptions (that this semi-knowledgeable person can see) but, then there is Arch Linux...

It is different. Like I mentioned Ubuntu does not add the **/initramfs-linux.img** to the bottom boot line like it should.
This is what it puts:
```
initrd    /intel-ucode.img
```
Which will put you in grub rescue.
This is what is required:
```
initrd    /intel-ucode.img /initramfs-linux.img
```

When grub is installed on Ubuntu I can only use the fallback kernel, using this:
```
initrd    /initramfs-linux-fallback.img
```

Although it boots Xenial, where it is installed without a single message, error or info.

I installed grub back on Arch and just the default seems to work OK. Windows 10 is the 3rd option so, I have that as default.
The picture, font colors, and default option are all in /etc/default/grub. There is no **/etc/grub.d/05_debian_theme** file in Arch.
I purge the lts kernel as I didn't realize that it becomes the default option. I've never had a need for it anyway.

**/etc/grub.d/30_os-prober** is only there if you explicitly install it.

---

### Post by oldfred on 2018-05-18
Just did another 18.04 install to flash drive. First one was extremely slow. Not sure if flash drive or because not final version.
But new install overwrote (as expected) my /EFI/ubuntu in sda, my main working install which I now set to 18.04 (may not be permanent).
But my 18.04, I had changed grub_distributor to my name.
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR='Bionic_18_04'

Then when I did this, it created a new UEFI boot entry, and changed menu entries in grub.
sudo grub-install /dev/sda
Boot0004* bionic_18_04    HD(1,GPT,c371fe4e-a6db-4c46-b056-a4eea609f81d,0x800,0x639c000)/File(\EFI\BIONIC_18_04\SHIMX64.EFI)
But even though /EFI/bionic_18_04 folder had its own grub.cfg, it used /boot/efi/EFI/ubuntu/grub.cfg # or entry from flash drive.
So I had to do this:
sudo grub-install --bootloader-id ubuntu /dev/sda #and set that as default boot in UEFI.

I guess I am now so used to speed of SSD, that flash drive seems slow. But this install a lot quicker than my first flash drive install. Still not sure why.
I only have flash drive install for emergency use.

---

### Post by Cavsfan on 2018-05-19
> **oldfred said:**
> Just did another 18.04 install to flash drive. First one was extremely slow. Not sure if flash drive or because not final version.
But new install overwrote (as expected) my /EFI/ubuntu in sda, my main working install which I now set to 18.04 (may not be permanent).
But my 18.04, I had changed grub_distributor to my name.
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR='Bionic_18_04'

Then when I did this, it created a new UEFI boot entry, and changed menu entries in grub.
sudo grub-install /dev/sda
Boot0004* bionic_18_04    HD(1,GPT,c371fe4e-a6db-4c46-b056-a4eea609f81d,0x800,0x639c000)/File(\EFI\BIONIC_18_04\SHIMX64.EFI)
But even though /EFI/bionic_18_04 folder had its own grub.cfg, it used /boot/efi/EFI/ubuntu/grub.cfg # or entry from flash drive.
So I had to do this:
sudo grub-install --bootloader-id ubuntu /dev/sda #and set that as default boot in UEFI.

I guess I am now so used to speed of SSD, that flash drive seems slow. But this install a lot quicker than my first flash drive install. Still not sure why.
I only have flash drive install for emergency use.

I'm not sure I'm following you. You installed 18.04 from a USB flash drive, Then changed **/etc/default/grub** like this?
```
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR='Bionic_18_04'
``` 

Then you entered **sudo grub-install /dev/sda** and it gave the output of:
```
Boot0004* bionic_18_04 HD(1,GPT,c371fe4e-a6db-4c46-b056-a4eea609f81d,0x800,0x639c000)/File(\EFI\BIONIC_18_04\SHIMX64.EFI)
```

But, that did not work correctly? Because it put the grub in **\EFI\BIONIC_18_04\** ?
So, then you did the 
```
sudo grub-install --bootloader-id ubuntu /dev/sda
``` 
because the default grub was in  **/EFI/bionic_18_04** ?

And that fixed the problem?

This EFI stuff is not getting much clearer to me. I have yet to have a custom entry work and I doubt I could incorporate EFI grub customization with the legacy MBR grub that I am familiar with in this wiki.

---

### Post by oldfred on 2018-05-19
I wanted a unique entry in UEFI  and boot menu description.
And the install of grub created both.
But grub is somewhere hard coded to only use /EFI/ubuntu/grub.cfg in the ESP to find the full install. Or it does not work.
There now is a grub.cfg in my /EFI/bionic_18_04 folder, but it is not used. Before it did not even have a grub.cfg.

So I did another grub install just to see if using the ubuntu description would work, and it did. More because you asked if grub-install worked.
But I normally just manually edit /EFI/ubuntu/grub.cfg to have correct UUID & drive/partition of my default boot.

---

### Post by Cavsfan on 2018-05-20
> **oldfred said:**
> I wanted a unique entry in UEFI  and boot menu description.
And the install of grub created both.
But grub is somewhere hard coded to only use /EFI/ubuntu/grub.cfg in the ESP to find the full install. Or it does not work.
There now is a grub.cfg in my /EFI/bionic_18_04 folder, but it is not used. Before it did not even have a grub.cfg.

So I did another grub install just to see if using the ubuntu description would work, and it did. More because you asked if grub-install worked.
But I normally just manually edit /EFI/ubuntu/grub.cfg to have correct UUID & drive/partition of my default boot.

Ok, thanks for the explanation.

---

### Post by oldfred on 2018-05-20
Whose grub2 are you using to boot.

I wanted to understand some of the differences with grub2, Ubuntu's grub2 and others.
I installed Fedora to a partition on sdb, and it actually let me install to sdb's ESP, combo box on partitioning table actually worked.  But it has notes on updating that if you do not do it correctly, it will end up using a grub2 default of grub in UEFI not Fedora. So they hard code something also to be Fedora.

Ubuntu's grub hard codes the entry in source code  to efi_distributor = "ubuntu" in lots of places in the code. 
Others have efi_distributor = bootloader_id or my change in /etc/default/grub of bootload_id would work in some versions of grub2 and did mostly work in Ubuntu except the use of grub.cfg. Some seem to embed the grub.cfg into grubx64.efi, so then you cannot change it, except with full grub update.

---

### Post by Cavsfan on 2018-05-20
> **oldfred said:**
> Whose grub2 are you using to boot.

I wanted to understand some of the differences with grub2, Ubuntu's grub2 and others.
I installed Fedora to a partition on sdb, and it actually let me install to sdb's ESP, combo box on partitioning table actually worked.  But it has notes on updating that if you do not do it correctly, it will end up using a grub2 default of grub in UEFI not Fedora. So they hard code something also to be Fedora.

Ubuntu's grub hard codes the entry in source code  to efi_distributor = "ubuntu" in lots of places in the code. 
Others have efi_distributor = bootloader_id or my change in /etc/default/grub of bootload_id would work in some versions of grub2 and did mostly work in Ubuntu except the use of grub.cfg. Some seem to embed the grub.cfg into grubx64.efi, so then you cannot change it, except with full grub update.

i'm using Arch Linux's grub since it puts the two img files in the intrd line:
```
initrd    /intel-ucode.img /initramfs-linux.img
```

Ubuntu only puts the first one for some reason and I cannot boot into the normal kernel without using the fallback img.
```
initrd    /intel-ucode.img
```

---

### Post by #&amp;thj^% on 2018-05-20
> **Cavsfan said:**
> i'm using Arch Linux's grub since it puts the two img files in the intrd line:
```
initrd    /intel-ucode.img /initramfs-linux.img
```

Ubuntu only puts the first one for some reason and I cannot boot into the normal kernel without using the fallback img.
```
initrd    /intel-ucode.img
```

+1 Nice Cavsfan
@oldfred I know this was asked of Cavsfan, but if I use Grub I let Arch handle all bootable partitions:
```
pacman -Ss grub
core/grub 2:2.02-5 [installed]
    GNU GRand Unified Bootloader (2)

```
So my "Default Grub" reads like this:
```
# GRUB boot loader configuration

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR='Arch'
GRUB_CMDLINE_LINUX_DEFAULT="quiet resume=UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83347 ipv6.disable=1"
GRUB_CMDLINE_LINUX=""

# Preload both GPT and MBR modules so that they are not missed
GRUB_PRELOAD_MODULES="part_gpt part_msdos"

# Uncomment to enable booting from LUKS encrypted devices
#GRUB_ENABLE_CRYPTODISK=y

# Uncomment to enable Hidden Menu, and optionally hide the timeout count
#GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=true

# Uncomment to use basic console
GRUB_TERMINAL_INPUT=console

# Uncomment to disable graphical terminal
#GRUB_TERMINAL_OUTPUT=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=auto

# Uncomment to allow the kernel use the same resolution used by grub
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you want GRUB to pass to the Linux kernel the old parameter
# format "root=/dev/xxx" instead of "root=/dev/disk/by-uuid/xxx"
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY=true

# Uncomment and set to the desired menu colors.  Used by normal and wallpaper
# modes only.  Entries specified as foreground/background.
#GRUB_COLOR_NORMAL="light-blue/black"
#GRUB_COLOR_HIGHLIGHT="light-cyan/blue"

# Uncomment one of them for the gfx desired, a image background or a gfxtheme
GRUB_BACKGROUND="/home/me/Pictures/bluedandelion.jpg"
#GRUB_THEME="/path/to/gfxtheme"

# Uncomment to get a beep at GRUB start
#GRUB_INIT_TUNE="480 440 1"

# Uncomment to make GRUB remember the last selection. This requires to
# set 'GRUB_DEFAULT=saved' above.
#GRUB_SAVEDEFAULT="true"
```
I will have to add that if I use Fedora I will not let it install grub, far too many issues crop up over time with multi boots.
```
inxi -xxx -D
Drives:
  HDD Total Size: 1.82 TiB used: 38.85 GiB (2.1%) 
  ID-1: /dev/sda vendor: Western Digital model: WD1001FALS-00J7B0 
  size: 931.51 GiB serial: WD-WMATV0362316 rev: 0K05 scheme: GPT 
  ID-2: /dev/sdb vendor: Western Digital model: WD5000AAKS-00V1A0 
  size: 465.76 GiB serial: WD-WCAWF0858813 rev: 1D05 scheme: MBR 
  ID-3: /dev/sdc type: USB vendor: Western Digital model: WD5000BPVT-00HXZT1 
  size: 465.76 GiB serial: WD-WXR1EB0PMV14 scheme: MBR 

```

---

### Post by Cavsfan on 2018-05-20
Nice [COLOR=#000000]1fallen.  I just installed Cosmic Cuttlefish 18.10 UEFI.  I didn't know that was already named and ISOs available. Clearly wasn't paying attention. :P

I've got little hope for adding SSDs and UEFI to the wiki at this point. If I cannot get a single custom boot entry to work, I can imagine the trouble people would have.
Hopefully it will get better with time.

BTW, I just added a Ubuntu bug about grub not putting the Arch Linux boot line correctly. It is on UEFI systems only.

[/COLOR]&#8203;[https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/1772314](https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/1772314)

If you are affected feel free to add your name.

---

### Post by #&amp;thj^% on 2018-05-20
I'll add me too! (And Done added me.)
But as a workaround for myself I just let Arch's grub handle it. (For now anyway :))

---

### Post by Cavsfan on 2018-05-20
> **1fallen said:**
> I'll add me too! (And Done added me.)
But as a workaround for myself I just let Arch's grub handle it. (For now anyway :))

+1
I do the same.

---

### Post by Cavsfan on 2018-05-21
> **1fallen said:**
> I'll add me too! (And Done added me.)
But as a workaround for myself I just let Arch's grub handle it. (For now anyway :))

I see only 1 person on that bug - me. Could you look at that bug again?

[https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/1772314](https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/1772314)

---

### Post by #&amp;thj^% on 2018-05-21
Did you refresh your browser?
You posted 7 hours ago maybe you now see it. :)

---

### Post by Cavsfan on 2018-05-22
> **1fallen said:**
> Did you refresh your browser?
You posted 7 hours ago maybe you now see it. :)

All I seen at the top that this bug affects 1 person. I do see it now though. :)

I also added it to the Arch and derivatives thread hoping it will get attention there. 

[https://ubuntuforums.org/showthread.php?t=2392441](https://ubuntuforums.org/showthread.php?t=2392441)

It's strange because it is a Ubuntu grub bug yet it only affects people with Arch Linux dual booting.

Thanks mate!

---

### Post by Dennis N on 2018-05-22
You may be able to just copy Arch menuentry from the Arch grub.cfg and use that in your Ubuntu custom menus.

I use Manjaro, and have done that to get Ubuntu to boot Manjaro. Otherwise, Ubuntu grub creates the same error when generating the Manjaro grub menu entry.

Manjaro is a distro based on Arch linux.

---

### Post by #&amp;thj^% on 2018-05-22
> **Dennis N said:**
> You may be able to just copy Arch menuentry from the Arch grub.cfg and use that in your Ubuntu custom menus.

I use Manjaro, and have done that to get Ubuntu to boot Manjaro. Otherwise, Ubuntu grub creates the same error when generating the Manjaro grub menu entry.

Manjaro is a distro based on Arch linux.

+1 This also works.

---

### Post by Cavsfan on 2018-05-22
> **Dennis N said:**
> You may be able to just copy Arch menuentry from the Arch grub.cfg and use that in your Ubuntu custom menus.

I use Manjaro, and have done that to get Ubuntu to boot Manjaro. Otherwise, Ubuntu grub creates the same error when generating the Manjaro grub menu entry.

Manjaro is a distro based on Arch linux.

I had an idea that Manjaro did the same. Thanks for confirming that.

I just do not like editing the grub.cfg file for any reason. If my grub is on Ubuntu I'll use the falllback kernel.
But, I do like having it on Arch as I can use the normal kernel.

Grub updated on Xenial Xerus 16.04 this morning and I thought It might fix another problem I'm having with it but, it did not.
So, my grub will go back to Arch for the time being.

But, this bug needs to be fixed and the more people that sign on to it, the better.

---

### Post by Dennis N on 2018-05-23
> I just do not like editing the grub.cfg file for any reason.

I didn't edit any grub.cfg when I did this, only copied the menu entry for Manjaro from the Manjaro /boot/grub/grub.cfg, pasted the copied entry into the template 40_custom  file, then saved it in Ubuntu's /etc/grub.d. I created a new file, but you could add to an existing custom menu file. (You can have any number of custom menu files in /etc/grub.d. No matter - they all get merged into a single grub.cfg when you or the OS executes the update-grub command or its equivalent).

---

### Post by Cavsfan on 2018-05-23
> [COLOR=#000000]*I just do not like editing the grub.cfg file for any reason.*[/COLOR]

> **Dennis N said:**
> I didn't edit any grub.cfg when I did this, only copied the menu entry for Manjaro from the Manjaro /boot/grub/grub.cfg, pasted the copied entry into the template 40_custom  file, then saved it in Ubuntu's /etc/grub.d. I created a new file, but you could add to an existing custom menu file. (You can have any number of custom menu files in /etc/grub.d. No matter - they all get merged into a single grub.cfg when you or the OS executes the update-grub command or its equivalent).

Oh, thanks for the clarification. In my Wiki I say to edit the /etc/grubd/40_custom file but, then save it as /etc/grub.d/06_custom so that it appears on top. (Ranch hand's original idea)
Then when you're sure all of the custom entries work you make 10_linux,  20_memtest86+ and 30_os-prober unexecutable so they no longer appear.

Just so you get some output on an update-grub execution, you _do_ change the part it says not to change so you can add an echo line: (Drs305's original idea)
```
#!/bin/sh
echo 1>&2 "Adding system 1, system 2, etc."
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
```

The +3 you change to +4 so that the 4th line is where execution starts (menuentry).

With Legacy/MBR partitioned systems, that works flawlessly but, so far on UEFI/GPT partitioned systems not so much...

D'oh! Now I see where you said you added it to your custom entry.

---

### Post by Cavsfan on 2018-07-14
@oldfred, I have an entire UEFI system and I wanted to have one grub in control of my system because grub keeps jumping around after an update.
So I tried the 1.8 section of the Wiki for efi:
```
sudo dpkg-reconfigure grub-efi-amd64
```

But, it did not ask me where to install grub at and just ended up installing grub to that partition, which is not the desired outcome.

On my old Legacy/MBR system,
```
sudo dpkg-reconfigure grub-pc
```
did allow me to move the asterisk from the disk to the partition to not have to worry about that grub installing or updating. 

The efi command does not do that and I do not understand why. Any tips?

---

### Post by oldfred on 2018-07-14
With UEFI & gpt, only the ESP has asterisk which parted/gparted use to indicate the ESP.
Other tools like gdisk use different codes to indicate ESP. But with gpt only an ESP can or should have asterisk. Some have multiple FAT32 partitions and switch which is ESP by moving boot flag. But normally you only have one ESP per drive. I put an ESP on every drive, including larger flash drives.

Somewhere in the UEFI version of Ubuntu's grub, it is set to only install to the first ESP, not always sda (but usually), as it seems to work with NVMe drives when they are first.

I installed Fedora, just to see the difference in grub. And it did install to sdb, when I specified that ESP, so grub is configured correctly, it is some change Ubuntu makes to grub. 

Ubuntu's grub also is hard coded to find the UEFI grub in /EFI/ubuntu/grub.cfg. They were updating grub with 18.10 and it installed to /EFI/grub which is standard grub2. But Ubuntu still booted using my old grub.cfg in /EFI/ubuntu, not the updated one with 18.10's UUID in /EFI/grub.
       Ubuntu 18.04 similar error /EFI/grub
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1781042](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1781042)
Ubuntu 18.10 Cosmic installed /EFI/grub
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743)

I always used (hd0,3) or (hd1,gpt4) type to find root partitions with grub. But always had issues when plugging in flash drives. 
So I now am starting to use labels.

Some good examples here:
[https://forum.manjaro.org/t/creating-a-new-os-independent-grub-2-bootloader/3150/4](https://forum.manjaro.org/t/creating-a-new-os-independent-grub-2-bootloader/3150/4)

```
menuentry "Cosmic 18.10 on USB ssd test" {
    search --label --no-floppy --set=root cosmicSSD --hint hd2,gpt4
    configfile /boot/grub/grub.cfg
}

```

---

### Post by Dennis N on 2018-07-14
> grub keeps jumping around after an update.

In the case of updates to grub, one solution is to only allow updating the grub packages on the controlling OS. That works for UEFI or BIOS. Mark the grub packages as 'hold' (or whatever term applies) on the other OSes.

Other Comments:

For Ubuntu 18.04 to always be the controlling OS, I copied it's grub files to another EFI system partition so that they won't be overwritten later by other Ubiquity installs. I had to regenerate the UEFI boot menu entry because of this with an efibootmgr command - but that's a one time thing. And you would also have to use efibootmgr to fix the boot order after installing any new OS, but that is even easier.

On UEFI, I think grub boot files for an OS will only be installed on an EFI system partition which must be FAT, not EXT4 so you can't install grub to the OS partition as we used to do in BIOS. UEFI firmware is only required to read FAT partitions.

---

### Post by Cavsfan on 2018-07-14
> **oldfred said:**
> With UEFI & gpt, only the ESP has asterisk which parted/gparted use to indicate the ESP.
Other tools like gdisk use different codes to indicate ESP. But with gpt only an ESP can or should have asterisk. Some have multiple FAT32 partitions and switch which is ESP by moving boot flag. But normally you only have one ESP per drive. I put an ESP on every drive, including larger flash drives.

Somewhere in the UEFI version of Ubuntu's grub, it is set to only install to the first ESP, not always sda (but usually), as it seems to work with NVMe drives when they are first.

I installed Fedora, just to see the difference in grub. And it did install to sdb, when I specified that ESP, so grub is configured correctly, it is some change Ubuntu makes to grub. 

Ubuntu's grub also is hard coded to find the UEFI grub in /EFI/ubuntu/grub.cfg. They were updating grub with 18.10 and it installed to /EFI/grub which is standard grub2. But Ubuntu still booted using my old grub.cfg in /EFI/ubuntu, not the updated one with 18.10's UUID in /EFI/grub.
       Ubuntu 18.04 similar error /EFI/grub
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1781042](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1781042)
Ubuntu 18.10 Cosmic installed /EFI/grub
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743)

I always used (hd0,3) or (hd1,gpt4) type to find root partitions with grub. But always had issues when plugging in flash drives. 
So I now am starting to use labels.

Some good examples here:
[https://forum.manjaro.org/t/creating-a-new-os-independent-grub-2-bootloader/3150/4](https://forum.manjaro.org/t/creating-a-new-os-independent-grub-2-bootloader/3150/4)

```
menuentry "Cosmic 18.10 on USB ssd test" {
    search --label --no-floppy --set=root cosmicSSD --hint hd2,gpt4
    configfile /boot/grub/grub.cfg
}

```

Thanks for the reply! I'm just thankful that I can get to other grubs to boot into via BIOS. My **Arch_grub** option is always there.
Here is what my /boot/efi/EFI/ folder looks like:
[ATTACH=CONFIG]280393[/ATTACH]

But, much of the time when I try to re-install the grub on Arch, it gives an error something about there is no more room. 
Default was 128KB but I was able to get a 550KB partition and only about 43KB is being used, so if I boot into TTY2 I can install grub without any error.

Also, the folders have folders within them there appear to be the same files. Sometimes in BIOS it will show Arch_grub and another Arch-grub. Not sure what the other one is probably a duplicate.
Sometimes after a grub update on one of the Ubuntu systems, it will boot to a blue screen saying windows has a problem, etc. I think the Windows boot took over when I see that.
But, like I say, I can always get to a bootable grub via BIOS thankfully. 

Even on every other Linux system besides Arch (Xubuntu and openSUSE Tumbleweed) where it fails to add the **/initramfs-linux.img** element to the **initrd** line.
I have to press 'e' and and add it to get to Arch or else use the fallback kernel. Then re-install grub there.

---

### Post by Cavsfan on 2018-07-14
> **Dennis N said:**
> > [COLOR=#000000]*grub keeps jumping around after an update.*[/COLOR]
In the case of updates to grub, one solution is to only allow updating the grub packages on the controlling OS. That works for UEFI or BIOS. Mark the grub packages as 'hold' (or whatever term applies) on the other OSes.

Other Comments:

For Ubuntu 18.04 to always be the controlling OS, I copied it's grub files to another EFI system partition so that they won't be overwritten later by other Ubiquity installs. I had to regenerate the UEFI boot menu entry because of this with an efibootmgr command - but that's a one time thing. And you would also have to use efibootmgr to fix the boot order after installing any new OS, but that is even easier.

On UEFI, I think grub boot files for an OS will only be installed on an EFI system partition which must be FAT, not EXT4 so you can't install grub to the OS partition as we used to do in BIOS. UEFI firmware is only required to read FAT partitions.

Thanks for the post! I guess you are absolutely right about UEFI boot, there is no longer an ext4 partition or disk that grub is installed to but, a partition that is vfat instead. 
So, that explains that! I wasn't thinking about that part. 

Oh, Fred I forgot to mention that I will try that custom entry again when I get a chance.

---

### Post by Cavsfan on 2018-07-23
Right now, I just have a wallpaper added, custom font colors, a default boot menuentry and a longer timeout.
With the way they have added the submenu, after the default menuentry, containing the extra boot entries for a system, that default remains pretty consistent.

---

### Post by Cavsfan on 2018-07-28
Woo Hoo! I am beginning to see how EFI systems can be customized. I just booted into Arch Linux from a custom entry.

Let's see how these other systems work and I'll have more to say. ;)

---

### Post by Cavsfan on 2018-07-28
OK, I successfully booted into Arch Linux, Arch Linux's Fallback kernel, Windows 10, openSUSE Tumbleweed and Bionic Beaver 18.04.1 LTS and all went well.
This is from within Arch Linux though but, the differences should not be much. Just perhaps different on some Linux distributions.
Arch Linux uses the UUID of the EFI system partition as well as the UUID of the Arch partition, for reasons unbeknownst to me.

Here is the custom file I used. I will explain what I did before it's added to the Wiki as I need input from you all to make sure it works first.
Of course I cheat and change that +3 to a +4 so that we can at least see what is between the quotes when doing an update-grub, that and the picture should be the only things you see (a tip Drs305 taught me).
```
#!/bin/sh
echo 1>&2 "Adding Arch Linux, Windows 10, openSUSE Tumbleweed and Xubuntu [COLOR=#000000]Bionic Beaver[/COLOR] 18.04 LTS"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Arch Linux' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-[COLOR=#0000ff]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR]' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_gpt
    insmod fat
    set root='hd2,gpt1'
    search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]688D-126B[/COLOR]
    linux    /vmlinuz-linux root=UUID=[COLOR=#0000ff]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR] rw  quiet
    initrd    /intel-ucode.img /initramfs-linux.img
}
menuentry 'Arch Linux (fallback kernel)' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-linux-fallback-[COLOR=#0000ff]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR]' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_gpt
    insmod fat
    set root='hd2,gpt1'
    search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]688D-126B[/COLOR]
    linux    /vmlinuz-linux root=UUID=[COLOR=#0000ff]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR] rw  quiet
    initrd    /initramfs-linux-fallback.img
}
menuentry 'Windows 10' --class windows --class os $menuentry_id_option 'osprober-efi-[COLOR=#ff0000]688D-126B[/COLOR]' {
    insmod part_gpt
    insmod fat
    set root='hd2,gpt1'
    search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]688D-126B[/COLOR]
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
menuentry 'openSUSE Tumbleweed' --class opensuse --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-[COLOR=#008000]274e3321-d7af-4544-9afa-b1b3c118c325[/COLOR]' {
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt7'
    search --no-floppy --fs-uuid --set=root [COLOR=#008000]274e3321-d7af-4544-9afa-b1b3c118c325[/COLOR]
    linux /boot/vmlinuz root=/dev/sdc7 splash=silent resume=/dev/disk/by-uuid/[COLOR=#ffa07a]be437b2b-9c95-4590-8d32-4da8e6c90318[/COLOR] quiet
    initrd /boot/initrd
}
menuentry 'Ubuntu 18.04.1 LTS' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-[COLOR=#4b0082]899f7460-1d2a-43ab-b98e-5e33953cb0c4[/COLOR]' {
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt8'
    search --no-floppy --fs-uuid --set=root [COLOR=#4b0082]899f7460-1d2a-43ab-b98e-5e33953cb0c4[/COLOR]
    linux /vmlinuz root=UUID=[COLOR=#4b0082]899f7460-1d2a-43ab-b98e-5e33953cb0c4[/COLOR] ro quiet splash $vt_handoff
    initrd /initrd.img
}
```

This is my system:
```
[cavsfan@ArchLinux ~]$ sudo blkid |grep sdc
[sudo] password for cavsfan: 
/dev/sdc1: UUID="[COLOR=#ff0000]688D-126B[/COLOR]" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="3c1b6d6f-8a24-43da-b595-8c304ceee48d"
/dev/sdc3: UUID="C4968A52968A44C0" TYPE="ntfs" PARTLABEL="Windows_10" PARTUUID="345c85f4-bce7-4bc7-bbe0-db03eb319cad"
/dev/sdc4: UUID="701AE4631AE427B4" TYPE="ntfs" PARTUUID="1e337754-b45d-45a5-a971-b8cdcae8a002"
/dev/sdc5: UUID="[COLOR=#ffa07a]be437b2b-9c95-4590-8d32-4da8e6c90318[/COLOR]" TYPE="swap" PARTLABEL="Basic data partition" PARTUUID="3a259867-656d-41ed-9931-cf15a3bd0148"
/dev/sdc6: LABEL="ArchLinux" UUID="[COLOR=#0000ff]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR]" TYPE="ext4" PARTLABEL="Arch_Linux" PARTUUID="5312b771-0835-4957-80a6-9a8a7107f24a"
/dev/sdc7: LABEL="opensuse" UUID="[COLOR=#008000]274e3321-d7af-4544-9afa-b1b3c118c325[/COLOR]" TYPE="ext4" PARTUUID="25d7851a-f45f-4d60-955a-4a31706f8452"
/dev/sdc8: LABEL="Bionic" UUID="[COLOR=#4b0082]899f7460-1d2a-43ab-b98e-5e33953cb0c4[/COLOR]" TYPE="ext4" PARTLABEL="Bionic_Beaver" PARTUUID="c4e0fdc9-7eac-4661-a7c6-c5a00c9a46fc"
/dev/sdc10: LABEL="Media" UUID="840ac879-510a-4b8d-be01-9d3a5f37dbb2" TYPE="ext4" PARTLABEL="Media" PARTUUID="61e2e7f9-1a98-44f7-881e-ae85fceaf994"
/dev/sdc2: PARTLABEL="Microsoft reserved partition" PARTUUID="49992d5b-79cd-4934-a12f-11782bb345bd"

```

So, this should boot an Ubuntu system, just the partitions and UUID needs changed to match your system.
```
#!/bin/sh
echo 1>&2 "Adding Xubuntu Bionic Beaver 18.04.1 LTS"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Ubuntu 18.04.1 LTS' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-[COLOR=#4b0082]899f7460-1d2a-43ab-b98e-5e33953cb0c4[/COLOR]' {
    insmod part_gpt
    insmod ext2
    set root='[COLOR=#4b0082]hd2,gpt8[/COLOR]'
    search --no-floppy --fs-uuid --set=root [COLOR=#4b0082]899f7460-1d2a-43ab-b98e-5e33953cb0c4[/COLOR]
    linux /vmlinuz root=UUID=[COLOR=#4b0082]899f7460-1d2a-43ab-b98e-5e33953cb0c4[/COLOR] ro quiet splash $vt_handoff
    initrd /initrd.img
}
```

Right now I see no way to boot Ubuntu to a backup kernel because there is only a /vmlinuz file and no /vmlinuz.old file. Which may be because I haven't had enough kernels get installed yet.

So, this is a tad more complicated than the Legacy/MBR partitioned systems were but, at least you do not have to go to the OS where your grub is installed and update the grub there when a kernel is added to a different system.
Because the default grub has the /vmlinuz and /initrd tied to a kernel number.

A lot if not all of each entry can be copied from the existing /boot/grub/grub.cfg file and then modified, which makes it MUCH easier.

---

### Post by Cavsfan on 2018-07-28
First picture of a customized EFI Grub menu. I just took a picture of the menu, which is sort of small but, could not make out the highlighted color of red taking the whole screen.

 [[IMG]http://i.imgur.com/tvcOyrtl.jpg[/IMG]]("https://imgur.com/tvcOyrt")

All of them work so I made **/etc/grub.d/10_linux** and **/etc/grub.d/30_os-prober** unexecutable.

---

### Post by oldfred on 2018-07-29
I use a configfile to boot the grub of my other Ubuntu installs.
And I now like labels over UUID, but you have to manage labels. When I re-install cosmic and reformat partition, it needs label updated.
You can then have two entries, one to directly boot kernel, and one to configfile to that installs grub with all its entries. I only have used configile to other grub so far.

```

menuentry "Cosmic 18.10 on sdb12" {
    configfile (hd2,gpt12)/boot/grub/grub.cfg
}

menuentry "Cosmic 18.10 on sdb12 test" {
    search --set=root --label cosmic_b --hint hd2,gpt12
    configfile /boot/grub/grub.cfg
}

menuentry 'Live ISOs on SSD' {
search --set=root --label iso_ssd --hint hd1,gpt5
configfile /livecdimage.cfg
} 

menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 
```

---

### Post by Cavsfan on 2018-07-30
> **oldfred said:**
> I use a configfile to boot the grub of my other Ubuntu installs.
And I now like labels over UUID, but you have to manage labels. When I re-install cosmic and reformat partition, it needs label updated.
You can then have two entries, one to directly boot kernel, and one to configfile to that installs grub with all its entries. I only have used configile to other grub so far.

```

menuentry "Cosmic 18.10 on sdb12" {
    configfile (hd2,gpt12)/boot/grub/grub.cfg
}

menuentry "Cosmic 18.10 on sdb12 test" {
    search --set=root --label cosmic_b --hint hd2,gpt12
    configfile /boot/grub/grub.cfg
}

menuentry 'Live ISOs on SSD' {
search --set=root --label iso_ssd --hint hd1,gpt5
configfile /livecdimage.cfg
} 

menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 
```

+1 
I never would have guessed you could do that with a config file!

---

### Post by Cavsfan on 2018-08-02
OK, for EFI, I copied the exact code from above into Xubuntu 18.04 and successfully booted into each operating system so I know that it works on Ubuntu.

Guess I'll add it to the Wiki when I can.

Basically everything is the same in **/etc/default/grub** you just change 2 entries. Also the same in **/etc/grub.d/05_debian_theme**, the 3 menu colors go after line 122.

It's just the menu entries in **/etc/grub.d/06_custom** that have drastically changed.

One cannot no longer prevent grub from moving from one system to another if grub is updated and installed on that other system.

It's also best to back up the EFI grub immediately after installing a Ubuntu system if you plan on installing another one.

I have Arch Linux, Windows 10, openSUSE Tumbleweed and Xubuntu 18.04 LTS installed currently and this is what I mean:
```
cavsfan@cavsfan-Bionic-Beaver:~$ sudo su
[sudo] password for cavsfan:
root@cavsfan-Bionic-Beaver:/home/cavsfan# cd /boot/efi/EFI
root@cavsfan-Bionic-Beaver:/boot/efi/EFI# ls
[COLOR=#0000ff]Arch_grub  bionic  Boot  Microsoft  opensuse  ubuntu[/COLOR]

```

The blue is just meant to denote folders. I copied ubuntu to bionic to back it up.

The grub install command has also changed drastically for EFI as you may as well already know.
```
sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi/EFI/ubuntu --bootloader-id=ubuntu  --recheck
```
I am not sure if every system is the same, you just have to look for this root owned/read only ubuntu folder to re-install grub back on Ubuntu.

---

### Post by Cavsfan on 2018-08-21
Since no feedback, I guess I am not going to add EFI booting to the Wiki at this time. Everything you need though is in [post #534]("https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787614#post13787614").

It contains the contents of **/etc/grub.d/06_custom** for booting to Ubuntu, Arch Linux, openSUSE and Windows 10.

It has worked for me very, very well for quite a while now.

---

### Post by Cavsfan on 2019-02-08
Well, after some time and thought, I think I'll add the menuentries for an UEFI (Unified Extensible Firmware Interface) system (SSD) to the Wiki. 

I've learned there are several ways that one *could* customize the UEFI grub but, the only sure fire way I have been able to do it is with UUIDs.

Everything else is the same: the fonts, background picture. Just the menuentries and the way you install grub is different.
Just like the Legacy/MBR partitioned custom grub, this does not ever require any changes except for the same reasons the Non-UEFI systems would.

I've learned how to customize UEFI grub for Ubuntu, Arch Linux, Fedora and openSUSE. I will only include Ubuntu and Windows 10 in the Wiki though. 
If anyone would be interested in any of the others, just ask and I will happily provide that too.

I do not know how long it will take me but, it will be done.

---

### Post by Cavsfan on 2019-04-01
Ok, I figured out what was necessary and what was superfluous in the previous posts I have made about a custom UEFI grub.

I updated the Wiki, only the menuentries and way to install grub has changed on Ubuntu. I have been installing and experiencing many different Linux systems.

I would customize each one and there are various differences from system to system.

I currently have Arch Linux, Fedora 29, openSUSE Tumbleweed, MX Linux 18.1 Continuum, Xubuntu 18.04 LTS and Windows 10.

If anyone is interested in more information about anything whatsoever, post it here.

For example here is how easy one boot entry is for Xubuntu Bionic Beaver 18.04 LTS linking UUIDs:
```
/dev/sdc4: UUID="[COLOR=#ff0000]bbc771f8-ba61-4e50-aeca-d2754b112aee[/COLOR]" TYPE="[COLOR=#ff0000]swap[/COLOR]" PARTLABEL="swap" PARTUUID="dc354366-1300-48d4-8a60-133aa2e2ca57"
/dev/sdc9: LABEL="Bionic" UUID="[COLOR=#0000ff]833501fb-4f83-4d51-9903-685d56cb6891[/COLOR]" TYPE="ext4" PARTLABEL="Bionic" PARTUUID="4f579967-b025-47dc-b080-64a0865d7165"

``````
menuentry '18.04 LTS (Bionic Beaver) LTS' {
    search --no-floppy --fs-uuid --set=root [COLOR=#0000ff]833501fb-4f83-4d51-9903-685d56cb6891[/COLOR]
    linux /vmlinuz root=UUID=[COLOR=#0000ff]833501fb-4f83-4d51-9903-685d56cb6891[/COLOR] ro quiet resume=/dev/disk/by-uuid/[COLOR=#ff0000]bbc771f8-ba61-4e50-aeca-d2754b112aee[/COLOR] splash
    initrd /initrd.img
}

```
Also, let me know if I have made any mistakes.

---

### Post by Cavsfan on 2019-04-03
In Fedora and MX Linux, it does not create symlinks for the **vmlinuz** and **initrd** like most Linux systems.

But, I created a script that will create them after the kernel is installed. If anyone wants to know how it works, I gots it. :P

---

### Post by Cavsfan on 2019-06-28
I have 4 drives in this computer.

 
[LIST=1]
[*]dev/sda - TOSHIBA 2TB HDD
[*]dev/sdb - TOSHIBA 2TB HDD
[*]dev/sdc - WD Blue 1TB SSD
[*]dev/sdd - OCZ Vertex 480GB SSD
[/LIST]

The 2nd TOSHIBA apparently is bad because it prevented it from booting when connected. 
So, I disconnected it and sdc became sdb but, my custom grub didn't skip a beat because it is tied to UUIDs and not drives.

I believe if I were using default grub, it would have needed some adjustments. Another reason to use a custom grub. :D

---

### Post by Cavsfan on 2019-07-19
Anyone multi-booting with Fedora 30, I finally figured out how to produce the kernel symlinks with this script: (the one I was using in Fedora 28,29 didn't work in 30)
```
#!/bin/bash
#

# We're passed the kernel version being installed
KERNEL_VERSION="$1"

ln -s -f "initramfs-"${1}".img" /boot/initrd.img

ln -s -f "vmlinuz-"${1} /boot/vmlinuz

echo "   SUCCESS: symlink initrd.img created for "initramfs-"${1}".img"" >&2
echo "   SUCCESS: symlink vmlinuz created for "vmlinuz-"${1}" >&2

exit 0


```

Save it as 52-symlink-kernel and if it's in your home directory, you would first [COLOR=#333333]make it executable [/COLOR]**sudo chmod +x 52-symlink-kernel**
Then to install it you would use this command: 
```
sudo install 52-symlink-kernel /etc/kernel/postinst.d/52-symlink-kernel
```

Then in the terminal output of a new kernel installation you will see the SUCCESS lines. You can check in /boot with **ls -lA** and verify that they are symlinked correctly.

Cheers ;)

---

### Post by Cavsfan on 2019-11-12
Custom grub on Fedora 31. No background, colors or fonts; just a custom menu:

[[IMG]http://i.imgur.com/yerb7Icm.jpg[/IMG]]("https://imgur.com/yerb7Ic")

The script above that works in 30 also works in 31 to create the kernel symlinks.

---

### Post by malspa on 2019-11-12
From the linked page:

> Although it says not to, you will need to change
exec tail -n +3 $0 to
exec tail -n +4 $0

Why?

---

### Post by malspa on 2019-11-12
Oh, and thanks very much for all the work on that "MaintenanceFreeCustomGrub2Screen" page, and this thread -- it's all been a big help to me. I've done lots of maintenance-free grub setups in the past, dual-booting or multi-booting. I used these valuable resources most recently to set up a maintenance-free grub for dual-booting two Debian Buster systems.

---

### Post by Cavsfan on 2019-12-12
> **malspa said:**
> From the linked page:

> [COLOR=#000000]*Although it says not to, you will need to change*[/COLOR]
[COLOR=#000000]*exec tail -n +3 $0 to*[/COLOR]
[COLOR=#000000]*exec tail -n +4 $0*[/COLOR]

Why?

[B](1)#!/bin/sh
(2)echo 1>&2 "Adding Bionic Beaver 18.04 LTS, Ubuntu Version name nn.nn and Windows 10"
(3)exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.[/B]

The reason to change it to 4 is so it starts execution on the 4th line, the **menuentry** line ***_if_*** you add the echo line to get some output when you enter update-grub.

If you do not include the echo line, the first menuentry line is the the 3rd line and you would leave it **+3**.

> **malspa said:**
> Oh, and thanks very much for all the work on that "MaintenanceFreeCustomGrub2Screen" page, and this thread -- it's all been a big help to me. I've done lots of maintenance-free grub setups in the past, dual-booting or multi-booting. I used these valuable resources most recently to set up a maintenance-free grub for dual-booting two Debian Buster systems.

Thank you for the kind words!

---

### Post by Cavsfan on 2019-12-14
> **malspa said:**
> From the linked page:

> [COLOR=#000000][COLOR=#000000]*[I]Although it says not to, you will need to change*[/I][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]*[I]exec tail -n +3 $0 to*[/I][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]*[I]exec tail -n +4 $0*[/I][/COLOR][/COLOR]

Why?

This is my current **06_custom** file - (**/etc/grub.d/06_custom**):
```
#!/bin/sh
[COLOR=#ff0000]echo 1>&2 "Adding Arch Linux (rolling), Debian Buster, Debian Testing, Fedora 30 (Thirty), Fedora 31 (Thirty One), openSUSE Tumbleweed (rolling), MX Linux 18.3 Continuum, MX Linux 19 (Antix kernel) Patito Feo, MX Linux 19 Patito Feo, Xubuntu 18.04.3 Bionic Beaver LTS and Windows 10"[/COLOR]
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Arch Linux' {
    search --no-floppy --fs-uuid --set=root 688D-126B
    linux  /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw quiet
    initrd /intel-ucode.img /initramfs-linux.img
}
menuentry 'Arch Linux (fallback kernel)' {
    search --no-floppy --fs-uuid --set=root 688D-126B
    linux  /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw quiet
    initrd /initramfs-linux-fallback.img
}
menuentry 'Debian Buster' {
    search --no-floppy --fs-uuid --set=root dbbd22d7-0110-47d4-932b-2f19c83bcbca
    linux  /vmlinuz root=UUID=dbbd22d7-0110-47d4-932b-2f19c83bcbca ro quiet
    initrd /initrd.img
}
menuentry 'Debian Buster (recovery mode)' {
    search --no-floppy --fs-uuid --set=root dbbd22d7-0110-47d4-932b-2f19c83bcbca
    linux  /vmlinuz root=UUID=dbbd22d7-0110-47d4-932b-2f19c83bcbca ro recovery nomodeset
    initrd /initrd.img
}
menuentry 'Debian Testing' {
    search --no-floppy --fs-uuid --set=root 1b019591-4bf0-4781-bf86-fdc044ef8ae7
    linux  /vmlinuz root=UUID=1b019591-4bf0-4781-bf86-fdc044ef8ae7 ro quiet
    initrd /initrd.img
}
menuentry 'Debian Testing (recovery mode)' {
    search --no-floppy --fs-uuid --set=root 1b019591-4bf0-4781-bf86-fdc044ef8ae7
    linux  /vmlinuz root=UUID=1b019591-4bf0-4781-bf86-fdc044ef8ae7 ro recovery nomodeset
    initrd /initrd.img
}
menuentry 'Fedora 30 (Thirty)' {
    search --no-floppy --fs-uuid --set=root 43cd93b8-2442-42df-88a3-7bf069390d49
    linux  /boot/vmlinuz root=UUID=43cd93b8-2442-42df-88a3-7bf069390d49 ro rd.driver.blacklist=nouveau modprobe.blacklist=nouveau nvidia-drm.modeset=1 resume=UUID=b564ed75-b9ee-410f-9f87-04afc30a0ff4 rhgb quiet LANG=en_US.UTF-8
    initrd /boot/initrd.img
}
menuentry 'Fedora 31 (Thirty One)' {
    search --no-floppy --fs-uuid --set=root 3ba4cef1-ee4e-47a9-acd4-52bccb07a237
    linux  /boot/vmlinuz root=UUID=3ba4cef1-ee4e-47a9-acd4-52bccb07a237 ro rd.driver.blacklist=nouveau modprobe.blacklist=nouveau nvidia-drm.modeset=1 resume=UUID=b564ed75-b9ee-410f-9f87-04afc30a0ff4 rhgb quiet LANG=en_US.UTF-8
    initrd /boot/initrd.img
}
menuentry 'openSUSE Tumbleweed (rolling)' {
    search --no-floppy --fs-uuid --set=root 00bd1c4f-112a-493b-b956-63c414cb844a
    linux  /boot/vmlinuz root=UUID=00bd1c4f-112a-493b-b956-63c414cb844a splash=silent resume=/dev/disk/by-uuid/b564ed75-b9ee-410f-9f87-04afc30a0ff4 mitigations=auto quiet
    initrd /boot/initrd
}
menuentry 'MX Linux 18.3 Continuum' {
        search --no-floppy --fs-uuid --set=root e2a9be0a-6b63-40e9-9a3f-029b14c8403e
        linux  /boot/vmlinuz root=UUID=e2a9be0a-6b63-40e9-9a3f-029b14c8403e ro quiet splash
        initrd /boot/initrd
}
menuentry 'MX Linux 18.3 Continuum - Systemd' {
        search --no-floppy --fs-uuid --set=root e2a9be0a-6b63-40e9-9a3f-029b14c8403e
        linux  /boot/vmlinuz root=UUID=e2a9be0a-6b63-40e9-9a3f-029b14c8403e ro quiet splash init=/lib/systemd/systemd
        initrd /boot/initrd
}
menuentry 'MX Linux 19 (Antix kernel) Patito Feo' {
        search --no-floppy --fs-uuid --set=root 66eebc19-c3f8-4b17-b912-0c5099ca7ae4
        linux  /boot/vmlinuz-antix root=UUID=66eebc19-c3f8-4b17-b912-0c5099ca7ae4 ro quiet splash
        initrd /boot/initrd-antix.img
}
menuentry 'MX Linux 19 (Antix kernel) Patito Feo Systemd' {
        search --no-floppy --fs-uuid --set=root 66eebc19-c3f8-4b17-b912-0c5099ca7ae4
        linux  /boot/vmlinuz-antix root=UUID=66eebc19-c3f8-4b17-b912-0c5099ca7ae4 ro quiet splash init=/lib/systemd/systemd
        initrd /boot/initrd-antix.img
}
menuentry 'MX Linux 19 Patito Feo' {
        search --no-floppy --fs-uuid --set=root 66eebc19-c3f8-4b17-b912-0c5099ca7ae4
        linux  /boot/vmlinuz root=UUID=66eebc19-c3f8-4b17-b912-0c5099ca7ae4 ro quiet splash
        initrd /boot/initrd.img
}
menuentry 'MX Linux 19 Patito Feo Systemd' {
        search --no-floppy --fs-uuid --set=root 66eebc19-c3f8-4b17-b912-0c5099ca7ae4
        linux  /boot/vmlinuz root=UUID=66eebc19-c3f8-4b17-b912-0c5099ca7ae4 ro quiet splash init=/lib/systemd/systemd
        initrd /boot/initrd.img
}
menuentry 'Xubuntu 18.04.3 Bionic Beaver LTS' {
    search --no-floppy --fs-uuid --set=root 338e6d3b-cbd4-496d-9cc2-b688a90c17c3
    linux  /vmlinuz root=UUID=338e6d3b-cbd4-496d-9cc2-b688a90c17c3 ro quiet resume=/dev/disk/by-uuid/b564ed75-b9ee-410f-9f87-04afc30a0ff4 splash
    initrd /initrd.img
}
menuentry 'Xubuntu 18.04.3 Bionic Beaver LTS (recovery mode)' {
    search --no-floppy --fs-uuid --set=root 338e6d3b-cbd4-496d-9cc2-b688a90c17c3
    linux  /vmlinuz root=UUID=338e6d3b-cbd4-496d-9cc2-b688a90c17c3 ro recovery nomodeset
    initrd /initrd.img
}
menuentry 'Windows 10' {
    set root='hd2,gpt1'
    search --no-floppy --fs-uuid --set=root 688D-126B
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

```

My partitions:
```
sudo blkid | grep sdc
/dev/sdc1: UUID="688D-126B" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="15661847-bc65-401a-84b0-97a157f3949f"
/dev/sdc2: PARTLABEL="Microsoft reserved partition" PARTUUID="6b26da12-6fdc-4ce5-bde3-c990cdfc081b"
/dev/sdc3: LABEL="C:" UUID="C4968A52968A44C0" TYPE="ntfs" PARTLABEL="Windows_10" PARTUUID="a76c4894-4d85-457e-8bc6-9d5308bef571"
/dev/sdc4: UUID="9C9AE5269AE4FE20" TYPE="ntfs" PARTUUID="94858fd1-334c-47f7-bfab-266b49f0a0ba"
/dev/sdc5: UUID="b564ed75-b9ee-410f-9f87-04afc30a0ff4" TYPE="swap" PARTLABEL="swap" PARTUUID="dc354366-1300-48d4-8a60-133aa2e2ca57"
/dev/sdc6: LABEL="ArchLinux" UUID="bbca28b2-503e-4dc8-9850-c54bd0492da8" TYPE="ext4" PARTLABEL="Arch_Linux" PARTUUID="ea32dc7f-6d56-4a5c-b544-008abb8026e4"
/dev/sdc7: LABEL="Media" UUID="840ac879-510a-4b8d-be01-9d3a5f37dbb2" TYPE="ext4" PARTLABEL="Media" PARTUUID="7af1d6dd-bfac-4c24-90ef-8da3d218898d"
/dev/sdc8: LABEL="openSUSE" UUID="00bd1c4f-112a-493b-b956-63c414cb844a" TYPE="ext4" PARTLABEL="openSUSE" PARTUUID="dcaa5edb-0510-4bab-93e4-b238b329dbf7"
/dev/sdc9: LABEL="Fedora" UUID="43cd93b8-2442-42df-88a3-7bf069390d49" TYPE="ext4" PARTLABEL="Fedora" PARTUUID="ee5e61eb-eab9-4794-aabe-a84a910fe9a0"
/dev/sdc10: LABEL="Bionic" UUID="338e6d3b-cbd4-496d-9cc2-b688a90c17c3" TYPE="ext4" PARTLABEL="Bionic" PARTUUID="4f579967-b025-47dc-b080-64a0865d7165"
/dev/sdc11: LABEL="rootMX18.3" UUID="e2a9be0a-6b63-40e9-9a3f-029b14c8403e" TYPE="ext4" PARTLABEL="mxlinux18" PARTUUID="e9eae6c4-f48a-4aa2-ba97-0ccadb7aa32f"
/dev/sdc12: LABEL="Fedora31" UUID="3ba4cef1-ee4e-47a9-acd4-52bccb07a237" TYPE="ext4" PARTLABEL="Fedora31" PARTUUID="c76d0607-d89b-49b5-82fd-f0460ec47cfe"
/dev/sdc13: LABEL="Debian-Buster" UUID="dbbd22d7-0110-47d4-932b-2f19c83bcbca" TYPE="ext4" PARTLABEL="Debian-Buster" PARTUUID="0e1cf947-9391-43d2-8d26-4384b98015a6"
/dev/sdc14: LABEL="Debian-Testing" UUID="1b019591-4bf0-4781-bf86-fdc044ef8ae7" TYPE="ext4" PARTLABEL="Debian-Testing" PARTUUID="9b354d04-fd5e-48b3-a8f0-35cc873eb7e6"
/dev/sdc15: LABEL="rootMX19" UUID="66eebc19-c3f8-4b17-b912-0c5099ca7ae4" TYPE="ext4" PARTLABEL="rootMX19" PARTUUID="ab7453e8-12b2-4530-9408-313bc9d8828f"

```

Sort of like a puzzle to be setup once.

---

### Post by Cavsfan on 2020-07-03
It took me awhile but, I finally figured out what most people probably already knew. :p

When I customized Xubuntu 20.04 grub the menu would always never show, so rather than delving in to see what the problem was I had my grub on another system that didn't do that. 

Anyway, I err um, stumbled upon the fact that if I pressed the ESC key the menu would show. Figured out why that was in **/etc/default/grub**:
Just needed to change this:
```
GRUB_TIMEOUT_STYLE=hidden
```
to this:
```
GRUB_TIMEOUT_STYLE=menu
```
Then everything worked like it should. ;)

---

### Post by Cavsfan on 2020-07-04
on Xubuntu 20.04:

[[img]http://i.imgur.com/FcqRsunl.jpg[/img]](https://imgur.com/FcqRsun)

---

### Post by Cavsfan on 2020-07-31
> **Cavsfan said:**
> It took me awhile but, I finally figured out what most people probably already knew. :p

When I customized Xubuntu 20.04 grub the menu would always never show, so rather than delving in to see what the problem was I had my grub on another system that didn't do that. 

Anyway, I err um, stumbled upon the fact that if I pressed the ESC key the menu would show. Figured out why that was in **/etc/default/grub**:
Just needed to change this:
```
GRUB_TIMEOUT_STYLE=hidden
```
to this:
```
GRUB_TIMEOUT_STYLE=menu
```
Then everything worked like it should. ;)

Turns out my 18.04 install had this same issue. That should solve it and I updated the Wiki.
If anyone has any problem on any version let me know.

---

### Post by von Stalhein on 2020-08-13
Hi Cavsfan - my old frankenbox finally fell over so I bit the bullet and went all new. This combo should last a week before obsolescence, it's that cutting edge :-)

Anyway, upon plugging in HDDs and booting I saw the same thing in the GRUB menu, very truncated. Luckily I remembered your post!

Keep up the good work!

---

### Post by Cavsfan on 2020-08-15
> **von Stalhein said:**
> Hi Cavsfan - my old frankenbox finally fell over so I bit the bullet and went all new. This combo should last a week before obsolescence, it's that cutting edge :-)

Anyway, upon plugging in HDDs and booting I saw the same thing in the GRUB menu, very truncated. Luckily I remembered your post!

Keep up the good work!

Newer is always nice. Mine is a beast but, it's a few years old with a 4th gen i7.

Glad I could help! :)

---

### Post by Cavsfan on 2020-09-03
Grub on Bionic Beaver 18.04.5. 

[[IMG]http://i.imgur.com/6gBFfhIl.jpg[/IMG]]("https://imgur.com/6gBFfhI")

---

### Post by Cavsfan on 2021-01-19
If you dual or multi boot Linux systems and are interested in preventing your grub moving from one partition to another every time a new version of grub is installed. There are some steps you can take.

I currently have mine on Fedora 33 but I am booting Arch Linux, Fedora 33, openSUSE Tumbleweed, Xubuntu 18.04, Xubuntu 20.04 and Xubuntu 20.10.
On Ubuntu you can put the grub packages on hold with this command:
```
sudo apt-mark hold <pkg>
```

[apt-mark man page]("https://manpages.ubuntu.com/manpages/bionic/man8/apt-mark.8.html")

I was customizing all my systems because grub moves from one to another, Ubuntu and openSUSE do anyway.

This makes it so you only have to worry about customizing one system.

Just thought I'd mention it. Working pretty well here.

---

### Post by Michael Dooley on 2021-02-15
Thanks Cavsfan for this thread. I recently acquired a laptop from Ebay that had a UEFI bios. So far I've managed to get things set up in 06_custom so as to boot everything except a live CD or ISO.

#!/bin/sh
echo 1>&2 "Adding MATE 20.04 LTS focal, MATE 21.04 hirsute, live CD + parted magic"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Ubuntu-MATE 20.04 (on /dev/sda5)' {
	search --no-floppy --fs-uuid --set=root e5cc4b83-5a56-4d3e-b885-dee279e6d6eb
	linux /boot/vmlinuz root=UUID=e5cc4b83-5a56-4d3e-b885-dee279e6d6eb ro  quiet splash $vt_handoff
	initrd /boot/initrd.img
}
menuentry 'Ubuntu-MATE 21.04 (on /dev/sda8)' {
	search --no-floppy --fs-uuid --set=root 1588c768-4536-43d7-963f-2ababd7d4022
	linux /boot/vmlinuz root=UUID=1588c768-4536-43d7-963f-2ababd7d4022 ro quiet splash $vt_handoff
	initrd /boot/initrd.img
}
menuentry 'live CD (on /dev/sda5)' {
    search --no-floppy --fs-uuid --set=root e5cc4b83-5a56-4d3e-b885-dee279e6d6eb
    set isofile="/home/data/Iso/ubuntu-mate-16.04.4-desktop-amd64.iso"
    loopback loop (hd1,msdos5)$isofile
    linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile quiet splash
    initrd (loop)/casper/initrd.lz
}
menuentry 'Parted Magic (on /dev/sda5)' {
	search --no-floppy --fs-uuid --set=root e5cc4b83-5a56-4d3e-b885-dee279e6d6eb
	linux /boot/pmagic/bzImage64 root=/dev/sda5 directory=boot edd=on vga=normal
	initrd /boot/pmagic/initrd.img /boot/pmagic/fu.img /boot/pmagic/m64.img
}

There seems to be a bug in grub 2.04  Please see - [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1851311)
The bug probably is keeping me from mounting an ISO. Do you have any thoughts as to what I might do to solve or work around this issue?

---

### Post by oldfred on 2021-02-15
I just installed Hirsute using UEFI & loopmount.

My configuration is a bit involved as I use a data partition and configfile into the ISO folder in the data partition. And in ISO folder I have a file livecdimage.cfg which has all my ISO boot info. I always forgot to update grub, so I now use configfile into the text file as then I do not have to update grub. Note inconsistency with hd0 & hd1, I often have to manually edit one or the other as I boot.

In 40_custom:
[FONT=monospace]```
[COLOR=#000000]menuentry 'Live ISOs in data drive' { [/COLOR]
search --set=root --label nvme_data --hint hd0,gpt5 
configfile /ISO/livecdimage.cfg 
}

```

Then in [/FONT][FONT=monospace][FONT=monospace]/ISO/livecdimage.cfg

[/FONT]```
menuentry "Kubuntu 21.04 Live ISO" {
    set isofile="/ISO/hirsute-desktop-amd64.iso"
    rmmod tpm
    loopback loop (hd1,5)$isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram noeject
        initrd (loop)/casper/initrd
}


```

Because I installed to sda drive but boot from NVMe drive, I have a numbering issue. Default boot is always hd0, but if I boot NVMe drive as hd0, my install in sda drive becomes hd1. But I also have an external drive plugged in and that often changes order again. It my only work after I unplug external drive, just to avoid confusion (mine).
[/FONT]

---

### Post by #&amp;thj^% on 2021-02-15
> **oldfred said:**
> I just installed Hirsute using UEFI & loopmount.

My configuration is a bit involved as I use a data partition and configfile into the ISO folder in the data partition. And in ISO folder I have a file livecdimage.cfg which has all my ISO boot info. I always forgot to update grub, so I now use configfile into the text file as then I do not have to update grub. Note inconsistency with hd0 & hd1, I often have to manually edit one or the other as I boot.

In 40_custom:
[FONT=monospace]```
[COLOR=#000000]menuentry 'Live ISOs in data drive' { [/COLOR]
search --set=root --label nvme_data --hint hd0,gpt5 
configfile /ISO/livecdimage.cfg 
}

```

Then in [/FONT][FONT=monospace][FONT=monospace]/ISO/livecdimage.cfg

[/FONT]```
menuentry "Kubuntu 21.04 Live ISO" {
    set isofile="/ISO/hirsute-desktop-amd64.iso"
    rmmod tpm
    loopback loop (hd1,5)$isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram noeject
        initrd (loop)/casper/initrd
}


```

Because I installed to sda drive but boot from NVMe drive, I have a numbering issue. Default boot is always hd0, but if I boot NVMe drive as hd0, my install in sda drive becomes hd1. But I also have an external drive plugged in and that often changes order again. It my only work after I unplug external drive, just to avoid confusion (mine).
[/FONT]

Brilliant! :KS
Thanks for the share oldfred,

---

### Post by Michael Dooley on 2021-02-15
I'll look up this configfile business as I have a data partition too. But only one SSHD.

> My configuration is a bit involved as I use a data partition and configfile into the ISO folder in the data partition. And in ISO folder I have a file livecdimage.cfg which has all my ISO boot info. 

How do I make these config files?

I read oldfred's post with more attention to detail and came up with my livecdimage.cfg file.

This is it -

menuentry "Ubuntu-Mate 18.04 Live ISO" {
    set isofile="/Iso/-amd64/ubuntu-mate-18.04.4-desktop-amd64.iso"
    rmmod tpm
    loopback loop (hd0,7)$isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram noeject
        initrd (loop)/casper/initrd
}

Getting closer but no boot to ISO yet. I'll post back with observations and details once I get this working. My suspicion is that I'll have to install a different grub.

---

### Post by Cavsfan on 2021-02-18
> **Michael Dooley said:**
> Thanks Cavsfan for this thread. I recently acquired a laptop from Ebay that had a UEFI bios. So far I've managed to get things set up in 06_custom so as to boot everything except a live CD or ISO.

Thanks for the kind words! Although, I have never used a grub entry to mount a live ISO; I've no doubt that it can be done as Fred and 1fallen have done it.

> **Michael Dooley said:**
> I'll look up this configfile business as I have a data partition too. But only one SSHD.



How do I make these config files?

I read oldfred's post with more attention to detail and came up with my livecdimage.cfg file.

This is it -

menuentry "Ubuntu-Mate 18.04 Live ISO" {
    set isofile="/Iso/-amd64/ubuntu-mate-18.04.4-desktop-amd64.iso"
    rmmod tpm
    loopback loop (hd0,7)$isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram noeject
        initrd (loop)/casper/initrd
}

Getting closer but no boot to ISO yet. I'll post back with observations and details once I get this working.
My suspicion is that I'll have to install a different grub.

I was _never_ able to get *any* config file to boot and I tried many times. Let me know when you get that to work.
I use UUIDs to link the partitions in my custom grub menu. It's as simple as I could get it; I figured out what was necessary and it makes sense to me.
```
[cavsfan@Arch ~]$ sudo blkid | grep -e EFI -e sdc5 -e Bionic
/dev/sdc1: UUID="688D-126B" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="15661847-bc65-401a-84b0-97a157f3949f"
/dev/sdc5: UUID="[COLOR=#ff0000]b564ed75-b9ee-410f-9f87-04afc30a0ff4[/COLOR]" TYPE="swap" PARTLABEL="swap" PARTUUID="dc354366-1300-48d4-8a60-133aa2e2ca57"
/dev/sdc10: LABEL="Bionic" UUID="[COLOR=#0000ff]338e6d3b-cbd4-496d-9cc2-b688a90c17c3[/COLOR]" BLOCK_SIZE="4096" TYPE="ext4" PARTLABEL="Bionic" PARTUUID="4f579967-b025-47dc-b080-64a0865d7165"

```

Showing the EFI boot partition just because, the swap is [COLOR=#ff0000]red[/COLOR] and the system partition is [COLOR=#0000ff]blue[/COLOR]. Some systems use the EFI boot partition's UUID, Arch Linux is one of those.
```
menuentry 'Xubuntu 18.04.4 Bionic Beaver LTS' {
    search --no-floppy --fs-uuid --set=root [COLOR=#0000ff]338e6d3b-cbd4-496d-9cc2-b688a90c17c3[/COLOR]
    linux  /vmlinuz root=UUID=[COLOR=#0000ff]338e6d3b-cbd4-496d-9cc2-b688a90c17c3[/COLOR] ro quiet resume=/dev/disk/by-uuid/[COLOR=#ff0000]b564ed75-b9ee-410f-9f87-04afc30a0ff4[/COLOR] splash
    initrd /initrd.img
}
menuentry 'Xubuntu 18.04.4 Bionic Beaver LTS (recovery mode)' {
    search --no-floppy --fs-uuid --set=root [COLOR=#0000ff]338e6d3b-cbd4-496d-9cc2-b688a90c17c3[/COLOR]
    linux  /vmlinuz root=UUID=338e6d3b-cbd4-496d-9cc2-b688a90c17c3 ro recovery nomodeset
    initrd /initrd.img
}

```

---

### Post by oldfred on 2021-02-18
I find path to be one of the issues.
As system is not yet mounted with grub, it is defaults as seen if using live installer, but not if you have booted and mounted using your own mount.

I have a partition (hd0,7) and in that partition I have my data partition. While data partition once booted is /mnt/data, before mount it just has a bunch of folders, one of which is ISO. So grub will see it as (hd0,7)/ISO. If you do a ls of that from grub's c for command line then you should see your ISO & if you create a textfile for grub stanza, you see that file. The file has to have correctly formatted grub boot stanza, just like you have in 40_custom.

So is your data partition the hd0,7?
and is path to ISO this? /Iso/-amd64/ubuntu-mate-18.04.4-desktop-amd64.iso"

---

### Post by Michael Dooley on 2021-02-21
Yes oldfred, my data partition is sda7 (hd0,7). And the path is also correct.

---

### Post by Michael Dooley on 2021-02-22
I'm going to abandon this project at this point as it is taking up way too much of my time. A newer grub was installed in 20.04.2 this morning and I'll work with that rather than 18.04's grub. Thanks to all of you for your assistance and if I ever get a live CD or ISO to mount, I'll report back.

---

### Post by Cavsfan on 2021-03-07
> **Michael Dooley said:**
> I'm going to abandon this project at this point as it is taking up way too much of my time. A newer grub was installed in 20.04.2 this morning and I'll work with that rather than 18.04's grub. Thanks to all of you for your assistance and if I ever get a live CD or ISO to mount, I'll report back.

I know you will get it going, you definitely know what you are doing. If you need additional support, please open up a thread in the Help section. 
I mean no ill will whatsoever, it's just that booting anything live was never included as a part of this Wiki; only booting operating systems.

Thank you kindly. :D

If you ever need help booting operating systems in a custom grub, virtually any Linux OS system, that I can help with, Ubuntu, Arch Linux, Fedora, openSUSE, etc.

---

### Post by brkpoint on 2021-05-05
I'm trying to follow the instructions of [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries_for_UEFI.2FGPT_partitioned_systems](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries_for_UEFI.2FGPT_partitioned_systems), but it says 

> DO NOT CLICK SAVE! Click file, save as and save it as 06_custom and not 40_custom. 
 This way the custom entries will be display at the top which is the goal. 
 
Find where it is saved. If it is saved in /etc/grub.d/ you are good to go.


It's unclear where save as is coming from, is it a grub edit tool? Elsewhere in the wiki only nano is mentioned to edit files and there you don't need to find where the files are saved.

---

### Post by Cavsfan on 2021-05-07
> **brkpoint said:**
> I'm trying to follow the instructions of [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries_for_UEFI.2FGPT_partitioned_systems](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries_for_UEFI.2FGPT_partitioned_systems), but it says

> [COLOR=#000000]*DO NOT CLICK SAVE! Click file, save as and save it as 06_custom and not 40_custom.*[/COLOR]
[COLOR=#000000]*This way the custom entries will be display at the top which is the goal.*[/COLOR]

[COLOR=#000000]*Find where it is saved. If it is saved in /etc/grub.d/ you are good to go.*[/COLOR]


It's unclear where save as is coming from, is it a grub edit tool? Elsewhere in the wiki only nano is mentioned to edit files and there you don't need to find where the files are saved.

The intention is to edit **/etc/grub.d/40_custom** and then save it as **/etc/grub.d/06_custom** so it will show first above all other menu entries.
At one point I made a copy of 40_custom and changed the name to 06_custom.
I always keep an updated 06_custom file in my home directory. I edit it there and move a copy to /etc/grub.d/

This [section]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries_for_Legacy.2FMBR_partitioned_systems") explains about changing the +3 to +4. It is so the 4th line gets executed instead of the 3rd.

This is 40_custom:
```
#!/usr/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```
This is my current 06_custom file on Fedora 34 (distro really doesn't matter) booting Arch Linux, Fedora 34, 3 Xubuntu versions and Windows 10: 
```
#!/bin/sh
echo 1>&2 "Adding Arch Linux, Fedora 34 (Thirty Four), Xubuntu 18.04 LTS Bionic Beaver, Xubuntu 20.04 LTS Focal Fossa, Xubuntu 21.04 Hirsute Hippo and Windows 10"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Arch Linux' {
        search --no-floppy --fs-uuid --set=root 688D-126B
        linux  /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw loglevel=3 quiet
        initrd /intel-ucode.img /initramfs-linux.img
}
menuentry 'Arch Linux (fallback kernel)' {
        search --no-floppy --fs-uuid --set=root 688D-126B
        linux  /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw loglevel=3 quiet
        initrd /initramfs-linux-fallback.img
}
menuentry 'Fedora 34 (Thirty Four)' {
        search --no-floppy --fs-uuid --set=root db5887a8-9c9f-4c06-9bd5-f4c123ff7839
        linux  /boot/vmlinuz root=UUID=db5887a8-9c9f-4c06-9bd5-f4c123ff7839 ro rd.driver.blacklist=nouveau modprobe.blacklist=nouveau nvidia-drm.modeset=1 resume=UUID=b564ed75-b9ee-410f-9f87-04afc30a0ff4 rhgb quiet LANG=en_US.UTF-8
        initrd /boot/initrd.img
}
menuentry 'Xubuntu 18.04 LTS Bionic Beaver' {
        search --no-floppy --fs-uuid --set=root 338e6d3b-cbd4-496d-9cc2-b688a90c17c3
        linux  /vmlinuz root=UUID=338e6d3b-cbd4-496d-9cc2-b688a90c17c3 ro quiet resume=/dev/disk/by-uuid/b564ed75-b9ee-410f-9f87-04afc30a0ff4 splash
        initrd /initrd.img
}
menuentry 'Xubuntu 18.04 LTS Bionic Beaver (recovery mode)' {
        search --no-floppy --fs-uuid --set=root 338e6d3b-cbd4-496d-9cc2-b688a90c17c3
        linux  /vmlinuz root=UUID=338e6d3b-cbd4-496d-9cc2-b688a90c17c3 ro recovery nomodeset
        initrd /initrd.img
}
menuentry 'Xubuntu 20.04 LTS Focal Fossa' {
        search --no-floppy --fs-uuid --set=root b78c207b-9fc9-4230-b3bc-cee5e8e4e288
        linux  /boot/vmlinuz root=UUID=b78c207b-9fc9-4230-b3bc-cee5e8e4e288 ro quiet splash
        initrd /boot/initrd.img
}
menuentry 'Xubuntu 20.04 LTS Focal Fossa (recovery mode)' {
        search --no-floppy --fs-uuid --set=root b78c207b-9fc9-4230-b3bc-cee5e8e4e288
        linux  /boot/vmlinuz root=UUID=b78c207b-9fc9-4230-b3bc-cee5e8e4e288 ro recovery nomodeset
        initrd /boot/initrd.img
}
menuentry 'Xubuntu 21.04 Hirsute Hippo' {
        search --no-floppy --fs-uuid --set=root ea44cecd-5fe4-46ba-9914-bcddba6b34d1
        linux  /boot/vmlinuz root=UUID=ea44cecd-5fe4-46ba-9914-bcddba6b34d1 ro quiet splash
        initrd /boot/initrd.img
}
menuentry 'Xubuntu 21.04 Hirsute Hippo (recovery mode)' {
        search --no-floppy --fs-uuid --set=root ea44cecd-5fe4-46ba-9914-bcddba6b34d1
        linux  /boot/vmlinuz root=UUID=ea44cecd-5fe4-46ba-9914-bcddba6b34d1 ro recovery nomodeset
        initrd /boot/initrd.img
}
menuentry 'Windows 10' {
        set root='hd2,gpt1'
        search --no-floppy --fs-uuid --set=root 688D-126B
        chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

```

I did find out that this **_must_** be in **/etc/default/grub **on any system or else your custom menu will not show:
```
GRUB_TIMEOUT_STYLE=menu
```

---

### Post by von Stalhein on 2021-09-08
I can't for the life of me remember how I got to my last (and preferred) setup - I've gone over the wiki etc & fiddled but no result.

I had to reload Win & Ubuntu (separate drives) as for the original build last year I installed them under the legacy BIOS and recently shenanigans ensued.

Anyway, all up and going again except for the GRUB screen.

It used to boot to my selected picture with the menu of OSs. When picking Ubuntu the screen then reloaded to the same background image with a login text box sited in the bottom right corner. 

Now, when I select Ubuntu the next screen is (I think) the Plymouth? purple one with the box in the middle.

Would love some pointers on modifying this sequence to have the same image and also how to position the login text box.

---

### Post by Cavsfan on 2021-09-08
> **von Stalhein said:**
> I can't for the life of me remember how I got to my last (and preferred) setup - I've gone over the wiki etc & fiddled but no result.

I had to reload Win & Ubuntu (separate drives) as for the original build last year I installed them under the legacy BIOS and recently shenanigans ensued.

Anyway, all up and going again except for the GRUB screen.

It used to boot to my selected picture with the menu of OSs. When picking Ubuntu the screen then reloaded to the same background image with a login text box sited in the bottom right corner. 

Now, when I select Ubuntu the next screen is (I think) the Plymouth? purple one with the box in the middle.

Would love some pointers on modifying this sequence to have the same image and also how to position the login text box.

You say you have a Legacy/MBR system or UEFI/GPT system?

After the BIOS screen it should go to the custom grub screen, then to whichever OS is selected. Could be grub files left executable maybe?

Once customized and certain all custom menu selections work, you make these (files shown in white) unexecutable.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289154&stc=1[/IMG]

---

### Post by von Stalhein on 2021-09-08
It's now a UEFI/GPT system after much pain to the management.

Selecting an OS works fine.

If I select Win, the little wheel thingy rotates in a sort of cutout box in the middle of the GRUB screen for a few seconds before the Win login screen appears.

If I select Ubuntu, it drops to a purple screen headed "Ubuntu" with my account name and a password box underneath - there are also the usual options to select a desktop environment or restart etc.

The previous setup was similar except instead of the purple screen, the next screen contained my background image with a text box in the bottom right corner for the pword.

Hop e that makes sense!

---

### Post by Cavsfan on 2021-09-12
> **von Stalhein said:**
> It's now a UEFI/GPT system after much pain to the management.

Selecting an OS works fine.

If I select Win, the little wheel thingy rotates in a sort of cutout box in the middle of the GRUB screen for a few seconds before the Win login screen appears.

If I select Ubuntu, it drops to a purple screen headed "Ubuntu" with my account name and a password box underneath - there are also the usual options to select a desktop environment or restart etc.

The previous setup was similar except instead of the purple screen, the next screen contained my background image with a text box in the bottom right corner for the pword.

Hope that makes sense!

My Windows logon looks pretty much the same, I have a wheel thing that rotates while Windows 10 is coming up.

Also, I believe your purple screen is your Plymouth logon screen on Ubuntu; I have the same except it's not purple. You've reached the system you selected at that point.

Here is a bit a bout Plymouth **[here]("https://wiki.ubuntu.com/Plymouth")**

I hope this is what you meant.

---

### Post by von Stalhein on 2021-09-14
Thanks!

Yep - I remember the Plymouth one as being coloured purple from I don't know how many distros ago so it didn't worry me as it was familiar.

As I said above, in my last setup, the next screen after selecting Ubuntu had the same background as the initial GRUB screen, with the login box at the bottom RHS of the screen & the usual symbol to select whatever other desktops I had installed etc.

My uncertain memory is that I found a tute that detailed how to do that - I will do some search-engineing and report back.

---

### Post by Cavsfan on 2021-09-14
> **von Stalhein said:**
> Thanks!

Yep - I remember the Plymouth one as being coloured purple from I don't know how many distros ago so it didn't worry me as it was familiar.

As I said above, in my last setup, the next screen after selecting Ubuntu had the same background as the initial GRUB screen, with the login box at the bottom RHS of the screen & the usual symbol to select whatever other desktops I had installed etc.

My uncertain memory is that I found a tute that detailed how to do that - I will do some search-engineering and report back.

You're welcome! Yeah I do a lot of research as well. :)

I've had my grub screen, logon screen and background all the same before too.

Let me know what you find and If I can help I will.

---

### Post by Cavsfan on 2022-05-19
Nothing changed with Ubuntu 22.04.

[[img]http://i.imgur.com/9CNu8t8l.jpg[/img]](https://imgur.com/9CNu8t8)

My custom menu file:
```
#!/bin/sh
echo 1>&2 "Adding Arch Linux, Fedora 35 (Thirty Five), Xubuntu 22.04 Jammy Jellyfish LTS and Windows 10"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Arch Linux' {
    search --no-floppy --fs-uuid --set=root 688D-126B
    linux  /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw loglevel=3 quiet
    initrd /intel-ucode.img /initramfs-linux.img
}
menuentry 'Arch Linux (fallback kernel)' {
    search --no-floppy --fs-uuid --set=root 688D-126B
    linux  /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw loglevel=3 quiet
    initrd /initramfs-linux-fallback.img
}
menuentry 'Fedora 35 (Thirty Five)' {
    search --no-floppy --fs-uuid --set=root 88b17257-fd5e-4261-96d6-fc6cef32254f
    linux  /boot/vmlinuz root=UUID=88b17257-fd5e-4261-96d6-fc6cef32254f ro rd.driver.blacklist=nouveau modprobe.blacklist=nouveau nvidia-drm.modeset=1 resume=UUID=b564ed75-b9ee-410f-9f87-04afc30a0ff4 rhgb quiet LANG=en_US.UTF-8
    initrd /boot/initrd.img
}
menuentry 'Xubuntu 22.04 Jammy Jellyfish LTS' {
    search --no-floppy --fs-uuid --set=root 7905894e-6202-4adb-bdf5-a43aaa82af6b
    linux    /boot/vmlinuz root=UUID=7905894e-6202-4adb-bdf5-a43aaa82af6b ro quiet splash
    initrd    /boot/initrd.img
}
menuentry 'Xubuntu 22.04 Jammy Jellyfish LTS (recovery mode)' {
        search --no-floppy --fs-uuid --set=root 7905894e-6202-4adb-bdf5-a43aaa82af6b
        linux  /boot/vmlinuz root=UUID=7905894e-6202-4adb-bdf5-a43aaa82af6b ro recovery nomodeset
        initrd /boot/initrd.img
}
menuentry 'Windows 10' {
    set root='hd2,gpt1'
    search --no-floppy --fs-uuid --set=root 688D-126B
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
```

---

### Post by Cavsfan on 2022-05-25
I found a more concise way to list the bootable menu lines:
```
grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f2,2 | nl --starting-line-number=0
```

```
cavsfan@Jammy-Jellyfish:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f2,2 | nl --starting-line-number=0
     0    Arch Linux
     1    Arch Linux (fallback kernel)
     2    Fedora 35 (Thirty Five)
     3    Xubuntu 22.04 Jammy Jellyfish LTS
     4    Xubuntu 22.04 Jammy Jellyfish LTS (recovery mode)
     5    Windows 10



```
Just the menu line numbers and what the systems names have been set to.

---

### Post by Cavsfan on 2022-05-25
> **Cavsfan said:**
> I found a more concise way to list the bootable menu lines:
```
grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f2,2 | nl --starting-line-number=0
```

```
cavsfan@Jammy-Jellyfish:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f2,2 | nl --starting-line-number=0
     0    Arch Linux
     1    Arch Linux (fallback kernel)
     2    Fedora 35 (Thirty Five)
     3    Xubuntu 22.04 Jammy Jellyfish LTS
     4    Xubuntu 22.04 Jammy Jellyfish LTS (recovery mode)
     5    Windows 10



```
Just the menu line numbers and what the systems names have been set to.

I take that back; this is another decent way to display to menu lines but, the one in the Wiki is good too.

---

### Post by Cavsfan on 2022-08-27
> **lolitta95 said:**
> great work keep going tanks for the post! :grin:[SIZE=1]
[/SIZE]

Sorry this is a little late.
Thank you! Glad to help. :D

---

### Post by von Stalhein on 2022-09-22
Hey @Cavsfan - send me away if this is the wrong spot!

I had a glitch today & had to re-set Win11.
There was some reordering of disks as I had to boot from a USB to get to the repair area.

I've changed the disk boot order back to the original and I can get into Ubuntu by holding F11 (MSI board & BIOS) and selecting the Ubuntu which then boots to the GRUB menu.
The 2 options at that juncture are Win11 & Ubuntu, and they both reference the same disk, which didn't worry me as ostensibly it is the Win disk and I thought that's where the bootloader resided anyway (UEFI).

So, I thought running the old ```
sudo update-grub
``` would restore things but it doesn't. 

I assume the re-set has overwritten the bootloader - can you link me to a fix please or point me to the Path of Solutions?

---

### Post by oldfred on 2022-09-22
I suggest starting a new thread, and post link to summary report from Boot-Repair.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

New grub 2.06 turns os-prober off by default. You can manually turn it back on temporally and then turn it back off. There is some security issue with trying to mount & scan every partition for operating systems. 

Since this thread is about maintenance free, I would copy Windows UEFI boot stanza into 40_custom. And include 40_custom in you normal backups. I copy mine into /home so backup of /home includes it.

Windows fast start up must be off, otherwise grub will not see it to add to menu, nor then boot it.
Or if UEFI Secure boot is on, grub does not pass security key to Windows so that does not work either.
Windows may turn those settings on with updates or run UEFI update that resets UEFI to defaults. (more with most laptops).

---

### Post by von Stalhein on 2022-09-22
Thanks Oldfred,will do - sorry for the clog.

---

### Post by Cavsfan on 2022-10-20
Yes, thanks Fred! :)

---

