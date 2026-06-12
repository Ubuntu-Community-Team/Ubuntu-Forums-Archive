---
title: "partition questions"
date: 2009-04-08
forum: General Help
---

### Post by tabarnackle on 2009-04-08
hey, im just learning linux/ubuntu (and having a blast learning it) but when i open places>computer all i see is my cd/dvd drive and what i believe to be my hardrive named "filesystem" 

-is filesystem the only partition i have? or should there be a few? can someone explain this more for me? and is it only doable by reinstalling. i do remember on the install it had two listed and one of them was swap i jsut have no clue.... about partitioning. learn me :popcorn:
-dave

---

### Post by _Purple_ on 2009-04-08
You can install gparted to have an idea of your hard disk partitions. Using gparted, you can even make partitions without reinstalling again. Your swap partition is still there.

---

### Post by tabarnackle on 2009-04-08
much thanks, is it hard to install? i tried to install flash last night to watch some videos without success lol

^^^ yea. im on the site, and i have no sweet clue what im doing.

---

### Post by _Purple_ on 2009-04-08
You can install it by typing in the terminal:
```
sudo apt-get install gparted
```

Then you can run it by typing:
```
sudo gparted
```

---

### Post by tabarnackle on 2009-04-08
ok sweet! the buddy who first showed me ubuntu showed me the simplicty of that i just dont know how to open "terminal" im guessing its a fairly common thing ill be using from herein eh'? 
BTW: i found it in the add/remove app menu :D so simple.... im still blown away lol

---

### Post by _Purple_ on 2009-04-08
Application> Accessories > Terminal
For command line interface, you will need the terminal.

You can also install packages using Synaptic Package Manager. 
System> Administration > Synaptic Package Manager 

There you can select any package and install.

---

### Post by JECHO on 2009-04-08
> **tabarnackle said:**
> much thanks, is it hard to install? i tried to install flash last night to watch some videos without success lol

^^^ yea. im on the site, and i have no sweet clue what im doing.

glad to see youre getting into linux... PM me and I would be more than happy to help you out in detail!

---

### Post by Elfy on 2009-04-09
> **_Purple_ said:**
> ```
sudo gparted
```

Best to use gksudo or kdesu for gui apps

```
gksudo gparted
```

---

### Post by tollboy on 2009-04-09
i know many of the beginners dont want to read it...
but still you can refer this .
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by mb_webguy on 2009-04-09
> **tabarnackle said:**
> much thanks, is it hard to install? i tried to install flash last night to watch some videos without success lol

^^^ yea. im on the site, and i have no sweet clue what im doing.

To install Flash, open the terminal (Applications->Accessories->Terminal), then copy and paste the following commands into the terminal to install Flash (and a lot of other really nice things).```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

sudo apt-get install ubuntu-restricted-extras libdvdcss2 non-free-codecs
```The first set of commands adds the Medibuntu repository to your Software Sources (which you need to get the libdvdcss2 and non-free-codecs packages).  It's fairly scary looking only because it's written to work regardless of the specific release of Ubuntu you're using.  The commands to add the Medibuntu repository if I knew what version you were using would be much simpler.

The ubuntu-restricted-extras package contains the Flash plugin, Java, mp3 support, and basic support for playing DVDs.  The libdvdcss2 package adds support for playing encrypted DVDs (i.e. many commercial movies).  The non-free-codecs package adds support for a [huge list]("http://www2.mplayerhq.hu/DOCS/codecs-status.html") of proprietary audio and video formats.

If *all* you want is Flash, you could just install the  "Macromedia Flash plugin" using Add/Remove, or the flashplugin-nonfree package using Synaptic (System->Administration->Synaptic Package Manager), or the command "sudo apt-get install flashplugin-nonfree" in the terminal.

You'll see a lot of people posting commands to run in the terminal.  In almost every case, there is a way of doing the same thing without using the terminal, but it's easier to tell someone to enter a command or two than it is to say "click here, then here, then here, then here" to do the same thing.  Also, since numerous desktop environments are available for Ubuntu, terminal commands are the one way to make sure that the help you're giving will apply to everyone.

Oh, and btw... welcome to Ubuntu!

---

