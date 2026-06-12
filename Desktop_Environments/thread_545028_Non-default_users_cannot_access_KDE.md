---
title: "Non-default users cannot access KDE"
date: 2007-09-07
forum: Desktop Environments
---

### Post by adasiak on 2007-09-07
What I expect to happen:
On booting, KDE offers a few choices of users to log in – call them <default> (the account created during installation) and <newuser>.  After five seconds of user inaction, <default> is logged in to KDE automatically, no password required.  (I have set the "Conveniences" thus in Login Manager.)  Or, if I choose <newuser>, I click on that name or type it in, enter the password, and am taken to <newuser's> desktop.

What happens instead:
The username <default> appears in the login window, highlighted, as it should.  But no other users appear in a list.  After five seconds, login is completed and the desktop loads.  If, instead of waiting, I enter <newuser> and password, the screen blacks out for a few seconds, and the login screen again appears, with <default> in the window.  (This time, it does not log <default> in automatically.)

Now, I know that <newuser> is a legitimate user: I can switch over to a console and log him in.  However, from within that console, I cannot start KDE with "startx" (which I think worked when I was trying Debian).  I get a message that starts with: ```
xauth:  creating new authority file: /home/<newuser>/.serverauth.5522
``` and ends with: ```
xinit:  no such process (errno3): Server error.
```

(If you need the complete output, please advise me on where to find it, that I may cut and paste.)

While I won't attempt diagnosis, I'll mention a few things which may or may not be relevant: (1) When creating <newuser>, I assigned him to all the same groups as <default>.  (2) I've activated the root account to avoid having to futz with sudo-ing every command.  (3) When adjusting the Login Manager, I surely changed some of the selected and hidden users on the "Users" tab – though, if I read it right, it should still show a list of the two created accounts.  (4) None of the changes I tried to make in the Login Manager's "Appearance" tab have taken effect, though my selected values are visible after repeated logins.

(I can't tell you where I've looked already, because I can't think of any keywords that would elicit a useful set of results.  I suspect that my search would be nothing but false hits.)

Any suggestions, external references, or clarifying questions will be kindly appreciated.

--Paul

---

