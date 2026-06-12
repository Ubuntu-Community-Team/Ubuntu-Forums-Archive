---
title: "Malicious Commands, maybe an opportunity?"
date: 2009-09-08
forum: Forum Feedback &amp; Help
---

### Post by nuclear216 on 2009-09-08
I've just read the Malicious commands sticky thread and realized something.

some malicious people could not just erase the user data messing with disks and file or cause system hang up, they could actually make user download any files from anywhere and execute it and make the user computer a zombie, just like a worm.

They could also write a series of good simple howtos which really do the stuff they're supposed to but also something else.

On this forum there's moderation and lot of good information, as the mentioned sticky thread, but I am thinking about users who don't read english well that search for support forums in their own language.

I am Italian and altough I do read english and come here for ubuntu support if I search google for support in my language many blogs pops up and who knows if everyone is doing due diligence.
An attacker could also break into those server and change existing post adding some lines, and who would notice than? 
I am no way a software expert so I only figure it out that forum post shold be in a database somewhere and if someone get access to it he can change them, correct me if I am wrong here.

A way around that, and maybe a good add to the ubuntu linux, could be to make it use an apps for terminal command input which stays on top of the terminal so that it checks for malicious or risky commands being executed.
It could also be a mean to provide a more user friendly interface to the terminal, as it is a really powerfull linux tool, it could also provide something like a command builder or any other good stuff.

I am no programmer or have real time to share into actually doing this but still, I'd like to know your opinion.

---

### Post by nikhilbhardwaj on 2009-09-08
it may not be possible to teach the terminal which commands are dangerous
rm and dd are very very useful 
but they can be misused

on this forum its highly unlikely that you'll find something like that
i tell you this from my experience

---

### Post by NoaHall on 2009-09-08
To use sudo commands(the more powerful ones), you must first be allowed to elevate your status to root. It is warned at the beginning that anyone who does not know what they are doing, they should not do ANYTHING using sudo. The same applies for su. If a user does so, then it is the user's fault for not first reading the first message ever displayed in the Ubuntu Terminal, and for not reading the documentation. So many problems could be solved if they just read about their problem. Also, as a standard here, people do not tell users to use rm in the terminal, where they are more likely to cause damage, but instead through using the GUI.

---

### Post by QIII on 2009-09-08
When I post something to be run in the terminal, I often tell the original poster to wait until someone concurs -- except for the very obvious (to us) commands.

It might not hurt to google whatever commands you find here and see if others concur.  It would be hard for someone with malicious intent to find everything on the internet, hack dozens of servers...

That said, this forum is well policed and I think you can be assured that code has not been maliciously changed.

However, people do unintentionally post commands that are incorrect or have errors, so it doesn't hurt to wait until two or three people chime in and watch the discussion.

---

### Post by QIII on 2009-09-08
> **NoaHall said:**
> To use sudo commands(the more powerful ones), you must first log in as root.

Not exactly.

When you have logged in normally, sudo temporarily elevates your privileges as if you were root.

---

### Post by NoaHall on 2009-09-08
Yes, I know, sorry, I wrote it wrong.. I get confused xD

---

### Post by afroman10496 on 2009-09-08
OMG ```
yes
``` is a wierd command. It doesn't do anything to your syetem, but...
```
y
y
y
y
y
y
y
y
y
y
y
```yeah.

---

### Post by Joeb454 on 2009-09-08
If you wanted to run something that asked for a lot of input, and you already knew you wanted to answer 'y' then you can use pipes & yes to solve the problem :)

---

### Post by afroman10496 on 2009-09-08
> **Joeb454 said:**
> If you wanted to run something that asked for a lot of input, and you already knew you wanted to answer 'y' then you can use pipes & yes to solve the problem :)
oooooooooooooooooooooooooooooooooooooooooooh... yes.:P

---

### Post by winotree on 2009-09-08
I have to believe that with the tens of thousands of users on this forum -- that if someone attempted to do as OP considers, it would surely be caught soon enough by someone, don't you think?

---

### Post by raymondh on 2009-09-08
> **winotree said:**
> I have to believe that with the tens of thousands of users on this forum -- that if someone attempted to do as OP considers, it would surely be caught soon enough by someone, don't you think?

Hopefully ... but the sub-forums go so fast that catching a malicious command could be difficult.

---

### Post by Chronon on 2009-09-08
True, but you can always ask for someone to explain what the commands do and for a second opinion.

---

### Post by cariboo on 2009-09-08
I have to say our members are some of the best when it comes to reporting posts with malicious commands, it usually only takes a couple of minutes from  the time such a post is created and it is reported.

---

### Post by raymondh on 2009-09-08
> **Chronon said:**
> True, but you can always ask for someone to explain what the commands do and for a second opinion.

Also true ... but how often does a new user ask for clarifications or a second opinion?

I think consistent, continuing education  about malicious commands is important.  

Also, a script that could catch/warn about malicious commands (wishful thinking, perhaps :) .

---

### Post by Bodsda on 2009-09-10
> **raymondhenson said:**
> Also true ... but how often does a new user ask for clarifications or a second opinion?

I think consistent, continuing education  about malicious commands is important.  

Also, a script that could catch/warn about malicious commands (wishful thinking, perhaps :) .

A script or any major checking done to catch malicious commands is almost impossible. Commands are not malicious by themselves, it is the manner in which they are used. I think there is already more then enough prevention, for example if you try using rm to delete your root you recieve this message
```

rm: cannot remove root directory `/'

```, it can't be done on later versions of ubuntu without deliberately using the --no-preserve-root argument.
If you go any further with restrictions of the rm command then the usefulness of the command gets drastically reduced. For example there could be perfectly valid reasons for wanting to rm your ~/.

If a user does not know what a command does then s/he should not run it.
You cant protect everyone from themselves.

---

### Post by nuclear216 on 2009-09-10
Let me clarify that I completely agree that this very forum here is well organized and both user and admin do their due diligence in regards to malicious commands.
I think the real threat lies in the many more other forum which are on the internet.

> **Bodsda said:**
> A script or any major checking done to catch malicious commands is almost impossible.

Well that's exactly my point, it's not feasible nor wise to try to catch malicious command sent to the terminal because who knows what the user want to do, even I once wanted to delete all files from /, but if you have an app which is intended for basic user to use to input command to the terminal, like the one found in howtos and forums, than you may want to catch malicious command and have the mean to do so, the apps would just be something around bash which checks for series of input.

Moreover if including a GUI command builder, it could be an interface for basic user to handy terminal commands, like for batch renaming or generating logs from your system.

---

### Post by SoftwareExplorer on 2009-09-12
> **winotree said:**
> I have to believe that with the tens of thousands of users on this forum -- that if someone attempted to do as OP considers, it would surely be caught soon enough by someone, don't you think?

I'll say this--I,ve had people spam a thread I was subscribed to and I'll go to the thread to check it out only ten minutes after it was posted, and it is already completely gone.

---

