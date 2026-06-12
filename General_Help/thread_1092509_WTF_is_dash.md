---
title: "WTF is dash?"
date: 2009-03-10
forum: General Help
---

### Post by semitone36 on 2009-03-10
Update manager is recommending that I install the DASH shell... why?

Why would I want to replace a shell that I am very familiar with, with a different shell?  Does dash recognise the same commands as bash?  Is bash suddenly obsolete?

Im afraid to hit the update button, anybody care to explain this new shell recommendation to me?

---

### Post by pennacook on 2009-03-10
An article from ubuntu:
[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

Basically (from the article)
The major reason to switch the default shell was efficiency. bash is an excellent full-featured shell appropriate for interactive use; indeed, it is still the default login shell. However, it is rather large and slow to start up and operate by comparison with dash. A large number of shell instances are started as part of the Ubuntu boot process. Rather than change each of them individually to run explicitly under /bin/dash, a change which would require significant ongoing maintenance and which would be liable to regress if not paid close attention, the Ubuntu core development team felt that it was best simply to change the default shell. The boot speed improvements in Ubuntu 6.10 were often incorrectly attributed to Upstart, which is a fine platform for future development of the init system but in Ubuntu 6.10 was primarily running in System V compatibility mode with only small behavioural changes. These improvements were in fact largely due to the changed /bin/sh.

The Debian policy manual has long mandated that "shell scripts specifying '/bin/sh' as interpreter must only use POSIX features"; in fact, this requirement has been in place since well before the inception of the Ubuntu project. Furthermore, any shell scripts that expected to be portable to other Unix systems, such as the BSDs or Solaris, already honoured this requirement. Thus, we felt that the compatibility impact of this change would be minimal.

---

### Post by semitone36 on 2009-03-10
Huh.  well I guess that sets my mind at ease.  But if I start having problems and none of my bash commands work Im comming after you lol :)

---

### Post by cchester on 2009-03-10
I picked to do the update and now nothing will install because I keep getting that there was an error in the dash file?

I can't seem to fix this or get rid of the issue. It say it is an essential package when I try to remove it as well.

Any ideas?

Thanks.

---

### Post by Yellow Pasque on 2009-03-10
> Update manager is recommending that I install the DASH shell...
No, it's already installed, and Update Manager is recommending you update it.

> I picked to do the update and now nothing will install because I keep getting that there was an error in the dash file?
Can you copy/paste the exact error?

---

### Post by n4lbl on 2009-03-11
I chose to defer the update because the update manager says, in the change tab:  "Failed to download the list of changes.  Please check your Internet connection."  Even though I don't always understand the changes I always read them.  If there is no description I have to wonder if there is some mistake.

---

### Post by n4lbl on 2009-03-11
The update manager now says:

"Version 0.5.4-8ubuntu1.1: 

  * SECURITY UPDATE: current directory .profile file parsing (LP: #335421)
    - debian/diff/0045-dash-l-option.diff: updated patch to remove extra line
      so .profile doesn't get loaded twice.
    - CVE-2009-XXXX"

I ran the update and if I notice anything untoward next time I boot I will update this thread.  Latest boot will be tomorrow A.M.

---

