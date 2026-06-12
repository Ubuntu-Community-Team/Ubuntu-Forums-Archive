---
title: "Panels do not appear on Administrator account anymore"
date: 2007-05-27
forum: Desktop Environments
---

### Post by avai on 2007-05-27
A while ago, I had a problem that was caused from trying to install Compiz. Though, in trying to repair the problem by myself, which ended successfully, I caused another problem: the panels stopped appearing on the administrator account, though these still appear (thankfully) for the root account.

I modified the file 'en.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages' in the directory: var/lib/apt/lists/ clearing out anything with compiz in it. When I edited this file, I believed that it was altered as a result of trying to install compiz; later, I learned otherwise. To restore the file to its original form, I used the file name as a link, copied and pasted the results, which appeared to fix the panel problem for the admin account on the next reboot of my laptop. However, the following reboot, the panel problem reoccurred. When I replaced the file again, the problem is fixed until the following reboot again.

I need to find a way to make the repairs permanent.
I would appreciate any insight anyone can offer me.

---

