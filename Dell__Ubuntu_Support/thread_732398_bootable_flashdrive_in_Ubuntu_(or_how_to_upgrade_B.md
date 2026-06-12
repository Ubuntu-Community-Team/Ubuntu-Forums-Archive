---
title: "bootable flashdrive in Ubuntu (or how to upgrade BIOS on Dell Inspiron 530)"
date: 2008-03-22
forum: Dell  Ubuntu Support
---

### Post by motoperpetuo on 2008-03-22
so, my inspiron 530 with ubuntu preinstalled arrived last night and i was all excited to have a computer designed for linux and to not have to deal with a bunch of hardware and BIOS compatibility problems like i have on most computers i've set up linux on. granted, i learned a lot by resolving (most of) those problems, but i was looking forward to having something just work this time around.

well, no luck with that. ubuntu works great, but i can't get most of the linux live CDs i use (gparted, clonezilla, puppy linux, the linux mint install CD) to boot correctly. it's very, very frustrating and prevents me from doing a large part of what i wanted to do with this computer. however, i've posted about it elsewhere on this forum ([http://ubuntuforums.org/showthread.php?t=731569](http://ubuntuforums.org/showthread.php?t=731569)) and the mint forum, so i won't go into details.

anyway, one thought i had was to try updating my BIOS. it looks like there's a more recent BIOS available at  

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R181000&SystemID=INSP_DSKTP_D530&servicetag=96SMXF1&os=BIOSA&osl=en&deviceid=14390&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=246767](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R181000&SystemID=INSP_DSKTP_D530&servicetag=96SMXF1&os=BIOSA&osl=en&deviceid=14390&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=246767)

but, not surprisingly, it's a DOS/Windows executable. the dell site says that non-windows users need to copy the file to a DOS bootable flashdrive and run it from DOS. has anyone here ever done this? i've been looking around for detailed instructions but haven't found anything yet. i think i'm up to six hours or so of unsuccessful efforts to get this computer to boot a gparted cd now. any help would be awesome...ty.

---

### Post by kioftes on 2008-03-23
This reminds me of old times:-) I believe you can try out a boot disk image from this site

[http://www.allbootdisks.com/download/dos.html](http://www.allbootdisks.com/download/dos.html)

put it in your usb stick and boot from there....Good luck!

---

### Post by motoperpetuo on 2008-03-23
> **kioftes said:**
> This reminds me of old times:-) I believe you can try out a boot disk image from this site

[http://www.allbootdisks.com/download/dos.html](http://www.allbootdisks.com/download/dos.html)

put it in your usb stick and boot from there....Good luck!

i appreciate the response, and i'll probably use one of these images once i figure out how to make the flashdrive bootable. that's the main problem i'm having. can anyone help me with that?

---

### Post by WCD on 2008-03-24
If you want to go the flash drive route check this out [http://gentoo-wiki.com/HOWTO_Create_a_DOS_boot_USB_flash_drive](http://gentoo-wiki.com/HOWTO_Create_a_DOS_boot_USB_flash_drive).  You might also want to consider this approach [https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS).  Let me know how it works out.  I just order the same machine.

---

### Post by motoperpetuo on 2008-03-24
> **WCD said:**
> If you want to go the flash drive route check this out [http://gentoo-wiki.com/HOWTO_Create_a_DOS_boot_USB_flash_drive](http://gentoo-wiki.com/HOWTO_Create_a_DOS_boot_USB_flash_drive).  You might also want to consider this approach [https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS).  Let me know how it works out.  I just order the same machine.

i finally figured out how to make the DOS bootable USB key. unfortunately, the BIOS update didn't work. it errored out with the cryptic message "Error! udosexe = -5".

i might try the second link you posted. it looks like it might be geared specifically towards updating the BIOS on a Dell computer running Linux.

i have to say that i'm pretty frustrated with this computer so far. when you get yours, could you post back and tell me what you think, if it's not too much trouble? i'm specifically interested to see if you're able to get CDs like gparted or puppy linux to boot. who knows, maybe my computer is just a lemon.

---

### Post by prinknash on 2008-03-24
If you've got an Inspiron 530n series (i.e. Dell Inspiron 530 which comes with Ubuntu loaded and no Windows) I'm not sure there IS a BIOS update available yet. I think the update advertised on the Dell site is for the Inspiron 530 or 530S. Certainly, when you check the SystemId (0x020D) against the Dell list of available BIOS headers, no update is mentioned.

p

---

### Post by motoperpetuo on 2008-03-25
> **prinknash said:**
> If you've got an Inspiron 530n series (i.e. Dell Inspiron 530 which comes with Ubuntu loaded and no Windows) I'm not sure there IS a BIOS update available yet. I think the update advertised on the Dell site is for the Inspiron 530 or 530S. Certainly, when you check the SystemId (0x020D) against the Dell list of available BIOS headers, no update is mentioned.

p

the BIOS update did come up when i entered my service tag number. however, i suppose that's not a guarantee that it's actually for my system. the update method the dell site suggests, running the update .exe from a DOS bootable flashdrive, doesn't work, so i wouldn't be surprised if the update itself isn't actually correct for my system.

although, it just occured to me that maybe i need to run the update from a windows 9x boot floppy (or a flashdrive that emulates one). when i was talking to dell support last night, the tech mentioned something about the executable being for windows and not DOS.

---

