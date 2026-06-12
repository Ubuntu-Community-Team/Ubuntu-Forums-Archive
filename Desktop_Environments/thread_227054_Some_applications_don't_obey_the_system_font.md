---
title: "Some applications don't obey the system font"
date: 2006-08-01
forum: Desktop Environments
---

### Post by Nannygoat on 2006-08-01
Hello,

I've followed a cleartype howto and I am very satisfied with the result. But some applications don't seem to work correctly with Tahoma and have awlful jagged menu fonts - Open Office, Amarok, Skype. Is there a way to customize these single apps settings? In OO ana Amarok I've already set to use the system fonts but without success. Thanks for your help!

edit: Skype fixed with qtconfig. Amarok and OO still ugly.
edit2: Amarok fixed with kcontrol.

Can't find solution for OO anywhere though.

---

### Post by jonrkc on 2006-10-18
I think this will fix your ugly menu problem in OpenOffice.org:

Under "Tools" choose "Options" and then in the General Options choose "Fonts."  Check "Use substitution table," and then click the box on the left where you can choose what font you want to substitute another for.

Go down to where it says "Interface User."  Select that one.

Then in the box for the font you WANT to use, choose whatever font that is.

I have had to do this every time I've installed a new version of OpenOffice.org; the instructions are buried on their website as I recall.  

Hope it works for you.

---

### Post by arjones85 on 2007-10-05
Can you please explain what you mean by fixed with qtconfig? I have installed tahoma with subpixel smoothing and medium hinting and its great, very easy on the eyes.

But some applications are ignoring that as well and I can't seem to figure out how to fix that

---

### Post by nothingxs on 2007-10-24
This doesn't seem to work in the current version of OpenOffice.org -- I'm still confused.

I'll see if Skype is fixed with the qtconfig fix, though.

EDIT: No dice. OO.org and Skype ignore qtconfig.

---

### Post by timcredible on 2007-10-28
same question here - i like gutsy real well, except for the system fonts in openoffice

---

