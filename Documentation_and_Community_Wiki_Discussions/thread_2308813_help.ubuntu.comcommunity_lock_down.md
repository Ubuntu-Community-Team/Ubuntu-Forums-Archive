---
title: "help.ubuntu.com/community lock down"
date: 2016-01-05
forum: Documentation and Community Wiki Discussions
---

### Post by Doug S on 2016-01-05
Please be aware of a lock down on the help.ubuntu.com/community pages, due to sabotage. Below is a copy of an e-mail to the doc team e-mail list:

Subject: Community Help Wiki locked down (was: Re: Fwd: Fwd: WikiGuide destroed by spammers)

On Sat, Jan 2, 2016 at 10:34 AM, Elizabeth K. Joseph <lyz@ubuntu.com> wrote:
> There are thousands of pages and it looks like this started on
> December 23rd. I'm not going to spend my whole day deleting pages when
> the spam accounts keep being created. Endless, time-wasting war with
> bots.
>
> I've submitted a ticket with Canonical IS (#27950) to see what they
> can do on the administrative side to shut this down.

I have good news and bad news about our [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) wiki.

Good news: The thousands of spam pages that were created have been
deleted and purged by Canonical IS. Thanks to Ryan Finnie of Canonical
for handling this so quickly after their holiday break! There were
also some spam edits on existing pages that Pasi (knome) took care of.
Please let us know if you find any more and we'll work to take care of
them.

Bad news: In order to triage this attack, the wiki has been locked
down. Right now, only members of these two groups now have access to
editing:

