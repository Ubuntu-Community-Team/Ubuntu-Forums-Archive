---
title: "Xfce 4.8 Shutdown from menu just logs me out"
date: 2011-04-13
forum: Desktop Environments
---

### Post by BrokenKingpin on 2011-04-13
I have installed the Xubuntu Beta 1 and I am having an issue where if I select Log Out from the menu and then select Shutdown from the dialog box it just logs me out. If I select it from the panel it works fine, but I want to remove this from the panel and just use the menu. Does anyone else have this problem, or know how to fix it?

---

### Post by 3Miro on 2011-04-14
Do you see an error right before you logout. I have seen something like this and it had to do with PolicyKit and my not having proper permissions to reboot the system.

Try updating the system, there was PolicyKit update yesterday, maybe that will fix the issue.

---

### Post by BrokenKingpin on 2011-04-14
No, I do not see an error just before the log out (but I suppose there could be one that I just didn't pick up on). I think my system was up to date as of last night, but I will have to double check that.

---

### Post by 3Miro on 2011-04-14
Is this consistent behavior or did it just happen once. It may have been due to the update, the first time that you reboot after the update may be broken, but it may get back to normal afterwards.

---

### Post by BrokenKingpin on 2011-04-14
It happens every time, and the system is fully updated.

---

### Post by sldavid on 2011-04-15
Settings Manager > Session & Startup > General Tab > uncheck 'prompt on logout'

---

### Post by BrokenKingpin on 2011-04-16
The last round of updates fixed the issue. There was a known bug for this in Launchpad.

---

### Post by teachop on 2011-04-23
> **BrokenKingpin said:**
> The last round of updates fixed the issue. There was a known bug for this in Launchpad.
Still happens for me most of the time, not all.  I am fully updated...

---

### Post by aezren on 2011-04-28
I am having the same issue. I had it in the Natty Beta even though I read several placed that this was patched. I just did a fresh install of the final release 11.04 and it has the same problem. Any ideas?

---

### Post by BrokenKingpin on 2011-05-02
I now have the issue again. I did a fresh install on one of my machines and now it is just logging me out again. I think if you save your session on logout it works fine, but I do not want to do this.

I have changed this back to Unsolved... if anyone has any suggestions that would be great.

---

### Post by BrokenKingpin on 2011-05-03
Anyone?

---

### Post by Neo40 on 2011-05-06
I have the same problem. 
Someone has solved this problem?
Thanks.

---

### Post by edwardp on 2011-05-30
This bug has been around a while now.

---

### Post by s5GbJReJ on 2011-07-25
> **edwardp said:**
> This bug has been around a while now.

Yes... I just did a fresh install of Xubuntu 11.04 on my laptop and this bug is present! How sad :-(

---

