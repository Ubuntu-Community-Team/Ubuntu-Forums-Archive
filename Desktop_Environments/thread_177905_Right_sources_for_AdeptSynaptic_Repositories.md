---
title: "Right sources for Adept/Synaptic Repositories?"
date: 2006-05-17
forum: Desktop Environments
---

### Post by Delphi123 on 2006-05-17
Dear friends:

As a newbie, may I ask what are your recommended official, legitimate (K)Ubuntu sources to add to my list of sources.list in apt/Adept and Synaptic? I see that the current list of applications in my new install is barely over 4,000, yet I read somwhere that Ubuntu has over 16,000 applications in their database. I'd be especially interested in multimedia (I already know where to find Mplayer), Java, RealPlayer, video, etc.

Thank you all so very much.

Benjamin

---

### Post by Sutekh on 2006-05-17
Your current sources (the default ones) do not have the **universe** and **multiverse** repositories enabled.

The universe and multiverse repositories contain thousands of extra packages.  Neither repository are officially supported by Ubuntu, this is usually due to non-free licences used by the packages.  Note this doesn't mean they are illegal, just not free in the truest sense of the word.

Mplayer, Java, RealPlayer, MP3, DVD and related packages are invariably found in the universe and multiverse repositories, because they have software licences that are incompatible with the Ubuntu philosophy.  Note some of these packages I mentioned could be illegal (MP3/DVD?), but IANAL (I am not a lawyer) so don't take my word for it.

Be aware of these issues, but don't be put off, enabling the universe repository is one of the first things I do when I install Ubuntu.

It's very easy to do this.


Start by backing up your current sources
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` Then edit it with your preferred editor
```
sudo nano /etc/apt/sources.list
``` When the editor opens you need to find these lines
```

# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe

...

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
``` And uncomment them - remove the # signs.  This enables the universe repository.  To enable the multiverse repository, add multiverse to the end of these lines.

It would look something like this
```

deb http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
deb-src http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
 
...

deb http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
deb-src http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
``` If you save the file (Ctrl +O using nano) and exit (Ctrl + X) you can then update the repositories with
```
sudo apt-get update
``` Then you are set.

If you'd prefer a graphical method to doing this, try the [Ubuntu Wiki - Adding Repositories HOWTO]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by linuxa on 2006-05-17
Just to add to the very comprehensive post by **Sutekh**, if you setup your network during the installation phase. 

(K)ubuntu should have picked the best sources for you depending on your geographical location. i.e. you should get the US servers if that's where you are (or where ever it is that you live). So theoretically, other than enabling the universe, multiverse and other repository that you might need which are commented out in source.list, you should by default get the best speed when downloading the packages off the server. In other words not much tweaking is needed unless a server is down...

---

### Post by Sutekh on 2006-05-17
That's a good point.  

I actually removed the **au.** from the repositories I posted above, as they are my local repositories.  I haven't tried any sort of tests, but apt-get runs *very*  fast with the local ones.  Sometimes there are problems with the local ones and removing the local part (au. us. etc) is required, but not often.

---

### Post by Delphi123 on 2006-05-17
Dear Sutekh and friends:

Thanks a million for a great explanation and illustration. Will do just that.

Benjamin

---

### Post by kko1 on 2006-05-17
To clarify a bit further on the differences between main & universe plus restricted & multiverse, you can refer to this page: [http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components) .

kko

---

### Post by Sutekh on 2006-05-17
[quote=Delphi123]Dear Sutekh and friends:

Thanks a million for a great explanation and illustration. Will do just that.

Benjamin[/quote]
Your welcome, hope it helpsyou out.  Enjoy all that Ubuntu has to offer!
 
[quote=kko1]To clarify a bit further on the differences between main & universe plus restricted & multiverse, you can refer to this page: [http://www.ubuntu.com/ubuntu/components]("http://www.ubuntu.com/ubuntu/components") .

kko[/quote]
Thanks kko, I knew there was a link that explained the universe/multiverse situation, I just couldn't find it.

---

### Post by link141 on 2006-05-17
Just one thing before you decide if you want to enable the universe repositories, when your in a package manager and you search for a specific package with the universe repositories enabled, it takes much, much, longer to search for a package- not that it should affect your decision.  Just if you've installed a new system or some other case where you need to install a bunch of your preferred applications, you shouldn't enable them right away.  Hope this advise helps :).

---

### Post by linuxa on 2006-05-18
[QUOTE=Sutekh]That's a good point.  

I actually removed the **au.** from the repositories I posted above, as they are my local repositories.  I haven't tried any sort of tests, but apt-get runs *very*  fast with the local ones.  Sometimes there are problems with the local ones and removing the local part (au. us. etc) is required, but not often.[/QUOTE]

Interesting enough, I've found that apt-get is faster than adept when I download a package. Not sure if that's because some resource is allocated to redrawing the GUI or whatever...

Cheers **kko**. The link provided some really good info.

---

