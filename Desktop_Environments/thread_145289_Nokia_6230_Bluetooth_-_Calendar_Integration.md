---
title: "Nokia 6230 Bluetooth - Calendar Integration"
date: 2006-03-16
forum: Desktop Environments
---

### Post by dguido on 2006-03-16
Does anyone know how I can get my Nokia 6230 to sync over bluetooth with a calendar (Evolution or otherwise) in Dapper?  Although I am a very experienced Linux user, I have never had success with bluetooth and would appreciate detailed steps.

I know that the 6230 uses SyncML.  I'm also aware of the Multisync project.  Multisync seems very buggy and I'm not sure it's working.  I'm also aware of OpenSync but I don't see it in Dapper's package repository.  Evolution doesn't seem to have functionality built into it to sync over bluetooth.

Can someone help me out?  Thanks.

---

### Post by dguido on 2006-03-16
I found these Debian packages at OpenSync: [http://www.opensync.org/wiki/download#debian]("http://www.opensync.org/wiki/download#debian")

Has anyone used them before?

It would be nice if someone could give me a big picture overview of how PIM and bluetooth work in Linux because I haven't figured it out yet.

---

### Post by dguido on 2006-03-16
Ok, after more research this forum post is quickly becoming: Can someone explain how I can use Open or Multisync to sync my Nokia 6230 over Bluetooth or USB?  Thanks.

If no one can I'm thinking of making a bounty.  Anyone with me?

---

### Post by JoWilly on 2006-03-16
I can't help you here. My phone is a motorola mpx220 with windows mobile. I think its supposed to sync with the multisync synCE plugin, but I was not able get it working with bluetooth.

Bluetooth seems very primitive with gnome. I have once tried knoppix v.3.x one years ago, bluetooth worked perfectly out of the box. I could even use my mobile phone as a gprs modem with 2 mouse clicks.

I would also be interested to hear more about this. Yes, a bounty would be a good idea.

---

### Post by shu on 2006-03-16
I have Nokia 6310i phone. I'm not sure what its exact capabilities are. However, I managed to connect to it via bluetooth and I'm able to download/upload things to/from the phone. I'm using gnokii though.

Gnokii seems to have some kind of support for VCAL files, so (at least in theory) it is possible to sync phone with evolution in very primitive (manual) way. If I don't find anything better, I may just write some application to automate this.

---

### Post by wout.wepsait.com on 2006-03-16
I think not only gnome is bluetooth is bad but linux bluetooth is bad. Opensync seems to be a good effort but it still sucks.

Is there any change of creating a task force like thing to solve this problem? I have a nokia n70 and I can only use obex to exchange files with my computer. I think this would be a major "selling point" for ubuntu if we had out of the box support for most major smart phones or devicess.

Does anybody have a good idea as to how we could solve this problem. I'm not talking about howto's, I'm talking about end user usability.

---

### Post by shu on 2006-03-16
Well, I think that being able to connect to phone out of the box would be huge step forward. Right now we do have support for bluetooth modules/dongles, but the configuration of bluez-utils is broken. If we had working low level bluetooth connectivity out of the box, we can start thinking about user visible things.

Gnome-bluetooth is a joke. Multisync doesn't look like actively developed anymore. If you are a happy owner of nokia you can always fall back to gnokii, but it also lacks decent gui.

---

### Post by anders.ostling on 2006-03-16
My experience of bluetooth and Linux has been very positive. I have succesfully used my SE P900 as bt modem and can surf over gprs or gsm. I am using ppp and some scripts that I found on the internet. 

Also, bluez and gnome bluetooth works just fine. I can browse for bt devices and use obex to transfer stuff back and forth. 

But as someone else stated, syncing phones is a completely different story. I have struggled with gnokii and multisync, but to no avail. Have never managed to get syncml or anything else to talk to my P900. I would definitively participate in a "bounty" if someone sets that up. The task should then be to enable Symbian phones (P9xxx and others Nokias) to sync (bi-directional) with Evolution.

Cheers
Anders

PS. If someone is interested, I use an USB dongle with a CSR chip

anos@zoolog:~/tmp/wpa/NetworkManager$ hciconfig hci0 version
hci0:   Type: USB
        BD Address: 00:10:60:A4:F6:CC ACL MTU: 192:8 SCO MTU: 64:8
        HCI Ver: 1.1 (0x1) HCI Rev: 0x460 LMP Ver: 1.1 (0x1) LMP Subver: 0x460
        Manufacturer: Cambridge Silicon Radio (10)

anos@zoolog:~/tmp/wpa/NetworkManager$ hcitool scan
Scanning ...
        00:0E:07:C7:7B:D3       OZON
        00:12:EE:97:19:84       K750i

anos@zoolog:~/tmp/wpa/NetworkManager$ sudo hcitool info 00:0E:07:C7:7B:D3
Requesting information ...
        BD Address:  00:0E:07:C7:7B:D3
        Device Name: OZON
        LMP Version: 1.1 (0x1) LMP Subversion: 0x9040
        Manufacturer: Ericsson Technology Licensing (0)
        Features: 0xff 0xfb 0x01 0x00 0x00 0x00 0x00 0x00
                <3-slot packets> <5-slot packets> <encryption> <slot offset>
                <timing accuracy> <role switch> <hold mode> <sniff mode>
                <park state> <RSSI> <SCO link> <HV2 packets> <HV3 packets>
                <u-law log> <A-law log> <CVSD>

---

### Post by shu on 2006-03-16
Ok, guys. Seems like OpenSync is the way to go. As far as I understand opensync is the framework and multisync provides cli/gui interface to it. There is a plugin for evolution syncing and also brand new gnokii plugin. It seems as it may actually work. I'm trying it compile this beast...

Oh, and for those with brand new phones there gnapplet, which is supposed to be installed on the phone and provide gnokii with everything it needs.

Edit:
I've successfully synced my phone calendar with evolution calendar. 

Ingredients:
- gnokii-0.6.12: debs from gnokii.org
- libopensync-0.18: debs built from source from opensync.org
- multisync: debs built from svn from opensync.orgt 
- gnokii-sync: deb built from svn from opensync.org

I may put those debs somewhere if you guys feel brave enough. Gnokii-sync plugin is currently capable of syncing only calendar and even that has some limitations. But hey... it works!!

---

### Post by dguido on 2006-03-17
Yes please post them!

Also, does anyone know how to start a bounty?  I'd want one where the amount is not static and is instead donation based.  Can you do that with Ubuntu's setup?

---

### Post by awakatanka on 2006-03-17
I'm also interested in the debs. Does anyone also have some input on kubuntu bluetoooth and kmobiletools? Have been fighting with it for 2 days and no luck.

Have a nokia 3610i and a siemens sx1 that i want to connect so i can update phonebooks and the calendar.

Installing ubuntu.desktop on my main pc again to test gnokii. 

If ubuntu is targeting laptops/companies and normal users then this needs to be high on the wish list to.

---

### Post by dguido on 2006-03-21
I posted a sample spec for a bounty, please comment on it so I can add it to the official Bounty list.

[http://www.ubuntuforums.org/showthread.php?p=847879](http://www.ubuntuforums.org/showthread.php?p=847879)

---

### Post by shu on 2006-03-22
Ok, guys. I've set up a wiki page with instructions how to get thigs going.

[https://wiki.ubuntu.com/NokiaEvolutionBluetoothSyncing](https://wiki.ubuntu.com/NokiaEvolutionBluetoothSyncing)

Feel free to test it out.

---

### Post by kehan on 2006-03-22
Thanks for this.
Will try this with my 6280

---

### Post by shu on 2006-03-22
I added list of supported phones to the page. You can know find there link to Gnokii Wiki with instructions for various phones, including Nokia 60-series via gnapplet.sis.

---

### Post by wout.wepsait.com on 2006-03-23
I'm Going to test this with my Nokia N70. I really hope this works...

Is this the best place to post my results.....

---

### Post by Totzo on 2006-04-03
Funnily enough with Debian unstable I was able to import my contacts (from a 6230) using gnokii straight into the kontact addressbook using the "import from mobile phone" option. No sign of this in Dapper. Same version of KDE as well I think.

Having said that, I really like evolution and this is the only weakness it has against kdepim in my opinion.

---

### Post by Totzo on 2006-04-03
Might I add a suggestion for the wiki, for us mortals who haven't a scooby doo with vi try the configure like this:

export EDITOR=gedit && msynctool --configure nokia-evo 1

I had a bit of a time before trying this! :)

---

### Post by shu on 2006-04-03
Thanks. Changed it.

---

### Post by Totzo on 2006-04-03
No problem,

great howto by the way, got it to sync my calendar with not too much bother. Any idea when contacts sync may be implemented? I couldn't see any mention of it on the opensync site, but looking at cvs the gnokii-sync plugin was updated a couple of weeks back, must be seeing a bit of development.

---

### Post by shu on 2006-04-04
Last time I checked cvs there weren't any changes since two initial commits. Looks like author doesn't have time at the moment or is developing it outside cvs. If there will be any changes I'll rebuild packages.

---

### Post by wout.wepsait.com on 2006-04-04
Nokia N70 doesn't work....

:(:(:(:(:(:(:(

---

### Post by shu on 2006-04-04
N70 sounds like "advanced phone". Did you try to use gnokii java applet for the your phone? It's supposed to emulate lower-end phones that gnokii is compatible with.

---

### Post by wout.wepsait.com on 2006-04-04
if you're talking about that thing called "gnapplet" i did.
It's been 2 weeks since I tried so I don't remember exectly but it fails when opensync tries to connect to the phone. The problem seems to be with some part of the protocol.

Greetz

---

### Post by Totzo on 2006-04-05
Managed to get a  cvs snapshot of multisync 82 working with evolution and gnokii plugins. No calendar though, just the contacts. Seems it's either or! Syncing the contacts is more useful for me though.

If anyone is interested it's [here]("http://www.multisync.org/files/multisync-cvs-snapshot.tar.gz"):

---

### Post by shu on 2006-04-05
Totzo, 0.82 is a legacy release. You should use 0.90.x series, either 0.90.18 or cvs snapshot.

---

### Post by LittleLion on 2006-05-29
Hi

I make Ubuntu Dapper packages for OpenSync :D 
I somebody want test its they can find here: [http://koti.mbnet.fi/littleli/ubuntu/dapper/opensync/](http://koti.mbnet.fi/littleli/ubuntu/dapper/opensync/)

There is also source packages so if somebody want make own packages or build more plugins he be worth look that packages.

If you find bugs from they packages please send email to me.

Please read README.txt


KNOWN BUGS:
syncml says: "I/O error : Attempt to load network entity..." don't worry its.
Synchronization between syncml and evolution2 warning duplicates.
There isn't syncml support over http because Dapper use libsoup version 2.2.92 and there is bug. If somebody want test syncml over http he must install libsoup version 2.2.91 to he Dapper.

---

### Post by ketsugi on 2006-05-31
Just thought I'd mention that the wiki howto helped me get calendar syncing up on my Nokia 6280.

Wondering if there's a deb for the current SVN version of libopensync-plugin-gnokii which has experimental contact syncing? I tried to compile it myself but I ran into errors running the "autoreconf -sfi" command.

```
ketsugi@Asahara:~/Applications/gnokii-sync$ autoreconf -sfi
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE
configure.in:19: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:20: error: possibly undefined macro: AC_PROG_LIBTOOL
autoreconf: /usr/bin/autoconf failed with exit status: 1

```

---

### Post by ketsugi on 2006-06-01
I can no longer sync. I get this error:

```
$ msynctool --sync nokia-evo
Synchronizing group "nokia-evo"
Member 1 of type evo2-sync just connected
Member 2 of type gnokii-sync just connected
All clients connected or error
Segmentation fault

```

---

### Post by LittleLion on 2006-06-06
Good news. Matthias Jahn make Debian Unstable and Ubuntu Dapper. You can download packages from: [http://www.in.fh-merseburg.de/~jahn/](http://www.in.fh-merseburg.de/~jahn/)

EDIT: And now SyncML over http is supported :)

---

### Post by Cue on 2006-06-06
[QUOTE=ketsugi]I can no longer sync.[/QUOTE]

So did you or did you not manage to sync your 6280?
Is BT the problem when trying to sync a Nokia phone or a general one?

---

### Post by Andcor on 2006-07-11
I succesfully connected my Nokia 6230i with my linux ubuntu dapper. 
VERY NICE

But something is a little wrong, when I sync the computer to the phone I can only read the date for the appointment, not the time.

Have I got a setting wrong? or do I have to wait until multisync and opensync get better and more updated ?

---

### Post by Zieher on 2006-09-28
Hi,

first of all, I'd like to thank the community for this added functionality. I'd like to know if and when full sync'ing (contacts and tasks) will be implemented.

Is anybody still working on this, or has this "solution" been superseded by something I didn't find yet?

---

### Post by dwomble on 2006-12-06
I've been trying with a Nokia 6682 but with no luck. It seems as though the gnapplet crashes when I try and do the identify.

If I switch it over to AT mode (no gnapplet) I can get the identify to work but nothing else. ](*,)

---

