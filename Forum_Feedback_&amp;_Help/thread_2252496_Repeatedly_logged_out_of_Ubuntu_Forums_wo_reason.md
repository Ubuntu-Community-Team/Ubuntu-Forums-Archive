---
title: "Repeatedly logged out of Ubuntu Forums w/o reason"
date: 2014-11-12
forum: Forum Feedback &amp; Help
---

### Post by baudrillard on 2014-11-12
While going from different forum on here (Just by clicking on the forum tab and then choosing an individual forum) I will often get logged out of my account. This happens non-stop. In fact, when I try to post (I write my post and then click submit new thread) I'll sometimes get the message that I need to be logged in to post. Any ideas? I'm using the most recent version of Chrome, with addblock, WOT, and a few other plugins. This is only my second post, but it's extremely noticeable.

---

### Post by coffeecat on 2014-11-12
> **elias13 said:**
> and a few other plugins.

I suggest you check those. Unless you delete cookies you will remain logged in for 24 hours if you don't actively log out.

The only other thing that I can think of that will log you out is if you return from another IP address - that is, if the public IP of your internet connection changes.

---

### Post by baudrillard on 2014-11-12
I legitimately thought that was the problem, but here I am using Firefox  w/ no plugins at all and I'm still getting logged out randomly.

My school's wifi is PEAP based and is encrypted with WPA2-Enterprise.  Would that by any chance have a connection? I'm thinking it may be your  second suggestion, because I'm functionally changing IPs at least every  50 minutes as I switch classes or go back to my dorm. That still doesn't  answer why it would change within a single minute, though. 

(for instance, once I finished typing up this response, I clicked quick  reply and was denied permission bc I'm not registered anymore. I click  "go advanced" and it's the same story. I'm logged out. I then click SSO  Log in, and get directed to the main menu for all the forums. I click on  my profile to go my most recent activity and as I'm sent back to this  thread, I got logged out. This happened now [3] times before I managed  to come back and post successfully. the problem seems to often happen  when I click on a link to a forum/thread.)

---

### Post by coffeecat on 2014-11-12
> **elias13 said:**
> I'm thinking it may be your  second suggestion, because I'm functionally changing IPs at least every  50 minutes as I switch classes or go back to my dorm. That still doesn't  answer why it would change within a single minute, though. 

If I follow you correctly, that IP change would be a local network IP change, not a publicly facing IP change, so that shouldn't make a difference. Unless, for some reason, your school is changing its IP or you go through a different route to the internet when you switch classes.

It might be worth making a note of your external IP before and after you get logged out. The site I use is this:

[http://www.danasoft.com/](http://www.danasoft.com/)

It's a light-hearted one, but it's functional. See what pattern emerges if the external IP does indeed change. Otherwise, I can't think of anything else at the moment.

**Edit**: and no, you won't be able to incorporate the html code in your sig as I've seen on other forums. :) The forum software won't allow you to use functional html code in posts or sigs.

---

### Post by baudrillard on 2014-11-12
Here's an interesting development:

I used the link you sent me and it gave me X IP address.
I refresh the page literally 5 seconds later and it gave me Y IP address, and the difference was so substantial that it said I was closer to a different city than what X gave me.
I did not physically move at all during this.

I'm not using a VPN or anything for clarification.

---

### Post by bapoumba on 2014-11-12
I there any chance you could check with your school network admins ? Their setup maybe.

---

### Post by baudrillard on 2014-11-12
I'm going to walk by the small IT center we have. It must be something unique to the network the school uses, although this is the first website to give me any trouble over it. It's also across OS as well, becuase I'm now switched over to my Ubuntu partition and I'm still experiencing this problem.

---

### Post by bapoumba on 2014-11-12
Yeah, that behavior is between U1 SSO and the forums login, not related to the OS you are using..
We and others do experience it too,

---

### Post by baudrillard on 2014-11-12
Alright, well I unfortunately haven't been able to go today because of studying/tests, so I'll try doing that tomorrow.

