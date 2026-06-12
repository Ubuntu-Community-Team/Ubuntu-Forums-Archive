---
title: "Best support needed to recover data."
date: 2012-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aakash_scsa_hellyeah on 2012-09-16
Please, I need the Best Tech Guys to be working on this case.
 
Let me explain the complete story.
 
I recently bought a new DELL INSPIRON 15 R 5520
It has a 1tb Hard Drive. // now which contains all my data.
Last week I kept My laptop plugged in to charger & went away after turning on the Full Scan against viruses by McAfee Antivirus.
When I came back the system was restarted with error as "No Boot Media Found."
When I checked into BIOS, there was no Hard Drive detected. I just reported to DELL Support and they asked Me to run several Diagnostic tests and then concluded the disk to be faulty, they just simply arranged a replacement for hard drive.
The New Hard Drive doesn't matter to Me if My data is not recovered from that faulty HD.
 
Details about HD: Western Digital 1.0 TB WD10JPVT SATA 5400 RPM
There is a clicking sound comming from inside when the system tries to read this drive.
I belive it might be a problem with bad 'Reading Head' of drive or it might be related to the 'Circuit Board' of drive.
 
Now what I have done from My side :
 
1. Using SATA cable :
""
- I just pulled out the HD from laptop, and tried to read it in My desktop PC. // Again same clicking noise and no detection by BIOS as well as Windows.
- I tried detectiong it with Knoppix. // No device detected to mount.
- I tried using it in Ubuntu live mode. // Again no device detected to mount.
- In test disk Test disk. // The disk is not listed to 'Analyze'.
- Tried some RAW Partiton recovery softwares. // Again no device listed to perform check.
""
 
2. Using USB2.0 to SATA/IDE cable :
""
- In My desktop PC using Windows. // Same clicking noise.
But in Disk Management a new disk is detected, with 'not initialized' written below 'Disk2'. then I tried initializing it as MBR as well as GPT, which returned "Data Error (Cyclic Redundancy Check)".
I repeated testing in
- Knoppix. // no device detected.
- Ubuntu. // No device detected.
- Test disk & Recovery Softwares in windows. // No device listed.
""
 
3. Again using USB2.0 to SATA/IDE cable.
this time I analyzed the clicking noise during read operation of disk, that by holding the disk in inclined position i.e. 80 degrees to ground surface, the clicking noise has stopped and disk started spinning properly[/COLOR]. (If the position is changed the clicking restarts.). So i started testing it by keeping in inclined position.
""
- In windows, Disk management. // Disk detected but not initialized. This time, in front of Disk2, an allocated space of around 980 GB is also shown but not highlighted to deal with. (i.e. no option to create/edit partiotion.). When I tried initialing disk, it returned same CRC error.
- In Test disk. // Disk is listed. When I put it into analyze mode, there is an ongoing unsuccessfull attempt to read data with continuous response of '[COLOR=#ff0000]data read error at ____[/COLOR]some number (clusters I guess)___'
- Recovery Softwares. // Disk detected. But unsuccessfull tries to recover/read data.
""
 
Thats all what I have tried till now.
**I just want My data back anyhow, it doesn't matter if warranty is voided, all I need is to recover My data.**
I will give My Best Co-operation.
**Any help will be appriciatted.**
Thank You.

---

### Post by Kirk Schnable on 2012-09-17
Sometimes, when a drive is clicking, I've been able to restore at least some data using the freezer trick.

Basically, you put your drive in the freezer for a long time (overnight is fine) then put it back in your computer.

If you have a SATA\USB adapter, you can use a long USB cable and actually run the drive while it's in the freezer (this has gotten me the best results).

[http://lifehacker.com/5515337/save-a-failed-hard-drive-in-your-freezer-redux](http://lifehacker.com/5515337/save-a-failed-hard-drive-in-your-freezer-redux)

It's a temporary fix and the drive may only work for a few minutes.  Be mindful of what data you want, and be ready to get it off.

A lot of people claim this is a myth.  I have seen it work two or three times, but I've seen at least as many times where it has not been effective.

Good luck!

---

