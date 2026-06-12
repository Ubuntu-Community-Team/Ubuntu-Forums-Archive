---
title: "PATH environment variable issue"
date: 2009-03-03
forum: General Help
---

### Post by Geobot on 2009-03-03
So I installed a few games a couple days ago, and they work fine, except for the fact that I had to change the targets for the launchers in the menu, because apparently my PATH isn't working correctly.

It seems to work for anything except the /usr/games directory. Any time I try to run a program from there, I get an error message saying (paraphrasing) "pingus was found at /usr/games/pingus but cannot be run because usr/games was not found in your PATH environment variable."

Now, I assume it's referring to /etc/environment, which was the only place I found a path setting, but the thing is, /usr/games IS there, and it always has been. I've never changed this file, because all I needed was there, and up until a couple days ago, programs ran fine from the directory.

Nevertheless, I deleted /usr/games, saved the file, then readded it and saved again, thinking maybe it would update itself, but to no avail.

Any ideas? I mean, I can always just alter the launcher targets for every game I install, but I'd really like to know why my PATH doesn't seem to be reading right anymore.

---

### Post by ajgreeny on 2009-03-03
What is the output in terminal of ```
echo $PATH
```  Perhaps something is wrong with your default PATH environment.  On my machine I get:-
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by Slim Odds on 2009-03-03
> **Geobot said:**
> Now, I assume it's referring to /etc/environment, which was the only place I found a path setting, but the thing is, /usr/games IS there, and it always has been. I've never changed this file, because all I needed was there, and up until a couple days ago, programs ran fine from the directory.

I would avoid making assumptions.... ;)
especially with computer stuff..

How did you install the games?

P.S. Show us your path```
echo $PATH
```

---

### Post by Geobot on 2009-03-03
ok, well, here's the interesting part:

$PATH as user:
./:/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin

$PATH as root:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

So I was -half- right, the /etc/environment DOES seem to set the $PATH for root, just not for the current user. And if I try to run the programs as root, they work fine, since the PATH for root is good.

After further digging, I found a .profile file in my home folder that -looks- like it should set the user's path. an excerpt here so you can see what I mean:

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

Now, what I make of that is that it should set PATH to the /home/geobot/bin folder and follow it with what is currently in PATH when the user logs in, which should be the full path list found in /etc/environment.

In my case, it seems to be getting a whole other PATH from some other script that I can't find, and it completely ignores the root's PATH, instead of just adding to it. If I could find the script responsible, I could change it, but it's eluding me.

---

### Post by makisupa123 on 2009-03-03
```
gedit ~/.bashrc
```

--Mak

---

### Post by bodhi.zazen on 2009-03-03
> **Geobot said:**
> # set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

My only comment is , IMO, ~/bin should be last on the path, especially for an administrative account.

```
# Add ~/bin to $PATH (if it exists)
# IMO ~/bin should be LAST on the PATH :)
if [ -d "$HOME/bin" ]; then
  PATH="**$PATH:$HOME/bin**"
fi
```

---

### Post by Slim Odds on 2009-03-03
> **Geobot said:**
> In my case, it seems to be getting a whole other PATH from some other script that I can't find, and it completely ignores the root's PATH, instead of just adding to it. If I could find the script responsible, I could change it, but it's eluding me.

Well... it does seem to be unique to you.... because I have a path just like the one in /etc/environment (as does AJGreeny).

---

### Post by Slim Odds on 2009-03-03
> **bodhi.zazen said:**
> My only comment is , IMO, ~/bin should be last on the path, especially for an administrative account.

```
# Add ~/bin to $PATH (if it exists)
# IMO ~/bin should be LAST on the PATH :)
if [ -d "$HOME/bin" ]; then
  PATH="**$PATH:$HOME/bin**"
fi
```

The "default profile" in Ubuntu does this for non-root users.

---

### Post by bodhi.zazen on 2009-03-03
> **Slim Odds said:**
> The "default profile" in Ubuntu does this for not-root users.

I understand, but not all OS do this ;)

---

### Post by Geobot on 2009-03-04
> **makisupa123 said:**
> ```
gedit ~/.bashrc
```

--Mak

Thank you for this. My .bashrc didn't have a PATH entry, so I added one, and it works fine now.

---

