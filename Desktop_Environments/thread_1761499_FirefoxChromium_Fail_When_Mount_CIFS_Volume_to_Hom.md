---
title: "Firefox/Chromium Fail When Mount CIFS Volume to Home Directory"
date: 2011-05-18
forum: Desktop Environments
---

### Post by showmanlkz on 2011-05-18
Hi guys,

I am using Ubuntu 10.10 Desktop amd64. I configured to mount a CIFS volume to my home directory.

The mounted home directory works fine, I can see everything I get and do whatever I want (like read, modify and add files) in the home directory.

However, Firefox lost its functionalities, it could not fully startup. I said not fully because Firefox's GUI was presented but it didn't accept user input, like entering a URL then hit enter, nothing happened.

Then I installed Chromium and tried: it tried to startup but failed and shutdown by itself.

I switched my home directory back to local drive, they all ran fine!!

Since Firefox put .mozilla directory under home, I guess it maybe some file locking issue on CIFS volume????

Any idea will be great!
Derrick

---

### Post by showmanlkz on 2011-05-18
bump! any one with the similar experiences?? I guess it's not too rare to CIFS mount home directory on Desktop??

---

### Post by showmanlkz on 2011-05-18
A fairly quick fix for Firefox would be adding "nobrl" to the mount options. Now Firefox happy.

However, Chromium still fails to launch with "nobrl".

---

