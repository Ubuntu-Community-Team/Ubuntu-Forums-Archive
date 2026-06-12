---
title: "Serious Problems, Desperate For Help!"
date: 2005-06-28
forum: Desktop Environments
---

### Post by semilemon on 2005-06-28
Hello. I'm a newbie and I have had serious problems over the last week. This will be a long post, but please find the time to help me. Here is my story:

My ubuntu CD's came, great! Couldn't wait to get home and try them. First I decided to try the LiveCD. I have ran windows all my life and wasn't ready to just write over everything right away. I now know this was a good decision. 

I couldn't figure out the parameters to use to get the LiveCD to work, so I came here. I asked for help, but the person told me how to fix the problem with the install cd, not the live cd. So I figured I'll just have a dual-boot system until I get ubuntu working perfectly.

After my install, I had serious problems. First time, during the install, I must have mis-spelled the root password, and so, I had to install again. After installing a second time, I couldn't perform root actions such as Sudo, and it seemed nobody here could help me because their suggestions weren't working. Also, I couldn't open windows such as Networking and Users and Groups. All that would happen was it would say  "Starting Networking", and then it would disappear, with no Networking window open. One more thing. When I would log in, it told me that ubuntu couldn't find an IP address, or something, and it may be fixed by adding it to /etc/hosts. Could this be the root of my problems?

Finally, I gave up and got rid of linux. But, I screwed up the partitioning afterwards and ended up writing over all of my windows stuff (thank god for backups), and started all over. But now, about 4 days later, those ubuntu cd's on my table have started "calling" me. 

What I am asking of all of you is to help me prevent this mess from happening again. One clue I got by looking through the message boards was that I should be using a DHCP internet connection. I remember such a question during the install, and I believe I said no. Could saying yes fix my problems?

Please help me. I really appreciate it! ](*,)

---

### Post by cwaldbieser on 2005-06-28
I see that you say you are an Ubuntu newbie, but have you ever had much experience with Linux in general, before?  It is probably best that you try to get the LiveCD working first.  That way, once you have figured out what will make things work there, you will have an easier time with the install CDs.

There are probably lots of questions we will need to help you out, but lets proceed slowly.  I will ask you a few questions at a time, and you can try them out and give back the results.

1) What kind of computer are you trying to run the LiveCD on (laptop/notebook or desktop)?
2) Put the LiveCD in the computer and boot it up.  Take note of everything that happens.  Where does the process seem to fail/get stuck?

---

### Post by semilemon on 2005-06-28
Ok, thank-you for your patience with me, because I must be annoying. But, anyway:

- I have not had any experience with linux before

- I am using a Compaq Presario Desktop computer (Intel processor, if it makes a difference)

- With the LiveCD, I'm not always 100% sure what selection I should make. I do know, that I have tried both the "live" and "live-expert" boot modes, and that I need to parameters acpi=off, nolapic, and noapm. Everything goes ok. However, once it starts to boot ubuntu, it tells me that I have set up my graphics/monitor settings wrong (it asked many questions, including refresh rates and screen resolutions (I used the same settings I did in Windows), and that I would need to fix them to run GDM again. Then it took me to a text prompt which started out with "ubuntu@unbuntu...", and then waited for my input. Then I took the CD out and restarted back into windows to get help.

---

### Post by semilemon on 2005-06-28
It is tuesday night and I'm very happy. I noticed a mistake in my first post. I said that I tried the LiveCD in both live and live-expert modes. I meant to say I only tried live-expert (stupid for someone of my skill level). I just tried live and all but two of my problems were gone.

1) My screen resolution is stuck at 640x480. I know there is extensive documentation about fixing this problem using "sudo gedit /etc/X11/xorg.conf" (which, isn't it great, I can use Sudo now!), but they don't say exactly how to do it at a newbie level. I was wondering if you could assist me here.

2) Now that I can use pppconfig, I cannot figure out how to use it. I would like to set up a dial-up connection to my ISP. I have the phone number, user name, and password. Hopefully ubuntu recognizes my modem, otherwise I'll be stuck with windows for the net!

If you reply tomorrow (wednesday), I won't be able to respond until later in the day, but I'm looking forward to my linux installation!!!

