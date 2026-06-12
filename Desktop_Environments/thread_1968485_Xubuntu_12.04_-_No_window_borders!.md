---
title: "Xubuntu 12.04 - No window borders!"
date: 2012-04-29
forum: Desktop Environments
---

### Post by Rytron on 2012-04-29
Hi.

I installed Xubuntu 12.04 in vbox. The window borders have disappeared. A reboot did not solve it. Also I cannot select window border in settings. :confused:

---

### Post by Toz on 2012-04-29
xfwm4 has probably crashed. Try Alt+F2 then:
```
xfwm4 --replace
```

---

### Post by Rytron on 2012-04-30
> **Toz said:**
> xfwm4 has probably crashed. Try Alt+F2 then:
```
xfwm4 --replace
```

Thank you Toz. Sorted.

Edit: A reboot caused the problem to return. :confused:

---

### Post by Toz on 2012-04-30
Try clearing out your sessions cache:
```
rm -rf ~/.cache/sessions
```

The session cache will be properly re-created to include xfwm4.

---

### Post by Rytron on 2012-04-30
> **Toz said:**
> Try clearing out your sessions cache:
```
rm -rf ~/.cache/sessions
```

The session cache will be properly re-created to include xfwm4.

Ok.

I ran:
```
rm -rf ~/.cache/sessions
```

and then (not sure if this was required again):
```
xfwm4 --replace
```

Solved! ):P

---

### Post by Breadalbane on 2012-04-30
Exactly the same problem on my Samsung N145. Even re installed xubuntu and it just happened again. Your solution worked. Thanks very much indeed

KB

---

### Post by Rytron on 2012-04-30
> **Breadalbane said:**
> Exactly the same problem on my Samsung N145. Even re installed xubuntu and it just happened again. Your solution worked. Thanks very much indeed

KB

Kudos to [Toz]("http://ubuntuforums.org/member.php?u=27546").

BTW Breadalbane, is the ***Samsung N145*** fully GNU/Linux compatible?

---

### Post by dummy910 on 2012-05-02
fixes also work on UbuntuStudio12.04 as well... fine work Toz

---

### Post by Breadalbane on 2012-05-24
Sorry for not replying but have been away for a while.

Yes the N145plus does work with both ubuntu and xubuntu. I had to load samsung tools and fuddle with the settings of the touch pad (settings - settings manager - mouse and touchpad) to get the pad working correctly but everything else is great.

I have loaded both Unity and xfce and switch between them at login as I use a Wacom Tablet that only works in Ubuntu but I prefer xfce to unity.

The ONLY issue I have not resolved is that when I boot into xfce the screen is always dim if on battery power but Fn +up key solves that and I can live with it

Sorry for not replying sooner.
:p
KB

---

### Post by Rytron on 2012-05-24
> **Breadalbane said:**
> Sorry for not replying but have been away for a while.

Yes the N145plus does work with both ubuntu and xubuntu. I had to load samsung tools and fuddle with the settings of the touch pad (settings - settings manager - mouse and touchpad) to get the pad working correctly but everything else is great.

I have loaded both Unity and xfce and switch between them at login as I use a Wacom Tablet that only works in Ubuntu but I prefer xfce to unity.

The ONLY issue I have not resolved is that when I boot into xfce the screen is always dim if on battery power but Fn +up key solves that and I can live with it

Sorry for not replying sooner.
:p
KB

Hi Breadalbane. No problem with the delay. Better late than never.

---

### Post by seul on 2012-08-05
Thanks mate, solved my problem, too!

---

