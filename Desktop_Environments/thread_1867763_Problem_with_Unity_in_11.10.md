---
title: "Problem with Unity in 11.10"
date: 2011-10-23
forum: Desktop Environments
---

### Post by jalberro on 2011-10-23
Hello! 
Yesterday I upgrade from 11.04 to 11.10 and now I've a problem with the style of Unity and Unity 2D. As you can see in the screenshot, the top bar is gray without style and the icons looks old (classic theme I think). I believe this is a problem with my user because if I create a new one, everything looks fine.

I try with 

```
unity --reset 
```and 

```
unity --reset-icons 
```but doesn't work. Also, I try to change the theme from Appearance but nothing happens :(

Any idea? Thanks in advanced!

---

### Post by Paddy Landau on 2011-10-23
Try this.


[LIST=1]
[*]Run ccsm (Alt-F2 and enter ccsm). If it is not installed, install ccsm through Ubuntu Software Manager, Synaptic Package Manager or the command line (whichever you prefer).
[*]Select *Desktop* on the left.
[*]If ticked, untick Ubuntu Unity Plugin. (Do *not* exit ccsm yet.) Your Unity bars will disappear (scary!).
[*]Now tick Ubuntu Unity Plugin. If it displays one or more messages about conflicts, every time select the right-hand button (to disable the conflicting setting). Your Unity bars will re-appear -- be patient, it may take two or three minutes, or even longer on an older machine.
[/LIST]

Log out. Log back in again.

---

### Post by Frogs Hair on 2011-10-23
The following command works in some cases. ```
nautilus -q
```

---

### Post by jalberro on 2011-10-23
Thanks for all the tips, but I don't have lucky with anyone :(

I solve the problem with this

```
mv /home/USER/.config/dconf/user /home/USER/.config/dconf/user.old
```That file has all the preferences for the user, so if I rename it, in the first login the OS will create a new one :)

Thanks again!

---

### Post by Paddy Landau on 2011-10-24
That's a great tip. Thanks for sharing your solution.

---

### Post by jalberro on 2011-10-24
> **Paddy Landau said:**
> That's a great tip. Thanks for sharing your solution.

You're welcome :)

---

### Post by _Impact_ on 2011-10-24
> **jalberro said:**
> Thanks for all the tips, but I don't have lucky with anyone :(

I solve the problem with this

```
mv /home/USER/.config/dconf/user /home/USER/.config/dconf/user.old
```That file has all the preferences for the user, so if I rename it, in the first login the OS will create a new one :)

Thanks again!

Thanks, this helped me as well!!!

---

