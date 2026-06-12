---
title: "Dennis"
date: 2009-03-01
forum: General Help
---

### Post by dpreed77 on 2009-03-01
Hi, i am using Ubuntu 8.10. I have installed fonts to /usr/share/fonts/truetype/msttcorefonts
When i added more fonts .ttf to that folder they have an X by them I tried to refresh the cache, i tried restarting, but the x wont go away and i cannot use them. Can anyone tell me how to fix this. 
Thanks in advance!

---

### Post by fragos on 2009-03-02
There's more than one place where fonts can be stored. I've found what works best for me is to place the indivudual fonts I add in /home/{user}/.fonts. After the next boot or running "sudo fc-cache -fv". the fonts you placed there are availble to applications like OpenOffice and GIMP. A side benefit is that it's very easy for you to identify the fonts you've added if you choose to to a clean install update in the future. 

Note: that if you run fc-cache currently open applications that use fonts won't be able to see the new fonts until they are restarted.

---

