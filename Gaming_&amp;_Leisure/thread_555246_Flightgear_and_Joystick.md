---
title: "Flightgear and Joystick"
date: 2007-09-19
forum: Gaming &amp; Leisure
---

### Post by goofeyfoot on 2007-09-19
Hello;

I am trying to install Flight Gear and I am trying also to use an old force feedback usb joystick.

AMD machine.

Seems like Flight Gear kind of wants to run.  But the joystick is erratic and all the controls are in the wrong place on the stick.

Is there some way to both get the stick configured and to run it in Flight Gear?

I am pretty new to all this Linux stuff so probably will require a little more detail than the average user in this forum.

Thanks for your help.

michael

---

### Post by Ron Byers on 2007-09-19
I hope somebody answers this question. I was just about to ask it myself.

---

### Post by goofeyfoot on 2007-09-21
Bump.

I expect someone knows this one. Anyone?

Michael

---

### Post by goofeyfoot on 2007-09-22
...and as the sun sets slowly into the west and the credits begin to run we see a message spanning the skyline.

"Ubunto Does Not Work With Flight Gear and Joysticks"

"The End"

---

### Post by master_kernel on 2007-09-24
> **goofeyfoot said:**
> ...and as the sun sets slowly into the west and the credits begin to run we see a message spanning the skyline.

"Ubunto Does Not Work With Flight Gear and Joysticks"

"The End"
You're lucky your joystick even almost works. Mine doesn't with Filght Gear.

---

### Post by master_kernel on 2007-09-24
> **master_kernel said:**
> You're lucky your joystick even almost works. Mine doesn't with Filght Gear.
I spoke too soon. I found instructions on configuring the joystick for flightgear at [http://ubuntuforums.org/showthread.php?t=55173](http://ubuntuforums.org/showthread.php?t=55173)

---

### Post by goofeyfoot on 2007-09-24
Wow:

Looks good and I am going to try it.

Best regards.

Michael

---

### Post by goofeyfoot on 2007-09-24
Ah, but I believe the link that you are talking about is for an analogue gameport joystick and mine is a Sidewinder Force Feedback 2.

Does anyone know how to make mine work in Ubuntu?

To be more specific.

AMD 64 machine.
Sidewinder Force Feedback 2 joystick..
Connects with USB, not a gamport.
Running Feisty.
Trying to make the stick run in Flight Gear.

Wanted to mention to that in jscalibrator the joystick calibrates fine.  But, in Flight gear none of the axis' are being recognized, just buttons.

Thanks.

Michael

---

### Post by goofeyfoot on 2007-09-25
Well, to a total new guy it looks like this might come down to something called "modprobe sidewinder."  I was reading stuff on the internet about something of this sort. 

From the context it sounds like modprobe sidewinder is some kind of module that makes sidewinder work, which apparently it doesn't normally want to do.  At least to a newbie that's what it seems like.

Is my interpretation correct?  If so, where do you get the "modprobe" sidewinder or whatever it is called?  And if you do get it, how do you install it?

Thanks again.

Michael

---

### Post by nalmeth on 2007-09-25
Run in it the terminal:
```
modprobe sidewinder
```
See what happens :)

---

### Post by viciouslime on 2007-09-25
You'll need to run "sudo modprobe sidewinder" as this command loads a kernel module and so you need to have root permissions to do it.

---

### Post by goofeyfoot on 2007-09-25
Dear Gents:

Well, I did the sudo modprobe sidewinder thing and I did almost the same thing with another one I saw called "gamedev" or something like that.

Anyway, when I run the game all the axis are screwed up.  So for instance the elevator or the ailerons might be reversed.

But at least there is some axis showing up, even though it is wrong.

Is there some way to tweak the axis to they work correctly?

Thanks, it seems like we are getting somewhere but not totally there.

Best.

Michael

---

### Post by goofeyfoot on 2007-09-25
Oh, and one more thing, here is a complete list of the modules I changed.

"# Modules needed to set-up my gamepad or joystick
sidewinder
joydev
ns558
usbhid"

Did I mess this up.  The joystick is a sidewinder force feedback 2.  It is a usb one.  I don't know whether it is digital or not but I would imagine so.

Did I put the wrong modules in here or something?

Thanks.

Michael

---

### Post by goofeyfoot on 2008-05-24
Well I'm still plagued with the problem of the usb Microsoft Sidewinder Force Feedback 2 not working in the most recent version of Ubuntu.  Am trying to get it to work in Flight Gear.

I finally got sound working in FlightGear but I don't have any way to control the plane with the joystick.

I did set the configuration file to point to the Sidewinder profile that I made.  And, when you play the game, all the buttons seem to do what they are supposed to but none of the axis worked.

I do believe that the profile is actually loading into the game because when you view the internal parameters during game play, the correct assignments for all the axes do appear.

But the axes don't actually do anything.  So no rudder, ailerons etc.

I would imagine that someone has figured out a way through this and I sure would like to hear about it.

Thanks for your help.

Michael

---

### Post by goofeyfoot on 2008-05-25
I would like to update my last post.

The problem that I was having with the sidewinder definitely has everything to do with the force feedback feature.

How do I know?  I _unplugged_ the power running to the stick.  All the AC power does is make the force feedback effects side of the stick work.  The rest of the axes, buttons, etc all work even with no power.

Guess what?  When you unplug the power the stick works perfectly.

So now I have two questions.

One, is there a way to get the force feedback side of the stick to work?

Two, if there isn't, is there a way to disable the forces on the stick with software instead of unplugging the stick each time?

As an aside let me tell you that Flight Gear runs great.  The sound isn't so good because I am using OSS (It is an X Fi card and I have to, apparently)but if I get the sound straightened out I will be good to go.

Best regards.

Micahel

---

