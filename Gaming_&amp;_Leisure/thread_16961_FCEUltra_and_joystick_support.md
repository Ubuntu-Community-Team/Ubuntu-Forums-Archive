---
title: "FCEUltra and joystick support?"
date: 2005-02-24
forum: Gaming &amp; Leisure
---

### Post by watchitman on 2005-02-24
I don't have a clue how to make my gamepad work with FCEU and the documentation doesn't have any useful info. It's supposed to support joysticks. Btw, my gamepad is working with ZSNES just fine.

---

### Post by watchitman on 2005-02-26
*bump*

---

### Post by watchitman on 2005-03-01
*bump*

Come on, someone has got to know something about this!

---

### Post by keyshawn on 2005-03-07
Well, 

hmm...i'm guessing it's a microsoft sidewinder ?!?! :-D
[random guess] 
Since there isn't any info posted on the type of controller that you're using, I can't offer any help to ya 

regards,
keyshawn

---

### Post by watchitman on 2005-03-08
It's a Game Elements Gemini Recoil. It works in ZSNES.

I'm actually wondering if perhaps I'm misinterpreting the readme and FCEUltra for Linux doesn't have joystick support.

---

### Post by argux on 2005-08-02
What I did was make sure the controller's module is loaded, then I run 

```
fceu -inputcfg gamepad1 rom.zip
```

and then it'll ask me how I want to map each button, and then it will run. Documentation is in the  /usr/share/doc/fceu/ directory.

---

### Post by punkrockguy318 on 2006-06-07
[QUOTE=argux]What I did was make sure the controller's module is loaded, then I run 

```
fceu -inputcfg gamepad1 rom.zip
```

and then it'll ask me how I want to map each button, and then it will run. Documentation is in the  /usr/share/doc/fceu/ directory.[/QUOTE]

That got me up and running instantly.  I plugged in my PSX controller and ran the above command, and everything worked without a hitch.  Wow :)

---

### Post by punkrockguy318 on 2006-06-12
GNOME Fceu currently supports input configuaration.  For more information, check out my post here:
[http://ubuntuforums.org/showthread.php?t=195413&highlight=fceu](http://ubuntuforums.org/showthread.php?t=195413&highlight=fceu)

---

### Post by zooter on 2006-07-04
[QUOTE=argux]What I did was make sure the controller's module is loaded, then I run 

```
fceu -inputcfg gamepad1 rom.zip
```

and then it'll ask me how I want to map each button, and then it will run. Documentation is in the  /usr/share/doc/fceu/ directory.[/QUOTE]


thanks alot for this!  I've wanted to do this for a while and didn't know how.  Now it runs great!

Also, I found a great program for emulating the mouse and keyboard with a joystick.  It works great except for a few small bugs.  [http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/)  The original developer isn't working on it anymore and I'm hoping more people can pick up on it.  I use it on mandriva and it works on fceu.  It should get rid of the need for any joystick configuration stuff in individual programs.  One problem is that It's not available for ubuntu yet.  I think it should be a part of every distro so please help to promote it or something like it.

---

### Post by cfaber on 2009-08-14
Hey guys, I'm trying to get this working with a logitech rumblepad 2. All buttons seem to work except the directional pad. Calibrating with jscal and then jscalibrator shows that the pads work. As well as jstest. However when I try and fceu -inputcfg gamepad1 myrom.nes it asks for the buttons to be input. All the buttons work except the directional pad? Does anyone have any suggestions on what I should try?

---

### Post by overdrank on 2009-08-14
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

