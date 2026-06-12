---
title: "Thunderbird dock launcher is not working"
date: 2021-05-05
forum: Desktop Environments
---

### Post by fredrik-ellborg on 2021-05-05
After upgrading to 21.04 the launcher of Thunderbird isn't working as expected:

- The indicators are showing more open windows than there are (see attachment, no running thunderbird).
- When this happens, the launcher doesn't work (nothing happens when left clicking it).
- When this happens, right-clicking the launcher opens the context menu, but it's not clickable and it's positioned wrongly.

This only happens with Thunderbird. Anyone else experiences something similar?

Best,
Fredrik

---

### Post by ActionParsnip on 2021-05-05
If you run the application from the terminal, do you get any useful output?

---

### Post by deadflowr on 2021-05-05
processes running and proceeses loaded are different things, most of the time thunderbird would be idle/sleep and the ps -r output would show nothing.
Perhaps try *killall thunderbird *to kill all the loaded thunderbird processes,
and see if opening one instance again does the same thing.

(Also check if thunderbird is running on a different workspace,
also double check that you display isn't setting it to run on a non-existent secondary display.
You can check that in Settings > Displays.
That has happened to users before, where apps weren't opening correctly and it was found that somehow the system was believing a non-existent monitor was attached)

---

### Post by fredrik-ellborg on 2021-05-07
Thanks for your replies. 

1. I'll get a "thunderbird: no process found" response from killall command. Also that doesn't explain the odd behavior of the context menu.
2. No interesting output from running thunderbird from the terminal. 
3. I just got a similar behavior from ImageMagick.

Best,
Fredrik

---

### Post by ajgreeny on 2021-05-07
Telling us ***No interesting output from running thunderbird from the terminal. *** does not help us very much, but assuming there was output of something, what was it?

Just to double check what is running, what output do you get from command ```
ps aux | grep thunderbird
```
You may see just one line which is the grep service itself  looking for thunderbird which you can remove with an addition to that command ```
ps aux | grep thunderbird | grep -v grep
```which hopefully will output nothing at all.

---

### Post by robert48 on 2021-06-24
> **deadflowr said:**
> processes running and proceeses loaded are different things, most of the time thunderbird would be idle/sleep and the ps -r output would show nothing.
Perhaps try *killall thunderbird *to kill all the loaded thunderbird processes,
and see if opening one instance again does the same thing.

(Also check if thunderbird is running on a different workspace,
also double check that you display isn't setting it to run on a non-existent secondary display.
You can check that in Settings > Displays.
That has happened to users before, where apps weren't opening correctly and it was found that somehow the system was believing a non-existent monitor was attached)

I get the same issue and confirm that ```
killall thunderbird
``` DOES NOT close it down when the issue is manifest. I have no idea why this is happening but it seems to be co-incident with running Remmina vnc OR receiving lots of scam emails wanting to gift me an iphone if I paid $1/£1 twards postage.....etc. By the way, if you are in the UK you can forward as >attachment scam emails to [EMAIL="report@phishing.gov.uk"]report@phishing.gov.uk[/EMAIL]. ClamAV has also failed and I can't check the emails for viruses. The 'can't close down thunderbird from the laucher icon' issue persists with me. I can close down thunderbird using right click>quit on the launcher panel icon if I have no other windows open when I launch and close it.

---

### Post by monkeybrain20122 on 2021-06-25
You are on wayland?

---

### Post by philhughes on 2021-06-28
Seeing the same thing. It is not related to Remmina or receiving emails. Found a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1932328](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1932328)

---

### Post by zircon_34 on 2021-07-10
I have the same thing going on with thunderbird, last time it even crashed my computer. Then I noticed that I was logged in using wayland. I will now try to stay on xorg to see if that is the culprit.  Did not have this problem before.

---

