---
title: "Window Title Bar Requires metacity --replace to display after logon"
date: 2010-05-27
forum: Desktop Environments
---

### Post by iposner on 2010-05-27
Running 10.04 64-bit. After logging on, the title bars around all the windows are missing. Adding "metacity --replace" as a startup command resolves the problem, but something's obviously wrong.

Doesn't occur on my other computer, so probably hardware related.

Please see attached checkbox-generated submission.xml.gz for hardware report.

---

### Post by iposner on 2010-05-27
Drilling further into this, the other logins on my machine work fine, only mine isn't working the way it should. The other logins have not had their appearance altered from the default. My login has had the appearance changed to a custom style, but even if I revert the setting to the default Ambiance and log off - log on again, it still doesn't show the window border without running metacity --replace.

---

### Post by iposner on 2010-05-28
Making some progress - looks for sure like my login is the only one where the window border disappears. If I only knew the order in which config files are accessed following logon, I'd be able to check my config files against those of the other users.

Any ideas out there?

---

### Post by reyquito on 2010-05-29
Hi.

I am experiencing the same issue, in at least two logins with custom style. Still haven't found a solution. If I do, I'll be back to tell you about it.

Regards,
Q

---

### Post by iposner on 2010-05-29
Making some progress. Installed the compiz configuration manager and looked at the Window Decorator settings. Set the window manager to /usr/bin/compiz-decorator as this is the setting set on the other profiles.

Logged off-and-on. Problem still exists. Then attempted to change the Appearance from None to Normal window decoration using the Appearance app. All of a sudden the window border comes back. However after searching for an appropriate driver, I get the message "Desktop effects could not be enabled".

If I can work out why the desktop effects can't be enabled, maybe I can sort this out...

---

### Post by iposner on 2010-05-29
FIXED -- Looking through gconf-editor, I noticed that some of my settings for metacity had the unusual string "sAVED by zERO" in them. One thing for certain, is I never put that in. So I set those strings to that listed in profiles working properly.

I then went into the Appearance app again. This time I looked at the Fonts tab. Again, there were fonts listed as sAVED by zERO. I changed these to Sans.

I then attempted to change the visual effects from None to Normal - it worked!

Could it be that some malicious code has entered the Ubuntu repositories?

---

### Post by Rebelli0us on 2010-05-30
Title bars missing here too after upgrade to Lurid Lucy 10.04. Setting "Appearance" > Visual Effects to Normal restores title bars, but they're gone again on reboot.

---

### Post by f.zacka on 2010-06-12
In startup applications, I found Devils Pie application set to run with the parameters 

(Maximize)
(undecorate)
(focus)

After removing this from startup then doing a restart, it has fixed the problem.
Hope it helps ](*,)

---

