---
title: "CD burning hangs every time"
date: 2006-07-05
forum: Desktop Environments
---

### Post by atenlaugh on 2006-07-05
Hey, 

I have tried various CD-burning programs and every time the process 'hangs' before it even starts burning the disc. The drive is an ASUS DVD+R (DRW-1608P2), and none of the programs really give any sort of error message. It just...hangs there.

---

### Post by atenlaugh on 2006-07-08
Nobody has any idea?

---

### Post by Viper666 on 2006-07-09
never seen this before... i always use gnomebaker and it works fine. Does the system also hang?

---

### Post by cotcot on 2006-07-09
Have you tried K3B ? I had the same some time ago (on Ubuntu 5.04) and got it working with k3b.

---

### Post by JohnBoy55 on 2006-07-09
If you have multiple OS bootup options, you might try booting the computer (with the same hardware complement) up in micro$oft windows. Then try to do a burn. If it works, you may be dealing with a linux driver compatibility issue with your burner. If it doesn't work, you may be dealing with a defective burner or a system BIOS compatibility issue with your burner. Might I suggest you beg or borrow another type/brand of burner from a friend for testing. Try burning with theirs. Obviously, if it works then get another burner to replace yours.

---

### Post by atenlaugh on 2006-07-09
Viper, the system doesn't hang, just the burning process.

JohnBoy, it works fine in Windows. That said, it's strange, because it detects the burner perfectly, and it "green-lights" all of the correct burning options for the drive (CD-R, DVD-R, so on). So it seems to DETECT it fine. Options specifying it show up everywhere. Is there a list with drives that are known to work, or do I just have to guess or steal one from a friend? 

I'll see if K3b works; Nautilus, Gnomebaker, and Serpentine haven't worked, however. We'll have to see.

Update: K3b doesn't work either. The drive starts spinning, like it's ready, and it says "Starting SAO writing at xx speed...", and goes nowhere from there.

---

### Post by orb9220 on 2006-07-09
You said you have tried prorams does that include the built-in right click copy disc command?

---

### Post by yuv on 2006-07-09
The drive is an ASUS DVD+R (DRW-1608P2), so I asume that you want to burn a DVD and if I am right than you have some work to do, but you can solve it for sure. You have to enable the DVD burn and install cdrecord-ProDVD (do not forget to install the key for personal use too).

---

### Post by atenlaugh on 2006-07-09
I have tried right-clicking to burn, which acts more or less as the others have. 

> **yuv said:**
> The drive is an ASUS DVD+R (DRW-1608P2), so I asume that you want to burn a DVD and if I am right than you have some work to do, but you can solve it for sure. You have to enable the DVD burn and install cdrecord-ProDVD (do not forget to install the key for personal use too).

That would be fine, except that I can't burn CD's, either, which is what I PRESENTLY want it for (though DVD-burning would be great, too, so thank you)!

---

### Post by atenlaugh on 2006-08-26
Short story: Bump. 

Long story: It's been a few weeks, and I still haven't been able to get it to budge. By now I know that it's definitely not because of any individual application (I've tried most of them), and being new to all of this, I'm not sure what to do from here, except just use Windows each time I want to burn a CD or DVD. Which is fine, just not ideal. :)

Edit: Here, something finally happenned, but it's really weird...I tried to burn a CD through Banshee, and nothing happened, but I let it go for a little while. I came back, restarted the computer, and there was a CD on the desktop, mounted! However, when I went to open it, and access a file, everything locked up, like the pre-information for the data was there, but there wasn't actually anything there. As if. I don't know.

---

### Post by atenlaugh on 2006-09-27
Breakthrough! Sort of. 

I fixed it by upgrading to Edgy. Just tried burning a CD, and it works fine. I can't complain.

---

