---
title: "problems with apt-get update"
date: 2009-03-06
forum: General Help
---

### Post by Dallywood on 2009-03-06
I just installed Ubuntu 8.10.
I can't seem to get it to boot properly.
I am going into recovery mode and using the root shell prompt to try and repair broken packages because that's what someone told me to do but I end up getting the messages:

Failed to fetch [http://security.ubuntu.com/](http://security.ubuntu.com/).....
could not resolve 'security.ubuntu.com'
and 
Failed to fetch [http://ca.archive.ubuntu.com/](http://ca.archive.ubuntu.com/)....
could not resolve 'ca.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

when I run apt-get update I get the same could not resolve ....

any help would be appreciated 
thanks

---

### Post by entr3p on 2009-03-06
Your chosen server may be fault. Follow this guide:
***_Updating Your Download Server_***
For this task you will have to go to “System --> Administration --> Software Sources”. It will open up in the “Ubuntu Software” tab. In that tab go down to the drop down menu next to the “Download from:” text and click on “Other...”.
Once you click on “Other...” a new window will appear. Choose a Country and then click on “Select Best Server”. Once it's done it will highlight the suggested server so click on “Choose Server”, and that window will close.
Now close the window and click  “Reload” in the new window that appears and you're done.

Note: If the window “freezes” when you click on the “Reload” button then close the window, go to “Applications --> Add/Remove...” and the same window will appear again. Press “Reload” and this time it should succesfully update your server without freezing.

---

### Post by SuperSonic4 on 2009-03-06
Can you ping google or the router?

```
ping -c 3 www.google.com
```

```
ping -c 3 192.168.0.1
```

---

### Post by Dallywood on 2009-03-06
when I try to ping I get
connect: Network is unreachable

---

### Post by entr3p on 2009-03-06
> **Dallywood said:**
> when I try to ping I get
connect: Network is unreachable

Then it's not with your server but maybe your not even connected to the internet :P.

---

### Post by Dallywood on 2009-03-06
when I try to login after I type in my username and password everything just stalls and won't go any further

---

