---
title: "Evolution Calendar Month View - 7 day week?"
date: 2009-04-22
forum: General Help
---

### Post by Herman on 2009-04-22
Hey, all my life there have been seven days in every week.
It has been so ever since the beginning of time, (so I'm told). 

:) Somebody who made up Evolution calendar thinks there are only five full days and two half-days?

How do I get Evolution Calendar to display all seven days in every week when it's in month view?

Every day of the week is equally important to me, there are no half days.

I really like Evolution apart from that one problem and I want to keep on using it and I don't want to have to add some other separate calendar program. I like the way the Evolution calendar is integrated.

Is it just me? Is there a setting I have missed? 
I have tried, but all I can do so far is make the two half-days be in some other column.
If no-one here can help me, I'll go ask the evolution maintainers, but I thought I'd ask here first in case there's an easy fix.

Regards, Herman :)

---

### Post by joeyknuccione on 2009-04-22
Do:

Applications>System Tools>Configuration Editor

In that do:

apps>evolution>calendar>display

In that uncheck compress_weekend

---

### Post by Herman on 2009-04-22
:) Thank you for your response.
I looked for Applications>System Tools>Configuration Editor but I can't find it, according to Add/Remove, 'configuration editor' is installed.
I'm out of time for now though, thanks for your help.

EDIT: 
AHA:
```
herman@amd64hh:~$ gconf-editor
```
Thank you.

Regards, Herman :)

---

### Post by egalvan on 2009-04-22
> **joeyknuccione said:**
> Do:

Applications>System Tools>Configuration Editor

In that do:

apps>evolution>calendar>display

In that uncheck compress_weekend

Absolute Thanks!

That fixed a problem that cropped up exactly five minutes ago!

I started setting up Calendar on my Work Laptop...

Again, Thanks!

---

### Post by Herman on 2009-04-22
:) That worked! Thanks once again, joeyknuccione :)

---

### Post by egalvan on 2009-04-22
> **Herman said:**
> :) Thank you for your response.
I looked for Applications>System Tools>Configuration Editor but I can't find it, according to Add/Remove, 'configuration editor' is installed.
I'm out of time for now though, thanks for your help.

EDIT: 
AHA:
```
herman@amd64hh:~$ gconf-editor
```
Thank you.

Regards, Herman :)

It may also be that "Edit Menus" will get that app...

Right click the Gnome menu...

it was the problem for me...

And Thank You for your HermanZone web site...

it is absolutely remarkable!

---

### Post by joeyknuccione on 2009-04-22
Jaunty-

In helping with this I notice that Evolution in Jaunty compresses Wed/Thu when w/ends are uncompressed, and Sat and Sun are set as working days.

My Report a Problem feature is broken at the moment so I can't tell if this is a bug or what. Any ideas?

---

### Post by Herman on 2009-04-25
My Jaunty Jackalope has Sat/Sun compressed, and as far as I know all Ubuntu installations have that in the Evolution Calendar by default. 
I suppose that would be a bug if it happens to all new Jaunty installations. The installation I have here is one I've had for a long time, so the fact that mine's okay doesn't rule out the possibility that a bug could exist in a more recent Jaunty CD.

You probably already know this but in Calendar view I can change mine by going 'Edit'-->'Preferences', and check that 'Calendar and Tasks' is highlighted in the left-hand column.
Under the 'General' tab, look for the heading 'Work Week', and use the 'Week starts on:' spinbox to change which two days are compressed.

That's not as good as making all seven days equal though.

Sorry for the late reply, I have been away for a few days doing some travelling. I'm home again now though.
Regards, Herman :)

---

