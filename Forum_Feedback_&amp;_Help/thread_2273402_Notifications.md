---
title: "Notifications"
date: 2015-04-13
forum: Forum Feedback &amp; Help
---

### Post by michi1983 on 2015-04-13
Hey guys,

is there a place in the settings of the forum (which I obviously haven't found yet) where I can set up notifications like:
When ever someone replies to a thread I am involved in (where I also left at least 1 comment) send me an E-Mail.

Or is the only way (at least that is what I have seen so far) to click on the top right section on "settings" and see if there is something new to my so called "subscribed" threads?

greetz

---

### Post by coffeecat on 2015-04-13
Settings link -> General settings (on the left) -> Default Thread Subscription Mode. Click on the drop-down to get the list of options. There are three for email. When you've selected your preference, click on the orange save changes button at the bottom.

It's worth exploring the various options available through the links on the left in the settings page. For example, again under General Settings, you can change the message editor interface if you wish. I find the standard editor more useful than the enhanced WYSIWYG one.

---

### Post by michi1983 on 2015-04-13
Oh man, thanks for your helping me pointing to the right direction ;) I have no clue why I haven't seen that option there.
Yeah you are right, I also have the standard editor activated. I will take a closer look to all these options there, thanks!

---

### Post by michi1983 on 2015-04-14
Hi coffeecat, 

sorry to bother you again but something seems to be wrong.
When I switched the **default thread subscription mode** to *instantly, using e-mail* yesterday and I got at least 2 replies on threads I am evolved in, I didn't get one e-mail.
Did I miss something?

---

### Post by bapoumba on 2015-04-14
Is the email you are checking the one linked to your account here ?

---

### Post by michi1983 on 2015-04-14
exactly bapoumba, it's the one linked to my account.

---

### Post by bapoumba on 2015-04-14
This is a gmail account here. Did you get the email for my reply above ? Mays be check the spam folder ?

---

### Post by michi1983 on 2015-04-14
nope, no e-mails at all :/ not from your 2 replies nor from the one thread reply I received a cpl of minutes before.
even checked the spam folder.

---

### Post by bapoumba on 2015-04-14
The email comes from [email]info@ubuntuforums.org[/email], could you please search for that from the web interface if you are using a client ? 
I also have sent a test email to your gmail address linked to this account here.

---

### Post by michi1983 on 2015-04-14
I just received your testmail.
I only use the browser when using Gmail.

edit:/ I received an e-mail at the 12th April when someone sent me a private message.
but it seems I don't get the e-mails when someone replies to a thread.

---

### Post by bapoumba on 2015-04-14
That is quite strange, let me have a look again :)

---

### Post by michi1983 on 2015-04-14
Thanks man, I'll hang on here and wait ;) If you need me to test/do something, let me know

---

### Post by michi1983 on 2015-04-14
Here are 2 screenshots of my settings, maybe I misconfigured something.

[ATTACH=CONFIG]261277[/ATTACH][ATTACH=CONFIG]261278[/ATTACH]

---

### Post by bapoumba on 2015-04-14
Sent an email with [email]info@ubuntuforums.org[/email] copied (in case you have filters that catch this email for some reason).
Edit : we can see your options from the admin panel, so yeah, I already checked you had ticked the right options ;)

---

### Post by coffeecat on 2015-04-14
> **michi1983 said:**
> When I switched the **default thread subscription mode** to *instantly, using e-mail* yesterday and I got at least 2 replies on threads I am evolved in, I didn't get one e-mail.

One thing to check - please see if you are subscribed to those threads. If I remember correctly, you were set to subscribe automatically to any thread you posted to before you changed your settings, but we won't need to investigate further if you aren't subscribed for some reason.

Go to a thread for which you did get replies but no email. Click on thread tools at the top right. If it offers "Subscribe to this thread" then you are not subscribed and won't get emails unless you subscribe. If it says "Unsubscribe from this thread" then obviously you are subscribed and we need to investigate.

---

### Post by bapoumba on 2015-04-14
Good point coffeecat :)

---

### Post by michi1983 on 2015-04-14
> **coffeecat said:**
> One thing to check - please see if you are subscribed to those threads. If I remember correctly, you were set to subscribe automatically to any thread you posted to before you changed your settings, but we won't need to investigate further if you aren't subscribed for some reason.

Go to a thread for which you did get replies but no email. Click on thread tools at the top right. If it offers "Subscribe to this thread" then you are not subscribed and won't get emails unless you subscribe. If it says "Unsubscribe from this thread" then obviously you are subscribed and we need to investigate.

I definitely am subscribed to the threads as I am for this one :)

[ATTACH=CONFIG]261279[/ATTACH][ATTACH=CONFIG]261280[/ATTACH]

---

### Post by bapoumba on 2015-04-14
OK, other than the subscription needing a script to run on the forums (and for you to wait it runs), I have not other idea.

---

### Post by coffeecat on 2015-04-14
@bapoumba, I was wondering that too.

@michi1983, how long has it been since you changed your subscription mode from ordinary subscribe to instant email? There are a number of cron jobs that have to run.

---

### Post by michi1983 on 2015-04-14
> **coffeecat said:**
> @bapoumba, I was wondering that too.

@michi1983, how long has it been since you changed your subscription mode from ordinary subscribe to instant email? There are a number of cron jobs that have to run.

Immediately after you told me how to do it in your first comment on my post yesterday

---

### Post by bapoumba on 2015-04-14
> **michi1983 said:**
> Immediately after you told me how to do it in your first comment on my post yesterday

