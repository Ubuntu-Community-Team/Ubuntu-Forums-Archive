---
title: "Install Ubuntu on a Inspirion 1525"
date: 2008-03-01
forum: Dell  Ubuntu Support
---

### Post by rickmans on 2008-03-01
I am planning to buy a new Dell laptop, unfortunately Dell does not ship laptops with Ubuntu preinstalled to the Netherlands. I would like to install Ubuntu on it, however my main concerns are drivers and wireless. Are these simply running out of the box, or do they require very specific Dell configuration? I also noticed Dell offers iso's ([http://linux.dell.com/files/ubuntu/iso-images/](http://linux.dell.com/files/ubuntu/iso-images/)). could I use these to install ubuntu on my new laptop?

---

### Post by sillyxone on 2008-03-01
I'm using Gutsy on my Dell D620. Usually you need to play with video (ATI or Nvidia) and wireless driver (the Winmodem is hopeless and not worth it).

My D620 has an Intel video chipset so it's automatically installed (but installing ATI or Nvidia driver is pretty easy too). The wireless is Broadcom BCM43xx, and can be easily installed using Ndiswrapper. Combining with wicd, wireless is painless, even better than on Windows.

By looking at a sample Inspiron 1525 configuration, the video is Intel X3100 and the wireless seems to be Broadcom chipset too. I'm not sure if other optional features such as mobile broadband is supported under Ubuntu.

I don't know about the ISO as I didn't have any serious problem to look elsewhere.

---

### Post by rickmans on 2008-03-04
Anyone any experience with installing Gutsy on a 1525 which was shipped with Vista on it? Or should I take the minor risk ;).

---

### Post by maheshjagadeesan on 2008-03-08
I've been trying to install 7.04 (64-bit) on it, but haven't met with any success yet. It gets stuck every time with an initramfs problem and stops at the ash prompt

---

### Post by Aurora@FleetBuzz on 2008-03-08
> **rickmans said:**
> Anyone any experience with installing Gutsy on a 1525 which was shipped with Vista on it? Or should I take the minor risk ;).

Got mine today.  It's a great machine.  I've set it up to dual boot, no problem there.

Big problem getting Ubuntu to recognize the Dell 1505 Wireless N card.  I've got a thread working here, but so far, I can't get it going.
[http://ubuntuforums.org/showthread.php?p=4477369#post4477369](http://ubuntuforums.org/showthread.php?p=4477369#post4477369)

---

### Post by maheshjagadeesan on 2008-03-09
> **rickmans said:**
> Anyone any experience with installing Gutsy on a 1525 which was shipped with Vista on it? Or should I take the minor risk ;).

rickmans, I solved my problem. I managed to install Feisty on my Inspiron 1525 laptop by adding the following kernel parameter while booting the LiveCD: "all_generic_ide" (without the quotes, of course).

I hope you're able to sort out your problem too. Good luck!

---

### Post by wertyuiop408 on 2008-03-30
i bought Inspiron 1525 with vista pre-install, but switched to gutsy, cant get wireless working but havent really looked at how to, but wired works fine.

---

### Post by demoric on 2008-03-31
You can either go through the hassle of ndiswrapper, or what I suggest is just use the restricted driver manager.  Boot your laptop up w/ it connected to your wired network connections and then download the restricted driver.

Sytesm->Administration->Restricted Drivers Manager

When you enable the Broadcom 43xx chipset it will prompt you for a file, just download it from the menu.

---

