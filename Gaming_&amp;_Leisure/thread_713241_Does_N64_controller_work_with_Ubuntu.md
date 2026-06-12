---
title: "Does N64 controller work with Ubuntu?"
date: 2008-03-02
forum: Gaming &amp; Leisure
---

### Post by feenicks on 2008-03-02
I'm very happy to have Mupen64 and zsnes running right now.  But I'm just using a generic USB gamepad which doesn't have enogh buttons or an exta joystick for the N64 games.  Has anyone gotten an N64 controller with adapter to work under Ubuntu with mupen4?

---

### Post by frenchn00b on 2008-03-02
> **feenicks said:**
> I'm very happy to have Mupen64 and zsnes running right now.  But I'm just using a generic USB gamepad which doesn't have enogh buttons or an exta joystick for the N64 games.  Has anyone gotten an N64 controller with adapter to work under Ubuntu with mupen4?
 
if I recall well, you have to do it with deleting , then a slight moving the gamepad ... and it shoudl work
it takes 5 min

---

### Post by feenicks on 2008-03-03
I'm not sure I know what you mean by "deleting" before moving the gamepad.  Can you explain?

---

### Post by Termina on 2008-10-31
I generally try not to revive dead threads, but since this is #1 on google when I ran into this problem...

To get a N64/PSX USB controller (converter) with Ubuntu, run this command before running mupen/whatever:

```

jscal -s 4,1,0,129,129,7561331,8012754,1,0,127,127,8134160,8521500,1,0,128,128,8521500,9941751,1,0,127,127,8012754,8658944 /dev/input/js0

```

---

### Post by justcop on 2009-08-11
This almost worked for me.

The controller is now filly recognised in Mupen64+

The only problem is that the analouge stick doesn't appear to have a range attached to eat. Have only tried zelda, I can only walk in any direction and this is only activated after pushing the analouge stick to the end of its trail.

---

### Post by Termina on 2009-08-11
sudo apt-get install joystick jscalibrator

Then use jscalibrator to calibrate your joystick (in my experience each n64 controller is different, unfortunately you have to calibrate each one).

Then run 'jscalibrator' and press 'Calibrate'.

Move the joystick only about 1/2 way in each direction (or else you will be unable to run in games).

Also make sure to use mupen64plus instead of the old version:

[http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)

---

### Post by Kidwell on 2012-03-20
Any fix for this?  I know this thread is old... but I'm not finding anything else.  Have a 64 controller attached via USB, it works in mupen64plus, but in Legend of Zelda, can only walk, so i'm assuming full range of joystick is not calibrated completely.  None of these solutions have work for me that are displayed in this thread.  Any help is awesome! Thanks

---

### Post by Pierrick584 on 2012-03-20
You might want to try with a newer version of Ubuntu, 8.10 is pretty old.. the 12.04 is kind-of stable right now, you might want to try it, i use it on my laptop, its use-able.

---

### Post by Perfect Storm on 2012-03-21
This is an old thread.

Thread closed.

---

