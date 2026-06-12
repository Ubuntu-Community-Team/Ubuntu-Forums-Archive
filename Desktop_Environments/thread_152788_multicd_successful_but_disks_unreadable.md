---
title: "multicd successful but disks unreadable?"
date: 2006-03-30
forum: Desktop Environments
---

### Post by entryname on 2006-03-30
Hi gang

After something of a struggle managed to get multicd to produce some backup CDs. cdrecord which it used claimed to have written these successfully, and multicd appeared to terminate normally. However I can't read the resulting disks. 
:confused: 
Am I right in thinking they are therefore worthless? SHOULD I be able to read multicd backup disks? If not, what can I do with them? Are they supposed to be bootable??

dmesg (extracts):
[COLOR="Blue"][I]michael@ubuntu:~$ dmesg
[   56.874180] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

[   56.874384] Probing IDE interface ide1...
[   57.698315] hdc: HITACHI DVD-ROM GD-2500, ATAPI CD/DVD-ROM drive
[   58.411963] hdd: IOMEGA ZIP 100 ATAPI, ATAPI FLOPPY drive
[   58.462805] ide1 at 0x170-0x177,0x376 on irq 15
[   58.463342] Probing IDE interface ide2...
[   58.975390] Probing IDE interface ide3...
[   59.488072] Probing IDE interface ide4...
[   60.000753] Probing IDE interface ide5...
[   60.534074] hda: max request size: 128KiB
[   60.534092] hda: 20044080 sectors (10262 MB) w/512KiB Cache, CHS=19885/16/63, UDMA(33)
[   60.534116] hda: cache flushes not supported
[   60.534360]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[   60.733974] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache
[   60.733999] Uniform CD-ROM driver Revision: 3.20
[   62.339750] Attempting manual resume
[   62.340222] swsusp: Suspend partition has wrong signature?
[   62.531860] usbcore: registered new driver usbfs
[   62.532008] usbcore: registered new driver hub
[   62.538773] USB Universal Host Controller Interface driver v2.2
[   62.539000] uhci_hcd 0000:00:07.2: Intel Corporation 82371AB/EB/MB PIIX4 USB
[   62.600586] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   62.600616] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000e000
[   62.601196] hub 1-0:1.0: USB hub found
[   62.601236] hub 1-0:1.0: 2 ports detected
[   62.770046] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   64.800489] SCSI subsystem initialized
[   64.810631] Initializing USB Mass Storage driver...
[   64.812440] scsi0 : SCSI emulation for USB Mass Storage devices
[   64.812685] usb-storage: device found at 2
[   64.812697] usb-storage: waiting for device to settle before scanning
[   64.812727] usbcore: registered new driver usb-storage
[   64.812740] USB Mass Storage support registered.
[   66.352485] Attempting manual resume
[   66.352880] swsusp: Suspend partition has wrong signature?
[   66.426773] kjournald starting.  Commit interval 5 seconds
[   66.426815] EXT3-fs: mounted filesystem with ordered data mode.
[   68.580118] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   69.917719]   Vendor: CD-RW     Model: CDR-6S52          Rev: 6SG4
[   69.917768]   Type:   CD-ROM                             ANSI SCSI revision: 00
[   69.948757] usb-storage: device scan complete
[   73.308558] sr0: scsi3-mmc drive: 12x/12x writer cd/rw xa/form2 cdda tray
[   73.313038] Attached scsi CD-ROM sr0 at scsi0, channel 0, id 0, lun 0
[   73.452557] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 5
[   77.417290] Adding 369452k swap on /dev/hda5.  Priority:-1 extents:1
[   77.763567] EXT3 FS on hda1, internal journal
[   93.922147] parport: PnPBIOS parport detected.
[   93.922208] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   93.967053] parport0: faking semi-colon
[   93.967832] parport0: Printer, HEWLETT-PACKARD DESKJET 710C
[   93.990303] lp0: using parport0 (interrupt-driven).
[   94.109907] mice: PS/2 mouse device common for all mice
[   94.403479] ide-floppy driver 0.99.newide
[   94.521220] hdd: 98304kB, 196608 blocks, 512 sector size
[   94.524792] hdd: 98304kB, 96/64/32 CHS, 4096 kBps, 512 sector size, 2941 rpm
[   94.671330] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[   94.811683]  /dev/ide/host0/bus1/target1/lun0:<6>ts: Compaq touchscreen protocol output
[   97.696265]  p4
[  101.466189] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[  101.962373]  /dev/ide/host0/bus1/target1/lun0: p4
[  104.110027] cdrom: open failed.
[  104.188883]  /dev/ide/host0/bus1/target1/lun0: p4
[  104.263349] cdrom: sr0: mrw address space DMA selected
[  104.294343] cdrom open: mrw_status 'not mrw'
[  111.124897] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  111.150396] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
[  128.722795] cdrom: This disc doesn't have any tracks I recognize!
[  249.411132] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[  249.411154] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[  249.493910] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[  249.493932] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[  249.599861] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[  249.599881] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[  249.682650] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[  249.682672] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[  249.788635] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[  249.788658] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[  249.871426] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[  249.871448] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[ 4518.340196] cdrom: This disc doesn't have any tracks I recognize!
[ 4652.364303] loop: loaded (max 8 devices)
[ 8107.704988] cdrom: This disc doesn't have any tracks I recognize!
[12634.084032] cdrom: This disc doesn't have any tracks I recognize!
[16891.540883] cdrom: sr0: mrw address space DMA selected
[16891.549365] cdrom open: mrw_status 'not mrw'
[16891.930641] cdrom: sr0: mrw address space DMA selected
[16891.939628] cdrom open: mrw_status 'not mrw'
[16893.032980] Unable to identify CD-ROM format.
michael@ubuntu:~$
[/I][/COLOR]

