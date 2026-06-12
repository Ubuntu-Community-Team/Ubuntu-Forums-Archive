---
title: "Mail Server on Ubuntu Desktop 8.10?"
date: 2009-04-10
forum: General Help
---

### Post by zjagannatha on 2009-04-10
Ok. So basically, I am a college student and out college is soon to change their servers. In the past they used pine for mail. They are switching to google, which is good, but it restricts use a lot. Basically, it prevents sending excecutable files, which isn't too good.

I would like to set up a small mail server for myself on my PC so that I can send and recieve things that gmail won't let me. Is it possible to set up a command line based e-mail server for myself on my computer?

I'm running Ubuntu 8.10 Desktop Edition btw.

---

### Post by maheshasolkar on 2009-04-10
If it is just moving files, why not set up an FTP server or a Web server. You can upload/download files from there.

---

### Post by zjagannatha on 2009-04-10
I suppose I was looking for some way to send files to and recieve from professors. Giving them access to my computer I don't think would be too good.

Mainly some way to set up pine so that it would send and recieve e-mails and store them onto my computer.

---

### Post by fireworld2406 on 2009-04-10
Two popular MTAs for Linux/Unix (and available from the Ubuntu repos) are Sendmail and Postfix.

---

### Post by maheshasolkar on 2009-04-10
I came across this How-to on setting up a mail server on Ubuntu. I haven't used it, although it looks very thorough. May be it will give you some pointers:

  [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by fieroboom on 2009-04-10
The biggest caveat for a mail server is being extremely careful that you're not an open relay, because your entire campus could get blacklisted for your server sending out spam that you're not aware of. Also, DNS records can be a huge pain to set up and get verified. Externally, most ISP servers will block & ban your server for having an incorrect/missing reverse pointer for your mail server.

If you're not very familiar with those topics, I would strongly suggest finding a cheap hosting plan with email that doesn't restrict your sending & receiving capabilities. I have my own colocated server, and I refuse to run a mail server on it. I run about 10 websites, a DNS server, ampache, and a multitude of other servers & services, but my email is hosted elsewhere, because to me, it's just more trouble than it's even worth.
:D
-Paul

---

### Post by wubrgamer on 2009-04-10
> **fieroboom said:**
> The biggest caveat for a mail server is being extremely careful that you're not an open relay, because your entire campus could get blacklisted for your server sending out spam that you're not aware of. Also, DNS records can be a huge pain to set up and get verified. Externally, most ISP servers will block & ban your server for having an incorrect/missing reverse pointer for your mail server.

If you're not very familiar with those topics, I would strongly suggest finding a cheap hosting plan with email that doesn't restrict your sending & receiving capabilities. I have my own colocated server, and I refuse to run a mail server on it. I run about 10 websites, a DNS server, ampache, and a multitude of other servers & services, but my email is hosted elsewhere, because to me, it's just more trouble than it's even worth.
:D
-Paul

Where do you have your email hosted?

---

### Post by fieroboom on 2009-04-10
> **wubrgamer said:**
> Where do you have your email hosted?

I use a company called ISOMEDIA that's based in Seattle, WA, but only because I used to work there. If you've got the time, then do a google search for "email hosting" and read the breakdown of the different plans, then you can make an informed decision on what you want. If you don't have the time to do that, I'd probably have to recommend something like [TierraNet](https://www.tierra.net/products/email/index), at $4.95/month. Of course, shoot them an email and verify they provide all the services you want.
Also, if you happen to have your own website, most of them are capable of running your top-level domain as a mail server for you. For example, I own grandesigns.net, and I just made a DNS record that points mail.grandesigns.net to the people doing my mail hosting. This way I still control my domain, but all email to it gets routed through ISOMEDIA's servers.
Hope that makes sense to you and helps in your decision!
:D
-Paul

EDIT:
Wanted to also say that I just ran across [this site](http://www.yourdomainhost.com), and it seems to do exactly what I was referring to with your own domain.

---

### Post by zjagannatha on 2009-04-11
I suppose I don't exactly fit the stereotype for the broke college student, but I'm close, so I don't really want to pay for something. I'd rather figure out a way to do it for myself since it would be helpful experience in the future.

I think I might ask one of the CS professors to set up a folder on the Math/CS ftp server that is free for everyone to access. That might be a good way to transfer homework and executables to and from professors. Although you'd need to teach the students how to use an ftp client.

---

### Post by wubrgamer on 2009-04-11
> **zjagannatha said:**
> I suppose I don't exactly fit the stereotype for the broke college student, but I'm close, so I don't really want to pay for something. I'd rather figure out a way to do it for myself since it would be helpful experience in the future.

I think I might ask one of the CS professors to set up a folder on the Math/CS ftp server that is free for everyone to access. That might be a good way to transfer homework and executables to and from professors. Although you'd need to teach the students how to use an ftp client.

Shouldn't the CS kids be smart enough to use an FTP client?

That's just a basic computer proficiency thing!

---

### Post by apmcd47 on 2009-04-11
> **zjagannatha said:**
> Ok. So basically, I am a college student and out college is soon to change their servers. In the past they used pine for mail. They are switching to google, which is good, but it restricts use a lot. Basically, it prevents sending excecutable files, which isn't too good.

I would like to set up a small mail server for myself on my PC so that I can send and recieve things that gmail won't let me. Is it possible to set up a command line based e-mail server for myself on my computer?

I'm running Ubuntu 8.10 Desktop Edition btw.

Our MS-Exchange Server blocks executables. The workaround? Zip'em. Won't this work with Google mail?

Andrew

---

### Post by zjagannatha on 2009-04-11
> **wubrgamer said:**
> Shouldn't the CS kids be smart enough to use an FTP client?

That's just a basic computer proficiency thing!

Ideally, yes. But at my university some students take the intro to computer science just because it fulfills the math requirement. I was in the class with some people last semester that **shouldn't** have been taking the class. I think all the majors would either know how to use one already, or be able to figure it out pretty quickly.

---

### Post by zjagannatha on 2009-04-11
> **apmcd47 said:**
> Our MS-Exchange Server blocks executables. The workaround? Zip'em. Won't this work with Google mail?

Andrew

It didn't work in the past. I haven't tried it recently, but I'm pretty sure they wouldn't change it. Guess I'll have to try it again.

---

### Post by fieroboom on 2009-04-11
> **apmcd47 said:**
> Our MS-Exchange Server blocks executables. The workaround? Zip'em. Won't this work with Google mail?

Andrew

A lot of mail servers scan inside zip files for possible threats. However, many can't scan a rar file, and since it's a format that's easy to manipulate in both Windows (WinRar) and Linux (rar, unrar, unrar-free), it's a good choice.
:D
-Paul

---

### Post by zjagannatha on 2009-04-12
That's a good idea. I rechecked the google mail servers though and they'll let me send a unix executable file. I'm not sure about a *.exe* file though. And I can't easily check that because I don't use windows any more. I suppose it's time to head back to the computer labs.

---

