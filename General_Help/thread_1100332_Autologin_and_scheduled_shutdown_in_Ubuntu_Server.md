---
title: "Autologin and scheduled shutdown in Ubuntu Server"
date: 2009-03-19
forum: General Help
---

### Post by mha2908 on 2009-03-19
Hi, I've got a brand new PC, which I use as server. It is headless, and I've got my BIOS set up to automatically boot at 8 AM, and since the PC is put away, and has no attached keyboard or mouse, i DO NOT want to type in my credentials. Instead I want it to autologin my user, or at least login using another PC. I was able to do this with the Desktop Edition using XDMCP, but I do n't know how to do it in the Server Edition. I can't access it with SSH as long as its not logged in.

And there's one more thing I want to do: Schedule an automatic shutdown at 24 PM. How do I do that?

Some might ask: Why shut it down? Then you don't have to login!
But, since it is placed in my home, I am paying for electricity, and those 8 hours is just a waste. I've also set up the BIOS to accept the WakeOnLan-signal, so I can turn it on between 24PM and 8AM if I want to.

---

### Post by Brucevdk on 2009-04-18
> **mha2908 said:**
> And there's one more thing I want to do: Schedule an automatic shutdown at 24 PM. How do I do that?

I'm not quite sure why you'd want to auto-login but to schedule an automatic shutdown just add a cron job (sudo crontab -e). Here's an example:

```

# +------------------- minute (0 - 59)
# |  +---------------- hour (0 - 23)
# |  |  +------------- day of month (1 - 31)
# |  |  |  +---------- month (1 - 12)
# |  |  |  |  +------- day of week (0 - 7) (Sunday=0 or 7)
# |  |  |  |  |  +---- command
# |  |  |  |  |  |
  0  0  *  *  *  shutdown -h now

```

This will shutdown the machine at 00:00 every day.

If you have a convincing argument for auto-login I'd be willing to look up how to achieve this.

---

### Post by lisati on 2009-04-18
I'm not sure either why you'd not want to enter your credentials on a server - it weakens its security to not need it.

---

### Post by Brucevdk on 2009-04-18
Ouch mha2908, you cross-posted this exact question multiple times. I'm sorry but that's just not cool (to put it lightly) since now I've wasted precious minutes I could have spent answering truly unanswered posts. Please don't do this as it is also clearly against the [Ubuntu Forums Policy](http://ubuntuforums.org/index.php?page=policy) (search for "cross post").

A list of the duplicate threads:

[LIST]
[*]Cross posted in [Server Platforms](http://ubuntuforums.org/showthread.php?t=1100319)
[*]Cross posted in [Absolute Beginner Talk](http://ubuntuforums.org/showthread.php?t=1100343)
[/LIST]

---

### Post by juancarlospaco on 2009-04-18
sudo apt-get install openssh-server

ssh youruser@serversip

[B]Dont install X on a Server, dont auto-login on a Server, 
use Webmin, you can Shutdown/Reboot from Webmin.[/B]

---

### Post by KaRiToR on 2009-04-19
I was wondering if you managed to do what you described on your first post. I have an itx computer with ubuntu 8.10 Server that i use as a mediacenter server & bitorrent manager without any mouse, keyboard or monitor attached. 

I need to do the same thing. On windows i managed to do this with pc autoshutdown programing the days & hours i wanted my pc to shutdown automatically.

Thanks.

---

### Post by cwilhoit on 2010-06-01
I am using Ubuntu server as a text based workstation to connect to an AS400 using tn5250. In order to keep things as simple as possible, I would like the PC to log in automatically and start tn5250 automatically. The tn5250 part is done via the users .bashrc file but not the auto login. I am using this in a distribution center and it keeps the users from doing nothing but their designated work on the PC. I used Ubuntu server because I could not get the latest version of Ubuntu desktop to boot in text mode other than the recovery mode which is not acceptable.

---

### Post by cwilhoit on 2010-06-01
I had the PC login automatically by adding the below line to /etc/init/tty1.conf and replacing USERNAME with the actual username:

[INDENT]   	 	 	 	 	 	  [FONT=ARial, sans-serif]exec /bin/login -f USERNAME < /dev/tty1 > /dev/tty1 2>&1[/FONT]


[/INDENT][FONT=ARial, sans-serif]If you happen to type it incorrectly then do a "Ctrl-Alt-F2" to get to a differt tty screen and make your corrections.
[/FONT]

---

