---
title: "Recover broken hard drive?"
date: 2009-05-10
forum: General Help
---

### Post by Potters Son on 2009-05-10
I know that this doesn't have much to do with Ubuntu, but I'm hoping that people will be able to help me regardless.

Yesterday, Ubuntu froze on me. (Apparently, such a thing is possible; I've actually had it happen to me several times since upgrading to Jaunty.) I was tired, so I got really mad at my laptop and brought my fist down--right over where the hard drive was. At that moment, the hard drive started making noises: two tones at the same frequency followed by another a fourth step up and a quarter rest (to describe it musically), and the pattern repeats six times.

I force shut down the computer, and the sound stopped immediately. I turned it back on, and the same musical sequence continued through the BIOS screen. Then the computer said "Operating System not found" and couldn't boot to GRUB.

I had the BIOS try to run a hardware diagnostic, but it came back with an error message "No IDE device found" or something like that.

I'm convinced that *something* in my hard drive is shot. I removed it and put it in an external enclosure, and when I plugged it in to another computer, it started to make the same buzzing noises.

This is both a good thing and a bad thing. It's a good thing because I know that the computer itself is OK. I could just buy a new hard drive. But this is a bad thing because all my data is on there, and I haven't run a backup for months. :(

I got the laptop from Best Buy, meaning I have it under warranty from Geek Squad. But I'm worried that data recovery isn't included in my policy, and even if it is, they probably wouldn't think to look in my ext3 partitions.

Which brings me to my problem: Can I get the data off the HD myself? I remember seeing on CSI or Numb3rs a way of taking an identical hard drive, opening them both up, and swapping the platters. How hard is this to do? Can I do it?

Thank you in advance for any help.

---

### Post by JonLittle on 2009-05-10
Here is a link on how to swap hard drive platters: [http://www.wikihow.com/Swap-Hard-Disk-Drive-Platters](http://www.wikihow.com/Swap-Hard-Disk-Drive-Platters)

I would read the tips first and try the freezing method. 

Just a caution, if you are not sure you can do it, don't. It would be better to take it to some one who has experience(maybe you do, but since you asked how to I am assuming you don't have experience with hard drive guts)

Good luck.

---

### Post by DeMus on 2009-05-10
> **Potters Son said:**
> I know that this doesn't have much to do with Ubuntu, but I'm hoping that people will be able to help me regardless.

Yesterday, Ubuntu froze on me. (Apparently, such a thing is possible; I've actually had it happen to me several times since upgrading to Jaunty.) I was tired, so I got really mad at my laptop and brought my fist down--right over where the hard drive was. At that moment, the hard drive started making noises: two tones at the same frequency followed by another a fourth step up and a quarter rest (to describe it musically), and the pattern repeats six times.

I force shut down the computer, and the sound stopped immediately. I turned it back on, and the same musical sequence continued through the BIOS screen. Then the computer said "Operating System not found" and couldn't boot to GRUB.

I had the BIOS try to run a hardware diagnostic, but it came back with an error message "No IDE device found" or something like that.

I'm convinced that *something* in my hard drive is shot. I removed it and put it in an external enclosure, and when I plugged it in to another computer, it started to make the same buzzing noises.

This is both a good thing and a bad thing. It's a good thing because I know that the computer itself is OK. I could just buy a new hard drive. But this is a bad thing because all my data is on there, and I haven't run a backup for months. :(

I got the laptop from Best Buy, meaning I have it under warranty from Geek Squad. But I'm worried that data recovery isn't included in my policy, and even if it is, they probably wouldn't think to look in my ext3 partitions.

Which brings me to my problem: Can I get the data off the HD myself? I remember seeing on CSI or Numb3rs a way of taking an identical hard drive, opening them both up, and swapping the platters. How hard is this to do? Can I do it?

Thank you in advance for any help.


Did you try to boot from a live CD and see if you can get to your data this way? Not all of the disc has to be broken. Maybe some parts are still reachable. Just try it.

---

### Post by Potters Son on 2009-05-10
I seriously doubt that a LiveCD can help; if the BIOS doens't know the HD exists, I don't think the LiveCD will.

---

