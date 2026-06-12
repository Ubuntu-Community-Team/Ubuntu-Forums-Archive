---
title: "XSane with Epson Workforce 600 through LAN"
date: 2009-01-04
forum: General Help
---

### Post by olivero1 on 2009-01-04
I am using Ubuntu 8.04 Hardy Heron and I have an Epson Workforce 600 connected via LAN (Full Duplex) and I am not able to find the scanner with XSane. I have noted that the network connection is not supported, nevertheless, I have followed the manual configuration steps with no luck. 

As a side note I do know that the Workforce is installed properly for I am able to use it completely within my VirtualBox Xp Install. I am also able to print to the device from within Ubuntu with no problems as well as other XP machines from various locations within my home.

I have 2 questions:

1) Has anybody had success in getting this Epson All-In-one working with XSane via the network connection? If so, can you guide me to how you have accomplished this?

2) Is there another application that will work with the scanner via network? If so, what is the name and where can I acquire a installation command for it?

I have searched for 3rd party application and found one that only supports the USB connection. I would like to use the LAN connection since this is a home office application that requires several PCs to print to it as well as scan.

Thanks in advance for your help and please let me know if you require any further information.

---

### Post by xefialtis on 2009-01-06
I am thinking about buying one of these, but I need to have scanning working...
I found this information, which may or may not help you...
> 
[http://www.nabble.com/-iscan--New-release-available-td20532086.html](http://www.nabble.com/-iscan--New-release-available-td20532086.html)


But the XSane site says:
> 
WorkForce 600 	USB 	0x04b8/0x0847 	good 	network interface not supported<br>all-in-one


If you get it working, please let me know, as I will buy one...

Thanks!

---

### Post by olivero1 on 2009-01-06
> **xefialtis said:**
> I am thinking about buying one of these, but I need to have scanning working...
I found this information, which may or may not help you...

I have downloaded this and gave it a try - still no scanning via network:( - but the printer seems to like this driver a lot better - so I will keep using it!


> **xefialtis said:**
> But the XSane site says:

I saw that too. Perhaps in the future it will? I have the XSane site bookmarked so I will keep an eye on it. I might even consider being a beta tester!


> **xefialtis said:**
>  If you get it working, please let me know, as I will buy one...

If you plan on using it via the USB connection everything (including scanning) works great! But alas I have it in a location that will require a very, very long USB cable, or I could run a cat5 cable to it from my network switch- But since it has WiFI built in it is more economical!

Also worth noting if you are going to use any Window$ machines with it just install the software from the CD and your done - Ubuntu on the other hand not so easy...

> **xefialtis said:**
> Thanks!

No, Thank You! I have searched all over the place for a alternative for XSane and I never found iscan. Pretty cool utility!

I will keep this posting updated of any fixes or other useful information for anyone interested. 

I must confess that this Epson is a pretty sweet machine! Just need to figure out the scanning in Ubuntu so I can use it without Window$:D

---

### Post by stbub on 2009-02-19
> **olivero1 said:**
> 
If you plan on using it via the USB connection everything (including scanning) works great!

Is that so?

No luck with either 8.04 or 8.10 at my end, using xsane.

What version of ubuntu are you using?  What scanning software are you using?

---

### Post by olivero1 on 2009-02-20
I am using Ubuntu 8.04 (Hardy Heron) with the latest xsane installed.

But I have also used a driver from OpenPrinting.

[Here is the link to the site that has the directions to install the driver in Ubuntu. I have linked this paragraph so that you can verify the code.]("http://www.linuxfoundation.org/en/OpenPrinting/Database/DriverPackages")


Add the line to your /etc/apt/sources.list file

```
deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.2 main
```

And then run

```
sudo apt-get update
```

Once you do this go into your printer configuration and add a new printer - it should find the following driver:

Epson WorkForce 600 - CUPS+Gutenprint (OpenPrinting LSB 3.2) v5.2.2

That should do it. 

If you have any questions let me know - if I do not know the answer I will help you find one:D

BTW - I have never really posted codes before so I am not sure if I have done this properly (that is why I have included the link to the directions).

Hope this helps!

---

### Post by robenroute on 2009-03-08
Just wanted to let you know I'm trying to get a BX600FW (basically the same as a Workforce 600) to scan via the network (see [thread]("http://ubuntuforums.org/showthread.php?t=1089972")). So far, no good.

Wish it was Christmas...

---

### Post by robenroute on 2009-03-08
Found some more info in the following thread: [here]("http://ubuntuforums.org/showthread.php?t=199147")

But somehow, I can't get it working...

Help would be greatly appreciated ;-)

---

### Post by olivero1 on 2009-03-08
> **robenroute said:**
> Found some more info in the following thread: [here]("http://http://ubuntuforums.org/showthread.php?t=199147")

But somehow, I can't get it working...

Help would be greatly appreciated ;-)

