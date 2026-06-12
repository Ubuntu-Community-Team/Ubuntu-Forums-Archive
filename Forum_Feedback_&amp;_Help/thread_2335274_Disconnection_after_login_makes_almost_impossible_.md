---
title: "Disconnection after login makes almost impossible my use of UF"
date: 2016-08-27
forum: Forum Feedback &amp; Help
---

### Post by Cbhihe on 2016-08-27
Hello,
I am constantly being disconnected from Ubuntu Forum after I log in.
Here is a description of the problem:

- Click on "Login with SSO"
- New page: "you are about to be redirected to your SSO provider"
  Click "Continue"
- New page: "Personal Data Request"
  Click on "Full name"
  Click on "Yes, log me in"
- Check that I am correctly logged on.
  i.e. my username "Cbhihe" shows at the top of the page.
- Select a forum by clicking on its link on the :
  e.g. "Forum Feedback & Help"
- See that as a new page appears I am disconnected from my account
  i.e. a new page appears with the selected forum's latest posts, but my username is replaced with "Login with SSO".... ?????!

This occurs whenever I click on something that sends me to another page: e.g. clicking on "preview", on "go advanced", on "Submit"... Anything will do it. It is as if cookies had zero permanence.
In fact in order to post in a thread (new or not), clicking on "Submit" after redacting a post will usually disconnect me and make me lose the redacted content. I write "usually" because once out of 5, I can post. The remaining 4 times, I just have to try again. That means log again, go to the right forum, paste the redacted blurb in a new reply field (if I had the presence of mind to commit it to copy/paste buffer before being disconnected) and submit again, and again and again, and ... post.

[CENTER][SIZE=2]*At this point any suggestion would be helpful.*[/SIZE]
[/CENTER]
 
I used Fx v45.0 on Trusty 14.04.4 Desktop LTS with:
 - "don't track me" enforced
 - cookies permanently allowed for ubuntuforums.org
 - Noscript enabled  (I.e.: javascript generally blocked and [ubuntuforums.org]("http://ubuntuforums.org") whitelisted).
 - from behind a simple firewall setup with `ufw`
 - from behind a proxy

***This here is my 6th attempt at posting the above.***

---

### Post by &amp;KyT$0P# on 2016-08-27
> **Cbhihe said:**
> cookies permanently allowed for ubuntuforums.org
What cookie-related extensions are you using?
Does it work if you disable all of them and set the browser to accept first-party cookies only?

> Noscript enabled (I.e.: javascript generally blocked and ubuntuforum.org whitelisted).
You mean ubuntuforum**_s_**.org right?
If so, I know the problem is not related to NoScript as I have the same configuration.

---

### Post by Cbhihe on 2016-08-27
Hey halogen2, thank you for taking the time.

The funny thing is I don't have any cookie-blocking extension, save *Noscript* which has this capability.

By default I just enforce a strict "no third party cookies ever" policy for *Firefox* with very few exceptions. One of them is [ubuntuforums.org]("http://ubuntuforums.org") (typo corrected - thanks), that I whitelisted 3 days ago, not just in *Noscript* but also directly in Firefox, so all of UF's own (1st-party) cookies are accepted and retained from one session to the next. 
I do have AdBlockPlus, but this is unrelated to cookies and in any case, yet again, UF is whitelisted there.

When  I started troubleshooting, I did turn off the handful of extensions I  use and re-enabled them one by one with a Firefox restart each time. No  luck. 

I thought maybe this could in some strange way be related to my onion proxy.  Just as on 2 of my other boxes *privoxy* is at work here ...

I have several boxes with practically identical setups (vastly different  hardwares though). Just this one acts up very strangely and _only  when visiting [ubuntuforums.org]("http://ubuntuforums.org")_. That is the reason I decided to mention that in a post here ... It's annoying and just not getting it makes it even more so.

Maybe somebody will read this and a bell will ring however faintly...

---

### Post by &amp;KyT$0P# on 2016-08-27
> **Cbhihe said:**
> The funny thing is I don't have any cookie-blocking extension, save *Noscript* which has this capability.
With ubuntuforums.org being served over https, NoScript can't do this unless you have a custom ABE rule set to be able to Anonymize requests to ubuntuforums.org.  Is that the case?

