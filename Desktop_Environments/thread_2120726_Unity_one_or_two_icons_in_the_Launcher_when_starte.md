---
title: "Unity: one or two icons in the Launcher when started?"
date: 2013-02-27
forum: Desktop Environments
---

### Post by josm on 2013-02-27
Why is it that when I start Thunderbird from the Launcer, the started windows are indicated at the existing icon in the launcher but when I start Firefox, another icon is created and the open windows are indicated there?

---

### Post by unheeding on 2013-02-27
That would be because of your following the advice you asked for in another thread.  When you click on your "Launch Firefox w/profile" icon, it launches it with that profile, but then identifies the window as Firefox - so it shows up under the "Firefox" icon, rather than "Firefox with profile"

[s]It doesn't seem possible to run[/s] You have to run Firefox with the --no-remote option to run two instances with different profiles.  

See your other thread for instructions on how to fix it.

---

### Post by josm on 2013-03-02
This seems to be cuased by some bug in my case since for Firefox, the behavior is different for two different users on the same machine: for one user, a new icon is created when Firefox is started, for the other user, no new icon is created and the started window is indicated in the existing starter icon.
For the affected user, the directory .local/share/applications is empty, so another desktop file in there can be ruled out as the cause for the problem.

I have found a workaround, that fixes  the behavior also for the affected user: edit /usr/share/applications/firefox.desktop and below the line "Exec" insert the following line: "StartupWMClass=Firefox"
This should really be the default, but it seems for the affected user, this information must have been changed or a different value cached somewhere.

---