I will see if I can find some time and look into that. Be patient it may be a week before I can get to it.

Also - the link you provided above had the extra http:/ in the address.
[http://ubuntuforums.org/showthread.php?t=199147](http://ubuntuforums.org/showthread.php?t=199147) is the correct address based on your link - is it the right one? It is talking about SQL.

If so, i may have retyped it wrong.

I have opted to hook up the printer wireless and have a XP machine setup for scanning. So I am very interested in getting Ubuntu scanning - but as I mentioned before I have a lot on my plate right now and as soon as I get some time I will start looking into what you have found.

If you happen to find anything else please post it here and I will look into it.

BTW - I know networking and so I can most likely figure it out.

Thanks for posting!:D

---

### Post by robenroute on 2009-03-08
Hi there Olivero1,

Sorry for the typo, I've corrected it. I have found a few more web pages with additional information. I will collect the urls and post them here.

Thanks for your efforts. :-)

---

### Post by robenroute on 2009-03-12
Hi Olivero,

I found these pages (mind you, the first one is a google translation from German into English). I have no problems reading German, so if you need help, don't hesitate.

[http://translate.google.com/translate?hl=en&langpair=de|en&u=http://forum.ubuntuusers.de/topic/netzwerkinstallation-hp-officejet-6310/](http://translate.google.com/translate?hl=en&langpair=de|en&u=http://forum.ubuntuusers.de/topic/netzwerkinstallation-hp-officejet-6310/)

[http://ubuntuforums.org/showthread.php?t=112364&highlight=sane-net](http://ubuntuforums.org/showthread.php?t=112364&highlight=sane-net)

Regards,
Rob

---

### Post by olivero1 on 2009-03-14
thanks for the links!

I have been researching all sorts of information that you have provided and it seems that the SANE epson2.conf, net.conf, services all require some editing.

As soon as I figure out the recipe I will post the recipe that works.

BTW - make sure that you are part of the "saned" group. You can do this by going to: System/Administration/Users and Groups then click "unlock" and enter the sudo password and then "Manage Groups".

I have made a little progress - but no luck yet. I now have XSANE taking about 10 minutes to timeout and then the famous "no devices found". Right now it looks like it is a matter of finding the right port to use and configuration to have it "talk" and work.

Another avenue I am going to look into is importing the .bin file from Window$ and see if that will help. I will have to do more research to see if it is worth the time: 1) to find & 2) if it will help at all.

Well I am done banging my head against the monitor for now and try again fresh tomorrow.

Thanks again for the research and if you find more please let me know!

---

### Post by olivero1 on 2009-03-15
Possible solution.

After much research and help I think I have found a way to scan over the network. However, it may not be ideal. You still have to have the machine connected via USB and then networked through the host (server) pc.

Here is what I have found: (this is my first major attempt at a walk throuh - so please let me know if I have made any errors;))

[Image Scan! for Linux]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do")

this is provided by Seiko Epson Corporation.

It supports networking scanning when the device is connected via USB to a Server PC that client PC's can connect to through your network. [The cleint and server may be one in the same machine.]

When you goto the site fill out the radio buttons and select the proper answers to the questions that they have. Once you get to the next screen look for the .deb file for Image Scan. They also provide a printer utility as well if you want/need it.

Once you download the .deb file install it.

You may need to do some final configurations to the following files:

/etc/sane.d/dll.conf
/etc/sane.d/net.conf
/etc/services

