---
title: "OpenRPG Install/Run issues...help pls!"
date: 2009-06-06
forum: Gaming &amp; Leisure
---

### Post by ajpfox on 2009-06-06
Hey all,  

   I'm running Ubuntu 9.04 Jaunty Jackalope, and I'm trying tin install OpenRPG on my system, but it is a royal pain to get working for some reason.  I found an old guide on these forums, which didn't work,  the official install instructions don't work...nothing works!!

In my most recent attempt, I followed the guide outlined here (after I deleted everything to try and start fresh):

[http://www.assembla.com/wiki/show/dIvWc45xer3lzlabIlDkbG](http://www.assembla.com/wiki/show/dIvWc45xer3lzlabIlDkbG)

Using the method this site describes (which seemed very simple) I got all the way to 

cd OpenRPG
python setup.py

This gives me the following:

me@me-laptop:~$ cd /home/me/.openrpg/OpenRPG/
[email]me@me-laptop:~/.openrp[/email]g/OpenRPG$ python setup.py
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 13535, in <lambda>
    lambda event: event.callable(*event.args, **event.kw) )
  File "setup.py", line 97, in install
    self.log.Value += "Installing OpenRPG user files to " + os.environ["OPENRPG_BASE"] + "\n"
AttributeError: 'TextCtrl' object has no attribute 'Value'

This also opens a blank window with the "Open RPG setup wizard", which does nothing...

I made an attempt to continue anyway, following the guide, but I am continually blocked by missing modules;
First  "start_release.py" was missing, then "pyver.py" and now finally "orpg.orpg_version.py"  I got progressively farther step by step by finding the missing files elsewhere and putting them in the OpenRPG directory, but I couldn't get past the missing "orpg.orpg_version.py" file.

Please help if you can, I'm at my wits end with this program...are there other guides out there?  Maybe some files I'm missing?  Do I need to reinstall openrpg from the depositories (which is an outdated version) again?

---

### Post by tommenquar on 2009-06-16
i would say try and get in contact with prof_ebral. he just released a new version of openrpg and i know he has a guide to install it on ubuntu somewhere around his area. you can get incontact with him at his websirte [http://www.knowledgearcana.com](http://www.knowledgearcana.com)

---

### Post by Trebawa on 2009-06-27
I had the same problem, until I realized that the guide [here]("http://www.assembla.com/wiki/show/openrpg/InstallUbuntu_Hardy") says to install python-wxtools and python-wxaddons as well as python-wxgtk.  In addition, I made sure I only installed python-gtk2.8.  I don't know if it was python-gtk2.6 or not having the other packages that caused it to fail, but that fixed it for me.

---

### Post by theophiles on 2011-05-27
I'm having trouble python-wxaddons is not in the repositories. Where should I get it?

---

