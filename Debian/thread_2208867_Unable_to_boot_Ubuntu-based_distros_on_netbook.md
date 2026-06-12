---
title: "Unable to boot Ubuntu-based distros on netbook"
date: 2014-03-02
forum: Debian
---

### Post by PondPuppy on 2014-03-02
This netbook, ASUS 1015e (dual-core Celeron, not Atom), came with a factory install of Ubuntu 12.04. Runs fine.

I wanted to test a few other distros on the machine. It has an unused 140-gb partition, so that's where they went.

So here's an odd thing: a lot of distros would not boot from a DVD, or only partially booted. Here's a list of the fails:

Elementary
WattOS
Zorin
Linux Lite
Vector Linux

However, I was able to install a couple of other distros without difficulty:

Manjaro
Salix

It strikes me that the fails are all Debian/Ubuntu based distros, and the successful installs are Arch and Slackware based, respectively.

I've read elsewhere that some people have run into difficulties with UEFI on this netbook. When I try 

```
[COLOR=black][FONT=Ubuntu Mono][[/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono]-[/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono]d [/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono]/[/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono]sys[/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono]/[/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono]firmware[/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono]/[/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono]efi [/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono]][/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono]&&[/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono] echo UEFI [/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono]||[/FONT][/COLOR][COLOR=black][FONT=Ubuntu Mono] echo BIOS[/FONT][/COLOR]
```

under the different installed systems, I get:

Ubuntu = UEFI
Manjaro = UEFI
Salix = BIOS

I have Ubuntu 12.04 installed on a desktop machine, and I compared some of the Grub config scripts. There are a few differences in /etc/grub.d/10_linux.

Desktop:

```
 if test -d /sys/firmware/efi && test -e "${linux}.efi.signed"; then    cat << EOF
    linux    ${rel_dirname}/${basename}.efi.signed root=${linux_root_device_thisversion} ro ${args}
EOF
  else
    cat << EOF
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  fi
```

Netbook:

```
cat << EOF    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}

```

It looks like the Grub script on the desktop tests for uefi, and the script on the netbook does not. Same sort of thing happens again farther down the same file:

Desktop: 

```
in_submenu=falsewhile [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  case $linux in
    *.efi.signed)
      # We handle these in linux_entry.
      list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
      continue
      ;;
  esac
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
```

Netbook:

```
in_submenu=falsewhile [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
```

Maybe I'm barking up the wrong tree with the Grub & UEFI stuff. I don't know.

However, my two questions:

1. Why do live-DVD boots fail for so many distros on this netbook?

2. Is this pattern of failure going to bite me when I try to install Trusty after the final release in April?

Thanks for any words of wisdom, and I apologize for the very long and overly detailed first post.

-----------

Edit: Oh, I forgot, I really haven't been using Linux long and don't have any expertise in getting around the OS. Speak veerrrrry slowly and clearly, I'm a newb.

---

### Post by oldfred on 2014-03-02
You may have system set for UEFI boot and then any distribution that has not yet updated for UEFI boot may not work. Or you have gpt partitioning which is for UEFI, but Ubuntu will boot with BIOS or UEFI from gpt partitioning.

How you boot installer is how it installs. And you cannot easily dual boot if one install is UEFI and the other BIOS. UEFI & BIOS are not compatible so once you start booting in one mode you cannot switch or grub cannot boot another install in a different boot mode, only those that are the same.

---

### Post by PondPuppy on 2014-03-02
Thanks, oldfred. 

You wrote, "...[COLOR=#000000]once you start booting in one mode you cannot switch or grub cannot boot another install in a different boot mode..." And that is exactly what I've read elsewhere. So it puzzles me that Salix, the Slackware distro, reports BIOS boot, while Ubuntu and Manjaro report UEFI boot on the same machine. Maybe I misunderstand, or maybe Salix is not reporting the mode correctly.[/COLOR]

As far as disabling uefi on the machine, there's no configuration entry for that in some models of the ASUS 1015e. I've websearched the subject quite a bit, and it's true -- people report the same config options I see, and uefi enable/disable or "legacy boot" are not among them. 

I'm pretty sure that some of the Ubuntu-based distros I tried are just as uefi-enabled as 12.04. For instance, the WattOS 7.5 distro is, I think, based on Ubuntu 13.04. 

So I agree completely that one can either boot UEFI or BIOS, but not both. I believe! And yet, I can boot Ubuntu 12.04 from the HDD and it reports UEFI mode. And I can boot a Slackware distro that *appears* to be in BIOS mode. 

