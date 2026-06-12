---
title: "Email Accounts"
date: 2006-09-11
forum: Desktop Environments
---

### Post by pod25 on 2006-09-11
Not sure if this is the correct place for this.

I've got my server version up and running, got webmin and ispconfig all installed and running lovely.
I've setup my main account, web,ftp and email.
Web works perfect, ftp works perfect, but email does not.

My problem is checking my emails from another comp, I keep getting user name or password was refused ? or words to that effect.
I'm using outlook on a windows box to read emails.
I'm not even sure if i can receive emails 

Any suggestions ?

---

### Post by reclusivemonkey on 2006-09-11
> **pod25 said:**
> 
My problem is checking my emails from another comp, I keep getting user name or password was refused ? or words to that effect.
I'm using outlook on a windows box to read emails.
I'm not even sure if i can receive emails 

Any suggestions ?

What type of email have you set up?

---

### Post by pod25 on 2006-09-11
> **reclusivemonkey said:**
> What type of email have you set up?

I'm using Postfix, if thats what you mean.

---

### Post by reclusivemonkey on 2006-09-11
> **pod25 said:**
> I'm using Postfix, if thats what you mean.

I was hoping for more information. You've not given me enough to help. Are you talking about you default internel unix email, or some POP3 emails you have set up?

---

### Post by pod25 on 2006-09-12
> **reclusivemonkey said:**
> I was hoping for more information. You've not given me enough to help. Are you talking about you default internel unix email, or some POP3 emails you have set up?

Sorry, I have setup my main email account using ispconfig (so i assume pop3 ?).
I do not want to check my messages using the linux server box, i want to use my windows laptop, so i put my details into outlook, however when outlook tried to pull my messages i receive the error "user or password was rejected" 

example, i use [email]admin@somedomain.com[/email]  password="admin"  i then used those details in outlook, but without any luck.
Also when i setup my account in ispconfig my user name was, example : web1_admin.
I'm obviously doing something wrong, but have no idea what.

To add, is it nessasary to use ispconfig to create my email accounts, cos i would rather be able to just create my email accounts without the need of ispconfig.

---

### Post by pod25 on 2006-09-12
This is driving my crazy now.

What do I use for my login details in outlook express so i can pull my emails off the server ?

My server is reporting that pop3 and smtp are both running.

---

