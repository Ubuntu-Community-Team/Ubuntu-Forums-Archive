---
title: "Facebook authentication failure in Empathy."
date: 2010-05-19
forum: Desktop Environments
---

### Post by MechaMechanism on 2010-05-19
In Empathy, Facebook worked just fine but upon a recent restart of Empathy, I started to get an authentication error and I can no longer get Facebook chat to work.  My password has not changed.

---

### Post by kid1000002000 on 2010-05-19
had this problem.  try disabling facebook device authentication through their website.

---

### Post by monino on 2010-05-19
> **kid1000002000 said:**
> had this problem.  try disabling facebook device authentication through their website.

Where? i cant found it and i have the same problem.

thx

---

### Post by MechaMechanism on 2010-05-19
> **kid1000002000 said:**
> had this problem.  try disabling facebook device authentication through their website.Been looking all over for this device authentication thing and can't find it.

---

### Post by kid1000002000 on 2010-05-19
sorry for the wait- it was late last night.
Facebook > Account Settings > Account Security (change) >
Change "[B]Would you like to receive notifications for logins from new devices?" to NO.
That solved it for me.
[/B]

---

### Post by monino on 2010-05-19
> **kid1000002000 said:**
> sorry for the wait- it was late last night.
Facebook > Account Settings > Account Security (change) >
Change "[B]Would you like to receive notifications for logins from new devices?" to NO.
That solved it for me.
[/B]

thx i just change but not solved. i can log facebook with a jabber account but not with the specific facebook account in empathy

---

### Post by MechaMechanism on 2010-05-19
I filed a bug because that Facebook setting was already off and it did not work.  I did try setting to on and then back to off.  Thanks for your help anyway.

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/582993](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/582993)

---

### Post by monino on 2010-05-19
> **MechaMechanism said:**
> I filed a bug because that Facebook setting was already off and it did not work.  I did try setting to on and then back to off.  Thanks for your help anyway.

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/582993](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/582993)
oks thx

---

### Post by kid1000002000 on 2010-05-19
different issue then.
Have you tried to see if it works in pidgin?  That would tell whether the issue is universal or not.

---

### Post by monino on 2010-05-19
> **kid1000002000 said:**
> different issue then.
Have you tried to see if it works in pidgin?  That would tell whether the issue is universal or not.

With pidgin ok and with empathy configured as jabber account run ok too, the issue is if i configure with facebook account type.



sorry for my english.

---

