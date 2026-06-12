---
title: "trusted repositories"
date: 2009-03-06
forum: General Help
---

### Post by grubster on 2009-03-06
how do i know if my repositories are trustworthy as i had to download ipblock and i needed to use another repository

---

### Post by martrn on 2009-03-06
You never know weather a repository is truly trustworthy or not.

The more files it maintains and the more people who are on a forum, that you can reach if there are any problems the more trustworthy the repository is.  You have to decide yourself if the repository is truly trustworthy or not.

External repositories are always good, for specialist pieces of software or for people who have common interests, or for packages not available in ubuntu, but you can never be sure.

---

### Post by grubster on 2009-03-06
Can i check if i am using a malicious repository or is there no such thing?

---

### Post by entr3p on 2009-03-06
> **grubster said:**
> how do i know if my repositories are trustworthy as i had to download ipblock and i needed to use another repository

Try it out. If you get the program you needed then your all good. It's not like you can get a virus ;).

---

### Post by entr3p on 2009-03-06
> **grubster said:**
> Can i check if i am using a malicious repository or is there no such thing?

One: Stop posting multiple threads.
Two: You can't get a virus. So no there's no such thing. (yet)

---

### Post by Slim Odds on 2009-03-06
> **entr3p said:**
> One: Stop posting multiple threads.
Two: You can't get a virus. So no there's no such thing. (yet)

That doesn't mean that a repository can't have bad stuff that you can install (don't forget that you use "sudo" to apt-get install stuff).

So, YES, there can be such a thing......

---

### Post by entr3p on 2009-03-06
> **Slim Odds said:**
> That doesn't mean that a repository can't have bad stuff that you can install (don't forget that you use "sudo" to apt-get install stuff).

So, YES, there can be such a thing......

There are no Ubuntu viruses in the wild **yet**. And I said there's none yet. From any reports there are NO wild viruses. It's possible that someone made one but it's either on their computer for testing purposes or they haven't let it out in the wild. Please don't try to make the new user more paranoid.

---

### Post by jpeddicord on 2009-03-06
Threads merged; please do not make duplicate threads for the same issue.

---

### Post by Slim Odds on 2009-03-06
> **entr3p said:**
> Try it out. If you get the program you needed then your all good. It's not like you can get a virus ;).

Dude, another know nothing post..... 

When you install from a repository, you use "sudo apt-get install". That means that you damn well better trust what you're getting. You can **definitely** get a "virus" when you install as the **SUPER USER!!!**

---

### Post by Skripka on 2009-03-06
> **Slim Odds said:**
> Dude, another know nothing post..... 

When you install from a repository, you use "sudo apt-get install". That means that you damn well better trust what you're getting. You can **definitely** get a "virus" when you install as the **SUPER USER!!!**

And to repeat, do not encourage the paranoid OP user to be more paranoid.

Yes there *can* be such a thing but it does not exist-as of yet.

---

### Post by dcstar on 2009-03-06
> **grubster said:**
> Can i check if i am using a malicious repository or is there no such thing?

Simple solution: Don't add repositories that you don't trust to your system.

Any non-official repository may or may not contain contain software that can do damage to your system (whether deliberate or not), it is up to **you** to do enough research to decide if you want to give your system access to what may be in these repositories.

Having said that, I haven't heard of any that have been deemed "malicious", and I'd suspect these forums would be full of posts if such a thing existed.

---

### Post by entr3p on 2009-03-06
> **Slim Odds said:**
> Dude, another know nothing post..... 

When you install from a repository, you use "sudo apt-get install". That means that you damn well better trust what you're getting. You can **definitely** get a "virus" when you install as the **SUPER USER!!!**

It's funny because the only one writing "know nothing" posts are you. Please before posting any further, point me out to anyone who has gotten a virus in Ubuntu by adding a "malicious" repository. Also when you use the command "sudo apt-get install" it only installs the program as super user for that moment, the program itself wont run as super user when you use it.

---

### Post by Slim Odds on 2009-03-06
> **entr3p said:**
> There are no Ubuntu viruses in the wild **yet**. And I said there's none yet. From any reports there are NO wild viruses. It's possible that someone made one but it's either on their computer for testing purposes or they haven't let it out in the wild. Please don't try to make the new user more paranoid.

You have **NO IDEA** what the heck you are talking about.

If you install an application with "sudo", the door is **WIDE OPEN.** So cut the crap about "not in the wild yet". 

You **definitely** must **TRUST** the repositories that you use.

---

### Post by Slim Odds on 2009-03-06
> **entr3p said:**
> It's funny because the only one writing "know nothing" posts are you. Please before posting any further point, me out to anyone who has gotten a virus in Ubuntu. Also when you use the command "sudo apt-get install" it only installs the program, the program itself doesn't run as super user.


Dude, you really have not a clue.

If you install via "sudo apt-get install", the installed application can do **whatever it wants**.This is how services, etc. are installed.

Go do your homework.

---

### Post by entr3p on 2009-03-06
> **Slim Odds said:**
> You have **NO IDEA** what the heck you are talking about.

If you install an application with "sudo", the door is **WIDE OPEN.** So cut the crap about "not in the wild yet". 

You **definitely** must **TRUST** the repositories that you use.

I'm sorry but you have shown no proof at all. As I stated please point me out to someone who haas gotten effected by this door which is supposedly so wide open. Do you actually know what the command "sudo apt-get install" does? I'm also using this command as an example as you were the one who brought the command up. Sudo runs root only to install the program. Basically it created the folders and binaries and that's it. It doesn't **run** the program at all. So any "malicious" code in the program doesn't run at root at all when you install it.

---

### Post by Slim Odds on 2009-03-06
> **Skripka said:**
> Yes there *can* be such a thing but it does not exist-as of yet.

How do you know that?   (You don't)

---

### Post by Slim Odds on 2009-03-06
> **entr3p said:**
> I'm sorry but you have shown no proof at all. As I stated please point me out to someone who haas gotten effected by this door which is supposedly so wide open. Do you actually know what the command "sudo apt-get install" does? I'm also using this command as an example as you were the one who brought the command up. Sudo runs root only to install the program. Basically it created the folders and binaries and that's it. It doesn't **run** the program at all. So any "malicious" code in the program doesn't run when you install it.

I'll tell you what. I will create a "special" repository just for you. It's just too simple.

---

### Post by Slim Odds on 2009-03-06
I'll try to put the simple logic together for you.

1) You install stuff with sudo
2) sudo means that it runs as super user

What else do you need to know?

---

### Post by entr3p on 2009-03-06
> **Slim Odds said:**
> I'll tell you what. I will create a "special" repository just for you. It's just too simple.

Haha. Alright :). Do that and I'll test it out with screenshots so you can look like more of a dumbass. How will this "special" repository affect me? Install some files that I will have to delete because it's wasting space? Will I get infected with a virus? **No.** Will I get my information stolen? **No.** Please. I have used many operation systems such as FreeBSD, Gentoo and Slakware and I also run my own ftp and firewall server in FreeBSD so I have enough experience to know more then some newbie who thinks their 1337 elite because their running Ubuntu.

