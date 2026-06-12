---
title: "Run a script on USB drive insertion"
date: 2006-09-29
forum: Desktop Environments
---

### Post by TrinitronX on 2006-09-29
EDIT: I've found a solution to this and to getting truecrypt to automount a volume with udev.

Run a script: [http://www.ubuntuforums.org/showpost.php?p=1574752&postcount=16](http://www.ubuntuforums.org/showpost.php?p=1574752&postcount=16)
Truecrypt: [http://www.ubuntuforums.org/showpost.php?p=1578267&postcount=22](http://www.ubuntuforums.org/showpost.php?p=1578267&postcount=22)


I've been trying to get udev to run a shell script that I made upon inserting a certain USB key.  This shell script copies some files from my firefox profile to the profiles folder of a portable version of firefox installed on the USB disk.

I have no idea why it won't work.  I have extensively looked at the 'writing udev rules' guide here: [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html) .

Here is my rules file in /etc/udev/rules.d/98-usbkeysync.rules:
```
ACTION=="add", BUS=="usb", SYSFS{manufacturer}=="SanDisk Corporation", SYSFS{product}=="U3 Cruzer Micro", SYSFS{serial}=="0000060434031880", RUN+="/home/trinitronx/applications/startupscripts/synckey.sh"
```

The drive's device has been showing up as /dev/sdc, so I looked up the udevinfo:
```
 udevinfo -a -p /block/sdc

udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

device '/sys/block/sdc' has major:minor 8:32
  looking at class device '/sys/block/sdc':
    KERNEL=="sdc"
    SUBSYSTEM=="block"
    SYSFS{dev}=="8:32"
    SYSFS{range}=="16"
    SYSFS{removable}=="1"
    SYSFS{size}=="4013713"
    SYSFS{stat}=="     313     1095     1562      308        0        0        0        0        0      308      308"

follow the "device"-link to the physical device:
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0/host10/target10:0:0/10:0:0:0':
    BUS=="scsi"
    ID=="10:0:0:0"
    DRIVER=="sd"
    SYSFS{device_blocked}=="0"
    SYSFS{iocounterbits}=="32"
    SYSFS{iodone_cnt}=="0x14f"
    SYSFS{ioerr_cnt}=="0x1"
    SYSFS{iorequest_cnt}=="0x14f"
    SYSFS{max_sectors}=="240"
    SYSFS{model}=="U3 Cruzer Micro "
    SYSFS{queue_depth}=="1"
    SYSFS{queue_type}=="none"
    SYSFS{rev}=="2.18"
    SYSFS{scsi_level}=="3"
    SYSFS{state}=="running"
    SYSFS{timeout}=="30"
    SYSFS{type}=="0"
    SYSFS{vendor}=="SanDisk "

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0/host10/target10:0:0':
    BUS==""
    ID=="target10:0:0"
    DRIVER=="unknown"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0/host10':
    BUS==""
    ID=="host10"
    DRIVER=="unknown"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0':
    BUS=="usb"
    ID=="5-7:1.0"
    DRIVER=="usb-storage"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceClass}=="08"
    SYSFS{bInterfaceNumber}=="00"
    SYSFS{bInterfaceProtocol}=="50"
    SYSFS{bInterfaceSubClass}=="06"
    SYSFS{bNumEndpoints}=="02"
    SYSFS{modalias}=="usb:v0781p5406d0010dc00dsc00dp00ic08isc06ip50"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.7/usb5/5-7':
    [color=green]BUS=="usb"[/color]
    ID=="5-7"
    DRIVER=="usb"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bMaxPower}=="200mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0010"
    SYSFS{bmAttributes}=="80"
    SYSFS{configuration}==""
    SYSFS{devnum}=="12"
    SYSFS{idProduct}=="5406"
    SYSFS{idVendor}=="0781"
    [color=green]SYSFS{manufacturer}=="SanDisk Corporation"[/color]
    SYSFS{maxchild}=="0"
    [color=green]SYSFS{product}=="U3 Cruzer Micro"[/color]
    [color=green]SYSFS{serial}=="0000060434031880"[/color]
    SYSFS{speed}=="480"
    SYSFS{version}==" 2.00"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.7/usb5':
    BUS=="usb"
    ID=="usb5"
    DRIVER=="usb"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bDeviceProtocol}=="01"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0206"
    SYSFS{bmAttributes}=="c0"
    SYSFS{configuration}==""
    SYSFS{devnum}=="1"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{manufacturer}=="Linux 2.6.15-27-686 ehci_hcd"
    SYSFS{maxchild}=="8"
    SYSFS{product}=="EHCI Host Controller"
    SYSFS{serial}=="0000:00:1d.7"
    SYSFS{speed}=="480"
    SYSFS{version}==" 2.00"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.7':
    BUS=="pci"
    ID=="0000:00:1d.7"
    DRIVER=="ehci_hcd"
    SYSFS{class}=="0x0c0320"
    SYSFS{device}=="0x24dd"
    SYSFS{irq}=="193"
    SYSFS{local_cpus}=="ff"
    SYSFS{modalias}=="pci:v00008086d000024DDsv00001028sd00000172bc0Csc03i20"
    SYSFS{subsystem_device}=="0x0172"
    SYSFS{subsystem_vendor}=="0x1028"
    SYSFS{vendor}=="0x8086"

  looking at the device chain at '/sys/devices/pci0000:00':
    BUS==""
    ID=="pci0000:00"
    DRIVER=="unknown"
```

As far as I can tell, those rules should match the USB disk, and run my shell script.  They're all under the same device chain header, so that can't be the problem.  I have even attempted using a simple rule of: ```
BUS=="usb",  SYSFS{manufacturer}=="SanDisk Corporation"
```

I peeked into the udev events that trigger when I plug in the key, and here's what udevmonitor shows:
```
UEVENT[1159584460.678608] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-7
UEVENT[1159584460.678722] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0
UEVENT[1159584460.678782] add@/class/scsi_host/host10
UEVENT[1159584460.678838] add@/class/usb_device/usbdev5.12
UDEV  [1159584460.697129] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-7
UDEV  [1159584460.747792] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0
UDEV  [1159584460.776126] add@/class/scsi_host/host10
UDEV  [1159584460.803855] add@/class/usb_device/usbdev5.12
UEVENT[1159584465.678028] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0/host10/target10:0:0/10:0:0:0
UEVENT[1159584465.679814] add@/block/sdc
UEVENT[1159584465.687022] add@/block/sdc/sdc1
UEVENT[1159584465.687046] add@/class/scsi_device/10:0:0:0
UEVENT[1159584465.687062] add@/class/scsi_generic/sg2
UDEV  [1159584465.713936] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-7/5-7:1.0/host10/target10:0:0/10:0:0:0
UDEV  [1159584465.804403] add@/class/scsi_generic/sg2
UDEV  [1159584465.807978] add@/class/scsi_device/10:0:0:0
UDEV  [1159584465.822576] add@/block/sdc
UDEV  [1159584465.899346] add@/block/sdc/sdc1
UEVENT[1159584466.003490] mount@/block/sdc/sdc1

```

After plugging it in, I test whether or not the script ran by looking into the drive to see if the files were copied, and each time nothing has happened.

Anyone know how to get this to work?

---

### Post by TrinitronX on 2006-09-30
I've confirmed that the keys are matching my drive by changing the rules file to be:
```
ACTION=="add", KERNEL=="sd?1", BUS=="usb", SYSFS{manufacturer}=="SanDisk Corporation", SYSFS{product}=="U3 Cruzer Micro", SYSFS{serial}=="0000060434031880", NAME="%k", SYMLINK+="usb/cruzer", RUN+="/home/trinitronx/applications/startupscripts/synckey.sh"

```

I also ended up changing the name of the file to be 10-usbkeysync.rules so it would be read before all the rest in /etc/udev/rules.d

Now whenever I insert the drive, I can see that udev creates a /dev/usb/cruzer device, and when ejecting it, it goes away again.

But why does the script not execute?  Or does it actually do so, but I can't see that it failed?  Does udev work with shell scripts, or must the run command be a binary?  Can file IO be performed at this stage, or does this all happen before it is mounted?

---

### Post by TiredBird on 2006-10-01
I too have encountered a similar problem and have never been able to get it to work. I can get it to assign the name okay and am using that regularly, but can't get the 'run' part to work. Like you, I read the documentation but there are no examples of using 'run'. I think maybe the developer doesn't understand it either. If you get it figured out please let me know and I'll do the same. Good luck.

---

### Post by TiredBird on 2006-10-01
By the way, your rule seems to be unnecesarily complex. I have several thumbdrives, an external usb drive and several usb peripherals. The only thing I use is the serial number.

I might also add that it appears there are very few people who even know this capability exists, much less how to exploit it. I see an awful lot of posts from some very knowledgeable and experienced people who are still talking about device names being different when they change the sequence of plugging something in.

---

### Post by TiredBird on 2006-10-01
I spent a lot of time trying to solve this problem a couple of weeks ago but I got sidetracked by something else and never finished.

However, I remember something from my testing. See if this helps at all.

There may be a timing issue involved here. I was getting some indications from the script output that the script wasn't finding the device as I was naming it in the same rule. When I got sidetracked, I was thinking that the 'run' command needed to be on the next line so that the name assignment was already completed before the script began. 

In the example the developer used he had the 'run' command as a stand-alone. The name had been previously assigned by a rule he didn't show in the example. What I was thinking about doing was putting my 'run' commands further down the priority line. (I put my rules in a 10-local or something like that. I was going to put the run commands in something like 85-local to make sure it ran after the name had been assigned.

Why don't you try something like that and see what happens. Never can tell, it might work.

---

### Post by TrinitronX on 2006-10-01
I think I'll definately try that tomorrow.  I'll also see if I can force my script to output messages to a logfile to analyze what's going on.  I know the rule is executing the symlink directive, but still am not sure if the run one is being executed in the same command.
Perhaps this is why the examples only had RUN on it's own line.

The reason for my overly selective rule is because I am copying some other sensitive data to the drive along with my firefox profile, and want to make sure that the script will authenticate that it's my drive before copying it over.  It's probably enough to just use serial number, but I like to make sure :P.

I'm also looking into other alternatives, seeing what hotplug and hal do, and how exactly Ubuntu is mounting the drive since it doesn't seem to be using usbmount (although a 'usbmount' package exists in synaptic, it's just not installed on my system).  Is gnome itself responsible for listening to the hal info and then automounting any usb storage devices it finds?

It's definately an interesting subject, and I'd like to get to the bottom of this.  If I figure anything out, I'll be sure to post what I did to get it working.

---

### Post by TiredBird on 2006-10-01
I certainly understand the sensitivity issue as I have something like five encrypted containers, several of them on USB storage devices. I guess you can't be too careful. Maybe I need to beef up my own selection criteria.

The script I'm trying to run unlocks the encryption on a USB storage device, (thumb drive or external drive - I have both) if certain conditions are met. I know the script works because I use it as a command. But I was'nt able, at least not so far, to get udev to execute it when I plug the drive in. It would be nice if I could do that. 

As you may have noted from the documentation, udev puts a number of automatic entries in /dev without us having to write any rules. I discovered this before I knew anything about udev and was already using it along with fstab to consistently get my USB drives mounted in the same place. 

The only thing I have gained so far by writing rules is that my devices now have more recognizable names. (If you haven't already done so, look in the /dev/disks subdirectories after you've plugged in a couple of USB devices. They'll all be there, probably using the serial number as a unique file name.) 

Anyway, you've got me interested again and I'm going to try some experiments myself later today. I'll post what I learn.

---

### Post by TiredBird on 2006-10-01
I think I just found an important piece of information in the documentation that suggests we may be on the right track:

"Do not confuse this with the PROGRAM functionality described above. PROGRAM is used for running programs which produce device names (and they shouldn't do anything other than that). *_When those programs are being executed, the device node has not yet been created_*, so acting upon the device in any way is not possible." (Emphasis added.)

I'm going to do some experimenting and post again later.

---

### Post by TiredBird on 2006-10-02
I have just spent 11 hours working on this problem. I'm still not fully satisfied with the results but I think I have some answers.

To answer one that you asked early on, yes, it does work with scripts. 

But my theory about why neither of us could get RUN to work was wrong. It was not a matter of trying to run something on a volume that hadn't been mounted.

The drive of course does have to be mounted. You didn't post your script so I couldn't see what provisions you've made for that but based on what I've learned I would suspect that your problem is in the mounting or in the path to the script and/or paths to commands used in the script. It might also be in your permissions.

Following is what I did:

(1) I am using a Gnome desktop on the machine I used for testing. I had it set to automatically mount USB drives. I turned off the automatic mounting. I wasn't able to get anywhere as long as I allowed the system to automatically mount removable storage devices.

(2) /etc/udev/rules.d/10-local.rules contains the following:

```
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", SYMLINK+="usb/*thumbdrive*"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", RUN+="/home/*username*/bin/*scriptname*"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", OPTIONS+="last_rule"
```

[INDENT]Notes on the above: 

(a) I didn't change the device name. I let it keep the system assigned name. However, I did test it with other devices mounted at random times so that sometimes my thumb-drive was called 'sda1' and sometimes it was called 'sda2'.

(b) The SYMLINK statement was used to assign a persistent name that I could use for mounting. 

(c) I fully qualified the path to the script. It seems that udev doesn't pay any attention to environment variables.

(d) I added the last rule to keep udev from assigning another name as a result of other .rules files.
[/INDENT]
(3) /etc/fstab included the following line:

```
/dev/usb/*thumbdrive* /home/*username*/*thumbdrive* vfat user,rw,suid,dev,exec,auto,utf8,umask=000,uid=1000,gid=1000 0 0
```

[INDENT](I probably went overboard with my options there but it works.)[/INDENT]

(4) The script is as follows:

```
#! /bin/bash
/bin/mount /dev/usb/thumbdrive
{other commands with fully qualified paths}
```

[INDENT](Again please note that the **paths are spelled out in full**. I was not able to get this to work without the full pathnames although the script worked fine when I ran it from the command line.)[/INDENT]

Actually a lot of my time was spent trying to get udev to run TrueCrypt. I was never able to do that. It either requires root privileges or the setuid bit. Although it would run fine from the command line as an addition to the script, (either with sudo and no setuid or with setuid and no sudo), I could not get it to run in any form when the script was being executed by udev.

Permissions could also be a problem for you. If your permissions aren't set correctly, copying files to or from your thumbdrive could require root capability and udev will not run anything requiring root privileges, or at least it wouldn't for me.

Tell me what you find out. 

In particular, I'm still looking for a way to get TrueCrypt to run under udev.

And please forgive the ignorance which undoubtedly shows above. I've only got a few months with Linux.

---

### Post by TiredBird on 2006-10-02
I just went through the posts in this thread again and I see that what you're copying is your Firefox profile. That's one of the reasons I use a thumbdrive. It has a portable Windows version of Firefox and my profile. I plug it into any machine I want when I want to run Firefox. If its a Windows machine, (and I don't care where it is or whose it is), I run firefox from the thumbdrive. 

On a Linux machine, I run the version of Firefox that's installed there but I have it using the profile from my thumbdrive. That way I never have to copy the profile and because my profile is on my thumbdrive I don't have to worry about anyone starting up one of my machines and checking out my surfing habits or glomming onto my passwords. 

And the reason for all this business with TrueCrypt is that the profile folder is in an encrypted portion of my thumbdrive.

---

### Post by TrinitronX on 2006-10-02
Well, it seems you've figured some things out before I even had time to take a deeper look at it :p .

From what I understand, the PROGRAM command and RUN commands are indeed different, so what we'd need to use is the RUN one, correct?

I'm not at my home PC at the moment, so I can't post my script yet, but here's the basics of what it's doing:
[LIST]
[*]The script resides in my home directory on the PC's local hard drive, as to avoid file permission problems.  My RUN command is the full path to the script in my homedir.[/LIST]
[LIST=1]
[*]When the script is run, first it takes a variable that is defined in the script, which is a 'URI' for my device.  The uri is a unique identifier for the type of device, and it shows up when I issue the `lshal` command.
[*]Using hal-get-property along with this URI, I query the block.device property of my USB drive to find it's current /dev/sd?? device name. I could also use this to get my serial number in the future for validation; or alternatively, put an encrypted file or signed file on the key, then verify the contents or signature with gpg.
[*]After finding this, I then grep /etc/mtab for the block device entry found previously to get the current mount point of my drive.
[*]Then it finally copies the files over to their predetermined directories on the drive.
[/LIST]
[LIST]
[*]If any point in this process fails, the script will stop and output an error message to stderr (although when it's run by udev, I'm not sure how to look at the output :P )
[*]I don't explicitly mount the drive in the script, I assumed that Ubuntu's magic automount program would take care of that (whatever it actually is).  I didn't think I had to mess with that part, since ubuntu seems to do a good job of it.
[/LIST]

However, now I'm thinking this may be the problem, since udev is supposed to run before mounting the device (a /dev/ entry has to exist before mounting of course :P ).  So, maybe if I force the script to output to a logfile in my homedir, then I'll see that it's not finding the entry in mtab since it probably shoudn't be mounted when udev is running.

The script of course works normally when I run from the command line after the drive is already mounted.  So I'll probably end up either mounting the drive in the script, or putting the fstab entry in assuming that ubuntu will take care of mounting as soon as it sees the symlink created by udev pop up.  I'm thinking that doing it through fstab is more secure, since the file is only root writable, but there may be a sort of 'race condition' between my script run by udev, and ubuntu's automounting of the drive from fstab.  So if ubuntu is too slow in mounting, since the script is supposedly run directly after or right when the device symlink is created, then the script will fail.

I've got some more time tonight that I can use to work on it, and I'll post my script as well.

---

### Post by TiredBird on 2006-10-02
I guess that knowing very little about Linux, (my first exposure to Linux was a few months ago), is a blessing in disguise. I don't understand most of what you are doing and the whole thing seems to be way too complex for what I understand you are trying to do.

Let me make sure I understand the objective. 

You have some sensitive data on both your computer and the thumb drive. You want to sync those two, or at least exchange some of that data between the two of them. You want to be sure you are exchanging with the proper one and not a substitute.

Have I got that much right? or close anyway?

I am going to assume further that you are NOT worried about someone cloning your memory stick but that you will be satisfied it is the right one if you get a match on serial number and/or some of other identifiers placed on it by the manufacturer.

Unless I'm missing something someplace, if the foregoing is reasonably correct it would appear that you are doing a lot of unneccesary stuff and making it more difficult to make it work.

I thought that's what udev was for. Until you mentioned it I had never even heard of 'lshal'. I ran it to see what it did and got more data than I could ever imagine to wade through. And that probing you were talking about to get the proper name and mount point of the device - udev does all of that for you - at least I think it does.

Since I'm just a dummy I'd have to do something like this:

(1) udev scans the rules files every time the kernel gives it an event. You already know the serial number and you know that the system's going to assign it a name like sda1, sdb1, sdc1, etc. So your rules are to look at 'add' only, match the serial number and a kernel name that looks like 'sd?1'. 

(That last match is important because the serial number and other stuff you commonly check is also in the sys block for the total device, which you don't want to mount. You want to mount the partition.) 

(2) Okay, so you've got it matched. Forget about the name. Leave what ever the system assigned to it, sda1, sdb1, sdc1, whatever. The symlink you add is the important thing. You've already uniquely identified the device, now give it a unique symlink. Then use the symlink in your fstab because the symlink's never going to change. 

Example: you call the symlink 'usb/thumbdrive'. Now you've got a device that answers to the name of /dev/usb/thumbdrive. Put that in your fstab with a mount at the place you want it to be mounted. You might even put the  mount point in your home directory and call it thumbdrive.

If you used 'auto' on the fstab line you can start up your system without the thumbdrive plugged in and it won't give any errors. Eliminate that auto mounting, (if you eliminate the desktop you won't have it anyway).

(3) So your system's running and you plug in the thumbdrive. Udev looks at your rules and finds a match. It then assigns the symlink. Now it can be mounted. Your second rule matches the same things as the first one but instead of creating the symlink, this one runs a script that uses the symlink.

(4) First step in the script is to mount the device name assigned by the symlink, (/dev/ plus whatever you assigned), and mount that on the spot you set up in fstab, eg: /bin/mount /dev/usb/thumbdrive. You've already defined the rest of it in fstab so that's all you need.

One line in the script to get it mounted. Then the other lines deal with actually exchanging the data between your computer and the flashdrive. (I use 'unison' for true synchonization and 'rsync' otherwise.)

My earlier post, showing the contents of my files, is probably what you need. Just add your file transfer commands after the mount command and it should work. Except for the fact that my thumbdrive is encrypted, it appears that we are trying to do the same thing, just going about it different ways. 

Or am I misunderstanding something...

---

### Post by TrinitronX on 2006-10-02
Ok, here's the script I wrote:
```
#!/bin/bash
USB_udi="/org/freedesktop/Hal/devices/storage_serial_<BRAND>_<SERIAL #>
#USBDEVICE=`lshal --long --show $USB_udi | grep block.device | awk '{print $3}' | tr --delete [=\'=]`  # grab the USB key's block device path in /dev from lshal using it's udi, then format with awk & tr
USBDEVICE=`hal-get-property --udi $USB_udi --key block.device 2>/dev/null`  #simpler method of getting the block device from hal (discard errors so we can assume a NULL output means no target device plugged in)
USBPATH=`cat /etc/mtab | grep $USBDEVICE | awk '{print $2}' 2>/dev/null`  # find the device in mtab and grab the cooresponding mount point
PROFILEPATH=/FirefoxPortable/Data/profile/
GPGPATH=/ThunderbirdPortable/Data/gpg/
EXITSTATUS=0 #initialize our exitstatus to success
if [ -n "$USBDEVICE" ]
then
    if [ -n "$USBPATH" ]
    then
        PROFILEPATH=${USBPATH}$PROFILEPATH
        GPGPATH=${USBPATH}$GPGPATH
        if [ -d "$PROFILEPATH" ]
        then
            if cp ~/.mozilla/firefox/<profile ID>.default/bookmarks.html $PROFILEPATH
            then
                echo "Successfully copied bookmarks.html to $PROFILEPATH"
            else
                echo "Failed to copy bookmarks.html to $PROFILEPATH" >&2
                (( EXITSTATUS++ ))
            fi
        else
            echo "$PROFILEPATH does not exist" >&2
            (( EXITSTATUS++ ))
        fi
        if [ -d "$GPGPATH" ]
        then
            if cp ~/.gnupg/*.gpg $GPGPATH
            then
                echo "Successfully copied gpg files to $GPGPATH"
            else
                echo "Failed to copy gpg files to $GPGPATH" >&2
                (( EXITSTATUS++ ))
            fi
        else
            echo "$GPGPATH does not exist" >&2
            (( EXITSTATUS++ ))
        fi
    else
        echo 'No disk at /dev/sdc1 found in mtab' >&2
        (( EXITSTATUS++ ))
    fi
else
    echo "Could not find udi: $USB_udi in lshal" >&2
fi

if [ "$EXITSTATUS" -gt 0 ]
then #there were errors
    echo "$EXITSTATUS errors encountered" >&2
    EXITSTATUS=1
fi
exit $EXITSTATUS

```

I'm not actually copying my entire profile anymore, I realized all I wanted was to keep my bookmarks updated since I rarely change anything else in my profile, and that on the portable version of firefox, I wanted to keep the 'clear private data tool' on all the time.  Copying my entire profile kept overwriting this setting :p .

I realize that the whole UDI identification procedure is now unnecessary, but I wrote the script before I even considered making it autorun when I add the drive, and before I even knew about udev ;) .  Because I'm lazy (that's why we all use shell scripts anyway right?), I just left it this way since it still performs its task.

Anyway, we are indeed trying to do the same thing, and I think you've got the most efficient method down :D .  It makes much more sense to keep everything on the thumb drive encrypted and then have your PC use the remote profile.  I'd love to do it this way, but there was a problem that prevented me from doing it at the moment.  I attempted to install the Ubuntu .debs of truecrypt last week, and recieved some 'kernel module failed to load' errors.  I also attempted installing from source but got the same exact error.  It may just not like the 686 kernel at the moment, or maybe it was configured with some wrong options.  Cross platform encryption is a must if I were to use this method.  I hope they somehow fix the kernel or truecrypt so they can work together.

I'm going to try what you suggest, with two separate rules to create the symlink and then run the script.  In your fstab you tell it to auto mount on boot, also specifying the userid and groupid so your user can work with the drive, as well as user so any user can mount it.  You also disabled automounting from gnome too?  Did it not work without doing this?
You then mount the drive using the options found in the fstab by simply issuing `/bin/mount /dev/usb/thumbdrive`.

I'm wondering what user the script is actually running under as well, since doing `ps -lA | grep 'udev\|PPID'` shows that it has a UID of 0 (root).  I also wonder if because of this that it is not running the script as root for security reasons, however /etc/udev/rules.d is only writeable by root anyway, so noone could add a RUN command to a .rules file.

One last thing, when you installed truecrypt, did you select the option to allow non root users to run it?  Are you using the 386 kernel?

---

### Post by TrinitronX on 2006-10-03
Ok, the logfile idea is working and I have verified that the script is executing everything as root by adding a call to `whoami` at the very beginning of the script.
I also added some code to confirm that the usb key was not mounted at the time the script was run:
```
whoami  >> /home/<username>/Desktop/logfile.txt
echo "mtab is:" >> /home/<username>/Desktop/logfile.txt
cat /etc/mtab >> /home/<username>/Desktop/logfile.txt
echo "mount -l is:" >> /home/<username>/Desktop/logfile.txt
mount -l >> /home/<username>/Desktop/logfile.txt
```

the output was:
```
root
mtab is:
/dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-686/volatile tmpfs rw 0 0
/dev/sda2 /media/sda2 ntfs rw,noexec,nosuid,nodev,uid=1000,nls=utf8,umask=0222 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
mount -l is:
/dev/sdb1 on / type ext3 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-686/volatile type tmpfs (rw)
/dev/sda2 on /media/sda2 type ntfs (rw,noexec,nosuid,nodev,uid=1000,nls=utf8,umask=0222)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
No disk at /dev/sdc found in mtab
1 errors encountered

```

Directly after plugging in my usb key, I ran `mount -l` again and saw that my usb key was mounted:
```
/dev/sdc1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8) 
```

I also had `udevmonitor` running in an open console window to directly look at the udev events that were happening, and here's what I got:
```
UEVENT[1159846626.521599] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-8
UEVENT[1159846626.522228] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8:1.0
UEVENT[1159846626.522309] add@/class/scsi_host/host7
UEVENT[1159846626.522377] add@/class/usb_device/usbdev5.9
UDEV  [1159846626.543185] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-8
UDEV  [1159846626.583556] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8:1.0
UDEV  [1159846626.640962] add@/class/scsi_host/host7
UDEV  [1159846626.642469] add@/class/usb_device/usbdev5.9
UEVENT[1159846631.520123] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8:1.0/host7/target7:0:0/7:0:0:0
UEVENT[1159846631.521816] add@/block/sdc
UEVENT[1159846631.528671] add@/block/sdc/sdc1
UEVENT[1159846631.528860] add@/class/scsi_device/7:0:0:0
UEVENT[1159846631.528937] add@/class/scsi_generic/sg2
UDEV  [1159846631.546010] add@/devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8:1.0/host7/target7:0:0/7:0:0:0
UDEV  [1159846631.612448] add@/block/sdc
UDEV  [1159846631.619857] add@/class/scsi_generic/sg2
UDEV  [1159846631.660547] add@/class/scsi_device/7:0:0:0
[color=red]UDEV  [1159846631.732210] add@/block/sdc/sdc1[/color]
UEVENT[1159846631.841953] mount@/block/sdc/sdc1

```

I saw the logfile pop up almost simultaneously with the hilighted line, or maybe directly afterward.  The unix timestamp "1159846631.732210" translates to "Mon 02 Oct 2006 21:37:11.732210 (GMT -6)". My logfile's modified date is "Mon 02 Oct 2006 21:37:11 (GMT -6)".  Since the logfile's timestamp is not as precise as the ones given in the udevmonitor report, I decided to add a `sleep 5` command to my script to estimate around which block of events that the script was being executed.  I have determined that the script and that last 'add' event are being executed fractions of a second away from one another, but just close enough for the 'mount' event to occurr afterwards

---

### Post by TiredBird on 2006-10-03
TrinitronX,

I am clearing most everything from my profile on each log-off. However, I am keeping 3 days worth of history and about 20 cookies. Everything else goes though. Different strokes for different folks.

I too started on this project before I had ever heard of udev. I saw my USB stuff get automatically mounted in /media and figured there had to be a /dev entry some place. I discovered the ones udev had created, (still had never heard of udev), and saw they were creating a symlink with the DOS name I had given the device on XP. So I used that name in my fstab and with automount turned on, my devices always went to the same place no matter what order I mounted them in.

Then I heard about udev and wanted to make all this stuff happen automatically. Well, I still haven't gotten TrueCrypt to working with it yet but I have learned a lot about udev.

One of the machines I run on should be using a '686' kernal and one of them should be using a 'k7' type. But the live/install disk for Dapper put '386' kernels on both machines and it ran fine. The deb downloaded from TrueCrypt worked with the '386' kernel without recompiling. I did some experimenting however and got the same message you did when I installed the '686' and 'k7' kernels. But it has worked fine through 3 versions of the 386 kernel.

The uid and gid options in my fstab entry provide ownership settings for a fat partition which wouldn't have them otherwise. And the umask of 000 gives every file a 777 I think.

I really don't remember what all those options do but I had a reason for using them when I set this up several months ago. I think 'man mount' describes the options.

Yes, I shut off the auto-mounting features of Gnome. I would strongly recommend you doing the same. By putting the mount into your script and letting udev initiate it, you have more control over the where and when of the mount. Controlling the where and when makes the rest of the scripting a lot easier. 

On the permissions stuff I'm still very confused. I have read some other people's comments about this and have gotten conflicting answers. One seemingly knowlegeable person said that the kernel won't run a script that requires root permission. I guess that's only if it's being run by another program. 

Watch the permissions on the files you're copying. Make sure theiy're set up so that everything you need to do can be done as a non-privileged user. Udev might run as root but I don't think it's going to run a script that requires root permissions.

Also, make sure you spell the paths out completely. I saw in someone else's post that udev doesn't use paths. My experience confirms that. You have to tell it explicitly where to find something. I couldn't even get it to run the 'mount' command until I told it exactly where to find it.

The only way I know of allowing non-root users to run TrueCrypt is by adding the suid bit to the permissions, at least that's what the howto said that I was following when I installed it. So I did that and it works fine for me. It just won't work when I put it in a script that udev is going to execute. I've tried it with and without that bit set. Udev doesn't want to run it no matter what.

I'm not sure what you mean by cross-platform. If you mean runs on XP and Linux, then I agree. I have both and that's the ideal for me. TrueCrypt does run on both. One of my machines is a dual boot with a partition that is shared by both OS's. But the partition is encrypted with TrueCrypt. If I'm on XP I use the Windows version of TrueCrypt to access it and if I'm on Linux I use the Linux version. Actually the Windows version is a lot easier to use. It has a very nice GUI that I hope will appear on Linux sometime soon. 

Well, I'm going to bed now. I'll look at your scripts tomorrow. I don't do much scripting so it's a real treat for me. In the past I wrote a lot of c and c++ code. I understand that one of the shells is very similar to c. Do you by any chance know which one it is and whether or not that shell is in the Ubuntu repositories.

---

### Post by TrinitronX on 2006-10-03
Ok... I finally have everything running pretty much perfectly (according to my own preferences).  Of course feel free to use whatever options suit your situation :D.

Here's what I have:
filename: /etc/udev/rules.d/10-usbkeysync.rules
```
ACTION=="add", KERNEL=="sd?1", BUS=="usb", SYSFS{manufacturer}=="SanDisk Corporation", SYSFS{product}=="U3 Cruzer Micro", SYSFS{serial}=="0000060434031880", NAME="%k", SYMLINK+="usb/cruzer", RUN+="/home/trinitronx/applications/startupscripts/synckey.sh", OPTIONS+="last_rule"
```

filename: /etc/fstab
added this line:
```
/dev/usb/cruzer /media/cruzer   vfat    users,rw,exec,nosuid,nodev,uid=1000,gid=1000,umask=0002        0       0
```

filename: synckey.sh
```
#!/bin/bash
USBPATH='/media/cruzer'
PROFILEPATH=/FirefoxPortable/Data/profile/
GPGPATH=/ThunderbirdPortable/Data/gpg/
EXITSTATUS=0 #initialize our exitstatus to success
mount /dev/usb/cruzer #mount using options in /etc/fstab

if [ -n "$USBPATH" ]
then
	PROFILEPATH=${USBPATH}$PROFILEPATH
	GPGPATH=${USBPATH}$GPGPATH
	if [ -d "$PROFILEPATH" ]
	then
		if cp /home/trinitronx/.mozilla/firefox/<profile ID>.default/bookmarks.html $PROFILEPATH
	        then
 	               echo "Successfully copied bookmarks.html to $PROFILEPATH"
		else
                	echo "Failed to copy bookmarks.html to $PROFILEPATH"
	                (( EXITSTATUS++ ))
            	fi
        else
            echo "$PROFILEPATH does not exist"
            (( EXITSTATUS++ ))
        fi
        if [ -d "$GPGPATH" ]
        then
		if cp /home/trinitronx/.gnupg/*.gpg $GPGPATH
	        then
	                echo "Successfully copied gpg files to $GPGPATH"
            	else
                	echo "Failed to copy gpg files to $GPGPATH"
                	(( EXITSTATUS++ ))
            	fi
        else
		echo "$GPGPATH does not exist"
		(( EXITSTATUS++ ))
        fi
else
	echo "No disk at $USBDEVICE found in mtab"
	(( EXITSTATUS++ ))
fi

if [ "$EXITSTATUS" -gt 0 ]
then #there were errors
    echo "$EXITSTATUS errors encountered"
    EXITSTATUS=1
fi
exit $EXITSTATUS

```

Ok.. so I figured out that udev does indeed run whatever it finds in the RUN string with root priviledges.
This means that if you're still running 386 and truecrypt is working normally, then it should inherit root permissions from udev.  The problem may be if you're not passing your truecrypt password or path to a keyfile on the command line, and the script is hanging trying to get user input for a password.

There are a few important options in the fstab as well.  The major one is 'users'.  Note that this is different from just plain 'user'.  The problem with the singular 'user' option is that it doesn't allow you to unmount the drive when root mounts it.  Since the script runs with root permissions, the mount command also gets root permissions and makes it so noone else can unmount the drive but root.  However, if you use 'users', then anyone can mount/unmount it as they please, so you can right click on the desktop icon and unmount it normally without an error.  I'm using 'exec,nosuid,nodev,uid=1000,gid=1000,umask=0002' so I can execute files directly from the drive, not have any setuid programs on the drive (for security reasons), not have any block devices on the drive, set the userid and groupid owners on the drive to my user, and finally set the permissions to 775.  One thing to note is that the umask is the inverse of what you'd type into chmod, so just subtract the umask numbers from 777.  Also, there are apparently 4 digits in it for some reason... I'm not really sure what the first one is for, but it is there.  One last thing I found out was that when writing your script, you don't need to put full paths on commands unless they don't reside in your $PATH variable.  To see what this is, just type $PATH into a bash shell.  This works exactly like the system path variable in Windows and DOS :D.
I also found that you shouldn't use the "~" shortcut to your home directory, since root is running the script, it will be evaluated as root's home directory which is: /root/
I had problems figuring out why my files wouldn't copy over for a while, and finally realized I was using the ~ shortcut... lol.

The udev rules file matches a few properties on the drive, then creates the symlink which I used in the fstab as a mount point, runs my script, and then tells udev to not match any more rules to the drive.  I've found that the last little OPTIONS+="last_rule" part makes it so only one shortcut is made on your desktop.  I haven't needed to disable gnome's automount feature because it seems to not be causing any problems for me.

I have also done a `sudo chown root:root synckey.sh` to change user and group ownership of the file to root, then done `sudo chmod 755 synckey.sh`.  I did this because I didn't want the file writeable by anything other than root, since it is effectively run by root when udev calls it.  If somehow someone got into my machine, they could have an easy way to escalate their permissions or execute anything as root by editing the file.  Anyone can still execute the file though.  I took out the hal-get-property part as it wasn't needed, and I may eventually attempt to code in a simple authentication using a gpg signed file.  I just realized it would have been dumb to encrypt a file to myself using the public key, since anyone could do that :p.  Only I can sign a file, since that uses the secret key.

It seems you have this working so far, just the truecrypt you're having troubles with?  First I'd suggest trying to pass the password or keyfile to it through the command line (you may want to chmod the script so only root can read it if you do this).  You could set the permissions to rwxr-x--x (751) so only root and people in group root can read it.)  For some reason when I set my scripts permissions to 751, it won't let me execute it, even though technically the 'other' group has x permissions... weird.
If that doesn't work, maybe look into mounting the disk image or partition through a cryptoloop.  I'm not sure myself on how to do this, or if it even is compatible with truecrypt... but maybe you can find something.
I've got to wait for it to be fixed for the 686 kernel if I want to use it in linux sadly (since I'm too stubborn to run a non Hyperthreading kernel for that extra little boost.. lol)

---

### Post by TiredBird on 2006-10-03
Glad you got it working. I didn't go to bed after all. I've been wading through the TrueCrypt forum looking for a solution to my problem but I just finished everything they have on Linux and can't even find a mention of udev.

I was just about to make my own post on their website when I discovered that you had written again.

Thanks for the explanation of 'users' vs 'user'. It solves another problem I was having.

No user input needed. I'm using a combination of keyfiles which are preset before the program runs. My security is in the fact that my USB key has to be plugged into a machine of mine for the decryption to take place automatically. If I'm on someone else's machine I have to reconfigure to make it work. 

The the USB key is mostly encrypted, if it is lost or stolen, it has a very high level of encryption that will not be broken very easily and if someone tries to do something to one of my computers, they can't without the USB key, (which is on my key ring), being plugged into the machine. And if I don't reset the algorith every so often, (like if I'm dead or in the hospital), the automatic scheme breaks and you have to rearrange a whole bunch of files before it will work again. (Not likely!)

I can use the exact same command to make it work from the command line but under Udev, it doesn't work. I've tried every combination I can think of to try and make it work but I can't figure out how to do it. I put it in a script by itself with a one line echo to a log file. I get the entry in the log file but TrueCrypt doesn't execute, or if it does, it does so with errors which I have yet to look at. The same script file runs just fine from the command line.

I already have everything on the command line with it. There is no password and the keyfile is a directory so it isn't really telling anything. Only the program when it executes knows whether or not the files it finds in the directory are the right ones or not. 

Since I don't know what hyper-threading is I don't know what I'm missing. Probably just as well.

---

### Post by TrinitronX on 2006-10-03
Hmm... are you using something like: ```
 2>> /path/to/logfile.txt
``` after the truecrypt command?  The reason the 2 is there is to redirect stderr to the logfile.  On some commands I was testing in my script (like cp)... the normal append ">>" operator didn't spit out the error, but when I redirected stderr to the logfile, I could see what was going wrong.  That's how I figured out that ~ was referencing /root/ and not my homedir :p.
If that still doesn't show an error, then I'm not sure how you can see what's going on.

Perhaps trying `dmesg | tail` or `dmesg >> /some/file.txt` so you can see if the kernel module gets loaded?
Try looking at the system log through System->Administration->System Log too if you still can't find anything.

I looked back in the thread and found that you were asking about "C Shell".  I don't know much about it myself, but I found this: [http://en.wikipedia.org/wiki/C_shell](http://en.wikipedia.org/wiki/C_shell)
There are many shells available other than the default bash, and they're all in synaptic if you wish to try them out :D.  I think I remember seeing these ones in there: csh, ksh, tcsh, fish, zsh, etc...
I haven't tested any out myself... I'm not sure if I'd be all that great at using C syntax for stuff since I haven't done much C programming really, lol.

Oh... if you're going to get into shell scripting, one very useful tip I found to debug things in bash is to set the -x flag in your interpreter declaration on the first line of the file like this:
```
#!/bin/bash -x
```
When using this, it will show you what it's seeing as each command is run with a + in front, and then the output too.

---

### Post by TiredBird on 2006-10-03
Okay, I'm going to try some of your suggestions regarding the error messages. Maybe I can figure something out from those. Thanks for the tip.

I posted a message on the TrueCrypt forum. I'll see if I get anything from that. With all the time I've spent on this lately I remember now why I abandoned the project the first time I got in trouble with it.

---

### Post by TrinitronX on 2006-10-03
I just reviewed your udev rules and realized that you've got a bunch:
```
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", SYMLINK+="usb/thumbdrive"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", RUN+="/bin/mount /dev/usb/thumbdrive"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84",
 RUN+="/usr/bin/truecrypt -N 1 -p '' -k /home/username/thumbdrive/TrueCrypt/keypath /home/username/thumbdrive/TrueCrypt/Krypto.tc"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", RUN+="/bin/mount /dev/mapper/truecrypt1"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", OPTIONS="last_rule" 
```

I'm not really sure, but I think since all these rules are using the same exact matching options, they will be executed almost simultaneously when the 'add' event happens.  I also see why you needed to use the full paths to commands in the .rules file.  The reason is because udev does not create a shell environment when it executes stuff in RUN="".  This means there is no $PATH variable, and so no way to find executables without a full path to them.

I'd also consider trying to put all your run commands in a script, then just execute the script with 1 run command.  That way you'll be sure to have a root shell executing the commands all in order.

Try using something like this:
```
#!/bin/bash
mount /dev/usb/thumbdrive
truecrypt -N 1 -p '' -k /home/username/thumbdrive/TrueCrypt/keypath /home/username/thumbdrive/TrueCrypt/Krypto.tc
mount /dev/mapper/truecrypt1
```
name the file to whatever you want, usually I stick to using the '.sh' extension for shell scripts.  Then remember to `chmod +x yourscriptfile.sh`.  Also, remember that whenever you mount something shorthand without giving it both the device and mountpoint, you'll need a cooresponding entry in /etc/fstab so that it will know how to mount a certain device or mountpoint.

Then for your .rules file in /etc/udev/rules.d/, you'd only need 1 rule :
```
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", SYMLINK+="usb/thumbdrive", RUN+="/path/to/yourscriptfile.sh", OPTIONS="last_rule"
```

That way during the add event, you create a symlink, run the script, and make sure that your rule is the only one executed to prevent gnome from automounting etc...

Using a script you can also use shell scripting syntax, including pipes "|", redirection ">", append to file ">>", and all other shell commands, environment variables, and shell scripting constructs (if...then...else...fi, functions, arrays...etc..).  And you don't need to spell out the full paths to commands either because the shell environment sets up your PATH variable when it runs :D.

I attempted to redirect output to a logfile within the udev RUN command, but it didn't seem to work before... so if you're still using the same rules and no script, then be sure to try it this way.

---

### Post by TiredBird on 2006-10-03
TrinitroniX:

I see you found my post on TrueCrypt. I appreciate your suggestions but I have tried everything you suggested. Actually, the multiple run commands were at one time in a single script just as I posted on this forum. I've also had each command in a separate script with a separate run for each script. That was where I put the log file postings I referred to and there is no doubt that each script was executing - it just wouldn't run the one with TrueCrypt in it. I'm about to try putting those commands into a script again and adding the error logging, (2>> I believe you said), to see if I can learn anything that way. I'll let you know.

I also see that you are doing some compiling of TrueCrypt. It will be interesting to find out what you discover. Can you make it work from edev?

If you start another thread or think you are too far off topic, pm me.

---

### Post by TrinitronX on 2006-10-03
WOW!   I just managed to figure out 2 problems today!
Now I've got truecrypt installed and working on the 686 kernel :D.
Details of this are here for the benefit of others on the forum having problems with the truecrypt kernel module failing to load: [http://www.ubuntuforums.org/showpost.php?p=1577276&postcount=29](http://www.ubuntuforums.org/showpost.php?p=1577276&postcount=29)

Once I got that installed, I decided to tackle the automount truecrypt volume on drive insertion.  After a lot of debugging, I've figured it out! :D

Here's what I did:
[list=1]
[*]Set up my other usb key using truecrypt with a testvolume.tc encrypted volume with no password and a keyfile called testkeyfile.txt.
[*]Looked up the usb key's sysfs info using: ```
udevinfo -a -p /sys/block/sdc/
```
(my usb key happened to be mounted this time at /dev/sdc)
[*]Copied a few of the matching rules from one of the 'device chain' headings (they've definately got to be under the same heading)
[*]Edited my custom rules file again /etc/udev/rules.d/10-usbkeysync.rules and added:
```
ACTION=="add", KERNEL=="sd?1", BUS=="usb", SYSFS{manufacturer}=="M-Systems", SYSFS{product}=="Dell USB Memory Key", SYSFS{serial}=="06B1FC3129001F38", NAME="%k", SYMLINK+="[color=red]usb/dellkey[/color]", RUN+="[color=green]/home/trinitronx/test.sh[/color]", OPTIONS+="last_rule"

```
[*]Created mount points, and edited my /etc/fstab with these 2 lines:
```
[color=red]/dev/usb/dellkey[/color]	[color=#ffac10]/media/dellkey[/color]	vfat	users,rw,nosuid,nodev,uid=1000,gid=1000,umask=077	0	0

[color=brown]/dev/mapper/truecrypt0[/color] [color=blue]/media/secure[/color] vfat users,rw,uid=1000,gid=1000,umask=0007	0	0
```
[*]Made my /home/trinitronx/test.sh script:
(mount points I chose were: [color=red]/media/dellkey[/color], and [color=blue]/media/secure[/color])
```
#!/bin/bash
DevNum=0
KeyFile="[color=#ffac10]/media/dellkey/[/color]testkeyfile.txt"
CryptVolume="[color=#ffac10]/media/dellkey/[/color]testvolume.tc"
mount [color=red]/dev/usb/dellkey[/color]
sudo truecrypt -p "" -k $KeyFile --device-number $DevNum $CryptVolume
mount [color=brown]/dev/mapper/truecrypt$DevNum[/color]

```
[/list]
I chown this file: ```
sudo chown root:root [color=green]/home/trinitronx/test.sh[/color]
```
... and chmod it 750: ```
sudo chmod 750 [color=green]/home/trinitronx/test.sh[/color]
```
That's it :D.

For some reason running truecrypt normally in a script executed by udev thinks there are no loop devices free.  I think this is a bug in truecrypt, since I tested that losetup was in the shell environment's path, and that the appropriate kernel modules for the loop devices were loaded.  It shouldn't need sudo because it's already running as root... but it seems happy this way so whatever :p.

The stuff that's important is that for everything you mount in your script, you need an entry in /etc/fstab.  I previously tried using the '-M' flag with some mount options passed to truecrypt in the script, but the 'users' option would not take effect so that any user could unmount it.  That made it so I had to open a command line to unmount that volume.

There is one problem though, to unmount the host usb drive that your truecrypt volume is mounted on, you need to run 'sudo truecrypt -d /media/dellkey/testvolume.tc' so that the thumbdrive won't be marked as in use by truecrypt.

To fix that, I made a 1 line nautilus script in ~/.gnome2/nautilus-scripts called "Unmount-Truecrypt"
```
#!/bin/bash
gksudo --sudo-mode "truecrypt -d"

```
I chmod this one 744.
(this script will unmount all truecrypt volumes, so if you only want to unmount a specific one, add it after the '-d')

I hope this helps you get yours running too :D, and also that I've made it clear enough for anyone else that may find this thread.

---

### Post by TiredBird on 2006-10-03
Alright, I'm going to try it but what happens when you put 'sudo' in the script? That's one I hadn't tried because I didn't think it would work.

---

### Post by TrinitronX on 2006-10-03
When sudo is run by root, no password is required, so the script will not hang as I previously thought.  Udev is definately running the script as root, as evidenced by the output of `whoami >> /path/to/some/logfile.txt`, which yields "root".  It's definately weird that this is required though... it's probably got to do something with some low level effective userid bug in truecrypt or something :p.

Good luck :D

---

### Post by TiredBird on 2006-10-03
okay, one more question before I get too far into this. Where is your truecrypt executable located and what are its permissions. Did you suid it?

---

### Post by TrinitronX on 2006-10-04
My truecrypt is in /usr/bin, with file permissions: ```
-rwxr-xr-x 1 root root 247700 2006-10-03 16:53 /usr/bin/truecrypt

```
I did not need to suid it.

EDIT: I also just edited the stuff in the solution so it's color coded and easier to see all the stuff that needs to match up.  It ends up being a bit messy :P.

Just change things to suit your file paths of course.

---

### Post by TiredBird on 2006-10-04
:p Wow - its working - you're a genius!

I did it exactly like you did except for a few minor changes.

I broke the rules file into steps. It really doesn't have to be on the same line. I've done a lot of reading on udev, including from the org that's responsible for it and I can safely say that it's okay to have multiple lines with all the same qualifiers. In fact, in some cases it's a necessity.

But anyway, it's working thanks to you. 

Now I can go get drunk. (Well it's kind of late to get drunk but at least I can get a few drinks.)

Thanks again.

P.S. My next project is to get Ubuntu running from a thumb-drive, much of which is encrypted. Interested?

---

### Post by TiredBird on 2006-10-04
We've been using 'add' in udev. There is also a 'remove'. Isn't there someway we can get udev to reverse all these steps when we pull the usb key out? It would be nice not have to use any commands at all.

I hate to lay this on you but since you did so well with the rest of it, I thought maybe you could solve this one too.:twisted:

---

### Post by TrinitronX on 2006-10-04
Hahaha, glad to hear it's working for you too :D.

I was already one step ahead of you in attempting to use the 'remove' command to unmount things instead of the nautilus script.
However, I wasn't sure if it would be a good thing to unmount a drive after it was pulled out :p.  Since file writing is asynchronous, it could be a bit risky to just pull the drive out before all operations in the queue are done.
I suppose you could try using the 'sync' option in your fstab for both of the usb device and the truecrypt mapping to force synchronous writing.  Just be sure to wait a while after writing things to the drive just in case.

I think I read somewhere that using synchronous writing to a flash device could possibly shorten its lifetime, but I dunno :p.

Another thing I noticed in udevmonitor was that another block device was being unmounted and removed after issuing the `truecrypt -d` command.  I can't remember what it was exactly, but the sys path to it was something like /sys/block/dm-<some number>.  I attempted to hook onto the 'umount' action at one point, but apparently udev only uses 'add' and 'remove'.  I figured since udevmonitor reports some things with 'mount@blahblah' and 'umount@blahblah', then I could use it too, but guess not, hehe.

Feel free to try it out if you wish, but I decided to stick with the safer way of unmounting by hand.  Even though I've got some assistance from the nautilus-script :D.

---

### Post by TiredBird on 2006-10-04
Well I don't have it yet but I'm getting close.

I changed the mapper number from 0 to 9. I did that because sometimes I have other TrueCrypt containers mounted and if you don't specify it in TrueCrypt it uses the next available, which if it is the first device being decrypted, is going to be 0. So it is possible the 0 is already taken when I put my encrypted stick in. To make sure that doesn't cause it to fail I changed it to 9.

Re 'sync': I had already added that to my fstab entries before I read your post because sometimes my script wasn't able to do the dismount because the device was still busy. (I'm not using the same script as you. I really just did a complete reverse of what we used to get the stuff mounted. My script is below.)

```
#! /bin/bash
umount /home/username/KRYPTO
sudo truecrypt -d /home/username/Mem1GbTDa/TrueCrypt/Krypto.tc
umount  /home/username/Mem1GbTDa
```

So far these reverse steps seeme to work pretty much as might be expected. (At least in the script.)

If I run this script before I pull the USB stick out, everything reverts to the way it was before the stick was plugged in.

HOWEVER, if I pull the stick out first, then run the script, it can't execute the final 'umount' because the symlink no longer exists. It wants it to be dismounted by its kernal name as in 'umount /dev/sda1 or /dev/sdb1 depending on what sequence it was in the mounting. 

I can run the 'mount' command to find out what I need and I can dismount it by hand after finding that out. I'm hoping that from udev I can find out what that is. Otherwise I've got to go back to the first step in the udev rules file and give the device a unique name. (I was letting it keep the kernal assigned name by not including the NAME= clause in my rules. You were keeping it by using NAME="%k" which assigns it the same name it already has. It is possible to give it a unique name and that maybe what we have to do.)

I'll post more after I do some more experimenting.

---

### Post by TiredBird on 2006-10-04
Update...

I added the following line to the front of my udev rules file:
```
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", NAME="EncryptedTD"
```
(If you do this you're going to have to take the 'NAME="%k"' entry out of your next line as that would just rename it back to its original name.)

Then I redid my script:
```
#! /bin/bash
sudo umount /home/username/KRYPTO
sudo truecrypt -d /home/username/Mem1GbTDa/TrueCrypt/Krypto.tc
sudo umount  /dev/EncryptedTD
```
(I added the 'sudos' to it so that I could run the script from the command line.)

This works from the command line. I haven't tried it yet from the udev rules file. I can run this script before or after I pull the key out and it will still clean up the system for me. As long as I use this script once for each time I pull the USB key out, I don't have any problems with multiple mount errors etc.

Now to get the script working from the udev rules file...

---

### Post by TiredBird on 2006-10-04
I've got it working!

It's putting two icons on my desktop for the USB stick, (in addition to another one for the encrypted container, total three icons), but I can live with that until I figure out how to get rid of the extra one. I think the extra one came about because I eliminated the 'last_rule' option. I think it's coming from another rule further down the line that's built in.)

Here's what I did:

/etc/fstab
```
/dev/usb/Mem1GbTDa   /home/username/Mem1GbTDa  vfat  sync,users,rw,umask=000,uid=1000,gid=1000  0  0
/dev/mapper/truecrypt9  /home/username/KRYPTO  vfat  sync,users,rw,umask=000,uid=1000,gid=1000  0  0
```
/etc/udev/rules.d/10-local.rules
```
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", NAME="EncryptedTD"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", SYMLINK+="usb/Mem1GbTDa"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", RUN+="/home/username/bin/mountkey"
ENV{ACTION}=="remove", ENV{DEVNAME}=="/dev/EncryptedTD", RUN+="/home/username/bin/umountkey"
```
/home/username/bin/mountkey
```
DevNum=9
KeyFile="/home/username/Mem1GbTDa/TrueCrypt/MasterKey"
CryptVolume="/home/username/Mem1GbTDa/TrueCrypt/Krypto.tc"
mount /dev/usb/Mem1GbTDa
sudo truecrypt -p "" -k $KeyFile --device-number $DevNum $CryptVolume
mount /dev/mapper/truecrypt$DevNum
```
/home/username/bin/umountkey
```
umount /home/username/KRYPTO
sudo truecrypt -d /home/username/Mem1GbTDa/TrueCrypt/Krypto.tc
umount  /dev/EncryptedTD
```

---

### Post by TiredBird on 2006-10-04
Whoops, I discovered a problem.

The way I had it set up, if I rebooted without another key plugged in, I was never able to get it to find the encrypted key. I think it was something to do with the 'last_rule' option.

Anyway, I've changed it again. The 'last_rule' option is gone and I'm back to getting three icons but otherwise it works fine. I think that this time I've tested all the combinations of reboot, with the stick plugged in by itself, with nothing plugged in, with something else plugged in and with two sticks plugged in. They all seem to work. 

Now if anyone knows how to get rid of the extra icon I might do that but otherwise I'm done screwing with this.

---

### Post by TrinitronX on 2006-10-06
In the umount script, you don't need to unmount "/home/username/KRYPTO" if you're using truecrypt to dismount it.  It should already take care of it for you.

Looks like you've got it set up nicely though... I think I may test it out at some point.

---

### Post by TiredBird on 2006-10-08
I know that you're correct. I did it because I wanted to exactly reverse the mounting steps, not because I had to. 

I've carried things a lot further now. I have udev so it recognizes any of four different USB storage devices when I plug them in and remove them. Also, plugging in the one we were working with also unencrypts a partition on the internal harddrive and sets it so that an external harddrive is also unencrypted if it is plugged in later.

I've also got it working on two different systems. 

I expanded the use of variable names in the scripts so that all I have to do to add a device is copy the scripts and change the variable names. I didn't really need to do that but it is cleaner and easier to maintain.

And for some reason the extra icons have disappeared. (I'm not using the auto mount feature as two of my sytems don't have it anyway.)

---

### Post by TrinitronX on 2006-10-09
That's a very interestng use of the script :D.
In essence, the possibilities of this are endless as long as linux programs have command line support :D.

Currently I've got one of my usb keys with an encrypted file container and the windows version of Truecrypt installed with the very useful "autorun.inf" traveller disk functionality.  I used the XP version of Truecrypt to first install itself onto the drive using 'Tools->Traveller Disk Setup', and selecting options to mount always on a constant drive letter.
I've got it using keyfiles from another smaller usb key, so I can plug into any windows machine and automount the drive as long as the other USB *key* is present (pun intended ;) ).

I've been wondering if there's a way to edit that autorun.inf file and force it to somehow find the other key and unlock automatically as long as it's there.  Then I wouldn't have to select which keyfiles to use every single time :p.  The problem is that in windows there is no way to force the drive to be mounted on a specific drive letter every time on any given computer (as far as I know).

I was thinking on somehow creating a batch script that would run through all the different drive letters searching for a specific folder on them, and when found, use that folder's keyfiles automatically.  Then just set this batch script to run in the autorun.inf file next to it's respective action.  Right now I'm pretty bad at batch scripting though :D, and am pressed for time with exams etc...

Any other suggestions that may be an easier way?

---

### Post by TiredBird on 2006-10-09
Oh damn, I have to think again...

I did this several months ago but at the moment I can't remember how. I'll  look and see how I did it later tonight. (One of my XP systems typically mounts the USB key at E: but sometimes it comes up on F: so I know I made it work somehow.) 

I think it had something to do with the program 'PStart' but I'm not sure. ('PStart is a windows program launcher that uses relative addresses instead of absolute addresses. I have it on my USB stick. It's available free - [click here]("http://www.pegtop.net/start/").) 

I also use TrueCrypt Traveler. I'll be using an XP system later tonight and I'll look to see how I set it up. (I'm on Xubuntu right now.)

---

### Post by TrinitronX on 2006-10-10
D'oh, nevermind, I managed to piece together a batch file that will find where my keyfile folder is, not only on the other usb key, but also local hard drive copies in other predefined paths.  I like to keep a backup of my keyfiles on a different drive, so I don't have to plug in both keys at home, or if the usb key gets lost or the files are messed up.

Here's the modified autorun.inf file:
```
[autorun]
open=mountscript.bat
shell=mount
action=Mount TrueCrypt Volume
shell\open\command=TrueCrypt\TrueCrypt.exe /lT /e /m rm
shell\open=TrueCrypt Start
shell\mount\command=mountscript.bat
shell\mount=TrueCrypt Mount
shell\dismount\command=TrueCrypt\TrueCrypt.exe /q /d
shell\dismount=TrueCrypt Dismount All

```

And, here's the mountscript.bat file:
```
@echo off
SET KEYFILE=0
for %%a in (C D E F G H I J K L M N O P Q R S T U V W X Y Z) do for %%b in (%%a:\Path1 %%a:\Some\Alternate\Path %%a:\Yet\Another\Path) do if exist %%b set KEYFILE=%%b
IF NOT %KEYFILE%==0 CALL TrueCrypt\TrueCrypt.exe /q /a /lT /e /m rm /v "myvolume.tc" /k %KEYFILE%
```

Due to the horrible syntax that MS decided to use for batch files, it looks really ugly with 2 nested for loops on one line... eew :-?
At least it beats having to manually put in my keyfiles each time.

---

### Post by TiredBird on 2006-10-10
I'm glad you got it worked out by yourself because I never got to the XP machine tonight. I'm trying to get Xubuntu ready to load on a USB key.

I am running Xubuntu from two small partitions, one is 0.5GB, (that's root), and the other is 1.0GB, (/usr). I've been trying to get it set up the way I want without using a lot of space. I want to put the whole thing on a USB key without compression. (The two partitions together are currently about 1.0 GB total.) 

The reason that /usr is in a different partition is that it, or at least most of it, will be encrypted. Hopefully, an autorun script will decrypt it and mount it at boot time.

I am really surprised at how good the XFCE GUI is considering it takes so much less space and processor time. I'm impressed. Actually, I'm liking it a lot better than than the Gnome desktop.

---