[https://help.ubuntu.com/community/EditorGroup](https://help.ubuntu.com/community/EditorGroup)
[https://help.ubuntu.com/community/AdminGroup](https://help.ubuntu.com/community/AdminGroup) **

They suggested we also set up a ContributorGroup of known users who
contribute that can still edit even when the wiki is on lock down.
This seems like a reasonable thing, but it does mean administrative
overhead.

I don't know how long the lock down will last, and right now I'm not
sure how logins look to folks not in EditorGroup or AdminGroup. That
may be worth testing by someone not in those groups, it would be good
to know if they are able to log in at all, or if it just shows all
pages as Immutable.

Given all of our problems generally with this help wiki and logins
since the switch to Ubuntu SSO, the overall future of this wiki may be
worth a discussion.

-- 
Elizabeth Krumbach Joseph || Lyz || pleia2

** for unknown reasons the AdminGroup list is showing some Russian text for non members. Members (which I am not) see the actual AdminGroup list, if they are logged in.

---

### Post by CharlesA on 2016-01-05
I just tested logging in and it seemed to work for me. I have no clue what user groups I am in though.

Thanks for the update! That is pretty insane imo.

---

### Post by matt_symes on 2016-01-05
*sighs*

---

### Post by MikeMecanic on 2016-01-05
> **Doug S said:**
> 
[https://help.ubuntu.com/community/EditorGroup](https://help.ubuntu.com/community/EditorGroup)
[https://help.ubuntu.com/community/AdminGroup](https://help.ubuntu.com/community/AdminGroup) **
Elizabeth Krumbach Joseph || Lyz || pleia2
** for unknown reasons the AdminGroup list is showing some Russian text for non members. Members (which I am not) see the actual AdminGroup list, if they are logged in.

As a member of the community, I Login successfully in both accounts.  **Should I have the right  to login in the admin account (login to edit)?**

---

### Post by QIII on 2016-01-05
If you have a launchpad account, you should be able to edit.

I'm finding all the pages locked down as "immutable".

---

### Post by Doug S on 2016-01-05
Everybody,

You can still login, but you can not edit, unless you are in the proper group.
Actually, I can not test this stuff because for unknown reasons, I have never been able to edit help.ubuntu.com/community pages. I have no problems editing wiki.ubuntu.com pages.

EDIT: Oh, I see the Russian text is gone, and it now shows English.

---

### Post by ventrical on 2016-01-06
> **QIII said:**
> If you have a launchpad account, you should be able to edit.

I'm finding all the pages locked down as "immutable".

You have to join the team to be able to edit.

I see no Russian characters there.

Regards..

---

### Post by ventrical on 2016-01-06
> **Doug S said:**
> Everybody,

You can still login, but you can not edit, unless you are in the proper group.
Actually, I can not test this stuff because for unknown reasons, I have never been able to edit help.ubuntu.com/community pages. I have no problems editing wiki.ubuntu.com pages.


 I'm pretty sure you have to be a member of that team to be able to edit. It needs approval .. otherwise anybody could go in and deface the pages.

Regards..

---

### Post by Doug S on 2016-01-06
> **ventrical said:**
> I'm pretty sure you have to be a member of that team to be able to edit. It needs approval .. otherwise anybody could go in and deface the pages.

Regards..No, at least not during normal times, current lock down aside.  You just need an account (launchpad or SSO or whatever), hence how this got so out of control so fast. There is a debate on [the doc-team e-mail]("https://lists.ubuntu.com/archives/ubuntu-doc/2016-January/date.html") list right now about what to do moving forward.

Note also, that there are now some issues with wiki.ubuntu.com, although it has not been locked down, at least not yet.

---

### Post by ventrical on 2016-01-06
> **Doug S said:**
> No, at least not during normal times, current lock down aside.  You just need an account (launchpad or SSO or whatever), hence how this got so out of control so fast. There is a debate on [the doc-team e-mail]("https://lists.ubuntu.com/archives/ubuntu-doc/2016-January/date.html") list right now about what to do moving forward.

Note also, that there are now some issues with wiki.ubuntu.com, although it has not been locked down, at least not yet.

Yes... I recall that I was able to correct some spelling there about a year back. I am glad you brought this up because I often wonder about the security of the wiki pages at U+1 (now UDV).

Ummm just having a launchpad account did not give me privlidges to edit the U+1 wiki. I had to be approved as a member by the admin (btw which I am now admin of). So.. my question would be then: does it all come down to trusting the meritocracy of the wiki infrastructure?

Regards..

---

### Post by ventrical on 2016-01-06
I can edit wiki pages but not community help pages.

Regards..

---

### Post by sudodus on 2016-01-06
> **QIII said:**
> If you have a launchpad account, you should be able to edit.

I'm finding all the pages locked down as "immutable".

> **Doug S said:**
> Everybody,

You can still login, but you can not edit, unless you are in the proper group.
Actually, I can not test this stuff because for unknown reasons, I have never been able to edit help.ubuntu.com/community pages. I have no problems editing wiki.ubuntu.com pages.

EDIT: Oh, I see the Russian text is gone, and it now shows English.

Me too, I can edit the wiki pages, but not the help pages. I see "immutable" too. At first I thought I was locked out because I retired from moderator, but now I understand what is the problem. I hope there will be some ***group to join soon*** in order to be able to edit the help pages that we 'are responsible for'.

---

### Post by Doug S on 2016-01-06
> **sudodus said:**
> I hope there will be some ***group to join soon*** in order to be able to edit the help pages that we 'are responsible for'.Please be patient. Here is quote from an e-mail from Lyz:

> The problem is that the spammers were creating hundreds of pages, a new one every couple of minutes. We couldn't keep up. Locking the wiki down was the only way to pause the attack.

---

### Post by MikeMecanic on 2016-01-07
If possible or not too complicated, disabling anything related to Support Language would be a good starter.  That way English would be default.  No possibility to paste in an another language.  There are other ways to increase security but I'm sure that you work on it.


Regards,

---

### Post by Doug S on 2016-02-17
Please be aware: Due to a sudden lot of spam the lockdown has been expanded to include wiki.ubuntu.com

Everyone, potential contributors, wiki admins attempting to still do edits on behave of others, Canonical IS, are very annoyed with this.

---

### Post by slickymaster on 2016-02-17
> **Doug S said:**
> Please be aware: Due to a sudden lot of spam the lockdown has been expanded to include wiki.ubuntu.com

Everyone, potential contributors, wiki admins attempting to still do edits on behave of others, Canonical IS, are very annoyed with this.

Hi Doug S.

The wiki is read-write again. Just edited the [https://wiki.ubuntu.com/Xubuntu/Meetings](https://wiki.ubuntu.com/Xubuntu/Meetings) page

---

### Post by lisati on 2016-02-17
From the Admin page just now, doesn't look like Rusian or English to me, more like Spanish (or related): > No tienes permisos para editar esta página.
I'll wander off and login.

---

### Post by slickymaster on 2016-02-17
> **lisati said:**
> From the Admin page just now, doesn't look like Rusian or English to me, more like Spanish (or related): 
I'll wander off and login.

Actually it is Spanish, lisati :p

---

### Post by lisati on 2016-02-17
> **slickymaster said:**
> Actually it is Spanish, lisati :p

Kind of figured that. :D

I'm not sure if I can make a useful contribution to any of the pages at the moment (the handful I looked at were showing "immutable"), so time to wander off and look for other ways of [s]being a pain[/s] making myself useful.

---

### Post by slickymaster on 2016-02-17
> **lisati said:**
> Kind of figured that. :D

I'm not sure if I can make a useful contribution to any of the pages at the moment (the handful I looked at were showing "immutable"), so time to wander off and look for other ways of [s]being a pain[/s] making myself useful.

You should be able to edit, lisati. After login in with your LP account, refresh the page you're intending to edit and the page should then be showing 'Edit' instead of 'Immutable Page'

---

### Post by Doug S on 2016-02-17
> **slickymaster said:**
> Hi Doug S.

The wiki is read-write again. Just edited the [https://wiki.ubuntu.com/Xubuntu/Meetings](https://wiki.ubuntu.com/Xubuntu/Meetings) pageThat is very interesting. I also observe, based on [the recent changes page]("https://wiki.ubuntu.com/RecentChanges"), that the spam is back in full swing also.

---

### Post by lisati on 2016-02-17
> **slickymaster said:**
> You should be able to edit, lisati. After login in with your LP account, refresh the page you're intending to edit and the page should then be showing 'Edit' instead of 'Immutable Page'

Success. Now to wander around and take a look.

---

### Post by QIII on 2016-02-17
> **Doug S said:**
> That is very interesting. I also observe, based on [the recent changes page]("https://wiki.ubuntu.com/RecentChanges"), that the spam is back in full swing also.

Ever so slightly embarrassing...

---

### Post by sammiev on 2016-02-17
It seems I could edit as well.

Should I stay out of it or help clean out some of the spam?

---

### Post by lisati on 2016-02-17
> **sammiev said:**
> It seems I could edit as well.

Should I stay out of it or help clean out some of the spam?

Good question. There seems to be quite a bit there......

---

### Post by QIII on 2016-02-17
Do they have it set up so just anyone can walk in from the street and start typing?  Or are they well and truly hacked still?

---

### Post by Irihapeti on 2016-02-17
If all you need is a SSO, then, yes, anyone from off the street can create a login and start typing.

Just like they do on the forums.

---

### Post by QIII on 2016-02-17
Well, we should only let the "right kind of people" in.

---

### Post by Irihapeti on 2016-02-17
> **QIII said:**
> Well, we should only let the "right kind of people" in.

I'm not sure if that's meant to be tongue-in-cheek or not, but I don't see the need for complete newcomers to need instant editing access to the wiki. Some sort of screening process would make sense.


Maybe we should be surprised that the spam attack didn't happen a lot sooner.

---

### Post by sudodus on 2016-02-17
> **Irihapeti said:**
> I'm not sure if that's meant to be tongue-in-cheek or not, but I don't see the need for complete newcomers to need instant editing access to the wiki. Some sort of screening process would make sense.


Maybe we should be surprised that the spam attack didn't happen a lot sooner.

+1

---

### Post by sammiev on 2016-02-17
I'm likely wrong and then some as I never tried to get into any of the wiki till I signed the COC.

I thought at that time it was required. Just saying...

---

### Post by Irihapeti on 2016-02-17
> **sammiev said:**
> I'm likely wrong and then some as I never tried to get into any of the wiki till I signed the COC.

I thought at that time it was required. Just saying...

I'm no authority on it myself – I'm just assuming that if the spammers got in that easily, then there's no vetting process in place.

---

### Post by bapoumba on 2016-02-18
I had removed over 100 spam pages and labeled them as such. All of them are gone now, and the wiki is locked again. Unfortunately, there were genuine pages in the middle, I had left them unchanged, all gone now :(

Could wiki users be allowed on either grandfathering old timers or allowing new users on 10 genuine new pages / edits / contributions ?

---

### Post by sudodus on 2016-02-18
It seems we cannot have an open wiki system. Either some people enjoy spamming when and where it is possible, or there is one particular enemy, that really tries hard to destroy our open system.

I think we need ***a method to give trusted people a 'limited in time' access to the wiki/help pages*** (maybe similar to the process to give admins and moderators access to edit other people's threads at the Ubuntu Forums. I think a rather larger number of people can be given such access, at least all Ubuntu members and also other people who are regularly maintaining wiki/help pages.

(I am maintaining a few wiki/help pages, and would apply for such access. It means that I can be one of the persons, who can help people without access to make edits too.)

---

### Post by slickymaster on 2016-02-18
> **sudodus said:**
> <---snip--->

I think we need ***a method to give trusted people a 'limited in time' access to the wiki/help pages*** (maybe similar to the process to give admins and moderators access to edit other people's threads at the Ubuntu Forums. I think a rather larger number of people can be given such access, at least all Ubuntu members and also other people who are regularly maintaining wiki/help pages.

(I am maintaining a few wiki/help pages, and would apply for such access. It means that I can be one of the persons, who can help people without access to make edits too.)

That role already exists sudodus, it's the [“Ubuntu Community Help Wiki Editors” team]("https://launchpad.net/~ubuntu-community-wiki-editors").

---

### Post by Doug S on 2016-02-18
> **bapoumba said:**
> ... All of them are gone now, and the wiki is locked again....Seems to be unlocked at the moment (the wiki.ubuntu.com one) and seems to be under attack. ( [recent changes page]("https://wiki.ubuntu.com/RecentChanges") )

There is an ongoing discussion about this on the [Ubuntu-docs mail list]("https://lists.ubuntu.com/archives/ubuntu-doc/2016-February/thread.html"). (the link does not point to a specific thread, because there are a few. Look at January also.)

---

### Post by sudodus on 2016-02-18
> **slickymaster said:**
> That role already exists sudodus, it's the [&#8220;Ubuntu Community Help Wiki Editors&#8221; team]("https://launchpad.net/~ubuntu-community-wiki-editors").

Would it work to accept more people into that group, in principle all the people who are active developing and modifying wiki/help pages. I'm thinking of those of us who edit pages several times each year (for example updates for each new version of the Ubuntu family flavours)?

---

### Post by slickymaster on 2016-02-18
> **sudodus said:**
> Would it work to accept more people into that group, in principle all the people who are active developing and modifying wiki/help pages. I'm thinking of those of us who edit pages several times each year (for example updates for each new version of the Ubuntu family flavours)?
It's a restricted team, which means membership is closed and requires approval. Only the team's administrators can invite a user to be a member.

That said, potential members, before applying to join the team, should build up a portfolio of wiki pages and edits that the team's administrators can take a look at. See [https://wiki.ubuntu.com/DocumentationTeam/Organization](https://wiki.ubuntu.com/DocumentationTeam/Organization) for more details.

---

### Post by sudodus on 2016-02-18
So you mean that it is not a solution to the problem we are facing now.

---

### Post by slickymaster on 2016-02-18
What I'm saying sudodus, is that the [https://help.ubuntu.com/community/EditorGroup](https://help.ubuntu.com/community/EditorGroup) serves exactly the presupposition of what you suggested. The only thing required is for people to apply for membership along the lines of what's described in [https://wiki.ubuntu.com/DocumentationTeam/Organization](https://wiki.ubuntu.com/DocumentationTeam/Organization)

---

### Post by sudodus on 2016-02-18
So it can be a solution, at least a temporary solution :-)

Let's say that 20-50 wiki editors apply for membership in the group. If everybody is accepted and gets full authority, maybe things will get out of control. Maybe there should be some time limit - or interim membership with limited power to do things.

Example: As a regular user, I could create and edit wiki and help pages. But I could not delete pages, not even delete old attachments, that I had replaced with new versions. But I know that people with full privileges can delete pages and attachments.

---

### Post by slickymaster on 2016-02-18
Exactly, sudodus.

See [https://lists.ubuntu.com/archives/ubuntu-doc/2016-January/019650.html](https://lists.ubuntu.com/archives/ubuntu-doc/2016-January/019650.html) and [https://lists.ubuntu.com/archives/ubuntu-doc/2016-January/019674.html](https://lists.ubuntu.com/archives/ubuntu-doc/2016-January/019674.html)

---

### Post by bapoumba on 2016-02-18
> **Doug S said:**
> Seems to be unlocked at the moment (the wiki.ubuntu.com one) and seems to be under attack. ( [recent changes page]("https://wiki.ubuntu.com/RecentChanges") )

There is an ongoing discussion about this on the [Ubuntu-docs mail list]("https://lists.ubuntu.com/archives/ubuntu-doc/2016-February/thread.html"). (the link does not point to a specific thread, because there are a few. Look at January also.)
Thanks Doug :)
Slicky had reminded me a bit earlier that I had been subscribed to the doc team list for longer than I can recall (I used to do some wiki work and translation work long long long time ago).

So what is the best thing to do when spam hits the wiki ? I deleted a large number of pages earlier today, labeling them as spam, is that helpful or not ?

---

### Post by QIII on 2016-02-18
Just applied to be a member of the Editors Group.  We'll see if I am worthy.  :)

---

### Post by Doug S on 2016-02-18
> **bapoumba said:**
> So what is the best thing to do when spam hits the wiki ? I deleted a large number of pages earlier today, labeling them as spam, is that helpful or not ?
I assume any help is welcome, but I don't really know. I am not a wiki admin. I am an [Ubuntu Documentation Committer]("https://launchpad.net/~ubuntu-core-doc"), which is a bit of a different beast.

---

### Post by bapoumba on 2016-02-18
> **Doug S said:**
> I assume any help is welcome, but I don't really know. I am not a wiki admin. I am an [Ubuntu Documentation Committer]("https://launchpad.net/~ubuntu-core-doc"), which is a bit of a different beast.
Thanks again. I had time today (which is quite rare nowadays) and despise other people's community work being ruined and attacked that way.

---

### Post by lisati on 2016-02-18
I've deleted a handful, there seems to be a new batch there now.

---

### Post by lisati on 2016-02-18
Hmmm, almost a forum glitch. Is the wiki on the same server? There seemed to be a lag there as well.

---

### Post by sammiev on 2016-02-18
It seems I can still edit wiki.

Isn't the site locked down?

---

### Post by sudodus on 2016-02-19
I can edit the wiki pages but not the help pages (8 hours after you posted, sammiev).

---

### Post by slickymaster on 2016-02-19
> **lisati said:**
> Hmmm, almost a forum glitch. Is the wiki on the same server? There seemed to be a lag there as well.

I don't think so, lisati.

---

### Post by Doug S on 2016-02-19
> **lisati said:**
> Hmmm, almost a forum glitch. Is the wiki on the same server? There seemed to be a lag there as well.I noticed a huge lag on both at the same time, and close to the time of your posting.

---

### Post by ventrical on 2016-05-05
We had a live web session on this yesterday. We were discussing the CoC and these topics came up.

[http://summit.ubuntu.com/uos-1605/meeting/22669/code-of-conduct-review/](http://summit.ubuntu.com/uos-1605/meeting/22669/code-of-conduct-review/)

regards..

---

### Post by Doug S on 2016-05-08
The wiki's are locked down again. See [this]("http://ubuntuforums.org/showthread.php?t=2323735&p=13485545#post13485545") from another thread on this sub-forum.

---

### Post by PaulW2U on 2016-05-08
> **Doug S said:**
> The wiki's are locked down again. See [this]("http://ubuntuforums.org/showthread.php?t=2323735&p=13485545#post13485545") from another thread on this sub-forum.
It seems that the wikis are not **completely** locked down.

Editing is still *possible* for anyone in the ~ubuntumembers Launchpad group.

---

### Post by ventrical on 2016-05-10
it will only allow me to edit the wiki.ubuntu.com help pages. I cannot edit the U+1 page which I am an admin of. We have been being spammed with new users for last couple of days. Also the ether.pad instance for SSO is also gone!.

Regards..

---

### Post by PaulW2U on 2016-05-10
> **ventrical said:**
> I cannot edit the U+1 page which I am an admin of.
That's strange as I can edit your pages.

I have no special access apart from being a member of the ~ubuntumembers Launchpad group of which you should also be a member. :confused:

---

### Post by Bashing-om on 2016-05-10
ventrical; Hello'

I too, early this AM, was able to edit wiki page . I still have the ether.pad instance membership shown.

All I know to do is await for IS to determine the fix for the spammers .

[INDENT][INDENT]that evil 10 %
[INDENT][INDENT]makes it so tough on the rest of us
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ventrical on 2016-05-10
> **PaulW2U said:**
> That's strange as I can edit your pages.

I have no special access apart from being a member of the ~ubuntumembers Launchpad group of which you should also be a member. :confused:

Yes I am member.  I have a theory about firefox. I am going to use another PC to log in and see if that fixes.

---

### Post by ventrical on 2016-05-13
Still locked out of the U+1 wiki.

---

### Post by ventrical on 2016-05-14
Just got an e-mail from elizabeth. All wiki edits have to be done via a mailing list and have to be approved that way until IS solves this problem. Appears to be some real damage.

sigh

Regards..

---

### Post by PaulW2U on 2016-05-14
@ventrical, I've sent you a PM with some information, which I didn't want to post here, that might help.

Despite what you may have been told the wikis **are** still editable as you'll see by looking at my minor edit at [https://wiki.ubuntu.com/U+1](https://wiki.ubuntu.com/U+1).

---

### Post by ventrical on 2016-05-14
> **PaulW2U said:**
> @ventrical, I've sent you a PM with some information, which I didn't want to post here, that might help.

Despite what you may have been told the wikis **are** still editable as you'll see by looking at my minor edit at [https://wiki.ubuntu.com/U+1](https://wiki.ubuntu.com/U+1).

Thanks for the reply. Yep .. yours is working .. but not mine :)

Regards..

---

### Post by ventrical on 2016-05-14
Here is vicious cycle I get. Please see two part screenshots.

It starts with:

---

### Post by ventrical on 2016-05-14
..and finally this one. It goes around  and around, back to immutable page.

---

### Post by ventrical on 2016-05-14
@Paul

  I just made a small edit here: [https://wiki.ubuntu.com/Home?action=logout&logout=logout](https://wiki.ubuntu.com/Home?action=logout&logout=logout)

I put an exclamation mark at the end of Ubuntu Code of Conduct!

and yet I still cannot  edit U+1. I also tried my other account , but to no avail.

Regards..

---

### Post by bapoumba on 2016-05-14
@ ventical, I do not see you in the ubuntu-member LP group. Have you left your renewal PM slip through ? I think you need both, etherpad and members LP groups.

---

### Post by ventrical on 2016-05-14
> **bapoumba said:**
> @ ventical, I do not see you in the ubuntu-member LP group. Have you left your renewal PM slip through ? I think you need both, etherpad and members LP groups.

Awww geeesh... (pulling my hair out) :) ... um.. elfy used to renew that I think... I honestly forgot how to do it..  I did not get a notification through e-mail ... uh  um unless it got sent to alternate.

Thanks 
Regards..

---

### Post by PaulW2U on 2016-05-14
> **ventrical said:**
> I put an exclamation mark at the end of Ubuntu Code of Conduct!

and yet I still cannot  edit U+1. I also tried my other account , but to no avail.
I'm confused now as I thought I'd found the solution to your problem.  :)
> **bapoumba said:**
> @ ventical, I do not see you in the ubuntu-member LP group. Have you left your renewal PM slip through ? I think you need both, etherpad and members LP groups.
ventrical has two Launchpad IDs which is not helping. :)

The ability to edit the wiki(s) for members of ~ubuntu-etherpad has been removed by Canonical IS. That was what Elizabeth was referring to when she advised that the wiki has been "locked down." Members of ~ubuntu-members should still be able to edit both wikis.

---

### Post by bapoumba on 2016-05-14
> **PaulW2U said:**
> I'm confused now as I thought I'd found the solution to your problem.  :)

ventrical has two Launchpad IDs which is not helping. :)

The ability to edit the wiki(s) for members of ~ubuntu-etherpad has been removed by Canonical IS. That was what Elizabeth was referring to when she advised that the wiki has been "locked down." Members of ~ubuntu-members should still be able to edit both wikis.

Yes, that is what I just realized !
@ ventrical, you have to use the LP account that has ubuntu-membership. I can edit your wiki page as Paul does.
And thanks Paul, I have not got to catching up with the various ml so I missed the removal of the etherpad requirement.

To note, ubuntu membership you have to renew yourself when you get the notification email.

---

### Post by ventrical on 2016-05-14
> **PaulW2U said:**
> I'm confused now as I thought I'd found the solution to your problem.  :)

ventrical has two Launchpad IDs which is not helping. :)

The ability to edit the wiki(s) for members of ~ubuntu-etherpad has been removed by Canonical IS. That was what Elizabeth was referring to when she advised that the wiki has been "locked down." Members of ~ubuntu-members should still be able to edit both wikis.

Elizabeth says she had asked Canonical IS to lock down the wikis and that to edit a page , one has to  go to a mailing list .. etc.. perhaps there is some confusion about. I am not complaining.. just very curious as to why some can edit and others can not.  Could this mean that other members who have joined a while  could be laying in wait to cause more damage ?

Regards..

---

### Post by ventrical on 2016-05-14
> **bapoumba said:**
> Yes, that is what I just realized !
@ ventrical, you have to use the LP account that has ubuntu-membership. I can edit your wiki page as Paul does.
And thanks Paul, I have not got to catching up with the various ml so I missed the removal of the etherpad requirement.

To note, ubuntu membership you have to renew yourself when you get the notification email.

Did not get the notification e-mail.As I said, it was Elfy who last renewed my account. I will look further into this.

Thanks you guys.

Regards..

---

### Post by PaulW2U on 2016-05-14
> **ventrical said:**
> Elizabeth says she had asked Canonical IS to lock down the wikis and that to edit a page , one has to  go to a mailing list .. etc.. perhaps there is some confusion about. I am not complaining.. just very curious as to why some can edit and others can not.  Could this mean that other members who have joined a while  could be laying in wait to cause more damage ?
I don't think Elizabeth realised that edit access for Ubuntu Members was retained as that group is "restricted", i.e. we know who everyone is in that group. That couldn't be said of the ~ubuntu-etherpad group as many gained access through a "back door". Non Ubuntu Members have to email their edits to the Docs team.

I think it's time to abandon one of your Launchpad IDs and get everything moved over to the one that you want to use.

You might need the forum admins help with that. :)

---

### Post by ventrical on 2016-05-14
> **PaulW2U said:**
> I don't think Elizabeth realised that edit access for Ubuntu Members was retained as that group is "restricted", i.e. we know who everyone is in that group. That couldn't be said of the ~ubuntu-etherpad group as many gained access through a "back door". Non Ubuntu Members have to email their edits to the Docs team.

I think it's time to abandon one of your Launchpad IDs and get everything moved over to the one that you want to use.

You might need the forum admins help with that. :)

I think that may be so.  I am still an Ubuntu Member on my twocamels launchpad account. But I think that was the discussion with SSO back a while ago .. so I followed the thread and merged the two accounts.

ok.. I'll take a time out here.... the U+1 wiki just needs some contents in the Blog and news etc.. so if you guys want to do some editing or adding of content please feel free. I wanted to help Daniel Holbach witht he Snappy Docs and other  docs that were outdated or needed some caveats .. etc... 

regards..

edit;

If any admins have a suggestion to fix this without "un_merging" my SSO  :)

