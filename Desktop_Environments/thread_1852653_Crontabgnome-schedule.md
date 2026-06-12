---
title: "Crontab/gnome-schedule"
date: 2011-09-30
forum: Desktop Environments
---

### Post by h4x0rjd420 on 2011-09-30
All want to do is have gnome-schedule or something run "sudo killall apt-get" every hour. Will someone please tell me how to do this?

---

### Post by judoka9999 on 2011-09-30
This is almost surely not what you actually want... but, as root, put a file in /etc/cron.d/ called killapt

The contents of the file should be:
0 * * * * root killall apt-get

Then restart cron (not sure if this is necessary, but it won't hurt.)
sudo /etc/init.d/cron restart

This will show an error on 11.04, but will work. I specify this method because it should be more portable than:
sudo service cron restart

This will run "killall apt-get" as root every hour on the hour. If you want to run at 15 minutes past the hour, change the 0 to 15, etc.

Again, this seems to me like a bad idea, but good luck!

---

### Post by WasMeHere on 2011-09-30
Here are some good examples how-to set up crontab. I have used these tutorials to set up a talking clock.

[_Cron and Crontab usage and examples_]("http://www.pantz.org/software/cron/croninfo.html")
[_Linux Crontab: 15 Awesome Cron Job Examples_]("http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/")

---

### Post by h4x0rjd420 on 2011-10-01
I run ubuntu 10.10, and about every hour or so apt-get uses all of my cpu in the background, the only way I've been able to find to stop it is "sudo killall apt-get" about every hour or so. 

I'm not totally sure what you mean by or the purpose of saving that as a file, I downloaded gnome-schedule and have no idea how to use the cron in a terminal, I've been trying to figure it out for weeks to solve this problem specifically. 

Thank you for the help though, hopefully it does what I need it to lol. =)

---

### Post by WasMeHere on 2011-10-01
> **judoka9999 said:**
> ... as root, put a file in /etc/cron.d/ called killapt

The contents of the file should be:
[FONT="Courier New"]0 * * * * root killall apt-get[/FONT]
...

*cron* looks into the directory */etc/cron.d/* every minute and reads the files (simple text files with one line for each action).

But there is a reason why *apt-ge*t is busy. You must allow it to download and install at least the security updates! The recommended updates download and install improvements of different programs, so they are also good to get. I don't know, but it is possible that apt-get is started by cron. In that case you can look for a file in /etc/cron.d/ with a line of numbers and stars in the beginning and the name 'apt-get' plus some other text at the end.

Normally *apt-get* will work silently in the background. It should not bother you. Usually it will add an icon on the bottom panel, showing that there are updates waiting to be installed.

---

### Post by Krytarik on 2011-10-01
+1 to what *judoka9999* said:
> **judoka9999 said:**
> Again, this seems to me like a bad idea, but good luck!
Why? Imagine this: 'apt-get' is automically killed right when it does upgrades, or when you run it yourself, to install or remove packages. Do you get the point, why letting kill 'apt-get' automatically, no matter what it does right then, is one of the worst ideas you can have!?

So, better figure out why it's recurringly using up all your CPU, as *Olle Wiklund* kinda pointed out.

Greetings.

---

