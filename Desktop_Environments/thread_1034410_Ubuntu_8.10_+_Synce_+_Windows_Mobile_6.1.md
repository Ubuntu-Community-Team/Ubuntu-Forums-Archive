---
title: "Ubuntu 8.10 + Synce + Windows Mobile 6.1"
date: 2009-01-08
forum: Desktop Environments
---

### Post by kaefert66014235 on 2009-01-08
I'm playing around with synce and I managed to get everything to work, but synchronizing.

Here's what I did: add ```
deb http://ppa.launchpad.net/synce/ubuntu intrepid main
``` to your sources.list

Install "synce-hal" version "0.2-0ubuntu0~ppa4+interpid" from the added repository. It has a lot of requirements, and if you got "odccm" or "synce-serial" installed, you need to remove them before installing "synce-hal".

For a having a icon in your taskbar, install "synce-kpm" version "0.12-0ubuntu0~ppa1+interpid". Its much more stable than the the alternative "synce-trayicon" version "0.12-0ubuntu0~ppa6+interpid"

For accessing the device in nautilus by opening the link "synce:///" install the package "synce-gvfs" version "0.1-1.0.2-0ubuntu0~ppa1". DON'T use "synce-gnomevfs" version "0.11.1-1". It doesn't work anymore and has been replaced by "synce-gvfs".

The last 3 sentences a bit shorter:
```
sudo apt-get install synce-hal synce-kpm synce-gvfs
```
This was everything I had to do to make it work. To view the icon in your taskbar, just run the command synce-kpm.

If anyone knows how to get synchronizing to work in Linux with Windows Mobile 6.1 PLEASE TELL ME SO!

Here is what i tried yet for getting synchronizing to work:
The website [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu) tells us to install all of the following:
```
sudo apt-get install multisync-tools opensync-plugin-evolution opensync-plugin-synce
```
When following the next step:
```
create_partnership.py "Linux desktop" "Contacts,Calendar"
```
I get the following output
```
Creating partnership...

error: failed to create partnership
error: org.synce.SyncEngine.Error.Disconnected
```

Since I can't create a partnership, I can't synchronize my device.

---

### Post by Ehol on 2009-01-12
When you connect your PDA to PC (via USB I suppose), what messages dmesg give to you (Plese report them here) ?

---

### Post by kaefert66014235 on 2009-01-12
> **Ehol said:**
> When you connect your PDA to PC (via USB I suppose), what messages dmesg give to you (Plese report them here) ?

```
[ 3066.708944] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 4684.433168] CE: hpet increasing min_delta_ns to 22500 nsec
[ 4923.492089] usb 4-2: new high speed USB device using ehci_hcd and address 4
[ 4923.633527] usb 4-2: configuration #1 chosen from 1 choice
[ 4923.778473] usbcore: registered new interface driver usbserial
[ 4923.779519] usbserial: USB Serial support registered for generic
[ 4923.780502] usbcore: registered new interface driver usbserial_generic
[ 4923.780508] usbserial: USB Serial Driver core
[ 4923.790449] usbserial: USB Serial support registered for PocketPC PDA
[ 4923.790455] ipaq: USB PocketPC PDA driver v0.5
[ 4923.790509] ipaq 4-2:1.0: PocketPC PDA converter detected
[ 4923.791430] usb 4-2: PocketPC PDA converter now attached to ttyUSB0
[ 4923.791443] usbcore: registered new interface driver ipaq
[ 4924.011358] PPP generic driver version 2.4.2
[ 4925.863399] PPP BSD Compression module registered
[ 4925.897748] PPP Deflate Compression module registered

