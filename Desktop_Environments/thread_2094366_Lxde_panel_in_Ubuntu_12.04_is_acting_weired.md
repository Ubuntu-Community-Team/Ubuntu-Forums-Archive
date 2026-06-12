---
title: "Lxde panel in Ubuntu 12.04 is acting weired"
date: 2012-12-13
forum: Desktop Environments
---

### Post by uzumakifahim on 2012-12-13
I've installed LXDE on Ubuntu 12.04. It works great with my netbook. Suddenly, after rebooting my PC, I'm facing a problem with the default LXDE menu.

**There is a unwanted space in the default panel of LXDE. Please check the attached image for better understanding. Just look at the "free space" between the Dropbox and QB icon.**

I'm new for LXDE. Please help, how can I get rid from this unwanted "free space".

Thanks in advance.

---

### Post by vasa1 on 2012-12-13
> **uzumakifahim said:**
> I've installed LXDE on Ubuntu 12.04. ...
There is a unwanted space in the default panel of LXDE. ...

Hi, not of much help to you but this is a [known issue in 12.04]("http://askubuntu.com/questions/208251/strange-space-in-lubuntu-desktop/208285#208285") which goes away in 12.10.

It maybe possible to fix the problem in 12.04 but I don't know how. I'm now on 12.10 and there's no unwanted space (which I did suffer when on 12.04).

---

### Post by uzumakifahim on 2012-12-13
Hi, Vasa1 thanks for your reply. I need to solve this problem in Ubuntu 12.04. I want to stick with 12.04 for its LTS. Looking forward for anyone who can help me on this regard.

---

### Post by vasa1 on 2012-12-14
I don't know if what I'm suggesting is correct or not, but have you enabled backports in your software sources?

BTW, when I type **xfce4-power-manager --version** in a terminal, I see **Xfce Power Manager 1.2.0**.

What do you see?

The other thing you could do is to tag your question with Xfce and Xubuntu.

---

### Post by uzumakifahim on 2012-12-14
> **vasa1 said:**
> I don't know if what I'm suggesting is correct or not, but have you enabled backports in your software sources?

BTW, when I type **xfce4-power-manager --version** in a terminal, I see **Xfce Power Manager 1.2.0**.

What do you see?

The other thing you could do is to tag your question with Xfce and Xubuntu.

May be you are in the right way to solve this problem. I have Xfec4 installed on the same PC. 

[LIST=1]
[*]Is this issue somehow related to xfce?
[*]When I type **xfce4-power-manager -version**, it shows **The program 'xfce4-power-manager' is currently not installed. You can install it .....**? How can xfce power manger help me to solve this?
[*]I've backports enabled in my software sources.
[/LIST]
Thanks.

---

### Post by vasa1 on 2012-12-14
> **uzumakifahim said:**
> May be you are in the right way to solve this problem. I have Xfec4 installed on the same PC. 

[LIST=1]
[*]Is this issue somehow related to xfce?
[*]When I type **xfce4-power-manager -version**, it shows **The program 'xfce4-power-manager' is currently not installed. You can install it .....**? How can xfce power manger help me to solve this?
[*]I've backports enabled in my software sources.
[/LIST]
Thanks.

I'm not absolutely sure but I understand that the xfce4 power manager is used by **the LXDE implementation of Lubuntu**. I do not know whether it is part of the LXDE you have installed.
From whatever I've read, it seems that the excess spacing in the lxpanel is related to the xfce4 power manager. Since you do not seem to have it installed, your problem may be different?
If you're interested, you could look at [https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000335.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000335.html).

---

### Post by uzumakifahim on 2012-12-20
Which version of LXDE has been used for Lubuntu 12.04? I think as this is an issue related with LXDE, so if LXDE have released any new version, then installing that version could solve the problem.

---

