---
title: "login form problems"
date: 2009-02-23
forum: Forum Feedback &amp; Help
---

### Post by tmetro on 2009-02-23
The login form that appears in the upper right hand corner of most forum pages seems to be having problem...or at least it isn't working correctly on my Firefox 3.0.6 on Ubuntu 8.10. On this machine, clicking in the user name field has no effect and the "User Name" template text in the field never disappears. However, giving focus to the password field, then hitting shift-tab does successfully clear the user name field and permit entry.

On another machine running Firefox 3.0.6 on Ubuntu 8.04 it works as expected. Forms in general seem to be working on the machine in question, so it must be an odd sensitivity to the JavaScript used probably due to one of the 8 non-default extensions that are installed. Still, I haven't noticed a problem like this on any other site with this browser.

 -Tom

---

### Post by jpeddicord on 2009-02-23
What extensions do you have installed? If it works fine on a browser without them it is most likely just that. Try disabling them and see if it helps.

---

### Post by cariboo on 2009-02-23
I have the same problem if I have the minimum font size in Firefox set to anything bigger than 16. It's a pain in the butt getting older. :)

Jim

---

### Post by tmetro on 2009-02-24
> **jacobmp92]Try disabling them and see if it helps.[/QUOTE]

I knew as I wrote the message that the likely way to determine the cause would be to disable each extension in turn to see which is causing the problem, but the time required to do that for 8 extensions exceeds the inconvenience of the problem.


[QUOTE=cariboo907 said:**
> I have the same problem if I have the minimum font size in Firefox set to anything bigger than 16.

The machine having problems had it set to 16 point, the same as the 8.04 machine that wasn't having problems. Setting it to 17 on 8.04 didn't trigger the problem, either.

Though I think you're on to it. The machine having problems is using the "No Squint" extension, and is set to a default text zoom of 120%. I started up another instance of FF on 8.10 using a profile I happened to already have that doesn't have "No Squint" installed, and the login worked. I then selected:

View->Zoom->Zoom Text Only
View->Zoom->Zoom In
View->Zoom->Zoom In
 
and was able to reproduce the problem. I was able to reproduce it on 8.04 as well, but needed to boost the zoom another step or two. Probably due to variations in resolution or browser window size.

Thanks for the tip. That saves me the effort of having to restart FF a dozen times to find the offending extension.

My guess is that the search box is crowding out the user name box, and FF is pushing it to a lower layer. Most likely a bug, but one that could be worked around.


> **cariboo907 said:**
> It's a pain in the butt getting older. :)

Definitely. Though I try and convince myself that it's not so much my eyes as it is the screens increasing in resolution and making fonts of the same point size appear smaller. If you're old enough to remember what text looked like on a CGA resolution screen, you'll know hat I mean. :-)

 -Tom

---

### Post by drubin on 2009-02-24
> **cariboo907 said:**
> I have the same problem if I have the minimum font size in Firefox set to anything bigger than 16. It's a pain in the butt getting older. :)

Jim

This has been shown in a previous thread(with screen shots) if only I could find it. 

The login box tends to be unusable with larger font sizes and an average screen.

---

