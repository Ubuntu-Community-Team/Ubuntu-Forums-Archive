---
title: "HOW TO: Windows Mobile sync with Intrepid"
date: 2009-02-27
forum: General Help
---

### Post by HittingSmoke on 2009-02-27
[I]I just managed to get this right after about a year of multiple threads and many different ways of trying. This way took me about four hours and should take you even less with this guide.

This has been tested to work as described on a CDMA HTC Touch Pro from Sprint as well as an HTC Apache with the same radio[/I]

[COLOR="Red"][B]WARNING, BACK UP ALL CONTACTS AND EVENTS BEFORE SYNCING. IT IS HIGHLY LIKELY THAT ON YOUR FIRST SYNC YOU WILL LOSE ALL YOUR CONTACTS ON ONE OR BOTH DEVICES!
On my first sync (with all my contacts on my phone) they were wiped out and I had to manually add them all to Evolution again because I didnt have a compatible backup format and CVS sucks... [PIMBackup]("http://freewareppc.com/database/pimbackup.shtml") for your WM device is a nice free option[/B][/COLOR]

This is a guide to getting your Windows Mobile 5+ smartphone or pocket PC to sync with Evolution. It should also work (using extra opensync plug-ins) with Sunbird, KDE 3.x PIM, Blackberry, Palm, and Open Palm packages and devices. This guide, however will only focus on Windows Mobile to Evolution.

To start off, we need to install a few packages that our GUI sync apps will rely on.

```
sudo apt-get install synce-sync-engine synce-kpm multisync0.90
```
****note*** There is no Gnome native sync option that I can find for Intrepid that's nearly as good as sync-kpm. I recommend it to both KDE and Gnome users. Use synce-kde or synce-gdm for Hardy*

For file browsing under Nautilus in Gnome also install
```
sudo apt-get install synce-gnomevfs
```
****note*** this is not necessary with newer WM 6+ devices as they give you an option to use a mass storage connection when pluged in which works like any other removable storage in Ubuntu.*

Now we need to install our OpenSync plugins for use with MultiSync. For Windows Mobile and Evolution we want to run
```
sudo apt-get install opensync-plugin-synce opensync-plugin-evolution
```

At this point you want to use Alt-F2 to run **synce-sync-engine** then Alt-F2 and run **synce-kpm**

****note***synce-kpm wont create a launcher in your menu, you might want to set a desktop shortcut to it*
****note*** you want to make sure RNDIS is enabled on your phone by going to "Settings > Connections tab > USB to PC" and making sure the "Enable advanced network functionality" box is check, otherwise this wont work. **Many other guides require this to be disabled, so if you've tried other guides to sync your WM device, this might be disabled**.*

At this point you should be able to connect your device and it should be recognised by the already running sync-kpm. This will ask you to create a partnership for your device.[SIZE="1"](*see issues at bottom)[/SIZE] Pick a name and what you'd like synced and you should see a screen that shows you battery info, basic device info and an add/remove programs tab.

If at this point your device isn't detected open up ActiveSync on your device and go to "Menu > Connections" and make sure "Synchronize all PC's using this Connection:" is checked and set to USB

If that still doesn't work, try disabling the Ubuntu firewall by using [COLOR="Red"]**(only if you are behind a router with a firewall, otherwise see bottom of post for ports to open individually)**[/COLOR]
```
sudo ufw disable
```

If you've got a connection with synce-kpm now then you can start up the program that actually makes the sync connection, MultiSync.

Start multisync by running **multisync0.90** via Alt+F2 or from a terminal window. In the top left click the Add button and choose a group name for this sync profile. After choosing your group name you will be presented with a window to set up the actual sync profile.

Click the **"Add Member"** button and select **"Evolution 2.x"**. Click the "Add Member" button once more and select **"Plugin to synchronize with Windows CE device"** and click close.

Now with the KDE PDA Manager (synce-kpm) running, click the refresh button under your newly created group in MultiSync and your contacts and calendar **should** sync.

Like I said, the first time it wiped my contacts from my device but it seems as long as you don't delete anything from your PC that you don't want deleted form your device then it will work fine and sync both ways. I had deleted all the contacts in Evolution to try and to a clean sync to the PC but instead it registered the deletes on my device.

