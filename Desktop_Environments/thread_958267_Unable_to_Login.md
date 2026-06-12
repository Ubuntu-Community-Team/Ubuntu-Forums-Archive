---
title: "Unable to Login"
date: 2008-10-25
forum: Desktop Environments
---

### Post by imrank on 2008-10-25
Hi,

I am running Ubuntu 8.04. I have been using the system for about a month now and all has been great. However recently I am not able to login.

This is what I experience:

1. Enter my username into the text field on login screen at startup
2. Hit enter/tab
3. Error box comes up before I can enter my password with exclamation mark but no message.

I cannot proceed any further and can't login.

What is going on, how do i fix it?

Thanks,

Imran

---

### Post by saltire89 on 2008-10-25
I had this problem (sort of: I could enter the password then I got stopped), and what I did was to enter the gnome failsafe session. If you select options->sessions on the login screen and then failsafe session.

This didn't fix it for me, but it did allow me to login.

Out of curiosity, do you have more than one users? and do any of them log in?

---

### Post by imrank on 2008-10-25
Anybody ????

Did I not include enough detail? Has this been solved somewhere else?

HELP!!!

---

### Post by imrank on 2008-10-25
No I only have a single user.

When I try to login using the gnome failsafe session, it doesnt actually change anything. That is the same login screen is there and I have the same problem.

How did you actually end up fixing it?

---

### Post by hictio on 2008-10-25
Have you tried login in thru a Virtual Console? To see, if, at least you are able to properly login to your box at all.
On the graphical login screen, type:

Ctrl + Alt + F3 keys at the same time

(You can press any F1-F6 key, pressing the keyboard combo, but using F7 will put you back at the graphical login screen.)

Once you are on the Virtual Console, type your username ENTER and then your password and ENTER and you'll be on your box.
If that works, we can see of turning the graphical login for a minute and test a manual start of the graphical environment.

---

### Post by imrank on 2008-10-26
Hey hictio,

I have tried what you have said. Basically when I go into this virtual console, it comes up with:

khan login: 

khan being the name of the computer and my username (could this be an issue). I type my username and it tells me my login has failed. Also when I type my password directly it fails as well. 

I have also went down the path of signing in through recovery mode. I am able to get in this way, is there something I can do when in recovery mode?

Is this is a UI problem? Can I revert back to "default" UI settings?

Cheers,

Imran

---

### Post by hictio on 2008-10-26
This is really weird...
Let me see if get this straight, on the console, you type your username, hit ENTER, and prints a message that your login has failed?
The usual way should be, type in your username, hit ENTER, the system prompts you back for your Password, you type that, hit ENTER, and then it might or not fail, depending if typed it well, you are allowed, etc, etc.
I have never seeing a such a problem on a Linux box before.

Did installed something, upgraded the system? When did this started?

There are way of restoring the 'defaut GUI', but I don't think thats the solution on this case.

If you type any other username than the valid one (yours) what happens? Does it prompt you for a password? On the graphical logins as well as on the console.

---

### Post by hictio on 2008-10-26
What really puzzles me -to put it simple- is that, no matter what you type as username, it should always ask you for a password.

---

### Post by imrank on 2008-10-26
So what I've done is gone into recovery mode and added a new user since I only had a single user. I then started up the box as per normal. Unfortunately it is the same behavior, i.e. I type my username and then am told immediately that my login has failed.

The only thing that I changed on the system is some UI stuff such as Quartz and modified my themes.

---

### Post by hictio on 2008-10-26
That's too bad... I was going to suggest as next step test to create a new user, and see if it worked.

My guess is that since it so drastic, I mean, no even getting the password, I would think that one of the [pam](http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules) libraries got snuffed?

---

### Post by imrank on 2008-10-27
Thanks for all ur replies hictio.

Lol, there goes my argument with my brother that switching to Ubuntu would make things more stable. :p

If I reinstall ubuntu over the top of my existing installation. Would that solve the problem? I mean obviously I lose a all my settings etc. But most of my important stuff is on another drive.

Thanks

---

### Post by hictio on 2008-10-27
It really seems weird, but, I have never personally seeing such a situation before, on any linux box.
Yes, most certainly reinstalling will fix, but it is a major PITA, at least, login thru a recovery mode would allow you to pull out your data.

---

