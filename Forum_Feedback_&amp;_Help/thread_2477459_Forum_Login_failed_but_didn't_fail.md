---
title: "Forum Login failed but didn't fail"
date: 2022-07-25
forum: Forum Feedback &amp; Help
---

### Post by col48 on 2022-07-25
Attempted to login just now..

First attempt failed (I think) with Invalid Redirect URL (but I was so surprised I did not check properly)

Second attempt, likewise.. but

In both cases it showed my username etc correctly and then the next screen was reporting the Invalid Redirect URL.  The second url was

([https://ubuntuforums.org?](https://ubuntuforums.org?))  <--- EDIT: what I pasted included this string after the '?'  95efa03b6b63c8778304b183a71ed383&

but certainly this time it had actually logged me in - or else I would not be here now.

Anyone know what's going on here?

---

### Post by Frogs Hair on 2022-07-25
Moved FF&H for a better fit.

---

### Post by col48 on 2022-07-26
@Frogs Hair:  Thanks, it is indeed a better fit, as today the login was straightforward.

But I'm still curious, if anyone can explain what the likely cause was.

---

### Post by col48 on 2022-07-26
Weird.  It's happened again.

Login OK to the screen where it shows my personal details but when I click Login it gives me the 'Invalid Redirect URL' message, and the 'Login with SSO' at the top right as if I have failed to login.
So I close the tab, go back to the Firefox bookmark and click again.  Same result, but this time instead of backing off, I thought I'd just try something else - I type something (anything) in the Search box, and lo! I'm in.  The search (for 'bb') fails, of course but here I am.

What's going on?

---

### Post by coffeecat on 2022-07-26
> **col48 said:**
> What's going on?

Haven't a clue. You aren't giving us precise/complete details. 

> **col48 said:**
> Login OK to the screen where it shows my personal details

Precise details please. I'm guessing you are on a login.ubuntu.com page (but please confirm), but are you logged into Ubuntu One or logged out? If you are logged out from Ubuntu One, you will see a page headed "One account for everything on Ubuntu" where you have fields for the email registered to your **Ubuntu One** account and **Ubuntu One** password. If you click on the green "log in" button, you get to another login.ubuntu.one page headed, "Personal Data Request" which shows your Full name, Ubuntu One username, and email, and....

> **col48 said:**
> t shows my personal details but when I click Login

... the green button on the Personal Data Request page says, **Yes, log me in"** not login. Precise details, please, or we can't follow what you are doing or where you are.

> **col48 said:**
> it gives me the 'Invalid Redirect URL' message

What does? A login.ubuntu.com page or an ubuntuforums.org page?

That all being said, I cannot reproduce your problem on firefox. Do you have a browser addon interfering with cookies?

---

### Post by col48 on 2022-07-26
Thanks coffecat.

I'll Logout and see if I can reproduce, but it will probably be a while due to other duties.  On giving precise details, we are fighting my lack of ability to remember details accurately, so please bear with me.

Your narrative says I was logged out of UbuntuOne.
Clicking the green button sends me to a page with the Invalid Redirect message but at the moment I am not sure whether forums or login.

And yes, I delete cookies when Firefox is closed, but this has been the case for some years.

---

### Post by col48 on 2022-07-26
I was hoping to show the process as a sequence of screenshots but I can't attach them and submitting the post with them pasted fails.

Here it is as a narrative story:

1. (Re)start Firefox, then open my Ubuntu Forums bookmark.

Screen shows the list of Ubuntu Forums.

2. Click the 'Login with SSO' button near the top right

Screen shows Ubuntu One 'One account for everything on Ubuntu'
I enter my email address and the password and

3. Click the green 'Log In' button

Screen shows Ubuntu One 'Personal Data Request' and my correct details - name, username, email, and I

4. Click the green 'Yes, log me in' button

Screen now shows a page with a Ubuntu Forums header including a 'Login with SSO' button, but the body of the screen displays a vBulletin message with the text
                      'Invalid Redirect URL (https:\\ubuntuforums.org?s'  followed by a long hex string which is not the same each time.

The 'Login with SSO' button takes me back to step 2, but I find by experiment that I can get into the forum by either
   (a) typing anything into the search box which is on the screen and initiating the search - I then see whatever I would have seen if I did the same thing inside the forum proper
   (b) clicking the 'Ubuntu Forums' text in the orange bar below the screen body - I then see the list of forums, with my username etc in the top right
I haven't tried other actions on this screen, but in both these cases I am now in the forum, correctly logged in.


I don't know if the newly discovered inability to upload small (< 100Mb) jpg attachments is related, but turning the 'Enhanced Attachment Uploading' setting off made no difference, nor did turning it back on.
I would hope that the fact that cookies do not survive the end of the Firefox session would be irrelevant - what I want from a given session is only loosely connected with any previous one and a website's assumptions rarely coincide with my train of thought.

---

### Post by coffeecat on 2022-07-26
> **col48 said:**
> I was hoping to show the process as a sequence of screenshots but I can't attach them and submitting the post with them pasted fails.

<snip>

I don't know if the newly discovered inability to upload small (< 100Mb) jpg attachments is related, 


Like this?

[ATTACH=CONFIG]290769[/ATTACH]

Since I can upload pictures as attachments without any problem and do not see the invalid redirection message in Firefox (or Chrome) even after several logouts and logins, and the fact that no other forum member is currently complaining of the same issues, all suggests that something local to your system is responsible. Look at all your browser addons if you have any. If you do, try disabling them one by one to see if that solves the problem. Can you try another browser?

The cookies were only the first thing that came to mind. I agree - that's probably irrelevant.

Thanks for clarifying your step by step process. That makes the situation clear. That is what I see if I start off from being logged out from Ubuntu One, but with the exception of not seeing the invalid redirect message.

---

### Post by col48 on 2022-07-26
@coffeecat

Yes, got it!  The culprit was the cookie autodelete add-on.  It was also stopping me uploading attachments - by way of evidence, here is one of the screenshots I wanted to put in my last post.

[ATTACH=CONFIG]290770[/ATTACH]

Following your suggestions, I signed into the forum using the Opera browser with no problem at all.
Back in Firefox it was only when I disabled the Cookie Autodelete add-on that the issue went away.
For the record, it was version 3.8.1 running in Firefox 88 (64-bit), which had been updated on 5 July 2022.
The documentation does say it may not be supported on some [unspecified] versions of Firefox and Chrome but I had not had any problem up to now.  If I can figure out how to raise the issue on GitHub I will do so, but not tonight.

Thanks for your help and pointing the way to the solution to the problem.

---

