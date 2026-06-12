---
title: "account locked"
date: 2018-11-04
forum: Forum Feedback &amp; Help
---

### Post by luca31 on 2018-11-04
Hi all I can't anymore write on the forum 

I receive the following message when I try to answer/modify the following thread [https://ubuntuforums.org/showthread.php?t=2405194](https://ubuntuforums.org/showthread.php?t=2405194) or send private message...

**Forbidden**

 You don't have permission to access /newreply.php on this server.


Could you check what happened?
Regards 

Luca

---

### Post by slickymaster on 2018-11-04
There's nothing wrong with you account and I see that you already were able to post so I'm guessing that it was just a temporary glitch.

---

### Post by luca31 on 2018-11-04
Hi the problem is not solved yet, I retried to edit my answer as the initial one, where I also pasted a curl test (between code tags), whose output included the http header and the boby with the php tag/code and again I got the same error:

**Forbidden**

 You don't have permission to access /editpost.php on this server.

 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443
 
Maybe it's something related to content filter on the httpd server (mod_security/filtering modules) or on the application server.
Could you check/report the bug please?

thanks

Luca

---

### Post by lisati on 2018-11-04
I can see that you were able to post in the thread just a few hours ago. What type of content were you trying to post?

---

### Post by luca31 on 2018-11-04
I don't manage to post the content because I get the same error.. I wanted to post a test with curl, so I wrap the command and his output in the code tags, the output contains http headers and the http body with php code and php tags.. if you send me a private msg with a mail I will send you the exact message 
Anyway it's not important... I think I got the point in the thread. Let me know if you're interested to investigate further. 
regards 

Luca

---

### Post by cariboo on 2018-11-05
It looks like you ran afoul of some of the restrictions Canonical IS has placed on what and how we post. If anything looks even vaguely like it might be malicious code you will run into what you ran into. the best way to get around this is to use [Ubuntu Pastebin]("https://paste.ubuntu.com/")

---

### Post by luca31 on 2018-11-05
Cool. Here's the orginal locked content

[https://paste.ubuntu.com/p/xb22W67VGq/](https://paste.ubuntu.com/p/xb22W67VGq/)

thanks a lot for the support

---

### Post by slickymaster on 2018-11-05
> **luca31 said:**
> Cool. Here's the orginal locked content

[https://paste.ubuntu.com/p/xb22W67VGq/](https://paste.ubuntu.com/p/xb22W67VGq/)

thanks a lot for the support

What cariboo meant was for you to post the pastebin link in the original thread you wanted to post from the start, not here in the FF&H thread

---

