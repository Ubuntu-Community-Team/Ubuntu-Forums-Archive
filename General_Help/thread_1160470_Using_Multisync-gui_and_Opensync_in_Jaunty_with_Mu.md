---
title: "Using Multisync-gui and Opensync in Jaunty with Multiple Devices (Nokia Symbian)"
date: 2009-05-15
forum: General Help
---

### Post by ajmctaggart on 2009-05-15
Hey everyone,

I have been working for a few days on developing a sync between my laptop's running Jaunty with Evolution  and 2 Nokia phones using SyncML via Opensync...
starting point [here]("http://ubuntuforums.org/showthread.php?t=705103")

E71
N95

The Main problem is, the calendars and fields are slightly different on each.  I came from a Mac, and whatever iSync was doing in the background to make these things sync is beyond me.  

Following basic directions, using Opensync and multisync-gui I've got all correct packages installed, etc.  
My main problem continues to be though with the actual gui for multisync.  While it's good enough, it's far from great.  

For instance, what if I consider both phones to have the same info, but in one group they both must connect for the sync to proceed.  Well, what if I have only one phone?  This is where I decided it would be best to develop two different group profiles and go from there.  The problem is, however, that each of these phones have some quirks in how SyncML work, and I guess since each of the devices is slightly different, it throws up a lot of errors...Calendar functions, I believe, is a big place where the N series and the E series differ. 

So, as I continue to figure this beast out, I will post my findings.  What has worked for me (Remember my devices were almost exactly the same in terms of content) 

-BACKUP PHONE DATA! BOTH TO MEMORY CARDS IF POSSIBLE!
-Delete one set of information (Calendars on the N Series, notes on my E series, as it causes the sync to hang, I left Contacts untouched on both phones.
-I first sync my E series as it has the "Most" information, sync goes fine takes nearly 10 minutes (334 contacts, tons of calendar entries)
-THEN I sync the N series (just contacts, 332 contacts, no cals, doesn't take as long)
-Then I resync both again, AND I PERSONALLY TEND TO CHOOSE THE EVOLUTION OPTION WHEN CONFLICTS COME UP

Its not working great or anything, but I'm not loosing data, mostly it's trying to figure out some character differences or field discrepancies. (Like I was saying, I think the E series has more options for the "business man,")

I'll let you all know if I get this working any better...Hope this helps!

After I get my syncs worked out, I'd really like to get a gui going that rivals isync...any takers?

---

### Post by ajmctaggart on 2009-05-19
After a few days, everything seems to still be going pretty well.  I haven't encountered any of the data corruption others have seen.  

Attached is a QUICK mockup of what I'd like to see the frontend for multisync and opensync to look like in the future...any criticism is welcome...

I hope that others will be able to finally make the switch based on the great work of the Opensync team.  For a long time this was a really big problem because there was essentially very minimal sync ability, and typically would have to run through ScheduleWorld, for example.

Now that my Symbian smartphones can sync relatively worry free with Ubuntu, I can honestly say there's no going back!

---

### Post by ajmctaggart on 2009-05-27
For the time being, I find there is no way to get the seamless sync each and every time.  I really don't know where to start from this point, it seems to be that once the info is transferred to the different devices, discrepancies begin to arise on next sync.

For the time being, I am syncing my phones together using Nokia's included program on my E71 Phone Switch.  This works great, and then allows me to keep one phone in sync w/ evolution.  So far, this is all that works.  

Has anyone else had luck with two devices and Evolution?

---

### Post by Skerit on 2009-06-23
I'm not even able to sync my calendar. sync-ml-obex-client gives me a "commited" status, but the evo2-sync bit keeps on sending data. I'm not sure how to fix that, too.

Kind of strange, some people have said it works on their phones ...

---

### Post by ajmctaggart on 2009-06-23
What type of phone do you use?  Would you post your config for the phone?  Obviously, if you feel, you can X out your Bluetooth address.

Also, I have started a Launchpad Team/ Blueprint to Re-design the Multisync-gui...I feel for an end-user it lacks in many ways...Feel free to join in if you'd like...

[https://launchpad.net/~multisync-gui]("https://launchpad.net/~multisync-gui")

Thanks! and Good Luck!

---

### Post by Skerit on 2009-06-23
Oh, sorry, I'm also using the E71.

```

<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>xx:xx:xx:xx:xx:xx</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>10</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>1</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>
  
  <!-- The username to use. Leave empty to not require a username -->
  <username></username>
  
  <!-- the password for the username -->
  <password></password>
  
  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>2</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>1</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>0</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>10000</recvLimit>
  
  <maxObjSize>0</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db></note_db>
</config>

```

I'm using the multisync 0.90 version, btw. Already a lot cleaner and easier then 0.82 :P

---

### Post by ajmctaggart on 2009-06-23
hmm, other than using Notes for notes 
 and
having 0 for If wbxml is enabled...

Looks pretty much the same as mine...

But to be honest, something is slightly different on the E71, makes things trickier...I believe it resides in Calendars...

Would you mind trying to sync ONLY Contacts, and see if that works?

Also, I like to use the terminal and go to 

~/.evolution/calendar/local/system 
   and clear everything out of there

do the same for ~/.evolution/addressbook/local/system

only do it if your data is backed up elsewhere!

It seems easier to start with all DATA on phone and none in evolution and then sync, just my idea...

Syncing works much better with  my N95...no idea why, other than E series is business, and maybe some calendar options aren't available in older N series? I am not really sure...

Good Luck!

---

### Post by ajmctaggart on 2009-07-09
For the record, Notes is pretty iffy in terms of syncing...

My syncs work PERFECTLY assuming I have notes turned off...

I don't change anything but in the obex sync client, I remove Notes' name...

---

### Post by ajmctaggart on 2009-09-01
Most Recently, I have spoken to some of the developers of an opensync-gui, I believe they work in Solaris mostly.

[http://wiki.genunix.org/wiki/index.php/Opensync_new_gui_design]("http://wiki.genunix.org/wiki/index.php/Opensync_new_gui_design")

I will report my issues back here with installation and use.

At least one dev has committed to revamping THEIR gui, as I find it already to show more promise than that of multisync.  

I will probably need to rename the Launchpad team in the near future.

---

### Post by roghae on 2009-09-10
Hi

I have a 5800 XM and have found a problem with the way opensync handles my calendars. 

If I have an item set as an "all day event" on my phone, opensync converts that to an event running from 12am to 12am.
Then, on the next sync, it places the 12-12 event on my phone as a new event, and sees the "all day event" on the phone as a new item, converts that again, and then I have 2 copies!

Every time I sync, another copy gets added on.

Now, imagine having the birthdays of 100 people on your phone, all recurring annually, and all being all day events. The phone very quickly gets clogged up with birthday events in the calendar.

Unfortunately, I have not found a way around this yet. Anyone know? 

Thanks, 
Roger

---

### Post by ajmctaggart on 2009-10-05
I am so very sorry for the delay in my response...

Have you spoken to the Opensync devs about this?

[https://lists.sourceforge.net/lists/listinfo/opensync-devel]("https://lists.sourceforge.net/lists/listinfo/opensync-devel")

I believe that would be the fastest way to get your response!

Good Luck, and please let us know if you find a workaround.

Thanks,
ajmctaggart

---

