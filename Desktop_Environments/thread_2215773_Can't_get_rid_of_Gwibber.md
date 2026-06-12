---
title: "Can't get rid of Gwibber"
date: 2014-04-08
forum: Desktop Environments
---

### Post by pcal on 2014-04-08
I'm confused. I don't use ANY social media by choice, and consequently have no use for Gwibber. I uninstalled it via the Ubuntu Software Centre, but still get all the updates whenever there are any for gwibber itself and all its components.

Why does the system keep on installing updates to something that isn't there? I get sick of having to scan through the entire list of updates to unselect everything related to Gwibber. Can I somehow tell the update engine to stop it?

Thanks

---

### Post by vasa1 on 2014-04-08
Can you post (between code tags) the output you get when you open a terminal and run
```
apt-get purge -s gwibber
```?

---

### Post by pcal on 2014-04-08
Thanks for your reply vasa1.
The output was...

```
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-48 mb-skeinforge linux-headers-3.2.0-48-generic-pae
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gwibber*
0 to upgrade, 0 to newly install, 1 to remove and 13 not to upgrade.
Purg gwibber
```

Does this suggest that gwibber is still actually installed?

I can (will) run it again with sudo to give effect to the change, but ...

1) If it is still there, why didn't the Software Centre remove it? (Software Centre lists it as available, but not installed.)
2) This seems to suggest, that the other bits won't be deleted, but just not get updated any more. While a welcome outcome, wouldn't removing them also be the more efficient thing to do?

Thanks

---

### Post by vasa1 on 2014-04-08
> **pcal said:**
> Thanks for your reply vasa1.
The output was...

```
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-48 mb-skeinforge linux-headers-3.2.0-48-generic-pae
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gwibber*
0 to upgrade, 0 to newly install, 1 to remove and 13 not to upgrade.
Purg gwibber
```

Does this suggest that gwibber is still actually installed?

I can (will) run it again with sudo to give effect to the change, but ...

1) If it is still there, why didn't the Software Centre remove it? (Software Centre lists it as available, but not installed.)
2) This seems to suggest, that the other bits won't be deleted, but just not get updated any more. While a welcome outcome, wouldn't removing them also be the more efficient thing to do?

Thanks
Based on the output, it does look like gwibber is still installed. But what is troublesome (to me) is the **13 not to upgrade**. I've never seen such a situation. Have you done something to result in **13 not to upgrade**? If you have, could you explain what you did?

As for **The following packages were automatically installed and are no longer required**, I suggest you run **sudo apt-get autoremove** but examine the proposed removals before accepting.

---

### Post by pcal on 2014-04-11
> **vasa1 said:**
> Based on the output, it does look like gwibber is still installed. But what is troublesome (to me) is the **13 not to upgrade**. I've never seen such a situation. Have you done something to result in **13 not to upgrade**? If you have, could you explain what you did?

Sorry for my delay in answering - real life intervened...

I'm not aware of having done anything in particular. Firstly, I selected uninstall gwibber in the Software Centre, and then each time the update system offers a list of updates, I scan through the list and unselect any that I notice relate to gwibber while wondering why they are there at all. Have never done anything else...

---

### Post by pcal on 2014-04-14
> **vasa1 said:**
> As for **The following packages were automatically installed and are no longer required**, I suggest you run **sudo apt-get autoremove** but examine the proposed removals before accepting.

I ran the autoremove command, and also re-ran the purge command with sudo. Both appeared to work.

However tonight, the update package again includes the Gwibber GTK Widgets, and Gwibber Shared Library. Not as many updates as usual - but I don't understand why there are any!!

---

