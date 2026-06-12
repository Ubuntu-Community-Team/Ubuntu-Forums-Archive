---
title: "[SOLVED] Can not display share contents in Nautilus"
date: 2008-05-01
forum: Desktop Environments
---

### Post by markofealing on 2008-05-01
Upgraded from 7.10 to 8.04, went through okay. I can see computers on my workgroup network, when I browse a Win Xp PC I can open it up bot no files are displayed in the share.

If I go to Terminal and enter smbclient -L computername
all my shares are correctly displayed and using

smbclient \\\\computername\\sharename -U username

correctly allows me to display all the files in the share.

So, I've established Samba is working correctly, it appears that Nautilus is not and this is a Ubuntu bug :(

Anyone with a similar experience?

---

### Post by shanepardue on 2008-05-01
I'm having the same experience. I can see the machines, but not their shares in Nautilus. I don't even get an authentication dialog.

---

### Post by eallenjacobs on 2008-05-01
Happening here too, though a slight difference. On my laptop I did a fresh install, and am having this problem. On my desktop I performed an upgrade while retaining whatever settings I had, and am NOT having this issue.

---

### Post by Kabir on 2008-05-02
After upgrade from 7.10 to 8.04 - the same problem. No authentication box, no content.

---

### Post by mike2357 on 2008-05-02
Same problem.  The following worked for me:

1.  Select Places -> Connect to Server . . .
2.  Service Type:  Windows Share
3.  Enter Server and Share names

---

### Post by markofealing on 2008-05-02
Thanks, that's a good work-around. 

It doesn't resolve the Nautilus browsing problem with shares, but for the time being I can live with that until someone fixs the bug.
:)

---

### Post by 3rods on 2009-02-15
How is this solved again? I have the same issue. Is there a solution I'm not seeing?

---

### Post by shanepardue on 2009-02-15
> **3rods said:**
> How is this solved again? I have the same issue. Is there a solution I'm not seeing?
Two posts up shows a workaround. This nautilus bug is fixed in Jaunty.

---

