---
title: "Firefox cut &amp; paste kills X"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Mocker on 2006-06-30
Hmm... not sure where to turn with this... the obvious solution for now is "don't do that" but I thought I'd throw this out here in case others are seeing this problem.

I was just using Spamcop (a web-based spam reporting system) to report some spam I recieved. I cut the source of the spam from Thunderbird's view source window, and pasted it into the text box on Spamcop's reporting page, which I had open in Firefox. Immediately, X dies and I am sent back to the login screen. I was able (unintentionally) to verify that this is a repeatable issue because I stubbornly logged back in and tried it again. 

Anyhow, when I took a closer look at the spam I was trying to report, I noticed that it had a graphic enclosure (to avoid the anti-spam text scanners, I guess). What was unusual about this one is that it had all of the image's data on a single line, rather than broken up across several. I'm guessing that one line is 10-20K long. 

I've had Firefox hang on me a few times since I upgraded to Dapper, but this is the first time I've seen it actually bring X down.

---

### Post by thingy on 2006-06-30
This is a bad bug and you should definitely goto launchpad and file it as a problem.

I just checked launchpad and the closest thing I can find is this:

[https://launchpad.net/distros/ubuntu/+source/nvidia-glx/+bug/47122](https://launchpad.net/distros/ubuntu/+source/nvidia-glx/+bug/47122)

Do you have a nvidia card?

---

