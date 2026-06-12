---
title: "Calling All Command Line Ninjas: I Know You're Out There..."
date: 2008-12-14
forum: General Help
---

### Post by Therion on 2008-12-14
It's finally happened to me: I've fallen in love with the CLI.  That's right, The command line.  The Terminal, the Konsole (my fav!), call this rose by whatever name you will, it will smell just as sweet.

It became official when I installed OpenOffice 3.0 from source.  I downloaded.  I extracted.  I compiled... It was like magic...  Flashes of light in my head as suddenly every command made sense!  My fingers danced across the keyboard.  Files were moved, copied and deleted.  Applications launched and obscure information about my system spilled forth.  My heart raced.  I cackeled with evil laughter as my mouse sat, unmoved and untouched.  With no clunky interface  to slow me down I chmod'ed, I used su, and gedit!  AHH HAHAHAHAHAHAHAHAHAHA!!!  I tar'ed, I grep'ed!! Not for any sound reason mind you, I just couldn't stop myself... I was a man on fire!

How could I ever have been afraid of this thing of beauty?  So simple, so elegant, so... utterly powerful!  It's amazing!!!

So now I am committed to joining the ranks of the Command Line Commandos, the Ninja-set of the CLI.  Oh yes, I know you're out there...  Are you listening?

Tell me: How **DO** I master the CLI?  What book(s) must I read, what feeds must I subscribe to, what superhuman feats must I perform to join your ranks?

---

### Post by bluefrog on 2008-12-14
in a terminal
info coreutils and read on.

that'll be a good start. Reading just for the sake of it won't do much good except if you have a huge memory (in your brain). Reading/searching to solve a problem you have might be better. You choose.

---

### Post by Tilex on 2008-12-14
Wow that was touchful ! ;)

---

### Post by smo0th on 2008-12-14
so poethic Therion

I also like the band =)

---

### Post by northern lights on 2008-12-14
Two jewels of shell documentation:

[Linuxcommand.org - Learning the shell]("http://www.linuxcommand.org/learning_the_shell.php")

[BASH programming How To]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

---

### Post by calrogman on 2008-12-14
To be a true CLI ninja, you'll have to compile Gentoo from a stage1 tarball, I won't be doing that for a few years.

---

### Post by Therion on 2008-12-14
> **northern lights said:**
> Two jewels of shell documentation:

[Linuxcommand.org - Learning the shell]("http://www.linuxcommand.org/learning_the_shell.php")
Nice!

---

### Post by karlr42 on 2008-12-14
You used gedit? Why not vi? :P

---

### Post by jimi_hendrix on 2008-12-14
1 command at a time...and learn vim ;)

---

### Post by drubin on 2008-12-14
> **Therion said:**
> It's finally happened to me: I've fallen in love with the CLI.  That's right, The command line.  The Terminal, the Konsole (my fav!), call this rose by whatever name you will, it will smell just as sweet.

....

How could I ever have been afraid of this thing of beauty?  So simple, so elegant, so... utterly powerful!  It's amazing!!!

Tell me: How **DO** I master the CLI?  What book(s) must I read, what feeds must I subscribe to, what superhuman feats must I perform to join your ranks?

Nice post. \o/

Start using CLI application instead of your normal GUI apps. Working in a CLI environment will help you be come comfortable working in a pure CLI learning the commands is trivial after that.
1) Learning to read man pages is a must.
2) Sense of security don't just run things with out knowing what they do
3) Have fun and enjoy the superior way of the CLI

Basic CLI apps you might want to play with
Text Editor - vim
Irc client - weechat, irssi
CLI pidgin - finch 

