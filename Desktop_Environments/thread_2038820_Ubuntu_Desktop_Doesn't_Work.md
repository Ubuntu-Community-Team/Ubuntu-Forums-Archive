---
title: "Ubuntu Desktop Doesn't Work"
date: 2012-08-07
forum: Desktop Environments
---

### Post by Yunito on 2012-08-07
When I start Ubuntu, the desktop doesn't load. I think is a Compiz's Problem, but I don't know it.

Thanks

---

### Post by peryang on 2012-08-07
You can run it live off the disc, meaning you can boot the OS without installing it, so you can try it and see if you like it.
Ubuntu is a basic OS that lets you surf the web and check your email.

---

### Post by Yunito on 2012-08-07
I have Ubuntu Installed, yesterday all okey. But Today, Ubuntu's Desktop doesn't load. I can run Console no more.

---

### Post by irv on 2012-08-07
You are not giving much information here. So I am guessing it might be a boot entry in your grub. You could try running a boot repair.
See: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
Just follow the instructions on this webpage.

---

### Post by Yunito on 2012-08-07
But Ubuntu works okey. If I entry in recovery mode and uninstall and Reinstall Compiz I can enter in Ubuntu, but This trick I must do ever when I want enter in Ubuntu.

---

### Post by irv on 2012-08-07
> **Yunito said:**
> But Ubuntu works okey. If I entry in recovery mode and uninstall and Reinstall Compiz I can enter in Ubuntu, but This trick I must do ever when I want enter in Ubuntu.

Try running in 2D not 3D to see if it boots that way. 3D uses Compiz where 2D uses Metacity.

---

### Post by Yunito on 2012-08-07
Anyway, I can't switch it, However I have Radeon HD 5870, I think It can run 3D Effects.

---

### Post by irv on 2012-08-07
> **Yunito said:**
> Anyway, I can't switch it, However I have Radeon HD 5870, I think It can run 3D Effects.

Why can't you switch? When you startup and get to the login screen click on the Ubuntu logo and select 2D.
I know your video care can run 3D, all I was doing was to see if it will boot in 2D to see if it is the Compiz causing the problem. I don't think it is?

---

### Post by Yunito on 2012-08-07
I can't see the login screen, When I start Ubuntu I only see my wallpaper.

---

### Post by irv on 2012-08-07
By the way, was this just a fresh install? And are you running Ubuntu along side Windows or just Ubuntu?

---

### Post by Yunito on 2012-08-07
I have dual boot with Windows, but I think the problem is Compiz because the problems began when I try to put 3D Effects with Compiz Manager.

---

### Post by irv on 2012-08-07
> **Yunito said:**
> I can't see the login screen, When I start Ubuntu I only see my wallpaper.

You need to set your user account to _**NOT**_ login automatically

---

### Post by Yunito on 2012-08-07
Okey, I have automatically login, for this reason I can't switch nothing, and automatically I see the wallpaper and nothing more

---

### Post by irv on 2012-08-07
> **Yunito said:**
> I have dual boot with Windows, but I think the problem is Compiz because the problems began when I try to put 3D Effects with Compiz Manager.

There is some problems with Compiz. Change the setting back to what there were and this should fix your problem.
What version of Ubuntu are your running. 11.xx or 12.04?

---

### Post by Yunito on 2012-08-07
I have Ubuntu 12.04. I upgraded yesterday.

---

### Post by irv on 2012-08-07
> **Yunito said:**
> I have Ubuntu 12.04. I upgraded yesterday.
Like I said, just change your compiz setting back to what there were and see if this fixes the problem.
There is a bug on this: [http://askubuntu.com/questions/127782/ubuntu-12-04-compiz-failure-computer-has-nothing-to-use]("http://askubuntu.com/questions/127782/ubuntu-12-04-compiz-failure-computer-has-nothing-to-use")

---

### Post by irv on 2012-08-07
There's also this bug.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/993189]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/993189")

---

### Post by Yunito on 2012-08-07
> **irv said:**
> Like I said, just change your compiz setting back to what there were and see if this fixes the problem.
There is a bug on this: [http://askubuntu.com/questions/127782/ubuntu-12-04-compiz-failure-computer-has-nothing-to-use](http://askubuntu.com/questions/127782/ubuntu-12-04-compiz-failure-computer-has-nothing-to-use)

Okey... I did it, and Now I cant do anything in Ubuntu, However I can run recovery Mode and run Terminal There.

---

### Post by irv on 2012-08-07
> **Yunito said:**
> Okey... I did it, and Now I cant do anything in Ubuntu, However I can run recovery Mode and run Terminal There.
Did you follow the instruction at:
[http://askubuntu.com/questions/127782/ubuntu-12-04-compiz-failure-computer-has-nothing-to-use]("http://askubuntu.com/questions/127782/ubuntu-12-04-compiz-failure-computer-has-nothing-to-use")

---

### Post by Yunito on 2012-08-07
> **irv said:**
> Did you follow the instruction at:
[http://askubuntu.com/questions/127782/ubuntu-12-04-compiz-failure-computer-has-nothing-to-use](http://askubuntu.com/questions/127782/ubuntu-12-04-compiz-failure-computer-has-nothing-to-use)

Yes, all instructions.

---

### Post by xycris on 2012-08-08
i strongly believe that you have a hardware problem yunito. it is not with ubuntu.

though your hardware maybe functioning well, it is poorly supported by the kernel to date.

here is some discussion: [http://askubuntu.com/questions/168216/ubuntu-12-04-does-not-boot-even-with-nomodeset](http://askubuntu.com/questions/168216/ubuntu-12-04-does-not-boot-even-with-nomodeset)

---

### Post by irv on 2012-08-08
Like you said you just did an upgrade a few days ago. What i would do is backup all your data then do a fresh install of Ubuntu. Also make a list of the apps you need to install. Believe me, it doesn't take that long and you will have a clean installed system. I did my system lest than a month ago. I got a new SSD and re-installed everything, and it only took part of a day and I was back running with a nice clean system. I am running pure Linux now no Windows and I don't even miss it.

---

### Post by Yunito on 2012-08-08
> **irv said:**
> Like you said you just did an upgrade a few days ago. What i would do is backup all your data then do a fresh install of Ubuntu. Also make a list of the apps you need to install. Believe me, it doesn't take that long and you will have a clean installed system. I did my system lest than a month ago. I got a new SSD and re-installed everything, and it only took part of a day and I was back running with a nice clean system. I am running pure Linux now no Windows and I don't even miss it.

Ah... Is your solution reinstall Ubuntu?

---

### Post by irv on 2012-08-08
> **Yunito said:**
> Ah... Is your solution reinstall Ubuntu?

Yes it is. Sometime I find it the easiest fix. But remember there is a bug that is not fixed yet so maybe this won't help either. But if you do this you will know if it is the bug or not.

---

### Post by Austin Texas on 2012-08-08
Here is how you can disable the automatic login:
boot your installation disk and edit  /etc/lightdm/lightdm.conf  on your hard drive.

Remove the text that makes automatic login happen. That text looks like:

[SeatDefaults]
autologin-user=<YOUR USER>
autologin-user-timeout=0
user-session=ubuntu
greeter-session=unity-greeter

Then you will get the login screen and click on the Ubuntu logo and select 2D, as irv advised.






also from a town on the Mississippi River...

---

