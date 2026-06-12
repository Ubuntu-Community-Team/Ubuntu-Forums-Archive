---
title: "Mail-notification popups look wrong"
date: 2009-05-29
forum: General Help
---

### Post by the real omni on 2009-05-29
I have a weird issue having updated from 8.04 to 9.04

mail-notification popups no longer appear in the bottom-right corner of my screen in a nice tan-coloured window like they did in 8.04

They now pop up in the middle of my screen and they look like any other standard dialog. Can anyone tell me how to make mail-notification popups look the way they did in 8.04?

---

### Post by HuckleSmothered on 2009-05-29
I'm using it as well and in pre-9.04 it was the tan color. Now it is integrated with the system pop-ups. The black window that defaults to the top right. Obviously this is not what you are getting.

Check the Configuration Editor under System Tools. Then under Apps | mail-notification | popups. I have a key there for "position" which is equal to "free." Maybe that could help you out.

---

### Post by I_can_see_the_light on 2009-06-03
Same thing happening to me. Anyone know how to fix it? When displaying test messages from the properties dialog things seem to work with the new notification system.

---

### Post by I_can_see_the_light on 2009-06-04
From [_**www.ubooboo.net**_]("http://www.ubooboo.net/zimPage.php?page=Mail-Notification"): 

To get the new Jaunty notification system working, hit <Alt>F2 and enter gconf-editor then:
apps>mail-notification>popups> double click actions and remove everything.

Then start the mail-notification configuration and open the *message popups* tab: Check 'enable popups'. Position: in popup stack. Expiration: default


Did the trick for me :)

---

### Post by the real omni on 2010-02-05
> **I_can_see_the_light said:**
> From [_**www.ubooboo.net**_]("http://www.ubooboo.net/zimPage.php?page=Mail-Notification"): 

To get the new Jaunty notification system working, hit <Alt>F2 and enter gconf-editor then:
apps>mail-notification>popups> double click actions and remove everything.

Then start the mail-notification configuration and open the *message popups* tab: Check 'enable popups'. Position: in popup stack. Expiration: default


Followed these steps - now it's even worse. Instead of a dialog box, I get a black floating window in the top-right of my screen that only displays for about 5 seconds before fading away.

I just want to go back to normal - have a dialog box pop up in the bottom right of the screen and stack up towards the top when multiple e-mails come in.

Is this not possible?

I've now upgraded to 9.10 (Karmic Koala) and am getting the same results.

---

