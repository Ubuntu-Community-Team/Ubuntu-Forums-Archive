---
title: "PyChess unexpectedly crashes just before I win a game."
date: 2013-05-19
forum: Gaming &amp; Leisure
---

### Post by aaditmshah on 2013-05-19
[SIZE=3]PyChess is evil. Pure evil. When I'm playing a game versus a human opponent and I have a checkmate in the next move PyChess unexpectedly crashes the moment I play that move. It takes a grand total of one clock cycle to realize that I've won and hang up so that I can't get the reward or the bragging rights for beating my opponent. In addition since it disconnects me from FICS I lose the game and some elo depending on whether I played a rated or an unrated game. The first time this happened I didn't think much of it, but it has been happening so frequently that I don't think it's just a coincidence anymore. PyChess is a bitch. I'm so ****ed that I don't mind writing my own FICS client from scratch. Is there any other good FICS client out there? Please don't mention xboard or Raptor. I've already tried them both.[/SIZE]

---

### Post by sudodus on 2013-05-19
Are you sure it's not your human opponent who presses ctrl c or something else to kill the process ;-)

I mean, I could understand if you played against the computer, but why would PyChess favour your opponent?

Did you try ***glchess***?

---

### Post by aaditmshah on 2013-05-19
[SIZE=3][/SIZE]I'm playing versus a human opponent online. I doubt most of my opponents have the skill to gain shell-level access to my computer. PyChess is a bitch. Perhaps the developers intended this behavior. Perhaps they wrote a snippet of code that crashes the application the moment you checkmate your opponent based on the probability of a random variable. What I know is that PyChess is discriminating and favors my opponent. I'll try glchess. Thank you. :)

---

### Post by R33D3M33R on 2013-05-20
If it happens everytime, it could also be because it can't do something: play a sound, write moves to a file, display a box you won or something. I would recommend that you run the game through the terminal and see what is the output when it crashes.

---

### Post by gbtami on 2013-06-23
> **aaditmshah said:**
> [SIZE=3]PyChess is evil. Pure evil. When I'm playing a game versus a human opponent and I have a checkmate in the next move PyChess unexpectedly crashes the moment I play that move. It takes a grand total of one clock cycle to realize that I've won and hang up so that I can't get the reward or the bragging rights for beating my opponent. In addition since it disconnects me from FICS I lose the game and some elo depending on whether I played a rated or an unrated game. The first time this happened I didn't think much of it, but it has been happening so frequently that I don't think it's just a coincidence anymore. PyChess is a bitch. I'm so ****ed that I don't mind writing my own FICS client from scratch. Is there any other good FICS client out there? Please don't mention xboard or Raptor. I've already tried them both.[/SIZE]

Several bugs was fixed in our latest releases. Try 0.12beta2 please!
 [http://pychess.googlecode.com/files/pychess_0.12beta2-1_all.deb](http://pychess.googlecode.com/files/pychess_0.12beta2-1_all.deb)

p.s.: Use our issue tracker to report bugs, please, please, please!
[http://code.google.com/p/pychess/issues/list](http://code.google.com/p/pychess/issues/list)

---

