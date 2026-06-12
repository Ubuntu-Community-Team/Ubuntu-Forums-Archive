---
title: "&gt; dev.copy2eps(file=&quot;~test&quot;) in R"
date: 2008-11-19
forum: Education &amp; Science
---

### Post by spamalot on 2008-11-19
Hi,

I'm calling

> contour(x,y,z) #produces a grah on Graphics Device 2
> dev.copy2eps(file="~test") 

from the R console (I used RKWARD).

it saves the file as expected, except the file icon show a little watch icon (that usually indicates in the process of saving) and although Document Viewer is able to open the file, it shows nothing but Loading...

thanks!

ps: I'm also trying save my graphs another way, see:

[http://ubuntuforums.org/showthread.php?t=987831](http://ubuntuforums.org/showthread.php?t=987831)

---

### Post by hzambran_cl on 2008-11-22
I haven't used the function 'dev.copy2eps', but a similar thing happened to me using the commands:

png(file="plot1.png")
plot(x)

And I found two ways of solving this:

1) with a new call to 'plot' (in your case to 'dev.copy2eps')

2) calling 'dev.off()' from the console, because htis function closes the graphical device. I think this is the correct way of doing it.

Regards,

Mauricio

---

### Post by spamalot on 2008-11-27
Thanks.

Actually, dev.off() didn't work for me, but restarting RKWard altogether did the job.

---

