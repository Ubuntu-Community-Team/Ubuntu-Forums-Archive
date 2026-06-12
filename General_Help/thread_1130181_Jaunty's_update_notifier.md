---
title: "Jaunty's update notifier"
date: 2009-04-19
forum: General Help
---

### Post by theozzlives on 2009-04-19
Has anyone had probs with Jaunty notifying you of updates? I have Jaunty on 2 computers and have to start Update Manager on both to see if there is updates.

---

### Post by orlox on 2009-04-19
I also have two laptops wth jaunty (one is an upgrade from intrepid and the other a clean install of alpha 6, but updated) and I never see the updates though update-notifier is included in the startup applications...

---

### Post by 67GTA on 2009-04-19
The default settings have been changed to work better with the new notification framework. To revert to the old settings with the icon in the panel to show updates, open a terminal and run ```
gconftool -s --type bool /apps/update-notifier/auto_launch false
``` After a reboot, the old settings will take effect.

---

### Post by justinjstark on 2009-04-20
> **67GTA said:**
> The default settings have been changed to work better with the new notification framework. To revert to the old settings with the icon in the panel to show updates, open a terminal and run ```
gconftool -s --type bool /apps/update-notifier/auto_launch false
``` After a reboot, the old settings will take effect.

Wait!  So they decided not to run automatic updates **at all** in order for it to "work better" with the new notification framework?  Seems a little odd to me.

But thank you for the tip.

---

### Post by Partyboi2 on 2009-04-20
> **justinjstark said:**
> Wait!  So they decided not to run automatic updates **at all** in order for it to "work better" with the new notification framework?  Seems a little odd to me.

But thank you for the tip.
This is taken from the release notes:
> Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command: 
 
 gconftool -s --type bool /apps/update-notifier/auto_launch false 

---

### Post by svaens on 2009-04-28
what a regression!

Now there's yet one more task to run before I can get Ubuntu in a good state after install. Annoying.

---

### Post by mobrien118 on 2009-04-28
> **svaens said:**
> what a regression!

Now there's yet one more task to run before I can get Ubuntu in a good state after install. Annoying.

Agreed. While I usually stand behind Ubuntu's decisions, this one just seems silly!

Why couldn't they leave the icon AND add the new notifier capability? Are the two ideas not compatible? I don't see what that little icon there would hurt anyway, especially if the reason was that people were not noticing it in the first place!

---

### Post by coffeecat on 2009-04-28
> **svaens said:**
> what a regression!

Now there's yet one more task to run before I can get Ubuntu in a good state after install. Annoying.


You must have misunderstood the release note quote that Partyboi2 posted. This is no regression, but a perfectly good development, imo. You still get notified for security updates daily, but non-security related updates only weekly. For me this fixes the irritating daily hassle about non-critical updates.

When you do a fresh install, good practice demands that the **first** thing you should do is a manual update without being prompted, whatever the OS. So true for Windows too and true for MacOS. I see no reason to be annoyed.

---

### Post by StevenHarper on 2009-04-29
I think a simple checkbox in one of the applets (Software Sources) would do the trick.

Something like - Only notify Weekly of non-security updates.

I prefer daily, but I can see why you newer and more basic users would get annoyed with having to do something every day to keep their OS up to date.

Steve

---

### Post by Aearenda on 2009-04-29
The annoying thing for me is the way the Update Manager pops up a window when there are updates. I can just imagine it happening in front of a roomful of people during a completely unrelated presentation, making the presenter look like a fool.

---

### Post by Brandon Williams on 2009-04-29
If I recall correctly, the update manager window is supposed to pop up under all the other windows so that it doesn't get in the way of work you're currently doing. Is this not the case?

---

### Post by Kareeser on 2009-04-29
> **Brandon Williams said:**
> If I recall correctly, the update manager window is supposed to pop up under all the other windows so that it doesn't get in the way of work you're currently doing. Is this not the case?

Yep, but the pop-under behaviour means it flickers first before minimizing.

I'd much prefer the old behaviour, but I do see where they're going with this.

---

