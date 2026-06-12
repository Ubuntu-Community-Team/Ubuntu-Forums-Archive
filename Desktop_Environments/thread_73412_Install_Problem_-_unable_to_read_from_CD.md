---
title: "Install Problem - unable to read from CD"
date: 2005-10-09
forum: Desktop Environments
---

### Post by tmfs on 2005-10-09
Configuration: Dell GX620 Pentium 3.2 GHz 2mb cache, SATA hard drives, Philips CD/DVD Drive, 1 GB Ram.

I downloaded Ubuntu Hoary and Kubuntu Breezy. In both of them I got the same problem. When the comp. was loading the additional components, it stopped on libc6-udeb and said that it couldn't read from the cd rom and asked me to check the cd rom's integrity.
I did that and the cd rom was valid. Then it started the installation again, asked me for some PCMIA parameters. I pressed Enter and then it hanged. 

Please help me.

---

### Post by Knome_fan on 2005-10-09
Weird. Sure sounds like a bad CD.

You could try to burn the isos again at a very low speed. This does help quite often.

---

### Post by tmfs on 2005-10-09
I've tried it. No effect.

I tried to install directly from windows and followed all the steps in the wiki. But at boot it just shows me the GRUB prompt. How do I proceed?

---

### Post by tmfs on 2005-10-10
Please help

---

### Post by tmfs on 2005-10-10
Can anyone help please?

Since the CD is not working, I am going with direct windows install. What do I type at the GRUB prompt which comes after I select Install Ubuntu?

I have followed all the steps in the Wiki and tried both versions of Grub which  are linked too at the wiki

---

