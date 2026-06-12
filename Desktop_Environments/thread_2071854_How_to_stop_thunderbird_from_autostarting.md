---
title: "How to stop thunderbird from autostarting"
date: 2012-10-16
forum: Desktop Environments
---

### Post by grahams on 2012-10-16
Running xubuntu 12.04 and in the last few weeks thunderbird starts up when I login and I do not want this to happen.

When I look at Setting> Session and Startup Thunderbird is not set to start. I can confirm this via ls /etc/xdg/autostart/

I've also disabled the messaging plugin in Thunderbird but all to no avail. 

Any clues as to where to look next ?

Thanks

---

### Post by drmrgd on 2012-10-16
I don't use Xubuntu, but I think most DEs are similar.  Is there a function in the same location to either start a new session or remember a previously run session when you log in?  I know it exists in Kubuntu and Ubuntu, and this might be what's happening.  It may be loading a previously saved session where you had Thunderbird running.

---

### Post by nonamedotc on 2012-10-16
When you logout/shutdown next time, uncheck the option that says "Save Session" in the pop-up that appears. This will ensure that the session is not saved and none of the programs will auto-restart.

Alternatively, open the "Session and Startup" from the settings manager and uncheck the "Automatically save session on logout" option.

Hope this helps.

---

### Post by grahams on 2012-10-19
Thanks for replies

Save sessions is not enabled. I can also close TB before shutdown, but it always starts on 1st login.

---

### Post by Elfy on 2012-10-19
Try closing thunderbird and anything else you don't want starting.

Settings Manager - Session and Startup - Session tab

Clear saved sessions - Save Session 

I get odd things starting from time to time and that appears to deal with it here.

---

### Post by grahams on 2012-10-19
> **Elfy said:**
> Try closing thunderbird and anything else you don't want starting.

Settings Manager - Session and Startup - Session tab

Clear saved sessions - Save Session 

I get odd things starting from time to time and that appears to deal with it here.

Thanks Elfy

I had just tried this exact step and was about to mark this as solved. Thunderbird wasn't listed in the session, but clearing saved sessions did the trick.

---

### Post by Elfy on 2012-10-20
> **grahams said:**
> Thanks Elfy

I had just tried this exact step and was about to mark this as solved. Thunderbird wasn't listed in the session, but clearing saved sessions did the trick.

Never sure why things don't appear there either. But heyho - glad you're sorted now :)

---

