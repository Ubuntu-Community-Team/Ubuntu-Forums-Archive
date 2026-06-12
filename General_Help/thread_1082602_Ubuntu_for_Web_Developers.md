---
title: "Ubuntu for Web Developers"
date: 2009-02-28
forum: General Help
---

### Post by mdgrech on 2009-02-28
Hey guys I'm creating a Ubuntu for Web Developers distro, what applications or features do you guys feel are absolute most for the distro?  

You can check out the project home page at [http://mijio.com]("http://mijio.com")

---

### Post by satish_j on 2009-02-28
Apache,PHP and MySql...
cant imagine  a day not working on any of these applications

---

### Post by mdgrech on 2009-02-28
got those on there already... as well Ruby on Rails and Django.  By the way whats the general feel for RoR around here?  A lot of Django loyalists I would predict?

---

### Post by HotelUnderSeige on 2009-02-28
eh "for web developers" that mean i can implement php into programs?

---

### Post by theApokalypsis on 2009-02-28
php of course as satish says :)


ok I do a lot of web dev. below are some of the things I find useful


Some Editors

Bluefish (from unstable SVN would be best)
Aptana Studio (Eclipse) (with RadRails, etc)
Mono .NET Develop 2
Ftp app


Features

Mono 2 (.NET)
Mono apache module
Webrick/Mongel ROR servers (EDIT: forgot they are GEMs i believe)
Mysql & management



Also perhaps a variety of browsers/backends. i.e. Presto (Opera), Epiphany/Midori (Webitkit), Firefox, perhaps Konqueror...


lastly perhaps a Virtual Machine app would be cool as well. Specifically for web developers wanting to test out IE7/8.

VMware Server 2 or perhaps Virtualbox OSE.

---

### Post by Thirtysixway on 2009-02-28
along with theothers posted, multiple browsers (maybe wine with IE installed?).  Cross-browser testing is a bit of an issue when developing on Ubuntu because of IE.

Some nice text editors with ftp and syntax highlighting like gedit.
how about lighttpd on an alternate port than apache?  lighttpd is neat :)


for your support forum you should look at [http://esotalk.com](http://esotalk.com)

---

### Post by mdgrech on 2009-02-28
Good recommendation for esotalk.  I agree with having multiple browsers.  I especially like epiphany.  I could install ie4Linux on the distro however I must admit I don't like the idea of putting anything microsoft on the distro.  

I've debated using netbeans, which is a nice ide with a wide variety of uses, however I must admit that I rather despise bulky ide's and have just used a simple text-editor.

---

### Post by lykwydchykyn on 2009-02-28
Have a look at Quanta plus.  Admittedly, I mostly write PHP in EMACS or KATE, but Quanta always looked slick.

How about having a source versioning system (like maybe subversion) set up and ready to use?

EDIT: ok, I see you have subversion and git already on there.  my bad.

---

### Post by satish_j on 2009-02-28
> **Thirtysixway said:**
>  Cross-browser testing is a bit of an issue when developing on Ubuntu because of IE.


totally agree with u on that...
mdgrech,I also support your view not to add MS stuff into the distro,but since the thread title is 'for Web Developers',you should atleast consider support for IE as the only stuff of Microsoft,which,as you said,can be acheived through IE4Linux.

---

### Post by bobdobbs on 2009-02-28
Quanta Plus is pretty slick alright.
I've been using it for years.

I've looked at other web dev tools and environment, but I always come back to quanta.

I'm more productive in quanta than I am in any version of dreamweaver.

Caveat - Quanta, like any tool, is incomplete, and still has some very annoying bugs.
(It's the best annoying, buggy tool that there is)

So, I would say that including quanta is neccessary.

---

### Post by Xiong Chiamiov on 2009-02-28
Right now, I use Komodo Edit with vim bindings, but I'm looking very hard at Eric.  If you're doing python work, ipython is a must.

Personally, I prefer lighttpd or nginx as webservers over apache, but if it's just for development, it doesn't matter too much.

---

### Post by mdgrech on 2009-02-28
Regarding servers so far its Apache2, and webrick which got bundled in with Ruby on Rails.  I have Monodevelop, and python idle, as well as sqlite on my own desktop.  I was considering adding them to the distro.  

Ideally I would like to get the distro rather light out of the box, and focus on adding additional unique features.  For example, has anyone used project deploy?  It let you easily create templates for web projects, ie blank html and css files.  I was think it might be nice to include something like that.

---

### Post by andrew.46 on 2009-04-17
Hi theApokalypsis,

> **theApokalypsis said:**
> Bluefish (from unstable SVN would be best)

Can I ask what feature you are especially after that the svn Bluefish holds rather than the release version 1.0.7? I ask mainly because I am using the release version :-).

Andrew

---

### Post by theApokalypsis on 2009-04-17
> **andrew.46 said:**
> Hi theApokalypsis,



Can I ask what feature you are especially after that the svn Bluefish holds rather than the release version 1.0.7? I ask mainly because I am using the release version :-).

Andrew


The most noticeable things from svn I was finding was a lot of bug fixes and issues, also (does stable have this) much better js/css etc intellisense. There are probably more things I am missing but I always like to get the most latest package myself lol, but the version is from 1.07 -> 1.3.3

---

### Post by bobdobbs on 2009-04-17
> **Xiong Chiamiov said:**
> Right now, I use Komodo Edit with vim bindings, but I'm looking very hard at Eric.  If you're doing python work, ipython is a must.

Personally, I prefer lighttpd or nginx as webservers over apache, but if it's just for development, it doesn't matter too much.

Just curious -
How come ?

I've only ever used apache, so I'm curious about the advantages of other servers.

---

