---
title: "Kannada font problem in Ubundu-firefox"
date: 2006-07-07
forum: Desktop Environments
---

### Post by CrazyGenie on 2006-07-07
Hi, I have observed problem in Kannada fonts rendering in Firefox. This problem is traced to some in-compatibility with ttf-freefonts package. The ttf-kannada-fonts appear clumpsy in firefox, if freefonts exist in the system. Currently, the fix I found was to remove the font files from /usr/share/fonts/truetype/freefont/ directory and running fc-cache -fsv (Note: I just removed font files, not the ttf-freefonts package itself, as it may break some dependencies).

Can this problem be fixed? I have seen the same problem in both Breezy and Dapper.:-k

---

