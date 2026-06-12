---
title: "Getting php mail function to work- wanting to use postfix"
date: 2007-01-06
forum: Desktop Environments
---

### Post by icedcheese on 2007-01-06
Hi There

I was wondering if someone can help me.  I am a php programmer and run a local server on Ubuntu which enables me to run and test my web applications quickly.

Unfortunately the only thing not working is my php mail function.  I need this to work so that I can test out web forms going to an email etc.  I want to send an email to my external email address.

I was wondering if someone was able to provide me with an idots guide to getting it to work.  So far from spending hours browsing the web, I have concluded the following:

There seem to be 2 aspects to getting this working, the php.ini file and configuring sendmail or postfix.

By the looks of things, most people recommend using postfix instead of sendmail.

So far I have only really managed to install postfix and tell it that the server is an Internet site.

I managed to get it working this way under 6.06, but that may have been all luck!  Is anyone able to provide assistance in the matter?

Thank you
Michael

---

### Post by icedcheese on 2007-01-06
Problem solved!  I Installed exim4 and this did the trick!

---

### Post by McTwist on 2008-06-07
How did you do it? I tried it, but it wont work for me!

---

### Post by rem on 2008-06-09
> How did you do it? I tried it, but it wont work for me! 

yeah, i installed exim4 and additional packages and that removed my postfix but still no go... can you share any eventual extra steps you did?

thanks!

---

