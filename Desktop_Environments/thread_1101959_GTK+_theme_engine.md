---
title: "GTK+ theme engine"
date: 2009-03-20
forum: Desktop Environments
---

### Post by joplass on 2009-03-20
Please someone stir me in the right direction.  Apperance keep telling me that I need to instal GTK+ theme engine.  I have installed almost every package with GTK engine but nothing is working.

---

### Post by MissKitty on 2009-03-20
What is it that you are trying to do? Why do you need to install GTK + theme engine?

---

### Post by joplass on 2009-03-21
> **MissKitty said:**
> What is it that you are trying to do? Why do you need to install GTK + theme engine?
There are a few themes I installed but "Apperance" has this sort of error message: "This theme will not look as intended because the required GTK+ theme engine is not installed".
In another thread I found here the poster said adding a known engine name in the below lines in gktrc will fix that error. 
FROM:
style "unstyle"
{
	engine ""
	{
	}
}

TO (i.e.):
style "GTK2-engines-pixbuf"
{
	engine ""
	{
	}
}

---

