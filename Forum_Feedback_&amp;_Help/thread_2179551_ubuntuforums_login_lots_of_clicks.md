---
title: "ubuntuforums login lots of clicks"
date: 2013-10-08
forum: Forum Feedback &amp; Help
---

### Post by Kevin McCready on 2013-10-08
With the new SSO login I have to click about three different things before I'm here. The first click takes me to the login site, I have to click a second time when it asks me do I really want to login (doh) and then there's another and finally I'm here. Is there a way to set Firefox 24.0 to remember all this and automatically log me in?

---

### Post by DuckHook on 2013-10-08
Short answer--No.
Shortish answer--They're working on it.

---

### Post by sandyd on 2013-10-08
moved to forum help & feedback

---

### Post by coffeecat on 2013-10-09
> **Kevin McCready said:**
> With the new SSO login I have to click about three different things before I'm here. The first click takes me to the login site, I have to click a second time when it asks me do I really want to login (doh) and then there's another and finally I'm here. Is there a way to set Firefox 24.0 to remember all this and automatically log me in?

It's your third click I don't follow - I cannot reproduce it, unless I log out of Ubuntu One, but that doesn't seem to be the case that you are describing. Assuming Firefox has remembered your Ubuntu One login details and that you are already logged into Ubuntu One, then this is the sequence I see:

[list=1][*]Click on "Login with SSO" button on forum home page.
[*]There is a brief (about 1 second) display of a "You are about to be redirected to your openid provider" page with a continue button, but I am redirected before I need or am able to click on it.
[*]At the login.ubuntu.com page I am presented with the personal data request page and I click on the "Yes, log me in" button, after which I am returned to the forum logged in.[/list]

That's it - 2 clicks. If I am not already logged into my Ubuntu One account, I see this:

[list=1][*]As 1 above.
[*]As 2 above.
[*]I see the Ubuntu One log in page and have to click the Log In button. Firefox has remembered my email and Ubuntu One password.
[*]As 3 above.[/list]

Three clicks instead of 2, but only when I am not logged into Ubuntu One already. I stay logged into Ubuntu One permanently and this survives closing firefox.

Compare this with the previous way of logging into ubuntuforums using the native vbulletin login, assuming firefox was already remembering your login credentials:

[list=1][*]Click in username field to place the cursor there.
[*]Type first letter of username to get Firefox to display the drop-down with the remembered username.
[*]Click on the username displayed in the drop-down to get it written to the username field.
[*]Click in the password field for firefox to fill in the remembered password.
[*]Click on login button.[/list]

No redirects, but phew! I think people have short memories.

---

### Post by jmarkrobinson on 2013-10-22
The old way may have been clunky and it's all well and nice to explain but what has that got to do with today?  I don't have one other site of over 200 that I have to click more than once to get logged in.  I manage all my sites with a password manager, it stores all login data and auto-populates that login screen.  Once click and I'm in, but not here!  Still 3 clicks.  Also, because there is no password for SSO, my password manager does not like it.

---

### Post by tomearp on 2014-02-06
I use Firefox 26, and the Ubuntu One sign in survives quite happily across restarts. The part that I find a little annoying is that I have to approve the Personal Data Request every time I click Login with SSO.

Surely it must be able to set a cookie, or retain the selections somewhere in my Ubuntu One account, or something else, so that I don't have to approve it repeatedly?

---