### Post by Dennis N on 2012-12-20
On your original post (#1):

Do you have stretch enabled in the Task Bar applet? This will shove all the stuff to the right of it as far as possible. You can also add spacers in other places with stretch enabled to move stuff to the right.

Panel Settings > Panel Applets

check the "strech" box next to task bar, or next to any spacer.

---

### Post by uzumakifahim on 2012-12-22
> **Dennis N said:**
> On your original post (#1):

Do you have stretch enabled in the Task Bar applet? This will shove all the stuff to the right of it as far as possible. You can also add spacers in other places with stretch enabled to move stuff to the right.

Panel Settings > Panel Applets

check the "strech" box next to task bar, or next to any spacer.

Thanks for your reply. It works partially, but a new problem with panel have appeared. Please take a look at the screenshot. Now my panel is stretched that other indicators like, Dropbox, Ubuntu One etc. are in the second desktop. I think screen shot will clarify everything. Please take a look and help anyone with this problem.

Thanks in advance.

---

### Post by Dennis N on 2012-12-22
> **uzumakifahim said:**
> Thanks for your reply. It works partially, but a new problem with panel have appeared. Please take a look at the screenshot. Now my panel is stretched that other indicators like, Dropbox, Ubuntu One etc. are in the second desktop. I think screen shot will clarify everything. Please take a look and help anyone with this problem.

Thanks in advance.

Please show us a screenshots of both desktop 1 panel and desktop 2 panel to clarify what this new problem looks like. Otherwise, it is hard to visualize.

---

### Post by uzumakifahim on 2012-12-22
> **Dennis N said:**
> Please show us a screenshots of both desktop 1 panel and desktop 2 panel to clarify what this new problem looks like. Otherwise, it is hard to visualize.

Ohhh.. Just forgot to upload the screen shots. Sorry for that. Here is the screen shots....

---

### Post by TREESofRIGHTEOUSNESS on 2012-12-22
That is really weird I am using 12.04 and not experiencing any of those issues... I do not use dropbox, though....  12.10 gave me lots of problems so I reverted back to 12.04 because it is really stable and the core elements will be supported for a long time.  I have tweaked my setup quite a bit, so I am going to ask some basic questions first... and don't be offended if I am being to basic or obvious... sometimes these are the easiest things to overlook

1. Right click panel --> Panel preferences --> Panel Applets tab
 make sure there are no odd spacers in there...
(it doesn't look like this is your problem, but it is worth checking anyhow)

2. get rid of the dropbox icon and the cloud (ubuntu-one indicator perhaps?) see if this solves the issue, if it does, then it is a problem with the System tray applet.  If this is the case, you might be able to tweak your panel some to get it to squish it all onto your single desktop.

3.  You can rename your panel config files, and reconfigure it from scratch.
/home/<your USERNAME>/.config/lxpanel/Lubuntu/
(I usually just move the lxpanel folder into a new directory named backup)

4. I have found issues can result from having Xfce4 and Lxde both installed occasionally.  The best answer is to backup and reinstall.... of course if you make a separate /home partition this is fairly painless (though it takes  a long time).  You may have to delete some of your panel config files if it still persists.

I am attaching my screenshot so you can see that I don't have the issue here.

---

### Post by uzumakifahim on 2012-12-23
@ [TREESofRIGHTEOUSNESS]("http://ubuntuforums.org/member.php?u=1436851") , Thanks for your help. I'll update here ASAP.

---

### Post by uzumakifahim on 2012-12-23
> **TREESofRIGHTEOUSNESS said:**
> That is really weird I am using 12.04 and not experiencing any of those issues... I do not use dropbox, though....  12.10 gave me lots of problems so I reverted back to 12.04 because it is really stable and the core elements will be supported for a long time.  I have tweaked my setup quite a bit, so I am going to ask some basic questions first... and don't be offended if I am being to basic or obvious... sometimes these are the easiest things to overlook

1. Right click panel --> Panel preferences --> Panel Applets tab
 make sure there are no odd spacers in there...
(it doesn't look like this is your problem, but it is worth checking anyhow)

2. get rid of the dropbox icon and the cloud (ubuntu-one indicator perhaps?) see if this solves the issue, if it does, then it is a problem with the System tray applet.  If this is the case, you might be able to tweak your panel some to get it to squish it all onto your single desktop.

3.  You can rename your panel config files, and reconfigure it from scratch.
/home/<your USERNAME>/.config/lxpanel/Lubuntu/
(I usually just move the lxpanel folder into a new directory named backup)

4. I have found issues can result from having Xfce4 and Lxde both installed occasionally.  The best answer is to backup and reinstall.... of course if you make a separate /home partition this is fairly painless (though it takes  a long time).  You may have to delete some of your panel config files if it still persists.

I am attaching my screenshot so you can see that I don't have the issue here.

It worked!!! Your third solution (reconfiguring the panel) worked for me perfectly. Really thanks for your help.):P

---

### Post by TREESofRIGHTEOUSNESS on 2012-12-24
Great!!!  I am glad to hear it.  Lubuntu is a great distro and has come very far... there are just a few minor quirks here and there :)

Will you mark the Thread as solved, so others will know your issue has been solved.

---

### Post by TREESofRIGHTEOUSNESS on 2012-12-27
An interesting development is that I have found how to 'include' this bug in my system.  I have installed Xubuntu on my machine as well as Lubuntu, and I now have the sys tray problem. 

SO HERE ARE MORE solutions for all future people that come across this.


These 3 links contain all the info in this post... and this post contains the basic info collected from them all.

[http://ubuntuforums.org/showthread.php?t=1869357](http://ubuntuforums.org/showthread.php?t=1869357)
[http://forum.lxde.org/viewtopic.php?f=21&t=31432](http://forum.lxde.org/viewtopic.php?f=21&t=31432)
[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/846878](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/846878)

Here is all this info that I found that presents the most complete answer to this issue.

The problem is in the overlay scrollbars OR the xfce power manager.

So, you can do a few things to fix it or workaround the issue.
in a terminal type:
```
 lxpanelctl restart 
```
will restart your panel and get rid of the extra space.

Some people have made a script to restart it, and added a button to the panel as described here in post #16 or #29 and other places...
[http://ubuntuforums.org/showthread.php?t=1869357&page=2](http://ubuntuforums.org/showthread.php?t=1869357&page=2)

some people have removed the System Tray from the panel, and some have moved it all the way to the right side of the panel.
of course removing this removes the battery icon which is important for laptops to have.  One workaround is to use this battery app (as the lxpanel's battery app doesn't work very well (it always says 100% on my computer)

[https://code.google.com/p/batti-gtk/downloads/detail?name=batti-0.3.8.tar.gz](https://code.google.com/p/batti-gtk/downloads/detail?name=batti-0.3.8.tar.gz)

Some people have removed the libraries for the overlay scrollbars

in a terminal type:
```

sudo apt-get remove liboverlay-scrollbar-0.2-0
sudo apt-get remove liboverlay-scrollbar3-0.2-0

```

Some people like to go into the xfce power manager settings and set it to not display an icon ever.

in a terminal type:
```
xfce4-power-manager-settings
```
Under 'System tray icon' select 'Never show icon' and click Close.

---

