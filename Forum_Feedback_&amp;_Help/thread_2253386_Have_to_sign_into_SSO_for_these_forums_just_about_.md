---
title: "Have to sign into SSO for these forums just about every time"
date: 2014-11-19
forum: Forum Feedback &amp; Help
---

### Post by defaria on 2014-11-19
Just about every time I come here I'm not logged in. I have to go through the procedure of logging in with my SSO thing or whatever and a few days later when I come back here I have to log in again. What gives? How do I make these forums remember me?

---

### Post by slickymaster on 2014-11-19
*Moved to the ***Forum Feedback & Help*** sub-forum*

---

### Post by vasa1 on 2014-11-19
> **defaria said:**
> Just about every time I come here I'm not logged in. I have to go through the procedure of logging in with my SSO thing or whatever and a few days later when I come back here I have to log in again. What gives? How do I make these forums remember me?
I understand that the forums remember us by means of a cookie that has a life about ~24 hours.

---

### Post by ventrical on 2014-11-19
I noticed with unity-desktop .. yes ..about 24 hours but I have had longer periods with gnome3 and xubuntu. (using firefox of course). It's been over 48 hours for my xubuntu vivid install. I am going ot log out. boot up the xubuntu install and I'll brb! :)lol


bwaaahahahahaha ... :)   I only had one machine going at the time so it logged me off globally on all machines .. :)lol

---

### Post by ventrical on 2014-11-19
This bug/option is only exclusive to ubuntuforums and not the wikis or launchpad. It may be that forum admins had tightened the screws because of security problem last year.

 No bother here ..really.

---

### Post by Elfy on 2014-11-19
It is absolutely nothing whatsover to do with us. 

It is and always has been Canonical IS.

> It's been over 48 hours for my xubuntu vivid install. Not relevant. All that is relevant is coming back to the forum within a 24 hour period. I get logged out only when I get a browser update or I physically log myself out.

---

### Post by pqwoerituytrueiwoq on 2014-11-19
i usually have to login back in after i login from a different device

---

### Post by ventrical on 2014-11-19
> **Elfy said:**
> It is absolutely nothing whatsover to do with us. 

It is and always has been Canonical IS.


Thanks for clear and succinct answer.

Regards..

---

### Post by CantankRus on 2014-11-20
ip address seems to affect this too.
ie my ip address is dynamic and when it changes I need to log in again.

---

### Post by coffeecat on 2014-11-20
> **CantankRus said:**
> ip address seems to affect this too.
ie my ip address is dynamic and when it changes I need to log in again.

This has come up before and is nothing to do with the 24-hour login cookie, nor is it specific to ubuntuforums. If your IP address changes you will be logged out. It is a feature, I would guess a security related feature, built into vbulletin forum software and phpBB software. This forum is built on vbulletin. I haven't tested it against other bulletin board softwares but I wouldn't be surprised if it is true in at least some of them as well.

---

### Post by CantankRus on 2014-11-20
> **coffeecat said:**
> This has come up before and is nothing to do with the 24-hour login cookie, nor is it specific to ubuntuforums. If your IP address changes you will be logged out. It is a feature, I would guess a security related feature, built into vbulletin forum software and phpBB software. This forum is built on vbulletin. I haven't tested it against other bulletin board softwares but I wouldn't be surprised if it is true in at least some of them as well.
Never said it did....was an explanation to the OP as to a way you can become logged out.

---

### Post by coffeecat on 2014-11-20
I&#8217;m going to close this now because the same question comes up again and again and the answer is always the same. I re-iterate the answer and also give some background and associated information.

[list]

[*]The vbulletin remember me function is not compatible with SSO login, which itself was introduced for security reasons. 

[*]A workaround was applied by Canonical IS (sysadmins) so that logged in members are kept logged in for 24 hours if they have not deliberately logged out. This is not under forum admin control. We will see if this time can be extended, but don&#8217;t hold your breath.

[*]To ensure that your forum login is as convenient as possible, do not log out of your Ubuntu One account. Login will then require only 2 mouse-clicks from starting at the forum home page &#8211; or 3 if you need to click on the continue (redirect) button. Redirect is rarely needed in my experience. 

[*]Please spare a thought for the forum admins, who have to endure both a short session logout time for admin control panel and a more tedious login procedure to adminCP, both for security reasons.
[/list]

Other matters which have arisen in this thread are:

[list]
[*]Session timeout is nothing to do with the Linux desktop or even operating system that you are using. The timeout will be the same. It is a cookie thing.
[*]If you move to a different device, you will have to log in again, of course. It is a cookie thing.
[*]If your external IP changes, you will probably be logged out. This appears to be a feature of vbulletin, and other forum software.
[/list]

---

