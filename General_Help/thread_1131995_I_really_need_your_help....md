---
title: "I really need your help..."
date: 2009-04-21
forum: General Help
---

### Post by mdsevero on 2009-04-21
Hi guys... 

Ive been using Ubuntu for quite some time now and I haven't got any problem except today... 

when I logged in, I cant get into the desktop and instead, I see a lot of numbers. To be honest, I am not a techie guy, and I am completely lost. I don't know why it just stopped working.

Here is what I'm seeing every time I restart my computer...

[B]   
   [291.287819]ata1.00:status: {DRDYERR}
   [291.287873]ata1.00:error: {UNC}
     EXT3-fserror(device sda6):ext3-get-inode-loc: unable to read
     inode block - inode:3620865, block = 14483458
     init: Error parsing configuration
           No such file or directory
   [291.330976]kernel panic-not syncing: attempted to kill init!
[/B]

After this, the capslock and numlock on the keyboard blinks continuously.

When I force the computer to restart... the same message appears, but the numbers in the beginning of the line changes...

I dont know what is happening...
I can't access the desktop and all my files are there. I don't have any back-up copy and I am really dead if I cant get it. 

Could this be repaired?

I hope you could help me. Im desperate at the moment. 

Thanks in advance

---

### Post by codeseer on 2009-04-21
Don't panic. :P

There's ways to get your files, even if it can't be fixed.

---

### Post by mdsevero on 2009-04-21
how? 

and could I still use my computer?

---

### Post by codeseer on 2009-04-21
The first thing we need to do is have you back up your files.

Do you have the Ubuntu CD? Also, do you have some way of backing up your files? A USB drive or something?

---

### Post by somnusnoctem on 2009-04-21
You might want to try booting with an Ubuntu LiveCD. At the very least, that would probably give you a starting place for figuring out the problem. Hopefully, it would also allow you to access your files.

---

### Post by sir_nasty on 2009-04-21
1st things first.  do you have a live cd and a usb stick?  if so I'd boot off the cd and backup the stuff you need.  Then just re-install to make life easier.  This issue is fixable without a re-install, google for ubuntu kernel panick and you'll find lots of documentation on it.

---

### Post by codeseer on 2009-04-21
> **sir_nasty said:**
> 1st things first.  do you have a live cd and a usb stick?  if so I'd boot off the cd and backup the stuff you need.  Then just re-install to make life easier.  This issue is fixable without a re-install, google for ubuntu kernel panick and you'll find lots of documentation on it.

It could be drive failure.

---

### Post by mdsevero on 2009-04-21
yes, I have the cd and i've just run it, there are choices there and I clicked try ubuntu without installing... 

Im in but how do I get my files back?

When I check the drive, there were no files in it

---

### Post by codeseer on 2009-04-21
> **mdsevero said:**
> yes, I have the cd and i've just run it, there are choices there and I clicked try ubuntu without installing... 

Im in but how do I get my files back?

When I check the drive, there were no files in it

You will need to click the 'Places' menu at the top and pull it down. There should be a white drive-like icon in the list that has some numbers and "GB Media" beside it. Click on that.

Edit:

This should place a shortcut to your drive on the Desktop. You can then double-click on this new shortcut and open the 'home' directory. If you have enough room on your backup device, you can copy the entire folder labeled after your username under the 'home' directory to your backup device.

Your 'Desktop' files will be under /home/username/Desktop.

[COLOR="DarkOrange"]**Page 2 this way -_>**[/COLOR]

---

### Post by mdsevero on 2009-04-21
whew! codeseer... your an ANGEL!!!

Your GODSEND!... Thank you very much... ive seen it. Im copying it right now.

Whats the next step with these?

Will I retain the programs when I reinstall Ubuntu?

---

### Post by codeseer on 2009-04-21
You will retain (most likely) all of your configuration information and files for the programs by copying the /home/username directory. You will also retain all of your files on the 'Desktop'. The binary programs themselves are usually installed in other areas of the disk, however and they may need to be reinstalled; but, their configuration that you set up will probably remain intact.

The next step is to run a check on your install.

Open a terminal by going to Applicaitons->Accessories->Terminal and type the following in it, then copy/paste the output back here:

```
sudo blkid
```

---

