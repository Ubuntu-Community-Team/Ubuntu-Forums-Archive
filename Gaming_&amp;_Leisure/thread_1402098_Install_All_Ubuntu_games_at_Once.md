---
title: "Install All Ubuntu games at Once?"
date: 2010-02-08
forum: Gaming &amp; Leisure
---

### Post by Zornox on 2010-02-08
Hello, I'm Zornox and I recently Installed Ubuntu 9.10 on my hard drive. I'm wondering if there is a command for Ubuntu that you can Put in the Terminal to install all the games at once. 

I know you can do with Fedora because I'm taking a "intro to linux class with Fedora." and my Instructor Insisted that we did the command and Even though it took a while. It worked and installed all the games.

So Yeah. Is there a command like that for Ubuntu?

---

### Post by hikaricore on 2010-02-08
You could just open up synaptic package manager and select all the packages listed as games.
I can't for the life of me figure out why you'd want to do this however unless you want every single linux game in the repos installed for some crazy reason.

You may also want to checkout playdeb.net they have a nice selection of up to date titles.

---

### Post by Zornox on 2010-02-08
I just want to install every game on the Terminal Like I did using Fedora that was all. Thats really the only reason I have that I want to install all the Ubuntu games.

---

### Post by Simian Man on 2010-02-08
The command used in Fedora was probably
```
yum groupinstall "Games and Entertainment"
```

If I remember rightly, that wouldn't install ALL the games in the Fedora repos, it would install all of the ones in the games group which come with the games spin.  You can see all of those games [here]("http://fedoraproject.org/wiki/Games_Spin").  They are probably all in the Ubuntu repos, though I don't think Ubuntu has anything like Fedora's package group of games.

---

### Post by Zornox on 2010-02-08
> **Simian Man said:**
> The command used in Fedora was probably
```
yum groupinstall "Games and Entertainment"
```

If I remember rightly, that wouldn't install ALL the games in the Fedora repos, it would install all of the ones in the games group which come with the games spin.  You can see all of those games [here]("http://fedoraproject.org/wiki/Games_Spin").  They are probably all in the Ubuntu repos, though I don't think Ubuntu has anything like Fedora's package group of games.

That wasn't the command

This is the command that I used. 

```
yum install ` yum groupinfo games | grep'^   ' | grep -v maniadriver`
```

---

### Post by hikaricore on 2010-02-08
It would probably really just be easier to do it the way I mentioned.
Unless you have to do this for like 100 systems there's no reason to jump through hoops to accomplish this.

---

### Post by ingramproductions on 2012-07-04
Here is how to install over 200 of the best games from the Ubuntu repositories in 1 command:

[http://itswapshop.com/tutorial/how-install-200-free-and-open-source-games-one-command-ubuntu-1204-1110-1104-1004]("http://itswapshop.com/tutorial/how-install-200-free-and-open-source-games-one-command-ubuntu-1204-1110-1104-1004")

It's not "all" the games, but it's definitely all the ones worth playing.

---

### Post by lrcaballero on 2012-07-04
sudo apt-get install game1 game 2 game 3 and so on....

---

### Post by overdrank on 2012-07-04
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