### Post by Leed on 2009-04-29
I agree this new behavior is annoying, keeps happening to me that I suddenly notice the manager on one of my windows, in 99% when I want to shut down. It may not be preventing me from shutting down, but I would have done the update if I would have seen the icon in the bar above. 

For me it was one of the great things in ubuntu, that updates silently appear in the background as an icon and can be processed in one go, as soon as you feel like dealing with it. I only want to know when updates are available, I want to decide when I'm ready to do them, I don't want balloons, notifications and definitely not pop-ups demanding actions from me.

---

### Post by SyL on 2009-04-29
Instead of getting the update manager popping up, a simple notification message -for security update- would have been much better!!
Furthermore, i have the habit to trigger the update in a terminal, therefore getting the update manager appearing when i do an apt-get update is kind of weird.

---

### Post by Aearenda on 2009-04-29
It's widely publicised that old update behaviour is restored by ```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

I also revert Pidgin to its old behaviour.

---

### Post by brandon88tube on 2009-04-29
That is strange. I have yet to have the update-manager notify me even when there were security updates. I had to manually check.

---

### Post by mb_webguy on 2009-04-29
I don't agree with the new behavior, either.  The reasoning behind the change was that the notification area has gotten to be a catch-all for just about anything that any software developer wants to put there, and isn't obvious enough in reporting important notifications.  The developers therefore consider the notification area "broken", and are trying to move as much as possible out of it.

While I like the new notification messages (the black windows that appear in the upper-right corner), they're only good for transient notifications, not persistent ones, such as the need to update.  IMO, that's *exactly* the sort of thing for which the notification area was designed.  And while I think it's being misused -- what exactly is the point of minimizing an application to the notification area instead of to the window list, anyway? -- I don't think that means it's broken.

The current behavior of Update Manager certainly isn't an improvement for several reasons.  First of all, an application should never open itself without explicit user action.  It's simply bad design.  Also, opening the application when updates are available is not a constant reminder that the user needs to install updates.  Since it may pop up at inopportune times, the user is likely to simply close it to get it out of the way.  And since it opens *under* open windows, a user that keeps an application (such as a web browser) open all of the time may not notice it's there.

IMO, the best solution would be to continue to keep the old behavior of an icon appearing in the notification area whenever any updates are available, coupled with one of the new notification windows when an important security update becomes available as well as at login if such an update is available.  That way, you have a persistent reminder that the user should take action (i.e. the notification icon) as well as a transient "alert" notification to draw attention to the persistent notification.

---

### Post by Razmear on 2009-04-29
I just ran the command so hopefully that will resolve this issue, but Mr Webguy brings up another annoyance. 
The new flashy black notification popup shows in the upper left corner of the desktop. I run a dual monitor setup with my TV set as the left screen for watching movies, streams or whatever. if I'm watching regular tv then that half of my screen isn't used or visible, and if i'm watching a stream then the mail notification pops over it instead of from the notification section of the panel on my main screen like it used to. 

Guess this is the next thing to hunt up a fix for since the upgrade. 

eb

---

### Post by Leed on 2009-04-30
I'd think it would be good enough if there would simply be two icon colors, a more descreet one for normal updates and a brighter, possibly red one for security updates. 

Webguys idea of a notification in the top right corner would also be good, as long as it only appears for a few seconds and is never in front of anything else that may be there

---

### Post by theozzlives on 2009-04-30
WOW, who'd a thunk one simple question would trigger this kinda response. I'm glad I'm not the only one that thinks sometimes change isn't always good.

---

### Post by Yfrwlf on 2009-04-30
> **mb_webguy said:**
> IMO, the best solution would be to continue to keep the old behavior of an icon appearing in the notification area whenever any updates are available, coupled with one of the new notification windows when an important security update becomes available as well as at login if such an update is available.  That way, you have a persistent reminder that the user should take action (i.e. the notification icon) as well as a transient "alert" notification to draw attention to the persistent notification.

Very agreed on all counts.  The new system is annoying and at the very least if they want to have the manager auto-run you should NNNNNNNOOOOOOOTTTT have to pull up the command line.  Make it an option in the updates section of software sources at the very least.  However I can't image anyone wanting to turn on that setting very often, and it should definitely not be the default behaviour IMO.

