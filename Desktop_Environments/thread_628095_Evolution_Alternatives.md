---
title: "Evolution Alternatives"
date: 2007-11-30
forum: Desktop Environments
---

### Post by lsutiger on 2007-11-30
I looked through countless posts while looking for an alternative to Evolution. What hapens in most posts is that everyone talks about how great evolution is, not what the alternative is.

The problem I have is that it is buggy with HTML mail, locks up a whole lot with large attachments, and all in all, just is BUGGY! (Yes I do run Compiz)

I want something that is similar to a full package like Outlook (which Evolution is trying to mimick). Is there an alternative?

---

### Post by TeaSwigger on 2007-11-30
Hello, 

You bet :) There are a number of approaches you can take, from outlook-ish to command line types. 

I'm assuming you're running ubuntu 7.10 (Gutsy Gibbon)? Two of them that would be easy and quick to try would be Claws (Sylpheed-Claws-gtk2 or Claws, search in Synaptic; name changed recently and I'm not sure which it'd be called for ubuntu 7.10; also note it has a number of optional features you can choose to install with it) and of course Mozilla Thunderbird. If you're using Kubuntu (or if you're not and want to try it anyway), there's also KMail for a third option. 

There are more choices out there, but it's probably easiest to see if any of those will do. :)

EDIT: as a note, Thunderbird is much more widely used, being on linux and Windows, while Claws is lighter, faster and can be more richly configured.

---

### Post by exactopposite on 2007-12-01
i really like thunderbird personally. i've been uing it for at least 5 years now (before i ever tried linux)  and it works well for me. i haven't tried evolution tho, so i can't say how the 2 stack up.

---

### Post by rplantz on 2007-12-11
> **lsutiger said:**
> 
I want something that is similar to a full package like Outlook (which Evolution is trying to mimick). Is there an alternative?

The suggested programs, Thunderbird and Claws, are not "full package." They only do email.

I've used Evolution for several years. I use the calendar and contact features quite a bit. I like it because it syncs with my old Palm PDA.

The latest version, 2.12.1, is VERY buggy. For example, it's time for me to send my holiday cards. All my contacts have been assigned to categories. But filtering on categories is broken in this version. (Yes a bug report has been filed. The claim is that it's fixed, but the fix has not made its way to the Ubuntu repositories.)

I have tried jPilot, but it only allows one category for each contact. And it's nice to have all my email, contacts, and calendar interact with each other so I don't have to keep duplicated info in sync.

The only thing I don't like about Evolution (aside from its current bugginess) is that it reminds me of Outlook.

---

### Post by steve_waters on 2008-01-10
I have also fund the latest evolution locking during mail creation, it pauses while i am entering the message but then catches up and spits out all the characters i have entered while it was paused, very painful.

If you are in KDE, or not I suppose you could install and run it anyway, is Kontact it is a complete package you are looking for and is quite nice to use. But as with most things KDE I find it to over the top. But it is good none the less......

From Add/Remove Applications:

KDE pim application  
Kontact is the integrated solution to your personal information management needs. It combines KDE applications like KMail, KOrganizer, and KAddressBook into a single interface to provide easy access to mail, scheduling, address book and other PIM functionality.
This package is part of KDE, and a component of the KDE PIM module. See the 'kde' and 'kdepim' packages for more information.

