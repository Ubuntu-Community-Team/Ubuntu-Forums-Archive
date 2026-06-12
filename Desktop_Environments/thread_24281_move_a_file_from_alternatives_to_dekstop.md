---
title: "move a file from alternatives to dekstop"
date: 2005-04-06
forum: Desktop Environments
---

### Post by nickx on 2005-04-06
Hello Guys, 

Got a strange problem, probably a very easy to you guys. This is what I have.

I have in etc/alternatives a file called vncviewer. I created a link (shortcut) "link to vncviewer" .. ok I have rights on that dir cause I can create files in it.

So far so good...

No I try to copy the file from representative to my desktop. When I try to copy I'm getting the following error "etc/alternative/ to vncviewer" cannot be moved cause you don't have permissions to change it or its parent folder?

So I tried a few things but no go. What am I doing wrong and why do I get that message? Thnx for your information guys!


----------------------------> 
Strange!!! I copyed and past the link on my dekstop it suddenly worked??? but my other question is. It's on my dekstop now. How do I get that in my start menu and not in my taskbar? thnx again

---

### Post by Jad on 2005-04-08
means you don't have permissions to copy files to that folder, try to use terminal
sudo cp filename /home/user/path/

---

