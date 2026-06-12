---
title: "Visual Effects settings not saving."
date: 2009-02-26
forum: Desktop Environments
---

### Post by theonemule on 2009-02-26
Okay...in the Appearance settings, I set my Visual Effects to 'Extra', and the settings work fine.

Every time I restart my computer, the settings are back to 'None' and I have to manually reset Visual Effects back to 'Extra'

Any reason why this happens?

Thanks

---

### Post by snman3131 on 2009-03-10
I'm having the same problem, any luck?

---

### Post by Committed on 2009-03-10
Have you installed compiz?  Once I installed it and started using compiz settings manager the appearance/visual effects meant nothing and would not stay as selected.  If your compiz effects are working, I wouldn't worry about it.

---

### Post by oneafrikan on 2009-05-20
Nope, same for me with both compiz settings managers installed...
although the simple settings manager seems to crash after starting up...

any ideas?

---

### Post by _0R10N on 2010-04-30
Same problem here!! I'm also having this problem with Cairo Dock. If I add a launcher, when I reboot it's not there...:confused:

---

### Post by CaptainPasty on 2010-05-01
Same problem. Every time I log in I need to change the settings again.

---

### Post by _0R10N on 2010-05-01
> **CaptainPasty said:**
> Same problem. Every time I log in I need to change the settings again.

I found this workaround in other thread here, add ```
/usr/bin/compiz --replace
``` as startup application. That will do the trick.

---

### Post by auh2o on 2010-05-01
I have the same problem, after upgrading to 10.04. After every restart, I need to:

[LIST]
[*]Turn ON visual effects
[*]Re-import my Compiz configuration profile into the Compiz Settings Manager *(this might be because when I turn on visual effects, in my case the "Extra" option, the default Extra settings will be applied, and my settings are substantially different.)*
[*]Reload Compiz via the Fusion icon to get the window borders to reappear
[/LIST]
> **_0R10N said:**
> I found this workaround in other thread here, add  ```
/usr/bin/compiz --replace
``` as startup application. That will  do the trick.

That works, for now. But it is as you say a workaround, not a solution. ;-)

---

### Post by _0R10N on 2010-05-01
> **auh2o said:**
> I have the same problem, after upgrading to 10.04. After every restart, I need to:

[LIST]
[*]Turn ON visual effects
[*]Re-import my Compiz configuration profile into the Compiz Settings Manager *(this might be because when I turn on visual effects, in my case the "Extra" option, the default Extra settings will be applied, and my settings are substantially different.)*
[*]Reload Compiz via the Fusion icon to get the window borders to reappear
[/LIST]


Did you tried what I suggested in the previous comment?

---

### Post by _0R10N on 2010-05-01
I subscribed to the bug report relating this problem, and I've just received an email notification, suggesting the following workarounds:

a. Having selected effects as above, select "Remember running applications" from Startup Applications
b. Invoke /usr/bin/compiz --replace as a startup application
c. ln -s /usr/bin/compiz /usr/bin/compiz.real
d. Invoke /usr/bin/metacity from command line or as a startup application

I hope this help.

---

### Post by dchenbecker on 2010-05-06
Just adding "/usr/bin/compiz --replace" as a startup app seems to get things going just fine for me.

---

### Post by _0R10N on 2010-05-06
I updated the kernel and other packages, last night. I'll remove the /usr/bin/compiz --replace of my startup applications list and see if it still working properly.

I'll let you know.

---

### Post by nutellajunkie on 2010-10-09
> **_0R10N said:**
> I updated the kernel and other packages, last night. I'll remove the /usr/bin/compiz --replace of my startup applications list and see if it still working properly.

I'll let you know.

did it blow up?

---

