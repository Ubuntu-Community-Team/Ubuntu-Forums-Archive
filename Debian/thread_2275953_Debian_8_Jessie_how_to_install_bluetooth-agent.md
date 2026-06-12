---
title: "Debian 8 Jessie how to install bluetooth-agent"
date: 2015-04-29
forum: Debian
---

### Post by erotavlas on 2015-04-29
Hi,

I recently installed Debian 8 Jessie on my virtualbox in order to try it. I have a problem with bluetooth. I cannot find bluetooth-agent even if I installed bluetooth exactly in the same way of Debian 7.5 Wheezy with the command

```

aptitude install bluetooth bluez

```

I verified here [https://packages.debian.org/search?searchon=contents&keywords=bluetooth-agent&mode=path&suite=stable&arch=any](https://packages.debian.org/search?searchon=contents&keywords=bluetooth-agent&mode=path&suite=stable&arch=any) that bluetooth-agent is included in bluez package.

Where could be the problem?

Thank you

---

### Post by TheFu on 2015-04-29
virtual box provides "virtualized hardware" to the guestOS - so ... if there isn't any bluetooth virtual hardware provided, it will not be seen.  The real hardware on the physical machine *almost always* has nothing to so with what a VM sees.

---

### Post by erotavlas on 2015-04-29
> **TheFu said:**
> virtual box provides "virtualized hardware" to the guestOS - so ... if there isn't any bluetooth virtual hardware provided, it will not be seen.  The real hardware on the physical machine *almost always* has nothing to so with what a VM sees.

I do not think that the problem is matter of virtual machine or driver since I also installed the same operating system directly on a PC and it has the same behaviour. I think that Debian Jessie does not provide bluetooth-agent module.

---

### Post by TheFu on 2015-04-29
Sorry - perhaps I wasn't  clear.  Did you configure bluetooth hardware for the VM in some way - this would be a virtualbox setting on the hostOS, not something inside the GuestOS/ClientOS/VM.

Of course, if you installed directly on hardware that has bluetooth hardware, then it becomes a normal question of applications, manager, and driver support for the device. I would use **lshw** to see if the driver is located - but I won't bother doing this inside a VM.  Only do it on the real host running on physical hardware - that actually has a Bluetooth device.

---

### Post by erotavlas on 2015-04-29
I installed again Debian 7.5 Wheezy on a PC and then I upgraded it to Debian Jessie 8.0; unfortunately after this operation, the bluetooth-agent is disappeared. So this seems to confirm that Debian Jessie 8.0 does not have bluetooth-agent.
I added the following repository:
```

deb http://ftp.debian.org/debian/ jessie main contrib non-free

```
and then I typed
```

aptitude dist-upgrade

```
Is it possible to install bluetooth-agent on Debian 8.0 Jessie? If yes, how?

---

### Post by arochester on 2015-07-19
"Using bluetooth-agent

Bluetooth-agent is part of package bluez if you use Debian testing or unstable, so should already be installed.

Just start bluetooth-agent (as root), giving an arbitrary PIN, such as 4835:

# bluetooth-agent 4835
Then, as described above, choose something like the "setup", "connect" or "Bluetooth" menu on the device to be paired, and search for Bluetooth devices. Select your computer once found; the device should prompt you for a PIN. Now enter the PIN you gave to bluetooth-agent, and pairing is completed.

Note: Instead of initiating the pairing process from the phone, you can also initiate it from the computer. Start bluetoogh-agent as explained above, then run a command that will try to connect to the phone, e.g.

rfcomm connect hci0 <phone address>
where <phone address> is your phone's bluetooth address, as shown by hcitool scan (note that this will only work if the phone is discoverable, though the computer need not be). This will force a connection from computer to phone, which should cause the phone to ask you to confirm the connection attempt by prompting for a PIN. Enter the pin you used with bluetooth-agent." --- [https://wiki.debian.org/BluetoothUser](https://wiki.debian.org/BluetoothUser)

---

### Post by erotavlas on 2015-09-11
> **arochester said:**
> "Using bluetooth-agent

Bluetooth-agent is part of package bluez if you use Debian testing or unstable, so should already be installed.

Just start bluetooth-agent (as root), giving an arbitrary PIN, such as 4835:

# bluetooth-agent 4835
Then, as described above, choose something like the "setup", "connect" or "Bluetooth" menu on the device to be paired, and search for Bluetooth devices. Select your computer once found; the device should prompt you for a PIN. Now enter the PIN you gave to bluetooth-agent, and pairing is completed.

Note: Instead of initiating the pairing process from the phone, you can also initiate it from the computer. Start bluetoogh-agent as explained above, then run a command that will try to connect to the phone, e.g.

rfcomm connect hci0 <phone address>
where <phone address> is your phone's bluetooth address, as shown by hcitool scan (note that this will only work if the phone is discoverable, though the computer need not be). This will force a connection from computer to phone, which should cause the phone to ask you to confirm the connection attempt by prompting for a PIN. Enter the pin you used with bluetooth-agent." --- [https://wiki.debian.org/BluetoothUser](https://wiki.debian.org/BluetoothUser)

I cannot find bluetooth-agent on my Debian 8.0 Jessie, but only bluetoothctl.

---

### Post by arochester on 2015-09-12
Using bluetoothctl

"If bluetooth-agent is not available, try bluetoothctl:

Start the bluetoothctl interactive command. Enter "help" to get a list of available commands.

Turn the power to the controller on by entering "power on". It is off by default.
Enter "devices" to get the MAC Address of the device with which to pair.
Enter device discovery mode with "scan on" command if device is not yet on the list.
Turn the agent on with "agent on".
Enter "pair MAC Address" to do the pairing (tab completion works).
If using a device without a PIN, one may need to manually trust the device before it can reconnect successfully. Enter "trust MAC Address" to do so.
Finally, use "connect MAC address" to establish a connection." -  [https://wiki.debian.org/BluetoothUser](https://wiki.debian.org/BluetoothUser)

---

### Post by erotavlas on 2015-09-12
> **arochester said:**
> Using bluetoothctl

"If bluetooth-agent is not available, try bluetoothctl:

Start the bluetoothctl interactive command. Enter "help" to get a list of available commands.

Turn the power to the controller on by entering "power on". It is off by default.
Enter "devices" to get the MAC Address of the device with which to pair.
Enter device discovery mode with "scan on" command if device is not yet on the list.
Turn the agent on with "agent on".
Enter "pair MAC Address" to do the pairing (tab completion works).
If using a device without a PIN, one may need to manually trust the device before it can reconnect successfully. Enter "trust MAC Address" to do so.
Finally, use "connect MAC address" to establish a connection." -  [https://wiki.debian.org/BluetoothUser](https://wiki.debian.org/BluetoothUser)Than

Thank you for the answer. I know how to use bluetoothctl, I only would like to know if bluetooth-agent is deprecated.

---

