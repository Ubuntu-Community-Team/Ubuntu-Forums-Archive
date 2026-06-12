---
title: "Setting webmail as default e-mail (or setting web forms to fire up webmail)"
date: 2006-08-01
forum: Desktop Environments
---

### Post by peterwr on 2006-08-01
Is this doable? I have two applications in mind:

1. My employer favours a webmail app rather than clients like Outlook, Thunderbird, etc. We have many online forms on our intranet, so it would be good to be able to get the forms to fire up the webmail app instead of the user's chosen client. 

2. People using public-access computers to fill in forms on our external website obviously don't have access to an actual client on the machine they're using, so it would be good to be able to allow them to pick a webmail app (gmail etc) to send the form. 

Maybe this would be better asked on a web design forum, but I just thought I'd post it here in case anyone here knows of a solution. 

TIA,


Peter

---

### Post by tturrisi on 2006-08-01
This sounds a bit confusing.
You have "forms" on an intranet.  How are these forms accessed?  A browser?  If so, all anyone must do is open a browser, fill in a form & submit it.  The form, if in a www doc, is coded to post or get the form input to a server side application to process the form input, such as a script that uses sendmail or other mail handler.  Not sure what you want to do...

---

### Post by peterwr on 2006-08-01
Doh! Sorry about that - I was working on forms at the time and did the post in terms of forms. I meant "mailto" links, obviously. Can I/how do I get a mailto link to offer the user a webmail link instead of firing up the default e-mail client set up on that computer?

Sorry for the confusion. I need more coffee. That or a damn good slap...  

#-o

---

### Post by ewl1217 on 2006-08-01
I'm you're using Firefox, try the [WebmailCompose]("http://jedbrown.net/1.0/mozilla/extensions/") extension. I've used it before and it works like a charm.

**EDIT:** I updated the link. The version at addons.mozilla.org didn't want to work with Firefox 1.5.

---

### Post by rmjb on 2006-08-01
Is there anyway to do this system wide? Perhaps using the WebmailCompose extension and then setting Firefox as your Preferred Mail Reader?? Will that work?

- rmjb

---

### Post by Jhongy on 2006-08-02
Instead of using a mailto: link, why not just use a weblink? If each user uses a different webmail app, then you just need a simple webform or javascript popup to ask the user to type in the webaddress of their webmail homepage. This could then be saved as a persistent cookie and remembered for future sessions.

---

