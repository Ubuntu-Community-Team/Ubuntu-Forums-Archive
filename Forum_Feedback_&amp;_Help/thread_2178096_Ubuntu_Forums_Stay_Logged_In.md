---
title: "Ubuntu Forums Stay Logged In"
date: 2013-10-01
forum: Forum Feedback &amp; Help
---

### Post by Prime624 on 2013-10-01
I didn't know where to put this, so I'll try here. Is there a way to stay logged in to these forums even after restart?

---

### Post by QIII on 2013-10-01
*Moved to **Forum Feedback & Help***

---

### Post by deadflowr on 2013-10-01
> **Prime624 said:**
> I didn't know where to put this, so I'll try here. Is there a way to stay logged in to these forums even after restart?

Unfortunately, no.
At least at the moment.

but hopefully they'll get a fix soon.
Or at least some sort of fix for the login redirect to the forum home page.

---

### Post by DuckHook on 2013-10-01
Ever since the login process was cracked a few weeks ago, I believe your login now times out after x minutes of inactivity and also does not persist after a browser is closed.

---

### Post by tgalati4 on 2013-10-01
I wish they would fix this.  The login process takes too long.  The login period needs to be longer (4-8 hours).  This forum is becoming more difficult to use.

---

### Post by cariboo on 2013-10-02
> **tgalati4 said:**
> I wish they would fix this.  The login process takes too long.  The login period needs to be longer (4-8 hours).  This forum is becoming more difficult to use.

So do we, the moderation team has even shorter time limits for some of the administration functions than regular members, which we all find very frustrating, We are at the mercy of Canonical IS when it comes to fixing problems, so all we can do is keep reminding them of our several outstanding issues.

---

### Post by DuckHook on 2013-10-02
> **cariboo907 said:**
> ...all we can do is keep reminding them of our several outstanding issues....but... but... but... given your avatar, you *like* the zombie apocalypse...

---

### Post by Elfy on 2013-10-02
I have actually just bumped the ticket for this and the e-mail change needing a password that no-one knows anymore ... 

I cc'd the Community Council in to them both, perhaps they'll realise that there's rather a large lump of community here being wound up like tops again.

---

### Post by R33D3M33R on 2013-10-06
> **tgalati4 said:**
> I wish they would fix this.  The login process takes too long.  The login period needs to be longer (4-8 hours).  This forum is becoming more difficult to use.

+1. The thing that bothers me most is, that login takes you back to the first page. Of course, the constant logouts are also annoying. Judging by the experience at Launchpad bug reports, these bugs will never get fixed. If they had the intention to fix this, they would do this right after the SSO was implemented ...

---

### Post by cariboo on 2013-10-06
> **R33D3M33R said:**
> +1. The thing that bothers me most is, that login takes you back to the first page. Of course, the constant logouts are also annoying. Judging by the experience at Launchpad bug reports, these bugs will never get fixed. If they had the intention to fix this, they would do this right after the SSO was implemented ... 

I'm not sure how you figure it is an Ubuntu problem, the problem is with vBulletin and Canonical IS. No Ubuntu developers are involved.

---

