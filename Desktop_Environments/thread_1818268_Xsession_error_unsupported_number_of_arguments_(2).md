---
title: "Xsession error: unsupported number of arguments (2); falling back to default session"
date: 2011-08-04
forum: Desktop Environments
---

### Post by filosofiamanga on 2011-08-04
Hi, I just installed my Lubuntu, but I upgrade to lubuntu 11.04 (natty), after that I decided to try unity, so I installed ubuntu-desktop and unity, but when I try to start session on Ubuntu or unity it told me the title error, then I got the error.
It open me a session without any menues and just a clean desktop.

I would love any help.

On another topic, after I upgrade, Lubuntu ask the password each time I turn on my computer, But when I try to change the settings and click on the button that say: enter session without asking password, that button appear locked.
How do I unlock it?

Thanks.

---

### Post by Rodrigo on 2011-08-06
> **filosofiamanga said:**
> Hi, I just installed my Lubuntu, but I upgrade to lubuntu 11.04 (natty), after that I decided to try unity, so I installed ubuntu-desktop and unity, but when I try to start session on Ubuntu or unity it told me the title error, then I got the error.
It open me a session without any menues and just a clean desktop.

Same problem here, I had a perfect & healthy Ubuntu 10.04 install in my netbook, added lubuntu-desktop for fun, and two weeks later upgraded to 11.04... and got the SAME error you have.
LXDE works perfectly, I don't know what is the problem here. :confused:

---

### Post by LebLinux on 2011-08-28
Bumpppppppppp!

---

### Post by doogiekd on 2011-09-18
same problem here.

i have a low end machine and wanted to be able to use lubuntu for some things requiring high memory.

---

### Post by doogiekd on 2011-09-18
more information regarding this problem:

1. selecting anything but lubuntu in the session menu on the login screen always gives the following message:

"xsession: unsupported number of arguments (2) falling back to default session.

2. regardless if you pick unity, unity 2d, or ubuntu classic from the session menu on the login screen, the above message appears (clicking "okay" makes it dissapear - but unity ALWAYS starts, even if you picked ubuntu classic.

3. in unity, the mouse left button does not work.

4. in unity, the unity menu bar does not autohide and is always on top.

5. in unity, when starting synaptic, the following message appears: 
"a malicious client may be eavesdropping on your session or you may have just clicked a menu or some application just decided to get focus. try again.

the system usually freezes at this point.

6. when attempting to correct the menu autohide problem in config settings manager, clicking the plugins option displays a message that plugins are in conflict and asks if you want to correct.

i have always clicked "no" - and would like clarification if i should resolve those plugin issues by clicking "yes."

it appears that gnome (unity) is conflicting with xfde (lubuntu) - although i dont know why this happening because selecting either session from the login screen should only start the appropriate desktop mgr.

like everyone here, i installed lubuntu from the synaptic in unity because there are some times when i want to run things in lowest memory possible because i have an old computer. (512mb compaq i386). I really was hoping that i could choose between unity (or more preferably gnome classic) or lubuntu from the login screen.

any suggestions?

---

### Post by doogiekd on 2011-09-18
apparently there is a required method for installing lubuntu with ubuntu:

[https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu](https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu)

i would recommend removing lubuntu and all of its components thru synaptic, then install lubuntu following this thread.

---

### Post by doogiekd on 2011-09-18
well i tried the thread from above on the lubuntu forum, and the problem continues. i am posting this question on the lubuntu site.

---

### Post by ujangbandung on 2011-12-24
hope this can help you

ok my history first

i install lubuntu on my netbook

then i miss ubuntu unity...but i dont want to change my lubuntu with ubuntu, so i decide to install unity in my lubuntu natty

after install it i got the xsession error message if i choose ubuntu (unity) when i login to my computer, and just like you, unity doesnt start at all, i have to use terminal to call unity....this doesnt solve the problem though if i have to do this every time i login using unity

solution to my problem:

i install ubuntu-desktop, the command:

sudo apt-get install --no-install-recommends ubuntu-desktop

then i reboot my netbook

result:

so far when i login using unity, i dont see the xsession error message again and unity is already there running..

hope this help although i read that you already installed ubuntu-desktop

---

### Post by mrak018 on 2012-05-09
I was able to get rid of this message by commenting out "source .bashrc" section in my ~/.profile file.

---

