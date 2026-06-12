---
title: "Evolution - &quot;Send an Email&quot; Alarm grayed out. SMS option?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by tekguy on 2006-06-19
One problem kind of leads to the other. What I am trying to do is have Evolution send an SMS message to my cell phone at a specified amount of time before the event. I thought I could use the "Send an Email" feature in the Alarm setting on the Calender. This option is grayed out.

So I was going to try to use start a program to run a command line command that would mail a message to my cell phone email address being able to specify the body on the command line. I have not been able to find what I should use.

Someone had suggested to me to use sendmail. Reading through the manual it seemed that it was over kill and to complicated for this project. A lot of the syntax examples I had found was mostly for using it in a server environment.

Any help would be great! I guess if I knew what to use for command line email I could even have my cron jobs sms'd to me :)

---

### Post by scxtt on 2006-06-19
i use mailx (it's in the repos) - works great, can even specify a subject! (couldn't w/ sendmail) ... and you can have crons use it (i do) ...

---

### Post by tekguy on 2006-07-05
I don't seem to know what i'm doing with mailx. I installed it from the repos.

If I run mailx -s "test" [email]email@domain.com[/email] I get a blank line next waiting for the body. If I put in a . then hit enter I can continue on. I need to be able to send everything with out user intervention.

I'm not really sure what i'm missing.

---