I get the update manager popping up at work on boxes which are supposed to be displaying statistics, and it's highly annoying especially for a reason that no one has yet posted about:

[COLOR="Red"]**[SIZE="3"]Update settings are now broken.[/SIZE]**[/COLOR]

When checking the box to have updates automatically download and install in the background, this does NOT happen.  It seems that all of the three settings in System > Admin > Software Sources > Updates > Automatic Updates are now completely broken.

If I'm wrong let me know, but so far I've seen this happen on three boxes.

---

### Post by sefs on 2009-04-30
can someone verify that 

```

gconftool -s --type bool /apps/update-notifier/auto_launch false 

```

actually restores old behaviour.  I did this a couple days ago and still have to manually check for updates daily.  They are some but the icon does not appear in the notification tray to alert me.

---

### Post by MarkusAurelius on 2009-04-30
> **sefs said:**
> can someone verify that 

```

gconftool -s --type bool /apps/update-notifier/auto_launch false 

```

actually restores old behaviour.  I did this a couple days ago and still have to manually check for updates daily.  They are some but the icon does not appear in the notification tray to alert me.
I have done this and I don't think it does anything much, at least it does not bring the Update Notification Icon in the bar as in pre-9.04. All I see is that Update-Manager starts up in the minimized mode...

**EDIT: ** [COLOR="DarkRed"]I retract the above:[/COLOR]  seems like it took a couple of days as I usually suspend.  I shutdown all my machines and the previous behaviour is back.  Thanks ! 

That is not what the previous behaviour was! I really do not like this new behaviour of Update-Manager starting itself, I definitely agree with *mb_webguy* about self-starting programs: *an application should never open itself without explicit user action*. 

Please add my vote as not liking this Update-Manager changes.

I really don't mind changes, but Istill should be able to revert to a previous behaviour...

Regards!

---

### Post by Brandon Williams on 2009-04-30
Yes ... changing that setting has given me back the old behavior. I've received a few update notifications via the icon. I was receiving them quite regularly between beta and release, less so now.

---

### Post by rajeev1204 on 2009-04-30
> **sefs said:**
> can someone verify that 

```

gconftool -s --type bool /apps/update-notifier/auto_launch false 

```

actually restores old behaviour.  I did this a couple days ago and still have to manually check for updates daily.  They are some but the icon does not appear in the notification tray to alert me.


Its not working for me either.Its  been a week now since i got any updates.

---

### Post by rajeev1204 on 2009-04-30
> **brandon88tube said:**
> That is strange. I have yet to have the update-manager notify me even when there were security updates. I had to manually check.


Agreed here too. I havent seen security updates via notify osd yet .Not in a month i have been using jaunty.

---

