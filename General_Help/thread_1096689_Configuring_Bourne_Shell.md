---
title: "Configuring Bourne Shell"
date: 2009-03-15
forum: General Help
---

### Post by alzaf on 2009-03-15
Hi 

This is more of a request for info rather than help.

I have a Cnm Minibook that uses the Bourne Shell. I was trying to amend  it's startup file to change prompt and add aliases. On googling, I found that the Bourne shell's startup files are located in /etc/profile and $HOME/.profile.

The details of what I did is in my blog:

[http://cnm-minibook-mucking-about.blogspot.com/2009/03/configuring-xterm-shell.html](http://cnm-minibook-mucking-about.blogspot.com/2009/03/configuring-xterm-shell.html)

I did the same on Ubuntu's Bourne Shell and amended the /etc/profile and $HOME/.profile by changing the prompt to:

PS1='\u\w> '

When I type in sh to go into Bourne shell it still displays 

$

Is this the normal behaviour of the Bourne Shell?

---

### Post by taurus on 2009-03-15
Put your stuff in ~/.bashrc instead.

---

### Post by lloyd_b on 2009-03-15
First off, in Ubuntu, when you type "sh" you are *not* getting a "Bourne Shell".  This invokes "dash", which is POSIX compliant shell somewhat like the Korn Shell, but different enough that it's not considered a clone of the Korn Shell.

Second - ~/.profile is only read by *login* shells.  When you invoke "sh" (or "bash" or any other shell) after logging in, it is not accessed again.

The standard shell ("bash", a.k.a "Bourne-Again Shell") is probably the closest in a standard Ubuntu install to a true Bourne Shell.

As noted by another poster - to change settings for "bash" and have them work whenever a shell is invoked (login or not), make the changes to "~/.bashrc".

Lloyd B.

---

