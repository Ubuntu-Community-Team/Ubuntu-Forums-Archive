---
title: "Removing all files from the current session"
date: 2010-07-14
forum: Desktop Environments
---

### Post by emanuel.feruzi on 2010-07-14
Hi,

I have just manage to set up a number of computers using NComputing thin clients. I have set up 5 user accounts.

Problem

People will be using these account randomly. So what I want is to set up everything as it should be and that to be the default setting. If users download files or make changes to the files these should be for the session. On startup/shutdown all the files and changes should be deleted this way the next user can find the machine clean. And also there is limited maintenance to be done.


If there a tool or way to go about this issue.

I will appreciate some help and ideas.

---

### Post by MooPi on 2010-07-14
I think the first step should be setting privileges to the user to only access to certain /home/folders. The next step is a custom shutdown script to delete the content from the folders that user have access to. Can't you password individual accounts so that users only access their individual accounts without having to go through this process to begin with?

---

