---
title: "Acroread Problem"
date: 2009-05-17
forum: Desktop Environments
---

### Post by phillip181 on 2009-05-17
Everytime I try to start Acrobat Reader 9, it comes up An Internal Error Has Occured. I have tried reinstalling it, but it still happens. Does anyone have any idea?

---

### Post by kpkeerthi on 2009-05-17
How did you install acrobat reader?

Do you really need acrobat? Its one heck of a bloated closed source junk. The default Document Reader (evince) that comes preinstalled with Ubuntu handles PDFs just fine. 

If you still insist, :), I suggest you install it from the repository. Make sure 'partner repository' is enabled under System -> Admin -> Softwares Sources and then run this command:
```
sudo apt-get install acroread
```

---

### Post by coffeecat on 2009-05-17
> **kpkeerthi said:**
> If you still insist, :), I suggest you install it from the repository. Make sure 'partner repository' is enabled under System -> Admin -> Softwares Sources and then run this command:

That's true for 32-bit Jaunty, but for 64-bit you have to use Medibuntu and you only get version 8. Or at least that was true a couple of weeks ago when I last checked.

**phillip181**, if you really get stuck with Acroread and find Evince too basic for your needs, have a look at Okular. It's in the repositories and is excellent. It's a KDE app though and will bring in some KDE dependencies if you're running Gnome.

---

