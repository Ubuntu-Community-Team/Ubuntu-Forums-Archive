---
title: "&quot;HTML code is Off&quot; - can it be turned on?"
date: 2010-06-06
forum: Forum Feedback &amp; Help
---

### Post by sdaau on 2010-06-06
Hi all,

Typically below each page on ubuntuforums, there is the message "HTML code is Off" - I am guessing this does not refer to wrapping stuff in   	 [noparse][html]*[/html][/noparse] BBCode tags (which would simply apply HTML syntax coloring to a code snippet) :) 

So I was wandering - is this somehow possible to enable it? What I'm missing is a horizontal rule ([noparse]<hr/>[/noparse]), and it seems there is no BBcode equivalent for it.. 

Cheers!

---

### Post by new_tolinux on 2010-06-06
> **sdaau said:**
> Hi all,

Typically below each page on ubuntuforums, there is the message "HTML code is Off" - I am guessing this does not refer to wrapping stuff in        [noparse][html]*[/html][/noparse] BBCode tags (which would simply apply HTML syntax coloring to a code snippet) :) 

So I was wandering - is this somehow possible to enable it? What I'm missing is a horizontal rule ([noparse]<hr/>[/noparse]), and it seems there is no BBcode equivalent for it.. 

Cheers!
I guess the moderators could turn it on, but they probably won't.
As you probably know, allowing HTML is a potetial security risk.

There's indeed no BB-code equivalent to <hr/> but you can always use a bunch of underscores (________________) or dashes (-------------------) to separate 2 or more things from another.

Besides that, I guess the <TABLE> functionality is missed more than the <HR>-function.

---

### Post by sdaau on 2010-06-06
Hi new_tolinux,

Thanks for the reply!

> **new_tolinux said:**
> I guess the moderators could turn it on, but they probably won't.
As you probably know, allowing HTML is a potetial security risk.


Ok, I see - I thought, maybe there is some sort of a "super user" in the forum which actually can use HTML, and then that notification there serves to inform you of your status :) 

Also totally agree with you on underscores (ended up using that) - and the table :) 

And I understand the security risk of [noparse]<object> or <script> or <frame>[/noparse], but I cannot see how  [noparse]<hr> or <table>[/noparse] would be security risks; maybe the mods would eventually allow a subset of risk-free HTML? 

Anycase, thanx again,

Cheers!

---

### Post by new_tolinux on 2010-06-06
> **sdaau said:**
> Hi new_tolinux,

Thanks for the reply!
You're welcome :)
> **sdaau said:**
> Ok, I see - I thought, maybe there is some sort of a "super user" in the  forum which actually can use HTML, and then that notification there  serves to inform you of your status
vBulletin (the "software" used for this forum) does allow the admins to enable HTML for specific groups (or everyone) in certain places:
> Allow HTML Code in  posts
This allows users to use HTML while posting. It is **strongly  recommended** that you DO NOT turn this on as it can severely  compromise security and/or severely mess up layout if users insert  malformed HTML. Even if you set this to Yes, users still cannot use  certain tags, including javascript: and about:.> **sdaau said:**
> And I understand the security risk of [noparse]<object> or <script> or <frame>[/noparse], but I cannot see how  [noparse]<hr> or <table>[/noparse] would be security risks; maybe the mods would eventually allow a subset of risk-free HTML? 
I guess the quote above does answer your question.

Edit: I found a thread [here](http://www.vbulletin.com/forum/archive/index.php/t-142478.html) about some BB-codes that could be implemented for tables, which according to "TosaInu" should not mess up the layout, as vBulletin verifies that bb-codes are "closed" properly.
Since <hr> does not need any closing tag (not <hr>sometext</hr>, because it's just a line that has to be displayed) I think that it's not possible to provide a bb-code for that.
A thread about that can be found [here](http://www.vbulletin.com/forum/showthread.php?168885-Add-a-QUICK-bbcode).

---

### Post by Phrea on 2010-06-06
No.
Not for users, if the admins chose to set it that way.
To be fair, none of the admins normally would also not use HTML, and they theoretically can, if they know HTML that is. ;)

It's just a vB setting, vB really should not display it anymore, because no admin will normally ever allow HTML to be used on his/her forum, unless it's only specified tags [like <strong>, <i>, etc] but those are replaced by UBB code, as they are sometimes called [things like [b], [i], etc].

---