---

### Post by semilemon on 2005-06-29
I had a few extra minutes this morning to continue playing around with pppconfig. I've set up my connection, but, if I type "pon *myisp* ", it does not connect (it does nothing, no error, and no connection). I also tried playing around with the Networking option in ubuntu, but again could not get it to connect. Also, I'm not sure which COM port my modem is on (I'll look in windows when I get home).

I'm pretty sure that my modem is recognized by ubuntu because in the device manager, one of the items is "V9.2 56K WinModem".

---

### Post by davahmet on 2005-06-29
[QUOTE=semilemon]I had a few extra minutes this morning to continue playing around with pppconfig. I've set up my connection, but, if I type "pon *myisp* ", it does not connect (it does nothing, no error, and no connection). I also tried playing around with the Networking option in ubuntu, but again could not get it to connect. Also, I'm not sure which COM port my modem is on (I'll look in windows when I get home).

I'm pretty sure that my modem is recognized by ubuntu because in the device manager, one of the items is "V9.2 56K WinModem".[/QUOTE]

Winmodems are problematic for Linux since they require software support that comes from Microsoft, although in the last few years a lot of progress has been made to support them in Linux.  You might check your modem against the Linux hardware list  [http://www.tldp.org/HOWTO/Hardware-HOWTO/modems.html](http://www.tldp.org/HOWTO/Hardware-HOWTO/modems.html)  to verified that it is supported.

Linux uses /dev/ttyS# for serial port assignments where the '#' is replaced by a number, beginning with 0.  So, a port that is COM1 in Windows would be /dev/ttyS0 in Linux.

I hope this helps.

---

### Post by semilemon on 2005-06-29
[QUOTE=davahmet]Winmodems are problematic for Linux since they require software support that comes from Microsoft, although in the last few years a lot of progress has been made to support them in Linux.  You might check your modem against the Linux hardware list  [http://www.tldp.org/HOWTO/Hardware-HOWTO/modems.html](http://www.tldp.org/HOWTO/Hardware-HOWTO/modems.html)  to verified that it is supported.

Linux uses /dev/ttyS# for serial port assignments where the '#' is replaced by a number, beginning with 0.  So, a port that is COM1 in Windows would be /dev/ttyS0 in Linux.

I hope this helps.[/QUOTE]
 I used the link above and I have found my way to a binary .deb download at the following URL: [http://www.heby.de/ltmodem](http://www.heby.de/ltmodem)

I'll try it out and see what happens. I do have a question. Do you think it is more worth my time to get my winmodem working or buy a linux-compatible modem. If you recommend the latter, do you have any specific recommendations of what to buy and where to buy it?

---

### Post by cwaldbieser on 2005-06-29
I started out using dial-up on Linux.  I couldn't get my PCI Win modem to work, so I bought an external Zoom fax modem.  It was pretty decent for dial-up.  I used a (KDE) program called kppp that was pretty helpful in setting up the modem.  Anybody know what the corresponding Gnome program is called?

---

### Post by davahmet on 2005-06-29
[QUOTE=semilemon] Do you think it is more worth my time to get my winmodem working or buy a linux-compatible modem. If you recommend the latter, do you have any specific recommendations of what to buy and where to buy it?[/QUOTE]

That's hard to say.  For me, it would be worth my time to find a Linux compatible modem since winmodems are intentionally crippled to force an OS dependancy.  This is the deal that Microsoft made years ago with the major modem vendors to push functionality from hardware to software.

Linux works with winmodems only by emulating this intentionally bad design.  While it should work fine in Linux, it is always a bit chancy.

---

### Post by semilemon on 2005-06-29
[QUOTE=davahmet]That's hard to say.  For me, it would be worth my time to find a Linux compatible modem since winmodems are intentionally crippled to force an OS dependancy.  This is the deal that Microsoft made years ago with the major modem vendors to push functionality from hardware to software.

Linux works with winmodems only by emulating this intentionally bad design.  While it should work fine in Linux, it is always a bit chancy.[/QUOTE]
 I have a a couple of modems laying around. I'm not sure if they're winmodems (unfortunately they probably are), so I'll try these first and see what happens before I buy new.

---

