---
title: "customizing terminal  (maverick/gnome)"
date: 2011-06-09
forum: Desktop Environments
---

### Post by abqhandyman on 2011-06-09
Hello good people of the world.

To flesh out my *nix capability, I create new identities and give them the functionality that I liked in previous ones.  I've added the "open terminal here" script, which I find invaluable.  Now I want to change the prompt.  This is what the terminal does right now:

ITo run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

elliot@dan:/media/KINGSTON$ 

q1)  Where do I go to shorten the prompt dramatically?  I can't really think of a situation where a shorter prompt isn't better or color matters.

q2)  How do I adios the 2 sentences that want to appear every time I open this terminal?  I'm aware what sudo does.

q3)  Instead, I would like the equivalent of a pwd command.  Where would I put that?

q4) How do I get the output of this terminal to be simultaneously saved in a file.  I do so much copying and pasting out of these terminals that I'm looking for easier ways to do it.

Peace.  Love.  Rock n Roll.:popcorn:
-- 
abqhandyman

---

### Post by searchfgold6789 on 2011-06-09
Hello back!
I think I can answer 3 of these:

[LIST=1]
[*]To shorten the  prompt would be to alter a very important part of the terminal, and I  think you would have to at least edit the source code of the terminal,  or patch the kernel, or something like that. Listing the 'working  directory' is one of the very vital things a CLI of this type should do,  and you'd have to dig pretty deep to change something like that. As far  as I am aware there is no config file you can change to suppress the  working directory.
[*]You would either have to edit the source code  for gnome-terminal, or look for a config file or script that opens the  terminal, and edit that. I wouldn't know where such a file would be as I  do not use gnome-terminal, being a KDE freak. ;) I use Byobu Terminal,  and I see a message about Ubuntu and the help website, but it is not the  same as the gnome-terminal message.
[*]I'm afraid I can't answer this.
[*]Byobu  has a convenient 'Save Output As...' feature that may be what you are  looking for. Also try the 'script' command ("man script" for more info)
[/LIST]
I hope I provided useful info :)
 - search

---

### Post by lotuseclat79 on 2011-09-14
Hi abqhandyman,

It is easy to shorten your prompt via the home directory .bashrc file, e.g. ~ubuntu, i.e. /home/ubuntu.

Edit the .bashrc file by adding the following, as an example:
PS1="[\u@\h \W:\!] "

After exiting your text editor, then execute the following command:
$ . .bashrc
which reexecutes the .bashrc file and shortens the prompt.

-- Tom

---

