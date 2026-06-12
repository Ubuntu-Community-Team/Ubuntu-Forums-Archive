---
title: "Synchronising Ubuntu 8.10 with Nokia N95 8Gb"
date: 2009-02-05
forum: General Help
---

### Post by NZSynth on 2009-02-05
I am a refugee from Vista and have only recently installed Ubuntu 8.10. One thing I an having trouble with is synchronising my Nokia N95 8Gb phone with Ubuntu. I found this thread [http://ubuntuforums.org/showthread.php?t=705103](http://ubuntuforums.org/showthread.php?t=705103) which is for Bluetooth, but I used it to make a start. As my desktop doesn't have Bluetooth, I want to use USB.

When I try to sync with multisync I get this:

[INDENT]$ msynctool --sync evolution-n95
Synchronizing group "evolution-n95" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
Member 2 of type syncml-obex-client had an error while connecting: Forbidden (0x43)
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error while synchronizing: Unable to connect one of the members
[/INDENT]

If I understand the above I am connecting with Evolution OK, but not to the phone.


the settings for syncml-obex-client are:
[INDENT]<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address></bluetooth_address>

  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel></bluetooth_channel>

  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>

  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>

  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>2</version>

  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>

  <!-- The username to use. Leave empty to not require a username -->
  <username></username>

  <!-- the password for the username -->
  <password></password>

  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>5</type>

  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>1</usestringtable>

  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>0</onlyLocaltime>

  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>0</recvLimit>

  <maxObjSize>0</maxObjSize>
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>

  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>

  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db>Notes</note_db>
</config>[/INDENT]

The server version on the Nokia is 1.2.

I have tried changing various settings but nothing seems to work. Does anyone know how to synchronise a Nokia N95 with Ubuntu?

---

### Post by toon on 2009-02-09
I would be **very** interested in this as well, as I have an n95 comming my way. However I'm not holding my breath - I have a nokia n73 right now (s60 series 3 also), and it has been **pure hell** trying to get this thing working like it should. There's always something - contacts duplicate or get bugged names, todo's does not sync, phone crashes, slow sync needed each time, etc.. I've given up on the damn thing and I don't sync anything, which is just awfull because I sort of live and die by my calendar. I was planning on ditching s60 and get some other phone and see how that performs on linux, but I'm getting the n95 for free so..

You should have a look at the opensync.org users-mailinglist, there's a few tips here and there, it seems 0.2 never did implement proper syncml support, only partially. There were hosts of problems, and 0.4 intends to fix these.. But it's not out yet unfortunately. I've seen a few people use 0.3X and for them it works, I haven't tried it myself still though (they highly discourage it).

Frankly I am puzzled by the whole state of mobile in Linux.. Rotating cubes we need, proper support for mobiles, probably our most important gadget, is not so important (/me sprays himself with "make it yourself"-repellent). 

I remember seing kmobiletools and screaming for joy, but it has died a long time ago. Google released some synctools just now by the way, might be worth a look..

---

### Post by NZSynth on 2009-02-11
I have given up and got an USB bluetooth for my desktop. I can now sync but get a lot of duplicates.

---