### Post by notwen on 2008-03-31
I would recommend getting a 1525 w/ Intel 3945 wireless and using one of the custom Dell Ubuntu images hosted at their wiki.  I run a Inspiron 1420n(Intel x3100 graphics chipset and Intel 3945 wifi) and re-installed the custom Gutsy image w/o any problems.  I would recommend building your machine at [http://dell.com/open](http://dell.com/open) pre-installed w/ Ubuntu.  Then build your machine w/ matching hardware specs as close as possible to ensure your machine will be covered by the appropriate custom Gutsy image.  Best of luck w/ your future purchase.  =]


---EDIT---
[Here]("http://ubuntuforums.org/showthread.php?t=713227") is a thread regarding machines w/ Dell's wifi cards, I cannot comment on how well they function if at all or any problems related to said Dell cards.

---

### Post by amarant on 2008-04-04
> **rickmans said:**
> I am planning to buy a new Dell laptop, unfortunately Dell does not ship laptops with Ubuntu preinstalled to the Netherlands. I would like to install Ubuntu on it, however my main concerns are drivers and wireless. Are these simply running out of the box, or do they require very specific Dell configuration? I also noticed Dell offers iso's ([http://linux.dell.com/files/ubuntu/iso-images/](http://linux.dell.com/files/ubuntu/iso-images/)). could I use these to install ubuntu on my new laptop?

I bought a Inspiron 1525 with Vista, I installed Ubuntu and everythiong just worked out of the box. Ubuntu did not enable my wlan by default but a notification that restricted drivers was available appeared, and i got to enable it manually. Hopefully a free alternative will show up.

It was a wonderful experience.

---

### Post by maheshjagadeesan on 2008-04-11
amarant, which version of Ubuntu did you install?

---

### Post by crimsontime on 2008-04-13
Hi Amarant,
I just installed Ubuntu on my 1525 preloaded with Vista and could not get the wlan to work.  I'm wondering if you can elaborate on how you got it to work.  

I was also wondering if there is a safe way to use the Dell reinstall ISO to get the other drivers.  Has anyone been able to do that without damaging the Vista installation?

---

### Post by gertjant on 2008-04-13
Hi all,
I also orderered a dell 1525 and was planning to use the [ http://linux.dell.com/files/ubuntu/iso-images/ubuntu-dell-1525n-intelvideo-reinstall.iso]("this iso")

I will let you know if it all works as expected after the notebook is arrived.

---

### Post by littlebattler on 2008-04-14
Do you guys with the 1525's have any issues with suspend or did it work out of the box? I just bought one too and waiting for it to be delivered. What about compiz and sound? any issues there?

---

### Post by notwen on 2008-04-14
[This sticky'd thread]("http://ubuntuforums.org/showthread.php?t=750250") has multiple links on it you guys will find useful.  =]

---

### Post by crimsontime on 2008-04-14
My 1525 shipped with vista and I'm in the process of setting it up.  I used this tutorial and it worked great for the initial install: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

My next challenge was getting WIFI to work.  This was somewhat of a nightmare.  This is the thread which contained instructions that actually worked:
[http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)

What I'd like to know is if the reinstall ISO from dell could be used to reinstall to just my Ubuntu partition part of my dual boot with Vista so I'd have more of the proper drivers out of the box.  From what I read on the dell instructions for the ISO here this seems a bad idea:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/OS_Reinstallation#Reinstalling_from_DVD_disc](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/OS_Reinstallation#Reinstalling_from_DVD_disc)

 It seems that this ISO blows out your entire drive and i don't want to lose Vista so I haven't tried using it.

 It would sure be nice not to have to hunt for all the drivers if this were possible to use this install on ONLY the Ubuntu partition leaving Vista intact.

---

### Post by snowjm on 2008-04-14
I just stuck Ubuntu on my fiance's laptop which came preinstalled with vista. Though I made sure to purchase the intel WiFi card since I knew it would have a better chance of working out of the box, and it did. :D The only hardware I am having an issue with is the webcam and builtin mic. Though I have not admittedly really played with it enough to know how hard it will be to get working.

---

### Post by notwen on 2008-04-14
> **crimsontime said:**
> 
What I'd like to know is if the reinstall ISO from dell could be used to reinstall to just my Ubuntu partition part of my dual boot with Vista so I'd have more of the proper drivers out of the box.  From what I read on the dell instructions for the ISO here this seems a bad idea:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/OS_Reinstallation#Reinstalling_from_DVD_disc](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/OS_Reinstallation#Reinstalling_from_DVD_disc)

 It seems that this ISO blows out your entire drive and i don't want to lose Vista so I haven't tried using it.

 It would sure be nice not to have to hunt for all the drivers if this were possible to use this install on ONLY the Ubuntu partition leaving Vista intact.

You can use this custom Ubuntu image, it works just as any other Ubuntu LiveCD/DVD.  Boot from DVD, double click the install icon and you will get to select which partitions the install will use.

---

### Post by gertjant on 2008-04-24
As I promised earlier. Here are my first findings on installing the dell reinstall iso.
At first I made an image of the disk so it will be no problem to get back to the original situation and it gives me much more comfort in formatting the entire disk.

The installation itself was very easy. Just two enters and a cup of coffee later I need to fill in my username and password.

Wifi (intel card) works almost outofthebox. Until now I did not use wifi so I wasn't aware of the different implemetations of WPA2. That was all.

I also came across the different known errors already mentioned in [http://linux.dell.com/wiki/index.php/Ubuntu_7.10]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10")
Like the not working microphone; the muted volume and the know recognized webcam. The volume is fixed as described on the dell wiki. I haven't tried enough to make the rest work.

Further I wasn't able to find a keyboard setting that enabled the numerical keyboard (by using the function settings). What keyboard do you people use?

What I find disturbing at the moment. I occurs often when I select via the menubar an application and it take 10-20 seconds to popup. This seems to long for me to be normal. What is your experience?

@Notwen: the default installation does format your entire disk.

At this moment I haven't installed that much and I have downloaded 8.04 lts release :) so I will try that first to see if that works also and hopefully much better.

I will post it here!

---

### Post by gajanan.khandake on 2008-07-16
> **rickmans said:**
> Anyone any experience with installing Gutsy on a 1525 which was shipped with Vista on it? Or should I take the minor risk ;).

I have installed ubuntu 7.10 on my dell inspiron 1525 which is shipped with windows vista home premium, the installation of ubuntu 7.10 is successful. After the installation on first login my wireless was working fine, system has given me error about the GUI will not work properly(themes and other thing), I continued and updated the system using updated manager it took 2-3 hr with 256kb broadband connection. On restart after update showed the grub loader, where I choose to boot into windows vista just to check that it is working. Vista showed me some system check before log-in screen, and every thing is working fine in and on vista. After Rebooting form vista I choose to boot in ubuntu. which booted successfully and every thing is working fine on and in ubuntu. Till date I haven't checked for web cam and other things such as mobile broadband card modem, Ethernet and other function such as dvd drive, but I think it should work fine. I am happy with the dell inspiron 1525 which is now having vista + ubuntu 7.10 dual boot. since every thing i wanted working fine on both windows vista and ubuntu

---