### Post by kid1000002000 on 2010-05-19
Your english is almost perfect  :)
Definately a bug in empathy then.  Sometimes it takes a day after they update their software before it makes it into ubuntu updates (I assume you've tried running that?).  

The only other suggestion I have is to try installing the latest version  from empathy's website, rather than the one in the repositories.

---

### Post by monino on 2010-05-20
Always i have the last version ^^ this is one thing that i like it in linux, so easy to update all dependences and programs.

---

### Post by MechaMechanism on 2010-05-20
Well, this is weird.  Facebook chat in Empathy now works.  I just happened to look at the chat window and the authentication failure notice was gone.  Might have been a problem with Facebook who knows.

---

### Post by aggiemarine07 on 2010-05-22
logging out of facebook and logging back in (with the facebook username, not email) fixed the problem for me. 

Maybe it bases its log-in/authentication from a cookie that your browser stores? (i dont know enough about programming to back up that conclusion, its just a guess)

---

### Post by liutszho on 2010-05-24
> **aggiemarine07 said:**
> logging out of facebook and logging back in (with the facebook username, not email) fixed the problem for me. 

Maybe it bases its log-in/authentication from a cookie that your browser stores? (i dont know enough about programming to back up that conclusion, its just a guess)

me too!

great post, that solved it for me.

---

### Post by loldrup on 2010-10-08
I have just installed Maverick Meerkat release candidate. I can authenticate my Facebook account using Gwibber, but Empathy fails ("Disconnected - authentication failed"). I experienced the same on Lucid Lynx. I have followed this guide:

Facebook > Account Settings > Account Security (change) >
Change "Would you like to receive notifications for logins from new devices?" to NO.

but, I couldn't find this "Would you like to receive notifications for logins from new devices?" option.

Has any one else experienced this problem with Maverick Meerkat?

---

### Post by funkwurm on 2010-10-09
@loldrup for me the option is called "Get notified by SMS or email if a new computer or mobile device logs into your account." but that was already set to off.

What did it for me was logging out of Facebook in the browser I use (Chromium) and logging back in, making sure that I use just my username for login name, not my e-mail address (which they ask for).

This also worked for aggiemarine07 and liutszho apparently, so give it a try.

Why there would be a correlation between how you log into Facebook with your browser and Empathy is beyond me, but if it works I'm happy :)

---

### Post by zer010 on 2010-10-29
I'm having the same issue. I've tried logging into FB with my username, but still still no success. Maybe FB is now blocking 3rd party apps from accessing chat? I'm just guessing, but it sounds like something they would do.

---

### Post by georider on 2010-11-02
I had this issue until I actually visited the "username" page. For example, follow these steps.

- Set up Facebook account in Empathy with username "UserName"
- Try to connect with Empathy (Authentication Failed)
- Visit [http://facebook.com/UserName](http://facebook.com/UserName)
- Try to connect with Empathy (Success!)

If this workaround can be confirmed and duplicated I believe this would be a facebook issue.

Give it a shot, it cannot hurt!

HTH!

-georider

---

### Post by nlsthzn on 2010-11-03
> **aggiemarine07 said:**
> logging out of facebook and logging back in (with the facebook username, not email) fixed the problem for me. 

Maybe it bases its log-in/authentication from a cookie that your browser stores? (i dont know enough about programming to back up that conclusion, its just a guess)

Can verify that this worked for me in Maverick Meerkat :D

Neil

---

### Post by loldrup on 2010-11-06
> **monino said:**
> thx i just change but not solved. i can log facebook with a jabber account but not with the specific facebook account in empathy

I have tried all solutions suggested in this thread, including logging in [[COLOR="Blue"]using Jabber/XMPP[/COLOR]]("http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/") (using [email]myfacebookusername@chat.facebook.com[/email] as login ID)

What on earth am I doing wrong? My username/password combo works fine at [www.facebook.com](www.facebook.com)

---

### Post by ThatLucidGuy12 on 2010-11-07
Wow, thanks! Logging in with my username helped. I owe you, man.

---

### Post by nithin933 on 2010-11-16
> **aggiemarine07 said:**
> logging out of facebook and logging back in (with the facebook username, not email) fixed the problem for me. 

Maybe it bases its log-in/authentication from a cookie that your browser stores? (i dont know enough about programming to back up that conclusion, its just a guess)

yup mine too i did the same and it worked

---

### Post by Che.SSL on 2010-12-21
> **aggiemarine07 said:**
> logging out of facebook and logging back in (with the facebook username, not email) fixed the problem for me. 

Maybe it bases its log-in/authentication from a cookie that your browser stores? (i dont know enough about programming to back up that conclusion, its just a guess)

Worked for me as well! :)
Thanks!

---

### Post by androiduser345 on 2011-01-04
I was able to log in directly to facebook in empathy. I used [email]facebookusername@chat.facebook.com[/email] with my usual password and finally got it to work that way.

---

### Post by lardy on 2011-01-09
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by lardy on 2011-01-09
I have tried all the suggestions in this thread and none of them work for me any suggestions? p.s I am a numbskull so keep it simple please.

---

### Post by jdabgotra on 2011-01-13
> **androiduser345 said:**
> I was able to log in directly to facebook in empathy. I used [email]facebookusername@chat.facebook.com[/email] with my usual password and finally got it to work that way.

This worked for me.

---

### Post by irvingswiftj86 on 2011-01-19
Logging onto the facebook website using my username instead of email address fixed the problem for me.

This was a really annoying bug.

---

### Post by irvingswiftj86 on 2011-01-19
Logging onto the facebook website using my username instead of email address fixed the problem for me.

This was a really annoying bug.

---

### Post by irvingswiftj86 on 2011-01-19
Logging onto the facebook website using my username instead of email address fixed the problem for me.

This was a really annoying bug.

---

### Post by stroke1988 on 2011-01-20
Yh i had to log out of my web facebook and log back in again before it would work

---

### Post by stroke1988 on 2011-01-20
Yh i had to log out of my web facebook and log back in again before it would work

---

### Post by TheGermanBaron on 2011-02-08
I can confirm that this worked for me, as well. That is, log out of facebook, log in with the facebook username, then connect with empathy again, which then works.

---

### Post by loveyoubun on 2011-02-13
what i did to make it work: 

1. setup username
2. logout in facebook, log back in with username instead of email adres
3. remove facebook account in empathy, ad it again

it works now.

---

### Post by zerodai on 2011-02-15
thx

---

### Post by Kill_steR on 2011-02-26
Nice...thanks...it fix the bug.....what a lame bug!!

---

### Post by fermin on 2011-03-05
> **loveyoubun said:**
> what i did to make it work: 

1. setup username
2. logout in facebook, log back in with username instead of email adres
3. remove facebook account in empathy, ad it again

it works now.
Logging into facebook with username instead of email worked for me too. Just that I had to log out and in twice before trying to reconnect in Empathy and then it worked. I did not need to remove and add again my account, though maybe it is safer that way.

---

### Post by [Manzill0] on 2011-07-28
I had the same problem, and thanks to this thread I solved it, by logging to Facebook web using my username instead of my mail.

---

### Post by Autie on 2011-08-21
Had the same issue...
Solved with login into fb with username instead of login with email.
Worked well until a few days ago.
Lame bug indeed :)
Thanks guys.

---

### Post by GoldWing on 2011-08-29
> **Autie said:**
> Had the same issue...
Solved with login into fb with username instead of login with email.
Worked well until a few days ago.
Lame bug indeed :)
Thanks guys.

This solved the issue for me as well, very lame bug indeed and I don't understand how the solution actually might work.

---

### Post by Greblok on 2011-09-12
Increadible that this bug still exist. :P
Today, a simple logout and username login fixed it like for the rest of you.
Note that I have been logged in with username for å long time but suddenly, because of reasons unknown to me and my God Google, it needed a logout to get it working today.

---

### Post by Stanley2011 on 2011-10-11
Had no luck doing any of it. I have log in with my username log out on facebook, and empathy removed and add.

---

### Post by BigCityCat on 2012-05-29
OKAY as of this post it is Kubuntu 12.04. I was having the same difficulty. It says your username is [email]yourname@facebook.com[/email]. That is true but after countless times trying this it would not work. UNTIL I logged into facebook went to account settings and realized that a username has not been set. I set the username and logged into facebook with only the usernam and password loged out and connected with kopete. It works. My suggestion is if you cant log into facebook without your email then you have not set your usernam yet in facebook.

After you set your username in facebbok then the settings are [email]username@chat.facebook.com[/email]. Password and then uncheck ssl. You may need to allow port 5222 through your firewall.

---

### Post by oldos2er on 2012-05-29
Old thread closed.

---

