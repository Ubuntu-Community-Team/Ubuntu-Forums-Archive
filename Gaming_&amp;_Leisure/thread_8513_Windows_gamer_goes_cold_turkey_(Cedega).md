---
title: "Windows gamer goes cold turkey (Cedega)"
date: 2004-12-18
forum: Gaming &amp; Leisure
---

### Post by Dylanby on 2004-12-18
I built myself a new comp to replace my old one which died two weeks ago. I just swapped out the hard drives into the new system & everything was pretty much good to go (both XP & Ubuntu). Well 2 days ago I decided to upgrade XP to SP2....& it's been nothing but bluescreens since. It seems that only a reinstall of XP will sort it out, & thinking it over I just can't be bothered, which suprises me. So much for my gradual migration (Win=>Linux) plan.

So I used a live-cd to backup data from the XP partitions to a temporary ext3 partition. I have no OS's installed & am currently posting via live-cd. Now on to my questions...

I'm planning my new partition layout & was wondering how much space to give root & home. Does Cedega install games into the home directory? Or is that just its config? Or should I make a separate /usr? I have some games that I'll be installing natively (Doom 3, UT2004, RTCW...) as well.

---

### Post by AndersAA on 2004-12-18
Per default cedega installs games in $HOME/.transgaming, but you can change that (even move the transgaming directory) if you feel like it :)

```

#example:
cd $HOME
sudo mkdir /mnt/storage
sudo chown $USER:$USER /mnt/storage
mv .transgaming /mnt/storage
ln -s /mnt/storage/,transgaming .

```


and I know the feeling, I've seen other people go this way again, play with linux/windows, if windows breaks... it stays broke ;)

---

### Post by Dylanby on 2004-12-18
Thanks for the reply.
I'm a newbie so some of the syntax/lingo is still "greek" to me, but at least I know that the answer is here when I need it (in a day or two).
Thanks again.

---

