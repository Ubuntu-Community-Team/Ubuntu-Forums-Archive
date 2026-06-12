---
title: "stellaire upgrade"
date: 2007-11-12
forum: Education &amp; Science
---

### Post by conradandrose on 2007-11-12
i successfully downloaded the planetarium program stellarium and then downloaded an additional and greatly expanded list of stars.

i have the file on my desktop but cannot move it to the "stars/default" folder of the program as it resides in root.  i tried sudo but i can't change the permissions of the folder. i also searched for a local user folder that the program manual says should exist but doesn't.  i'm lost and need help.

i'm running ubuntu 7.10 on a pentium 4 machine.

---

### Post by xeth_delta on 2007-11-13
Hi there, I am also use stellarium from time to time. The first time the program is run it should create a .stellarium directory in your home directory.
You should be aware that files and directories starting with a dot are considered to be hidden. Many graphical file managers might hide them by default and hence you won't be able to find them. You could either enable an option to showing those hidden files or just use a console / terminal.

Where did you get the extended list of stars from? Did you use apt-get / aptitude / synaptic / adpet to install stellarium?

I looked up for any files that could be called "stars/default" on my computer but did not locate it. Where exactly should it be located?

I am not sure what you mean by root, is it the "/root" or "/" directory?
/root is the home directory dedicated to the root superuser and files of regular users should not be placed in there.

Hope I could be of any help,
Xeth

---

