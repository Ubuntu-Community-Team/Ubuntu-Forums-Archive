---
title: "Root login"
date: 2006-07-15
forum: Desktop Environments
---

### Post by Mishal on 2006-07-15
I could log in as root in Breezy but I can't do that in Dapper. Is there any way out?

---

### Post by aysiu on 2006-07-15
Yes--just avoid root altogether:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

If you really want to use root in the terminal: ```
sudo -s
``` should help.

---

### Post by Mishal on 2006-07-15
I know it's not a good idea but I still need to. Has the option of loggin in as root disabled in Dapper?

---

### Post by T700 on 2006-07-15
> **Mishal said:**
> I know it's not a good idea but I still need to. Has the option of loggin in as root disabled in Dapper?

Did you read what aysiu [[COLOR=#5F2D06]****[/COLOR]]("http://www.ubuntuforums.org/member.php?u=21941") posted?  It explains how to do that.

That said, perhaps if you explain what you are trying to accomplish, someone can suggest a better way to do it.

Paul

---

### Post by Ramses de Norre on 2006-07-15
You mean graphical login? ```
gksudo gdmsetup
``` gives you the gdm setup, in the security tab you can then enable "Allow local system administrator login".
This is when you use gdm and as said before you should only use this when it's really necessary and you know what you're doing.

---

### Post by Mishal on 2006-07-15
Yes I meant graphical login. Actually, this sounds silly but the reason I wanted to log in as root was to change the root's desktop theme.

When I change my own user's theme to some particular flavour (not the default ones like Human or Industrial), it's not a system-wide change in theme. Like for example, when I open Synaptic (as root of course), it's not in the theme I had selected. When I used Breezy, I just logged in as root and changed its theme too.

So, to cut things short, is there a way I can bring up the themes option of root while being a non-root user. Like for example: if gksudo nautilus can work, will something like gksudo themes work?

---

### Post by Ramses de Norre on 2006-07-15
Easy fix: ```
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.fonts /root/.fonts
```

---

### Post by Mishal on 2006-07-15
Wow...great idea. You just made the root's themes, icons and fonts folders as symbolic links to the user's actual folders, right? As a result, any changes made in the user's folders will also be reflected in the root's folders?

---

### Post by Ramses de Norre on 2006-07-15
Indeed, so all root apps will have same theme, fonts and icons as your user apps.

---

### Post by 3rdalbum on 2006-07-15
Erm... doesn't that happen anyway? That's the way it's always worked on my computers, and I haven't created symbolic links.

(By the way, clever idea!)

---

### Post by Mishal on 2006-07-15
3rdalbum, it doesn't happen with themes downloaded from the internet as far as my experimentation tells me. However, if you use some of the default themes provided by Ubuntu like 'Simple', Smokey-Blue' or 'Industrial', then the changes are system-wide.

---

### Post by MrHorus on 2006-07-15
> **Mishal said:**
> Yes I meant graphical login. Actually, this sounds silly but the reason I wanted to log in as root was to change the root's desktop theme.


Curious, but why would you ever want to do a graphical login as root?

I fail to see what you will acomplish that cannot be achieved from a standard login and su/sudo at the console, so I am pretty curious as to why you feel you need a graphical login as root?

---

### Post by Ramses de Norre on 2006-07-15
He explained, he used to login as root to set the themes used by programs launched by gksudo.

---

### Post by MrHorus on 2006-07-15
My mistake, I misread :)

---

### Post by aysiu on 2006-07-16
Still no need to log in as root. Set the themes by doing ```
gksudo gnome-theme-manager
```

---

### Post by jgcamp99 on 2006-07-16
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

There is an excerpt on going back to the traditional root way of doing things. Ubuntu created a root user when you installed it, it is disabled from graphical logins. If root wasn't necessary, why was it created ? I can understand locking it down for security reasons. I can't imagine why you wouldn't want an administrator to be able to login though on any system. As sudo commands, I fail to see the difference. Under sudo, anyone can re-enable root, can even do what the super user can do. The rational given is a false sense of security. After installing Ubuntu, it didn't take long to realize root was disabled and even less time to google it and reenable root. Of course if I hacked a sudo user account, it would make no difference whether root was enabled or disabled. I guess if you are after learning sudo, this makes sense, but to have both options available, what's the harm/difference ?

---

### Post by aysiu on 2006-07-16
Root as a user is necessary, but that doesn't mean you have to log in as root. For example, you'll notice that if you run a program with *sudo* of *gksudo* and then run the ```
top
``` command, it won't say that you're running the program--it'll say root is. This is despite the fact that you are logged in as user and not root.

So I don't really see how the root account *existing* is relevant to the debate about whether to log in as root or not. The login is disabled, the password is disabled, and none of the administrative tasks ask for the root password (Synaptic, Networking, etc.)

I don't see how it's a false sense of security at all. Why would it be easier to crack into a sudo account than root? First of all, a sudo account could be one of any number of usernames. And then how would you know which username has sudo privileges?

On the other hand, root is always called root, and it always has administrative privileges.

If you were a cracker, which one would you go for?

I'm just repeating arguments made in the page you linked to, so I don't really see why you're ignoring them in the first place.

Besides, the best thing about the *sudo*/*gksudo* model is convenience, not just security. Thankfully, the *sudo* model offers both.

It's much easier for me to change root themes by pressing Alt-F2 and typing ```
gksudo gnome-theme-manager
``` than logging out of user, logging in as root, launching the theme manager, and then logging out of root, and logging back in again as user.

If I do that separate login as root, it also means everything else I do while changing that theme is also done by root.

With sudo, you can easily switch back and forth, making one command a user command, another command a root command. You can have one program running as root and another program running as user.

---

### Post by jgcamp99 on 2006-07-16
This never happens when logged in as root !

[http://www.ubuntuforums.org/showthread.php?t=216520&highlight=unable+sudo](http://www.ubuntuforums.org/showthread.php?t=216520&highlight=unable+sudo)

And then there's recovery mode, root to the rescue !

[http://www.ubuntuforums.org/showthread.php?t=216796&highlight=unable+sudo](http://www.ubuntuforums.org/showthread.php?t=216796&highlight=unable+sudo)

So why would grub choose to bail out sudo user as root and not vice versa ?

notice a pattern here, when sudo doesn't work for whatever reason(s), root does, it's a fail safe for sudo.

I do all my updates as root, never had a single issue, on the other hand, there are those folks that have been doing the updates as the sudo Ubuntu user and wind up crying the blues of hosed updates. Sudo works for you, and that's fine, but for others that don't know the sudo command inside and out, Ubuntu needs to allow it's users to choose which method best works for the user.

You say it's easier to do sudo commands, so which is harder knowing when to type in "gksudo" vs just "sudo" @ the prompt or command line, or logging in as root and just typing the command without having to type either. Does it matter what the permissions are when you are root, or having to go hunt down a file or two or several with different dependencies and then sudo chown command. Root doesn't care because it owns all other users and can do whatever it wants. I wish I were a blackbelt in SUDO, then again as root I am master of SUDO users, which makes me better than a blackbelt with SUDO.

So it is, it's easier to remember a password for root than it is to preface every thing you run thru the command line with sudo or gksudo and have to type that every time you run something. Do a simple keystroke count. Everything else is the same across the board, opening windows and clicking logout and typing username and password. On the fly, already in as sudo user can be less time consuming if you're lucky and all goes well, but is it really when the error message(s) of denial/denied pops up ?  I went thru that once with sudo, following a "how to", it kept denying me a simple copy procedure. So I got fed up with it and logged out as sudo user, logged in as root and there I was off and running, where sudo left me thinking what I was going to have to do next and stonewalled for a solution. For the most part softwares should install without issue and everytime I've run into issues, it's been under sudo. never under root. Give me root anyday, this way whatever I've done under root I know changed across the board and is there and available for every user. In my home I am the only person that uses the computer, why should I lock it down like it's a computer over at the local internet cafe of local Best Buy/CircuitCity/CompUSA or whatever location where some pissant little dweeb has decided to change the settings for the demo model system ?

And stating that it's safer to hack the admin/root account is nonsense, hacking a sudo user account is no more difficult and does the same thing, because once in that sudo user account, you run the same root password re-eanble that sudo can do anyway and just like hacking a root account, the password can be changed and so forth. So as for which user I would crack/hack, of course, the root one, then again, how long would it take to simply try the sudo user account for sudo ? I'm sure the hacker would feel so inconvenienced after waiting hours/days to get a userid and password from brute force attacks that it would never occur to the hacker to try it, especially when they could run the menu from the desktop and get the password trying to use synaptic.

---

### Post by aysiu on 2006-07-16
I don't feel like doing [this](http://www.ubuntuforums.org/showthread.php?t=197892&page=2) again.

---

### Post by jgcamp99 on 2006-07-16
Me too ! ;)

---

