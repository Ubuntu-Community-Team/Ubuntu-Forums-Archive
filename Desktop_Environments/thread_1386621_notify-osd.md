---
title: "notify-osd"
date: 2010-01-20
forum: Desktop Environments
---

### Post by mazz0 on 2010-01-20
Ubuntu's own Canaconical designed notification system has been with us for a while now, I'm wondering what people think about it, having had plenty of time to get used to it.

For me it still has two **major** shortcoming:

1) The positioning is both ugly and impractical:
  i. The weird gap between the bubbles and the edge of the screen/panel just looks wrong
 ii. My notification area is not at the top right, so it's not a consistent place to have the pop-ups
iii. I have two monitors, the right one being secondary - when the pop-ups are on the far right of the right monitor they're not noticeable.
2) They're really annoying when they tell you about something but give you no way of responding to it, such as having no ability to click on the pop-up for an instant message to bring up the window so you can reply.

Point 1, in my opinion, is inexcusable - the position should be customizable and there is no good reason for it not to be.  I'm a little more understanding of the decision to make the pop-ups purely informational and not click-able, although I still strongly disagree with it.

I've raised suggestions on [Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/") for both of these issues, I'll post link when they're approved.

What do poeple think?

---

### Post by omns on 2010-01-20
I have no issues with notify-osd. I quite like it.

---

