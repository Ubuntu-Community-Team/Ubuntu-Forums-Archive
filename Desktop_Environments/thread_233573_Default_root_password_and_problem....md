---
title: "Default root password? and problem..."
date: 2006-08-10
forum: Desktop Environments
---

### Post by Kl0wN on 2006-08-10
Hi. I'm trying to change my screen resoulution from 640x478 or something, to 1024x768. Last time I was here they said to instasll drivers, so, this post is about the root password. When in terminal on the desktop directory (/home/kl0wn/Desktop), I type su and it shows:

Password:

Then, it freezes...It doesnt actually freeze, it just wont let me type anything on the terminal. If i did happen to get it to work, what would it be?

---

### Post by ardchoille on 2006-08-10
> **Kl0wN said:**
> Hi. I'm trying to change my screen resoulution from 640x478 or something, to 1024x768. Last time I was here they said to instasll drivers, so, this post is about the root password. When in terminal on the desktop directory (/home/kl0wn/Desktop), I type su and it shows:

Password:

Then, it freezes...It doesnt actually freeze, it just wont let me type anything on the terminal. If i did happen to get it to work, what would it be?

You should use sudo instead of su. Read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

This may help your resolution problem: [http://wiki.ubuntu.com/FixVideoResolutionHowto](http://wiki.ubuntu.com/FixVideoResolutionHowto)

---

### Post by deeek on 2006-08-10
> **Kl0wN said:**
> Hi. I'm trying to change my screen resoulution from 640x478 or something, to 1024x768. Last time I was here they said to instasll drivers, so, this post is about the root password. When in terminal on the desktop directory (/home/kl0wn/Desktop), I type su and it shows:

Password:

Then, it freezes...It doesnt actually freeze, it just wont let me type anything on the terminal. If i did happen to get it to work, what would it be?
If you want to run commands with root privledges you should use the sudo command infront of it like this:

```

sudo vi /tmp/t

```

The password is your password that you created when you installed the system.

But, if you really want to log in as root you issue this command:

```

sudo su

```

For more info, see this page:

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by maniacmusician on 2006-08-10
> **Kl0wN said:**
> Hi. I'm trying to change my screen resoulution from 640x478 or something, to 1024x768. Last time I was here they said to instasll drivers, so, this post is about the root password. When in terminal on the desktop directory (/home/kl0wn/Desktop), I type su and it shows:

Password:

Then, it freezes...It doesnt actually freeze, it just wont let me type anything on the terminal. If i did happen to get it to work, what would it be?

common misconception; it doesn't freeze. it's still reading whatever you're typing, it just doesnt show it for security reasons. when you use sudo, and it asks for password, just type in the password as it is, and hit enter. At least I am assuming this is your problem. i've never heard of root things not working.

---

### Post by Kl0wN on 2006-08-10
Ummm I ran the auto detection, and now its asking me 

Enter the amount of memory you want by your video card...

I have a 256 MB Radeon x700 ATI AGP

---

### Post by MrHorus on 2006-08-10
> **Kl0wN said:**
> 
Enter the amount of memory you want by your video card...

I have a 256 MB Radeon x700 ATI AGP

If it's asking how much RAM is on your video card then I think you answered your own question mate... :)

---

