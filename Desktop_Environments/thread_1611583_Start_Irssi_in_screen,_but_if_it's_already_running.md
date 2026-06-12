---
title: "Start Irssi in screen, but if it's already running (detach?) and attach to it?"
date: 2010-11-02
forum: Desktop Environments
---

### Post by Dáire Fagan on 2010-11-02
Sometimes I start Irssi when I'm in front of my Ubuntu desktop at home, but just as often I SSH home from work and start Irssi.

I was looking for a command I could put into Gnome terminal's *Edit >> Profiles >> Edit >> Title and Command >> Run a custom command instead of my shell* that when run from home through an Irssi launcher in my application's menu, would check to see if there's a screen already running Irssi that it can (detach from first? and then)  attach to, and if there's none already running start a new one in screen.

So far I have been recommended: 

```
screen -S irssi -xR irssi
```and

```
screen -RaAd irssi irssi
```Can you tell me which is better and why? And also, is there a way to not just put that command in my gnome terminal, but also make it what happens when I enter the command irssi? That way when I SSH home I just have to type irssi whether or not it's already running in screen.

---

