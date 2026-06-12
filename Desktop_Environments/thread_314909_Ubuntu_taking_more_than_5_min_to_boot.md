---
title: "Ubuntu taking more than 5 min to boot"
date: 2006-12-08
forum: Desktop Environments
---

### Post by hm_naveen on 2006-12-08
hi,
I sucessfully installed Ubuntu OS in to my personal computer.
But Ubuntu taking more than 5 min to boot. Only blinking cursor will be visible on my monitor.
So instead on doing power off i started to do Hibernate. It made booting faster some extent. But while doing hiberbate  error messages is displaying "Unable to save"
What i can do.Please help me regaring this.

---

### Post by studiesrule on 2006-12-08
Which version of ubuntu are you running? Also, very importantly, what are you sys specs. Another thing you should post is when exactly is it taking time. At the beginning, or after the login window?

I don't know if it will help, but in my experience, its solved all types of problems in the least bit related to graphics. press Ctrl + Alt+ F2 to get into termnial mode. Then login, and type:
sudo dpkg-reconfigure xserver-xorg.
Walk through, and select the appropriate options.
This is the second time in like 20 min. that I'm suggesting this code, and I've used it hundreds of times. It will basically reconfigure your graphics display (or X) configuration. Generally, it will work on its own, but if not, when it comes to selecting graphics drivers, choose vega, which always works. You could also use ati if you have and ATI card, or nvidia if you have a nVidia card. These are the open-source drivers.

---

### Post by coolclassic on 2006-12-08
Unbuntu may be trying to find a network when booting try disabling or reconfiguring your network connections even if you don't have one. This problem affected me on an older version.

---

