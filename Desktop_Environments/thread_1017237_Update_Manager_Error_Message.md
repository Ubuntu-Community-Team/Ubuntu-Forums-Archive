---
title: "Update Manager Error Message"
date: 2008-12-20
forum: Desktop Environments
---

### Post by arepaking on 2008-12-20
Hello experts,
When the update manager starts to check for updates, at the end of the process I received the following error message:
[B]
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE[/B]

My guts tells me that something is not right in System->Administration->Software Sources, specifically speaking in the tab called "Third Party Software".

Now, I am using VirtualBox 2.0.6. Could anyone tell me how to properly set up the link so the Update Manager can get updates without receiving this error?

Thanks in advance for your help.
AK

---

### Post by howefield on 2008-12-20
Try using this command via terminal

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

More detail at [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by arepaking on 2008-12-20
Hi,
Thanks for your reply. 

But why do we need the key?

I checked the website you mentioned and I notice that we can download the key from there.

Thanks again,
AK

---

