---
title: "Staying logged in to Forums and Bad Request"
date: 2015-04-12
forum: Forum Feedback &amp; Help
---

### Post by Keith_Helms on 2015-04-12
Is there an option somewhere to stay logged in to the forums?  When I'm on public wifi somewhere and the connection drops and I reconnect, I usually have to sign back in.  Is this because my IP address changed?

Also, about every 10th login or so, I get a nice message 
>                                                                                **Bad Request**

         
                    Bad bot, go away! Request aborted.
          
      


And I have to back out and try again.  What is causing this?

---

### Post by jeremy31 on 2015-04-12
I am fairly sure you get logged out when your IP changes and it happends to me frequently, sometimes while writing a post

---

### Post by lisati on 2015-04-12
*Thread moved to **Forum Feedback & Help**.*

---

### Post by sammiev on 2015-04-12
My IP over the day changes so I do have to log back in but I have never got the message you got.

---

### Post by coffeecat on 2015-04-13
Yes - a change in IP means that you have to log in again. 

I've never seen the bad bot message. Is it an Ubuntu One server message or a forum (vbulletin) one? If the former you'll have to ask the Ubuntu One admins. If you're not sure, please grab a screenshot when it next happens and post it.

---

### Post by Keith_Helms on 2015-04-13
I get it when I click on the "sign me in" button, so I imagine it's coming from Ubuntu One.  How do I direct a question to the Ubuntu One admins?

---

### Post by coffeecat on 2015-04-13
> **Keith_Helms said:**
> I get it when I click on the "sign me in" button, so I imagine it's coming from Ubuntu One.  How do I direct a question to the Ubuntu One admins?

Not necessarily. After clicking on the log me in button you are immediately taken to a vbulletin (forum) page. Please provide a screenshot if you can get one. I can't find any portion of "Bad Request Bad bot, go away! Request aborted" in the vbulletin setup for the forum, but let's be sure that this isn't coming from the forum.

---

### Post by Keith_Helms on 2015-04-13
I will try and do a screen capture the next time it happens.   It might be a few days.

---

### Post by johnaaronrose on 2015-04-14
For approx 2 months, I have usually not been able to SSO login under Firefox. I get a page displaying:Bad Request
Bad bot, go away! Request aborted.

Ubuntu login support are not able to help. They suggested that the problem might be a Firefo extension. I have disabled all Firefox extension and the problem still occurs. However, logging in using Chromium always works. Any ideas?

---

### Post by coffeecat on 2015-04-14
Strangely, someone else has reported this bad bot message only a day or so ago. I've never seen it myself - and I am using firefox - and I don't remember anyone reporting this before the other person did. 

It would be helpful if you could post a screenshot when this next occurs. It's not yet clear whether this is a message being displayed by Ubuntu One SSO or the vbulletin software we use.

Also - do you know if your IP is fixed or dynamic? If dynamic, is it prone to change often?

---

### Post by johnaaronrose on 2015-04-14
I'm using Firefox 37.0.1 under Ubuntu Trusty on both my desktop & laptop, with both having the same issue. My ISP supplies me with a Static ip address. Screenshot attached.

---

### Post by Keith_Helms on 2015-04-14
Okay, so once in a while after I click on the Login with SSO button and the next screen titled "Personal Data Request" comes up and I click on the "Yes, Log me In" button there, I get the attached back.

---

### Post by coffeecat on 2015-04-15
@johnaaronrose and @Keith_Helms thank you for posting your screenshots. I've merged your two threads since they are essentially about the same thing &#8211; the &#8220;Bad Request Bad bot, go away! Request aborted&#8221; message. Your screenshots tell us that the message is coming from the Ubuntu One server and it is interesting that the Ubuntu One servers were delivering the same message as a bug with Software Centre purchases earlier this year:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1413665](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1413665)

That, of course, is not directly relevant to the forum and, although that bug is marked fix released, there is obviously still an issue at Ubuntu One SSO, now affecting forum login. 

I'll discuss this with the other forum admins. In the meantime if either or both of you could contact Ubuntu One admins and provide them with your screenshots and a link to this thread, that would be helpful. I'll see if I can find a link for that.

---

### Post by johnaaronrose on 2015-04-16
What is the link/email to contact Ubuntu One admins?
PS I think that I might already have done so in that I've been having an unresolved email correspondence with login support at Canonical (login-support@canonical.com).

---

### Post by bapoumba on 2015-04-16
> **johnaaronrose said:**
> What is the link/email to contact Ubuntu One admins?
PS I think that I might already have done so in that I've been having an unresolved email correspondence with login support at Canonical (login-support@canonical.com).

From [https://help.ubuntu.com/community/ISD](https://help.ubuntu.com/community/ISD) as it does not fall under any listed Q, I'd say [email]isd-support@canonical.com[/email]

---

### Post by johnaaronrose on 2015-04-21
Sent email to [EMAIL="isd-support@canonical.com"]isd-support@canonical.com[/EMAIL] on the 16th. No reply.

---

### Post by Elfy on 2015-04-22
They do take a while it seems - even a mail to them from the FC took weeks to get a response

---

### Post by Keith_Helms on 2015-06-09
Any update on this?  I still get that stupid "Bad bot, go away! Request aborted." error every now and than.

---

### Post by QIII on 2015-06-09
You may want to send an email to the address in post #16.  There is really nothing else we can do here.  We don't administer Canonical's servers.

---

