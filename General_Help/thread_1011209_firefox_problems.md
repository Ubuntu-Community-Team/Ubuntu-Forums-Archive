---
title: "firefox problems"
date: 2008-12-14
forum: General Help
---

### Post by wildmanne39 on 2008-12-14
Hi My firefox is broken and I uninstalled it and reinstalled it but it keeps giving me the same problem. I guess it is not removing the config file. Can anyone tell me how to get rid of the config file so I can reinstall fresh. Thanks in advance.

---

### Post by taurus on 2008-12-14
I assume you installed some add-ons that didn't agree with firefox.  Try removing either ~/.mozilla/firefox or even the ~/.mozilla.

---

### Post by Ender41 on 2008-12-14
> **wildmanne39 said:**
> Hi My firefox is broken and I uninstalled it and reinstalled it but it keeps giving me the same problem. I guess it is not removing the config file. Can anyone tell me how to get rid of the config file so I can reinstall fresh. Thanks in advance.


In what way is it broken, what is it that requires you to uninstall and reinstall ? Are you sure that an uninstall and reinstall will fix the problem anyway. It could be something as simple as a lock or .parentlock file that is breaking it.


Ender

---

### Post by wildmanne39 on 2008-12-14
> **taurus said:**
> I assume you installed some add-ons that didn't agree with firefox.  Try removing either ~/.mozilla/firefox or even the ~/.mozilla.
Hi, I have tried to remove the files as you suggested but it keeps telling me it is dir and it wont let me delete it. I lost my buttons on the top to close fire fox and it extends all the way to the bottom of the screen when firefox is open covering up my task bar at the bottom. I have tried everything that I know to fix it that is why I tried to reinstall it. If you can tell me how to delete the directory I think it will fix it. Thank you for helping me I really appreciate it.

---

### Post by ee19921 on 2008-12-14
> **wildmanne39 said:**
> Hi, I have tried to remove the files as you suggested but it keeps telling me it is dir and it wont let me delete it. I lost my buttons on the top to close fire fox and it extends all the way to the bottom of the screen when firefox is open covering up my task bar at the bottom. I have tried everything that I know to fix it that is why I tried to reinstall it. If you can tell me how to delete the directory I think it will fix it. Thank you for helping me I really appreciate it.

To delete a directory and it's contents use "rm -R ~/.mozilla"

---

### Post by wildmanne39 on 2008-12-14
Hi, it is still not letting me remove the directory, now it is asking me if I want to remove the write protected files but when I type y and hit enter it doent remove the file. Any suggestions? Thank you for your help so far as you can tell I dont have much experience working with bash. I am going to buy a book with the commands maybe that will help me.

---

### Post by amdalex on 2008-12-14
Are you putting sudo infront of the commands?

---

### Post by wildmanne39 on 2008-12-14
No I am not do I need to?

---

### Post by wildmanne39 on 2008-12-14
Thank you that was the problem. It is fixed. I appreciate all your help.

---

### Post by Ender41 on 2008-12-15
> **wildmanne39 said:**
> Thank you that was the problem. It is fixed. I appreciate all your help.

Glad you got it fixed even if the solution was a little drastic. Just a thought, did you try hitting the F11 key fullscreen mode in and out for firefox.

Ender

---

