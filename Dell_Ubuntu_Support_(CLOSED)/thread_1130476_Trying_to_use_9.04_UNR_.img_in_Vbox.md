---
title: "Trying to use 9.04 UNR .img in Vbox"
date: 2009-04-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jaqrah on 2009-04-19
I don't know if I have missed a step or have blundered in some other way but I cannot get 9.04 UNR .img to boot in Virtualbox.

Has anybody else tried this and succeeded?  Any help would be appreciated.

Thank Jaq

---

### Post by anjilslaire on 2009-04-20
I Haven't tried in VBox, just in real hardware, but try this:
1. Use Imagewriter to write the .img to a usb flash drive.
2. Launch VirtualBox, mount the usb drive and boot from it.

---

### Post by jaqrah on 2009-04-20
I was trying to avoid that route but so be it.

Thanks

---

### Post by karimone on 2009-04-20
I don't know VirtualBox 'cause I use always Parallels, but I think that boot from the .img as a CD isn't possible. Could you "attach" the img at your virtual machine as virtual hard disk?

---

### Post by anjilslaire on 2009-04-20
> **jaqrah said:**
> I was trying to avoid that route but so be it.

Thanks

Here's a wild thought:
Do as I mentioned. write it to a real usb, but then create an ISO of the functional usb stick. Then you can restore your usb to a normal state, and mount the ISO as needed.

No idea if that will work, though.

---

### Post by dcstar on 2009-04-22
> **karimone said:**
> I don't know VirtualBox 'cause I use always Parallels, but I think that boot from the .img as a CD isn't possible. Could you "attach" the img at your virtual machine as virtual hard disk?

Yep, it is not an .ISO CD/DVD format image it is a special USB boot image.

If the VM BIOS can be set to boot off a USB drive then it should boot and install as per "real" hardware.

---

### Post by karimone on 2009-04-22
> **dcstar said:**
> 
If the VM BIOS can be set to boot off a USB drive then it should boot and install as per "real" hardware.

Yes, but he can also use the img as hard disk on the VM and boot from there.

---

### Post by jaqrah on 2009-04-22
> karimone  	

Yes, but he can also use the img as hard disk on the VM and boot from there. 

Unfortunately, no I cannot.  Vbox does not recognize the .img as a legitimate hard drive.

And Vbox does not allow for booting from USB devices.

Can I just load 9.04 and then enable UNR packages?

Or (infinitely more complicated) in Vbox Xp guest install daemontools and mount the image in a virtual drive and install from the image drive?? Is that even remotely possible?  I know it would repartition the Xp host but it seems like an interesting possibility albeit **very** time consuming.

Thanks for help and suggestions so far.

---

### Post by karimone on 2009-04-22
> **jaqrah said:**
> Unfortunately, no I cannot.  Vbox does not recognize the .img as a legitimate hard drive.


Maybe there are some tools for converting the file in something that Vbox can handle.

---

### Post by jaqrah on 2009-04-22
Tried img to iso conversion app...it doesn't work.  File type of img is not supported.  Tried renaming img to iso.  No luck.:confused:

I am not beat yet.  Will keep trying.:-k

---

### Post by superbubba on 2009-05-06
Convert the IMG file into a VDI disk image with **VBoxManage**:

```
$ VBoxManage convertdd jaunty-netbook-remix-i386.img jaunty-netbook-remix-i386.vdi
```

---

### Post by jaqrah on 2009-05-06
Superbubba

Nice job...I will give it a try tonight when I get home from work.

=D>  Grazie

---

### Post by karimone on 2009-05-06
Grazie?! Ma arrivi dallo stivale? Anche tu italiano all'estero?

---

### Post by jaqrah on 2009-05-06
> **karimone said:**
> Grazie?! Ma arrivi dallo stivale? Anche tu italiano all'estero?

 :lolflag:  When I ran that through Babelfish, it provided a confusing translation: it arrives from the boot?  what does that mean? ;)

---

### Post by karimone on 2009-05-06
> **jaqrah said:**
> :lolflag:  When I ran that through Babelfish, it provided a confusing translation: it arrives from the boot?  what does that mean? ;)

I read your "Grazie" on the signature than I thought you are italian. The "boot" (Stivale) in another name of Italy, 'cause if you look Italy from the Google Maps, you can see that have the shape of a boot... :-) :)

---

### Post by floborg on 2009-05-06
Way easier approach: just enable the virtual floppy and mount the IMG there.  :P

---

### Post by jaqrah on 2009-05-07
> **floborg said:**
> Way easier approach: just enable the virtual floppy and mount the IMG there.  :P

Unfortunately, this did not work.  Returned  BOOT ERROR


> superbubba  	
Re: Trying to use 9.04 UNR .img in Vbox
Convert the IMG file into a VDI disk image with VBoxManage:

Code:

$ VBoxManage convertdd jaunty-netbook-remix-i386.img jaunty-netbook-remix-i386.vdi



This did work. 

1.  Convert .img to jaunty-netbook-remix-i386.vdi
2.  Create NEW machine in Vbox including a new harddrive (I named it Ubuntu 9.04 UNR.)
3.  Finish creating NEW machine.
4.  Settings>Harddisk  remove Ubuntu 9.04 UNR (or whatever name you might choose) as the IDE Primary Master. Attach jaunty-netbook-remix-i386.vdi as the IDE Primary Master.  Re-attach Ubunt 9.04 UNR as IDE Primary Slave.
5.  Start the machine.  Install Ubuntu.  It will give you option to repartition and install on Ubuntu 9.04 UNR.  When done installing, it require reboot.  reboot.  when it comes back up to main install screen close the machine, forcing it to quit.
6.  Settings>Harddisk detach both .vdi's.  Re-attach Ubuntu 9.04 UNR as IDE Primary Master.
7.  Re-start the machine and I was ready to rock and roll UNR!

Superbubba...thank you!

Sadly...UNR is so slow...so painfully slow and buggy.

---