[http://mssaleh.wordpress.com/2008/05/10/command-line-alternatives-in-ubuntu-linux/](http://mssaleh.wordpress.com/2008/05/10/command-line-alternatives-in-ubuntu-linux/)

---

### Post by bodhi.zazen on 2008-12-14
Read the bash man page , learn to use the man pages, and take zsh for a test drive (although you need to copy a .zshrc from someone because the default .zshrc is nothing special).

---

### Post by drubin on 2008-12-14
> **bodhi.zazen said:**
> Read the bash man page , learn to use the man pages, and take zsh for a test drive (although you need to copy a .zshrc from someone because the default .zshrc is nothing special).

/me hints at bodhi.zazen posting his some where :)

---

### Post by dannytatom on 2008-12-14
> **bluefrog said:**
> if you have a huge memory (in your brain).

I laughed so hard that you clarified this. :P

---

### Post by snova on 2008-12-14
As powerful as commands are by their own, I second learning the shell itself- pipes are extremely useful, stringing commands together to do something new.

Just play around. :)

---

### Post by karlr42 on 2008-12-14
The command-line is indeed a wonderful thing. 
My college's Internet Society maintains a Debian box which all members can ssh into from anywhere, via putty or ssh in terminal. It's a headless machine with no Xserver. You learn so much working in such an enviroment- I've set up webspace, learned about permissions, learned scp and rsync so I can work on assignments at home, then rsync via this Debian box to my College account, so I can then work on them in the labs. There's an irssi client set up for users to chat with, so I've learned how to use that as well, in combination with screen. As a computer science student, the wealth of *nix utilities opened my eyes to the power of computers far beyond what I had ever seen possible on Windows machines.

---

### Post by bodhi.zazen on 2008-12-14
> **drubin said:**
> /me hints at bodhi.zazen posting his some where :)


You can get it here :

