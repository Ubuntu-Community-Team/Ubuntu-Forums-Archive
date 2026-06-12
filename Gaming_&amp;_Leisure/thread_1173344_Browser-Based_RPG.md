---
title: "Browser-Based RPG"
date: 2009-05-29
forum: Gaming &amp; Leisure
---

### Post by Bios Element on 2009-05-29
People are always complaining about a massive lack of RPG games for Ubuntu. One thing I've noticed is that there are quite a large number of 'dead' projects and I believe there are several key reasons for this.

Firstly, in any project there is a threshold of entry into the team and depending on what your working with it could be very high (such as C++) or quite low (such as python or perhaps lua).

Secondly, the biggest problem any project faces is burnout. The project founders (aka. the ones paying for hosting) get tired of working on the project and dump it. Keeping projects Open-Source (Or as much so as is possible) mostly negates this problem but it still exists to some degree.

And finally, There's a massive amount of time and energy that must be invested into any project to even get something presentable. Sadly, this means that even projects where huge amounts of effort were expended there is little to show for it.


So now that I've shown where I believe the problems are, let me see what you think of my proposed solutions.

To lower the threshold of entry, The programming language would be python. While PHP is more popular, there are several key advantages to python. Firstly, unlike PHP, there isn't a need to have a full webserver installed which means that a standalone version of the RPG could be created with minimal effort. Using a framework such as Pylons or TurboGears (Based off Pylons) would provide a common platform to develop from.

To prevent burnout, spreading the "authority" and decision-making process throughout a team would prevent every decision being made by one or two people while still keeping things moving in a consistent manor. Disputes would be resolved by assigning heads of "Department" for things such as design, mechanics, rules, art and so forth. Furthermore, the project would be (probably) be hosted on GitHub or (for sure) a similar service. The project would probably be licensed under the Creative Commons Attribution-Share Alike 3.0 United States License. This is to allow more fine-grained control while still ensuring that that the community can freely use/modify/distribute the project.

There really is no simple solution to the amount of time that must be spent but there are several routes that can be taken. The first project will be to design a simple bare bones system with very little in the ways of actual "game" but focusing entirely on function. This will include a basic combat system, mapping system, movement and very basic administrative features. After this is complete we will work to create a very simple "tech demo" style single player game which will allow us to better test things as we add new features. This will also have the effect of attracting new team members and forming a community which can further expedite the development process.


I welcome any questions, comments and ideas and will do my best to respond to every post. It may sound like a pipe dream but if enough people come together, anything is possible.

*Note to mods: I wasn't sure if this was best for games/leisure or programming talk. I kinda figure games/leisure but I may be mistaken. >.>*

---

### Post by Bios Element on 2009-05-31
I gotta admit that I'm quite surprised that there isn't more interest in this. >.>

---

### Post by del_diablo on 2009-05-31
People around here kind of suck at commenting. But it does sound interesting. And i do need something to do this summer besides working.

---

### Post by simeon87 on 2009-05-31
I'm not sure, are you proposing to create a web-based RPG under the conditions that you've described above or is this a thread for discussion?

> **Bios Element said:**
> Firstly, in any project there is a threshold of entry into the team and depending on what your working with it could be very high (such as C++) or quite low (such as python or perhaps lua).

The topic title is about browser-based RPGs which are commonly written in a web language, like PHP or Python as you mention later. The threshold of entry for these language is not very high so I don't think the language is the problem. I think projects come to a halt for other reasons, like lack of organisation or direction or the burnout reason that you mention below. I also think people underestimate the amount of work needed to create a quality RPG: people start creating a website with PHP which is easy and then they come across a web-based RPG. They like it and they think they can create something similar (but always greater than anything ever seen :P). But a web-based game is much larger than a basic website and it takes much effort to create something that is both playable and fun.

> **Bios Element said:**
> Secondly, the biggest problem any project faces is burnout. The project founders (aka. the ones paying for hosting) get tired of working on the project and dump it. Keeping projects Open-Source (Or as much so as is possible) mostly negates this problem but it still exists to some degree.

And finally, There's a massive amount of time and energy that must be invested into any project to even get something presentable. Sadly, this means that even projects where huge amounts of effort were expended there is little to show for it.