* There seems to be a problem with synce-kpm registering the device as new each time it's pluged in. Each time you plug in your device to sync it you may have to create a new partnership with synce-kpm. I'm not sure how to fix this or why each new one created sticks under *synce-configure-bindings* but the syncing itself works so hopefully someone will be able to work out this lesser problems later.

*The individual ports to open for Windows Mobile syncing are TCP 990, 999, 5678, 5721, 26675. I'm not going into detail on how top open firewall ports, you can find this info many other places with a quick Google search.

---

### Post by loongye on 2009-03-04
Works! Thank you :popcorn:

---

### Post by wucherpfennig on 2009-03-09
Well, I guess it works only with Gnome... I tried now for hours to set it up with KDE, but with no luck! 
With Gnome everything works flawlessly, but some how I'm too stupid to get it synchronized with KDE 4.2 and Kontact?! Probably you know a solution?

---

### Post by HittingSmoke on 2009-03-17
> **wucherpfennig said:**
> Well, I guess it works only with Gnome... I tried now for hours to set it up with KDE, but with no luck! 
With Gnome everything works flawlessly, but some how I'm too stupid to get it synchronized with KDE 4.2 and Kontact?! Probably you know a solution?

I haven't got it working with Kontact but I do have it working with Evolution under KDE 4.2.1. Some of the plugins for multisync aren't available for KDE 4 so for now we're kind of stuck using Evolution. It's the only program I can get to properly sync up. I holding out for a way to use Thunderbird myself.

---

### Post by dtom2444 on 2009-03-17
Well, I almost got it to work. I was able to get SynCE to detect my phone, Sprint HTC Touch, but am unable to setup a partnership. The "Create" button doesn't become active or "click-able". Any idea how to fix this?

---

### Post by HittingSmoke on 2009-03-18
> **dtom2444 said:**
> Well, I almost got it to work. I was able to get SynCE to detect my phone, Sprint HTC Touch, but am unable to setup a partnership. The "Create" button doesn't become active or "click-able". Any idea how to fix this?

Are you using SynCE KDE PDA Manager in Intrepid?

If so what does it say under "ActiveSync Status"

---

### Post by RichardCain on 2009-03-20
Thanks.  I tried Tomthewombat's rather more convoluted method which worked for a short time and then stopped.  This is working OK, thankfully.  Only one thing though - when I go into Evolution, all my contacts and appointments appear 3 times!  any reason for this?

---

### Post by HittingSmoke on 2009-03-22
> **RichardCain said:**
> Thanks.  I tried Tomthewombat's rather more convoluted method which worked for a short time and then stopped.  This is working OK, thankfully.  Only one thing though - when I go into Evolution, all my contacts and appointments appear 3 times!  any reason for this?

I'm not sure but I'm noticing that too now. Also on my phone. Do you have to set up a new partnership in Sync-KPM every time you connect like I do?

---

### Post by mbarvian on 2009-03-27
looks great!

I'm going to try this out as soon as I can.  Hopefully it'll finally be the one that works :)

---

### Post by gdiepen on 2009-03-30
> **wucherpfennig said:**
> Well, I guess it works only with Gnome... I tried now for hours to set it up with KDE, but with no luck! 
With Gnome everything works flawlessly, but some how I'm too stupid to get it synchronized with KDE 4.2 and Kontact?! Probably you know a solution?

Hi,

I have updated the wiki on [www.synce.org](www.synce.org) and you will now see the answer to your question in the ubuntu installation instructions.

For the moment it is not possible to sync to kontact of KDE 4.x. The reason for this is that OpenSync does not work with this yet.  So until a new stable release (0.4x) of OpenSync is released, I don't think that you can sync to Kontact in KDE4.

Kind regards,

Guido Diepen

---

### Post by lizhijie on 2009-04-04
Thank you.it really work.but took me much time.your note mislead me...

[COLOR="Red"]*note* you want to make sure RNDIS is enabled on your phone by going to "Settings > Connections tab > USB to PC" and making sure the "Enable advanced network functionality" box is check, otherwise this wont work. Many other guides require this to be disabled, so if you've tried other guides to sync your WM device, this might be disabled.[/COLOR]

on my device WM6.1,activesync4.5.[COLOR="Red"]JUST DISABLE THE "Enable advanced network functionality" [/COLOR],otherwise wont work!!:popcorn:

---

### Post by joker77 on 2009-04-12
Thanks, looks very promising, can someone help me here? :

