---
title: "Synaptic failed"
date: 2005-04-22
forum: Desktop Environments
---

### Post by Promethe on 2005-04-22
I was going to install TeX system for my Ubuntu. I've opened synaptic, and synaptic informed me about old database. I've clicked Refresh/Update (I'm using Polish version), wait a while, and after updating i've clicked search. And... Synaptic disappered.
I've checked once more - the same problem.
I've runned it from Terminal, and I've get it:
```
promethe@ubuntu:~$ sudo synaptic
I/O error : Input/output error

(synaptic:9925): XML-CRITICAL **: Document is empty


(synaptic:9925): XML-CRITICAL **: Start tag expected, '<' not found


(synaptic:9925): GLib-CRITICAL **: g_string_free: assertion `string != NULL' failed
I/O error : Input/output error

(synaptic:9925): libglade-WARNING **: did not finish in PARSER_FINISH state
synaptic: rggladewindow.cc:57: RGGladeWindow::RGGladeWindow(RGWindow*, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >): Warunek `_gladeXML' nie zosta&#322; spe&#322;niony.
Przerwane
``` 
Could anybody help me?

---

### Post by alastair on 2005-04-22
Looks a bit like some of Synaptic's XML config files are corrupt.

Shame about the terrible error messages and no idea what the problem file is (or are).

You might be best to uninstall synaptic and reinstall (use apt-get or aptitude). Unless someone else has a better idea.

---

### Post by godsunderstudy on 2005-04-22
:razz: A week after downloading Hoary stable on  April 8th (my birthday, what a present!, Ubuntu rocks! and so forth!) we checked for updates. Synaptic says there are some, but will not download them.
Fine.
On unstable I didn't have landscape printing and music and stuff and then I did.
I trust Ubuntu to fix problems.
Synaptic still hangs. 

apt-get gets:

me:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  cupsys kdewebdev kdm kicker-applets kimagemapeditor kommander
  kubuntu-default-settings kxsldbg libxdmcp6 quanta quanta-data
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.6MB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Waiting for headers]

And so it goes.
How do I update when I can't?

There are plenty of other threads on problems, such as "whats up with 5.04?" and long threads on the kubuntu forum basiclly saying that K now stands for krash, not kool.
 [-X 
My question is:
Should I go back to the unstable stable version of Ubuntu, or stick with the stable unstable release?


ps This is not godsunderstudy. This is godsunderstudysdad and I can't be bothered to log out and loginagain.

---

### Post by i-tech on 2005-04-22
it happened to me also when a package has dependencies to install synaptic disappears ](*,) i could not find a solution! single packages should work, well it was working for me :)

---

### Post by alastair on 2005-04-22
Sorry to see you have problems. But you should post to a new thread because this is nothing to do with the current thread/problem.

---

