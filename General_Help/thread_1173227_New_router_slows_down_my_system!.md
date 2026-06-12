---
title: "New router slows down my system!"
date: 2009-05-29
forum: General Help
---

### Post by JoskeTobben on 2009-05-29
I have a pretty bizarre issue. Ever since I replaced my router, my system experiences strange slowdowns. My CPU load isn't high, my RAM is barely used, but the x-server loads slowly (some extra time between the moment my desktop shows and the moment everything else is ready), and whenever I start a program (or even a simple terminal window) I get a very significant lag. Once a program is started, things go at normal speed. I'm having no problem with browsing the Internet, by example.

Another strange symptom is that I can't mount my truecrypt volume anymore, at least not in the orthodox manner. Whenever truecrypt requests administrator privileges and I enter my root password, it says it was unable to get administrator privileges. If I run the command line as root before I start truecrypt, it mounts without any problem. I'm dazed and confused here.

Any takers on how my router might be able to sabotage my system and how I can teach it to behave?

---

### Post by dhughes on 2009-05-29
Why do you think it's your router? 

 I know you said you replaced it recently but if you remove it from your system does your system act normally, faster?

---

### Post by JoskeTobben on 2009-05-29
Yes. If disconnected, it behaves normally.

---

### Post by fuzzyworbles on 2009-05-29
cum hoc ergo propter hoc.
 
what happens when you're not connected at all?
 
what does 'sudo top' say?

---

### Post by anarchyinc on 2009-05-29
The **only** thing I can think of that would cause a **router** to make your computer slower loading programs (we are talking about programs, not anything having to do with getting out to the internet, right?) would be some form of power surge. And that is a long shot. Bad configurations causing some form of DOS attack to 127.0.0.1 could do it too... Reminds me of when I used to write crappy kiddiescripts.
 
 
If that is the case you might need to get yourself another router and test it out.

---

### Post by JoskeTobben on 2009-05-29
> **fuzzyworbles said:**
> cum hoc ergo propter hoc.
 
what happens when you're not connected at all?
 
what does 'sudo top' say?

Nothing out of the ordinary. Some frequently changing list with the usual active processes.


> **anarchyinc said:**
>  Bad configurations causing some form of DOS attack to 127.0.0.1 could do it too... Reminds me of when I used to write crappy kiddiescripts.


Actually.. I might have some crappy kiddie-ish scripts around somewhere. It's been a while since I got enthousiastic with shell scripts, so there might be some bothersome stuff somewhere out there. Gonna clean out some bin folders. Thanks!

As for the power surge theory: are you saying that my router is giving electrical shocks via the network cable precisely at the times I start a program? I can't say I really understand how you'd imagine this could happen.

---

### Post by JoskeTobben on 2009-05-29
Removed suspicious scripts. No changes.

It seemed like a good moment to test the jaunty live cd I obtained recently. Everything appears to work as it should. 

I think I'm just gonna do a fresh install. It's been a while since I've done one of those. This screwed up state my system's in is an excellent opportunity to finally start over.

---

