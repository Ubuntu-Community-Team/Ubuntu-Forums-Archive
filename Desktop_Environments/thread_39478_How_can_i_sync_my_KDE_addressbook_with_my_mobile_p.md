---
title: "How can i sync my KDE addressbook with my mobile phone?"
date: 2005-06-05
forum: Desktop Environments
---

### Post by André on 2005-06-05
Hi everybody,

i have a T610 mobile phone. 

I can sync my addresses via evolution easily. I switched to KDE and would prefer kontact now. So i would like to sync my kde addressbook with my phone. It this possible?

I heard about a plugin for multisync which enables syncing with kdepim apps (like the addressbook). Is this one avaible for (K)Ubuntu somehow? Does somehow have a repository for this?

Any other ideas??

Greetings
André

---

### Post by ltmon on 2005-06-05
If you open kontact from the menu there should be an item in the far left menu called "synchronisation".

You then call file->new and select 2 plugins to synchronize between.  There is no multisync in my plugins menu, but there is one called IrmcSync which may be similar (I don't know much about this stuff).  Possibly new plugins are able to be added, but you will have to google for it i think.

Let me know if you have success.  I have a k700i (very similar to the T610) which I talk to with kdebluetooth, but I haven't tried to get synching working at all.  I'll give it a go when I have some time.

L.

---

### Post by André on 2005-06-05
Hi ltmon,

thanks for your answer. I nearly gave up :-/

When i use the kontact - synchronisation plugin and click on new i don't get the irmcsync option.

Did you install some addintional stuff that maybe missing on my system?

Btw, do you have a nice repository for kdebluetooth?

Greetings and thanks again for your help
André

---

### Post by ltmon on 2005-06-05
I used the packages that Simone Gotti made for Kubuntu: [here](https://www.ubuntulinux.org/wiki/SimoneGotti).  Before you install these I think you need to install bluez-utils, which is a dependency.

That installed kdebluetooth no problems.

Then (after reading around a bit) I modified my file /etc/bluetooth/hcid.conf to look like this:

```

#
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.4 2004/04/29 20:14:21 holtmann Exp $
#
# HCId options
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
 # pin_helper /usr/bin/bluez-pin;
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
 class 0xff0100;

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
 lp hold,sniff,park;

 # Authentication and Encryption
 #auth enable;
 #encrypt enable;
}

```

This should be enough to get kdebluetooth working.  When I plug my bluetooth dongle in, I get a notification alerting me that it has been found.  I can now pair the devices and send files back and forth.

Hope this gets you to the same stage.

L.

---

### Post by André on 2005-06-06
Hi,

that's so newbish but could you tell me the line you added to your sources.list?

I just can't get it right :-/

// Got it right already ;-) I am testing the new konnector right now..

Greetings and thanks in advance
André

---

### Post by André on 2005-06-06
Mmmmhhh...

that doesn't seem to work.

I have kdebluetooth installed and it works pretty well. I can see my phone, exchange data, ...

Then i switched to kontact, calling the sync plugin. I chose addressbook and irmcsync as pair but when i click on sync it seems to do nothing :-(

Any ideas??

André

---

### Post by ltmon on 2005-06-06
I just got it to work last night.

1. sudo apt-get install multisync

Multisync is GTK based app that Multisynk (with a K, which is what is used in Kontact) is a frontend to.

2. In Kontact, choose a IrmcKonnector as the first device.  You then click on "Options" (or is it "Configure", I'm at work and can't remember quite).  You then choose a device (your phone should appear in the list of possible devices if kdebluetooth is working properly), and choose whether to sync address book or calendar.

3. The second device should _NOT_ be Addressbook (makes sense huh?) but "Local Resource".  In the options view for this device you need to choose the files that contain your address book/calendar.  This is pretty easy, because when you browse for files, the default is the one you want.

Now you can sync. :)

I did find it a little buggy, in that it didn't work every time.  Sometimes I couldn't get the options window up for IrmcConnector, and other times it would start synching and freeze.

L.

---

### Post by André on 2005-06-07
Hi, thanks again for your post. I still have some problems:

[QUOTE=ltmon]I just got it to work last night.
[/QUOTE]

You should be really happy :-)

[QUOTE=ltmon]
1. sudo apt-get install multisync

Multisync is GTK based app that Multisynk (with a K, which is what is used in Kontact) is a frontend to.
[/QUOTE]

Okay, i forgot that one before. Installed multisync with all plugins via Synaptic.

[QUOTE=ltmon]
2. In Kontact, choose a IrmcKonnector as the first device.  You then click on "Options" (or is it "Configure", I'm at work and can't remember quite).  You then choose a device (your phone should appear in the list of possible devices if kdebluetooth is working properly), and choose whether to sync address book or calendar.
[/QUOTE]

Here my problems start. I just exchanged files via kdebluetooth so it seems to work. But when i click on the Options button for the IrmcKonnektor nothing happens!

[QUOTE=ltmon]
3. The second device should _NOT_ be Addressbook (makes sense huh?) but "Local Resource".  In the options view for this device you need to choose the files that contain your address book/calendar.  This is pretty easy, because when you browse for files, the default is the one you want.
[/QUOTE]

Good to know. Was wondering about that one.

[QUOTE=ltmon]
Now you can sync. :)
[/QUOTE]

