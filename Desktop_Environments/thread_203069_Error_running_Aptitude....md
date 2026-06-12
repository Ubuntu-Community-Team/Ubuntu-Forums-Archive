---
title: "Error running Aptitude..."
date: 2006-06-24
forum: Desktop Environments
---

### Post by momaw27 on 2006-06-24
I woke up this morning and found that I'm having an error while trying to run Aptitude...
[B]
E: Syntax error /etc/apt/apt.conf.d/10periodic:4: Extra junk at end of file[/B]

Anybody know what this means?

Thanks!

Beau

---

### Post by aysiu on 2006-06-24
Well, [it doesn't turn up anything in Google](http://www.google.com/search?hl=en&q=E%3A+Syntax+error+%2Fetc%2Fapt%2Fapt.conf.d%2F10periodic%3A4%3A+Extra+junk+at+end+of+file&btnG=Google+Search).

Can you post the output of ```
cat /etc/apt/apt.conf.d/10periodic
```? Mine looks like this: ```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "1";
```

---

### Post by momaw27 on 2006-06-24
Here is my output... very strange...

[B]search domain_not_set.invalid
nameserver 192.168.0.1
nameserver 192.168.0.1[/B]

What the heck?

---

### Post by aysiu on 2006-06-24
Since mine dosn't seem to be specific to my particular installation, try using mine instead.

```
sudo cp /etc/apt/apt.conf.d/10periodic /etc/apt/apt.conf.d/10periodic.old
gksudo gedit /etc/apt/apt.conf.d/10periodic
``` Paste in my code and save. ```
sudo aptitude update
```

---

### Post by momaw27 on 2006-06-24
First, thank you for your help!

Here's what happens when I try what you have suggested...

[B]Could not open the file /etc/apt/apt.conf.d/10periodic using the Unicode (UTF-8) character coding.
Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again.
[/B]

I then tried to go in the back door using Nautilus but I can't even open the file 10periodic... what's going on?

Beau

---

### Post by aysiu on 2006-06-24
How about this?

Alt-F2 ```
gksudo nautilus
``` and then navigating to /etc/apt/apt.conf.d/

---

### Post by momaw27 on 2006-06-24
Thank you VERY much!

That did it!

I'm up and running again...

Beau

---

### Post by ifokkema on 2006-06-24
[QUOTE=momaw27]Thank you VERY much!

That did it!

I'm up and running again...

Beau[/QUOTE]
Good that you got it to work, BUT... that doesn't explain how this got messed up for starters. Your contents look like that was from /etc/resolv.conf, but the error messages suggest other contents following that. I would suggest you run a fsck on your drive, to rule out drive corruption!

---

