---
title: "Wireless not connecting to a network?"
date: 2009-05-03
forum: Desktop Environments
---

### Post by cbwcjw on 2009-05-03
When I attempt to connect to my network, named "Fasttimes", it begins, but then re-opens the window asking for the WEP key. If I enter the WEP Key in, it opens again, asking for the WEP key once more.

I don't really get whats going on, considering its able to find networks showing its working. This is definitely KDE specific for me.

---

### Post by wirechief on 2009-05-03
you should try researching  your issue at [https://bugs.launchpad.net/](https://bugs.launchpad.net/)
using short keywords for your search.
I have heard others complain about knetwork manger that might be one of the keywords to search on.

---

### Post by hictio on 2009-05-03
Are you sure that the window that pops up it is asking you for the WEP key to your Access Point?
Isn't asking the password to unlock your keyring?

---

### Post by loray on 2009-05-04
I just could connect to my wireless network  using kdewallet to store my password. Every time I open kubuntu kdewallet askme for the password and then i can connect.

---

### Post by cbwcjw on 2009-05-04
Im definitley not having an issue with kwallet, just this:

[IMG]http://chuckw.com/wireless.png[/IMG]

That keeps popping up, no matter how many times I put in the correct password.

---

### Post by abi0909 on 2009-05-04
Maybe you could check your wireless settings on the router. Before working on this from Ubuntu's end, try on the end of the router. 
See if you could connect wireless using Windows (if you have one). 
Else, check if its WEP or WPA setup on the router by connecting it wired with your computer and checking the firmware of the router.

---

### Post by cbwcjw on 2009-05-04
It works in windows and gnome. I troubleshooted just a tiny bit here :) I just dont know why it keeps doing the thing with the network manager.

---

### Post by cbwcjw on 2009-05-05
Solved, Im now using WICD

```

sudo apt-get install wicd

```

---

