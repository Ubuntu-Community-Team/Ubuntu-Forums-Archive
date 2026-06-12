---
title: "Can't edit a file!"
date: 2009-05-27
forum: General Help
---

### Post by Boomer38 on 2009-05-27
I'm trying to get Thinkfinger to work on my Dell M1330 and the instructions are telling me to add a couple sources to /etc/apt/source.list but it won't let me save this file once I do it.  It's a root file and I'm logged in as a user.  How do I access this file as the root or log in as the root user to edit this file?  UGH!

---

### Post by Cheesemill on 2009-05-27
Hit ALT+F2 and type in
```
gksudo gedit /etc/apt/sources.list
```

Cheesemill

---

### Post by drs305 on 2009-05-27
You must temporarily gain root privileges:
```

gksudo gedit /etc/apt/sources.list

```

You will be asked for a password. Type your password, but you won't see it. Press ENTER once you have typed it in.

---

### Post by gamblor01 on 2009-05-27
You need to prefix the command with **sudo** which will temporarily grant you root access while you run a command.  In your particular case, the following command should do the trick:

```

sudo gedit /etc/apt/sources.list

```

---

### Post by Yellow Pasque on 2009-05-27
```
gksudo gedit /etc/apt/sources.list
```

Note that it's generally safer to use System -> Administration -> Software Sources to modify software sources.

---

### Post by Cheesemill on 2009-05-27
> **gamblor01 said:**
> You need to prefix the command with **sudo** which will temporarily grant you root access while you run a command.  In your particular case, the following command should do the trick:

```

sudo gedit /etc/apt/sources.list

```

You really shouldn't do this, you should use gksudo instead.
See here for more info:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Cheesemill

---

### Post by Boomer38 on 2009-05-27
> **Temüjin said:**
> ```
gksudo gedit /etc/apt/sources.list
```

Note that it's generally safer to use System -> Administration -> Software Sources to modify software sources.

So I should add the sources there instead of editing this file?  I'd rather do it the right way...safe way, right?

---

### Post by drs305 on 2009-05-27
> **Boomer38 said:**
> So I should add the sources there instead of editing this file?  I'd rather do it the right way...safe way, right?

You can take a look at this ubuntu wiki link on Repositories for ways to update the sources.list file:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

You can mess up the sources.list via the gui interface just as you can from editing the file directly. The above link will give you the format on how to add a repository via the gui if you choose or prefer to do it that way. If you mess up either way, you won't damage your system - you just won't be able to update your packages until you fix it.  ;-)

---

### Post by sandy8925 on 2009-05-27
Doing it through the gui isn't exactly safe.....it's just the more user friendly way.
As he said open up software sources and there's a tab where you click on add source. Then just copy paste the lines you are supposed to add. They should start with the word deb

---