### Post by sefs on 2009-04-30
Can someone file a bug report at lanuchpad.net where we can all tag on with our woes (that's if you are at your system). I am currently not at mine.

Thanks.

---

### Post by sports fan Matt on 2009-04-30
When i got up this morning update manager was immediately there with updates..now im not sure how it had been as there were a hefty amount...If ya'll need more info, let me know

---

### Post by benmoran on 2009-04-30
I very much preferred the old system. In Intrepid it was perfect. Orange bubble for updates, bright red "down" arrow for security updates. This new system is trying to be something it shouldn't.

---

### Post by theozzlives on 2009-04-30
The fix for me works, I got my notification just this morning, just like Intrepid.

---

### Post by mb_webguy on 2009-04-30
> **sefs said:**
> Can someone file a bug report at lanuchpad.net where we can all tag on with our woes (that's if you are at your system). I am currently not at mine.

Thanks.

There already is one on Launchpad ([Bug # 332945]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945"), as well as numerous duplicates), and it's getting a lot of discussion.  Mark Shuttlesworth himself has even made a few comments.

---

### Post by coeus82 on 2009-04-30
How did the old behaviour mess with the notification system?

Why can't the notification system just have that black popup notifier simply say "New updates are available" and have the small icon show up on the tray?

---

### Post by mb_webguy on 2009-05-01
Apparently, the idea is to eventually make the notification area unneccessary, and do away with it completely.

---

### Post by pbpersson on 2009-05-01
I like to have my machine check for updates daily and I like the little icon down in the tray - I check it and wait until there are more than 10 packages before I install them.  I was shocked to find a window buried beneath my other windows with a list of updates I was supposed to install.  What if that window was covered up for days or weeks?

---

### Post by Yfrwlf on 2009-05-01
> **mb_webguy said:**
> Apparently, the idea is to eventually make the notification area unneccessary, and do away with it completely.

Won't happen.

1) You can't use the new notification system to leave this huge black mass at the top right of your screen for days until you finally choose to install updates, not to mention the fact that it doesn't even contain a button to let you open the update manager, it's just not designed for that at all and it wasn't meant for persistent notifications.

2) You can't have programs notifying you about everything by having them open themselves.  The notification area is there to be just that, so that you won't have to open a big window to see what's going on.

The issue here is simple: there are "blurbs", and there are persistent notifications.  The new notification system was designed for blurbs, the tray was designed for persistence.  Having the window pop up is fine for a third option I guess but it should definitely be left as an option because it's annoying.  If they want to get rid of the tray, they need something else there for persistent notifications.  Um, how about...oh I know, the tray?  Sounds good to me! :popcorn:

P.S. yeah I know "tray" is a Windows term, so sue me...wait, don't, they might actually try to do it. :P  THE TRAY IS COPYRIGHT/PATENED BY MICROSOFT ZOMG

---

### Post by mb_webguy on 2009-05-01
That's my argument as well.  There are transient notifications (e.g. "Now connected to the network" or "20% charge remaining"), and then there are persistent notifications (e.g. "Restart required").  The availability of updates would definitely fall into the persistent category in my opinion.  

Persistent notifications need to be both persistent (duh) and unobtrusive.  The notification area is perfect for this, and has the advantage of being a familiar part of the desktop.  Users are familiar with the notification area, and how it's used.

I think it would be a great idea for the new notification OSD to be used to alert the user of important security updates -- in *addition* to the persistent notification of an icon in the notification area.

And having applications open without being initiated by the user is a *horrible* idea.  It's incredibly intrusive and a bit disturbing.  It makes you doubt whether you're really in control of your own system.  Imagine if Firefox automatically opened every time there was an update for one of your extensions...

---

### Post by Peter09 on 2009-05-01
removed text

---

### Post by Aearenda on 2009-05-04
> **Kareeser said:**
> the pop-under behaviour means it flickers first before minimizing.

I watched this happen today on my netbook. The window outline appeared at full size on top of what I was doing, and then it shrank up to the panel, showing a series of ever-smaller boxes as it went. This just looks awful. I often have my netbook connected to a projector, and others will see it. It's no use saying 'it will be faster on a better laptop', that's not the point. 

I am glad there is a gconf setting that allows us to revert this behaviour, and that pidgin can be reverted, because I like the new notification system in general.

---

### Post by Sisophon2001 on 2009-05-05
I only update at night when I have unlimited downloads for free, and for me, the new system is not only annoying but next to useless, because I have to close the window it without updating, and then I must remember run the update manager myself without the benefit of the icon to remind me.

I think the developers were not keeping in mind that people want to set up their personal computers to do what they want, not what somebody else thinks they want. Pop-up windows are distracting and annoying. I set up my notification area to display only what I need it to display, and it works very well. As for the "well documented way to revert to the old behaviour", this needs to be in an option switch, preferably along with a few other options.

I hope this gets fixed in future releases, and is not a trend in UI that ubuntu intends following.

Garvan

---

### Post by leandromartinez98 on 2009-05-06
I also find the new update system extremelly anoying, and a regression. One of the great advantages I think Ubuntu has over Windows is been free of windows poping up warning about updates. Having a daily (or weekly) basis update is not important for the majority of people, and making the update notifier that intrusive makes Ubuntu loose that advantage. I would prefer, a lot, that the update notifier keeps as a small and discrete icon, with eventually a notification that appears ONLY at logon.

---

### Post by sddfdds on 2009-05-09
Has anyone else experienced a problem with the pop-under where it causes the currently open window to disappear?  I was reading mail in thunderbird stepped away, and when I returned my screen was blank.  The only thing in my taskbar was the minimized update-manager, and thunderbird only reappeared when i clicked the update-manager taskbar button

---

### Post by bpursley on 2009-05-13
I also find the new update system extremely annoying, I very much preferred the old system. In Intrepid it was perfect. Orange bubble for updates, bright red "down" arrow for security updates. This new system reflects a Microsoft - let the user be damned approach.

---

### Post by mattalexx on 2009-05-20
> **StevenHarper said:**
> I can see why you newer and more basic users would get annoyed with having to do something every day to keep their OS up to date.

Ugh, I get so tired of Linux geek arrogance.

---

### Post by Yellow Pasque on 2009-05-20
> **sefs said:**
> Can someone file a bug report at lanuchpad.net where we can all tag on with our woes (that's if you are at your system).

That's what this forum and others like ubuntu brainstorm are for. Once an LP bug is confirmed, a bunch of users adding comments that basically say, "Me too; this sucks!" is counter-productive.

SIGNAL > NOISE

---

### Post by mattalexx on 2009-05-20
> **Temüjin said:**
> Rhetorical question: What would happen if your hard disk physically failed right now?

You can say "Back up your data!" all you want but you put it into real terms. Hehe, nice..

---

### Post by coeus82 on 2009-05-20
> **mattalexx said:**
> Ugh, I get so tired of Linux geek arrogance.

He also completely missed the point of the complaint. It had nothing to do with the amount of times the window pops up (hence, having it only pop up weekly is not the solution). I like to keep my system updated daily too, that doesn't mean I want a window to pop up and disrupt what I'm currently work on because there's a new update. A simple notification message would do.

---

### Post by jsenlai on 2009-05-21
The old notification is sufficient and something that I'm really convinient with. At least I can decide when to update and don't have to wait for a week to have my system to be updated. I agree that any application shouldn't pop up just like that as a window. 

It's like to have pop up when u surf the internet and it's something that is mostly blocked by browser nowadays, why make an app acting the same behaviour?

I am sure that this new update-notifier is there for a good purpose, but I just can't see how it's better than the old one.

---

### Post by redDEADresolve on 2009-05-23
popups are never a good idea.

never have been, never will be. what's the point of a notification area if it isnt being used to notify me of updates?

---

### Post by braddock on 2009-06-02
What happened to the wide-spread usability principle that modal dialogs (aka, an unwanted update window) are BAD?

The notification area IS an abused swamp (Shuttleworth's words) IN WINDOWS, where every vendor shoves their logo in your face.

But it is NOT a swamp UNDER UBUNTU.  I have only five VERY USEFUL icons in my notification area.  If I forget what they are I just mouse-over.

Let's not take lessons from Vista and shove unexpected message windows in front of the user every five minutes.  My mother-in-law can barely use Vista because the pop-up modality of it prevents her from simply learning the few tasks she needs to do.

---

### Post by pjalegria on 2009-06-02
I do not understand why such a conversation around this issue, when what is at issue is a simple matter of configuring the system that is at the discretion of each User. If you want de old beavior just unteak at config editor APPS/UPDATE NOTIFIER/AUTOLAUNCH.

---

### Post by theozzlives on 2009-06-02
> **pjalegria said:**
> I do not understand why such a conversation around this issue, when what is at issue is a simple matter of configuring the system that is at the discretion of each User. If you want de old beavior just unteak at config editor APPS/UPDATE NOTIFIER/AUTOLAUNCH.

> Has anyone had probs with Jaunty notifying you of updates? I have Jaunty on 2 computers and have to start Update Manager on both to see if there is updates.

This what started it all, a simple question. Just fix it and quit complaining.

---

### Post by cybergalvez on 2009-06-03
I've changed the settings back to what they should be for the old behavior, and I have yet to recieve a single update notice on my computer at all.  Does anyone know of a reliable way to actually get this working?  At this point I'll take any notification system I just want it to do it automatically

---

### Post by undoIT on 2009-07-18
I've got to say, changing the way the update notifier works was a poor decision. The list of updates is minimized and steals focus from other applications. I stepped away from my laptop and the update notifier loaded up. When I came back, I couldn't click anything in the app I was currently working on. It took me a while to figure out that the update notifier window was minimized and stealing focus.

I think the best way to handle updates is to revert back to the notification icon by default, like it was pre-Jaunty, and then have a callout so people know what the little orange icon means that says something to the effect "5 Security updates available, please update as soon as possible."

Hopefully this is fixed in the next release.

---

### Post by Yfrwlf on 2009-07-18
Ugh, just make it an option, a check box in the software sources configuration window in the updates tab, problem easily solved for everyone without having to know some random command line command.

While it is in the gconf editor, basically equivalent to the registry editor on Windows, just like in Windows there is no link to it from the desktop, and I think such an option does not need to be buried in such an "advanced options" editor, clearly, judging by all the complains about it.

---

### Post by Ron O on 2009-07-20
> Re: Jaunty's update notifier
The default settings have been changed to work better with the new notification framework. To revert to the old settings with the icon in the panel to show updates, open a terminal and run
Code:

gconftool -s --type bool /apps/update-notifier/auto_launch false

After a reboot, the old settings will take effect.

I tried this in Xubuntu Jaunty and the behavior is still the same. I also unchecked Update Notifier in Startup and the application STILL starts on every reboot.

---

### Post by Yfrwlf on 2009-07-21
> **Ron O said:**
> I tried this in Xubuntu Jaunty and the behavior is still the same. I also unchecked Update Notifier in Startup and the application STILL starts on every reboot.

If you do gconf-editor then navigate to the option in apps > update-notifier and then de-select auto launch, it shouldn't pop up.  Haven't rebooted to make sure though.

Maybe an update wiped out your configuration setting?  That would be annoying.

---

### Post by Ron O on 2009-07-22
Thanks YFWRLF. I tried that and it did not work.

I stumbled into a solution within XFCE4 Settings Manager that did work though. Under Sessions and Startup, on the Sessions Tab, I found an Update reference in the list that had "always" listed in the right hand collumn instead of the usual "if running" or "immediately". I selected the line and hit the Quit Program button then the Save Session Button. Problem solved, or at least Update Manager does not start with each reboot anymore.

These forums are listed as "all variants", and it seems like solutions in Xubuntu are often different than those in Ubuntu, which is the variant most posters seem to be working with. I seem to remember that when I started with Xubuntu a few years back, they had their own dedicated forums which I cannot seem to find anymore.

One tool that was recommended in a post was gconf-editor, which is a GUI for gconf terminal commands. It must be included in Ubuntu, but when I went to start it in Xubuntu, I got an apt-get option to install it, which I did, and find it very useful. But I suppose that if I keep adding Gnome applets to Xubuntu, I'll wind up with bloatware which I was trying to avoid by choosing Xubuntu in the first place. Bloatware phobia is an occupational hazard from years of running Windoze.

---

### Post by ssdt on 2009-07-31
Really, could I just add the new style by going to Add to Panel and adding notification Indicator? I tried doing that but seems not to work. Cany help?

---

### Post by J V on 2009-09-23
Just give back the old update notification already...

If its really not flashy enough, make it slowly in a pulsating style switch from orange to red and back...

Not the windows style alerts, they are just insane, but the nice ubuntu-style pulse that is noticable but doesn't shock someone out of their chair...

And if someone really prefers the intrusive popups to the nice freindly pulsating icon, put it somewhere in gconf-editor, its not so much of a priority...

---

### Post by bedhead75 on 2009-09-23
I find that the update manager isn't reliable after resuming from suspend, regardless of whether I switch back to the old style notification or change the settings so that it checks for updates daily.  After resuming from suspend I have to leave my computer on for 24 hours before it checks for updates even though technically 24 hours might have already passed between the time I initially suspended it and resumed from suspend.  If I reboot soon after resuming from suspend, it notifies me of updates within minutes.  Since I don't leave my computer running 24/7 and suspend it at night, I find that I have to run update manager manually each day in order to get any updates.  Does anyone else have a similar situation?

---

### Post by mtb-cliff on 2009-11-06
yeah, I have the same issue. if it sleeps - no updates. If I reboot it usually tells me - but I rarely reboot...

---

