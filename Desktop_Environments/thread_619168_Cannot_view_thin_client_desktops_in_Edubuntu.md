---
title: "Cannot view thin client desktops in Edubuntu"
date: 2007-11-21
forum: Desktop Environments
---

### Post by Dzenhax on 2007-11-21
I previously posted this in the networking forum but had no help.  I'm thinking I posted it to the wrong place so am trying here.

I've been working with edubuntu trying to get the Thin Client Manager to work. There are a dozen explanations on this spread throughout the web and it seems each one leaves a small but important detail out.

The most useful one was here: [https://wiki.edubuntu.org/InstallX11VncOnLtspClients](https://wiki.edubuntu.org/InstallX11VncOnLtspClients) *Edit: This was taken down the day after I wrote this. Do a search on google and see the cached page.*

However it barely mentioned updating the apt sources.list which should have been part of the text boxes. It's also worth mentioning that in the chroot pico does not work, so have a vi command list ready if you are not familiar with it.

The second thing is that your /etc/resolf.conf file needs to match that of your server. I just copied and pasted mine.

My problem is this one. My thin client connects to the server and boots up and works fine. In the Thin Client Manager I can see the client, send messages to it, blank and unblank the screen, execute commands on it and end processes. However when I try to view the screen of the client I can't.

Following the above instructions I have installed the x11vnc package in the chroot and updated the client with ltsp-update-sshkeys && ltsp-update-image.  I can connect with a vnc viewer outside of Thin Client Manager, but TCM still shows no server on the thin client.

The screen viewer shows the correct user and IP address, but has not connected in bold print. At the bottom it has "Unavailable" in red and "Install x11vnc on the client", which I already have.

I have tried running x11vnc with sudo from the client and it seems to start up. I have also tried using the execute button to start it from TCM. No luck.

One more thing, though not important yet, it will be later. When I click Share Screen at the top of the GUI an error message pops up on the client saying "Opening password file failed." I'm pretty sure this is to let students see what's on the server screen but don't know since I can't get it to work.

I bought *The Official Ubuntu Guide* yesterday, which discusses everything I have working but leaves this particular funtionality out. Is this supposed to be a future feature that isn't working yet?  Its strange that its missing from the guide.

The product is awesome and I'm trying to introduce it to a school. I think this is a winning point for the software if I can get it to work. I'd hate for the school to be down on it because I can't figure it out.

Many thanks to all who offer help.

---

### Post by kugn on 2007-11-21
I can't help with your problem, but have you tried the server forum?

---

### Post by Dzenhax on 2007-11-22
No, I didn't think of it necessarilly as a server problem.  But maybe I should have.  I will give it a couple of more days and then post there.

Thanks,

---

### Post by sawback on 2007-12-03
Do you realise that you are one of the culprits of leaving an incomplete answer to this question on the web?

Anyhow I have x11vnc installed in chroot as described in the how-to you link, keeping in mind your notes (the apt-sources pointer being a big one, thanks) and have rebooted a client -- still get the same error from Thin Client Manager "Install x11vnc on the client"

---

### Post by Dzenhax on 2007-12-03
Hi Sawback,

     I haven't posted the answer because I don't have one.  I was really hoping to get one here.  For me, if I don't get an answer in the Ubuntu forum I figure there is no solution.  So I guess that ther isn't one for this one.  I will just assume that this is a planned future feature that does not yet work.  I can't find anyone else that has been able to get this to work either.

     That's too bad too.  Inclusion of that feature would have sealed the deal of making this the best classroom package I've ever dealt with.

---

### Post by Dragonbite on 2007-12-06
I am so glad to see other people using Edubuntu and LTSP.  I'm setting up a system and running into issues and trying to get information has not been easy.

I've seen this issue too, and thanks for the wiki link!  I had no idea how to even start!

Wish Ubuntu would set aside a forum for Edubuntu for these more specific questions.

---

