---
title: "More screen resolution options?"
date: 2006-06-30
forum: Desktop Environments
---

### Post by lwr on 2006-06-30
Hi,
Can I get more options for my screen resolution? I've got quite a few, but the usable one's are eithe 1024x768, which is a bit low for my liking, or 1280x1024, which is so high that it makes most text impossible to read. I seem to remeber something like 1152×864 on Windows. Any suggestions?

Thanks

---

### Post by Ctrl+Alt+Del on 2006-06-30
You will have to edit these Resolutions to your xorg.conf
I have recently explained howto accomplish that in another thread. [http://www.ubuntuforums.org/showpost.php?p=1129718&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1129718&postcount=2)

---

### Post by lwr on 2006-06-30
Thanks for that. I did what you suggested, and some things have changed. I got rid of the 1280x1024 resolution, and it's now no longer selectable, but the 1152x864 resolution i added doesn't appear under System>Preferences>Screen Resolution. Is that because this resolution isn't supported?

---

### Post by Ctrl+Alt+Del on 2006-06-30
It should be available, but i cannot check right now because i am sitting at my Notebook with a fixed max-res of 1024x768. Normally X.org will pick the highest value from the available list, so if 1152x864 is your highest it should be running it, no need to change it via the dialogue. But then again i have never tried running it :)

---

### Post by lwr on 2006-07-17
I've recently got the 1158x864 resolutiuon working by using 
sudo dpkg-reconfigure xserver-xorg.
Thanks for all your help.

---

