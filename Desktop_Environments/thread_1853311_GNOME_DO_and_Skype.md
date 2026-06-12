---
title: "GNOME DO and Skype"
date: 2011-10-02
forum: Desktop Environments
---

### Post by matjaz_pirnovar on 2011-10-02
Gnome-DO doesn't pick up skype contacts.
Gnome DO works for everythinmg except I can't make skype calls or chat.

How do I bring up skype contacts and call / chat them from Gnome DO?

PS: I can see my gmail contacts, but not skype ones.

M

---

### Post by matjaz_pirnovar on 2011-10-02
Anybody has this issue? Gnome do doesn't pick up skype contacts?

Specs:
Ubuntu 10.10
Built in skype.

---

### Post by renataogarcia on 2011-10-20
Same here, I get the following error message when starting from terminal:

Skype.SkypeContactItemSource "Skype Buddies" encountered an error in UpdateItems: System.ArgumentOutOfRangeException: Argument is out of range.
Parameter name: startIndex
  at System.String.Substring (Int32 startIndex) [0x00000] in <filename unknown>:0 
  at Skype.Skype.Get (System.String request, System.Object[] args) [0x00000] in <filename unknown>:0 
  at Skype.Skype+<>c__IteratorB.MoveNext () [0x00000] in <filename unknown>:0 
  at Skype.SkypeContactItemSource.UpdateItems () [0x00000] in <filename unknown>:0 
  at Do.Universe.Safe.SafeItemSource.UpdateItems () [0x00000] in <filename unknown>:0 .

---

### Post by flg on 2012-04-07
The bug has been reported: [https://bugs.launchpad.net/do-plugins/+bug/781553](https://bugs.launchpad.net/do-plugins/+bug/781553)

---

