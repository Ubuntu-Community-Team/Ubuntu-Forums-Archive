---
title: "sudo is crap. i am adding a root user."
date: 2006-08-08
forum: Desktop Environments
---

### Post by fakie_flip on 2006-08-08
Without using any of these commands or ones similar to it, 'sudo -s`, `sudo -i`, `sudo -K`, 'sudo su', and `sudo chown $USER /etc/apt/sources.list`, how can I get this to work? I also do not want to use a text editor or do this by some other way. I wan't to figure out why this is not working.

ubuntu@ubuntu:~$ sudo echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
ubuntu@ubuntu:~$

---

### Post by clparker on 2006-08-08
Wait, what are you trying to do?

---

### Post by someguyouknow on 2006-08-08
Running as root is a very bad idea.....
it is 5x less same as using Windows.....

---

### Post by fakie_flip on 2006-08-08
> **someguyouknow said:**
> Running as root is a very bad idea.....
it is 5x less same as using Windows.....

news flash for you Dude. just about every distro except Ubuntu has a root user, and that's what I will get if these issues with sudo are not solved.

---

### Post by fakie_flip on 2006-08-08
> **clparker said:**
> Wait, what are you trying to do?

append a line of text (repository) to my sources.list without doing it the other ways. i know how to do it the other ways, but what i am trying to figure out is why is this sudo not working properly and how can it be fixed.

---

### Post by someguyouknow on 2006-08-08
i know every distro has a root user.  but running as root is a bad idea.  ask around before you make snappy remarks.
if you are trying to add that repository to your list, just
```
sudo gedit /etc/apt/sources.list
```
and copy and paste it to the list....

(i think thats the editor for Gnome)

---

### Post by fakie_flip on 2006-08-08
> **someguyouknow said:**
> i know every distro has a root user.  but running as root is a bad idea.  ask around before you make snappy remarks.
if you are trying to add that repository to your list, just
```
sudo gedit /etc/apt/sources.list
```
and copy and paste it to the list....

(i think thats the editor for Gnome)

no, i will not run gedit. only newbies depend on gui apps. i am trying to resolve an issue with sudo, not figure out how to add a repository. if you read what i wrote several times before, then you would know that already.

---

### Post by someguyouknow on 2006-08-08
chill son.....

---

### Post by jimmygoon on 2006-08-08
> **fakie_flip said:**
> no, i will not run gedit. only newbies depend on gui apps.

You're doing a pretty good job as coming off very rude and it makes people very much so want to not help you.

Maybe if you came here asking for help as to how to do what you are trying to do... You would get a much better response than the flamebait nonsense that you've posted... be considerate

---

### Post by scotty2hott2k on 2006-08-08
hahaha, only newbies run gedit, lol, bet he's hardcore, bet he runs vim and has religiously memorised all the commands/shortcuts

---

