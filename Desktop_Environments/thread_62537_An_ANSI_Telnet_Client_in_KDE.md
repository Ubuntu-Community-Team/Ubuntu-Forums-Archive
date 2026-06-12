---
title: "An ANSI Telnet Client in KDE"
date: 2005-09-05
forum: Desktop Environments
---

### Post by J. Allen on 2005-09-05
Hello everyone,

First of all, I love Ubuntu. It is magnificent, and light years ahead of the Microsoft platform. The work
done on this project is phenomenal. I am so happy with this OS. I just wanted to say that first.

Anyway, to the topic at hand.I looked through the topics to make sure this didn't exist yet, and if it does, I apologize, I may have missed it. I have a question if I may ask.

I used to run telnet programs often, because I enjoy telnet BBSing. Unfortunately, while 
Ubuntu has a telnet client, it does not appear to support ANSI, which makes telnet BBSing
almost useless. I looke for clients across the internet, but to no avail for Linux.

I used the Synaptic Package Manager and found a program called francine. I downloaded
it (via Synaptic Pkg Manager) and I can't find it. I typed francine in the command line and 
nothing happened. So I typed "francine" (without quotes) in the Terminal and it popped up and asked for a password to Debian telnet. So I don't know what's up.

Sincerely,
-J.

---

### Post by ltmon on 2005-09-05
I don't know anything about francine, but there is a *nix version of PuTTY.  If it's not in repositories you can download the source at [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) and compile yourself (what fun ;) )

L.

---

### Post by Harleen on 2005-09-05
What's wrong with the plain old telnet command run from a konsole window? I'm not using telnet too much, but unlike windows I didn't have any trouble yet using telnet on a UNIX machine.
You can effect the behaviour by setting the TERM environment variable after connecting. It should work like this:

 telnet 123.456.789.1
<login>
export TERM=ansi

---

### Post by J. Allen on 2005-09-05
Thank you. That works, **harleen**, the only problem I have is that the characters are oddly shifted, and I don't get complete ansi menus, only partial ones. Is there a way to fix that?

You see, I used to have a program called mTelnet. It was wonderful and worked like a charm. The only problem is there is no alternative like it for Ubuntu as far as I can see. I could be wrong though, which is why I asked. :)

Oh and **Itmon**, thank you, too. I downloaded putty, but it didn't seem to work right. It wouldn't let me beyond the login screen. But I appreciate your advice!

-J.

---

