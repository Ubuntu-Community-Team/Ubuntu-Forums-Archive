---
title: "How to install this app without root access?"
date: 2010-07-26
forum: Desktop Environments
---

### Post by lavadisco on 2010-07-26
So, my company has a new web-based VPN client. I go to a specified URL, log in, and then a Java widget starts and tries to install some stuff. I get this screen:

[IMG]http://mohodisco.com/screenshot.png[/IMG]

It's asking me for my root password. I know how to set the root password, but I want to avoid that and use sudo instead. But as you can see from the image, the install is initiated in such a way as to prevent me from doing anything but entering my root password. And apparently my sudo/admin password isn't the same as my root password, because it doesn't work. And I can't access the executable from any other way. Is logging in as root briefly my only option here?

---

### Post by wojox on 2010-07-26
> **lavadisco said:**
>  Is logging in as root briefly my only option here?

Go for it. What is your company running as a web server? How about you as well?

---

### Post by wojox on 2010-07-26
You could also try

# Right-click on the file.
# Go to Properties. And then the 'Permissions' tab.
# Check 'Allow executing file as program'. Say OK.
# Now double-click on the file the way you open any other file.
# That should install the application by running the script in .sh file.
# Follow the prompts (if any) while installation which should look the same as they look in Windows.
# That's it. You are all set

---

### Post by lavadisco on 2010-07-26
> **wojox said:**
> You could also try

# Right-click on the file.
# Go to Properties. And then the 'Permissions' tab.
# Check 'Allow executing file as program'. Say OK.
# Now double-click on the file the way you open any other file.
# That should install the application by running the script in .sh file.
# Follow the prompts (if any) while installation which should look the same as they look in Windows.
# That's it. You are all set

Thanks, but there is no file for me to right-click on. When I log in at the URL, the page goes out and grabs the file remotely and executes it. Viewing the page source does not reveal the executable URL either.

---

### Post by wojox on 2010-07-26
Try this [RootSudo]("https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account")

---

### Post by lavadisco on 2010-07-26
That worked, thanks. I disabled it afterwards.

---

### Post by wojox on 2010-07-27
> **lavadisco said:**
> That worked, thanks. I disabled it afterwards.

Good job. Your Welcome.

---

