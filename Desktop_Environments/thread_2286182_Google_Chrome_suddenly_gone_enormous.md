---
title: "Google Chrome suddenly gone enormous"
date: 2015-07-10
forum: Desktop Environments
---

### Post by Jonners59 on 2015-07-10
Really odd.  Google-Chrome was working fine, then suddenly, this AM it opens really huge.  I have deleted the entire cache in /Home/user/.cache, but it made no difference.

Please see attached.

---

### Post by vasa1 on 2015-07-10
With Google Chrome not running (even in the background), rename ~/.config/google-chrome/Default to something else and see if the problem goes away when you start the browser up again. Because you've renamed the profile, a new profile with be created.

If the problem doesn't go away, it maybe that your theme is corrupted somehow.

---

### Post by Jonners59 on 2015-07-11
Thanks
It got even bigger :-)
I may have to purge it and start again..

---

### Post by Jonners59 on 2015-07-13
OK, I have found out that this is a known bug.....

There is a temp fix.  Add
```
 --force-device-scale-factor
```
to the cmd to open the app.  If using in a pannel, which I do then I changed the  cmd to
```
/usr/bin/google-chrome-stable %U  --force-device-scale-factor
```

I.e. right click the panel icon
Select properties
and change the cmd line that opens the app to the above.

Hope this helps others until the bug is fixed.

---

