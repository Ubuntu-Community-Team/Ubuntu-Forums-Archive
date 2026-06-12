---
title: "Till Software?"
date: 2009-05-15
forum: General Help
---

### Post by aaronmarsh632 on 2009-05-15
Hi.

I was wondering if there is any invoice software for ubuntu.

I would like it to have an inventory.
Store and print invoices.
Store customers details
and Store and print repair forms.

I know i can do this with a database in openoffice. but i would like to know if there are any alternatives as i only know how to use microsofts access. There is some software for windows called simply invoice ([http://www.simplyinvoice.co.uk/](http://www.simplyinvoice.co.uk/)). If there is something similar to this on ubuntu that would be great, and i dont want to run simply invoice thru wine.

Thanks

---

### Post by gettinoriginal on 2009-05-15
Have you tried here ??  :D
[http://www.ubuntu.com/products/softwarecatalogue](http://www.ubuntu.com/products/softwarecatalogue)

---

### Post by mbeach on 2009-05-15
I was toying with BambooInvoice for a bit, but it lacks an inventory component.  I believe the author is porting it to django which would make it quite interesting, and likely quite easy to add on your own modules. It may not be exactly what you want, but it may be a place to start looking.
[http://www.bambooinvoice.org](http://www.bambooinvoice.org)

gnucash is another option
[http://www.gnucash.org/features.phtml](http://www.gnucash.org/features.phtml)
but I've never really used that in a production environment with real data.

You may find some other options in a thread about gnucash alternatives:
[http://ubuntuforums.org/showthread.php?t=102844](http://ubuntuforums.org/showthread.php?t=102844)

---

### Post by dankegel on 2009-05-16
> **aaronmarsh632 said:**
> There is some software for windows called simply invoice ([http://www.simplyinvoice.co.uk/](http://www.simplyinvoice.co.uk/)). If there is something similar to this on ubuntu that would be great, and i dont want to run simply invoice thru wine.


While you're looking for a native package, I decided to see
if Simply Invoice would run in Wine (even though you didn't
want this, somebody else might). 
It looks like the answer is yes, but you have to do 
  wget kegel.com/wine/winetricks
  sh winetricks dotnet20 wsh56 mdac28 jet40
first.  (See [http://bugs.winehq.org/show_bug.cgi?id=18486](http://bugs.winehq.org/show_bug.cgi?id=18486) )
If you decide to try that, please let us know if you run into any trouble.
(You might need the latest wine; see 
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313) for more help.)

---

### Post by aaronmarsh632 on 2009-05-18
Thanks for all these replies, i'm just giving bamboo invoice a try now

---

### Post by dankegel on 2012-04-08
[http://bugs.winehq.org/show_bug.cgi?id=18486](http://bugs.winehq.org/show_bug.cgi?id=18486) is now marked as fixed.

---

### Post by howefield on 2012-04-08
Old thread closed.

---

