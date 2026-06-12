---
title: "cryptkeeper icon in unity"
date: 2011-06-27
forum: Desktop Environments
---

### Post by lister171254 on 2011-06-27
I've just upgraded to 11.04 from 10.10. When logginin in with the default GUI (Unity?) and selecting Crypkeeper, I cannot see the icon that enables me to mount the encrypted file system. 

In classic, that icon what at the top menu bar.

---

### Post by nilarimogard on 2011-06-28
In Natty, only a few apps are allowed to use the notification area. You must whitelist the icon to get it to show up, using the command below:
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'cryptkeeper']"
```

You can also whitelist all applications, but appindicators may become unclickable after this:
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

After any of the above commands, log out and log back in (or restart Unity).

---

### Post by atari130xe on 2011-06-28
A friend of mine has a problem: she has encrypted a folder in her home folder using cryptkeeper on Ubuntu 10.04.2 after updating 1st to 10.10 and finally to 11.04 she has a problem to find and open the folder because when she try to open the encrypted folder gets the following message:

```
This encrypted folder is currently not available

It may be located on a removable disk, or has been deleted.
```  and she swear didnt erase anything. any help_ she is desperated. thanks!

---

### Post by lister171254 on 2011-06-29
gsettings worked, lost my background though.

Thanks.

---

### Post by vladanik on 2012-02-12
I have Ubuntu 11.10. I did the following in the terminal:

gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"

however the Cryptkeeper icon doesn't show in Unity 3D, nor in Unity 2D. Any ideas?

---

