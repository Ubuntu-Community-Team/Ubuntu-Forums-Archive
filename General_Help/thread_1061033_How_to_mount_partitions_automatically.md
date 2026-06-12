---
title: "How to mount partitions automatically?"
date: 2009-02-05
forum: General Help
---

### Post by Jengu on 2009-02-05
By default, Ubuntu doesn't mount my windows partition or my pen drive until I open them in the Places menu. I do a lot of work from the console, so this behavior is kind of annoying -- I have to interrupt my efficient stream of typing to reach for the mouse and interact with the GUI just to open a window that I'll close right away because I really want to mess with the files from the command line, not from Nautilus. Is there a way to have Ubuntu mount both my windows partition and any removable drives automatically without me having to select them from the Places menu? I believe versions before Hardy acted this way.

---

### Post by matey3 on 2009-02-05
I am new to linux but I think you can insert a line in fstab under /etc
my fstab file looks like this;

```
root@super-desktop:/etc# cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```


BTW I think you can alsso put the command line (mount) in a script, chmod it and then put it in startup. like if your file is called pen.sh then;
 
May be some one else can be more specific?
good luck;

---

### Post by stchman on 2009-02-05
> **Jengu said:**
> By default, Ubuntu doesn't mount my windows partition or my pen drive until I open them in the Places menu. I do a lot of work from the console, so this behavior is kind of annoying -- I have to interrupt my efficient stream of typing to reach for the mouse and interact with the GUI just to open a window that I'll close right away because I really want to mess with the files from the command line, not from Nautilus. Is there a way to have Ubuntu mount both my windows partition and any removable drives automatically without me having to select them from the Places menu? I believe versions before Hardy acted this way.

You are going to have to setup your fstab file to mount Windows partitions upon bootup.  Your pendrive should automount when inserting it into a USB port.  I have a tutorial on how to mounts partitions.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by Jengu on 2009-02-05
My pen drive doesn't automount when inserted, that's the problem. I have to select it in the Places menu first. It's NTFS formatted, not FAT32 (because on Windows FAT32 drives don't get a write cache), maybe that's part of it?

Also I'd prefer not to mess with /etc/fstab if possible because that a distribution upgrade could blow it away -- it seems like the 'correct' solution should just be a switch that causes any partitions detected on any local or removable drives to be automounted, rather than adding entries to a system file. I suspect this must exist since Ubuntu used to work this way.

---

### Post by jerome1232 on 2009-02-05
> **Jengu said:**
> My pen drive doesn't automount when inserted, that's the problem. I have to select it in the Places menu first. It's NTFS formatted, not FAT32 (because on Windows FAT32 drives don't get a write cache), maybe that's part of it?

Also I'd prefer not to mess with /etc/fstab if possible because that a distribution upgrade could blow it away -- it seems like the 'correct' solution should just be a switch that causes any partitions detected on any local or removable drives to be automounted, rather than adding entries to a system file. I suspect this must exist since Ubuntu used to work this way.

It does work this way, when you insert removable media it get's auto-mounted.

I would check a few things, go into System-Administration-Users and Groups, Click unlock, select your user and hit properties. Make sure "Access external storage devices automatically" is checked and also make sure "Mount user-space filesystems (FUSE)" is checked.

---

### Post by Jengu on 2009-02-05
I looked and mounting userspace filesystems was not checked! But checking it didn't change the behavior. Maybe we're working with different meanings of 'mounted'? I mean that when I put in my pen drive, a folder in /media is not created until I view the drive in Nautilus.

---

### Post by jerome1232 on 2009-02-05
> **Jengu said:**
> I looked and mounting userspace filesystems was not checked! But checking it didn't change the behavior. Maybe we're working with different meanings of 'mounted'? I mean that when I put in my pen drive, a folder in /media is not created until I view the drive in Nautilus.

No we are meaning the same thing (that is what mounting a drive is) I. for example. plug in my thumbdrive (fat16) it automatically get's mounted and show's up on my desktop, with an entry in the places menu as well.

Same with my external drive which is formated as ext3, worked when it was ntfs as well. I'm guessing there's some other setting somewhere that's doing it I just wouldn't know where to look. (I've never had an issue with it not happening)

---

### Post by stchman on 2009-02-05
> **Jengu said:**
> My pen drive doesn't automount when inserted, that's the problem. I have to select it in the Places menu first. It's NTFS formatted, not FAT32 (because on Windows FAT32 drives don't get a write cache), maybe that's part of it?

Also I'd prefer not to mess with /etc/fstab if possible because that a distribution upgrade could blow it away -- it seems like the 'correct' solution should just be a switch that causes any partitions detected on any local or removable drives to be automounted, rather than adding entries to a system file. I suspect this must exist since Ubuntu used to work this way.

I would make your USB flash drives FAT32.  I have an external USB hdd formatted in NTFS which auto mounts.  There is a setting in Gnome that auto mounts inserted media.

---

### Post by SenatorKane on 2009-02-06
If I may I would like to post a very similar problem here:

About a week ago, without any conscious action of mine, USB drives and drives not listed in fstab stopped being listed under "places" in nautilus. It all worked flawlessly before. They are recognized and I can mount them manually but only by prefixing mount with "sudo". This is extremely annoying since the drives can then not be written on by  users. I probably messed with something to create this disturbance but I cannot think of anything. I have already searched the forums and asked google to no avail.

---

### Post by philidox on 2009-02-06
All the fstab editing is great but there is a much much much easier way of mounting your partions in ubuntu! A program called disk-manager will do it all for you automatically, its so easy to use. If you using intrepid you can get it from the repos, via Add/Remove... or synaptic package manager.  If your not follow this link and download the .deb file and install it.  It will solve all of your mounting issues.

[http://flomertens.free.fr/disk-manager/download.html](http://flomertens.free.fr/disk-manager/download.html)

---

### Post by SenatorKane on 2009-02-07
I installed the program and it does takes care of the drives not listed in fstab but it does not even recognize the plugged in usb stick although it can be mounted as "sde1".

---

### Post by philidox on 2009-02-07
hmmm... you cant mount your flash drives? Does it give any type of error message?  just to be clear your internal hard drive are working now right?

---

### Post by krayon on 2009-02-09
I believe the OP is having the same problem as me however people may not realise what the issue is.  If I understand him correctly, it is not that the device isn't mountable, or detected for that matter, it is simply that the only way to mount the device WITHOUT modification of configuration files such as /etc/fstab, or sudo mount commands, is via a GUI app.

You MAY be able to fix this by modifying */etc/hal/fdi/policy/preferences.fdi*

On my Ubuntu 8.10 system at least, it contains this:

```

  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>

```

The ***automount_enabled_hint*** looks like the issue as it's false atm.  You may need to reboot after changing this, I don't know.

---

### Post by SenatorKane on 2009-02-17
I did change the line

>   <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">true</merge>
      </match>
    </match>
  </device>

It now says "true". But it didn't solve my problem. Every drive not listed in fstab no matter if it is USB flash or internal does not show in nautilus and can only be mounted using "sudo"

Kane

---

