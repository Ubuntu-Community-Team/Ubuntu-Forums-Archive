---
title: "help with wireless for a linux nooby"
date: 2006-01-08
forum: General Help
---

### Post by shadowfist on 2006-01-08
I need some serious help with getting my wireless working on my ancient laptop.
I have tried several distros of linux and like ubuntu the best but I have yet to find one that my wirless card works with. I have a SMC2635W pcmcia card. but I dont know how to configure it to work on ubuntu. I dont even know the first thing to check. help please :-) thank you much, in advance.

---

### Post by Quirky on 2006-01-08
A Google search reveals that it uses either the rt2400 or adm8211 kernel module, both of which are included in Ubuntu. Have you tried plugging the card in to see what happens? You can use the System->Administration->Networking GUI to configure it.

---

### Post by socrazy143 on 2006-01-08
When I first installed ubuntu I had to pull up System -> Administration -> Networking to enable the wireless.  This would be the first place to start.

---

### Post by ahave2005 on 2006-01-08
While I wrote this socrazy142 came with an obvious first step, but if you allready done that read on.

I have to begin this reply by telling, that I'm a long way of beeing a linux expert, I'm only sharing my own experience on wireless networking.

In my desktop computer i have a card, thats based on the rt2400 chipset, it doesn't work out of the box in Ubuntu. If it doesn't work for you, you could use ndiswrapper to load the driver for xp.

If you need this solution, here's a howto to use ndiswrapper:
[https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper)

There's just one thing they don't mention, which could be the difference between failure and success.

You have to remove the old module beforehand. If its loaded that is.

Start up a console and do:
> lspci

Here you have to look through the lines for your wireless network, this will tell you if it's reconized and likely what chipset it is.

Here is my output:
0000:01:07.0 Network controller: RaLink Wireless PCI Adpator RT2400 / RT2460

So now you know what to look for in the next section.

Again in console:
> lsmod | grep rt2400

lsmod lists the loaded modules. The grep funktion is telling, that you only want output where rt2400 is a part of, otherwise its a very long output. If this doesn't give any output, try to change grep rt2400 with the other module Quirky is reporting adm8211.

If this doesn't give any either, your module might not loaded and you can proceed with the wiki link.

If it gives a result, which would look something like this:
> rt2400                 67008  0
Only with your modulename.

You now have to remove the old module, otherwise no matter what you do, it will just keep on using that module.

In console:
> sudo rmmod rt2400

Now your ready to use ndiswrapper, which is relative simpel.

Theres just one thing, next time you reboot you have to do the rmmod step again, if you don't change this. The only way I know so far to do this, is to remove the module files, but I'm sure that there is a much smarter way to do this. Somewhere, I guess, there's a config file, telling the kernel to use this driver for this wireless device.

So lets just hope someone with more experience comes along and give a solution to this. If not I'll tell you what I've done, but I regard my way as a bit messy.

A note. When Ubuntu 5.10 just upgraded its kernel, my wireless card stopped working again. It took me a long time to figure out why, but if I had followed what I just wrote, it would have been easy. It started to use the old module again, s&#229; I had to rmmod the module again.

/ahave

---

### Post by shadowfist on 2006-01-09
alrighty now I have "configured" the wireless card but it dosent seem to work right the system says that eth0 is active and such. it also knows that it is a wireless card so it seems that its detecting it properly. I am hoping to not have to use an ndis wrapper if i dont have to cause i heared that it can cause some problems etc. is there a program that i can use that i can find out if the card is getting a signal or even if it is pulling an ip?

---

