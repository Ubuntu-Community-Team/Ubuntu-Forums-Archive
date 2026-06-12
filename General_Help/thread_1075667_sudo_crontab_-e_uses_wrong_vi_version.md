---
title: "sudo crontab -e uses wrong vi version"
date: 2009-02-20
forum: General Help
---

### Post by carl.davis on 2009-02-20
Can someone tell me where to change the editor that crontab uses? When I type the following:

```
sudo crontab -e
```

I get:

```
Error detected while processing /usr/share/vim/vimrc:
line   20:
E319: Sorry, the command is not available in this version: syntax on
Press ENTER or type command to continue
```

I know when I initially typed crontab I did not have vim-full installed, so I had to choose vi. I am unable to determine what change needs made.

crontab -e without sudo works fine.

I have tried and verified the following:

```
sudo update-alternatives --config editor

There are 5 alternatives which provide `editor'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/vim.tiny
          2    /bin/ed
          3    /bin/nano
          4    /usr/bin/vim.basic
*+        5    /usr/bin/vim.gnome

Press enter to keep the default[*], or type selection number:
```

```
lrwxrwxrwx 1 root root 18 2009-02-20 11:22 /etc/alternatives/vi -> /usr/bin/vim.gnome

```

```
sudo echo $EDITOR
vim
```

---

### Post by dcstar on 2009-02-20
> **carl.davis said:**
> Can someone tell me where to change the editor that crontab uses? When I type the following:

```
sudo crontab -e
```

I get:

```
Error detected while processing /usr/share/vim/vimrc:
line   20:
E319: Sorry, the command is not available in this version: syntax on
Press ENTER or type command to continue
```

I know when I initially typed crontab I did not have vim-full installed, so I had to choose vi. I am unable to determine what change needs made.
.......
```
sudo echo $**EDITOR**
vim
```

I would suggest you remove that from your root profile, it is overriding the other settings.

---

### Post by lensman3 on 2009-02-20
Set the EDITOR environment variable to your favorite editor.  Use the following:

export EDITOR=/usr/bin/vim

Then to the crontab -e.  The default on my system is /bin/vi for the editor.  When I changed it to vim then escape to shell using :!ps (colon-bang-command), I could see the new shell running.  It is probably a good idea to use the entire path to the editor.  I'm not sure if crontab exports the PATH variable.  That way you control exactly which editor you use.

You could probably change the editor to emacs which I don't know.  <FLAME>Real sysadm's use vi.</FLAME>.

---

### Post by Slim Odds on 2009-02-20
Try this:
```
sudo apt-get install vim
```

Even in Ubuntu there is a difference between vi and vim

Once you install vim, when you typ vi, you'll get vim

---

### Post by kpkeerthi on 2009-05-05
I have the same issue in Ubuntu (GNOME) 9.04. None of the suggestions posted here works. Anyone able to fix this?

---

### Post by geirha on 2009-05-05
Either of these should work.
```
export EDITOR=vim
sudo crontab -e

# or

EDITOR=vim sudo crontab -e
```

EDIT: Err, no wait.
```
sudo EDITOR=vim crontab -e
```

Check if EDITOR or VISUAL variables are getting set to anything in /root/.profile and /root/.bashrc

---

### Post by kpkeerthi on 2009-05-05
There is no EDITOR or VISUAL env variable set in /root/.profile and /root/.bashrc

_**Method-1:**_
/home/<user>/.bashrc has **export EDITOR=/usr/bin/vim**

This works when I do **crontab -e** but not when **sudo crontab -e**

Why? 

_**Method-2:**_
1. Removed EDITOR environment variable from /home/<user>/.bashrc
2. And tried 
```

sudo update-alternatives --config editor

There are 5 alternatives which provide `editor'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/vim.tiny
          2    /bin/ed
          3    /bin/nano
          4    /usr/bin/vim.basic
*+        5    /usr/bin/vim.gnome

```
Again, this works when I do **crontab -e** but not when **sudo crontab -e**. I tried 1, 4 and 5. No dice. Why?

_**Method-3:**_
**sudo EDITOR=vim crontab -e** works. But why should I prefix the command with the environment variable everytime I run it. It should pick the editor as set in Method-1 and Method-2.

---

### Post by cariboo on 2009-05-05
Why not just select nano from the list?

---

### Post by kpkeerthi on 2009-05-05
I need vim as the editor :)

---

### Post by kpkeerthi on 2009-05-06
Reported this as a [bug]("https://bugs.launchpad.net/ubuntu/+source/vim/+bug/372588")

---

### Post by carl.davis on 2009-05-06
What is the Bug #? I would like to watch is progress.

---

### Post by kpkeerthi on 2009-05-06
> **carl.davis said:**
> What is the Bug #? I would like to watch is progress.

I have linked the bug in the last post

---

### Post by sisco311 on 2009-05-06
> **kpkeerthi said:**
> There is no EDITOR or VISUAL env variable set in /root/.profile and /root/.bashrc
...


by default, sudo doesn't preserves all environment variables.
```
sudo -E crontab -e
```
or edit the sudoers file and add *env_keep="EDITOR"* to the Defaults line.

```
man sudo
man sudoers
```

---

### Post by kpkeerthi on 2009-05-06
> **sisco311 said:**
> 
or edit the sudoers file and add *env_keep="EDITOR"* to the Defaults line.
This is probably what I need. Will check that when I get back home. Thanks for the pointer.

---

### Post by kpkeerthi on 2009-05-06
That did it. Here is my /etc/sudoers

```

Defaults    env_reset
Defaults env_keep += "EDITOR"

```

---

### Post by macey on 2009-05-19
> **kpkeerthi said:**
> That did it. Here is my /etc/sudoers

```

Defaults    env_reset
Defaults env_keep += "EDITOR"

```


I have also tried this, doesn't seem to keep over e-boots.
I want to force use to nano editor. 

Regards.

---

### Post by kpkeerthi on 2009-05-19
Do you have EDITOR environment variable already set in ~/.bashrc ?

```

export EDITOR=/usr/bin/nano

```

---

### Post by squibs on 2010-01-10
Old thread but came across this issue today and none of the suggestions had any effect on the editor choice. What worked for me was to use "select-editor" to choose the editor. For more info [see this post]("http://blog.dustinkirkland.com/2008/08/per-user-editor-selection-in-ubuntu.html")

---

### Post by ibuclaw on 2010-01-10
Old thread indeed.

What really works is this:
```
sudo vi /usr/share/vim/vimrc
```
And going to line 20, and change:
```
syntax on
```
to
```

if has("syntax")
  syntax on
endif

```

With that - am closing.

Regards
Iain

---

