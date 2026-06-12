---
title: "Problems with Twinview"
date: 2009-10-22
forum: Desktop Environments
---

### Post by Dave_57204 on 2009-10-22
Hello, I recently picked up a second monitor, I am using twinview and it works fine except when i shutdown or restart the computer. the settings dont seem to saving. So I keep having to go in and set everything up again? anyone know how to fix this? Any help is greatly appreciated

Ok, Looks like I was forgetting to hit Save to config file, But when I try that I get this message: Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'

---

### Post by kbielefe on 2009-10-22
You probably need to run nvidia-settings as root.
```
sudo nvidia-settings
```

---

### Post by earthpigg on 2009-10-22
> **kbielefe said:**
> You probably need to run nvidia-settings as root.
```
sudo nvidia-settings
```

+1, and make sure you click 'save'.

post back if you continue to have problems.

---

### Post by Dave_57204 on 2009-10-22
Yup, It works now, thanks alot. :)

---

### Post by RTrev on 2009-10-22
Isn't it weird that they give menu options to run nvidia-settings, but it can't work without privs and they don't prompt for privs.  Just going to confuse people who've never had to mess with these things before.

---

### Post by kbielefe on 2009-10-22
Agreed, RTrev.  You can still change the display for the current session without privs, but it doesn't stick.  I've considered filing a bug report for that one.  Pretty simple fix that's a prime candidate for papercuts.

---

### Post by earthpigg on 2009-10-22
since the NVidia drivers are non-free, changing that may be out of the hands of Ubuntu developers.

of course, you yourself can change the menu entry. right click -> edit menus.

change the command from 'nvidia-settings' to 'gksudo nvidia-settings'

---

### Post by RTrev on 2009-10-22
> **earthpigg said:**
> since the NVidia drivers are non-free, changing that may be out of the hands of Ubuntu developers.

of course, you yourself can change the menu entry. right click -> edit menus.

change the command from 'nvidia-settings' to 'gksudo nvidia-settings'

Um, if we can do it, how come the Ubuntu folks can't set it that way themselves?  Not that I mean to sound critical, I'm just a bit puzzled.  Maybe it was a simple oversight to not include the gksudo in the menu?

BTW, I never knew about that right-click menu-edit trick.. so thanks for that. :)

---

### Post by earthpigg on 2009-10-22
> **RTrev said:**
> Um, if we can do it, how come the Ubuntu folks can't set it that way themselves?  Not that I mean to sound critical, I'm just a bit puzzled.  Maybe it was a simple oversight to not include the gksudo in the menu?

BTW, I never knew about that right-click menu-edit trick.. so thanks for that. :)

non-free software is puzzling, i agree.

note that i said it was possible for that to be the case, not that i knew that to be a fact.

we would have to look into the terms under which NVidia is allowing Ubuntu (and others) to distribute and redistribute their non-free NVidia drivers.

since it is NVidia's proprietary software, they can release it under ***whatever terms they like*** - even if it means the community must "right click on the menu -> edit menus" to make it work properly. 

i only suspect this because this bug has been around with all nvidia drivers for soooo long, and the fix is sooooo freaking obvious, yet still has not been corrected.

---

### Post by RTrev on 2009-10-22
> **earthpigg said:**
> 
since it is NVidia's proprietary software, they can release it under ***whatever terms they like*** - even if it means the community must "right click on the menu -> edit menus" to make it work properly.

Thanks.  Never realized how messy the whole process could become.

We need a new emoticom here.. Spock raising one eyebrow. :???:

---

### Post by doas777 on 2009-10-22
my twinview or xscreen config has always come up at boot ( I learned the 'gksu nvidia-settings' thing when I first started), but some of the more esoteric driver config may not load by default even if you have your xconfig correctly saved (overscan for instance, which is weird as that is configable in xorg.conf). in these cases i had to run 'gksu nvidia-settings -l' at login. rather sucked, but at least overscan control did work (I've had problems with that in past particularly with 8300 and 8400 cards).

---

