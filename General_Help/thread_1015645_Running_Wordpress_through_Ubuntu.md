---
title: "Running Wordpress through Ubuntu"
date: 2008-12-19
forum: General Help
---

### Post by IKhider on 2008-12-19
Greetings fellow Ubuntu users, 

I purchased a url name and web server space. I would like to post and edit a wordpress blog theme on that space. I am not clear as to how to do that. I installed Wordpress via synaptic package manager, but do not see any additional options. Research yielded that I need to use LAMP, an acronym for various packages. When I try to download the acronym packages via terminal--I get messages that I already have said packages. When I examined the date of research info, I realized a lot of it is dated--from 2005/2006. Even on official documentation. I bet it is easier now than ever to post Wordpress blogs on webhosting spaces using Ubuntu. Question is, how do I do it?

---

### Post by hyper_ch on 2008-12-19
so you rent some websapce on some server or do you rent an own server or do you want to try to run wordpress from your home computer?

---

### Post by reality1011 on 2008-12-19
> **IKhider said:**
> Greetings fellow Ubuntu users, 

I purchased a url name and web server space. I would like to post and edit a wordpress blog theme on that space. I am not clear as to how to do that. I installed Wordpress via synaptic package manager, but do not see any additional options. Research yielded that I need to use LAMP, an acronym for various packages. When I try to download the acronym packages via terminal--I get messages that I already have said packages. When I examined the date of research info, I realized a lot of it is dated--from 2005/2006. Even on official documentation. I bet it is easier now than ever to post Wordpress blogs on webhosting spaces using Ubuntu. Question is, how do I do it?


LAMP stands for Linux, Apache, Mysql, Php  If you already have them installed great... try going to [http://localhost:80](http://localhost:80) in the web browser of that computer to see if apache is running...

These 4 components are the main components of most webservers.  It sounds like you are looking to host your own domain and run a wordpress blog.  This is not difficult but it takes time to make sure everything is configured and working.  Something that you will need to research.  I have done this myself so I can attest to the easy and hard conflicts to resolve but there is too much to cover here.

Here are some basic details  ==>
you need to:

- get your domain to point to your computer, probably using some type of dynamic dns service

- configure your router to allow the incoming requests for the website, some ISP's block port 80 ( mine does and you have to get a port forwarding service to bypass it)

- install wordpress - do it from their website, the install is much newer and updated

- I think that mostly all... any questions

---

### Post by ianhaycox on 2008-12-19
If you have purchased web space then I would suggest running Wordpress on your hosting providers server is much easier.

Some hosting providers have an option on the control panel to install/activate Wordpress. Take that option if it exists, otherwise follow [http://codex.wordpress.org/Installing_WordPress](http://codex.wordpress.org/Installing_WordPress).

Basically you need to create a mySQL database on the host then upload the files via ftp.

---

### Post by LinuxPS2 on 2008-12-19
From his original post it seems like he just wants to edit a wordpress theme that is currently on the web server he is renting, not sure how one would edit it but you should be able to download the theme from your web server, edit the files, then upload them to your rented server... correct me if I'm wrong in assuming what exactly it is that you are trying to do.

---

### Post by IKhider on 2008-12-19
Wow, lots of great replies! Thanks all!

I am renting space from a company and a server. Tera-byte where they charge $25.00 a year. 

So I have filezilla as an FTP client, a template I like and a bunch of content I want to get cracking on. The site is dedicated to covering emerging electronic and experimental music where I post a new show about every two weeks. The previous site with Yahoo! web hosting I had got hacked or butchered by spam--not sure which, just couldn't access it. So this time I want to have back-up material off line as well. 

So I installed Wordpress via Synaptic, have a template on my desktop screen, filezilla...and I think that's it? I will try some posted suggestions and see what to do next. 

Thanks and please keep the suggestions coming!

-I-

---

### Post by IKhider on 2008-12-19
Hello Fellow Ubuntu Users, 

I looked up said information and now understand that I have to install Wordpress on the servers. I was hoping I could layout and write all the information I need on the computer and then post it on line. When I read up on MySql--I realized that it is something I would like to avoid. Is it possible to simply compose and post wordpress as I go along?

That way all my info is safely backed up on my various hard drives where it is a bit harder to get in and hack. Or do you think there is no way to get around MySql when it comes to Wordpress? Maybe go with a different program?

-I-

---

