---
title: "How do I forward mail with Postfix?"
date: 2009-02-26
forum: General Help
---

### Post by linuxNewb on 2009-02-26
I have my Ubuntu server all set up except for one last thing -- email forwarding. I've been googling for about an hour now to no avail.

What I need is simple (lol) -- to tell Postfix to forward email sent to username to [email]username@gmail.com[/email].

All of the tutorials are for multiple users, and redirecting to other mail servers, etc. I am the only user on this server. I just want it to forward mail sent to [email]username@mydomain.com[/email] to my gmail account. That's it. I tried adding:

username: [email]username@gmail.com[/email]

to the aliases file, but that didn't work. Am I missing something? Please tell me that there is an easy way to do this. Thanks in advance.

---

### Post by albinootje on 2009-02-26
> **linuxNewb said:**
> I tried adding:

username: [email]username@gmail.com[/email]

to the aliases file, but that didn't work.
You're using "plain" postfix with system users ? Not with LDAP or mysql ?

After adding that you ran the following ?
```

sudo newaliases
sudo postfix reload

```

You can also use a .forward in the home directory of your user with 
just one line having your gmail email address.

---

### Post by albinootje on 2009-02-26
And just to be sure, which alias file did you edit ?
Please check the output of the following :
```

postconf -n|grep -i alias

```

(I'm testing the above command in a VPS, so I'm not sure whether sudo is needed for this specific command or not.)

---

### Post by linuxNewb on 2009-02-26
Thanks for your quick response.

Yes the output matches the aliases file that I am editing:

/etc/aliases

I did run # sudo newaliases
but not # sudo postfix reload

After running the 'reload' command it still isn't forwarding the email.

I also tried removing the alias from /etc/aliases and instead using the .forward file as you suggested, but it still isn't forwarding.

I can send an email to my gmail account using 'mail' on the command line. I am assuming that if that works the forwarding should work.

---

### Post by linuxNewb on 2009-02-26
I just lookined at my logs, and it says the emails are indeed forwarding to my gmail account, but they arent making it for some reason. Maybe they are being rejected.

This problem might be outside of the scope of this forum. Thank you for you help to this point.

---

### Post by linuxNewb on 2009-02-26
It works!!!

This might save someone alot of time and frustration...

When you test Postfix forwarding, don't send the test email from the destination address!!!

I am forwarding mail on mydomain.com to my gmail account, but I was testing my setup by sending an email from my gmail account (and expecting it to come back as a forward). THAT WON'T WORK. Test by sending mail from another account.

---

### Post by albinootje on 2009-02-26
> **linuxNewb said:**
> It works!!!

Great that you got it working, well done :)
>  I am forwarding mail on mydomain.com to my gmail account, but I was testing my setup by sending an email from my gmail account (and expecting it to come back as a forward). THAT WON'T WORK. Test by sending mail from another account.

I suspect this is a Gmail only "feature". I've seen behavior like this before with Gmail. 
There's imho no reason why this type of test normally would not work in a well working forwarding setup.

---

