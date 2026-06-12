---
title: "Hey! What happaned to Dodge?"
date: 2007-07-25
forum: Desktop Effects &amp; Customization
---

### Post by floke on 2007-07-25
Just noticed today that the dodge animation is no longer available on CF!

Anyone know what happened, besides Compiz giveth and Compiz taketh away?

---

### Post by tgrisier on 2007-07-25
I noticed that a couple of days ago.  Not only that but now when I click on the 'Animations' button all that happens is that the icons are removed, so I'm not even able to change animation effects.  Kind of stinks.

---

### Post by floke on 2007-07-25
I notice we have the Vista flip-flop do-dah whatsit though.

Hmmm.

---

### Post by andrewsomething on 2007-07-25
> **floke said:**
> Just noticed today that the dodge animation is no longer available on CF!

Anyone know what happened, besides Compiz giveth and Compiz taketh away?

It's still there. They just redesigned the preference dialog. I'm not sure why, it's not as user friendly. Look at the screen shoot. Go to that tab and double click under the entry under focus effect (where it says dodge on mine it should say none by default).

---

### Post by tgrisier on 2007-07-25
> **andrewsomething said:**
> It's still there. They just redesigned the preference dialog. I'm not sure why, it's not as user friendly. Look at the screen shoot. Go to that tab and double click under the entry under focus effect (where it says dodge on mine it should say none by default).


For some reason I can't even get to THAT screen.  I haven't changed anything except to install the updates as they become available.

---

### Post by andrewsomething on 2007-07-25
> **tgrisier said:**
> For some reason I can't even get to THAT screen.  I haven't changed anything except to install the updates as they become available.

Strange... =( 

What repo are you pulling the CompizConfig Setting Manager from? Mine comes from Trevino's maybe somethings wrong with one of the other repos? Maybe try reinstalling the package "compizconfig-settings-manager" Just a few ideas...

---

### Post by floke on 2007-07-25
Ah Lovely Jubbly!

Thanx Andrew.

---

### Post by tgrisier on 2007-07-25
> **andrewsomething said:**
> Strange... =( 

What repo are you pulling the CompizConfig Setting Manager from? Mine comes from Trevino's maybe somethings wrong with one of the other repos? Maybe try reinstalling the package "compizconfig-settings-manager" Just a few ideas...


Well, I got it to work.  I uninstalled/reinstalled the entire package but it still had the same problem.  Then I went in and changed the backend to GConf Configuration and it started working.  Very odd.

---

### Post by hyperair on 2007-07-26
In my case, I reenabled the Dodge animation and it had issues, like the window that was supposed to go behind stayed in front, although any click events went through to the active window. Then I removed my ~/.compizconfig folder and reconfigured from scratch. Then it worked.

---

