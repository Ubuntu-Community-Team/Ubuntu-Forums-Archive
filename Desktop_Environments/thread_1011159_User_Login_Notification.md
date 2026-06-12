---
title: "User Login Notification"
date: 2008-12-14
forum: Desktop Environments
---

### Post by MaindotC on 2008-12-14
Is there a way to receive a notification if a user logs into my machine remotely?

I could just keep the window open from System -> Administration -> System Log -> auth.log.  I've also read about zenity and that seems very close to what I'm looking for but it seems that has to be initiated by the user logging in.  Is there some way to set sshd to invoke zenity when a user logs in so I get a pop-up saying someone has connected to my machine?  Thanks!

---

### Post by eotakos on 2008-12-19
nice thinking - this would be a nice tool! 

what i noticed the other day, is that i was connected with my laptop to my desktop via winSCP to transfer files, and the w and who commands wouldn't display the remotely logged-in user.

not quite helpful i know... i'm just saying

please post again here if you find anything

---

### Post by MaindotC on 2008-12-19
The 'users' command shows who's logged in.  Like I said, I could just display the auth.log, so maybe I can just come up with a nice little interface for it.

Edit: I just found this thing called Grok: [http://www.semicomplete.com/projects/grok/](http://www.semicomplete.com/projects/grok/)  I don't know how to use Perl but I think I can set aside some time to get this working.  He even provides some good examples.

---

