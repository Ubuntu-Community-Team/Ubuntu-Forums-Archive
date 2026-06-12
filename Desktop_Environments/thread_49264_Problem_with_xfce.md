---
title: "Problem with xfce"
date: 2005-07-15
forum: Desktop Environments
---

### Post by ignavia on 2005-07-15
I have an old P2-233 Dell Latitude that I wanted to install Linux on, so I ran Ubuntu Hoary last night. Obviously, neither KDE nor GNOME are going to run very well at all, so I want to install XFCE. I enabled the universe and multiverse repositories, and did an apt-get update, then apt-get install xfce, but that didn't give me an option on login for xfce. Then I found out I was supposed to run apt-get install xfce4. So I did, and it seems to run fine exept with xfce4-panel, which it gives an MD5sum error for. This time, however, I got an xfce login option, so I selected it, but it boots me right back to the login screen. I get a screen with an error log, but I can't copy and paste between login  sessions. Do you think it's because I installed xfce before xfce4, the panel issue, or both. How do I install the panel having installed everything else through apt-get?

Thanks.

---

### Post by rosslaird on 2005-07-15
If I were you, what I would first do is uninstall all xfce packages. Then add these repos to your sources.list:

# os-works.com #

deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

Then apt-get update

Then visit the os-works site and follow the directions:

[http://os-works.com/view/debian/](http://os-works.com/view/debian/)

Good luck.

Ross

---

### Post by ignavia on 2005-07-16
[QUOTE=rosslaird]If I were you, what I would first do is uninstall all xfce packages. Then add these repos to your sources.list:

# os-works.com #

deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

Then apt-get update

Then visit the os-works site and follow the directions:

[http://os-works.com/view/debian/](http://os-works.com/view/debian/)

Good luck.

Ross[/QUOTE]
 Thanks for the reply. It worked. I wasn't sure at first how to remove it because apt-get remove xfce xfce4 only removed two packages. I think it was apt-get remove libxfce4util-1, according to that link. Then I added those repositories, reinstalled, and voila!

Thanks again. It runs a lot better now.

---

### Post by emperor on 2005-07-16
I installed xfce4 on my Dell Inspiron 3200 266XT and did not find it necessary to use the  os-works  repo's.  Entry  in gdm was  added  and xfce4 session ran fine.

---

### Post by ignavia on 2005-07-16
[QUOTE=emperor]I installed xfce4 on my Dell Inspiron 3200 266XT and did not find it necessary to use the  os-works  repo's.  Entry  in gdm was  added  and xfce4 session ran fine.[/QUOTE]
 I'm imagining you didn't get an md5sum error on xfce4-panel. I think if the panel had worked, I wouldn't have had any problems.

---

### Post by ounn on 2005-07-16
Hi

That error is always happen to me to with other packages. When you see that error try, and try and try .... until the instalation goes ok, or else change yours backports utrl to ones more stable. See the backports mirrors somewhere here in the forum.

ounn

---

