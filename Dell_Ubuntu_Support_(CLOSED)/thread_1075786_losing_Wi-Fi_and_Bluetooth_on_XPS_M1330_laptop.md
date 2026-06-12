---
title: "losing Wi-Fi and Bluetooth on XPS M1330 laptop"
date: 2009-02-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimDaniels on 2009-02-20
My XPS M1330 was working fine for 9 months - both the Bluetooth mouse and Wi-Fi under Feisty and Hardy.  Then I did something in Network Manager which turned of the Wi-Fi, and although it worked fine under the dual-booted Vista, it didn't work under Ubuntu.  Finally, I gave up and re-installed Ubuntu, version 8.04.2 with the Broadcom STA driver selected.  Bluetooth worked fine, but Network Manager couldn't see my wireless router.  At one point, I unchecked Roaming - and that's all she wrote.  No more wireless network option on the Network Manager menu, and Bluetooth doesn't work on Ubuntu **or** Vista.

When I try running `sudo hdd --server --search` on the Ubuntu terminal to jog Bluetooth into action (as it did previously under 8.04.1), sudo says that the "hdd" command couldn't be found.  Does anyone have any suggestions to get Wi-Fi and Bluetooth working again?

*TimDaniels*

---

### Post by TimDaniels on 2009-02-20
The problem with "hdd" was that it should have been "hidd".  When I ran `hidd --server --search` Bluetooth found the mouse and connected.  After a couple startups, the Bluetooh mouse connects upon startup without running the command, and I have no idea why.

Wi-Fi restoration was just an hour-and-a-half of fiddliing, first in Vista, then in Ubuntu.  I have no idea what got Wi-Fi working.

That's has been the frustrating part about Ubuntu's wireless - at least with the Broadcom B43.. chipset - it can take a couple hours of fiddling, and when it starts working again, you have no idea why, and it will take the same amount of fiddling the next time it craps out.

*TimDaniels*

---

### Post by soderstrom on 2010-07-07
I borrow this thread a bit because the title explains my problem as well.

I've been using Ubuntu 10.04 but stumble on problems with loosing wifi connection as soon as I use a bluetooth headset (tried 2 different ones) and also my wifi connection shows around 60% wich is a bit weird when I am 3 meter from the router?

Decided to try out Linux Mint 9 instead which is based on latest Ubuntu. The distro is easier to use for me, but still have the same problems with wifi and bluetooth.

When using a bluetooth headset I get disconnected and it refuse to reconnect even tho the password is the same. But as soon as I turn off bluetooth I can connect to my access point again?

Also the bluetooth signal is really weak. No more than 2 meter from the computer or else the sound starts to break.

Last thing that also bothers me allot is how slow my samba server is. I can download a file from my shared samba folder in full speed at 2-3mb/s, but after just a minute it drops down to 100kb/s and everything gets slow. If I disconnect and then reconnect I am back at full speed on the samba server, but then it starts to be slow again. I don't know why it is like this and tried to get help at the Linux Mint forum, but guess there are more users with a Dell XPS M1330 here.

Is there a way to save logfile for wifi, bluetooth and samba problems? Wich I could help out more but this is all I get.

---

