---
title: "sudo gedit issue after upgrading to 18.04 from 16.04?"
date: 2018-04-29
forum: Desktop Environments
---

### Post by daition on 2018-04-29
As shown in the picture attached, when issuing "sudo gedit" in terminal, the  content of gedit is just a snapshot of my desktop instead of a new  document. Launching gedit without sudo is good.

I also tried with pluma. The behaviors are the same as I describe above.

Anyone can help?

---

### Post by joegry on 2018-04-30
Can you try sudo gedit ~/test.txt to see if it will open a new file correctly when specifying a filename?

---

### Post by Xian on 2018-04-30
For more detailed info read:

[http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html](http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html)


The basic steps are to swtich from gksu to pkexec:

```
[COLOR=#000000][FONT=&amp]sudo apt-get install nautilus-admin[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]wget https://raw.githubusercontent.com/hotice/webupd8/master/org.gnome.gedit.policy -O /tmp/org.gnome.gedit.policy[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]sudo cp /tmp/org.gnome.gedit.policy /usr/share/polkit-1/actions/[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]pkexec gedit[/FONT][/COLOR]
```

---

### Post by daition on 2018-04-30
Specifying a filename doesn't change anything. The behavior is the same.

---

### Post by daition on 2018-04-30
> **Xian said:**
> For more detailed info read:

[http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html](http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html)


The basic steps are to swtich from gksu to pkexec:

```
[COLOR=#000000][FONT=&amp]sudo apt-get install nautilus-admin[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]wget https://raw.githubusercontent.com/hotice/webupd8/master/org.gnome.gedit.policy -O /tmp/org.gnome.gedit.policy[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]sudo cp /tmp/org.gnome.gedit.policy /usr/share/polkit-1/actions/[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]pkexec gedit[/FONT][/COLOR]
```

Thank you for your reply.

I tried the steps above. But it doesn't work. The problem remains...

---

### Post by Xian on 2018-04-30
Well ... there's a fly in the ointment somewhere. 

When you execute the command:

```
pkexec gedit
```

Does a GUI dialogue box appear asking for your sudo password?

If it does and still gedit won't open what is the terminal output?

[IMG]https://i.imgur.com/KsJC7vzm.png[/IMG]

---

### Post by wildmanne39 on 2018-04-30
Please try:
```
sudo -H gedit
```
There have been changes in 18.04, gksu was removed, here is a link that will help.

You should never have run a GUI application with sudo in previous versions of ubuntu either because you run the risk of root taking ownership.

[https://ubuntuforums.org/showthread.php?t=2389656](https://ubuntuforums.org/showthread.php?t=2389656)

---

### Post by monkeybrain20122 on 2018-04-30
How about this

gedit admin:// ...

... is the FULL PATH to your file to be edited. 

In other words instead of using sudo or gksudo , prepend the full path with admin:// 

e.g if you want to edit your sources list

instead of 
```
gksudo gedit  /etc/apt/sources.list
```

now 

```
gedit admin:///etc/apt/sources.list
```


Apparently using relative path doesn't work. I.e, before you could do
```
cd /etc/apt
gksudo gedit sources.list

```
but  neither of the followings work

```
cd /etc/apt
gedit admin://sources.list
```


```
cd /etc/apt
gedit admin://./sources.list
```

---

### Post by monkeybrain20122 on 2018-04-30
> **wildmanne39 said:**
> Please try:
```
sudo -H gedit
```
There have been changes in 18.04, gksu was removed, here is a link that will help.

You should never have run a GUI application with sudo in previous versions of ubuntu either because you run the risk of root taking ownership.

[https://ubuntuforums.org/showthread.php?t=2389656](https://ubuntuforums.org/showthread.php?t=2389656)

This appears to  be the cleanest way. thanks!

---

### Post by monkeybrain20122 on 2018-04-30
> **Xian said:**
> For more detailed info read:

[http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html](http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html)


The basic steps are to swtich from gksu to pkexec:

```
[COLOR=#000000][FONT=&amp]sudo apt-get install nautilus-admin[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]wget https://raw.githubusercontent.com/hotice/webupd8/master/org.gnome.gedit.policy -O /tmp/org.gnome.gedit.policy[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]sudo cp /tmp/org.gnome.gedit.policy /usr/share/polkit-1/actions/[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]pkexec gedit[/FONT][/COLOR]
```


That sounds crazy to expect users to create or download policy files from third parties just to get a basic functionality, if this is the way to run pkexec it just encourages people to abuse sudo.

---

### Post by wildmanne39 on 2018-04-30
I think it is a lot to go through and sudo -H is safe so that is what I will stick with, here is an article by the developer that removed gksu.

[https://jeremy.bicha.net/2018/04/18/gksu-removed-from-ubuntu/](https://jeremy.bicha.net/2018/04/18/gksu-removed-from-ubuntu/)

Your welcome!

---

### Post by again? on 2018-04-30
For a right click menu item, the nautilus-admin package has been updated to use "admin://"
```
sudo apt install nautilus-admin
```

---

