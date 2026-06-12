---
title: "Having resolution trouble on my laptop"
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by KorovaOrange on 2008-03-03
I'm pretty new to ubuntu and on my laptop I changed the resolution to 1280x1024. I don't think the laptop can support this and now when i boot up the screen is all messed up. I can still log in and everything but i can't see any icons and really cant do anything.

My question is there a way to get back to default resolution when i can't see anything on my panel? maybe some keyboard commands that could get it back to the proper resolution. I appreciate any help i can get.

---

### Post by {BzF}~JOKesTER on 2008-03-05
Sure Thing Dude.

At The Login Screen -{Where You'd Normally Type Username/Password}

Press 

ctrl+alt+f1    --At Once--

Now Hit Enter

It Will Ask You For Username And Password

Give Them And Login.

Now Type:

sudo dpkg-reconfigure -phigh xserver-xorg

And

sudo reboot

Your System Will Now Reboot.

It Will Say "Safe Graphics Mode" When You Boot.

Just Click "Configure" And Setup The Resoloution And Graphics Drivers/Screen Again.

Enjoy!!

---

