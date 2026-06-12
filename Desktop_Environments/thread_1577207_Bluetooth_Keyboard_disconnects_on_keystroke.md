---
title: "Bluetooth Keyboard disconnects on keystroke"
date: 2010-09-18
forum: Desktop Environments
---

### Post by bturrie on 2010-09-18
I have two machines one Ubuntu Lucid and one Kubuntu Lucid. They share a bluetooth keyboard through a KVM switch. As of last week both were working. At this point my KDE machine disconnects from the keyboard on the first keystroke. The Ubuntu machine is still okay. What I've tried/checked so far without success

I can connect my keyboard through Kbluetooth but it disconnects when I start typing. 
The timeout time is set to none. 
I tried rebooting and then reinstalling the software to no avail. 
I replaced the batteries in the keyboard.
Plugging the bluetooth usb adapter directly into the KDE box.
Removing and then adding the trust

I find this in the syslog:

2010-09-18 12:09:42   godel   bluetoothd[1911]   link_key_request (sba=00:1B:DC:0F:F1:E7, dba=00:22:48:87:B3:49)
2010-09-18 12:09:42   godel   bluetoothd[1911]   Encryption failed: Permission denied(0x5)

Here's the kbluetoothrc from my home folder  

[KBlueLock]
Device=
LockEnabled=false
UnlockEnabled=true

[ObexServer]
Autostart=true
savePath=/home/bruce/Documents


Any ideas on how to proceed???

---

### Post by bturrie on 2010-09-18
So, I tried deleting the entry for the keyboard and recreating it. The wizard sees the keyboard and pops up a window to enter a keycode but does not see my keystrokes and then times out. Note I can see the bluetooth interface flash when i press the keys, but the wizard doesn't see anything.

---