Here is the setup procedures. NOTE - you need to be SUDO to make the changes. Be sure to make a backup copy of the original file before you make any changes.

Client PC

Make sure that the net module is enabled in /etc/sane.d/dll.conf. (if there is a "#" before the entry, remove it.) Also, make sure that an entry exists for epkowa # needed by iscan is present and without a preceding #.

Example:

```
net
epkowa # needed by iscan
```

Now you need a sane entry in etc/services. The install file may have done this - but check to be sure!

Look for the following entry, and if you do not see it - add it. It should be at the very bottom of the page.

```
sane 6566/tcp # SANE network scanner daemon
```

You can also easily find it by using the following code

```
$ grep 6566/tcp /etc/services
```

Server PC

On the server (PC that has the scanner connected to) side you need to add clients that are allowed to use the scanner. > NOTE: Use the IP address that is assigned to your PC. You may want to assign a static address for this. If you need help with this please let me know - it is actually really simple!:D

/etc/sane.d/saned.conf

```
scan-client
192.XXX.X.XXX
```

Be sure that /etc/sane.d/dll.conf has the epkowa module enabled. See the directions for the client PC above.  Note that the install should have done this - better safe than sorry though!

The /etc/services needs a sanr entry as well, again see the direction for the client PC above for the entry.


Hopefully you have made or ensured that all the entries are present and you are ready to restert your PC. You could just restart the services - but I like to refresh the RAM, personal preference I think.

Once your machine comes back up - give it a try. Hopefully I have written this clearly and you have a working network scanner.

I have n Ubuntu Server machine running and I think this is how I will overcome the issue. Unless somebody out there is better at figuring this out better than me!:)

I have noticed that on the Epson site it states that network scanning is only available for Linux users via this route:

> Please note that scanning over the network is only supported in a client/server setup. Scanners directly attached to the network are not supported.:(

Let me know if you have any questions and if I can answer them I will.

---

### Post by robenroute on 2009-03-19
Thanks a lot for all the work Olivero. I can't test this set-up having just one PC in my network, but the description looks pretty solid. It's a pity Epson don't support scanners directly connected to the network. I guess I was hoping for the community to have filled this functionality gap. Maybe next time I should buy an HP all-in-one, as HP delivers Linux drivers that do support network scanning (via hplip)...

Thanks again Olivero!

Kind regards,
Rob

---

### Post by robenroute on 2009-04-04
I've sent Epson and Avasys (the driver developers) emails about this lack of functionality. So far, only an Epson engineer has responded and said he would bring it to the attention of the developers at Epson. I haven't heard anyhting yet of Avasys, but who knows, in the coming days...

My guess is it won't happen any time soon. The reason I've got an Epson is they are using waterproof ink. I would have bought an HP if HP would supply waterproof inks. I just don't understand HP doesn't have these.

---

### Post by boblizar on 2012-10-01
1st off sorry to dig up old threads...  1st hit from google and yet unsolved, until linux god boblizar shows up....

my environment is NOT ubuntu.  however under gentoo i have gotten it to pull at least 1 preview over the network only wire involved is ac power....

printer end setup for wifi 802.11b make sure it pulls your pinters new ip address, netmask so on....

linux box end i installed....

iscan-2.26.2
iscan-data-1.9.0.1
sane-backends-1.0.22-r1
sane-frontends-1.0.14
xsane-0.998
gimp-2.8.2

power up printer, then run to pc, load gimp up...

file > create > xsane dialog

loads up xsane, then hit acquire preview and it pulls its preview from the network.  the printer end of the device is (old gnome) : 

system > admin > print settings

add printer > fold down network options > wait 2 seconds > epson workforce 600....

(printer ip address):515
queue: passthru

if you want to bribe me with an exact ubuntu specific fix even with linux from scratch style compiles if nessisary hit my donation link on my master thesis thread.... found here [http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)

(to note a problem i ran into, when the printer went to sleep after so long of inactivity i had to restart it)

PROOF of a scan through xscanimage via network....
[IMG]http://imageshack.us/a/img593/2985/screenshotqv.png[/IMG]

---

