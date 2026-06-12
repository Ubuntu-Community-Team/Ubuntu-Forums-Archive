---
title: "Can't open user settings as root"
date: 2010-12-15
forum: Desktop Environments
---

### Post by elperrillo on 2010-12-15
I was trying to upgrade from Ubuntu 10.04 to 10.10 and the upgrade froze half way. (I have to force the upgrade because the message to upgrade never came out in "update manager") and I had to reboot the computer and issue some commands to reconfigure everything. When the computer finally let me into gnome. I logged in as root, however when I click on ***SYSTEM -> ADMINISTRATION -> USERS AND GROUPS.*** it open but it stays shadow and Ubuntu's equivalent to the windows hourglass remains forever. 

Can an anybody help me? 

Thanks is advance.

---

### Post by elperrillo on 2010-12-15
I also noticed I don't have sound as root, I cannot even slide the sound volume. I am sure there is other stuff too. I have another user and everything works as that user.

---

### Post by elperrillo on 2010-12-15
CAN SOMEBODY HELP ME FOR THE LOVE OF GOD!!!!!!!!

I am in a really desperate situation.

---

### Post by mcduck on 2010-12-16
Have you tried as normal user? You shouldn't even be logging into desktop as root in the first place, and many of the tools are configured to fit with Ubuntu's security model (root disabled, and normal user handling admin tasks through sudo & policyKit). Trying to use them directly as root could very well be the reason for your problems.

---

### Post by elperrillo on 2010-12-16
Yes everything seems to work fine as a regular user. Exept I can no longer drag video files into AVIDEMUX. What you are saying was certainly not the case in previous Ubuntu versions is this something new for 10.10 Maverick Meerkat? I don't understand the logic behind it, if you are root you are root, there is not a higher user than that you are supposed to have access to everything.

---

### Post by mcduck on 2010-12-16
no, there is no higher user. But there shouldn't be a root user either (at least not one that's being used like a normal user account), and definitely not using graphical applications. Which is why many of the graphical admin tools are made to be run by a normal user account, using PolicyKit to handle the permissions for whatever admin task they need to do. Such tools will not work if you try to run them as root, simply because they were never meant to be used that way.

I know older versions of many of these tools were simply executed as root (through sudo) but using PolicyKit will provide better security than running the whole tool as root. You'll definitely see more and more of the admin tools being converted to work this way in upcoming Ubuntu releases.

---

### Post by elperrillo on 2010-12-16
Do you have any idea as to why I can no longer drag and drop video files into Avidemux like I used to with 10.04? and how to fix it?

---

### Post by mcduck on 2010-12-17
Sorry, I have no idea what could cause that. 

You might want to start a separate thread about that, people who might know the answer are much more likely to find your question that way. :)

---

