---
title: "Simple Backup Config install creates problems...HELP!"
date: 2009-04-26
forum: General Help
---

### Post by shuukazedojo on 2009-04-26
Well, this morning I had the bright idea to upgrade to Jaunty, but before I did anything I wanted to backup my data. I installed the Simple Backup Config and Restore applications via the Synaptic Manager. I configured it to backup under the "standard" or "common" option (the top one of three with radio buttons in the config GUI). Then the fun started. 

I initiated the backup and stepped away from my computer only to return with everything acting funny. So. I logged out and tried to log back in. I received a message stating:

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator."

So, with login being futile, I restarted in recovery mode. I deleted the directory that the new application was saving to (/var/backup/) and restarted. 

Well, I figured my disk space may be running out so I would try the backup via ftp to my website. So, I go to login to my hosting company to get the ftp UN and PW. After I enter my login info to access the admin functions and click enter, nothing happens. I thought it might be the site, so I tried logging into gmail. Same thing! Then I tried logging in here. NOTHING! Except, on these forums, when I entered the password then hit login, the password would disappear. So, it seems like my passwords aren't holding or something. I don't have any of this setup to be entered automatically. It's all manual entry.

So, next I removed the backup utility via synaptic, hoping it would change the situation. But still, it's failing to login to gmail, hosting company, or ubuntu forums.

Any idea what this is all about and how to fix it? Any recommendations for a backup AFTER this is fixed? I have a 2nd HD that I use to dual boot XP. Also, if you need to know, I'm running Intrepid.

Thanks for the help!

EDIT: Well, I thought I'd try and start the upgrade through the Update Manager, but it turns out I now have a problem with the authorization file! Any ideas on this?

---

### Post by shuukazedojo on 2009-04-27
I decided to do some more research and found that the HD I have Ubuntu on was maxed out! A 40GB HD was showing 42GB used!!! LOL. I guess that's why things weren't working. I transferred a ton of stuff over to the HD I have Winbloze on and removed the load. That seems to have done the trick. Now I know AND I will be doing a backup on a regular basis.

---