syslog (extracts):
[I][COLOR="Blue"]Mar 30 14:41:23 localhost syslogd 1.4.1#17ubuntu3: restart.
Mar 30 14:44:29 localhost gconfd (root-7313): GConf server is not in use, shutting down.
Mar 30 14:44:29 localhost gconfd (root-7313): Exiting
Mar 30 14:45:07 localhost kernel: [  788.407363] cdrom: open failed.
Mar 30 14:45:10 localhost kernel: [  791.459737] cdrom: open failed.
Mar 30 14:46:19 localhost kernel: [  860.674128] cdrom: This disc doesn't have any tracks I recognize!
Mar 30 14:48:36 localhost kernel: [  998.176115] cdrom: sr0: mrw address space DMA selected
Mar 30 14:48:36 localhost kernel: [  998.184018] cdrom open: mrw_status 'not mrw'
Mar 30 14:48:36 localhost kernel: [  998.215073] cdrom: sr0: mrw address space DMA selected
Mar 30 14:48:36 localhost kernel: [  998.223104] cdrom open: mrw_status 'not mrw'
Mar 30 14:48:37 localhost kernel: [  999.228179] Unable to identify CD-ROM format.
Mar 30 14:48:38 localhost kernel: [  999.802658] loop: loaded (max 8 devices)
Mar 30 14:53:22 localhost gconfd (root-21757): starting (version 2.12.0), pid 21757 user 'root'
Mar 30 15:39:15 localhost kernel: [   55.991583] PIIX4: IDE controller at PCI slot 0000:00:07.1
Mar 30 15:39:15 localhost kernel: [   55.991626] PIIX4: chipset revision 1
Mar 30 15:39:15 localhost kernel: [   55.991637] PIIX4: not 100%% native mode: will probe irqs later
Mar 30 15:39:15 localhost kernel: [   55.991735] Probing IDE interface ide0...
Mar 30 15:39:15 localhost kernel: [   56.255210] hda: WDC AC310200R, ATA DISK drive
Mar 30 15:39:15 localhost kernel: [   56.874180] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Mar 30 15:39:15 localhost kernel: [   56.874384] Probing IDE interface ide1...
Mar 30 15:39:15 localhost kernel: [   57.698315] hdc: HITACHI DVD-ROM GD-2500, ATAPI CD/DVD-ROM drive
Mar 30 15:39:15 localhost kernel: [   58.411963] hdd: IOMEGA ZIP 100 ATAPI, ATAPI FLOPPY drive
Mar 30 15:39:15 localhost kernel: [   58.462805] ide1 at 0x170-0x177,0x376 on irq 15
Mar 30 15:39:15 localhost kernel: [   58.463342] Probing IDE interface ide2...
Mar 30 15:39:15 localhost kernel: [   58.975390] Probing IDE interface ide3...
Mar 30 15:39:15 localhost kernel: [   59.488072] Probing IDE interface ide4...
Mar 30 15:39:15 localhost kernel: [   60.000753] Probing IDE interface ide5...
Mar 30 15:39:15 localhost kernel: [   60.534360]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Mar 30 15:39:15 localhost kernel: [   60.733974] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache
Mar 30 15:39:15 localhost kernel: [   60.733999] Uniform CD-ROM driver Revision: 3.20
Mar 30 15:39:15 localhost kernel: [   62.339750] Attempting manual resume
Mar 30 15:39:15 localhost kernel: [   62.340222] swsusp: Suspend partition has wrong signature?
Mar 30 15:39:15 localhost kernel: [   62.531860] usbcore: registered new driver usbfs
Mar 30 15:39:15 localhost kernel: [   62.532008] usbcore: registered new driver hub
Mar 30 15:39:15 localhost kernel: [   62.538773] USB Universal Host Controller Interface driver v2.2
Mar 30 15:39:15 localhost kernel: [   62.539000] uhci_hcd 0000:00:07.2: Intel Corporation 82371AB/EB/MB PIIX4 USB
Mar 30 15:39:15 localhost kernel: [   62.600586] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Mar 30 15:39:15 localhost kernel: [   62.600616] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000e000
Mar 30 15:39:15 localhost kernel: [   62.601196] hub 1-0:1.0: USB hub found
Mar 30 15:39:15 localhost kernel: [   62.601236] hub 1-0:1.0: 2 ports detected
Mar 30 15:39:15 localhost kernel: [   62.770046] usb 1-2: new full speed USB device using uhci_hcd and address 2
Mar 30 15:39:15 localhost kernel: [   64.800489] SCSI subsystem initialized
Mar 30 15:39:15 localhost kernel: [   64.810631] Initializing USB Mass Storage driver...
Mar 30 15:39:15 localhost kernel: [   64.812440] scsi0 : SCSI emulation for USB Mass Storage devices
Mar 30 15:39:15 localhost kernel: [   64.812685] usb-storage: device found at 2
Mar 30 15:39:15 localhost kernel: [   64.812697] usb-storage: waiting for device to settle before scanning
Mar 30 15:39:15 localhost kernel: [   64.812727] usbcore: registered new driver usb-storage
Mar 30 15:39:15 localhost kernel: [   64.812740] USB Mass Storage support registered.
Mar 30 15:39:15 localhost kernel: [   66.352485] Attempting manual resume
Mar 30 15:39:15 localhost kernel: [   66.352880] swsusp: Suspend partition has wrong signature?
Mar 30 15:39:15 localhost kernel: [   66.426773] kjournald starting.  Commit interval 5 seconds
Mar 30 15:39:15 localhost kernel: [   66.426815] EXT3-fs: mounted filesystem with ordered data mode.
Mar 30 15:39:15 localhost kernel: [   68.580118] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Mar 30 15:39:15 localhost kernel: [   69.917719]   Vendor: CD-RW     Model: CDR-6S52          Rev: 6SG4
Mar 30 15:39:15 localhost kernel: [   69.917768]   Type:   CD-ROM                             ANSI SCSI revision: 00
Mar 30 15:39:15 localhost kernel: [   69.948757] usb-storage: device scan complete
Mar 30 15:39:15 localhost kernel: [   73.308558] sr0: scsi3-mmc drive: 12x/12x writer cd/rw xa/form2 cdda tray
Mar 30 15:39:15 localhost kernel: [   73.313038] Attached scsi CD-ROM sr0 at scsi0, channel 0, id 0, lun 0
Mar 30 15:39:15 localhost kernel: [   73.452557] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 5
Mar 30 15:39:15 localhost kernel: [  101.962373]  /dev/ide/host0/bus1/target1/lun0: p4
Mar 30 15:39:15 localhost kernel: [  104.110027] cdrom: open failed.
Mar 30 15:39:15 localhost kernel: [  104.188883]  /dev/ide/host0/bus1/target1/lun0: p4
Mar 30 15:39:15 localhost kernel: [  104.263349] cdrom: sr0: mrw address space DMA selected
Mar 30 15:39:15 localhost kernel: [  104.294343] cdrom open: mrw_status 'not mrw'
Mar 30 15:39:15 localhost kernel: [  111.124897] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 30 15:39:15 localhost kernel: [  111.150396] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Mar 30 15:39:15 localhost kernel: [  112.282127] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
Mar 30 15:39:19 localhost kernel: [  128.722795] cdrom: This disc doesn't have any tracks I recognize!
Mar 30 16:52:31 localhost kernel: [ 4518.340196] cdrom: This disc doesn't have any tracks I recognize!
Mar 30 16:54:45 localhost kernel: [ 4652.364303] loop: loaded (max 8 devices)
Mar 30 17:17:02 localhost /USR/SBIN/CRON[16414]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar 30 17:39:15 localhost -- MARK --
Mar 30 17:52:22 localhost kernel: [ 8107.704988] cdrom: This disc doesn't have any tracks I recognize!
Mar 30 19:07:50 localhost kernel: [12634.084032] cdrom: This disc doesn't have any tracks I recognize!
Mar 30 19:17:02 localhost /USR/SBIN/CRON[5208]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar 30 20:04:40 localhost kernel: [16041.617784] cdrom: This disc doesn't have any tracks I recognize!
Mar 30 20:18:50 localhost kernel: [16891.540883] cdrom: sr0: mrw address space DMA selected
Mar 30 20:18:50 localhost kernel: [16891.549365] cdrom open: mrw_status 'not mrw'
Mar 30 20:18:50 localhost kernel: [16891.930641] cdrom: sr0: mrw address space DMA selected
Mar 30 20:18:50 localhost kernel: [16891.939628] cdrom open: mrw_status 'not mrw'
Mar 30 20:18:51 localhost kernel: [16893.032980] Unable to identify CD-ROM format.
[/COLOR][/I]
 
