---
title: "Failed to initialize HAL (Dell Mini 910)"
date: 2012-03-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by francopdx on 2012-03-13
I have a Dell Mini 910 laptop that uses Ubuntu 8.04 (Hardy Heron). My computer has been freezing up more often over the past month. I hold down the "on" button to turn it off, and over the past week, when I turn it on again, it gets stuck on a DOS (?) screen and does not start up Ubuntu. Then, I turn it off again in the same manner, and the next time I turn it on, it starts up properly. Until yesterday...
 
This DOS screen pops up when I start up:
 
ata1.00: status {DRDYERR}
ata1.00: error: {UNC}
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: BMDMA stat 0x24
ata1.00: cmdc8/00:08:40:f8:04/00:00:00:00:00/e0tag0dma4096 in
 
This set of lines appears over and over again with a number count, so the first set of lines has a "1" in front of on, the next set has a "2" and these sets of lines scroll up the screen very fast. At first, it would do this to no end until I forced a hard turn off and turned it back on several times. Sometimes the screen would turn on and off. Eventually, it would slowly load, but when Ubuntu starts, it says:
 
"failed to initialize HAL!"
 
And when it finishes loading, it also says:
 
"Panel encountered a problem while loading: "OAFIID: GNOME_Mixer Applet" Do you want to delete from your configuration?"
 
I also click on the "Don't delete" button.
 
All my files seem to be intact, but programs open slowly, and the biggest problem is that I cannot connect to the internet. Usually, the upper righthand corner has a the date, time, battery life meter, and network connection status (I used Wicd to connect), but now it only shows the date & time. When I try to open the Wicd program through the Applications/Internet tabs, nothing happens.
 
Also, I tried inserting a memory stick that I think has the Wicd program saved onto it, but then I found out that the memory stick doesn't come up either. So, I cannot connect to the internet or use a memory stick to transfer files on/off the laptop. And just as FYI, my laptop does not have a CD drive either.
 
Help?
 
p.s. - I did find some info on these forums about opening a terminal window to type in (although, it was for a problem related to installing a program - my problem seems to come up out of the blue):
 
sudo gedit /etc/apt/sources.list
 
And add the # sign to the start of the last two lines (where the other lines had # # in front of them already - but my file had no #'s in front of any lines - so I added # # in front of all the lines except the last two lines that I only added one #), and then type this in the terminal:
 
sudo aptitude update
sudo aptitude reinstall hal
 
But after entering the last line, a couple error lines came up and it stopped before reinstalling.

---

