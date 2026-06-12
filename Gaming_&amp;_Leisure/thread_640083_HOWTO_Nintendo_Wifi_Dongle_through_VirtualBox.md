---
title: "HOWTO: Nintendo Wifi Dongle through VirtualBox"
date: 2007-12-13
forum: Gaming &amp; Leisure
---

### Post by OttoDestruct on 2007-12-13
First off, let me just say that I really shouldn't get credit for this. All the information is already here, it just so happens that it took quite a bit of searching and messing around.

Also, if anyone sees anything blatantly incorrect feel free to correct. I'm still very new to Linux, and this is my first howto.

**[SIZE="2"]Whats a dongle[/SIZE]**
[img]http://img170.imageshack.us/img170/3750/donglethumbnc6.jpg[/img]
[quote=Wikipedia]The Nintendo Wi-Fi USB Connector is an accessory, developed jointly by Nintendo and Buffalo Technology, which allows Nintendo DS and Wii users without a Wi-Fi connection or compatible Wi-Fi network to establish one via a broadband-connected PC. Inserted into the host PC's USB port, the connector functions as a wireless access point for the Nintendo DS and Wii, permitting the user to connect to the Internet to play Nintendo Wi-Fi Connection games and various other online functionality.[/quote]

The problem with the Nintendo dongle is that it is... well... Nintendo. Or rather Buffalo. Oh nevermind. Basically all you need to know is that due to it being extremely proprietary it is very hard to get to work under Linux. No matter how you go at it, its going to be pretty roundabout getting the thing to work. I've read around and some people suggested using hacked drivers for other similar devices and messing with kernel modules. Really, it just sounded like a big headache. The easiest solution is "buy a wireless router." I happen to be a college kid cramped for space though, not to mention routers are banned on campus and can get your internet revoked. So we're going to be fixing the original problem instead of inventing a new wheel.
[B][SIZE="2"]
The Solution[/SIZE][/B]
The easiest (and so far only) way I've found to get the dongle working is to install VirtualBox. Again, like I said at the start of this 'howto', most of this stuff isn't mine. And quite frankly, I don't think I could write it decently even if it was. There is a great guide by P4man [_on the forums here_]("http://ubuntuforums.org/showthread.php?t=603661") going over how to get VirtualBox installed.

Seeing as I don't have a copy of Vista, I can only comment on the procedures for an XP installation of Virtualbox. Make sure you are also installing the version of VirtualBox that supports USB. Just follow the guide until you get to the portion about integration, as that is all optional. If you really want to, go ahead, but it isn't necessary. The bits about shared folders are optional as well. Once you get a working XP virtual machine, make sure that it is properly connected to your network! You should be able to browse the internet on the virtual machine  no differently than  a non virtual machine. (If you have problems with this, I honestly don't know enough about networking or VirtualBox to help, but feel free to ask anyone else who does know).

**[SIZE="2"]Ok, I got a VirtualBox XP running now what[/SIZE]**
The next shoutout goes to domino for his post [_over here_]("http://ubuntuforums.org/showpost.php?p=2082674&postcount=11") detailing how to get USB working with VirtualBox. I'm going to rewrite his directions, though, as I am not sure they are very clear on what EXACTLY to do.

1) Go to System > Administration > Users and Groups
2) "Add group" with the name usbfs, and give permission to all the users that need access. Close out of the group manager.
3) Open a terminal and do the following:
```
sudo gedit /etc/fstab
```
add the following to the end:
```
# 85 is the USB group
none /proc/bus/usb usbfs devgid=85,devmode=664 0 0
```
Save and close
4) Reboot

Connect your Nintendo adapter, start up VirtualBox and go into the Settings of the machine you created. Go to the USB settings, and Click the little USB icon with the green plus sign to add a device filter, and select the "Nintendo Wifi USB connector". Hit ok and start up the machine into Windows. If there are no errors right away, you're probably already golden! Wait for it to boot up, and Windows should pop up an annoying wizard saying it found new hardware. Go ahead and cancel it. Inside the virtual machine, download the latest nintendo drivers for XP [_from Nintendo here_]("http://www.nintendo.com/consumer/wfc/en_na/customersupport/downloadUSB.jsp"), and install them. It should install, and you can stare at your nice and shiny new drivers. What are you waiting for, test it out! Use your Wii / DS to connect to the dongle as normal and follow the instructions given. Now we just need Smash Brothers Brawl to come out!