multicdrc (as amended):
[COLOR="Blue"][I]# Dan Born
# [email]dan@danborn.net[/email]

# ***************************************************************************
# MY WARNING - THIS PROGRAM TAKES ABOUT 35 MINUTES TO MAKE ONE DISK FILE
# PLUS THE TIME TAKEN TO BLANK THE CD-RW AND THEN WRITE THE DISK. 
# IN ROUND NUMBERS YOU COULD BE TALKING AROUND 3HRS FOR THE WHOLE BACKUP!!
# NOTE THAT BACKUP FILES CREATED AS ROOT WILL THEREFORE GO INTO ROOT'S
# WASTE BIN AT /root/.Trash AND NOT INTO THE MAIN ONE.
# YOU SHOULD ALSO USE BLANK OR REFORMATTED CDs - RELYING ON CDRECORD TO BLANK
# THEM LEADS TO PROBLEMS. USE GRAVEMAN - OTHER OPERATIONS - FULL ERASE
# ***************************************************************************

# See [http://danborn.net/multicd/](http://danborn.net/multicd/) for documentation, information
# about usage, and how to configure multicd on your system.

# This is a sample configuration file for my multicd program.  Everything that
# is configurable about my program is listed here.  You'll want to make sure
# you change these to useful values for your system.

# All file paths must be absolute.  No relative path names.
# If a line contains a "#", everything after that is a comment.

