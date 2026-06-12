---
title: "Failed to Fetch error"
date: 2012-02-21
forum: Desktop Environments
---

### Post by mikesedgley on 2012-02-21
Hello, I am new to Ubuntu and have been trying to run updates and have been getting failed to fetch errors.  I have also tried to install firefox as well with the same problem.  This is the error I get only for all my updates:

Failed to fetch [http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_15.0.874.121-r109964_i386.deb](http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_15.0.874.121-r109964_i386.deb)
  404  Not Found [IP: 74.125.157.136 80]

Can anyone tell what this means and how to fix this?

---

### Post by younglemon on 2012-02-22
I too am experiencing a similar issue. When I start the Ubuntu software manager I am prompted to repair broken packages and when I attempt this it fails with a message it 'failed to fetch' and asks if I'd like to attempt repairs again.

---

### Post by youngunix on 2012-02-22
You can try the following:

1. find the repo links that can't be fetch and delete/replace them in "sources.list"
2. ```
sudo apt-get --fix-broken update
```

For more options regarding "apt-get" try: ```
man apt-get
``` or look [here]("http://http://linux.die.net/man/8/apt-get").

---

### Post by younglemon on 2012-02-22
Thank you.  Yes I did try this and others commands I found throughout the forum.  Unfortunately these commands yield an internet connection error that advises me to check my internet connection.  Unfortunately, its not my internet  connection.  I can get to the internet as I have the ip and routing info set, however, I changed it to DHCP after I began having the fetch issue.  I have tried various forms of apt-get including -f, update and --fix-missing.  All of which yeild some sort of error and do not lete me fix the broken system package.

---

### Post by roelforg on 2012-02-22
> **younglemon said:**
> Thank you.  Yes I did try this and others commands I found throughout the forum.  Unfortunately these commands yield an internet connection error that advises me to check my internet connection.  Unfortunately, its not my internet  connection.  I can get to the internet as I have the ip and routing info set, however, I changed it to DHCP after I began having the fetch issue.  I have tried various forms of apt-get including -f, update and --fix-missing.  All of which yeild some sort of error and do not lete me fix the broken system package.
Try pinging the servers;
try running:
```

sudo apt-get update

```

---

### Post by younglemon on 2012-02-23
Thank you, yes I did try the 'Update' option too and am still unable to reach the Ubuntu Software Manager. I have sort of an odd setup. I am running 64 server with the desktop interface (overlay if you will). I see that I am running 12.04, so I'm sure that this is the reason for my 'Fetch' error. I wonder if I could try to revert back to 11.10..? I probably could but, I'm not sure that I want to, I'd much rather get 12.04 working. I would be grateful for any thoughts anyone has on the subject, thank you in advance. Otherwise, I may post this again to the server side and see if I come up with anything.  
 
mikesedley, have you had any luck with your 'fetch' error?  I'm sure your error is a bit different and one of the previous suggestions would probably work beautifully.

---

