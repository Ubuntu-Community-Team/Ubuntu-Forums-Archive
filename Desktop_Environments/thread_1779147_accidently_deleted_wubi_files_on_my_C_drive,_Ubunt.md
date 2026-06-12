---
title: "accidently deleted wubi files on my C: drive, Ubuntu won't boot!"
date: 2011-06-10
forum: Desktop Environments
---

### Post by penn919 on 2011-06-10
Hi,

A while back I was cleaning out what I thought to be unnecessary files from the root directory of my Windows 7 drive because I noticed that there were quite a few remnants from my previous XP installation which must of came from the Windows easy transfer I had performed. Anyways, I can't boot into Ubuntu anymore so I suppose it had something to do with some of the files I deleted. At first I was getting the following error prompt screen:

[IMG]https://lh3.googleusercontent.com/-NUZinHmK2DA/TfGvHSHYqtI/AAAAAAAAM1E/U--zKgtJoIg/s400/Pic_0607_001.jpg[/IMG]

After doing some research, I found out that I could access the missing files on my ubuntu drive which are located in the winboot folder. When I transferred them over to my C: drive and rebooted I was at least able to get to the GNU grub screen and after selecting the top entry it appeared to be loading as usual, but then I got this message:

"Alert /host/ubuntu/disks/rootdisk does not exist. Dropping to a shell!"

...and then a shell prompt appears. Any ideas how I can fix this? I don't know If it makes any difference, but my Ubuntu installation is on an external hard drive.

---

### Post by penn919 on 2011-06-10
Ideas? Anyone?

---

### Post by penn919 on 2011-06-10
:-\"

---

### Post by bcbc on 2011-06-10
Can you boot an ubuntu cd and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")?(Make sure the external is plugged in).

It's a little strange, because the grub menu comes from the root.disk, so it's obviously there.
Maybe the drive number has changed though.

Do this when you see the grub menu:
1. Hit 'e' on first entry and look for the line starting "linux /boot/vmlin..." and report what the part "root=/dev/sdXY" says.
2. Hit ESC to go back to the menu
3. Hit 'c' to go to a grub command line
4. Enter the following and write down the result:
```
search -s -f -n /ubuntu/disks/root.disk
echo $root
```
5. To reboot enter:
```
reboot
```

Report back on what you found.

---

### Post by penn919 on 2011-06-10
> **bcbc said:**
> Can you boot an ubuntu cd and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")?(Make sure the external is plugged in).

It's a little strange, because the grub menu comes from the root.disk, so it's obviously there.
Maybe the drive number has changed though.

Do this when you see the grub menu:
1. Hit 'e' on first entry and look for the line starting "linux /boot/vmlin..." and report what the part "root=/dev/sdXY" says.
2. Hit ESC to go back to the menu
3. Hit 'c' to go to a grub command line
4. Enter the following and write down the result:
```
search -s -f -n /ubuntu/disks/root.disk
echo $root
```5. To reboot enter:
```
reboot
```Report back on what you found.


Well, here's the Results.txt content I got from the bootinfoscript you referred me to:

[http://pastebin.com/1LnSSSg4](http://pastebin.com/1LnSSSg4)

I'll report on the other stuff in short while since I've got to restart my computer from the Ubuntu live session which I'm in now.

---

### Post by penn919 on 2011-06-10
Alright. Here's the other info you requested:

1. root=/dev/sdc1

2. hd4,1

---

### Post by Rubi1200 on 2011-06-11
I hope bcbc won't mind me jumping in here.

It seems that the disk designation must have changed. Wubi is no longer on sdc but is now sde. Did you add another disk recently?

In any event, I would start by copying the  /wubildr /wubildr.mbr files from sda2 and putting them at the root of sde1.

Leave the copies on sda2 of course :-)

If this doesn't work, I am sure bcbc will come along and offer further advice.

---

### Post by bcbc on 2011-06-11
Boot to the grub menu, hit 'e' to edit the first entry, change "root=/dev/sdc1" to "root=/dev/sde1" and then hit CTRL+x to boot.

Drop to terminal (CTRL+ALT+t) and run:
```
sudo update-grub
```

As Rubi1200 said, it looks like you've added a drive (or two) lately? If you make changes or notice that plugging/unplugging other drives results in the same problem, update the "root=/dev/sdXY" part as appropriate. Or try to keep things stable.

---

### Post by penn919 on 2011-06-11
> **bcbc said:**
> Boot to the grub menu, hit 'e' to edit the first entry, change "root=/dev/sdc1" to "root=/dev/sde1" and then hit CTRL+x to boot.

Drop to terminal (CTRL+ALT+t) and run:
```
sudo update-grub
```

As Rubi1200 said, it looks like you've added a drive (or two) lately? If you make changes or notice that plugging/unplugging other drives results in the same problem, update the "root=/dev/sdXY" part as appropriate. Or try to keep things stable.

Yeah, that worked although the first time I tried it Ubuntu hanged at the splash screen, but it worked the second time. Also, I installed a new 2TB samsung hard drive about two weeks ago so I'm guessing that may have led to the problem. 

Thanks for the help guys. I appreciate it.

---

### Post by Rubi1200 on 2011-06-11
Glad you got things sorted out :-)

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

