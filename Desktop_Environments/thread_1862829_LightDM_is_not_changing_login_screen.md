---
title: "LightDM is not changing login screen"
date: 2011-10-17
forum: Desktop Environments
---

### Post by BigTobster on 2011-10-17
I am trying to change the image of the login screen after upgrade to Ubuntu 11.10

I followed this tutorial

[http://www.webupd8.org/2011/09/how-to-change-lightdm-login-screen.html](http://www.webupd8.org/2011/09/how-to-change-lightdm-login-screen.html)

Which seems to be the common method.

Whilst this does change the login image from the default purple swirlyness, it does NOT change it to what I would like it to. The new image is about 250KB, same file type (.png) and in the same folder with the same filename as what the orignal image was.

I have used lightDM Manager on Ubuntu 11.10 as well as terminal changes to get this to work with no joy.

Any ideas?

Thanks in advance

---

### Post by BigTobster on 2011-10-18
Solved.

The above does not work if the Home Folder is encrypted (image source for the Login Screen is stored in a hidden folder in the Home Directory).

2 Solutions

[LIST=1]
[*]Remove Home Folder Encryption (More trouble than it's worth...)
[*]Make the sourced image "Read Only" in permissions
[/LIST]

---

