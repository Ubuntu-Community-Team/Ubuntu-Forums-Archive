---
title: "HP Spectre X360 freezes on boot"
date: 2019-08-16
forum: Desktop Environments
---

### Post by pdzwig on 2019-08-16
I recently bought a SpectreX360. I am trying to get it to run Ubuntu 18.04 (without Windows, ie no dual-boot) but keep encountering problems withthe system freezing.
  
 To be specific I  go to install 18.04 from a USB 3.1 drive; initially I ran the "Try Ubuntu" bit to check things are OK; it works fine (I can get a terminal up, run gedit and so on). I then move to installing Ubuntu on the system. It goes through the whole thing and  gets to restart. When I move the pointer over the restart button,  it goes grey andt nothing happens for a while.
  
 Eventually it comes back with :
  
 [      0.234618] ACPI BIOS ERROR (bug): Failure creating [\_SB.PCIO.XHC.RHUB.SS08_UPC], AE_ALREADY_EXISTS (20181213/dswload2-324)
 [      0.234618]ACPI_ERROR: AE_ALREADY_EXISTS, During name lookup/catalog (20181213/psobject-221)
  
 it then repeats the same for SS09, SS10
  
 Then it gives
  
 [ OK] Started Holds Snappy demon refresh
 Mounting Mount unit for core, revision  7270...
 [OK] Mounting Mount unit for core, revision  7270...
 [1704.836015] VFS: busy inodes on changed media or resized disk sda
 then a lot of messages relating to systemd-shutdown
 then a message:
 exiting kvm: exiting hardware virtualisation
  
 Then hangs with a flashing "_". It took about two hours to get this far!!
  
 If I try to boot from the copy that has been installed to my hard disk (by the "install Ubuntu" process)  I get the normal splash screen and login, it then goes to the usual purple(-ish) screen with a pointer that no longer responds to the touchpad.
  
  Re-booting doesn't help, I have tried another USB stick - that doesn't fare any better, as I said earlier booting from the disk (SSD) doesn't help. WHAT is going on.
  
  
 To be more explicit about the hardware it's a 15-df1010na  (i7-9750H  6-core  +16GB + 1TB SSD + NVIDIA GTX1650). Should be more than up to it handling Ubuntu.

I should add that I am typing this on a 7 year old Pavilion that runs  Ubuntu and has the same structure that I am trying to replicate on the  Spectre. Grub here is identical to that on the Spectre. I have run Ubuntu on my last four HPs without this much hassle.

Legacy boot is enabled

HELP!! I would be grateful for any help you can offer.

---

