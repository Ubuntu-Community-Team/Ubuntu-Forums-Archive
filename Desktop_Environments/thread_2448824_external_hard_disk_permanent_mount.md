---
title: "external hard disk permanent mount"
date: 2020-08-14
forum: Desktop Environments
---

### Post by christon74 on 2020-08-14
Good afternoon fellow ubunters_ :D_ I am in very serious trouble. I have a western digital hard disk to which I have saved many video and music files, plus other documents. This morning I wanted to mount it permanently. I found a web page that helps you do just that. So I read it, followed the instructions and copy/pasted the command line below to a terminal window. I duly edited the username, but the problem is there is no sdb4 plugged to this desktop. So I re-entered the same command line, this time with "sdb1" instead of "sdb4". Now Ubuntu simply will not boot or I'm stuck with Ubuntu emergency mode and I cannot remember my root password. That's just how bad things are now. Can deleting the wrong command line (sdb4) fix this problem?
Thanks in advance for all help and trouble.
  echo "/dev/sdb4 /home/username/secondary-hard-drive ntfs defaults,noatime 0 2" >> /etc/fstab

---

### Post by TheFu on 2020-08-14
Running commands without fully understanding what they do is dangerous.  Always make a backup of any system file BEFORE you make changes.  Having a backup of the system (daily, automatic) would be really smart too.  If this data is so important, it needs to have at least 1 backup, preferably 2 (local and remote).

Cannot answer the question from the data provided.  To get started, we need to see all the partitions on the system, including what they are each for, the full fstab and any UUIDs.

Gather this information by booting from a "Try Ubuntu" flash drive and running the commands from a terminal window.  Then post both the command AND the output back here, wrapped in 'code tags', using the "Advanced Editor" - (#) button is the code-tag button.  Without the code tags, it is impossible to read the data.

**We don't need to see any data that has "loop" in the name, so please remove those parts.**

```
sudo fdisk -l
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
blkid # may need a sudo for this one)
cat /etc/fstab

```
Above is a 'code tag' entry. That's what yours needs to look like. It is non-proportional fonts so columns line up just like in the terminal.  Until you post, the copy/pasted stuff won't line up - don't fix any spacing, just wrap in the 'code-tags'

---

### Post by christon74 on 2020-08-15
Good morning TheFu:) _Thank you for answering so quickly. I have taken good note of the command lines you are suggesting, and I have created a Ubuntu Live usb memory stick. Now another problem is that when I plug the usb and choose the Try Ubuntu, I then get a perfectly black screen. It's thing "no mode set" thing. I think I'm missing some step. Well, I have just tried again, but the F6 key is of no help, I get a black screen. What's more, when I choose the "Try without installing" option, I get this message: unexpected SPCR access width, return to default e.  Now what if I try the rescue mode and try to edit Ubuntu, using CTRL+e and then type system.unit = rescue.target, then F10 or Ctrl+x, then mount -n -o remount, rw / ?. If nothing works at all, then I guess I will have to completely erase the Ubuntu partition and do a fresh install, thus losing some data. Luckily enough, I have saved the most important on a portable LaCie hard drive.
Perhaps of some relevance, here are some details about the hardware: Fujitsu-Siemens desktop Esprimo E5731 E-stars.  External hard drive is a Western Digital "My Book" usb 2.0 750 Gb.
Have a nice week-end;)

---

### Post by christon74 on 2020-08-24
:DHello again TheFu. I am marking this thread as solved. There was no other way but doing a fresh Ubuntu install, using the entire disk, thus erasing Windows 7 completely, and of course losing some data, yet nothing too important. And I had already saved the most important things to a portable LaCie hard disk. The only nagging thing today is that Grub no longer shows on startup. And yet it is present. Anyway, thank you for all help and trouble.

---

### Post by tea for one on 2020-08-24
> **christon74 said:**
> The only nagging thing today is that Grub no longer shows on startup. And yet it is present. 

You will have to edit the grub file to allow Grub to show when starting your PC.

```
sudo nano /etc/default/grub
```

Here is a copy of my grub file, which gives me a maximum 10 second delay for booting

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash fastboot"
GRUB_CMDLINE_LINUX=""

```

Don't forget to also update the new grub configuration.

```
sudo update-grub
```

Reboot and see if Grub appears - I hope so

---

### Post by TheFu on 2020-08-24
Sorry I didn't see this before.
I don't know the answers to most of the questions asked.

To change between console sessions, use <cntl><alt>F1 thru <cntl><alt>F8. F7 is normally the graphical console where the GUI runs.  Sometimes these need to see a few <enter> key presses to show the login prompt.

I've needed to edit the grub prompt only once the last 5-10 yrs, so I'd have to look up any commands just like you. In the last 5 yrs, everything about grub booting has changed since systemd took over. I have ZERO experience with that. Sorry.

I've noticed that more and more people seem to see blank screens these days that ever before.  I've never seen that here unless the GPU had died. Don't understand it.  Most of my systems use Intel iGPUs, but a few have nvidia GPUs - a 430 GS and a GT 1030.  I've had issues with both, but not the blank screen.

Whenever there is an error shown on the screen, I'll take that error verbatum and ask google for an answer. The trick is to add "ubuntu 20.04" and remove any parts of the error text that are only for my system.  For example, the timestamp will be unique and almost always, memory locations will be unique.

I'll start fresh using backups after spending about 30-45 minutes on any issue. I have daily, automatic, versioned, backups for all my systems. Effectively, within 30-45 minutes, I can perform a fresh install and restore system settings, system data, system config tweaks, my settings, my data, my config tweaks, and about 20G of data. Then I have a list of manually installed packages from the repos and force those to be installed in 1 command. As they install, the prior settings are seen and used.  45 min later - my system is back pretty much as it was from the backup that happened sometime last night.  Many people don't have this option because they don't have good backups and have to spend hours trying to solve issues that I'd simply not bother doing. As soon as it looks like more than 30 minutes is needed to fix something, I'll go nuclear and pave the road clean.  Generally, this doesn't happen very often - perhaps once every 4+ yrs to 1 of my systems.  The last time was in June with a 20.04 install.  My guess is that a bad patch to grub caused it.  Solutions that I though would be 100% certain to fix it failed, which completely surprised me.  I'm not new to this stuff, right?

Anyways, happy you had backups and weren't too afraid to use them.  Like all things, practice makes for confidence and speed. USB2 external device - ouch. Think I'd spend the $25 and get a USB3 device. Huge difference. Totally different class of performance than USB2.  Going from USB3 to USB3.2 isn't really noticeable and not worth the extra money, assuming your computer(s) even have a USB3.2 port.

Wiping Win7 may not have been needed, but it could be for the best since it shouldn't be used on any network at this point except as a target for attack practice.

---

