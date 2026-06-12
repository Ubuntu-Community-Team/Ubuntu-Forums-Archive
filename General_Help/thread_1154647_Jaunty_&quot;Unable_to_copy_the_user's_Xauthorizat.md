---
title: "Jaunty: &quot;Unable to copy the user's Xauthorization file&quot;"
date: 2009-05-10
forum: General Help
---

### Post by matthew.ball on 2009-05-10
Hi,

I tried to update the 2.6.28 kernel to 2.6.30 yesterday, unfortunately the process didn't go as smooth as I would have liked it to, but oh well, I'm pretty sure 2.6.30 is working now (I finally get acpi readings - the whole reason I upgraded, so cool).

But, I managed to fubar my nvidia driver in the process I guess.
I have found a driver which works with DKMS (re: [https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)), but I'm not entirely sure what to download... So I figured I'd try and add the deb, and deb-src lines to my software sources list, see if any new nvidia updates were available.

Then I tried to open software sources, and got the error "Failed to run /usr/bin/software-properties-gtk as user root", with the above message perhaps being the cause(?), then just for giggles I tried to open Update Manager, which opened fine, but then I clicked on the Check for Updates button, I get "Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '52428837' '--update-at-startup' as user root.", again with the above message perhaps being the cause...

Umm, not really sure what the problem is, could anyone offer any help? Heh...

---

### Post by Yellow Pasque on 2009-05-10
Does this return any output?
```
ls -la ~/ | grep .Xauth
```

---

### Post by matthew.ball on 2009-05-10
Yep - I get 3 results:

chu@Lucy:~$ ls -la ~/ | grep .Xauth
-rw-------  1 root root     164 2009-04-03 20:54 .Xauthority
-rw-------  2 chu  chu        0 2009-05-10 14:32 .Xauthority-c
-rw-------  2 chu  chu        0 2009-05-10 14:32 .Xauthority-l

---

### Post by Yellow Pasque on 2009-05-10
Your .Xauthority file should be owned by your user, not root.
```
sudo chown chu:chu ~/.Xauthority
```

---

### Post by matthew.ball on 2009-05-10
Thanks very much.

---

### Post by sihelset on 2010-02-23
I had the same problem (and some others) after upgrade, but this certainly helped me. Thanks!

---

### Post by jasonsirota on 2011-03-10
I am having the same issue but I do not have an Xauth file, the command 

```
ls -la ~/ | grep .Xauth
```

does not return any results for me.

I am trying to run Ubuntu over xrdp using sesman-xvnc and it looks like some functions don't correctly (like this one) over the remote interface.

Any help appreciated!
Jason

---

### Post by Hitchhiker76 on 2011-03-15
I am having the exact same issue with the same results as jasonsirota.

---

