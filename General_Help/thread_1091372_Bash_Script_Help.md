---
title: "Bash Script Help"
date: 2009-03-09
forum: General Help
---

### Post by jamefarm on 2009-03-09
Hello all!  I have free wifi in my apartment complex, but it has this annoying access page that you have to log in to (and the username and password is printed on that page) which the first time is no problem to log into, but my wireless card isn't really well supported in Linux (works well enough though) and sometimes the connection drops and I have to log back in (the wifi automatically redirects you to this page regardless of where you were going) Is there any way I can get a script to check to see if the internet is available and if not then to log in automatically?  This way I can download large files (updates etc...) without having to monitor the status of my connection.

---

### Post by davmac on 2009-03-09
When you say "get a script" do you mean download one? Probably not, but with a bit of effort you should be able to write one.

I found this guide really useful for getting started

[http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html](http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html)

From the way you describe it it sounds like every time the connection gets dropped you are automatically directed to a specific login page.

You should be able to use curl (sudo apt-get install curl) to access any web page, and then if it returns the gateway page, should be able to identify that you need to log back in, pull the details from the page and log in with them.

Is this the sort of thing you mean?

If so, happy to help you work through writing this script.

Regards,

Dave MacLeod
[http://twitter.com/davmac](http://twitter.com/davmac)

---

### Post by jamefarm on 2009-03-09
By 'get a script to' I mean, can I make a script that will do that.  You've correctly figured out exactly what I need.  Curl huh?  I'll look into it.  Thanks for the link as well, I've always wanted to learn how to write bash scripts.  Any help or suggestions you could offer would be great.  Thanks alot!!!

---

### Post by Slim Odds on 2009-03-09
> **jamefarm said:**
> Thanks for the link as well, I've always wanted to learn how to write bash scripts.  Any help or suggestions you could offer would be great.  Thanks alot!!!

I always recommend this: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

