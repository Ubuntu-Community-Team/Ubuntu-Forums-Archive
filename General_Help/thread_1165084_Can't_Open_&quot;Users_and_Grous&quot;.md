---
title: "Can't Open &quot;Users and Grous&quot;"
date: 2009-05-20
forum: General Help
---

### Post by Bender2k14 on 2009-05-20
When I try to open System->Administration->Users and Groups with my account (which is the second account on the system), it gives me the follow error:

**The configuration could not be loaded**
You are not allowed to access the system configuration.

This problem does happen if I use the original account created on this system.  Using the original account, I gave my second account all possible privileges (by checking everything in the Privileges tab of the Users and Groups window).  I also checked the /etc/group file and the only group that my original account is in that my second account is not is "floppy".

Both the original account and second account execute the same command when clicking the Users and Groups menu item; namely "users-admin".  If I instead execute "sudo users-admin" (on the command line) with my second account, then the menu opens, but I cannot click unlock (because the button is disabled).  Additionally there is the following text printed to the command line:

** (users-admin:32093): CRITICAL **: Unable to lookup session information for process '32093'

Normally there is a picture of a keyring with two keys on the Unlock button (the same picture used for System->Administration->Authorization), but my second account sees a sphere (aka ball or circle).

---

### Post by tekstr1der on 2009-06-16
Seeing the same here after upgrade from Jaunty to Karmic Alpha 2. Attempting to open Administration > Users & Groups results in dialog box stating, "The configuration could not be loaded. You are not allowed to access the system configuration."

Any update on this issue?

---

### Post by bigboy_pdb on 2009-06-16
Granted that it's a new account you should check that the user is in groups 'adm' and 'admin'. Both are required to perform administrative tasks from other accounts. To make changes like that you'd need to use your account with root access.

Also, you should see if it's just 'Users and Groups' that cannot run with escalated privileges or others as well. For example, check to see if 'sudo ls', Synaptic Package Manager, or 'Time and Date' runs. If you can run commands as root or open programs that require root privileges (and make modifications that require root privileges), but you can't open 'Users and Groups' then the problem might be with 'Users and Groups' or the authentication program. However, if the problem is with all programs that require administrative privileges then it's a problem with the groups you are a member of or your account settings.

---

### Post by eris23 on 2009-06-19
Same problem.  I can sudo from the command line.  I'm in the adm and admin groups.  Can't open "Users and Groups" from the menu.  Can open Synaptic.  Running Karmic.

---

### Post by tekstr1der on 2009-07-08
Ditto post above by eris23. Wanted to add that it works on a second attempt. Meaning, the first time after boot that I select System > Administration > Users and Groups, it fails with the aforementioned error. However, repeating the sequence leads to the expected result of opening the group management app.

---

### Post by tekstr1der on 2009-07-31
This is still an ongoing issue.

I filed: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/407366](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/407366)

---

### Post by tekstr1der on 2009-08-11
If anyone else is still seeing this issue please select "this bug affects me too" in the bug report or add a comment if you have more information. I still get this with my primary account the very first time I attempt to launch users-admin following login.

---

### Post by uBeer on 2009-08-12
Weird: cat /etc/groups gives me a lot of groups, but when I try to manage the groups from the Users and Groups tool I only see 2 groups: root and beer (as in account name, not the lovely drink).

Anyone same experience?

---

### Post by tekstr1der on 2009-08-24
uBeer - yes that is by design so as not to expose users to possibly confusing system user accounts. I don't like that either. Are you seeing the "The configuration could not be loaded." issue noted above?

---

