---
title: "Tor, privoxy, foxyproxy - browsing works, but not annonymously"
date: 2009-03-08
forum: General Help
---

### Post by svaens on 2009-03-08
Hi all, 

Sorry if this after all a duplicate type post. But i haven't really read the same problem as I have. So here I am. I hope someone can suggest a fix. 

I have setup tor and privoxy to be used with foxyproxy in firefox. 
If this was working, it would have seemed like a very simple installation and setup;

1. I AM able to browse
2. when i stop the privoxy daemon (when foxyproxy is configured to use tor), i CANNOT browse (good! proof it is going through privoxy). 
3. when I stop the TOR daemon, I can still browse. BAD!!! That seems to mean that privoxy is bypassing TOR!! !?  Why?

Proof that I have no TOR enabled was already seen by bringing up the site:
[https://torcheck.xenobite.eu/](https://torcheck.xenobite.eu/)
which told me so. Turning off the TOR application, and having browsing still possible gave me proof. 

I'm going to read and play about with the configurations now,

but just in case i'm unsuccessful in working this out, if anyone has any ideas and experience with this problem, and knows exactly what I need to change, please let me know!

thanks

---

### Post by Dr Small on 2009-03-08
Did you follow this guide?
[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

Most notably with your problem, you forgot to configure Privoxy to use Tor. Try adding this line to /etc/privoxy/config:
```
forward-socks4a / localhost:9050 .
```

Restart Privoxy and try again :)

---

### Post by svaens on 2009-03-08
hi, thanks for the reply. 

You definitely had it right. 

Actually, the fault was mine, but it was because i mindlessly copy and pasted that particular line from a website in which there was no space where a space was required. 
Just figured that out and was going to paste my success, but you beat me to it! Thanks all the same! Works fine now.

p.s. i also need help with the Ubuntu forum! How do I set this to solved...?

---

### Post by Dr Small on 2009-03-08
The [SOLVED] option has been disable due to problems with the forum. Hopefully it will be back someday. Glad you got the problem fixed :)

---

### Post by hyperdude111 on 2009-03-08
Download OperaTor it is a windows app but it works perfectley in wine not configuration needed.

---