> **Slim Odds said:**
> I'll try to put the simple logic together for you.

1) You install stuff with sudo
2) sudo means that it runs as super user

What else do you need to know?

I have already disproved this. You even proved yourself wrong. Read what you just typed **slowly**. You **install** "stuff"(binary files) with sudo. Are you running the program? No, your basically copying files. You think that when you install a program it's automatically being run simultaneously. That's incorrect ;).

---

### Post by mb_webguy on 2009-03-06
> **entr3p said:**
> Try it out. If you get the program you needed then your all good. It's not like you can get a virus ;).

Eh...  I'm not sure this cavalier attitude is the best approach.  True, Linux is essentially virus-proof, but that doesn't mean it can't run malicious software.  If someone has slipped in some code that deletes all of your config files, then if you run that code, your config files will be deleted.  This risk is magnified significantly if you run the software as root.  So I think it's healthy to be a bit skeptical about running software from unverified sources.

That said, in my experience, the Linux community as a whole is fairly benign.  Reputation is key when it comes to open-source software, and the community is communicative enough that anyone releasing malicious code is quickly identified and shunned.  If someone recommends a software source on this forum, you can almost certainly trust it.  And if you ever have any doubt at all about the veracity of a specific source, just ask here.  Chances are that someone will know about and be able to tell you whether it's ok.

---

### Post by Slim Odds on 2009-03-06
> **entr3p said:**
> Haha. Alright :). Do that and I'll test it out with screenshots so you can look like more of a dumbass. How will this "special" repository affect me? Install some files that I will have to delete because it's wasting space? Will I get infected with a virus? **No.** Will I get my information stolen? **No.** Please. I have used many operation systems such as FreeBSD, Gentoo and Slakware and I also run my own ftp and firewall server in FreeBSD so I have enough experience to know more then some newbie who thinks their 1337 elite because their running Ubuntu.



I have already disproved this. You even proved yourself wrong. Read what you just typed **slowly**. You **install** "stuff"(binary files) with sudo. Are you running the program? No, your basically copying files. You think that when you install a program it's automatically being run simultaneously. That's incorrect ;).

Not meaning to offend, but you are the most clueless person that I've ever seen post here.

How you think that new kernels are installed?

I could create a repository where every single thing that you install deletes all of the kernels on your system.

Go type "man sudo" on your system and do some reading.

---

### Post by jpeddicord on 2009-03-06
I can see this thread is not going anywhere fast and is quickly turning into a flamewar, so I'm going to close it. My sincerest apologies to the original poster.

---

