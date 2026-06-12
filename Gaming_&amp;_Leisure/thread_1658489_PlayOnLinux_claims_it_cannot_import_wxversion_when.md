---
title: "PlayOnLinux claims it cannot import wxversion when it is installed"
date: 2011-01-02
forum: Gaming &amp; Leisure
---

### Post by Durandal512 on 2011-01-02
I'm trying to get PlayOnLinux up and running on my computer.  I have previously had it running with no problems at all, but now it claims it cannot import wxversion when I know for a fact that I have it installed.  I have searched Google and UbuntuForums using various different search terms, but nothing I have found has been of any use to me.  I have tried completely removing and reinstalling all of the python-wx[etc.] packages and the playonlinux package in Synaptic.  No matter what I do, though, I still get the following error when I try to run PlayOnLinux in a terminal (nothing at all happens if I use a shortcut):

Traceback (most recent call last):
  File "/usr/share/playonlinux/python/mainwindow.py", line 23, in <module>
    import wxversion
ImportError: No module named wxversion

Any help is greatly appreciated.

---

### Post by Durandal512 on 2011-01-04
I got it working.  Turns out it was a problem that arose because I had installed Python 2.7.1 from source code on top of 2.6.6 having been installed through Synaptic Package Manager.  Although my fix was far from optimal and I'm likely to catch crap for it later, PlayOnLinux runs fine.  Let this be a lesson learned to never install from source when you can add the repository to your software sources.

Solved.  If anyone is interested in my (albeit clumsy) fix, I'd be happy to share.

---

### Post by peterfernandes238 on 2011-01-06
I still get the following error when I try to run PlayOnLinux in a terminal.
----------
Peter Fernandes

---

### Post by Durandal512 on 2011-01-06
Have you installed Python from source code while also having Python installed in Synaptic?  If that's what you've done, then I might be able to help you.  Otherwise, it would probably be a different problem producing the same error.  My fix involved replacing the binary in /usr/local/bin/ that was created from the source-code-installed Python with a copy of the python2.6 binary and putting a copy of the python2.6-config file in the same directory.

As I said, probably not the best method, but it works.  For now, at least.

---

### Post by lserranojaral on 2011-01-22
> **Durandal512 said:**
> Have you installed Python from source code while also having Python installed in Synaptic?  If that's what you've done, then I might be able to help you.  Otherwise, it would probably be a different problem producing the same error.  My fix involved replacing the binary in /usr/local/bin/ that was created from the source-code-installed Python with a copy of the python2.6 binary and putting a copy of the python2.6-config file in the same directory.

As I said, probably not the best method, but it works.  For now, at least.

Hi,

I have the same problem. Unfortunately I new in ubuntu. Could you please show me how to perform your fix?

I installed python 2.7, since then, play on linux didn't work.

Regards,

---

### Post by Durandal512 on 2011-01-22
Before you try the following, make sure you have the package called "python" installed in Synaptic.  Otherwise, you probably won't have the python2.6 files I mention.

I'll explain this as best I can for a beginner, although if you aren't familiar with super-user privileges and using the file browser as root, you may want to look away (not too concerned with that, though; you did manage to install a program from source code, after all).

Follow these instructions and things should work out:

Open a terminal (Open Applications menu, Accessories, Terminal).  Run "sudo nautilus" (no quotes), giving your password when prompted.

Using the file browser that opens, navigate to /usr/local/bin/

Delete the file called "python" (again, no quotes)

Go to /usr/bin/

Right-click the file called "python" and click copy.  Paste it into /usr/local/bin/

Go back to /usr/bin/ and copy "python2.6" and paste it into /usr/local/bin/

Do the same with the file called "python2.6-config"

Hope this helps.  Good luck to anyone who tries this.

---

### Post by lserranojaral on 2011-01-24
> **Durandal512 said:**
> Before you try the following, make sure you have the package called "python" installed in Synaptic.  Otherwise, you probably won't have the python2.6 files I mention.

I'll explain this as best I can for a beginner, although if you aren't familiar with super-user privileges and using the file browser as root, you may want to look away (not too concerned with that, though; you did manage to install a program from source code, after all).

Follow these instructions and things should work out:

Open a terminal (Open Applications menu, Accessories, Terminal).  Run "sudo nautilus" (no quotes), giving your password when prompted.

Using the file browser that opens, navigate to /usr/local/bin/

Delete the file called "python" (again, no quotes)

Go to /usr/bin/

Right-click the file called "python" and click copy.  Paste it into /usr/local/bin/

Go back to /usr/bin/ and copy "python2.6" and paste it into /usr/local/bin/

Do the same with the file called "python2.6-config"

Hope this helps.  Good luck to anyone who tries this.

**It worked fine for me also. Thanks!!**

---

