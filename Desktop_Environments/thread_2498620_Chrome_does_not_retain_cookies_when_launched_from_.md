---
title: "Chrome does not retain cookies when launched from different place"
date: 2024-06-21
forum: Desktop Environments
---

### Post by pnuke on 2024-06-21
Hi, 

when launching Chrome from the KDE task-manager (or is it the taskbar?), I can use it for days to come and restart as often as I like, all cookies (and therefore sessions/logins) will persist. 

But as soon as the initial launch of Chrome after a reboot is from within Thunderbird for example (clicking on a link in an email), all passwords are missing and all cookies are deleted. I have to close Chrome and start it over the task-bar again to get all saved passwords back, but the cookies are gone still. 


I suspect it has something to do with the keychain and the inability of Chrome to work with that? But why is there a difference in the first place depending how Chrome is launched? What is happening differently when I click on a link in Thunderbird?

---

### Post by pnuke on 2024-06-27
nobody has a clue or hint where I could start digging? :(

---

### Post by The Cog on 2024-06-27
I have no idea what your problem might be, but I thin I would start by running "ps -ef | grep chromium" and look at the command arguments that were used to launch it in each case, and look for any differences.

---

### Post by Andreyshel on 2024-06-27
Would be nice to see your files and attachments section in  Thunderbird settings. Start Thunderbird - go Edit - settings - General  and scroll down.

---

### Post by him610 on 2024-06-27
@pnuke
It is in Chrome; you probably do not have Settings > You and Google > Syncing to pnuke@gmail.com set to Turn ON

---

### Post by pnuke on 2024-06-27
> **The Cog said:**
> I have no idea what your problem might be, but I thin I would start by running "ps -ef | grep chromium" and look at the command arguments that were used to launch it in each case, and look for any differences.

is chrome I need to search for chrome instead of chromium. There is only one noticable difference, when starting from Thunderbird, there is the URL passed as unnamed parameter. If started from the task-bar, there is no parameter for the first chrome-process at all. After that there are quite a lot of sub-processes of chrome with lots of arguments but they are almost identical (except for some crash-handler IDs) and they are started from the main process as it looks like

Is there a way to see in which user-environment or so the process was started? 


> **Andreyshel said:**
> Would be nice to see your files and attachments section in Thunderbird settings. Start Thunderbird - go Edit - settings - General and scroll down.


there is just  PDF preview in Thunderbird and always ask before downloading.






> **him610 said:**
> @pnuke
It is in Chrome; you probably do not have Settings > You and Google > Syncing to [email]pnuke@gmail.com[/email] set to Turn ON
thats turned on of course and wouldnt affect the problem either because cookies are not synced.

---

