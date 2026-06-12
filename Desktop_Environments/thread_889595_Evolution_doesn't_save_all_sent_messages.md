---
title: "Evolution doesn't save all sent messages"
date: 2008-08-14
forum: Desktop Environments
---

### Post by anlag on 2008-08-14
I am using Ubuntu 8.04 and Evolution 2.22.3.1, the latter on trial as I thought I would try it out and see if it can beat Thunderbird.

However, there is a very annoying problem at the moment. I want all my sent messages to be saved into the 'Sent' folder on my IMAP account, and have made settings accordingly in Edit->Preferences->Mail Accounts->Edit->Defaults->Sent Messages Folder. And it works, most of the time! But then occasionally, say once every four e-mails I send, one will simply not be saved into that folder, and indeed cannot be found to have been saved at all. 

Even replying to the same e-mail twice in a row, one may get saved and the other may not. I have asked the recipients and the e-mails seem to arrive, but I still need the copies myself as well.

This is an exceptionally unreliable behaviour for a default e-mail client, and I'm wondering if anyone has a suggestion as to what might be wrong?

---

### Post by anlag on 2008-08-14
Now this is getting even stranger. The last hour I have sent three e-mails to the same person, two as replies to his and one forward of another mail. Copies of the replies are nowhere to be found. Copy of the forward is in my LOCAL sent-box, where no other e-mails have ended up previously.

The setting is still to save to 'Sent' on my IMAP account. I have not changed any settings since yesterday, when it would save at least 3/4 messages correctly. I have switched around between different connections, ethernet and wireless, but am on the same laptop and have not had any other connectivity issues.

Is there something wrong with my installation, or is Evolution simply a very hit-and-miss piece of software?

---

### Post by cmost on 2008-08-14
I have a Gmail account and for some reason, no 'sent' messages are being saved at all for me.  I'm running Evolution 2.22.3.1 on Debian Testing.  Fortunately, in my case, a copy is being retained on Gmail (just not a local copy.)  This is strange....  and irritating!!!

---

### Post by anlag on 2008-08-18
> **cmost said:**
> I have a Gmail account and for some reason, no 'sent' messages are being saved at all for me.  I'm running Evolution 2.22.3.1 on Debian Testing.  Fortunately, in my case, a copy is being retained on Gmail (just not a local copy.)  This is strange....  and irritating!!!

Have you checked the setting under Edit->Preferences->Mail Accounts->Edit->Defaults->Sent Messages Folder? I'm not sure how it's supposed to work with Gmail, I've not tried it.

For me, the problem remains. It seems mostly to occur when on wireless. I just replied to three e-mails and realized none of them were saved in 'Sent'. Without changing any settings, I tried sending three e-mails to one of my other addresses, all three saved! Then try replying to another e-mail I sent to myself, also saves.

The only possible explanation I can think of is that the wireless connection is less solid somehow, for Evolution, and that when I spend more than a short while writing an e-mail it sort of times out on the connection to the IMAP server so it can't save the sent mail on there.

Weird. Not had it with Thunderbird, and I believe unless someone has any suggestion to make, I will simply switch back and (hopefully) avoid the problem that way.

---

### Post by anlag on 2008-08-18
Ah, just had it happen again. Took maybe two minutes to reply to an e-mail and now for the first time noticed the following error message in a corner:

> Error while performing operation.

Failed to append to [email]anlag@imap.acc.umu.se[/email]:Sent: Server unexpectedly disconnected: Connection reset by peer
Appending to local `Sent' folder instead.


Of course, the connection to the server is not disconnected at all, I can check for new e-mails and read whatever folders/mails I like just as before. Nonetheless, thought it might be useful for documentation purposes to give the error message as well.

---

### Post by Smurffette on 2008-09-06
I am also trying to make a switch from Thunderbird, as I attempt to submerge myself into Ubuntu.  I am a complete beginner, and I was also having problems with saving emails.

I realized (thanks to the default settings) that the messages sent are kept in your local sent box.  I tried then to change this to save in the sent box for my imap for my other accounts (including gmail). The problem (that I found) is that when the wireless fades, or for some reason there is an interruption in your connection, then it doesn't know what to do, and it doesn't save.  This is specially true when I use my work email through vpn connections.

To solve this, I reseted to the defaults, and periodically I move them to the respective server boxes.  Is there an easier way to do this? Through sync maybe?

---

### Post by dajhorn on 2008-10-10
I can confirm this behavior with Evolution 2.22.3.1 on Hardy.  (I found this forum post when I was searching for a bug ticket.)

Evolution is losing data by failing to copy some outbound messages to the designated remote IMAP folder after staging them in the local Sent folder.

I can provoke the bug by having the IMAP server disconnect during copy or report "try again later, I'm too busy".  Evolution will drop the message and report false success.

---

### Post by drsar on 2008-11-24
Confirmed for Evolution on Dapper Drake.

A flaky work-around is to request a reconnection to the server manually (hit Send/Receive button) just before you submit your send message. Might also just be wishful thinking that it occurs less often.

Is there a bug report / ticket anywhere?

DrSAR

---

### Post by egran2ca on 2009-08-01
I know this is an old thread, but I've just come up against the same problem (using Ubuntu 9.04 & Evolution 2.26.1) and have found a work-around.

I created a filter on **Outgoing** messages, entering all my email addresses as Conditions for Sender, and had the messages **copied** to a new folder (I called it Copy of Sent). Now, when I send messages a copy gets put in the new folder even tho' it doesn't appear in the Sent folder.

Hope this helps someone else.

Eleanor

---

### Post by Dullstar on 2009-08-01
Personally, I think it's best to find an email provider with a nice interface built in as opposed to an email client program.

---

### Post by alfh on 2009-09-14
So far I've been using the webmail client of my isp, but wanted to give evolution a try.

Running the default installation on Ubuntu 8.0.4, I have a similar problem: Evolution is not saving sent mail to the imap folder, even if the settings specify to do so. All sent mail is saved in the local "outbox" and I have to manually move them to the imap folder.

Some previous posters reported the problem might have to do with being on wireless connection (I am), but I received no error messages.

Not interested in looking for workarounds, moving on to test Firebird.

---

### Post by alfh on 2009-09-14
So I set up Thunderbird and tried to send mail. I got an error message! Then I was able to check and correct the send mail options, which also applied to Evolution.

But: Now Evolution decided I'm not allowed to view all messages in my inbox. The counter says 575 messages, however right-clicking and selecting properties says 602 messages in folder. (Thunderbird displays all of them just fine.)

This happened after doing a search. After resetting the search form, all unread messages are hidden, somewhere.

---

