---
title: "Bluetooth Phone as modem"
date: 2006-03-30
forum: Desktop Environments
---

### Post by rbrugman on 2006-03-30
Hello,
I've tried using the search feature, but I haven't found exactly what I'm trying to do.  I want to know if its possible to use my Sony Ericsson T616 as a 56K (or whatever it may connect at) modem via my D-Link DBT-120 bluetooth adapter.  I don't have GPRS service and don't want to pay the data fee, but I'd like to be able to dial in every once and a while when I'm on the road.  Is this even possible?  If it is, does anyone know how to set it up?


Thanks!!!

Robert

---

### Post by GeneralZod on 2006-03-30
Not much help, I'm afraid, but I've actually done this with my Nokia 6021 and my dial-up ISP (opensurfuk.com) - it was pretty easy.  I think the Nokia's all have hardware modems, though, which is pretty much essential - I don't know whether the Ericsson's have these, though.

Basically, I amended my /etc/bluetooth/rfcomm.conf like this:

```

rfcomm0 {
        bind yes;
        # Bluetooth address of the device
        device XX:XX:XX:XX:XX:XX;
        # RFCOMM channel for the connection
        channel 1;
        # Description of the connection
        comment "Phone Dial Up";
}

rfcomm1 {
        bind yes;
        # Bluetooth address of the device
        device XX:XX:XX:XX:XX:XX;
        # RFCOMM channel for the connection
        channel 3;
        # Description of the connection
        comment "Phone Serial";
}

```

where XX:XX:XX:XX:XX:XX is the MAC address of my phone.  Then I crank up kppp (my dial-up ISP's phone number, login and password are already in there) and change the modem to 

/dev/rfcomm0

and Connect as I would if I were using a normal modem! :)

NB: The "rfcomm1" definition might not actually be necessary for this - I use it for sending/ receiving SMS via KMobileTools :)

Also, if this doesn't work right off the bat, then I have no idea how to go about debugging it; sorry! :/

Oh, and you'll have to restart bluez-utils after editing rfcomm.conf.

---

### Post by warpforge on 2006-04-08
My new wiki entry might be of help:
[https://wiki.ubuntu.com/BluetoothDialup](https://wiki.ubuntu.com/BluetoothDialup)

---

### Post by magicrobotmonkey on 2006-05-05
I was able to do this under FC5, I had all the bt packages installaed and got rfcomm connecting, and I was able to go to Netowrking and Add and add a modem pointing at rfcomm0. I can get it all working in ubuntu up to the point when I go to 'Add' in Networking as Ubunutu doesnt have it. What gives? How do I add the modem in Dapper?

---

