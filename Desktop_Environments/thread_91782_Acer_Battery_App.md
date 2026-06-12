---
title: "Acer Battery App"
date: 2005-11-18
forum: Desktop Environments
---

### Post by 4plus2 on 2005-11-18
Hello,

I have ubuntu 5.10 gnome (2.6.12-9-386) working on an Acer Aspire 3003LC and are very pleased with it so far, but would like to know my Battery status.
Is there another app I could install via the Synaptic Package Manager (have enabled all repositories) as the default Battery Charge Monitor 2.12.1 does not work. Ive googled for a fix to it and it all seems rather complicated so I wondered if another app could replace it - one which works.

EDIT: To fix the current app I think I need a new DSDT from [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php) but they dont have the Aspire 3003LC 

Thanks in advance.

---

### Post by Simon Bridge on 2005-12-02
You will be interested to know that I have the exact same setup as you. And, thus, the same issue. It's not just the battery either - wake from suspend is odd too - like you can lose the touchpad after a suspend. Battery life is about an hour, even suspebded. At least the fan control works, but it cannot switch between battery and AC settings - because the battery cannot be read.

I am working on it - I have a custom DSDT for this which compiles without errors, but am having trouble getting ubuntu to use it. more bullitins as events unfold :)

There is no app that will fix this becasue the problem is not with the app. It is with the firmware. The firmware is broken. AFAIK: It dosn't work properly in windows either. ACER do not respond to inquiries about this... apart from that it's quite a neat little gizmo!

The only solution is to install a custom dsdt.
I'll be submitting mine as soon as I've got it going.
If you like, I can send you the dsl file and you can compile it yourself? We can compare notes?
Simon

[QUOTE=4plus2]Hello,

I have ubuntu 5.10 gnome (2.6.12-9-386) working on an Acer Aspire 3003LC and are very pleased with it so far, but would like to know my Battery status.
Is there another app I could install via the Synaptic Package Manager (have enabled all repositories) as the default Battery Charge Monitor 2.12.1 does not work. Ive googled for a fix to it and it all seems rather complicated so I wondered if another app could replace it - one which works.

EDIT: To fix the current app I think I need a new DSDT from [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php) but they dont have the Aspire 3003LC 

Thanks in advance.[/QUOTE]

---

### Post by renJones on 2006-04-28
hi

I've got a 3003LC as well with the same power issues :(

I've followed the guide here [https://wiki.ubuntu.com/ACPIBattery]("https://wiki.ubuntu.com/ACPIBattery") and used the 3003LC dsdt from [http://acpi.sf.net/]("http://acpi.sf.net/") (I assume it's been posted since the start of this thread)

the thread talks about a dsdt.asl file, but the file from sf is .dsl.

everything seemed to work, tho I did have to edit the dsl file as the guide says you might.

I then copied the kernal, edited the boot menu and copied the DSDT.aml file to /etc/mkinitramfs/DSDT.aml. am using Breezy so didn't patch the initrd.img file. then finally reconfigured the kernal.

So now grub says it's loading the .acpi kernal, tho there doesn't seem to be any difference.

I'm new to Ubuntu and Linux in general but, following my way through the guide i didn't see how the new kernal is any different other than in name or how it knows where to look for /etc/mkinitramfs/DSDT.aml. 

I've got no idea where to go from here... plz help a newbie out! ;)

---

### Post by Simon Bridge on 2006-04-29
> I've followed the guide here [https://wiki.ubuntu.com/ACPIBattery](https://wiki.ubuntu.com/ACPIBattery) and used the 3003LC dsdt from [http://acpi.sf.net/](http://acpi.sf.net/) (I assume it's been posted since the start of this thread)That's a good link - and that dsdt has, indeed, been contributed after this thread ... it may even be the one I sent them. However - the firmware dsdt is not actually broken in terms of the actual code.> the thread talks about a dsdt.asl file, but the file from sf is .dsl.That's right. The aml file is the machine-readable version. As you probably figurd out, you get it from the dsl using the iasl interpreter.> So now grub says it's loading the .acpi kernal, tho there doesn't seem to be any difference.

I'm new to Ubuntu and Linux in general but, following my way through the guide i didn't see how the new kernal is any different other than in name or how it knows where to look for /etc/mkinitramfs/DSDT.aml.AFAIK: there is no substantial difference between the firmware dsdt and the one from sf.net - nothing that will make a difference to the 3003LC anyway.

The only thing actually broken is the mention in the code of an object (Z007) which does not exist in the machine.

I am curious, however, if you have kept the windows rescue partition and the acer partition when you installed ubuntu - or if you started from a clean HDD?

I have a suspicion that the missing information is in these partitions instead of being in the BIOS like it's supposed to be.

At the moment - I am waiting new versions of adsl support to see what happens. The alternative is to compile a vanilla kernel, with all the latest adsl patches, and see if that helps.

As far as the mkinitramfs (there are copious discussions about this on the web) is concerned - this is slated to take over from the minitrd method of booting linux. The 2.6 kernel series automatically looks for these things. You can check that it is happening by looking in your syslog.

---

### Post by renJones on 2006-04-30
Thnx for the info, now I know what I was doing (ish) when messing around with the kernel! :)

> I am curious, however, if you have kept the windows rescue partition and the acer partition when you installed ubuntu - or if you started from a clean HDD?

I have a suspicion that the missing information is in these partitions instead of being in the BIOS like it's supposed to be.

I got the ubuntu install to wipe the HDD and start again...  I got the machine new with xp home on and only remember there being 2 partitions, one with windows installed and a larger ACERDATA partition. Do you know where the info would have been or how I'd get it back now?

> At the moment - I am waiting new versions of adsl support to see what happens. The alternative is to compile a vanilla kernel, with all the latest adsl patches, and see if that helps.

adsl? now I'm really confused... :???: 

on boot the kernel is loading the acpi services ok. 

it seems to be doing some of the power mangement. the lcd screen brightness dims when the power lead is taken out, but the battery monitor reports that it is always running on ac power with 0% charge left. Also I've noticed a weird problem when it puts the screen to sleep, although the screen is black the back light seems to flash on and off about every second, but only when the power options put the screen to sleep, it turns the screen off (but not the machine itself) ok when you close the lid. it was showing this behaviour before i complied the new dsdt...

Is your battery readout correctly showing? I don't think you confirm it. And I assume that you also have a windows partition on your 3003lc?

---

