---
title: "Pidgin Help"
date: 2009-06-14
forum: General Help
---

### Post by thundaraptor on 2009-06-14
Hi, I have a few alias accounts on the gmail server, ie  [email]xxx@global.thunderbird.edu[/email] and [email]xxx@archimedesglobal.com[/email] both of which are using the gmail server.  how do I load these bad boys into the pidgin chat client?  i tried the basics using my login names and pwd but didn't quite workout.  thanks  TR

---

### Post by briguy47 on 2009-06-14
> **thundaraptor said:**
> Hi, I have a few alias accounts on the gmail server, ie  [EMAIL="xxx@global.thunderbird.edu"]xxx@global.thunderbird.edu[/EMAIL] and [EMAIL="xxx@archimedesglobal.com"]xxx@archimedesglobal.com[/EMAIL] both of which are using the gmail server.  how do I load these bad boys into the pidgin chat client?  i tried the basics using my login names and pwd but didn't quite workout.  thanks  TR


Can you give a little more detail about "the basics" you tried?

The normal process would be:

1. Go to Account ---> Manage Accounts

2. Click Add and select Google Talk in the Protocol drop down menu.

3. Then just enter your username (without the "@gmail.com") and password.

4. Then click Add and you should be good to go.


If that is what you did, then there might be a different way, but that usually works.  

Let me know if you have any questions.  :D

---

### Post by thundaraptor on 2009-06-14
didn't work.  you steps 1-4 are exactly the steps that I already tried.  there must be some way to get the chat client to understand that I am not a direct "@gmail.com" kind of account similiar to the login configurations for an email client.  cheers TR

---

### Post by b.a.w on 2009-06-14
Did you set up those accounts through POP in gmail? Are you trying to use your accounts as chat accounts in pidgin? I don't believe this is possibly. They are registered in gmail underneath your main account not as an official account that has access to the google talk chat server. Only your main account is a valid for chat.

---

### Post by briguy47 on 2009-06-14
I'm wondering if there is a way to directly setup a Pidgin XMPP account that would bypass the gmail presets.  I'm betting there is a mixup in how pidgin is reporting the username, since it's expecting [email]xxxxx@gmail.com[/email].

I'm gonna look into it and report back. :)

---

### Post by briguy47 on 2009-06-14
Did you try puting your domain ([EMAIL="xxx@global.thunderbird.edu"]global.thunderbird.edu[/EMAIL] and [EMAIL="xxx@archimedesglobal.com"]archimedesglobal.com)[/EMAIL] as the domain and setting the Connect Server (Advanced Tab) to talk.google.com?  I just read this --> [article <--]("http://www.google.com/support/a/bin/answer.py?answer=49147") for setting up pidgin for google-talk and it mentions changing the domain if you use Google-Apps for Your Domain.  Not sure if that's your situation or not, and I can't try it myself because I don't have emaill addresses outside of gmail, but I think it's probably worth a shot. :)

---

### Post by thundaraptor on 2009-06-15
> **briguy47 said:**
> Did you try puting your domain ([EMAIL="xxx@global.thunderbird.edu"]global.thunderbird.edu[/EMAIL] and [EMAIL="xxx@archimedesglobal.com"]archimedesglobal.com)[/EMAIL] as the domain and setting the Connect Server (Advanced Tab) to talk.google.com?  I just read this --> [article <--]("http://www.google.com/support/a/bin/answer.py?answer=49147") for setting up pidgin for google-talk and it mentions changing the domain if you use Google-Apps for Your Domain.  Not sure if that's your situation or not, and I can't try it myself because I don't have emaill addresses outside of gmail, but I think it's probably worth a shot. :)

BG, that was dope.  worked like a charm and now have multiple accounts stored in my pidgin.  super useful and i salute you!!!

---

### Post by thundaraptor on 2009-06-15
> **briguy47 said:**
> Did you try puting your domain ([EMAIL="xxx@global.thunderbird.edu"]global.thunderbird.edu[/EMAIL] and [EMAIL="xxx@archimedesglobal.com"]archimedesglobal.com)[/EMAIL] as the domain and setting the Connect Server (Advanced Tab) to talk.google.com?  I just read this --> [article <--]("http://www.google.com/support/a/bin/answer.py?answer=49147") for setting up pidgin for google-talk and it mentions changing the domain if you use Google-Apps for Your Domain.  Not sure if that's your situation or not, and I can't try it myself because I don't have emaill addresses outside of gmail, but I think it's probably worth a shot. :)



It also makes me wonder, why didn't my google searching uncover this same article?  Because i was searching for "alias google chat" type stuff and not "domain google talk"... but if google is so smart, aren't these words related to the same subject?

---

### Post by briguy47 on 2009-06-15
haha.  Seriously.  Ahh the mysteries of google...

---

