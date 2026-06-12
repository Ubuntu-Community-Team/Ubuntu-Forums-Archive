---
title: "Networking -- command line only Ubuntu"
date: 2009-04-13
forum: General Help
---

### Post by willz06jw on 2009-04-13
Hi and let me start by saying thanks for reading/helping,

I am running command-line only Ubuntu and I would like to connect to
the information on a Windows XP Shared drive.  I am running 9.04 but
I don't think that really matters since I am using a command-line 
only alternative install.  

Thanks for the help again,
Will

---

### Post by antikristian on 2009-04-13
As long as you have a network connection I believe you can do something like this:

```

mkdir /media/winshare
mount -t cifs //dnsnameOrIPaddressWinXP/name/of/share /media/winshare -o user=YourUsername,password=YourPassword
```

If you want it permanent you add i to /etc/fstab
```
//dnsnameOrIPaddressWinXP/name/of/share /media/winshare cifs user=YourUsername,password=YourPassword 0 0
```

Other options that could be nice to add would be iocharset=utf-8, noauto (if you want to mount it manually when you need it) 

Hope this helps:)

---

