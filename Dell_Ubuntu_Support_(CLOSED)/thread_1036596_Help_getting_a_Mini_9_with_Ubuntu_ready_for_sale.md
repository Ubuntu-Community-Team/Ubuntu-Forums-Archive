---
title: "Help getting a Mini 9 with Ubuntu ready for sale"
date: 2009-01-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Hula2Pahoa on 2009-01-11
Aloha to all,
And from now on I will say "thanks" in my posts when you help, instead of "Mahalo" which is "Thank You" in Hawaiian :)

I am selling a Dell Mini9 Inspiron 910 with UBUNTU on eBay. It closes tonight and I promise ANY buyer it will go out the first business day after auction closes. That is why, when I list, I have till Monday to pack, wrap, postage and ship.
I don't have a whole lot on the Mini but I did use it for some secure sites before I decided to upgrade. I am now using one WITH a Webcam AND a 16 GB solid state Drive. I have no external anything to be able to connect to it to do anything that way. I know to clear the cache, cookies, history, etc. but what else? I am not familiar enough with UBUNTU to know what/where to locate this on the hard disc.:confused:
Sorry, but I was a Windows user for too long to know what to look for in Ubuntu to clear these items. I would also need to clear my user/administrator credentials as well.
Any assistance is appreciated and "thanks" will be given, as I believe in taking the time to show "thanks"!

---

### Post by ugm6hr on 2009-01-11
I have never done this, but it should be possible.

The easiest thing would be to use a USB stick to reinstall - but I assume this is not an option.

The other option is to:
1. Create a new "oem" superuser
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)
Use "oem" as the username, and whatever password you want ("oem" is fine), and make sure they have full administration access (i.e. "Executing system administration tasks")

2. Reboot and Login as "oem"
Ensure autologin is disabled first! See System -> Administration -> Login Window
Delete Trash:
```
sudo chown -R oem ~/.local/share/Trash
rm -rf ~/.local/share/Trash/*
```

3. Delete your current user and /home/username directory (substitute your username)
```
sudo userdel username -r
```

4. Run "oem-config-prepare"
```
sudo oem-config-prepare
```

In theory, this should work.

When you reboot, it should prompt you to create a new username etc.

As mentioned - I have never done this, but I can't think of any reason why it shouldn't work.

None of this "securely" deletes your data though - so if you sell it to a data recovery specialist, they will more than likely be able to recover some data.

---

