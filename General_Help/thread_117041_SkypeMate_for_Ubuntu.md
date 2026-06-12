---
title: "SkypeMate for Ubuntu"
date: 2006-01-14
forum: General Help
---

### Post by mattm591 on 2006-01-14
I bought a USB to normal phone adaptor so I can use my wireless phone with Skype. To work it needs a program called SkypeMate which can I downloaded from here [http://www.yealink.com/en/skypedown.asp](http://www.yealink.com/en/skypedown.asp) and got the file "  SkypeMate for Linux ZIP file For Fedora Core 3 Support USB-P1K & USB-B2K". When it downloaded an I had extracted it I had a file called install-SkypeMate which I'm not sure how to use. Also it says it's for Fedora Core 3, but I hope it will work on Ubuntu. Can anyone tell me how to get this file to install as sh install-SkypeMate didn't work, it returned "install-SkypeMate: install-SkypeMate: cannot execute binary file".
Thanks, Matt

---

### Post by chele on 2006-01-14
[quote=mattm591] "install-SkypeMate: install-SkypeMate: cannot execute binary file".[/quote]Try "chmod +x install-SkypeMate" & then "sudo install-SkypeMate".

---

### Post by mattm591 on 2006-01-14
No, same problem.

---

### Post by mattm591 on 2006-01-14
Never mind. I solved it. I just had to do ./install-SkypeMate

But now when I try and run SkyeMate I get the error
"SkypeMate: error while loading shared libraries: libdbus-1.so.0: cannot open shared object file: No such file or directory".

Does anyone know how I can solve this. Thanks

---

### Post by mattm591 on 2006-01-15
I foudn that the libdbus-1so.0 is in Ubuntu as libdbus-1-1 so I created a link between the two and then tried to start SkypeMate, but this time got this error,
"matt@Y2K:~$ SkypeMate
SkypeMainWindow()
{{AzmDeviceManager()
AzmDeviceManager()}}
{{OpenDevice()
{{USBDeviceControl(101)
================Msg type = 0x01
USBDeviceControl(101)}}
OpenDevice()}}
Segmentation fault"
I checked in the sound control program thing and looked in the devices and it includes the VOIP USB Phone, I tried selecting this device as well. It still gives the error.
Can anyone help solve this?
Thanks

---

### Post by mattm591 on 2006-01-16
If no one can solve this, could they suggest an alternative program which may work. Thanks

---

### Post by Matchless on 2006-02-05
[QUOTE=mattm591]I bought a USB to normal phone adaptor so I can use my wireless phone with Skype. To work it needs a program called SkypeMate which can I downloaded from here [http://www.yealink.com/en/skypedown.asp](http://www.yealink.com/en/skypedown.asp) and got the file "  SkypeMate for Linux ZIP file For Fedora Core 3 Support USB-P1K & USB-B2K". When it downloaded an I had extracted it I had a file called install-SkypeMate which I'm not sure how to use. Also it says it's for Fedora Core 3, but I hope it will work on Ubuntu. Can anyone tell me how to get this file to install as sh install-SkypeMate didn't work, it returned "install-SkypeMate: install-SkypeMate: cannot execute binary file".
Thanks, Matt[/QUOTE]

SkypeMate: error while loading shared libraries: libdbus-1.so.0: cannot open shared object file: No such file or directory

Anybody got a clue?  Thx[/QUOTE]

Hi,
   I have the same problem. Here is a site where some work has been done, but due to my very limited Linux knowledge I do not really understand what to do here. Maybe you can sort out and let us know if it works.
[http://memeteau.free.fr/usbb2k/](http://memeteau.free.fr/usbb2k/)
They claim to have a working API by Savanna, but what is this and how is it installed?

---

### Post by lonetree on 2006-04-10
Has this problem been solved yet? I bought one of this device from Ranger - RUA-350 USB personal VoIP gateway few dyas back, and I have deployed it with Windows, it works fine. But I am thinking of getting another one for my Linux Box. So I hope someone can help to solved this problem soon.

Thanks

Regards,

---

### Post by mattm591 on 2006-05-02
Nope. I have no solution anyway and I'd still really like one :( is there anyone with the powers to solve this problem. Maybe if they could go back to the basics and try and get the file from the Yealink site to install for them and let us know how. Someone with skills and spare time :P

---

### Post by bluenova on 2006-05-04
Due to the crappyness of skype on linux, I have an old laptop running windows, purly to serve my phone.

---

### Post by Zymous on 2006-07-07
I get this with Skypemate
```

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
SkypeMainWindow()
{{AzmDeviceManager()
AzmDeviceManager()}}
{{OpenDevice()
{{USBDeviceControl(101)
================Msg type = 0x01
USBDeviceControl(101)}}
OpenDevice()}}
Segmentation fault
```

and this with the CallMe software [http://www.yamamoto-group.co.uk/download/CallMe_Linux.zip](http://www.yamamoto-group.co.uk/download/CallMe_Linux.zip) which seems to have come from a very similar stable

```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault
```

Unfortunately, I don't know what it all means either.

P.S. This is with Dapper not Breezy

-- 
Zym

---

### Post by sas on 2006-07-20
the problem comes from the linux binary being old. I think nearly all linux distros are using a newer version of dbus than the binary wants.

To fix it the binary will probably just need a recompile from the software vendors.

---

### Post by blitzer on 2006-10-24
I know this is a late post but Ubuntu Dapper has support for USB phones.  My XACT phone works great in Dapper.  I just went in Skype > tools >options then to sound devices it brought up a page that had 3 buttons : Audio in, Audio out,and ringing.  Click on the button for a drop down and choose use VOIP USB PHONE for each button and click save at the bottom. :-D 

Thanks Ubuntu :mrgreen:

---

### Post by coverup1128 on 2006-11-23
Yes, but do the buttons on the phone work?

---

### Post by lonetree on 2006-11-24
The button will not work. Ubuntu merelydetect it as what "Windows" call it a USB sound device. I may be wrong, but I have tested it with 5.10. One more thing, once plug in the USB, you must not pull out the USB cable as it will hang the system.

---

### Post by adamthompson on 2006-12-01
blitzer, what XACT phone do you have? Thanks.

---

### Post by jbayone on 2007-01-21
Has anyone had luck or heard of skypemate or something similar for Ubuntu yet?

---

### Post by altariel on 2007-01-23
[http://sourceforge.net/projects/kb2kskype/]("http://sourceforge.net/projects/kb2kskype/")
might perhaps be interesting? 
I have installed it on Kubuntu 6.10 at least ...

---

### Post by Matchless on 2007-01-30
> **altariel said:**
> [http://sourceforge.net/projects/kb2kskype/](http://sourceforge.net/projects/kb2kskype/)
might perhaps be interesting? 
I have installed it on Kubuntu 6.10 at least ...

What does this actually do?

---

### Post by altariel on 2007-01-31
> **Matchless said:**
> What does this actually do?

it is an alternative driver for the **USB-B2K-telbox**, not using dbus-message-bus-communication between Skype and the telbox (and the telephones connected to the telbox), but using the new X11-messaging-option in newer versions of Skype instead. It's still under development, but already is quite usable at least in some distributions. 

I never could get Skype and SkypeMate working, not even under Fedora Core 3 which Yealinks only official Linux driver for this type of Telbox SHOULD work for so I am very happy I found this package! 
The main problem with the "normal" combo of Skype and SkypeMate is that SkypeMate for linux is expecting an OLD version of that DBUS (I think 0.22 or 0.23) whereas -most- new distributions have FAR newer versions leading to endless depency problems and downgrading problems - or the SkypeMate not working at all or Skype freezing the computers ... 
[http://www.yealink.com/en/skypedown.asp]("http://www.yealink.com/en/skypedown.asp")


The Telbox itself is a device you connect to the USB-port of your computer (which has internet access and Skype installed) and then you can connect whichever telephone you choose, even wireless ones!) to one port of the telbox and your regular telephone line (if you have any) to the other port and then you can use your normal telephone for both Skype / internet calls and normal / landline calls. quite handy! (especially if you have skype running on an OLDER type of computer where the processing of sound would take to much computer power! I am setting up a dedicated skype server this way on a rather old slow computer but it does work since the telephone itself takes care of the sound-to-digital-conversion!) 

most of the other types of telboxes out there NEED windows XP but this B2K does not ...  

[http://www.yealink.com/en/view.asp?ClassLayer=6]("http://www.yealink.com/en/view.asp?ClassLayer=6")
[http://www.yealink.com/en/newest.asp]("http://www.yealink.com/en/newest.asp")

USB Telbox
MODEL: USB-B2K
	
	KEY FEATURE
&#8226; Support regular and wireless (DECT) phones
&#8226; Make/Receive both Skype calls and regular PSTN calls
&#8226; Dial & Ring by the phone

---

### Post by altariel on 2007-06-12
The new versions of both usbb2k-api-mod and kb2kskype are out and fix (hopefully) most of the bugs folks have reported ... 

please report any feedback to the forums over at the sourceforge net - or here, but I rarely check out this place :(

---

### Post by Matchless on 2007-06-18
OK, this installs beautifully on Kubuntu feisty, but on an ordinary USB IP Phone I still do not have any button functionality, just the usual audio. Does this work on anything else than the telbox? Or am I doing something wrong? If this actually works on an USB phone then this is going to be a winner! kb2kskype has a nice gui and seems to pick up my USB device. Skype shows that it is linked by API  and BK_2 connector, so much is happening. Except that my USB phone does not update its screen and the dial buttons beep, but are not working when pushing speed dial number and #
Any advice?

---

### Post by KillerBob-it on 2007-08-04
I installed kb2kskype following the instruction on [http://kb2kskype.sourceforge.net/]("http://kb2kskype.sourceforge.net/")
but when I launch kB2Kskype from terminal I get this:

[IMG]http://www.lasuperba.net/images/kb2kskype.png[/IMG]


This is my lsusb output:

```
Bus 005 Device 006: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 005 Device 005: ID 047d:2030 Kensington 
Bus 005 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0d9a:0004 RTX Telecom AS 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:08f5 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

The phone is the RTX Telecom AS.

And this is a screenshot of usbview:

[IMG]http://www.lasuperba.net/images/usbview.png[/IMG]

So I think the phone is detected, but it doesn't work... any suggestion?

---

### Post by opticmoose on 2007-08-08
> **Matchless said:**
> OK, this installs beautifully on Kubuntu feisty, but on an ordinary USB IP Phone I still do not have any button functionality, just the usual audio. Does this work on anything else than the telbox? Or am I doing something wrong? If this actually works on an USB phone then this is going to be a winner! kb2kskype has a nice gui and seems to pick up my USB device. Skype shows that it is linked by API  and BK_2 connector, so much is happening. Except that my USB phone does not update its screen and the dial buttons beep, but are not working when pushing speed dial number and #
Any advice?

Im in this exact same situation.  Any help or something that would get the buttons working in linux woudl be fantastic.

---

### Post by altariel on 2007-08-20
well, I'm not the programmer of this (only involved in the packaging :) ...) but I think it only works for telboxes :( 

as far as I understand it there's a lot of communication going on between skype and the box - 
which I don't "ordinary usb-phones" do in quite the same way (most I think are only seen and treated as usb-soundcards basically) ... 

but as I said, I'm not the programmer ...

---

### Post by altariel on 2007-09-05
new package versions are out - but be aware that the NEWEST builds of Skype might give problems with the "Automatic Gain Control" thing they added - there is a way to set it inactive in the config files of Skype though ... Feedback is welcome, as always :) 


[http://forum.skype.com/index.php?showtopic=93881](http://forum.skype.com/index.php?showtopic=93881)
[http://forum.skype.com/index.php?showtopic=95329](http://forum.skype.com/index.php?showtopic=95329)

---

### Post by paulkingnz on 2007-10-06
my phone is a usb7100 from vtech and im using kubuntu and ubuntu and it shows up as a RTX Telecom AS under lsusb. I think we need a linux driver for the phone like it uses for windows

---

### Post by UberKnight on 2008-02-02
Would anyone mind packaging the latest versions as .deb files?  The author has only provided source files and I am having problems compiling from source (bit of a newbie).

Would really appreciate it!

PS  You can get the latest source files here:
[kb2kskype-0.3.6]("http://sourceforge.net/project/showfiles.php?group_id=186708&package_id=217783")
[usbb2k-api-mod-2.7]("http://sourceforge.net/project/showfiles.php?group_id=186708&package_id=217887")

---

### Post by altariel on 2008-03-11
am right now packaging the new versions, should show up sometime around the weekend at the latest ... if you desperately need the package for Kubuntu 7.10 pm me and I'll mail it - that one is finished, the 6.10 version is not :(

---

### Post by altariel on 2008-03-31
new packages are out, with a new one for (k)ubuntu 7.10 added since that's what I run this under right now right here :) 
[http://sourceforge.net/project/showfiles.php?group_id=186708](http://sourceforge.net/project/showfiles.php?group_id=186708)

---

### Post by gywst on 2008-05-15
> **mattm591 said:**
> Never mind. I solved it. I just had to do
```
./install-SkypeMate
```

Works with the Tesco Internet Phone E337. Actually the Tesco E337 is a Yealink USB-P1K VOIP handset.

---

