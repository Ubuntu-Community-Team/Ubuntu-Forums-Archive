---
title: "Evolution won't send messages"
date: 2008-09-16
forum: Desktop Environments
---

### Post by SchneiderIS on 2008-09-16
Evolution worked fine for several month and then suddenly stopped sending.  It will receive just fine.  When you hit the send/receive button the progress dialog box comes up and shows the POP completing and then freezes on the SMTP.

One possible issue is the port that the SMTP is checked on.  It worked before so I don't see how this could be an issue but stranger things have happened.  How does one change the port as it can't be done from the preferences page?

This is a problem I have seen posted many times but never see the solution being posted.

Between this, printer issues, and laptop pathetic support I am just about ready to pack it in with running Linux.

---

### Post by chesterelperro on 2008-09-23
I had a similar problem with Evolution on Ubuntu 8.04, but could sometimes send emails.  I checked my old WinXP and could send using the same settings with Thunderbird.  So I switched to Thunderbird on the Ubuntu machine and all was well.

I really liked Evolutions filters and integration with GPG.  But I don't have time to fiddle with it.

---

### Post by Arfdaddy on 2008-09-30
Warning:  Long, boring post follows.  Do not drive or operate heavy machinery while reading it.

I had this problem, and fixed it.  Evolution worked fine in Hardy for a while, and then just stopped sending at all - POP completed, SMTP froze.

The origin of the problem was with my ISP - Comcast, Houston, Texas, USA.  I was using Comcast as my ISP, and a different provider for my email in order to retain my twelve-year-old email address.  Comcast claimed that one of the computers on my internet connection had begun sending spam, and had responded with two measures:  blocking outgoing email traffic to foreign servers, and  changing the port number for its own SMTP server.  I never found anything to account for Comcast's claim, though, and I suspect that they just wanted to make those changes to prevent some spamming in the future - or maybe they were fooled by some hefty uploads around that same time.

Here's what I had to do:
[LIST]
[*]Figure out that Comcast had done it in the first place, by noting that my Windows machine, using Outlook express, had developed similar symptoms.  The Windows machine, which used Comcast servers for POP and SMTP, fixed immediately with a change of SMTP port.
[*]Chat online with a Comcast tech about the problem for a long time.  You can skip this step, since it yielded only red herrings.
[*]Figure out what Comcast had done, by scouring all of the information about my account on Comcast's web pages.
[*]Create a new Comcast identity to be the channel for my outgoing email.
[*]Change the settings to point Evolution's outgoing email to Comcast's SMTP server, with my new identity's username.
[*]Tell Evolution Comcast's port number, by appending a colon and the port number to the SMTP server, like this:  **smtp.server.address:123**, using, of course, the real server name, and the real port number in place of "123."  Evolution apparently uses the default port number 25, unless it finds a different number appended to the SMTP server name with a colon in between.
[*]Tell Evolution to forget the passwords that it had already remembered for the POP and SMTP servers: **File -> Forget Passwords**, in Evolution 2.22.3.1.
[*]Create a new message to send, and try sending it.  **This is a crucial step**, and you're likely to be be misled and frustrated if you don't do it.  Messages that I had tried to send before I corrected the Evolution settings, that were slumbering in the Outbox, wouldn't send even after I had made all the adjustments.  I eventually found that new messages would send, while the old ones never left the Outbox.  To get those old messages to go, I had to drag them to Drafts, reopen them, and send them again.  Then they worked fine.  Since Evolution had forgotten the passwords, It asked me for them again.  Make sure that you have them handy, or you'll just be annoyed.[/LIST]

If you've made adjustments to Evolution's settings, and are trying to test those new settings by sending messages that are already in the Outbox, you won't be successful, and will think that Evolution is still broken.  Either delete those messages and make and send new ones, or drag them to Drafts and try to send them again.  If you're hoping that they will exit the Outbox when you get the settings right, you'll be disappointed.

