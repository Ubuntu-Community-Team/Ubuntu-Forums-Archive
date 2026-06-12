---
title: "Is there still a way to edit the computers name w/ GUI"
date: 2009-06-02
forum: General Help
---

### Post by SoftwareExplorer on 2009-06-02
I know you can do it by editing text files, but you have to edit two of them and sudo won't work until they are the same, so my question is: can you change your computer's name with the GUI in jaunty? It sounds like it was possible in previous versions of ubuntu under System -> Administration->???, but I can't find it where a read to look for it.

---

### Post by MyR on 2009-06-02
so you're saying there are 2 files that contain the "computer's name" and currently they are different on your system, so "sudo" won't work, and thus you cannot fix the problem?

1. boot into recovery mode (choose the recovery mode option when the list of kernels comes up in grub, or if you just have one OS you need to hit esc to bring up the list).  If you're still not sure how to boot into recovery mode I'm sure you can find that information pretty easily.

2. choose root prompt (without networking)

3. "hostname -v newhostname" will be the command you enter to set the name.

4. reboot. (shutdown -h now)

peace

---

### Post by dcstar on 2009-06-02
> **SoftwareExplorer said:**
> I know you can do it by editing text files, but you have to edit two of them and sudo won't work until they are the same, so my question is: can you change your computer's name with the GUI in jaunty? It sounds like it was possible in previous versions of ubuntu under System -> Administration->???, but I can't find it where a read to look for it.

Install the **gnome-network-admin** package.

---

### Post by Meson on 2009-06-02
> **dcstar said:**
> Install the **gnome-network-admin** package.

That would require sudo =)

---

### Post by dcstar on 2009-06-03
> **Meson said:**
> That would require sudo =)

Installing **ANY** package required the admin password, nothing more.

---

### Post by SoftwareExplorer on 2009-06-09
Thanks dcstar. That was what I was looking for. 

@Meson & MyR Not to worry, I made sure that I didn't mess up sudo, I just read how to change the name of the computer and it warned that you have to open both files before you change them or you get locked out. 


The main reason I asked my question was that I was trying to figure out if Ubuntu required you to use the CLI to do this (and not only that but using it to do something that could be a little risky if not done correctly), or if it was possible to do with a GUI.

It's not that the CLI scares me, in fact, I use it quite a bit, but what about a person who is new to Ubuntu? What happens when they come from windows expecting a GUI way to change their computer's name?

---

### Post by CatKiller on 2009-06-09
Glad you had the presence of mind to check first. Yes, it did used to be easy to do it safely in the normal Network setup tool; gnome-network-admin was the graphical way to change any network setting and worked well. Unfortunately, it assumed quite a static networking setup since at the time it was written people didn't change the networks that they were on especially frequently. Since then, people have expected to be able to join and leave wireless networks at the drop of a hat, and gnome-network-admin wasn't really set up for that. So NetworkManager was created, which can do some of the new things. Unfortunately, it can't do quite a few of the old things. Like change the host name. Or use a static IP address. Until NetworkManager gets up to scratch, a number of people have chosen to use the old tools instead.

---

### Post by SoftwareExplorer on 2009-06-10
Hm, ok, I think that I will go and put an idea on brainstorm to have GUI way to change the host name again. Thanks for the help.

@CatKiller Is your signature from the matrix or something else?

---

### Post by CatKiller on 2009-06-10
> **SoftwareExplorer said:**
> @CatKiller Is your signature from the matrix or something else?

Something else ;)

It's from Redemption Song, a Bob Marley song, which in turn is quoting Marcus Garvey.

---

### Post by haemphyst on 2009-07-11
I'm not looking for any way to change my host name, I'm happy with that.  However, I want to connect my PC to a specific workgroup.  I can't seem to see any of my windows shares, as I think I am not a member of their workgroup/domain.

How does somebody do that?  ...and being as I am so NOT familiar with the CLI, if there is/are command lines required, please post the entire text as would be necessary...

---

### Post by SoftwareExplorer on 2009-07-11
Go to applications ->  Accesories -> Terminal and run:
```
gksudo 'gedit /etc/samba/smb.conf'
```

Search for workgroup in the file that comes up. You should find a place in the file that says
```
workgroup = WORKGROUP
```
change it to
```
workgroup = MYWORKGROUP
```
save the file and close the gedit window.
To load the new changes, run
```
sudo /etc/init.d/samba restart
```
In the terminal.
If that doesn't do it, you can restart your computer.

---