### Post by VirtuAlex on 2006-08-08
> **fakie_flip said:**
> I wan't to figure out why this is not working.
ubuntu@ubuntu:~$ sudo echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
You can use something like
```
echo "deb http://kubuntu.org/packages/amarok-latest dapper main" | sudo tee -a /etc/apt/sources.list
```
If you want to know why this is not working read this [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by fakie_flip on 2006-08-08
I'll be asking this question at linuxquestions.org and my college's linux user group on it's mailing list, so I can get some experts on Linux to help with this problem, or I could just ask an engineer and college professor tomorrow when I go to the linux user group meeting.

---

### Post by fakie_flip on 2006-08-08
> **VirtuAlex said:**
> You can use something like
```
echo "deb http://kubuntu.org/packages/amarok-latest dapper main" | sudo tee -a /etc/apt/sources.list
```
If you want to know why this is not working read this [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

that works good. i fixed the ubuntu community wiki, and now ubuntu users won't have "permission denied" when trying to run the bad sudo command.
[https://help.ubuntu.com/community/Amarok#preview](https://help.ubuntu.com/community/Amarok#preview)

---

### Post by bensexson on 2006-08-08
VirtuAlex gave the only answer you need.  Just use the command provided and look at the link as well.

---

### Post by fakie_flip on 2006-08-08
> **bensexson said:**
> VirtuAlex gave the only answer you need.  Just use the command provided and look at the link as well.

thats alright if you think so. ill still be asking the linux user group for my city why the command doesn't work, and linuxquestions.org.

---

### Post by scxtt on 2006-08-08
the reason it doesn't work is because shell redirection (the >>) doesn't inherit the sudo, which is why piping it through a **sudo tee -a** does work ...

try not to be such a douche-bag next time fakie_flip ... and remember that sudo isn't crap, and you can't blame it for a users shortcomings ...

and something tells me that if you take your current attitude anywhere else, where you seem to think they're superior to this forum - you'll just get made fun of even more ...

---

### Post by fakie_flip on 2006-08-08
> **scxtt said:**
> the reason it doesn't work is because shell redirection (the >>) doesn't inherit the sudo, which is why piping it through a **sudo tee -a** does work ...

try not to be such a douche-bag next time fakie_flip ... and remember that sudo isn't crap, and you can't blame it for a users shortcomings ...

and something tells me that if you take your current attitude anywhere else, where you seem to think they're superior to this forum - you'll just get made fun of even more ...

tell your momma that. ubuntu is starting to get away from real linux by using  sudo and not having a root user account. i can fix this problem by removing sudo and adding a root user, but im thinking about switching to debian etch for a server because it has all the newest software in its repositories, and debian is known to make a great server.

---

### Post by FuturePast on 2006-08-08
The reason your command doesn' work is that ">>" is built-in to bash and is interpreted as your normal user.
The only thing that's run as superuser is the command "echo blah", which obviously doesn't neet root privileges.

---

### Post by someguyouknow on 2006-08-08
> **fakie_flip said:**
> tell your momma that.

[-X  what are you 12?.....
third grade insult.....
on a frickin linux forum.....
grow up.....

---

### Post by jimmygoon on 2006-08-08
> **fakie_flip said:**
> tell your momma that. ubuntu is starting to get away from real linux by using  sudo and not having a root user account. i can fix this problem by removing sudo and adding a root user, but im thinking about switching to debian etch for a server because it has all the newest software in its repositories, and debian is known to make a great server.

"tell your momma that"

"real linux"

Linux is about choice and about community. If you want to use debian etch, then do so and stop trolling these forums.

---

### Post by jlapier on 2006-08-08
```
sudo sh -c "echo \"blah blah blah\" >> /etc/apt/sources.list"
```

sudi is extremely useful, I use it even on debian servers where root already exists. I'm not going to go into why, because I don't like you, fakie_flip.

---

### Post by Frem on 2006-08-08
> **jlapier said:**
> ```
sudo sh -c "echo \"blah blah blah\" >> /etc/apt/sources.list"
```

sudi is extremely useful, I use it even on debian servers where root already exists. I'm not going to go into why, because I don't like you, fakie_flip.

Just ignore the guy. His violin has become exceedingly small. :-({|=

---

### Post by VirtuAlex on 2006-08-08
> **fakie_flip said:**
> no, i will not run gedit. only newbies depend on gui apps. i am trying to resolve an issue with sudo, not figure out how to add a repository. if you read what i wrote several times before, then you would know that already.
If you so despise gedit you can run vi. The reason to use editor? Configuration files are meant to be edited, not just appended. People who follow howtos are often have no idea what they are doing, and if such unlucky newb would misspell your command she'll end up with badly screwed up repositories containing bunch of garbage. In howto it is better to tell user to add repository and refer to another howto explaining the process in general, like [https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html") or [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")
Try to educate people, not to impress them with magical commands.

---

### Post by fakie_flip on 2006-08-08
> **scotty2hott2k said:**
> hahaha, only newbies run gedit, lol, bet he's hardcore, bet he runs vim and has religiously memorised all the commands/shortcuts

run this. you may already know most of it, but im sure you can learn a few tricks from it.

vimtutor

---

### Post by foxhound_oki on 2006-08-08
fakie_flip u need to chill.  u just make all the wrong comments that gets u no where.  there are ppl alot smarter then u.  get that? they are telling you info that solved your problem.  if u don't like it don't ever post back.  go install the new linux and take ur ugly comments with u.

---

### Post by fakie_flip on 2006-08-08
midnight commander is also very useful. you should learn it if you haven't.

---

### Post by VirtuAlex on 2006-08-08
Unfortunately I ought to admit that educational system in TX is far from perfect. You do not have to be especially bright to maintain perfect 4.0 GPA here. The problems begin when you understand more about the subject than your professor does. That is when your grades are starting to go down... The good thing is that people are so nice here in the south. No, really, me ain't kidding not. Probably that is the reason to be so obnoxious online - just to let the steam out. But there ain't no bugs on me.

---

### Post by fakie_flip on 2006-08-08
> **VirtuAlex said:**
> Unfortunately I ought to admit that educational system in TX is far from perfect. You do not have to be especially bright to maintain perfect 4.0 GPA here. The problems begin when you understand more about the subject than your professor does. That is when your grades are starting to go down... The good thing is that people are so nice here in the south. No, really, me ain't kidding not. Probably that is the reason to be so obnoxious online - just to let the steam out. But there ain't no bugs on me.

are you going to U of H? i am going to UTA.

---

### Post by VirtuAlex on 2006-08-08
> **fakie_flip said:**
> are you going to U of H? i am going to UTA.
Nope, god forbid, I'm done. Looking for some other job than community service. Would be better off down here if I was geoscientist... but I'm programmer :(

---

### Post by ardchoille on 2006-08-09
> **fakie_flip said:**
> tell your momma that. ubuntu is starting to get away from real linux by using  sudo and not having a root user account. i can fix this problem by removing sudo and adding a root user, but im thinking about switching to debian etch for a server because it has all the newest software in its repositories, and debian is known to make a great server.

1. Ubuntu has a root account but it's disabled by default. If someone wants to break into your computer, they know there is a root account. Having the root account disabled makes it much harder for them to break in. And they can't break into user accounts because they don't know which users exist on your machine.

2. I have been using Linux since 1999 and have learned quite a bit. I have also been using sudo for years because it's much more secure to use sudo and have the root account disabled.

3. Chill.. your attitude leaves much to be desired.

---

### Post by huygens on 2006-08-09
> **fakie_flip said:**
> no, i will not run gedit. only newbies depend on gui apps. i am trying to resolve an issue with sudo, not figure out how to add a repository. if you read what i wrote several times before, then you would know that already.

*Note: I do not qualify anylonger as a newbie in the Linux world (perhaps for Ubuntu I am quite new), and I do love the GUI! Although, I have always a terminal open ;)*

Anyway, your command could not work because you give privilege to 'echo' but not to the redirection '>>' thus you do not have write permission. Your solution is to use 'cat' or 'tee' :) see the manual page for instance:
```
echo "what you want" | sudo tee -a /etc/the_file
``` With 'cat' it is a bit more complex, because you need to go via an intermediate file if you do not want to lose the content of your /etc/the_file...

You could have use also 'sed', or 'vi', etc. :) check their corresponding page.

Huygens

---

### Post by dusu on 2006-08-09
These forums are really great :D
People even answer kindly to someone who's writing "sudo is crap" in the title of his thread...
this self-control deserves admiration

---

### Post by Riverside on 2006-08-09
> **ardchoille said:**
> 1. Ubuntu has a root account but it's disabled by default. If someone wants to break into your computer, they know there is a root account. Having the root account disabled makes it much harder for them to break in. And they can't break into user accounts because they don't know which users exist on your machine.Playing Devil's Advocate slightly, I wonder if this is true?

Traditionally, those with root access on a Linux machine take great care (or, at least, are encouraged by distribution related documentation to take great care) to ensure that the root password is crytographically strong; a random string of upper and lower case characters and numerals is generally advised.

If, in contrast, an ordinary user account is given sudo privileges, will that user (particularly if they are a newcomer to Linux in general) typically be aware of the requirement for a cryptographically strong password to be chosen?  Will the stereotypical "it's just a user account, so password security isn't *that* important" mindset prevail?

Additionally, most distributions (for example SuSE) enforce (as default), or recommend, that root SSH login is disabled in /etc/sshd/sshd_config.  In Dapper, this is not the case, and root SSH login is enabled by default - so if the root account has been enabled by a user, remote SSH login as root is by default possible.  This is not a good thing; default should be that root SSH login is disabled by default, from a security point of view.

In respect of the "they don't know which users exist on your machine" argument, that is true but not particularly relevant.  Unless one selects cryptographically strong usernames (as well as passwords), that won't deter nor hamper a competent cracker to any worthwhile extent - and no-one is going to select cryptographically strong usernames, I wouldn't have thought.

I agree with Ubuntu's policy of disabling the root account by default - but don't believe that it is the universal security panacea that some believe it to be.

---

### Post by huygens on 2006-08-09
Hi again,

Just a few lines in response to 2 remarks you have formulated.

> **fakie_flip said:**
> [...]ubuntu is starting to get away from real linux by using  sudo and not having a root user account. [...]
What is real Linux? I have not an answer ;)
Anyway, by using sudo, Ubuntu is making Linux safer. Why, because you do not then need to use the root account, like most people do on Windows XP, and this is the major security issue in this last system and its vendor has not yet found a working solution...
We always need privileges for acting on our system, the goal of safety is to ensure that we always have the minimum required privilege for each task we performed, and possibly making the privilege higher for the shortest necessary period of time. This is what sudo does simply. It is far from being the best solution, as in this case you are a simple user or an all mighty user, there is no intermediate level. But it is still safer than with any other OS offering you a super user!


> **fakie_flip said:**
> [...]im thinking about switching to debian etch for a server because [...] debian is known to make a great server.
Good point, but this is why Ubuntu is a *Linux for Human Beings*, not server ;) Well, I'm sure Ubuntu can make a great server. But it seems to me that it's primary design was to make it accessible to anyone, thus clearly be a desktop and not a server.
If you want a server, the best, then yes, why not switching to Etch!

Huygens

---

### Post by kazuya on 2006-08-09
I like the first poster seriously had issues with using sudo as compared to being root. I was very turned off from Ubuntu breezy for this reason for almost a year plus; The look of dapper and ease of functionalities made me come back and stay. Now the sudo thing has seriously grown on me.

I really see the benefit for the others that use my Ubuntu install. It is truly great to have something like that in place to protect us the users from ourselves. And those that go through to enable the root account are then responsible for what happens to their machine should they operate all the time as root.

I left root disabled on the wife's PC. On my PC, I enabled root, but have not used it for a while except to manage files b/w users when a partition becomes full.

I know you can use "run nautilus as root " through automatix.

The attitude towards moderators should be toned down fakie flip. I like vim, and started with that, but gedit is more capable for my purpose.

As usual this community is awesome and your distro is exceptionally great.

---

### Post by huygens on 2006-08-09
> **Riverside said:**
> Playing Devil's Advocate slightly, I wonder if this is true?
[...]I agree with Ubuntu's policy of disabling the root account by default - but don't believe that it is the universal security panacea that some believe it to be.

Hello Riverside,

I guess you missed one point here. When you are an outside attacker, not knowing anything of the owner of a particular system, you first probe the machine from the network and try to determine the services it offers and what OS it is. If you find it to be a Linux OS and it has an ssh service for instance, then you know one thing for almost sure, when SSHd ask you for a login and password, you do not know the password, but you know one login at least ;) and this login is 'root'. That's why usually services such as ssh, telnet or rlogin can deny login to a remote user if he tries to identify - even legitimaly - as root. The best way, is to have root disable!
In this last case the attacker does not know the login and the password. Even if the user is having a short login and a short password, imagine all the possibility the combination of both are making? Well that's far better than having root allowed to log-in even with a strong password :)
A brute force attack is not the solution. If the attacker really need to gain access, he will have to use other technique like social engineering, so he can guess/find out at least the login of the user...

Huygens

---

### Post by huygens on 2006-08-09
> **dusu said:**
> These forums are really great :D
People even answer kindly to someone who's writing "sudo is crap" in the title of his thread...[...]

Salut,
This is great and normal because this is somehow what the [guidelines of the forum]("http://ubuntuforums.org/index.php?page=policy") and the [Ubuntu code of conduct]("http://www.ubuntulinux.org/community/conduct") - which anyone can signed :) btw - really are.
I really like the introduction of the code of conduct, if you allow me a small quote from this code, which in itself is a small quote from Desmond Tutu:
> [LIST]
[*]"A person with ubuntu is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole."[LIST]
[*] Archbishop Desmond Tutu, in No Future Without Forgiveness[/LIST] [/LIST] 
Huygens

