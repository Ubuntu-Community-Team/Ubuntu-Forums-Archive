---
title: "GRUB2 requires &quot;press any key to continue&quot; for failed HD search"
date: 2012-07-30
forum: Desktop Environments
---

### Post by kernal42 on 2012-07-30
I have a GRUB2 menu item which looks for a particular hard drive by UUID.  If the drive is present, GRUB2 boots into one operating system (Windows).  If the drive is not present, GRUB2 boots into another instead (Ubuntu).  I check to see if the drive is attached with "search --fs-uuid --no-floppy --set=foo $foo_uuid".  This all works correctly.

The problem I encounter is that if search is unable to find the drive in question, it requires me to press a key to continue.  This is not a desired effect - I make this check specifically so I will not have to provide further input.  

Is there a way to bypass the "press any key to continue..." statement?  Is there a different way to determine the presence of the drive that will not require keyboard input upon failure?  

My goal here is to have a hardware switch to designate the OS to boot into so I don't accidentally miss the GRUB menu and therefore need to reboot.  The switch connects or disconnects a flash drive from the computer.  The hardware switch works; the script mostly works; the only hangup is the requirement to press a key to continue the boot.  

My 40_custom file:

```
menuentry "auto" {
	  set foo_uuid=2CAD-0AA8
	  set foo=empty

	  insmod part_gpt
#	  insmod vfat
	  insmod search_fs_uuid

	  search --fs-uuid --no-floppy --set=foo $foo_uuid

	  if [ $foo = "empty" ]; then
	        #boot linux
  	        recordfail
                gfxmode $linux_gfx_mode
                insmod gzio
                insmod part_msdos
                insmod ext2
                set root='(hd3,msdos4)'
                search --no-floppy --fs-uuid --set=root bc1ba5fa-971c-4a94-b808-0b28855647af
                linux   /boot/vmlinuz-3.2.0-26-generic root=UUID=bc1ba5fa-971c-4a94-b808-0b28855647af ro   quiet splash $vt_handoff
                initrd  /boot/initrd.img-3.2.0-26-generic
	  else
		#boot windows
		insmod part_msdos
		insmod ntfs
        	set root='(hd3,msdos1)'
       		search --no-floppy --fs-uuid --set=root CA3C07483C072F4F
       		chainloader +1

	  fi		
}
```

Thanks,
Kernal

---