Homepage: [http://kontact.kde.org/](http://kontact.kde.org/)


Good luck.....

---

### Post by chadeldridge on 2008-03-14
If you turn off the ability to auto load images in HTML mail it seems to fix that stability issue.  Although its a very annoying workaround.

---

### Post by tone77 on 2008-03-18
Has anyone tried evolution 2.22 that is part of Hardy?  It is stable?

I am probably going to get nailed for this, but do the guys who code evolution even use it?  It is the only thing on a Linux box that works with Exchange email, and calendar, but it so slow and buggy?

---

### Post by Unconscious on 2008-03-18
I too have had problems with evolution. I used to try it on every upgrade, but I don't even bother anymore. 

I've also found most of the palm related stuff to be fairly buggy and inconsistent as well. 
In my experience, Palm support is one area where ubuntu is pretty weak.

---

### Post by rune0077 on 2008-03-18
+1 for Kontacts. I'm using Evolution now, but used for a while before that, and it's really good (looks and feels a lot more "professional" than Evolution). Problem is it's KDE, so it won't integrate so nicely into your desktop and you need all the KDE libraries installed to work (but will work well once that's taken care of).

---

### Post by tone77 on 2008-03-18
How does Kontact integrate with an Exchange Server?

---

### Post by chadeldridge on 2008-03-18
I think through LDAP .. and my understanding is "poorly".

---

### Post by pbhill on 2008-03-18
Take a look at Mozilla Lighning, a plug in for Thunderbird.

[http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/)

---

### Post by chadeldridge on 2008-03-18
A note of caution about Lightning that I experienced while using it.  If your exchange server is in a TZ that is different than your own there is a known bug that will cause some of your appts to be massively off in time ranging in time from 2 - 5 hours. 

Just a tidbit of fyi.

---

### Post by tone77 on 2008-03-19
I have tried Thunderbird with Lightning and IMAP works great, but Lightning can only handle accpeting calendar events to the local calendar.  It does not have the ability to create meetings, etc. on the Exchange server.

---

### Post by chadeldridge on 2008-03-19
Unfortunately then your only option is Evolution.

---

### Post by tone77 on 2008-03-19
Thanks a bummer, as Thunderbird with Lightning is such a good combo

---

### Post by chadeldridge on 2008-03-19
I completely agree, but it seems that you are stuck in the same boat as I am.  Hurts even more that I am the Exchange server admin and I am stuck with the least working mail in the company thanks to Evolution's crumminess.

---

### Post by tom_e_reynolds on 2008-03-20
Hi all,

This is day three of my Ubuntu 7.10 experience.

I am also trying to get an email client to work with my Exchange 2003 Server.  Evolution has worked great for 3 days...when it doesn't lock up...which is about once every 2 hours for me now.

As an alternative, I just loaded Thunderbird via IMAP settings, but notice that all my sub-folders under my inbox are not showing up?  Am I missing something?  (I get 100s of emails per day and must have rules that sort some of them, so I need to be able to access these subfolders.)

Are there other clients better suited for accessing MS Exchange?

Any help would be appreciated!

-Tom

---

### Post by chadeldridge on 2008-03-20
If you are using IMAP then you need to subscribe to those other folders in thunderbird.

File - subscribe, click the folders you want.

And any mail client will work with exchange that supports IMAP, but you will loose your collaboration features:  Calendar/Global Address Book (can be setup through LDAP, but painful

---

### Post by guapo32 on 2008-03-20
Jumping on the Evolution-naysaying bandwagon here.  I'm currently on vacation, but I ssh into my home machine occasionally to do random things (a.k.a. "did I leave Amarok on..?").  Well I just did a *ps aux* and lo and behold, Evolution was chewing on something with ~90% CPU time... and I don't even _use_ Evolution for anything!  I'm running Hardy, so take this with a grain of salt.

---

### Post by postilion on 2008-04-04
So I may be forced to get back to using Evolution (2.22) since my firm are moving to GroupWise, and getting that to work on a 64 bit Ubuntu is more work than I care for right now.

And please, don't regale me with this or that application is better :-|, unless it offers complete GroupWise integration, it isn't, so I am left with Evolution or GroupWise - Thunderbird won't cut it.

My beef with Evolution, aside from stability problems, is that there are all of these things I do not use which I cannot get rid of.  For example, in the calendar view, the sidebar is littered with calendar types which I do not use:
[LIST]
[*]CalDav
[*]Google
[*]On This Computer
[*]On The Web
[*]Contacts
[*]Weather
[/LIST]
At the *bottom* of the list is the only one I actually care about, the only one I actually configured: My GroupWise calendar.  I can understand that there are people who want all of these other calendar types, but since I don't want to use them I should be able to remove them from the sidebar so I can see the one I actually use without having to scroll down to get to it.
The same sorts of problems pop up in the other modules; mail, contacts, memos, tasks.  I am a network dweller, so I don't want *anything* to be local, yet in Evolution the assumption is that I will.

I have removed the Google and CalDav plugins and yet I still see these things wasting real estate in my sidebar.

I will suffer through, but it is a yucky experience not to be able to control the application.  If I wanted my GUI experience to be shackled I would use Windows.
     -nic

---

### Post by lsutiger on 2008-04-12
Ok I downloaded Kontact and it looks sweet. Now I am looking for how to import my mail/contacts/etc from evolution to kontact. There is not an option in the menu, and goole only offers the reverse. Anybody here have a link or have done it before?

---

### Post by rune0077 on 2008-04-14
For your contacts, just right click the contact register you want to import into Kontact (like "Personal" etc), then select "Save as vCard". You should then easily be able to import this file into Kontact (or any other mail client that uses vCards).

As for mail, you need to locate the file where Evolution has all your mail stored, then somehow tell Kontact to use that same file (not sure how to go about that, though).

---

### Post by commonlyUNIQU3 on 2008-06-04
> **postilion said:**
> So I may be forced to get back to using Evolution (2.22) since my firm are moving to GroupWise, and getting that to work on a 64 bit Ubuntu is more work than I care for right now.

And please, don't regale me with this or that application is better :-|, unless it offers complete GroupWise integration, it isn't, so I am left with Evolution or GroupWise - Thunderbird won't cut it.

My beef with Evolution, aside from stability problems, is that [B]there are all of these things I do not use which I cannot get rid of.  For example, in the calendar view, the sidebar is littered with calendar types which I do not use:
[LIST]
[*]CalDav
[*]Google
[*]On This Computer
[*]On The Web
[*]Contacts
[*]Weather
[/LIST]
At the *bottom* of the list is the only one I actually care about, the only one I actually configured: My GroupWise calendar.  I can understand that there are people who want all of these other calendar types, but since I don't want to use them I should be able to remove them from the sidebar so I can see the one I actually use without having to scroll down to get to it.
The same sorts of problems pop up in the other modules; mail, contacts, memos, tasks.  I am a network dweller, so I don't want *anything* to be local, yet in Evolution the assumption is that I will.[/B]

I have removed the Google and CalDav plugins and yet I still see these things wasting real estate in my sidebar.

I will suffer through, but it is a yucky experience not to be able to control the application.  If I wanted my GUI experience to be shackled I would use Windows.
     -nic

You can change the order that these entries appear in (i.e. move your groupwise account to the top) in the gnome configuration editor.  Just run:

```
gconf-editor
```

Then go to apps > evolution > calendar, then select (double-click) "sources", then re-order the sources.
I also imagine that you could delete the other sources, but I didn't want to do that on my system.

I hope this helps!

---

### Post by chadeldridge on 2008-06-04
.

---

