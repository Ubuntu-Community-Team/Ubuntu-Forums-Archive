---
title: "Bad bot, go away! Request aborted."
date: 2021-07-18
forum: Forum Feedback &amp; Help
---

### Post by walts48 on 2021-07-18
I get this message every time I use Firefox Nightly 91.0a1, now version 92.0a1.

I was able to use Firefox Beta 90.0b(x) to sign on and read the forums.

Now I get the same message using Firefox Beta 91.0b3.

I am able to use the Firefox 89.0.2 release.

Are we only allowed to use release versions now?

---

### Post by Frogs Hair on 2021-07-18
I can't reproduce the error message with the latest nightly build. have not tried the beta version. We may have to wait for more nightly/beta users to chime in.

---

### Post by coffeecat on 2021-07-18
> **walts48 said:**
> 
I was able to use Firefox Beta 90.0b(x) to sign on and read the forums.

Now I get the same message using Firefox Beta 91.0b3.


From imperfect memory, I've believe I've seen the "bad bot..." message, but from ubuntu.com, not from ubuntuforums.org. Which page was on screen when you got the message? Next time you see it, make a note of whether the URL bar shows ubuntu.com or ubuntuforums.org for the domain. If the former, it's an SSO login site issue and nothing to do with the forum. If the latter it's a forum software issue.

**Edit:** Yep. Memory not so imperfect after all.

Here are some leads for you:

[https://askubuntu.com/questions/650544/login-launchpad-net-tells-me-bad-bot-go-away-request-aborted](https://askubuntu.com/questions/650544/login-launchpad-net-tells-me-bad-bot-go-away-request-aborted)

[https://bugs.launchpad.net/canonical-identity-provider/+bug/1779876](https://bugs.launchpad.net/canonical-identity-provider/+bug/1779876)

[https://bugs.launchpad.net/canonical-identity-provider/+bug/1775588](https://bugs.launchpad.net/canonical-identity-provider/+bug/1775588)

The message is not coming from the forum software. The third link, although three years old and primarily about Chrome, has some interesting clues.

---

### Post by walts48 on 2021-07-19
Thanks for the responses and tips.

I don't use Last Pass, or Chrome, but will try the Fx Beta and Nightly in safe mode and see what happens when time permits.

Update: Still got the Bad bot message when trying Firefox Nightly in Troubleshoot Mode, was able to sign in using a new test profile.

---

### Post by walts48 on 2021-07-20
Solved for now by removing the username and password from my Fx Nightly, logging back in and saving them again.

---

### Post by erosman on 2021-07-22
I would like to add that I had the exact same problem and could not log in even though I got logged in `login.ubuntu.com`, the login wouldn't get through to `ubuntuforums.org`.

I also deleted and reset the password and it is working now.

*Firefox 92.0a1 (2021-07-21) (64-bit)*

---

### Post by erosman on 2021-08-05
For reference ...

A bug was filed over this issue:
 [Password Manager fails when username is on one page and password is on another]("https://bugzilla.mozilla.org/show_bug.cgi?id=1724136")

For the time being:
Turning off **Autofill logins and passwords** in Firefox Nightly Settings prevents the problem

---

