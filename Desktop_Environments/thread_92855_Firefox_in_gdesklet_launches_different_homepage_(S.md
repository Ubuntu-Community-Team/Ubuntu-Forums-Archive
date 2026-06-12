---
title: "Firefox in gdesklet launches different homepage (Solved)"
date: 2005-11-20
forum: Desktop Environments
---

### Post by Darrin on 2005-11-20
I have gdesklet installed and am using the starter bar. I have firefox as a new starter there. When I launch firefox from the starter bar the default web page displayed is [http://www.arizona.edu/](http://www.arizona.edu/). Looking at the settings it still has my default home in there which is [http://ubuntuforums.org/](http://ubuntuforums.org/). However if I click the home button on firefox, Ubuntu forums is launched. Ubuntu forums is the default homepage when I launch firefox through the shortcut in applications. 
Why does it launch the arizona page by default when launching firefox from the starter bar? How do I fix that?

---

### Post by darknuala on 2005-11-20
go to properties, and get rid of the %u

make sure the command just says firefox

---

### Post by Darrin on 2005-11-20
Thank you. Problem solved. By the way, what does the %u define?

---

### Post by PaulEdwards on 2006-08-13
> **Darrin said:**
> Thank you. Problem solved. By the way, what does the %u define?
%u allows you to drag a file onto the icon to open it with that application.

However, that is so rarely done that it's a good trade-off to escape the arizona.edu junk.

Oddly enough, the menu entry in the main applications menu for firefox includes the %u and doesn't have the arizona.edu effect... I looked in the python code for the StarterBar gDesklet and didn't find anything, so I conclude that it may be something hard-coded into gDesklets itself.

---

### Post by sublime_ndg on 2006-11-07
I'm really glad I found this thread!  I had this same problem, and coincidentally, two of the other computers on my home network do have [www.arizona.edu](www.arizona.edu) as their home page, so I thought something was going fishy there.

The solution worked, by the way, thanks.

---

