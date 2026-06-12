---
title: "Bluetooth mouse problems"
date: 2007-11-14
forum: Dell  Ubuntu Support
---

### Post by fisting_mayfield on 2007-11-14
So we got the XPS m1330 yesterday, and OOB it mostly seems to be OK with Ubuntu, but I can't get the Bluetooth module working.  It's up in my notification section, and when I right click on the icon and 'browse devices' both my phone and mouse are there, however trying to connect them gives the error message "Obex://[00:07:61:94:3b:ca]" is not a valid location, please check the spelling and try again (the letters obviously change as I try to connect different devices)

---

### Post by sr20ve on 2007-11-14
> "Obex://[00:07:61:94:3b:ca]" is not a valid location, please check the spelling and try again

That's because you can't browse your mouse, it's trying to open it like a storage device.

Make sure your mouse in discover mode and type into the console:

sudo hidd --search

Also check your /etc/default/bluez-utils file and make sure you have HIDD_Enabled 1.

If you don't have a /etc/default/bluez-utils file, look for /etc/default/bluetooth

---

### Post by fisting_mayfield on 2007-11-15
Thankyou.  Now it works perfectly.

---

### Post by borinotborinot on 2007-11-18
Hi!

When I write sudo hidd --search , Ubuntu detect my mouse and then I can use the mouse. But i want that Ubuntu detect my mouse always. Now i have to write this sentece everytime. How can I make it automatic? 

This is my /etc/default/bluetooth  :

BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="-i 00:07:61:93:FD:C4 --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.

############ COMPATIBILITY WITH OLD BLUEZ-PAN
# Compatibility: if old PAN config exists, use it
# rather than this file.
if test -f /etc/default/bluez-pan; then
    . /etc/default/bluez-pan
    return
fi
############

############ DUND
#
# Run dund -- this allows ppp logins. 1 for enabled, 0 for disabled.
DUND_ENABLED=0

# Arguments to dund: defaults to acting as a server
DUND_OPTIONS="--listen --persist"

# Run dund --help to see the full array of options.
# Here are some examples:
#
# Connect to any nearby host offering access
# DUND_OPTIONS="--search"
#
# Connect to host 00:11:22:33:44:55
# DUND_OPTIONS="--connect 00:11:22:33:44:55"
#
# Listen on channel 3
# DUND_OPTIONS="--listen --channel 3"

# Special consideration is needed for certain devices. Microsoft
# users see the --msdun option.  Ericsson P800 users will need to
# listen on channel 3 and also run 'sdptool add --channel=3 SP'

############ PAND
#
# Run pand -- ethernet: creates new network interfaces bnep<N>
# that can be configured in /etc/network/interfaces
# set to 1 for enabled, 0 for disabled
PAND_ENABLED=0

# Arguments to pand
# Read the PAN howto for ways to set this up
# [http://bluez.sourceforge.net/contrib/HOWTO-PAN](http://bluez.sourceforge.net/contrib/HOWTO-PAN)
PAND_OPTIONS=""

# example pand lines
#
# Act as the controller of an ad-hoc network
# PAND_OPTIONS="--listen --role GN"
#
# Act as a network access point: routes to other networks
# PAND_OPTIONS="--listen --role NAP"
#
# Act as a client of an ad-hoc controller with number 00:11:22:33:44:55
# PAND_OPTIONS="--role PANU --connect 00:11:22:33:44:55"
#
# Connect to any nearby network controller (access point or ad-hoc)
# PAND_OPTIONS="--role PANU --search"

############ SDPTOOL
# this variable controls the options passed to sdptool on boot, useful if you
# need to setup sdpd on boot.
# options are ;-separated, i.e. for every ; an sdptool instance will be
# launched
#
# examples:
# SDPTOOL_OPTIONS="add --channel=3 SP" # ericsson P800 serial profile
# SDPTOOL_OPTIONS="add --channel=8 OPUSH ; add --channel=9 FTRN" # motorola
#                                             # object push and file transfer
SDPTOOL_OPTIONS=""

(Sorry for my English :P )

---

