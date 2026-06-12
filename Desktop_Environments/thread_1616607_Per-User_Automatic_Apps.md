---
title: "Per-User Automatic Apps"
date: 2010-11-08
forum: Desktop Environments
---

### Post by BigMamma on 2010-11-08
I need to have my system automatically source a specific csh environment and run a custom script. In the past, I've had a .cshrc and a .login file for each user that did what needed to be done for that specific user. These were sourced upon login and the appropriate stuff ran automatically. With gnome however, a login shell is not produced automatically, so the .cshrc and .login files aren't being sourced. 
 
I've tried exec'ing a csh -l from a .Xsession.d file, but since my users' stuff is csh and the run-parts stuff under .Xsession.d is Bourne shell, it isn't working. 
 
Can anyone help?

---

