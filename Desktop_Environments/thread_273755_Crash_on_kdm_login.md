---
title: "Crash on kdm login"
date: 2006-10-08
forum: Desktop Environments
---

### Post by khedron on 2006-10-08
Hi everyone,
I recently installed kubuntu-desktop over an ubuntu installation. All went well, except for this one thing: kdm doesn't want to log in.

I use ```
sudo dpkg-reconfigure kdm
``` to set kdm as default and reboot. The login screen comes up, but when I attempt to log in with my username+passwd, X restarts and the login screen comes up again.

This is not a huge problem as I can use gdm to login to my kde session, but it would be nice to get kde totally working on my box.

Sorry if this thread is a dupe of another; I am not very good at manipulating searches.

---

### Post by khedron on 2006-10-16
Anyone? I could even do with what logs might give info on the error, or what /etc files are used to initiate login. I have checked all the rc files I know, but they all seem fine to me.

---

### Post by glantucan on 2007-12-26
Hi 
I have the same problem here. I have no clue about what to do, except to go back to gdm :(

Thanks in advance

---

### Post by khedron on 2007-12-26
Unfortunately the time I had this problem I installed a new Kubuntu version fresh over the misbehaving version - the new version came out soon after I posted this. So I never found out what was causing the problem.

However, I can help you with debugging.
Here are some log files to check after you have made X crash: 
```
/var/log/Xorg.0.log
/var/log/kdm.log
```If you have restarted X in the meantime (e.g. by logging in on a virtual console (**Ctrl-Alt-F1**) and then typing **startx**), then you may have to check **/var/log/Xorg.1.log** or **/var/log/Xorg.0.log.old** instead of Xorg.0.log. This is because X creates a new logfile each time it starts up, moving the other logs one "position" down.

Try to look for an error message in one of the **Xorg.log**'s or **kdm.log** ; then post the error message along with the surrounding lines if they are related.

Hope this helps. Please tell me if I am talking too far below or above your level.

---

### Post by glantucan on 2007-12-27
Thanks a lot, khedron, I'm not a linux hacker but I can follow your explanations.
Anyhow, I found the solution yesterday evening following the instructions given here 
[http://ubuntuforums.org/showthread.php?t=81431](http://ubuntuforums.org/showthread.php?t=81431)

Didn't understand what sabayon had to do with kdm and kde but it worked fine.

Now, I'm more worried about my windows being locked when I run compiz-fusion, but I'm following other threads on this subject.

Thanks again

---

