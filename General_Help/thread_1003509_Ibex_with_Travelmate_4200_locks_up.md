---
title: "Ibex with Travelmate 4200 locks up"
date: 2008-12-06
forum: General Help
---

### Post by lift_test on 2008-12-06
If not used for 15minutes or so it locks up and does not respond to any keys/combination of keys.  The only way to continue is to remove power and battery.  The "A" led is flashing when this happens.  Any ideas?
Vic

---

### Post by komoto on 2008-12-06
My first guess is a power management issue.  I'm thinking it's either:
[LIST=1]
[*]An issue with your graphics card drivers.  Ubuntu may be asking your screen to turn off or change it's DPM power saving mode.  If your graphics card drivers aren't handling this properly then it could cause the machine to lock up like it is.
[*]An issue with ACPI sleep mode.  Perhaps your machine is going to sleep but it can't wake up from it.  Usually there is a button to wake from sleep: eg one press of the space bar or the power button.
[/LIST]

You can check for both of these things in System -> Preferences -> Power Management.  If the sleep option is set to "Never" then obviously it's not a ACPI Sleep issue.  Otherwise you could try setting it to "Never" and see if it stops your problem.

If the Display option is set to about 15minutes (which is how long you said it takes), then that is quite likely the problem.

You can confirm it's the problem by manually triguring the ACPI mode and seeing if it causes your puter to lock up:

Typing the following in a terminal should turn your screen off, and may trigure the issue you have.
```
xset dpms force off
```

If it does trigger the issue then I would advise you move the Display slider (in the Power Management window) to Never (to disable power saving on your monitor) and then file a bug.

-Kom

---

### Post by lift_test on 2008-12-06
Tried setting battery and ac mode to never, still happens!

---

### Post by komoto on 2008-12-06
Perhaps follow the "A" led lead.  Find out what that light means by looking in the manual.  If you don't have the manual you can probs download it from the manufacturers site.

You might find out the light signifies some kind of hardware error, like faulty RAM.  It might be the laptop is just in some kind of ACPI state.



-Kom

---

### Post by lift_test on 2008-12-13
I doubt it's a hardware problem, it's dual XP boot and I don't have the same problem with XP.  It's getting worse because it locked up during an update and I'm getting error messages which I'm currently trying to sort out.

---

