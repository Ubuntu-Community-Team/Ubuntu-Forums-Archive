---
title: "Weird numlockx behavior with XFCE"
date: 2019-02-17
forum: Desktop Environments
---

### Post by Hagar Delest on 2019-02-17
Hi,

I used to install numlockx at each new release of xubuntu and it used to work fine. In 18.10, it works well for the login BUT after login, it is switched off. I think it did not do that with 18.04.
After lengthy searches on the net, I ended using xfconf to create a new entry with Numlock as boolean and true. Then what I oserbved is that:
[LIST]
[*]The keyboards.xml file was created in my .config/xfce4/xfconf/xfce-perchannel-xml folder (and I checked it was not there before since I saw that a fix was to add the Numlock property in that file)
[*]After login, the LED for Num. Lock was turned off and then turned on again quickly
[/LIST]
So in the end, it works but it has to be done for every user on the machine and it doesn't explain why the numlock is switched to off after login.
Anyone could explain what happens exactly?
Thanks.

---

### Post by ajgreeny on 2019-02-17
Numlock state in Xfce4 (Xubuntu) is set in the **Settings-manager -> Keyboard -> Behaviour** tab.

I have never done this in any other way, so I'm surprised that you are having this problem.
Have you checked the setting I show above?

---

### Post by Hagar Delest on 2019-02-17
Yes, I've tried with and without that setting (before editing the keyboard setting with Xconf) and no change at all.

---

