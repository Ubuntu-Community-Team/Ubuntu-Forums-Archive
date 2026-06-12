---
title: "No notification emails for subscribed threads"
date: 2009-02-26
forum: Forum Feedback &amp; Help
---

### Post by smbm on 2009-02-26
Hi

I don't seem to be getting any notification emails about threads I've subscribed to.

Anybody able to have a tinker and see if they can get them working again?

Cheers

---

### Post by smani on 2009-02-26
Look at "Thread Tools", just above the first post.

---

### Post by smbm on 2009-02-26
I'm aware of how to subscribe to threads and check subscriptions.

The problem is that the emails are apparently* not being sent despite activity on the threads that I'm subscribed to.

Thanks anyway though.

* That is to say they are not arriving at my inbox. I've also checked my spam box just in case too.

---

### Post by jenkinbr on 2009-02-26
Did you explicity set the thread subscriptions to send an e-mail notification?  go to [http://ubuntuforums.org/subscription.php?do=viewsubscription](http://ubuntuforums.org/subscription.php?do=viewsubscription) .  You should see your subscriptions.  Under the notification column, it should tell you how you will be notified.  if it shows 'none' (as mine do*), you will not be notified. 

If you see 'none', but want e-mail notification, put a check in the box next to the messages you want notifcation for.  At the bottom of the page, there is a dropdown list that defualts to 'move to folder...'. Click this dropdown, and you will be presented with different actions, the bottom four are notification types.

In the future, when you subscribe to a thread through thread tools > subscribe to thread, be sure to set your notifaction to whatever you want on the page that comes up.

If you do have something other than 'none' listed, we have a diffent issue.

I just set instant notification on a rather popular thread.  I will post back when i get notified of a reply, or if that notification never comes.
(* I check my user control panel frequently, so I have disabled E-mail notifications)

---

### Post by smbm on 2009-02-27
I always set mine to instant as I usually only use it for threads I have posted in and am waiting on a reply.

It started working over night anyway so I guess this is moot now.

Thanks everyone.

---

### Post by jenkinbr on 2009-02-27
Glad to here it's working now.  It worked for me.

---

### Post by bapoumba on 2009-02-27
@ smbm: notifications are sent only for the first reply _after you log out_ and not for all the other ones. Once you log in, email notifications are sent for each reply.

Please report again if you have trouble. It's fine here for me but I recall (long ago) it stopped too and there was a smart and magic tweaking admins had to perform :)

---

### Post by jenkinbr on 2009-02-27
Apparently, there's an issue with the forums php mail() function, or something.  Check out the Res Center to see what I mean.

...or I'll tell you - 5 users without activation e-mails.

---

### Post by bostonaholic on 2009-02-27
I also did not get an instant email regarding a post that happened about 30 minutes ago.

---

### Post by smbm on 2009-02-27
It's working on and off for me now.

It's not a major deal though.

---

### Post by smbm on 2009-02-27
> **bapoumba said:**
> @ smbm: notifications are sent only for the first reply _after you log out_ and not for all the other ones. Once you log in, email notifications are sent for each reply.

Please report again if you have trouble. It's fine here for me but I recall (long ago) it stopped too and there was a smart and magic tweaking admins had to perform :)

Cheers bapoumba

I wasn't getting *any* forum emails for a time.

Now I'm getting some of the ones I should be getting but not all.

It's not a major problem though.

Thanks for your reply though.

---

### Post by bostonaholic on 2009-02-27
I just got the email about this thread.  So like others have said, it must be working intermittently.

---

### Post by smbm on 2009-02-27
I just got the one from your post (this could be a new fun game).

So I guess it's ostensibly working again.

---

### Post by Elfy on 2009-02-28
I have been getting this off and on over the last couple of days - regardless of whether I am logged in or out I should get at least one mail.

Today - I didn't receive a mail for a thread I posted in - same yesterday.

I wonder if there is something awry somewhere - certainly there appears to be a whole bunch of activation e-mail threads in the RC - perhaps there is a common link here.

---

### Post by bapoumba on 2009-02-28
u-g knows why, and Canonical sysadmins have to do something. I did not receive emails after I logged out yesterday, but looks it is working again since I logged in. One web server is not sending emails (if I understood correctly), and that also explains the series of activation emails problems.

Oh well, it will all get better in the future :)
Hang in there, thanks.

---

### Post by Elfy on 2009-02-28
Cool - as long as it's in the pile with thanks/solved/ignoring forums that's fine :)

I did wonder if there was a common theme - reason for the post in the first place :D

---

### Post by bapoumba on 2009-02-28
> **forestpixie said:**
> Cool - as long as it's in the pile with thanks/solved/ignoring forums that's fine :)

I did wonder if there was a common theme - reason for the post in the first place :D

Not to upset all of you guys, but unless the thanks and solved plugins get rewritten, they probably won't come back. They did cause all the database corruptions some time ago, and none of it happened after they were disabled. These plugins directly access the database. The recent problems are different, and being taken care of.

I miss the solved plugin, very helpful. The thanks plugin was nice, but I can very well live without it. Ignore forums is different, I think. I'll poke admins again to make sure. We also had a one-click plugin to handle spam (ban, move all posts/threads to jail, check IPs and pull other accounts from same IP etc.) that I _really_ miss ;)

---

### Post by jenkinbr on 2009-02-28
> **bapoumba said:**
> Not to upset all of you guys, but unless the thanks and solved plugins get rewritten, they probably won't come back. They did cause all the database corruptions some time ago, and none of it happened after they were disabled. These plugins directly access the database. The recent problems are different, and being taken care of.

