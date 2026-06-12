---
title: "console-kit-daemon consuming 400MB res memory???"
date: 2013-03-10
forum: Desktop Environments
---

### Post by jac12345 on 2013-03-10
Hi all, apologies in advance if I'm posting this question in the wrong forum.

I am currently administrating a number of linux servers running Ubuntu 10.04LTS and I have noticed that all of these servers have a process called console-kit-daemon which is consuming anywhere from 200-400MB of memory. In some cases SWAP memory is used which may or may not be having an impact on performance.

A brief search on Google shows that the console-kit-daemon is used to manage user logins via the graphical user interface. So the fact it's using so much memory for such a simple task makes me assume this is a memory leak.

In a terminal I ran "$ dpkg -s consolekit" and was able to find out the version of console-kit-daemon: version: 0.4.1-3ubuntu3.

I believe this is a common issue and I have spent several hours trying to look for a solution to no avail. So I was wondering if anyone could shred some light on my problem and possibly give me some advice.

If it helps, these servers are virtualized and run in headless mode. We very rarely have to remote desktop onto them so I would be open to removing the consolekit altogether. However, I wouldn't want to do so if this package is needed.

Cheers

---

