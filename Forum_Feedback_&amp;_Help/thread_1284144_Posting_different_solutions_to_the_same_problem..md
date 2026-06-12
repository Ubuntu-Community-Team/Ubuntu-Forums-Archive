---
title: "Posting different solutions to the same problem."
date: 2009-10-06
forum: Forum Feedback &amp; Help
---

### Post by credobyte on 2009-10-06
> **aysiu said:**
> Why bother editing the kernel line when you can use the built-in recovery mode?
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Is there any difference between these 2 guides, except the fact that they do one and the same thing in two different ways ? I mean, I've quite few solutions to various problems and not always they are the shortest/fastest ones, tough, that's what I prefer.

---

### Post by aysiu on 2009-10-06
> **credobyte said:**
> Is there any difference between these 2 guides, except the fact that they do one and the same thing in two different ways ?
The difference is that the one you linked to requires you to edit a kernel line in the Grub menu, and the one I linked to does not--it uses the existing Grub menu option that boots you into recovery mode.

Why bother editing the Grub menu when the menu entry you need already exists? It's just an extra unnecessary step. > I mean, I've quite few solutions to various problems and not always they are the shortest/fastest ones, tough, that's what I prefer. Unless you're asking help from yourself, then it shouldn't be about what you prefer. The vast majority of users asking for help want their problems solved in the quickest way, not with unnecessary steps thrown in.

---

### Post by credobyte on 2009-10-06
> **aysiu said:**
> 
Why bother editing the Grub menu when the menu entry you need already exists? It's just an extra unnecessary step.  Unless you're asking help from yourself, then it shouldn't be about what you prefer. The vast majority of users asking for help want their problems solved in the quickest way, not with unnecessary steps thrown in.

I'll better suggest something that works and takes a little bit more time, than something that I haven't tried. If there would be only 1 solution, we wouldn't need this forum and discussions about what to prefer and what not, would be useless.
It's easier to install software via Add/Remove or Synaptic .. I prefer command-line - so what ? Shouldn't I reply to any of posts related to installing software for newbies ? 

[COLOR=DimGray]- offtopic -

* Not all messages were moved *
[/COLOR]

---

### Post by aysiu on 2009-10-06
> **credobyte said:**
> I'll better suggest something that works and takes a little bit more time, than something that I haven't tried. If there would be only 1 solution, we wouldn't need this forum and discussions about what to prefer and what not, would be useless. I prefer to suggest something that works that takes less time and fewer steps. There shouldn't be only one solution, but if you have to pick among many to suggest to new users (especially new users with some kind of urgency--"I'm locked out of my system" or "I just deleted something important"), it's not an appropriate time to suggest what you think is a fun fix to do because it takes more time.

> It's easier to install software via Add/Remove or Synaptic .. I prefer command-line - so what ? Shouldn't I reply to any of posts related to installing software for newbies ?  Frankly, you shouldn't. If the new user later wants to play around and figure out how to install stuff with *apt-get*, good for her. But if the new users simply asks how to install stuff, you should refer her to Add/Remove or Synaptic first... or don't reply at all. If you prefer *apt-get*, that's fine for you.

---

### Post by credobyte on 2009-10-06
> **aysiu said:**
> 
 Frankly, you shouldn't. If the new user later wants to play around and figure out how to install stuff with *apt-get*, good for her. But if the new users simply asks how to install stuff, you should refer her to Add/Remove or Synaptic first... or don't reply at all. If you prefer *apt-get*, that's fine for you.

I thought you'll have something better to say .. Linux is all about what **YOU** prefer, not others.

---

### Post by sisco311 on 2009-10-06
> **credobyte said:**
> Is there any difference between these 2 guides, except the fact that they do one and the same thing in two different ways ?


Yes, adding *rw init=/bin/bash* doesn't work. :)

I can not find the bug report (maybe it's fixed now). The splash screen prevents any keyboard input. 

You have to remove the *ro quiet splash* (at least the splash) option from the kernel line before adding *rw init=/bin/bash*.

Moreover, if you boot with *rw init=/bin/bash* the system starts bash after the root partition is mounted and no other init scripts are executed.

In some cases (even if rw is used), the root partition is mounted ro. You are in a very limited shell and some apps may not run properly or at all. i.e. the host name is not set so you can not us sudo(NOTE: i know you are root and you probably don't have to use sudo. this is just an example). 

On the other hand, Recovery Mode (a.k.a. Single User Mode) provides a fully functional recovery shell.

---

### Post by aysiu on 2009-10-06
> **credobyte said:**
> I thought you'll have something better to say .. Linux is all about what **YOU** prefer, not others.
When you're helping others, Linux is about what others prefer.

If you want to help yourself, stay out of other people's support threads.

I prefer *apt-get* personally, but I think new users (unless they explicitly say "I want to learn a command-line way to do this") should be introduced to Add/Remove first.

---

### Post by lisati on 2009-10-08
Opinion 1: In life, there often exists more than one way to solve a problem

Opinion 2: Sometimes the simplest solution is best

---