I miss the solved plugin, very helpful. The thanks plugin was nice, but I can very well live without it. Ignore forums is different, I think. I'll poke admins again to make sure. We also had a one-click plugin to handle spam (ban, move all posts/threads to jail, check IPs and pull other accounts from same IP etc.) that I _really_ miss ;)
:(

---

### Post by bapoumba on 2009-02-28
Yes, I know, jenkinbr..

For the Solved threads, may be users could add tags. Anyone can add a Solved tag to a thread, so that it does not require to report the thread. Someone suggested it in the Staff area, that could be a good replacement.

---

### Post by jenkinbr on 2009-02-28
> **bapoumba said:**
> Yes, I know, jenkinbr..

For the Solved threads, may be users could add tags. Anyone can add a Solved tag to a thread, so that it does not require to report the thread. Someone suggested it in the Staff area, that could be a good replacement.
That's actually a good idea.  The downside is that anyone could add the 'solved' tag to a thread.  If I wanted, I could do it to this thread.  Even worse, is the OP couln't remove it (unless the OP was a mod)

---

### Post by Elfy on 2009-02-28
I don't know sounds like a good idea - I would love to mark thread's solved that obvioulsy are

and yea - thanks is ok but not as useful

---

### Post by bapoumba on 2009-03-01
> **forestpixie said:**
> I don't know sounds like a good idea - I would love to mark thread's solved that obvioulsy are

and yea - thanks is ok but not as useful

Please feel free to do so. Anyone can add tags to threads.

And "thanks" for your understanding :)

---

### Post by Elfy on 2009-03-01
:D

Now it just remains to be seen if people read tags - smaller and a different colour to stickies - /me thinks it's unlikely :lol:

ps - no e-mail notification here for your post bapoumba

---

### Post by bapoumba on 2009-03-01
> **forestpixie said:**
> :D

Now it just remains to be seen if people read tags - smaller and a different colour to stickies - /me thinks it's unlikely :lol:

ps - no e-mail notification here for your post bapoumba
I got the notification for this post. Gremlins!!

re: tags. We can try and see if people catch on it or not :)

---

### Post by Elfy on 2009-03-01
mmm - gremlins indeed - I got this one 

I'm off to mark everything solved then :)

---

### Post by bapoumba on 2009-03-01
> **forestpixie said:**
> mmm - gremlins indeed - I got this one 

I'm off to mark everything solved then :)
Lol, I did not get this notification :D
May be emails are sent to half of the subscribers to save server loads ? (j/k).

---

### Post by Elfy on 2009-03-01
> **bapoumba said:**
> Lol, I did not get this notification :D
May be emails are sent to half of the subscribers to save server loads ? (j/k).

More likely that it is North and South hemispheres - I didn't get one that time and we are not that far away from each other.

---

### Post by smbm on 2009-03-01
Hmm, I haven't had any from this thread since yesterday. 

I haven't had one for any of the posts on this page.

I'm not that far from the New Forest so I don't think it's geographical ;-)

---

### Post by drubin on 2009-03-01
> **bapoumba said:**
> Yes, I know, jenkinbr..

For the Solved threads, may be users could add tags. Anyone can add a Solved tag to a thread, so that it does not require to report the thread. Someone suggested it in the Staff area, that could be a good replacement.

Great suggestion. I am correct in saying on mods and OP can add tags right?

---

### Post by bapoumba on 2009-03-01
> **drubin said:**
> Great suggestion. I am correct in saying on mods and OP can add tags right?
No no :)
Anyone can, that's the point ;)

Edit: I'm not getting any notifications period :/

---

### Post by Elfy on 2009-03-01
I got one for yours Bapoumba - none for drubin's or smbm's - so that foils the south/north hemisphere thing ...

Must be a ghost in the machine then

---

### Post by drubin on 2009-03-01
> **bapoumba said:**
> No no :)
Anyone can, that's the point ;)

Edit: I'm not getting any notifications period :/

I got this notification. :)

I can't add tags to this thread reason for my assumption. Then i tried one in the PPT section..
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6818723](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6818723)

Also can't add tags...

---

### Post by Elfy on 2009-03-01
I can - you can see it - looks like the english for test.

No notification here though

---

### Post by bapoumba on 2009-03-01
drubin, strange you cannot add tags.. More gremlins ?

---

### Post by smbm on 2009-03-01
I don't seem to be getting Launchpad emails either :(

It's not my week for email notifications.

---

### Post by Arlanthir on 2009-03-01
Also not getting subscription e-mails.

When I click "Thread tools" I always get "Subscribe to this thread". 
I thought it updated to "Unsubscribe to this thread" when I was already subscribed. Probably my mistake though.

---

### Post by Elfy on 2009-03-02
I appear to have received all the missing notifications in one go.

---

### Post by ubuntu-geek on 2009-03-02
> **forestpixie said:**
> I appear to have received all the missing notifications in one go.
The new web server didn't have the correct firewall ports opened. Once corrected pending emails were sent.

---

### Post by Elfy on 2009-03-02
and are still being sent - just came back to edit post - I just got one from the 27th :)

Thanks UG :D

---

### Post by jenkinbr on 2009-03-02
> **ubuntu-geek said:**
> The new web server didn't have the correct firewall ports opened. Once corrected pending emails were sent.
So we're on new hardware?

I suppose that explains the page of activation email issues in the Res Center, too?

Anyways, thands for all the hard work, U-G!

---

### Post by smbm on 2009-03-02
Cheers UG

---

### Post by drubin on 2009-03-02
> **Arlanthir said:**
> Also not getting subscription e-mails.

When I click "Thread tools" I always get "Subscribe to this thread". 
I thought it updated to "Unsubscribe to this thread" when I was already subscribed. Probably my mistake though.

This is a known bug from a while ago. I also thought it was fixed but guess not.

---

