---
title: "every student with ubuntu netbook - permissions"
date: 2011-06-09
forum: Desktop Environments
---

### Post by defunkt on 2011-06-09
hey all, 

i have a question but first i want to lay out a scenario so you understand where I'm coming from.  

i work in a high school and we have been looking to implement a one to one program where every student will receive a net-book.  in order to cut cost for the program we are looking at using ubuntu.  so far we have run a pilot in a few classrooms and the teachers and students really seem to like it.  but our big concern is more with web filtering at home...

my stance towards permissions is to give students full (root) access to the net-book as when they graduate the net-book will become theirs.  this poses problems as students can alter/remove software on the machine; see where I'm going with this?  my argument is that if they have root access they can remove any filtering software, and if we don't give them root access, management of the net-books could become a nightmare (installing any software or updates).  on the other side, when the students graduate, they need to be able to use the net-book normally with whatever restrictions we have put in place, i don't think you would expect the seniors to hand in their net-books when they graduate so that they could be re-imaged to give them full access.  

i would rather give them full access to the net-book than restrict them, and i don't want this to turn into a "whether they should or shouldn't be filtered" conversation.  i may not have a choice depending on what our board decides.  so at this point I'm making an effort to explore my options.

the software were looking to implement is a kernel patch, which most students wouldn't be able to find, but there are always a few talented students who will find it.  

**so... is there a way that i can give users the ability to install and update software without having root access??? or maybe mroe importantly prevent them from having the ability to change/update the kernel.**

i know the answer is most likely no, but I'm trying to get the best of both worlds.


I'm open to any suggestions, but I'm not super optimistic...

thanks for any comments!

---

### Post by defunkt on 2011-06-09
i have found another link that "may" work... 

[http://askubuntu.com/questions/3/how-can-i-set-the-software-center-to-install-software-for-non-root-users](http://askubuntu.com/questions/3/how-can-i-set-the-software-center-to-install-software-for-non-root-users)

ill look into this a bit further.  

again, any further comments would be appreciated.  i know this whole idea is somewhat backwards as when things are installed they almost always need root access.  but I'm a single tech that would be looking at managing 1000+ computers.

---

### Post by sanderd17 on 2011-06-09
Even without root access, the users are able to change the kernel by simply booting a live USB. This is even more simple than just changing the kernel from inside the OS.

As a simple solution to exclude kernel updates from the default updates, you could use Mint (or only the Mint update manager). This update manager excludes the kernel updates (because they could break something) and also doesn't notify for OS upgrades. If a user is smart enough to get past this barrier, he will also be able to install an OS with a live USB.

---

### Post by defunkt on 2011-06-09
setting up a password in the bios and telling it to only boot the the disk is easy, although that doesn't prevent them from removing the disk...  

actually this is part of my argument of why we shouldn't be filtering them at home anyway...  there is NO way to prevent them from modifying the disk... assuming they know how.  

well using the mint manager may prevent them from upgrading the kernel, but they would still have to be root to install upgrades or applications if i read that properly.  i've tinkered with the link i posted above but don't have it working quite how i had hoped (yet).  i am getting a "requires installation of untrusted package" error...  google here i come.

---

### Post by sanderd17 on 2011-06-09
> **defunkt said:**
> setting up a password in the bios and telling it to only boot the the disk is easy, although that doesn't prevent them from removing the disk...  

 And a bios password can be bypassed when you have access to the motherboard (at least in most cases). This is a bit difficult on a netbook, but it is possible.

>   

well using the mint manager may prevent them from upgrading the kernel, but they would still have to be root to install upgrades or applications if i read that properly.  

They will need to be root to install things, and they can install new kernels if they want to, but Mint hides the upgrades by default and if you find them, it gives a clear warning that "it could break your computer and you're not advised to upgrade those packages". So it would stop any average user but it's not meant to stop the occasional hacker.

But I see no reason to filter them at home, they are not protected from the real world on the street too. Giving them an option to be protected seems the maximum you can do.

---

### Post by defunkt on 2011-06-09
well the idea behind it is that the net-books will be theirs as long as a contract has been fulfilled, but the school is worried about adult content being viewed on the net-books prior to the contract being completed.  the contract basically states that they must have all fees paid and have served 4 years (aka to pay back the cost of the net-book).  this is more of a CYOA that their looking at...  and honestly i don't know all the state regulation behind it.  

the more and more i look into this the more i think that management will become a nightmare if we do restrict permissions.

well thanks for your input, i was hoping for a magical fix-all but i know i cant always get everything i want!

---

### Post by defunkt on 2011-06-09
actually i was able to accomplish what i wanted with editing the group section of the sudoers file.

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%packageinstallers ALL = NOPASSWD: /usr/bin/software-center, /usr/bin/apt-get, /usr/bin/apt-cache


this allows members of the packageinstallers group the ability to run apt-cache, apt-get, and software-center without being prompted for a password.  all other sudo commands are denied.  

honestly a bit more restrictive than i had hoped but until i find a better solution that may have to do.

---