[http://bodhizazen.net/adblock/zshrc](http://bodhizazen.net/adblock/zshrc)

Save it as .zshrc

To use it :

```
sudo apt-get install zsh most display-dhammapada
```

most will add color to your man pages.

I use display-dhammapada to give Buddhist quotes.

You will need to edit my zshrc it you do not wish to use these features.

---

### Post by lswb on 2008-12-14
There is a bash scripting guide in the repositories but it is usually out of date. Get the latest version of the abs guide from the author's site: 

[http://personal.riverusers.com/~thegrendel/](http://personal.riverusers.com/~thegrendel/) 

Both html and pdf versions are available. 

Direct link to the latest html version:

[http://personal.riverusers.com/~thegrendel/abs-guide-5.5.tar.bz2](http://personal.riverusers.com/~thegrendel/abs-guide-5.5.tar.bz2)

---

### Post by TBSN on 2008-12-14
> **bodhi.zazen said:**
> Read the bash man page , learn to use the man pages, and take zsh for a test drive (although you need to copy a .zshrc from someone because the default .zshrc is nothing special).

What is .zshrc? Is it an alternative shell to bash? Why is it better?

---

### Post by snova on 2008-12-14
Zsh is another shell. .zshrc is to Zsh as .bashrc is to Bash.

There's a lot of extra features, but I can't think of any particular one to name.

---

### Post by bodhi.zazen on 2008-12-14
[http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)
    [http://www.ibm.com/developerworks/linux/library/l-z.html?dwzone=linux](http://www.ibm.com/developerworks/linux/library/l-z.html?dwzone=linux)

---

### Post by Therion on 2008-12-14
> **bodhi.zazen said:**
> [http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)
    [http://www.ibm.com/developerworks/linux/library/l-z.html?dwzone=linux](http://www.ibm.com/developerworks/linux/library/l-z.html?dwzone=linux)
Sooo... Would I better off learning Zsh right from the start?  

I'm willing, since I don't really know s--t from shinola about either Bash or Zsh.

---

### Post by TBSN on 2008-12-14
> **snova said:**
> Zsh is another shell. .zshrc is to Zsh as .bashrc is to Bash.

There's a lot of extra features, but I can't think of any particular one to name.

> **bodhi.zazen said:**
> [http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/](http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/)
    [http://www.ibm.com/developerworks/linux/library/l-z.html?dwzone=linux](http://www.ibm.com/developerworks/linux/library/l-z.html?dwzone=linux)

Ah, now I get it. the .zshrc (and .bashrc) are configurations of the shell, right? I'm just learning the command line as well, so I should probably stay with the default Ubuntu bash shell for now...

---

### Post by snova on 2008-12-14
There are many conf files related to the shell, but .<shell>rc is the primary interactive one from what I know.

---

### Post by bodhi.zazen on 2008-12-14
> **Therion said:**
> Sooo... Would I better off learning Zsh right from the start?  

I'm willing, since I don't really know s--t from shinola about either Bash or Zsh.

> **TBSN said:**
> Ah, now I get it. the .zshrc (and .bashrc) are configurations of the shell, right? I'm just learning the command line as well, so I should probably stay with the default Ubuntu bash shell for now...


IMO you should learn bash first. zsh is similar to bash and is an easy transition to make, but bash is the default in most distros and there is more documentation.

It will help if you understand bash when you read the zsh documentation.

You can use the z shell while you are learning bash.

---

### Post by TBSN on 2008-12-14
How can you use bash and the z shell at the same time?

Is the z shell different than zsh?

excuse my utter ignorance...

---

### Post by snova on 2008-12-14
You can have both installed, they do not conflict. Bash will remain your default shell until you change it, however.

"Zsh" means the same as "Z shell". Csh, "C shell"; Ksh, "Korn Shell"; you get the idea.

---

### Post by TBSN on 2008-12-15
Ok, I see. What's the command to switch shells? Do you just do "./bin/zsh" ?

---

### Post by bodhi.zazen on 2008-12-15
To start a new shell, call it

zsh

bash

and on ....

To set it as default use chsh (change shell)

chsh will as for your password and use a path of the shell (/bin/zsh for example).

---

### Post by snova on 2008-12-15
> **TBSN said:**
> Ok, I see. What's the command to switch shells? Do you just do "./bin/zsh" ?

Ah, no. That would look for a directory called 'bin' and a file named 'zsh' within that directory... all of which, where you currently are. It wouldn't work. Either '/bin/zsh' or just 'zsh', since /bin is in PATH.

---

### Post by TBSN on 2008-12-15
Thanks, I just figured it out. I tried out the configuration to above, I like the buddhist quotes!

I am going to stick to bash for now, as I'm still very new to Linux. So far all I can do in Terminal is navigate the filesystem, move, copy, remove, change permissions, etc... pretty basic stuff.

---

### Post by drubin on 2008-12-16
> **Therion said:**
> Sooo... Would I better off learning Zsh right from the start?  

I'm willing, since I don't really know s--t from shinola about either Bash or Zsh.

> **bodhi.zazen said:**
> IMO you should learn bash first. zsh is similar to bash and is an easy transition to make, but bash is the default in most distros and there is more documentation.

It will help if you understand bash when you read the zsh documentation.

You can use the z shell while you are learning bash.

Most systems will not have Zsh installed/set up so  knowing bash is a must since it appears on most if not all systems. 

Changing your current system to much as far as commands go can hinder you with working with other systems.

example always adding ll alias to ls -l will fail on systems where this is not set up and will fail.. and if you forget what ll was aliased to you can be kinda lost with out a paddle. (There are more complicated examples)

---

### Post by bodhi.zazen on 2008-12-16
Nothing a little wget can not fix :)

wget [http://bodhi's_secret_server/bashrc](http://bodhi's_secret_server/bashrc)

---

### Post by drubin on 2008-12-16
> **bodhi.zazen said:**
> Nothing a little wget can not fix :)

wget [http://bodhi's_secret_server/bashrc](http://bodhi's_secret_server/bashrc)

You might not have sudo/root access to install another shell.

Also changing/installing extra stuff on *live* systems might not be a great idea :)

---

### Post by doobiest on 2008-12-16
> **northern lights said:**
> Two jewels of shell documentation:

[Linuxcommand.org - Learning the shell]("http://www.linuxcommand.org/learning_the_shell.php")

[BASH programming How To]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

[BASH programming How To]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html") Is a must!

---

### Post by Therion on 2008-12-16
I must say that **Learning the Shell** link/document is outstanding.  I only wish it was in a downloadable format (.pdf anyone?) for ease-of-use.

Anyone know of a way to do that?  I'd be happy to do it and upload it for the good of one and all if it's possible.

Thanks for all the great replies, by the way.

---

### Post by bodhi.zazen on 2008-12-16
> **drubin said:**
> You might not have sudo/root access to install another shell.

Also changing/installing extra stuff on *live* systems might not be a great idea :)

he he he :

> wget [http://bodhi's_secret_server/**[COLOR=darkred]bashrc[/COLOR]**]("http://bodhi%27s_secret_server/bashrc")

---

### Post by Slim Odds on 2008-12-16
> wget [http://bodhi's_secret_server/**[COLOR=darkred]bashrc[/COLOR]**]("http://bodhi%27s_secret_server/bashrc")

That link does not work.....

---

### Post by unutbu on 2008-12-16
Therion, 
Go to [http://sourceforge.net/projects/linuxcommand/](http://sourceforge.net/projects/linuxcommand/),
download "linuxcommand-view-offline".

If the download page does not seem to work, choose a different mirror.

---

### Post by drubin on 2008-12-16
> **bodhi.zazen said:**
> he he he :

I plead the 5th :) 

But still I still stand by my point of the users should understand where their "nice-eties" come from all the little cool short cuts we add to our own systems are great but sharing those with newbies can hurt them in the long run.

---

### Post by bodhi.zazen on 2008-12-16
> **Slim Odds said:**
> That link does not work.....

LOL. No, I posted my zshrc (look up).

I can post my bashrc if you like, but again you need most and display-dhammapada

[http://bodhizazen.net/adblock/bashrc](http://bodhizazen.net/adblock/bashrc)

---

### Post by Therion on 2008-12-16
> **unutbu said:**
> 

Therion,

... download "linuxcommand-view-offline".

Awesome!! Nabbed and...  Printed.

Figured out that printing from Preview allowed me to remove the url and header/footer stuff for a nice, clean printout.

---

### Post by Slim Odds on 2008-12-16
> **bodhi.zazen said:**
> LOL. No, I posted my zshrc (look up).

No, the address that you posted was > [http://bodhi%27s_secret_server/bashrc](http://bodhi%27s_secret_server/bashrc)Which is not a place on the interweb :confused:  ):P

---

### Post by Slim Odds on 2008-12-16
dup

---

### Post by bodhi.zazen on 2008-12-16
> **Slim Odds said:**
> No, the address that you posted was Which is not a place on the interweb :confused:  ):P

I know, that was a joke :lolflag:

I posted my bashrc if you like :

[http://bodhizazen.net/adblock/bashrc](http://bodhizazen.net/adblock/bashrc)

---

### Post by captainhydrollama on 2008-12-16
I didn't particularly feel like learning my bash cli until this thread came along. Now I'm loving it the power and simplicity! Cheers to you all for the teachings.

---

### Post by donkyhotay on 2008-12-16
> **calrogman said:**
> To be a true CLI ninja, you'll have to compile Gentoo from a stage1 tarball

ROFL! Thats more in the realm of masochism. Seriously though the CLI is very useful. Personally I have yakuake running automatically on my user accounts (I prefer gnome but find it's worth having all the KDE libs just for that program) which is a quake style CLI that I can make appear and vanish at whim. I'm not a person that thinks either the GUI or the CLI is better but each one has it's own strengths/weaknesses and I flip between the two often depending on what I'm doing. Compiling from source, I'm in the CLI. Needing a specific picture based on it's thumbnail, GUI all the way.

---

### Post by Therion on 2008-12-16
> **captainhydrollama said:**
> 

Now I'm loving it the power and simplicity!

*Intoxicating*, isn't it?

---

