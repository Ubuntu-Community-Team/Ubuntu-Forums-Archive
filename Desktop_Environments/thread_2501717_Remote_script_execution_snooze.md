---
title: "Remote script execution snooze"
date: 2024-10-18
forum: Desktop Environments
---

### Post by mmuzar on 2024-10-18
Hello everyone, I might be lost in the channels, so Ill just ask here


Trying to find if there is a solution for my situation - managing ubuntu desktops remotely, and I have some remediation scripts that hang the system when run


Is there a way to offer a prompt to the user that will let them snooze a few times and then get forced countdown so they can plan the execution in their work day?
We could construct around yad or zenity and store user input with some countdown, but wanted to see if there an existing solution that I missed

---

### Post by TheFu on 2024-10-18
We use **ansible** and just tell people to leave their computers on the network overnight once a week.  We don't want to impact users during their work day.
It would be hard to allow users to choose to run the updates early, and leave a file to mark they've already been run which your script could test before just running them all at 6pm or 11pm or 3am.  In theory, re-running patches won't matter.  Ansible is designed to only cause changes when changes are needed, not just blindly re-running the same stuff over and over when it isn't necessary.  They call it "omnipotent".

Stop thinking like MSFT.  That isn't doing you any service.

---

### Post by ActionParsnip on 2024-10-18
> **TheFu said:**
> We use **ansible** and just tell people to leave their computers on the network overnight once a week.  We don't want to impact users during their work day.
It would be hard to allow users to choose to run the updates early, and leave a file to mark they've already been run which your script could test before just running them all at 6pm or 11pm or 3am.  In theory, re-running patches won't matter.  Ansible is designed to only cause changes when changes are needed, not just blindly re-running the same stuff over and over when it isn't necessary.  They call it "omnipotent".

Stop thinking like MSFT.  That isn't doing you any service.

idempotent

We use Ansible too :)

---

### Post by TheFu on 2024-10-18
> **ActionParsnip said:**
> idempotent

We use Ansible too :)

idempotent - yeah - that's it. ;)

---

### Post by mmuzar on 2024-10-21
> **TheFu said:**
> Stop thinking like MSFT.  That isn't doing you any service.

I like that one, since that is a mayor theme for us - completely MS oriented company with only like 300 Linux desktops :D

We are already using Landscape from ubuntu to manage devices, with a heavily customized flow for a lot of our needs we need to monitor.

Problem that we deal with in general, and would be with something like telling all those people to leave their devices on and connected at a specific time - its just not reliable, as it depends on users doing the right thing.
Primary case that I wan't to resolve is running of the CIS remediation through usg fix, that is bound to freeze the laptop for a minute, or even longer if the user is not aware that they just need to let it do its thing.

We have CINC/CHEF on the VMs but the environment for laptops was setup before that so we didn't switch to it.

---

### Post by TheFu on 2024-10-21
Tell them when patches will happen, then do it.  For systems that aren't available, use the @REBOOT option in anacron to apply patches.

In the corporate world, you can tell/train people for logins to take a few minutes.  I'd boot up my system, then login and walk away to get coffee, say good morning to coworkers, then come back to my office and everything will be ready to go.  That's a corporate thing. In a secure environment, I'd just sit there while it does everything. Can't leave a system unattended in an environment like that.

Assuming your desktops use NFS for HOME directories and LDAP for centralized account management, this shouldn't be too hard.  Of course, if you use those things, you probably can't use snap packages.

---

