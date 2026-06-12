---
title: "Do we really need so much security?"
date: 2009-05-06
forum: General Help
---

### Post by AlecJ on 2009-05-06
I may be a recent convert to the Linux camp (3 years now), and it's been a good move. I've not had this much fun since DOS 6.
 

 But I am sick of SUDO!
 I get it, it's not my file or folder or log in, BUT IT'S MY COMPUTER!
 And if I need to edit xorg.conf or let myth-burn use a temp directory to build a DVD or mount a usb ext3 drive at boot up. I would like too without the red tape of permission denied!
 

 Don't get me wrong, I understand the hierarchy, I just question it's usefulness on a desktop or media PC. Even if the PC is shared, all that most people have to hide is a games or porn collection and you can't do that without logging out! Can't just password a folder like they do on the movies.
 

 Is it really possible for a spotty youth on the other side of the planet to hack into my home network and what would he want if he got there? Can he get my bank details from Firefox?

---

### Post by buzzmandt on 2009-05-06
in a word....YES

It is what it is by default, you can change the way it works if you wish less security.  just search.  

I happen to very much like all the security.

---

### Post by AlecJ on 2009-05-06
> **buzzmandt said:**
> in a word....YES

It is what it is by default, you can change the way it works if you wish less security.  just search.  

I happen to very much like all the security.
How can he get my bank details?

---

### Post by buzzmandt on 2009-05-06
> **AlecJ said:**
> How can he get my bank details?
I actually meant "YES" for the original question, do we really need so much security.

Not yes for the last hypothetical question of the original post.

---

### Post by AlecJ on 2009-05-06
ok, that was a hypothetical question. and not possible (online banking is totally safe!)

---

### Post by _Purple_ on 2009-05-06
Why don't you edit your sudoers file and allow the applications you use frequently to run without password?

---

### Post by hansdown on 2009-05-06
> **AlecJ said:**
> ok, that was a hypothetical question. and not possible (online banking is totally safe!)

I would worry more about the bank's database being compromised than my personal computer.

[http://www.google.ca/search?q=database+thefts&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=database+thefts&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by AlecJ on 2009-05-06
> **_Purple_ said:**
> Why don't you edit your sudoers file and allow the applications you use frequently to run without password?
I could, buts thats a work around, still I question the need for it in the first place. My mythbuntu machine won't burn a DVD without me deleting a hidden authority file, (now scripted too).
I can't backup a system file without using the terminal to start a "root" file manager nautilus or thunar.
This is my question

I love this [http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by AlecJ on 2009-05-06
> **hansdown said:**
> I would worry more about the bank's database being compromised than my personal computer.

[http://www.google.ca/search?q=database+thefts&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=database+thefts&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Now see I was'nt worried before!

---

### Post by theozzlives on 2009-05-06
Programs like LimeWire can bust into a Windows machine, steal bank info, tax returnes, etc. They don't have the security.

---

### Post by lisati on 2009-05-06
What we do with our own machines is our business. When we hook up to any kind of network, it's what we *don't* want happening that's the issue when it comes to security. One of the banks I'm with has, in addition to the regular user-id/password approach, a "captcha" image for us to decode, and the option of being asked a question only I'd know the answer to.

---

### Post by edibanez on 2009-05-07
Linux was built with security in mind and I think if it would lose its security it wouldn't be Linux at all does it??

ot: isn't this feeding the troll????

---

### Post by Promethalus on 2009-05-07
just a hint, but if you like, you can login as root, with gui and everything. But, you`ll have to google to get instructions, for there aren`t threads conserning root login on this forum

---

### Post by lloyd_b on 2009-05-07
> **AlecJ said:**
> I may be a recent convert to the Linux camp (3 years now), and it's been a good move. I've not had this much fun since DOS 6.
 

 But I am sick of SUDO!
 I get it, it's not my file or folder or log in, BUT IT'S MY COMPUTER!
 And if I need to edit xorg.conf or let myth-burn use a temp directory to build a DVD or mount a usb ext3 drive at boot up. I would like too without the red tape of permission denied!
 

 Don't get me wrong, I understand the hierarchy, I just question it's usefulness on a desktop or media PC. Even if the PC is shared, all that most people have to hide is a games or porn collection and you can't do that without logging out! Can't just password a folder like they do on the movies.
 

 Is it really possible for a spotty youth on the other side of the planet to hack into my home network and what would he want if he got there? Can he get my bank details from Firefox?

The thing to remember is that good security is built in *layers*. Linux has excellent resistance to attackers.  But it isn't perfect - there have been, over the years, some attacks that would give a "spotty youth" access to remote machines.  Without restrictions on root access, once they get into the machine, via any mechanism, it's theirs to do with as they please.  Without root access, the damage they could do is much more limited.

It's your machine - compromise it in any fashion that you choose.  Just don't complain if by some chance it winds up as a spam-spewing botnet zombie...

Lloyd B.

---

### Post by AlecJ on 2009-05-07
Granted and understood. 
But my PC is one of billions around the world, why would anybody want anything from a free OS box running open source software?
So really I'm protecting it from vandals and my router have a firewall for that.
My point is:
All this file ownership and rights is getting in the way and seams responsible for most of the problems I get with my applications. Mainly on the media box I have to add.


"spam-spewing botnet zombie..." Superb!

---

### Post by tribaal on 2009-05-07
Again, please feel free to use your own machine as you like :)

I'm pretty sure editing the sudoers file is not a workaround - that's the way it's intended to be used ;)

On the other hand, I deploy GNU/Linux machines (including Ubuntu) on a daily basis for production purposes, and I can assure you the default configuration is what I expect from a security perspective (and so does my employer) :)

File access rights are there for the same reason. They are easy to change and allow you to fine grain control in a very efficient way.

- Trib'

---

### Post by DLG102282 on 2009-05-07
> **theozzlives said:**
> Programs like LimeWire can bust into a Windows machine, steal bank info, tax returnes, etc. They don't have the security.
Thats ony because idiots but that stuff in the same folder as the have shared for Limewire. The could happen in Linux too if they did the same thing. It has nothing to do with what OS you are running it has to do with people being idiots.

---

### Post by overdrank on 2009-05-07
Moved to General and a reminder 
[Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by lloyd_b on 2009-05-07
> **AlecJ said:**
> Granted and understood. 
But my PC is one of billions around the world, why would anybody want anything from a free OS box running open source software?
So really I'm protecting it from vandals and my router have a firewall for that.
My point is:
All this file ownership and rights is getting in the way and seams responsible for most of the problems I get with my applications. Mainly on the media box I have to add.


"spam-spewing botnet zombie..." Superb!

As stated - it's your machine.  It would take only a few minutes to completely eliminate those problems by switching to a root login.  

As noted by "overdrank", we are not allowed to tell you how to do this.  But a quick Google search should provide you the necessary instructions.

But such a configuration will never be a default.  Most botnet zombies are Windows boxes, for two reasons - first, there are a lot of Windows machines out there, and second, because the OS has many known vulnerabilities that make it easy to take over.  If any Linux distro starts shipping with a less secure default configuration, the bad guys will take note of it, and possibly start targeting it as well.

Read up on "[herd immunity]("http://en.wikipedia.org/wiki/Herd_immunity")" - the concept applies to computers as well as living creatures...

Lloyd B.

---