---

### Post by dusu on 2006-08-09
Hallo Huygens,

thanks for the links. I had never noticed these pages :o 
Nice to see people have codified what should be common sense.

Tschuess

---

### Post by aysiu on 2006-08-09
Too hard-core to use Gedit but can't figure out how to use *sudo*...

---

### Post by rogblake on 2006-08-09
> **scotty2hott2k said:**
> hahaha, only newbies run gedit, lol, bet he's hardcore, bet he runs vim and has religiously memorised all the commands/shortcuts

It's reminiscent of the hardcore line-editor freaks who were looking down their noses at screen editor users ~25 years ago. A manager at a company I worked at back then had that attitude, he refused to use anything but a line editor and berated those using those new-fangled screen-oriented text editors. Yes, all of those "vi" and "emacs" users peering into their tubes are wimps, Real Programmers use "ed" on an ASR33 teletype! And if you really want to put hair on your chest you use TECO!!

I edit files with vi because I learned it decades ago and don't have to think about it, the commands are burned into my brain and automatic at this point. For the new user something like gedit is fine.

Anyway, for the original poster, if you want to enable the root account in Ubuntu, just issue the command "sudo password" and enter the desired root password. Then you can just "su" from any terminal to get a shell as the root user and edit config files to your heart's content.

---

