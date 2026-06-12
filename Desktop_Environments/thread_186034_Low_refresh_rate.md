---
title: "Low refresh rate"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Zdravko on 2006-06-01
Hi there!
I just started using Dapper a few minutes ago... Crystal bright colors - splendid!
But I have a problem with the refresh rate. My 19" Compaq P910 can support up to 100-120Hz at 1024x768, but the System tool allows only 60Hz. I had the same problem with Breezy. I remember I had to change several lines in xorg.conf. What do I have to do now?
Best regards

---

### Post by LAurel on 2006-06-01
When I had refresh rate problems, I ran the command
```
sudo dpkg-reconfigure xserver-xorg
```
(thanks, tchock :) )

Just accept the default choices regarding keyboard and mouse.
It will come to a part where it will detect your display.
Then, you will be asked to select which resolutions you want to be able to use.
Finally, you will be asked to select the highest refresh rate you want to be able to use (you will have three choices: simple, medium and advanced - medium is the most common-sense, it will show you all resolutions you selected earlier each with corresponding refresh rates).

---

### Post by Zdravko on 2006-06-01
[LAurel]("http://ubuntuforums.org/member.php?u=103928"), thank you very much - it worked!

---

