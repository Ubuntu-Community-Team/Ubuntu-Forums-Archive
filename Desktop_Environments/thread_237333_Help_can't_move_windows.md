---
title: "Help can't move windows"
date: 2006-08-16
forum: Desktop Environments
---

### Post by st0ney on 2006-08-16
I have been playing around with compiz lately and I think I screwed something up.  I have it setup so that the compiz is running on a seperate session than the standard gnome session.  The Xgl session is up and running fine but when I switch over to the gnome session the windows act funny.  I cannot resize windows or click on a title bar to move them.  I am unaware of any other issues but I'm not sure how to fix this one.  Please help.

Thanks.

---

### Post by JerMe on 2006-08-16
it's because you window decorator (probably gnome-window-decorator, or could be cgwd) isn't working.  Try running your /usr/bin/startcompiz script again.  Remove /usr/bin/startcompiz from System > Preferences > Sessions > Startup Programs, and run /usr/bin/startcompiz manually on login instead.

Are you using cgwd?

---