Here's another couple of tests.

I booted Porteus (slackware) from a USB stick. When I enter "[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS" it responds BIOS.

Also, tried booting to Puppy Linux from a USB stick. At the boot menu (not Grub, so is it a menu generated by EFI?) I had a couple of choices (besides the Ubuntu on the hard drive) -- 

1. UEFI: VerbatimStoreNGo
2. VerbatimStoreNGo

If I chose 1, the UEFI option, instead of booting from the USB stick the machine booted to Ubuntu from the HDD. If I chose 2, then the machine booted to Puppy from the USB stick. (And, in fact, when I tested boot mode Puppy reported BIOS boot.)

I'm confused. What do you think?

-------------------------

Oh, wait: [http://askubuntu.com/questions/338894/how-to-disable-the-efi-check-in-13-04-x64](http://askubuntu.com/questions/338894/how-to-disable-the-efi-check-in-13-04-x64)

---

### Post by oldfred on 2014-03-03
You can boot both UEFI and BIOS from the same computer or even hard drive if not Windows. But once drive is for UEFI it must be gpt partitioned. 
Ubuntu will then boot in either UEFI or BIOS from gpt drives and some other distributions should also. But some may not. 
Windows and Ubuntu only boot from MBR(msdos) with BIOS.
Windows only boots from gpt with UEFI.

But grub then cannot control booting. You have to choose what to boot from UEFI/BIOS or one time boot key. Some will let you boot from one time boot key, others may require you to turn on/off UEFI settings or CSM/BIOS/Legacy settings to boot in the other mode. Some then auto switch configuration based on what you are booting. It seems like yours auto switches and does not even have the settings to lock in one mode or the other. You just have to choose device or install with UEFI or BIOS.

If secure boot is on, only those systems configured for UEFI with secure boot will be available to boot.

How you boot install media is how it installs. And Ubuntu has both BIOS and UEFI boot modes on the 64 bit distribution. 
Currently no 32 bit distributions have UEFI. But some have posted they recompiled grub2 and can boot 32 bit in UEFI mode. You can also boot a 32 bit version of Ubuntu on a gpt partitioned UEFI drive. 

I would expect any 64bit distribution using a current version of grub2 to be UEFI (but maybe not secure boot) enabled.

With gpt partitioning you need an efi partition near the beginning of the drive to boot in UEFI mode or a bios_grub flagged unformatted partition anywhere on drive to boot in BIOS mode. You can have both on any drive, but only one of each.

---

### Post by PondPuppy on 2014-03-03
[SIZE=2]Thanks again, oldfred.

You wrote, "It seems like yours auto switches and does not even have the settings to lock in one mode or the other. You just have to choose device or install with UEFI or BIOS." 

I think you nailed it. That's very helpful. I found my way to the Arch wiki entry on UEFI, and then noticed you have it listed in the resources at [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) too. Thanks there as well.

For what it's worth, this netbook is set up the way user Gaussian describes on [http://ubuntuforums.org/showthread.php?t=2176667](http://ubuntuforums.org/showthread.php?t=2176667) . An EFI partition formatted as FAT32, but the Linux partition formatted as ext3, not GPT.

I downloaded the daily build of Trusty and burned it to a DVD. It boots fine on the netbook, so that reassures me that when the LTS is released I'll be able to upgrade. Since I've also got the machine to multi-boot a couple of alternate OSes, and you've helped me get a start on understanding UEFI, I'll mark this thread as solved. 

I appreciate the helpful community.[/SIZE]

---

### Post by oldfred on 2014-03-04
Drives are partitioned with either MBR(msdos) or gpt(GUID). Gpt is not a format. (see post #4)

And then each partition can be formatted. Windows often uses NTFS and Linux ext4, but there are many other formats.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by PondPuppy on 2014-03-04
Read through the references.... much to learn.

---

### Post by newbie2244 on 2014-03-10
Change the boot order in BIOS so that DVD drive is the first place the loader will check for a boot. When you this, you will not be able to boot the existing OS  on your HD. My understanding is that you can't have two Ubuntu Linux distros on the same partition. I tried putting Ubuntu on a separate partition in Windows8 and was not successful.

---

### Post by PondPuppy on 2014-03-10
Interesting note. Some of the distros I mentioned booted 'partially' -- I got a splashscreen and live DVD menu in WattOS, for instance -- but failed to run past the menu. They did run fine on another machine with another Ubuntu distro already on the HDD, though. Have to think about it. Thanks.

---

