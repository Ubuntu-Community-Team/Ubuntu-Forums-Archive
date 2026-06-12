---
title: "Synaptic Package Manager question"
date: 2009-06-15
forum: General Help
---

### Post by fooey on 2009-06-15
From time to time, I'll open up Synaptic throughout the day. I hate having to key in my damn password all the time. Is there a way to "remember password" with it? I don't need the spiel of "*well it's more secure not to do that*", if it's even possible. I'm aware of security concerns, and my computer/network is plenty secure. I'm just looking for a resolution to that annoyance...that's all. Thanks in advance.

---

### Post by scrooge_74 on 2009-06-15
That security feature is in there for a reason, taking that out will defeat the purpose of security and will be as using the "security" feature in Vista that lets you click away.

Why you need to check synaptic so often? I can go weeks without opening it, only use it when I want to install something.

---

### Post by fooey on 2009-06-15
Sigh. I'm aware it's there for a security reason. I just wanted to know if there was an option I could add to the synaptic command to stop it.

I don't go in there that often. I usually just use apt-get, but especially lately, I've been going in there & just looking up different media players etc (*i'm aware of aptitude*).

Anyways, thanks for the reply & adding in that "security is there for a reason" response that I didn't want to hear.;)

Also, why bash Vista in your response? That OS is fine, if you're not a complete moron & know how to use/setup Windows properly, no?

---

### Post by Cheesemill on 2009-06-15
You could always extend your sudo timeout value, that way you only need to type your password in once.

See [http://ubuntuforums.org/showthread.php?t=763142](http://ubuntuforums.org/showthread.php?t=763142) for more details.

---

### Post by scrooge_74 on 2009-06-15
I wasnt exactly bashing VISTA (I sure dont like it), but it was the only example I had at the moment. MS went to lenghts to tell that the system was more secure etc, etc. And then you realize what they did was dumb. I always complain that normal users (my dad, my wife, friends), click on stuff and dont read what it said (be XP or VISTA), then complain something is wrong. You go and ask them what went wrong, they just say they saw a message and clicked on it....arrrghhhh!!!

---

### Post by fooey on 2009-06-15
> **Cheesemill said:**
> You could always extend your sudo timeout value, that way you only need to type your password in once.

See [http://ubuntuforums.org/showthread.php?t=763142](http://ubuntuforums.org/showthread.php?t=763142) for more details.

Hot damn. Thank you Cheesemill ! :p

> **scrooge_74 said:**
> I wasnt exactly bashing VISTA (I sure dont like it), but it was the only example I had at the moment. MS went to lenghts to tell that the system was more secure etc, etc. And then you realize what they did was dumb. I always complain that normal users (my dad, my wife, friends), click on stuff and dont read what it said (be XP or VISTA), then complain something is wrong. You go and ask them what went wrong, they just say they saw a message and clicked on it....arrrghhhh!!!

Oh ok...I gotcha now. I know what you mean though - very frustrating. I deal with that almost everyday it seems.

---

### Post by JKyleOKC on 2009-06-15
In addition to Cheesemill's suggestion of increasing the timeout value, you can modify your sudo settings using visudo to eliminate the password requirement entirely for selected applications while leaving matters "as-is" for the rest. You're aware of the security risk in doing so; it can be minimized by such editing, though. The man pages for sudo and visudo give the details.

---

### Post by Simian Man on 2009-06-15
You could also have a terminal open and su to root.  Then if you launch synaptic from the command line it shouldn't bug you about the password.  This way if you are leaving your computer or are done for the day, you can just exit that shell and no more security problem.

---

