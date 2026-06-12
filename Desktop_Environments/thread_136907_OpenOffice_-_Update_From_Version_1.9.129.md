---
title: "OpenOffice - Update From Version 1.9.129?"
date: 2006-02-26
forum: Desktop Environments
---

### Post by rf131 on 2006-02-26
Hi There,

I have a situation where I'm getting incorrect behavior with an Impress presentation on Ubuntu 5.1.  It has a variable clock on each slide that updates everytime the slides are re-displayed.  This works good on Windows with OpenOffice version 2.0, but the time doesn't get updated on 1.9.129 on Ubuntu 5.1.

I wanted to see if there was an easy way to obtain an update for OpenOffice in the hope that I can get the clock to update as it does in Windows.  The update manager doesn't indicate that an update is available.

If the versions are the same and I get different behavior, then I'll submit a bug report.

Thanks,
Kevin

---

### Post by jrib on 2006-02-26
add the appropriate line to your sources.list, then update and upgrade: [http://lists.ubuntu.com/archives/ubuntu-devel/2005-October/012520.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-October/012520.html)

if you are not sure what to do, paste the contents of /etc/apt/sources.list and what architecture you use :)

---

### Post by rf131 on 2006-02-27
Hi Jason,

Thanks for your tips.  I did add this line to the /etc/apt/sources.list:

**deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./**

However, when I go into **Add Applications / File / Advanced**, I get a message:
[B][I]"W:Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory).
[/I][/B]
Some kind of syntax error in the sources.list?  I followed the syntax exactly as listed in your reference.

Kevin

---

### Post by jrib on 2006-02-27
Go into system > administration > synaptic and press the 'reload' button at the top.  Then use it to update OpenOffice, 'Mark all upgrades' should do it.  I've never used the add applications thing, so just stick with synaptic :)

[edit] Just so you know, anytime you manually edit the sources.list, you need to tell the package system to update.  The terminal command is 'sudo aptitude update' or 'sudo apt-get update'.  Hitting reload in Synaptic does the same thing.

---

### Post by rf131 on 2006-02-27
Ah, I'm getting close... downloading the updates now.

I'll let you know if this resolves my time problem (cross your fingers).

KR

---

### Post by rf131 on 2006-02-27
Jason,

The update works!  :D 

The clock behavior is consistent with the Windows version.  I still have some wierd behavior though.  For some reason, I have to put in a slide on the end WITHOUT a variable time field.  It doesn't matter whether or not I have a delay at the end of the presentation; without the slide that doesn't have the time, the time doesn't get updated. Go figure.

Now, I have everything I need to retire yet another Windows system.

Thanks for your tips... I'm a noob to Ubuntu, but in the 10 days I have been using it, I think it puts a lot of other distros to shame.

Kevin

---

### Post by jrib on 2006-02-27
Yep ubuntu is great!  Glad to see you got your issue sorted out

---

### Post by wacole on 2006-03-08
Thanks much.  I was getting bad behavior in writer tables when formatting numbers.  Upgrade solved it.

---

