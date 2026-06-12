---
title: "Fun greeting in login shells, but not in terminal in GUI"
date: 2006-01-12
forum: General Help
---

### Post by carlosqueso on 2006-01-12
I followed the directions in other posts and edited my .bashrc file to produce a much friendlier greeting.  However, now when I open up a terminal, it produces that same greeting.  How do you make the greeting show up when you SSH in or log in through a console, but not in the terminal that you use in the GUI?

---

### Post by kaamos on 2006-01-12
I think the file you are looking for is /etc/motd. It is showed with ssh and tty-terminals, but not in the gui.

---

### Post by schilcha on 2006-01-12
Edit: Yeah, just because I hit "Quick Reply", it doesn't mean I'm typing quickly too... Anyways, here my thoughts:

Try to put in in your .profile -- it'll be only displayed for login-shells. In contrast .bashrc is sourced for every shell.

Also you can put it in /etc/motd (message of the day). That's where the default ubuntu-message is stored.

---

### Post by kabus on 2006-01-12
If you put something in you .bashrc to produce that greeting you could also enclose it in an 'if'-statement :

```
if [ $TERM = "x" ]; then
  *do something*
fi
```

Just replace x with the type of terminal were you want the message displayed. 
You can find out the correct setting by typing "echo $TERM" in such a terminal.

---

### Post by carlosqueso on 2006-01-12
[QUOTE=schilcha]Edit: Yeah, just because I hit "Quick Reply", it doesn't mean I'm typing quickly too... Anyways, here my thoughts:

Try to put in in your .profile -- it'll be only displayed for login-shells. In contrast .bashrc is sourced for every shell.

Also you can put it in /etc/motd (message of the day). That's where the default ubuntu-message is stored.[/QUOTE]

I'm using the fortune and cowsay programs, so that doesn't work.....any other ideas?

---

### Post by carlosqueso on 2006-01-12
[QUOTE=kabus]If you put something in you .bashrc to produce that greeting you could also enclose it in an 'if'-statement :

```
if [ $TERM = "x" ]; then
  *do something*
fi
```

Just replace x with the type of terminal were you want the message displayed. 
You can find out the correct setting by typing "echo $TERM" in such a terminal.[/QUOTE]


I'll try that...do you know the $TERM value for a terminal that you open in the GUI?  I'm not at home at the moment so I only have SSH

---

### Post by schilcha on 2006-01-12
> **carlosqueso]I'm using the fortune and cowsay programs, so that doesn't work.....any other ideas?[/QUOTE]

Sorry, my fault. Don't use .profile -- for some reason it doesn't work with ubuntu's bash (although the manual says so). Use ~/.bash_profile instead. I added fortune to my .bash_profile, opened a terminal from the gnome-menu and ssh'd into my my machine. Here, the output:
[QUOTE]
schilcha@smithers:~$ ssh schilcha@smithers
schilcha@smithers's password:
Linux smithers 2.6.12-10-686 #1 Thu Dec 22 11:55:07 UTC 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software said:**
> 
applicable law.
No mail.
Last login: Thu Jan 12 21:57:56 2006 from smithers.springfield
Nothing so needs reforming as other people's habits.
                -- Mark Twain
schilcha@smithers:~$


So, none of fortune's quotes as the terminal starts, but a quote indeed after ssh-login.

---

### Post by carlosqueso on 2006-01-12
Awesome....thanks for the help! I've got cows under SSH, and when I return home, I'll check that.

---

