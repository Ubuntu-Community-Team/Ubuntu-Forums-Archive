---
title: "bluetooth printer problems"
date: 2006-04-26
forum: Desktop Environments
---

### Post by bflores on 2006-04-26
Having a problem with breezy/dapper flights 6 

I have setup a bluetooth printer on breezy and it worked perfectly.
i have moved to dapper flight 6 Is the bluetooth broken i think not my bluetooth mouse works fine and loads on startup I am thinking i have settings problem with bluez cups here are my setting.  I am running version 2.25 of bluez.
Any ideas help !!!
 RFCOMM configuration file.
#

 rfcomm0 {
        # Automatically bind the device at startup
        bind yes;

        # Bluetooth address of the device
        device 00:0C:78:50:56:65;

        # RFCOMM channel for the connection
        channel 1;

        # Description of the connection
        comment "Bluetooth Printer";
#}
hcid.conf 
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
        pin_helper /usr/bin/bluez-pin;

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
        class 0x3e0100,0x6 ;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;

        # Default link mode
        #   none   - no specific policy
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept,master;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;
printers.conf 
# Written by cupsd on 2006-04-26 09:58
<Printer DeskJet-460>
Info DeskJet-460
DeviceURI ipp://bluetooth:/000C78505665/
State Idle
StateTime 1146063471
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer

services
 4824 ?        00:00:00 hcid
 4828 ?        00:00:00 sdpd
 4839 ?        00:00:00 hidd
cupsd is also running 

i had this working perfectly upgrading is not always the answer i guess ](*,)

---

