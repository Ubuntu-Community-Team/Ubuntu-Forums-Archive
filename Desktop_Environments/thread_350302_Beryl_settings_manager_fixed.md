---
title: "Beryl settings manager fixed?"
date: 2007-01-31
forum: Desktop Environments
---

### Post by mts-fi on 2007-01-31
I installed Beryl about a week ago and my beryl settings manager have never worked. I've read lots of instructions to fix it, but nothing.
Now it seems that this bug has been fixed.
 
See: [http://bugs.beryl-project.org/ticket/815](http://bugs.beryl-project.org/ticket/815)
and [http://bugs.beryl-project.org/changeset/3460](http://bugs.beryl-project.org/changeset/3460)

But so what!!!
I'm new with linux and I don't know what to do to fix my Beryl Settings Manager.

Please help me! :confused:

---

### Post by Waappu on 2007-01-31
Hi

Type in terminal```
beryl-settings
``` and post output here. I hope I can help you then

---

### Post by mts-fi on 2007-01-31
Output:

Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 2, in <module>
    import berylsettings
ImportError: No module named berylsettings

---

### Post by xopher on 2007-01-31
```
sudo apt-get install beryl-settings-bindings
```

---

### Post by Waappu on 2007-01-31
Hi

Type in terminal```
gksudo gedit /usr/bin/beryl-settings
```
text editor should open and replace first line with this```
#!/usr/bin/env python2.5
```and save file.
Then type in terminal again```
beryl-settings
```and if setting manager don't open and gives some error messages to terminal post errors here. Then we need proceed other way

---

### Post by mts-fi on 2007-01-31
> **xopher said:**
> ```
sudo apt-get install beryl-settings-bindings
```

I have done that several times... no help!

---

### Post by mts-fi on 2007-01-31
> **Waappu said:**
> Hi

Type in terminal```
gksudo gedit /usr/bin/beryl-settings
```
text editor should open and replace first line with this```
#!/usr/bin/env python2.5
```and save file.
Then type in terminal again```
beryl-settings
```and if setting manager don't open and gives some error messages to terminal post errors here. Then we need proceed other way

It was already that way.

---

### Post by Waappu on 2007-01-31
Hi

OK, Then change that first line to this ```
#!/usr/bin/env python
```

---

### Post by mts-fi on 2007-01-31
> **Waappu said:**
> Hi

OK, Then change that first line to this ```
#!/usr/bin/env python
```

No help!

Did you read this? [http://bugs.beryl-project.org/ticket/815](http://bugs.beryl-project.org/ticket/815)

---

### Post by Waappu on 2007-01-31
Hi

Ok.

I fix same problem this way.

first I check that I have only SVN repos in /etc/apt/sources.list
then in terminal ```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude remove beryl-settings-bindings
sudo aptitude install beryl
```

and I have in  /usr/bin/beryl-settings file first line
```
#!/usr/bin/env python
```

I don't know does that fix your problem, so use with own risk.

What repositorys you used to install beryl?

Edit:
Repos that I use can be found here
[http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/)

---

### Post by mts-fi on 2007-01-31
I used these istructions
 [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation)

I got my beryl working with that but without beryl settings manager. I also use nvidia beta driver and I don't feel like changing too much on my computer now when everything else seems to work fine.

Thank you anyway.

---

### Post by mexlinux on 2007-01-31
Yes, it's solved, in the SVN packaged from Treviño already.

Warning: Official beryl-setting-bindings version is 0.1.9-something.
While Treviño's svn, is 0.1.5-something
(don't ask me why)
So, make sure you have the Treviño SVN repo in your sources file.
But NOT the official Beryl, otherwise that package won't upgrade.

---

### Post by jshayden on 2007-01-31
> **mexlinux said:**
> Yes, it's solved, in the SVN packaged from Treviño already.

Warning: Official beryl-setting-bindings version is 0.1.9-something.
While Treviño's svn, is 0.1.5-something
(don't ask me why)
So, make sure you have the Treviño SVN repo in your sources file.
But NOT the official Beryl, otherwise that package won't upgrade.


Thanks.  That worked for me.  They really should get the numbering straight, though...

---

### Post by mts-fi on 2007-02-02
Update fixed this bug :-\"

---

