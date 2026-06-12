---
title: "How to reset compiz settings from command-line to default system settings."
date: 2010-01-31
forum: Desktop Environments
---

### Post by alex_kent_18 on 2010-01-31
Hi folks,

Did you play too much with compiz and after-a-while you realize that certain functions are not working anymore?

Well, just follow the steps below:

> gconftool-2 --recursive-unset /apps/compiz

Then,

> Restart your PC / lappy 

Special Thanks to the people in following link:

Reference : 
[http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html]("http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html")

---

### Post by aspergill on 2010-09-16
Thanks for saving my butt. Somehow while sitting the airport I managed to set the opacity of every single window in my system to 0%. I had a good freakout with my newly dubbed "Invisible Linux", then found this page, and now my computer has stopped being a vampire's reflection.

---

### Post by afrodeity on 2010-11-06
or just restart compiz

```

compiz --replace

```

---

### Post by stolid_agnostic on 2011-01-15
> **alex_kent_18 said:**
> Hi folks,

Did you play too much with compiz and after-a-while you realize that certain functions are not working anymore?

Well, just follow the steps below:



Then,



Special Thanks to the people in following link:

Reference : 
[http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html]("http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html")
thansk a lot! saved me from /dev/null-ing my profile!

---

### Post by f3rland on 2011-05-08
> **aspergill said:**
> Thanks for saving my butt. Somehow while sitting the airport I managed to set the opacity of every single window in my system to 0%. I had a good freakout with my newly dubbed "Invisible Linux", then found this page, and now my computer has stopped being a vampire's reflection.

Exactly the same here. that thread save my night. :popcorn:

thanks you soooo much!!

---

### Post by Hoaggie on 2011-11-20
[alex_kent_18, ]("http://ubuntuforums.org/member.php?u=359707")
Thank you very much, saved me a great deal of stress:)
[]("http://ubuntuforums.org/member.php?u=359707")

---