# Options in the global config file are overridden by options in a user's
# config file, which can both be overridden by command line options.

# Command line options have the same name as their name in here.  Boolean
# options don't need a value on the command line.  For booleans, if the option
# appears, true (or enabled) is assumed.
# Examples:
# multicd --files /home /etc /usr/local --exclude /home/httpd --only_one
# multicd --files / --exclude /tmp /dev /proc --multi

# NOTE: If you are a user of a previous version of multicd, it is important
# to note that the use of image_dir is no longer supported.  Image file
# locations are now specified by giving the full path to the name of the
# image file by using image_file1 and image_file2.

# Turns on multithreadedness.  This will cause the files for the next CD image
# to be copied while the current one is still burning.  0 to disable this, 1
# to enable it.
multi = 0

# If this is enabled, then multicd will run in a non-interactive mode.  It
# will fit all of the files it can onto a single CD image, assume that a
# disc is in the writer, burn the CD, and then quit.  1 to enable this, 0
# to disable it.  You can assume that enabling this disables any
# multithreading.
only_one = 0

# Tell multicd where to put and what to name the image file.  After a CD
# has been burned from a given image file, a new file system is created on the
# image file and it is reused for the next set of data.  This is much better
# than deleting the old image file and creating a new one, because creating
# image files usually takes a long time.
# Required field.
image_file1 = /var/tmp/multicd_image1

# If multi is enabled, a second image file is required.
image_file2 = /var/tmp/multicd_image2

# The mount point for the image file while files are being copied to it.
# Required field.
image_mount = /var/tmp/multicd_image_mount

# The size of the image file to create.  Can be specified in terms of
# megabytes, kilobytes, or bytes.
# Examples:
# 4G          # Use a "G" for gigabytes.
# 650M        # Use an "M" for megabytes.
# 665600K     # Use a "K" for kilobytes.
# 681574400   # Don't use any letter for bytes.
# Required field.
cd_size = 650M

