---
title: "help! :("
date: 2005-08-07
forum: Desktop Environments
---

### Post by Cyberman on 2005-08-07
Alright, so I recently downloaded the KDE Kubuntu 5.04 linux distro.
I installed it on my laptop and everything was goig great, UNTIL it didn't detect my wireless card or ethernet card.

I'm a AMD 64 user.

I've tried other linux distros before and they usually figure out my ethernet but this distro didn't seem to be able to figure it out.

So now I have a laptop that can't connect to the internet and it's my only means of burning files to a storage unit for transfer. It doesn't except floppy disks.

So I'm wondering what the next step I should take is.

How do I enable my ethernet card so that it will work with the cat 5 plugged in it from the router?

If you question what card I have, I don't know.
How do I find out what wireless cards and ethernet cards I have?

I figure getting the ethernet card working here is more important because it will allow me to download things like ndiswrapper.

I believe I have a broadcom 802.11 G wireless card built into the laptop (soldered on)

I don't know what ethernet card I have though. I'm assuming 10/100.

---

### Post by varunus on 2005-08-07
Can you post the output of lspci in a terminal?  Also lsmod in a terminal?  This will let us know what card you have.

here's a howto on how to get broadcom chips to work:
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+ndiswrapper)

---

### Post by wvslkr on 2005-08-07
In terminal do lspci and ifconfig and post results so we can see what card you have and
if it was recognised.

---

### Post by Cyberman on 2005-08-07
Found it, it's called konsole.

Uh...

Network Controller:  Broadcom Corportation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I'm looking at the ethernet...

Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)


--------

IFCONFIG::

link encap: Local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:76 errors:0 dropped:0 overruns:0 frame:0
TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:5420 (5.2 KiB) TX bytes:5420 )5.2 KiB)

------------

I have some card in the laptop for dialup but it's not important to me at this time for setting up.

---

### Post by wvslkr on 2005-08-07
Yes in the application menu probably under system utilities.  I"m in Gnome at the moment.  Click to open terminal and type in the commands.  Copy +paste.

---

### Post by varunus on 2005-08-07
Its called the "konsole" in KDE.  I think its under system tools in the K menu.  Console output will allow us to debug your system a lot better; don't be scared of it.  The console is very powerful in linux.

---

### Post by Cyberman on 2005-08-07
[QUOTE=varunus]Its called the "konsole" in KDE.  I think its under system tools in the K menu.  Console output will allow us to debug your system a lot better; don't be scared of it.  The console is very powerful in linux.[/QUOTE]
 go up a few posts.

---

### Post by varunus on 2005-08-07
What is the output of lsmod in a konsole?  Specifically, do you see the "via-rhine" module there?

If not, in konsole, type "sudo modprobe via-rhine" and enter your password when asked.

If this command succeeds (ie, no error messages) then type ifconfig.  You should see your new ethernet interface eth0 there.  You can configure it graphically after this.

If this change works for you, you can make it permanent by adding the line "via-rhine" to the file /etc/modules.  Use "sudo kwrite /etc/modules" in a konsole and enter your password.

If this doesn't work, post back here.

---

### Post by Cyberman on 2005-08-07
I see a bunch of things that say via82xx

they have to do with snd_*** [*=misc variable/(w/e)]

the only thing that i see that says via_rhine is

mii 5504 1 via_rhine

i tried that sudo stuff, I got a bash error thing.

there's also some other via things...

---

### Post by varunus on 2005-08-07
If via-rhine is being loaded, then your ethernet card should work.  Try the following:

```
sudo /etc/init.d/networking restart
sudo ifup eth0
```

in a konsole.  Wait for the minute this may take.  Then, type ifconfig.  Do you see eth0, your ethernet card?

---

### Post by Cyberman on 2005-08-07
Line 1--sudo /etc/init.d/networking restart (worked)
Line 2--didn't work: sudo ifup eth0

ifconfig didn't display anything abotu the eth0.
the second line of code didn't work either.

I'm going to come to the conclusion real quick that linux sucks.
I've used other distros and it's just hard shit to set up for my laptop.
I think that this type of problem might go away in a few years when my laptop is obsolete.

Blah.
Maybe I should go buy a linux pcmia card and put it in then install the drivers so I never have to deal with this crap again.

---

### Post by wvslkr on 2005-08-07
Are you sure you typed in Konsole: sudo modprobe via-rhine   correctly?  It has to be just as shown including spaces or you will get an error.  This appears to be the correct module for you.

---

### Post by Cyberman on 2005-08-07
[QUOTE=wvslkr]Are you sure you typed in Konsole: sudo modprobe via-rhine   correctly?  It has to be just as shown including spaces or you will get an error.  This appears to be the correct module for you.[/QUOTE]
 i may have the first time.
I did it this time.. but still..

ifconfig didn't display anything about the eth0.

---

### Post by wvslkr on 2005-08-07
Were there any errors when you ran modprobe this time?

---

### Post by Cyberman on 2005-08-07
no.

in control center fo

internet and network >> network settings 

i see eth0 with a large circle X and the state being disabled. comment is ethernet network device.

---

### Post by wvslkr on 2005-08-07
Try the sudo ifup eth0 command now.  Then run ifconfig again.

---

### Post by Cyberman on 2005-08-07
Error:

Ignoring unknown interface eth0=eth0.

---

### Post by wvslkr on 2005-08-07
The only other thing I can suggest is trying the network restart again and then try to restart the card again.  If that doesn't work I'm at a loss at the moment.  Going to have to go get some sleep now.  Maybe someone else can jump in and help.

GL. :)

---

### Post by varunus on 2005-08-07
Sorry your ethernet card isn't working for you. Its very strange that this is the case; the rhine ethernet chipset is supported and I can find few errors relating to it.  Can you try to boot the Ubuntu Live CD or KNOPPIX maybe, and see if your ethernet loads there?  If it does, we know its just a configuration problem...

If you can't download a liveCD, then I have a couple more things to try.

You said in the networking panel there was an X through your ethernet card; can you activate it in the GUI somehow?  I know you can activate in GNOME, i'm not that familiar with KDE's networking.

Does the command "sudo ifconfig eth0 up" give you an "interface not found error" or something like that?  Please be specific about the error.

Also, try "sudo rmmod via-rhine" in a konsole, followed by "sudo modprobe via-rhine" in a konsole.  Then, type "dmesg | grep via" and post the output here.  Do you see any error messages?  (Dmesg shows you the system log; grep shows only parts with via in them; rmmod removes a driver; modprobe loads a driver.)

After doing the above, does "sudo ifconfig eth0 up" work without errors?  Does an eth0 then show up if you just type "ifconfig"?  If so, type "sudo dhclient eth0" to connect to the internet!

Sorry you're having so many problems; its very strange that your ethernet card wasn't detected properly.  I'd suggest trying a liveCD.  Ubuntu is a great distro; with a little tinkering, everything should work, and then you'll have a spyware-proof, virus-proof, fast, and nice-looking computer!

---

