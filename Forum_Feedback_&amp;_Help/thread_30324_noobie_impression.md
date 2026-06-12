---
title: "noobie impression"
date: 2005-04-28
forum: Forum Feedback &amp; Help
---

### Post by Gowator on 2005-04-28
I have to say I find the forums confusing...  
I think less categories and even no split hoary/warty would be simpler?  

I fid it hard to know where to post and where to look for advice..Im sure as I stick around ill get to know it but I think it might put a few people off ...

OK lets be honest, it is putting people off because they are asking on other forums which are dedicated to other distro's!  

I mod on the mandrakeusers forum (for my sins) although I no longer have a installed mandrake and I visit gento often as I have one gentoo server and I see a lot of Ubuntu questions which Im sure would be better off here!  

I feel if it was less intimidating then they might have stuck about!  

just me 2c  ...  Love the distro and Im sure Ill get the site worked out since Ill stick at it!

---

### Post by 23meg on 2005-04-28
i don't think that the reason people ask Ubuntu questions in other forums is that they don't know where to post here; mostly, when they can't get a satisfactory solution to their problems (which is a rare case!), they tend to ask around in other places as well, and that's natural.

---

### Post by Gowator on 2005-04-28
maybee...
However I wonder where the heck to ask my upgrading hoary->warty amd64?  
under hoary-or warty?  

but lets see what any noobs think?  

Its hard to rebecome a noob once you know the site!

---

### Post by ubuntu-geek on 2005-04-28
[QUOTE=Gowator]maybee...
However I wonder where the heck to ask my upgrading hoary->warty amd64?  
under hoary-or warty?  

but lets see what any noobs think?  

Its hard to rebecome a noob once you know the site![/QUOTE]
 If you are upgrading to Hoary then the post would go in the Hoary section. There are many posts relating to why we are broke up into different distro sections. If we combined them together it would be seriously confusing since there are major differences between Warty and Hoary.

---

### Post by DJ_Max on 2005-04-28
Maybe it's just me, but I don't see the layout confusing at all. If you have Hoary, use that section, Warty has it's on section, if you develop, go to the Development section, the other support is open for about anyone.

---

### Post by 23meg on 2005-04-28
right, it's all very clearly laid out.

---

### Post by Gowator on 2005-04-28
OK, just an observation.... strange though someone just said the same thing elsewhere ... (without prompting)  but then they are used to a different layout too.  


Lets see If I get used to it :D  but perhaps its just because its easier to ask the question in a familiar place even if its not for Ubuntu and also perhaps because my experience is enough to not need too many questions...  ??

Love the distro though (with the exception of the silly sudo thing but hey it wouldn't be a different distro without some foibles :D )

---

### Post by TravisNewman on 2005-04-28
oh, sudo is hardly silly-- many many advantages-- and when you get used to it you'll wonder how you ever lived without ;)

But anyway, if we combined the warty/hoary sections, unless we did more subtopic splitting, you could post a question for help and in an hour it would have moved past the first page-- and most people don't read past the first page. So you'd end up with nobody getting the help they need.

---

### Post by Gowator on 2005-04-29
nope sudo is silly the way its implemented....

root is root and a user is a user and forcing someone to type the root password has a reason... at least its what the programmers expect.  

Nothing wrong with sudo'ing just you should need the root password not your own else you mightest well just run as root!

---

### Post by Professor X on 2005-04-29
Since it seems that ubuntu is attracting new users to linux, I would think that sudo is a good solution because it requires use of only one password.  It's easy enough to set a root password (sudo passwd) for those that want it.

---

### Post by Stormy Eyes on 2005-04-29
[QUOTE=Gowator]root is root and a user is a user and forcing someone to type the root password has a reason... at least its what the programmers expect.  [/QUOTE]

Being a programmer, I expect sudo to ask for *my* password, not root's. One of the purposes of sudo is to allow root to allow certain users to perform certain tasks with elevated privileges. If sudo requires the root password, then users have no reason to use sudo; they can just use su to *become* root and take control of the system.

I'd suggest reading [Sudo in a nutshell](http://www.courtesan.com/sudo/intro.html) before talking about how sudo should work.

---

### Post by Gowator on 2005-05-02
[QUOTE=Professor X]Since it seems that ubuntu is attracting new users to linux, I would think that sudo is a good solution because it requires use of only one password.  It's easy enough to set a root password (sudo passwd) for those that want it.[/QUOTE]
Yep my problem is its easy enough for anyone to set it!  


incidentally its not sudo its having passwd in the list that is bizarre!  Any user can set the root password and I find that weird!

---

### Post by Stormy Eyes on 2005-05-02
[QUOTE=Gowator]Yep my problem is its easy enough for anyone to set it!  


incidentally its not sudo its having passwd in the list that is bizarre!  Any user can set the root password and I find that weird![/QUOTE]

*shrugs* Then why not just set the root password to "ahtkerhkjh4539434)()(&#" or something similar and forget about it? That's what I do with all of my boxen.

---

### Post by Gowator on 2005-05-03
because any user can set it to anything else.  

As I said sudo is not the problem its the use of it (for passwd) which is the problem ...  I need to look into the kdesu stuff to see if I can reverse it out but having any user on a network (or any 'hacker') able to change the root passwd is not secure.

---

### Post by Stormy Eyes on 2005-05-03
[QUOTE=Gowator]because any user can set it to anything else.[/QUOTE]

Only if he's granted permission to use sudo in /etc/sudoers. If you don't trust user foo to use sudo, then lock him out.

---

### Post by Gowator on 2005-05-03
This is all well and good for veterans.  The first thing I did was activate root and I didn't need instructions on how to do it...

However its dangerous for noobies since they are presumably browsing and using p2p with their user account...   so if this is comprimised and they don't even know about root then a maliceous person could set their root password.  

They don't even realise root exists, let alone that  its been subverted!
security through ignorance is not a real security..  

> ahtkerhkjh4539434)()(&#" 

jeez stormy how dod you crack my root password?  I thought I was safe with that one  :???:

---

### Post by Stormy Eyes on 2005-05-03
> **Gowator]This is all well and good for veterans.  The first thing I did was activate root and I didn't need instructions on how to do it...[/quote]