> At this point you want to use Alt-F2 to run synce-sync-engine then Alt-F2 and run synce-kpm

*note*synce-kpm wont create a launcher in your menu, you might want to set a desktop shortcut to it
*note* you want to make sure RNDIS is enabled on your phone by going to "Settings > Connections tab > USB to PC" and making sure the "Enable advanced network functionality" box is check, otherwise this wont work. Many other guides require this to be disabled, so if you've tried other guides to sync your WM device, this might be disabled.

At this point you should be able to connect your device and it should be recognised by the already running sync-kpm. This will ask you to create a partnership for your device.(*see issues at bottom) Pick a name and what you'd like synced and you should see a screen that shows you battery info, basic device info and an add/remove programs tab.

kpm started like it should; then I selected the partnerships tab, and tried to add a name. The box below (where I should specify things to sync) is blank, and I can't write anything there. How should it appear? Should I find something there to select? (like Contacts, Calendar, Tasks, etc) Any ideas on how to correct things here?

Ignoring this glitch, I tried to proceed setting up multisync, and that too went exactly as described by HittingSmoke here. But at the end theres no sync happening.... 

The following is the output on starting synce-sync-engine

> 2009-04-12 22:40:59,684 DEBUG syncengine : running main loop
2009-04-12 22:40:59,684 DEBUG syncengine : creating SyncEngine object
2009-04-12 22:40:59,701 DEBUG syncengine : installing signal handlers

The following is the output around the time I tried to do what I should in kpm

> 2009-04-12 22:41:38,494 INFO engine.syncengine.kernel : _CBHalDeviceConnected: device connected at udi /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00
2009-04-12 22:41:38,495 INFO engine.config.Config : UpdateConfig - unable to open config file /etc/syncengine.conf.xml ([Errno 2] No such file or directory: '/etc/syncengine.conf.xml') - using defaults
2009-04-12 22:41:38,495 INFO engine.config.Config : UpdateConfig - unable to open config file /home/viju/.synce/syncengine.conf.xml ([Errno 2] No such file or directory: '/home/viju/.synce/syncengine.conf.xml') - using defaults
2009-04-12 22:41:38,501 INFO engine.syncengine.kernel :  device WINDOWSMOBILE13 connected
2009-04-12 22:41:38,501 INFO engine.syncengine.kernel : ProcessAuth : processing authorization for device 'WINDOWSMOBILE13'
2009-04-12 22:41:38,504 INFO engine.syncengine.kernel : ProcessAuth: authorization not required for device 'WINDOWSMOBILE13'
2009-04-12 22:41:38,504 DEBUG engine.syncengine.kernel : OnConnect: setting up RAPI session

** (process:6429): WARNING **: synce_info_from_hal: Failed to obtain property pda.pocketpc.iface_address for device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.iface_address on device with id /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00
process 6429: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 278.
This is normally a bug in some application using the D-Bus library.

** (process:6429): CRITICAL **: synce_info_from_hal: Failed to obtain property pda.pocketpc.platform for device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.iface_address on device with id /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00
** Message: Odccm is not running, ignoring
2009-04-12 22:41:38,527 ERROR dbus.connection : Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/SyncEngine/kernel.py", line 272, in _CBHalDeviceConnected
    self.OnConnect()
  File "/usr/lib/python2.5/site-packages/SyncEngine/kernel.py", line 427, in OnConnect
    self.rapi_session = rapicontext.RapiContext(pyrapi2.SYNCE_LOG_LEVEL_DEFAULT)
  File "/usr/lib/python2.5/site-packages/SyncEngine/rapicontext.py", line 29, in __init__
    pyrapi2.RAPISession.__init__(self,loglevel)
  File "pyrapi2.pyx", line 405, in pyrapi2.RAPISession.__init__
RAPIError: -2147467259: An unspecified failure has occurred

Hoping madly that someone will be able to find what's happening...Thanks in advance.
 
My setup: intrepid; asus p527 with w mo 6.1. (BTW some of the options in activesync for me were not exactly as described by HittingSmoke)

BTW, (an open question to those in the know) will Win Mo syncing become cleaner in Jaunty?

---

### Post by Ehol on 2009-04-13
Did you upgrade libsynce during the last few days ?
'cause since I upgraded from 0.13 to 0.14, hal is reporting more or less the same error ...
Could it be that the new libs are broken ?

---

