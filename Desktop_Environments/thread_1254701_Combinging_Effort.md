---
title: "Combinging Effort"
date: 2009-08-31
forum: Desktop Environments
---

### Post by Attean on 2009-08-31
Hey, my first post here but I signed up to start this discussion since I didn't see one similar. I've been a Windows app developer for years but mostly just dabbled in linux distros.

I saw a speech a while back from someone in the OS community talking about how they really needed to combine effort if linux was ever to gain massive adoption. I'm trying to get a handle on why the basic application libraries for KDE and Gnome aren't unified, with their direction controlled by an independent commission, with its own release dates, similar to .NET in Windows. I realize KDE offers features that GNOME doesn't, but the libraries applications on the front-end have access to really shouldn't change. That just leads to duplication of effort for developers and confusion for end users. 

It seems like the lack of abstraction between projects is really lacking. If the libraries were abstracted and given independence, it would turn the KDE and Gnome packages into themes, essentially. All these independent projects make potential developers like me feel like the whole thing is a bit of a futile enterprise.

Is there any collusion between these two groups (KDE and GNOME), and if not, why?

---

### Post by earthpigg on 2009-08-31
hi,

i am not a programmer, but i will toss in my $0.02 as an end user.

what put you under the impression that a KDE app will not run in GNOME, or vice versa?

I run apps for both on a regular basis, and I use *neither*.

If you develope a KDE app using standard KDE libs, that will *not* stop GNOME users from being able to run it. Pick the one you like and develope for that.

picking on or the other to develope for really only matters if you are trying to build something lightweight - something proprietary software very rarely even attempts to do. especially if it is specifically targeted at enterprise use.

it doesn't lead to duplication of effort for devs unless they chose to duplicate their efforts. Opera Web Browser, proprietary VirtualBox, and World of Goo are some examples of proprietary software that does **_not_** release in separate versions for separate DEs.

World of Goo just tosses every library it needs in /opt when it installs and doesn't worry about the DE.

The vast vast vast majority of needs for GNU/Linux users are satisfied by what we can already find in the repos - Free Software developed by GNU/Linux users for GNU/Linux users.

What kind of software do you intend to develop for Linux, if I could ask?

> I'm trying to get a handle on why the basic application libraries for KDE and Gnome aren't unified, with their direction controlled by an independent commission

one size does **not** fit all, ergo there are people that use OS X and Linux.

within the Open Source community, *competition is celebrated* rather than duplication of effort being concerned about. GNOME and KDE both ripoff concepts and ideas from each other and other user interfaces all the time. this is not seen as a bad thing - in fact, if someone uses your idea it is considered among the higest forms of flattery.

---

### Post by Attean on 2009-08-31
I think you'd really need to be a programmer to understand what I meant by abstraction (maybe not). Most people don't want to deal with interoperability. They want libraries that do that for them. I realize you can get the programs to work under either, however, a lot of the interoperability is duplicated and/or doesn't work. All the fringe benefits of using a unified system are lost if you cross Gnome applications over to KDE and visa versa, at least in my experience. For example, in Amarok in Gnome, the CD burning utilities don't do squat unless you do some crazy workarounds. That's just confusing for end users and totally unnecessary from a developer's point of view. I do NOT want to deal with two separate DVD/CD burning engines. Competition is not always a good thing for the end user and the linux communities "do two of everything" and it'll be better seems counterproductive and silly to me.

Right now, I'm writing a script parser with ANTLR that generates UIs based on the contents of the scripts. It works over a broad range of scripts and there's no reason it couldn't work in linux, but it's in C# and the GUI elements utilize WPF so converting it would be a nightmare, given all the data binding it employs. :D

---

