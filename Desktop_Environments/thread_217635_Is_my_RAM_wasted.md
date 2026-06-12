---
title: "Is my RAM wasted?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Loffe_ on 2006-07-17
Hello folks!

Sorry for the long post, but I thougt I had to give a proper explanation.

I have a big problem. The other day I tried out Windows Vista Beta. It all worked, but I think it froze once or twice. But that is what you are prepared of in a beta...

However, back in Ubuntu I now get random hard locks:confused: . The computer just freeze. Normally I run XGL but the standard gnome session frooze too.

Maybe it's a hardware problem I thought, disconnected all usb devices LAN, etc. But it still hung up on some occasion.

I also tried disconnect the secondary harddrive (the one with Vista). The problem grew worse. Now the machine didn't reach GRUB. It halted on the first screen. Before checking for harddrives...

I removed half of my RAM and now it worked. I connected all stuff again (not the RAM) and the machine ran fine.

I also ran Memtest86+ and it gave me no errors with only one memory module. However when I put the second one the it found a lot of errors( >7 million) ](*,) 

Is my memory totaly wasted?

How could this happen? I have not opened the case for the last 4 month or so... RAM just doesn't break, does it?

Is there anyone else who have had the same problem?
What should I do? Is there usually any warranty on memory modules? I can't understand it just broke...

I am a little suspicious of that a thing called Vista is involved. It is the only major thing I've done with the computer lately... But can an OS break your hardware? If it can Microsoft should not have released a public "waste your hardware" beta. That would just be stupid...

My specs:
AMD 64 X2 4200+
Kingston ValueR. PC3200 DDR-DIMM 2048MB Kit w/two matched ValueRAM 1024MB (I think)
ATI Radeon x800

Thanks
Loffe

---

### Post by Lunar_Lamp on 2006-07-17
There is probably a warranty on the RAM, though depending on when you bought it, it may have expired - check it out with your manufacturer.

---

### Post by az on 2006-07-17
If one stick has different timing than the other, you can see errors like that.  Sometimes, changing the order in which they are installed can fix the problem.

Sometimes, a motherboard will only look at the first stick to decide the timings and not look at the slowest stick and use it's.

Also check your bios settings for ECC and other ram variables, as applicable.

---

### Post by x64Jimbo on 2006-07-17
> **azz said:**
> If one stick has different timing than the other, you can see errors like that.  Sometimes, changing the order in which they are installed can fix the problem.

Sometimes, a motherboard will only look at the first stick to decide the timings and not look at the slowest stick and use it's.

Also check your bios settings for ECC and other ram variables, as applicable.
None of this should have changed. The box hasn't been opened. I'd say the RAM is bad.

---

### Post by Loffe_ on 2006-07-17
> **Lunar_Lamp said:**
> There is probably a warranty on the RAM, though depending on when you bought it, it may have expired - check it out with your manufacturer.

I'll check the warranty. Bought the computer half a year ago. THe warranty should not have expired I think.

What can the reason be behind this? Is it just giving up without reason?

Is there anyway I can blame Vista for this? :p That was the only change I made to the computer when it began the crashing...

Thanks
Loffe

---

### Post by x64Jimbo on 2006-07-17
> **Loffe_ said:**
> I'll check the warranty. Bought the computer half a year ago. THe warranty should not have expired I think.

What can the reason be behind this? Is it just giving up without reason?

Is there anyway I can blame Vista for this? :p That was the only change I made to the computer when it began the crashing...

Thanks
Loffe
Vista is putting a new power management system into play, and that is the only way I could see an operating system damaging hardware. You might file a complaint with Microsoft. Who knows? They've got so many complaints against them and so much negative publicity that they might just buy you a new stick of RAM just to shut you up. ;)

---

### Post by philippe_carlo on 2006-07-17
Vista does have high performance requirements. Maybe it pushed your hardware beyond some limits, triggering some latent problems. You seem to be sure that you memory is broken, but could it not be one of the memory busses too?

---

### Post by Loffe_ on 2006-07-17
> **philippe_carlo said:**
> You seem to be sure that you memory is broken, but could it not be one of the memory busses too?

You've got a point... The machine worked when removing one of the ram-sticks, and then I guessed that the one I removed was broken...

I'll make try placing the "broken" one int the slot I know is working...

//Loffe

---

### Post by Loffe_ on 2006-07-17
The "bad" ram didn't work in the other slot either. It looks like the ram stick is dead...

Thanks
Loffe

---

### Post by philippe_carlo on 2006-07-17
At least that's good news in terms of costs. Weird story, though.

---

### Post by x64Jimbo on 2006-07-17
> **philippe_carlo said:**
> At least that's good news in terms of costs. Weird story, though.
Heh. One more reason I won't be installing Vista in anything but a virtual machine. ;)

---

### Post by lindyslack on 2006-07-17
Kingston memroy (even ValueRAM) has a lifetime warrenty.

[http://www.kingston.com/company/warranty.asp](http://www.kingston.com/company/warranty.asp) - Check out the details at this link

---

### Post by jgcamp99 on 2006-07-17
"Is there anyway I can blame Vista for this?"

Sure go ahead, blame Vista, but you'll have to RMA your memory for it's lifetime warranty. That much is coming out of your own pocket for S&H. They should be able to cross ship it for you. They'll probably charge your credit card and credit it back when you return the bad memory stick.

---

