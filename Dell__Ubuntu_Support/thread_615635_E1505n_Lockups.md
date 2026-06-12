---
title: "E1505n Lockups"
date: 2007-11-17
forum: Dell  Ubuntu Support
---

### Post by DonA on 2007-11-17
I've had my E1505n since July.  It's been back to Dell twice: once for a loose connector between the LCD and nVidia card, and once for a new motherboard after the familiar problem with the headphone jack killed my speaker audio.

Now I'm having spurious lockups that freeze the system, requiring a power off and reboot to recover.  For the life of me, I can't figure what's causing this.  I've been unable to isolate a potential cause, as it happens whether or not I'm running wireless or wired, with the (added) Bluetooth interface on or off.  I thought perhaps VMPlayer might have been the culprit, but the lockups occur whether or not I've started a VM session.

I recently upgraded from Dell-installed Feisty to Gutsy, hoping that something in the new version would magically fix the problem, but alas, the lockups continue in Gutsy.

I thought perhaps the memory (2GB installed) might be flaky.  (My daughter's 600m used to lockup until I upgraded her RAM from the factory 233mhz devices to 333mhz.)  But all the system diags pass in the E1505n.

I'm left to wonder if I have another hardware problem, or if there's something in my Ubuntu (Feisty or Gutsy) config  that's messing things up.

I find nothing obvious in /var/logs, but I'm no expert in analyzing these.  Any clues?

Thanks:   ..DonA

---

### Post by Linicks on 2007-11-17
It seems you done most things to analyse this, but overheating.

Are the fans all working OK?

Nick

---

### Post by DonA on 2007-11-17
Hi Nick,

Yes, the fan (or fans--i8kmon indicates that there are two, but I've read that there's only one) comes on and increases speed periodically.  I lowered the threshold to keep the temp below 45C, but the lockups still occur.

..DonA

---

### Post by DonA on 2007-11-30
Ah.  I think I've found the culprit, but unfortunately no real fix.

I use Apani's VPN client to establish a secure tunnel to the office.  During periods of heavy network usage, if the tunnel is up, the PC is prone to lockup.  With the tunnel disconnected, the PC seems rock-solid.  

I suspect the problem is with the Apani client.  Co-workers who use various Linux's (Ubuntu, Fedora, SuSE, RHEL) all seem to experience similar lockups. Unfortunately, while Apani releases frequent upgrades for Windows, they seem to have abandoned Linux--no new releases in an aeon.  

..DonA

---

