---
title: "Problem with Pidgin and Empathy -  too many authorization requests"
date: 2008-12-29
forum: General Help
---

### Post by galvao on 2008-12-29
Greetings.

I'm having a huge headache with a problem that is, in part, my own fault. This will be a somewhat long post, but I really wanna explain this well:

I was working at a company that uses Psi as their IM client. I was using it there with no problem at all (although this is hardly relevant to the subject) and then I've made the (sad) decision to import my MSN contacts into this Psi client.

Problem is I have something around 230+ contacts on my MSN contact list and due to particularities of the network of this company every and each one of them got a '@name-of-the-company-I-was.com' appended to it, generating 230+ new authorization requests that I had to send and approve (same as when you add a contact to the list).

After doing all this I've got home and when I started Pidgin the real problem began: Pidgin now opens one authorization request for each of this 230+ contacts, but unlike Psi it tries to open the 230+ authorization windows at once, causing a huge resource comsumption.

My problem is not even that (I'm somewhat patient with these things), but the problem is Pidgin then crashes before I can authorize even one contact. 

I then tried to use Empathy, hoping that Empathy would do as Psi does and open one window at a time, allowing me to fix this. Well, Empathy doesn't even connect to the MSN network: it just causes some kind of network error, which I believe is related to the 230+ authorization requests (... right?).

I then thought "Well, the solution is to install Psi here. It will open one window at a time and I'll be able to fix this!". Although it was a somewhat smart solution, it all failed because I just can't find any plugins or something like that to allow the Psi I've installed to connect to the MSN network.

So, basically my situation is this: I can't use my MSN account anymore because I can't find a program that connects to it and stays stable so I can fix the problem. I even thought about creating a new MSN account, but c'mon it's hard to believe there's no solution to this...

BTW, not sure if it's relevant, but anyway: at home (where the problem is) I use Ubuntu 8.10. At the company I was using Windows XP.

Can anyone please advise? I hope I was clear enough about the whole thing.

[UPDATE] 

Someone at the Pidgin's Support Mailing List suggested that I could add the MSN Transport Agent to Psi and try to solve that. I'll try this tonight and post the results here. 

[/UPDATE]

TIA,

---

