---
title: "Unreal 2004"
date: 2007-06-27
forum: Gaming &amp; Leisure
---

### Post by XRichX on 2007-06-27
Umm this may sound noobish, well really noobish but how would i go about installing Unreal on a full Ubuntu partition? I need to get on it as i have Teamspeak working now and im Co-Leader of a clan lol. I had to move completely from Windows as it went all weird.

When i try the Linux install the package just cant be read and the Windows install requires a C:\ directory (using Wine), i tried to change the directory to lead to "/home/MYUSERNAME/Unreal 2004/" but it says directory invalid or something, is there an easy way to get it installed?

thanks in advance :)

Rich

---

### Post by alphane on 2007-06-27
Not used wine, and not an expert on installing games in linux, but when using wine, don't you define a virtual C:\?  Shouldn't you install windows apps in there?

---

### Post by XRichX on 2007-06-27
oh yeah, that would explain it... thanks for that, i shall look into creating a virtual drive.

thanks again :)

---

### Post by Dokatz on 2007-06-27
UT2004 is Linux native, Why use WINE?

---

### Post by alphane on 2007-06-27
It depends on which version he's got.  I know my UT2004 multi-cd installer is the windows version.

---

### Post by XRichX on 2007-06-27
because my Linux installer brings an error as the package cant be read, unknown code or something, il send you the error via pm when i get home.

---

### Post by XRichX on 2007-06-27
right i know why it isnt working, its coz its opening the installer with gedit... what program do i need to run the Unreal Linux installer with? where is it located?

thenks :)

XRichX

---

### Post by MonkeyBoy on 2007-06-27
As I recall if you insert the disk and browse its contents you should have a file called something like linux-installer .sh.  You need to navigate to the cd in the terminal and type ```
sh linux-installer.sh
```
That should start the install.

---

### Post by XRichX on 2007-06-27
thanks for the reply :) i tried that myself and it just says 'Can't Open File'. Is that installer corrupt? :(

---

### Post by wishyjr on 2007-06-30
i'm also having similar trouble with this. I've got a dvd version with the 6 cd folders on it. I've read somewhere that i should copy the linux installer script onto the harddrive but doing that didn't help at all.

I just keep getting permission errors, even running as sudo

---

### Post by voidmage on 2007-06-30
I have the dvd version and installing was as simple as
```

sudo sh /media/cdrom0/installer.sh

```
If that doesn't work try running it with bash instead of sh.

---

### Post by wishyjr on 2007-07-08
ACE! that acutally worked for me -thanks so much. strange as ive tried many variations of that but none worked. aw well, it works for me! :)

---

### Post by XRichX on 2007-07-08
> **voidmage said:**
> I have the dvd version and installing was as simple as
```

sudo sh /media/cdrom0/installer.sh

```
If that doesn't work try running it with bash instead of sh.

sorry for the delayed reply, i have tried both and it just comes up with

```
sh: Can't open /media/cdrom0/installer.sh

```

So theres a problem, correct?

thanks

Richard

---

### Post by XRichX on 2007-07-08
oh its working now, i got the installation but the permissions arent right, just says cannot write to any folder that i choose, how do i set permissions?

thanks

XRichX

---

### Post by QR770 on 2007-07-11
I think you are supposed to install it in your home directory where you already have permission.  If you insist on installing it somewhere else then you would change permissions on the directory with sudo chmod 777 putdirectorynamehere.  As you may know 777 gives unlimited access to everyone.

---

### Post by Cresho on 2007-07-28
MAN!  I was having problems installing this but copying the sh file to the desktop enabled me to install it.  the sh file launched from the cd drive totally would not allow me to eject the cd when changing disk from one to two.  also after inserting the disk, i had to mount it with the taskbar mount utility or clicking on cd drive in the nautilus file browser Made my life easier.

---

### Post by AJB2K3 on 2007-07-29
Now if only there was a way to convert my wine anthology install to a linux native.

---

### Post by ShangTsungOmega on 2007-08-06
Ditto.

---

