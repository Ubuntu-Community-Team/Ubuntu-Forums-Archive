---
title: "easier softer linux ?"
date: 2011-04-15
forum: Desktop Environments
---

### Post by weedeater64 on 2011-04-15
Isn't that one of the primary goals of ubuntu ?

sudo apt-get install ratpoison
   blablalba
   blablabla
    bllblabllaa

restart >> login >>> no ratpoison

[SIZE=4][U][I][B] [COLOR=Red]FAIL!!



[/COLOR][/B][/I][/U][/SIZE]

---

### Post by 3Miro on 2011-04-15
> **weedeater64 said:**
> 
   blablalba
   blablabla
    bllblabllaa


That is where the real fail is. You probably got important information here, but you didn't bother to read.

Try starting from the terminal:
```
ratpoison
```
if it cannot find it, then try again:
```
sudo apt-get install ratpoison
```

Once you get the "blah" messages, please post them here wrapped in code tags.

---

### Post by tgm4883 on 2011-04-15
> **weedeater64 said:**
> Isn't that one of the primary goals of ubuntu ?

sudo apt-get install ratpoison
   blablalba
   blablabla
    bllblabllaa

restart >> login >>> no ratpoison

[SIZE=4][U][I][B] [COLOR=Red]FAIL!!



[/COLOR][/B][/I][/U][/SIZE]

In my experience, any attempt to make any system idiot proof will only challenge God to make a better idiot.

Touché God, Touché.

---

### Post by Copper Bezel on 2011-04-15
That's a little unnecessary. 

weedeater64, you need to create the Ratpoison login session manually. There's nothing soft or easy about Ratpoison, regardless of the linux distribution it runs on.

---

### Post by deconstrained on 2011-04-16
> **tgm4883 said:**
> In my experience, any attempt to make any system idiot proof will only challenge God to make a better idiot.
I am so plagiarizing the hell out of this quote the next time I get into a usability argument with someone who hates on Linux.

---

### Post by stinkeye on 2011-04-16
Ok, you guys took offence at someone having a bit of a rant but where's the help.
I just installed ratpoison and it doesn't add an entry to the session menu.
 Run ```
gksudo gedit /usr/share/xsessions/ratpoison.desktop
```

And paste this into the file and save.
```
[Desktop Entry]
 Encoding=UTF-8
 Name=Ratpoison
 Comment=Start Ratpoison as your window manager
 Exec=ratpoison
 Icon=
 Type=Application
```

Should now be available on next reboot/logout.

---

### Post by weedeater64 on 2011-04-16
[3Miro]("http://ubuntuforums.org/member.php?u=777773"), get a clue please.

[Copper Bezel]("http://ubuntuforums.org/member.php?u=1228996") , did I say there was ? I commented on Ubuntu's apparent goal of appealing to linux noobs, and it total and utter failure in this case. This task is quite simple with debian, apt-get install ratpoison, and guess what...  entry made in menu, as it should be. While I haven't any experience with other distro's , I suspect that's the norm. 

BTW, ratpoison is plenty easy, and soft. 
Cntrl + t , ?
if you are confused.

[stinkeye]("http://ubuntuforums.org/member.php?u=684510"), thank you.

---

