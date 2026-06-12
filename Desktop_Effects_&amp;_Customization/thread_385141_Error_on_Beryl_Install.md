---
title: "Error on Beryl Install"
date: 2007-03-15
forum: Desktop Effects &amp; Customization
---

### Post by o0Jerry0o on 2007-03-15
I just upgraded to the beta version of Ubuntu 7.04, I wish to install Beryl so I tried; 
"sudo apt-get install beryl" but my output was;
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package beryl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package beryl has no installation candidate

What is this weird output?

---

### Post by Waappu on 2007-03-15
Hi

Have you add repositorys to your /etc/apt/sources.list  ??

To edit and add repositorys type in terminal ```
gksudo gedit /etc/apt/sources.list
```.
You may want do backup first ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

Here is guides to Beryl for Feisty
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

---

### Post by Neobuntu on 2007-03-15
The bottom line is, you may have gone too far. If you are just testing a SEPARATE install, from your main work systems, then thank you you for contributing. That makes the "released" non-Alpha or after-Beta released systems (eventually) more stable. The maximum stability comes from a release that has been out in the wild; used my many (Just ask Microsoft. LOL. They still have MORE problems).

One can not expect every new add-on and every, everything to work in an Alpha. This is why I say there's stability and then there's stability. First, hey, it doesn't crash. Then real stability is when almost any thing you want to throw at it (real world benefits), just works.

But you know that, right? I'm sure you'll get it working anyway.

I just got Beryl working with Kubuntu Edgy and a Nvidia legacy Geforce2 with normal nvidia-legacy drivers auto installed. After Beryl install, I just had to add a few recommended changes  to my "xorg.conf ". I though it was fluff. It adds extra user functionality (not just wiggley) out of the gate. Cool. looks like I'll have to turn it off to run direct 3D type games ([TORCS]("http://www.youtube.com/watch?v=un1zKktVm3s")) though.

---

### Post by russo.mic on 2007-03-18
Went too far?  He just didn't have the sources updated...

---

### Post by Neobuntu on 2007-03-19
Maybe not him at all. I am just trying to inform the casual reader and/or new user that one has to use self control and not go to far when picking a newer distribution CD. The newest is not done. Do not just download (or dist-upgrade to) the newest CD or version that you can get. That is,  unless you are just testing. That's all. 

Keep testing separate from you main system. Don't upgrade from a stable system to testing.

...and do not expect perfect stability from a new release out of testing. Stable then, is the goal. The reality is some time after release (but not ridicules like Windows) .

Don't forget, testers make the releases better, and sooner.

---

