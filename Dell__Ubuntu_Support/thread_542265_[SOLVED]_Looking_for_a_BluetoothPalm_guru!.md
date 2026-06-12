---
title: "[SOLVED] Looking for a Bluetooth/Palm guru!"
date: 2007-09-03
forum: Dell  Ubuntu Support
---

### Post by perryrt on 2007-09-03
OK, folks - I've been trying to get my Treo 700p to work and play with my Ubuntu/Dell 1420n. I feel that this is reasonably achievable, as I was doing the same thing with my old (and now dead) Thinkpad (it was running Dapper.)

Anyway, I was following the instructions here:

[ [COLOR="Blue"]Synchronize your PalmOS® Handheld over Bluetooth in Linux [/COLOR]](http://howto.pilot-link.org/bluesync/index.html)

...and everything was working fine until step 6.2 - Configuring and Testing.

I know the adapter in the Dell is working because I can "see" it and "trust" it from the Treo (it took a while to figure out the passkey business, but that's another episode), and also because:

```
$ hciconfig
hci0:   Type: USB
        BD Address: 00:19:7E:D8:C6:CB ACL MTU: 1017:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:3165 acl:60 sco:0 events:97 errors:0
        TX bytes:1980 acl:60 sco:0 commands:53 errors:0
```

Also, I can "see" the Treo from the computer:
```
$ hcitool scan
Scanning ...
        00:07:E0:BD:A9:4C       ToddsTreo700

```

However, according to the HOWTO, I'm supposed to be able to issue the command ***hcitool info 00:07:E0:BD:A9:4C*** to the Palm and have it respond  over Bluetooth with information.

However, all I get is:
```

$ hcitool info 00:07:E0:BD:A9:4C
Requesting information ...
Can't create connection: Operation not permitted
```

and the rest of the HOWTO falls apart from there.

...so I'm a bit stuck. What am I missing? Can anyone help? Is anyone doing this successfully? I would appreciate a steer in the right direction. 

Frankly, this is a "nice to have" rather than a "must have", but it does mean that I would get to go on the road with one less wire, so I'd classify this as a Good Thing if someone can help.

---

### Post by peterLinux on 2007-09-04
I am not the guru but it looks like a permission issue.
First thing I would try is
sudo 
before the command in question.

Next make sure your Palm is set allow bluetooth coming in.

Regards

---

### Post by perryrt on 2007-09-04
[QUOTE="PeterLinux"]I am not the guru but it looks like a permission issue.
First thing I would try is
sudo
before the command in question.[/QUOTE]

Duh. I should have thought of that one.

Sure enough, I got back:

```
$ sudo hcitool info 00:07:E0:BD:A9:4C
Password:
Requesting information ...
        BD Address:  00:07:E0:BD:A9:4C
        LMP Version: 1.2 (0x2) LMP Subversion: 0x309
        Manufacturer: Broadcom Corporation (15)
        Features: 0xbf 0xfe 0x0d 0x00 0x00 0x00 0x00 0x00
                <3-slot packets> <5-slot packets> <encryption> <slot offset> 
                <timing accuracy> <role switch> <sniff mode> <RSSI> 
                <channel quality> <SCO link> <HV2 packets> <HV3 packets> 
                <u-law log> <A-law log> <CVSD> <power control> 
                <transparent SCO> 

```

...so problem solved. 

If it talks like a guru, and quacks like a guru...it must be a duck! :)

Thanks, peter.

---

### Post by peterLinux on 2007-09-04
> If it talks like a guru, and quacks like a guru...it must be a duck! 

No duck in this case, but Canadian goose ;-) Glad I could help...

---

### Post by jamaas on 2007-09-07
I have the same problem but am new enough not to know how to fix the permission problem .... and yes I am originally from Ontario ....

What permissions do I need to change to get this to work as user rather than root?

Thanks

Jim

---

### Post by perryrt on 2007-09-07
> What permissions do I need to change to get this to work as user rather than root?


Well, on a temporary basis, I can answer. On a permanent basis, that's above my head. I apologize if I'm covering territory you already know....

For reasons that still aren't quite clear to me, Ubuntu doesn't use a classic "root"/"users" structure. However, what it does do is make a lot of use of a command that allows you to issue root-level commands from a normal user-level account. The command is ***sudo***, which is short for Super User DO.

It's normally tacked on to the command in front. So, looking at the above,

***hcitool info 00:07:E0:BD:A9:4C*** 

gave me an error because I was running it as a user, but using

[B][I]sudo hcitool info 00:07:E0:BD:A9:4C
[/I][/B] 
returned what I was looking for. Now, I did have to input my password to get super-user priveleges, but it was the same as my login password, not some special one, so that was pretty routine.

...and the sudo privelege lasts for a while once issued, too - I think 15 minutes by default (?)

Is that the info you were looking for?

---

### Post by ravl on 2008-05-29
Hello!
This tutorial is very good, I followed it and can connect succesfully with my Tungsten E2 to Kubuntu 8.04. But I can't surf the web.
I think it might have to do with the dund config file. I'm using the IP I get from DHCP for my local machine, and the DNS I use to connect to the web everyday.
The Palm IP can be anything, right?

Thanks in advance

Rene

---

### Post by ederic on 2008-06-24
I should try this tonight. Wondering if it will work with JPilot. :)

---

