---
title: "HP Laptop with Docking Station not showing video when played in Docking station"
date: 2009-05-07
forum: General Help
---

### Post by G0lg0thaZA on 2009-05-07
Hi

Not sure if this is Hardware and Laptop related or rather Multimedia and Video, so I am posting it in General.

I have a HP NX6325 laptop. In previous versions of Ubuntu I did not have this problem, but it started when upgrading to (and still persists in a fresh install of) 9.04.

Out of the Docking Station any video clips I play using a multimedia player (like VLC or Movie Player) shows 100%. In the Docking Station with an external LCD display it only shows a black screen (with sound). Youtube movies plays fine in a browser either in or out of the Docking Station.

I Googled and searched the forums without luck... any direction where to even start troubleshooting would be great. I think it might be related to the fact that the ATI proprietary drivers are no longer supported.

Any ideas?

Thanx for your patience

---

### Post by erolsen on 2009-05-10
i have the exact same problem using a dell latitude d630 with an nvidia quadro video card. i thought it could be a driver issue, but if an hp with an ati vid card is having the same problem, must be a bug within 9.04?

---

### Post by G0lg0thaZA on 2009-05-14
hmmm... might be time for my first bug post...

---

### Post by G0lg0thaZA on 2009-07-27
Hi

Thought I would update this as I finally had time to play with it and figure it out...

I changed my Video players "Video Output" from default to either OpenGL or to X11. 

In my case I use VLC (have not tried other players, but might work as well).

In VLC, check in preferences, video, output.

In my case the OpenGL displays the video (no more black screen), but the quality is pretty bad. The X11 video output works a lot better (better quality).

Hope this helps someone...

Cheers

---

