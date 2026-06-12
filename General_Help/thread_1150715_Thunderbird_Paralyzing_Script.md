---
title: "Thunderbird Paralyzing Script"
date: 2009-05-06
forum: General Help
---

### Post by Montserrat on 2009-05-06
On Intrepid Ibex 8.10, I get the following message every time I fire up Thunderbird to check e-mail or get a new message.

“Warning: Unresponsive script”

“A script on this page may be busy, or it may have stopped responding. You can stop the script now, or you can continue to see if the script will complete.”

As recommended for both Mozilla products (Thunderbird & Firefox), I've changed the value for dom.max_script_run_time from 5 to 1,000. However, this has had no effect. 

Again, this happens every time I check e-mail or get a new message. It freezes up the system, preventing all other activity until I get the dialog box to stop the script (after several minutes).

Help!

---

### Post by monsterstack on 2009-05-06
I've come across this problem once before. It was a misbehaving extension that was causing the fuss if I remember so I turned them all off. Looks like you've been going through the motions anyway but you didn't mention this step so I thought I'd pipe up.

---

### Post by Montserrat on 2009-05-08
Thank you Monsterstack. 

I didn't initially know how to turn off extensions, but then realized that Add-ons under the Tools menu is synonymous. Excuse my newby status. 

I apparently have five add-ons. Is it wise to turn them all off? 

Here they are, for the heck of it.

Beagle Indexer
Display mail user agent
New mail icon
Nostalgy
Quickfile

---

### Post by monsterstack on 2009-05-08
Sure, turn them all off. If that fixes the problem, great! Then try turning them back on one-by-one to try to isolate the extension that's giving you grief.

---

### Post by Montserrat on 2009-05-09
Monsterstack, that seemed to work. Thanks.

I'd turn them back on one by one, but I don't see that any of these unasked-for add-ons do anything I need. And oddly enough, since turning them off, I now have a previously non-existent pop-up telling me I've got mail. I generally like Dunderbird, but it's got some quirks

Now how the heck do I close this thread?

---

### Post by jezzz on 2011-02-16
I have just migrated from Hardy 8.4 to Maverick Meerkat 10.10 and Lightning is causing this problem in my TB 3.1.7, too. Uninstalling it solves the problem but while the operation has been successful the patient is dead: I am left with no calendar. Is there any solution to this? Are there any calendar alternatives for Lightning in Ubuntu? Thanks for any tips anyone could have!

---

### Post by chitowner2 on 2012-02-06
related:

[http://ubuntuforums.org/showthread.php?p=11668020#post11668020](http://ubuntuforums.org/showthread.php?p=11668020#post11668020)

---

### Post by ottosykora on 2012-02-06
>but I don't see that any of these unasked-for add-ons do anything I need. <

there should be definitely no such extensions installed by default, so it looks like you got some strange mail one day and this made you install those extensions.
You can sure remove them completely if it was not you who wanted them.

But investigate further who or what installed them, as this may be some malware on your system.

---

### Post by chitowner2 on 2012-02-06
[QUOTE=ottosykora;11669385]>but I don't see that any of these unasked-for add-ons do anything I need. <

I should have been more specific: the 'related' thread is not about add-ons or extensions, but the problem of script failures in general.

CT

---

