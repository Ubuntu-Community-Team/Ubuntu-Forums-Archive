---
title: "Self Inflicted boot prolem :S"
date: 2009-06-13
forum: General Help
---

### Post by Ifrgtmyname on 2009-06-13
Hi,

Recently, in a moment of frustration due to a string of permission denied errors, I changed all the permissions on my computer so that the etc, bin and home files etc. were all owned by my account, ifrgtmyname as opposed to root or no owner (i'm not sure which) previously. Now when I boot, the loading bar splash screen thing shows but the login screen doesn't. Instead I get this screen: 

[IMG]http://img8.imageshack.us/img8/2525/img0323v.jpg[/IMG]

I am pretty sure the error message was called by the permission changes. If anyone could tell me how to fix this I would appreciate it greatly :)

-Thanks

---

### Post by McNils on 2009-06-13
You shouldn't let your frustration kill your installation...

What did really you do exactly?

---

### Post by Ifrgtmyname on 2009-06-13
I know that now!

I logged in as root, selected all the files under 'computer' and changed my account to the owner

---

### Post by Ifrgtmyname on 2009-06-13
Anyone got any ideas, maybe I can fix it using a live CD?

---

### Post by Ifrgtmyname on 2009-06-14
Still looking for help, thanks

---

### Post by gradinaruvasile on 2009-06-14
Now thats a mess. Why did u do that?

can u log in from here?
with you account name and password?

---

### Post by wanderingtux on 2009-06-14
worst case scenario, you can use the live CD. but i dont see a reason why you should not be able to log in from the login screen here with your username.

---

### Post by Ifrgtmyname on 2009-06-14
When I try to log in from there I get this message:

[IMG]http://img7.imageshack.us/img7/1441/img0332l.jpg[/IMG]

Thanks again for the help all, I really apreciate it

---

### Post by gradinaruvasile on 2009-06-14
Reinstall and never mess with permissions again.

---

### Post by Ifrgtmyname on 2009-06-14
Do I have to? Can I not somehow change the permissions back using a live CD?

---

### Post by gradinaruvasile on 2009-06-14
> **Ifrgtmyname said:**
> Do I have to? Can I not somehow change the permissions back using a live CD?
Maybe possible but do u know who was the owner of every file and folder?

---

### Post by Ifrgtmyname on 2009-06-14
> **gradinaruvasile said:**
> Maybe possible but do u know who was the owner of every file and folder?

Not exactly but it can't get much worse! So the live CD will let me change permissions?

---

### Post by nandemonai on 2009-06-14
Even if you did know the owner and permissions for all the files on the system it would take you days to try and fix it. Your best bet is to boot with the live CD, backup any data you need and reinstall.

This is exactly the reason the root account is disable and warnings are posted all over the forums about not messing with things via root or sudo unless you know exactly what you're doing.

Unfortunately you've had to find this out the hard way.

---

### Post by Ifrgtmyname on 2009-06-14
Will do, thanks for the help everyone. Luckily I did not like jaunty one bit anyway!

---