```

the things that work for me are:
-) browsing synce:/// with nautilus: reading & writing
-) using synce-kpm for seeing the details of the device, installing & deinstalling programms (cab-files)

the thing that doesnt work:
-) using synce-kpm for browsind / editing / creating partnerships
-) using the commands synce-list-partnerships & synce-create-partnership
-) therefore: no synchronizing

---

### Post by Ehol on 2009-01-16
Sorry for my delay.
I saw that your PDA is recognized as an ipaq or, better, the module ipaq is loaded when you connect your PDA.
This is kinda wrong, since you have a WM 6.1, haven't you ?

When you connect your PDA, it should load rndis-host module.
So I guess you should :
1) ```
sudo apt-get install librra0-tools librapi2-tools
```
2) blacklist ipaq in /etc/modprobe.d/blacklist
3) modify your /etc/network/interfaces in order to allow rndis0 to get an IP address. It should have a line like
```
auto rndis0
iface rndis0 inet dhcp
```

Try to restart and reconnect.
Then, if the creation of the partnership still fails, report here dmesg log again

---

### Post by kaefert66014235 on 2009-01-17
Thanks for your help Ehol!

However, I justed sent in my device for repair yesterday (other reasons), so it will take me some weeks (until my device has returned) to test this.
But one question, because you write something about ip adresses and stuff: I changed the device settings (unticked the fast active-sync connection checkbox) so that it doesn't do this network stuff, because I thought this would be more stable.

---

### Post by Ehol on 2009-01-17
synce-hal is working only on IP address.
So if you don't manage to assign an address to your PDA, synce shouldn't be able to connect to it.

These are the info in my possession: they could be partial or incomplete or defective.
But to me they are quite effective (i connected my new HTC Touch HD using rndis-host and it works like a charm).

So maybe they are worth a try.
Ah, also consider to install (svn download, then compile and then install ... there's no deb package compiled for Ibex) usb-rndis-lite from synce.org, because the module included in the kernel may be not enough for your device (if it's an HTC, they'll CERTAINLY not be :) )

If you need an updated guide, try to look at this post :
[http://ubuntuforums.org/showpost.php?p=6258719&postcount=6](http://ubuntuforums.org/showpost.php?p=6258719&postcount=6)

---

### Post by kaefert66014235 on 2009-01-17
My device is a HTC Touch HD too ;)
So do you have enabled or disabled the "fast connection" setting in active sync on your device?

---

### Post by Ehol on 2009-01-17
Absolutely enabled (if you mean advanced network functionality under Usb to PC settings ... or something similar ... my HTC is italian, so I don't know the correct english translation)

---

### Post by kaefert66014235 on 2009-01-17
mine is German, so I too don't know the correct English translation. However, I think we're talking about the same thing. I had that setting disabled, because I didn't want to make the network manager to ignore eth1, because when I want to use the device as a modem (which works very well with linux in the new windows mobile 6.1 way, you just have to set the TMU to 1394) it is comfortable when I see the connection there.

However, I'm gonna try your suggestions and the guide @ [http://ubuntuforums.org/showpost.php?p=6258719&postcount=6](http://ubuntuforums.org/showpost.php?p=6258719&postcount=6)

Many Thanks, Thomas.

---

### Post by kaefert66014235 on 2009-01-24
Okey, I got my HTC Touch HD back. The setting I was talking about can be found under Settings -> Connections -> USB to PC. It is called:
```
Enable faster data synchronization (Clear this check box if ActiveSync does not recognize the device)
```

However, regardless if I check this checkbox or not, the partnership commands always give the same error:
```
kaefert@Mobulux:~$ synce-delete-partnership
error: org.synce.SyncEngine.Error.Disconnected
```

may the command synce-matchmaker be an alternative?
```
kaefert@Mobulux:~$ synce-matchmaker status
Current partner index: 0
kaefert@Mobulux:~$ synce-matchmaker create
Partnership creation succeeded. Using partnership index 1.
kaefert@Mobulux:~$ synce-matchmaker status
Current partner index: 1
Partner 1 id:    0x0f908ef6
Partner 1 name:  "Mobulux"
kaefert@Mobulux:~$
```

having used synce-matchmaker seems to not be enough. Using msynctool I get the following errors from the plugin "synce-opensync-plugin"
```
...
Traceback (most recent call last):
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 152, in get_changeinfo
    self._TriggerSync()
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 117, in _TriggerSync
    self.engine.Synchronize()
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.synce.SyncEngine.Error.Disconnected: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 696, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.5/site-packages/sync_engine-0.11.1-py2.5.egg/SyncEngine/kernel.py", line 534, in Synchronize
    pship = self._CheckAndGetValidPartnership()
  File "/usr/lib/python2.5/site-packages/sync_engine-0.11.1-py2.5.egg/SyncEngine/kernel.py", line 257, in _CheckAndGetValidPartnership
    self._CheckDeviceConnected()
  File "/usr/lib/python2.5/site-packages/sync_engine-0.11.1-py2.5.egg/SyncEngine/kernel.py", line 231, in _CheckDeviceConnected
    raise errors.Disconnected
