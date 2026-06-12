---
title: "Vostro V13 Networking Issues"
date: 2010-09-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wjhobbs on 2010-09-28
I recently acquired a Dell Vostro V13 with Windows 7 Professional installed. Windows seemed to work well. (Except that I had a problem removing the Trend Micro 30-day trial security product. It demanded a password to uninstall! After about an hour on the phone with Dell support they finally determined that the uninstall password is the single digit ‘1’.)

I then proceeded to install an Ubuntu 10.04-based Linux (LinuxMint 9) system in dual boot mode. Everything went well except that I had no network communications capability in Linux. Since there was no CD/DVD drive I did this install from a USB drive. Poking around led me to the fact that the Ethernet card was a RealTek RTL8111/8168B and the wireless card was a Broadcom BCM4312. But neither the wireless nor the Ethernet port were functional. 

Attempts to install the proprietary hardware drivers failed because I had no communications capability. I was unable to apply any upgrades.

Fortunately I had an Internet Air Card which was recognized. At that point I applied waiting upgrades, including the drivers for the network cards. The available proprietary drivers included: Broadcom b43 wireless driver, Broadcom STA wireless driver, and RealTek RTL-8168 Gigabit Ethernet driver. The b43 was the recommended wireless driver, so I installed it as well as the RTL-8168 Ethernet driver.

The wireless driver would not recognize my hidden wireless network (SSID Broadcast disabled on my hotspot). Even when I set the hotspot to broadcast the SSID, communication was sporadic. Sometimes I would get a connection but no data would flow. At other times I could not even get a connection established. It seemed that many times (but not always) when I logged in to Windows, initiated some network activity, and then rebooted into Linux, the connection worked for a while but then would die.

On top of that, the Ethernet connection always showed as ‘disconnected’ whether I had a cable plugged in or not. I was NOT a happy camper.:(

After browsing around the Dell Ubuntu forums I encountered a thread that indicated that the “wake-on-lan” feature might interfere with the 8168 Ethernet card. It also indicated that any time Windows booted it probably set the wake-on-lan feature. So I proceeded to disable this feature:[INDENT]In Windows I went into Control Panel and opened the Device Manager, expanded the Network adapters node, selected the RealTek controller, displayed the Properties and clicked on the Advanced tab. I set the ‘Shutdown Wake-On_Lan’ value to ‘disabled’. Then I went to the Power Management tab and unchecked the option to “Allow the computer to turn off this device to save power”. (My rationale for the last action was based on ignorance. I did not know if the setting would be stored in the Ethernet card and carry over to the Linux session and shut off the card at an inappropriate time.)[/INDENT][INDENT]I also disabled Wake-on-lan in the BIOS. (Click F2 while the Dell boot splash screen is visible and adjust the setting.)[/INDENT]When I booted Linux I had a working Ethernet connection.

But the unreliable wireless connection was still a problem. Despite the fact that the b43 driver was supposed to be the recommended one I decided to try the other one. I removed the b43 driver and activated the STA driver.

After a reboot, both wired and wireless communications channels appeared to be working properly. The STA driver even connected to the hidden network.

I am now enjoying my Vostro V13.:)

---

