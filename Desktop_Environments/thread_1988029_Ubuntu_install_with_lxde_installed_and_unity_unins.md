---
title: "Ubuntu install with lxde installed and unity uninstalled"
date: 2012-05-26
forum: Desktop Environments
---

### Post by crazyJay648 on 2012-05-26
Hello all,

Here's what I did. 

- Installed Ubuntu 12.04 LTS
- I then found out about lxde and installed that
- I then determined that I wanted to get rid of unity all together so I uninstalled it
- My login screen still look like unity though.

Here's my problem.
1 in every 2 logins my screen looks like the attached image. That weird stuff you see on the left looks like my old unity desktop, with the wallpaper and all. How do I get this to stop happening? As far as I can tell I removed unity all together, it's not an option at long in.

As I mentioned my login screen still looks like the original screen when I installed ubuntu. Is there some way to sort of have the whole thing be handled by lxde?

Any help would really be awesome.

Thanks,

---

### Post by kc1di on 2012-05-26
> **crazyJay648 said:**
> Hello all,

Here's what I did. 

- Installed Ubuntu 12.04 LTS
- I then found out about lxde and installed that
- I then determined that I wanted to get rid of unity all together so I uninstalled it
- My login screen still look like unity though.

Here's my problem.
1 in every 2 logins my screen looks like the attached image. That weird stuff you see on the left looks like my old unity desktop, with the wall paper and all. How do I get this to stop happening? As far as I can tell I removed unity all together, it's not an option at long in.

Any help would really be awesome.

Thanks,
how did you install lxde?

---

### Post by crazyJay648 on 2012-05-26
I used the ubuntu software center. That is also how I uninstalled unity.

I've also just discovered lubuntu, but I REALLY don't want to have to nuke my install and start fresh. >=\. There is so much I've configured.

---

### Post by kc1di on 2012-05-26
here's what to do:

go to a terminal and enter the following commands one at a time 
you can just copy and paste them if you want.
you will be asked for your password.

```
sudo apt-get update
sudo apt-get install lubuntu-desktop
```
that should take care of the problem.

---

### Post by jldoll on 2012-05-26
Maybe try putting unity back? I've switched to full lubuntu on my laptop, but my desktop still runs hybrid unity/lxde.  I did similar as you, but I left unity alone.  I just log into lxde by default. Haven't had issues with this setup.  Also you may want to poke around here a little [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) Many tutorials there.

---

### Post by crazyJay648 on 2012-05-26
> **kc1di said:**
> here's what to do:

go to a terminal and enter the following commands one at a time 
you can just copy and paste them if you want.
you will be asked for your password.

```
sudo apt-get update
sudo apt-get install lubuntu-desktop
```that should take care of the problem.

I did those two commands. Unfortunately it didn't work. I see that when I shutdown and boot up it does say lubuntu now. My login screen still looks like the origina ubuntu login though. The second just installed the lubuntu DE I'm guessing right? What does the first command do?


jldoll thanks for the link, I will have a look

---

### Post by kc1di on 2012-05-26
the first one just update the package list on your machine.

When you sign in are you selection lubuntu from the drop down menu?

---

### Post by BLewis on 2012-05-26
> **crazyJay648 said:**
> I did those two commands. Unfortunately it didn't work. I see that when I shutdown and boot up it does say lubuntu now. My login screen still looks like the origina ubuntu login though. The second just installed the lubuntu DE I'm guessing right? What does the first command do?


jldoll thanks for the link, I will have a look

Ok, sorry to be blunt here, but you are clearly a very early beginner with any Ubuntu/Debian based distros.

Sudo - Gaining superuser privelages using your current account password, only used in some distros. To learn more about superuser, google it.

Apt-get - The framework which manages packages which are applications or frameworks or parts of programs, this program, apt-get enables you to install them using the command install, remove them with remove, purge them (clear all data) from them and uninstall them using purge

Other main commands used with apt-get include update (which is what he used) which updates the information from repositories which are the places that store the applications and information about them and the latest build information etc. 

Other common ones include apt-get upgrade which updates/upgrades installed applications/parts of applications.

I would recommend a few things. 1. Learn a little more about terminal, it will save you a huge amount of time. 2. Think about reinstalling using Lubuntu very seriously. 3. Next install install a separate partition for data and system ([https://www.google.co.uk/webhp?sourceid=chrome-instant&ie=UTF-8&ion=1#hl=en&output=search&sclient=psy-ab&q=separate%20partitions%20for%20system%20and%20data%20ubuntu&oq=&aq=&aqi=&aql=&gs_l=&pbx=1&fp=85e5437805df3299&ion=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&biw=1440&bih=788](https://www.google.co.uk/webhp?sourceid=chrome-instant&ie=UTF-8&ion=1#hl=en&output=search&sclient=psy-ab&q=separate%20partitions%20for%20system%20and%20data%20ubuntu&oq=&aq=&aqi=&aql=&gs_l=&pbx=1&fp=85e5437805df3299&ion=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.,cf.osb&biw=1440&bih=788)) which will enable you to reinstall an Ubuntu-based OS or version without wiping data or application settings only applications and OS. 4. At the moment before reinstalling or whatever, looking into login managers such as GDM (Gnome 3 default), lightdm (Ubuntu default), KDM (Kubuntu default), LXDM (LXDE default) and maybe install LXDM. 

If you need anything just ask, I will try to respond quickly but if I don't I'm sure others will. Good luck. 

P.S. Hope that wasn't too much of an overload...

UPDATE: Try this command in terminal BTW, this might fix the double backdrop stuff:

sudo apt-get purge nautilus

This removes nautilus the file manager and desktop manager used in Ubuntu. 

If that doesn't work, report back :)

---

### Post by crazyJay648 on 2012-05-26
> **kc1di said:**
> the first one just update the package list on your machine.

When you sign in are you selection lubuntu from the drop down menu?

No, I kept using lxde. I forgot to switch. After trying lubuntu, it looks to be resolved. I'll have to try rebooting a few times to make sure, but this might have taken care of the problem.

BLewis,

Yea, my experience is rather limited. I do know what sudo is, just wasn't sure what apt-get was. Even if this problem has been resolved, I am still considering doing a new install of lubuntu. I'll try removing sudo apt-get purge nautilus.

---

### Post by kc1di on 2012-05-27
Glad to here it's working for you :)
enjoy

---

