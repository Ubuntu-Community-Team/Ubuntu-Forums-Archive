---
title: "Evolution doesn't sync addresses"
date: 2008-12-07
forum: General Help
---

### Post by prenger745 on 2008-12-07
I am trying to sync my Palm Centro on Evolution (2.24.2).  I set it to copy the information from my phone.  I have the conduits set to copy from my PDA (as follows):

Backup - Disabled
Eaddress - Copy from PDA
Ecalendar- Copy from PDA
Ememos- Copy from PDA
Etodo- Copy from PDA
Expense- Copy from PDA
File - Disabled
MAL - Disabled
Memofile - Copy from PDA
Sendmail - Disabled
Test - Disabled
Time - Disabled

Well it seems everything syncs right, I don't get any errors.  But when I go into a contact all that has copied over from the PDA is Contacts Name, Phone Numbers and Email addresses.  When I double click on a Contact and select the "Mailing Address" tab, they are all blank.

I really need it to copy over the addresses or else this programs really does me no good.  Any help is greatly appreciated!

Dan

---

### Post by skankster on 2008-12-19
I have a similar issue, though with different set-ups. This is syncing Evolution with Scheduleworld.

Generally, not only do *most* of the mail addresses get lost, but when I managed some to work, I've found they've been mangled. One example was, after changing someone's home address, their old home address was getting synced, and the new one lost.

I have exported the contacts as vcards, and tried importing to KAddressbook, and converting to LDIF via a website converter, and had odd results. I downloaded a script that should change the vcard file to a csv file that TBird can upload and got the same result as you. It turned out that Evolution was creating vcard field headers that the script wasn't expecting so they were getting ignored. My guess is this will be the cause of your problem.

EDIT: the script/evolution issue looks like it was down to VCard version differences 2.1 vs 3.0. However even changing the field names doesn't really work as the addresses are put into random fields.

I looked at the vcard file, and it seems that Evolution is being very random where it places the various mail addresses. For example  some are appearing in home and some in the home label. Some have the address parts in one field separated by "\n" - these tend to get lost in the LDIF conversion.

The address where the old home address was being synced and the new one lost, it turns out that the vcard for that contact has the old home address exported and marked as "pref" and the new one also exported but not marked. The importers take the "pref" address and ignore the other. The problem is, the old address does not appear in the UI at all.

It looks like the Evolution is basically messed up in the DB. I'm going to spend some time cleaning up the vcard file, import it into TBird and use that from now on. I've used TBird and Scheduleworld to sync with my palm no problem (the Palm client cost, but it was very cheap).

Doesn't help you, I know, but it might give you a place to start looking.

---