### Post by shadowfist on 2006-01-09
annother odd peice of the puzzle is that I went to install a wired 10/100 pcmcia card to install the updates and such. whenever I booted linux with the card in the machine it would cause the machine to freeze :-( is there something that could cause that, or a way to prevent it?

---

### Post by pelle.k on 2006-01-11
I understand you. NDISwrapper isn't really the most clean solution.
Well i don't really know about the rt2400.

Is the module loaded? (lsmod)
can you see you card (lspci)
Can you see it using ifconfig? (eth0 i suppose?)
Can you see it using iwconfig? (eth0?)

My rt2500 stays inactive until i tell it what essid to connect ot and so on. ill tell you how to do that but first i want to know the answer to my questions...

---

### Post by Strife on 2006-01-11
ndiswrapper isn't *that* bad. But if you have a driver available to you, then that is clearly the better solution. Are you sure that eth0 is the wireless device? I suppose if you're starting the computer without the wired ethernet card in, this is probably the case.

To be sure, run iwconfig. If it says "no wireless extensions" then there is a problem. Otherwise, you should be able to use the Network Admin tool (or command line tools, or NetworkManager, or etc....) to get it configured.

I've noticed at times, when I configure my card with the Network Admin tool, I have to manually run dhclient to get an IP address. To do this:

```
sudo dhclient eth0
```

---

### Post by shadowfist on 2006-01-11
thanks for all the great info I have been wondering how to do lots of this stuff. but now I know alittle more about the problem.

I have mannaged to get the wireless card configured and it HAS worked now. it seems that when i boot the computer up the wireless works for the first 3 minutes or so. then it inexplicably stops working. I have the network monitor graph set up on the top menu and at some point the traffic just stops.

usualy my browsing sessions go something like this:

[www.google.com](www.google.com) -> works fine! woooo! I fixed it
clicks on images tab -> also works! alright!
[www.gmail.com](www.gmail.com) -> no response
Back to google -> no response

so usualy i have about 1.5 pages i can load before the network stops working I am baffled as to what could be causing this. any ideas?

---

### Post by Mr_Grieves on 2006-01-11
If you are using DHCP, check if you lost you're IP-adress.
Check if you're interface via ifconfig -a

Via ifconfig you can also see diffrent kind of errors going to/from you're network interface.
```

          RX packets:224111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145415 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000

```

Counters should show 0 on errors, dropped, overruns, frame, carrier and collisions.

---

### Post by shadowfist on 2006-01-13
[QUOTE=pelle.k]
Is the module loaded? (lsmod)
can you see you card (lspci)
Can you see it using ifconfig? (eth0 i suppose?)
Can you see it using iwconfig? (eth0?)
[/QUOTE]

yes,
yes,
yes, and
yes. respectively

[QUOTE=Strife]
I have to manually run dhclient to get an IP address.
[/QUOTE]
once the card stops working about 3 minutes after boot it just gets no response. other than that it seems to be loaded should be working. it still has its ip address and everything.

---

### Post by pelle.k on 2006-01-14
I suggest [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

If you don't know how to compile it, ask for help.
I'm a little tired right now, but i'll check this thread again tomorrow...

---

### Post by shadowfist on 2006-01-15
looks like my card uses the adm chipset. will that driver work for my card?

---

### Post by abrainlessdude on 2006-01-15
That's strange because if i remember correctly I have the same card as the OP. I maybe misreading and being on lots of meds but I am almost sure that mine worked straight after install. I might have had to set up a plan (as I have 3 or 4 wireless connections in my area), but it worked fine.


Wow that was one hell of a run-on sentence.

---

### Post by shadowfist on 2006-01-15
[QUOTE=abrainlessdude]That's strange because if i remember correctly I have the same card as the OP. I maybe misreading and being on lots of meds but I am almost sure that mine worked straight after install. I might have had to set up a plan (as I have 3 or 4 wireless connections in my area), but it worked fine.


Wow that was one hell of a run-on sentence.[/QUOTE]
well it sounds as though there are two chipsets. and it might have something to do with my laptop's hardware as well.

---

### Post by pelle.k on 2006-01-15
It's really quite simple. Is rt2400 module loaded? (lsmod) If so hotplug (should) have detected your card, and you should see it using iwconfig...

If not - then you probably have the adm chipset :(

There is an open source driver which is not far along.
I would recommend the NDISwrapper. Install NDISgtk.
By the way, your card should show up as wlan0 when correctly installed.
The tricky part is how to get the .inf and .sys file from the driver package, if it's not a zip/rar package that is... (go visit a friend, and install driver package on his computer when he is using the toilet, and then tell him someone backed into his car. Now you have a minute or two to burn the files to a cd :P )

---

### Post by shadowfist on 2006-01-16
[QUOTE=pelle.k]It's really quite simple. Is rt2400 module loaded? (lsmod) If so hotplug (should) have detected your card, and you should see it using iwconfig...

If not - then you probably have the adm chipset :(

There is an open source driver which is not far along.
I would recommend the NDISwrapper. Install NDISgtk.
By the way, your card should show up as wlan0 when correctly installed.
The tricky part is how to get the .inf and .sys file from the driver package, if it's not a zip/rar package that is... (go visit a friend, and install driver package on his computer when he is using the toilet, and then tell him someone backed into his car. Now you have a minute or two to burn the files to a cd :P )[/QUOTE]

well the getting of the inf and sys files are not a problem seince i have it dual booting 98 on the same machine ;-)

---

### Post by pelle.k on 2006-01-16
Windows!? Shame on you ;)

Nah... but seriously, good luck with ndis. Can be a tricky bastard to configure sometimes. But you know the melody, ask if in trouble...

---

