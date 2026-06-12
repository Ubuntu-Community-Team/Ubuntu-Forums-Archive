---
title: "lockdown xubuntu guest account"
date: 2008-12-09
forum: Desktop Environments
---

### Post by skintythe1andonly on 2008-12-09
Im trying to setup a guest account under xubuntu hardy. I am aware that a guest account is available in intrepid but cannot upgrade for other reasons.

I am trying to do the following
[LIST=1]
[*]Have a guest account on the GDM login with no password
[*]lockdown the background, panel and desktop items on this account so it is the same each time somebody goes to login.
[*]delete all new files on logging out, so that it is essentially a blank slate every time you login
[/LIST]

It is essentially a kiosk mode i know, so i was looking  on [http://wiki.xfce.org/howto/kiosk_mode]("http://wiki.xfce.org/howto/kiosk_mode")to implement this. I have most things working. The backgrounds cannot be changed. They cannot move the panels etc..... one option i didnt see in this wiki is to fix the theme. Can i stop the theme from being changed?

On resetting the home folder each time, is there some setting I can just turn on or is it best to do it through a script, just copying a dummy account each time over?

If i was to copy a dummy home each time the guest logged in, would it have the theme choice already saved in .themes or something, fixing the above problem.

I was thinking of going with the script posted by slavik in
[http://ubuntuforums.org/showthread.php?t=410222&page=3]("http://ubuntuforums.org/showthread.php?t=410222&page=3")
 but was wondering about ownership and permissions. If the dummy home is saved in the root home, wouldnt the owner of the guest home be root making it impossible to use?

One last question, if i was to go ahead with the commands could i append them to the bash_logout file, in other words.... should i do it logging out or logging in?

Thanks in advance and I have been reading the arguments on security and stuff but this is a home family computer with not much on it but the users of each of the accounts have gotten to like their desktop their way. We have a bunch of kids staying with us for christmas so im trying to keep it the way it is

---

### Post by skintythe1andonly on 2008-12-10
Ok so ive had a look at pessulus but it only locks down gnome and the gconf editor isnt what i am looking for xubuntu

---