---

### Post by ventrical on 2016-05-14
Tried to add account to SSO .  Will not send instructions after "click send instructions".

regards..

---

### Post by PaulW2U on 2016-05-14
> **PaulW2U said:**
> You might need the forum admins help with that. :)
> **ventrical said:**
> If any admins have a suggestion to fix this without "un_merging" my SSO  :)
> **ventrical said:**
> Tried to add account to SSO .  Will not send instructions after "click send instructions".
I think some of my hints are too subtle for you ventrical  :)

You're an Ubuntu Member through forum contributions. So why not ask the forum admins to move your Ubuntu Membership from one Launchpad ID to the other, i.e. the one that is connected to your Ubuntu SSO? When they've done that and you've dealt with anything else then simply delete the redundant ID.

---

### Post by twocamels on 2016-05-14
OK.. I closed other instances and made twocamels default but after doing this in SSO then my launchpad ID does not recognize me as Ubuntu Member.. only ethernet.pad.instance member and it will only allow me to edit previously open windows of the wiki: ie;

[https://wiki.ubuntu.com/U%2B1/contact](https://wiki.ubuntu.com/U%2B1/contact)
^(you will see small edit and username twocamels at bottom)

So when I try to click on another section it goes back to immutable page.

This is really stepping in the dog's pile so to speak eh ? :)

hehehe

Regards..

---

### Post by twocamels on 2016-05-14
> **PaulW2U said:**
> I think some of my hints are too subtle for you ventrical  :)

