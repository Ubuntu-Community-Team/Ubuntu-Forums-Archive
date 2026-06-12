---
title: "BIOS update in emergency"
date: 2009-05-05
forum: General Help
---

### Post by pmla_dailha on 2009-05-05
Hello everybody,
I have a big problem with my laptop, it can no more boot from a LiveCD or USB device. I'm not an Absolute Beginner in Ubuntu (I'm rather a Absolute Beginner in English, sorry for my errors)), so I changed all options in my BIOS and it didn't work.

Yesterday I saw that my laptop can boot from a LiveCD or a USB device if I take out the hard disk. So I was thinking about the following strategy to solve the problem: 

1. burn a BIOS update-CD
2. shut the laptop down
3. take the hard disk out
4. put the BIOS update-CD in
5. start the system
6. update the BIOS (WITHOUT A HARD DISK)

Because I'm not really experienced in Ubuntu, I'm not sure if it will work, or if it will crash my BIOS. Therefore I'd like very much to know the opinion of more experienced users about my strategy!

Thanks!

Details: I don't have windows, so I believe I can't do a BIOS update with DOS.
Because I can't boot from CD, I can't use my XP Recovery CD to install Windows and do from there a BIOS Update. I can't do a normal BIOS update from CD, because the laptop doesn't boot from CD.

---

### Post by dandnsmith on 2009-05-05
> **pmla_dailha said:**
> Hello everybody,
I have a big problem with my laptop, it can no more boot from a LiveCD or USB device.  I changed all options in my BIOS and it didn't work.

Yesterday I saw that my laptop can boot from a LiveCD or a USB device if I take out the hard disk. So I was thinking about the following strategy to solve the problem: 

1. burn a BIOS update-CD
2. shut the laptop down
3. take the hard disk out
4. put the BIOS update-CD in
5. start the system
6. update the BIOS (WITHOUT A HARD DISK)

Because I'm not really experienced in Ubuntu, I'm not sure if it will work, or if it will crash my BIOS. Therefore I'd like very much to know the opinion of more experienced users about my strategy!


Taking out the hard disk won't affect the ability to boot from CD or USB.
This means (I'm sorry to say) that your whole strategy will fail.

There should be a key which you press (details depend on what laptop it is - for some it is F12) to get into a menu which can give you at least a change of boot device for this time of booting.
I hate to think what your BIOS changes will have done.

I suggest you look intently at the screen when it boots to see the message about keys to press, or look at any documententation which may tell you, or post the make and model number so somebody can confirm which key(s) will do the job.

---

### Post by pmla_dailha on 2009-05-05
dandnsmith, thank you very much for the help!

Like I said, I've already tried to boot wihout hard disk but with a LiveCD in CD-drive. It worked!

And like I also said, I tried to change the sequence of device, from which the boot should follow, but if I have the hard disk (or even a LiveUSB-device) connected to the laptop, it doesn't boot from the CD.

The vendor of my mainboard is Phoenix Technologies Ltd. and the modell is SB400.

---

