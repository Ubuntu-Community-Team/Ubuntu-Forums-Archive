---
title: "where's multi-gnome-terminal"
date: 2008-05-17
forum: Desktop Environments
---

### Post by grizzlysmit on 2008-05-17
ok I'm trying to get back multi-gnome-terminal as it seems to have been pulled from ubuntu 8.04 LTS and I find it cannot run because it cannot find libglade-gnome.so.0 which also apears to have been pulled will it be brought back later??? please gnome term is no good it names all the tabs the same, and even if u rename them all they loose it all on startup next time (I've tried storing it in session) ](*,)

---

### Post by macaholic on 2008-05-17
How did you install gnome-multi-terminal?

---

### Post by yoda2031 on 2008-05-17
A simple apt-cache search yielded:

terminator - Multiple GNOME terminals in one window

I suggest trying that one out (sudo apt-get install terminator).

---

### Post by m83 on 2008-05-17
Why use gnome-multi-terminal when gnome-terminal has tabs?

---

### Post by grizzlysmit on 2008-05-23
> **macaholic said:**
> How did you install gnome-multi-terminal?

I got a binary installer of their site, it's not as good as using apt-get/synaptic of course.

---

### Post by grizzlysmit on 2008-05-23
> **m83 said:**
> Why use gnome-multi-terminal when gnome-terminal has tabs?

the name of all the tabs in gnome term is just the prompt which means you cannot tell most of them apart, plus it has lots of other features like splitting the tab up to have multiple terminals in one tab i.e.
**************************************
*TTTTTTTTT*TTTTTTTTT*TTTTTTTT*
*TTTTTTTTT*TTTTTTTTT*TTTTTTTT*
*TTTTTTTTT*TTTTTTTTT*TTTTTTTT*
*TTTTTTTTT*TTTTTTTTT*TTTTTTTT*
***************************************
*TTTTTTTTTTTTT*TTTTTTTTTTTTTT*
*TTTTTTTTTTTTT*TTTTTTTTTTTTTT*
*TTTTTTTTTTTTT*TTTTTTTTTTTTTT*
*TTTTTTTTTTTTT*TTTTTTTTTTTTTT*
***************************************
and more unfortunately u cannot save the above to the session yet 
my pet peave

---

### Post by grizzlysmit on 2008-05-23
> **yoda2031 said:**
> A simple apt-cache search yielded:

terminator - Multiple GNOME terminals in one window

I suggest trying that one out (sudo apt-get install terminator).

I've just tried installing that but it lacks tabs, multi-gnome-terminal has the same capability but it's like a note book of terminator's plus it has some other features

---

### Post by eentonig on 2008-05-23
Why not use screen?

---

### Post by jcbodnar on 2008-05-28
> **grizzlysmit said:**
> I got a binary installer of their site, it's not as good as using apt-get/synaptic of course.

I tried the binary installer but it still need libglade-gnome0. I tried installing the gutsy verison of libglade-gnome0 but couldn't get all of its dependencies to install.

Were you able to actually run mgt with the version from the binary installer?

As for why I use mgt, it's because I can set up a tab for each host I want to log into (about 10 of them) and bind some keystrokes to that tab. I then can hit Ctl-Alt-****-H to open a tab that automatically ssh's me to my home machine and sets the tab title accordingly. No other terminal emulator I've used allows me to do this.

---

### Post by joshualivesay on 2011-05-25
TOPIC:  Where's multi-gnome-terminal?

     Answers so far in this post.  
                "How did you install multi-gnome-terminal?"
                "Do an apt-cache search"
                "Why do you want to install that?"
                "Why not use screen?" 
        
      Best Answer -> "Install from source"... still unacceptable for modern distro.
            
However...  What 3 years later, what is the answer?  Where is multi-gnome-terminal?

---

### Post by O.elgedawy on 2013-02-05
you can use multixterm instead of gnome-terminal 

# apt-get install expect-dev

---

### Post by oldos2er on 2013-02-05
Old thread closed, please don't bump old threads.

---