You're an Ubuntu Member through forum contributions. So why not ask the forum admins to move your Ubuntu Membership from one Launchpad ID to the other, i.e. the one that is connected to your Ubuntu SSO? When they've done that and you've dealt with anything else then simply delete the redundant ID.

No. I think you hit the nail on the head. I had ABSOLUTELY no idea!! that I had an account on ubuntuforums  with username 'twocamels'.

 I logged off of all instances of EP, LP and ubuntuforums and it looks like I have edit privledges back... hmmm one second..

Yeah .. only three beans.. :) Gee .. I feel like a noob again! :)

---

### Post by twocamels on 2016-05-14
@PaulW2U and Paboumba

Ok.. looks like resolved.  I have the option now to log on with my ventrical account (which only has EP member) or my twocamels account with is ubuntumember with all editing privileges of wikis.
btw.. I had to close other windows that were open so I do not think two account instances can be working at the same time. I'll asks the admins in the furture about the one account or merging my twocamels username to my ventrical username.

Thanks for helping me get to the bottom of this issue. I certainly got a good refresher course.:)

Regards..

---

### Post by ventrical on 2016-05-14
Can't log in to SSO  with two different usenames across another ip adress.

kewl

---

### Post by bapoumba on 2016-05-15
OK, what do you wish to do ?
If I understand correctly, you'd rather keep the ventrical account on the forums. What you need to do is log out of everything, log into the twocamels U1 account and change the preferred email to a new unrelated valid one (not the one from ventrical, you'll need to confirm the email iirc), then log out and log in U1 with the ventrical credentials. Then change the preferred email to the one you set up for twocamels and see if it works. **But please before doing that either report this post or PM me, we need to disassociate your forums accounts from the current U1 accounts !**

---

### Post by ventrical on 2016-05-17
Currently  it works ok for now. When I need to edit the wikis I just log off and switch to twocamels account. I need ventrical account to manage U+1 team in launchpad so rather than take a chance and break it I'll just go along until I get another update from Elizabeth. If it becomes an annoyance or they can't fix etherpad.instance backdoor problem then I will PM you and I will do as you suggested.

Thank you  and,

Regards..

---

### Post by bapoumba on 2016-05-17
OK, no rush :)

---

### Post by ventrical on 2016-06-03
@bapoumba

  I can now be logged on to both accounts simutaneously and edit the wikis. Why .. I don't know.. perhaps some little elfin in the background scenes:)

Regards..

---

### Post by ventrical on 2016-07-03
> **bapoumba said:**
> OK, no rush :)

Hi bapoumba,

 I am now a memebr of ubuntu-wiki-editors teams so I can use both accounts now.

Thanks , 
Regards..

---

### Post by bapoumba on 2016-07-03
happy to see it's working for you too ventrical :)

---