So there you have it.
Pros:
The Nintendo Dongle works in Linux with the official Nintendo drivers (well... sort of Linux)
No messing with the kernal
No messing with hacked drivers
No wireless router necessary

Cons:
Any time you want to use the dongle you have to be running VirtualBox
The dongle has a small transmitting range.

---

### Post by K.Mandla on 2007-12-20
Moved to Gaming and Leisure.

---

### Post by t0n1 on 2008-02-03
Would this method work on a 64-bit version of Ubuntu?

---

### Post by Blitzkr1eg on 2008-02-03
This may not be too useful to users of the dongle, but I recommend you get a wireless router instead.

A typical wireless router that supports both wired and wireless is like $40, the cost of the dongle. It's a better purchase IMO.

And you'll probably get the wireless router working more flawlessly than the dongle. I hear that there are some issues with it. Also the range from the wireless router is probably higher.

---

### Post by Sockerdrickan on 2008-02-03
Yes a wireless router is better **BUT** for people who already have a dongle and not a router, this is a great how2!
(I have a wireless router)

---

### Post by t0n1 on 2008-02-08
> **Blitzkr1eg said:**
> This may not be too useful to users of the dongle, but I recommend you get a wireless router instead.

A typical wireless router that supports both wired and wireless is like $40, the cost of the dongle. It's a better purchase IMO.

And you'll probably get the wireless router working more flawlessly than the dongle. I hear that there are some issues with it. Also the range from the wireless router is probably higher.
A fair advice, but I already have a wireless router. The problem is, the network security is WPA and the nintendo DS does not support WPA, only WEP. Lowering the security level is not an option for me.

What I want to know, however, is if this method will work with the 64-bit version of ubuntu.

---

### Post by OttoDestruct on 2008-02-09
> **t0n1 said:**
> A fair advice, but I already have a wireless router. The problem is, the network security is WPA and the nintendo DS does not support WPA, only WEP. Lowering the security level is not an option for me.

What I want to know, however, is if this method will work with the 64-bit version of ubuntu.

Test it and see, because I have no idea. I don't have any experience with 64 bit machines, so I coudln't even begin to offer advice.

---

### Post by andrewjoy on 2008-02-10
> **Blitzkr1eg said:**
> This may not be too useful to users of the dongle, but I recommend you get a wireless router instead.

A typical wireless router that supports both wired and wireless is like $40, the cost of the dongle. It's a better purchase IMO.

And you'll probably get the wireless router working more flawlessly than the dongle. I hear that there are some issues with it. Also the range from the wireless router is probably higher.

Problem with this is the DS only supports WEP and not WPA/2 i am not going to use WEP on my main network.

As the  Wi Fi adaptor for the DS/Wii only supports conections form sutch devices its not as bad as having the  whole network on WEP.

---

### Post by Sockerdrickan on 2008-02-10
I use WPA-PSK for Wii and DS

---

### Post by hesloppy on 2008-03-13
hi,

i know the last reply to this was a month ago but...

using the above how-to i have been able to install the nintendo usb connector in an XP virtualbox.  I  installed the drivers, connected to my wii and selected "usb connector" in the wii internet settings, my wii name then popped up in the driver window in virtual box and i selected "allow access" (or whatever it was called).  My wii then said "configuration complete, would you like to test your connection?" , I select test and then the wii pops up a box saying that it is unable to connect?  Yet, i can STILL see my wii listed in the virtualbox window.

any thoughts and why it is not connecting?  It seems to me like the wii can see the computer and the computer can see the wii (because my wii shows up in the nintendo wifi box) but it just doesnt want to connect.  My wii is about 10 feet away from the dongle/computer.

Thanks!!

---

### Post by OttoDestruct on 2008-03-21
Try turning off the software firewall that comes default in windows.

---

### Post by Unanimated on 2008-07-30
Yeah, um, mine won't work. I did everything you said, my XP works, it'll get on the internet, but Devices doesn't recognize it in XP, but it's recognized by Ubuntu.

---

### Post by Unanimated on 2008-07-30
bump..

---

### Post by Rich930 on 2008-08-27
is there a way to do this on ubuntu server? Would be very greatful.

cheers.

---

### Post by DemonParasite on 2009-08-05
> **Unanimated said:**
> Yeah, um, mine won't work. I did everything you said, my XP works, it'll get on the internet, but Devices doesn't recognize it in XP, but it's recognized by Ubuntu.

I'm having the same problem. It's not being recognized by XP inside the VM, although VirtualBox 3.0 sees it in the config settings.

I'm also running TinyXP rev09, is this causing problems?

---

