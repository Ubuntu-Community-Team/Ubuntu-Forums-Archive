---
title: "WiFi printing 8.10 + Brother MFC-640CW"
date: 2009-03-30
forum: General Help
---

### Post by MichaelSM on 2009-03-30
This printer connected perfectly at first try via wifi.

It has a built-in wireless unit which talked happily with my

Netgear modem/router, WAP password a breeze.

My problem is that after each shut down, the computer's lost the printer, 

and it has to be re-installed. 

Everything's fine with the router. I've never had to re-look at its comms

with the printer. 

On each re-_install_, 8.10 assigns the printer to one of these three 

addresses: 192.168.0. (2, 3, or 4) port 9100. (At the moment it's 192.168.0.2.1900)

By the way, the error message after this reboot and the printer won't work 

is:

"Processing - recoverable: Network host '192.168.0.2'

is busy: will retry in 30 seconds ...."

If I cancet the print queue, that message simply swaps 'idle' for 'recoverable'.

I've waited half an hour sometimes, and it's never 'recovered ....'

So what makes '02.168.0.2' busy? Is there something else happening? No other

printers are connected, and my PC's connected to the router via Ethernet. And that address is 192.168.0.4.

Hmmm. Hadn't looked at THAT before.... (WICD Manager) I'm missing something .... a brain ...?

Any ideas greatly appreciated.

Is there a way of doing it in Sessions?

Cheers.

Mike.

---

### Post by MichaelSM on 2009-03-30
Back again ... after thinking about Wicd ... so I opened it.

I pulled out the Ethernet connector from the router, then clicked

'Connect' for the wireless connection.

Hit the arrow beside Michael WiFi, then ticked 'Automatically connect to

this network.'

Opened Advanced Settings, and

ticked 'Use these settings for all networks sharing this essid'

Clicked OK.

So far so good.

Two shut-downs later, all fine.

If someone knows WHY this worked, please explain if that's OK.

Otherwise I'll mark this as SOLVED after a few more successful tries.

I'd never thought to fiddle with Wicd before, so now I'll google it and

find that this scenario was sorted out yonks ago ...probably...

Mike.

PS. I'd hoped that this may have enabled the MFC'S scanner. It didn't. 

There must be a line I have to add to some 'Sane' folder.

Any solutions to that would be greatly appreciated !

---

### Post by plucky on 2009-03-30
> PS. I'd hoped that this may have enabled the MFC'S scanner. It didn't.

There must be a line I have to add to some 'Sane' folder.

Any solutions to that would be greatly appreciated ! 


You will have to follow the instruction to install the **brscan2**  scanner driver from the Brother website.See this [link](http://solutions.brother.com/linux/en_us/download_scn.html).
Use the instructions for a network scanner.


Good Luck

---

### Post by MichaelSM on 2009-03-30
Thanks for the reply.

 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:0f:a4:6d:0a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.3 multicast=yes wireless=IEEE 8

That's all done. Wireless-wise.

The printer/scanner is fuly accessible usb-wise.

Why not with wifi?

After all, I suppose, my PC is talking to my router. Am I wrong here?

All the Brother gear has been signed, sealed and delivered  via CUPS with all the scan tools and keys enabled. 

Which is why it works so well and so perfectly with usb.

What's the problem with wifi?

There must be something utterly SIMPLE I haven't looked at....?

I must be a moron.

Sorry for so many questions, Plucky.

Thank you.

Mike.

---

### Post by plucky on 2009-03-30
See this [page](http://solutions.brother.com/linux/en_us/instruction_scn1b.html) on the Brother website.

Post output of ```
sudo dpkg -l | grep Brother
```

and ```
brsaneconfig2 -q | grep SCANNER
```

:)

---

### Post by MichaelSM on 2009-03-30
Here's the output:

~$ sudo dpkg -l | grep Brother
[sudo] password for michael: 
ii  brscan-skey                                0.2.1-1                                 Brother Linux scanner S-KEY tool
ii  brscan2                                    0.2.4                                   Brother Scanner Driver
ii  cupswrappermfc210c                         1.0.2-3                                 Brother MFC210C CUPS wrapper driver
ii  cupswrappermfc620cn                        1.0.2-3                                 Brother MFC620CN CUPS wrapper driver
ii  mfc210clpr                                 1.0.2-1                                 Brother lpr Inkjet Printer Definitions
michael@michael-desktop:~$ brsaneconfig2 -q | grep SCANNER
michael@michael-desktop:~$ 

Hope that helps.

Thanks Plucky.

When I get some time later today I'll wwork on the info on that Brother page.


EDIT.

Thanks for the Brother Network Scanner page. I of course never thought of mine as a Network scanner - bit of a no-brainer, really - but it

most certainly _IS_ and now working perfectly with wifi. (It was the 'sudo' entry I suspect which enabled SCANNER access to the network)

Tremendous help.

Greatly appreciated, Plucky,

Michael.

---

### Post by MichaelSM on 2009-04-06
Hello again to this Forum's thread.

The only issue I have remaining is that just SOMETIMES (10% ?) I'll  

start the PC, try to print something, and the wifi printer won't print

and has to be re-installed. This doesn't take long, but it's a

nuisance.

Maybe the answer is to assign static IP addresses to the printer and the

PC.

If anyone knows how to do that - with Wicd - help would be appreciated.

Thanks in advance.

Mike.

---

