---
title: "upgrade Dell 530n to 8.02TLS - fatal"
date: 2008-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by emlinux on 2008-05-02
Just got a new Dell 530N with Ubuntu factory installed.
Plugged it in, updated installation, then upgraded to 8.04.
Nothing else changed or added, just straight out of the box.
Now it won't fully boot the new 2.6.24 kernel.
The old 2.6.22 does boot OK (but the video driver is wrong version, get low res graphics).

The new kernel gets ATA error messages and eventually reboots.
various messages like: (sorry, can not capture them)
 ATA1 QC Timeout (Cmd-0x27), Failed to read native max address
 ATA2 STATUS (DRDY)
It cycles through trying different UDMA speeds on ATA1 through 4
then does a hard reboot.

Any ideas???

---

### Post by Aearenda on 2008-05-02
Try the RAID setting in BIOS, or all_generic_ide as explained in post 15 of this thread: [http://ubuntuforums.org/showthread.php?t=762257](http://ubuntuforums.org/showthread.php?t=762257)

---

### Post by emlinux on 2008-05-02
Changing the BIOS to Integrated Peripherials -> SATA mode to RAID worked great.


Change to RAID mode the steps are:
1. Reboot
2. Press F2 at the DELL splash screen to enter 'setup'
3. Go to the Integrated Peripherals page
4. Move to the 'SATA Mode' line and press <ENTER>
5. Select RAID and accept the change
6. Press F10

Thanks a bunch.

---

### Post by RedRat on 2008-05-05
> **emlinux said:**
> Changing the BIOS to Integrated Peripherials -> SATA mode to RAID worked great.


Change to RAID mode the steps are:
1. Reboot
2. Press F2 at the DELL splash screen to enter 'setup'
3. Go to the Integrated Peripherals page
4. Move to the 'SATA Mode' line and press <ENTER>
5. Select RAID and accept the change
6. Press F10

Thanks a bunch.

OK had this same problem with upgrading my 7.10 Ubuntu (vanilla not Dell's) with the 8.04LTS upgrade. Followed your instructions and it worked!!! Thanks much!

However, I have a question: Why does this work??? Is there something different in 8.04 then in 7.10. The thing is I don't really have a RAID system installed, so why should this work? Really curious.

BTW I checked out the thread listed above, and the explanations still do not seem to really make sense, leaving me with more questions than answers.

---

### Post by Aearenda on 2008-05-05
The setting is misnamed in the BIOS, I think. It should be 'NATIVE'. It modifies the way the BIOS presents the drives to the kernel, such that *they stop pretending to be IDE drives* for compatibility with aging operating systems that don't have drivers for the new way of working. This does two things: it works around a problem in the kernel that stops it working with these SATA drives in IDE mode; AND it makes them run faster (that's my subjective opinion, anyway). Just because the BIOS setting is called 'RAID' doesn't mean we have to use the drives as RAID drives.

---

### Post by RedRat on 2008-05-06
> **Aearenda said:**
> The setting is misnamed in the BIOS, I think. It should be 'NATIVE'. It modifies the way the BIOS presents the drives to the kernel, such that *they stop pretending to be IDE drives* for compatibility with aging operating systems that don't have drivers for the new way of working. This does two things: it works around a problem in the kernel that stops it working with these SATA drives in IDE mode; AND it makes them run faster (that's my subjective opinion, anyway). Just because the BIOS setting is called 'RAID' doesn't mean we have to use the drives as RAID drives.

OK, I have seen this explanation and it seems reasonable but it worries me nonetheless. This means either that the Ubuntu kernel or the Dell BIOS is screwed up. If so, this seems to mean trouble. If the the BIOS is screwed up and mis-named what does this mean if I did want to install RAID. If it is the kernel, then what happens down the line. In either case, it seems we may have a problem laying in wait here. 

None of these outcomes is a good way to either build a computer. Now in Ubuntu 7.10, this situation did not arise, never had the problem, so I am thinking that perhaps the error is in the kernel or on Ubuntu's side.

---

### Post by Aearenda on 2008-05-06
To proceed with setting up RAID, there would be more steps to do in the BIOS. However, I think the software RAID in Linux is just as good - this BIOS stuff is not true hardware RAID.

I do think there is a regression fault in the Hardy kernel that prevents it from identifying the drives properly when set to IDE. The all_generic_ide workaround is mentioned in the Release Notes, if I recall correctly. There are several similar bugs in Launchpad about this kind of problem.

---

