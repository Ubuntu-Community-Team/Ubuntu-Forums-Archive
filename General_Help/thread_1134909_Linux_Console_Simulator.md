---
title: "Linux Console Simulator"
date: 2009-04-24
forum: General Help
---

### Post by David C. on 2009-04-24
Didn't know exactly where to post this and didn't find anything regarding this in the forum.

Is anyone aware of an existing software app that simulates the CLi? Something that a beginner to Linux can install and utilize to learn Linux commands, what they do, how they function, etc. It wouldn't be a real terminal tied into the existing Linux OS, but a "dummy" or simulated linux os. Something similar to the networking simulation apps that exist, where beginning network techs can enter routing commands without any adverse effect on an actual network. 

Thanks,
David C.

---

### Post by adult swim on 2009-04-24
im not aware of anything that does what you want but ive never really looked.  if you boot a live cd you can run about any command you want to and its not going to mess anything up.  just make sure to not mount any of your hard drives partitions and get to bashing

---

### Post by aaronp on 2009-04-24
David,

I've never heard of such a thing but it's a great idea actually. Especially given the fact that it appears most new users main reason for avoiding or disliking Ubuntu (or Linux in general) is having to use the cli.

Maybe something we can look to develop if it doesn't already exist??

---

### Post by wfp on 2009-04-24
You can try here first to learn some basic commands > [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Working with the terminal is pretty easy once you lean some of the basic commands good luck.

---

### Post by David C. on 2009-04-24
WFP - I've read through that and though very useful, especially the file & directory commands, I am somewhat hesitant to enter some of the advanced commands that I've come across and am not familiar with, and have no idea what they actually do, other than a description. I don't want to inadvertly freeze up my system because of a "noob" mistake. Personally, I like to see the function operate. For me, it solidifies the learning process. 

If such an app exists, it would or should alleviate potential user caused disasters and users could enter known (and unknown errors) into it, watch what happens and not worry about screwing up their system (or someone else's).

Aaron - I wouldn't mind getting involved with something like this to cut my teeth or the other montage--baptism by fire. However, when it comes to programming I am still a beginner. I've messed around w/C++ a bit, but have refocused my efforts on learning Python first, of which I'm really enjoying. I find it less stressful and frustrating than when I attempted to learn Java as a first programming language. 

A software app of this nature would probably require a good bit of C coding (perhaps C++ if it's possible) to simulate the Linux OS properly, since (as I understand) it is written in C and (I think) some assembly language.

---

### Post by jowilkin on 2009-04-24
Well there's cygwin on Windows which does a great job of reproducing much of the linux environment. [http://www.cygwin.com/](http://www.cygwin.com/)

Or you could run Virtual Box and install a copy of Ubuntu in it.  [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox).  Then if you screw something up just revert to an old snapshot or reinstall the virtual machine, neither of which will effect your regular OS.

---

### Post by David C. on 2009-04-24
The Virtual Box seems plausible. I'll look into it. Thanks.

---

### Post by nothingspecial on 2009-04-24
Or you could do what I did. Find an old busted box to use as your experimenting machine.

Mine`s a laptop with a  broken display. It was going to be thrown away but i`ve hooked it up to an external monitor and it works fine.

I break it on purpose to see if I can fix it. Best way to learn.

---

### Post by David C. on 2009-04-24
> **nothingspecial said:**
> Or you could do what I did. Find an old busted box to use as your experimenting machine.

Mine`s a laptop with a  broken display. It was going to be thrown away but i`ve hooked it up to an external monitor and it works fine.

I break it on purpose to see if I can fix it. Best way to learn.

That's another plausible idea. Thanks.

---

### Post by aaronp on 2009-04-25
> **David C. said:**
> That's another plausible idea. Thanks.

I think installing on a Virtualbox is a good idea. That is where I try out new releases before I decide if I will upgrade my real system. It's a little bit of overhead for someone just wanting to try out terminal commands but it's pretty safe and the overhead is minimal given the fast and easy install process for Ubuntu.

However, I did just have a thought and maybe a chroot might be an option. I'm not 100% on chroot and the impacts on other parts of the file system so if anyone is an expert in this area maybe you could advise?

---

### Post by marshag63 on 2009-04-25
You could also try an INX live CD or virtual box.  I'm learning tons of stuff with INX - its amazing what you can do through a console.

Its a totally live CD that is console only with tutorials on the basics with lots of stuff to explore - I highly recommend it!!!

Check out the videos too.

[http://inx.maincontent.net/](http://inx.maincontent.net/)

MarshaG63

---

### Post by dcstar on 2009-04-25
> **David C. said:**
> Didn't know exactly where to post this and didn't find anything regarding this in the forum.

Is anyone aware of an existing software app that simulates the CLi? Something that a beginner to Linux can install and utilize to learn Linux commands, what they do, how they function, etc.


You simply create a standard "user" account and let 'em rip. Because they do not have any administrator privileges they cannot do any harm whatsoever to the underlying system and if they break their own environment, you simply delete the user and create another one.

---

### Post by lisati on 2009-04-25
I gather from the comments that we're talking about something other than the normal "terminal" on the Applications->Accessories menu, which, in a way, is a terminal "simulator". 

I'd go with the suggestions of using a spare box, where it doesn't matter so much if you bust something, and possibly using a "day to day" account which doesn't have administrator privileges.

---

### Post by David C. on 2009-04-28
Thanks for all the suggestions. They're all great! Now, to figure out which one to implement. Thanks again.

---

### Post by mb_webguy on 2009-04-28
Of those suggested, I think the simplest would be simply to create a new user, and use it as your sandbox account.  If the account doesn't have admin privileges, it won't be able to affect anything outside of its home directory.  And if something there gets fubar'ed, all you have to do is scrap it and start over.

The other options suggested seem to me to be overkill if all you want is to learn to use the terminal without worry of breaking your system.

---

### Post by Anzan on 2009-05-04
I recommend Inx as well.

"Some Info...
Briefly, INX is a Live CD currently based on Ubuntu 8.04
It has no GNOME, KDE, XFCE... or any other desktop or window manager for that matter.

It is console-only - the idea is to give you a tool to learn more about the command line, while having some fun. You might be surprised how much can be done with such a system.

So what is this "X" thing, anyway?"
To put it simply and somewhat inaccurately, "X" is the graphical system that underpins "Desktop" environments and window managers. INX is not X because it deliberately does not use this system. The idea is to learn about the underlying commands that make GNU/Linux systems do what they do... This knowledge is helpful in any GNU/Linux system, but INX concentrates on the "Debian Way" of doing things, which is also used by Ubuntu, for example."

[http://inx.maincontent.net/info/info.html]("http://inx.maincontent.net/info/info.html")

---

