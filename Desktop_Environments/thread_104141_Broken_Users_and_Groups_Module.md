---
title: "Broken Users and Groups Module"
date: 2005-12-15
forum: Desktop Environments
---

### Post by LordRaiden on 2005-12-15
When I try to go into 'Users and Groups' under System Settings i get the following

The diagnostics is: <blank - nothing here>

Possible reasons:
-An error with you're last kde upgrade
-you have old third party modules lying around


Personally, i think im missing some package(s).  Any clue which one(s)? I have kuser installed so its not that.

thanks in advance

---

### Post by mlomker on 2005-12-16
You could try reinstalling all of the packages that it depends upon, but looking at the list they are pretty basic packages...I should think that other things would be broken if they weren't okay.

---

### Post by LordRaiden on 2005-12-17
I won't be able to say until after the new year since I am leaving the country. However, nothing else seems broken, just can't access that specific tab. I'll live with it until a) I find out how to fix it b)I have to reinstall Kubuntu c) Dapper Drake is released :)

---

### Post by neilmusgrove on 2006-04-09
I've got this problem too, i uninstalled kde-guidance and reinstalled it from the kde-latest repositories, still the same problem.

Anyone have any idea?

Below is  what is output when i try to launch the module manually from a terminal.

> 
0755  default chmod
0755  default chmod
Traceback (most recent call last):
  File "/usr/bin/userconfig", line 1617, in ?
    userconfigapp = UserConfigApp()
  File "/usr/bin/userconfig", line 255, in __init__
    self.admincontext = unixauthdb.getContext(isroot)
  File "/usr/lib/python2.4/site-packages/unixauthdb.py", line 41, in getContext
    return PwdContext(editmode)
  File "/usr/lib/python2.4/site-packages/unixauthdb.py", line 744, in __init__
    user.polish()
  File "/usr/lib/python2.4/site-packages/unixauthdb.py", line 837, in polish
    self.setPrimaryGroup(self._context.lookupGID(self._gid))
  File "/usr/lib/python2.4/site-packages/unixauthdb.py", line 492, in setPrimaryGroup
    self.addToGroup(groupobj)
  File "/usr/lib/python2.4/site-packages/unixauthdb.py", line 511, in addToGroup
    groupobj._addUser(self)
AttributeError: 'NoneType' object has no attribute '_addUser'


Looks like a bug in the code to me rather than a system problem.

---

### Post by hippyjim on 2006-06-02
I'm having the same problem after upgrading to Dapper - it was fine before so I guess I broke something.

Has anyone else had this and figured what to do? What did you do?

---

### Post by jakoblund on 2006-06-07
Hi
I just installed Kubuntu (dapper), and I had the same problem with the Users & Groups module AND the Display module in KControl. With me it turned out to be a problem with locale... I'm using a danish locale, so my LANG variable was set to da_DK.

I switched to (K)ubuntu from another distro (gentoo), and the problem was in my ~/.bashrc: I had 

> 
export LANG=da_DK
export LC_ALL=da_DK

in there, but the only available (in /usr/lib/locale) danish locale was da_DK.utf8
Changing the two values in .bashrc to the valid locale, and then logging out & into KDE fixed the problem.

-:)  Jakob.

---

