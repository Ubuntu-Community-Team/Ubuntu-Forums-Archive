---
title: "im switching to firefox beta 2...."
date: 2006-09-05
forum: Desktop Environments
---

### Post by rabid9797 on 2006-09-05
and i need to know how i can remove the current version of ff without removing any other packeges from system, or how to replace beta with 1.5...

at the moment this is what happens:

```

rabid9797@rabid9797-ubuntu:~$ sudo apt-get remove firefox
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  firefox firefox-gnome-support gnome-app-install ubuntu-desktop yelp
0 upgraded, 0 newly installed, 5 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 27.5MB disk space will be freed.
Do you want to continue [Y/n]?

```

so how do i get rid of firefox without removing the other packeges(which would be bad)...or...how do i just replace my existing firefox version with beta?

---

### Post by kerry_s on 2006-09-05
You can just swap the firefox folder. Go to /usr/lib/firefox rename firefox to firefox.old then rename the swiftfox folder to firefox and put it there, you need to be root to do this. if somewhere down the line you get problems with swiftfox just rename the old folder back.

---

### Post by jolan_jj on 2006-09-05
Why replace? you can just install it as a new browser (beta isn't in the repositories anyway, so you have to download it and install manually). Download the beta and install to a directory of your choice (I have it in my /home directory). If you want it to be your default browser you can open ff2beta and go to Edit->Properties->General and set it to your default browser there. Then it should install the plugins and extensions automatically. 
By keeping your original ff you have the possibility  to go back to it if anything should go wrong...

PS. It's possible you will have to make a symlink to your java libraries manually in order to make java work.

---

### Post by rabid9797 on 2006-09-05
i just did what jlan_jj said. my primary reason for wanting to replace it was that flash player installed automatically only to ff in /usr/lib/ , but i figured out i could just do it manually =/ so problem solved.

thanks for the help guys

---