# Files larger than this will not be copied to the CD.  This value needs
# to be smaller than cd_size, but exactly how much smaller depends on
# the filesystem type used on the CD.  Rather than trying to guess this
# myself, or put an arbitrary number in the code, I'm leaving it up to
# the user.  620M/650M should be pretty safe, but maybe too
# conservative.
maxfile_size = 620M

# Type of file system to create on the backup CDs.  This will probably
# be expanded to include other filesystem types in the future.
# Required field.
fs_type = ext2

# Extra options to give to mkfs.  The options shown here apply to
# the default filesystem type of ext2 shown above.  -m 0 means
# reserve 0 space for root, -q means quiet, and -F forces file
# system creation on an image file.
# If you wish to use multicd to burn DVDs, try:
#   mkfs_opts = -m 0 -q -F -b 2048
mkfs_opts = -m 0 -q -F

# List of files to backup.
# Example: files = /home /etc /usr/local "/home/joe smith"
# Note: In the config file, you may use double quotes with the files and
# exclude options for files that contain spaces.
# Use a dash to indicate that a list of files, one per line, should be
# read from stdin.
files = /

# Alternative to "files" option.  Specify a text file with files listed one
# per line.
# One of either files_list or files is required.
# files_list = /tmp/myfiles.txt

# This sets the type of compression to use, if any.  Each file in the
# backup set will be compressed and renamed to end in either .gz,
# .bz2, or .z, depending on the type of compression.  Set to 0 for no
# compression, 1 for gzip, 2 for bzip2, and 3 for compress.
compress = 1

# Set the compression level.  The gzip program defaults to 6, bzip2
# defaults to 9, and compress doesn't support levels.  See the man
# pages for gzip and bzip2 for details.  Leave this option blank to
# use the default.
compress_level = 6

# List of files to exclude from the list given for files above.
exclude = /dev /lost+found /mnt /proc /tmp /usr/tmp /var/tmp /home/michael/Backup /root/.Trash /michael/.Trash

# Alternative to "exclude" option.  Speciify a text file with files listed
# one per line.
# exclude_list = /tmp/excludes.txt

# This is how cdrecord should be run.  multicd will append the name of
# the image file to burn to the end.  Any output cdrecord produces is
# sent to STDERR.
# Required field.
# ******************************************************************************
# MY NOTE - LEAVE OUT blank=fast IF USING CD-Rs WHICH OF COURSE CAN'T BE BLANKED
# YOU CAN ALSO LEAVE OUT -v WHICH IS TELLING CDRECORD TO BE VERBOSE
# IF IT DOESN'T LIKE blank=fast TRY blank=all
# COULD ALSO TRY cdrecord = sudo cdrecord ...ETC, TO AVOID PERMISSION PROBLEMS
# THO SHOULD BE RUNNING AS ROOT ANYWAY
# COULD TRY LEAVING dev OUT AS SYSTEM WILL WORK IT OUT ANYWAY...
# DITTO SPEED=4, SYSTEM TRIES 24 LEFT TO OWN DEVICES
# SCAN APPEARED TO SHOW DEVICE WAS 0,0,0
# (HAVE ALSO SET CDRECORD FILES TO set user id (SUID) BY TICKING BOX)
# IE FOR CD-RW PUT
# cdrecord = cdrecord -v blank=fast dev=-2,-2,-2 -data
# OR FOR CD-R PUT
# cdrecord = cdrecord -v dev=0,0,0 -data
# ******************************************************************************
cdrecord = cdrecord -v dev=0,0,0 blank=fast -data

# You can use this to specify a command to run after each CD is done
# burning.
# The example shown simply opens the CD tray, but you could configure
# it to run a command that plays a sound, or both ejects and plays a sound,
# like this: cd_done = eject /dev/cdrom; cat cdsound.wav > /dev/dsp
# cd_done = cdrecord dev=0,0,0 -eject
cd_done = eject /dev/cdrom1 

# Yet another mode of operation.  If enabled, then multicd will create as
# many image files as it needs to backup all of your files.  It won't burn
# any CDs, just create a bunch of image files.  For the image file names it
# will use the image_file1 value followed by the CD number.
# 1 to enable, 0 to disable.
noburn = 0

# Another way to speed things along.  If this is enabled, then it is
# assumed that the first disc for burning is already in the drive.  The
# first CD will be burned automatically without prompting the user to put a
# disc in, but all discs after the first will be prompted for.
first_disc = 0

