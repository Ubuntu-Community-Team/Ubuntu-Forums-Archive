---
title: "Places menu won't launch Nautilus"
date: 2008-02-14
forum: Desktop Environments
---

### Post by Arathon on 2008-02-14
As bizarre as this may sound, most of the links on my Places menu simply don't work.  Nothing in the top section (Home, Desktop, Documents, Music, Pictures, Videos) works at all - clicking on any one of them closes the menu as expected, but nothing happens.  Nautilus doesn't start at all, and even if it's open, it doesn't switch to that folder or anything.  
The second section partially works; Computer and CD/DVD Burner both open Nautilus correctly.  But neither of my hard drive partitions (which are listed as Files and Vista) do anything either.  

As what may or may not be a related issue, I can't seem to create any Network shortcuts using the Connect to Server option on the Places menu either.  The dialog comes up, and I can fill in all the information, but when I've clicked Connect, the dialog just disappears and nothing happens.  I can ssh into servers with the terminal just fine.




Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 02:46:46 UTC 2008

---

### Post by Arathon on 2008-02-18
No one has any ideas for me?  Also, the About GNOME and Help links on the System menu are just gone.  How can I get those back?

---

### Post by Arathon on 2008-02-19
By simply reinstalling Nautilus with the package manager, I managed to get most of the Places menu to work.  However, using the menu opens up Nautilus as the root user, which is a little scary.  Also, my stored ssh Network Places just open up Nautilus in the /root directory.  

It'd be really nice if someone could shed some light on these issues......

---

### Post by banjopikker on 2008-02-19
I have the same problem except everything works except my places menu and add remove programs... so far!  I need help.

---

### Post by banjopikker on 2008-02-21
> **banjopikker said:**
> I have the same problem except everything works except my places menu and add remove programs... so far!  I need help.

Problem solved. I re-installed xubuntu desktop with synaptic package manager.

---

### Post by Arathon on 2008-02-21
That didn't help.  =P  I reinstalled ubuntu-desktop and it screwed up my pidgin installation.  My Places menu worked once; it brought up the folders as root.  Now it doesn't work at all again, and I'm gonna have to remember what I did to get the correct version of libpurple installed for Pidgin 2.3.1.

---

### Post by Arathon on 2008-02-21
Pidgin is OK again now.  sudo apt-get purge libpurple fixed the pidgin problem.  

Still, Nautilus sometimes doesn't come up at all, and sometimes it opens things in the root directory.  Neither of which is OK.  Why hasn't anyone else had this problem?

---

### Post by Arathon on 2008-03-04
gedit also sometimes fails to be opened (when I open text files from within Nautilus, there will often just be a long delay and then nothing happens); I can open the files if I open the files "with" Emacs (GTK).  I am pretty sure this is related somehow, because it's been happening as long as the Places menu issue. 

Does no one have any ideas about this?  I'm running Ubuntu on two other machines and they aren't giving me any problems like this.....   :(

---

