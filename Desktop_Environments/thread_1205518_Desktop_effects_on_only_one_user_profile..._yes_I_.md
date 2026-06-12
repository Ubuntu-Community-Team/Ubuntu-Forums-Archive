---
title: "Desktop effects on only one user profile... yes I did a search."
date: 2009-07-06
forum: Desktop Environments
---

### Post by aj_the_first on 2009-07-06
Okay, I did a search and couldn't find anything that would fix my specific problem.
I am pretty sure it has to do with some mistakes I may have made with folder permissions.
My wife's profile, sarah, CAN enable desktop effects, yet on my profile, aj, I can not enable desktop effects, it simply searches for drivers and then says "desktop effects could not be enabled"
My wifes profile could enable effects, and then I messed with some folder permission settings trying to make sure that I could access all the media on her profile, and then her profile wouldn't boot properly (644 permissions to .dmrc), and during that time it wouldn't enable desktop effects. So I thought I set the proper permissions to the proper folder (should I have just done it for a specific file?), and then just moved her media to my profile (she doesn't use the computer anymore).
Her profile now boots properly, and it can enable desktop effects, but mine no longer can enable desktop effects.
I have no idea where the desktops effects programs are, and I think I must have messed up something when re-setting the permissions on her profile, since her profile has desktop effects now, and mine doesn't.
Any ideas?
 
Thanks,
AJ

---

### Post by fballem on 2009-07-06
> **aj_the_first said:**
> Okay, I did a search and couldn't find anything that would fix my specific problem.
I am pretty sure it has to do with some mistakes I may have made with folder permissions.
My wife's profile, sarah, CAN enable desktop effects, yet on my profile, aj, I can not enable desktop effects, it simply searches for drivers and then says "desktop effects could not be enabled"
My wifes profile could enable effects, and then I messed with some folder permission settings trying to make sure that I could access all the media on her profile, and then her profile wouldn't boot properly (644 permissions to .dmrc), and during that time it wouldn't enable desktop effects. So I thought I set the proper permissions to the proper folder (should I have just done it for a specific file?), and then just moved her media to my profile (she doesn't use the computer anymore).
Her profile now boots properly, and it can enable desktop effects, but mine no longer can enable desktop effects.
I have no idea where the desktops effects programs are, and I think I must have messed up something when re-setting the permissions on her profile, since her profile has desktop effects now, and mine doesn't.
Any ideas?
 
Thanks,
AJ

A question that might help solve the problem. When you first setup the computer, which id did you use first - sarah or aj? I suspect that it is sarah, but I don't want to make an assumption without checking the facts.

Thanks,

---

### Post by aj_the_first on 2009-07-06
Ah yes, it is originally my wife's computer, so the primary user profile (1000) is my wife, sarah.
Mine, aj, is the second profile (1001)
Hope this helps.

---

### Post by fballem on 2009-07-06
> **aj_the_first said:**
> Ah yes, it is originally my wife's computer, so the primary user profile (1000) is my wife, sarah.
Mine, aj, is the second profile (1001)
Hope this helps.

Please try the following:

[LIST=1]
[*]Log on to the system as **sarah**.
[*]Select System > Administration > Users and Groups from the menu. This will result in the User and Groups panel being displayed.
[*]From that panel, select the Unlock button and type in sarah's password. This will unlock the User Administration.
[*]On the User Administration panel, click on **aj**, then select the Properties button. This will open up the User Account screen for aj.
[*]On the User Account screen, select the User Privileges tab. This will produce a list of items. One of the items on the list will include Administer the system.
[*]Make sure that you put a check mark beside that, then select the OK button. Then select the Close button.
[*]To be safe, restart the system.
[*]Once restarted, sign in as aj. This should allow you to administer the system. Whenever you are using an administrative service, such as sudo or making system changes, use aj's password.
[/LIST]

Hope that this solves the problem.

Regards,

---

### Post by aj_the_first on 2009-07-06
Damn, I already have those privilages, I set that up right when I got the computer.  So it isn't that.
Here is another odd thing I just found out when I switched users, don't know if it will help: I had a mouse plugged in for the first time when I just switched, and it works on my profile, but not on hers.
So she has desktop effects but no usb mouse (I unplugged and replugged hoping it would recognize...nope) and I have a usb mouse, but no desktop effects.

---

