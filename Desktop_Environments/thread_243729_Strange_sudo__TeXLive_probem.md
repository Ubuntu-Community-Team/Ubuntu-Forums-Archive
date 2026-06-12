---
title: "Strange sudo / TeXLive probem"
date: 2006-08-25
forum: Desktop Environments
---

### Post by shaviro on 2006-08-25
I have TeXLive installed on my Dapper system. The binaries are in /usr/local/texlive/2005/bin/i386-linux, and this directory is in my $PATH. When I run the texhash command, all works well. But when I try to run:
sudo texhash,
I get the message:
sudo: texhash: command not found

Why can't sudo find the command, when it is in my path, and the regular command line does find it?

This is perplexing; thanks for any help.

Steve Shaviro

---

### Post by chandra on 2006-09-02
It all depends on how you got
/usr/local/texlive/2005/bin/i386-linux 
to be in $PATH.

If it was through a line in your personal .bashrc, than you need to include a similar line in the .bashrc file of /root.

If it was through a change on the system-wide .bash* file I am sorry but I cannot offer any suggestion.

HTH.

---

### Post by glennric on 2006-09-02
I have the same problem.  I added texlive to the path by editing the file /etc/bash.bashrc.

---