Maybe after some additional configuration?? Any ideas what else i should try??

Greetings
André

---

### Post by André on 2005-06-07
Hi,

i am still not giving up ;-)

I called kitchensync from the commandline and it accepted my mobile phone as a kitchensync konnector. But i just can't it configured right. When i click on sync it makes a copy of my local address file and stored a protocol in backup but nothing seems to happen beyond that. I deleted someone not so important ;-) from my telephone book and my own name from the addressbook. Both things do not appear on the "other side" when i click on syncing.

My Syncing tool in Kontact is still ill :-(

Greetings
André

---

### Post by ltmon on 2005-06-07
I tried using Kitchensynk, but found it very crashy and gave up.

In multisynk I had the same problem as you... the options box just didn't want to work.  I thought I fixed that when I installed multisync, but sometimes it does and doesn't work ????

All I can suggest is launching multisynk from the command line and trying again (and again) until the options box comes up.  You only need to see it once anyway.

L.

---

### Post by André on 2005-06-08
Mmmmhhh... 

still no go. But let's try some dirty tricks.

Could you post the contents of your syncing pair. I think it's located in ~/.kde/share/config/multisynk

I think that i have all the information i need to configure it for me. Maybe this could work :-)

Greetings
André

//edit:

I think, i also need your multisynk* files from ~/.kde/share/config/ to get your syncing pairs. The information i need will come from kdebluetooth/multisync and hopefully i can tinker around with it and get it to work :-)

---

### Post by ltmon on 2005-06-09
Attached to this post.  The ".txt" was added to satisfy the upload filter on this board.

Cheers,

L.

---

### Post by André on 2005-06-11
Hi,

