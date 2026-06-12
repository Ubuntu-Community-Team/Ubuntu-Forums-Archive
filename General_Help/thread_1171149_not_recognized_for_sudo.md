---
title: "not recognized for sudo"
date: 2009-05-27
forum: General Help
---

### Post by pranesh on 2009-05-27
i have been using Ubuntu 9.04 without trouble. Suddenly a few minutes ago, Im not recognized as administrator. 
For
pranesh@pranesh-laptop:~$ sudo apt-get install amarok

It says

pranesh is not in the sudoers file.  This incident will be reported

Please help

---

### Post by Soul-Sing on 2009-05-27
1. Boot in recovery mode
2. Type visudo (you're already root so you don't need to sudo here......)
3. confirm that there is a line matching the following:
%admin ALL=(ALL) ALL
whitespace is irrelevant, just make sure it is its own line NOT preceded by a # symbol
4. If not, add that line (hit i to enter insert mode and escape to return to normal mode)
5. type :wq (in normal mode)
6. If you get an error message, comment out any other lines with # symbols. If you still get an error message, visudo is misbehaving or I mistyped that line above.
7. To be on the safe side, type (on the command line) groups pranesh (or whatever your normal username is)
8. Check if the output contains the word admins. If not, you'll have to do a quick adduser pranesh admins
9. Type shutdown -r now
10.Boot as normal
11.This will fix your sudoers issue.

---

