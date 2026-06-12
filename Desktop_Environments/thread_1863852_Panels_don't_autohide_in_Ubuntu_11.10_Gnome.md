---
title: "Panels don't autohide in Ubuntu 11.10 Gnome"
date: 2011-10-18
forum: Desktop Environments
---

### Post by electrosnake on 2011-10-18
Greetings to everyone ! I have a problem with my panels in Ubuntu 11.10 distributive, but may be it exists in some earlier distributives too, I switched from 8.10. 

At first, I installed gnome panel to use gnome environment, it is more appropriate for me and I accustomed to it, not unity.

And now my both panels don't autohide at all ! I tried to rightclick on them, but there was no response. I checked configuration at gconf-editor, and what I see is that there is no /apps/panel/toplevels branch. Yes, there is /apps/panel/default_setup/toplevels with two subbranches top_panel and bottom_panel, but there are no keys in them at all, not about hiding, not about nothing. I can't change width, opacity, and I can't force them to autohide, not to mention to set autohide delay :) I tried to add auto_hide and set it to true, but it didn't help. Really, I don't understand what happens with my lovely gnome :)

Please, help anybody.

P.S. I posted it in Main Support Category section, but I have not completely understood description at [http://ubuntuforums.org/showpost.php?p=4526971&postcount=2](http://ubuntuforums.org/showpost.php?p=4526971&postcount=2) : I am absolutely new to this forum, but I'm not completely novice in linux. Should I move it to Absolute Beginner, or it is the right place ?

---

### Post by electrosnake on 2011-10-18
Now I solved part of the problem by some googling: one need to press Alt with right click, and - voila - there is panel menu, and one can make it autohidable. But what to do with gconf and how to tune autohiding time and other panel properties, I still don't know. Actually I have the sensation that all gnome connections with gconf is broken and forgotten now, and I haven't any idea where panels keep their settings.
So help is still needed :(

---

### Post by Copper Bezel on 2011-10-18
I *think* it's handled from dconf-editor, now? I'm not certain on that - I haven't upgraded to Gnome 3.

---

### Post by electrosnake on 2011-10-18
> **Copper Bezel said:**
> I *think* it's handled from dconf-editor, now? I'm not certain on that - I haven't upgraded to Gnome 3.

Thanks a lot for your response ! 
Actually I am speaking about "*Gnome classic*", it is its issues, both "with effects" and without. And as far as I understand, problem is slightly deeper: gconf-editor and dconf-editor are just interfaces to appropriate storages. And there are so little records that dconf-editor shows, and they are nothing to do with panels - it looks like they rather describe their own applications (unity or gnome-3, I don't know). And I'm just interested: where in the hell that panels keep their settings :p

P.S. by the way, can you help me with some other problems :p: how to tune this forum to send notifications about replies to my posts to my mailbox ? I thought It would be automatically, but I didn't received nothing till now. And is there any way to get list of my posts ? I had to search my question through the list of all posts in this theme, using firefox inpage search

---

### Post by Copper Bezel on 2011-10-18
The best way would probably be to "subscribe" to the thread in Thread Tools in the upper right. You can set an e-mail notification, but not a PM notification. The idea is, you could post your problem and be somewhere else doing other things and still get back to it if someone has a follow up question or solution, and while you're here, you can watch your subscriptions from the Control Panel.

gconf-editor is a front end for gconf, which is a big folder heirarchy where Gnome, and a bunch of other apps, used to store their settings in Gnome 2. Most of them still do, including Compiz, apparently, in Gnome 3.  Other front ends for gconf include gconftool-2, which allows you to run complex and automated edits from a terminal window. However, Gnome itself now uses dconf, which is a compressed database to which dconf-editor is presently the only front-end.

If the panel itself doesn't store settings in gconf or dconf, which is apparently the case, the next likely option would be a folder in .config or its own hidden folder in your home directory. But it would be difficult to guess the folder name, which might or might not have "panel" or "fallback" in it.

If that's the case, though, there probably isn't any more fine tuning that you could do from there, such as autohide time and size when hidden, as you could with the old Gnome Panel. Sorry. = (

---

### Post by electrosnake on 2011-10-18
> **Copper Bezel said:**
> The best way would probably be to "subscribe" to the thread in Thread Tools in the upper right. You can set an e-mail notification, but not a PM notification. The idea is, you could post your problem and be somewhere else doing other things and still get back to it if someone has a follow up question or solution, and while you're here, you can watch your subscriptions from the Control Panel.

gconf-editor is a front end for gconf, which is a big folder heirarchy where Gnome, and a bunch of other apps, used to store their settings in Gnome 2. Most of them still do, including Compiz, apparently, in Gnome 3.  Other front ends for gconf include gconftool-2, which allows you to run complex and automated edits from a terminal window. However, Gnome itself now uses dconf, which is a compressed database to which dconf-editor is presently the only front-end.

If the panel itself doesn't store settings in gconf or dconf, which is apparently the case, the next likely option would be a folder in .config or its own hidden folder in your home directory. But it would be difficult to guess the folder name, which might or might not have "panel" or "fallback" in it.

If that's the case, though, there probably isn't any more fine tuning that you could do from there, such as autohide time and size when hidden, as you could with the old Gnome Panel. Sorry. = (

Thank you for your reply again !

1. Sorry, I didn't completely understand what means 'PM notification'. I subscribed in the process of previous reply, but letter said to me that "There may also be other replies, but you will not receive any more notifications until you visit the forum again." What means "visit forum" I didn't understand either. It obviously doesn't mean that when I open forum and login, if needed, I'll receive all new notifications at that specific moment. But what ?
2. Back to my title question. Thank you, now I understand, why and what for this weird dconf exists, but its interface is very poor, I even can't search throw all records to find 'panel'. And sometimes it hangs and one have to kill it from command line. 
And what I completely don't understand is what is the need to break connection with perfectly working tool like gconf storage and shift back to ugly olf-fashioned-style configuration file ? How do you think, is it a good idea to e-mail to panel developers (nice, but probably very busy guys which receive near a billion letters per minute) ? or may be better I should ask question at some gnome-developers forum ? or either it could be possible to report this issue as a bug to some kind of bugzilla ? If you know some places, please tell me

---

### Post by Copper Bezel on 2011-10-18
> Sorry, I didn't completely understand what means 'PM notification'.
I wasn't sure whether the "mailbox" you were referring to was your e-mail mailbox or your Private Message mailbox here at UF.

> What means "visit forum" I didn't understand either. It obviously doesn't mean that when I open forum and login, if needed, I'll receive all new notifications at that specific moment. But what ?
It just means that you'll only be notified once while you're away.

> And what I completely don't understand is what is the need to break connection with perfectly working tool like gconf storage and shift back to ugly olf-fashioned-style configuration file ? 
I don't fully understand that either. Supposedly, dconf is faster and more versatile - you can see more details on Gnome's  [_project page for dconf._](http://live.gnome.org/dconf)

---

### Post by electrosnake on 2011-10-18
> **Copper Bezel said:**
> 
I don't fully understand that either. Supposedly, dconf is faster and more versatile - you can see more details on Gnome's  [_project page for dconf._]("http://live.gnome.org/dconf")
But they didn't use dconf (afaik) ! :) They just break with gconf instead :)
P.S. I'll probably try strace to catch panel on writing to the file :) but they could use some advanced techniques like dbus, I'm afraid :)

---

### Post by Copper Bezel on 2011-10-18
Yeah, and I think they're trying to phase out gconf in any case, even if for the panel, they didn't decide to save its settings in dconf. 

I think it is more complicated, yeah - if the panel settings are stored in dconf, the panel is more likely to send a message to gsettings, which will then send off to dconf, as opposed to the panel process making the change itself directly to the dconf database file. Of course, since you said there aren't any keys in there for the panel visible in dconf-editor, those settings are probably stored somewhere else.

---

### Post by crdlb on 2011-10-18
The panel stores its configuration in dconf at org.gnome.gnome-panel. It looks like some of the applet-specific configuration is still in gconf though. I'm sure that's just temporary.

---

### Post by electrosnake on 2011-10-18
> **crdlb said:**
> The panel stores its configuration in dconf at org.gnome.gnome-panel. It looks like some of the applet-specific configuration is still in gconf though. I'm sure that's just temporary.

Aha ! Sorry for my mistake, it wasn't so hard to scan all tree entirely,  probably ten-twenty minutes, but I wasn't accurate and missed it.  Thanks a lot !
It's a kind of mistery why gnome and gwibber are in org, and other applications are in apps. And another mistery, why they drop structure from gconf and build another one; and third :) - why don't they just extend gconf-editor to support both engines (because gconf-editor let you bookmark and search) - or do some copy-paste, actually application is very simple and source code is tiny.

Thanks again, you have solved all my problems. Now, I think, I can close this issue

---

### Post by electrosnake on 2011-10-18
Last time sorry, pals, but HOW TO MARK THIS THREAD AS SOLVED ???
:lolflag:

---

### Post by crdlb on 2011-10-18
The reverse domain name structure matches the one used by dbus and helps prevent name collisions. The names that don't start with a TLD are mostly straight ports from gconf, and will probably be fixed over time. Also, dconf-editor certainly lacks polish, but I think it would be more work than you suspect to retrofit gconf-editor. It would be easier by far to add the missing features to dconf-editor.

---

### Post by electrosnake on 2011-10-18
Thank you very much for thorough explanation of this important details.
The only urge for criticism remained in me is feeding by feeling that
semi-finished components and technologies should not be a part of production state system; so may be a better solution would be to incorporate dconf storage into testing-state version and wait until it would be ready for the incompetent user - with bugs, probably, but without semi-finished stuff. Because bookmarking is may be polish indeed, but searching is very important.
 But may be I do not understand all subtleties of the issue. 
And one more thing, sorry again, seriously bothers me - why press right button WITH ALT ? I believe that very reasonable explanations exist, but I myself cannot invent any

---

### Post by crdlb on 2011-10-18
> **electrosnake said:**
> why press right button WITH ALT ? I believe that very reasonable explanations exist, but I myself cannot invent any Well, the panel has always had the problem that it was too easy to accidentally modify. I would have preferred a more discoverable solution such a firefox-style "edit mode", but I suspect that'd be a lot of work.

---