### Post by redbull_monsta on 2006-08-09
fakie_flip go install windoze im sure you will find that easier as your struggling a bit with *nix concepts tbh!

I work as a sysadmin and have done so for around 10 years. I have a Ph.D in artificial intelligence and autonomous computer systems and quite frankly have seen more manners, intelligence and professionalism on an 8kb ROM

Go away

Rant over

Redbull_Monsta

PS please fail at everything you do at UTA, maybe then you will realise the failings you truly have

---

### Post by tseliot on 2006-08-09
Guy**s**, try to be more respectful, please

**fakie_flip**
you'd better  be polite with people who are trying to help you. And avoid starting threads which title is "xxx is crap" (or anything similar).

---

### Post by Warrenpeace on 2006-08-09
Geeze...can't we all just get along?

What's so hard about being polite in your questions?

---

### Post by ardchoille on 2006-08-09
> **huygens said:**
> Hello Riverside,

I guess you missed one point here. When you are an outside attacker, not knowing anything of the owner of a particular system, you first probe the machine from the network and try to determine the services it offers and what OS it is. If you find it to be a Linux OS and it has an ssh service for instance, then you know one thing for almost sure, when SSHd ask you for a login and password, you do not know the password, but you know one login at least ;) and this login is 'root'. That's why usually services such as ssh, telnet or rlogin can deny login to a remote user if he tries to identify - even legitimaly - as root. The best way, is to have root disable!
In this last case the attacker does not know the login and the password. Even if the user is having a short login and a short password, imagine all the possibility the combination of both are making? Well that's far better than having root allowed to log-in even with a strong password :)
A brute force attack is not the solution. If the attacker really need to gain access, he will have to use other technique like social engineering, so he can guess/find out at least the login of the user...

