---
title: "Weird Forum Issues."
date: 2008-11-08
forum: Forum Feedback &amp; Help
---

### Post by Roasted on 2008-11-08
Half the time when I refresh the page, it comes up as normal.

the other half of the time when I refresh the page, it's like the formatting is gone. Blue text, white background, different font, etc.

What gives? I never had this issue before. Ever.

---

### Post by LaRoza on 2008-11-08
> **Roasted said:**
> Half the time when I refresh the page, it comes up as normal.

the other half of the time when I refresh the page, it's like the formatting is gone. Blue text, white background, different font, etc.

What gives? I never had this issue before. Ever.

That is just the delay in the style sheet loading. The white and blue look is what the forum looks like with no theme :-)

---

### Post by kellemes on 2008-11-08
> **Roasted said:**
> Half the time when I refresh the page, it comes up as normal.

the other half of the time when I refresh the page, it's like the formatting is gone. Blue text, white background, different font, etc.

What gives? I never had this issue before. Ever.

Sometimes you may need to refresh your browser's cache also..
With Firefox you can do this with CTRL-Shift-F5 or CTRL-Shift-R as far as I know. "Shift-clickrefreshbutton" works also.

---

### Post by Roasted on 2008-11-08
Thanks!

---

### Post by Frak on 2008-11-08
Nope, theme still gone for me.

Safari 3

---

### Post by kellemes on 2008-11-08
To be honest, I've had this issue a couple of times today (more than normal), it seems the CSS-stylesheet isn't loading too well.

---

### Post by Ozor Mox on 2008-11-08
This is happening a lot for me as well.

---

### Post by killer2239 on 2008-11-08
Glad to know im not the only one with this problem.

---

### Post by cdtech on 2008-11-08
It happens to me as well. I've only noticed this with the upgrade to intrepid. I can refresh the page and it loads properly sometimes.

---

### Post by Joeb454 on 2008-11-08
It's likely due to the addition of new hardware. Now we have 2 webservers they both need to read the stylesheet from a shared resource.

I'm willing to bet that it's one of the servers having a delay in reading from the source

---

### Post by LaRoza on 2008-11-08
> **Joeb454 said:**
> It's likely due to the addition of new hardware. Now we have 2 webservers they both need to read the stylesheet from a shared resource.

I'm willing to bet that it's one of the servers having a delay in reading from the source

It may be browser cache issues as well. I experienced this once, a day ago, and haven't since.

I use Opera, and we all know of Fx's cache issues ;-)

---

### Post by ubuntu-geek on 2008-11-08
> **LaRoza said:**
> It may be browser cache issues as well. I experienced this once, a day ago, and haven't since.

I use Opera, and we all know of Fx's cache issues ;-)
The forums will be going down really quick so I can potentially fix this issue.

---

### Post by LaRoza on 2008-11-08
> **ubuntu-geek said:**
> The forums will be going down really quick so I can potentially fix this issue.

Thanks, although I haven't experienced except once :-)

I hope the issue is uncomplicated.

---

### Post by ubuntu-geek on 2008-11-08
If you are having style sheet issues please hit "f5" in firefox to force a refresh. This should correct the issue for you.

---

### Post by -grubby on 2008-11-08
> **ubuntu-geek said:**
> If you are having style sheet issues please hit "f5" in firefox to force a refresh. This should correct the issue for you.

Browser discrimination :P. 

I'm pretty sure most browsers use F5 to refresh though (Or you can just press refresh..).

---

### Post by LaRoza on 2008-11-08
> **nathangrubb said:**
> Browser discrimination :P. 

I'm pretty sure most browsers use F5 to refresh though (Or you can just press refresh..).

Well, other browsers don't have the problem :-)

(I don't know if that is true, but I know it is true for me)

---

### Post by Joeb454 on 2008-11-08
Ctrl + F5 is a hard refresh I believe, that may work better :)

---

### Post by ubuntu-geek on 2008-11-08
Some people don't know the issue because they were always on the same webserver that was serving the css correctly. Either way if you have the issue you must force a refresh in order for the issue to be corrected.

---

### Post by Frak on 2008-11-08
It's working again. Hooray

---

### Post by Roasted on 2008-11-09
Working great for me! Thanks fellas.

---

