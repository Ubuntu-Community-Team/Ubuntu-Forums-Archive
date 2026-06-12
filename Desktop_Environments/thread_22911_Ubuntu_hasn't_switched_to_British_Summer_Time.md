---
title: "Ubuntu hasn't switched to British Summer Time"
date: 2005-03-30
forum: Desktop Environments
---

### Post by jnoreiko on 2005-03-30
Clocks changed in the UK last Sunday, and my ubuntu is now an hour ahead. Since clocks went forward, it looks like two hours have somehow been added on ubuntu. Is this because Windows has directly changed the system clock and ubuntu doesn't?

I've checked the time zone setting; it's correctly set to GMT/London.

---

### Post by bailout on 2005-03-30
The trick with time clocks is to only allow one OS to automatically adjust the bios clock. It sounds as if both win and ubuntu have done it on your pc. If this is the case then your win os will now be one hour ahead when you go back to it. There was a dialogue in the ubuntu install where you should have answered no to allowing ubuntu to handle the hardware clock. I did so and ubuntu has correctly moved to summer time and left the bios alone.

---

### Post by jnoreiko on 2005-03-31
I remember the ubuntu install dialog, and I'm pretty sure I answered no to it.

Windows still has the correct time.

---

### Post by TjaBBe on 2005-03-31
[QUOTE=jnoreiko]I remember the ubuntu install dialog, and I'm pretty sure I answered no to it.

Windows still has the correct time.[/QUOTE]

Your hardware clock is right, but Linux usually doesn't change the hardware clock, but instead applies an offset according to your timezone. Obviously this is your problem. There is a way of telling Linux to do it de Windows-way (and I'm pretty sure there is a dialog for this in the Ubuntu install).

But don't go reinstalling stuff or something ;). Offcourse it's fixable, I don't know the exact fix by head, but I'm sure it will not be that hard to find. Just google a bit :).

[edit]
I just remembered: I believe you shouldn't set a timezone if you are installing Linux next to windows. That will solve your problem. I don't remember exactly how to unset the timezone. (I think you should remove /etc/localtime or something, but don't rush into that, at least backup localtime first if you are to try that!) 

I would suggest google again to make sure first :).
[/edit]

---

### Post by wxm505 on 2005-03-31
My box changed to summer time automaticlly :)
It reminded me to catch the train at the correct time.
Although all the other devices such as Mobile , clock
did not changed automaticly.
It seems my Ubuntu worked pretty well.

---

### Post by jnoreiko on 2005-04-05
I found this page on the ubuntu site: [http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-10-20.4373491988/view](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-10-20.4373491988/view)

I've made the changes it suggests, but I'm still an hour ahead on Ubuntu.

---

### Post by jnoreiko on 2005-04-05
[QUOTE=jnoreiko]I've made the changes it suggests, but I'm still an hour ahead on Ubuntu.[/QUOTE]

On returning to Windows, I found that was an hour ahead too. So I set that back, and Linux is correct too now.

Hopefully it's now fixed.

---

