---
title: "Lost window frames"
date: 2007-04-18
forum: Desktop Environments
---

### Post by Birion on 2007-04-18
When I logged in to Ubuntu this morning, all my windows lost the frames and the top panel and most of them got stuck over the upper gnome panel.

[[img=http://img216.imageshack.us/img216/7288/obrazovkavn6.th.png]](http://img216.imageshack.us/my.php?image=obrazovkavn6.png)

I can't post any screenshot with the panel covered as my keyboard shortcuts don't work either.

When I try to start window manager settings, it tells me that there is no suitable application for running window manager 'unknown'. :(

I had this problem once already and solved it by reinstalling Ubuntu, but I don't want to do it too often (and especially not before the final version comes out).

---

### Post by nottingham on 2007-04-21
Hi there

I found a post where it says using the following command to get back your window frame:

$ metacity --replace

Obviously, this is the fix to the problem. I am still looking for a real solution. If you come across any good post, pls copy it to here.

---

### Post by rich.bradshaw on 2007-04-22
Have you half installed Beryl?

If so,

sudo apt-get install beryl emerald

beryl-manager

then set beryl-manager to start at boot in System/Pref?/Sessions

You can tell beryl-manager to use metacity or emerald.

Only do it if you have tride to use Beryl.

---

### Post by nottingham on 2007-04-22
I am not using Beryl, just the new released Feisty 7.04 (fresh install). Feisty comes with Compiz as pre-installed package. Over the last 2 days, I tried some actions as follows:

1. Before I knew the command 'metacity --replace', I added a new user and the new user has everything fine.
2. As the new added user, I changed the theme to glossy and modified the color (of winfow frame) from its default blue  to grey. It worked until the next few restarts; the problem arised.
3. I googled the problem and I came across one post mentioning the problem related to compiz. I came back and tried to remove Compiz package using Synaptic package manger and it always forced to remove the Ubuntu-desktop package. But the Ubuntu-desktop is so important according to its description so I did not dare to go any further to avoiding losing the whole GUI.

Personally, I guessed the problem is from modifying the theme so I just use the default Human theme and see if it is true. So far, the problem haven't appeared again. However I do not like the default theme and still wait for a real solution.

---

### Post by bixejo on 2008-02-29
Hi, Biron.

I guess it's "a bit" late for this reply to be helpful to you, but maybe somebody else may also get this problem and may find this thread looking through these forums, just like I did.

I got this same problem too yesterday. This came together with some panel applets missing, including network nm-applet.

It all happened when I tried to make compiz work in my amd64-Ubuntu-7.10 laptop equipped with an ATI Mobility Radeon HD 2600 (which, by the way, I've been still unable to make work). The problem disappeared when I did uninstall the xserver-xgl package.

I do not claim that this is the ultimate solution, but it worked for me. I'm starting to resign to never have desktop effects available.

Regards,

--Bixejo

---

