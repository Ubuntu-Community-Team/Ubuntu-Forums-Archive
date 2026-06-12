---
title: "Troubleshooting Problems with Responsiveness of UI"
date: 2009-03-22
forum: General Help
---

### Post by cfree220 on 2009-03-22
Hi all,
Lately I've been having some issues with the responsiveness of various parts of the gnome user interface. Some examples of this are the top bar, which will occasionally not respond to clicking on the drop down menus (will take a very long time to do so, anyways). I can see the the menu title is highlighted, but no menu...

Sometimes when I am running an application, usually firefox, the window will dim, and closing it brings up the force quit dialogue. This is a relatively new issue... with the exception of the Emerald UI, I have rarely had problems with applications ceasing to respond until only very recently.

Sometimes a program will not dim, but I am not able to interact with it. For example, OOo 3.0. Sometimes when I switch to that window, I am not able to place the cursor within the text field. I have found that minimizing it and raising it again can resolve the issue... but I would prefer if it just worked as intended.

Finally, AWN sometimes ceases to work. I suspect that this is more related to the OS freezing up, as other programs become sluggish when this issue is active.

If I were using Windows, I'd try various system restore points to go back until whatever bit of software was causing the problem was eliminated. Obviously I do not have that luxury with Ubuntu (as far as I know). Also, I'm the kind of person who goes a little crazy with the free, open source thing. I don't know how to pull up the package install history, and even if I could... yikes, that's a lot to go through.

I've never really had to troubleshoot this type of a problem before. I'm good at using google and these forums to troubleshoot and fix configuration issues when I know the source of the problem (and just not the solution). With these issues, however, I do not even know how to begin identifying cause...

I don't expect that anyone will be able to read this and say, "Well there's your problem! You have the finnotiny rod connected to the harmonic stabilizer when it should be connected to the nautiloid wingnut," but any help you can give me in finding a starting point would be great!

---

### Post by cariboo on 2009-03-22
I would suggest you have something running using all of your cpu cycles. You can check SYstem-->Administration-->System Monitor, but that won't realy be conclusive. Open an Applications-->Accessories-->Terminal and type:

```
top
```

And note which apps are using all your cpu cycles. See screenshot for an example.

Jim

---

### Post by cfree220 on 2009-03-22
AWN does seem to use a lot...

---

### Post by Neobuntu on 2011-02-06
Yeah, people running top, in the CLI will go over well... [NOT!]

I've been a geek since (before) 1982. I used GNU/Linux for a long time and I can't define the problem.

I've been **all over** the System monitor and I can't see the offending program. 

I suspected Firefox and have been trying all manner of plug-in removal and all. Nothing has helped. 

I have the same problem and Firefox was not even running! (No, it wasn't in top, or the System Monitor.)

Currently the Software Manager is crashing (It dims and upon closing the windows, it's requiring a Forced Quit.

I've had this problem off and on over a week now. I wish I had a clue where to start. Not to mention the 5 other major regressions that I've been battling, these months. Look friends; if this stuff starts requiring more time, than Windows, were done; game over. 

Looks like I must upgrade my advice, to wait even longer than 3 months; after a new "release" is, "official". Of course, hanging-back (the LTS lie) is failing too. It loses, "safety in numbers" support, all to quickly.  So, I guess we're done. The only question is **why**?

Is it...

a) Simple incompetence; too little stability. Do we need to **slow down**?  or...

b) Somebodies getting paid off; to Sabotage Ubuntu's good reputation. 

Take your pick; things are screwy! Stick a **fork** in it, I guess. Is this the beginning of the end, for overly commercial Ubuntu? Maybe it should actually work, before trying to mold it into your own personal money machine, aye?

Listen! Some of us, actually want to do something; besides fix complex and time consuming issues, all the %#@ time! Even if we can!

I think we've lost, working, leadership.

I tell you one thing more, too. For all you "smart tale" people, out there or even moderating; that have a distaste for my feelings about this mess, just tell me one thing. How can I continue to recommend (and multiple install for them) all this stuff, when it starts to reflect **poorly** upon me, with all these regressions?!

---

### Post by Neobuntu on 2011-02-07
OK, the dimming is a new "visual bell", just indicating a error. The real issues is; why are various, different programs hanging and requiring a forced quit?

---

