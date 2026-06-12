---
title: "SuperTuxKart Resolution Help Needed"
date: 2012-01-08
forum: Gaming &amp; Leisure
---

### Post by norgath on 2012-01-08
I ended up setting the resolution for STK to what I thought were the correct parameters. It appears I was mistaken, as whenever I launch it my monitor tells me that it is "out of range." How do I change the config file to bring back the resolution to 800x600?

---

### Post by Arthur_D on 2012-01-09
Hi, this is a bit strange, because if you don't confirm a resolution is working before the timeout it should blacklist the resolution and bring you back to the last working one. However, if you've accidentally blacklisted a working resolution you should be able to resolve the issue by following [http://supertuxkart.sourceforge.net/FAQ#Where_does_STK_store_the_user_config_file.3F](http://supertuxkart.sourceforge.net/FAQ#Where_does_STK_store_the_user_config_file.3F) and editing the config.xml file.

---

### Post by norgath on 2012-01-09
Thanks, that solved everything. Apparently it was the fullscreen that was the problem. Changed its value back to #f and everything works fine now. My appreciations.

---

### Post by Arthur_D on 2012-01-09
Glad you got it sorted. :)

---

