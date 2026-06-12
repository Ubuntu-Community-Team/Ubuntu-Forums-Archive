---
title: "Firefox 1.9.04 and problems installing firefox 3.0.4"
date: 2008-12-16
forum: General Help
---

### Post by lgp171188 on 2008-12-16
I tried to install firefox 3.0.4 from the tarball and extracted it in /opt. When I ran it as a superuser, the new firefox started. But when I ran it as a normal user, the old firefox started. So I manually deleted all firefox installations and installed firefox-3.0 through the ubuntu repository and it got installed in /usr/lib/firefox-3.0.4. But when I open the "about:" page in firefox, the version shows up as 1.9.0.4 whereas the About Firefox dialog shows Firefox 3.0.4. I am confused and I want to have a clean installation. Please help me:confused:

---

### Post by Polygon on 2008-12-16
try uninstalling any instances of firefox that you have, then reinstalling. and if that fails, you can try moving your firefox profile (i think its in ~/mozilla/firefox) and then try starting firefox again, and if then 3.0 works, you can just copy over your bookmarks from the old profile and use the newly created one

---

### Post by lgp171188 on 2008-12-16
I removed all firefox folders after uninstalling it. Then I untarred the tarballed and tried to run firefox as normal user, the firefox started but a lot of things like the bookmarks and other stuff were missing. But once again when I ran it as a superuser, things were fine. Now I have a crippled version of firefox for my normal user.

---

### Post by lgp171188 on 2008-12-16
How do I restore firefox now? I am able to run it only as a superuser, reinstalling from ubuntu repository doesn't seem to solve the problem and I get a message saying "There is already a firefox process running..." when in reality there isn't any. Please help me restore firefox.

---