> By default I just enforce a strict "no third party cookies ever" policy
That's what I do too, but I don't set exceptions.

> I thought maybe this could in some strange way be related to my onion proxy. Just as on 2 of my other boxes privoxy is at work here ...
Those are where I'd suggest to look for the issue, as I don't use either.

> I have several boxes with practically identical setups
So something you could try, as a test, is to copy an entire [profile]("http://kb.mozillazine.org/Profile") from a working box into a new profile on the non-working box: **completely quit Firefox before copying or replacing profile**, also delete any existing contents of the new profile before replacing.  Then check it there, does it work?

---

### Post by Cbhihe on 2016-08-28
> **halogen2 said:**
> With ubuntuforums.org being served over https,  NoScript can't do this unless you have a custom ABE rule set to be able  to Anonymize requests to ubuntuforums.org.  Is that the case?
Right on the dot. No, I have no custom ABE rule. Too time-consuming to tweak for a security-noob.
I  have also turned off the https-active-web-content prohibition as it may  impact local links in UF (not sure about that), even though it is  recommended by NoScript (See tab "Advanced properties / HTTPS") to  uphold that prohibition for https with proxied setups and tor.  

> **halogen2 said:**
>  Those [Privoxy +Tor] are where I'd suggest to look for the issue, as I don't use either.
Had that hunch too, but rejected it because, as mentioned earlier, two other boxes do not generate the same trouble.
So,  I am going to try something I usually do as a last resort: stop  proxying for UF pages. I can introduce an exception either in Firefox itself  and Privoxy will honor it, or directly in Privoxy
That should give me some clues by which to go. Will report soon here.

> **halogen2 said:**
>  So something you could try, as a test, is to copy an entire [profile]("http://kb.mozillazine.org/Profile") from a working box into a new profile on the non-working box: ***completely quit**** completely quit Firefox before copying or replacing profile***, also delete any existing contents of the new profile before replacing**...**OK that will be next.

---

### Post by Cbhihe on 2016-08-28
OK, just checked that with all proxy off, simply refreshing the page (while logged in on UF), logs me out automatically. So it has nothing to do with proxying and I proceed to lift my proxy exception. 
Next I will try the profile route indicated above.

EDIT: actually I'm confused. I tried refreshing the page more times while logged in on UF, and even though doing so logged me out _the first time_, it did not on subsequent times with proxy off.

---

### Post by deadflowr on 2016-08-28
If your IP address changes you automatically get logged out of the forums.
Cookie or no cookie.
Take look at this site: [http://www.whatsmyip.org/]("http://www.whatsmyip.org/")
Open it and in another tab/window try logging into the forums.
Take note of whatever the IP shows for you when you login, and when you try to refresh the forums and get the logout go back to the whatsmyip page and refresh that and see if their is a change in the address.

Reference an older thread same basic issue:
[https://ubuntuforums.org/showthread.php?t=2252496]("https://ubuntuforums.org/showthread.php?t=2252496")

---

### Post by Cbhihe on 2016-08-29
@deadflowr: 
Thanks for yr reply. As I logged in and read yr post I had client-IP#1 (as revealed by [http://www.whatsmyip.org/](http://www.whatsmyip.org/)). I immediately hit the "Advanced Reply" button below yr post, and was ipso facto disconnected from UF.
I then refreshed my still open page at [http://www.whatsmyip.org/](http://www.whatsmyip.org/)  and got client-IP#2 (same country, different city and exit node).

So   my being constantly disconnected is probably related to IP changes,  and rather unstable exit nodes with little permanence. I am not going to  quit using tor/privoxy for that matter, maybe find exit nodes with less  variability ? Right now I have my setup optimized for always  prioritizing lowest latency. It might be the reason.

I'd be  curious to know though, if there is a workaround to set UF servers up,  so a login client session is identified based on client cookies and not  on login-connection IP  
I suppose identifying client by IP during a  login session is safer than doing so via a cookie, although in reality  both can be spoofed, I guess. (although ... that would be difficult  through a MITM for https connections). But I'm rambling.

Thank you for your collective help,
-ced

PS: I will mark this thread solved as soon as you've acknowledged this last post.

---

