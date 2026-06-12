---
title: "How to copy Thunderbird mail DB from old gutsy comp to new gutsy computer?"
date: 2007-12-08
forum: Desktop Environments
---

### Post by bliffle on 2007-12-08
I have had Mozilla Thunderbird running nicely on Gutsy on my old computer (IBM T40) for several months. I had to port from XP OE to XP Tbird and then to ubuntu Tbird, but all that went smoothly.

Now I want to get Tbird running on my new Gutsy computer (IBM T60), and have had a lot of problems. Some of which come, I am sure, from the fact that the Tbird I installed on the T40 was the version on the mozilla website. I tried installing "thunderbird 2.0.0.9.tar.gz" from the mozilla website on the T60 but it blewup with an error I couldn't fix, 2 or 3 times, so I installed the Synaptics  version, which claims to be 2.0.0.8, but after installation the "about" box says it's 2.0.0.6! So it appears that the new computer has an older TBird than the old computer!

I've discovered, after a lot of false starts, that the two versions have their DB in different directories, in the case of the T40 (2.0.0.9 from mozilla) it's in "/home/user/.thunderbird" and in  the case of the T60 (2.0.0.8 from mozilla) it's in "/home/user/.mozilla-.thunderbird".

So I copied the data from the old "/.thunderbird" to the new "/.mozilla-thunderbird" and Tbird came up with the correct local folders and it even fetched mail from my POP account. Without requesting any POP passwords, so I guess it got that from the DB.

But when I attempted to send a new email Tbird reported that it couldn't connect to my SMTP server. So I poked around and tried to figure out 'why' and what I should do, but no luck. I just don't understand where and when I supply the password (and maybe the userid as well) so that the Tbird can logon to the SMTP server.

Very mysterious. Should I go back and try to install the TBird 2.0.0.9 from mozilla again? How do I setup SMTP?

---

### Post by komputes on 2007-12-08
I also use thunderbird (along with the calendar add-on called lightning). And I had trouble finding help to migrate all my settings, accounts, email, and calendar from XP to 7.10. I just don't know which directories to play from where to where.

How were you able to copy thunderbird info from XP to Ubuntu? I still have my XP HD imaged somewhere but I don't know how to import it from XP to Ubuntu. You seem to have it working well, any recommendations?

[IMG]http://komputes.com/images/komputes_userbar.gif[/IMG]

---

### Post by bliffle on 2007-12-08
> **komputes said:**
> I also use thunderbird (along with the calendar add-on called lightning). And I had trouble finding help to migrate all my settings, accounts, email, and calendar from XP to 7.10. I just don't know which directories to play from where to where.

How were you able to copy thunderbird info from XP to Ubuntu? I still have my XP HD imaged somewhere but I don't know how to import it from XP to Ubuntu. You seem to have it working well, any recommendations?

[IMG]http://komputes.com/images/komputes_userbar.gif[/IMG]

The XP OE imigration to XP Tbird was pretty easy. As I recall it was just a matter of using the OE "export" and the Tbird "import".

---

### Post by komputes on 2007-12-09
I guess it's different with Outlook, but I don't see an export in Thinderbird.

---

### Post by bliffle on 2007-12-09
> **komputes said:**
> I guess it's different with Outlook, but I don't see an export in Thinderbird.

You're right, too: there is no "Export" AFAIK in Thunderbird altho there is an "import". Very odd.

When I try to "send" a message I get the attached error report:

"Sending of message failed
The message could not be sent because connecting to SMTP server
sendmail.xxxxxx.com failed. The server may be unavailable or is refusing SMTP
connections. Please verify that your SMTP server setting is correct and try again, or else
contact your network Administrator"

---

### Post by bliffle on 2007-12-09
I think I've solved this problem by deleting and re-entering the SMTP server info in the TB "accounts" page.

---