### Post by samnmax on 2009-04-13
I have the same problem. SynCE used to work fine, but not anymore after upgrading libsynce0 to this version:

0.14~20090410-0ubuntu0~ppa1~intrepid1

Now synce-trayicon segfaults continuously until i disconnect the device. If I remove synce-trayicon, the commandline programs also fail with this error:

```
** (process:9458): WARNING **: synce_info_from_hal: Failed to obtain property pda.pocketpc.iface_address for device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.iface_address on device with id /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00
process 9458: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 278.
This is normally a bug in some application using the D-Bus library.

** (process:9458): CRITICAL **: synce_info_from_hal: Failed to obtain property pda.pocketpc.platform for device /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00: org.freedesktop.Hal.NoSuchProperty: No property pda.pocketpc.iface_address on device with id /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'
```

---

### Post by Ehol on 2009-04-14
Is there any way to downgrade to previous version of libsynce in order to test if our assumptions are correct ?

---

### Post by btech on 2009-04-15
I am running Ubuntu 8.10. I was running fine for weeks. I did the libsynce upgrade and bam, it is broken and I am getting the same error message.

---

### Post by hormone on 2009-04-15
+1 for not being able to sync since upgrading this package. Would love to be able to roll back...

---

### Post by Ehol on 2009-04-15
Guido Diepen says it's a bug. It should be corrected in a few days. Keep updating !