Disconnected: org.synce.SyncEngine.Error.Disconnected: 

...

Member 2 of type evo2-sync just sent all changes
Member 1 of type synce-opensync-plugin had an error while getting changes: Error during get_changeinfo() method
DEBUG:SynCE:disconnect() called
Member 1 of type synce-opensync-plugin just disconnected
Member 2 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
DEBUG:SynCE:finalize() called
Error while synchronizing: Unable to read from one of the members
```


Everything else works nice.

---

### Post by schiz on 2009-01-24
I just followed the guide in the first post, but am still unable to access my HTC Touch pro from nautilus(it says it cant open "synce" locations) , this is all that I want to do, but cannot, what could I do to access the phone files from ubuntu 8.10?

---

### Post by kaefert66014235 on 2009-01-24
> **schiz said:**
> I just followed the guide in the first post, but am still unable to access my HTC Touch pro from nautilus(it says it cant open "synce" locations) , this is all that I want to do, but cannot, what could I do to access the phone files from ubuntu 8.10?

does the command synce-pls work for you?

---

### Post by Stefanie on 2009-01-26
isn't there a restriction on how many partnerships your phone can handle? maybe you should try to list the existing partnerships and delete them. you can use synce-list-partnerships and synce-delete-partnerships to do this.

---

### Post by Runamok on 2009-01-27
You CAN sync the Sprint HTC Touch Pro directly through Ubuntu using a program called synce. I used the information found on this page...
[http://smealko.blogspot.com/2008/10/...-work-for.html](http://smealko.blogspot.com/2008/10/...-work-for.html)

In Summary, you need to go System>Administration>Synaptic Package Manager and make sure all of the following programs are installed.

multisync-tools multisync0.90 opensync-module-python opensync-plugin-evolution opensync-plugin-google-calendar opensync-plugin-synce python-opensync synce-gnomevfs synce-gvfs synce-hal synce-sync-engine synce-trayicon

Also, I did open an terminal and type "sudo modprobe ipaq" Not sure if this made a difference....

Reboot and the synce-trayicon should start. Right click to browse files, works like a charm.

- Enjoy
Runamok

P.S. I didn't add any sources.  Running Hardy Heron 8.04 Fully Updated since last week.

---

### Post by mroki on 2009-02-05
Hello!

I had a Mio a701 smartphone and I tried to synchronize with Evolution.
With a bit googgling I can succesfully synchronize the Contacts, but the Calendar not. (I hat a Nokia 8250 phone also and with that is no problem to synchronize either the calendar and the contacts)

Do You have an idea what should be the problem?

Ubuntu 8.04
WM 6.1

$ synce-list-partnerships 
            AVAILABLE DEVICE PARTNERSHIPS
Index   Name    Device          Host         SyncItems
-----   ----    ------          ----         ---------
0	abc	WM_llelkes	llelkes-home	[Calendar Contacts ]

$ msynctool --listgroups
Available groups:
synce-sync
Nokia

$ msynctool --showgroup synce-sync
Groupname: synce-sync
Member 1: synce-opensync-plugin
	No Configuration found: Member has not been configured
Member 2: evo2-sync
	Configuration : <config>
<address_path>default</address_path>
<calendar_path>default</calendar_path>
<tasks_path>default</tasks_path>
</config>

---

### Post by clcoyle on 2009-02-05
> **Runamok said:**
> 

In Summary, you need to go System>Administration>Synaptic Package Manager and make sure all of the following programs are installed.

multisync-tools multisync0.90 opensync-module-python opensync-plugin-evolution opensync-plugin-google-calendar opensync-plugin-synce python-opensync synce-gnomevfs synce-gvfs synce-hal synce-sync-engine synce-trayicon



Okay, NONE of those programs are installed.    I really hate to say these words...     What now?

---