Hmm, so it's been 24h, the script processing emails stuck in the queue runs every 10 mins.

---

### Post by coffeecat on 2015-04-14
I'll try setting mine to instant email for a time and see what happens - or not as the case may be. I've never, ever had email notification of subscribed threads so I don't know what the pattern is. I *think* what happens with instant email notification is that if you are offline and someone posts to a subscribed thread, you get an email. But if more posts are made to that thread while you are still offline, you don't get any further emails, the rationale being that you already have a notification for that thread and you'll see all the additional posts when you are next online. 

What interests me is what happens when someone posts to a subscribed thread when you are online. Do you get an email, or does the script pass you by because you are online? Hopefully, I'll find out.

---

### Post by bapoumba on 2015-04-14
Yes you do coffeecat. I receive instant email notification for threads/PMs and I do receive one email for each reply when I am online. I only receive the first reply when offline.

Opened a RT ticket with canonical IS BTW.

---

### Post by michi1983 on 2015-04-14
Thanks guys for helping to resolve this. I could try to change my e-mail address to my work e-mail to see if it is GMail related if you want me to?

---

### Post by bapoumba on 2015-04-14
> **michi1983 said:**
> Thanks guys for helping to resolve this. I could try to change my e-mail address to my work e-mail to see if it is GMail related if you want me to?

No, that wont be necessary. I use gmail, and you should be free to use any active email account. We already checked you are reading the correct email address :)

---

### Post by michi1983 on 2015-04-14
I am not sure if it **could** have something to do with it but way before this SSO Login stuff (which I still don't understand totally haha) I think I had an account here and I am quite sure I used my old e-mail address there. Maybe this is somehow still connected with it. Just a guess though

---

### Post by bapoumba on 2015-04-14
> **michi1983 said:**
> I am not sure if it **could** have something to do with it but way before this SSO Login stuff (which I still don't understand totally haha) I think I had an account here and I am quite sure I used my old e-mail address there. Maybe this is somehow still connected with it. Just a guess though

Well, you do log in here with the michi1983 account, you do have access to the email address listed in the michi1983 account, so you should receive the emails. What was your previous account ?

---

### Post by michi1983 on 2015-04-14
> **bapoumba said:**
> Well, you do log in here with the michi1983 account, you do have access to the email address listed in the michi1983 account, so you should receive the emails. What was your previous account ?

It was mlu17

---

### Post by bapoumba on 2015-04-14
> **michi1983 said:**
> It was mlu17

OK thanks. it's not been active since July, 19th, 2013 and not linked to any Ubuntu One account. I disabled it.

That may be it : [http://ubuntuforums.org/showthread.php?t=2230004](http://ubuntuforums.org/showthread.php?t=2230004)
gmail treats all emails with the same strings with or without dots as the same. Please see if you get my next test email to the address registered in mlu17.

---

### Post by michi1983 on 2015-04-14
I received it as well

---

### Post by bapoumba on 2015-04-14
> **michi1983 said:**
> I received it as well
OK thanks, I was ready to bet you would receive it..

---

### Post by michi1983 on 2015-04-14
I dunno who or what did the magic but I just received an e-mail which says that someone replied to a thread :) So I guess this thing is sorted and I can set it to solved? :)

---

### Post by bapoumba on 2015-04-14
Cool :)
Asked for the ticket to be closed, but there has been no activity on it in such a short time. My best guess is that for some reason it needed 24h or so for the notification be taken into account. Not sure why as my understanding is that instant notification are applied .. instantly ..

That is the second time I say an "Automagically Solved" thread marker is needed :)

---

### Post by michi1983 on 2015-04-14
hehe thanks again you two! have a nice day

---

### Post by coffeecat on 2015-04-14
I'm seeing a pattern. I changed my thread subscription mode from control panel only to instant email a few hours ago. Since then I've only had email notifications of threads I've subscribed to **after** changing my subscription mode. Threads that I subscribed to before changing this setting, I only see when I click on settings, not via email.

That sort of makes sense in a vbulletin type way. @michi1983, is it possible that the non-arrival of email notifications for you was all to do with old subscriptions?

Now that I've satisfied myself that email notification is working, I'm changing back. I don't want all that spam in my inbox! :wink:

---

### Post by michi1983 on 2015-04-14
Hey coffeecat, that makes totally sense now that you mention it ;)

---

### Post by bapoumba on 2015-04-14
Yep, thanks coffeecat :)
One additional detail to add to our own knowledge base.

---

### Post by coffeecat on 2015-04-15
Another little quirk that I've noticed since changing back to control panel notification in my profile from instant email notification, is that I'm still getting email notifications for those threads I auto-subscribed to during the period I had my profile set to email notification. Irritating but it makes sense. If you manually subscribe to a thread through thread tools, you get the option to choose which notification method you want. The database must be keeping a record of your subscription type for each thread you are subscribed to, rather than a global subscription type for each member.

---

### Post by michi1983 on 2015-04-15
Good to know :) Maybe we can write that down in some kind of "wiki" or a sticky post somewhere where subscriptions get explained so that there is no future confusion of new users? :)

---

### Post by bapoumba on 2015-04-15
Something like [http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656) and maybe edit this post : [http://ubuntuforums.org/showthread.php?t=726150&p=4537471#post4537471](http://ubuntuforums.org/showthread.php?t=726150&p=4537471#post4537471) ?

---

### Post by michi1983 on 2015-04-15
yeah, something like that :)

---