### Post by Takis on 2005-10-10
Howdy! Let's see what we can do. It really does sound like you've downloaded a bad iso image - did you run an MD5 check against it? Unfortunately I don't think Nero gives you this option, you'll need to download a program like winmd5sum ([http://www.nullriver.com/index/products/winmd5sum)](http://www.nullriver.com/index/products/winmd5sum)). Then try burning again. Unfortunately if the CD you've been using is unreliable it's nearly impossible and certainly impractical to repair your system using it.

So how were you going to run the install? Were you going to overwrite Windows, or dual-boot? If you're trying to dual-boot and GRUB's not giving you the option of booting into Windows, get a Windows 98 bootdisk, boot from that and at the command prompt type ```
fdisk /mbr
```Reboot and Windows should work as it used to.

---

### Post by tmfs on 2005-10-11
Thank you for the reply.

I copied the code for my iso into another file and saved it as a .md5 and checked it through md5summer. (Is that how you run a check) There were no errors.

Also I downloaded Kubuntu Breezy and Ubuntu Hoary through BitTorrent and both are facing the same problem. In fact when I tried installing RedHat, when it came to the installation point, it again said it could not read from the CD Rom and asked me to insert the CD Rom again.


I am using Windows XP SP2. I have one partition and 6 GB empty space. I was going to do a dual boot.
I am able to boot into Windows but I am not able to install Ubuntu Linux through CD. And I can't to figure out how to install it directly from Windows.

---

### Post by Takis on 2005-10-11
[QUOTE=tmfs]I copied the code for my iso into another file and saved it as a .md5 and checked it through md5summer. (Is that how you run a check) There were no errors.[/quote]
I'm not sure if you're doing the md5 check correctly. If you still have the .iso image on your computer, run winMd5Sum. Click the '...' button, and find the iso image you want to test. I'm guessing you downloaded the i386 versions, so the sums should come up as:
> f4fcccef9dac1ab40654a156e39b1a6f  (Kubuntu Breezy i386 CD)
f6b3f164c99761234858a4d2c12d0840  (Ubuntu Hoary i386 CD)
I'm presuming you downloaded the CDs, not the DVD.

From here we assume that your md5 sums are correct. Now you say that Red Hat gave you the same problem? If it's happening so much, you may possibly have a bad CD drive, or more likely are burning the images too fast. Slow the burn speed down to quite slow and see if it's any different.

> And I can't to figure out how to install it directly from Windows.
Uh, you can't. It's an operating system. The first and most important reason why you can't install from Windows, just to let you know, is because as it's an OS it needs to do massive changes to your system that Windows for security and stability reasons would never let you do. The Ubuntu installer CD needs complete control of your system, so there's no way you can do this without rebooting. This would be the same as if you wanted to dual-boot two versions of Windows.

---

### Post by tmfs on 2005-10-12
The MD5 sum for Ubuntu is OK but for Kubuntu is wrong.

[QUOTE=Takis]
From here we assume that your md5 sums are correct. Now you say that Red Hat gave you the same problem? If it's happening so much, you may possibly have a bad CD drive, or more likely are burning the images too fast. Slow the burn speed down to quite slow and see if it's any different.
[/quote]

I have slowed down the burn speed to 4x with no effect. 

As for the CD Drive being bad, it's possible although it has worked fine for me till now except for Linux. Is there any definitive way to check?

[QUOTE=Takis]
Uh, you can't. It's an operating system. The first and most important reason why you can't install from Windows, just to let you know, is because as it's an OS it needs to do massive changes to your system that Windows for security and stability reasons would never let you do. The Ubuntu installer CD needs complete control of your system, so there's no way you can do this without rebooting. This would be the same as if you wanted to dual-boot two versions of Windows.[/QUOTE]

I meant installing it the way they have listed it in the wiki - [https://wiki.ubuntu.com/Installation/FromWindows]("https://wiki.ubuntu.com/Installation/FromWindows")

I can't get past the GRUB prompt on reboot.

---

### Post by Takis on 2005-10-12
Ah I see what you mean (about the from Windows install). I don't think that's going to help much, because it seems the CDs turn out bad. Then you'll be just copying corrupted data to the hard disk and trying to boot from that.

If the CD drive works okay otherwise, it's highly unlikely that it's broken, so we'll have to look elsewhere. With regards to the burning speed, I had 2x or even 1x burning. Try it at the slowest speed possible.

Also, you say you keep getting the grub prompt, I'm presuming you mean the ```
>
```which tells you absolutely nothing (as opposed to the boot menu screen). It seems that although your installation crashed, the GRUB image was written to the hard drive and now dies because the Linux installation it's supposed to be pointing to doesn't exist.

How do you boot into Windows, though?

---

### Post by tmfs on 2005-10-14
[QUOTE=Takis]
If the CD drive works okay otherwise, it's highly unlikely that it's broken, so we'll have to look elsewhere. With regards to the burning speed, I had 2x or even 1x burning. Try it at the slowest speed possible.
[/quote]

Tried it. No effect.

[QUOTE=Takis]
Also, you say you keep getting the grub prompt, I'm presuming you mean the ```
>
```which tells you absolutely nothing (as opposed to the boot menu screen).
[/quote]
It's like this

```

GRUB>
```

Whenever I press escape it takes me to a list where the options are 
Find menu.lst
Find glrdr
Grub

[QUOTE=Takis]
It seems that although your installation crashed, the GRUB image was written to the hard drive and now dies because the Linux installation it's supposed to be pointing to doesn't exist.
[/quote]

But I haven't installed Ubuntu

[QUOTE=Takis]
How do you boot into Windows, though?[/QUOTE]

I followed the instructions in the wiki which told me to add an option "Install Ubuntu" to the boot.ini file. I did that and it showed me a dual boot screen where the options were

Windows XP
Install Ubuntu

Whenever I click on Install Ubuntu, it shows me the GRUB prompt.

I can't figure out how to install it from an image on the hard drive. 

The wiki also didn't ask me to add the address of the image file, on the hard drive, to any file. Am I supposed to do this on the GRUB Prompt?

---

### Post by Takis on 2005-10-14
> But I haven't installed Ubuntu
[quote="your first post"]I downloaded Ubuntu Hoary and Kubuntu Breezy. In both of them I got the same problem. When the comp. was loading the additional components, it stopped on libc6-udeb and said that it couldn't read from the cd rom and asked me to check the cd rom's integrity.[/quote]
You've clearly *tried* to install Ubuntu, otherwise how do you have GRUB on your computer? That's what I meant, anyway.

Because your installation failed (did not complete) your GRUB menu is quite useless at the moment.

So when you say you try burning the CD at slower speed at it doesn't work, what do you mean? Do you reboot and go through the whole installation procedure again, and it fails again at the libc6 problem? Do you do this each time?

---

### Post by tmfs on 2005-10-14
[QUOTE=Takis]You've clearly *tried* to install Ubuntu, otherwise how do you have GRUB on your computer? That's what I meant, anyway.

Because your installation failed (did not complete) your GRUB menu is quite useless at the moment.
[/quote]
OK, I get it now. Do you have any idea how to rectify the problem, i.e. how to make the installation succeed?

[QUOTE=Takis]
So when you say you try burning the CD at slower speed at it doesn't work, what do you mean? Do you reboot and go through the whole installation procedure again, and it fails again at the libc6 problem? Do you do this each time?[/QUOTE]

It always fails when it is trying to load the libc6-udeb file, every time.

---

### Post by Quellcore on 2005-10-14
[QUOTE=tmfs]It always fails when it is trying to load the libc6-udeb file, every time.[/QUOTE]
I've got the same problem, same file "libc6..." ... i'm using The Live-Version Ubuntu 5.10 "The Breezy Badger" (Intel X86).
I'm totally new to the Linux Community, and i'm stuck for now, too.
Couldn't find too much informatin about that issue except for this thread.

I really hope there is a solution for that. :???:

---

### Post by tmfs on 2005-10-15
I just realized from this [Link]("http://www.ubuntuforums.org/showthread.php?t=71401") thread, that the CD may not be working because I have a Phillips CD Drive.

So now the only thing left for me is to install directly from the hard drive or from an external CD Drive. Unfortunately, the computer is refusing to install Linux from the hard drive.

Can anyone help on that? 

1. I downloaded the linux and initrd.gz files into c:\boot
2. I downloaded grub for dos and extracted glrdr and menu.lst from it
3. I placed glrdr in c:\ and menu.lst in a folder grub in the boot folder.
4. I added the given text to the menu.lst file
5. I placed the iso in the boot folder.
6. I added the required text to the boot.ini file.
7. I rebooted and the computer showed me two options
   Windows XP
   Install Ubuntu
8. I selected Install Ubuntu and the computer showed me the prompt
```

grub>

```

9. Upon pressing the Esc key, the computer showed me the following.
```

find \boot\menu.lst
find \boot\grub\menu.lst
find \boot\glrdr
commandline prompt
reboot
halt

```

Have I followed the steps correctly? If yes, then where could be the problem?

PS I have SATA hard drives. Could those be creating a problem in hard drive install?

---

### Post by tmfs on 2005-10-15
deleted

---

### Post by tmfs on 2005-10-16
Can anyone help on the netboot install please?

Thank you

---

### Post by Takis on 2005-10-16
Sorry buddy but now you're getting out of my league, I don't know how to do any of the stuff you're asking about. Maybe you could borrow a friend's CD drive temporarily?

---

### Post by tmfs on 2005-10-16
I do have an external CD Drive (Predator iomega), only the computer cannot boot from it and I don't have a floppy drive either to boot using a floppy.

---

### Post by ApexWebSolutions on 2005-10-25
Post deleted and [re-created in Breezy Badger 5.10 forum]("http://ubuntuforums.org/showthread.php?p=442947")...

---