However, is there any work around it till I figure out a permanent solution, assuming it exists? Including this post, I've made three responses in the past 10 minutes and it has, **by no exaggeration**, taken at minimum 20 attempts to post them because of the repeat logging out. I love the feedback I'm getting on this website and it's infuriating that I can't responded in a convenient manner, lol.

Another discovery also is that a wired connection makes no difference. I'm honestly not too familiar with IT related stuff, including how IPs specifically work, so I don't know if that should come as a surprise or not. I experience the same level of difficulties using the incredibly fast  LAN connection my school has.

P.s. It's so bad that upon loading the home page after logging in, I was already logged out, hahahahaha. I have to admit that's pretty funny despite the annoyance.

---

### Post by coffeecat on 2014-11-13
I'm sorry to hear of your problems, but if the network you are connecting from is changing its external IP as dramatically and as often as you state, I don't think there is much we can do at the moment, except see below. It would be interesting to hear what your IT people say about this.

Using a wired connection on your internal connection would make no difference. The forum software cannot distinguish what sort of connection you are using internally. What it does is to record your public IP at the time you registered your account, and for every post you make thereafter. So far, there are four distinct IP addresses recorded to your account, 2 each from different subnets. In this thread, your posts #1, #3, #5, and #7 are from the same IP address in one subnet, and post #9 is from another IP in the other subnet. It's interesting that although from your description you were connecting to the internet from different IPs during the period covered between your posts #1 and #7, you managed to land back on the same IP for those four posts. Is there a pattern there that might help? 

By the way, your IPs are considered confidential; only forum staff can view them. For more, see our [Privacy Policy]("http://ubuntuforums.org/showthread.php?t=2231107").

If you can get some sort of explanation from your network admins regarding this apparent pattern of rapidly shifting public IPs, then we could consider involving the Canonical sysadmins to see if there is something that could be done. People have occasionally complained about being disconnected from the forum but, from memory, this has usually had another cause. If an educational establishment has set up its network in such a way that it conflicts with the forum software, then that is something we ought to look into because, apart from this making your use of the forum almost impossible, there may be others who have simply given up without communicating their difficulty.

I have to admit that I have hitherto assumed that it is a security feature of vbulletin that causes one to be logged out when the public IP changes. It is a reasonable assumption, but it could be a very wrong one. Do you have an account on any other forum that uses vbulletin software? It is one of the most popular forum platforms. If you do, can I trouble you to try this out on another forum to see whether this is indeed a vbulletin feature or peculiar to this forum.

I'll end by telling you a little of my own experience. Where I post from, I have access to two different ISPs both of which have assigned a fixed public IP, obviously very different ones. I can swap from one to the other quickly. If I am logged into the forum and switch ISP/IP I am usually logged out and have to log in again. Occasionally I am not and can continue my login session uninterrupted. So far, I have not been able to detect a pattern for when I am or am not logged out.

---

### Post by coffeecat on 2014-11-13
@ elias13, just to add:

> **coffeecat said:**
> 
I have to admit that I have hitherto assumed that it is a security feature of vbulletin that causes one to be logged out when the public IP changes. It is a reasonable assumption, but it could be a very wrong one. Do you have an account on any other forum that uses vbulletin software? It is one of the most popular forum platforms. If you do, can I trouble you to try this out on another forum to see whether this is indeed a vbulletin feature or peculiar to this forum.

I've made a quick test myself. I logged into another forum which also uses vbulletin. I then changed IP by connecting to the other ISP and found that I had been logged out. I also tried this with an account at a forum using the phpBB forum software. Same story - as soon as I changed IP I was logged out.

Although it would be sensible to test further with other forums, this suggests that this probably is a feature of most if not all forums and, if so, there may be nothing that can be done. Nevertheless, see what your IT people's response is - they may have a solution.

---

### Post by bapoumba on 2014-11-13
Thanks for the info coffeecat, I did not know that.

elias13, would you happen to have another internet access point ? Home, a smartphone (not on your school wifi), an internet shop (please do not store your passwords on public computers and clear cache/cookies before you close your session) ? Do you see the same behavior ?

---

