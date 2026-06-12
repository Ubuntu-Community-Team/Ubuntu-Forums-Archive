---
title: "Please bring back the old login method"
date: 2013-09-04
forum: Forum Feedback &amp; Help
---

### Post by bkline on 2013-09-04
I tried logging in with the new mechanism yesterday and I got the following error message:

> Oops!

Something broke while generating the page. Please try again in a few minutes, and if the problem persists file a bug or contact customer support. Please quote OOPS-ID ['OOPS-1cc20df06b62fc6a4a022abe630febdd']

There was no information on the page about how to file a bug or contact customer support.  I tried emailing [email]support@ubuntuforums.org[/email] but that bounced.

Please bring back the old login method.

---

### Post by Elfy on 2013-09-04
We'll not be bringing back the old method of logging in - our hands are tied.

Where did you find that e-mail address?

---

### Post by santosh83 on 2013-09-04
Hi bkline. Agree that the Ubuntu SSO method of logging in is clunky and complicated enough to confuse many users. Fortunately for me, I'd previously had a Ubuntu One account (which has now become the Ubuntu One or Ubuntu One SSO ID), so things were smooth for me when logging into Ubuntu Forums after the hacking episode. My ID was properly linked (as I'd used the same email address in both Forums and Ubuntu One SSO) together, and my name was not mangled, as has seemingly happened to a lot of users. So essentially you need an account with Ubuntu One, which you must create if you haven't already got, and you must ensure the email addresses in both accounts (Forums & Ubuntu One SSO) are the same before logging into Forums for the first time after this overhaul.

Another confusing aspect is the precense of another login ID in the form of Launchpad login account, which is yet to be completely merged with Ubuntu One SSO. I also have a Launchpad account created long back to file a bug report. One more tricky thing is that you are NOT automatically signed out of your Ubuntu One account when you sign out of the sites where you'd logged into in the first place. Thus when you click logout in Ubuntu Forums, you wont be automatically signed out of Ubuntu One SSO. You must manually visit login.ubuntu.com and sign out there. All this just appears awkward and clunky and complicated, and I hope the process will be polished and streamlined in the coming days.

---

### Post by cariboo on 2013-09-05
The good thing about SSO is that it allows you to sign on to any of the services Ubuntu offers using a single sign-on. I used the same login for Ubuntu One as I did for Launchpad, so I only have one SSO account. To merge SSO accounts, have a look [here]("https://one.ubuntu.com/help/faq/i-have-two-accounts-how-can-i-merge-them/")

---

### Post by plucky on 2013-09-05
> **bkline said:**
> I tried logging in with the new mechanism yesterday and I got the following error message:

Oops!

Something broke while generating the page. Please try again in a few minutes, and if the problem persists file a bug or contact customer support. Please quote OOPS-ID ['OOPS-1cc20df06b62fc6a4a022abe630febdd'] 

There was no information on the page about how to file a bug or contact customer support.  I tried emailing [email]support@ubuntuforums.org[/email] but that bounced.

Please bring back the old login method.

Try clearing the cache in your browser and see if that fixes the problem.

That worked for me when I got the error.

Good Luck

---

### Post by bkline on 2013-09-05
> **Elfy said:**
> Where did you find that e-mail address?

I didn't find it.  That's part of what I was trying to say.  I was given a page telling me to contact customer support, without any instructions for how to do so.  So that left me having to guess, hoping that the organization would use the most commonly used structure for the customer support email address.  The guess turned out to be wrong, given the bounced message.  For all I know there's no support address at all, and the instructions to contact customer support are just hot air (or more appropriate to this context, cold bits).

---

### Post by bkline on 2013-09-05
> **plucky said:**
> Try clearing the cache in your browser and see if that fixes the problem.

That problem wasn't in my browser's cache: the server itself was broken.  I just had to wait a day to get back in.

Unfortunately, no amount of waiting or cache clearing is going to address the many problems introduced by the new login method. :-(

---

### Post by Elfy on 2013-09-05
I've never seen a page for customer support. If you can point me to that I can try and get that clearer for users in the future. 

As far as I am aware there are 2 ways to contact us - the Contact Us link at the bottom of the page and direct to the FC from our wiki page [https://wiki.ubuntu.com/ForumCouncil](https://wiki.ubuntu.com/ForumCouncil)

---

### Post by coffeecat on 2013-09-05
> **bkline said:**
> I didn't find it.  That's part of what I was trying to say.  I was given a page telling me to contact customer support, without any instructions for how to do so.  So that left me having to guess, hoping that the organization would use the most commonly used structure for the customer support email address.  The guess turned out to be wrong, given the bounced message.  For all I know there's no support address at all, and the instructions to contact customer support are just hot air (or more appropriate to this context, cold bits).

The oops message you quoted is not a vbulletin message, therefore not from the forum. My guess is that it was a message from the Ubuntu One SSO server and therefore customer support would be at Ubuntu One. The fact that Ubuntu One has customers and we don't (we have forum members) would support this theory. And since Ubuntu One is not a thing we have any control over, there's little we can do about this issue except raise it with Canonical IS if it gets to be a significant problem.

> **bkline said:**
> That problem wasn't in my browser's cache: the server itself was broken.  I just had to wait a day to get back in.

Out of interest, how many times did you retry during the day? I am having to login half-a-dozen times a day or more (the timeout on the admin control panel is much quicker than with the forum - security), and have done so daily since the forum came up again on 30th July. I have seen this oops message but once, and when I did I simply refreshed the page and I was able to log in immediately. I'm sorry you experienced difficulty, but we haven't much to go on until more people report similar difficulty.

---

### Post by ventrical on 2013-09-05
I can't login to the ubuntu wiki. I had used a separate launchpad account to log in and now all I get is an endless spin with Ubuntu One. I logged out of my SSO account but that did not help..

---

### Post by ventrical on 2013-09-05
> **cariboo907 said:**
> The good thing about SSO is that it allows you to sign on to any of the services Ubuntu offers using a single sign-on. I used the same login for Ubuntu One as I did for Launchpad, so I only have one SSO account. To merge SSO accounts, have a look [here]("https://one.ubuntu.com/help/faq/i-have-two-accounts-how-can-i-merge-them/")


"
Follow the instructions on screen, and you should be able to merge your accounts.
 Please note that merging your Launchpad accounts is very likely to  break your access to Summit, AskUbuntu, any apps you have purchased in  Software Center, and any third-party sites which use your Launchpad  username as your login."

And yet another miserable failure. one sec...

edit:

Fortunately I am logged on  to launchpad on other installs .. so all is not lost .. until I either get bumped or accidently close my browser ! :) LOL

---

### Post by Elfy on 2013-09-06
> **ventrical said:**
> I can't login to the ubuntu wiki. I had used a separate launchpad account to log in and now all I get is an endless spin with Ubuntu One. I logged out of my SSO account but that did not help..

That'll be a U1/sso issue - no good telling us, we've got our own issues to worry about.

---

### Post by carl4926 on 2013-09-06
> **cariboo907 said:**
> The good thing about SSO is that it allows you to sign on to any of the services Ubuntu offers using a single sign-on. I used the same login for Ubuntu One as I did for Launchpad, so I only have one SSO account. To merge SSO accounts, have a look [here]("https://one.ubuntu.com/help/faq/i-have-two-accounts-how-can-i-merge-them/")
Seems to have eliminated much spam too

---

### Post by ventrical on 2013-09-06
> **Elfy said:**
> That'll be a U1/sso issue - no good telling us, we've got our own issues to worry about.


Right !   I know that. I'll keep that one in my back pocket ;)

Thanks

Regards..

---

