---
title: "Unable to Login normal users"
date: 2006-01-02
forum: General Help
---

### Post by mosestruong on 2006-01-02
I've done something stupid today - I pressed Ctrl-C during a "sudo checkinstall", and now, when I try to login as a normal user, I get the error "Unable to cd to "/home/user""
I can log in as root with no problem, but when I try su to a normal user, I get the error "No shell".

The home user directory exists and has the right permissions.

I've googled and check other mailinglist, but none seem to have a solution apart from reinstalling linux. Could anyone help me out? Thanks.

---

### Post by mosestruong on 2006-01-02
Found the answer to my problem at [http://groups.google.com.au/group/muc.lists.debian.user/browse_thread/thread/44140ca38ef07da1/6a5dcb26f39fd8f0?lnk=st&q=%22unable+to+cd+to%22&rnum=1&hl=en#6a5dcb26f39fd8f0](http://groups.google.com.au/group/muc.lists.debian.user/browse_thread/thread/44140ca38ef07da1/6a5dcb26f39fd8f0?lnk=st&q=%22unable+to+cd+to%22&rnum=1&hl=en#6a5dcb26f39fd8f0)

the permission for the root directory '/' for some reason was set to drwx------ 

After doing a "chmod 755 /" i am now able to login again. Hope this will help others who might have the same problem.

---

