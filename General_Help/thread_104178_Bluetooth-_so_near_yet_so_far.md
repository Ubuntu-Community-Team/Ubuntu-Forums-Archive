---
title: "Bluetooth- so near yet so far"
date: 2005-12-15
forum: General Help
---

### Post by DocFox on 2005-12-15
Hi all

Am rather frustrated, trying to get bluetooth to work with my Sony T630 phone. It *did* work, but suddenly stopped, and now I cant find the original "how to" that I followed.

Basically my PC can see my phone and vice versa. Both via the KDE and Gnome bluetooth GUI. PIN numbers have been exchanged and accepted. 
In konqueror I can see the phone's bluetooth services displayed but I cant use any of them. Similarly I cant use the PUSH to send files to the phone.

If some could point me in the correct direction, I would be very grateful.

My /etc/bluetooth/hcid.conf:

> HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security user;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # PIN helper
        #pin_helper /usr/bin/bluez-pin;
        #pin_helper /usr/bin/bluepin;
        pin_helper /usr/lib/kdebluetooth/kbluepin

        # D-Bus PIN helper
        #dbus_pin_helper;
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        class 0x3e0100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;

        # Default link mode
        #   none   - no specific policy
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;

        # Authentication and Encryption (Security Mode 3)
        #auth enable;
        #encrypt enable;
}


---

### Post by DocFox on 2005-12-19
OK. No-one's replied...

I made some progress, by editing my hciconf file, and so forth.

My phone exchanges PINs and pairs with my computer, and I can send files to my phone using either kbtobexclient or gnome-obex-send.

When I start obexserver and try to send from the phone, i get:

```
conn_request:   bdaddr 00:0F:DE:EC:E9:84
conn_complete:  status 0x21

```

Annoying this. The only thing that *just worked* in SUSE that doesnt in ubuntu! I am guessing that I somehow need to switch on some bluetooth services on my computer, but I've got stuck in how to do this. I'm sure there is something very simple to do. Can anyone help?

BF

---

### Post by fannymites on 2005-12-19
Try changing # Local device class to ```
class 0x100100;
```
If this doesn't work, when you come to send a file to the computer and it asks for the recipient, let it finish searching then refresh and let it find ubuntu again and try sending then.  After that try sending to the phone again.

A couple of links that may help - 
[http://ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth)
[http://www.ubuntuforums.org/showthread.php?t=28312&highlight=gnome-bluetooth](http://www.ubuntuforums.org/showthread.php?t=28312&highlight=gnome-bluetooth)

[NOTE] If you are still using suse along with ubuntu, I have encountered quite a lot of problems using bluetooth on multiple distro's.  For instance, it works fine in suse and dapper then I try it in breezy and it's stopped working.  I then get it working again in breezy and it will stop working in dapper or suse.  It seems to be working fine in all three now but I don't know why.

---

### Post by DocFox on 2005-12-19
Dear fannymites

First, as doctor, I recommend permethrin ;) 

[QUOTE=fannymites]Try changing # Local device class to ```
class 0x100100;
```
If this doesn't work, when you come to send a file to the computer and it asks for the recipient, let it finish searching then refresh and let it find ubuntu again and try sending then.  After that try sending to the phone again.
[/QUOTE]

I did that already, believe it or not. Still no joy, no matter how many times I restart bluez or obex server or whatever.

I'm really only using ubuntu now. I switched on SUSE today to look at the hciconf file and so forth, which didnt really help me.

Do you know what **conn_complete:  status 0x21** means?

---

### Post by fannymites on 2005-12-19
conn_complete:  means that the connection was sucessful,  status 0x21 I'm not so sure.  For me the status changes constantly so it could be signal strength possibly.

You could try changing Security Manager mode to auto, see if that helps.
Just out of interest, make sure no bluetooth programs are running then restart bluetooth ```
/etc/init.d/bluez-utils restart
```
Next, start kbluetoothd and once it's running, click on the system tray icon (if using gnome and the icon doesn't appear, open another terminal and type kbluetoothd again)
Now, assuming konqueror opens ok and it finds your phone, click on obex file transfer and see what happens? Does it connect? if so, does it let you browse your phone but then stalls and fails when trying to copy them across to your computer or does it fail to see what's on the phone at all? 

Now do ```
killall kbluetoothd
``` then ```
/etc/init.d/bluez-utils restart
```
Now launch kbluetoothd again but this time, find a file on your phone and 
 send via bluetooth but let it finish searching and refresh then select ubuntu.  What message do you get?

---

### Post by DocFox on 2005-12-20
Well!

That actually worked - and I have no idea why! 

Changes the hcid.conf as you suggested.

First time around, in konqueror I see the phone's services, and also the picture, sound, theme directories at [FONT="Courier New"]obex://[00:0f:de:ec:e9:84]:7/[/FONT], but I get a connection failed dialog when trying to show the actual pictures etc.

After shutting down and restarting, I managed to send a photo directly from my phone to the computer. Still no joy via konqueror, though.

This is all very mysterious to me. But at least it works. So a very large thank you.

Do I have to do this palava every time/write a script for this?
Also, any clues as to how to save my addressbook from the phone/sync to evolution?

---

### Post by aamukahvi on 2005-12-20
I have a K700i. I managed to get Evolution syncing with multisync and irmc. Make a sync pair with "IrMC Mobile Device" and "Ximian Evolution 2" and you're good to go.

Unfortunately mine only synced the phonebook once, and on subsequent attempts it would tell me that getting changes from Evolution had failed. Unless I can solve this it's not very useful.

---