There - I think I've addressed all the issues that you raised:  
[LIST=1]
[*]How the SMTP port could be the issue after it had previously been OK.
[*]How to change the port on the "Preferences" page.
[*]The lack of solutions on the web - this is a solution to the problem that you described, and, while it's my hope that it works for you, it may not be your solution.  As usual, your mileage may vary.
[*]"... pathetic support ..."  Hey!  What am I, chopped liver?  I'm staying up late, just to write this for you.
[/LIST]

This is a frustrating problem.  Good luck.

---

### Post by SchneiderIS on 2008-09-30
I recently found that my host was causing problems for my iPhone e-mail and switched away from GoDaddy as a result.  In the shift I also learned about how to specify the port (wish that was more obvious) and now things appear to be working properly.  So,  would say that your post, though not completely applicable to my situation, is bang on the mark for the provision of the port number.  It seams that the documentation for Evolution does not make the specification of the port number most clear.   Actually I think there should be a specific field for specifying the port as that is a critical part of any account setup, from my opinion.

Thanks again.

Now only if I could get a printer issue working.

---

### Post by scholzfs on 2008-10-24
In Arfdaddy's instructions it says:
Create a new Comcast identity to be the channel for my outgoing email.

Does this mean that I will need to get a new comcast e-mail address?
I would like to keep just one e-mail address, if possible.

---

### Post by Arfdaddy on 2008-11-16
scholzfs writes:
> In Arfdaddy's instructions it says:
Create a new Comcast identity to be the channel for my outgoing email.


Those aren't exactly instructions.  They're a list of things that I had to do, with my particular setup, to get my email working again.  You may have to do more, fewer, or different things if you're facing a similar problem.

I was using a non-Comcast email account, with non-Comcast servers.  Comcast, as my ISP, was transporting my email to and from those foreign servers; however, the actual emailing was handled by the foreign servers.  Comcast determined, in a mysterious way that hasn't ever been explained, that a computer on my account had been hijacked and was sending spam, and that they had made some changes to my account setup to prevent further problems.  I never found any evidence of anything wrong with either of our machines, and I looked pretty hard.  I suspect that their claim was just some baloney they made up to get me to make adjustments to my account.

Comcast told me to change the port number on the outgoing server - and that was a bit of a trick, since the specification of the port number doesn't show up in any of the Evolution documentation that I was able to find.  What Comcast didn't tell me was that they had also begun blocking email traffic from my house to foreign outgoing servers, so I could no longer use my original outgoing server to send email.

In order to send email, I had to go through a Comcast outgoing server.  To do that, I needed a username and password that Comcast would recognize and honor.  I had never established a Comcast email address, so I had to create a new Comcast identity to host my outgoing email transmissions.  That's the new Comcast identity that I was talking about.

I still only use my old email address.  I still receive email from my old server, and people still reply to me there.  No one ever sends email to my Comcast address; if they did, I'd never know, since Evolution isn't set up to check the Comcast address for messages.  My email works just like it did before all this happened.

I infer from your post that you already use Comcast for your email.  If that's so, then you needn't establish a new Comcast address - just use the one you already have.  I'm betting that all you really have to do to get it working - if you haven't already - is to adjust the port number on the outgoing server.  The technique is explained in the September 30 post, in the item that begins, > Tell Evolution Comcast's port number, ... 

I'm also guessing that you've already gotten your email working again, since it's three weeks since you posted as I write this reply.  Here's hoping that it's working well for you.

---

### Post by Swagman on 2008-11-18
Apparently it's a known bug.  It happened on my daughters machine and my mates laptop.

Cure is simple

File----> Work online <--- For some inexplicaple reason "offline" gets selected.

Even if Online is selected... click it a couple of times.

My issue, however is... I cant get the layout back to the way I like it.
I clicked Calender and now the buttons are horrible down the bottom. No matter what I do I cant get them all vertical.

It used to configure ok in 8:04.1

Not that it's a showstopper but it does piss me off !!

[IMG]http://i261.photobucket.com/albums/ii45/Outcast_Aussie/evo1.jpg[/IMG]

---

