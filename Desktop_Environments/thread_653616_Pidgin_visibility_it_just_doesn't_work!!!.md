---
title: "Pidgin visibility: it just doesn't work!!!"
date: 2007-12-30
forum: Desktop Environments
---

### Post by quirks on 2007-12-30
Today I had a closer look at how the visibility modes in Pidgin work, because I noticed that other people can still see me even if I checked "invisible". And this is something really annoying!

So what I did was, I created two separate accounts and logged in with both of them using two separate instances of Pidgin. I added both of them to the buddy-lists.

**1. Test:**
Situation: both are logged in and can see each other being online (visibility: "available").
Action: I switch one of them to "invisible".
Result: the messenger behaves correctly: in the buddy list of the other person, the buddy is in state "invisible" for about half a second and then seems to go offline.

**2. Test:**
Situation: on of them is logged in the other one is logged off.
Action: I log in with the account which is currently logged off directly into state "invisible".
Result: the other person can see the person who has just logged in. But not only that: he can even see that the other person is in invisible mode!!! This is ridiculous!

**3. Test:**
Situation: both persons are "available".
Action: I change the privacy settings of that person to "block all users".
Result: No one else can see that person anymore (appears as "logged off" in the buddy list). However, the little icon next to buddies indicating who is currently blocked doesn't work properly at all! Sometimes, buddies are marked as "blocked", although they clearly aren't. Sometimes, it's the other way around. And sometimes, it works as it should.

**4. Test:**
Situation: both users are logged in.
Action: I switch a little between states "invisible" and "available".
Result: Pidgin sometimes forgets about the blocking settings I have specified for a state. Often, other people are not blocked anymore, although I clearly stated that they should be.

**Conclusion:**
What were the guys who develop Pidgin thinking when implementing that?! That behavior doesn't make any sense! How can I rely on my availability status, when it behaves like that? I will never know, whether others can see me or not, when I switch to invisible-mode. Normal users expect to be truly invisible to all others, when they click on "invisible". And that's the way it should be!!!
In case this is a bug (I'd say it definitely is one - a critical one), why the hell hasn't it been fixed yet (not even in Gutsy)? It's been around ever since I used Gaim/Pidgin. This is one of the most unacceptable bugs for a messenger possible!

I guess, I will look for an alternative application. Any suggestions (should be gtk2-based and support visibility-features and implement them *correctly*)?

quirks

---

### Post by daengbo on 2007-12-30
Well, the future of Gnome (and Ubuntu) is in the [Telepathy]("http://telepathy.freedesktop.org/") backend, which will handle chat, VOIP, and video chat. Currently, you can install [Empathy]("http://live.gnome.org/Empathy") to use the telepathy backend. I think that Gossip also has a fork which suports the telepathy backend, but that's not in the repos. In any case, Telepathy doesn't support all protocols right now. Notably missing is the Yahoo! Messenger protocol.

Empathy is set to be part of GNome 2.22, last I heard, so it will be the official Gnome chat client.

Best of luck,

Daeng
[http://ibeentoubuntu.blogspot.org](http://ibeentoubuntu.blogspot.org)

p.s. Pidgin is kind of famous for being a little spaghettied. The project is working on splitting out the code to make it simpler to manage and on adding some long-requested features.

---

### Post by loell on 2007-12-30
what protocol in pidgin are you referring to?

---

### Post by quirks on 2008-01-01
@daengbo: thanks a lot! That was about the answer I hoped to find. Good two know that there is something better on the way. I don't want to say, I don't like Pidgin, but the invisibility-options are really buggy.

@loell: I was referring to ICQ. Too sad, Telepathy doesn't seem to support ICQ yet. I can't wait for it! :)

By coincidence, I found another instant messenger GnomeICU. I will give that a try.

quirks

---

### Post by mkarnicki on 2008-03-09
This also concerns polish protocol GG (gadu gadu). When I log-in in invisible state, my friend can see my status as off-line, but he gets notification, that "xyz has just appeared". That's ridiculous..

---

