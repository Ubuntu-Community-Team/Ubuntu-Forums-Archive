---
title: "Firefox and MS fonts"
date: 2005-10-23
forum: Desktop Environments
---

### Post by barry_s on 2005-10-23
Like a few other people it seems, I've had issues with Firefox (segmentation fault), and nothing seems to have resolved it. In the end I gave up, removed the ubuntu firefox package and downloaded and installed Firefox from mozilla.org. It works fine now, but it doesn't use the msfonts that I have installed, is there any way to enable this? 

Thanks

barry

---

### Post by barry_s on 2005-10-23
I managed to solve this myself, but thought I'd post the solution here in case it helps anyone. I should have learnt by now that if something doesn't behave the way you expect there are three things to check; permissions, permissions and permissions!

When I checked the msfonts the permissions were all set to read by root only. A quick chmod to 644 and all is working!

---

