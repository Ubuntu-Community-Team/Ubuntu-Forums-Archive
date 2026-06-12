---
title: "Stale Page?"
date: 2013-08-15
forum: Forum Feedback &amp; Help
---

### Post by LeeU on 2013-08-15
I am trying to log into the forums using the new procedure (I have already been here previously, re-established the account, etc.) but, in Firefox, I keep receiving the following error message:

[I]Your page was stale.

Apologies, the page you came from was a little old. Perhaps you navigated here from a browser window other
than the one you used to login. If so, try using the other browser window. Or, try your action again, starting
from our home page. [/I]

I have cleared the cookies and history but still nothing. I have closed any page remotely related to ubuntu.com or ubuntuforums.com and cleared the cache but **still** nothing. Even inputting the URL directly (so to eliminate the "the page you came from" problem) did no good.

I am able to log in using Chromium but don't really like this browser.

Anybody else have this problem? Anybody know how this can be fixed? I really don't like having to open another browser just to visit the forums.

---

### Post by cariboo on 2013-08-15
This is a known problem with Firefox, because we use a combination of http and https during the login process. Canonical IS is aware of the problem, and it will be fixed when they get around to it.

---

### Post by LeeU on 2013-08-15
Thanks for the quick answer. I appreciate it. I do hope they do see this as important, although your answer doesn't lead me to believe that. (I currently have a problem with the menu in Ubuntu 12.04 LTS -- which is supposed to be supported until near the end of 2017 -- but the problem was only fixed for the versions going forward; they said they won't fix the problem in 12.04 LTS. Oh well....)

It would be great though if this was put into the stickys in the forum and at Ubuntu One, which is where I checked first. It might help others.

Thanks again.

---

