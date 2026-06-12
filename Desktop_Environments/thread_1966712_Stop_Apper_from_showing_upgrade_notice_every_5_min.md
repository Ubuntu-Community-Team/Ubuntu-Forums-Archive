---
title: "Stop Apper from showing upgrade notice every 5 minutes?"
date: 2012-04-27
forum: Desktop Environments
---

### Post by street spirit on 2012-04-27
Dear Apper,

thank you for informing me that an upgrade to Precise is now available. I already knew that, but thanks for telling me anyway. Five minutes later you reminded me again, which is very thoughtful of you. My memory isn't what it used to be, and I might already have forgotten. Five minutes after that, you reminded me again, and I looked for a button to tell you "yes, I promise I will upgrade, just as soon as I've finished working", but couldn't find one. After the next notification, to my shame, I have to admit that I killed you (or rather, your sibling apper-sentinel). I felt horrible about that, and was greatly relieved when you showed your next notification five minutes later. You certainly are hard to kill, ha ha.

Still, I wish you'd stop distracting me every five minutes...

How can I tell you that I honestly promise to upgrade as soon as I can, cross my heart and hope to die?

---

### Post by mthorslund on 2012-04-27
Same problem here. 

I clicked on the upgrade icon to see if there was an option there to stop or slow the notifications. Nope, but as I clicked Cancel, the application crashed. I thought for a while that that might stop the notifications but I just got another one.

---

### Post by SeijiSensei on 2012-04-27
System > Update Manager > Settings > Configure Muon Update Manager

Uncheck the box for "Distribution upgrades".

---

### Post by street spirit on 2012-04-27
I don't seem to have System > Update Manager, but your mention of Muon put me on the right track. Now let's see if if works...

(five minutes later)

Looks like it did. Thanks a lot!

---

### Post by street spirit on 2012-04-27
Meh. I still get the notifications, but now they've switched to a 30 minute interval.
Guess I can live with that until I upgrade.

---

### Post by nillian on 2012-05-17
I think I may have figured this out. At least, it has worked for me.

Computer | Settings | Application and System Notifications

Select "Apper Notification" under "Event Source".
You should see an entry in the list for "A distribution upgrade is available."
If you click on this, you will see some checkboxes are selected ("Play a Sound" and "Show a message in a popup" probably). 
Simply uncheck these and you will no longer be pestered!

HTH,

- N

---

