---
title: "firestarter info"
date: 2009-01-19
forum: General Help
---

### Post by bu2971x on 2009-01-19
can I get Firestarter or the regular network icon thing to show me cumulative MB downloaded like for a week or month...??????  not just for the previous session.....    thanks

---

### Post by Titan8990 on 2009-01-19
Firestarter is a dead project....

You should check out ufw and ufw GUIs in Synaptic. 


For a network logger you will want to look in to something other than a firewall GUI. Someone should be able to drop in and recommend something.

---

### Post by blueshiftoverwatch on 2009-01-24
> **Titan8990 said:**
> Firestarter is a dead project....

You should check out ufw and ufw GUIs in Synaptic.
After installing GUFW (GUI for UFW) I've noticed that it doesn't seem as advanced as Firestarter. Under Firestarter you could view blocked or active connections and lock/unlock the firewall. Under UFW I don't have any of those options. All you can do is modify the settings for which ports are allowed/blocked.

What are the benefits of using GUWF over Firestarter? If all they are is graphical frontends to modify the actual firewall what difference would it make if the project was active or dead? It doesn't seem like something that would need to be regularly updated.

---

### Post by OrangeCrate on 2009-01-24
> **blueshiftoverwatch said:**
> After installing GUFW (GUI for UFW) I've noticed that it doesn't seem as advanced as Firestarter. Under Firestarter you could view blocked or active connections and lock/unlock the firewall. Under UFW I don't have any of those options. All you can do is modify the settings for which ports are allowed/blocked.

**What are the benefits of using GUWF over Firestarter? If all they are is graphical frontends to modify the actual firewall what difference would it make if the project was active or dead? It doesn't seem like something that would need to be regularly updated.**

Agreed. Most of the FUD regarding Firestarter, comes from just a couple security "experts" here on the forums, and others have seemed to accept their repeated negative comments, as "fact". I asked one of the individuals to put up or shut up in a previous thread, and no sources were provided to confirm their statements.

---

### Post by hyper_ch on 2009-01-24
you run firestarter as root and you should never run something as root when it's not really necessary. Besides firestarter hasn't seen any update for years and the official canonical stance is now towards ufw.

Furthermore, are you even sure you need to play around with iptables at all?

---

### Post by OrangeCrate on 2009-01-24
> **hyper_ch said:**
> you run firestarter as root and you should never run something as root when it's not really necessary.

If you're not running Firestarter as a service, and you're simply using it as a GUI to configure iptables, how is it running as root?

> Besides firestarter hasn't seen any update for years

What **exactly** has to be updated for it to continue to do what it was designed to do?

> and the official canonical stance is now towards ufw.

I'm sorry, I must have missed that announcement. Can you cite the source of that comment, and provide a link to the official announcement?

> Furthermore, are you even sure you need to play around with iptables at all?

Frankly, it's none of your business what other users do with, or how they wish to configure their computer.

---

### Post by hyper_ch on 2009-01-24
> **OrangeCrate said:**
> If you're not running Firestarter as a service
How do you start it then?

> **OrangeCrate said:**
> What **exactly** has to be updated for it to continue to do what it was designed to do?
This has been answered here countless times before, I think with a little research you'll find it out yourself.


> **OrangeCrate said:**
> I'm sorry, I must have missed that announcement. Can you cite the source of that comment, and provide a link to the official announcement?
Have a look at the ubuntu site.

> **OrangeCrate said:**
> Frankly, it's none of your business what other users do with, or how they wish to configure their computer.
And neither is illadvice appreciated ;)

---

### Post by OrangeCrate on 2009-01-24
> **hyper_ch said:**
> How do you start it then?


This has been answered here countless times before, I think with a little research you'll find it out yourself.



Have a look at the ubuntu site.


And neither is illadvice appreciated ;)


As expected, **not one** answer to my inquiries was provided. It's the same nonsense I referred to in my original post in this thread, and, in this thread:

[http://ubuntuforums.org/showthread.php?t=956202&highlight=orangecrate+firestarter&page=3](http://ubuntuforums.org/showthread.php?t=956202&highlight=orangecrate+firestarter&page=3)

---

### Post by hyper_ch on 2009-01-24
> **OrangeCrate said:**
> As expected, **not one** answer to my inquiries was provided.

Answer was given, you just refuse to do a little work yourself ;)

---

### Post by blueshiftoverwatch on 2009-01-24
> **hyper_ch said:**
> you run firestarter as root and you should never run something as root when it's not really necessary.
Doesn't Gufw do the same thing as Firestarter if you have it minimized onto your system tray? I set Gufw to "autostart with session" and I can click on the tray icon and have it come up without needing a password (after entering the password previously when I logged) in just like Firestarter.

Is going what I described above with Gufw not a good idea for security reasons? Or is having Gufw running all the time safer than having Firestarter run all the time?

---

### Post by OrangeCrate on 2009-01-24
> **hyper_ch said:**
> Answer was given, you just refuse to do a little work yourself ;)

No, that's not how it works. When a person shoots their mouth off, and they're called on it, they're expected to backup their statements with facts.

If all they can answer is "Google it", or "look for yourself", then they've simply been "outed", and more than likely what they're spreading as truth, is just FUD.

---

### Post by hyper_ch on 2009-01-25
> **OrangeCrate said:**
> No, that's not how it works. When a person shoots their mouth off, and they're called on it, they're expected to backup their statements with facts.
Why should I do the work that you can easily do yourself? Do whatever you want...

---

### Post by mb_webguy on 2009-01-25
> **OrangeCrate said:**
> I'm sorry, I must have missed that announcement. Can you cite the source of that comment, and provide a link to the official announcement?

Well, I can sort of address that bit.  Ufw is shipped as part of the Ubuntu distribution, and firestarter isn't.  Therefore, ufw is the "official" front-end for iptables, and firestarter isn't.

As far as updates being required for something to continue to do it's job...  Firestarter is a front-end for another program.  If the base program is updated, at best those changes may not be reflected in an out-of-date front-end, and at worst it will no longer be compatible.  Iptables is an active project.  Therefore, whatever front-end you use should also ideally be an active project.  Ufw is, and firestarter isn't (and hasn't been for a very long time).

---