### Post by R33D3M33R on 2013-10-06
I'm not blaming Ubuntu developers, where did you get that from? I'm just saying that Canonical is lacking people (and they probably don't have unlimited cash), and if they didn't fix it right away, it will probably not be fixed at all. That's all ...

---

### Post by mc4man on 2013-10-12
> **Prime624 said:**
> I didn't know where to put this, so I'll try here. Is there a way to stay logged in to these forums even after restart?

You can if you edit ubuntuforums.org  > bb_sessionhash cookie & set it to expire on a date, which date is not that unimportant due to below.
.
Overall it's not that useful as it's limited to the 2 hr. time out so one needs to revisit the forum within 2 hrs to then get another 2 hrs grace period.
If the time out was increased then it would be a bit of a decent workaround

(I've found it only works correctly in FF in linux, FF in windows remains on session even when the cookie is edited.

---

### Post by hloeung on 2013-10-21
Hi Guys,

I've been looking into how to get the "Remember me" feature working with OpenID/SSO. Should hopefully have this implemented shortly.

I've also increased the vBulletin session timeout from 2 hours to 6.


Regards,

Haw

---

### Post by cariboo on 2013-10-21
Thanks hloeung, we appreciate the work you're doing for us.

---

### Post by Cavsfan on 2013-10-21
That is great hloeung! I was wondering if this was forgotten.

Oddly Chromium requires me to login 2 times. I go through the 4 step process and the first time it goes back to the initial login screen.
I have to do the 4 step process a 2nd time then I am in. I had gotten used to this method but it will be fantastic if we could just stay logged in.

Whoot! :)

---

### Post by coffeecat on 2013-10-21
> **Cavsfan said:**
> 
Oddly Chromium requires me to login 2 times. I go through the 4 step process and the first time it goes back to the initial login screen.
I have to do the 4 step process a 2nd time then I am in. I had gotten used to this method but it will be fantastic if we could just stay logged in.


I'm not seeing this with Chromium. Login via SSO with Chromium is the same for me as in Firefox. You might want to check whether any of your browser settings are causing a problem here.

---

### Post by tgalati4 on 2013-10-21
Thanks for the temporary work-around.

---

### Post by Cavsfan on 2013-10-21
> **coffeecat said:**
> I'm not seeing this with Chromium. Login via SSO with Chromium is the same for me as in Firefox. You might want to check whether any of your browser settings are causing a problem here.

Yeah thanks coffeecat. :) I figure it's some addon causing the problem. I've got Ghostery, Vanilla which is a cookie handler and some others.
 The problem is not in Precise but, it happens on one of my installs not sure which one.

Firefox never causes this problem. It's not really a big deal but, thanks! :D

Just super happy that this login problem is going to be fixed. I know you admins have a tougher problem than regular members so it will be really great for you!

---

### Post by deadflowr on 2013-10-22
So I closed my browser a few minutes ago and reopened it, and came back to forums and I was already logged in.:P

I thought I was going senile, so I did it again, and same result.

Hopefully it's a start to a fix.

Hopefully it sticks, nice work.

---

### Post by hloeung on 2013-10-23
> **deadflowr said:**
> So I closed my browser a few minutes ago and reopened it, and came back to forums and I was already logged in.:P

I thought I was going senile, so I did it again, and same result.

Hopefully it's a start to a fix.

Hopefully it sticks, nice work.

Yes, the fix is in place and it's going to stay this way :)

---

### Post by deadflowr on 2013-10-23
> **hloeung said:**
> Yes, the fix is in place and it's going to stay this way :)

You're golden.

---

### Post by Irihapeti on 2013-10-23
> **hloeung said:**
> Yes, the fix is in place and it's going to stay this way :)

Three cheers! :guitar:

---

### Post by zika on 2013-10-23
Whoever fixed login and made it stick has my deepest gratitude...

---

### Post by ajgreeny on 2013-10-23
> **Irihapeti said:**
> Three cheers! :guitar:

Hip hip hooray!
Hip hip hooray!
Hip hip hooray!

Just what we all seemed to want, and at last it's here!  Brilliant!!!

---

### Post by Cavsfan on 2013-10-23
> **Irihapeti said:**
> Three cheers! :guitar:

How sweet it is indeed! I logged in this morning just after 7, left for an hour or two and just clicked on the forum and I was still logged in. :popcorn:

Oh Yeah! :D

---

### Post by SeijiSensei on 2013-10-23
As someone who requested this change in a couple of postings, I can only say "Thank you!"  For those of us who visit the Forums a few times a day, this is great improvement.

---

### Post by oldos2er on 2013-10-23
> **hloeung said:**
> Yes, the fix is in place and it's going to stay this way :)

Lovely, thank you.

---

### Post by CharlesA on 2013-10-23
> **hloeung said:**
> Yes, the fix is in place and it's going to stay this way :)

Sweet! I was wondering why I was logged in after I shutdown my laptop. Thanks!

---

### Post by Cavsfan on 2013-10-24
I last logged in yesterday and there was no need to login today! Whoot! I take it the admins are better off too?

---

### Post by iX9 on 2014-05-13
What about today? HOW-TO stay logged in permanently on diferrent PCs?

---

### Post by Cavsfan on 2014-05-13
> **iX9 said:**
> What about today? HOW-TO stay logged in permanently on diferrent PCs?

Shoot I have to do the login thing when I switch OSs on the same PC in a matter of minutes. 
It's not that big of a deal at least to me. A few clicks and I'm good for a day.

---

