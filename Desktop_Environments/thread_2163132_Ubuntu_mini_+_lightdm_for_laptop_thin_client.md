---
title: "Ubuntu mini + lightdm for laptop thin client?"
date: 2013-07-17
forum: Desktop Environments
---

### Post by rumpek on 2013-07-17
Hi

I'm working on a project for a family member's business which is to develop a laptop thin client solution for 5 employees. The reason I've decided to build my own solution is that there are very few commercial laptop thin clients on the market. I have even tried a commercial product to re-purpose a laptop such as IGEL Universal Desktop Converter (UDC), but the lack of essential features (e.g. usb modem support and full laptop hardware support) makes it unsuitable for our purposes.

I am considering the HP 655 laptop as it has the most barebones features (on the Ubuntu hardware certified list) I've seen of a laptop and the employees don't need anything fancy. In terms of the requirements/ features I need of the thin client solution they are as follows:

- Laptop hardware is fully supported, e.g. graphics, wifi, ethernet, display brightness. I know that Ubuntu has this covered out of the box.

- UTMS USB modem support

- RDP client, e.g. FreeRDP

- VPN client, e.g. L2TP/ IPsec

- Printer support

- Read-only OS that the user cannot modify

- Remote VNC shadowing for employee support

- Remote OS image updating

- Remote configuration updating


Essentially I would like the thin client solution to be as intuitive as possible for users and I envision the following user workflow.

1. When a user powers on the laptop he/she is presented with a login prompt.
2. The user must be connected via either LAN or a UTMS usb modem.
3. When the user logs in, a connectivity check is performed to determine whether LAN or USB modem connected.
4. If a USB modem is detected, the 3G connection is established.
5. Once the laptop has an internet connection (LAN or 3G), a VPN session is established.
6. Finally an RDP session to a terminal server is established.

All the user has had to do is power on the laptop, connect an ethernet or USB modem and supply his/ her login details. A printer connected via USB is forwarded to the Windows terminal server and local printing is possible.

From an administration perspective I need to be able to VNC to the laptop to help the user with any potential problems relating to the laptop OS itself. I also need to be able to update the OS image if possible or at least update the OS configuration such as VPN settings via the updating of a configuration file. This could be done automatically with the thin client pulling the updated config file from say a private Github repo or similar.

I have experience with Ubuntu server although I'm far from an expert, but my Ubuntu desktop experience is limited. Nonetheless, after a lot of googling and a couple of discussions on #Ubuntu someone suggested that Ubuntu mini and lightdm might be a solution to investigate. 

Any advice and help is greatly appreciate as I'm unsure of how to actually build my proposed solution using Ubuntu mini and lightdm.

Thanks ;)

---

### Post by rumpek on 2013-07-18
Anyone have any thoughts on this and can help me out?

---

### Post by rich-ainsworth on 2013-09-26
Hi I am looking to do the same, have you made any headway with this?

---

### Post by rumpek on 2013-09-28
Hi  Yes, I have a custom Ubuntu solution which I have deployed to about 20 users at two companies where I consult. My solution has been in production for about 2.5 months with excellent results.  My solution is not yet ready to be open sourced, but if you'd like to discuss your needs perhaps we can work something out ;) PM me if you'd like to talk in private.

---

