---
title: "Is there really a Difference between SUDO &amp; GKSUDO??"
date: 2009-04-19
forum: General Help
---

### Post by OzzyFrank on 2009-04-19
I've seen a lot of guides on many Linux subjects where tasks had to be done as root or superuser, and had the general impression **SUDO** and **GKSUDO** were basically interchangeable. However, I just came across a post where someone was explaining how to label and format drives using GParted, using **[COLOR="Navy"]sudo gparted[/COLOR]** as the terminal command to open GParted as root/superuser, and someone disagreed with the use of **SUDO**:

[COLOR="Indigo"][B]If I recall correctly, you technically &#8220;should&#8221; be using `gksudo gparted`. Running graphical programs using sudo can be 100% fine, or it can cause all sorts of problems. 

Now, I would guess that it is likely that GParted wouldn&#8217;t do anything that could cause those problems, but it is a good practice to use gksudo for graphical applications. Additionally, you can make shortcuts (launchers?) using gksudo, while you have to run sudo from a terminal to see the password prompt.[/B][/COLOR]

I'd just like to clear this up out of curiosity, so welcome any input. As far as I could see, there is no difference, and had the impression (from dates of posts/threads) that GKSUDO was what people commonly used in the first half of the decade and SUDO being used more recently (I rarely see recent posts where you are told to use GKSUDO). I could be wrong, so please feel free to clarify. Also feel free to give your input on the last bit about launchers (I've yet to test that one). Cheers.

---

### Post by Wiebelhaus on 2009-04-19
Watching thread...

---

### Post by cariboo on 2009-04-19
Using sudo with a graphical application does not work 100% of the time if you open an app using Alt-F2 for example if you if you press Alt-F2 and type:

```
sudo synaptic
```

nothing happens. If you type:

```
gksu synaptic
```

a box pops up allowing you to enter your password and synaptic opens. If you open a terminal and type:

```
sudo synaptic
```

you have to enter your password in the terminal before synaptic will open. Gksu and sudo have the same function, use gksu for graphical apps and use sudo in a terminal.

Jim

---

### Post by CatKiller on 2009-04-19
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by sisco311 on 2009-04-19
By default, if you run a command with sudo a minimal environment containing TERM, PATH, HOME, SHELL, LOGNAME, USER and USERNAME is preserved.

To list the preserved environment variables:
```
sudo sudo -V
```


i.e.
```
sudo gnome-terminal
```
```
echo $HOME
/home/username
```

gksu does not preserve $HOME environment variable. 

```
gksu gnome-terminal
```
```
echo $HOME
/root
```

For example, "sudo firefox" runs firefox with root privileges but uses the user's configuration file. for most GUI apps this is not the desired behavior. 

[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

---

### Post by OzzyFrank on 2009-04-19
I'm starting to see the difference... I just never had any problems with **sudo** and gui apps before. I tried the one with Synaptic (which I just generally launch from my panel) and sure enough **sudo** wouldn't work. Good piece of info to know, for when **sudo** doesn't work, or using it produces unexpected results/behaviour.

---

### Post by aysiu on 2009-04-19
> **OzzyFrank said:**
> I'm starting to see the difference... I just never had any problems with **sudo** and gui apps before. I tried the one with Synaptic (which I just generally launch from my panel) and sure enough **sudo** wouldn't work. Good piece of info to know, for when **sudo** doesn't work, or using it produces unexpected results/behaviour.
It doesn't happen all the time, but it does happen (*sudo firefox* and *sudo kate* I've seen to be problematic--there may be others as well).

It's better to just get people in the habit of doing the proper thing (*gksudo* or *kdesu* for graphical applications) instead of trying to "whitelist" or okay some graphical apps with plain *sudo*.

---

### Post by OzzyFrank on 2009-04-19
Hey, just out of interest, what's with opening Firefox as superuser? I mean I understand opening Gedit and Kate to edit system files, but don't understand why one would do this with a web browser. Obviously there is a reason for it, but it escapes me, so would like some clarification on this too, if possible. Also, regarding Nautilus, any differences? I usually just use **sudo nautilus** and haven't had a problem with it, but would be interested to hear if there is in fact a difference (as the info on Firefox points out, they can both be used, but there _are_ differences, so want to see if any of this applies to Nautilus). Thanks

---

### Post by egalvan on 2009-04-19
One "bad thing" that can happen is loosing ownership of your home directory or files.

This can give the infamous 

*User $HOME/.dmrd file is being ignored*

 error message on boot.

Took me three times to link the sudo/gksudo mis-use... :)

BTW, in this month's *Linux Pro Magazine*,  "Ask Klaus!" column has a short Q/A on this.

---