Good for you. When I set up Ubuntu for people, I make sure to set a root password, tell people how to use sudo, and warn them that they should not log in as root unless they absolutely *must* do so. I take care of my users.

But if you don't have a 'guru', it's your responsibility to take care of yourself. That means RTFM when the situation warrants it.

[QUOTE=Gowator]However its dangerous for noobies since they are presumably browsing and using p2p with their user account...   so if this is comprimised and they don't even know about root then a maliceous person could set their root password.[/quote]

As far as I'm concerned, it's their fault for not educating themselves. I'm a bit old-fashioned said:**
> They don't even realise root exists, let alone that  its been subverted! security through ignorance is not a real security...

Ignorance is not something to which the knowledgable should cater.

[QUOTE=Gowator]jeez stormy how dod you crack my root password?  I thought I was safe with that one  :???:[/QUOTE]

I bribed your cat.

---

### Post by Gowator on 2005-05-03
> **Stormy Eyes]Good for you. When I set up Ubuntu for people, I make sure to set a root password, tell people how to use sudo, and warn them that they should not log in as root unless they absolutely *must* do so. I take care of my users.

But if you don't have a 'guru', it's your responsibility to take care of yourself. That means RTFM when the situation warrants it.

[/QUOTE]  I agree but telling the noobies where the manual is and why is a good start.  

> 
As far as I'm concerned, it's their fault for not educating themselves. I'm a bit old-fashioned said:**
> 
Again I agree but then this is why users should be warned and the default isn't a good idea.  Hence you install and tell the users not to use root and activate it (and I hope take passwd out of sudo'ers or at least not leave ALL:ALL ...)  

If you put all:all then its close to using root as a nornal account...  
[QUOTE]
Ignorance is not something to which the knowledgable should cater.

ciaranm would agree!  
[QUOTE]
I bribed your cat.

Bastard cat, Its not being fed tonight and from now on its getting its own account not getting my password or root!

---

### Post by Stormy Eyes on 2005-05-04
[QUOTE=Gowator]I agree but telling the noobies where the manual is and why is a good start.[/quote]

Naturally. When answering questions with RTFM, I provide a link to the FM in question. I also point them to [http://en.tldp.org](http://en.tldp.org).

[QUOTE=Gowator]Again I agree but then this is why users should be warned and the default isn't a good idea.  Hence you install and tell the users not to use root and activate it (and I hope take passwd out of sudo'ers or at least not leave ALL:ALL ...)  

If you put all:all then its close to using root as a nornal account...[/quote]

Show me a sysadmin who runs sudo without at least running visudo to lock down sudo, and I'll show you a pwnage waiting to happen. I lock sudo down on machines I maintain.

[QUOTE=Gowator]Bastard cat, Its not being fed tonight and from now on its getting its own account not getting my password or root![/QUOTE]

Be kind to him. He does have a drug problem. He needs Catnip Anonymous.

---

