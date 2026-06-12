---
title: "&quot;Enable Thunderbird email indexing&quot; grayed out in Tracker Indexing Preferences"
date: 2007-10-25
forum: Desktop Environments
---

### Post by Endolith on 2007-10-25
I was looking through Tracker Indexing Preferences, and in the Emails tab, the only thing that's clickable is Evolution.  Thunderbird, Kmail and Mailboxes are all grayed out.  Why?  I use Thunderbird.

---

### Post by isecore on 2007-10-26
I'd like to know that as well.

---

### Post by olavjunior on 2007-10-27
Yep! Would like to know!

Seems it's not implemented yet.. So there's a good reason for using googledesktop instead...

---

### Post by Endolith on 2007-10-27
> **olavjunior said:**
> 
Seems it's not implemented yet..

Why would they include the option, though.  Seems more like a missing dependency or something.

---

### Post by jamiemcc on 2007-10-27
TB support is experimantal only and disabled in gutsy (would not be wise to enable an experimental feature in gutsy especailly as it needs more testing and refining)

---

### Post by crispinb on 2007-11-04
Is there a preference for this somewhere, or is the thunderbird support in gutsy's tracker disabled at compile time?

I noticed in .config/tracker/tracker.cfg a line reading 'IndexThunderbirdEmails=true' (despite the thunderbird option being disabled in the Indexing Prefs UI), but no email indexing seems to be happening.

---

### Post by andrewsomething on 2007-11-09
I'd be willing to test this feature. Anyone know how to enable it?

---

### Post by isecore on 2007-11-09
> **andrewsomething said:**
> I'd be willing to test this feature. Anyone know how to enable it?

There probably isn't a way to enable it. The tracker included in Ubuntu has most likely been compiled without this support, and there's probably no way of enabling it short of downloading sources and compiling them from scratch.

And this is provided that the code exists somewhere, and that the checkboxes aren't just there as placemarks for future functionality which has yet to be implemented.

---

### Post by Endolith on 2007-11-09
> **isecore said:**
> And this is provided that the code exists somewhere, and that the checkboxes aren't just there as placemarks for future functionality which has yet to be implemented.

They should compile it without those checkboxes, too.

---

### Post by adam_kimber on 2007-11-15
> **Endolith said:**
> They should compile it without those checkboxes, too.

I agree as it is frustrating to think there is hidden functionality when in reality there really is not.

---

### Post by Endolith on 2007-11-15
> **adam_kimber said:**
> I agree as it is frustrating to think there is hidden functionality when in reality there really is not.

Yeah.  I thought I was just missing a package or something.

---

### Post by eitan_a on 2007-12-05
I got tracker to index thunderbird emails and show their results.  However, it still saved all the evolution emails as well so now when I search for an email it shows 2, one from thunderbird and 1 from evolutoin.  So now, I gotta find a way to delete the evolution indexes.

The way I got thunderbird to work was install the SVN version of tracker, and I found a thunderbird plugin here [http://migi.azs.pwr.wroc.pl/stuff/tracker_922.xpi](http://migi.azs.pwr.wroc.pl/stuff/tracker_922.xpi)
You need to enable this add-on in thunderbird, and in your tracker.cfg file set the Thunderbird indexing to "True".  I found this only worked with the SVN version of tracker, but I could be wrong as it was indexing my whole directory at the time.

Anyways, if anyone knows how to purge all the evolution emails from the tracker database I'd lvoe to know.

---

### Post by sgbirch on 2008-01-14
Or at least put a comment on the dialoig box indicating that these are under development and will be available in a future release.

---

### Post by _Stevie_ on 2008-04-24
any news on this?
in hardy TB still seems to be greyed out. very annoying...

---

### Post by ascii79 on 2008-05-01
+1

> **_Stevie_ said:**
> any news on this?
in hardy TB still seems to be greyed out. very annoying...

---

### Post by _Stevie_ on 2008-05-01
well i tried it with that tb addon, but it only search in the subjects.
thats already a bit helpful but still not the whole thing. :(

---