# multicd normally starts out with blank CDs before it begins copying
# files.  With this option enabled, multicd will save a copy of all the
# files on the current CD, and add the new ones to it.  1 to enable, 0 to
# disable.
addfiles = 0

# If specified, only backup files that have been modified since the
# time specified.  Use d, h, m, and s to give units in days, hours,
# minutes, and seconds.
#since = 2d 4h 3m 18s

# If addfiles is enabled, then the rewriteable CD will need to be mounted
# and have files copied from it.  cd_dev and cd_mount are needed only when
# addfiles is enabled.  cd_dev is the device file for you cd burner.
cd_dev = /dev/scd0


# cd_mount is needed when addfiles is enabled.  This is where the
# rewriteable CD should be mounted in order to read files from it.
cd_mount = /mnt/cdrom1

# If this option is specified, an index file is created at the given
# location.  Otherwise, no index file is created.
# An index file is a simply a plain text file with a list of the files
# on each CD.  This helps in determining which CD a file can be located on.
# You can include %d to have the date and time be part of the file name.
index_file = /var/tmp/multicd_index_%d

# If check_config is set to 1, multicd will check to see if it has a valid
# configuration, and then exit without doing anything.
check_config = 0

# This is here because people often expect to be able to give a --help option
# on the command line.  If set, program prints a message and then exits.
help = 0
[/I][/COLOR]

I get the feeling that this may be a cdrecord problem rather than a multicd problem, that is that the command being given to cdrecord may not be right, but I could be wrong?

The CD writer has successfully written and read in the past. Usually I use it with Graveman and there isn't a problem.

Michael

---

### Post by PaulchenPanther on 2006-08-22
Hi,

here's what worked for me:

According to my ~/.multicdrc, multicd creates an ext2 filesystem on the CD-ROMs. Since this is highly unusual, most automounters will not recognise the CD-ROM properly. Manual mounting works, though:

> sudo mount /dev/scd0 /media/cdrom0 -t ext2 -r

Hope this helped.

Paul

---

### Post by grimdestripador on 2006-12-07
I spent hours trying to find out why they weren't burning correctly. Producing unreadable discs. Apparently, they were readable, just the automount doesn't work just like Paul said. 

If found out the hard way that these are non-standard iso (not an iso9660 or udf). and can't be burned... well, at least with K3b or the gnome default settings... 

Multicd is a program which does a backup into disc readable format. Similear to how iTunes allows one to burn their entire collection of music to cd after cd, without more user intervention than just swapping cds.

The default settings in the config file (/etc/multicdrc), errors when it reaches to cdrecord if you don't disable the "blank=fast" command.

But still it burns to ext2 format... your options are

1)mount the CD manually 
(check /etc/fstab for device paths) after burning with multicd normally.

```
sudo mount /dev/scd0 /media/cdrom0 -t ext2 -r
```

> The Downside:
This is obviously unreadable to windows. 


2)Start two terminal sessions, run "sudo multicd" in one, and use the other for manually handling the cd when it prompts you to Skip,Continue,Quit. After you run the following commands, press skip cd, and proceed to the next, repeating as necessary.

Mount manually
```
sudo mount /var/tmp/multicd_image1 /var/tmp/multicd_image_mount -t ext2 -o loop
```


Make iso manually (publically readable with joulet)
```
sudo mkisofs -r -J -o /var/tmp/multicd1.iso /var/tmp/multicd_image_mount
```

or for a windows friendly CD
```
sudo mkhybrid -r -J -o /var/tmp/multicd1.iso /var/tmp/multicd_image_mount
```

or for a windows friendly CD that allows filenames to be 130 or so characters.
```
sudo mkhybrid -r -joliet-long -o /var/tmp/multicd1.iso /var/tmp/multicd_image_mount
```


Burn manually at terminal (ONLY A CD)
```
sudo cdrecord -v speed=32 dev=0,0,0 driveropts=burnfree -dao -eject /var/tmp/multicd1.iso
```

or Burn manually with setting permissions and right clicking.
```
sudo chmod 777 multicd1.iso
sudo chown $USER multicd1.iso
(replace $USER with your username)
```

> The Downside:
Who knows what happens to longer than allowed filenames.


I hope this has been helpfull. I use this to backup just about everything I got. I set the disc to be 4350M and burn it to a DVD with no problems. Just make sure you have 10Gb spare on your root file system.

---

