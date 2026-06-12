---
title: "Firefox Page Rendering"
date: 2009-06-10
forum: General Help
---

### Post by jbradley5000 on 2009-06-10
I'm having a problem getting a page to render the same in firefox in ubuntu 9.04 as it does in firefox in windows.  The page is glcsonline.org which in windows puts the navigation bar on one line. In ubuntu it spills to two lines.  The css for the page sets the font to the myriad pro font family.  Is there any way to get this to show correctly in ubuntu?

---

### Post by maheshasolkar on 2009-06-10
Looks like font-size is the issue there. If you reduce the font-size (ul.dropdown in default.css), it does not spill into second line. But the navbar now is narrower than the banner - not sure if that is desirable.

One fix for that could be to place the navbar in a div of width same as the banner above. Then use the same background as the dropdown menu items.

Not a CSS expert, but that is what I think.

---

