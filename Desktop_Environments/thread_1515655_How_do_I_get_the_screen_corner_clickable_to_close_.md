---
title: "How do I get the screen corner clickable to close maximized windows?"
date: 2010-06-22
forum: Desktop Environments
---

### Post by inaneframe on 2010-06-22
Before I go any further let me make it perfectly clear that this post is not in regards to Shuttleworth's recent decision to move the "titlebar buttons".  I honestly don't care and in fact it saves me time since I've always moved the close button to the left side and then removed the minimize and maximize buttons anyway.

This problem is made even more annoying because I thought we were all done with it.  I've been back and forth between distros, KDE, and GNOME since 2000. . . I would run head first into this issue often out of nowhere. . . I feel like I'm back in 2003 again.

According to Fitt's Law, corners and edges have infinite width as far as the user is concerned, one of the reasons I have loved GNOME for so long now is because of the use of corners, so imagine my surprise when I can no longer simply throw my mouse cursor up into the corner and simply CLOSE the maximized window that I'm currently using, instead it drags the window.  This is obnoxious and useless.  I can already grab at any other part of the top edge of the screen outside of the far corner in order to drag a window, why is this happening again?  It is SO frustrating particularly since GNOME is supposed to be so damned concerned with usability.

I think this change might have something to do with that monstrosity known as gnome-shell.  I guess they were figuring that with the proposed 2.30/3.0 switch over to this new window manager, they could simply do whatever they like with metacity. . . or maybe gnome-shell USES the same configurations as metacity (seems plausible), all that I know is that this truly pisses me off.

It may seem trivial but it's a daily use factor for me and I have no way of changing the behavior.  I just want to be able to throw my mouse in a corner and click, it never seemed that big of an issue in the past, I don't see why the developer(s) saw the need to change this.

And to forestall all those that would ask me to switch from metacity to compiz or vice-versa, it's with both and I am NOT going to use compiz's own digusting window manager themes, I like my metacity themes.
My other choices are KDE, enlightenment, openbox or Xfce,  Well the first two are travesties since I'm used to my GNOME applications and they don't look good in those DE's, the third looks like crap (to me) and Xfce has corner close button functionality only per theme (some themes do and some don't) but I'm sorry I love my gnome-panel too much.  I'm very happy with the default Ubuntu layout but this change is just so annoying.

Am I alone?

---

### Post by aysiu on 2010-06-22
To anyone who wants to start an argument, the OP is actually looking for support on how to fix this, not a debate about whether it is a good implementation or not (despite the tone of the post).

---

### Post by ve4cib on 2010-06-22
I posted this in the earlier incarnation of this thread over in the cafe, but I'll duplicate my post here, in case anyone else with this issue is interested and doesn't frequent the cafe:

> I always have a top panel, so I run into this sort of issue a lot with the close/max/min buttons with maximized windows.

[This panel applet](http://gnome-look.org/content/show.php/Window+Applets?content=103732) is a very nice solution to the problem though. Basically you remove the border entirely from maximized windows, and move the close/max/min buttons onto the panel. They're clickable from the extreme corners of the screen, and they work very well with Metacity. Combine that with a global menu applet and the result is pretty slick.

---

### Post by inaneframe on 2010-06-23
> **aysiu said:**
> (despite the tone of the post).

Please reread my post again, where is there a tone in my original post?

I am listing the steps I'd taken to this point to try to resolve this issue, I went out of my way to tell people that my post has nothing to do with the placement of the window manager buttons.

What was the first reply I get?  "Open up gconf-editor and you can move the buttons to the other side".  You can't understand why I might take "tone" or get upset after I'd implicitly stated very VERY clearly in my first post that it had nothing to do with placement of buttons?  I KNEW that people would say that, I tried my very best to avoid it but it happened anyway.  And this, KNOWING that people would do this, trying to avoid it after months of dealing with this issue trying different ways of fixing this and getting no results.

Might I ask why or how you seem to believe that there is a "tone" in this first post?  Please point to one single section of this first post that has some kind of "tone" you are describing.

Do you mean where I state the facts concerning Fitts's Law?  I'm sorry, do you consider anyone displaying any kind of knowledge of a subject for which they are asking a tone?

I never had a tone until people went out of their way to NOT READ my post and respond in the exact way I ASKED THEM NOT TO, moved my post because they deemed my attempt at an EXACTING PRECISE SUPPORT QUESTION a "rant", or questioned my logic in desiring a behavior that had been STANDARD up until this point.

WTF?!?!

Whatever.  It's obvious I'm not going to get the hail mary of a response that is ACTUALLY HELPFUL that I was hoping for. . . I've seen two people that attempted to actually help so far and nothing more.

I just wish people would NOT RESPOND if they don't know how to fix the problem or don't understand the question.  It's not helpful.

"HERP DERP, DO YOU REELY NEED THIS?!?!  HERP!!! can't you just make teh buttons biggur??? LOL!?!"

And then they act like I AM the one being RUDE when I don't take kindly to their waste of a response.

Look, I'm not looking to have any "tone", I'm not looking for an argument, I never intended to "offend" you with my precise question but this is exactly the kind of crap that I DIDN'T need.  This is a HUGE waste of time, this whole interaction.  I'm already frustrated due to an omission of a nearly DECADE long feature.  What the hell?  I JUST WANT SOME HELP, NOT A DAMN DEBATE!  Is that enough of a tone?

---

### Post by ve4cib on 2010-06-23
> **inaneframe said:**
> Please reread my post again, where is there a tone in my original post?

I don't really need to point anywhere beyond this passage from your second post to illustrate your adversarial -- and yes: rude -- tone in both posts:

> Look, I'm not looking to have any "tone", I'm not looking for an argument, I never intended to "offend" you with my precise question but this is exactly the kind of crap that I DIDN'T need.  This is a HUGE waste of time, this whole interaction.  I'm already frustrated due to an omission of a nearly DECADE long feature.  What the hell?  I JUST WANT SOME HELP, NOT A DAMN DEBATE!  Is that enough of a tone?

There's a difference between politely, neutrally outlining the problem and the steps you've tried taking to solve it, and jumping up and down demanding that your way of doing things is correct, and berating anyone who offers a dissenting opinion.

In the earlier thread someone actually pointed out that not having the close buttons clickable from the extreme corners could be a good thing, since it reduces the chances of accidentally closing a window.  Whether or not you agree that is a valid point.

The other thread also suggested that if someone made a patch that allowed you to edit these settings via GCONF that such a patch would likely be accepted, thus solving the problem for everyone.  If you have any coding experience you could try taking that on yourself.  Or you could register a feature proposal and ask that this be patched in the next release.


Completely aside, but if you go with a Gnome/OpenBox session (using OpenBox instead of Metacity for window decorations -- there's an option for this in the GDM sessions if you install OpenBox in Ubuntu) does this problem go away?  Yes, I know you said that Metacity is your preference, but there are some nice OpenBox themes out there, and you'd still have the Gnome-Panel, and your GTK+ applications should still look exactly the same (minus the window borders).

Anyway, as one of the two people who tried to help you, I'm sorry I couldn't be more useful.  Good luck, and I hope you find a satisfactory solution for the problem.

---

### Post by cariboo on 2010-06-23
@inaneframe

From the forum code of conduct:

> Be respectful of all users at all times. This means please use etiquette and politeness. Treat people with kindness and gentleness. If you do this the rest of the code of conduct won't need more than a cursory mention.

This thread doesn't seem to be going anywhere. Closed.

---

