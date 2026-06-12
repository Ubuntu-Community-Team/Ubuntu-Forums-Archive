---
title: "[SOLVED] input problem with gens for linux"
date: 2007-03-26
forum: Gaming &amp; Leisure
---

### Post by unebaguettesvp on 2007-03-26
so, i installed gens for linux from this link:

[http://www.ubuntuforums.org/showthread.php?t=290008&highlight=gens]("http://www.ubuntuforums.org/showthread.php?t=290008&highlight=gens")

everything works great, except for my joystick. i am using a logitech cordless rumblepad 2. when i go to the input configuration, everything works fine. but when i play the game, everything works correctly except for the directional pad. the directional pad doesn't work at all but the analog stick works, sort of. the analog stick works backwards, sort of. i don't know. it's really weird. all of the other buttons seem to work just fine.

during the input configuration, i use the directional pad for up, left, down, and right and not the analog stick.

has anybody else had this problem?

has anybody else successfully configured their logitech cordless rumblepad 2 to work with gens for linux? any advice?

i am running edgy eft with 64 bit architecture. thanks in advance!

---

### Post by unebaguettesvp on 2007-03-27
so, i fixed it!!!

hopefully, this will help someone else out.

the way i did it was manually editing the gens.cfg file found in ./.gens/gens.cfg. when i first took a look at it, it looked like this:

[Input]
P1.Type=1
P1.Up=4097
P1.Down=4098
P1.Left=4097
P1.Right=4098

that's just the relevant section. all the other buttons worked perfectly. i noticed that up and left were the same buttons as were down and right. i had no idea what these numbers represented. so i had to redefine the keys using only one direction for every button! when i closed gens, i took a look at the config file and saw that up represented 4097. but i had to do this four times for every direction! you should probably do the same because the numbers might not match up. anyway at the end, i came up with this:

[Input]
P1.Type=1
P1.Up=4097
P1.Down=4098
P1.Left=4099
P1.Right=4100

and now all the key configurations work!!! i have no idea why this happened in the first place. no one else seems to be getting this error. hopefully this will be helpful to someone!

btw, i didn't get the directional pad to work, i had to stick with the analog stick. which is fine by me as long as it works.

---

### Post by frikadunse on 2007-06-01
Hi
I am thinking about bying this controller BUT I want it to work! Did you solve the problem with the directional pad? And did you find a tutorial in order to get it working? 

Cheers 

/Niels

---

### Post by acoustibop on 2007-06-01
Thanks, unebaguettesvp, I've managed to get my controller working after reading your post.

My experience was slightly different: I'm using a Logitech RumblePad 2 as well, except mine is a wired one.  First I checked the configuration file as you suggested and found the same as you.  I don't know if your pad has the button that switches the directional pad and the first analog stick, but I pressed that, so I was using the directional pad to set the first analog stick settings - and it worked to set up the pad.  My numbers are the same as yours.

When I tried setting the pad using the analog stack as an analog stick, the first press instantly ran right through the setup and finished it - so that wasn't much good.  No matter.  As I said, setting the analog stick settings with the directional pad fixes it for me.  I can then switch back to using the analog stick once it's set, seems to work fine in games.

@Niels: seems like an excellent controller to me. I've had mine for some time now and I'm still very happy with it - I do have the wired version though, as I mentioned.

---