Huygens

Thank you, sir :)

---

### Post by Redcard on 2006-08-09
It seems like Fakie isn't here anymore.. but that said..

One of the very first things I did with ANY linux server was to disable root in favor of Sudo.  This technique is nothing new at all.  It's actually a very old hat administration technique.

root is a neat user to have and all that when you're a kid and wanting to have "power" over everyone else.. but... when you have a machine that companies are relying on, the last thing you want to do is screw something up as root.  Ergo, lock root down.  

(Another technique we would do is change the root user name.. or lock down root and use toor.  etc.  This methodology of using a different name as the administrator is ALSO not new.)

Of course, if fakie knew this, he wouldn't be so critical..  but I'd wager he comes from the hobbyist crowd.. and not from the professional linux users crowd, where things like disabling the root account and using sudo or using a different account as root were common long before Ubuntu ever was a dream.

---

### Post by halfvolle melk on 2006-08-09
> **rogblake said:**
> Real Programmers use "ed" on an ASR33 teletype! And if you really want to put hair on your chest you use TECO!!
Sounds pretty old skool, rogblake.

---

### Post by 23meg on 2006-08-09
The OP, even though acting very naively, got the solution they wanted, and claimed they'll ask elsewhere as well, so this thread has served its purpose. Why don't we all stop posting to this thread? We don't want to see the phrase "SUDO IS CRAP" coming up again and again on the thread indexes and triggering further unneeded debate, do we? 

Let this be the last post.

---

### Post by VirtuAlex on 2006-08-09
> **23meg said:**
> Let this be the last post.
That's not going to work. We need to close it. Who is moderator?

---

### Post by 23meg on 2006-08-09
We don't need the moderators to do it; we can do it ourselves. Just stop posting, nothing could be simpler.

---

### Post by Curlydave on 2006-08-09
Ubuntu isn't terminal dependent like many Linux versions. What do you use the terminal for? I haven't touched it since I installed Dapper. Everything can be easily done with the GUI. (Meaning no need to memorize terminal commands)

---

### Post by VirtuAlex on 2006-08-09
> **23meg said:**
> We don't need the moderators to do it; we can do it ourselves. Just stop posting, nothing could be simpler.
You see, I can't help it. It's reflectory :D. Okay-okay, I'm retiring myself from this thread.

---

### Post by dschulz on 2006-08-09
first, please try

```
man sudo
```

then

```
sudo sh -c 'echo "#bullshit" >> /etc/apt/sources.list'
```

---

### Post by dschulz on 2006-08-09
first, please try

```
man sudo
```

then

```
sudo sh -c 'echo "#bullshit" >> /etc/apt/sources.list'
```

---

