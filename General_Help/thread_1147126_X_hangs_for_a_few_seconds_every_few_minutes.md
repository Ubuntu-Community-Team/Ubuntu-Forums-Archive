---
title: "X hangs for a few seconds every few minutes"
date: 2009-05-03
forum: General Help
---

### Post by Arizon_Dread on 2009-05-03
Hey!

I installed Ubuntu Jaunty a few weeks ago. I had this problem the whole time I think. 

The problem at hand consists of this: While doing nothing special other than listening to music through audacious, having skype and pidgin running, and surfing through Firefox, X hangs up for a few second, seemingly quite randomly. This occurs from several times a minute to once every 10-20 min. It seems to be partly connected to i.e when someone goes online in pidgin and that bubble-thingy comes up in the upper right corner, or when I send a message, or when I click on a link in Firefox. Any start of a process seems to do this. Sometimes it's just random when I don't do anything special. The whole X hangs up. I can't move the mouse, the music stops in one place an plays like a half second repeatedly until the hang-up stops, which is generally about 2-3 seconds. It's vastly annoying to have this thing all the time though. 

I don't know if it makes any difference, but when I installed jaunty, I used my home-dir from an earlier installation (Hardy), and I had trouble with pidgin. It would crash on login, I noticed that it was because one of the hidden directorys were owned by root, so I changed that to be owned by me and now it works smoothly. Dunno if it might be something else owned by root that causes somekind of "permission denied" in the background or something. 

let me know if you have any ideas!

I tried changing the nvidia-drivers to an older version but that just made it worse, crashing more often.

It feels like threading doesn't work properly. It feels like when some application is trying to run a process that needs focus for a few seconds, that doesn't start in a separate thread, but in the same thread that X is running, so everything just waits until it releases focus... dunno if I'm reaching though... somebody else probably knows this stuff better than me. 

When I clicked on the email notification thingy in pidgin just now, it hung up again for a few seconds.

---

### Post by wpshooter on 2009-05-03
I would re-install from scratch using the ALTERNATE (text based) CD version of Januty and then leave everything STOCK for a while.

---

