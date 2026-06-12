---
title: "Problems with internet page loading."
date: 2009-01-31
forum: General Help
---

### Post by dsrr47 on 2009-01-31
I have just now been starting to have problems with firefox. When I first installed ubuntu i had no problems at all with any pages. I decided since I was surfing the web to get a firewall. Well i got Lokkit. I configured it. Afterwards my browser will only Load certain pages quickly. Pages like google yahoo ect... but other pages it wouldn't work such as MSN hotmail and various other sites. I thought lokkit might be the problem so I uninstalled it it and removed it with the command "sudo apt-get purge lokkit". Well lokkit is now removed but I am still having problems loading pages. any help out there?

---

### Post by gettinoriginal on 2009-02-01
This works, I have done it:
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

You also might want to try this to get rid of dependencies left over after uninstallation:
```
sudo apt-get autoclean
```

---