thanks for your files. I am still having problems :-(

Multisynk finds my phone now but when i click on sync then it doesn't really sync. It copies all contacts from my KAB to the phone which are already on the phone. No matter which options i choose for conflict handling i have two entries in my phone address book and it won't copy addresses which are not already i the phone address book...

That's so strange that i am about to give up :-(

Greetings and thanks for everything
André

---

### Post by André on 2005-06-11
Syncing the calender works but the appointments are moved by an hour...

---

### Post by vicks on 2005-06-12
> Syncing the calender works but the appointments are moved by an hour...

This can actually be a SonyEriscsson bug. I had this problem trying to sync with outlook i WinXP with SonyE software. But maybe you haven't had this experience in windows? 

I'm trying to sync my T630, but i can't get IRMC to show up in kontact. I have the multisync plugins installed. How did you do this?

---

### Post by André on 2005-06-12
I used ltmon's files above and configured them for my needs.

If you need further help tell me then i will upload my files too.

Greetings
André

---

### Post by somez on 2005-06-15
Guys what if I have a Nokia? I own a Nokia 3650, and as far as I know, Nokia phones doesn't support ircm, they're using Syncml, but I don't know how to make SyncML via Bluetooth :-(
I've tried the kontact syncronization, but the irmc plugin not even finds my phone. I worked this out, by telling him my phones address, and after pressing sync, the kbluetoothd icon flashes blue, and my phone indicates the incoming connection, but nothing happens.
Kontact says "writing back data second plugin's name", or something like that (because my kontatc is not english). And that's all.

---

### Post by André on 2005-06-15
Hi everybody,

right now i am trying the cvs version of multisync.

It includes support for kdepim and maybe synchronize my device with it (worked like a charm before with evolution).

@somez: I saw that there is a gnokii plugin in the cvs version. It seems your device is working with this one: 
[http://svn.foo-projects.org/filedetails.php?repname=lunar&path=%2Fmoonbase%2Ftrunk%2Futils%2Fgnokii%2FDETAILS&rev=0&sc=0](http://svn.foo-projects.org/filedetails.php?repname=lunar&path=%2Fmoonbase%2Ftrunk%2Futils%2Fgnokii%2FDETAILS&rev=0&sc=0)


Here is the repository i use for the cvs version:

deb [http://packman.iu-bremen.de/debian/sid/multisync-cvs/](http://packman.iu-bremen.de/debian/sid/multisync-cvs/) ./

Remember that this stuff is a testing version. Use with care!

Greetings
André, who will give feedback about how it worked

---

### Post by André on 2005-06-15
Okay,

this is not really working. I am going straight to dependency hell using this. 

The new multisync package needs a newer libbluetooth1. This package on the other hand needs a newer libc6. After installing this several packages are broken...

Conclusion: Just don't do it ;-)

I got the new packages from Breezy. So we just have to wait some time til Breezy is on  a stable level and hopefully can sync our phones then.

Greetings
André

---

### Post by somez on 2005-06-15
[QUOTE=André]Okay,

this is not really working. I am going straight to dependency hell using this. 

The new multisync package needs a newer libbluetooth1. This package on the other hand needs a newer libc6. After installing this several packages are broken...

Conclusion: Just don't do it ;-)

I got the new packages from Breezy. So we just have to wait some time til Breezy is on  a stable level and hopefully can sync our phones then.

Greetings
André[/QUOTE]

Same to me :-)
I installed the breezy packages, and multisync start with gnokii, but multisynk doesn't see the gnokii plugin :-(

---

### Post by ltmon on 2005-06-16
[QUOTE=André]Syncing the calender works but the appointments are moved by an hour...[/QUOTE]

Funnily enough I remember when I used to share an ical from my windows computer at work (running Sunbird) with my kde desktop at home (running Kontact) the same thing happened.  I never really got that one sorted out.  I wonder if there's some funny way that linux handles timezones that other platforms don't that causes this bug, or if maybe it's a KDE/Kontact thing.

L.

---

### Post by lorenco on 2005-11-03
Was just wondering... did you eventually get this working ??

I just upgraded to breezy and are trying to getmy 6600 to sync vie BT ...:D

---

### Post by MHD on 2005-12-22
Hello all... I am also having problems syncing with my ipaq like PPC... 

My problem is, even though I have synce, and multisync installed when I go to Kontact I dont get any options for a remote device as mentioned above... anything else you need to install?

---

### Post by jonsson on 2005-12-27
I guess this was never solved? I'm trying to sync my K700i with Kontakt over bluetooth but it just hangs (like someone mentioned above). I have managed to make a backup of my phonebook with multisync but multisynK just hangs. And multisync does not seem to have an option to sync with the KDE calendar? :confused:

---

### Post by vojtek on 2006-02-02
[QUOTE=jonsson]I guess this was never solved? I'm trying to sync my K700i with Kontakt over bluetooth but it just hangs (like someone mentioned above). I have managed to make a backup of my phonebook with multisync but multisynK just hangs. And multisync does not seem to have an option to sync with the KDE calendar? :confused:[/QUOTE]

I have the same problem (I use SE T610.). After 4 hours I can do backup my phone-data with multisync, but I can't add this backup to Kontact. Multisynk (in Kontact) isn't working good - i have "receiving data" and nothing happen. I have tried many of applications, configs and for now I haven't more ideas...

Why multisync is seeing T610 and can do backup, but multisynk not? Can You help?

---

### Post by cclemon on 2006-02-03
Ok, I'm totally newbie here.... How do I install Multisynk? I tried apt-get install multisynk, but it didn't find any packages with that name. Can anyone help me?

---

### Post by vojtek on 2006-02-04
Try install first "kitchensync"

---

### Post by cclemon on 2006-02-05
It looks like Multisynk is working now, and the "synchronize" button in Kontact has changed. But... It doesn't looks like there are any plugins to synch bluetoothdevices with Kontact. I've tried to apt-get install kdebluetooth-irmcsync, but that requires libkcal2a and libkdepim1 (>= 4:3.4.1)? But there are bunches of other packages where libkdepim1a is reqired in stead, so I can't degrade that package.

Is it possible to force installing kdebluetooth-irmcsync to not interrupt any other dependencies, or is that a bad idea? Any solutions? I've installed KDE 3.5.1

---

### Post by vojtek on 2006-02-05
I have exactly the same problem, but I cant solve it. To install libkcal2a I must uninstall many of packages like amarok etc. - I didn't try without doing that (force install).

---

### Post by joey111 on 2006-05-13
hi, what about the nokia 6230?
where would i find a list of supported mobiles? i mean syncable not linuxinstallable.thx

---

### Post by akvik on 2006-05-30
Hi everyone,

[I'm moving this post over to Dapper and starting a new thread there :-) ]

It's crazy, I know, but this morning I managed to sync my Kontact calendar to my t630 phone! 1 hour wrong on the phone, but what the heck, it's working. I have managed to get this to work before as well, but it's been on and off, to say the least.

This is almost starting to look like a howto, but don't be fooled, there's probably a lot of other things that should be in here to make it a fully fledged howto. Why not send in your suggestions, and we can make an ultimate Kontact/Bluetooth sync howto?

Before you try this, make sure that your phone is detectable, and that you can transfer files back and forth. AND: backup your resource files! If you don't, there is a real risk that you won't see them again. You are warned. These files usually lies in $HOME/.kde/share/apps/[kabc, korganizer]. Check this in kontact (edit resource file settings).

My tip for people who's trying this, is to start kontact from the terminal (just type kontact as non-root) and follow multisynk's output. Good for debugging.

Under "Syncronisation" (which is really a separate program called multisynk), select "New". In my multisynk settings, I have the calendar and the addressbook as two separate lines. The first plugin is the Irmc-konnector (the phone), and the second plugin is the addressbook/calendar, connected through "Lokal konnector". I choose to click on the buttons that select the open resource files, meaning the files that Kontact use at the moment to show your contacts and appointments. 

Under the options tab, I always choose "Solve manually" - I don't like surprises. Once I deleted ALL contacts in the addressbook because of a wrong setting here...

Click on Syncronise and swap over to the terminal to see what happens. 
If you get:
```
kontact: disconnectDevice()
Got Response Packet
   Success, final bit set
```

It means that the sync is complete.

Do you sometimes get the message that syncronisation is complete, but nothing has been updated? I think that this is because kontact _thinks_ that everything is alright for some reason. The output from multisynk says that everything is done and fixed, but it isn't. I think when you try back and forth, killing connections and syncing over and over, it "touches" the file on the phone, so that it is fooled to think everything is ok. 

The output from multisynk indicates that there is a logfile on my phone that remembers my earlier sins, I presume:
```

kontact: readSyncees()
kontact: Getting Initial Changelog (0.log)
kontact: getting file: telecom/pb/luid/0.log

```

Would be great to sweep that file clean along with everything else on the phone, so that we could start with clean sheets. Someone that knows how to do this, besides doing a factory reset on the phone?

I think the above is one of the most common problems when syncing - that is actually works without any changes are made. I tried and tried to sync but all the time kontact was syncing and syncing, thinking I was mad or something. 

Have you ever been tempted to change the resource files to see if that works better? If you change the resource file in Calendar, it might complicate the sync process. My advice is to stick with the same addressbook and calendar files, and not mess around with changing them to make the sync work. Kontact just gets very confused and wants to duplicate your contacts and appointments. 

However, I have my calendar in vCalendar format, just because my t630 phone uses a vcs file, but I don't know if that is important.

Do you get the freeze, that it syncronise forever? (terminal says: "kontact: slotSynceeReceived()" but the phone says "Synchronising") Just kill the connection, because it will actually sync forever (at least over the night - i tried once...). This I think has to do with your settings in multisynk, that you have selected "addressbook" instead of "lokal connector" or something like that. 

Syncing with kontact over bluetooth is a bit of a mystery - sometimes it works and sometimes not, it's easy to get religious about it (it syncs only when it rains and so on...)

Keep it up - and please report happy stories -god knows we need it!

EDIT: about the 1 hour discrepancy between the phone and the addressbook: it seems that new appointments get the right time - the ones that I add after the first sync. Then I think it has to do with setting daylight savings on my phone. 

EDIT again: It seems my addressbook sync works again - OMG this is always too much. I can't _change_ the contacts though - if I do, the contacts on my phone is the same old. 

If the sync fails for some reason, it is wise to restart kontact (or multisynk, if you running it as a separate application). For me it just worked after restarting kontact. 

:-)

---

### Post by gavinpat on 2006-12-29
There seem to be a few problems with the K700i but I'm really interested in getting to the bottom of them. 

It would be nice to see some developers getting involved. I'll probably see if I can download the dev files myself but not sure where to start really.

For those who haven't seen the contact duplicate problem before - SE only sorted that one out in their MS synchronisation software a few (maybe 6) months ago. It would be great to get their input actually on this...

I find that if you run kitchensync from a shell you get a lot more info.

On starting kitchensync 2>output I get:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kitchensync: KSync::ThreadedPlugin::ThreadedPlugin(const KConfig*) this = 0x8169ea8
kitchensync: Creating a AddressBookThread. 
kitchensync: KSync::ThreadedPlugin::ThreadedPlugin(const KConfig*) this = 0x816c0a0
kitchensync: Creating a CalendarThread. 
kresources: ERROR: ManagerImpl::readResourceConfig: mFactory is 0. Did the app forget to call readConfig?
kitchensync: ERROR: Received DCOP: resource added for unknown resource me8aTbcrCJ
kresources: ERROR: ManagerImpl::readResourceConfig: mFactory is 0. Did the app forget to call readConfig?
kitchensync: ERROR: Received DCOP: resource added for unknown resource SJBLDtrn61
kresources: ERROR: ManagerImpl::readResourceConfig: mFactory is 0. Did the app forget to call readConfig?
kitchensync: ERROR: Received DCOP: resource added for unknown resource SJBLDtrn61
kitchensync: connectDevice()

I'll see if I can solve these problems then address the other issues as they arise. Has anyone in this thread built kitchensync from scratch?

G.

---

