---
title: "firefox crashes in some ASP pages"
date: 2007-01-05
forum: Desktop Environments
---

### Post by ryu kun on 2007-01-05
My Firefox (1.5.dfsg+1.5.0.9-0ubuntu0.6.06) suddenly crashes (closes itself) when I try to open some ASP login pages.

This began occuring after my last update, I think.

Any suggestions, please?

---

### Post by Paul41 on 2007-01-05
It shouldn't have anything to do with ASP because everything with the ASP runs on the server.  Nothing that gets sent to your browser from an ASP page is any different than from a normal HTML page. It could be that the login page you are going to has some other problem, such as a javascript error that is crashing your browser.

---

### Post by bodycoach2 on 2007-01-05
I'm experiencing the same problem. Firefox worked fine before the update, but today it crashes on my Community College login page.

Hopefully, this will be fixed soon.

> **ryu kun said:**
> My Firefox (1.5.dfsg+1.5.0.9-0ubuntu0.6.06) suddenly crashes (closes itself) when I try to open some ASP login pages.

This began occuring after my last update, I think.

Any suggestions, please?

---

### Post by ryu kun on 2007-01-06
I've got the output of "Segmentation Fault" in terminal during the crash. It looks like a bug.

---

### Post by ryu kun on 2007-01-06
I downgraded my Firefox to 1.5.0.3 and problem has gone. I will wait for a new version.

To downgrade, force package "firefox" to a lower version using Synaptic.

---

### Post by Paul41 on 2007-01-06
Did you report the bug?

[https://bugzilla.mozilla.org/](https://bugzilla.mozilla.org/)

---

### Post by ryu kun on 2007-01-08
Yes, I reported the bug. Here is its page: 
[URL="https://bugzilla.mozilla.org/show_bug.cgi?id=366297"]
https://bugzilla.mozilla.org/show_bug.cgi?id=366297[/URL]

---

### Post by ryu kun on 2007-01-08
I tried an official build of 1.5.0.9 and it didn't crash.. I guess it's with the Ubuntu's build.. I am not sure where to report this bug.

---

### Post by Paul41 on 2007-01-08
> I tried an official build of 1.5.0.9 and it didn't crash.. I guess it's with the Ubuntu's build.. I am not sure where to report this bug.

You can file them in Launchpad. This post tells you how to do it.

[http://ubuntuforums.org/showthread.php?t=284595&highlight=launchpad](http://ubuntuforums.org/showthread.php?t=284595&highlight=launchpad)

---

### Post by ryu kun on 2007-01-09
OK, here is the new bug report:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/78561]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/78561")

---

### Post by Stryker777 on 2007-01-09
Im not so sure its an ASP issue.  Those pages in the bug report did nothing to me.  Yet I have been reset repeatedly for the last 24 hours.  Most of the time it is on some of my own pages.    So far they all have had some java validation code in a form or button and it was clicking on the button that caused the crash for me.

---

### Post by Paul41 on 2007-01-09
> **Stryker777 said:**
> Im not so sure its an ASP issue.  Those pages in the bug report did nothing to me.  Yet I have been reset repeatedly for the last 24 hours.  Most of the time it is on some of my own pages.    So far they all have had some java validation code in a form or button and it was clicking on the button that caused the crash for me.

I think you are probably right since all of the ASP code runs on the server and never goes to the client. My initial thought was that it was something with javascript also.

---

### Post by ryu kun on 2007-01-26
I have good news. A fix for this bug has just been released. 

[http://www.ubuntu.com/usn/usn-398-4](http://www.ubuntu.com/usn/usn-398-4)

---

