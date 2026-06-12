---
title: "flexible workstations / roaming desktop"
date: 2008-07-31
forum: Desktop Environments
---

### Post by firfin on 2008-07-31
I am currently installing number of flexible working spots in my office. The goal is to have users to be able to login on a computer. Then they get their usual desktop environment. I'm thinking about:

- Shortcuts to applications the user has access too or uses often.
- Auto-mounting of favorite (password protected) samba shares.
- access to personal (e.g. firefox) settings.

Who had tips pointers on achieving this?
What would be the best way to do authenticate the users? How would I share the user 'profile' amongst the computers.

What terminology is used for these kind of issues? :confused:


Thanks in advance.

---

### Post by Fire_Chief on 2008-07-31
It may be a little different style of implementation than what you are considering but you may want to look at the Linux Terminal Server Project (LTSP).

Cheers!

---

### Post by allywilson on 2008-07-31
I looked into something similar previously for a company that used Macs and Windows workstations.

They wanted to have the same Desktop, My Docs, Bookmarks, etc. 

I can only really refer to the aspects I dealt with however.

The answer is symbolic links. Firefox keeps its bookmarks in a file called bookmarks.html (or similar), and as Windows used "%USERPROFILE%\Desktop" for the desktop and Macs used "~/Desktop" we were able to repoint it successfully, as an example (Profiles held on a mac server, but linkd.exe or junction.exe offers the same functionality on windows for symbolic links).

As long as your user profiles are stored in a central location I can't imagine that you'll have much difficulty in this - afterall pretty much everything is stored in "~/.whatever" let us know the results though ;-)

Cheers

---

### Post by firfin on 2008-08-01
Thanks for your answers.
The machines that are going to be used for this are not very thin. So using LTSP for this almost seems like something of a waste :-)

But how would I go about 'loading' the profile at login time? Or do you store the profile on the server? 
Wouldn't it be much easier on the server and increase the speed if you get the profile on boot and store it on the server on shutdown?

Is this possible at all?

---

### Post by firfin on 2008-08-06
I think I found the solution. ALthough I have yet to implement it. All setigns are stored in the /home directory . So I can just use NFS to mount the home dir that is stored on the server.

Just have to figure out how to do authentification now. And the mounting /home part :-)


Any tips?

---