### Post by Bucky Ball on 2013-08-15
> **LeeU said:**
>  (I currently have a problem with the menu in Ubuntu 12.04 LTS -- which is supposed to be supported until near the end of 2017 -- but the problem was only fixed for the versions going forward; they said they won't fix the problem in 12.04 LTS. Oh well....)

Not sure who 'they' are but perhaps you can try posting in the forums regarding this, if you haven't already. If there's not a fix, there could be a workaround (like using a more recent kernel in 12.04 LTS, entirely do-able).

---

### Post by LeeU on 2013-08-15
Thanks for the reply. Nice to know someone is listening.

It was reported over in [the bugs section of the launchpad]("https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/716324"). I have resigned myself to live with it; it's not really a big deal, it's just a dividing line in the menu but it is the point of it. And I understand it's a Gnome bug. It just seems that it should have been fixed for 12.04 LTS *instead* of the next version going forward.

You mentioned using a more recent kernel in 12.04 LTS. I currently have 3.2.0-51-generic-pae but now I see that there is a newer version. Why wouldn't I have received a notice of it? I am set-up to receive notice of all security updates immediately and others daily. (Forgive me; I have used Linux for 8+ years and am *finally* beginning to get deeper into the technical aspect of it.)

---

### Post by Dave_L on 2013-08-15
In 12.04 you have a choice of three kernel series: 3.2.x, 3.5.x and 3.8.x. You only get update notices if you install the appropriate metapackage(s): linux-generic (for 3.2.x), linux-generic-lts-quantal (for 3.5.x) or linux-generic-lts-raring (for 3.8.x).

(I think the above is accurate, but someone else should confirm it.)

I'm using 3.8.0-27 on 12.04, and have no problems with it.

---

### Post by coffeecat on 2013-08-16
Keep on-topic, **please**. This thread is about a stale page message in Firefox when trying to log into the forums, NOT about the menu or any other matters to do with Ubuntu 12.04. We need to see if others are experiencing the OP's original problem and will not be able to do so if the thread is submerged in off-topic chatter.

@LeeU, your problem may or may not be related to the issue cariboo907 mentioned. Since I have never seen this myself, use Firefox, log into the forum several times a day, and don't recall others mentioning it, I think it is more likely to be a problem in your browser itself. You might want to try setting a new profile in Firefox and seeing if the problem persists in the new profile. I've never had the need to do this myself but I believe this is how you set a new profile:

[https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)

Also...

@LeeU, a point of information. Canonical IS, who are the sysadmin team responsible for maintaining all the servers owned by Canonical +software running on them, are not the same as the Ubuntu dev team who are responsible for fixing bugs in Ubuntu. Your expression of non-belief based on the progress or lack of it of a single bug in Launchpad is a non-sequitur.

---

### Post by d2btoo on 2013-08-16
[QUOTE=LeeU]Your page was stale.[/QUOTE]
Same here, unless I enable "sendRefererHeader".
Usually sendRefererHeader is set to "0" in my config, however to log in to this forum I need to change it to "2" in about:config (network.http.sendRefererHeader), once logged in I change it back to "0".

---

### Post by coldraven on 2013-08-16
> **d2btoo said:**
> Same here, unless I enable "sendRefererHeader".
Usually sendRefererHeader is set to "0" in my config, however to log in to this forum I need to change it to "2" in about:config (network.http.sendRefererHeader), once logged in I change it back to "0".
I'm not sure about that.
I use the add-on "RefControl" set to fake all Referers and do not have login problems.

In about:config the settings are:

network.http.sendRefererHeader;2
network.http.sendSecureXSiteReferrer;true

I'm using FF 23.0 on Ubunti 12.10

---

### Post by LeeU on 2013-08-16
> **coffeecat said:**
> @LeeU, your problem may or may not be related to the issue cariboo907 mentioned. Since I have never seen this myself, use Firefox, log into the forum several times a day, and don't recall others mentioning it, I think it is more likely to be a problem in your browser itself. You might want to try setting a new profile in Firefox and seeing if the problem persists in the new profile. I've never had the need to do this myself but I believe this is how you set a new profile: [https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles) 

I don't really see any use in creating a new profile when it worked just fine after the forum was brought back up and I went through all the security steps and was in and out of the forum several times after that. AND I have a forum admin telling me there IS a problem they are aware of and are trying to fix. I DO believe that if they are trying to fix something on the forums -- AND they have told their admins about it (though they should inform the mods also) -- that it will eventually be fixed.

> **coffeecat said:**
> @LeeU, a point of information. Canonical IS, who are the sysadmin team responsible for maintaining all the servers owned by Canonical +software running on them, are not the same as the Ubuntu dev team who are responsible for fixing bugs in Ubuntu. Your expression of non-belief based on the progress or lack of it of a single bug in Launchpad is a non-sequitur.

I never said anything about "the servers owned by Canonical +software running on them" nor anything about their system admins. I was talking abut the *Ubuntu SOFTWARE itself*, the operating system on *MY computer*. Why would the company that offers the software be completely different from those who develop it? And why would a company that offers the software make a claim of long term support but then say they have nothing to do with it?

Thanks everyone for your help.

---

### Post by LeeU on 2013-08-16
It seems that setting *network.http.sendRefererHeader* to "2" works. I am using Firefox to post this. Thanks d2btoo! According to [MozillaZine]("http://kb.mozillazine.org/Network.http.sendRefererHeader"):

```

Network.http.sendRefererHeader
Possible values and their effects

0: Never send the Referer header or set document.referrer.
1: Send the Referer header when clicking on a link, and set document.referrer for the following page.
2: Send the Referer header when clicking on a link or loading an image, and set document.referrer for the following page. (Default)

Recommended settings
Those concerned with privacy can set this to 0, realizing that this may adversely affect some sites. Those wanting to ensure compatibility should leave it at the default.
```

"2" is the default. Notice that changing it to "0" can cause problems on some sites. And this was posted back in 2001. Glad we could work together and fix this problem. It might be a good to post this in a sticky but that's up to the admins and mods. Thanks guys!

---

### Post by LeeU on 2013-08-16
BTW, does anyone know why this forum is not using a secure server, especially after the recent hack? It uses http and not https and, in Firefox, there is no padlock in the browser next to the URL to show it is secure. I know that it uses Ubuntu One, etc., but it should still be an https connection and show as being secure.

Anyone got any ideas?

---

### Post by Bucky Ball on 2013-08-16
As far as I understand it, you are logging in via Ubuntu One which does use https, not Ubuntu forums, and your information is kept at Ubuntu One. When you login from there you are asked what information you want to share with Ubuntu forums. That is up to you.

[https://login.ubuntu.com/jGflt64ChMd23b7k/+decide](https://login.ubuntu.com/jGflt64ChMd23b7k/+decide)

See? https. Quite obvious if you had taken a look. There IS nowhere to login on the forums anymore, period. All from secure Ubuntu One account.

---

### Post by whatthefunk on 2013-08-16
> **cariboo907 said:**
> This is a known problem with Firefox, because we use a combination of http and https during the login process. Canonical IS is aware of the problem, and it will be fixed when they get around to it.

I dont think its a Firefox issue.  It happens to me with Opera as well.  Clear all your Ubuntu related cookies from your browser, clear the cache and try again.

---

### Post by d2btoo on 2013-08-17
[QUOTE=LeeU]It seems that setting network.http.sendRefererHeader to "2" works. I am using Firefox to post this. Thanks d2btoo![/QUOTE]
Glad, happy to help. :)

[QUOTE=LeeU]And this was posted back in 2001. Glad we could work together and fix this problem. It might be a good to post this in a sticky but that's up to the admins and mods. Thanks guys! [/QUOTE]
[QUOTE=whatthefunk]I dont think its a Firefox issue. It happens to me with Opera as well. Clear all your Ubuntu related cookies from your browser, clear the cache and try again. [/QUOTE]
I believe they already knew this. Please see [this](https://bugs.launchpad.net/canonical-identity-provider/+bug/1198101) and [this](https://bugs.launchpad.net/launchpad/+bug/560246). (they don't mention ubuntu forum specifically, but I think that because of the forum started using the SSO recently.)

---

