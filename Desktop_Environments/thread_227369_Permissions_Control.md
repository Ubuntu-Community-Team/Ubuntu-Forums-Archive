---
title: "Permissions Control"
date: 2006-08-01
forum: Desktop Environments
---

### Post by JcZndeR on 2006-08-01
I'm making a guest account on my computer 4 like other ppl and i was wondering if there was something i could use to set advanced permissions for example locking all other folders except the user home folder and maybe a deep freeze equivalent on windows..
I don't want to worry about others going thru my files or accidentally screw something up, and possibly disable the terminal too..
I've seen such programs like that on public comps at my library..
hopefully i can make the account idiot proof, I realize that will probably reduce the functionality of the account by a lot but the only thing I really need it to be able to do is like Internet and other stuff like write/read OpenOffice docs and games maybe..
thanks in advance :)

---

### Post by apjone on 2006-08-01
pessulus is the lockdown editor, while saboyon allow the administrator to profile a desktop for users and apply it where necessary.

---

### Post by JcZndeR on 2006-08-01
I get these with Synaptic?

---

### Post by aysiu on 2006-08-01
If you're using KDE, you can install [kiosktool](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kiosktool&searchon=name&subword=1&version=all&release=all).

---

### Post by ardchoille on 2006-08-01
What I did was chmod 750 my $HOME directory so others can't get into it.
I also went into /usr/share/applications and took all of the .desktop files for apps that I don't want other users to run and put those .desktop files in ~/.local/share/applications (in my home directory) so the menu items of apps I don't want them to run won't appear in their menus but will still appear in my menus.

I also recommend not putting untrusted people into the admin group, adding yourself to the wheel group and setting su so that others can't call it:

```

sudo chown root:wheel /bin/su && sudo chmod 4750 /bin/su

```

This will give unauthorised users a permission denied error instead of letting them sit there all day repeatedly calling su to try and brute force the root password. I learned this little trick from a veteran Red Hat employee :)

---

### Post by aysiu on 2006-08-01
JcZndeR, are these friends/acquaintances for the most part? If so, I would hope they're not trying to brute-force a root password. There are different kinds of security to put in place, depending on the social circumstances.

---

### Post by JcZndeR on 2006-08-01
> **aysiu said:**
> JcZndeR, are these friends/acquaintances for the most part? If so, I would hope they're not trying to brute-force a root password. There are different kinds of security to put in place, depending on the social circumstances.

Yes these r friends/family but either way I wouldn't worry about brute-force attacks because my password is a little long to guess..  No guessable pattern, and it would still take superfast computers a few decillion years (actually its much greater than that but those words get confusing)...
i tried calculating how long it will take to crack my password once but unfortunately the site only went up at 20 characters..
yes it is at that length.. ;)

---

### Post by JcZndeR on 2006-08-01
Thanks for all the replys.
I will try these..

---

### Post by JcZndeR on 2006-08-01
I failed to find a program named saboyon, so maybe its spelled wrong..
Anyhow can someone point me in the right direction?

edit: I found out it was spelled Sabayon with an a instead of an o

---

