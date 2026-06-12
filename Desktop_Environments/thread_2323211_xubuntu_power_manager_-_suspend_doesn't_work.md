---
title: "xubuntu power manager - suspend doesn't work"
date: 2016-05-03
forum: Desktop Environments
---

### Post by pastim on 2016-05-03
I have just installed xubuntu 16.04 on my laptop as a complete fresh install (including home).  All's well except the power manager.

I can sudo pm-suspend and that works.
I can set the action on shutting the lid to suspend, and that works.
When I set the action to suspend after 30 minutes inactivity I get a bubble saying "[COLOR=#000000][FONT=Tahoma]GDBus.Error:org.freedesktop.login1.SleepVerbNotSupported: Sleep verb not supported."[/FONT][/COLOR].

I am not trying to Hibernate, so swap issues should not apply, and anyway my swap partition is large enough (6GB on a 4GB machine) and active (and yes, I have double-checked).

On previous xubuntu versions (14.04 & 10,  15.04 & 10) it did work.

I'm no linux expert, but a user for several years, and usually make things work in the end.....

So what can this be?  Where do I look?  I'm guessing that somewhere there is a config file with the wrong verb in it (probably hibernate), or else there's an authorisation issue.

I can't find any log telling me anything useful.  Is there one I should be investigating?

---

### Post by ajgreeny on 2016-05-03
Flipping smilies!!

I edited your post and disabled them, which you can do if you use the **Advanced reply** and scroll down below the text entry box.

A colon immediately followed by some letters or bracket is read as a smily by default

---

### Post by pastim on 2016-05-03
Thanks.  How would I have written the original post to avoid it (since I was not replying to anything)?:D

---

### Post by ajgreeny on 2016-05-04
Scroll down below the text entry box and you will see an option to "Disable smilies".
A new thread alwsys gives you the Advanced text box, just like I mentioned above.

---

### Post by egeezer on 2016-05-04
You might check in Synaptic whether you have uswsusp installed (you probably do, but it wouldn't hurt to check).

---

### Post by pastim on 2016-05-04
> **egeezer said:**
> You might check in Synaptic whether you have uswsusp installed (you probably do, but it wouldn't hurt to check).
That isn't installed.  

However, before I read your suggestion I did find a answer that fixed the problem.  Having seen that Suspend did work for all actions I tried except inactivity, and chasing round umpteen different configuration files, dead ends (complaints from xfce4-power-manager in debug mode about not devices having backlight adjustment) and so on I concluded something must be missing from the configuration.

I noted that in xubuntu 16.04, the only allowed option for what to do after x minutes inactivity was 'suspend', I looked in the Settings Manager at xfce4-power-manager options.  Most actions are included, but there was nothing about what to do after the inactivity time out.

I eventually found mention of '[FONT=Liberation Sans]inactivity-sleep-mode-on-battery' on the web.  This was not present in the 'settings editor' dialog (matching the file in .[/FONT][FONT=Liberation Sans]config/xfce4/xfconf/xfce-perchannel-xml/xfce4-power-manager.xml). I added it, and set it to 1 (the same action as when closing the lid, which I have set as 'suspend' so I assumed '1' meant suspend).

[/FONT]It works.  Solved.

---

### Post by pastim on 2016-05-05
I have also found another entry missing from the xml file - "critical-power-level".  Without this, the system did not act on low battery at the specified %.  

I reported this to the xfce bugzilla (another person had report the inactivity suspend issue so I appended my solution).

Should I be raising a problem on the xubuntu bug system?

---

