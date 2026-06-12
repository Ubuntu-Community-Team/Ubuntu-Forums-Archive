---
title: "Evolution and Exchange in 10.10"
date: 2010-09-09
forum: Desktop Environments
---

### Post by drdabbles on 2010-09-09
I upgraded my desktop to Ubuntu 10.10 (maverick), and noticed that likewise-open was broken. I created a local user, moved my home directory, changed permissions on my old home folder, and moved on.

Evolution, though, will not connect to my Exchange server. When I configure an account, I can never expand the name to reveal my personal and public folders.

When I try to modify my Exchange account settings, Evolution hangs and requires a forced shutdown.

Anybody have any ideas? How might I start Evolution with some logging to see where it's running into problems?

Thanks!

---

### Post by surfin on 2010-09-10
Hello, i have exactly the same problem. Evolution-Exchange works on 10.04 but not on 10.10.
Hope they will add a correction.

Sincerely,

Charles

---

### Post by kreedtek21 on 2010-09-10
This bug is tracking a similar issue.  If it is the same, and the fix works for you too, then go ahead and add yourself to the issue so it can be fixed.

[https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/617549](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/617549)

---

### Post by jsampaio57 on 2010-10-11
The simplest workaround is to start Evolution offline then, after load-up, connect it (click the "connect plugs" in the left lower corner of the window). 

Either type in the terminal
$ evolution --offline  

or change the property of the Evolution menu item (System > Preferences > Main Menu > etc.) so that the command reads 
evolution --offline %U   or evolution --offline --component=mail

Cheers...

---

### Post by Angotull on 2010-10-11
*sigh* that works...............

---

### Post by akitto69 on 2010-10-11
Had the same issue, after upgrade exchange connection did not work. Setting to offline on startup fixed this issue for me.

---

### Post by FizzBuzz on 2010-10-11
Same issue here.  Starting in offline mode workaround seems to work for me as well.

--edit--
I take it back.  I can receive and read new messages, but Evolution seems to be having a hard time applying my filters to new messages.  The program hangs when trying to manually apply filters (CTRL-a, CTRL-y).  I'll just wade through all my log emails manually until a fix comes along...


--edit 2--
As per the bug tracking forum posted above, the better workaround is to start evolution from the command line as such:

evolution --disable-eplugin

This returns evolution to full functionality.

---

### Post by guisar on 2010-10-13
I don't know if it's better but it does work. Should we report this bug or figure it will be addressed in an update? 

Is there a way to add this flag to the graphical menu for Evolution? Right click, etc doesn't work.

---

### Post by lachild on 2010-10-13
> **guisar said:**
> I don't know if it's better but it does work. Should we report this bug or figure it will be addressed in an update? 

Is there a way to add this flag to the graphical menu for Evolution? Right click, etc doesn't work.

No the bugs already been reported as noted above.  Simply subscribing to it will work

[https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/606822]("https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/606822")


To edit the menu item:  Right Click on "Applications" and select "Edit Menus".  From there select "Office" on the left and then "Evolution" on the right.  Click on properties and edit the command.

---

### Post by chuckh1958 on 2010-10-15
I have a dual boot PC. Windows XP in one partition and Ubuntu 10.10 in the other. This workaround does not work for me in the Ubuntu partition, however it works fine in an Ubuntu VM running in Windows. Not sure why it works in one but not the other. I had to roll back the installation in it's own partition as not having a working version of Evolution is a show stopper in a corporate MS Exchange environment.

---

### Post by guisar on 2010-10-15
I just (15 Oct) got an update 2.30.3-1ubuntu7 which appears to have resolved the connection to Microsoft&#347; Exchange OWA.

---

### Post by chuckh1958 on 2010-10-15
What repo are you getting it from? I'm still showing 2.30.3-0ubuntu6 as the current version of evolution, and 2.30.3-ubuntu1 for evolution-exchange.

---

### Post by Aearenda on 2010-10-18
I just found 2.30.3-1ubuntu7 in maverick-proposed.

---

### Post by chuckh1958 on 2010-10-19
Very strange. If I install that version from the maverick-proposed repo in my ubuntu vm, it works. If I install it on a physical machine, it does not.

---

### Post by jmarks on 2010-11-28
I have never been able to get Evolution working with Exchange Server 2007. I upgraded to 10.10 because the evolution-mapi connector was supposed to have been improved.

Now, I have evolution, evolution-exchange, and evolution-mapi installed. However, upon firing up evolution, I do not even have the option of Exchange presented when I try to set up an account! Under Edit Plugins, there is not option for exchange.
Have I failed to install something?
A step-by-step account of how to set up Evolution with Exchange 2007 would be so appreciated.
I keep Ubuntu as a dual boot on my Windows machine in the hopes of being able to move to Ubuntu full time, but the ongoing lack of email support for  a corporate environment  continues to be the deal breaker for me.

Thank you for any any help people can provide!

---

