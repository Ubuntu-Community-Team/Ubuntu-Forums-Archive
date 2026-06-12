---
title: "Failed to initializate HAL!"
date: 2005-05-26
forum: Desktop Environments
---

### Post by marsopia on 2005-05-26
Hi people!

Since two weeks ago, after an update, I recibie this error message after choosing on gdm the Gnome desktop. Nothing appears, keyboard does nort respond, either the mouse. I can only reset the computer to get control again.

I can perfectly call KDE as user, w/o errors message.

I can do call Gnome desktop bootin on Rescue mode and signing as root. I still recieve the error message, but i have control of my desktop.

Any help will be welcomed.


I am using a clen Hoary installation, y have main, universe and multiverse enabeled.

PIII, 512 ram; Sis 6326; audio sb pci128

Thks

---

### Post by 23meg on 2005-05-27
did you by any chance upgrade to the 2.6.11 kernel? look [here](http://www.ubuntuforums.org/showthread.php?t=25247) if you have.

---

### Post by marsopia on 2005-05-30
No, i did not upgrade to kernel 2.6.11 I am running 2.6.10. 386 or 686, with both kernels I find this problem.

Mariano

---

### Post by dlpfmVfH on 2005-05-31
did receive the same message today, did a hard reboot, and logged in normally...
 :-? 
no problems...but what happened, how can I find out???

---

### Post by sethmahoney on 2005-05-31
I had the same issue after making changes to my /etc/hdparm.conf.  I loaded Ubuntu using a live CD (though if you can get in with KDE, you shouldn't have to do this) and changed the settings back, and everything worked again.  Though if you haven't made changes to /etc/hdparm.conf I can't really say what's going on.

Do you recall what was updated right before the HAL failure?

---

### Post by marsopia on 2005-05-31
I cant recall what was updated. 
I can actually run KDE but not Gmone as user, unless I boot on safe mode, log as root and then choose my username on gdm.

I haven't made any changes as I know on /etc/hdparam.conf as long as I know...

How should hdparam.conf look?

Here is mine:
## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}

Mariano

---

### Post by sethmahoney on 2005-05-31
Check this thread:

[http://ubuntuforums.org/showthread.php?t=21887&highlight=HAL+fail](http://ubuntuforums.org/showthread.php?t=21887&highlight=HAL+fail)

I'm not sure how to edit grub, but I'm sure someone around here knows.

---

### Post by marsopia on 2005-06-01
Heyyy great!!

Thats what is was heppening! I had a music cd on my dvd drive!! But I never thought that was the problem!! Thats why sometimes I could log, and some others not, but never realized about that.

I am using a new, clean final Hoary installation... is this a bug?

Mariano

---

### Post by marsopia on 2005-06-01
Thanks Mahonney!!

---

### Post by sethmahoney on 2005-06-04
No problem!  Glad I could help

---

