---
title: "How to put down resolution?"
date: 2008-02-26
forum: Desktop Effects &amp; Customization
---

### Post by rasmus91 on 2008-02-26
hi 

I have a little problem, i cant put down the screen resolution on my computer. if i put it down to 1024x768 at 51hz it'll just go back again...

any ideas on how to change it?

---

### Post by Therion on 2008-02-26
You can manually reconfigure your config file for X or you can try using [DisplayConfigGTK]("http://kevin.vanzonneveld.net/techblog/article/change_more_display_settings_in_ubuntu/").

---

### Post by rasmus91 on 2008-02-26
Okay... i did this, and I'm able to change it to 1024x768 but thats only the numbers, then i press keep configuration, but it doesn't change the resolution... :(

---

### Post by Therion on 2008-02-26
What are the specs of your graphics card or integrated graphics chipset?  You can either ```
sudo apt-get install sysinfo
``` or ```
lspci
``` for that information.

It's possible (though unlikely) that you may not be able to display resolutions any higher than what you have now.

---

### Post by rasmus91 on 2008-02-27
No wait, i fixed the problem... lol, it was because i had to restart my computer... :D But thanks anyway!

---

