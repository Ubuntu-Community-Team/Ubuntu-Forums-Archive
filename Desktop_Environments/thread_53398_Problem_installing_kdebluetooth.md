---
title: "Problem installing kdebluetooth"
date: 2005-07-31
forum: Desktop Environments
---

### Post by fatalglitch on 2005-07-31
Whenever i try to install kdebluetooth, I get :

> root@callahant_lt:~ # apt-get install kdebluetooth
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdebluetooth: Depends: libopenobex-1.0-0 (>= 1.0.0-rel) but it is not installable
E: Broken packages
root@callahant_lt:~ # 

I have tried < apt-get install libopenobex(1) > and it cannot find the files.

How do I install the required libraries?

Thanks,
Tom Callahan

---

### Post by SGC on 2005-07-31
libopenobex is in the universe repository, to enable it, 
- open /etc/apt/sources.list
- uncomment the following lines (remove #):
```

# deb http://us.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

```

Save the file, and then run these commands:
```

apt-get update
apt-get install kdebluetooth

```

---

### Post by c0rderr0y on 2005-07-31
hmmm it says

E: Couldn't find package kdebluetooth

---

### Post by SGC on 2005-07-31
[QUOTE=c0rderr0y]hmmm it says

E: Couldn't find package kdebluetooth[/QUOTE]
 In order to install kdebluetooth via apt-get you need to add this repository to sources.list:
```

# KDE-Bluetooth
deb http://fred.hexbox.de/debian ./

```

---

### Post by c0rderr0y on 2005-07-31
you are the man imma go try it out now

now its giving me some sdpd error anyone know what this is?

---

### Post by SGC on 2005-07-31
[QUOTE=c0rderr0y]you are the man imma go try it out now[/QUOTE]
 Thanks, I hope it works for you

---

### Post by c0rderr0y on 2005-07-31
Is there anything I am doing wrong?

---

### Post by SGC on 2005-07-31
[QUOTE=c0rderr0y]Is there anything I am doing wrong?[/QUOTE]
 Could you post the exact error message

---

### Post by c0rderr0y on 2005-07-31
it happens when i boot up hold on let me reboot

its an error from KbluetoothD

You may replace bluez's pin helper program; it is located in /usr/lib/kdebluetooth now.

I also get an error of;

Failed to connect to SDP server

---

### Post by c0rderr0y on 2005-08-02
bump SGC can you help?

---

### Post by ltmon on 2005-08-02
I don't know what the SDP related message means, but the pin helper message is telling you to replace the default bluez pin-helper with the one provided by kde-bluetooth.

You do it by editing the file /etc/bluetooth/hcid.conf, and changing the following setting:

pin_helper /usr/local/lib/kdebluetooth/kbluepin;

The docs on kde-bluetooth.sourceforge.net are pretty good, and their recommended hcid.conf setup got everything working just fine for me.

Cheers,

L.

---

### Post by SGC on 2005-08-02
[QUOTE=c0rderr0y]bump SGC can you help?[/QUOTE]
 Sorry I had no idea about the SDP error message

---

### Post by c0rderr0y on 2005-08-03
hmmm 
my kbluepin resides in

/usr/lib/kdebluetooth/kbluepin

NOT pin_helper /usr/local/lib/kdebluetooth/kbluepin

and if i change it to either it still gives me the error

also it works when i first install it ieven though it gives me the error then after i restart it says it can't find a blue tooth device..... any takers?

also i dont think sdpd or hcid is running how do i check this?

---

### Post by ltmon on 2005-08-03
Try:

/etc/init.d/bluez-utils restart

(I think)

This will restart the bluetooth related daemons.

I can probably give better answers when I get home tonight to look at my home PC.

L.

---

### Post by c0rderr0y on 2005-08-03
hmm doesnt work but when i try kbluetoothd from the terminal it gives me the error

kbluetoothd: WARNING: No usable bluetooth device found.

yet it was working when i 1st installed kbluetooth  :| 
restarting broke it  :mad:

---

### Post by c0rderr0y on 2005-08-04
UPDATE:

when i type hciconfig i get this:

hci0:   Type: USB
        BD Address: 00:00:00:00:00:00 ACL MTU: 0:0  SCO MTU: 0:0
        DOWN
        RX bytes:0 acl:0 sco:0 events:0 errors:0
        TX bytes:0 acl:0 sco:0 commands:0 errors:0

so I'm guessing its not seeing my bluetooth hardware which is weird because it had something before when i restart it.

---

### Post by ltmon on 2005-08-04
What kind of bluetooth hardware do you have?

L.

---

### Post by c0rderr0y on 2005-08-04
Its a dell truemobile  350 internel

---

### Post by c0rderr0y on 2005-08-05
UPDATE:

Okay I got it working but its still asking me to change bluezpin to kbluepin i think it has to to with permisions because I already have changed this in the hcid.conf file...

---

### Post by c0rderr0y on 2005-08-06
no matter what i set pin_helper to in /etc/bluetooth/hcid.conf its always doing that F-ing 

You may replace bluez's pin helper  program with kbluepin; it is located in /usr/lib/kdebluetooth now.

ITS ALREADY CHANGED~!!! this is driving me up the wall..... ](*,)

---

### Post by GeneralZod on 2005-08-06
> **c0rderr0y]no matter what i set pin_helper to in /etc/bluetooth/hcid.conf its always doing that F-ing 

You may replace bluez's pin helper  program with kbluepin said:**
> (*,)

Something's obviously wrong there, as mine works fine :) Please post your /etc/bluetooth/hcid.conf file and we'll see how it differs from mine :)

---

### Post by c0rderr0y on 2005-08-06
# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security auto;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # PIN helper
        pin_helper /usr/lib/kdebluetooth/kbluepin;

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
        class 0xff0101;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;

        # Default link mode
        #   none   - no specific policy
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        #
        #lm accept,master;
        #
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        #
        #lp hold,sniff;
        #
        lp rswitch,hold,sniff,park;

        # Authentication and Encryption
        #auth enable;
        #encrypt enable;
}

---

### Post by GeneralZod on 2005-08-06
[QUOTE=c0rderr0y]
hcdi.conf
[/QUOTE]

Hmmm...we're pretty much identical :/

Have you tried just running 

```

/usr/lib/kdebluetooth/kbluepin

```

from the command-line? Have you done 
```

sudo /etc/init.d/bluez-utils restart

```

 and restarting the kbuetoothd daemon?  Beyond that, I'm afraid I have absoluely no idea, sorry :(

---

### Post by c0rderr0y on 2005-08-06
i think that error keeps popping up even though its been changed.....

---

### Post by c0rderr0y on 2005-08-07
quick question when you guys changed it did the pop up of the error stop?

---

### Post by agentpt on 2005-08-26
I have exactly the same problem...Have followed and tried everything in this thread, but still cant get rid of it . Did you find a solution?

---

