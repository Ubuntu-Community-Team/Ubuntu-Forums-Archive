---
title: "Can't get a cube on beryl."
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by Zellio on 2007-04-30
How do I go about this?

What are the steps?

I can get it to turn like in Compiz, but a cube, I can't do.

Comeon, share those great secrets you have ;)

---

### Post by rolf-c on 2007-04-30
No secrets :)

Ensure beryl is active, ensure in beryl manager that the cube option is enabled.  If that doesn't work, scream out.

---

### Post by misconfiguration on 2007-04-30
Are you pressing your centre mouse scroll button down and moving out?

---

### Post by ronocdh on 2007-04-30
> **Zellio said:**
> How do I go about this?

What are the steps?

I can get it to turn like in Compiz, but a cube, I can't do.

Comeon, share those great secrets you have ;)
You haven't told us very much about your hardware. Are you running an ATI card? If so, you're likely to run into problems. With my X1600 I followed a guide and had the awesome flippycube working well; I promptly thereafter destroyed the functionality and on a refresh reinstall I used the same guide and the cube didn't work; but the rest of Beryl did.

Fun, huh? Buy Nvidia next time...

---

### Post by philby on 2007-04-30
OK have the same problem can't get the 3D cube to work, have Beryl installed and can see the effect options raindrops etc but they won't work when selecting the right keys (ie <shift> F9).

How do you know is Berly is enabled??? - the cube function is selected I am running a Dell 9400 with an Nvidia 7900 card, restricted drivers are enabled so what next???

---

### Post by rolf-c on 2007-04-30
philby, issue this command:
```
glxinfo |grep direct
```

What we are looking for is this result:
```
direct rendering: Yes
```

---

### Post by philby on 2007-04-30
> **rolf-c said:**
> philby, issue this command:
```
glxinfo |grep direct
```

What we are looking for is this result:
```
direct rendering: Yes
```

Yep direct rendering is a Yes - So what do I do next - Thanks Phil

And this was the first time I had entered any code manually - in MS I always new where the cmd prompt was but took a guess here - I'm beginning to feel like a Pro:)

---

### Post by philby on 2007-05-01
OK figured it out had to go <Alt> F2 then typed in Beryl - 3D effect then ran - only problem is that the sides of the cube are black??? and when I try to set up a side with any options the selections remain on the screen and the screen remains black

---

