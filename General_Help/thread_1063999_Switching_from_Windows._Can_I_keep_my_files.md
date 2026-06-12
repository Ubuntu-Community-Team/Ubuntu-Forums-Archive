---
title: "Switching from Windows. Can I keep my files?"
date: 2009-02-08
forum: General Help
---

### Post by ZiggyFry on 2009-02-08
I'm switching to Ubuntu from Windows. I have two hard drives. I'm hoping to reformat my master drive, install Ubuntu and still be able to access the files on my slave drive. Would this be possible?

Sin.Ziggy.

---

### Post by howefield on 2009-02-08
Absolutely possible. Ubuntu should see your second drive and mount it in your Places menu.

If it is an ntfs drive, you might need to install ntfsprogs.

---

### Post by overlord.gaurav on 2009-02-08
Yes. It is very much possible on Ubuntu! Have a happy switching !

---

### Post by ZiggyFry on 2009-02-08
Thank you very much. I guess I'll see you on the other side :D

Sin.Ziggy.

---

### Post by issih on 2009-02-08
Keeping files is fine, but be aware that unless they are from a relatively well known program you may have trouble finding a linux program that reads them.

With a bit of fiddling just about any multimedia files (audio or video) should be fine

Any web stuff - fine

Office stuff - fine 

anything a bit more esoteric you might have issues with, but will probably be fine.

Good luck and have fun :)

---

### Post by BuntuFreak on 2009-02-08
> **ZiggyFry said:**
> I'm switching to Ubuntu from Windows. I have two hard drives. I'm hoping to reformat my master drive, install Ubuntu and still be able to access the files on my slave drive. Would this be possible?

Sin.Ziggy.

I had an NTFS drive with media. I recently put it on my Ubuntu Gutsy desktop computer. Didn't have to do one darn thing for Ubuntu to recognize it. Just make sure you know how to use ***mount***

We have to be realistic. Ubuntu is great. Ubuntu is free. But the world is still with Windows. IMO, the drive/partition on which Ubuntu is installed should be whatever format it needs to be. If you are using a hard disk purely for data, better to keep it NTFS. This way you can always take the hard disk and plop it in another computer, any computer, which will more often than likely be running Windows and recover the data.

Just my 2 cents.

P.S. If you already have a separate HD on your computer that you want to format NTFS, you'll need ***mkntfs***. Then when you use ***gtparted***, you'll get option to format NTFS. I found this most annoying because while installing Ubuntu from live CD, I can go and format my secondary HD to ntfs. But once Ubuntu was installed, ***mkntfs*** did not make it my Ubuntu installation. In fact I even had to go and get ***gtparted***. Admittedly my installation of Ubuntu is old, i.e. Gutsy Gibbon, 7.10

P.P.S. The "Trash" feature for an NTFS drive is suspect. It doesn't always seem to recover HD space. i.e. you say "move to trash" and the Trash is empty, i.e. it really did not move items to trash. But then, the more HD space doesn't get freed up! I make it a point to do Shift+Delete while removing files. So that is a potential problem you have to compensate and careful about.

---

