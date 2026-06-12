---
title: "pidgin issues - seg fault &amp; buddy sync"
date: 2009-01-19
forum: General Help
---

### Post by bluepowder7 on 2009-01-19
i have two issues happening with pidgin - one that i caused, one that i have no idea how it happened.

the easier one i think is segmentation fault - it happened after i changed the protocol of one of my two MSN accounts from MSN to WLM (so i have 1 MSN and 1 WLM).  as soon as i made that change, it killed pidgin and now restarting it kills it with a seg fault.  is there a config file that i can manually edit to restore the protocol back to MSN for that one account?  i tried reinstalling pidgin (sudo aptitude reinstall pidgin), without removing it first, and that did nothing.

the harder one is the buddy sync issue - my buddies aren't synched with the server, and each time i start up pidgin it tells me about them all, for both my MSN accounts.  on pidgin, i have them under "Other Contacts", and when i boot into WinXP they seem to mostly be under "Non-IM contacts" or something like that - and moving them under WinXP doesn't seem to do much.  once i accept them all to be added, stuff MOSTLY works (well, except that i don't see if a contact is on "Mobile", which sucks) - for that session.  when i restart pidgin, same error shows up for each contact.  lather, rinse, repeat.

i think i'm running pidgin 2.5.3 at home.  one thing that comes to mind is uninstall, purge, and install again (and back up my .purple folder to keep the chat history).  will that possibly work?

---

### Post by kevdog on 2009-01-19
Pidgin 2.5.4 fixed some issues with MSN although I'm not exactly sure the exact details.  I would either install it from getdeb or compile from source: [http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

---

### Post by bluepowder7 on 2009-01-19
> **kevdog said:**
> Pidgin 2.5.4 fixed some issues with MSN although I'm not exactly sure the exact details.  I would either install it from getdeb or compile from source: [http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

i may try that as well, but 2.5.3 was totally fine up until around a week ago when we had that MSN / WLM protocol thing for a few hours. after that is when the sync issues came up, and logging into WinXP's MSN Messenger this time does NOT fix it up.  i have a feeling that if in install a new client, it'll pull my contacts from the server, and it won't find them there cuz somehow they got blown away - yet my pidgin still keeps them on its client side.  so...  i dunno.

if i log into WinXP's MSN Messenger, where SHOULD my IM contacts be, under what group?  it seems WinXP's only use over the past year or so has been to help fix up MSN hiccups...  so i really don't want to spend more time in there than i absolutely have to.


and as a short-term solution, where and how do i reset the protocols to get out of the seg fault thing?  this i'd obviously have to do manually by editing some config file somewhere, cuz i can't fire up pidgin to fix it from in there.

---

### Post by bluepowder7 on 2009-01-19
ok, seg fault is fixed - just had to do a dead-simple edit in my accounts.xml file for the protocol.  nice.  easy.

not sure if my contact list sync is fully back to normal, cuz i get errors on only 2 contacts instead of a dozen.  hmm, maybe something got semi-fixed in WinXP land?

---

