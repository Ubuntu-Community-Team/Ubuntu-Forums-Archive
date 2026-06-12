---
title: "failed to execute child process &quot;-x&quot; (no such file or directory)"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by tygern on 2007-08-31
I just installed, and then removed Compiz Fusion (according to [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/")) Now, whenever I try to access a launcher that is an "Application in Terminal" I get this message:

failed to execute child process "-x" (no such file or directory)

I can still open the terminal and execute commands, but the launchers will not work.

---

### Post by DonaldPK on 2008-03-08
a bit late to the rescue. i was searching for a fix myself as well

for the launcher, select Application instead of Application-in-terminal, then change the command to 

gnome-terminal -e "insert your command here"

without the quotes

---