These go hand in hand: many programming projects begin with initial optimism but are no longer worked on when the programmer has implemented the feature that he started the project for (i.e., you have an idea, you implement it, you play a bit with it but then it's still a long way from a real application).

> **Bios Element said:**
> To lower the threshold of entry, The programming language would be python. While PHP is more popular, there are several key advantages to python. Firstly, unlike PHP, there isn't a need to have a full webserver installed which means that a standalone version of the RPG could be created with minimal effort. Using a framework such as Pylons or TurboGears (Based off Pylons) would provide a common platform to develop from.

Installing Apache/PHP can be done with a few commands in the terminal and PHP itself is not a difficult language. I agree that Python is a good choice though. But like I said earlier, I don't think the language is the problem because people who think they have the capabilities will learn it anyway. However, you may only want to recruit people that already have programming experience in another language. If you know how to program, you can learn the language on the job but recruiting someone who is learning how to program by working on your project may not be very appealing.

> **Bios Element said:**
> To prevent burnout, spreading the "authority" and decision-making process throughout a team would prevent every decision being made by one or two people while still keeping things moving in a consistent manor. Disputes would be resolved by assigning heads of "Department" for things such as design, mechanics, rules, art and so forth. Furthermore, the project would be (probably) be hosted on GitHub or (for sure) a similar service. The project would probably be licensed under the Creative Commons Attribution-Share Alike 3.0 United States License. This is to allow more fine-grained control while still ensuring that that the community can freely use/modify/distribute the project.

That would be good but usually a hierarchy exists from the beginning of a project: the programmer who started the project and who has invested the most of the time doesn't want the project to by taken over by others who want to take it in a different direction (art-wise or gameplay-wise, et cetera).

Project management has always been difficult :P

> **Bios Element said:**
> There really is no simple solution to the amount of time that must be spent but there are several routes that can be taken. The first project will be to design a simple bare bones system with very little in the ways of actual "game" but focusing entirely on function. This will include a basic combat system, mapping system, movement and very basic administrative features. After this is complete we will work to create a very simple "tech demo" style single player game which will allow us to better test things as we add new features. This will also have the effect of attracting new team members and forming a community which can further expedite the development process.

That would be good.

---

### Post by Bios Element on 2009-05-31
> **simeon87 said:**
> I'm not sure, are you proposing to create a web-based RPG under the conditions that you've described above or is this a thread for discussion?


Really, Both. It's both a proposal and a discussion thread as I'm curious if my logic is sound or totally fried.
> **simeon87 said:**
> 

The topic title is about browser-based RPGs which are commonly written in a web language, like PHP or Python as you mention later. The threshold of entry for these language is not very high so I don't think the language is the problem. I think projects come to a halt for other reasons, like lack of organisation or direction or the burnout reason that you mention below. I also think people underestimate the amount of work needed to create a quality RPG: people start creating a website with PHP which is easy and then they come across a web-based RPG. They like it and they think they can create something similar (but always greater than anything ever seen :P). But a web-based game is much larger than a basic website and it takes much effort to create something that is both playable and fun.

That sums it up. A PHP Hello World script is easy so they think it'll all be as easy and guess what, it's not.> **simeon87 said:**
> 

These go hand in hand: many programming projects begin with initial optimism but are no longer worked on when the programmer has implemented the feature that he started the project for (i.e., you have an idea, you implement it, you play a bit with it but then it's still a long way from a real application).

Which is a major problem. I've seen it happen to quite a few projects so far.> **simeon87 said:**
> 

Installing Apache/PHP can be done with a few commands in the terminal and PHP itself is not a difficult language. I agree that Python is a good choice though. But like I said earlier, I don't think the language is the problem because people who think they have the capabilities will learn it anyway. However, you may only want to recruit people that already have programming experience in another language. If you know how to program, you can learn the language on the job but recruiting someone who is learning how to program by working on your project may not be very appealing.

Sums it up.> **simeon87 said:**
> 

That would be good but usually a hierarchy exists from the beginning of a project: the programmer who started the project and who has invested the most of the time doesn't want the project to by taken over by others who want to take it in a different direction (art-wise or gameplay-wise, et cetera).

Project management has always been difficult :P


Quite true. >.>

---