### Post by twister03 on 2010-01-20
Not exactly problems but they are annoyances. I disable my second monitor for Ubuntu since Compiz fusion allows multiple desktops. Not sure what you mean by a weird gap, but I do wish you could move it to wherever you want (unless you can, I'm still pretty new).

As for the notification being clickable, it would be nice for an option to enable/disable that.

Not to go off topic but is there a way to disable the notification?

---

### Post by mazz0 on 2010-01-21
Hmm, I just tried to replicate the "weird gap" and get a screenshot, but it isn't happening, possibly because the notifications are appearing on my second monitor where there is no panel.  When I'm only using one monitor the bubbles appear what looks like precisely one standard bubble hight below the bottom of the panel, as if leaving room for another bubble.

Yeah, multiple desktops is why I don't much look at my second screen - I usually just have Windows (VBox) running full-screen in there with Outlook in it.

Turning off notifications is generally done on a per application basis, such as in the preferences for Pidgin.  I expect there are preferences options somewhere in sound control to turn off volume notifications and in power for turning off battery notifications and somewhere for brightness notifications, etc.

If you never want to see any notifications you could uninstall notify-osd using Synaptic Package Manager (in your Administration menu).  It'll mean you no-longer have a default Ubuntu installation, but I don't think it will break anything.

Can anyone confirm that?

---

### Post by tgalati4 on 2010-01-21
I have growl (1.1.6) on my powerbook, running Tiger 10.4.x and you have many configuration settings:

Which corner to originate notification bubbles
How long to stay on screen
Style (at least a dozen to choose from)
Which applications use growl for notification--so you can cherry pick those apps and turn off the annoying/unimportant ones.
Listen over the network for other computers with growl notifications--I don't use this, but it could be useful for a small network.

Also, the starting corner position for growl allows one to click the minimize/maximize/close icons of the window behind the notify bubble.  Nofify-osd blocks the corner completely--this is a workflow issue.  I'm running jaunty on this laptop (ibm T43p) and I can't figure out how to change it.

How do I change the default notify-osd offset?

I wish my spanish was better: [http://lamaquinadiferencial.wordpress.com/2009/11/01/posicion-incorrecta-de-las-notificaciones-en-ubuntu-karmic-koala-9-10/](http://lamaquinadiferencial.wordpress.com/2009/11/01/posicion-incorrecta-de-las-notificaciones-en-ubuntu-karmic-koala-9-10/)

Update:  I changed some values in the source code and recompiled.

---

### Post by mazz0 on 2010-01-21
Hmm, I just replicated the weird gap I was talking about.  It seems the volume bubble comes up in the normal position but network bubbles don't.  In these examples I triggered the volume bubble *after* the network bubble had come up, so it's not like it new the volume bubble would need that space.

---

### Post by kaibob on 2010-01-22
About the only time I see the notification is when I'm changing speaker volume. I don't see any gaps, and the position is as good as any.

---

### Post by mazz0 on 2010-01-22
Yeah, looks like volume's OK, but network bubbles come up in a funny place.  I should report that as a bug - I thought it was intentional but maybe not.

You say the position is as good as any, but that's just for you in your current setup - what if you decided to move your panels about, or add another monitor to the right of your current one but that you don't always have your eye on?  The quality of the position depends on context.  I'm not saying the default positions aren't good, I'm saying if they don't suit you you should be able to change them.  I think the idea of simply not allowing this is dreadful.

---

### Post by wojox on 2010-01-22
I just disabled mine but I found this a while back searching: [http://www.ubuntugeek.com/how-to-restore-notifications-position-in-ubuntu-9-10-as-they-did-in-ubuntu-9-04.html](http://www.ubuntugeek.com/how-to-restore-notifications-position-in-ubuntu-9-10-as-they-did-in-ubuntu-9-04.html)

---

### Post by mazz0 on 2010-01-22
Thanks Wojax!  Just installed that, I expect I'll need to log out and in again to test it.

---

### Post by mazz0 on 2010-01-23
Thanks Wojax, that worked - my notifications now all come up near the edge :)

One thing I really like about these notifications (don't remember if it's the case in the old one, but it's certainly not the case in XP) is that notifications for the same thing replace each other - eg if the network connection is lost a bubble comes up to tell you so, then if it comes back that bubble doesn't go away and be replaced by a new one (and they certainly don't /both/ appear like in Windows), but it changes to show that the connections is active again :)

---

### Post by mpt on 2010-01-28
> **mazz0 said:**
> 1) The positioning is both ugly and impractical:
  i. The weird gap between the bubbles and the edge of the screen/panel just looks wrong

For Lucid we were planning to experiment with [three different ways]("https://wiki.ubuntu.com/NotifyOSD#position") of solving this problem (two proposed by sabdfl and one proposed by me). Unfortunately Canonical&#8217;s DX team recently concluded that [they don&#8217;t have enough people &#10005; time]("https://wiki.ubuntu.com/ReleaseTeam/FeatureStatus#Desktop%20Experience") to implement that for Lucid (though anyone else is welcome to contribute).

> *ii. My notification area is not at the top right, so it's not a consistent place to have the pop-ups*

That&#8217;s irrelevant: notification bubbles are no longer attached to the notification area, and [we&#8217;re phasing out the notification area]("https://wiki.ubuntu.com/CustomStatusMenuDesignGuidelines") anyway.

> *iii. I have two monitors, the right one being secondary - when the pop-ups are on the far right of the right monitor they're not noticeable.*

Please report that as a bug if it&#8217;s not reported already. Bubbles are supposed to appear on whichever display contains most of the focused window (since that&#8217;s the display you&#8217;re most likely to be looking at).

> *2) They're really annoying when they tell you about something but give you no way of responding to it, such as having no ability to click on the pop-up for an instant message to bring up the window so you can reply.*

Yeah, using notification bubbles for instant messages &#8212; and relying on you to find the messaging menu to reply to them &#8212; is a bit tenuous. It would be interesting to try using [morphing windows]("https://wiki.ubuntu.com/NotificationDesignGuidelines#Morphing%20window") for IMs instead.

> *Point 1, in my opinion, is inexcusable - the position should be customizable and there is no good reason for it not to be.*

That wouldn&#8217;t solve the problem at all. It would just delegate it from the OS designers, whose job it is to solve these problems, to users who have better things to do.

---

### Post by gradinaruvasile on 2010-01-28
Well plain and simple i dont like it. It is annoying, i cany make the bubble dissappear. The volume/brightness indicator is fine i like it. but the bubbles just suck. I disabled mine, i linked the notification-daemon in place of notify-osd. I just hope the devs wont kill off the old type notifications...

All in all my impression is that it just doesnt cut it as a default notification system. I still like better the old one, i dont have any idea why it wasnt good.

---

### Post by avix on 2010-05-18
bloody annoying! covering up the corner buttons, having to wait forever until they go away. we need a way to just turn them OFF!

---

