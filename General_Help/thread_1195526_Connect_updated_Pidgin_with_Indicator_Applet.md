---
title: "Connect updated Pidgin with Indicator Applet"
date: 2009-06-23
forum: General Help
---

### Post by guitarMan666 on 2009-06-23
I have installed the latest version of Pidgin from GetDeb.  I understand that that version of Pidgin isn't officially supported, but Yahoo! capability dropped out of the version currently available in Jaunty (at least for myself and two friends).

I miss the notifications with new messages being displayed by the Indicator Applet.  Is there a way to make the new version talk to the Indicator Applet?

This is not important, but thank you all anyway for your help.

---

### Post by Sentience on 2009-06-23
How do you install the latest unsupported version.

---

### Post by H2SO_four on 2009-06-23
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

this worked for me

---

### Post by Sentience on 2009-06-23
I followed those instructions. It says its up to date. Was that the newest supported version or is there another way to get the latest unsupported version?

---

### Post by redmk2 on 2009-06-23
> ...Yahoo! capability dropped out of the version currently available in Jaunty...

Yahoo! availability is throughly discussed [_**here**_]("http://ubuntuforums.org/showthread.php?t=1191064").

---

### Post by guitarMan666 on 2009-06-23
> **Sentience said:**
> I followed those instructions. It says its up to date. Was that the newest supported version or is there another way to get the latest unsupported version?

That is likely the newest supported version.  The way to get the most up-to-date is to go to [www.getdeb.net](www.getdeb.net) and download 2.5.7 from there.  It is only available for Hardy and Jaunty.

---

### Post by redmk2 on 2009-06-23
It won't be supported until 2.6.  Read the thread.

---

### Post by guitarMan666 on 2009-06-23
> **redmk2 said:**
> Yahoo! availability is throughly discussed [_**here**_]("http://ubuntuforums.org/showthread.php?t=1191064").

I can see that.  However, if they were rolling outages then upgrading to the latest Pidgin would not have affected it and we would be unable to connect.  My friend who is still using Intrepid can't connect either.

More to the point of this post is that now that I have the new version can I make it talk to the Indicator Applet?

---

### Post by guitarMan666 on 2009-06-23
I did.  I saw that.  Still, the point of this thread is to make the new version talk to the Indicator Applet.  Can that be done?

---

### Post by redmk2 on 2009-06-23
There are references to the official Yahoo! blog.  That explains what Yahoo! is really doing.  It is not rolling outages.  They are dropping older protocols when upgrading their servers.  Pidgin will (someday) be updated to v2.6 and be able to use these protocols.  But it is not done at this time.  

In short whatever you download it will not be compatable yet.

---

### Post by guitarMan666 on 2009-06-23
> **redmk2 said:**
> There are references to the official Yahoo! blog.  That explains what Yahoo! is really doing.  It is not rolling outages.  They are dropping older protocols when upgrading their servers.  Pidgin will (someday) be updated to v2.6 and be able to use these protocols.  But it is not done at this time.  

In short whatever you download it will not be compatable yet.

Ok.  Yes, I get it.  I read that whole thread.  Not until 2.6.  However this doesn't change that 2.5.7 is the version I have now and Yahoo or no Yahoo I would like to know if it can be connected to Ubuntu's indicator applet and if so how that's all.

---

### Post by redmk2 on 2009-06-23
> ...I would like to know if it can be connected to Ubuntu's indicator applet and if so how...

Maybe [**_this_**]("http://ubuntuforums.org/showthread.php?t=1073424") will help.

---

### Post by guitarMan666 on 2009-06-24
Thanks, that does.

---

### Post by m2orris on 2009-06-24
try this:

1) In Synaptic Package Manager:
   install pidgin-libnotify

2) In Pidgin:
    select: Tools --> Plugins
       check: Libnotify Popups
       click: Close

3) Restart Pidgin

---