Here is the news : [Guido Diepen's Blog](http://www.guidodiepen.nl/2009/04/)

**UPDATE**: There is a new update for libsynce0 e libsynce0-dev in the repos. I am updating now. Later, when I could connect the phone, I'll let you know if the issue is solved (I hope so :) )

---

### Post by samnmax on 2009-04-15
OK, with the new update from the repos it seems to be working again. :p

libsynce0 is now version:
0.14~20090410-0.13-0ubuntu0~ppa1~intrepid1

---

### Post by hormone on 2009-04-16
Thank-you Ubuntu/SynCE dudes:p

---

### Post by *sebbie* on 2009-04-29
hey guys,  has anyone tried to connect a htc prophet with windows mobile 5? Because FinchSync does not work with my mobile phone i'm interested in other solutions.  Best regards sebbie

---

### Post by dchen37 on 2009-05-03
Has anyone tried this in the newest version of Ubuntu, Jaunty?  I did a clean install and everything seems to be syncing fine, but when I open Evolution, there are no contacts or calendar events. 
Anyone else have better luck?

---

### Post by raul999 on 2009-05-09
Hi.
I tried this with jaunty and it seems to work. I encounter the problem that when i pull out the usb and pull it again in a minute later then it will not automaticaly connect. 

If i restart Ubuntu it will work until i pull out the usb.

---

### Post by elgordo123 on 2009-05-28
I have followed this guide and finally, after years for giving up I actually have this working!  
There is 1 problem I am having and wondering how to fix.  If I delete (or move) a calendar item in evolution it does not delete (or move) on my pocket pc (verizon samsung i760, mobile 6.1). It actually puts it back (probably so it matches how it is on the Pocket PC calender. 
  Also if I delete a contact from evolution and then sync, it doesn't delete on the pocket pc, and restores it (from the pocket pc) back into evolution. 

Any ideas? 
(Using ubuntu 9.04)
Thanks in advance.

SOLVED - I uninstalled all of the programs here, removed the .synce folder and rebooted.  Also did hard-reset on my PPC.  Reinstalled and everything is working awesome now!   BIG Thank you!!   Tasks, Calendar, Contacts all syncing back and forth, no matter where I edit/add/del.

---

### Post by adsf on 2009-06-01
Hi guys, I am using 9.04.

This is the closet I have gotten to get my windows 5 mobile working with linux.

everything seesms to work well until I try the actual sync with multisync. 

It comes up with 'error synchronizing: unable to read one of the members'  and disconnects?

Any ideas

---

### Post by elgordo123 on 2009-06-03
When you open the terminal and run synce-sync-engine and then another terminal and run synce-kpm, then plug in your phone, can you see actvivity in those terminal windows?  Does sync-kpm show battery, etc?

---

### Post by revcp on 2009-06-03
> **elgordo123 said:**
> When you open the terminal and run synce-sync-engine and then another terminal and run synce-kpm, then plug in your phone, can you see actvivity in those terminal windows?  Does sync-kpm show battery, etc?

I'm actually having the exact same issue.  Everything seems to run.  all plugs along in ms0.90, with evo2-sync and synce-opensync-plugin both reading "sent all changes" and, below, "5726 entries received" (seems a bit high, even with my numerous contacts and calendar intries) and "All clients sent changes or errors."  Two odd things... On is the synce-kpm gui just briefly blips with "looking for changes" and then disappears after I hit "refresh" on the ms0.90 gui.  Also, and most telling, I entered a "dummy" contact in evo 2.26.1 and after finishing supposed sync nothing showed up on my phone (htc touch).

---

### Post by TMachado on 2009-06-06
I've done everything and run SynCE and detected my HTC Touch Dual. Everything appears to be fine. However how do I browse my files in Nautilus?

There's "nothing new" there..

Im getting error synchronizing on multisync0.90... can you please help me ?

---

### Post by revcp on 2009-06-17
Still can't figure out what's going on.  Process seems to go smoothly, with 1145 contacts read in multisync and synce-kde.  Green bar in synce-kde grows in 100 contact increments, all finishes.  The problem, however, (and it's a biggie!) is that I still have no contacts in Evo!  Is there some box that should be checked that I'm not checking?
This is very frustrating.  I am set up perfectly with HTC Touch Sprint WinMo 6.1 to google calendar and contacts (through nuevasync) and google cal sync in evo, but I can't get contacts into evo (2.26.1, Jaunty) either through the gmail contacts to evo sync (which is horribly messed up) or from my phone.  AAAAArrrggghhh!

Any idea what's up?

---

### Post by HittingSmoke on 2009-06-18
> **TMachado said:**
> I've done everything and run SynCE and detected my HTC Touch Dual. Everything appears to be fine. However how do I browse my files in Nautilus?

There's "nothing new" there..

Im getting error synchronizing on multisync0.90... can you please help me ?

The synce-gnomevfs package is supposed to give you file browser support for your phone although I've not tried this on any newer devices as all the WinMo 6+ ROMs I've used give you an option when you plug them in to either Sync or to just act as a drive for file transfers.

When I chose the Disk Drive option on my phone it mounts like a USB drive under Nautilus for me.

---

### Post by magpa on 2009-07-07
> **lizhijie said:**
> Thank you.it really work.but took me much time.your note mislead me...

[COLOR="Red"]*note* you want to make sure RNDIS is enabled on your phone by going to "Settings > Connections tab > USB to PC" and making sure the "Enable advanced network functionality" box is check, otherwise this wont work. Many other guides require this to be disabled, so if you've tried other guides to sync your WM device, this might be disabled.[/COLOR]

on my device WM6.1,activesync4.5.[COLOR="Red"]JUST DISABLE THE "Enable advanced network functionality" [/COLOR],otherwise wont work!!:popcorn:

Cheers this seems to have solved the issue for me aswell. :KS

Running Jaunty and using HTC Touch Diamond with wm6.5 and followed the guide except for this part for those that might be in a similar situation..

edit:
and still trying to get contacts/calender synced to the phone..
getting this error if anyone knows a workabout, google is not giving much help today =/
```
Member 1 of type evo2-sync just sent all changes
Member 2 of type synce-opensync-plugin had an error while getting changes: Error during get_changeinfo() method
DEBUG:SynCE:disconnect() called
Member 2 of type synce-opensync-plugin just disconnected
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
DEBUG:SynCE:finalize() called
Error while synchronizing: Unable to read from one of the members
```

---

### Post by s0la on 2009-07-16
..

---

### Post by s0la on 2009-07-16
Hi.. First, thnx for this guide..This guide is realy fantastic, and it's pretty easy, but I don't know how to transfer files to my PDA(HTC Universal, with wm 6.1 ROM),.. Can you, pls, explain that, I don't wanna move to Windows just becuose of that.. Thnx in advance..

---

### Post by jpope on 2009-07-26
Thanks for the guide, worked beautifully for me.

---

### Post by RichardCL on 2009-08-03
Hi,

I tried this again and again with no luck on an XDA Orbit I. After no luck and running out of time, I just plugged the mobile device into a Windows machine. The Windows machine setup the device fine.

Then I plugged the Orbit back into the Ubuntu (9.04 Desktop 64bit Intel C4Q) box and it worked straight away too.

Seems that syncing once with Windows somehow sets up the device for sync. After that the Synce works too. Not sure what that device initialisation is though. Would be handy to know though since my device just needed a reset and I don't have a windows machine to initialise.

By the way, I'm using the config exactly as in the first post (Synce evolution, kpm, RNDIS enabled...).

Many thanks for the tutorial. I'm a newbie and would never have figured it out from the masses of sync applications in the repo.


Rich

---

### Post by Lemuel111 on 2009-08-07
Thanks for the great instructions, after months of trying I eventually got connected to my PDA. However, even following the instructions I can't sync, I just get Error message of can't connect to member. Any suggestions??

Thanks.

---

### Post by pantora on 2009-08-11
hi guys

i have some problems with the sync .
i ve  got ubuntu 9.04.
synce-pls works wonderful.
but when i want to create a partnership with 
synce-create-partnership , synce-kmp (KDE) or synce-trayicon , then i get this errormessage

```
error: failed to create partnership
error: org.freedesktop.DBus.Python.pyrapi2.RAPIError

```

---

### Post by ThePossum on 2009-08-20
Thanks much for this work around for my WM 6.1 Smart Phone.  Do have to do the sync using the Alt + F2 keys and pasting the commands for the sync engine and the synce-kpm before opening multisync.  But it works and that is all that matters.

One question though.  When I set this thing up I had to a couple "members" in multi-sync.  I assume that one is for the desktop calender and contacts list and the other is for the same info on the smartphone.  Can some one tell me which is for what device?  I assume that the **synce-opensync-plugin** represents the smartphone and the **evo2-sync** represents the desktop computer.  I was wondering which one so that I know which box to check when I have a conflict that needs resolved with the two sources of info that are being syncd.

Again, thanks for making it possible for me to sync my smartphone with Ubuntu.

---

### Post by VeeDubb on 2009-08-21
> **ThePossum said:**
> I assume that the **synce-opensync-plugin** represents the smartphone and the **evo2-sync**


For practical purposes, you're exactly right.  If you care about why, read on......


Both of those are plug-ins installed on your desktop that handle communication between various programs and opensync.

synce-opensync-plugin handles communication between opensync and Active-Sync.  The reason it is labeled "synce" (note the 'e' at the end)is that the original project to create stable communication between the Active Sync program on Pocket PCs (now called Windows Mobile) was called SynCE.  (Sync CE)

evo2-sync creates handles communication between Evolution and opensync in the same way.

So, in reality, there are 5 basic stops on the communication chain between your PDA and evolution.  (not counting all the libraries and background processes required to make them all play nice)

ActiveSync on windows mobile
<>
synce-opensync-plugin
<>
opensync
<>
evo2sync
<>
Evolution

---

### Post by ThePossum on 2009-08-21
Thanks VeeDubb for the confirmation and for the explanation of how the two plug-ins work.  Now if I can actually remember which plug-in is which when it comes time to sync.

---

### Post by ThePossum on 2009-08-28
Help,

Looks like this method of sync Evolution with my Windows Mobile Smartphone is only half working.  Seems that it will not sync appointments that are first entered in Evolution.  Items entered in the smartphone are getting syncd over to Evolution though.

Any help in solving this problem would be appreciated.

Thanks.

---

### Post by loowens on 2009-09-07
I am using Jaunty and am having a problem syncing all contact data from evolution to winmo.  I am not a Ubuntu expert, been using it for about 2 weeks.  What I am seeing is that while all my contact names sync to the phone most only have email addresses included on the phone. Evolution shows all phone numbers (business, mobile, home, etc) as well as email.  For the users which don't have numbers on the phone I can sometimes go into Evolution's contacts and click the phone number type drop down and select the same setting (i.e. business to business and hit ok.  Then it will sync over to the phone occasionally.

I'd be happy to provide whatever data and debugging I can, but I will need to be told what you need as far as command structure.

---

### Post by ThePossum on 2009-09-09
Loowens,

Thanks for the input on my (our) problem.  I can get things to work by first syncing my Smartphone with my Windows machine or by first entering the info in the Smartphone and the doing the sync.

Like you I am not in anyway an expert with Ubuntu so I could not even try to give any code or whatever you call it for you to debugg.  Thanks anyway. Maybe the guy who wrote the program will get around to working on it.

Have a great day.

---

### Post by ThePossum on 2009-11-01
Bump,

Please help with this problem.  One thing I hate is to be so dependent on Windows.

---

