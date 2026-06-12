---
title: "Can I install KDE too??"
date: 2010-08-11
forum: Desktop Environments
---

### Post by krishnandu.sarkar on 2010-08-11
Hey friends, I'm using ubuntu and now I want to try Kubuntu too. But I don't want another OS. Is it possible to install KDE DE too?? Won't it create any problem??

Please suggest anything other that I should keep in mind while performing this task.

---

### Post by linux18 on 2010-08-11
sudo apt-get install kubuntu-desktop

perfectly safe

---

### Post by krishnandu.sarkar on 2010-08-11
Thanks. How will I choose which DE to use?? I think there is a option at login screen, but I've enable auto-login. And I don't want to remove that feature. Is there any other ways out??

And one more question....Does KDE apps gets installed with KDE DE too?? I mean with the above command?? If yes, I don't want to see KDE apps in GNOME and vice-versa. Is this done automatically?? Or I have to do something to achieve that??

---

### Post by linux18 on 2010-08-11
you will have a choice at login, you can setup auto login after it is installed, yes some kde apps will come with kubuntu-desktop and will mix with gnome. you can limit this by only installing th DE not the whole kubuntu, unfortunately the command for that eludes me at the moment.

---

### Post by krishnandu.sarkar on 2010-08-11
It's ok..!! Thanks a lot..!! :)

---

### Post by LightningCrash on 2010-08-11
> **krishnandu.sarkar said:**
> It's ok..!! Thanks a lot..!! :)

If you install kubuntu-desktop you **might** end up with kdm and gdm running side by side.
If you find yourself unable to log in you might have to remove kdm from a command prompt and reboot.

---

### Post by krishnandu.sarkar on 2010-08-11
And for uninstalling it sudo apt-get remove/purge kubuntu-desktop right??

---

### Post by krishnandu.sarkar on 2010-08-11
> **LightningCrash said:**
> If you install kubuntu-desktop you **might** end up with kdm and gdm running side by side.
If you find yourself unable to log in you might have to remove kdm from a command prompt and reboot.


lol...thanks for the warning..!!

---

### Post by linux18 on 2010-08-11
you can't uninstall by purging the kubuntu-desktop as it is a meta package. I should make a script for  intergrating multiple DE's and removing them, I'll put it on my list of things to do.

---

### Post by krishnandu.sarkar on 2010-08-11
Thanks...But I got the package names by googing it out.

---

### Post by nick_goodfate on 2010-08-11
Hi , i ve installed ubuntu with /home in separate partition. I want to ask if i can install kubuntu in another separate partition sharing the same home partition with ubuntu(without formating /home)?

---

### Post by linux18 on 2010-08-11
> **nick_goodfate said:**
> Hi , i ve installed ubuntu with /home in separate partition. I want to ask if i can install kubuntu in another separate partition sharing the same home partition with ubuntu(without formating /home)?yes  you can

---

