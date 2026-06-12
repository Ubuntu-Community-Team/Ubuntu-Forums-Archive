---
title: "Guest Addittions"
date: 2008-08-19
forum: Desktop Environments
---

### Post by zay1967 on 2008-08-19
hey everyone, I just installed my first Ubuntu OS, and I want to install the guest additions, but it does not start. Another thing is that the screen is not right: example: I tried to configure Evolution for email, and could not see the forward or previous buttons. Any ideas why this is happening.

---

### Post by wd5gnr on 2008-08-19
Since you mention Guest additions, you must be running in Virtual Box? You need to mount the Virtual Box iso as your CD ROM drive. It may autostart or you may have to run the Linux install program depending on a couple of factors.

What are you doing to install?

---

### Post by zay1967 on 2008-08-20
I inserted the cd, then chose the option to install Ubuntu (not demo). Once completed, I removed the disk, rebooted, then installed the updates. When I click to install the guest additions, nothing happens. I am also unable to see all the buttons and so from applications (forward, previous, etc).

---

### Post by coffeecat on 2008-08-20
Are you running Ubuntu in VirtualBox or not? Or any other virtualisation software? You need to state this clearly if you want help.

If you are running Ubuntu as a guest OS in VirtualBox, you can't install the guest additions with a simple click. You have to install certain developer tools first, mount the guest additions iso and then run a script. It's all explained in the VirtualBox manual.

If you are using another virtualisation software, I can't help you.

If you are not virtualising and you have installed Ubuntu directly to the hard disc of your computer, and you are running it off the hard disc, what do you mean by guest additions?

---

### Post by zay1967 on 2008-08-20
Oh Ok, I apologize for not explaining myself. I am running Ubuntu in Virtual box. My host is XP/ SP3. I will check put the manual and get back with you. What about the issue where I am unable to see all the tabs or buttons for any of the dialoge boxes.

---

### Post by coffeecat on 2008-08-20
No problem.

One hint. In the VirtualBox manual, where it says you need to install certain packages before running the guest additions shell installer (actually it says this in an earlier section under kernel modules - they make you jump about a bit), for gcc and make, select 'build-essential' for installation. You also need dkms. You also need the correct kernel header files but I seem to remember they were already installed. Best to check this.

As far as your hidden tabs and buttons are concerned, I don't know. Could it be that the screen resolution on your virtual Ubuntu is simply too small? Until you install the guest additions, you are quite limited in the size of guest window you can have. After you've got the guest additions installed, you can resize dynamically right up to full-screen.

However, this is my experience running virtualised Ubuntu in a MacOS host. Reading a few threads here, I get the impression that there may be issues when you use a Windows host that I am not seeing with MacOS. Maybe; maybe not.

But if you ever need to start another support thread, you might be better off posting in the Virtualization subforum. Don't worry that you missed this. If you ever find you've posted in the wrong subforum, you can always click on the 'report' button of your own post and request a moderator to move the thread for you.

---

### Post by zay1967 on 2008-08-21
Thanks Coffeecat. Actually I was able to install the additions by double clicking the exe and then running it in terminal mode. After doing that, I am still unable to see the buttons. The window moves, but not up enough for me to see the buttons. I went to full screen, no luck. I uninstalled virtual box, I am going to reinstall and see what happens.

---

