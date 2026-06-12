---
title: "Bluetooth mouse not working after upgrading to 11.04"
date: 2011-05-04
forum: Desktop Environments
---

### Post by glalejos on 2011-05-04
Hi,

I've just upgraded my Ubuntu installation to 11.04 and my bluetooth mouse (Logitech Bluetooth Laser Travel Mouse) is not correctly recognized at start-up.

Every time I restart my computer I have to run the following commands in a terminal
```

sudo killall bluetoothd
sudo bluetoothd

```
and then remove and set up the bluetooth mouse (using an auxiliary USB mouse, of course :P ) through the bluetooth preferences dialogue.

Has anyone experienced this behaviour? Any clue on how to solve it? If not... any suggestion on how to carry out the remove/set-up process using a non-interactive shell script?

Thanks in advance,

Guillermo

---

### Post by glalejos on 2011-05-14
Hi,

According to launchpad ([https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/762964](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/762964)) this is a known bug, and its importance is set to "critical". It will probably be solved soon.

Cheers,

Guillermo

---

### Post by bcrawford on 2011-05-17
Been having the same issue with my Kensington USB Bluetooth adaptor and my Razor Orochi. I've been using

sudo /etc/init.d/restart bluetooth

and then having to remove the mouse from the bluetooth settings and re-pair it every boot. I hope they get it fixed soon.

---

### Post by glalejos on 2011-05-17
Hi,

Glad to find that I'm not alone :)

The best thing you can do is sign in [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/762964]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/762964") and click the "This bug affects # people" link. This way, Ubuntu developers will have an accurate indicator of how many people is experiencing the problem.

In the meanwhile, you might be interested in creating a shell script that executes the following commands:
```

sudo killall bluetoothd
sudo bluetoothd
bluetooth-properties

```

You will be asked once for your password, and then all the relevant services will be restarted and the Bluetooth devices dialogue will pop up.

Hope it helps someone.

Best,

Guillermo

---

### Post by bcrawford on 2011-05-17
I am somewhat new to the Ubuntu scene. Perhaps you could walk me through setting up a shell script. I played with it earlier but didn't know the correct way to go about creating the file or giving it the permissions it needs to function. :-k

Thanks

---

### Post by glalejos on 2011-05-20
Of course :)

[LIST=1]
[*]Open a text editor and paste the following lines in it (insert a new line at the end)
```

sudo killall bluetoothd
sudo bluetoothd
bluetooth-properties

```
[*] Save the file to your hard disk (I named it reset_bluetooth.sh). I suggest you place it directly into your home directory so you can easily find it later
[*] Navigate to the folder where you stored the file, right click on the file and select "Properties". Switch to the "Permissions" tab and make sure that the owner user of the file (you) has "Read/Write" access
[/LIST]
The script is now ready to be used. To execute it without using the mouse you can press the super key (i.e. "Windows" key), type "terminal" and press enter. If you saved the script in your home directory you can execute the command "./reset_bluetooth.sh" (the "./" is important) and follow the instructions. If you didn't save the script in your home directory you will have to use the "cd" command to change into the appropriate directory.

Kind regards,

Guillermo

---

### Post by glalejos on 2011-08-31
The problem was solved after updating my Ubuntu installation a couple of weeks ago.

Thanks Unbuntu team!!

---

