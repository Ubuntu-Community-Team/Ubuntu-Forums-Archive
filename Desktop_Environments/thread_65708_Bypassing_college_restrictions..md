---
title: "Bypassing college restrictions."
date: 2005-09-14
forum: Desktop Environments
---

### Post by Hig on 2005-09-14
I recently started a college course but their net access is restricted through the always lovely websense. I know of a number of workarounds, one being VNC into a home server, the other is a proxy. However I'm not sure if the VNC server in ubuntu is compatible with java-vnc.

What I want to know is can someone point me in the direction of either a method for setting up a web browsing proxy, or configuring the ubuntu VNC-server to support web based java VNC. Slow, I know, but these things must be done.

I'm open to other suggestions but I do need unrestricted web-access to get access to some college resources that are somewhat, unsavoury, to administrative folks.

---

### Post by Luke Redpath on 2005-09-14
I'm not sure if this is the place to ask how to bypass your college's rules and regulations. If they choose to filter out certain content or prevent access to certain things, that is their right - it is their network. If you need to access something for a legitimate reason, perhaps you could ask the IT department?

---

### Post by Hig on 2005-09-15
I'm attempting to access my Gmail account so I can use my remotely stored files. I've been a network administrator for years and I know how stubborn we are. 

I'm not asking for a moral debate, I could have rephrased and just asked for guides without context but in order to achieve the most positive feedback I've found that honesty is the best policy; but there's always someone who causes controversy.

---

### Post by wmcbrine on 2005-09-15
The whole idea of VNC is to be an open standard, so all VNC servers and clients are compatible; some offer extensions to the basic protocol, but they should fall back if the other side doesn't support them. So, I guess I don't understand your question.

I've been in a similar position, though. I don't remember all the details of what I did, but I didn't use web-based VNC; I just redirected some ports, so that the regular VNC connected on port 80 (or was it 21?). But I actually used a reverse connection, as well (initiating the connection from the server), because it was the system behind the firewall that I wanted to access from home.

Another thing to consider is SSH. You can do wonders with this, redirecting ports from both sides, all through a secure tunnel. It's almost like a VPN. Or you could set up an actual VPN, for that matter. :) But the advantage of SSH is that it can work in userspace, even unprivileged. Again, if necessary, you can set up your SSH server on a nonstandard port like 80, although many firewalls will already pass the default port 22. SSH has good support for X forwarding, too.

---

### Post by Hig on 2005-09-15
Doesn't SSH have to be installed on a Windows machine? I don't think we get privelages  to install.

---

### Post by Yagisan on 2005-09-15
[QUOTE=Hig]Doesn't SSH have to be installed on a Windows machine? I don't think we get privelages  to install.[/QUOTE] Look into putty for Windows [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/) that may be helpful for you. Alternatively, use sneakernet to bring your files in.

---

### Post by Luke Redpath on 2005-09-15
[QUOTE=Hig]I'm attempting to access my Gmail account so I can use my remotely stored files. I've been a network administrator for years and I know how stubborn we are. 

I'm not asking for a moral debate, I could have rephrased and just asked for guides without context but in order to achieve the most positive feedback I've found that honesty is the best policy; but there's always someone who causes controversy.[/QUOTE]

I'm not trying to be controversial, I just don't think this an appropriate place to ask how to break your college network restrictions. And if you have been a network admin "for years", you should know better.  :roll:

---

### Post by Hig on 2005-09-15
What I know from being a network administrator is that the net admins don't make the rules. The bosses do, and they don't always understand that by stopping some bad things they can kill a lot of good things.

In my college we can't use any email at all. We also have no local storage on the systems and are therefore limited to floppy discs. If I could access my Gmail drive my next 5 years in college would not be marred by the hundereds of megs of data lost because of garbled and broken floppies.

As I said, I could have just asked for a guide on proxys or VNC, but I thought that since other people here have gone through education they would empathise and see why this is a problem.

You should consider your point a bit more before posting inflammatory comments. Net admins are just GUIs for the bosses. A way of making things happen. We don't get much say in what rules are implemented, ridiculious as they may be.

---

### Post by wmcbrine on 2005-09-15
[QUOTE=Luke Redpath]I'm not trying to be controversial, I just don't think this an appropriate place to ask how to break your college network restrictions.[/QUOTE]Well, if we're voting (and I guess we must be, since you're not a moderator), I'm all in favor of it. :)

---

### Post by Fiyawerx on 2005-09-15
[QUOTE=Hig]What I know from being a network administrator is that the net admins don't make the rules. The bosses do, and they don't always understand that by stopping some bad things they can kill a lot of good things.

In my college we can't use any email at all. We also have no local storage on the systems and are therefore limited to floppy discs. If I could access my Gmail drive my next 5 years in college would not be marred by the hundereds of megs of data lost because of garbled and broken floppies.

As I said, I could have just asked for a guide on proxys or VNC, but I thought that since other people here have gone through education they would empathise and see why this is a problem.

You should consider your point a bit more before posting inflammatory comments. Net admins are just GUIs for the bosses. A way of making things happen. We don't get much say in what rules are implemented, ridiculious as they may be.[/QUOTE]

Just out of curiosity, where do you go to college? You don't even get a college email? Do the pc's you use at least have USB ports?  Could always check into a cheap flash drive, 20$ and you could save yourself on the "hundreds of megs of data lost" due to being forced to use floppies. You sound like you havn't even tried talking to the network ops/department. Just becase the admins don't make the rules, chances are they have sway with the people who do. Even large corporations usually have exceptions to blocked sites if you can prove a great enough need.  The whole scheme of how "locked down" this college seems just rings a bit odd, but maybe it's just me.

---

### Post by sameat on 2005-09-15
As a network admin, I feel comfortable adding my two cents here.  Hig is right about the way restrictions are sometimes applied...paranoid managers take extreme steps that become major annoyances for no reason other than to excercise control (and/or cover their butts).  Admins then get the pleasure of trying to make a kludge of policies and rules work while still allowing users to get some meaningful use out of the machines/network.

The use of the term "unsavoury" is a little, well, unsavoury.  I really don't think there is anything inherently unsavoury about gmail, but it certainly could be abused.

I once tested the strength of our restrictions (at work) by running ssh on port 80 on a test box in my home and tunneling vnc.  It was actually pretty trivial to forward x apps to my windows desktop in the office.

Caveat: I did this with the knowledge and support of my boss (IT Manager), and I demonstrated the results for her.  She was more than a little shocked at the ease with witch our controls were circumvented.

There are probably a dozen good ways to achieve what you want, and some of them may even be by the book if you asked.  It sounds like there might be a control freak in your schools' IT department, so don't be shocked if you get busted hard (and know the policy...you could end up in legal trouble).

---

### Post by Hig on 2005-09-17
With regards to USB ports, yes, some of the PCs have USB support, but a number of them in a specific lab do not.

We do get college mail, but only with 20Mb capacity storage. When I did my engineering degree last year my projects were vastly larger than that.

I'm not particularly afraid of the ramifications, I've talked to the I.T. department and they agree that it's overly restrictive but necessary due to the number of people who could abuse and otherwise threaten the integrity of the 400+ PC network. 

What I meant by the Java-VNC thing was that on a windows machine if you install VNC then there is a java section which will allow you to connect in via java over a web-page. From my experimentation that doesn't seem to be the case with the linux flavour of VNC.

I'm also interested in the mechanics of setting up a web surfing proxy, it's one of the few hurdles I've yet to overcome.

---

